# Workflow 4 — reconciliação do Drive

## Responsabilidade

Auditar jobs que permaneceram em processamento e reconciliar o banco com o estado físico observado no Google Drive.

![Workflow 4 — reconciliação do Google Drive](../assets/screenshots/workflow-4-reconciliacao-drive.png)

## Frequência e seleção

- Schedule a cada 2 minutos.
- Execução manual disponível.
- Seleção de até 20 jobs com idade mínima de 120 segundos.

## Dados inspecionados

Para cada arquivo, a API retorna somente os campos necessários:

```text
id, name, parents, trashed
```

## Matriz de decisão

| Observação física | Ação | Motivo estruturado |
| --- | --- | --- |
| `trashed = true` | Revisão humana | `file_trashed` |
| Quantidade de parents diferente de 1 | Revisão humana | `unexpected_parent_count` |
| No destino e nome correto | Marcar concluído | `file_already_in_target_with_correct_name` |
| No destino e nome incorreto | Renomear e concluir | `file_already_in_target_with_wrong_name` |
| Ainda na origem | Marcar erro/retry | `file_still_in_source` |
| Em outro parent | Revisão humana | `unexpected_parent` |
| Falha de inspeção | Revisão humana | `drive_inspection_error` |
| Falha de rename | Revisão humana | `drive_rename_error` |

A matriz registra o comportamento implementado pelo nó de classificação. Ela comunica as decisões com mais clareza do que uma captura parcial do código interno.

## Fluxo

```mermaid
flowchart TB
    S[Selecionar stale jobs] --> I[Inspecionar arquivo]
    I -->|erro| M1[Manual review: inspection]
    I --> C[Classificar estado]
    C -->|origem| R[Mark error / retry]
    C -->|destino + nome correto| D[Mark done]
    C -->|destino + nome incorreto| N[Rename only]
    N -->|sucesso| D2[Mark done]
    N -->|erro| M2[Manual review: rename]
    C -->|inesperado| M3[Manual review + snapshot]
```

## Por que não repetir o movimento sempre

Reexecutar cegamente uma operação externa pode introduzir novas inconsistências. O reconciliador escolhe a ação mínima com base no estado observado: apenas confirma, apenas renomeia, agenda retry ou interrompe para análise humana.

Esse comportamento demonstra uma estratégia de recuperação compatível com sistemas distribuídos e APIs sujeitas a falhas parciais.
