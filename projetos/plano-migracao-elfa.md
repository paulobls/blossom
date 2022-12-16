# Metodologia de Migração de Dados em um contexto de Migração de Sistemas Legados

PRINCIPAIS ABREVIATURAS

| Abreviatura | Significado                                |
| ----------- | ------------------------------------------ |
| ROI         | Return Of Investment                       |
| SGBD        | Sistema de Gerenciamento de Banco de Dados |
| SQL         | Structured Query Language                  |
| TIC         | Tecnologia da Informação e Comunicação     |
| XML         | eXtensible Markup Language                 |
| XMI         | XML Metadata Interchange                   |

## 1. Introdução

Segundo Larousse, migrar é mudar ou passar para outra região ou para
outro país. A Vida, no seu laboratório de 3,8 bilhões de anos, consolidou as migrações
como estratégia de sobrevivência. No ecossistema de Tecnologia da Informação e
Comunicação (TIC) aplica-se o conceito com a mesma semântica: mudança. Porém,
com atores e locais diferentes. É usual falar-se, entre outras migrações, em migração de
ambiente computacional, migração de plataforma, migração de arquitetura, migração de
dados. O que essas migrações têm em comum com a definição anterior é que,
geralmente, elas buscam vantagens em novos ambientes. Outra constatação é que não é
fácil migrar, pois exige preparação e esforço, além de nem sempre se conseguir alcançar
bons resultados.
Neste capítulo introdutório, mostra-se o contexto onde este trabalho se insere, a
motivação, os objetivos do trabalho e a estrutura da dissertação.

### 1.1 Contexto

Migração de dados é um tema bastante abrangente, sendo uma necessidade nos
negócios de qualquer empresa. Estima-se que as empresas americanas investem entre 5
e 10 bilhões de dólares anuais em projetos de migração de dados. Empresas
migram dados por diversos motivos. Os principais são: atualização de hardware,
mudança de sistema de gerenciamento de banco de dados (SGBD) e mudança de
sistemas aplicativos. Todos estes tipos de migração envolvem riscos. Maiores ou
menores, mas sempre presentes. O foco deste trabalho está relacionado com o terceiro
motivo apresentado: a migração de dados na mudança de sistemas aplicativos.
As empresas gastam muito dinheiro em sistemas de software, e para que elas
obtenham um retorno desse investimento o software deve ser utilizado por vários anos.
O tempo de duração de sistemas de software é muito variável e muitos sistemas de
grande porte permanecem em uso por mais de 10 anos. Muitos desses antigos sistemas
ainda são fundamentais para as empresas, isto é, as empresas dependem dos serviços
fornecidos pelo software, e qualquer falha desses serviços teria um sério efeito em seu
dia-a-dia. A esses antigos sistemas foi dado o nome de sistemas legados.
Os sistemas legados não são os sistemas que foram originalmente fornecidos.
Fatores internos e externos geram requisitos de software novos ou modificados; assim,
todos os sistemas de software úteis inevitavelmente são modificados quando as
empresas passam por mudanças. Portanto, os sistemas legados incorporam um grande
número de alterações, que foram feitas durante muitos anos por muitas pessoas. É
incomum que qualquer pessoa tenha uma compreensão completa do sistema.
Devido ao grande número de modificações, que geralmente não estão documentadas, e
ao número elevado de pessoas que programaram estas modificações, a complexidade do
software aumenta e com ela o custo de mantê-lo.
Empresas tendem a querer migrar seus sistemas legados para novos ambientes,
que permitem ao sistema de informação uma manutenção mais simples. Porém, a
decisão não é fácil, pois envolve muitos riscos.
Os benefícios da migração para novos ambientes são enormes em longo prazo:
ela oferece mais flexibilidade, um melhor entendimento do sistema, fácil manutenção e
custos reduzidos.

Porém, a migração de dados é uma tarefa tipicamente complexa e trabalhosa nos
ambientes computacionais atuais, dada a miríade de servidores de aplicação, sistemas
operacionais, sistemas de arquivos, equipamentos físicos e redes. Vários são
os desafios impostos pela migração, como o tempo no qual o sistema original ficará
inoperante, a necessidade de adicionar software de migração de dados em servidores, a
possibilidade de perda e corrupção de dados. Ainda o surgimento de erros advindos da
complexidade de ambientes heterogêneos, a possibilidade de atraso no cronograma ou
estouro do orçamento definido para o projeto.
As empresas vêm gastando milhões de dólares migrando dados entre aplicações
que lidam com informação em massa e, ainda com todo esse investimento, novos
sistemas falham em satisfazer as expectativas. Várias pesquisas vêm sendo
conduzidas na tentativa de desenvolver uma maneira segura e barata de guiar a
migração de um sistema legado como um todo [Ben95, BrS93, Dat07, IBM07, NaG92,
Til96, Wu+97a, Wu+97b, Wu+05, Wu+99, Wu+97c].

### 1.2 Motivação

Tradicionalmente recebendo a menor das atenções nos projetos de TIC,
habitualmente colocada no fim do planejamento do projeto, migração de dados pode ser
a diferença entre uma realização bem sucedida e uma oportunidade perdida. Migração
de Dados não é somente mover dados de um lugar para outro. Tem-se
observado que, geralmente, no ciclo de vida de um novo projeto de sistema de software,
pouca atenção, prioridade e planejamento são dispensados aos dados que porventura
necessitem ser migrados. Migrar dados exige olhar
para o passado legado quando, na maioria dos casos, a demanda pressiona para que o
futuro chegue mais depressa.
No atual estado da arte de TIC, é incomum construir-se um novo software
aplicativo sem a necessidade de migrar dados. Esta crescente necessidade torna a
atividade cada vez mais importante para o sucesso do projeto.

### 1.3. Objetivos

O objetivo desta dissertação é integrar algumas das principais estratégias de
migração de dados existentes na literatura com práticas de gerência de projetos para
definir uma metodologia genérica de migração de dados num contexto de migração de
sistemas legados, validando esta metodologia em um caso real de grande porte. Para tal,
propõe-se estudar e avaliar as estratégias disponíveis de migração de dados, os passos
envolvidos, os desafios e os fatores de sucesso de um projeto de migração de dados.
Será também verificada a aderência destas estratégias às boas práticas de gerência de
projetos. O estudo de caso escolhido para validar a metodologia proposta envolve um
grande sistema legado corporativo, com a migração de cento e vinte e nove milhões de
registros, realizado no Projeto E - Fisco da Secretaria da Fazenda do Estado de
Pernambuco. Os resultados obtidos serão analisados para a identificação dos
pontos fortes e fracos, erros cometidos e sugestões de melhoria. Neste trabalho, para
maior clareza, será chamado de sistema fonte o sistema legado e de sistema alvo o novo
sistema a ser implantado, os quais serão usados como exemplo para o estudo de caso.

### 1.4. Estrutura da dissertação

Este trabalho é composto de cinco capítulos, incluindo este. No Capítulo 2, serão
abordadas metodologias de migração de sistemas legados, o processo de migração de
dados, estratégias de migração de dados, os passos envolvidos no processo, além dos
principais desafios e fatores que levam um projeto de migração de dados ao sucesso.
Serão feitas algumas considerações em relação a tais estratégias de migração de dados.
Também serão abordadas as atividades de Gerência de Projetos. No Capítulo 3,
baseando-se nos conceitos mostrados no Capítulo 2, será apresentada a metodologia de
migração de dados proposta. No Capítulo 4, a metodologia definida no Capítulo 3 será
aplicada ao estudo de caso. Serão mostrados os resultados obtidos. No Capítulo 5 estão
as considerações finais deste trabalho, contendo uma avaliação da metodologia
desenvolvida, destacando-se o que funcionou, o que poderia ter sido melhor e são
apresentadas sugestões de trabalhos futuros.

## 2. Conceitos Básicos

Neste capítulo é feita uma revisão dos principais conceitos relativos a sistemas
legados e migração desses sistemas, bem como tópicos relevantes da gerência de
projetos. Assim, são levantadas as características das principais metodologias de
migração de sistemas legados, das principais estratégias de migração de dados, além de
tópicos importantes da gerência de projetos aplicáveis a esse contexto. Todos estes
assuntos são fundamentais como referenciais conceituais para a construção de uma
metodologia de migração de dados em um contexto de migração de sistema legado, que
é objetivo desta dissertação. Os termos origem, legado e fonte serão usados como
sinônimos quando se referirem ao ambiente ou sistema legado.

### 2.1. Sistemas Legados

Atualmente os sistemas de informação legados são um problema dominante em
várias organizações e grandes indústrias. Os maiores problemas enfrentados são a
manutenção dos sistemas para que eles possam continuar atendendo às necessidades dos
negócios e a dificuldade em deixá-los operacionais, devido principalmente à defasagem
tecnológica. Apesar destas características, a tecnologia não deve ser o fator que leva
qualquer organização a reestruturar o seu negócio. Os requisitos dos negócios é que
devem levar a uma mudança na tecnologia e nos sistemas de informação.
Segundo Brodie et al., um sistema de informação legado é qualquer
sistema de informação que resiste a mudanças e evoluções em grande parte devido às
dificuldades em manutenção. Desta forma, não somente sistemas com milhares ou
milhões de linhas de código, escritos em COBOL, mas também sistemas mais
modernos, escritos em C, podem ser exemplos de sistemas
legados. Outra característica dos sistemas legados é que eles costumam consumir grande
parte dos recursos financeiros do total aplicado em sistemas de informação de uma
organização, impedindo, muitas vezes, a sua migração para que possam atender às
necessidades dos negócios.
O desenvolvimento de sistemas centralizados, baseados em mainframes,
modelos de desenvolvimento totalmente dependente do hardware e software utilizados,
interfaces de usuário baseadas em terminais não gráficos e processamento batch,
predominante nas últimas décadas, levou várias empresas a uma verdadeira crise, pois
suas aplicações não conseguem evoluir com a mesma rapidez que os negócios exigem.
Além disso, elas são totalmente dependentes deste tipo de sistemas, o que os tornam
sistemas imprescindíveis para estas empresas.
As características dos sistemas legados são:
São grandes, com milhões de linhas de código;
São velhos, mais de dez anos, e passaram por várias reestruturações;
Usam linguagens legadas como COBOL;
Foram construídos sobre um sistema de banco de dados legado, por exemplo,
IMS e VSAM
;
São autônomos, isto é, não têm interface com nenhuma outra aplicação;
Apresentam baixo desempenho; e
Possuem pouca ou nenhuma documentação e geralmente estão desatualizadas.
4

Os sistemas de informações legados tradicionais são aqueles baseados em
mainframe, porém, o paradigma de sistemas legados pode ser aplicado a qualquer
plataforma. Características como aumento dos custos de manutenção e aumento
do intervalo de tempo em incorporar novas funcionalidades podem representar um
sistema de informação legado em formação.

### 2.2. Migração de Sistemas Legados

Apesar de este tópico estar sendo pesquisado há anos e ser um assunto muito
discutido e exposto, além de existirem várias ferramentas que se propõem a traduzir
estes sistemas, pouco tem sido feito neste sentido pelas grandes organizações. Quando
existe este esforço, o sistema é totalmente refeito, como exemplificado no estudo de
caso desta dissertação. Para que o processo de migração dos sistemas legados para uma
nova tecnologia tenha sucesso, é necessário ter um plano ou estratégia para esta
migração, uma vez que os sistemas legados não podem parar, isto é, continuam em
evolução, enquanto a migração está acontecendo.

#### 2.2.1. Metodologias de Migração de Sistemas Legados

O sucesso de um projeto de migração de sistemas legados depende do
desenvolvimento de uma metodologia que seja detalhada e bem definida, já que este
tipo de projeto é de enorme escala, complexidade e muito suscetível a falhas.
Atualmente, duas metodologias são mais aceitas pela comunidade: Chicken Little e
Butterfly.

##### 2.2.1.1. Chicken Little

Na metodologia Chicken Little, Brodie e Stonebraker propõem
uma estratégia de migração composta de onze etapas genéricas que utilizam complexos
gateways. Um gateway pode ser definido como qualquer módulo de software
introduzido entre componentes de software com o objetivo de mediá-los.
Esta metodologia deixa a cargo da equipe escolher qual método de migração utilizar: o
método Forward ou Database First ou o método Reverse ou Database Last.
O método de migração Forward ou Database First envolve a migração inicial
dos dados legados para uma nova base e, em seguida, a aplicação e as interfaces são
migradas incrementalmente. Um forward gateway é utilizado para que a
aplicação original acesse os dados na plataforma destino.
O método de migração Reverse ou Database Last faz com que a aplicação seja
migrada gradualmente para a plataforma destino, enquanto que a base de dados
permanece na plataforma original. A migração dos dados é a última etapa
deste processo. Um reverse gateway é utilizado para que a aplicação destino acesse os
dados da plataforma original.
Nesses dois métodos, os sistemas de origem e destino operam paralelamente
durante o processo da migração, o que adiciona complexidade. Os próprios
autores reconhecem que manter a consistência dos dados entre sistemas de informação
heterogêneos representa um problema técnico complexo e que ainda não foi proposta
uma solução geral. Os onze passos que compõem a metodologia Chicken
Little são:
5

1. Analisar o sistema legado;
1. Decompor a estrutura do sistema legado;
1. Projetar a interface destino;
1. Projetar a aplicação destino;
1. Projetar a base de dados destino;
1. Instalar o ambiente destino;
1. Criar e instalar os gateways necessários;
1. Migrar as bases legadas;
1. Migrar as aplicações legadas;
1. Migrar as interfaces legadas; e
1. Mudar para o sistema destino.
   Note-se que o presente trabalho envolve principalmente as fases 5 e 8. Um dos
   aspectos destacados é que estas fases devem ser tratadas como um subprojeto
   independente e o fato de não sê-lo, é uma fonte de falhas, atrasos e insucesso
   .
   2.2.1.2. Butterfly
   Ao contrário da metodologia Chicken Little, a metodologia Butterfly questiona a
   necessidade de interoperabilidade entre as aplicações. Ela leva em
   consideração o fato de que o sistema legado não estará em produção enquanto o
   processo de migração ocorre. A metodologia propõe o desenvolvimento de
   um motor de migração de dados, a fim de que o sistema legado fique fora do ar o
   mínimo possível. Ela difere dos métodos Forward e Reverse Migration na medida em
   que o sistema legado deve ficar fora do ar por um tempo considerável para facilitar a
   migração dos dados antes do sistema destino entrar em funcionamento. Este é uma
   abordagem mais simples, porém mais arriscada, pois todo o fluxo de informação da
   aplicação passará a ser executado em um sistema não confiável. Segundo
   Bing Wu et al., os passos que compõem a metodologia são:
1. Planejar a migração;
1. Entender a semântica do sistema legado e desenvolver o esquema de dados
   destino;
1. Migrar todos os componentes, exceto os dados, do sistema legado para a
   arquitetura destino;
1. Gradualmente migrar os dados legados para o sistema destino e treinar os
   usuários a usar a aplicação destino; e
1. Passar a utilizar a aplicação destino.
   Na fase 2, quando se destaca a importância de entender a semântica do sistema legado,
   geralmente faz-se com base no negócio atual da empresa. É incomum, e na maioria dos
   casos faltam fontes de informação, levantar requisitos históricos, ou seja, procurar saber
   como o sistema legado funcionava em suas diversas versões e em como ele usava e
   atualizava os dados da empresa naqueles momentos. Esta perda de memória
   institucional é, também, uma fonte de problemas quando se precisa definir as
   necessárias transformações sobre os dados legados para migrá-los para o novo sistema,
   principalmente quando se precisa migrar dados históricos. O Quadro 1
   apresenta uma comparação entre as metodologias Chicken Little e Butterfly.

Quadro 1 - Quadro comparativo entre as metodologias Chicken Little e Butterfly

### 2.3. Migração de Dados

Freqüentemente, os dados que uma nova aplicação 1 necessita vêm de outras
aplicações existentes. Caso estes dados estejam disponíveis em sistemas
existentes e seu volume seja muito grande, eles devem ser migrados das aplicações
existentes para a nova aplicação, em vez de recriados. O processo de transferir dados de
um sistema para outro é chamado de migração de dados.
Projetos de migração de dados são complexos e o foco deve ser a migração da
menor quantidade de dados possível para que a aplicação destino possa entrar em
funcionamento. Nem sempre todos os dados de origem serão necessários, logo
é importante filtrar os dados relevantes. Esta análise de relevância dos dados deve ser
realizada em conjunto com os usuários que serão impactados diretamente pela migração.
Porém, em alguns casos, por força de lei ou imposição do negócio, todos os dados
devem ser migrados e estes cenários de migração são os que requerem mais
planejamento e esforço.
A migração de dados tipicamente envolve o planejamento do projeto, a definição
do escopo, a extração, a transformação (para o formato adequado), a transferência e a
verificação dos dados. É geralmente desenvolvida em duas etapas: a extração
e a carga dos dados.
A extração de dados é o processo de extrair dados de um sistema existente e
armazená-lo em um arquivo. Se o volume dos dados for relativamente pequeno, estes
podem ser extraídos para um arquivo que será referenciado diretamente pela aplicação
destino. No entanto, se o volume dos dados for grande e os sistemas utilizam diferentes
ambientes computacionais, estes devem ser armazenados em alguma mídia, e então,
carregados na aplicação destino.
A carga de dados é o processo de transferir o conteúdo do arquivo gerado na
etapa de extração para a base de dados da aplicação destino. Se os domínios dos dois
sistemas possuem uma interpretação comum entre valores e os relacionamentos entre os
dados são bem definidos, então o processo de mapeamento é relativamente direto. Caso
os domínios sejam diferentes ou os relacionamentos não estejam bem definidos, é
necessário passar por um processo de transformação dos dados, que pode ocorrer na
etapa de extração ou de carga.

Neste caso, nova aplicação entende-se como todo sistema computacional em sua versão inicial ou
resultante da atualização de um sistema pré-existente.

#### 2.3.1. Estratégias de Migração de Dados

Migração de enormes volumes de dados não ocorrem rotineiramente na maioria
das empresas. Geralmente, a área de TIC da empresa não possui vasta experiência neste
tipo de operação. Para realizar um projeto de migração de dados, é necessário que uma
estratégia de migração seja adotada no início do projeto, já que seu planejamento e as
ações necessárias dependem dessa estratégia. Há dois tipos principais de estratégias de
migração de dados: Big Bang e Trickle.

##### 2.3.1.1. Big Bang

As migrações que adotam a estratégia Big Bang são realizadas de uma só vez.
Neste caso, o sistema original deve ficar fora do ar enquanto os dados são extraídos,
transformados e carregados na aplicação destino. Segundo Datanomic Ltd.
, esta estratégia tem a vantagem da migração ser finalizada no menor tempo
possível. Porém, ela apresenta riscos: algumas organizações não podem ter o seu
sistema fora do ar por muito tempo, o que aumenta a grande carga de pressão sobre a
execução da migração e a realização de seus testes. Datanomic Ltd. ainda
afirma que as empresas que adotam esta estratégia deveriam realizar uma migração de
testes antes da migração real, mas poucas o fazem, o que compromete a qualidade dos
dados. Normalmente, quando esta estratégia é adotada, o processo de execução da
migração ocorre durante um fim de semana ou feriado.

##### 2.3.1.2. Trickle

As migrações que adotam a estratégia Trickle são realizadas de forma
incremental. Os dois sistemas executam em paralelo e os dados são migrados em fases.
Segundo Datanomic Ltd., isto pode ser desenvolvido utilizando processos em
tempo real para transferir os dados da base de origem para a base destino e para manter
os dados da base destino atualizados.
Adotar esta estratégia adiciona complexidade ao projeto e há duas possíveis
maneiras de desenvolvê-lo: na primeira, os dois sistemas executam paralelamente e os
usuários devem chavear entre as aplicações, dependendo de onde está a informação que
precisam no momento. Na segunda, os usuários utilizam o sistema antigo até que a
migração termine, porém quaisquer mudanças nos dados da aplicação fonte exigem que
os novos registros sejam migrados, de modo que a base destino permaneça atualizada. O
Quadro 2 apresenta uma comparação entre as estratégias Big Bang e Trickle.

Quadro 2 - Quadro comparativo entre as estratégias Big Bang e Trickle

#### 2.3.2. Passos de uma migração de dados

Migrações de dados são realizadas freqüentemente, porém nem todas obtêm
êxito. Através de migrações de sucesso, boas práticas foram compiladas, de modo que é
possível enumerar uma seqüência de passos que ajudam a aumentar a probabilidade de
sucesso do projeto. Os passos necessários são destacados nas subseções 2.3.2.1 a 2.3.2.5.

##### 2.3.2.1. Passo 1

Planejamento

O processo de planejamento envolve descrever em detalhes o escopo do projeto,
determinar os requisitos da migração, identificar os ambientes atual e futuro, criar e
documentar o plano de migração e definir um cronograma a ser seguido. Os requisitos e
projeto incluem a arquitetura de migração, os requisitos de hardware e software, o
procedimento de migração e os planos de teste e implantação.
O plano de migração deve determinar se a migração será realizada em fases, incluindo
quantas fases serão necessárias e que tipos de dados serão migrados em cada fase. Deve
também determinar o responsável por cada tarefa e seus prazos, além de descrever o
impacto da migração no negócio em termos de necessidade de treinamento de pessoal,
custos envolvidos e o tempo de parada do sistema. Deve ainda estabelecer um plano de
contingência, especificando como lidar com processos de negócio críticos em termos de
tempo, como pagamentos, em caso de atraso no cronograma. Quanto maior a
importância dos dados para as operações da empresa e maior a complexidade do
ambiente, mais crítico é o planejamento da migração.
O cronograma e o orçamento devem levar em consideração todo o material e
tempo necessários para auditar os dados, desenvolver as especificações de mapeamento,
escrever o código de migração, construir as regras de transformações e limpeza dos
dados, carregar e testar a migração. O cronograma também deve incluir quando o dado
estará pronto para análise e teste, quando o sistema de origem ficará fora do ar
(dependendo da metodologia adotada) e quando o novo sistema estará pronto para os

usuários. Um projeto de migração típico tem uma duração média de seis meses
a dois anos com uma equipe de cinco desenvolvedores em tempo integral.

##### 2.3.2.2. Passo 2 - Profiling e Auditorias

Quando dados são migrados para um novo sistema, pode ficar aparente que eles
contêm redundâncias e imprecisões. Enquanto estes dados são perfeitamente adequados
para o funcionamento do sistema original, eles podem não ser adequados em termos de
estrutura e conteúdo para a nova aplicação. Sem o entendimento suficiente
de ambos os sistemas, a transferência de dados de um para o outro pode ampliar o
impacto negativo de qualquer dado incorreto ou irrelevante.
Para desenvolver um projeto de migração de dados eficaz, é importante entender
por completo as fontes de dados antes de especificar o código de migração. Isto é mais
bem alcançado através da realização de uma auditoria completa dos dados que fazem
parte do escopo da migração, nos estágios iniciais do projeto. Através do uso de
ferramentas de profiling e auditoria, é possível analisar o conteúdo dos dados e
identificar quais valem a pena ser migrados, já que uma migração requer tempo,
dinheiro e esforço. O principal resultado alcançado com a análise dos
dados é o refinamento do escopo e a definição do que será migrado automaticamente,
anualmente e o que não será migrado, os
benefícios trazidos por esta prática são:

1. Com uma visibilidade completa de todos os dados de origem, a equipe pode
   identificar potenciais problemas que permaneceriam escondidos até um estágio
   mais avançado do projeto;
2. As regras para planejamento, mapeamento, execução e teste da migração são
   baseadas na análise de todos os dados de origem em vez de uma pequena
   amostra;
3. As decisões podem ser realizadas baseadas em fatos em vez de suposições; e
4. Uma auditoria completa dos dados pode reduzir o custo de reparos no código na
   etapa de testes em até 80%.
   A seguir, será considerada uma estratégia de profiling e mapeamento. A
   Figura 1 mostra os passos para identificação e mapeamento de dados.

Figura 1

Passos para identificação e mapeamento de dados.
Fonte: DM Review Magazine, Junho 1999

Nessa estratégia são adotados seis passos:

1. Identificação de coluna
   Esta fase procura analisar os valores em cada coluna ou campo da fonte de dados,
   inferindo características como tipo do dado, tamanho, domínio, freqüência,
   distribuição, cardinalidade, nulidade e unicidade;
2. Identificação de dependência
   Esta fase procura identificar dependências entre colunas de diferentes fontes de
   dados. Geralmente, não é realizada manualmente;
3. Identificação de redundância
   Esta fase compara dados entre tabelas das mesmas fontes de dados ou diferentes,
   determinando que colunas contenham sobreposição ou conjuntos idênticos de
   valores. Ela procura padrões de repetição. Esta fase procura identificar atributos
   que contêm a mesma informação, mas com nomes diferentes (sinônimos) e
   atributos que têm o mesmo nome, mas informações diferentes (homônimos).
   Também ajuda a determinar que colunas sejam redundantes e podem ser
   eliminadas. Este processo não pode ser realizado manualmente;
4. Normalização
   Procede a normalização dos dados baseada no modelo relacional;
5. Alteração do Modelo
   Faz a adequação do modelo frente a novas necessidades de informação
   detectadas; e
6. Mapeamento dos atributos
   Define regras de transformação entre atributos fonte e atributos alvo.
   2.3.2.3. Passo 3 - Construção e Design
   Nesta etapa são desenvolvidas as especificações de mapeamento. Projetos de
   migração são mais eficientes quando segmentados, pois os dados podem ser auditados,
   mapeados, testados e transferidos em fases, facilitando o seguimento do cronograma,
   orçamento e possibilitando a realização de revisões de progresso. Segundo
   Datanomic Ltd., uma vez que as especificações de mapeamento forem
   convertidas em código de migração, elas devem ser verificadas individualmente, a fim
   de identificar possíveis erros.
   2.3.2.4. Passo 4

Execução

Neste passo, os dados são extraídos da fonte, transformados e carregados na
aplicação destino utilizando regras de migração carregadas em uma ferramenta de
migração escolhida durante a etapa de planejamento.

##### 2.3.2.5. Passo 5 - Testes e Validação dos Dados

