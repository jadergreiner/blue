# Bem vindo a nossa segunda aula!

Hoje vamos começar a ler dados de fontes externas.

Você sabia que o Pandas suporta a integração com muitos formatos de arquivo ou fontes de dados (csv, excel, sql, json, parquet,...). A importação de dados de cada uma dessas fontes de dados é fornecida por função com o prefixo. Da mesma forma, os métodos são usados para armazenar dados.

Para iniciar, vamos usar uma estrutura de JSON. 

:exclamation: Lembre-se de importar a biblioteca Pandas.

~~~ 
data = pd.read_json('https://servicodados.ibge.gov.br/api/v2/censos/nomes/joao?groupBy=UF')
~~~ 

Agora visualize nosso Dataframe! Tá pronto pra gente analisar e manipular! 

Vamos aproveitar e criar mais um Dataframe com os estados.

~~~
estados = pd.read_json('https://servicodados.ibge.gov.br/api/v1/localidades/estados?orderBy=id')
~~~

Fica o convite para conhecerem as APIs do IBGE e explorar seus recursos, criando novos Dataframes.

https://servicodados.ibge.gov.br/api/docs/nomes?versao=2

Vamos salvar nosso Dataframe em uma planilha? O Pandas já tem recurso para isso. 
Só execute o código abaixo:

~~~
estados.to_excel("estados.xlsx")
~~~

Muito simples, não é verdade? 

O Pandas permite esta interação entre diversos formatos, tanto de leitura quanto a exportação, como fizemos agora, mudando apenas o sufixo.

Fica o convite para interagir com outros formatos.

<img src="./img/readwrite.svg" align="middle">


