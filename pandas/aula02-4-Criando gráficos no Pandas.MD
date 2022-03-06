### Seria possível plotar gráficos no Pandas? Fica por aí que vamos fazer isto e muito mais nesta aula ❗

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