Apesar de os dados terem sido validados ao longo do processo de migração,
testes unitários, de sistema e de carga devem ser feitos para garantir que todos os dados

foram migrados e que o novo sistema se comporta como esperado. Caso os
passos dois e três não tenham sido realizados de maneira eficaz, a chance da ocorrência
de erros aumenta, acarretando em repetição de trabalho, o que leva a um aumento no
custo do projeto e um possível atraso no cronograma.

#### 2.3.3. Desafios de uma migração de dados

De acordo com IBM, os principais
desafios impostos por um projeto de migração de dados são:
A necessidade de minimização do tempo em que o sistema ficará fora do ar, pois
normalmente a organização congela a entrada de dados enquanto realiza a migração
dos dados;
A necessidade de aquisição e instalação de software de migração de dados em
servidores;
A ocorrência de inconsistência de valores. Isto acontece quando múltiplos sistemas
de origem possuem o mesmo conceito (entidade), mas as representações (valores)
variam (e.g. em um sistema o campo que armazena números de telefone utiliza o
formato XXXXXXXX, já em outro sistema, o mesmo campo utiliza o formato (XX)
XXXX-XXXX);
A necessidade de preservação da integridade referencial entre as entidades e
relacionamentos da aplicação destino durante o processo de carga;
A sincronização dos dados. Apesar de estes serem migrados do sistema original para
o sistema destino, o sistema original pode continuar em operação. Para preservar a
integridade dos dados, quando estes forem adicionados e/ou modificados no sistema
original, também devem ser adicionados e/ou alterados no sistema destino;
Necessidade de escrita das especificações e códigos de mapeamento orientada a
conteúdo, em vez de orientada a metadados. Para o propósito de migração de dados,
a informação que descreve a origem (e.g. o nome da base de dados, o nome da
tabela, o nome da coluna) e as características de cada coluna (e.g. o tipo, o tamanho,
a escala, a precisão) é considerada metadados. Conteúdo é o que está contido em
cada registro da coluna. Uma migração de dados orientada a metadados assume que
o conteúdo reflete a sua descrição, o que nem sempre acontece. Somente a
realização de profiling e auditorias pode confirmar de fato o conteúdo do registro;
Possibilidade de perda e corrupção de dados durante o processo;
Alocação insuficiente de tempo para a realização de testes; e
Cronograma imprevisível. Mesmo com um planejamento meticuloso, situações
inesperadas podem surgir durante a migração, ocasionando problemas que impactam
no cronograma.

#### 2.3.4. Fatores de Sucesso de uma migração de dados

Apesar dos desafios presentes em um projeto de migração de dados, existem
algumas boas práticas que diminuem a probabilidade de falha do projeto. Segundo
Datanomic Ltd., estas boas práticas são as que se seguem:
A migração de dados deve ser vista como um projeto completo. Portanto, faz-se
necessário alocar recursos, definir claramente o escopo do projeto, definir um plano
de projeto com um cronograma que leva em consideração a possibilidade de
ocorrência de problemas inesperados e angariar fundos necessários para a execução
do projeto;
Levar em consideração o tempo necessário para testar o resultado da migração e
resolver eventuais problemas ao definir o cronograma do projeto;
Utilizar ferramentas de profiling e auditoria para analisar completamente os dados,
refinar o escopo do projeto e escrever as especificações de mapeamento com mais
segurança. Entender que informação é importante e como deve ser usada é crítico
para o sucesso da empreitada;
Minimizar a quantidade de dados a serem migrados, quando possível;
Testar o resultado da migração o quanto antes; e
Enquanto que muitas tarefas podem ser automatizadas, outras devem ser realizadas
manualmente. Realizar estas tarefas com atenção ajuda a manter a consistência dos
dados.
Segundo Mohanty, o maior desafio de um projeto de migração de dados é
fazer com que o sistema alvo entenda o que o sistema fonte quer dizer. Abaixo estão
algumas boas práticas e problemas que devem ser evitados em um bom projeto de
migração de dados:
Mapeamento consistente Todos os campos de dados que serão migrados do
sistema fonte para o sistema alvo devem ser definidos e examinados para assegurar
consistência com o tamanho dos campos, tipos dos dados, valores de domínio
permitidos, regras de sistema, verificações de integridade e qualquer outro problema
possível. Um mapa de dados detalhado é crítico para entender para onde a
informação está indo; da mesma forma, se existem obstáculos conhecidos ou
evitáveis no caminho para o sistema alvo. Um bom mapa de dados irá detalhar em
profundidade a relação entre os campos do sistema fonte com o sistema alvo.
Preferencialmente, deve incluir:
Nomes significativos dos campos origem e destino;
Tamanhos e tipos destes campos; e
Qualquer lógica envolvida no mapeamento como tratamento de strings ou
validações contra regras de negócio.
Validação da extração É sabido que dados nos sistemas fonte geralmente contêm
problemas ou escondem erros causados pelas mais variadas razões, desde falhas
humanas até regras e validações mal testadas ou definidas em sistemas pouco
13

sofisticados. Regras de validação devem ser utilizadas como primeiro passo para
tentar identificar e corrigir estes problemas, estendendo o processo em tantas
iterações quantas forem necessárias. É comum que alguns tipos de erros não
apareçam até que outros tipos sejam detectados e corrigidos. Mesmo que o sistema
fonte tenha ignorado discrepâncias como, por exemplo, o mesmo cliente possuir
endereços de cobrança diferentes armazenados em diferentes arquivos ou tabelas, o
sistema alvo potencialmente deve ter regras de negócio que defina qual endereço
será considerado como o que irá ser carregado, eliminando esta inconsistência.
Validação e limpeza de dados são essenciais e componentes chave para um bom
plano de migração de dados.
Qualidade da transformação Dados extraídos do sistema fonte precisam ser
transformados ou traduzidos num formato que o sistema alvo possa importar e
entender. Estas transformações não serão definidas somente no mapeamento dos
dados, mas serão executadas sob funções de lógica de negócio que serão essenciais
para carregarem estruturas de dados mais complexas. Existem ferramentas de ETL
(acrônimo em inglês para Extração, Transformação e Carga) no mercado que podem
ajudar bastante neste estágio.
Até agora foram discutidos aspectos técnicos da migração de dados. Entretanto,
como acontece nos projetos de TIC, o como é tão importante como o quê, onde e
quando. Quando se trata com os aspectos gerenciais dos projetos de migração de dados,
as seguintes preocupações devem ser consideradas:
Abordagem Big Bang ou Trickle Quando se decide migrar dados de um sistema
para outro, faz mais sentido fazê-lo de uma só vez ou mover dados em fases
controladas com múltiplas iterações? Naturalmente existirão prós e contras em
ambas as opções. Considerar qual abordagem será a mais adequada para
determinada organização requer avaliar uma variedade de fatores. Alguns exemplos
destes fatores são:
Qual a quantidade de dados que vai ser migrada?
Quanto tempo será necessário, levando em consideração as condições
normais de processamento em produção da organização?
Quanto tempo a organização suporta parar os sistemas para a migração?
A organização tem condições de simular um big bang antes da migração
definitiva? E
É possível estimar o ROI (acrônimo em inglês de Retorno do Investimento)
de ambas as abordagens?
As respostas destas questões devem ser encaminhadas antes de um simples
objeto ser extraído ou uma simples transformação ser definida. Um projeto de
migração de dados não pode prosseguir se estiver pobremente definido em seu
escopo, agenda, estimativa de esforço, custos e recursos requeridos.
Rollback
Quando se carrega dados no sistema alvo, o que acontece se a migração de
dados falhar?
A equipe está preparada para utilizar alguma funcionalidade de transação de
rollback existente ou tem-se capacidade de desenhar e construir uma, caso
não exista?
14

Como serão administradas as expectativas dos clientes caso isto aconteça?
Há um plano de mitigação destas questões construído? E
Esta possibilidade, de retornar, foi discutida com os usuários?
As respostas destas questões proporcionam uma camada adicional de segurança
e contribuem muito em termos de concluir o projeto no prazo, sem alongar o
orçamento e gerenciando as expectativas do usuário.
Escalabilidade Naturalmente, quando alguém começa a falar de migração de
dados, com dados críticos indo e vindo, e como isto pode incrementar o negócio da
empresa, o assunto escalabilidade vem à tona. Como gerente, somente estando
seguro de que se tem infra-estrutura para suportar a sobrecarga de processamento
provocada pela migração e um eventual crescimento não previsto deste, é que se
deve começar o projeto.
Replicação A questão é a seguinte: o que acontece em caso de um desastre ou
uma falha irrecuperável do sistema? Comumente esta preocupação aparecerá em um
projeto de migração de dados. Tipicamente nasce da pressão colocada sobre o
gerente de fazer uma migração correta e não colocar em risco 100% da produção.
Migrar dados para um sistema espelho ao mesmo tempo em que se migra para o
sistema alvo deve ser seriamente considerado para adicionar uma camada a mais de
segurança e assegurar que um plano de recuperação de desastre existe.
Ainda segundo Mohanty, migração de dados é um importante aspecto
do esforço da maioria dos desenvolvimentos de software, mesmo que esta importância
seja freqüentemente subestimada ou inadvertidamente minimizada. Parece que, no
extraordinário esforço de desenvolver software, realmente, a eventual medida de
sucesso, de alguma forma, não depende de uma migração de dados precisa. A razão
disto é bastante simples optar por um novo sistema é uma decisão de negócio tendo
sua própria prioridade. Entretanto, migrar dados históricos para fazer o novo sistema
funcionar parece não ser a prioridade principal. Ao contrário, colocar o novo sistema em
produção para suportar os processos críticos da empresa é a prioridade principal. Uma
falsa impressão do sucesso de um projeto de migração de dados é quando se busca um
simples movimento de dados sem remendos, permanecendo, assim, à sombra da
implantação do novo sistema.

#### 2.3.5. Arquitetura de migração de dados

Para desenvolver uma arquitetura de migração de dados, a equipe de migração
de dados deve levar em consideração os seguintes tópicos:
Volume de dados a ser migrado;
Poder de processamento dos sistemas fonte e alvo; e
Complexidade das regras de mapeamento e das regras de negócio.
Baseados nestas questões, duas estratégias de arquitetura de migração de dados são
destacadas nas subseções 2.3.5.1 e 2.3.5.2:

##### 2.3.5.1. Point-to-Point

Nesta estratégia, os dados são extraídos do sistema fonte e carregados em uma área
intermediária local no sistema alvo. Depois da transferência dos dados, estes são
tratados e transformados localmente nesta área intermediária para depois serem
carregados na base definitiva do sistema alvo.
Características:
Redução do tráfego de rede; e
Aumento de processamento no sistema alvo.
A Figura 2 mostra a arquitetura Point-to-Point.

Figura 2

Arquitetura de migração de dados Point-to-Point.

Fonte: DM Review Special Report, maio 2004

##### 2.3.5.2. Hub-Spoke

Nesta arquitetura, os dados são extraídos do sistema fonte e carregados em uma
área intermediária independente que funciona como um concentrador. Os dados são
tratados e transformados neste ambiente para então serem carregados no sistema alvo.
Características:
Dá suporte a qualquer número de sistemas fonte e/ou alvo;
Regras de mapeamento e de negócio são mantidas em uma camada separada; e
Balanceamento do processamento do lado do sistema alvo.
A Figura 3 mostra a arquitetura Hub-Spoke.

Figura 3

Arquitetura de migração de dados Hub-Spoke.

Fonte: DM Review Special Report, maio 2004

O Quadro 3 apresenta uma comparação entre as estratégias Point-to-Point e Hub-Spoke.
Quadro 3 - Quadro comparativo entre as estratégias Point-to-Point e Hub-Spoke

#### 2.3.6. Riscos de uma migração de dados

Afirmam Morris que, como em todo projeto de
TIC, os riscos de um projeto de migração de dados devem ser identificados, mitigados e,
se ocorrerem, planos de contingência devem ser colocados em prática. A seguir, alguns
riscos mais comumente identificados na maioria dos projetos de migração de dados:
Falha ao tratar migração de dados como um projeto em si próprio Migração
de dados é um empreendimento complexo que não deve ser considerado meramente
como um esforço periférico no desenvolvimento do projeto principal. O esforço de
migração deve ser tratado como um completo subprojeto com um processo definido,
uma cuidadosa estimativa de custo e tempo, e uma série de fases que possam ser
rastreadas ou administradas.
Subestimar o tempo e o custo da migração de dados É importante realizar uma
diligente pesquisa no sistema fonte a fim de determinar a qualidade da
documentação e da fonte dos dados. Se o sistema fonte não possuir documentação
de dados atualizada na forma de modelos de dados e dicionário de dados, a tarefa de
determinar a estrutura e o tipo dos dados da fonte de dados desejada e o seu
mapeamento para os dados alvo deverá ser levada em consideração na estimativa de
custo e tempo. Se o sistema fonte é menos exigente nos requerimentos de qualidade
de dados que o sistema alvo ou se a qualidade dos dados do sistema fonte tem
permitido falhas ao longo do tempo, tem-se que considerar um custo e tempo extras
para a tarefa de limpeza dos dados na extração ou após a migração.
Deficiência no estado final da qualidade dos dados Se o esforço de migração
não especificar formalmente o nível desejado da qualidade dos dados e um conjunto
de testes de controle para verificá-los, o domínio alvo pode ser carregado com dados
de qualidade duvidosa. Isto irá impactar negativamente a percepção externa do
esforço do desenvolvimento.
Falha ao obter o suporte organizacional Quando a complexidade e importância
da migração dos dados não são adequadamente apreciadas, fica difícil mobilizar o
suporte organizacional para esta migração, principalmente em termos financeiros e

de recursos. Pode-se até ter mais dificuldades de conseguir um bom nível de suporte
organizacional se a equipe que mantém o sistema fonte se sentir ameaçada pelo
novo sistema ou simplesmente porque o esforço de migração não é a prioridade
principal da organização para aquele projeto.

### 2.4. Gerência de Projetos

Não está no escopo desta dissertação um aprofundamento na disciplina de
Gerência de Projetos. O que se pretende com este tópico é identificar os principais
conceitos envolvidos para servir como diretriz na integração com os itens de migração
de dados apresentados. Usou-se o Guia PMBOK como referência,
especificamente os grupos de processos de Planejamento, Monitoramento e Controle e
Execução por se adequarem ao ciclo de vida de um projeto de migração de dados. Esta
integração será a base da metodologia apresentada no Capítulo 3.
Um projeto é um esforço temporário empreendido para criar um produto, serviço
ou resultado exclusivo. Conforme Mohanty, o esforço de migração de dados
deve ser tratado como um completo subprojeto. Portanto, à luz das afirmações, propõese submeter às atividades de migração de dados às boas técnicas de gerência de projetos
para se obter resultados com uma taxa de sucesso maior do que a média apresentada
pelo The Standish Group diz: o gerenciamento de
projetos é a aplicação de conhecimento, habilidades, ferramentas e técnicas às
atividades do projeto a fim de atender aos seus requisitos. O gerenciamento de projetos
é realizado através da aplicação e da integração dos seguintes processos de
gerenciamento de projetos: iniciação, planejamento, execução, monitoramento e
controle e encerramento. O gerente de projetos é a pessoa responsável pela realização
dos objetivos do projeto. Gerenciar um projeto inclui:
Identificação das necessidades;
Estabelecimento de objetivos claros e alcançáveis;
Balanceamento das demandas conflitantes de qualidade, escopo, tempo e
custo; e
Adaptação das especificações, dos planos e da abordagem às diferentes
preocupações e expectativas das diversas partes interessadas.
Os projetos são um meio de organizar atividades que não podem ser abordadas
dentro dos limites operacionais normais da organização, como a migração dos dados de
um grande sistema. Os projetos são, portanto, freqüentemente utilizados como um meio
de atingir o plano estratégico de uma organização, seja a equipe do projeto formada por
funcionários da organização ou prestadores de serviços contratados.
A Figura 4 mostra uma visão geral das áreas de conhecimento envolvidas em
gerenciamento de projetos e os processos envolvidos.

Figura 4 - Visão geral das áreas de conhecimento em gerenciamento de projetos e os processos de
gerenciamento de projetos.
Fonte: Guia PMBOK

Já a Figura 5 destaca as áreas de especialização necessárias à equipe de
gerenciamento de projetos.

Figura 5 - Áreas de especialização necessárias à equipe de gerenciamento de projetos.
Fonte: Guia PMBOK

#### 2.4.1. Ciclo de vida do projeto

O ciclo de vida do projeto define as fases que conectam o início de um projeto
ao seu final. A transição de uma fase para a outra dentro do ciclo de vida de um projeto
em geral envolve e, normalmente, é definida por alguma forma de transferência técnica
ou entrega. As entregas de uma fase geralmente são revisadas, para garantir que estejam
completas e exatas, e aprovadas antes que o trabalho seja iniciado na próxima fase.
Não existe uma única melhor maneira para definir um ciclo de vida ideal do projeto.
Algumas organizações estabeleceram políticas que padronizam todos os projetos com
um único ciclo de vida, enquanto outras permitem que a equipe de gerenciamento de
projetos escolha o ciclo de vida mais adequado para seu próprio projeto. Os ciclos de
vida do projeto geralmente definem:
Que trabalho técnico deve ser realizado em cada fase (por exemplo, em qual fase
deve ser realizado o trabalho do arquiteto);
Quando as entregas devem ser geradas em cada fase e como cada entrega é
revisada, verificada e validada;
Quem está envolvido em cada fase (por exemplo, a engenharia simultânea exige
que os desenvolvedores estejam envolvidos com os requisitos e o projeto); e
Como controlar e aprovar cada fase.
A maioria dos ciclos de vida do projeto compartilha diversas características comuns:
As fases geralmente são seqüenciais e normalmente são definidas por algum
formulário de transferência de informações técnicas ou de entrega de
componentes técnicos;

Os níveis de custos e de pessoal são baixos no início, atingem o valor máximo
durante as fases intermediárias e caem rapidamente conforme o projeto é
finalizado;
O nível de incertezas é o mais alto e, portanto, o risco de não atingir os objetivos
é o maior no início do projeto. A certeza de término geralmente se torna cada
vez maior conforme o projeto continua; e
A capacidade das partes interessadas de influenciarem as características finais do
produto do projeto e o custo final do projeto é mais alta no início e torna-se cada
vez menor conforme o projeto continua. Contribui muito para esse fenômeno o
fato de que o custo das mudanças e da correção de erros geralmente aumenta
conforme o projeto continua.

#### 2.4.2. Processos de gerenciamento de projetos

Os processos de gerenciamento de projetos são apresentados como elementos
distintos, com interfaces bem definidas. As especificações de um projeto são definidas
como objetivos que precisam ser realizados com base na complexidade, no risco, no
tamanho, no prazo, na experiência da equipe do projeto, no acesso aos recursos, na
quantidade de informações históricas, na maturidade da organização em gerenciamento
de projetos e no setor e na área de aplicação. Os grupos de processos necessários e seus
processos constituintes são orientações para a aplicação do conhecimento e das
habilidades de gerenciamento de projetos adequados durante a execução do projeto.
Além disso, a aplicação dos processos de gerenciamento de projetos a um projeto é
iterativa e muitos processos são repetidos e revisados durante sua execução.
Existem cinco grupos de processos de gerenciamento de projetos necessários
para qualquer projeto. Esses cinco grupos de processos possuem dependências claras e
são executados na mesma seqüência em todos os projetos. Eles são independentes das
áreas de aplicação ou do foco do setor. Os grupos de processos individuais e os
processos constituintes individuais geralmente são iterados antes do término do projeto.
Os processos constituintes também podem ter interações, tanto dentro de um grupo de
processos como entre grupos de processos. Para o objetivo deste trabalho serão
abordados os seguintes grupos de processos:
Grupo de processos de planejamento. Define e refina os objetivos e planeja a
ação necessária para alcançar os objetivos e o escopo para os quais o projeto foi
realizado.
Grupo de processos de execução. Integra pessoas e outros recursos para
realizar o plano de gerenciamento do projeto para o projeto.
Grupo de processos de monitoramento e controle. Mede e monitora
regularmente o progresso para identificar variações em relação ao plano de
gerenciamento do projeto, de forma que possam ser tomadas ações corretivas,
quando necessário, para atender aos objetivos do projeto.
Dentre os grupos de processos citados, serão destacadas as atividades pertinentes em
um ciclo de vida de um projeto de migração de dados.
A Figura 6 apresenta uma visão de alto nível das interações entre os grupos de
processos.

Figura 6 - Resumo de alto nível das interações entre os grupos de processos.
Fonte: Guia PMBOK.

Observação: não são mostradas todas as interações entre os processos nem todo o fluxo
de dados entre os grupos de processos.

##### 2.4.2.1. Processos de Planejamento

Os processos de planejamento desenvolvem o plano de gerenciamento do
projeto. Esses processos também identificam, definem e amadurecem o escopo do
projeto, o custo do projeto e agendam as atividades do projeto que ocorrem dentro dele.
Durante o planejamento do projeto, a equipe do projeto deve envolver todas as partes
interessadas adequadas, dependendo da influência delas no projeto e nos seus
resultados. O Grupo de processos de planejamento inclui os seguintes processos:
Desenvolver o plano de gerenciamento do projeto
Este é o processo necessário para definir, preparar, integrar e coordenar todos os
planos auxiliares em um plano de gerenciamento do projeto. O plano de
gerenciamento do projeto se torna a principal fonte de informações de como o
projeto será planejado, executado, monitorado e controlado e encerrado.
A Figura 7 mostra Entradas e Saídas para o plano de desenvolvimento de projetos.

Figura 7 - Entradas e saídas: Desenvolver o plano de gerenciamento do projeto.
Fonte: Guia PMBOK.

Definição do escopo
Desenvolve uma declaração do escopo detalhada do projeto como base para futuras
decisões.
A Figura 8 mostra Entradas e Saídas para a definição do escopo de projetos.

Figura 8 - Entradas e saídas: Definição do Escopo.
Fonte: Guia PMBOK.

Definição da atividade
Identifica as atividades específicas que precisam ser realizadas para produzir as
várias entregas do projeto.
A Figura 9 mostra Entradas e Saídas para definição de atividade de projetos.

Figura 9 - Entradas e saídas: Definição da atividade.
Fonte: Guia PMBOK.

Seqüenciamento de atividades
Identifica e documenta as dependências entre as atividades do cronograma.
A mostra Entradas e Saídas para definição de atividade de projetos.

Figura 10 - Entradas e saídas: Seqüenciamento de atividades.
Fonte: Guia PMBOK.

Estimativa de recursos da atividade
Estima o tipo e as quantidades de recursos necessários para realizar cada atividade
do cronograma.
A Figura 11 mostra Entradas e Saídas para estimativa de recursos de atividade de
projetos.

Figura 11 - Entradas e saídas: Estimativa de recursos da atividade.
Fonte: Guia PMBOK.

Estimativa de duração da atividade
Estima o número de períodos de trabalho que serão necessários para terminar
atividades específicas do cronograma.

A Figura 12 mostra Entradas e Saídas para estimativa de duração de atividade de
projetos.

Figura 12 - Entradas e saídas: Estimativa de duração da atividade.
Fonte: Guia PMBOK.

Desenvolvimento do cronograma
Analisa os recursos necessários, restrições do cronograma, durações e seqüências de
atividades para criar o cronograma do projeto.
A Figura 13 mostra Entradas e Saídas para desenvolvimento do cronograma de
projetos.

Figura 13 - Entradas e saídas: Desenvolvimento do cronograma.
Fonte: Guia PMBOK.

Estimativa de custos
Desenvolve uma aproximação dos custos dos recursos necessários para terminar as
atividades do projeto.
27

A Figura 14 mostra Entradas e Saídas para estimativa de custos de projetos.

Figura 14 - Entradas e saídas: Estimativa de custos.
Fonte: Guia PMBOK.

Planejamento da qualidade
Identifica os padrões de qualidade relevantes para o projeto e determina como
satisfazê-los.
A Figura 15 mostra Entradas e Saídas para planejamento da qualidade de projetos.

Figura 15 - Entradas e saídas: Planejamento da qualidade.
Fonte: Guia PMBOK.

Planejamento de recursos humanos
Identifica e documenta funções, responsabilidades e relações hierárquicas do
projeto, além de criar o plano de gerenciamento de pessoal.

A Figura 16 mostra Entradas e Saídas para planejamento de recursos humanos de
projetos.

Figura 16 - Entradas e saídas: Planejamento de recursos humanos.
Fonte: Guia PMBOK.

Planejamento das comunicações
Determina as necessidades de informação e de comunicação das partes interessadas
no projeto.
A Figura 17 mostra Entradas e Saídas para planejamento das comunicações de
projetos.

Figura 17 - Entradas e saídas: Planejamento das comunicações.
Fonte: Guia PMBOK.

Identificação de riscos
Determina os riscos que podem afetar o projeto e documenta suas características.
A Figura 18 mostra Entradas e Saídas para identificação dos riscos de projetos.

Figura 18 - Entradas e saídas: Identificação dos riscos.
Fonte: Guia PMBOK.

Análise qualitativa de riscos
Prioriza riscos para análise ou ação adicional subseqüente através de avaliação e
combinação de sua probabilidade de ocorrência e impacto.
A Figura 19 mostra Entradas e Saídas para análise qualitativa de riscos de projetos.

Figura 19 - Entradas e saídas: Análise qualitativa de riscos.
Fonte: Guia PMBOK.

Planejar compras e aquisições
Determina o que comprar ou adquirir e quando e como fazer isso.
A Figura 20 mostra Entradas e Saídas para planejamento de compras e aquisições de
projetos.

Figura 20 - Entradas e saídas: Planejar compras e aquisições.
Fonte: Guia PMBOK.

##### 2.4.2.2. Processos de Execução

O Grupo de processos de execução é constituído pelos processos usados para
terminar o trabalho definido no plano de gerenciamento do projeto a fim de cumprir os
requisitos do referido projeto. A equipe do projeto deve determinar quais são os
processos necessários para seu projeto específico. As variações normais de execução
exigirão algum replanejamento. Essas variações podem incluir durações de atividades,
produtividade e disponibilidade de recursos, além de riscos não esperados. Tais
variações podem ou não afetar o plano de gerenciamento do projeto, mas podem exigir
uma análise. O Grupo de processos de execução inclui:
Orientar e gerenciar a execução do projeto
Orienta as diversas interfaces técnicas e organizacionais que existem no projeto para
executar o trabalho definido no plano de gerenciamento do projeto.
A Figura 21 mostra Entradas e Saídas para orientar e gerenciar a execução de
projetos.

