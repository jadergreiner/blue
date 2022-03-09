# Aula 18 - [AULA] Introdução ao Pandas - Parte 2

## Conteúdos

1. Ler e gravar dados em arquivos

2. Ler arquivos CSV e Excel

3. Criando subconjuntos

4. Criando gráficos no Pandas


## Ler a gravar dados em arquivos
### Bem vindo a nossa segunda aula!

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


## Ler arquivos CSV e Excel

Vamos usar o Dataset do Titanic

Caso não tenha o Dataset, poderá fazer o download neste link

https://www.kaggle.com/hesh97/titanicdataset-traincsv

Vamos analisar os dados dos passageiros do Titanic, disponíveis no arquivo CSV.

~~~ 
titanic = pd.read_csv("train.csv")
~~~ 

:exclamation: Verifique o caminho do diretório aonde está salvo o arquivo e seu nome.

Certifique-se de sempre de fazer uma verificação sobre os dados após a leitura. Ao exibir o Dataframe sem nenhum parâmetro, as primeiras e últimas 5 linhas serão mostradas por padrão.

~~~ 
titanic
~~~ 

Selecionando as 10 primeiras linhas

~~~ 
titanic.head(10)
~~~ 

:pushpin: Interessado em analisar as últimas linhas? O Pandas também fornece um método de cauda. Por exemplo, retornará as últimas 10 linhas do DataFrame:

~~~ 
titanic.tail(10)
~~~ 

Se você for uma pessoa observadora, deve ter reparado que montamos nosso Dataframe sen especificar os tipos de dados. E como será que o Pandas trata esta questão?
Será que definiu todos como String?

Uma verificação de como os pandas interpretaram cada um dos tipos de dados da coluna pode ser feita solicitando o atributo pandas: dtypes

~~~ 
titanic.dtypes
~~~ 

Para cada uma das colunas, o tipo de dados usado é listado. Os tipos de dados nestes são inteiros, floats e strings.

Interessado em um resumo técnico dos dados?

~~~ 
titanic.info()
~~~ 

As informações do método info() fornecem informações técnicas sobre um Dataframe, então vamos explicar a saída com mais detalhes:

É realmente um DataFrame.

São 891 inscrições, ou seja, 891 linhas.

Cada linha tem um rótulo de linha com valores que variam de 0 a 890 (index)

O Dataframe tem 12 colunas. A maioria das colunas tem um valor para cada uma das linhas (todos os valores de 891 são ). Algumas colunas têm valores perdidos e menos de 891 valores.

As colunas consistem em dados textuais (strings). As outras colunas são dados numéricos com alguns deles números inteiros e outros são números reais (também conhecidos como float ).

O tipo de dados (caracteres, inteiros,...) nas diferentes colunas são resumidos pela listagem do .dtypes

A quantidade aproximada de RAM usada para conter o DataFrame também é fornecida.

Que poder tem o Pandas, não acha?


## Criando subconjuntos

#### Vamos criar novos conjuntos a partir dos dados originais?

:exclamation: Seguiremos analisando o Dataset do Titanic

#### Como selecionar colunas específicas de um Dataframe :question: 

Vamos analisar a idade dos passageiros.

~~~
ages = titanic["Age"]
ages.head()
~~~

Para selecionar uma única coluna, usamos os colchetes com o nome da coluna de interesse. 

Cada coluna em um Dataframe é uma série. A medida que uma única coluna é selecionada, o objeto retornado é uma série Pandas. Podemos verificar testando o tipo

~~~
type((titanic["Age"]))
~~~

Vamos ver o shape deste conjunto de dados

~~~
titanic["Age"].shape
~~~

O shape é um atributo que retorna o número de linhas e colunas. Nosso conjunto tem apenas 1-dimensão, logo retorna apenas o número de linhas.

Seria interessante analisar a idade e o sexo dos passageiros.

~~~
age_sex = titanic[["Age", "Sex"]]
age_sex.head()
~~~

