# aluguel-de-esportivos
alugue seu carro esportivo aqui, com um custo baixo
## AlugarCar

O projeto AlugarCar consiste no desenvolvimento inicial de um banco de dados relacional para um aplicativo de aluguel de carros voltado para motoristas de aplicativos.

O objetivo geral do sistema é registrar informações básicas sobre clientes, veículos e contratos de aluguel, servindo como base para futuras implementações e regras de negócio.

O público-alvo são empresas de aluguel de veículos e motoristas que utilizam carros alugados para trabalhar com aplicativos de transporte.
## Estrutura inicial do projeto

alugarcar/
├── README.md
├── database/
│   └── modelo_dados.mmd
## Versão do projeto

Versão 1.0 – Estrutura inicial do banco de dados e documentação do projeto.
## Modelo de Dados

```mermaid
erDiagram
    CLIENTE {
        int id_cliente
        string nome
        string sobrenome
        string cpf
        string email
    }
   
    VEICULO {
        int id_veiculo
        string placa
        string marca
        string modelo
        string tipo
    }

    CONTRATO {
        int id_contrato
        string numero_contrato
        date data_contrato
        string tipo_pagamento
        date inicio
        date fim
    }

    CLIENTE ||--o{ CONTRATO : realiza
    VEICULO ||--o{ CONTRATO : utilizado