Figura 21 - Entradas e saídas: Orientar e gerenciar a execução do projeto.
Fonte: Guia PMBOK.

Realizar a garantia da qualidade
Aplica as atividades de qualidade planejadas e sistemáticas para garantir que o
projeto emprega todos os processos necessários para atender aos requisitos.
A Figura 22 mostra Entradas e Saídas para realizar a garantia da qualidade de
projetos.

Figura 22 - Entradas e saídas: Realizar a garantia da qualidade.
Fonte: Guia PMBOK.

Contratar ou mobilizar a equipe do projeto
Obtém os recursos humanos necessários para terminar o projeto.
A Figura 23 mostra Entradas e Saídas para contratar ou mobilizar a equipe de
projetos.

Figura 23 - Entradas e saídas: Contratar ou mobilizar a equipe do projeto.
Fonte: Guia PMBOK.

Distribuição das informações
Coloca as informações à disposição das partes interessadas no projeto no momento
oportuno.
A Figura 24 mostra Entradas e Saídas para distribuição das informações de projetos.

Figura 24 - Entradas e saídas: Distribuição das informações.
Fonte: Guia PMBOK.

##### 2.4.2.3. Processos de Monitoramento e Controle

O Grupo de processos de monitoramento e controle é constituído pelos
processos realizados para observar a execução do projeto, de forma que possíveis
problemas possam ser identificados no momento adequado e que possam ser tomadas

ações corretivas, quando necessário, para controlar a execução do projeto. O Grupo de
processos de monitoramento e controle inclui:
Monitorar e controlar o trabalho do projeto
Coleta, mede e dissemina informações sobre o desempenho e avalia as medições e
as tendências para efetuar melhorias no processo.
A Figura 25 mostra Entradas e Saídas para monitorar e controlar o trabalho de
projetos.

Figura 25 - Entradas e saídas: Monitorar e controlar o trabalho do projeto.
Fonte: Guia PMBOK.

Controle integrado de mudanças
Controla os fatores que criam mudanças para garantir que essas mudanças sejam
benéficas, determina se ocorreu uma mudança e gerencia as mudanças aprovadas,
inclusive o momento em que ocorrem.
A Figura 26 mostra Entradas e Saídas para controle integrado de mudanças de
projetos.

Figura 26 - Entradas e saídas: Monitorar e controlar o trabalho do projeto.Entradas e saídas:
Controle integrado de mudanças.
Fonte: Guia PMBOK.

Verificação do escopo
Formaliza a aceitação das entregas do projeto terminadas.
A Figura 27 mostra Entradas e Saídas para verificação do escopo de projetos.

Figura 27 - Entradas e saídas: Verificação do escopo.
Fonte: Guia PMBOK.

Controle do escopo
Controla as mudanças feitas no escopo do projeto.
A Figura 28 mostra Entradas e Saídas para controle do escopo de projetos.

Figura 28 - Entradas e saídas: Controle do escopo.
Fonte: Guia PMBOK.

Controle do cronograma
Este é o processo necessário para controlar as mudanças feitas no cronograma do
projeto.
A Figura 29 mostra Entradas e Saídas para controle do cronograma de projetos.

Figura 29 - Entradas e saídas: Controle do cronograma.
Fonte: Guia PMBOK.

Controle de custos
O processo de influenciar os fatores que criam as variações e controlar as mudanças
no orçamento do projeto.
A Figura 30 mostra Entradas e Saídas para controle de custos de projetos.

Figura 30 - Entradas e saídas: Controle de custos.
Fonte: Guia PMBOK.

Realizar o controle da qualidade
Monitora resultados específicos do projeto a fim de determinar se eles estão de
acordo com os padrões relevantes de qualidade e identifica maneiras de eliminar as
causas de um desempenho insatisfatório.
A Figura 31 mostra Entradas e Saídas para realizar controle da qualidade de
projetos.

Figura 31 - Entradas e saídas: Realizar controle da qualidade.
Fonte: Guia PMBOK.

Gerenciar a equipe do projeto
Acompanha o desempenho de membros da equipe, fornece feedback, resolve
problemas e coordena mudanças para melhorar o desempenho do projeto.
A Figura 32 mostra Entradas e Saídas para gerenciar a equipe do projeto de projetos.

Figura 32 - Entradas e saídas: Gerenciar a equipe do projeto.
Fonte: Guia PMBOK.

Monitoramento e controle de riscos
Acompanha os riscos identificados, monitora os riscos residuais, identifica novos
riscos, executa planos de respostas a riscos e avalia sua eficiência durante todo o
ciclo de vida do projeto.
A Figura 33 mostra Entradas e Saídas para monitoramento e controle dos riscos de
projetos.

Figura 33 - Entradas e saídas: Monitoramento e controle dos riscos.
Fonte: Guia PMBOK.

#### 2.4.3. Áreas de conhecimento em gerenciamento de projetos

Segundo o PMBOK, gerenciamento de projetos abrange nove áreas de
conhecimento. Não é do escopo deste trabalho detalhá-las. Vai-se apenas citá-las e
mostrar o mapeamento em relação às atividades apresentadas, pois a metodologia
proposta baseia-se nessas atividades.
As áreas de conhecimento são as seguintes:
Gerenciamento de integração do projeto
A área de conhecimento em gerenciamento de integração do projeto inclui os
processos e as atividades necessárias para identificar, definir, combinar, unificar e
coordenar os diversos processos e atividades de gerenciamento de projetos dentro
dos grupos de processos de gerenciamento de projetos.
Gerenciamento do escopo do projeto
O gerenciamento do escopo do projeto inclui os processos necessários para garantir
que o projeto inclua todo o trabalho necessário, e somente ele, para terminar o
projeto com sucesso.
Gerenciamento de tempo do projeto
O gerenciamento de tempo do projeto inclui os processos necessários para realizar o
término do projeto no prazo.
Gerenciamento de custos do projeto
O gerenciamento de custos do projeto inclui os processos envolvidos em
planejamento, estimativa, orçamentação e controle de custos, de modo que seja
possível terminar o projeto dentro do orçamento aprovado.
Gerenciamento da qualidade do projeto
Os processos de gerenciamento da qualidade do projeto incluem todas as atividades
da organização executora que determinam as responsabilidades, os objetivos e as
políticas de qualidade, de modo que o projeto atenda às necessidades que motivaram
sua realização.
Gerenciamento de recursos humanos do projeto
O gerenciamento de recursos humanos do projeto inclui os processos que organizam
e gerenciam a equipe do projeto.
Gerenciamento das comunicações do projeto
O gerenciamento das comunicações do projeto é a área de conhecimento que
emprega os processos necessários para garantir a geração, coleta, distribuição,
armazenamento, recuperação e destinação final das informações sobre o projeto de
forma oportuna e adequada.
Gerenciamento de riscos do projeto
O gerenciamento de riscos do projeto inclui os processos que tratam da realização
de identificação, análise, respostas, monitoramento e controle e planejamento do
gerenciamento de riscos em um projeto.

Gerenciamento de aquisições do projeto
O gerenciamento de aquisições do projeto inclui os processos para comprar ou
adquirir os produtos, serviços ou resultados necessários de fora da equipe do projeto
para realizar o trabalho.
A Figura 34 mostra o mapeamento entre os processos de gerenciamento de
projetos e as áreas de conhecimento.

.
Figura 34 - Mapeamento entre os processos de gerenciamento de projetos e as áreas de
conhecimento.
Fonte: PMBOK.

### 2.5. Conclusões do capítulo

Neste capítulo, procurou-se apresentar relevantes aspectos de três áreas
específicas: migração de sistemas legados, migração de dados e gerência de projetos. O
objetivo desta abordagem, além de definir um claro contexto, foi determinar as
interseções existentes entre as áreas observadas e como estas interseções vêm sendo
tratadas. Notou-se que, entre as estratégias de migração de sistemas legados estudadas,
migração de dados é uma atividade sempre presente. Porém não ficou evidente
tratamento especial para esta atividade. As estratégias de migração de dados descritas
não se aprofundaram no detalhamento de etapas e atividades. Já diversos autores citados,
Mohanty,
demonstraram preocupação com o alto índice de fracasso dos projetos de migração de
dados e apontaram motivos comuns para o insucesso. Um dos principais motivos de
insucesso observado diz respeito ao não tratamento de migração de dados como um
subprojeto à parte do projeto principal de migração do sistema legado. Tais autores
contribuem, também, listando sugestões de boas práticas.
A necessidade de abordar a atividade de migrar dados num projeto de migração
de sistema legado como um subprojeto sugere a adoção das boas práticas da gerência de
projetos. Procurou-se identificar dentre os grupos de processos da Gerência de Projetos,
proposta pelo Guia PMBOK, aqueles mais adequados para uma natural
seqüência de etapas de um projeto de migração de dados.
Conforme visto neste capítulo, existem muitos trabalhos na área de migração de
dados. Entretanto, não especificam uma metodologia, mas apenas estratégias e boas
práticas. Para estruturar a metodologia proposta nesta dissertação, serão tomadas como
base as etapas definidas em, pois atendem às necessidades de um bom
projeto de migração de dados e são aderentes ao ciclo de vida do projeto e aos grupos de
processos propostos pelo Guia PMBOK, acrescentando-se, para tal aderência,
uma etapa de Monitoramento e Controle. Como já citado, o Guia PMBOK foi
estudado no sentido de identificar-se, dentre as suas 44 atividades, quais deveriam estar
presentes no ciclo de vida de um projeto de migração de dados. Optou-se por utilizar
principalmente os processos dos grupos de processos de Planejamento, Monitoramento
e Controle e Execução. Outros trabalhos importantes que também serão utilizados são
os apresentados por Mohanty e Youn et al
, pois são bastante esclarecedores em relação à importância de migrar dados, as
atividades envolvidas e o risco de não fazê-las.
A Figura 35 mostra que a metodologia proposta baseia-se na interseção entre as
áreas estudadas. Procurou-se identificar os pontos de convergência das três disciplinas,
adequá-los a um projeto de migração de dados e propor as atividades necessárias para
executa-lo.

Figura 35 - Interseção entre as áreas estudadas

## 3. Metodologia proposta

Este capítulo define uma metodologia de migração de dados num contexto de
migração de sistemas legados. Serão tomados como base para a metodologia os
seguintes trabalhos:
As cinco etapas definidas em - Planejamento, Profiling e Auditoria,
Construção e Design, Execução e Testes e Validação dos dados - por serem
adequadas ao ciclo de vida de um projeto genérico de migração de dados;
Quatorze atividades do grupo de processos de Planejamento, nove atividades do
grupo de processos de Monitoramento e Controle e quatro atividades do grupo
de processos de Execução do Guia PMBOK, feitos os necessários
ajustes para um projeto de migração de dados;
Outros trabalhos importantes que também serão utilizados são os apresentados
por Mohanty e Youn et al
. Estes trabalhos estão relacionados, principalmente, à importância de
migrar dados, às atividades recomendadas e ao risco de não fazê-las.
No contexto estudado, entende-se que migração de dados faz parte de uma ação
maior, a migração do sistema legado. Portanto, pretende-se propor uma metodologia
ágil com as atividades imprescindíveis para o sucesso da empreitada, tornando-a viável
de ser executada em ambientes geralmente escassos de recursos. Ressalta-se que
migração de dados deve ser vista como um subprojeto e não como mais uma atividade
do projeto principal. Este é um requisito para a aplicação da metodologia. Outro
requisito é a indicação, pelo gerente do projeto, do responsável pela migração dos dados.
Em todo projeto que necessite transferir dados, o gerente deve pensar em migração de
dados desde o primeiro dia.
A metodologia proposta é composta de cinqüenta e duas atividades distribuídas
em seis etapas. Conforme visto no capítulo anterior, existem muitos trabalhos na área de
migração de dados. Entretanto, não especificam uma metodologia, mas apenas
estratégias e boas práticas. Nesta dissertação define-se uma metodologia genérica que
possa atender a ação de transferência de dados de um sistema para outro. Desta forma,
não serão indicadas ferramentas específicas, pois estas decisões são particulares para
cada situação. Como as atividades e problemas de qualquer migração de dados são
bastante parecidos, na definição das atividades da metodologia procurou-se dar
exemplos práticos para melhor entendimento dos objetivos. A maioria dos exemplos
utilizados refere-se ao estudo de caso apresentado nesta dissertação.
Na migração de grandes sistemas legados notam-se muitas dificuldades. Uma
das maiores é a migração de dados. Para muitas atividades da migração de dados, que
devem ser realizadas por técnicos que conheçam a tecnologia e tenham domínio da
aplicação, não existe nenhuma ferramenta específica. A possibilidade de erros é grande
e a utilização de uma metodologia para guiar os passos da migração é muito útil para
que esta não perca seu rumo nem o altere durante o processo.
A metodologia proposta nesta dissertação possui seis grandes etapas:

1. Planejamento;
2. Monitoramento e Controle;
3. Profiling e Auditorias;
   44

4. Construção e Design;
5. Execução; e
6. Testes e Validação dos dados.
   Note-se que a etapa de Monitoramento e Controle irá atuar durante todo o projeto e não
   apenas após a etapa de Planejamento. Ela foi introduzida exatamente com o objetivo de
   acompanhar e gerenciar todas as atividades da metodologia.
   A Figura 36 apresenta as interações entre as etapas da metodologia proposta. Inicia-se
   com a etapa de Planejamento do projeto, seguida da etapa de Profiling e Auditorias que
   irá determinar a qualidade da fonte dos dados. A etapa seguinte é a de Construção e
   Design onde serão construídos os programas para extrair, transformar, carregar e testar
   os dados. Na seqüência, a etapa de Execução marca a entrada da migração dos dados em
   produção. Por fim, a etapa de Testes e Validação dos dados que irá testar e atestar a
   qualidade e o escopo da migração. Gerenciando todas as etapas, durante todo o ciclo de
   vida do projeto, a etapa de Monitoramento e Controle irá garantir os objetivos do
   projeto. Este é o fluxo principal. Fluxos secundários de feedback e de tratamento de
   erros e rejeições também estão representados.

Figura 36 - Interações entre as etapas da metodologia proposta

### 3.1. Planejamento

Como citado anteriormente, um dos requisitos da aplicação da metodologia,
além da migração de dados ser tratada como um projeto à parte, é a existência de um
responsável pela migração de dados: o líder da migração de dados. A indicação do líder
deve ocorrer na fase de iniciação do projeto de migração do sistema legado, pois o
45

processo de migração de dados deve começar no primeiro dia do projeto principal,
evitando assim uma importante causa de atrasos, trabalho refeito e insucesso, que é
deixar a migração de dados para o final do projeto. O líder da migração,
preferencialmente, deve ter as seguintes características:
Técnico experiente da equipe do sistema legado, pois conhece o negócio e os
dados legados. Este conhecimento será fundamental para decisões futuras na
medida em que a essência de um projeto de migração de dados é a fonte dos
dados e como e por que estes estão armazenados;
Capacidade de liderança, pois terá que lidar com conflitos de prioridades entre o
projeto da migração dos dados e o projeto da migração do sistema legado e terá
que manter a equipe motivada e produtiva, mesmo sob pressão, que geralmente
é grande. Precisará negociar com equipes multidisciplinares como banco de
dados, infra-estrutura, suporte técnico, entre outras, e necessitará conduzir e
controlar todas as atividades do projeto de migração de dados;
Condições técnicas de acompanhar a modelagem de dados do sistema alvo.
Característica desejável, pois as opiniões e sugestões de um líder com
conhecimento de causa podem facilitar a migração dos dados, bem como evitar
problemas futuros; e
Bom relacionamento. A capacidade de lidar e conduzir pessoas é desejável em
qualquer líder. Em um projeto de migração de dados, que envolve equipes com
diferentes interesses e prioridades, um bom relacionamento cultivado facilitará
as negociações que serão necessárias para resolver estas diferenças.
Espera-se uma resistência inicial do gerente do projeto e dos líderes das equipes dos
sistemas legado e alvo em deslocar um profissional com o perfil acima para a liderança
da migração. Esta é outra causa de problemas com migração de dados. Precisa-se de um
líder, dedicado ao projeto e experiente.
Devido à complexidade que geralmente envolve o processo de migrar dados de
sistemas legados, a etapa de planejamento é fundamental. Nesta etapa deve-se responder
às seguintes questões:
O que fazer? (Escopo da migração);
Como? (Definir atividades);
Quando? (Definir cronograma);
Onde? (Definir ambientes);
Quem? (Definir equipe);
O que pode dar errado? (Definir riscos);
E se der errado? (Definir contingências); e
Qual o investimento? (Definir custos).
As respostas destas questões e suas implicações estão listadas a seguir em forma
de atividades da etapa de planejamento.

O Quadro 4 apresenta as atividades da etapa de Planejamento.
Quadro 4 Atividades da etapa de Planejamento

#### 3.1.1. Desenvolver o Plano de Migração

O Plano de Migração é o documento de referência que contém as respostas de
todas as questões acima. É a fonte de informação gerada pelos resultados das atividades
de planejamento. À medida que as atividades de planejamento vão se desenvolvendo, o
plano vai sendo construído. É o produto final da etapa de Planejamento. Deve ser
desenvolvido pelo líder da migração auxiliado por todas as partes interessadas,
dependendo da influência delas no plano e nos seus resultados. Por exemplo, área de
suporte técnico, de negócios, de contratos, de recursos humanos, entre outras. Se
algumas decisões a serem tomadas para a definição do plano fugirem da alçada do líder,
estas devem ser levadas para o gerente do projeto. Ressalta-se a importância de mantêlo atualizado durante o projeto, pois o Plano, com os artefatos que o compõem, fornece
documentação importante para consulta e referência, além de formar uma base histórica
para futuros projetos. O plano deve conter:
O escopo da migração de dados;
Os requisitos da migração de dados;
O levantamento dos ambientes legado e alvo;
A arquitetura da migração de dados;
Os requisitos de hardware e software;
As necessidades de aquisições;
A estratégia da migração;
As atividades para a migração;
O seqüenciamento das atividades;
A equipe;
47

As necessidades de treinamento;
As necessidades de contratações;
Os responsáveis pelas atividades;
Os prazos das atividades;
O cronograma;
O levantamento dos riscos;
A mitigação dos riscos;
O plano de contingência;
Os requisitos de qualidade;
O plano de testes e validação dos dados;
O plano de implantação;
Os custos; e
O controle de mudanças.

#### 3.1.2. Definição do escopo da migração

A definição do escopo da migração descreve, em detalhes, as entregas da
migração e o trabalho necessário para criar essas entregas. Também fornece um
entendimento comum do escopo da migração a todas as partes interessadas e descreve
os principais objetivos da migração. A seguir define-se o que um escopo deve conter:
Objetivos da migração
Os objetivos da migração incluem os critérios mensuráveis do sucesso do projeto.
Os projetos podem possuir uma ampla variedade de objetivos técnicos, de negócios,
custo, cronograma e qualidade. Os objetivos mais comuns que devem ser definidos
são:
o Critérios de limite da migração
Deve-se definir o que precisa ser migrado. Geralmente, este critério é
determinado por requisitos legais e operacionais. Avalia-se com o gestor do
negócio quais dados, por força de lei, precisam ser migrados e também quais
dados o sistema alvo precisa para começar a funcionar, como informações
contábeis, financeiras, administrativas, técnicas e operacionais. Os critérios
de limite mais comuns são temporais e de situação. Por exemplo: deve-se
migrar todos os dados legados de janeiro de 2003 até o dia da implantação
do sistema alvo. Ou, deve-se migrar todos os dados legados cuja situação
esteja ativa.
o Critérios quantitativos
Faz-se uma estimativa, baseada no limite da migração, da quantidade de
registros ou linhas que serão migrados. Esta é uma informação importante
para o controle do projeto e para a estimativa de esforço e recursos
necessários como tempo de processamento, hardware, software, equipe,
testes, validação. Esta informação fornece uma noção do tamanho do projeto
e orientará a estratégia da migração. Por exemplo: estima-se que serão
migrados cento e vinte milhões de registros.
o Critérios de aceitação
Estes critérios devem ser quantitativos e qualitativos. Deve-se prever que
alguns registros não serão migrados por razões discutidas adiante. Qual o

percentual de rejeição aceitável? Mesmo migrando 100% dos dados legados,
isto não significa 100% de sucesso. Qual o critério de qualidade do dado
migrado? Estes critérios podem ser particularizados pela importância da
informação. Podem ser definidos critérios por tipo de dados, por tabela e
assim por diante. Por exemplo: aceita-se até 1% como índice de rejeição. Ou,
os dados das contas correntes devem ser 100% migrados. Ou, deve-se
executar o relatório de fechamento de balanço de todos os meses migrados
no sistema fonte e no sistema alvo. Os resultados comparados devem estar
iguais.
o Critérios de cronograma
Define-se uma data limite para a conclusão da migração. Concluir a
migração significa que os critérios de limite e de aceitação foram cumpridos.
Os dados foram migrados e aceitos. O sistema alvo pode entrar em operação
com a qualidade dos dados esperada. Deve-se definir uma data com uma
antecedência segura da data limite de entrada em funcionamento do sistema
alvo. Esta antecedência é uma medida de segurança para o controle dos fatos
imprevistos e atrasos. Esta data será a data limite do cronograma da
migração dos dados.
o Critérios de custos
Esta é uma restrição financeira imposta pelo patrocinador do projeto ou pelo
departamento financeiro. Deve-se estimar o custo do projeto e o orçamento
disponível para detectar-se logo no início do projeto a necessidade de
alocação de mais recursos financeiros. O detalhamento do custo deve ser
feito em etapa mais adiante.
Descrição do escopo
Descreve as características da migração. Fornece um resumo do propósito do projeto
de migração. A descrição poderá ser mais detalhada à medida que se tiverem mais
informações do projeto. Por exemplo: este projeto de migração propõe-se a extrair
os dados do sistema legado Fronteiras, a partir de 01/01/2003, transformá-los
segundo as regras de mapeamento definidas, carregá-los nas tabelas do sistema
CMT do Projeto E - Fisco, validá-los e corrigi-los até atingir-se os critérios
definidos de qualidade dos dados migrados. Esta migração deverá estar concluída
até 30/10/2007.
Requisitos da migração
Descreve as condições ou capacidades que devem ser atendidas ou possuídas pelas
entregas da migração. As análises das partes interessadas, de todas as suas
necessidades, desejos e expectativas são convertidas em requisitos priorizados.
Além dos requisitos de negócio, é importante deixar definidos alguns requisitos
técnicos sempre presentes em grandes migrações de dados:
o Requisitos de integração com outros sistemas
Sistemas freqüentemente integram-se com outros sistemas. Se esta
integração traduzir-se em integridades referenciais em nível de SGBD, é
fundamental que fique clara esta dependência e a impossibilidade de migrarse dados que não satisfaçam à condição. Por exemplo: no estudo de caso

necessita-se que, antes da carga dos dados do sistema CMT, os processos de
débitos fiscais do sistema GPF estejam carregados.
o Requisitos de ambiente
Se for definido que o projeto usará ambientes intermediários como ambiente
de desenvolvimento ou ambiente paralelo ou ambiente de testes, estes
ambientes devem estar operacionais.
o Requisitos de validação e teste
Os dados migrados serão validados e testados segundo os critérios de
qualidade definidos. Uma das validações mais importantes acontece
testando-se funcionalidades, rotinas, relatórios do sistema alvo com os dados
migrados e comparando-os com os do sistema fonte. Para possibilitar tais
testes, os processos do sistema alvo devem estar operacionais na ocasião. Por
exemplo: precisa-se do serviço do cálculo de juros pro-rata e dos relatórios
de arrecadação por data e apropriação por data, operacionais, para a
validação de dados financeiros.
o Requisitos de hardware e software
É necessário que sejam levantadas e explicitadas as necessidades de
hardware e software para o sucesso do projeto. Baseando-se na necessidade
de processamento e armazenamento, o suporte técnico da organização deve
ser envolvido na avaliação do hardware disponível para que se evitem
surpresas durante o projeto. Deve-se avaliar a necessidade e adequação de
aquisição de software de apoio a determinadas atividades da migração como
gerenciamento do projeto, mapeamento e profiling dos dados.
Estratégia da migração
Quando se decide migrar dados de um sistema para outro, faz mais sentido fazê-lo
de uma só vez ou mover dados em fases controladas com múltiplas iterações?
Naturalmente existirão prós e contras em ambas as opções. Um fator decisivo é o
tempo que a migração irá consumir. Porém, neste ponto do projeto, é improvável
que esta variável seja confiável. É recomendável, o quanto antes, se ter fatos, como
a extração e carga de uma amostra dos dados, para obter-se uma noção mais apurada
do tempo envolvido. Considerar qual abordagem será a mais adequada para
determinada organização requer avaliar uma variedade de fatores. Alguns exemplos
destes fatores são:
o Qual a quantidade de dados que vai ser migrada?
o Quanto tempo isto levará levando em consideração as condições normais
de processamento em produção da organização?
o Quanto tempo a organização suporta parar os sistemas para a migração?
o Qual a complexidade de transformação dos dados?
o A organização tem condições de simular um Big Bang antes da migração
definitiva? e
o É possível estimar o ROI (acrônimo em inglês para Retorno do
Investimento) de ambas as abordagens?
Avaliados estes e outros fatores que a organização achar necessário, deve-se definir
um passo-a-passo, sem aprofundamento das atividades, de como a migração

