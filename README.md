# SSIS_AzureDataLakeDinamic
Criar planilhas Historicas no Azure Datalake 
ultilizando Integration Services 

# 1 - Instalação do Pack: <br> 
https://docs.microsoft.com/pt-br/sql/integration-services/azure-feature-pack-for-integration-services-ssis?view=sql-server-ver15

# 2 - Criar um Pacote do  Integration Services  
1 - Adicione uma Tarefa de Fluxo de Dados
2 - Abra a Tarefa de Fluxo de Dados para ir ao DataFlow

![alt text](https://github.com/Lmanoel1994/SSIS_AzureDataLakeDinamic/blob/master/Pictures/1.png) 

# 3 -  Conexão 
3 - Adicione uma conexão Origem OLE DB  <br />
4 - Abra a conexão  <br />
5 - Clique em New para busca uma nova conexão  <br />
6 - Clique em New Novamente para criar a Conexão   <br />
![alt text](https://github.com/Lmanoel1994/SSIS_AzureDataLakeDinamic/blob/master/Pictures/2.png) 

# 4 - Conexão com o Banco
7 - Provider  selecione o seu banco (SQL Server)  <br />
8 - Server name coloque o seu servidor (estou usando o local) <br />
9 - Selecione a sua database <br />
10 - teste a conexão  <br />
![alt text](https://github.com/Lmanoel1994/SSIS_AzureDataLakeDinamic/blob/master/Pictures/3.png) 

# 5 - Tabela
11 - Selecione a sua tabelas  <br />
![alt text](https://github.com/Lmanoel1994/SSIS_AzureDataLakeDinamic/blob/master/Pictures/4.png) 

# 6 - Azure Data Lake
12 - Selecione  o componente Azure Data Lake Store Destination  <br />
13 - Faça a conexao do Origem Ole DB com o Azure Data Lake Store Destination e abra o Azure Data Lake Store Destination  <br />
14 - Azure Data Lake Store Connection Manager  clique  New para fazer a conexao  <br />
15 - ADLS Host coloque os dados do seu Azure (servidor, User Name , Password) <br />
16 - Teste a conexão  <br />
![alt text](https://github.com/Lmanoel1994/SSIS_AzureDataLakeDinamic/blob/master/Pictures/5.png) 

# 7 - Warning
17 - Irá aparece um Warning informando que o File Path está em branco, apenas clique em OK
![alt text](https://github.com/Lmanoel1994/SSIS_AzureDataLakeDinamic/blob/master/Pictures/6.png) 

# 8 - Variaveis 
18 - Clique no icone onde está sinalizado na imagem  <br />
19 - Clique no icone onde está sinalizado na imagem para poder criar a variavel escolha um nome e tipo  String sem valor  <br />
20 - Clique nos [...] para abrir  o Expression Builder  <br />
![alt text](https://github.com/Lmanoel1994/SSIS_AzureDataLakeDinamic/blob/master/Pictures/7.png) 

# 9 - Caminho do DataLake 
21 - EM Expression  e digite :  <br />
"**Teste/Parcelas**"+"_0"+ <br /> 
(DT_WSTR, 4)  DATEPART("DD",GetDate())+ <br />
"-0"+ (DT_WSTR, 4)  DATEPART("MM",GetDate())+ <br />
"-"+(DT_WSTR, 4)  DATEPART("YYYY",GetDate()) <br />
+"_"+(DT_WSTR, 4)  DATEPART("HH",GetDate())+ <br />
" -"+(DT_WSTR, 4)  DATEPART("MI",GetDate())+"**.csv"** <br />

**O codigo é para definimos o caminho  do DataLake e o tipo de arquivo que iremos salvar com a data hora e minutos** <br />
 O codigo está basicamente esta criando uma pasta no meu Dataleke chamada **Teste** e dentro da pasta esta criando um arquivo com a data e Hora do computador  deixando o nome como  **Parcelas_04-06-2020_19-16.csv** <br />
**se quiser mudar o nome do diretorio ou do arquivo basta alterar o nome de Teste e Parcela do codigo** <br />

**Depois clique em Evaluate Expression para ver o resultado**
No meu caso ficou **Teste/Parcelas_04-06-2020_19-16.csv**
Então no Meu Dataleke tera uma pasta chamada **Teste** e dentro da pasta tera o arquivo chamado **Parcelas_04-06-2020_19-16.csv**
e de o OK
 <br />
![alt text](https://github.com/Lmanoel1994/SSIS_AzureDataLakeDinamic/blob/master/Pictures/8.png) 

# 10 - Control Flow  
22 - Volte para o Control Flow, clique com o botão direito no componente **Tarefa Fluxo de Dados**
 <br />
23 - Clique em **Propriedades**
<br />
![alt text](https://github.com/Lmanoel1994/SSIS_AzureDataLakeDinamic/blob/master/Pictures/9.png) 

<br />



