# # Aula ?? - [NoSQL] SQL - Parte 1

## Conteúdos

1. Bancos NoSQL: Diferenças dos bancos relacionais

2. Conceitos de banco de documentos

3. Coleções e campos

4. MongoDB

5. MongoDB: Como funciona

6. MongoDB: Select e filtros
 

## Bancos NoSQL: Diferenças dos bancos relacionais

E vamos pra nossa aula de NoSQL! Você já conhecia este termo?

Quando falamos de **NoSQL**, o que lhe vêm a cabeça? Diferente do que muita gente pensa a primeira vez que vê o termo, NoSQL não quer dizer "NO SQL", ou então, "sem SQL". 

Muito pelo contrátio, o termo **NoSQL** ao ler a tratar sobre bancos de dados não relacionais significa **"Not only SQL"**, "não apenas SQL", trata-se de um termo bastante flexível. Inclusive, alguns bancos de dados não relacionais dão suporte a uma versão do SQL (Structured Query Language) adaptada para documentos em vez de tabelas, o que facilita a operação por parte dos profissionais que conhecem o SQL.

Enquanto os bancos relacionais armazenam apenas dados estruturados, os bancos NoSQL proporcionam armazenamento de dados semi-estruturados ou não estruturados. Arquivos JSON, XML, são exemplos de arquivos armazenados em estruturas NoSQL.

Os bancos de dados **NoSQL** são amplamente usados em aplicativos da web em tempo real e big data, porque suas principais vantagens são alta escalabilidade e alta disponibilidade.

Os bancos de dados **NoSQL** também são a escolha preferida dos desenvolvedores, pois eles naturalmente aceitam um paradigma de desenvolvimento ágil, adaptando-se rapidamente aos novos requisitos. Como vimos na primeira aula deste módulo, um banco relacional necessita de modelagem dos dados, isso significa estabelecer previamente os atributos e qual o tipo de dado será aceito. Diferente de um banco não relacional, que rapidamente poderá migrar para outros atrinutos.

Os bancos de dados NoSQL permitem que os dados sejam armazenados de maneiras mais intuitivas e fáceis de entender, ou mais próximas da maneira como os dados são usados pelos aplicativos - com menos transformações necessárias ao armazenar ou recuperar usando APIs no estilo NoSQL. Além disso, os bancos de dados NoSQL podem aproveitar ao máximo a nuvem para oferecer tempo de inatividade zero.

Para entender os bancos de dados NoSQL, é importante saber qual é a diferença entre RDBMS e tipos não relacionais de bancos de dados.

Os dados em um RDBMS são armazenados em objetos de banco de dados que são chamados de tabelas. Uma tabela é uma coleção de entradas de dados relacionadas e consiste em colunas e linhas. Esses bancos de dados requerem a definição do esquema com antecedência, ou seja, todas as colunas e seus tipos de dados associados devem ser conhecidos de antemão para que os aplicativos possam gravar dados no banco de dados. Eles também armazenam informações vinculando várias tabelas por meio do uso de chaves, criando assim um relacionamento entre várias tabelas. No caso mais simples, uma chave é usada para recuperar uma linha específica para que ela possa ser examinada ou modificada.

Por outro lado, em bancos de dados NoSQL, os dados podem ser armazenados sem definir o esquema com antecedência—o que significa que você tem a capacidade de se mover e iterar rapidamente, definindo o modelo de dados à medida que avança. Isso pode ser adequado para requisitos específicos de negócios, seja baseado em gráficos, orientado a colunas, orientado a documentos ou como um armazenamento de valor-chave.

Até muito recentemente, os bancos de dados relacionais eram os modelos mais usados. Eles ainda são extremamente onipresentes em muitas empresas; no entanto, a variedade, velocidade e volume de dados que estão sendo acessados hoje às vezes requerem um banco de dados muito diferente para complementar o banco de dados relacional. Isso desencadeou a adoção em algumas áreas dos bancos de dados NoSQL—também chamados de "bancos de dados não relacionais". 

## Conceitos de banco de documentos

Como estudamos na aula 1, está bem difundido na comunidade quatro tipos de bancos não relacionais. Relembrando:
- Orientado a chave valor, orientado a coluna, orientado a Grafos e orientado a documentos.

Nesta aula, vamos aprofundar os conhecimentos no conceito de bancos orientados a documentos. O banco de dados não relacional mais conhecido e difundido na comunidade é o MongoDB. Justamente por ser orientado a documentos é que vamos utiliza-lo em nossa aula daqui para frente.

<img src = "https://wallpapercave.com/wp/wp8725088.jpg">