ocorrerá. Note-se que neste ponto se está definindo se a migração transcorrerá de
uma só vez ou em ciclos. Se será necessário sincronismo entre os sistemas legado e
alvo. Se começará dos dados mais antigos ou mais modernos. Não se está
considerando as atividades de levantamento, mapeamento dos dados e construção de
programas, pois estas são comuns a ambas as estratégias. Atém-se às atividades de
extração, transformação, carga e validação dos dados. Um exemplo baseado no
estudo de caso:
o Os dados serão migrados em ciclos iterativos (Estratégia Trickle);
o A extração dos dados começará pelos dados mais antigos, ou seja, a
partir de 01/01/2003;
o Um ciclo de migração corresponde às atividades de extração,
transformação, carga e validação dos dados de um determinado mês;
o As tabelas de domínio devem ser migradas no início da migração;
o As tabelas de movimento devem ser migradas em ciclos de migração;
o O sistema legado continuará em operação durante a migração;
o As atividades de extração, carga serão realizadas no horário das 00:00h
às 06:00h, pois é o horário disponível no ambiente de produção legado e
alvo;
o Haverá a necessidade de sincronismo no sentido do sistema fonte para o
alvo;
o Ao final de cada ciclo o sistema alvo será liberado para a validação dos
dados pelos usuários;
o Ao final de cada ciclo será liberado relatório de rejeições para ser tratado
pelos usuários e equipe da migração; e
o Ao final de cada ciclo serão avaliados e corrigidos os erros e problemas
ocorridos;
Entregas da migração
As entregas são as saídas ou resultados intermediários que devem ser declarados no
escopo da migração. De acordo com o estilo do escopo, as entregas podem ser
descritas de forma sumarizada ou detalhada. Como exemplos de entregas pode-se
ter:
o Modelo de dados do sistema fonte;
o Dicionário de dados do sistema fonte;
o Mapeamento dos dados;
o Programas de extração, transformação e carga;
o Relatórios de carga de dados;
o Relatórios de rejeição de dados; e
o Relatório de conclusão da migração.
Restrições da migração
Restrições são limites externos impostos ao projeto da migração dos dados.
Geralmente são prazos legais, cláusulas contratuais, fatores orçamentários ou
técnicos. Se alguma restrição existir, deve ser listada. Exemplo: um novo sistema
que dará suporte a uma eleição terá que estar totalmente operacional até a data da
eleição. Portanto, neste exemplo, tem-se uma restrição de prazo.

Organização inicial do projeto
São identificados os membros da equipe da migração, o(s) responsável(eis) pelas
regras de negócio e histórico dos dados fonte do lado do cliente, e o(s)
responsável(eis) pelos testes e validação dos dados do lado do cliente. Também os
técnicos, que darão suporte ao projeto, da equipe de banco de dados e do sistema
alvo. Não é indicado que seja o próprio gerente do projeto o responsável pela
migração dos dados. O tamanho da equipe varia de acordo com o porte da migração.
Para projetos de grande porte, de alta complexidade, sugere-se uma equipe formada
pelo líder, dois analistas de sistemas e três desenvolvedores, assim alocados: o líder
coordenando as ações da equipe, um analista de sistemas para o sistema fonte, um
analista de sistemas para o sistema alvo e os três desenvolvedores atendendo às
demandas dos analistas de sistemas de acordo com a disponibilidade. É fundamental
que pelo menos um dos analistas de sistemas e um dos desenvolvedores domine a
tecnologia do sistema fonte.
Riscos iniciais definidos
Definem-se os riscos já conhecidos. Esta definição servirá como diretriz para o
levantamento, qualificação, quantificação e mitigação dos riscos e plano de
contingência realizados mais adiante. Pode-se listar riscos clássicos já conhecidos
em projetos de migração de dados:
o Falha ao tratar migração de dados como um projeto em si próprio
Este é um risco sempre presente. Será mínimo se a metodologia proposta
for seguida;
o Subestimar o tempo e o custo da migração de dados
É importante realizar uma diligente pesquisa no sistema fonte a fim de
determinar a qualidade da documentação e da fonte dos dados. Se o
sistema fonte não possuir documentação de dados atualizada na forma de
modelos de dados e dicionário de dados, a tarefa de determinar a
estrutura e o tipo dos dados da fonte de dados desejada e o seu
mapeamento para os dados alvo deverá ser levada em consideração na
estimativa de custo e tempo. Se o sistema fonte é menos exigente nos
requerimentos de qualidade de dados que o sistema alvo ou se a
qualidade dos dados do sistema fonte tem permitido falhas ao longo do
tempo, tem-se que considerar um custo e tempo extras para a tarefa de
limpeza dos dados na extração ou após a migração;
o Deficiência no estado final da qualidade dos dados
Se o esforço de migração não especificar formalmente o nível desejado
da qualidade dos dados e um conjunto de testes de controle para verificálos, o domínio alvo pode ser carregado com dados de qualidade duvidosa.
Isto irá impactar negativamente a percepção externa do esforço do
desenvolvimento; e
o Falha ao obter o suporte organizacional
Quando a complexidade e importância da migração dos dados não são
adequadamente apreciadas, fica difícil mobilizar o suporte organizacional
para esta migração, principalmente em termos financeiros e de recursos.
Pode-se até ter mais dificuldades de conseguir um bom nível de suporte

organizacional se a equipe que mantém o sistema fonte se sentir
ameaçada pelo novo sistema ou, simplesmente, porque o esforço de
migração não é a prioridade principal da organização para aquele projeto.
Marcos do cronograma
O cliente ou a organização executora podem identificar marcos e colocar datas
impostas nesses marcos do cronograma. Essas datas podem ser consideradas como
restrições do cronograma.
O escopo da migração pode ser alterado à medida que o projeto segue e surgem
requisitos, restrições, riscos, entre outros, não previstos. Estas mudanças devem ser
criteriosas e submetidas à aprovação do gerente do projeto, do líder da migração e das
partes interessadas.

#### 3.1.3. Identificação dos ambientes atual e futuro

Segundo Garlan, os grandes problemas no desenvolvimento de grandes
sistemas de informação são a organização, em um alto nível, dos elementos
computacionais e a interação entre eles. Exemplos destes elementos são: protocolos de
comunicação, sincronização e acesso de dados; distribuição física dos sistemas e dados,
modelo de dados, linguagens de programação, SGBD, métodos de modelagem do
sistema, mediadores de comunicação entre aplicações e os SGBD, escalabilidade e
desempenho. Geralmente, em um sistema legado de grande porte, a interação entre estes
elementos não funciona perfeitamente, sendo um risco a ser considerado pela equipe de
migração.
Apesar de o foco de um projeto de migração de dados ser a transferência dos
mesmos do ambiente fonte para o ambiente alvo, a equipe de migração deve ter
conhecimento, embora sem necessidade de aprofundamento, dos dois ambientes em
questão, pois irá interagir com ambos. Dentre os elementos acima, citados por Garlan
, deve-se ter particular atenção com os seguintes:
o
o
o
o
o
o
o
o

Plataforma de hardware;
Sistema Operacional;
Modelos de dados;
Ferramentas de modelagem de dados utilizadas;
SGBD;
Utilitários do SGBD utilizados;
Linguagens de programação utilizadas; e
Ambiente de desenvolvimento integrado utilizado.

Com estes elementos conhecidos é possível se ter uma visão geral dos ambientes
envolvidos e montar uma equipe com competência para atuar nestes cenários. Pode-se
acrescentar outros elementos que se façam necessários, particularizando a definição.

#### 3.1.4. Definição da arquitetura da migração

Durante o processo de migração dos dados, haverá a necessidade de se
desenvolver programas de auditoria, extração, transformação, carga e validação dos

dados, além da instalação de ferramentas de suporte. Deve-se decidir se esse ferramental
ficará em ambiente ou camada independente ou se será absorvido pelos ambientes fonte
e alvo. Conforme discutido no Capítulo 2, existem prós e contras para ambas as opções.

#### 3.1.5. Definição das atividades da migração

A lista de atividades da migração é abrangente, incluindo todas as atividades do
cronograma planejadas para serem realizadas no projeto. Deve conter o identificador da
atividade, uma descrição, o escopo do trabalho para cada atividade suficientemente
detalhado para garantir que os membros da equipe do projeto a compreendam,
atividades predecessoras, atividades sucessoras, recursos necessários, datas impostas,
prazo previsto de entrega, data de início, restrições e premissas. Pode também incluir a
pessoa responsável pela execução do trabalho e a complexidade da atividade. Deve
identificar se a atividade é um marco e se o marco é obrigatório (exigido pelo contrato)
ou opcional (com base em requisitos do projeto ou em informações históricas). A lista
de atividades será a base do cronograma da migração. Pode ser apresentada em forma
de tabela ou relatório. Existem vários aplicativos no mercado que auxiliam esta tarefa,
como o Microsoft® Office Project Professional 2003 ou o OpenProj da
Projity®.
Para organizar melhor a lista e facilitar o trabalho de determinar as atividades,
deve-se seguir o roteiro das atividades propostas nesta metodologia. Se necessário for,
pode-se desmembrar uma atividade em várias atividades mais específicas. O Quadro 5
apresenta um exemplo da atividade de Construir o modelo de dados do sistema fonte da
etapa de Profiling e Auditorias em forma de Lista de Atividades.
Quadro 5 Exemplo de uma atividade da Lista de Atividades

#### 3.1.6. Seqüenciamento das atividades da migração

Tarefa necessária para determinar as dependências entre atividades e possibilitar
uma melhor administração do cronograma e priorização de recursos. Caso seja utilizado
54

software de gerenciamento de projetos para listar as atividades e construir o
cronograma, esta tarefa é bem apoiada pelo mesmo.

#### 3.1.7. Estimativa de recursos da atividade

É a identificação e a descrição dos tipos (pessoas, equipamentos e material) e
quantidades de recursos necessários para cada atividade. A confecção desta estimativa,
baseada na lista de atividades, é a base da estimativa de custos do projeto. Também
determina a necessidade de aquisições e contratações. Se os recursos, principalmente
pessoal, estão escassos ou compartilhados, um calendário de recursos com as
disponibilidades pode ajudar na melhor utilização destes recursos. O Quadro 6 mostra
um exemplo de Estimativa de recursos de uma atividade proposta por esta metodologia.
Quadro 6 - Exemplo de Estimativa de recursos de uma atividade

#### 3.1.8. Desenvolvimento do cronograma

O desenvolvimento do cronograma da migração, um processo iterativo,
determina as datas de início e término planejadas das atividades. Constrói-se baseado na
lista de atividades. O desenvolvimento do cronograma continua durante todo o projeto,
conforme o trabalho se desenvolve. Um projeto de migração típico tem uma duração
média de seis meses a dois anos com uma equipe de cinco desenvolvedores em tempo
integral. O cronograma do projeto pode ser apresentado de forma
sumarizada, às vezes chamado de cronograma mestre ou cronograma de marcos, ou
apresentado em detalhes. Embora um cronograma do projeto possa ser apresentado na
forma tabular, ele é mais freqüentemente apresentado de forma gráfica, usando software
de gerenciamento de projetos. A Figura 37 mostra alguns exemplos gráficos para um
cronograma de um projeto.

Figura 37 - Cronograma do projeto exemplos gráficos.
Fonte: Guia PMBOK.

#### 3.1.9. Estimativa de custos

A estimativa de custos envolve o desenvolvimento de uma aproximação dos
custos dos recursos necessários para terminar cada atividade do cronograma. Baseia-se
na estimativa de recursos da atividade. Os custos das atividades do cronograma são
56

estimados para todos os recursos cujos custos serão lançados no projeto. Isso inclui, mas
não se limita, a mão-de-obra, materiais, equipamentos, serviços e instalações, além de
categorias especiais como uma provisão para inflação ou um custo de contingência. A
estimativa de custos de uma atividade do cronograma é uma avaliação quantitativa dos
custos prováveis dos recursos necessários para terminar a atividade do cronograma.
Deve transformar em valores financeiros as quantidades da estimativa de recursos da
atividade.

3.1.10. Planejamento da qualidade
O planejamento da qualidade descreve esforços para que os critérios de
qualidade, definidos no objetivo da migração, sejam atingidos. Estes esforços
constituem-se em se analisar os critérios de qualidade definidos e incorporá-los às
atividades do projeto. O principal foco é a qualidade dos dados migrados. A baixa
qualidade desses dados compromete a percepção do sucesso da empreitada. Se métricas
de qualidade não ficaram claras na definição do objetivo, este é o momento de definilas. As métricas mais comumente usadas em projetos de migração de dados são
percentuais aceitos de rejeição de dados, percentuais aceitos de erros ao se comparar
rotinas no sistema fonte com rotinas no sistema alvo, percentuais aceitos de erros de
conteúdo de atributos dos dados. As métricas de qualidade devem ser metas a serem
atingidas pelas atividades de migração.
A etapa de Profiling e Auditorias, definida no tópico 3.3, revela a qualidade da fonte
dos dados, gerando subsídios para o cumprimento das metas de qualidade. Algumas
atividades descritas adiante nesta metodologia devem ser ajustadas para o cumprimento
dos critérios de aceitação e qualidade definidos. O Planejamento da qualidade deve estar
orientando estes ajustes. As atividades são:

#### 3.4.1. Definição das regras de limpeza dos dados;

#### 3.4.2. Construção do mapa de dados;

#### 3.4.9. Teste da migração dos dados;

#### 3.5.4. Tratamento das rejeições de dados;

#### 3.6.1. Testes unitários;

#### 3.6.2. Testes de carga; e

#### 3.6.3. Testes de sistema.

3.1.11. Definição das comunicações
Determina as necessidades de informação e de comunicação das partes
interessadas no projeto. Deve-se estabelecer a forma que as partes interessadas tomarão
ciência do andamento, mudanças e novos requisitos do projeto, entre outros. A forma
dependerá do porte do projeto, da quantidade de envolvidos, da distribuição geográfica.
Geralmente, é feita em reuniões periódicas e relatórios de acompanhamento.

3.1.12. Identificação de riscos
O risco no projeto é um evento ou condição incerta que, se ocorrer, terá um
efeito positivo ou negativo sobre pelo menos um objetivo do projeto, como tempo,
custo, escopo ou qualidade. Um risco pode ter uma ou mais causas e, se ocorrer, um ou
57

mais impactos. O risco do projeto se origina da incerteza que está presente em todos os
projetos. As pessoas e, por extensão, as organizações tomam atitudes em relação aos
riscos que afetam a exatidão da percepção desses riscos e a forma como respondem a
eles. As atitudes em relação aos riscos devem ser explicitadas sempre que possível.
Uma abordagem de risco consistente que atenda aos requisitos da organização
deve ser desenvolvida para cada projeto, e a comunicação do risco e o seu tratamento
devem ser abertos e transparentes. As respostas a riscos refletem o equilíbrio entre
enfrentar riscos e evitar riscos considerados por uma organização.
A identificação de riscos determina os riscos que podem afetar o projeto e
documenta suas características. Os participantes das atividades de identificação de
riscos podem incluir os seguintes, quando adequado: gerente de projetos, membros da
equipe de migração, especialistas no assunto de fora da equipe de migração, clientes,
usuários finais, outros gerentes de projetos e partes interessadas. Embora esse pessoal
seja muitas vezes constituído pelos principais participantes da identificação de riscos,
todo o pessoal do projeto deve ser incentivado a identificar riscos.
A identificação de riscos é um processo iterativo porque novos riscos podem ser
conhecidos conforme o projeto se desenvolve durante todo o seu ciclo de vida. Com
urgência de tempo prioriza-se o levantamento dos riscos com impacto negativo. Estes
atingem, geralmente, os objetivos de prazo, custo, escopo e qualidade do projeto. Uma
boa técnica para identificá-los é analisar o que pode impactar negativamente estes
objetivos.
A lista dos riscos identificados deve conter:
o
o
o
o

Identificador do risco;
Descrição do risco;
Respostas ao risco; e
Causa do risco.

O Quadro 7 apresenta um exemplo de risco negativo para o cronograma, identificado no
estudo de caso deste trabalho, apresentado na Lista de Riscos Identificados.
Quadro 7 Exemplo de Lista de riscos identificados

3.1.13. Análise qualitativa dos riscos
A análise qualitativa de riscos avalia a prioridade dos riscos identificados usando
a probabilidade deles ocorrerem, o impacto correspondente nos objetivos do projeto se
os riscos realmente ocorrerem, além de outros fatores, como o prazo e tolerância a risco
das restrições de custo, cronograma, escopo e qualidade do projeto. A análise qualitativa
de riscos é normalmente uma maneira rápida e econômica de estabelecer prioridades
para o planejamento de respostas a riscos. A escala de probabilidade e impacto deve ser

definida. Pode ser numérica (1, 2, 3...) ou categorizada (alto, médio, baixo...). O
importante é que o seu significado fique claro para os envolvidos. Pode-se acrescentar
as informações de probabilidade do risco acontecer e impacto sobre o projeto na lista de
riscos identificados. Assim, têm-se todas as informações em um só lugar. O Quadro 8
mostra o exemplo apresentado no Quadro 7 com a análise qualitativa.
Quadro 8 Exemplo de Lista de riscos identificados com a análise qualitativa

A análise qualitativa viabiliza a identificação dos riscos prioritários que devem
estar sob monitoramento constante. Também permite agrupar os riscos por categoria e
selecionar os que exigem respostas em curto prazo.

3.1.14. Definir necessidade de compras e aquisições
A metodologia identifica quais necessidades da migração podem ser mais bem
atendidas pela compra ou aquisição de produtos, serviços ou resultados fora da
organização do projeto e quais necessidades da migração podem ser realizadas pela
equipe da migração durante a execução do projeto. Esse processo envolve a
consideração de como, o que, quanto, se e quando adquirir. Também inclui a
consideração de possíveis fornecedores, especialmente se o comprador desejar exercer
algum grau de influência ou controle sobre as decisões de contratação.
Não se deve relevar o risco envolvido na decisão de comprar ou contratar. A
decisão pode trazer impactos negativos nos objetivos de escopo, custo, cronograma e
qualidade. Em projetos de migração, aplicativos de gerenciamento de projeto e de
mapeamento de dados são compras ou aquisições que podem ser consideradas. As
ferramentas comerciais para fazer o mapeamento dos dados não são do tipo plug&play.
Algumas se propõem a fazer o mapeamento entre alguns sistemas de bancos de dados,
mas exigem um trabalho muito grande de configuração, principalmente em relação à
semântica dos dados.

3.1.15. Definir necessidades de recursos humanos
Baseando-se na equipe da migração definida e no pessoal disponível, pode surgir
a necessidade de contratação de pessoal. Além disto, pode-se necessitar de serviços
especializados ou de consultorias. As contratações de pessoal também se constituem em
riscos que devem ser considerados. O atraso nas contratações pode atrasar o projeto. A
qualidade das contratações pode comprometer a qualidade do projeto, assim como o
custo.

3.1.16. Plano de testes e validação
É sabido que dados nos sistemas fonte geralmente contêm problemas ou
escondem erros causados pelas mais variadas causas, desde falhas humanas até regras e
validações mal testadas ou definidas em sistemas pouco sofisticados. Regras de
validação devem ser utilizadas como primeiro passo para tentar identificar e corrigir
estes problemas estendendo o processo em tantas iterações quantas forem necessárias.
Elas serão utilizadas na etapa de auditoria dos dados. É comum que alguns tipos de
erros não apareçam até que outros tipos sejam detectados e corrigidos. Somando-se a
isto, testes unitários, de sistema e de carga devem ser feitos para garantir que todos os
dados foram migrados e que o novo sistema se comporta como esperado. As regras de
validação devem ser definidas para serem usadas antes e depois da migração. Antes, na
auditoria dos dados fonte. Depois, na validação da migração.
O plano de testes e validação deve definir:
o O que será validado;
o Onde as regras de validação irão atuar (Extração, Transformação ou
Carga);
o As saídas da validação (relatórios, planilhas, logs, entre outros);
o O tratamento dos erros de validação;
o Os testes unitários; e
o Os testes de sistema alvo.

3.1.17. Plano de implantação
Seja qual for a estratégia de migração escolhida, de uma só vez ou em ciclos,
existirá um momento no qual o sistema fonte deixa de operar e o sistema alvo entra em
operação. Para que esta transição ocorra sem transtornos, é preciso que algumas
atividades sejam definidas. Estas atividades são de encerramento do sistema fonte e
iniciação do sistema alvo. As principais atividades, no tocante à migração de dados, são
relacionadas a:
Backup;
Verificações e testes parciais;
Último sincronismo;
Atualização de dados de controle (totalizadores, seqüências, entre
outros); e
o Testes finais do sistema alvo.
o
o
o
o

Estas atividades devem ocorrer com os sistemas inoperantes para os usuários.
Geralmente, em um fim-de-semana ou feriado.

3.1.18. Plano de contingência
Um plano de contingência deve prever ações para serem tomadas quando o que
foi planejado falhar.
Recomenda-se que em migrações de grande porte tenha-se um ambiente paralelo
onde a migração possa ser testada. Se a quantidade de dados e o tempo permitirem,
60

deve-se fazer toda a migração e validação nesse ambiente para, finalmente, fazê-la em
produção. Este cenário, na maioria dos casos, não é viável. Testam-se apenas amostras
dos dados.
Em muitas situações, o ambiente de produção abriga vários sistemas integrados
com suporte em único SGBD. Nestes casos, uma falha na carga dos dados migrados não
pode ser corrigida automaticamente pelo SGBD com um procedimento de rollback, pois
afetaria todos os outros sistemas.
Um plano de contingência deve atuar considerando as principais falhas que
podem acontecer. Deve definir atividades que possibilitem retornar a uma situação de
integridade, se problemas ocorrerem. Geralmente, estas atividades envolvem a
construção de programas e scripts, que, se tudo der certo, nunca serão usados. O
impacto no prazo e no custo da migração, se o plano de contingência for acionado, deve
ser conhecido por todas as partes interessadas. Principalmente os usuários do sistema
alvo e patrocinadores do projeto.

### 3.2. Monitoramento e Controle

As atividades de monitoramento e controle são realizadas para observar a
execução do projeto de migração, de forma que possíveis problemas possam ser
identificados no momento adequado e que possam ser tomadas ações corretivas, quando
necessário, para controlar a execução do projeto. Tais atividades desenvolvem-se
paralelamente às demais atividades das outras etapas do projeto de migração. Elas
devem ser do conhecimento de todos os envolvidos, mas o principal responsável pela
sua execução é o líder da migração.
O Quadro 9 abaixo mostra as atividades da etapa de Monitoramento e Controle.
Quadro 9 Atividades da etapa de Monitoramento e Controle

#### 3.2.1. Controle de mudanças

Controla os fatores que criam mudanças para garantir que estas sejam benéficas,
determina se ocorreu uma mudança e gerencia as que foram aprovadas, inclusive o
momento no qual ocorrem. O controle de mudanças é necessário porque raramente a
execução dos projetos segue com exatidão o plano de migração. Especial atenção deve
ser dada para as mudanças que afetam escopo, cronograma, qualidade e custos do
projeto.

#### 3.2.2. Verificação do escopo

Formaliza a aceitação das entregas do projeto de migração terminadas. A
verificação do escopo do projeto inclui a revisão das entregas para garantir que cada
uma delas foi terminada de forma satisfatória.
A verificação do escopo difere do controle da qualidade porque trata
principalmente da aceitação das entregas, enquanto o controle da qualidade trata
principalmente do atendimento aos requisitos de qualidade especificados para as
entregas. Em geral, o controle da qualidade é realizado antes da verificação do escopo,
mas esses dois processos podem ser realizados em paralelo.
As entregas terminadas que não foram aceitas são documentadas, juntamente
com as razões da não aceitação.

#### 3.2.3. Controle do cronograma

Esta é a atividade necessária para controlar as mudanças feitas no cronograma do
projeto. O controle do cronograma está relacionado a:
Determinação do andamento atual do cronograma do projeto;
Controle dos fatores que criam mudanças no cronograma; e
Determinação de que o cronograma do projeto mudou.

#### 3.2.4. Controle de custos

É a atividade de influenciar os fatores que criam as variações e controlar as
mudanças no orçamento do projeto. O controle de custos do projeto inclui:
Controlar os fatores que criam mudanças na linha de base dos custos;
Monitorar as mudanças reais, quando e conforme ocorrem;
Evitar que mudanças incorretas, inadequadas ou não aprovadas sejam incluídas
nos custos relatados ou na utilização de recursos; e
Agir para manter os estouros nos custos esperados dentro dos limites aceitáveis.

#### 3.2.5. Realizar o controle da qualidade

Monitora resultados específicos do projeto a fim de determinar se eles estão de
acordo com os padrões relevantes de qualidade e identifica maneiras de eliminar as
causas de um desempenho insatisfatório. Deve ser realizado durante todo o projeto.

#### 3.2.6. Gerenciar a equipe do projeto

Acompanha o desempenho de membros da equipe, fornece feedback, resolve
problemas e coordena mudanças para melhorar o desempenho do projeto.

#### 3.2.7. Monitoramento e controle de riscos

Acompanha os riscos identificados, monitora os riscos residuais, identifica novos riscos,
executa planos de respostas a riscos e avalia sua eficiência durante todo o ciclo de vida
do projeto.

### 3.3. Profiling e Auditorias

Esta é uma das etapas mais importantes de um projeto de migração de dados.
Como requer bastante esforço, é raro vê-la presente nos processos de migração de dados.
Mas o esforço é recompensado, pois é bem menor que o trabalho refeito na etapa de
testes e validação dos dados.
Quando dados são migrados para um novo sistema, pode ficar aparente que eles
contêm redundâncias e imprecisões. Enquanto que estes dados são perfeitamente
adequados para o funcionamento do sistema original, eles podem não ser adequados em
termos de estrutura e conteúdo para a nova aplicação. Sem o entendimento
suficiente de ambos os sistemas, a transferência de dados de um para o outro pode
ampliar o impacto negativo de qualquer dado incorreto ou irrelevante.
Para desenvolver-se um projeto de migração de dados eficaz, é importante
entender por completo as fontes de dados antes de especificar o código de migração.
Isto é melhor alcançado através da realização de uma auditoria completa dos dados que
fazem parte do escopo da migração nos estágios iniciais do projeto. Os benefícios
trazidos por esta prática são:
Com uma visibilidade completa de todos os dados de origem, a equipe pode
identificar potenciais problemas que permaneceriam escondidos até um estágio
mais avançado do projeto;
As regras para planejamento, mapeamento, execução e teste da migração são
baseadas na análise de todos os dados de origem em vez de uma pequena
amostra;
As decisões podem ser realizadas baseadas em fatos em vez de suposições; e
Uma auditoria completa dos dados pode reduzir o custo de reparos no código na
etapa de testes.
Quando a migração de dados é deixada para o fim do projeto principal, os dados
fonte não foram levados em consideração na construção da nova base de dados e tal fato
é motivo de grandes problemas. Ao tratar-se migração de dados desde o início do
projeto principal, tem-se a oportunidade de construir a nova base de dados com um
conhecimento prévio da fonte dos dados. Portanto, conhecer a fonte dos dados é
condição para o sucesso de um projeto de migração de dados. O Quadro 10 abaixo
apresenta as atividades da etapa de Profiling e Auditorias.

