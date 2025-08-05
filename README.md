# Data Processing API & Worker Service

## 🎯 Objetivo do Projeto

Este projeto tem como objetivo desenvolver um ecossistema simples e funcional, composto por:

1. **API RESTful (C# ASP.NET Core Web API)** – Responsável pelo cadastro, edição, consulta e exclusão de registros de **Clientes**.
2. **Worker Service (Windows Service)** – Serviço que consome uma tabela de **Dados a Processar**, realiza requisições na API para processar esses dados e atualiza o status dos registros.

## 🧑‍💻 Tecnologias Utilizadas
- ASP.NET Core Web API (.NET 6 ou superior)
- .NET Core Worker Service
- SQL Server (ou SQLite para simplicidade)
- Entity Framework Core

## 🎓 Conceitos Praticados
- Padrões Repository, Service e ViewModels
- Separação de camadas (API, Domain, Application, Infrastructure)
- Criação e consumo de APIs RESTful
- Criação de um Worker Service rodando como Windows Service
- Processamento assíncrono com Tasks e HttpClient
- Boas práticas de Clean Code e SOLID Principles

## 🗂 Estrutura do Projeto

| Projeto      | Tecnologia                | Nome do Projeto (Sugerido)      |
|--------------|---------------------------|---------------------------------|
| API          | ASP.NET Core Web API       | `CustomerManagement.API`        |
| Worker       | .NET Core Worker Service   | `DataProcessor.Worker`          |
| Banco de Dados | SQL Server / SQLite      | `Database`                      |

### API - CustomerManagement.API
Responsável pela gestão de **Clientes**:
- Endpoints: GET, POST, PUT, DELETE
- Implementação dos padrões Repository e Service
- Uso de ViewModels para entrada e saída de dados

### Worker - DataProcessor.Worker
Serviço em background que:
- Lê a tabela **Dados a Processar**
- Realiza chamadas HTTP para a API
- Atualiza o status do processamento
- Implementado para rodar como **Windows Service**

## 🏗 Estrutura de Pastas
/src
/CustomerManagement.API
/DataProcessor.Worker
/Domain
/Application
/Infrastructure
/database
Script.sql


## 🚀 Como Executar o Projeto

### Pré-requisitos
- .NET 6 SDK ou superior
- PostgreSQL
- Visual Studio 2022 ou Visual Studio Code

### Passos:
1. **Clone o repositório**
    ```bash
    git clone https://github.com/seu-usuario/DataProcessingAPI-Worker.git
    ```

2. **Configure o Banco de Dados**
    - Execute o script `Script.sql` para criar as tabelas iniciais.
    - Ajuste a string de conexão no `appsettings.json` da API e do Worker.

3. **Execute a API**
    ```bash
    cd src/CustomerManagement.API
    dotnet run
    ```

4. **Execute o Worker**
    ```bash
    cd src/DataProcessor.Worker
    dotnet run
    ```

5. **Testar os Endpoints**
    - Acesse o Swagger UI: `https://localhost:{porta}/swagger`
    - Endpoints disponíveis:
        - GET /api/customers
        - POST /api/customers
        - PUT /api/customers/{id}
        - DELETE /api/customers/{id}

## 📂 Estrutura das Tabelas (Exemplo)

### Tabela: Customers
| Id  | Name           | Email              | CreatedAt          |
|-----|----------------|--------------------|-------------------|
| 1   | João da Silva  | joao@email.com     | 2025-08-04 10:00  |

### Tabela: DataToProcess
| Id  | CustomerId  | DataField  | Status    | ProcessedAt        |
|-----|-------------|------------|-----------|--------------------|
| 1   | 1           | "ABC123"   | Pending   | NULL               |

## 🛠 Funcionalidades Implementadas
- [] CRUD de Clientes via API
- [] Processamento de dados via Worker Service
- [] Atualização do status dos dados processados
- [] Separação de responsabilidades em camadas
- [] Comunicação entre serviços (API e Worker)
- [] Execução do Worker como Windows Service (produção)

## 📋 Roadmap Futuro (Evoluções Sugeridas)
- [ ] Adicionar autenticação JWT na API
- [ ] Implementar fila de mensagens (RabbitMQ ou Azure Queue)
- [ ] Dashboard de monitoramento de processos
- [ ] Logs estruturados com Serilog
- [ ] Deploy do Worker como serviço no Windows Installer (ou Linux Daemon)

## 🤝 Contribuição
Sinta-se à vontade para abrir issues, sugerir melhorias ou enviar pull requests!