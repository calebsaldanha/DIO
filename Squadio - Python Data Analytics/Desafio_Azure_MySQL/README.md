# Desafio Módulo 3 – Processamento de Dados Simplificado com Power BI

## Descrição do Desafio

No Desafio do Módulo 3, meu objetivo foi integrar e transformar dados utilizando o Power BI em conjunto com um banco de dados MySQL hospedado no Azure. A tarefa envolveu criar e configurar a instância do banco de dados, importar e transformar os dados no Power BI, e finalmente, construir relatórios informativos para análise.

### Etapas do Desafio

1. **Criação de uma Instância MySQL no Azure**: Configurei uma nova instância de banco de dados MySQL no Azure.
2. **Criação e Configuração do Banco de Dados**: Estabeleci a estrutura do banco de dados, incluindo a criação de tabelas e definição de relacionamentos.
3. **Integração com Power BI**: Conectei o Power BI ao banco de dados MySQL e importei as tabelas necessárias.
4. **Transformação e Limpeza de Dados**: Realizei transformações e limpezas para garantir a integridade dos dados.
5. **Consultas e Análises**: Executei consultas SQL para gerar relatórios e insights a partir dos dados processados.

## Instruções de Configuração

### 1. Criação da Instância MySQL no Azure

1. **Acesse o portal do Azure** e selecione **"Criar um recurso"**.
2. Escolha **"Banco de Dados MySQL"** e clique em **"Criar"**.
3. **Preencha as configurações básicas**, como nome da instância, localização e parâmetros de segurança.
4. **Configure o firewall** para permitir conexões externas, como do Power BI.

### 2. Criação e Configuração do Banco de Dados

1. Após criar a instância, **conectei-me ao banco de dados MySQL** usando MySQL Workbench.
2. **Executei os seguintes scripts SQL** para criar e configurar as tabelas necessárias:

    ```sql
    CREATE TABLE department (
        Dnumber INT PRIMARY KEY,
        Dname VARCHAR(50),
        Mgr_ssn CHAR(9)
    );

    CREATE TABLE employee (
        Ssn CHAR(9) PRIMARY KEY,
        Fname VARCHAR(15),
        Minit CHAR(1),
        Lname VARCHAR(15),
        Bdate DATE,
        Address VARCHAR(30),
        Salary DECIMAL(10, 2),
        Superssn CHAR(9),
        Dno INT,
        FOREIGN KEY (Dno) REFERENCES department(Dnumber)
    );

    CREATE TABLE project (
        Pnumber INT PRIMARY KEY,
        Pname VARCHAR(50),
        Plocation VARCHAR(20),
        Dnum INT,
        FOREIGN KEY (Dnum) REFERENCES department(Dnumber)
    );

    CREATE TABLE works_on (
        Essn CHAR(9),
        Pno INT,
        Hours DECIMAL(4, 1),
        PRIMARY KEY (Essn, Pno),
        FOREIGN KEY (Essn) REFERENCES employee(Ssn),
        FOREIGN KEY (Pno) REFERENCES project(Pnumber)
    );
    ```

### 3. Conexão do Power BI ao MySQL

1. Abri o **Power BI Desktop** e selecionei **"Obter Dados"**.
2. Escolhi a opção **"MySQL database"** e inseri as credenciais da minha instância do Azure.
3. **Configurei a conexão** e selecionei as tabelas que precisava importar para análise.

## Transformações e Limpeza de Dados

### 1. Verificação de Cabeçalhos e Tipos de Dados

- Verifiquei e ajustei os cabeçalhos e tipos de dados importados para garantir que estivessem corretos.
- Ajustei tipos de dados no Power BI, especialmente para valores monetários e datas.

### 2. Tratamento de Valores Nulos

- Identifiquei valores nulos e substituí ou eliminei conforme necessário, utilizando o Power Query Editor.

### 3. Verificação e Correção de Dados

- Corrigi inconsistências como funcionários sem gerentes e departamentos sem gerentes usando transformações no Power Query Editor.

### 4. Transformações Adicionais

- **Mesclei Tabelas** para criar uma tabela de `employee` com o nome dos departamentos associados.
- **Eliminei Colunas Desnecessárias** que não eram relevantes para a análise.
- **Agrupei os Dados** por gerente para contar o número de colaboradores por gerente.
- **Concatenatei Nomes e Departamentos** para criar visualizações mais significativas.

## Consultas SQL

### Exemplos de Consultas

Durante o desafio, executei as seguintes consultas SQL para manipulação e verificação dos dados:

```sql
-- Consultas para verificar e manipular dados
SELECT * FROM employee;
SELECT Ssn, COUNT(Essn) FROM employee e JOIN dependent d ON e.Ssn = d.Essn GROUP BY e.Ssn;
SELECT * FROM dependent;

-- Informações dos empregados
SELECT Bdate, Address FROM employee WHERE Fname = 'John' AND Minit = 'B' AND Lname = 'Smith';

-- Departamentos específicos
SELECT * FROM departament WHERE Dname = 'Research';

-- Funcionários em departamentos específicos
SELECT Fname, Lname, Address FROM employee JOIN departament ON Dnumber = Dno WHERE Dname = 'Research';

-- Projetos em Stafford
SELECT Pnumber, Dnum, Lname, Address, Bdate FROM project JOIN departament ON Dnum = Dnumber JOIN employee ON Mgr_ssn = Ssn WHERE Plocation = 'Stafford';
