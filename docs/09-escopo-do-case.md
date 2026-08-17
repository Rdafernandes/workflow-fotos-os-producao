# Escopo do case público

## Finalidade

Este repositório foi preparado exclusivamente como portfólio. Seu objetivo é permitir que recrutadores, gestores, profissionais de automação e pessoas não técnicas compreendam o problema enfrentado, a solução desenvolvida e as decisões que tornaram a automação confiável.

Ele não é um produto para instalação, um template de n8n ou um backup do ambiente produtivo.

## O que o case permite avaliar

- Capacidade de transformar uma rotina operacional em uma solução automatizada.
- Organização de um problema complexo em responsabilidades independentes.
- Integração entre mensageria, orquestração, banco de dados e armazenamento.
- Tratamento de concorrência, duplicidade, falhas parciais e consistência eventual.
- Preocupação com experiência do usuário e redução de ruído operacional.
- Uso consciente de revisão humana quando não existe decisão determinística.
- Documentação de uma solução técnica para públicos com diferentes níveis de conhecimento.

## O que está publicado

- Explicação funcional e técnica da automação.
- Arquitetura e diagramas de estados.
- Detalhamento dos quatro workflows.
- Exemplos inteiramente fictícios.
- Cópias sanitizadas dos workflows para inspeção visual da lógica e das conexões.
- Orientações para capturas de tela seguras.

## O que não está publicado

- Credenciais, tokens, URLs e identificadores reais.
- Implementação interna das RPCs e estrutura produtiva do banco.
- Camada de ingestão e ferramentas internas de revisão.
- Dados, mensagens, arquivos, pessoas ou Ordens de Serviço reais.
- Instruções de implantação ou reprodução do ambiente.

## Como interpretar os exports

Os JSONs sanitizados servem como evidência técnica da construção no n8n. Eles preservam a topologia, os nós, as conexões, as expressões relevantes e o tratamento de erros, mas foram deliberadamente separados do ambiente de produção.

O valor deste material está na leitura da arquitetura e das decisões implementadas, não em sua execução fora do contexto original.

