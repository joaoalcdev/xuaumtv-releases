# XuaumTV Releases

Repositório público destinado exclusivamente à distribuição das versões desktop do XuaumTV para Windows.

O código-fonte e os serviços de produção não são publicados aqui. Este repositório armazena somente os instaladores, a versão portátil e os metadados usados pelo atualizador automático do aplicativo.

## Por que as releases ficam como draft?

Atualmente isso acontece por configuração, e não por uma restrição do GitHub.

O `electron-builder` do projeto principal usa o provedor GitHub com `releaseType` definido como `draft`. O workflow executa o empacotador com `--publish always`, que envia os artefatos para o GitHub, mas respeita essa configuração e mantém a release como rascunho.

Esse comportamento é intencional: permite validar o instalador, a versão portátil, os hashes, o arquivo `latest.yml` e os metadados de atualização antes de disponibilizar uma versão aos usuários.

Uma release draft:

- é visível somente para quem tem permissão de escrita no repositório;
- não aparece na página pública de releases;
- não é retornada pela rota de `releases/latest`;
- não é oferecida pelo atualizador automático aos usuários.

## Como publicar uma versão

Depois de validar os artefatos do draft, existem duas opções:

1. Abrir o draft no GitHub, revisar os arquivos e selecionar **Publish release**.
2. Alterar no projeto principal o `releaseType` de `draft` para `release`, caso a publicação automática apó o build seja desejada.

A publicação automática só deve ser habilitada quando o pipeline validar, no mínimo:

- inicialização e login no aplicativo instalado;
- carregamento de perfis e dados da conta;
- comunicação com a API de produção;
- instalação limpa e atualização sobre uma versão anterior;
- presença do instalador, do arquivo portátil, de `latest.yml` e dos respectivos blockmaps;
- correspondência entre a versão informada e os nomes dos artefatos.

Enquanto uma dessas verificações depender de revisão manual, manter a criação inicial como draft é a opção mais segura.

## Downloads

Versões aprovadas ficam disponíveis na página [Releases](https://github.com/joaoalcdev/xuaumtv-releases/releases).

