# # Aula 16 - [AULA] SQL - Parte 1

## Conteúdos

1. Conceitos iniciais de bancos de dados

2. Bancos relacionais e não relacionais

3. Modelagem de dados

4. Criando nosso banco e executando os primeiros comandos

## Conceitos iniciais de bancos de dados

Bem-vindo ao módulo 4. Parabéns pela jornada. 

Nesta semana vamos tratar de um tema muito interessante. O nosso querido "SQL". Será uma semana muito legal, cheia de desafios e aprendizado.

Os exemplos utilizados foram realizados e capturados no MySQL Workbench. Segue o link para download (https://dev.mysql.com/downloads/mysql/).

Procure pelo MySQL Workbench na versão Community.

Na instalação, recomendamos selecionar o tipo Custom, para selecionarmos os produtos que vamos instalar. 


<img src="./imagens/Install-01.png">

:exclamation:Você irá encontrar nos documentos complementares orientações de instalação.

Quando falamos de Banco de dados, precisamos voltar aos registros físicos de bibliotecas. Pense nos negócios em geral, registros policiais, fichas de pacientes, registros de estoque e também entradas e saídas de pessoas e materiais em um prédio ou pavilhão. Esse resgate é importante, pois foi lá que tudo começou.

Estes registros eram individualizados, mantinha-se um histórico muito longo de informações e também uma metodologia de indexação e recuperação da informação quando se precisava dela. Mas não vamos nos alongar muito, mas fica o convite para quem quiser pesquisar mais sobre o assunto. 

Os Bancos de dados como conhecemos hoje, o modelo relacional, é uma teoria matemática desenvolvida por Edgar Frank Codd. Ele desceve como as bases de dados devem funcionar. E veja bem, estamos falando de de um período entre 1960-1970. 

<img src = "https://www.ecured.cu/images/4/4a/EdgarFCood.jpeg">

Mas me conta aí, você sabia disso :bowtie: ? 

Caso queira conhecer um pouco mais sobre o criado do modelo relacional, pode começar por aqui: :arrow_right: <a href="https://pt.wikipedia.org/wiki/Edgar_Frank_Codd" target="_blank"> Edgar Frank Codd </a>

Bancos de dados ou bases de dados são conjuntos de arquivos relacionados entre si com registros sobre pessoas, lugares ou coisas. São coleções organizadas de dados que se relacionam de forma a criar algum sentido (informação). São de vital importância para empresas e se tornaram a principal peça dos sistemas de informação e segurança.

<img src = "https://www.homehost.com.br/blog/wp-content/uploads/2019/02/o-que-e-mysql1.jpg">

:pushpin: Agora um ponto de reflexão para debatermos em aula! 

Quando falamos em Dados e informações. Estou falando a mesma coisa❓

Os bancos de dados são operados pelos Sistemas Gerenciadores de Bancos de Dados (SGBD), que surgiram na década de 1970. Outro tipo notável é o SGBD Orientado a Objetos, implementado em bancos dados com estruturas complexas ou aplicações que mudam constantemente.

Por volta de 1976, o Dr. Peter Chen propõe o modelo Entidade-Relacionamento (ER) para objetos de bancos de dados, dando uma nova e importante percepção dos conceitos de modelos de dados. 

![image](https://user-images.githubusercontent.com/87602063/166435298-133f5f0b-3073-4aea-a889-907064d64185.png)


Na metodo dos anos 80, a linguagem de SQL se torna um padrão mundial :grin:.

Pela metade dos anos 90 começa a explosão das vendas na Internet (sim, houve um tempo que não existia a Internet :smile:).

Processos de transação de tempo real (OLTP - On-Line Transaction Process) e processos analíticos em tempo real (OLAP - On-Line Analitical Process) atigem maturidade através de muitos negócios utilizando pontos de venda.

<img src = "https://miro.medium.com/max/3144/1*kDxyqz9MqDuFb5AyYu53AA.png">

Em resumo, podemos dizer que OLTP armazena dados transacionais. Ou seja, as operações diárias do negócio. Geralmente, o sistema da empresa, dados como a venda dos produtos, a ficha técnica de um produto, uma transação financeira. 

Já o OLAP tende a consolidar dados históricos para demonstração e visualizações analíticas. 

Você pode ficar na dúvida do melhor modelo, isso é bem comum viu. Mas deixa te contar, não existe um modelo melhor. Eles servem para objetivos diferentes, então depende do problema a ser resolvido, um ou outro será utilizado. 

Parece muita coisa né, mas eu tenho certeza que no ao final do módulo, esta sopa de letrinhas ficará muito mais clara para você.

Recapitulando para você não se perder, ok? :bulb:

* Partimos de fichas e registros individuais até a organização em arquivos.
* Começamos a estruturar e indexar estes dados.
* Seguimos com o modelo relacional, lembra do Edgar Codd, né?
* Chegamos no modelo Entidade-Relacionamento do Dr. Peter Chen!
* Victory 💪! SQL se torna um padrão mundial.
* Até aqui, nossos dados estão de certa forma "isolados" dentro nosso ambiente corporativo.

Depois vem o :boom: boom da internet. Os dados começam a circular e precisamos repensar o modo de armazenar, transitar e dar segurança a estes dados.

Os dados começam a ser cruzados. Do ponto de vista de um negócio, tenho vendas presenciais e OnLine. Posso também ter várias lojas, como consolidar as vendas e o estoque de todas elas? 

Além disso, meus clientes estão indo pra internet. Por que não sugerir produtos com base em suas preferências? Vai dizer que nunca pensou sobre isso? Você pesquisa sobre algo na internet e logo após, como num passe de mágica, chuva de ofertas sobre o produto que você pesquisou!

A questão é que isso gera um volume incalculável de dados. Se antes eu tinha um "controle" do meu volume de dados e que tipo de informação seria armazenada no meu Banco de dados, quanto incluímos a "Internet", as coisas mudarem completamente.

Quais as tendências :confused: ❓

Sistemas gigantescos (na casa dos Terabytes) já são realidade e novos recursos são necessários para manipulação e análise dos dados.

Data mining(mineraçaõ de dados), Data WareHouse, Data Marts, Data Lake são técnicas atualmente utilizados. Sistemas de compras inteligentes e recomendações baseadas em dados. Isso sem falar nos Chatbots e Metaverso.

Ufa! Bastante conteúdo teórico. Mas é importante refletir e pensar sobre a evolução e de que como chegamos até aqui. 

## Bancos relacionais e não relacionais

Eu tenho certeza que você já ouviu falar de Bancos relacionaios e bancos não relacionais. Esse assunto esta cada vez mais em foco e entender claramente a diferença entre eles vai te diferenciar como um profissional de dados.

**O que é um banco relacional** ❓

Podemos considerar como banco relacional o armazenamento e a estrutura de qualquer sistema. Seja ele de gestão financeira, cadastro de clientes, cadastro de funcionários, cadasrto de cursos ou qualquer outra aplicação que possa pensar. O importante é compreender que neste mundo informatizado eles são fundamentais para o funcionamento dos programas. 

A depender de sua arquitetura e finalidade, os dados armazenados podem ser acessados e compartilhados entre outros bancos de dados.

O modelo relacional armazena dados estruturados. Cada um dos campos é planejado antes, seja em relação ao nome da coluna (idade, por exemplo), o tipo de dados (numérico) e se o campo é obrigatório ou pode ficar em branco (nulo).

Em um banco de dados relacional, caad linha na tabela é um registro com uma ID exclusiva chamada chave. As colunas da tabela contêm atributos dos dados e cada registro tem um único valor para cada um destes atributos, facilitando o estabelecimento das relações entre os pontos de dados.

Por exemplo, uma tabela que armazene os cursos oferecidos por nossa escola. Cada linha representa um curso e cada um deles deve receber uma chave única. Algo semelhante a estrutura abaixo poderia ser a tabela de cursos.

<img src="./imagens/diagramaCursos.png">

Esta primeira tabela tem os dados do curso, de forma que cada registro incluir o nome do curso, o professor e se o curso está ativo ou não. Cada um dos atributos recebe uma coluna específica e o banco de dados atribui uma ID única (uma chave) a cada linha.

Uma segunda tabela, nosso cadastro de professores contém o nome, dados de contato e um ID exclusivo.

