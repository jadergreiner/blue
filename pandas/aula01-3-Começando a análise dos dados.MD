# Começando a fazer análise de dados

Quero saber a idade máxima dos passageiros.

Podemos fazer isso na seleção da coluna aplicando um max

~~~
df["age"].max()
~~~

Interessado em algumas estatísticas básicas dos dados numéricos da minha tabela de dados

~~~
df.describe()
~~~

O método describe() fornece uma visão geral rápida dos dados numéricos. Como algumas colunas são dados textuais, estes são por padrão não levados em conta pelo método describe().

Este é apenas um ponto de partida. Semelhante ao software de planilha, os pandas representam dados como uma tabela com colunas e linhas. Além da representação, também as manipulações de dados e cálculos que você faria em software de planilha são suportados por pandas. 

Vamos adicionar novos dados ao nosso Dataframe?

~~~
df.append(
      pd.DataFrame(
          {
              "Name" : ["McCarthy, Mr. Timothy J",
                        "Heikkinen, Miss. Laina"
              ],
              "Age" : [54,26],
              "Sex" : ["male", "female"]
        }
    )
~~~

Vamos visualizar nosso Dataframe? 
~~~
df
~~~

Cadê nossas informações? 

Acontece que nossos função criou o objeto em "memória". Não salvamos dentro de um Dataframe. Neste caso, vamos salvar os dados dentro do mesmo Dataframe.
O novo código ficará assim:

~~~
df = df.append(
      pd.DataFrame(
          {
              "Name" : ["McCarthy, Mr. Timothy J",
                        "Heikkinen, Miss. Laina"
              ],
              "Age" : [54,26],
              "Sex" : ["male", "female"]
        }
    )
  )
  ~~~
  
  Visualizando os dados novamente, agora sim estamos com os dados completos. 
  
  Mas se você prestar atenção, olha como ficou nosso índice.
  
  Existem várias formas de organizar os índices, vale procurar um pouco na documentação. Usaremos o método de resetar.
  
  ~~~
  df = df.reset_index()
  ~~~
  
  Seja curioso! Navegue pela documentação a aprenda mais. :point_down:
  
  https://pandas.pydata.org/pandas-docs/stable/reference/api/pandas.DataFrame.reset_index.html#pandas.DataFrame.reset_index
 