:pushpin: Para múltiplas seleções, use uma lista de colunas entre as chaves.

:bulb: Os colchetes internos definem uma lista Python com os nomes das colunas, enquantos os colchetes externos são usados para selecionar os dados de um Pandas como visto nos exemplos anteriores.

Vamos verificar o tipo e o shape deste novo subconjunto?

~~~
type(titanic[["Age", "Sex"]])
~~~


~~~
titanic[["Age", "Sex"]].shape
~~~

Agora nosso conjunto retorna um Dataframe. Possui 891 linhas e 2 colunas.

#### É possível filtrar os dados de uma coluna específica

E se quisermos retornar apenas os passageiros com mais de 39 anos ❓

~~~
above_39 = titanic[titanic["Age"] > 39]
above_39.head()
~~~

Para selecionar linhas com base em uma condição, use a condição entre os colchetes.

Em nosso exemplo, a condição era <code> titanic["Age"] > 39 </code> . Esta condição checa as colunas que atendem a condição. Vamos ver apenas a condição isoladamente.

~~~
titanic["Age"] > 39
~~~

Nas condições podemos combinar as expressãoes ( >, ==, !=, <, <=, ...), enfim, conforme a lógica que queremos usar. A condição retorna valores boleanos (True/False) que combinados ao Dataframe original retorna um novo conjunto com os dados True.

Nosso Dataframe original tem 891 linhas, vamos ver como ficou nosso novo conjunto ❗

~~~
above_39.shape
~~~

Vamos ver agora apenas os passageiros das classes 2 e 3 ❗

~~~
class_23 = titanic[titanic["Pclass"].isin([2,3])]
class_23.head()
~~~

Semelhante as condições vistas anteriormente, o <code> isin() </code> retorna <code> True </code> a partir de uma lista informada entre os parênteses. Em nosso exemplo, filtramos <code> Pclass </code> e aplicamos uma lista pelo <code> isin() </code> para as classes 2 e 3.

O código acima é o equivalente a utilizar duas condições entre parênteses com o operador "ou"(or) (<code> | </code> )

~~~
class_23_new = titanic[(titanic["Pclass"] == 2) | (titanic["Pclass"] == 3)]
class_23_new.head()
~~~

E se quisermos selecionar apenas os dados aonde a idade do passageiro foi informada ❓

~~~
age_no_na = titanic[titanic["Age"].notna()]
age_no_na.head()
~~~

Incluindo o <code>notna()</code> retorna <code>True</code> apenas nos valores que não sejam nulos. Aplicamos esta condição dentro dos colchetes no Dataframe principal.

Vamos analisar nosso conjunto com os dados de idade informados.

~~~
age_no_na.shape
~~~

Olha que interessante! Nosso conjunto tem apenas 714 linhas. De forma prática e rápida

:triangular_flag_on_post: Dados não informados são conhecidos como "MISSING DATA". Dependendo do projeto, exigirá um tratamento e não poderão simplesmente serem descartados como fizemos aqui. 

#### Como selecionar linhas e colunas específicas ❓

Vamos filtrar um subconjunto apenas com o nome dos passageiros com mais de 30 anos

~~~
adult_names = titanic.loc[titanic["Age"] > 30, "Name"]
adult_names.head()
~~~

Neste caso, um subconjunto de linhas e colunas feito de uma só vez, usar apenas colchetes de seleção não é mais suficiente. Os operadores ('loc', 'iloc') são necessários em frente aoscolchetes. Ao usa-los, a parte antes da vírgula são as linhas desejadas (neste caso, aquelas aonde a idade está acima de 30) e a parte após a círgula são as colunas que você deseja selecionar.

Vamos filtrar mais especificamente agora. Vamos retornar a linha 10 a 25 e das colunas 3 até a 5.

~~~
titanic.iloc[9:25, 2:5]
~~~

Novamente, um subconjunto linhas e colunas feito de uma só vez, apenas usar colchetes não é mais suficiente. Quando estiver especificamente interessado em determinadas linhas e/ou colunas com base em sua posição na tabela, use o operador <code>iloc</code> em frente aos colchetes.