Quadro 10 Atividades da etapa de Profiling e Auditorias.

#### 3.3.1. Construir ou atualizar o modelo de dados do sistema fonte

Se esta atividade não estiver definida no projeto principal, e geralmente não está,
a equipe de migração deverá desenvolvê-la. É incomum encontrar-se uma boa
documentação de sistemas legados. Pelo exposto no Capítulo 2, o corriqueiro é que as
melhores fontes de informação sejam os técnicos e usuários do sistema e o código fonte
dos programas. Construir ou atualizar o modelo de dados do sistema fonte é a atividade
inicial desta etapa e o começo do contato da equipe de migração com os dados fonte.
Deve-se usar a ferramenta de modelagem definida para o sistema alvo, pois facilitará o
mapeamento. Dependendo da tecnologia de armazenamento do sistema fonte e da
ferramenta de modelagem utilizada, alguma técnica de engenharia reversa pode acelerar
o processo. A atividade exigirá a participação de um técnico com conhecimento do
sistema fonte.

#### 3.3.2. Construir ou atualizar o dicionário de dados do sistema fonte

Se esta atividade não estiver definida no projeto principal, e geralmente não está,
a equipe de migração deverá desenvolvê-la. Esta atividade é fundamental para o
mapeamento dos dados entre o sistema fonte e o sistema alvo e a definição de regras de
auditoria e validação. Muitas vezes não existe a relação direta entre o tipo de dados
fonte e o tipo de dados alvo. Por exemplo, o tipo numeric da tecnologia fonte pode ser
incompatível com o tipo integer da tecnologia alvo. Devido a estas possíveis
incompatibilidades, a dicionarização deve prestar bastante atenção ao conteúdo
verificando o que está descrito no metadados. Para o propósito de migração de dados, a
informação que descreve a origem (e.g. o nome da base de dados, o nome da tabela, o
nome da coluna) e as características de cada coluna (e.g. o tipo, o tamanho, a escala, a
precisão) é considerada metadados. Conteúdo é o que está contido em cada registro da
coluna. Uma migração de dados orientada a metadados assume que o conteúdo reflete a
sua descrição, o que nem sempre acontece nos sistemas legados. Este cuidado evita
muitas rejeições de registros. O dicionário deve conter, no mínimo, as seguintes
informações:

Nome do campo;
Tipo;
Tamanho;
Valores de domínio;
Regras de sistema;
Verificações de integridade;
Escala;
Precisão;
Unicidade;
Nulidade;
Descrição do conteúdo; e
Semântica do dado.

#### 3.3.3. Construir o modelo de dados do sistema alvo

Esta é uma atividade da equipe de desenvolvimento do sistema alvo. Está listada
como uma atividade da metodologia, pois é importante que a equipe de migração possa
acompanhá-la e emitir opinião. Se não for possível, a equipe de migração deve ter
acesso ao modelo de dados e recomenda-se que possa fazer solicitações de mudança.
Isto é mais plausível quando a equipe de migração integra-se ao projeto principal logo
no início. Depois que a base de dados e o sistema alvo estão construídos, qualquer
solicitação de mudança de dados é vista como um risco alto.

#### 3.3.4. Construir o dicionário de dados do sistema alvo

Assim como a anterior, é uma atividade da equipe de desenvolvimento do
sistema alvo. Também está listada como uma atividade da metodologia, pois é
importante que a equipe de migração possa acompanhá-la. Geralmente as ferramentas
de modelagem dão suporte à atividade de dicionarização, a qual é uma atividade
fundamental para o mapeamento dos dados. A equipe da migração também deve estar
familiarizada em como os dados devem ser armazenados no sistema alvo.

#### 3.3.5. Definir o profiling

Baseando-se nas validações requeridas descritas no plano de testes e validação
da etapa de planejamento e com o conhecimento adquirido nas atividades anteriores,
define-se o que se deseja auditar. Quanto maior o período entre o início e o fim
definidos como limites da migração, maior a probabilidade de se detectar problemas.
Como roteiro da auditoria, deve-se começar com as verificações mais simples. As mais
usuais são:
Verificação de unicidade e nulidade para campos candidatos à chave primária;
Verificação de integridade referencial para campos candidatos à chave
estrangeira;
Verificação de formato de data e hora;
Verificação de redundâncias;
65

Verificação de campos que serão decompostos no sistema alvo. Por exemplo, o
campo endereço do sistema fonte será decomposto em logradouro, número,
complemento, bairro, cidade, estado e CEP no sistema alvo. Os campos cidade
e estado são chave estrangeira e o campo CEP é obrigatório no sistema alvo; e
Verificação de regras de integridade. Por exemplo, em um sistema de controle
de empréstimos, se todas as parcelas do empréstimo estiverem pagas em dia, o
saldo devedor do empréstimo deve estar zerado.
A auditoria irá revelar em que nível de qualidade os dados fonte se encontram.
Mostrará a quantidade de dados que precisarão de alguma limpeza ou intervenção para
que possam ser migrados. E dará subsídios ao gestor para decidir o que não deve ser
migrado.

#### 3.3.6. Verificar a possibilidade de aquisição de ferramenta de

profiling
Existem algumas ferramentas comerciais que se propõem a fazer o trabalho de
auditoria dos dados. Deve-se analisar a adequação de alguma ferramenta ao caso
específico. São construídas para determinados bancos de dados e o trabalho de
configuração é grande. Algumas se baseiam no modelo de dados exportado em algum
formato padrão, como XMI. A aquisição de ferramenta específica pode
poupar esforços de construção de programas. O que ocorre é que as plataformas de
sistemas legados geralmente são proprietárias e as ferramentas precisam ser bem
específicas para tais plataformas.

#### 3.3.7. Construir os programas de auditoria

Esta atividade visa a materializar as definições da Seção 3.3.5. É executada pelos
desenvolvedores da equipe de migração. Se existir um ambiente de desenvolvimento ou
teste do sistema fonte, deve ser usado para os testes da auditoria. Para toda rotina de
auditoria deve ser especificado um resultado, na forma de arquivos, relatórios ou
planilhas, para servir de insumo para a atividade descrita na Seção 3.3.9.

#### 3.3.8. Realizar o profiling nos dados fonte

De posse da definição da forma e conteúdo dos dados fonte, cabe testar se
fisicamente os dados correspondem ao previsto. Um processo de auditoria de dados
consome muitos recursos do ambiente computacional de produção da organização. A
forma de realização da auditoria dependerá de alguns fatores, como:
Quantidade de dados a serem auditados;
Tempo de processamento para as rotinas de auditoria; e
Disponibilidade da máquina de produção.
De acordo com estes fatores, pode-se definir ciclos de auditoria compatíveis com
a disponibilidade do ambiente computacional. Estes ciclos podem ser limitados por

período, quantidade de registros, arquivo, tabela, entre outros. É fundamental que se
tenha o controle do que já foi auditado e o que falta ser feito.

#### 3.3.9. Análise dos resultados do profiling e auditoria

A etapa de profiling e auditoria antecipa os problemas que só iriam aparecer na
etapa de validação e testes dos dados. A análise dos resultados da auditoria deve ser
realizada pelo gestor do sistema alvo, gestor da área usuária do sistema alvo ou da área
de negócio, gerente do projeto e líder da migração. O que vai ser avaliado é a qualidade
dos dados fonte. Decidir-se-á o que não tem qualidade para ser migrado e o que precisa
de intervenção, sempre levando em consideração o que foi definido como meta no
planejamento da qualidade dos dados da etapa de planejamento. Se ao final da análise
for constatado que as metas são inatingíveis, deve-se levar o problema para os gestores
de sistema e de negócio e reavaliar as metas.
Este diagnóstico irá balizar a atividade de transformação dos dados, pois definirá
algumas intervenções necessárias, além das usuais, como, por exemplo, a definição de
valores default para campos obrigatórios. O que não foi homologado na auditoria é o
que seria rejeitado na atividade de carga dos dados no sistema alvo. A decisão de não
migrar dados de baixa qualidade deve ser uma decisão de negócio e não uma decisão
técnica. E devem ficar registrados os impactos desta decisão.

### 3.4. Construção e design

Esta etapa é caracterizada pela definição e construção do mapa de dados e dos
programas de extração, transformação, carga e validação dos dados. Nesta etapa do
projeto a equipe de migração já deve estar familiarizada com os dados fonte e estrutura
dos dados alvo e ter uma clara visão da qualidade da fonte de dados. Regras de limpeza
dos dados serão descritas baseadas nas auditorias da etapa anterior. Esta é uma etapa
bastante técnica na qual toda a equipe vai estar muito envolvida com desenho,
especificação e codificação. Se alguma ferramenta comercial foi adquirida para este
intuito, é o momento de instalá-la e começar a configurá-la. As atividades para esta
etapa são descritas nas subseções 3.4.1 a 3.4.9. O Quadro 11 mostra as atividades da
etapa de Construção e Design.
Quadro 11 - Atividades da etapa de Construção e Design.

#### 3.4.1. Definição das regras de limpeza dos dados

Com o diagnóstico obtido da etapa anterior sobre a qualidade da fonte dos dados,
sabe-se o que precisa ser tratado para garantir uma taxa de sucesso maior. Descreve-se o
que deve ser feito para corrigir os obstáculos encontrados pela auditoria. Estas
especificações farão parte do mapa de dados e servirão como regras de negócio para os
programas de transformação dos dados. As correções usualmente encontradas são:
Definição de valores default para campos obrigatórios;
Definição de valores default para chaves estrangeiras;
Correção de formato de datas e horas;
Padronização de formatação de campos alfanuméricos;
Limpeza de caracteres inválidos; e
Garantia de integridade de regras de negócio. Por exemplo, em um sistema de
controle de vendas, a soma do valor de todos os itens de um pedido deve
corresponder ao valor total do pedido armazenado.

#### 3.4.2. Construção do mapa de dados

Esta é, talvez, a tarefa mais laboriosa desta etapa. Porém, a mais importante. A
construção de um bom mapa de dados está para a migração de dados assim como uma
boa especificação de requisitos está para a construção de um sistema de informação. Um
bom mapa de dados é conseqüência da atenção com as etapas anteriores. O mapa de
dados, como o nome indica, é a rota que cada campo tem que percorrer entre o sistema
fonte e o sistema alvo. Numa analogia com uma boa rota, precisa deixar claro qual é a
origem, onde fica o destino, os obstáculos do caminho, o que é preciso para fazer a
viagem e o caminho mais eficiente e eficaz. Usam-se os dicionários de dados da etapa
anterior para fazer a referência entre os campos. A existência da etapa de auditoria e dos
dicionários de dados torna o mapa mais simples, permitindo que ele contenha as
informações necessárias para consultas e confecção dos programas. Maiores detalhes
sobre os dados podem ser consultados diretamente nos dicionários. Se a etapa anterior
não for executada, o mapa de dados deverá ser mais complexo, suprindo as informações
do dicionário de dados. O mapa de dados deve conter, no mínimo:
Identificador de coluna;
Nome da coluna alvo;
Descrição do campo;
Tipo do dado alvo;
Tamanho do dado alvo;
Obrigatoriedade;
Origem (Nome da coluna fonte);
Regra (Validação, limpeza ou transformação); e
Observações.
O Quadro 12 apresenta o mapeamento da coluna UNIDPROT_CD da tabela
CMT_REMESSA_NOTA_FISCAL do estudo de caso que será apresentado neste
trabalho.

Quadro 12 Exemplo de mapa de dados

#### 3.4.3. Especificação dos programas de migração

Atividade desenvolvida pelos analistas de sistemas da equipe de migração, que
devem ter como diretriz para a especificação os seguintes documentos:
Modelo e Dicionário de dados do sistema fonte;
Modelo e Dicionário de dados do sistema alvo; e
Mapa de dados.
Devem ser especificados os programas de extração, transformação, carga e
validação dos dados. Também os programas e scripts do plano de contingência. A
intenção de se ter grupos de programas específicos para cada função é utilizar melhor o
ambiente computacional, dividindo os recursos, visto que estes programas concorrerão
com o ambiente de produção.
Os programas de extração são os responsáveis por ler os dados definidos do
sistema fonte e gerar mídias intermediárias, geralmente arquivos, ainda no formato
fonte. Os programas extratores devem ser de baixa complexidade, pois não envolvem
muitas regras além das que especificam os limites da extração. Usualmente, são
construídos na tecnologia do sistema legado.
Os programas de transformação desenvolvem as regras definidas no mapa de
dados sobre as mídias intermediárias, saídas dos extratores, e geram novas mídias já
transformadas para o formato alvo. São mais complexos. É comum suprimir-se os
programas de transformação, e suas regras serem absorvidas pelos programas de
extração ou carga. Não é uma boa prática. É preferível que as camadas fiquem bem
definidas, pois a manutenção é mais eficiente. Além de, desta forma, os programas de
transformação poderem executar sem concorrer com as bases de dados de produção.
Eles usam apenas as mídias intermediárias. Geralmente, já são construídos com a nova
tecnologia do sistema alvo.
Os programas de validação se prestarão a verificar o resultado da migração. É
uma atividade mais leve que a auditoria, pois se deve verificar quantitativos de registros
migrados e regras de integridade de negócio. Pois, os programas de transformação já
fizeram o tratamento do conteúdo dos dados e, geralmente, a tecnologia de

armazenamento dos dados alvo também traz restrições de conteúdo. Eles são também
construídos com a nova tecnologia do sistema alvo.
Os programas e scripts do plano de contingência garantirão a integridade da base
de dados alvo, caso algum dano ocorra. Geralmente, são rotinas que irão desfazer o que
foi feito pelos programas de carga e são construídos com a nova tecnologia do sistema
alvo.
Recomenda-se que todos os programas gerem saídas do tipo log de
processamento para um melhor acompanhamento das rotinas e que procurem sempre
trabalhar com transações de banco de dados o mais curtas possível.

#### 3.4.4. Especificação dos programas de sincronismo

Dependendo da estratégia da migração escolhida no planejamento, a atividade de
sincronismo poderá estar presente. O sincronismo é necessário quando os sistemas fonte
e/ou alvo continuam em operação durante a migração dos dados. Tome-se como
exemplo o sistema fonte em operação durante a migração. Após a extração,
transformação e carga de um determinado dado no sistema alvo, este dado foi alterado
no sistema fonte. Ou seja, o dado está desatualizado no sistema alvo e precisará migrar
novamente para ficar consistente. Chama-se sincronismo o movimento de dados
atualizados no sentido do sistema fonte para o sistema alvo. E sincronismo reverso, o
movimento em sentido contrário. Embora mais raro de acontecer, o sincronismo reverso
pode ser adotado em estratégias que decidam manter os sistema fonte e alvo em
produção e em uso, cada um operando determinadas funcionalidades. Neste caso podese ter sincronismo nos dois sentidos.
Num mundo ideal, não se devia usar sincronismo. Freqüentemente, é uma fonte
de problemas. Deve-se evitá-lo, se possível. Entretanto, em grandes projetos de
migração é usual ter-se sincronismo.
A definição dos programas do sincronismo deve envolver as equipes de
desenvolvimento afetadas. Ou a do sistema fonte, ou a do sistema alvo, ou ambas. Estas
equipes têm a responsabilidade de gerar a informação para as rotinas de migração. A
melhor opção é que sejam gerados arquivos de sincronismo com o mesmo formato de
saída dos programas de extração da migração. Assim, estes arquivos estariam prontos
para serem transformados e carregados.
As particularidades de cada caso devem ser analisadas pelo líder da migração
juntamente com os líderes das equipes dos sistemas fonte e alvo e especificadas as
melhores soluções.

#### 3.4.5. Codificação dos programas

Atividade executada pelos desenvolvedores da equipe de migração seguindo as
especificações da atividade anterior. Nesta fase, com freqüência, faz-se necessário o
suporte das equipes dos sistemas fonte e alvo, dependendo da familiaridade dos
desenvolvedores da equipe de migração com os ambientes atual e futuro.

#### 3.4.6. Testes dos programas

Os programas devem ser testados nos ambientes definidos no planejamento.
Devem ser feitos testes unitários por programa. Dados reais precisam ser utilizados para
os testes. Esta atividade requer cuidados especiais, não só pela importância da atividade
em si, mas pela complexidade que normalmente se apresenta de se conseguir ambientes
que espelhem os ambientes de produção atual e futuro. Quanto mais fiel o espelhamento,
menores serão os problemas na etapa de testes e validação dos dados migrados. Um
aspecto determinante dos testes dos programas é o acompanhamento do tempo que
estão consumindo para executarem com sucesso. Precisa-se dar muita atenção a
requisitos de desempenho, diminuindo-se ao mínimo possível os tempos de
processamento. O conhecimento mais detalhado desta variável pode impactar o
cronograma.
Atenção especial deve-se ter com os programas de sincronismo, se existirem.
Deve-se testá-los meticulosamente.

#### 3.4.7. Construção dos jobs para execução das rotinas

Precisa-se analisar a necessidade desta atividade. Usualmente é requerida, pois
os programas de migração de dados utilizam muitos recursos do ambiente
computacional. Assim, não é uma boa prática que estes programas executem em modo
on-line. Devem ser agendados para o momento em que o ambiente de produção tenha
condições de suportá-los sem comprometimento das rotinas diárias da organização,
executando-os em modo batch. Recomenda-se construir todos os jobs com mecanismos
de restart, visto que a maioria deles é grande consumidora de recursos e pode ser
descontinuada por necessidades operacionais da organização. O mecanismo de restart
permite que o job recomece de onde parou.
Com freqüência, devido ao volume de dados a ser migrado, o processo de
migração se dá em ciclos. Portanto, a cada iteração, todos os tipos de jobs serão
executados. É importante criar-se mecanismos de controle destas iterações para saber-se
o que já foi extraído, transformado e carregado. Pode-se controlar os ciclos de várias
formas, desde o uso de rotinas automatizadas com registros em bancos de dados a
simples controles de nomes de arquivo ou de diretórios. Cabe ao líder da migração,
baseado na quantidade de iterações previstas, decidir a melhor maneira de controle.

#### 3.4.8. Testes dos jobs

Tudo o que foi dito para os testes dos programas (Seção 3.4.6) é verdade para o
teste dos jobs. Precisa-se ainda concentrar nas variáveis de ambiente que podem
interferir no desempenho das rotinas, como, por exemplo, a prioridade definida para os
jobs.

#### 3.4.9. Teste da migração dos dados

Após os programas e jobs estarem prontos e testados, precisa-se fazer um teste
geral das rotinas da migração dos dados. Se o cronograma e as condições permitirem,
indica-se migrar todos os dados definidos do ambiente fonte para o ambiente espelho
futuro. Usualmente, isto não costuma acontecer. O caso mais freqüente é realizar-se o

teste com um conjunto determinado dos dados fonte reais. Quanto mais dados, melhor o
teste. Deve-se testar os programas de validação e as regras definidas no plano de testes e
validação da etapa de planejamento. Os problemas relatados nos testes devem ser
tratados e corrigidos e feita uma nova migração, se forem problemas de dados. Nesta
atividade, a equipe do sistema alvo deve estar envolvida, pois rotinas, consultas e
relatórios do novo sistema serão testados. Recomenda-se aplicar quantas iterações
forem necessárias até se obter a qualidade desejada.
O objetivo maior do teste da migração é estabilizar o processo como um todo e
subsidiar a etapa seguinte, que é a etapa de execução em produção, com informações
mais precisas sobre tempo necessário, qualidade, segurança, entre outros.

### 3.5. Execução

Esta etapa é caracterizada pela entrada em produção do projeto de migração dos
dados. Ela e a etapa seguinte podem andar juntas. Ou seja, não é necessário migrar
todos os dados para começar a testá-los e validá-los. Ao contrário, o quanto antes os
testes e validações começarem, melhor. Também as atividades desta etapa podem ser
executadas em ciclos de migração. Não é necessário extrair todos os dados para
começar a transformá-los.
O gerente do projeto principal deve envolver-se no sentido de angariar apoio
organizacional para esta etapa, pois se este apoio não existir, normalmente só restarão
os fins-de-semana para as rotinas da migração dos dados. O Quadro 13 mostra as
atividades da etapa de Execução.
Quadro 13 - Atividades da etapa de Execução.

#### 3.5.1. Extração dos dados

Os jobs de extração serão agendados e executados. Esta atividade impacta o
ambiente fonte, geralmente um ambiente com disponibilidade comprometida. Esta
disponibilidade é uma restrição importante que, como já citado, deve envolver o gerente
do projeto para se discutir prioridades. Necessita-se de área em disco para armazenar as
mídias geradas. É normal dividir-se a extração em fases que irão compor o ciclo da
migração. As fases freqüentemente dizem respeito a períodos de tempo. A parada e
reinício dos jobs extratores, geralmente, não acarretam problemas.

#### 3.5.2. Transformação dos dados

Os jobs de transformação serão agendados e executados. Em princípio, estas
rotinas podem ser processadas em qualquer ambiente, visto que, normalmente,
processam e geram arquivos. Exceto se precisarem acessar determinadas bases de dados

para validarem alguma regra. Os jobs transformadores processarão os arquivos gerados
pelos jobs extratores.

#### 3.5.3. Carga dos dados

Com relação ao projeto principal, talvez seja esta a atividade mais importante e
mais aguardada. Para os menos informados, é o começo da migração dos dados.
Atividade que irá povoar a base de dados do sistema alvo. Os jobs de carga serão
executados no ambiente alvo. É a atividade mais delicada desta etapa. Pois, se está
povoando as tabelas definitivas do ambiente de produção. Quanto mais bem testada foi
esta rotina na atividade descrita na Seção 3.4.9, menos surpresas aparecerão. Se
problemas graves acontecerem nesta atividade, o plano de contingência terá que ser
acionado. Os problemas que costumam aparecer dizem respeito ao conteúdo de dados
que não foram testados na etapa anterior. Mesmo passando pelos testes da etapa
anterior, recomenda-se que antes de começar a atividade de carga de dados, o líder da
migração verifique a lista de requisitos da migração, descrita na etapa de planejamento,
e certifique-se da existência das condições requeridas, principalmente no que tange às
integrações com outras bases de dados que porventura existam.

#### 3.5.4. Tratamento das rejeições de dados

Mesmo com a auditoria dos dados realizada na etapa de Profiling e Auditorias e
das correções efetuadas na etapa de Construção e Design, falhas podem acontecer e,
usualmente, dados serão rejeitados. As principais causas de rejeição são:
Quebra de integridade referencial não prevista na auditoria, geralmente por
integração com outro sistema;
Não aderência a alguma restrição definida no SGBD;
Incompatibilidade de tipos de dados não verificados no mapeamento;
Conteúdo de dados não previsto; e
Semântica de dados não conhecida.
Ocorrida a rejeição, deve-se identificar a causa. Se o motivo for técnico, a
equipe de migração deve resolvê-lo. Se o motivo for conteúdo devido à semântica ou
regra de negócio, o gestor do sistema alvo ou de negócio deve ser acionado para
resolver, apoiado pela equipe de migração no que puder ser automatizado. Se o volume
de dados rejeitados for considerável, comprometendo a qualidade planejada, o
cronograma, o custo e o escopo do projeto de migração podem ser afetados. Este risco
será mínimo se as etapas 3 e 4 forem executadas com precisão. Grande parte do não
cumprimento das metas de custo e prazo nos projetos de migração de dados deve-se ao
trabalho extra gerado nesta atividade.
A Figura 38 mostra um ciclo de migração de dados da etapa de Execução. Este
ciclo, como já citado, pode-se repetir tantas vezes quanto for necessário dependendo da
estratégia de migração de dados adotada e da rejeição dos dados.

Figura 38 - Ciclo de migração de dados da etapa de Execução

### 3.6. Testes e Validação dos dados

Apesar dos dados terem sido validados ao longo da metodologia de
migração, testes unitários, de sistema e de carga devem ser feitos para garantir que todos
os dados foram migrados e que o novo sistema se comporta como esperado. O plano de
testes e validação dos dados, definido no planejamento, deve ser seguido, tendo suporte
nos jobs de validação construídos na etapa 4. Esta etapa é executada pela equipe da
migração juntamente com os usuários do sistema alvo. O Quadro 14 mostra as
atividades da etapa de Testes e Validação dos dados.
Quadro 14 Atividades da etapa de Testes e Validação dos dados

#### 3.6.1. Testes unitários

A variedade de testes unitários é uma particularidade de cada projeto. Algumas
sugestões de testes são:
Validar regras de negócio específicas;
Verificar a integridade destas regras;
Verificar o preenchimento das colunas dos registros;

Conferir formatação específica de colunas que possuam uma lei de formação
relacionando parte do conteúdo com outras colunas. Por exemplo, em um
sistema de controle de empréstimos bancários: o número do contrato precisa
começar com os quatro dígitos do ano que foi gerado, seguido de três dígitos que
representam o código da agência bancária que realizou a operação mais um
seqüencial de seis dígitos e dois dígitos verificadores. A informação do ano e da
agência precisa ser verificada; e
Verificar o tamanho do conteúdo de determinados campos. Por exemplo: esperase que determinado campo esteja preenchido com um conteúdo numérico com
10 posições, completadas com zeros à esquerda.

#### 3.6.2. Testes de carga

São realizadas contagens, no sistema legado e no sistema alvo, para verificar o
quantitativo de dados que deveriam ser migrados e carregados. Estas quantidades são
confrontadas. É uma atividade importante, pois dados podem ter sido rejeitados ou não
carregados sem que, por alguma falha, o rastreamento do ocorrido tenha sido registrado
e tenha passado despercebido na etapa de execução.

#### 3.6.3. Testes de sistema

