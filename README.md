<h1 align="left">Um resumo sobre o Apache Iceberg</h1>

<h2>Data Lakehouse</h2>

<p>O Iceberg é especialmente útil na arquitetura Data Lakehouse, assim, é fundamental entender esse conceito e, como o próprio nome diz, é uma junção de outras duas arquiteturas: o Data Lake e o Data Warehouse. Então, vamos ver um pouco sobre cada uma.</p>
<p>O Data Warehouse garante a qualidade dos dados e escalabilidade com seu sistema de armazenamento indexado e particionado, porém, por só permitir dados estruturados, acaba sendo muito custoso e pouco flexível.</p>
<p>Por outro lado, o Data Lake é um armazenamento que permite diferentes tipos de formatos de arquivos, trazendo consigo uma melhora no desempenho de consulta, além dos benefícios da interoperabilidade. Contudo, ele não consegue garantir a qualidade dos dados nem dá suporte a transações ACID.</p>
<p>Assim nasceu o Data Lakehouse, uma junção desses dois sistemas de armazenamento de dados. Ou seja, traz as propriedades ACID e a qualidade do Data Warehouse, ao mesmo tempo que tem baixos custos, aceita vários formatos de dados e possui a interoperabilidade do Data Lake. Além disso, essa arquitetura também suporta versionamento, possui um histórico que pode gerar relatórios e permite que diferentes processos podem utilizar os mesmos dados.</p>
<p>Aí surge uma pergunta: como isso é possível? Bom, isso é o resultado da junção de Open File Format e Open Table Format. Essa dupla combina um armazenamento eficiente e flexível (considerando que os Open File Format comprimem os dados e aceitam dados estruturados ou não) com funcionalidades de transação, versionamento e governança fornecidas pelo Open Table Format.</p>

<h2>Open Table Format</h2>
(o que é um formato de tabela -> depois falar sobre o open format) (dar exemplos de outros tipos além do iceberg)

<h2>Open File Format</h2>
  
<h2>Apache Iceberg</h2>

<p>Finalmente, chegamos à resposta sobre o que é o Iceberg.</p>

<p>Ele nada mais é do que um formato de tabela, portanto, não oferece armazenamento, sendo do tipo Open Table Format. Assim, garantindo transações consistentes com propriedades ACID e, junto com o isolamento de snapshots (visualizações pontuais do estado atual de uma tabela), tem a possibilidade de diferentes serviços alterarem os dados de uma mesma partição simultaneamente, desde que não haja conflito.</p>
<p>O Iceberg, além de ser 100% código aberto, é integrado com o SQL, trazendo simplicidade nas operações do dia a dia, ademais, é bem flexível em questões de usabilidade rotineira, pois aceita várias tecnologias e bibliotecas (como, por exemplo: Spark, Trino, Impala, Snowflake, Presto, etc.). Essa variedade também ajuda em outra funcionalidade: a migração de tipo de tabela, a qual ocorre através de cópias dos arquivos de metadados originais ou reutilizando-os e apenas criando os novos arquivos no formato Iceberg.</p>
<p>Além disso, esse formato de tabela conta com mais algumas características:</p>
<ul>
  <li>Partição "escondida"</li>
  <p>O usuário não precisa lidar com o particionamento dos dados, pois o próprio Iceberg já faz isso por trás dos panos.</p>
  <li>Evolução do schema</li>
  <p>O Iceberg permite que as colunas sejam alteradas sem risco de prejudicar os dados, pois somente os arquivos de metadados são atualizados, desta forma, assegurando a consistência dos dados ao mesmo tempo que permite o crescimento do schema.</p>
  <li>Histórico de ações</li>
  <p>Os snapshots permanecem guardados mesmo depois de terem sido substituídos por outros snapshots mais atuais, fazendo um versionamento de dados e disponibilizando consultas às formas antigas dos dados e da tabela.</p>
  <li>Processamento incremental</li>
  <p>Somente os dados de uma última execução são processados, consequentemente, economizando processamento e memória.</p>
  <li>Filtragem de partições</li>
  <p>O Iceberg otimiza as consultas através da omissão de dados desnecessários no contexto da consulta e da filtragem de partições, selecionando apenas o que é relevantes. Além disso, sua arquitetura de metadados otimizados contribui otimizando o desempenho das pesquisas.</p>
</ul>

<h3>História</h3>

<h3>Arquitetura</h3>

<p>Agora vamos entender um pouco sobre como o Iceberg consegue fazer isso?</p>
<p>Primeiramente, é importante saber que ele é dividido em três camadas:</p>
<ul>
  <li>Catálogo</li>
  <p>É a parte que armazena as informações de todas as tabelas, precisa de alguma tecnologia externa para guardar os metadados e ele sempre "aponta" para o último metadado criado.</p>
  <li>Metadados</li>
  <p>Essa camada contem tudo sobre uma tabela em específico, como quais as colunas, seus tipo, quantidade, partições, versões, últimas alterações, etc. Também é dividida em outras três sub camadas.</p>
  <ul>
    <li>Arquivo de metadados</li>
    <p>Contém um ou mais snapshots, assim, um catálogo "aponta" para uma camada de metadados e esses para vários snapshots</p>
    <li>Arquivo com listas de manifestos</li>
    <p>Cada snapshot "aponta" para um arquivo que contém listas com as informações sobre a localização de um manifesto e as partições dos dados.</p>
    <li>Arquivo manifesto</li>
    <p>Por fim, esse arquivo contém uma lista com a localização para os arquivos que conteém os dados de sua espectiva partição.</p>
  </ul>
  <li>Dados</li>
  <p>A última camada é onde estão os dados em si, em um Open File Format</p>
</ul>
