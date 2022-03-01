# Vamos avançar os estudos?

Vamos filtrar os dados, criar novos Dataframes e retornar dados estatísticos.

Recordando nosso Dataframe

~~~
df
~~~

E se quisermos retornar apenas os passageiros do sexo feminino?

Que tal iniciarmos criando um filtro?


~~~
filtro = df['Sex'] == 'female'
~~~

Qual o resultado? Vamos analisar :mag:

~~~
filtro
~~~

Conseguiu compreender! Se tiver com dúvidas, não deixe passar. Será importante compreender estes conceitos para a sequência das aulas.

Primeiro, criamos um novo Série Pandas, chamado "filtro".
Uma coluna com "True" ou "False" e o índice. Acredito que tenha compreendido, mas se ainda estiver confuso, fica tranquilo que vou te ajudar a entender :grin:

Observa os índices da Série Filtro e compare com os índices do Dataframe. Compare aonde está "True" no Series com o df. 

E aí? Agora melhorou? Faz o exercício, muda o filtro para "male" e refaça os passos.

Bom. E como é que usaremos este filtro? Agora vem a parte fácil :smile:

Execute o df com o filtro

~~~
df_filtrado = df[filtro]
df_filtrado
~~~

Conhecendo um pouco mais sobre outros métodos.

Quantos registros tem em nosso Dataframe?

~~~
df.count()
~~~

Veja que ele retorna a contagem em cada uma das Séries. E se quisermos uma contagem geral? 
Podemos aplicar um filtro no index.

~~~
df["index"].count()
~~~

Agora vamos criar novos Dataframes a partir do principal? Com algumas estatísticas!

Primeiro filtro do sexo feminino.
~~~
filtro = df['Sex'] == 'female'
~~~

Agora vamos criar um Dataframa armazendo os dados de sexo feminino

~~~
df_feminimo = df[filtro]
~~~

Qual a idade máxima, mínima e média do sexo feminino?

O Pandas já tem os métodos prontos pra gente. 

Idade máxima
~~~
df_feminimo["Age"].max()
~~~

Idade mínima
~~~
df_feminimo["Age"].min()
~~~

Idade média
~~~
df_feminimo["Age"].mean()
~~~

Vamos repetir para os dados do sexo masculino? Dica, vamos iniciar alterando o filtro.

~~~
filtro = df['Sex'] == 'male'
~~~

Criando nosso Dataframa com os dados de sexo masculino

~~~
df_masculino = df[filtro]
~~~

Idade máxima
~~~
df_masculino["Age"].max()
~~~

Idade mínima
~~~
df_masculino["Age"].min()
~~~

Idade média
~~~
df_masculino["Age"].mean()
~~~

E aí! Conseguiu acompanhar? 
Fique de olho na ordem dos filtros, usamos o mesmo nome para criar os dois Dataframes.

Terminamos por aqui nossa primeira aula! Está gostando? Pois é só o começo desta poderosa ferramenta Pandas.
