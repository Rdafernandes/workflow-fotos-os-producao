# Visão geral

## Contexto

Uma equipe de produção registra a execução de serviços por meio de fotos enviadas em um grupo operacional. A evidência precisa ser associada à Ordem de Serviço correta e armazenada de forma padronizada.

O desafio não é apenas mover arquivos. A automação precisa interpretar contexto, esperar complementos sem bloquear a operação, evitar mensagens duplicadas e lidar com falhas parciais entre banco, mensageria e armazenamento.

## Objetivo

Transformar uma mensagem com mídia em uma evidência rastreável:

```text
mensagem persistida
→ OS identificada
→ evidência registrada
→ arquivo organizado
→ resultado físico confirmado
```

Quando a OS não pode ser determinada, o sistema deve pedir ajuda com o menor ruído possível. Quando o estado externo é ambíguo, deve preservar os dados e encaminhar o caso para revisão humana.

## Requisitos funcionais

- Processar mensagens a partir de um identificador persistido.
- Resolver a OS por regras de negócio centralizadas.
- Aguardar complementos antes de perguntar.
- Enviar no máximo uma pergunta e um fallback por pendência elegível.
- Criar ou reutilizar a pasta correta da OS.
- Mover e renomear a mídia de maneira rastreável.
- Reconciliar operações que permaneceram em processamento.
- Registrar falhas e estados não determinísticos.

## Requisitos não funcionais

- Idempotência em execuções concorrentes.
- Rastreabilidade das integrações externas.
- Baixo acoplamento entre etapas.
- Consistência eventual entre banco e Drive.
- Segurança para publicação e operação.
- Intervenção humana explícita em ambiguidades.

## Resultado operacional

Cada foto resolvida termina vinculada a uma OS no banco e armazenada na pasta correspondente no Drive. Pendências legítimas permanecem visíveis, cobranças não se repetem indefinidamente e divergências físicas são detectadas por uma camada independente.

