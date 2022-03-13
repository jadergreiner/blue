# Aula 20 - \[AULA] Introdução ao Pandas - Parte 3

## Conteúdos

* Criar novas colunas a partir de colunas existentes
* Renomar colunas
* Calculando estatísticas
* Agregar estatística por categoria (group by)
* Contar registros por categoria
* Reordenando o layout das tabelas
* Criando novos dataframes com filtro de dados


## Criar novas colunas a partir de colunas existentes

Importando a biblioteca pandas

~~~
import pandas as pd
~~~

Usaremos o mesmo dataset da última aula, sobre a qualidade do ar.

~~~
air_quality = pd.read_csv("air_quality_no2.csv", index_col=0, parse_dates=True)
air_quality.head()
~~~

Vamos incluir a informação da concentração de ar em mg/m em Londres❗

Se assumirmos temperatura de 25 graus Celsius e pressão de 1013 hPa, o fator de conversão é de 1.882

~~~
air_quality["london_mg_per_cubic"] = air_quality["station_london"] * 1.882
air_quality.head()
~~~

:pushpin: Para criar uma nova coluna, use os colchetes com o nome da nova coluna antes da atribuição ("=").

O cálculo dos valores utiliza **element_wise**. Isso significa que todos os valores da coluna dada são multiplicados pelo valor 1.882 de uma só vez. Você não precisa usar um loop para iterar cada uma das linhas!

Agora vamos analisar a proportação dos valores entre Paris e Antwerp, salvando o resultado em uma nova coluna.

~~~
air_quality["ratio_paris_antwerp"] = (
    air_quality["station_paris"] / air_quality["station_antwerp"]
)

air_quality.head()
~~~

Novamente usamos o **element_wise**, calculando a divisão sobre duas colunas.

Imagino que já tenha percebido o potencial desta biblioteca! Podemos usar os operadores matemáticos (+, -, *, /) ou operadores lógicos (<, >, =, ...) junto com expressões condicionais. Fica o convite para brincar um pouco 😉

Como um material complementar, se precisar de algo mais avançado, pode usar o arbitrary Python com <a href="https://pandas.pydata.org/pandas-docs/stable/reference/api/pandas.DataFrame.apply.html#pandas.DataFrame.apply" target="_blank"><code>apply()</code> </a>.

## Renomar colunas

Vamos renomar as colunas com os identificadores de estação correspondentes utilizados pelo openAQ

~~~
air_quality_renamed = air_quality.rename(
    columns={
        "station_antwerp": "BETR801",
        "station_paris": "FR04014",
        "station_london": "London Westminster",
    }
)

air_quality_renamed.head()
~~~

A função <code>rename()</code> pode ser usada para renomear nome de linhas ou colunas. Sua sintaxe funciona através de um dicionário(chave-valor), informamos o nome atual na chave o novo nome como valor.

O mapeamento não está restrito apenas a nomes fixos, mas também pode ser uma função. Por exemplo, a conversão dos nomes das colunas em letras minúsculas também pode ser feita usando uma função:

~~~
air_quality_renamed = air_quality_renamed.rename(columns=str.lower)

air_quality_renamed.head()
~~~

:point_right: Material complementar sobre a renomeação de rótulos de coluna ou linha na documentação oficial https://pandas.pydata.org/pandas-docs/stable/user_guide/basics.html#basics-rename

## Calculando estatísticas

Para melhorar nossa didática e compreensão, vamos retomar a análise em nosso dataframe Titanic.


~~~
titanic = pd.read_csv("data/titanic.csv")

titanic.head()
~~~

Qual a idade média dos passageiros ❓

~~~
titanic["Age"].mean()
~~~

Diversas estatísticas estão disponíveis e podem ser aplicadas em colunas com dados numéricos. As operações em geral excluem dados perdidos e operam em linhas por padrão.

Qual a idade média dos passageiros e qual o valor médio das tarifas?

~~~
titanic[["Age", "Fare"]].median()
~~~

📌 Ao aplicar estatística a várias colunas, o resultado retorna um objeto DataFrame.

