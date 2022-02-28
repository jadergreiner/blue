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
