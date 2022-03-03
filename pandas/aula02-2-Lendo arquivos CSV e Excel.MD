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
