# Coleta_API_DrogariaSP

Script em Python que coleta **produtos e preços** do site da Drogaria São Paulo e organiza o resultado em uma **planilha/CSV** com Pandas.

> Projeto de estudo. Usa apenas dados públicos exibidos no site, sem login. Se for rodar, respeite os termos de uso do site e evite sobrecarregar o servidor (use pausas entre as requisições).

## O problema

Acompanhar preços de produtos de farmácia manualmente, produto por produto, é lento e sujeito a erros de digitação. A ideia deste projeto é automatizar a captura e entregar os dados já estruturados, prontos para análise.

## Como funciona

1. O script (Python + Selenium) abre o site e navega até os produtos.
2. Para cada produto, captura as informações exibidas na página.
3. Os dados são organizados em um DataFrame (Pandas).
4. O resultado é salvo em planilha/CSV.

## Tecnologias

Python, Selenium, Pandas.

## Dados coletados

**[PREENCHER: liste as colunas do CSV gerado, por exemplo nome do produto, preço, link, data da coleta]**

## Como rodar

1. Tenha o Python e o Google Chrome instalados.

2. Instale as dependências:

   ```
   pip install selenium pandas
   ```

3. Execute o script:

   ```
   [PREENCHER: comando para rodar, por exemplo python nome_do_arquivo.py]
   ```

4. O arquivo com os resultados será gerado na pasta do projeto.

## Exemplo de saída

**[PREENCHER: cole aqui 3 ou 4 linhas do CSV gerado, em forma de tabela, ou um print]**

## Limitações

- Depende da estrutura atual do site: se o layout mudar, a coleta pode precisar de ajustes.
- Os preços refletem o momento da coleta e podem variar por região ou promoção.

## Próximos passos

- Agendar a execução automática.
- Guardar o histórico de preços para acompanhar variações ao longo do tempo.
- Adicionar tratamento de erros e novas tentativas (veja o projeto **Orquestrador**).

