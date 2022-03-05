# Criando subconjuntos a partir do Dataframe original

:exclamation: Seguiremos analisando o Dataset do Titanic

### Como selecionar colunas específicas de um Dataframe :question: 

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

### É possível filtrar os dados de uma coluna específica

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

### Como selecionar linhas e colunas específicas ❓

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
