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
