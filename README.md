<h1 align="left">Um resumo sobre o Apache Iceberg</h1>

<h2>Data Lakehouse</h2>

<p>O Iceberg é especialmente útil na arquitetura Data Lakehouse, assim, é fundamental entender esse conceito e, como o próprio nome diz, é uma junção de outras duas arquiteturas: o Data Lake e o Data Warehouse. Então, vamos ver um pouco sobre cada uma.</p>
<p>O Data Warehouse garante a qualidade dos dados e escalabilidade com seu sistema de armazenamento indexado e particionado, porém, por só permitir dados estruturados, acaba sendo muito custoso e pouco flexível.</p>
<p>Por outro lado, o Data Lake é um armazenamento que permite diferentes tipos de formatos de arquivos, trazendo consigo uma melhora no desempenho de consulta, além dos benefícios da interoperabilidade. Contudo, ele não consegue garantir a qualidade dos dados nem dá suporte a transações ACID.</p>
<p>Assim nasceu o Data Lakehouse, uma junção desses dois sistemas de armazenamento de dados. Ou seja, traz as propriedades ACID e a qualidade do Data Warehouse, ao mesmo tempo que tem baixos custos, aceita vários formatos de dados e possui a interoperabilidade do Data Lake. Além disso, essa arquitetura também suporta versionamento, possui um histórico que pode gerar relatórios e permite que diferentes processos podem utilizar os mesmos dados.</p>
<p>Aí surge uma pergunta: como isso é possível? Bom, isso é o resultado da junção de Open File Format e Open Table Format. Essa dupla combina um armazenamento eficiente e flexível (considerando que os Open File Format comprimem os dados e aceitam dados estruturados ou não) com funcionalidades de transação, versionamento e governança fornecidas pelo Open Table Format.</p>

<h2>Open Table Format</h2>
  
<h2>Apache Iceberg</h2>

<h3>Históriat</h3>

<h3>Arquitetura</h3>
