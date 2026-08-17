# Privacidade e sanitização

## Objetivo

Preservar valor técnico e legibilidade sem publicar informações que permitam acesso, identificação de pessoas ou mapeamento da infraestrutura real.

## Removido ou substituído

- Tokens, chaves, segredos e referências de credenciais do n8n.
- URL e identificador do projeto Supabase.
- IDs da instância, workflow e versões internas.
- Identificador real do grupo de WhatsApp.
- Nomes de contas, endereços de e-mail e rótulos de credenciais.
- IDs reais de mensagens, arquivos, pastas, pendências e jobs.
- Metadados de implantação, pin data e dados de execução.
- Nomes de pessoas, mensagens e números de OS reais.

## Preservado

- Topologia dos nós e conexões.
- Nomes técnicos de RPCs.
- Expressões relevantes do n8n.
- Regras temporais e limites de lote.
- Código de classificação do reconciliador.
- Contratos genéricos entre componentes.
- Tratamento de sucesso, erro e revisão humana.

## Estratégia nos exports

- URLs, chaves e identificadores reais foram substituídos por referências demonstrativas sem valor operacional.
- Referências de credenciais Google foram removidas.
- Workflows são publicados desativados.
- IDs internos e metadados de instância são removidos.

## Controles aplicados antes da publicação

- [x] Busca pelo domínio real de Supabase.
- [x] Busca por identificadores de grupo, e-mails e nomes de credenciais reais.
- [x] Busca por padrões de JWT, bearer token e API key.
- [x] Confirmação de que nenhum arquivo de ambiente está versionado.
- [x] Remoção de URLs e referências sensíveis visíveis nas screenshots.
- [x] Inspeção dos JSONs após a sanitização.
- [x] Validação de que os exemplos são completamente fictícios.
- [x] Confirmação de que os workflows públicos estão inativos.

## Aviso

Sanitização deve ser refeita sempre que os workflows forem reexportados. Não se deve substituir o arquivo público diretamente por um export de produção.
