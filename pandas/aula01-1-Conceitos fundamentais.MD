# # Aula 16 - [AULA] Introdução ao Pandas - Parte 1

## Conteúdos

1. Conceitos fundamentais

2. Começando com o Pandas

3. Análise dos dados

4. Filtrando e tratando os dados 

## Conceitos fundamentais

Biblioteca mais utilizada para análise e manipulação de dados. 

Documentação oficial: https://pandas.pydata.org/pandas-docs/stable/index.html#


O dia a a dia de um profissional da área de dados consiste em coletar informações, armazenar, manipular e analisar os dados. E como veremos no decorrer da aula, esta bibliotea é perfeita para estes trabalhos.

Principais características e funcionalidades da biblioteca Pandas:

* Biblioteca usada para manipar e analisar dados;
* Realizar limpeza, filtragem e agregação de dados;
* Usando o pandas podemos ler dados de diferentes formatos de arquivos;
* Pandas é de fácil aprendizado;
* O Pandas possui uma extensa comunidade ativa;
* Os principais conceitos são: DataFrames e Series.

As duas estruturas primárias de dados de pandas, Series (1-dimensional) e DataFrame (bidimensionais), lidam com a grande maioria dos casos típicos de uso em finanças, estatísticas, ciências sociais e muitas áreas de engenharia

<h2> DataFrames </h2>
<img src="./img/DataFrame.png" width="780">

<h2> Series </h2>
<img src="./img/Series.png" width="780">

Aqui estão apenas algumas das coisas que pandas fazem bem:

* Fácil manuseio de dados perdidos (representados como NaN) em ponto flutuante, bem como dados de pontos não flutuantes;
* Mutabilidade de tamanho: colunas podem ser inseridas e excluídas do DataFrame, sem modificar os dados orgiginais;
* Ordenação automático e explícito de dados: os objetos podem ser explicitamente ordenados em um conjunto de rótulos;
* Grupo poderoso e flexível por funcionalidade para para agregar e transformar dados;
* Facilite a conversão de dados irregulares e indexados de forma diferente em outras estruturas de dados Python e NumPy em objetos DataFrame;
* Remodelagem flexível do conjuntos de dados;
* Ferramentas robustas de IO para carregar dados de arquivos planos (CSV e delimitados), arquivos Excel, bancos de dados e salvar / carregar dados do formato HDF5 ultrarrápido.

Muitos desses princípios estão aqui para abordar as deficiências frequentemente experimentadas usando outras línguas / ambientes de pesquisa científica. Para os cientistas de dados, trabalhar com dados é tipicamente dividido em múltiplas etapas: obtenção e limpeza de dados, analisando/modelando-os, em seguida, organizando os resultados da análise em um formulário adequado para plotagem ou exibição tabular. O pandas é a ferramenta ideal para todas essas tarefas.

Um DataFrame é o nome da estrutura que o Pandas dá uma tabela. Se você já viu uma tabela do Excel ou de bancos de dados, você sabe o que é um Dataframe. Sua composição básica são linhas e colunas.

As colunas são interpretadas no Pandas como Series. Que nada mais são do que estruturas muito similares a listas.

Podemos pensar nos DataFrames como um arquivo xls, uma planilha do Excel, ou até mesmo uma tabela de um banco de dados, Essa estrutura de dados bidimensional é composta por três elementos principais: linhas, colunas e índices.

:exclamation: Nota: Nos DataFrames, temos índices nas linhas e também nas colunas.

Cada uma das colunas de um DataFrame é uma série.
Tanto as Series quanto os DataFrames possuem funções específicas! A boa notícia é que veremos muitas delas hoje :wink:

## Começando com o Pandas

Para começar a usar o Pandas, primeiro precisamos importar sua bilioteca no Python.

~~~
import pandas as pd
~~~

Para carregar o pacote pandas e começar a trabalhar com ele, importe o pacote. A comunidade concordou que o alias dos pandas é pd. Na prática padrão para toda a documentação dos pandas irá encontrar este alias.

Vamos armazenar os dados dos passageiros do Titanic. Para um número de passageiros, eu sei o nome (personagens), idade (inteiros) e dados de sexo (masculino/feminino).

~~~
df = pd.DataFrame(
    {
        "Name": [
            "Braund, Mr. Owen Harris",
            "Allen, Mr. William Henry",
            "Bonnell, Miss. Elizabeth",
        ],
        "Age": [22, 35, 58],
        "Sex": ["male", "male", "female"],
    }
)
~~~

Podemos armazenar manualmente dados em uma tabela, criando um. Ao usar um dicionário Python de listas, as chaves do dicionário serão usadas como cabeçalhos de coluna e os valores em cada lista como valor nas colunas do DataFrame.

Um DataFrame é uma estrutura de dados bidimensional que pode armazenar dados de diferentes tipos (incluindo caracteres, inteiros, valores de pontos flutuantes, dados categóricos e muito mais) em colunas. É semelhante a uma planilha, uma tabela SQL ou a em R.data.frame.

A tabela tem 3 colunas, cada uma delas com um rótulo de coluna. Os rótulos da coluna são, respectivamente: Name, Age, Sex.

No software de planilha, a representação da tabela de nossos dados seria muito semelhante:

<img src="./img/01_table_spreadsheet.png" align="middle">

### Trabalhando com subconjuntos

E se quisermos trabalhar com os dados da coluna Age

~~~
df["Age"]
~~~

Ao selecionar uma única coluna de um DataFrame pandas, o resultado é uma série pandas. Para selecionar a coluna, use o rótulo da coluna entre os colchetes. 

## Análise dos dados

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
 
## Filtrando e tratando os dados

Vamos avançar os estudos?

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