Podemos calcular estatísticas sumarizadas para várias colunas ao mesmo tempo. Lembra-se do <code>describe()</code> que olhamos nas primriras aulas.

~~~
titanic[["Age", "Fare"]].describe()
~~~

E podemos customizar nossas estatísicas. Ao invés de usar as pré-definidas, podemos agregar combinações específicas usando o método <code>agg()</code>

~~~
titanic.agg(
    {
        "Age": ["min", "max", "median", "skew"],
        "Fare": ["min", "max", "median", "mean"],
    }
)
~~~

Material complementar de estatística descritiva ➡️ https://pandas.pydata.org/pandas-docs/stable/user_guide/basics.html#basics-stats

## Agregar estatística por categoria (group by)

Qual a idade média dos passageiros femininos e masculinos do Tinanic ❓

Sim, eu sei que você já sabe calcular individualizado! Mas quero te apresentar a agregação de resultados do Pandas ❗

~~~
titanic[["Sex", "Age"]].groupby("Sex").mean()
~~~

Como desejamos a idade média de cada gênero, primeiro montamos um subconjunto com estas duas colunas. Após, o método <code>groupby()</code> é aplicado na coluna para fazer um grupo por categoria de forma automática. Não importa o número de categorias, o método vai criar um novo agrupamento cada vez que encontrar um novo rótulo. 


Vamos ver outras formas bem interessantes de olhar os dados agrupados. 
Vamos agrupar os dados antes e depois vamos aplicar uma estatística neles.

~~~
titanic.groupby("Sex").mean()
~~~

Mas se quisermos a média de idade dos passageiros por sexo, podemos filtar com os colchetes após a agregação.

~~~
titanic.groupby("Sex")["Age"].mean()
~~~

Percebeu que o resultado é o mesmo que realizamos antes? Qual a forma correta?

Fica para discussão em aula. Quero ouvir sua opinião!

Um dos pápeis de análise de dados é interpretar os dados. Concorda que não faz muito sentido obter uma média da coluna <code>Pclass[]</code> ❓

A coluna contém dados numéricos, mas na verdade representa 3 categorias (ou fatores) com, respectivamente, os rótulos '1', '2' e '3'. Calcular estatísticas sobre isso não faz muito sentido. Portanto, o pandas fornece um tipo de dados para lidar com esse tipo de dados. 
Dica de material complementar sobre dados categóricos https://pandas.pydata.org/pandas-docs/stable/user_guide/categorical.html#categorical

Agora assim! Qual é o preço médio da passagem para cada uma das combinações de sexo e classe por cabine?

~~~
titanic.groupby(["Sex", "Pclass"])["Fare"].mean()
~~~

Agora fez mais sentido trazer a cabine para a análise. O agrupamento pode ser feito com várias colunas ao mesmo tempo. Informe o nome das colunas como uma lista no <code>groupby()</code> .

## Contar registros por categoria

Qual o número de passageiros em cada uma das classes ❓

~~~
titanic["Pclass"].value_counts()
~~~

O método <code>value_counts()</code> conta o número de registros de cada categoria em uma coluna.

A função é um atalho. Ela faz uma operação de agregação e combina com a contagem do número de registros dentro do grupo

~~~
titanic.groupby("Pclass")["Pclass"].count()
~~~

## Reordenando o layout das tabelas

Vamos classificar os dados do Titanic de acordo com a idade dos passageiros

~~~
titanic.sort_values(by="Age").head()
~~~

Vamos classificar os dados de acordo com a Classe da Cabine e a idade em ordem descrecente

~~~
titanic.sort_values(by=['Pclass', 'Age'], ascending=False).head()
~~~

Para saber mais sobre a ordenação de dados, visite a documentação https://pandas.pydata.org/pandas-docs/stable/user_guide/basics.html#basics-sorting

## Criando novos dataframes com filtro de dados

Voltamos ao dataset de qualidade do ar ❗

Vamos criar um pequeno subconjunto do conjunto de dados de qualidade do ar. Vamos filtar os dados de NO2 e apenas as duas primeiras medições de cada local. O subconjunto de dados será chamado no2_subset


