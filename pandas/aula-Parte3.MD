# Aula 20 - \[AULA] Introdução ao Pandas - Parte 3

## Conteúdos

* Criar novas colunas a partir de colunas existentes
* Renomar colunas
* Calculando estatísticas


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


