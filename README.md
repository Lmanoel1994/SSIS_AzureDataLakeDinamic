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
11 - Selecione a sua tabelas 
![alt text](https://github.com/Lmanoel1994/SSIS_AzureDataLakeDinamic/blob/master/Pictures/4.png) 

# 6 - Azure Data Lake
12 - Selecione  o componente Azure Data Lake Store Destination  <br />
13 - Faça a conexao do Origem Ole DB com o Azure Data Lake Store Destination e abra o Azure Data Lake Store Destination  <br />
14 - Azure Data Lake Store Connection Manager  clique  New para fazer a conexao  <br />
15 - ADLS Host coloque os dados do seu Azure (servidor, User Name , Password) <br />
16 - Teste a conexão  <br />
![alt text](https://github.com/Lmanoel1994/SSIS_AzureDataLakeDinamic/blob/master/Pictures/5.png) 