São testes realizados no sistema alvo. O objetivo é realizar conferências de
resultados entre rotinas executadas nos ambientes legado e alvo. As rotinas a serem
validadas foram definidas no plano de testes e validação da etapa de planejamento.
Outro aspecto de muita importância desta atividade é o acompanhamento do
desempenho do sistema alvo na execução destas rotinas.

#### 3.6.4. Análise dos testes

Os gestores do sistema alvo e de negócio, o líder do projeto principal, o líder da
migração e demais partes interessadas irão analisar o resultado dos testes, norteando-se
pelo plano de qualidade traçado na etapa de planejamento. O objetivo é verificar,
principalmente, se o escopo e a qualidade prescritos na etapa de planejamento foram
atingidos. E os dados podem ser considerados como migrados satisfatoriamente.

#### 3.6.5. Homologação da migração dos dados

É a atividade de aceite da migração. Marca o encerramento das atividades de
migração de dados. Deve ser elaborado um documento contendo:
A data de início prevista e real;
A data de término prevista e real;
A quantidade de dados migrados (Sintética ou analítica, dependendo do nível de
detalhamento que se queira dar);
O índice de qualidade atingido; e
O aceite do gestor do sistema alvo e de negócio.
Este documento deve ser anexado ao plano de migração.

### 3.7 Conclusões do capítulo

Neste capítulo, apresentou-se uma metodologia para migração de dados. A
metodologia fornece os subsídios necessários para a migração de dados de qualquer tipo
de sistema legado pela quantidade e variedade de tópicos contemplados. Ela cobre,
detalhadamente, todas as etapas que devem estar presentes em um projeto de migração
de dados.
A metodologia parte de dois pressupostos essenciais para o sucesso de um
esforço de migração de dados: a empreitada ser tratada como um projeto independente e
a existência de um líder dedicado exclusivamente ao projeto. Também, não diminuindo
a importância das demais etapas, a metodologia destaca o planejamento e o controle das
atividades, bem como o conhecimento e a qualidade dos dados fonte e alvo. Reservando
trinta e nove atividades, dentre cinqüenta e duas, para tais finalidades. O Quadro 15
mostra quais são estas atividades.

Quadro 15 Atividades relativas ao planejamento e controle das atividades e ao conhecimento e qualidade dos dados fonte e alvo.

O enfoque destes temas justifica-se por notar-se, na bibliografia disponível e em
casos práticos, que os motivos de insucesso ou sucesso parcial dos esforços de migração
de dados estão vinculados, quase em sua totalidade, à falta de atenção com os referidos
assuntos. Procurou-se, então, preencher as lacunas observadas no estudo das estratégias
de migração de dados abordadas no Capítulo 2.
Assim, destacam-se como pontos fortes da metodologia apresentada:
Cobertura dos passos necessários para um projeto de migração de dados;
A migração dos dados é tratada como um projeto independente;
É necessária a indicação de um líder dedicado exclusivamente ao projeto;
Organização em forma de atividades bem definidas agrupadas em etapas;
Ênfase no planejamento e controle das atividades;
Ênfase no conhecimento e na qualidade dos dados fonte e alvo; e
Possibilidade de redução da quantidade de atividades ou do escopo destas de
acordo com o porte do projeto.

O Quadro 16 resume as atividades da metodologia proposta, dividindo-as por etapa.
Quadro 16 Atividades da metodologia proposta divididas por etapa

## 4. Validação da metodologia

Neste capítulo será detalhado como ocorreu a validação da metodologia proposta
no capítulo anterior, com a aplicação da mesma em um caso real. O estudo de caso
utilizado é a migração de dados do sistema legado Fronteiras para o CMT (Controle de
Mercadorias em Trânsito) do Projeto E - Fisco da Secretaria da Fazenda do Estado de
Pernambuco. Nesta migração de dados, a metodologia pôde ser validada e
realimentada com necessidades que surgiram ao longo do projeto. Procurou-se, quando
necessário, a cada atividade executada, além de descrevê-la, destacar as intervenções
feitas para que funcionasse, esclarecendo se são alterações da metodologia ou opções
fornecidas por ela.
Serão feitas breves explanações sobre o Projeto E Fisco, o sistema Fronteiras e
o sistema CMT com o propósito de contextualizar o estudo de caso. Em seguida tem-se
a aplicação da metodologia.

### 4.1. Cenário do estudo de caso

Desde o ano de 2000, a Secretaria da Fazenda do Estado de Pernambuco
vem desenvolvendo um projeto de atualização tecnológica de sua estrutura de TIC: o
Projeto E - Fisco. Até então, seus principais aplicativos corporativos, cerca de trinta,
eram baseados em arquitetura mainframe. Estes aplicativos e a maioria da infraestrutura eram mantidos e processados pela Agência de Tecnologia da Informação do
Estado de Pernambuco ATI. Assim como o corpo técnico de TIC também
estava alocado nas instalações daquela empresa. As grandes metas do Projeto E Fisco
consistiam em dotar a Secretaria da Fazenda de sua própria estrutura de TIC,
modernizando seu parque tecnológico e seus sistemas aplicativos para melhor servir aos
cidadãos e ao Estado. Este grande projeto demandou aquisição de parque computacional,
infra-estrutura, instalações, software, contratação de pessoal e migração dos sistemas
legados para a nova arquitetura.
A migração de um destes sistemas legados, o sistema Fronteiras, foi escolhida
para validar a metodologia proposta nesta dissertação. O motivo da escolha foi que,
dentre os cerca de trinta sistemas legados que seriam migrados, o Fronteiras era o maior
em termos de volume de dados a serem migrados e complexidade. Além de que, as
datas previstas do projeto se adequavam aos prazos deste trabalho. De forma sucinta, o
sistema Fronteiras tem como propósito controlar a entrada e saída de mercadorias no
Estado. Baseado neste fluxo, principalmente o de entrada, pois Pernambuco é um estado
comprador, controla-se um determinado imposto cobrado pelo Estado. Este imposto é
responsável por cerca de 15% da arrecadação estadual, além de ser um importante
instrumento de combate à sonegação fiscal. O sistema legado possuía uma base de
dados centralizada no mainframe e bases de dados distribuídas off line em vinte e quatro
pontos do Estado que sincronizavam com o ambiente central, operava vinte e quatro
horas por dia, sete dias por semana, tinha cerca de quinze serviços na Internet
disponíveis para o contribuinte, integrava-se com bases de dados nacionais e regionais e
processava cerca de um milhão de documentos fiscais por mês, o que gerava
aproximadamente dois milhões de registros armazenados mensalmente. Foi construído
há quinze anos, sendo um sistema confiável, estável e fundamental para o negócio da
empresa. Entretanto, contava com pouca documentação disponível.
O sistema alvo, o CMT (Controle de Mercadorias em Trânsito), além de
contemplar todas as funcionalidades do sistema legado, deveria contar com novas
81

funcionalidades, além de ser povoado com cinco anos de informações do Fronteiras
para começar a operar. Isto daria algo em torno de cento e vinte milhões de registros a
serem migrados para povoar cento e quarenta e cinco tabelas.

### 4.2. Aplicação da metodologia

Apesar de a Secretaria da Fazenda dispor de uma metodologia para
desenvolvimento de software, migração de dados não estava contemplada na referida
metodologia com o enfoque dado neste trabalho. A metodologia de migração de dados
proposta era um fato novo e, portanto, precisou-se apresentar a nova metodologia à
equipe do projeto de migração do sistema legado. Esclareceu-se que a metodologia
estava sendo posto à prova e sujeito a correções e melhorias. Seria um bom teste, pois
outros sistemas legados estavam sendo migrados e ter-se-ia parâmetros para serem
confrontados.
A metodologia proposta pressupõe dois requisitos: ser aplicada em um projeto à
parte do projeto principal e existir um líder da migração de dados. Os requisitos foram
aceitos pelo time do projeto principal. Existiria um projeto de migração dos dados
legados e indicou-se um líder que possuía quase todas as características sugeridas na
metodologia. O perfil de líder traçado deixou o gerente do projeto principal com poucas
opções e tendo que abrir mão de recurso importante. A característica mais conflitante é
a de ser um técnico experiente do sistema legado. Baseando-se nos fatos deste estudo de
caso e no desenrolar do projeto, neste quesito, a metodologia proposta pode ser
adaptada no sentido de dar prioridade às características de um gerente de projeto para
líder e não de um técnico. O conhecimento especializado deve ser suprido pelo restante
da equipe de migração e pelas equipes do sistema legado e do sistema alvo.

#### 4.2.1. Planejamento

No início do projeto principal, as atividades de planejamento da migração de
dados estavam sendo tratadas nas reuniões semanais do projeto principal. Não se
mostrou uma boa prática, pois o objetivo primeiro da metodologia - migração de dados
ser tratada como um projeto independente - começou a perder o foco. Migração de
dados era um tópico do projeto principal. A cultura de projeto da empresa ainda
mantinha esta abordagem. Necessitou-se quebrar este paradigma com o convencimento
dos envolvidos. Assim, definiram-se reuniões semanais exclusivas da migração,
conduzidas pelo líder da migração, para desenvolver a etapa de Planejamento.
Dependendo do tópico a ser tratado, as partes interessadas eram convocadas. Ganhou-se
tempo, pois ambas as reuniões ficaram mais curtas, produtivas e focadas. O líder da
migração continuou participando da reunião do projeto principal, quinzenalmente ou
quando convocado. Desta forma acompanhava o andamento do projeto principal com o
intuito de manter-se certo sincronismo entre os projetos e informava, às outras equipes e
ao gerente do projeto, do desenvolvimento da migração. A data corrente era fevereiro de 2007.
Desenvolvimento do Plano de Migração
O Plano de Migração é o produto final da etapa de Planejamento. É composto
pelos produtos das outras atividades de planejamento. Foi sendo construído à medida
que as reuniões aconteciam e as atividades prosseguiam. O Plano foi alterado diversas
vezes durante o projeto, o que é esperado. Segundo a metodologia proposta, o Plano
82

deve manter-se atualizado. Porém, este foi o maior obstáculo desta tarefa. A
importância da atualização do Plano precisou ser reforçada algumas vezes.
O Plano de Migração proposto pela metodologia abrange todo o projeto,
fornecendo uma visão detalhada de escopo, cronograma, custo, qualidade, atividades,
testes, contingência, entre outros.
Definição do escopo da migração
A dificuldade da definição de um escopo é o seu nível de detalhamento. A
metodologia é bastante objetiva neste tópico, fornecendo um roteiro claro do que deve
ser definido.
Objetivo da migração
o Limite da migração
A partir de janeiro de 2003 até a data da
implantação do sistema alvo.
Por tratar-se de informações tributárias, por determinação legal, precisa-se
manter operacional cinco anos das informações armazenadas. A previsão de
implantação do sistema alvo era dezembro de 2007, portanto fazia-se
necessário migrar os dados legados a partir de janeiro de 2003.
o Quantitativos da migração Estimava-se que seriam migrados cerca de
cento e vinte milhões de registros.
Este número foi levantado baseado em médias mensais de processamento de
documentos fiscais. O intervalo de médias considerado foi de um ano.
o Critérios de aceitação
Definiu-se que os dados deveriam ser 100% migrados. Este
critério pode ser revisto quando a etapa de auditoria começar a
produzir resultados;
Os extratos mensais dos contribuintes deveriam produzir
resultados iguais nos sistemas legado e alvo. Para efeito de
homologação, deveriam ser apurados, pelo menos, os últimos
vinte e quatro períodos mensais;
Os quantitativos de notas fiscais por lote e por remessa deveriam
estar iguais nos sistemas legado e alvo;
Os valores da arrecadação mensal deveriam estar iguais nos
sistemas legado e alvo; e
A relação de termos de fiel depositário por transportadora com
suas respectivas notas fiscais retidas deveria estar igual nos
sistemas legado e alvo. Para efeito de homologação, deveriam ser
apurados, pelo menos, os últimos vinte e quatro períodos mensais.
Este tópico precisou ser trabalhado com os gestores, pois a visão de
qualidade da migração dos dados não estava muito clara. Tinha-se uma visão
mais prática de quantidade. O gestor do sistema e o gestor de negócio
decidiram definir um critério quantitativo abrangente e critérios qualitativos
que julgaram essenciais para a confiabilidade da migração.

o Cronograma A data limite para a conclusão da migração é outubro de 2007.
A implantação do sistema alvo estava prevista para dezembro de 2007,
estipulou-se 60 dias antes a data limite da migração. Era sabido por todos os
envolvidos que os prazos estavam estreitos. A metodologia proposta permite
que, de acordo com o projeto, atividades deixem de ser executadas e o
escopo destas possa ser alterado. Entretanto, o estudo de caso se propunha a
validar a referida metodologia. Não seria oportuno deixar algumas atividades
sem teste. Temia-se, seriamente, que o prazo estipulado não fosse suficiente
para seguir todas as atividades propostas. Tentou-se, em princípio sem
sucesso, colocar um cronograma mais realista e adequado à quantidade de
trabalho que se apresentava. A metodologia permitiu antever este cenário.
o Custos Parte da equipe envolvida com a migração do sistema legado e
que também participaria do projeto de migração dos dados é terceirizada.
A restrição orçamentária que se apresentava era que o contrato de
terceirização iria até junho de 2008 e não havia, então, previsão
orçamentária para renovação do contrato ou nova licitação.
Descrição do escopo
O projeto de migração de dados tinha como propósito migrar os dados legados do
sistema tributário Fronteiras para o sistema CMT (Controle de Mercadorias em
Trânsito) do Projeto E Fisco. Os dados legados seriam migrados a partir de janeiro
de 2003 até a data de entrada em operação do CMT. Os dados legados deveriam ser
tratados para que se atingissem os critérios de aceitação definidos no escopo do
projeto. Estimava-se que seriam migrados cento e vinte milhões de registros e a data
limite para a conclusão do projeto era outubro de 2007.
Requisitos da migração
o O sistema CMT deveria se integrar, no nível de integridade referencial
definida em sistemas de banco de dados, com os sistemas SCA (Sistema
de Controle de Acesso), TGE (Tabelas Gerais), ACG (Administração de
Cadastro Geral), GCC (Gestão do Cadastro de Contribuintes), GAE
(Gestão da Arrecadação Estadual), GAF (Gestão da Ação Fiscal), GPF
(Gestão de Processos Fiscais), AMA (Administração de Mercadorias
Apreendidas) e PRT (Protocolo Geral) do Projeto E Fisco. Na época da
migração dos dados do sistema Fronteiras para o sistema CMT, estas
integridades deveriam estar satisfeitas. A relação das chaves estrangeiras
deveria ser encaminhada para os líderes dos respectivos projetos.
o O projeto de migração de dados requeria um ambiente computacional
paralelo com as mesmas características do ambiente de produção futuro.
Este ambiente paralelo seria utilizado para os testes e validações da
migração de dados. O ambiente paralelo deveria estar operacional para a
etapa de Construção e Design.
o Para que os critérios de aceitação qualitativos definidos fossem
homologados, seria necessário que as rotinas requeridas do sistema alvo

estivessem operacionais no mínimo na etapa de Construção e Design e
no máximo na etapa de Testes e Validação dos dados. Seria preferível
que estivessem disponíveis na primeira etapa citada.
o As previsões do quantitativo de linhas que seriam carregadas nas tabelas
do CMT foram passadas para as equipes de Banco de Dados e InfraEstrutura para que estas equipes avaliassem a necessidade de hardware
para processamento e armazenamento dos dados. Esta demanda foi
registrada como um requisito da migração dos dados.
o O ambiente de produção futuro já estava sobrecarregado com a entrada
em produção dos sistemas financeiros e alguns tributários do Projeto E
Fisco. As equipes de Suporte Técnico e de Infra-Estrutura foram
informadas do porte deste projeto de migração de dados e da necessidade
de processamento iminente. Registre-se a necessidade de disponibilidade
de tempo de processamento em produção como um requisito da
migração.
Este tópico da metodologia antecipou um fato que viria impactar negativamente o
cronograma do projeto. Desde esta etapa ficou evidente que a alta integração entre
os sistemas que formavam o E Fisco seria um obstáculo à conclusão da migração
dos dados. Outros aspectos importantes levantados foram a necessidade de medir e
planejar o consumo de recursos computacionais pelas rotinas de migração e manter
certo sincronismo com o desenvolvimento do sistema alvo para os testes da
migração. Estas informações desencadearam ações preventivas, que sem a
metodologia, não iriam existir.
Estratégia da migração
o Devido ao volume de dados a ser migrado, a migração ocorreria com o
sistema legado em operação;
o Haveria a necessidade de sincronismo no sentido do sistema legado para
o sistema alvo;
o As tabelas de domínio do sistema alvo seriam as primeiras a serem
povoadas;
o A migração ocorreria em ciclos de migração mensais;
o Ao final de cada ciclo, os dados seriam testados e validados;
o Ao final de cada ciclo, os dados rejeitados deveriam ser tratados; e
o A migração começaria do mês mais recente que estivesse com a rotina de
cálculo do imposto encerrada à época do início da etapa de Execução,
prosseguindo com os meses antecedentes.
A estratégia definida para a migração do sistema Fronteiras previa que todo
o sistema CMT seria construído para em seguida os dados serem migrados
para o início da operação. Ainda não se tinha uma idéia precisa do tempo
que a migração dos dados iria consumir. Mas, para reduzir o risco sobre o
cronograma, decidiu-se começar a migração dos dados o mais cedo possível,
gerando a necessidade de sincronismo e aumentando o risco sobre a
qualidade, pois os dados poderiam começar a ser migrados sem que as
rotinas de validação dos dados do CMT estivessem operacionais. Outra

decisão para minimizar o risco sobre o cronograma foi começar a migração
dos dados mais modernos para os mais antigos. A justificativa era que se o
sistema CMT estivesse pronto para entrar em operação e a migração não
houvesse terminado, o sistema entraria com os dados mais modernos e a
migração continuaria com o sistema alvo em produção.
Entregas da migração
Plano da migração;
Modelo de dados do sistema fonte;
Dicionário de dados do sistema fonte;
Mapeamento dos dados;
Programas de extração, transformação, carga, contingência e validação
dos dados;
o Relatórios de carga de dados;
o Relatórios de rejeição de dados; e
o Relatório de conclusão da migração.
o
o
o
o
o

Restrições da migração
Por se tratarem de informações tributárias, por força de lei, é necessário manter
armazenados cinco anos de informações do contribuinte.
Organização inicial do projeto
A metodologia propõe, neste ponto, a definição da equipe necessária para a
execução do projeto de migração. Não discute nem sugere quantitativos, pois são
detalhes muito particulares para cada projeto. Porém, a análise das atividades
sugeridas, inseridas no contexto real, pode dar um suporte significativo para
mensurar-se o tamanho da equipe necessária. Assim foi feito. Ademais, a alocação
ou liberação de recursos pode ser feita a qualquer momento, quando a necessidade
se apresentar. Desde o Planejamento, ficou definido pelo gerente do projeto
principal que os recursos seriam compartilhados entre projetos. Apenas o líder da
migração estaria com dedicação exclusiva. Esta decisão, baseada nas circunstâncias
que se apresentavam, foi danosa para o projeto da migração, configurando-se como
uma das principais causas do não cumprimento do cronograma. Afetando também a
qualidade em algumas atividades.
A equipe da migração de dados foi assim definida:
o 1 líder da migração de dados Dedicação exclusiva;
o 2 Analistas de Sistemas Dedicação parcial;
o 2 desenvolvedores Dedicação parcial;
o 1 usuário especialista em regras de negócio Dedicação parcial;
o 2 usuários para tratamento das rejeições Dedicação parcial;
o 2 usuários para testes e validações Dedicação parcial;
o 1 responsável pelo projeto na equipe de Banco de Dados;
o 1 responsável pelo projeto na equipe de Suporte Técnico; e
o 1 responsável pelo projeto na equipe de Infra-Estrutura.

Riscos iniciais
Quando se incorporou os riscos iniciais da migração, e os demais levantados
posteriormente, às planilhas de riscos do projeto principal, observou-se uma
mudança de percepção da relevância da migração de dados para o sucesso do
esforço de migração do sistema legado. Devido aos impactos levantados, este tópico
teve que ser revisto e validado num fórum mais amplo com a participação de
representantes técnicos e gerenciais das áreas afetadas. A metodologia sugerida não
previu a validação de riscos e impactos que extrapolassem o projeto, mas mostrouse uma prática importante que deve ser adicionada à metodologia.
Foram identificados os seguintes riscos iniciais:
o Subestimar o tempo da migração de dados;
O sistema Fronteiras possuía pouca documentação. A qualidade dos dados
legados só seria conhecida na etapa de Profiling e Auditorias. Ainda não se
tinha uma boa estimativa do tempo envolvido na limpeza dos dados, nem
nos tempos de extração, transformação, carga e tratamento das rejeições dos
dados. Portanto, qualquer estimativa de tempo de migração para construção
do cronograma, por segurança, deveria ser pessimista. Os gestores técnicos e
de negócio deveriam estar cientes que a variável tempo da migração ainda
não estava bem definida, e que o cronograma deveria ser alterado após a
etapa de Profiling e Auditorias.
o Falta de suporte organizacional;
A carga de processamento e armazenamento dos ambientes computacionais
legado e alvo deveria ser considerada, pois as rotinas do projeto
demandariam alto consumo dos recursos citados. A organização deveria
priorizar este projeto sob pena de impacto negativo no cronograma, escopo e
qualidade.
o Falta de sincronismo entre a migração de dados e o sistema CMT;
Uma importante validação dos dados migrados ocorreria testando-se rotinas
do sistema alvo e comparando-as com o sistema legado. Se tais rotinas não
estivessem operacionais na época das validações, poder-se-ia ter impacto
negativo no cronograma e na qualidade. Por outro lado, se o sistema CMT
fosse concluído e a migração de dados não, poder-se-ia ter impacto negativo
no cronograma e no escopo; e
o Falta de sincronismo entre a migração de dados e os sistemas que se
integram com o sistema CMT.
Não se tinha controle sobre os cronogramas de migração dos dados dos
sistemas que se integram com o CMT. Poder-se-ia ter problemas de rejeição
de dados por quebra de integridade referencial dos dados destes sistemas,
gerando impacto negativo no cronograma.
Identificação dos ambientes atual e futuro
Esta atividade foi criticada pelas equipes envolvidas como sendo uma atividade
desnecessária, já que todos os participantes conheciam bem os ambientes. Concluiu-se
que esta era uma atividade de planejamento com o objetivo de dotar o Plano de

migração de um descritivo dos ambientes para referência futura e dados históricos.
Também dava apoio para contratações de mão-de-obra, traçando requisitos
profissionais. Portanto, uma atividade necessária. O Quadro 17 apresenta as
características do ambiente atual, enquanto que o Quadro 18 apresenta as características
do ambiente futuro.
Quadro 17 Características do ambiente atual

Quadro 18 Características do ambiente futuro

Definição da arquitetura da migração
Chegou-se à conclusão que o projeto de migração de dados utilizaria cinco
ambientes. Esta decisão foi motivada pelas discussões levantadas até então, provocadas
pelo conhecimento adquirido do projeto de migração de dados gerado pelas atividades
de planejamento da metodologia executadas. Os cinco ambientes seriam assim
utilizados:
Ambiente de desenvolvimento legado
Os códigos de identificação dos sistemas fazendários legados utilizavam quatro
letras. Duas fixas, SF de Secretaria da Fazenda, e duas variáveis para identificar
o sistema propriamente dito. Assim o sistema tributário legado Fronteiras tinha o
código SFFR, que não só o identificava, como a todo o subconjunto do ambiente
de desenvolvimento utilizado para o desenvolvimento e armazenamento dos jobs
e programas do sistema. No SFFR de desenvolvimento seriam construídos,
alterados e testados os jobs e programas do sincronismo. Seria criado o sistema

SFMF (MF de migração do Fronteiras) para abrigar os jobs e programas da
migração de dados do lado legado. No SFMF de desenvolvimento seriam
criados, alterados e testados os jobs e programas das atividades de Profiling e
Extração de dados.
Ambiente de desenvolvimento alvo
Seria montado um ambiente, na plataforma alvo, exclusivo para o
desenvolvimento e testes dos scripts, jobs e programas de Transformação, Carga
e Validação dos dados, além dos de Contingência.
Ambiente paralelo alvo (Espelho)
Este ambiente seria o ambiente de teste definitivo. Deveria ter todas as
características do ambiente de produção alvo, incluindo as integrações com
outros sistemas. Neste ambiente seriam testadas e validadas todas as rotinas da
migração do ambiente alvo. Também seriam executadas todas as
Transformações de dados da etapa de Execução. Após a transformação, os dados
seriam enviados para o ambiente de produção alvo para serem carregados. A
execução da Transformação dos dados neste ambiente visaria a liberar o
ambiente de produção alvo de mais este processamento.
Ambiente de produção legado
Neste ambiente existiriam os sistemas SFFR (Fronteiras) e SFMF (Migração
Fronteiras). No SFFR seriam executadas as rotinas de sincronismo. No SFMF,
as rotinas de Profiling e Extração de dados. Estas rotinas acessariam as bases de
dados do SFFR. Na etapa de Execução, os dados extraídos seriam enviados para
o ambiente paralelo para serem transformados.
Ambiente de produção alvo
É o ambiente definitivo do sistema alvo. Neste ambiente seriam executadas as
rotinas de Carga e Validação de dados. Se necessário fosse, também seriam
executadas as rotinas de Contingência. A etapa de Testes e Validação dos dados
seria executada neste ambiente.
A Figura 39 mostra os ambientes utilizados na migração dos dados.

Figura 39 - Ambientes utilizados na migração de dados

Notou-se aqui a necessidade da mudança de ordem em uma atividade da
metodologia: a atividade que define a necessidade de compras e aquisições, descrita na
seção 3.1.14. Esta deveria ser realizada antes da próxima atividade. O motivo é que as
atividades descritas nas seções 3.1.5 até a 3.1.9 seriam mais efetivas se apoiadas por
aplicativos de Gerência de Projetos. Se a organização não os possuísse, indicar-se-ia a
aquisição. Não é compulsório na metodologia, mas é indiscutível o ganho de tempo,
qualidade e integração nas atividades.
No estudo de caso, não houve necessidade de aquisição, pois a organização já
possuía licença do Microsoft® Office Project Professional 2003. O referido
aplicativo foi utilizado para documentar e administrar o projeto de migração de dados.
Definição das atividades da migração
A metodologia propõe cinqüenta e duas atividades que servem como diretrizes
para o projeto. As particularidades de cada projeto podem retirar, acrescentar, detalhar
ou repetir atividades. A metodologia foi bastante útil neste quesito, pois as atividades
estavam pré-definidas. Necessitou-se detalhar algumas macro-atividades como a
codificação de programas. Também foi necessária a criação de ciclos de migração. A
Figura 40 mostra lista de atividades contidas no cronograma.

