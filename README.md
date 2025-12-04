📝 Descrição do Projeto – Modelo Lógico de Banco de Dados da Oficina Mecânica
-----------------------------------------------------------------------------

Este repositório apresenta o **modelo lógico e normalizado** para o sistema de controle e gerenciamento de execução de Ordens de Serviço (OS) em uma oficina mecânica.

O objetivo deste projeto é estruturar a relação entre **Clientes**, **Veículos**, **Equipes de Serviço**, **Ordens de Serviço**, **Peças** e **Serviços (Mão de Obra)**. O modelo garante a **rastreabilidade completa** do histórico de manutenção de cada veículo, o **controle do fluxo de trabalho** (avaliação, autorização e execução) e a **integridade financeira** dos custos.

### O Modelo Define:

*   **✔ Clientes e Veículos**
    
    *   Clientes possuem um relacionamento **1:N** com Veículo.
        
    *   A **Ordem de Serviço** está estritamente ligada ao **Veículo**, permitindo o registro de múltiplas manutenções históricas ao longo do tempo.
        
*   **✔ Execução e Equipes**
    
    *   **Mecânicos** são agrupados em **Equipes**.
        
    *   Cada **Ordem de Serviço** é designada a **uma única Equipe**, responsável por toda a avaliação e execução dos serviços.
        
*   **✔ Histórico Financeiro (Snapshot)**
    
    *   Os custos de **Peças** e **Serviços** são vinculados à **OS** por meio de tabelas _N:N_ (OS\_Peca e OS\_Servico).
        
    *   O campo **Valor\_Cobrado DECIMAL(10,2)** nessas tabelas garante que o preço da peça ou do serviço fique **congelado** (snapshot) no momento da emissão da OS, protegendo os registros de faturamento contra futuras alterações nos catálogos de preços.
        
*   **✔ Controle de Fluxo de Trabalho**
    
    *   A tabela **Ordem\_Servico** inclui o **Status\_OS** (Ex: Aguardando Autorização, Em Execução) e o campo **Cliente\_Autorizou**, garantindo que o serviço só inicie após a aprovação formal do cliente.
        

### 🎯 Objetivo do Modelo

O modelo lógico foi projetado para:

*   Garantir **integridade e consistência** na associação de veículos a OSs (evitando múltiplos serviços ativos não controlados).
    
*   Permitir a **rastreabilidade total** do histórico de manutenção por veículo e por equipe.
    
*   Assegurar a **precisão financeira** através da tipagem correta de dados (DECIMAL para valores monetários).
    
*   Servir como base sólida para a implementação do **modelo físico** em SQL.
    

### 📊 Apresentação do Diagrama

Abaixo está o diagrama lógico em formato PNG que representa a estrutura final do modelo para a Oficina Mecânica:
