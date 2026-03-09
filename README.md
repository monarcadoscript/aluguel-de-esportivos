# aluguel-de-carros
O sistema proposto tem como objetivo gerenciar as operações de uma locadora de veículos, permitindo o controle de clientes, funcionários, contratos de locação, reservas e veículos disponíveis.

Para melhorar a organização dos dados, foi criado um catálogo de carros contendo os modelos disponíveis, suas categorias e o valor da diária. Os veículos físicos são registrados separadamente com suas placas e status de disponibilidade.

O sistema também registra qual funcionário realizou o atendimento ao cliente, permitindo melhor controle das operações e qualidade no serviço prestado.
## car rental

O projeto car rental consiste no desenvolvimento inicial de um banco de dados relacional para um aplicativo de aluguel de carros voltado para motoristas de aplicativos.

O objetivo geral do sistema é registrar informações básicas sobre clientes, veículos e contratos de aluguel, servindo como base para futuras implementações e regras de negócio.

O público-alvo são empresas de aluguel de veículos e motoristas que utilizam carros alugados para trabalhar com aplicativos de transporte.
## Estrutura inicial do projeto

| Marca      | Modelo  | Tipo  | Diária |
| ---------- | ------- | ----- | ------ |
| Toyota     | Corolla | Sedan | R$180  |
| Chevrolet  | Onix    | Hatch | R$120  |
| Hyundai    | HB20    | Hatch | R$115  |
| Jeep       | Compass | SUV   | R$250  |
| Volkswagen | T-Cross | SUV   | R$210  |
| Fiat       | Argo    | Hatch | R$110  |
| Honda      | Civic   | Sedan | R$200  |

alugarcar/

├── README.md

├── docs/

│       └── modelo_dados.png

├── db/



├── diagramas/

│     └── modelo_dados.mmd

├── schema/

│          └── create_tables.sql

│  └── seeds/

│                     └── dados_iniciais.sql
## Versão do projeto

Versão 2.0 – Estrutura inicial do banco de dados e documentação do projeto.
## Modelo de Dados

```mermaid
erDiagram

    CLIENTE {
        int id_cliente
        string nome
        string sobrenome
        string cpf
        string telefone
        string email
        string endereco
    }

    FUNCIONARIO {
        int id_funcionario
        string nome
        string cargo
        string telefone
        string email
    }

    CATEGORIA {
        int id_categoria
        string nome_categoria
        string descricao
    }

    CATALOGO_CARROS {
        int id_catalogo
        string marca
        string modelo
        int ano
        float valor_diaria
        int id_categoria
    }

    VEICULO {
        int id_veiculo
        string placa
        string cor
        string status
        int id_catalogo
    }

    CONTRATO {
        int id_contrato
        string numero_contrato
        date data_contrato
        date inicio
        date fim
        string tipo_pagamento
        float valor_total
        int id_cliente
        int id_veiculo
        int id_funcionario
    }

    RESERVA {
        int id_reserva
        date data_reserva
        date data_inicio
        date data_fim
        string status
        int id_cliente
        int id_catalogo
    }

    CLIENTE ||--o{ CONTRATO : realiza
    FUNCIONARIO ||--o{ CONTRATO : registra
    VEICULO ||--o{ CONTRATO : alugado_em
    CATEGORIA ||--o{ CATALOGO_CARROS : classifica
    CATALOGO_CARROS ||--o{ VEICULO : possui
    CLIENTE ||--o{ RESERVA : faz
    CATALOGO_CARROS ||--o{ RESERVA : reservado

