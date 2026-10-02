# Coleta_API_DrogariaSP

Script em Python que consulta a **API pública de catálogo** do site da Drogaria São Paulo para coletar **nome e preço** de uma lista de SKUs e salva o resultado em **CSV** com Pandas.

> Projeto de estudo. Usa apenas dados públicos do catálogo, sem login. Se for rodar, respeite os termos de uso do site e mantenha as pausas entre as requisições para não sobrecarregá-lo.

## O problema

Acompanhar o preço de vários produtos de farmácia abrindo página por página é lento e sujeito a erros de digitação. Este script automatiza a consulta de uma lista de SKUs e entrega os dados já estruturados, prontos para análise.

## Como funciona

1. Uma lista de SKUs é definida no próprio script (`sku_list`).
2. Para cada SKU, é feita uma requisição `GET` ao endpoint de busca de produtos do catálogo, filtrando por `skuId`.
3. Há uma pausa de 0,3 s entre as requisições para não sobrecarregar o site. Em caso de erro HTTP, o script espera 1 s e segue para o próximo SKU.
4. A resposta em JSON é reduzida aos campos relevantes e organizada em um DataFrame (Pandas).
5. O resultado é salvo em `produtos_drogariasp.csv`.
6. Ao final, o script lista os SKUs que a API não retornou.

Por usar a API em JSON em vez de automatizar o navegador (como no projeto **Orquestrador**), a coleta é mais rápida e menos frágil a mudanças de layout do site.

## Tecnologias

Python, Requests, Pandas.

## Dados coletados

| Coluna | Descrição |
|---|---|
| id | Identificador do produto |
| nome | Nome do produto |
| sku | Código SKU do item |
| preco | Preço atual do produto |

## Como rodar

1. Tenha o Python instalado.

2. Instale as dependências:

   ```
   pip install requests pandas
   ```

3. Se quiser consultar outros produtos, edite a lista `sku_list` no início do script.

4. Execute o script (use o nome do arquivo do projeto):

   ```
   python nome_do_arquivo.py
   ```

5. O arquivo `produtos_drogariasp.csv` será gerado na pasta do projeto, e o terminal mostrará o andamento e os SKUs não encontrados.

## Limitações

- A lista de SKUs é fixa no código.
- Para cada produto, é lido apenas o primeiro item e o primeiro vendedor da resposta.
- O tratamento de erros cobre erros HTTP; falhas de conexão e tempo esgotado ainda não são tratados.
- O CSV não registra a data e a hora da coleta, e os preços podem variar por região ou promoção.
- Depende de um endpoint público do site, que pode mudar sem aviso.

## Próximos passos

- Registrar data e hora da coleta para formar um histórico de preços.
- Adicionar `timeout` e retentativas automáticas nas requisições.
- Ler a lista de SKUs de um arquivo em vez de deixá-la no código.
- Agendar a execução automática.
