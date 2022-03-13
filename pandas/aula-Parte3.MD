# Aula 20 - \[AULA] Introdução ao Pandas - Parte 3

## Conteúdos

* Criar novas colunas a partir de colunas existentes
*


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