A principal diferença entre o <code>loc[]</code> e o <code>iloc[]</code> está na forma de montar a busca. 

Ao usar o <code>loc[]</code> espera-se o rótulo do dado(nome). Já no <code>iloc[]</code> é a posição da linha ou coluna (índice).

Ao selecionar linhas e/ou colunas específicas, usando por exemplo o <code>iloc[]</code>, novos valores podem ser atribuídos. Olha neste exemplo, aonde iremos selecionar as três primeiras linhas e vamos atribuir um nome a coluna 3('name').

~~~
titanic.iloc[0:3, 3] = 'Blue'
titanic.head()
~~~

Entendeu o código acima? Lembre que os índices do pandas iniciam em '0'.

## Criando gráficos no Pandas

#### Seria possível plotar gráficos no Pandas? Fica por aí que vamos fazer isto e muito mais nesta aula ❗

Vamos usar um dataset público do Pandas Dev.
https://raw.githubusercontent.com/pandas-dev/pandas/main/doc/data/air_quality_no2.csv

Se não conseguir baixar o dataset, copie os dados e salve em um arquivo com extensão csv.

Para plotar gráficos, vamos importar uma biblioteca muito massa e muito utilizada no mercado. O Matpotlib!

~~~
import pandas as pd
~~~

~~~
import matplotlib.pyplot as plt
~~~

Para esta aula vamos utilizar dados de qualidade do ar, disponibilizados pela openaq. O conjunto de dados fornece valores para as estações de medição FR04014, BETR801 e London Westminster em respectivamente Paris, Antuérpia e Londres.

~~~
air_quality = pd.read_csv("air_quality_no2.csv", index_col=0, parse_dates=True)
air_quality.head()
~~~

❗O uso dos parâmetros da função para definir a primeira (0) coluna como índice e converter as datas na coluna para objetos Timestamp.

Criando um gráfico rápido

~~~
air_quality.plot()
~~~

Muito fácil, né? 

A partir de um Dataframe, o Pandas cria por padrão um gráfico de linha para cada uma das colunas com dados numéricos.

Vamos plotar o gráfico apenas com os dados de Paris.

~~~
air_quality["station_paris"].plot()
~~~

Para traçar uma coluna específica, use o método de seleção das aulas anteriores em combinação com o método plot(). 

Vamos comparar visualmente os valores medidos em Londres vs Paris.

~~~
air_quality.plot.scatter(x="station_london", y="station_paris", alpha=0.5)
~~~

Além do plot padrão ao usar a função, uma série de alternativas estão disponíveis para plotar dados. Vamos rodar um laço for para obter uma visão geral dos métodos disponíveis.

~~~
[
    method_name
    for method_name in dir(air_quality.plot)
    if not method_name.startswith("_")
]
~~~

Uma das opções é DataFrame.plot.box(), que se refere a um boxplot. O método é aplicável nos dados do exemplo da qualidade do ar:

~~~
air_quality.plot.box()
~~~

Você já ouviu falar de Outliers? Sugiro que faça uma pesquisa sobre o assunto. A ferramento de boxplot é excelente na identificação de Outliers.

E agora vamos separar cada uma das colunas em um subplot.

~~~
axs = air_quality.plot.area(figsize=(12, 4), subplots=True)
~~~

Personalizar, estender ou salvar o resultado.

~~~
fig, axs = plt.subplots(figsize=(12, 4))        # Metodo que define e salva as medidas
air_quality.plot.area(ax=axs)                   # Plotar o gráfico usando a medida salva anteriormente
axs.set_ylabel("NO$_2$ concentration")          #Customizando o eixo Y 
fig.savefig("no2_concentrations.png")           # Salvando o gráfico
~~~

E aqui chegamos ao fim da aula! Espero que tenha gostado e fica o convite para pesquisar e aprofundar mais sobre tudo o que vimos até agora! 
Até logo.
