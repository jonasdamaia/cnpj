# Lupa CNPJ

Aplicação web para consultar os dados cadastrais de uma empresa a partir do CNPJ. Você digita o número e a página mostra o dossiê completo, organizado em cards, usando a [BrasilAPI](https://brasilapi.com.br/).

**[Teste aqui](https://jonasdamaia.github.io/cnpj/)**

## Funcionalidades

- **Consulta por CNPJ** com ou sem pontuação: a aplicação limpa o número antes de consultar.
- **Validação oficial** dos 14 dígitos e dos dígitos verificadores, antes de chamar a API.
- **Resumo da empresa:** razão social, nome fantasia, matriz ou filial, situação cadastral com selo colorido e natureza jurídica.
- **Indicadores:** data de abertura, porte, capital social e regime tributário atual.
- **Localização e contato:** endereço, telefones e e-mail clicáveis, botão para copiar o e-mail e link para o Google Maps.
- **Atividades econômicas (CNAE):** principal em destaque e lista completa das secundárias.
- **Quadro societário (QSA):** prévia no card e tabela completa sob demanda.
- **Regime tributário:** histórico por ano, do mais recente para o mais antigo.
- **Menu de opções (engrenagem):** alternar entre tema claro e escuro, copiar o dossiê, exportar os dados em JSON e imprimir.
- **Tratamento de erros** com mensagens específicas (CNPJ não encontrado, limite de requisições, serviço indisponível, falha de conexão) e botão "Tentar novamente".
- **Carregamento** com skeleton enquanto a consulta acontece.
- **Layout responsivo** para celular, tablet e desktop, com versão própria para impressão.

## Tecnologias

HTML, CSS e JavaScript puros, em um único arquivo (`index.html`). Não há dependências, build ou servidor: nada para instalar.

## Como usar

### Online

Acesse a [demonstração](https://jonasdamaia.github.io/cnpj/), digite o CNPJ e clique em **Consultar**.

### Localmente

```bash
git clone https://github.com/jonasdamaia/cnpj.git
cd cnpj
```

Depois, abra o arquivo `index.html` no navegador. Como a página chama a BrasilAPI diretamente, é preciso estar conectado à internet.

## Como funciona

A aplicação faz uma requisição `GET` ao endpoint de CNPJ da BrasilAPI, informando apenas os 14 dígitos no final do endereço:

```
https://brasilapi.com.br/api/cnpj/v1/{cnpj}
```

Exemplo com `curl`:

```bash
curl https://brasilapi.com.br/api/cnpj/v1/00000000000191
```

A resposta em JSON é formatada para exibição: datas no padrão brasileiro, CEP, telefones, CNPJ e capital social em reais.

## Publicar no GitHub Pages

1. Envie o `index.html` para a raiz do repositório.
2. No GitHub, abra **Settings** e depois **Pages**.
3. Em **Build and deployment**, escolha **Deploy from a branch**, selecione a branch `main` e a pasta `/ (root)`.
4. Salve e aguarde a publicação. O endereço será `https://<usuario>.github.io/<repositorio>/`.

## Privacidade

- As consultas saem direto do navegador para a BrasilAPI. A aplicação não tem servidor próprio e não guarda histórico de consultas.
- O único dado salvo no navegador é a preferência de tema (claro ou escuro), em `localStorage`.

## Limitações conhecidas

- Os dados vêm da Receita Federal por meio da BrasilAPI e podem ter atraso em relação ao cadastro oficial. Não substituem certidões ou documentos oficiais.
- O serviço da BrasilAPI tem limite de requisições. Em caso de excesso, a aplicação avisa e permite tentar novamente.
- A validação aceita apenas CNPJs numéricos. CNPJs alfanuméricos, formato adotado pela Receita Federal a partir de 2026, ainda não são suportados.

## Créditos

- Dados: [BrasilAPI](https://brasilapi.com.br/)
- Desenvolvido por [@jonasdamaia](https://github.com/jonasdamaia)