Figura 40 - Lista das atividades contidas no cronograma

Seqüenciamento das atividades da migração
A metodologia define uma seqüência natural de atividades para o projeto. Foi
necessário identificar quais atividades poderiam ser executadas em paralelo. Neste
aspecto, como melhoria, a metodologia poderia fornecer a sugestão de paralelismo das
atividades. A Figura 41 mostra o seqüenciamento das atividades realizado no
cronograma.

Figura 41 - Seqüenciamento das atividades realizado no cronograma.

Estimativa de recursos da atividade
Em atividades anteriores foram definidas equipe, dedicação dos recursos e
atividades. De posse destas definições, alocaram-se os recursos para cada atividade. A
Figura 42 mostra um relatório de recursos utilizados no projeto.

Figura 42 - Relatório de recursos utilizados no projeto.

Desenvolvimento do cronograma
O cronograma está baseado nas atividades previstas na metodologia. Tinha-se
uma restrição de cronograma que era a data de outubro de 2007. Depois que a equipe
estimou os prazos das atividades previstas, o término da migração ficou para junho de 2008. A atividade que mais impactou negativamente o cronograma foram os ciclos de
migração e testes. Seriam necessários 60 ciclos de migração, correspondentes a 60
meses de dados a serem migrados. Depois que a etapa de Construção e Design avançou,
pôde-se medir com mais precisão os tempos de migração. Com as melhorias de
desempenho que foram feitas nos programas e com a janela de produção que se
dispunha para execução dos jobs, a duração de um ciclo de migração ficou em dois dias,
contando-se com vinte e quatro horas por dia.
Passou-se a trabalhar com a data de fevereiro de 2008 como uma nova restrição
do cronograma, quando seria necessário estar com pelo menos um ano de migração
concluída. Começou-se, também, um esforço organizacional no sentido de se aumentar
a janela de produção para processamento dos jobs da migração. O detalhamento de
atividades fornecido pela metodologia permitiu a construção de um cronograma realista,
apesar de comprometer totalmente os prazos desejados pelo projeto principal.
A Figura 43 mostra o cronograma do projeto.

Figura 43 - Cronograma do projeto.

Estimativa de custos
A metodologia é bastante genérica na definição de custos do projeto, deixando a
critério da organização a profundidade do controle que se deseja adotar. A estimativa de
custos do projeto do estudo de caso está baseada exclusivamente na equipe da migração
de dados. Os custos relativos a recursos computacionais, outras equipes, custos fixos
rateados, material de expediente, entre outros, não foram computados. A Figura 44
mostra a estimativa de custos do projeto.

Figura 44 - Estimativa de custos do projeto.

Planejamento da qualidade
A preocupação com a qualidade é um dos pontos fortes da metodologia.
Considerando-se a cultura de migração de dados da empresa, a ênfase na qualidade dos
dados ainda era incipiente. A área de qualidade era recente e o foco era qualidade de
software. Questionou-se se a metodologia não deveria definir parâmetros de qualidade.
Definir o que seria qualidade de dados não fazia parte da metodologia. E manteve-se
esta decisão, pois o conceito é muito relativo. Varia de acordo com o amadurecimento
da empresa em relação ao assunto. A proposta da metodologia é genérica para ser
abrangente. Adotou-se, como opção oferecida pela metodologia, que a qualidade dos
dados requerida deveria estar alinhada com os critérios de aceitação da migração dos
dados. Segundo estes critérios, definidos no escopo do projeto, algumas diretrizes de
qualidade seriam adotadas. Estas diretrizes poderiam ser alteradas de acordo com o
resultado da etapa de Profiling e Auditorias:
As regras de limpeza dos dados deveriam resolver 100% das rejeições de dados
detectadas;
O mapa de dados deveria validar as regras de negócio definidas como critérios
de aceite da migração;
O teste da migração dos dados deveria ter como objetivo o cumprimento dos
critérios de aceite da migração;
Segundo os critérios definidos, o tratamento das rejeições de dados deveria ser
100% eficiente; e
Os testes unitários, testes de carga e testes de sistema deveriam estar alinhados
com os critérios de qualidade definidos.

Definição das comunicações
Este é um tópico de aparência simples que requereu bastante atenção para não
tornar-se conflituoso. Os projetos principal e de migração dos dados tinham muitos
pontos de interseção e sincronismo. Foi preciso cuidar para que as informações que
circulavam sobre os projetos fossem coerentes. Por vezes, a falta de sintonia entre eles
gerou ruídos de comunicação e alguns desgastes. Como melhoria, a metodologia deve
chamar a atenção para este obstáculo. A forma observada de suplantá-lo é manter as
equipes envolvidas integradas e informadas, com as informações deliberativas partindo
de uma única fonte: o gerente do projeto principal.
Definiu-se a comunicação no estudo de caso da seguinte forma: semanalmente
seriam realizadas reuniões da migração para acompanhamento das atividades definidas
na etapa de Monitoramento e Controle. Quinzenalmente, com a presença do gerente do
projeto, dos líderes do sistema legado e alvo e dos gestores de sistema e negócio. Nestas
reuniões seriam dados os informes do andamento do projeto e discutidas questões
relevantes que necessitassem da decisão dos envolvidos. As atas destas reuniões deviam
ser enviadas a todos os participantes e demais partes interessadas. Devia ser criada uma
lista eletrônica da migração, onde seriam postadas as informações de interesse do grupo.
O ponto focal e responsável pelas comunicações do projeto de migração é o líder da
migração. Em caráter de urgência, podiam ser convocadas reuniões extraordinárias.
Identificação de riscos
Problemas técnicos com o aplicativo de Gerência de Projeto motivaram o uso de
planilhas para o registro dos riscos. Seguindo a metodologia, passou-se a analisar
primeiramente os riscos que pudessem afetar os objetivos de cronograma, escopo,
qualidade e custo. Este roteiro mostrou-se uma boa prática pela falta de cultura de riscos
na organização. Ainda segundo a metodologia, a planilha de riscos foi sendo atualizada
conforme o andamento do projeto. As maiores preocupações diziam respeito à
integração com outros sistemas, sobre cujos prazos não se tinha controle, e com a falta
de tempo dos usuários para homologarem a migração - Riscos 4 e 9, respectivamente.
Análise qualitativa dos riscos
Conforme já comentado, a falta de cultura de risco na organização dificultou a
classificação de probabilidade e impacto dos riscos desta atividade. A ausência de dados
históricos documentados também foi um agravante. Ainda assim, foi possível
estabelecer prioridades de tratamento dos riscos. Espera-se que, com a adoção da
metodologia, os próximos projetos tenham mais subsídios para apoiar as decisões. A
Figura 45 mostra a planilha inicial de riscos do projeto.

Figura 45 - Planilha inicial de riscos do projeto.

Definir necessidade de compras e aquisições
Já foi citado anteriormente que esta atividade deve ser executada antes da
definição das atividades da migração. É uma sugestão de melhoria da metodologia.
Neste ponto do projeto, foram avaliados aplicativos de mapeamento de dados e
profiling, porém, como se trata de empresa pública, o processo de compra talvez
impactasse negativamente o cronograma. Portanto, decidiu-se pela não aquisição de tais
ferramentas.
Definir necessidades de recursos humanos
O único componente da equipe da migração com dedicação exclusiva era o líder
da migração. Os outros componentes estavam com dedicação parcial. Solicitou-se, sem
sucesso, dedicação exclusiva para toda a equipe, sob pena de impactar negativamente o
cronograma do projeto. Apesar de ter-se um projeto independente, não se conseguiu
uma equipe independente. A metodologia não foi objetiva o suficiente neste aspecto,
exigindo dedicação exclusiva apenas do líder da migração, fato que não se mostrou
suficiente para o cumprimento das metas do projeto.
Plano de testes e validação
A metodologia requer um planejamento da etapa de Testes e Validação dos
dados. O produto deste planejamento é o Plano de testes. As diretrizes do planejamento
da qualidade apontavam para os critérios de aceitação da migração. Por coerência, esta
atividade também usou tais critérios, dentro da metodologia proposta. O Plano de testes

foi construído baseado em casos de teste que comprovassem a eficácia da migração dos
dados. Os casos de teste referiam-se aos programas de validação e ao sistema CMT.
Alguns casos de teste utilizados foram definidos no Plano de teste do sistema CMT. A
Figura 46 apresenta o plano de testes.

Figura 46 - Plano de testes.

Plano de implantação
Neste tópico levantou-se questionamento sobre se a metodologia não deveria
sugerir a defesa e homologação do Plano de implantação frente às partes envolvidas.
Notou-se uma tendência, não só aqui, mas em outras ocasiões, de querer-se especializar
a metodologia para o estudo de caso. Mais uma vez, o consenso defendeu o caráter
genérico da metodologia sem a necessidade de mais uma atividade. A metodologia já
sugere que a etapa de Planejamento seja conduzida pelo líder da migração com a
participação das partes envolvidas. A criação de um número excessivo de atividades
desencoraja o uso da metodologia.
A principal contribuição do plano de implantação foi listar requisitos e
atividades para a implantação do projeto. Neste projeto de migração de dados, o plano
de implantação ateve-se aos requisitos e atividades necessários para a entrada em
operação do sistema alvo, no que dizia respeito à migração dos dados legados. A Erro!
Fonte de referência não encontrada.47 apresenta o plano de implantação.

Figura 47 - Plano de implantação.

Plano de contingência
O projeto E - Fisco foi desenhado totalmente integrado. Um único banco de
dados dá suporte a todos os sistemas envolvidos. A integração entre os sistemas está
definida no nível de chave estrangeira. Este fato garantia integridade, mas por outro
lado criava uma restrição muito forte para a migração dos dados dos sistemas legados
que estariam sendo feitas isoladamente. Outro fato importante é que o banco de dados
estava em produção com todos os sistemas financeiros e alguns tributários. O que
tornava desaconselhável qualquer utilização de utilitários do banco de dados que
afetasse o ambiente como um todo.
A principal contingência do projeto de migração era a capacidade de desfazer
uma carga de dados em produção que se apresentasse defeituosa. A equipe de banco de
dados desencorajou o uso de rollbacks. Apesar de todos os testes previstos, projetou-se
o Plano de Contingência contemplando a ação de desfazer as principais cargas através
de programas e scripts. Foram selecionadas as principais tabelas alvo, geralmente as
mais complexas em termos de regras, validações e integrações, e foram construídos os
programas e scripts baseados nesta seleção.
Um ponto importante, recomendado pela metodologia, foi a existência de um
ambiente paralelo. Foi um investimento em recursos, em princípio questionado, que se
revelou de grande utilidade, aumentando a eficiência e abrangência dos testes e
diminuindo a probabilidade do uso do Plano de Contingência. Outro ponto que merece
uma observação é que a metodologia propõe a informação, às partes interessadas, do
impacto no cronograma e custo do projeto caso o Plano de Contingência seja acionado.
Na prática, esta orientação careceu de mais objetividade, pois eram inúmeras as
combinações possíveis de utilização do Plano. Como melhoria, sugere-se, com o intuito

de opção da metodologia, a confecção de um cronograma do projeto considerando o
pior cenário do Plano de Contingência. No estudo de caso, isto não foi feito. Apenas
informou-se que haveria impacto e que as mudanças seriam discutidas com todos antes
de serem executadas, como previsto na metodologia.

#### 4.2.2. Monitoramento e Controle

Procurou-se manter as atividades desta etapa sempre presentes durante todo o
projeto. O acompanhamento do projeto era um item recorrente das reuniões semanais.
Há que se ressaltar o impacto cultural da implantação de uma metodologia. Como ainda
não era uma iniciativa institucional, mesmo com o patrocínio da Superintendência, as
dificuldades para o cumprimento das atividades propostas pela metodologia foram
evidentes. Em muitos momentos, dado o caráter metodológico, pareceu que o projeto de
migração dos dados era maior que o projeto principal. E isto gerava conflitos. Nesta
etapa, principalmente, a linha divisória entre atividades dos projetos, de migração e
principal, era muito tênue, necessitando grande sintonia entre as lideranças. Fato que,
num ambiente real, com tantas variáveis para controlar e outras tantas sem controle, não
é simples de conseguir. Com o agravamento de alguns conflitos de escopo de liderança
e de projeto, ficou claro que a metodologia necessita de uma implantação mais formal.
Para o estudo de caso foi feita uma apresentação para as equipes e passada para os
líderes a documentação disponível. Isto é pouco para a abrangência da metodologia.
Como melhoria proposta, sugere-se, como pré-requisito da metodologia, se esta ainda
não for uma prática da organização, o treinamento dos envolvidos.
Controle de mudanças
Todas as mudanças detectadas foram discutidas. Aquelas aprovadas foram
refletidas nos documentos do projeto. Estas afetaram negativamente, principalmente o
cronograma. Um exemplo de mudança foi a necessidade de sincronismo diante do
tempo necessário para concluir todos os ciclos de migração. As mudanças eram tratadas
nas reuniões semanais com a presença de todas as partes interessadas.
Porém, nem todas as mudanças foram tratadas no devido tempo. Não por falha
da metodologia, mas por falha de comunicação presente em um projeto deste porte. As
mudanças não identificadas que causaram maior impacto foram alterações da estrutura
do banco de dados alvo sem o conhecimento da equipe de migração e,
conseqüentemente, sem reflexo no mapa de dados, programas de transformação, carga e
validação, entre outros.
Verificação do escopo
As entregas do projeto ocorreram e foram aceitas, porém, muitas com atraso.
Este fato foi predominante nas etapas de Profiling e Auditorias e Construção e Design.
Atribuiu-se estes atrasos à dedicação parcial da equipe da migração. Algumas entregas
foram aceitas parcialmente, mas, com o andamento do projeto e a pressão do
cronograma não foram corrigidas. Um exemplo disto foi o Plano de Testes que não
continha todos os casos de teste previstos. Os testes ocorreram, mas o Plano de Testes
só foi atualizado após a implantação do sistema alvo, não aderindo à metodologia, que
sugere que todos os documentos se mantenham atualizados.

Controle do cronograma
Atividade semanal que sofreu diversos ajustes negativos devido às mudanças e
às entregas com atraso. Dir-se-ia ser este o aspecto mais negativo do projeto. A
imposição de data inicial era de oito meses para realizar o projeto. Entretanto, o projeto
foi concluído com dezoito meses de prazo, totalizando dez meses de atraso.
Levantou-se a hipótese de um dos motivos do atraso ser a quantidade de
atividades propostas pela metodologia. Para refutar a argumentação analisou-se o
cronograma do projeto e ficou claro, documentalmente, que as atividades que
repercutiram negativamente foram aquelas nas quais a equipe não estava totalmente
dedicada e as que dependiam de recursos computacionais compartilhados do ambiente.
Todas elas, atividades tradicionalmente executadas em projetos de migração de dados
independente de metodologia, como confecção e teste de programas e execução de
rotinas. Para reforçar a defesa da metodologia, comparou-se o cronograma do projeto
com outros projetos que não usaram a metodologia. Levando-se em consideração
números relativos, a metodologia mostrou-se mais eficiente nos principais objetivos do
projeto: cronograma, escopo, qualidade e custos.
Controle de custos
Como já comentado, para efeito de custos do estudo de caso, foram considerados
apenas os recursos humanos alocados à equipe de migração. Assim, o fator que criou
variações e mudanças no orçamento do projeto foi a dilatação do cronograma.
Realizar o controle da qualidade
Atividade que demandou bastante atenção durante todo o projeto. O cronograma
também foi impactado pela decisão de se priorizar a qualidade em detrimento do prazo.
Não por deficiência da metodologia, mas por deficiência da abordagem, o planejamento
da qualidade foi feito voltado exclusivamente para as metas de aceitação da migração.
Observou-se, no acompanhamento, que outros aspectos de qualidade deveriam ter sido
abordados, como, por exemplo, a qualidade das entregas previstas. A qualidade não
definida destes itens ficou implícita no conceito de qualidade que a equipe da migração
possuía, nem sempre homogêneo e satisfatório.
Gerenciar a equipe do projeto
A principal dificuldade apresentada nesta atividade foi o compartilhamento de
recursos da equipe da migração. A definição de prioridades do projeto de migração, em
algumas ocasiões, ficou comprometida com a superioridade das prioridades do projeto
principal. Estas mudanças eram sempre registradas e informadas aos gestores e partes
interessadas.
Cabe aqui, mais uma vez, registrar-se como sugestão de melhoria, que a
metodologia proponha, além do líder da migração com dedicação exclusiva, a existência
de uma equipe mínima também dedicada. Tal sugestão visa à melhor administração do
projeto em diversos aspectos, sendo o controle das atividades e da equipe, os principais.

Monitoramento e controle dos riscos
Os riscos foram mantidos sob controle. Mesmo assim, não se conseguiu mitigar
um risco tido, desde o começo do projeto, como de alta probabilidade de acontecer e de
grande impacto no cronograma, no escopo e na qualidade. Foi o risco da não migração
dos dados dos sistemas integrados no tempo previsto. Outro risco não previsto, a
inexistência de determinados dados entre 2003 e 2005, e só detectado na etapa de
Profiling, também demandou esforço extra impactando negativamente o cronograma.
Sugeriu-se a retirada desta atividade da metodologia, por ser redundante, já que
o projeto principal já incorporara os riscos da migração e também os monitorava. O
argumento contrapunha-se à independência dos projetos, requisito da metodologia, e o
consenso decidiu desconsiderá-lo.

#### 4.2.3. Profiling e Auditorias

Era a primeira vez que um trabalho desta natureza se realizava com os dados do
sistema legado. Quando o escopo da etapa foi apresentado, as equipes envolvidas
reagiram negativamente. A justificativa era que o investimento seria grande em um
sistema que estava sendo desativado, assim como o impacto no cronograma. Este tipo
de reação está documentado na bibliografia pesquisada e exposto no Capítulo 2. É uma
das causas de subestimar os tempos envolvidos em um projeto de migração de dados.
Os envolvidos não se dão conta de que os dados são os mesmos, não importando se a
embalagem é a velha ou a nova. A expectativa de um novo ambiente mascara o esforço
necessário de limpeza e transformação dos dados originais.
As atividades desta etapa foram essenciais para o conhecimento da qualidade da
fonte dos dados. Considera-se uma das etapas importantes da metodologia e que não
deve ser descartada em detrimento do prazo. Esta atividade foi toda orientada a
conteúdo e não a metadados. Iniciou-se em abril de 2007.
Construir ou atualizar o modelo de dados do sistema fonte
Não está no objetivo da metodologia definir tecnicamente como as atividades
devem ser desenvolvidas. Tal procedimento invalidaria o propósito genérico da mesma.
Uma instância da metodologia pode ser criada para o ambiente em questão. Não houve
tempo, no estudo de caso, da criação prévia de uma instância da metodologia. Ela foi
sendo construída à medida que o projeto andava. Sugere-se, como melhoria da
metodologia, a opção da geração de uma instância para o ambiente, na etapa de
planejamento, com a definição de técnicas e processos específicos para determinadas
atividades. O entendimento deste ponto gerou controvérsias. Houve críticas à
metodologia por não estar definida para atender especificamente a um problema da
organização. Neste tópico, por exemplo, os envolvidos esperavam que a metodologia
indicasse como seria feito o modelo de dados de uma base de dados não relacional
usando uma ferramenta de modelagem relacional. Este é um obstáculo técnico
específico que a metodologia não se propõe a resolver.
O sistema Fronteiras não possuía modelo de dados. As ferramentas disponíveis
na empresa não possibilitavam construí-lo utilizando engenharia reversa, pois não
tinham suporte para o ambiente legado. Necessitou-se construir o modelo com o apoio
da equipe de suporte a banco de dados do ambiente legado. A Figura 48 mostra o
modelo de dados do sistema legado.

Figura 48 - Modelo de dados do sistema legado

Construir ou atualizar o dicionário de dados do sistema fonte
O dicionário de dados do sistema Fronteiras foi construído, apoiado pela
ferramenta de modelagem de dados utilizada, baseado no modelo de dados criado.
Alguns cuidados com os tipos de dados foram necessários, pois a ferramenta não
utilizava todos os tipos de dados do ambiente legado.
Construir o modelo de dados do sistema alvo
Esta atividade estava sendo desenvolvida pela equipe do sistema alvo. A equipe
da migração integrou-se ao processo para acompanhar a atividade e dar sugestões
visando a facilitar a migração de dados sem comprometer a semântica do negócio. Esta
atividade não estava totalmente concluída quando a equipe da migração decidiu ir em
frente com as auditorias por pressão do cronograma. Esta é uma opção que deve constar
da metodologia, tomando-se o cuidado de controlar os riscos da decisão. Por este
motivo, algumas regras não foram testadas, o que resultou em rejeições na etapa de
Execução. Notou-se, também na etapa de Execução, que algumas alterações de estrutura
do banco de dados alvo não foram refletidas no respectivo modelo de dados. Já foi
comentado que estas mudanças não foram controladas, gerando impacto negativo no
projeto de migração de dados. A Figura 49 mostra o modelo de dados do sistema alvo.

Figura 49 - Modelo de dados do sistema alvo

Construir o dicionário de dados do sistema alvo
Esta atividade foi desenvolvida pela equipe do sistema alvo com o
acompanhamento da equipe de migração.
Definir o profiling
Seriam povoadas cento e quarenta e cinco tabelas no sistema CMT. Além das
verificações de unicidade e nulidade, integridade referencial e formatação, foram
definidas quarenta e três regras de negócio mais complexas a serem validadas nos dados
legados do período definido. As mais importantes estavam relacionadas a referências
cruzadas entre tabelas, dependências entre registros de diferentes tabelas e verificação
de redundâncias controladas como totalizadores e campos descritores. Foram utilizados
os dicionários de dados dos sistemas legado e alvo para definir as validações. A Figura
50 mostra o documento base usado para definir as regras de Profiling.

Figura 50 - Documento base para o Profiling

Verificar a possibilidade de aquisição de ferramenta de profiling
A aquisição de ferramenta de profiling foi descartada devido à necessidade de
processo licitatório.
Construir os programas de auditoria
Decidiu-se criar um programa para cada tabela alvo. Portanto, foram definidos e
desenvolvidos cento e quarenta e cinco programas de auditoria. Alguns muito simples,
pois apenas verificavam conteúdos de domínios. Os que tratavam informações de
movimento periódico foram parametrizados para tratarem dados por período informado.
Todos geravam relatório dos problemas encontrados. O prazo previsto no cronograma
inicial para esta atividade foi alterado. Além da resistência natural da equipe em investir
no sistema legado, a dedicação parcial comprometeu todos os prazos. Este fato já foi
comentado e proposta uma melhoria para a metodologia.
Realizar o profiling nos dados fonte
O profiling foi executado em ciclos mensais. Como foi executado em ambiente
de produção legado, os tempos disponíveis para execução foram limitados. Dispunha-se
da janela de processamento diária entre 17:00h e 07:00h do dia seguinte. Os prazos
previstos no cronograma inicial não foram suficientes. Detectou-se, aqui, como
melhoria, a necessidade da confecção de jobs que não fora prevista na metodologia. A
Figura 51 mostra o resultado do Profiling.

Figura 51 - Resultado do Profiling

Análise dos resultados do profiling e auditoria
Foram detectadas várias inconsistências nos dados fonte, mais concentradas em
dados mais antigos. As mais simples diziam respeito à formatação e a valores de
domínio. As mais graves eram ausência de dados e quebra em regras de negócio.
Ocorreram alguns problemas devido ao desconhecimento da semântica de dados mais
antigos. Em um determinado período do sistema, houve uma mudança de regra de
negócio que alterou o significado do conteúdo de determinadas colunas, gerando
inconsistências com as regras atuais. Estes tipos de erro deram mais trabalho, pois se
necessitava de um histórico das regras de negócio, o que não foi fácil de ser levantado.
De uma forma geral, os dados estavam com uma qualidade média. Os erros
detectados eram passíveis de correção. A maioria das correções poderia ser
automatizada. As correções manuais foram encaminhadas para os usuários designados
para tal. Os dados ausentes poderiam ser recuperados de outro sistema e as quebras de
regra de negócio deveriam ser corrigidas. Não houve necessidade de descarte de dados.
Devido à especificidade dos erros, decidiu-se corrigir os dados fonte e não
deixar a tarefa para os programas de transformação, pois isto os tornaria bastante
complexos. Era mais seguro deixar a fonte dos dados íntegra e mais fácil de testar os
referidos dados em um sistema mais estável e confiável. Esta é uma opção que não foi
explicitada, mas deve constar da metodologia.
A tarefa de correção dos dados demandou bastante esforço da equipe. Às vezes,
era necessário construir um programa para corrigir poucos registros. Foram necessários
mais trinta e dois programas, os quais foram executados várias vezes, até que o nível de

qualidade dos dados estivesse satisfatório. O cronograma foi seriamente impactado pela
correção dos dados.
Outro aspecto que merece atenção pela dificuldade gerada nesta etapa foi a
ausência de histórico da semântica dos dados. A falta de registro das alterações de
regras de negócio e o seu impacto nos dados foi um sério problema de complexa
solução. Não seria resolvido pela metodologia. Apenas, se existisse o registro histórico,
a metodologia deveria consultá-lo nesta etapa para a criação das regras de profiling.

#### 4.2.4. Construção e Design

