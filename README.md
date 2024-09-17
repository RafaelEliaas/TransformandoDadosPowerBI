## Desafio de Projeto - Processando e Transformando dados com Power BI

Etapas de Transformação de Dados no Desafio – Processamento de Dados Simplificado com Power BI

Após a criação da instância na Azure para MySQL, criei o banco de dados e inseri os dados por meio do Cloud Shell diretamente no site da Azure. Em seguida, fiz a integração do Power BI com o MySQL no Azure. Após a etapa de extração, iniciei o processo de transformação dos dados. Com base nas 6 tabelas originais da atividade, foram geradas outras 6, detalhadas abaixo, com os respectivos tratamentos realizados:

  1 - Gerente por Departamentos: Utilizei a mescla de consultas para gerar uma nova tabela a partir da união das tabelas “azure_company.department” e “azure_company.employee” pelas colunas “Mgr_ssn” e “Ssn”. Assim, obtive os nomes dos gerentes de departamento, excluindo as colunas desnecessárias.

  2 - Localização de Departamentos: A mescla de consultas foi usada para gerar uma nova tabela com a união das tabelas “azure_company.department” e “azure_company.dept_locations” pelas colunas “Dnumber” em ambas. O resultado foi uma tabela com os nomes dos departamentos e suas respectivas localizações. O único departamento com mais de uma localização é o “Research”. Excluí as colunas não necessárias.

  3 - Funcionários por Departamento: Novamente, utilizei a mescla de consultas para unir as tabelas “azure_company.employee” e “azure_company.department” pelas colunas “Dno” e “Dnumber”. Isso gerou uma tabela com os nomes de todos os funcionários e seus respectivos departamentos. O departamento "Research" possui 4 funcionários, "Administration" tem 3 e "Headquarters" conta com 1 funcionário. Excluí as colunas desnecessárias.

  4 - Gerentes por Funcionários: A mescla de consultas foi aplicada para unir as tabelas “azure_company.employee” e a tabela “Gerente por Departamentos” pelas colunas “Ssn” e “Super_ssn”. O resultado foi uma tabela com os nomes dos gerentes e, na segunda coluna, os nomes dos 7 funcionários (exceto o gerente geral). As colunas desnecessárias foram excluídas.

  5 - Horas de Projeto: Utilizei a mescla de consultas para unir as tabelas “azure_company.project” e “azure_company.works_on” pelas colunas “Pnumber” e “Pno”. O resultado foi uma tabela com os nomes dos projetos e 16 linhas de horas trabalhadas. Excluí as colunas irrelevantes e deixei apenas os nomes dos projetos e as horas. Em seguida, apliquei a função “Coluna Dinâmica” para somar as horas por projeto, o que transformou os projetos em colunas. Para corrigir, utilizei a função “Transformar Colunas em Linhas”, resultando em duas colunas: uma com os nomes dos projetos e outra com o total de horas dedicadas a cada projeto.

  6 - Dependentes por Funcionário: A mescla de consultas foi utilizada para unir as tabelas “azure_company.employee” e “azure_company.dependent” pelas colunas “Ssn” e “Essn”. Isso resultou em uma tabela com os nomes dos funcionários e seus respectivos dependentes. Filtrei os valores nulos, sobrando apenas 3 funcionários. Excluí as colunas desnecessárias e apliquei a função “Coluna Dinâmica” para somar os dependentes por funcionário. Isso gerou uma tabela onde os nomes dos funcionários estavam nas colunas e a quantidade de dependentes nas linhas. Utilizei a função “Transformar Colunas em Linhas”, obtendo uma tabela final com os nomes dos 3 funcionários e a quantidade de dependentes.
