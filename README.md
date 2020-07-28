# SSIS_AzureDataLakeDinamic
Como criar arquivos historicos no Azure **Data Lake**
Ultilizando **Integration Services** 

# 1 - Instalação do SSIS e Pack Azure: <br> 
1-**Integration services**  <br />
https://marketplace.visualstudio.com/items?itemName=SSIS.SqlServerIntegrationServicesProjects <br />

2-**Pack Azure**  <br />
https://docs.microsoft.com/pt-br/sql/integration-services/azure-feature-pack-for-integration-services-ssis?view=sql-server-ver15 <br />

# 2 - Criar um Pacote do  Integration Services  
1 - Arraste uma Tarefa de **Fluxo de Dados** para tela  <br />
2 - Abra a Tarefa de Fluxo de Dados para ir ao **DataFlow** <br />
![alt text](https://github.com/Lmanoel1994/SSIS_AzureDataLakeDinamic/blob/master/Pictures/1.png) 

# 3 -  Conexão 
3 - Adicione uma conexão **Origem OLE DB**  <br />
4 - Abra a conexão  <br />
5 - Clique em **New** para busca uma nova conexão  <br />
6 - Clique em **New** Novamente para criar a Conexão   <br />
![alt text](https://github.com/Lmanoel1994/SSIS_AzureDataLakeDinamic/blob/master/Pictures/2.png) 

# 4 - Conexão com o Banco
7 - **Provider**  selecione o seu banco (SQL Server)  <br />
8 - **Server name** coloque o seu servidor (estou usando o local) <br />
9 - Selecione a sua **database** <br />
10 - teste a conexão  <br />
![alt text](https://github.com/Lmanoel1994/SSIS_AzureDataLakeDinamic/blob/master/Pictures/3.png) 

# 5 - Tabela
11 - Selecione a sua **tabela**  <br />
![alt text](https://github.com/Lmanoel1994/SSIS_AzureDataLakeDinamic/blob/master/Pictures/4.png) 

# 6 - Azure Data Lake
12 - Selecione  o componente **Azure Data Lake Store Destination** e arraste para tela  <br />
13 - Faça a conexao do **Origem Ole DB** com o **Azure Data Lake Store Destination**  e abra o **Azure Data Lake Store Destination**  <br />
14 - **Azure Data Lake Store Connection Manager**  clique  **New** para fazer a conexao  <br />
15 - **ADLS Host** coloque os dados do seu Azure **(servidor, User Name , Password)** <br />
16 - Teste a conexão  <br />
![alt text](https://github.com/Lmanoel1994/SSIS_AzureDataLakeDinamic/blob/master/Pictures/5.png) 

# 7 - Warning
17 - Irá aparece um **Warning** informando que o File Path está em branco, apenas clique em OK
![alt text](https://github.com/Lmanoel1994/SSIS_AzureDataLakeDinamic/blob/master/Pictures/6.png) 

# 8 - Variaveis 
18 - Clique no icone de **variavel** (onde está sinalizado na imagem)   <br />
19 - Clique no icone de **criação de variavel** para poder criar a variavel escolha um **nome** e **tipo** (String sem valor) (onde está sinalizado na imagem)   <br />
20 - Clique nos **[...]** para abrir  o **Expression Builder**  <br />
![alt text](https://github.com/Lmanoel1994/SSIS_AzureDataLakeDinamic/blob/master/Pictures/7.png) 

# 9 - Caminho do DataLake 
21 - EM Expression  e digite :  <br />
"**Teste/Parcelas**"+"_0"+ <br /> 
(DT_WSTR, 4)  DATEPART("DD",GetDate())+ <br />
"-0"+ (DT_WSTR, 4)  DATEPART("MM",GetDate())+ <br />
"-"+(DT_WSTR, 4)  DATEPART("YYYY",GetDate()) <br />
+"_"+(DT_WSTR, 4)  DATEPART("HH",GetDate())+ <br />
" -"+(DT_WSTR, 4)  DATEPART("MI",GetDate())+"**.csv"** <br />

**O codigo é para definimos o caminho  do Data Lake e o tipo de arquivo que iremos salvar com a data/hora e minutos** <br />
 O codigo está basicamente criando uma pasta no meu **Data Lake** chamada de **Teste** e dentro da pasta esta criando um arquivo com a data e Hora do computador  deixando o nome como  **Parcelas_04-06-2020_19-16.csv** <br />

**OBS/; se quiser mudar o nome do diretorio ou do arquivo basta alterar o nome de 'Teste' e 'Parcela' do codigo** <br />

**Depois clique em Evaluate Expression para ver o resultado**
No meu caso ficou **Teste/Parcelas_04-06-2020_19-16.csv**
Então no Meu **Data lake** tera uma pasta chamada **Teste** e dentro da pasta tera o arquivo chamado **Parcelas_04-06-2020_19-16.csv**
e de o OK
 <br />
![alt text](https://github.com/Lmanoel1994/SSIS_AzureDataLakeDinamic/blob/master/Pictures/8.png) 

# 10 - Control Flow  
22 - Volte para o **Control Flow**, clique com o botão direito no componente **Tarefa Fluxo de Dados**
 <br />
23 - Clique em **Propriedades**
<br />
![alt text](https://github.com/Lmanoel1994/SSIS_AzureDataLakeDinamic/blob/master/Pictures/9.png) 
<br />

# 11 - Expression Builder  
24 - Nas propriedades clique nos  **[...]** <br />
25 - Irá aparecer uma janela de  propriedade de expresões, em **Propety** selecione a **[Azure Data Lake Store Destination].[FilePath]** <br />
26 - Em **Expressions** clique **[...]**  <br />
27 - Irá aparecer uma janela de **Expression Builder**, Selecione a Variavel que foi criada **(File_Path)** <br />
28 -  Arraste a variavel para **Expression**  e clique em **Evaluate Expression** e cliquem OK <br />
![alt text](https://github.com/Lmanoel1994/SSIS_AzureDataLakeDinamic/blob/master/Pictures/10.png) 

 <br />
 #12 -Data lake Config <br />
 29 - Clique em **DataFlow** <br />
 30 -  Abra o **Azure Data Lake Store Destination** , Veja que em **File Path** já vai está preenchido <br />

 
![alt text](https://github.com/Lmanoel1994/SSIS_AzureDataLakeDinamic/blob/master/Pictures/11.png) <br />

31 - Vá em **Mappings**  para Mapear as colunas  <br />
![alt text](https://github.com/Lmanoel1994/SSIS_AzureDataLakeDinamic/blob/master/Pictures/12.png)  <br />


# 14 - Excutando o pacote  
32 - Execute o Pacote  <br />
![alt text](https://github.com/Lmanoel1994/SSIS_AzureDataLakeDinamic/blob/master/Pictures/13.png)  <br />

Veja que no Data Lake foi criado  a Pasta **Teste** e dentro dela o Arquivo de chamado **Parcelas_04_06_2020_19-21.csv**
![alt text](https://github.com/Lmanoel1994/SSIS_AzureDataLakeDinamic/blob/master/Pictures/14.png)  <br />
Toda vez que rodar o pacote irá criar um novo arquivo com a data,hora e segundos,  dentro na mesma pasta 
![alt text](https://github.com/Lmanoel1994/SSIS_AzureDataLakeDinamic/blob/master/Pictures/15.png)  <br />