Esta é uma etapa bastante técnica na qual se notou dificuldade em gerenciar a
equipe, devido à dedicação parcial, e conseqüentemente, o cronograma. Nesta etapa,
devido à experiência da etapa anterior e seu impacto no cronograma, conseguiu-se
alocar dois desenvolvedores em tempo integral. Ela começou em setembro de 2007.
Definição das regras de limpeza dos dados
Por causa da decisão de se corrigir as inconsistências mais graves na etapa
anterior, esta atividade ateve-se a definir regras para corrigir desvios menos sérios. A
maioria das regras dizia respeito à formatação de conteúdo, como data, hora, colunas
que foram desmembradas, conversão de tipos, entre outros. Estas regras foram usadas
nos programas de transformação dos dados.
Construção do mapa de dados
Não se utilizou ferramenta para a construção do mapa de dados. Foi construído
baseado nos dicionários de dados dos sistemas legado e alvo e nas regras de
mapeamento levantadas junto aos usuários e técnicos. O mapa de dados do projeto pode
ser consultado no Anexo I deste documento, o qual é um resumo ilustrativo do
documento original, contendo as partes mais interessantes. As partes comuns a todas as
tabelas foram retiradas. O documento original possui cento e quarenta páginas. A Figura
52 mostra o mapa de dados do projeto.

Figura 52 - Mapa de dados do projeto.

Especificação dos programas de migração
Seguindo-se as orientações da metodologia, nesta atividade foram especificados
os programas de extração, transformação, carga e validação, além dos programas de
contingência. Decidiu-se pela geração de arquivos intermediários nas fases de extração
e transformação, pois diminuía a pressão nos ambientes de produção. Mais uma vez
questionada, a metodologia não especifica como a equipe deve executar seu trabalho.
Propõe algumas sugestões genéricas de boas práticas. A decisão de como desenvolver a
atividade é da equipe.
Especificação dos programas de sincronismo
A forma como o sincronismo iria operar ainda não estava muito clara nesta fase
do projeto. Decidiu-se por defini-lo da mesma forma da migração dos dados, em ciclos
mensais. Os programas de sincronismo foram especificados pela equipe do sistema
legado. Entre alteração e construção, cento e oito programas foram especificados.
Identificou-se a necessidade de maior atenção ao sincronismo por parte da
metodologia. Pela freqüência com que ocorre em grandes projetos e pelos danos que
pode causar se mal planejado, como sugestão de melhoria, deveria haver uma atividade
de planejamento do sincronismo. Ficou evidente no decorrer do estudo de caso que, se
maior atenção fosse dispensada ao planejamento do sincronismo, alguns problemas
teriam sido evitados. Deve-se citar que as rejeições de dados notificados deveram-se a
falhas no sincronismo e, devido à estrutura de dados que foi definida para apoiar as
rotinas de sincronismo, o job de sincronismo final precisou ser executado sessenta vezes,

uma vez para cada mês migrado, para que a migração dos dados fosse dada como
terminada.
Codificação dos programas
Atividade que exigiu intensa troca de experiências entre as equipes de migração,
do sistema legado e do sistema alvo. Esta atividade foi marcada por grande alteração de
código por motivo do baixo desempenho dos programas quando submetidos à
concorrência do ambiente paralelo. Principalmente, este fato ocorreu com os programas
de carga de dados. A equipe do sistema legado foi reforçada com recursos de outras
equipes para concluir os programas de sincronismo. Mesmo assim, esta atividade gerou
impacto negativo no cronograma. Esta atividade utilizou os ambientes de
desenvolvimento do sistema legado (SFFR e SFMF) e o ambiente de desenvolvimento
da migração na plataforma do sistema alvo.
Testes dos programas
Atividade bastante complexa por causa do ambiente muito integrado. Foi grande
o esforço para se conseguir reproduzir o ambiente de produção. Em alguns testes foi
necessário excluir restrições de integridade, como restrições de chave estrangeira e
triggers, do banco de dados alvo para que os mesmos pudessem ser concluídos. Nos
primeiros testes, o desempenho dos programas de carga foi crítico, o que motivou
retorno para a codificação e impacto no cronograma. A equipe de banco de dados foi
chamada a intervir para melhoria de desempenho das consultas ao banco de dados.
Outra causa de baixo desempenho foi o tamanho das transações de banco de dados.
Os testes do sincronismo não foram satisfatórios porque o ambiente de testes do
sistema legado estava com poucos dados carregados e não se dispunha de área em disco
no ambiente mainframe para fazer uma carga de dados, ressaltando mais uma vez a
necessidade de um melhor planejamento do sincronismo, não previsto pela metodologia.
Construção dos jobs para execução das rotinas
As atividades de migração seriam executadas em modo batch, portanto os jobs
necessários foram construídos, todos com mecanismo de restart.
Testes dos jobs
Os jobs foram testados com a mesma ressalva feita nos testes dos programas em
relação à fidelidade ao ambiente de produção. Um ciclo de migração, que corresponde a
extração, transformação e carga de um mês de dados legados, levou, em média, dois
dias para ser processado. Este prazo foi atualizado no cronograma.
Teste da migração dos dados
Como ressaltado pela metodologia, quanto mais dados, melhor a qualidade dos
testes. Por causa da alta integração entre os sistemas do E Fisco, precisava-se dos
dados de nove sistemas que se integravam com o sistema CMT. Não foi aceito pelas
demais equipes dos sistemas envolvidos migrar 60 meses de dados para o ambiente
paralelo para se fazer um teste geral com os dados reais. Além do esforço, estimava-se
que levaria seis meses para se fazer a carga destes dados. Acertou-se que o teste seria

feito com seis meses de dados, uma amostragem de 10%. E assim foi feito. Carregou-se
de janeiro a junho de 2006 o CMT e todos os sistemas que se integravam com ele.
Precisou-se de dez dias para se fazer a carga, a qual ocorreu dentro do prazo previsto. A
migração transcorreu sem surpresas com um índice de migração de 100% dos dados.
As validações foram feitas e os quantitativos satisfizeram os critérios. Os testes
unitários e de carga também foram satisfatórios. Alguns testes de sistema não puderam
ser realizados, pois as rotinas ainda não estavam prontas no sistema CMT. Este era um
risco previsto que não pôde ser evitado.

#### 4.2.5. Execução

Etapa que marca a entrada da migração de dados em produção. Como já
salientado, as atividades desta etapa ocorreram em ciclos mensais. As dificuldades desta
etapa foram notadamente a corrida contra o relógio e as constantes interrupções das
rotinas da migração por demanda de rotinas operacionais dos ambientes de produção. A
sensibilização organizacional da importância do projeto foi fundamental na negociação
dos tempos de utilização dos ambientes de produção. O acompanhamento da etapa foi
feito através de aplicativo para controle dos jobs e de sistema de diretórios para os
arquivos já processados. Assim foram construídos diretórios para os arquivos extraídos,
transformados e carregados.
Os testes realizados nas etapas de Profiling e Auditorias e de Construção e
Design também se mostraram de grande valia, pois minimizaram os problemas
ocorridos. Devido aos horários disponíveis para a execução das rotinas, a equipe
precisou adequar os horários de trabalho. Em relação à metodologia, não se encontrou
dificuldades dignas de menção nem necessidades de melhorias foram identificadas. Esta
etapa começou em fevereiro de 2008.
Extração dos dados
Atividade realizada no ambiente de produção legado, gerando arquivos extraídos
mensais. Devido à concorrência com o ambiente, os jobs de extração executaram
diariamente a partir das 17:00h e eram interrompidos às 07:00h do dia seguinte. Nos
finais de semana, estes horários eram mais flexíveis de acordo com as rotinas
agendadas. Após a extração, os arquivos eram transferidos para o ambiente paralelo da
migração na plataforma do sistema alvo para serem transformados.
Transformação dos dados
Esta atividade não concorria com os ambientes de produção, pois era executada
no ambiente paralelo da migração. Das atividades desta etapa foi a mais ininterrupta. Os
arquivos resultantes eram gerados já transformados para o formato de carga e, então,
transferidos para o ambiente de produção do sistema alvo.
Carga dos dados
Foi a atividade mais delicada e que demandou mais tempo. A concorrência com
o ambiente de banco de dados do E Fisco de produção mostrou-se bastante crítica,
levando as rotinas da migração a serem executadas sempre fora do horário do
expediente da empresa. A cada ciclo, incluíam-se cerca de dois milhões de linhas no
banco de dados, motivando a necessidade de reorganizá-lo semanalmente. Esta tarefa

deixava o banco de dados inoperante por até seis horas e pressionava ainda mais o
cronograma do projeto. Utilizou-se a janela de tempo entre as 20:00h e as 06:00h do dia
seguinte para a carga dos dados, geralmente com interrupções, sobrecarregando a tarefa
de administrar as rotinas, pois diariamente era necessário verificar-se até onde a rotina
executou para ser reiniciada. Nos finais de semana, estes horários eram mais flexíveis
de acordo com as rotinas agendadas. A Figura 53 apresenta um log de iteração de carga
de dados.

Figura 53 - Log de uma iteração de carga de dados

Tratamento das rejeições de dados
Apesar de todos os testes, dados ainda foram rejeitados. Os principais motivos
de rejeição de dados foram:
Algumas regras de transformação dos dados foram definidas após a etapa de
Profiling e Auditoria e, portanto, não foram validadas naquela etapa;
A estrutura do banco de dados do ambiente paralelo onde foram realizados os
testes não estava exatamente igual ao ambiente de produção - faltavam algumas
restrições;
Novas restrições de banco de dados foram criadas após o teste da migração na
etapa de Construção e Design;
Os dados dos sistemas que se integravam com o CMT não estavam totalmente
carregados em produção; e
Problemas com geradores de seqüência do banco de dados alvo ocasionaram
violações de chave primária.

Nesta atividade, cerca de duzentos e noventa registros foram corrigidos
manualmente e duzentos e onze mil foram corrigidos automaticamente. Foi
necessário esperar que os dados dos sistemas integrados fossem carregados com
sucesso para se realizar a carga dos dados rejeitados pela ausência destes, gerando
impacto no cronograma.

#### 4.2.6. Testes e Validação dos dados

Esta etapa iniciou-se em março de 2008. Tão logo a etapa de Execução começou
a homologar os primeiros meses carregados, foram iniciados testes e validações de
dados. A forte integração entre os sistemas do E Fisco foi um obstáculo para os testes.
Muitas informações dependiam de outras provenientes de outros sistemas, as quais
ainda não haviam sido carregadas comprometendo a conclusão de alguns testes.
Testes unitários
Foram detectados alguns preenchimentos de colunas com tamanhos não
esperados. O povoamento das referidas colunas originou-se de fontes e programas
distintos, provocando a incompatibilidade. Foram corrigidos com scripts, pois se tratava
de complemento com zeros.
Testes de carga
Os quantitativos comparados forneceram resultados bons. Apenas algumas
tabelas de domínio cresceram em relação ao sistema legado, fruto de regras de negócio.
Detectou-se também falha em alguns sincronismos de inclusão e exclusão, provocando
diferenças de quantitativos. Estas diferenças foram da ordem de 0,03% do total
migrado, que em números absolutos representava quase quarenta mil linhas. Os gestores
decidiram homologar o teste e resolver o problema após a implantação.
Testes do sistema
Foram realizados os testes definidos no Plano de Testes. Duas rotinas
importantes não puderam ser testadas, pois ainda estavam em desenvolvimento. Os
tempos do sistema apresentaram-se muito ruins, mas este problema não dizia respeito à
migração dos dados. Algumas telas e relatórios também não funcionaram bem por falha
na definição das consultas ao banco de dados.
A Figura 54 e a Figura 55 mostram telas dos sistemas Fronteiras e CMT,
respectivamente, usadas para validar a migração de dados, conforme definido no Plano
de Testes.

Figura 54 - Tela do sistema Fronteiras

Figura 55 - Tela do sistema CMT

Análise dos testes
Os testes da migração dos dados foram considerados satisfatórios, cumprindo os
requisitos de escopo e qualidade definidos. Foram migrados 99,97% dos dados do
sistema legado, que em números absolutos representava mais de cento e vinte e nove
milhões de linhas. Os requisitos de cronograma e custos não foram cumpridos. O
término da migração dos dados estava previsto para outubro de 2007, porém foi
realmente concluída em julho de 2008.
Homologação da migração dos dados
O termo de aceite da migração dos dados do sistema Fronteiras foi construído e
assinado em 22 de julho de 2008. Em 25 de agosto de 2008, o sistema CMT entrou em
produção.

#### 4.2.7. Conclusões do capítulo

O estudo de caso apresentado neste capítulo visou a demonstrar uma aplicação
prática da metodologia de migração de dados proposta por esta dissertação, com o
objetivo de fazer uma análise crítica da mesma. Ao longo dos dezoito meses do projeto,
cerca de vinte pessoas usaram diretamente a metodologia em alguma das suas atividades.
As conclusões aqui apresentadas baseiam-se na condução e observação direta da
metodologia e nas opiniões, sugestões e críticas destas pessoas.

A organização onde o estudo de caso foi realizado não possuía metodologia de
migração de dados. Os seus esforços de migração de dados anteriores foram definidos
de forma empírica baseados na experiência de seus técnicos, geralmente como uma
atividade a mais em um projeto maior. Os resultados passados verificados indicavam
características comuns como cronogramas não cumpridos, baixa qualidade dos dados
migrados e altos índices de rejeição de dados (em média 3,7%). Geralmente, os dados
rejeitados eram alvo de projetos futuros de recuperação que, freqüentemente, eram
atropelados pelas demandas urgentes do dia-a-dia corporativo.
As vantagens do emprego da metodologia começaram a aparecer desde o
começo do projeto principal ao se considerar migração de dados como um projeto
independente com um líder dedicado. A etapa de Planejamento, bastante detalhada,
permitiu antever o tamanho do desafio e desencadear um processo de sensibilização
institucional da importância do projeto, além de gerar um Plano de Migração com todos
os detalhes do projeto que servirá como fonte de consulta futura. O não cumprimento do
cronograma inicial foi conseqüência da falta de maturidade organizacional para lidar
com prazos tão longos em se tratando de uma tarefa até então tida como acessória. Mas
a equipe registrou, em várias atas inclusive, que seguindo a metodologia, os prazos
almejados não seriam alcançados. A etapa de Auditoria foi uma experiência de
resultados excelentes para a qualidade final dos dados. A organização nunca realizara
esforço de tal magnitude para recuperação de dados legados. A etapa de Monitoramento
permitiu manter os principais objetivos sob controle. As etapas operacionais, dentro do
contexto, funcionaram a contento fruto dos esforços realizados nas etapas de
planejamento e controle.
O resultado obtido, comparado com os anteriores, foi bem melhor. Apesar do
cronograma não cumprido, a qualidade dos dados migrados foi superior e o escopo teve
uma variação mínima (0,03%) comparada com a média histórica. A qualidade é um
conceito subjetivo e difícil de mensurar. O que se alegou da qualidade como sendo
superior foi baseado no silêncio do usuário final quanto aos dados, o que na implantação
de um novo sistema é um bom sinal. Também a não ocorrência de falhas de sistema
motivadas por dados incorretos ou mal formados. Outro resultado positivo foi a inserção
de uma instância da metodologia de migração de dados proposta na metodologia de
desenvolvimento de software da empresa, já em andamento e conduzida pela equipe de
qualidade. Foram comparados, também, os resultados obtidos com outras migrações
realizadas no mesmo período sem a utilização da metodologia. A Figura 56 mostra um
gráfico comparativo da migração dos dados com outros dois sistemas.

Figura 56 - Gráfico comparativo da migração dos dados

Pelo gráfico, nota-se a eficiência da metodologia no tocante ao escopo, com a
baixa rejeição, e a quantidade de dados migrados por período, resultado principalmente
do planejamento e do profiling.
Mas, nem tudo funcionou perfeitamente. Várias sugestões de melhorias foram
catalogadas durante a aplicação da metodologia e serão adotadas. As melhorias são as
seguintes:
Adequação do perfil do líder da migração para ter as características de um gerente
de projeto e não de um técnico experiente;
Definir como um requisito opcional da implantação da metodologia, o treinamento
da equipe de migração dos dados na metodologia;
Definir como um requisito opcional da implantação da metodologia, a existência
de uma equipe mínima dedicada, além do líder da migração;
Na etapa de Planejamento, definir uma atividade para criar uma instância da
metodologia para o projeto corrente;
Trocar a ordem da atividade Planejar Compras e Aquisições para ser realizada
antes da atividade Definir Atividades ;
Na atividade Definir seqüência de atividades , especificar, de uma forma geral,
quais atividades da metodologia podem ser executadas em paralelo;
Na definição do Plano de Contingência citar como opcional a inclusão das rotinas
de contingência no cronograma do projeto ou construir outro cronograma, ambos
considerando o pior cenário de contingência;
Definir uma atividade para o Planejamento do Sincronismo, se este existir, na
etapa de Planejamento;

Na atividade Construir o modelo de dados do sistema alvo , destacar como
opcional seguir com as demais atividades da etapa mesmo sem o modelo estar
concluído. Deve-se considerar os riscos da decisão;
Definir uma atividade Construir os jobs do Profiling na etapa de Auditorias e
Profiling;
Definir como opcional, na etapa de Auditorias e Profiling, a correção dos dados na
base legada, se for mais seguro para o projeto; e
Definir uma atividade de Consulta ao histórico de alterações das regras de
negócio , se existir algum registro histórico, na etapa de Auditorias e Profiling.

## 5. Conclusões

O principal objetivo deste trabalho foi propor uma metodologia de migração de
dados em um contexto de migração de sistemas legados. No desenvolvimento da
dissertação, foram investigadas as principais metodologias de migração de sistemas
legados, as principais estratégias de migração de dados e as boas técnicas de gerência de
projetos. Vários trabalhos estudados apontavam para estratégias eficientes de migração
de dados, mas não com a abrangência deste. Propôs-se uma metodologia composta de
cinqüenta e duas atividades distribuídas em seis etapas.
A metodologia fornece subsídios para a migração de dados de qualquer tipo de
sistema legado pela quantidade e variedade de tópicos abordados, indo desde o
planejamento do projeto, passando por monitoramento, auditorias, design, execução
chegando à validação e testes dos dados migrados. A validação da metodologia foi
executada em um estudo de caso real onde foram migrados cerca de cento e vinte e nove
milhões de registros. Os resultados obtidos com a metodologia proposta foram
promissores.
A seguir, serão apresentadas as principais contribuições do trabalho, algumas
limitações observadas, propostas de trabalhos futuros e as considerações finais.

### 5.1. Principais contribuições

As principais contribuições apresentadas por esta dissertação foram:
Análise das várias estratégias de migração de dados;
Proposta de uma metodologia que cobre todos os passos de uma migração de dados
em um contexto de migração de sistemas legados;
Aplicação da metodologia proposta em um estudo de caso real; e
Análise crítica da metodologia aplicada com sugestões de melhorias.

### 5.2. Limitações

As limitações descritas referem-se à aplicação da metodologia no estudo de caso
real. A iniciativa da utilização da metodologia, apesar de patrocinada pela alta gerência,
não foi institucional. Este fato, em alguns momentos, pareceu caracterizar a empreitada
como apenas de interesse pessoal gerando dificuldades na realização de tarefas e
obtenção de resultados com algumas partes envolvidas. Outro aspecto a salientar-se foi
a aplicação da metodologia em um ambiente não controlado, sujeito a muitas
instabilidades e em um momento crítico para a área de TIC da empresa. Em muitas
ocasiões, não se pôde dar a prioridade desejada ao trabalho. Por exemplo, a coleta de
dados estatísticos para dar subsídios a uma análise mais criteriosa da metodologia não
ocorreu como esperado, deixando este item incompleto.
As comparações feitas entre as migrações de dados do sistema CMT e de outros
dois sistemas carecem de maior aprofundamento. Considerou-se, para comparação,
características objetivas não se levando em consideração características subjetivas
importantes como qualidade dos dados legados dos sistemas, problemas ocorridos com
a equipe, entre outros. Precisar-se-ia de ambientes bem controlados para que a

comparação pudesse acontecer com bases mais criteriosas. Porém, os números obtidos
não invalidam o resultado promissor do estudo de caso.

### 5.3. Sugestões de trabalhos futuros

As extensões propostas a este trabalho são:
Realizar uma aplicação prática da metodologia em sistemas legados de menor porte
fazendo os ajustes nas atividades da metodologia;
Utilizar ferramentas comerciais para dar apoio às atividades de mapeamento de
dados e profiling e analisar os resultados obtidos;
Criar ferramentas para automatizar a metodologia; e
Realizar uma comparação de resultados, em ambiente controlado, entre migração de
sistemas legados com características semelhantes. Um sistema usando a
metodologia e o outro com um processo tradicional.

### 5.4. Considerações finais

Novas aplicações da metodologia vão garantir que as atividades propostas são
realmente abrangentes e úteis para qualquer situação que possa ocorrer durante a
migração de dados no contexto apresentado. Por fim, espera-se que este trabalho possa
ser melhorado com possíveis situações não cobertas sendo acrescentadas à metodologia,
tornando-a ainda mais abrangente e que o mesmo possa servir como fonte de consulta e
estudo.

Referências Bibliográficas
Agência de Tecnologia da Informação do Estado de Pernambuco
http://www.ati.pe.gov.br

ATI

Bennett, K. H.; Legacy Systems: Coping with Success, IEEE Software,
Volume 12, Número 11, Páginas 19 -23, Janeiro 1995.
Brodie, M.; Stonebraker, M.; DARWIN: On the Incremental Migration of
Legacy Information Systems, Relatório Técnico TR-022-10-92-165 GTE Labs Inc.,
Março 1993.
Brodie, M.; Stonebraker, M.; Migrating Legacy Systems: Gateways, Interfaces
and the Incremental Approach, Morgan Kaufmann Publishers Inc. 1995.
Datanomic Ltd.; Data Migration: Reengineering Data for Optimized Value.
http://www.datanomic.com/solutions/business-improvement/data-migration-reengineering-data-for-optimized-value/ - Último acesso em 6 de outubro de 2007.
Ganti, N.; Brayman W.; Transition of Legacy Systems to a Distributed
Architecture, John Wiley & Sons Inc. 1995.
Grande Dicionário Larousse Cultural da Língua Portuguesa
Cultural 1999 - Página 620.

Editora Nova

Group, The Open; Indexed Sequential Access Method (ISAM) Aug 15, 1990.
Howard, P.; Bloor Research
em http://www.it-analysis.com/technology/data_mgmt/content.php?cid=9856 - Último
acesso em 06/08/2008.
IBM; IBM Hardware-Assisted Data Migration Services.
http://www03.ibm.com/systems/resources/systems_storage_solutions_services_whitepapers_pdf_g
522-2583.pdf - Último acesso em 06/09/2007.
ISO/IEC/JTC 1/SC 32 ISO/IEC 19503:2005, Information Technology
XML Metadata Interchange (XMI) 2005.
Kernighan, B; Ritchie, D; C Programming Language (2nd Edition) (Prentice
Hall Software) April 1, 1988.
Lowe, D; Vsam: Access Method Services and Application Programming - Jun 1986.
Manek, P.; Microsoft CRM Data Migration Framework, Abril 2003.
Meltz, D; Long, R; Harrington, M; An Introduction to IMS(TM): Your
Complete Guide to IBM's Information Management System (Ibm Press) Jan 9, 2005.

Microsoft Office Online
http://r.office.microsoft.com/r/hlidAsstProjFromClientWithLogging/1046/EC01023041/
2 - Último acesso em 20/02/2009.
Mohanty, Soumendra; Data Migration Strategies, Part 2, DM Review Special
Report, maio 2004. http://www.dmreview.com/specialreports/20040525/10039611.html Último acesso em 06/08/2008.
Morris, John; Practical Data Migration, British Computer Society 2008 - Cap.

1.  Navathe, S. B.; Gadgil S. G.; A Methodology for View Integration in Logical
    Database Design, 8th International Conference on Very Large Databases, Cidade do
    México, México, Setembro 1992.
    OpenProj version 1.2 em www.projity.com
    PMBOK Guide

ultimo acesso em 15/01/2009.

3a Edição; ANSI/PMI 99-001-2004.

Previdelli, C.A.; Magalhães, G.C.; Moving geospatial applications towards a
mission critical scenario. To appear: Proceedings of the XXV GITA Annual Conference,
March, 17-20 2002.
Secretaria da Fazenda do Estado de Pernambuco
http://www.sefaz.pe.gov.br

Projeto E - Fisco

Shepherd, John B.; Data Migration Strategies em
http://www.dmreview.com/issues/19990601/996-1.html Último acesso em 06/08/2008
Sommerville, Ian; Engenharia de Software, 6ª Edição, Addison Wesley

- Cap. 26.

Stern, N; Structured Cobol Programming: For the Year 2000 and Beyond Aug 1999.
Stroustrup, B; The C++ Programming Language: Special Edition (3rd Edition) Feb 11, 2000 - Special Edition.
Tilley, S. R.; Smith D. B.; Perspectives on Legacy System Reengineering,
Novembro 1996.
Youn, C.; Ku, C. S.; Data Migration, IEEE International Conference on
Systems, Man and Cybernetics, Volume 2, Páginas: 1255 -1258, Outubro 1992.
Wu, B.; Lawless, D.; Bisbal, J.; Richardson, R.; Grimson, J.; Wade, V.;
O'Sullivan, D.; An Overview of Legacy Information System Migration, Asia Pacific
Software Engineering Conference e International Computer Science Conference,
Páginas: 529 530, Dezembro 1997.
Wu, B.; Lawless, D.; Bisbal, J.; Richardson, R.; Grimson, J.; Wade, V.;
O'Sullivan, D.; The Butterfly Methodology: A Gateway-free Approach for Migration

Legacy Information Systems, 3rd IEEE International Conference on Engineering of
Complex Computer Systems, Páginas 200 -205, Setembro 1997.
Wu, B.; Lawless, D.; Bisbal, J.; Grimson, J.; Wade, V.; O'Sullivan, D.;
Richardson, R.; Legacy Systems Migration -A Method and its Tool-Kit Framework,
Asia Pacific Software Engineering Conference e International Computer Science
Conference. Páginas: 312 320, Dezembro 1997.
Wu, B.; Lawless, D.; Bisbal, J.; Grimson, J.; Legacy Information Systems:
Issues and Directions, IEEE Software, Volume 16, Número 5, Páginas: 103 111,
Setembro/Outubro 1999.
Wu, L.; Sahraoui, H.; Valtchev, P.; Coping with Legacy System Migration
Complexity, 10th IEEE International Conference on Engineering of Complex Computer
Systems, Páginas: 600 -609, Junho 2005.
