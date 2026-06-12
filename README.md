# 💳 Payment Gateway API Automation Suite

[![Newman Automated API Tests](https://github.com/GabrielDSpec/payment-api-automation/actions/workflows/api-tests.yml/badge.svg)](https://github.com/GabrielDSpec/payment-api-automation/actions/workflows/api-tests.yml)

## 🎯 Objetivo do Projeto
Este repositório contém uma suite de testes automatizados desenvolvida para validar fluxos críticos em ecossistemas de pagamentos e adquirência. O foco é garantir a integridade dos dados, segurança e resiliência em operações financeiras (Autorização, Captura, Tokenização e Estorno).

## 🛠️ Arquitetura e Tecnologias
- **Postman:** Estruturação das coleções e requisições HTTP.
- **JavaScript:** Scripts de pré-requisição e validação (Test Scripts).
- **Newman:** Execução automatizada da suite via linha de comando (CLI).
- **Node.js:** Ambiente de execução.

## 🌐 Gateways Integrados
- **Stripe:** Validação de fluxos transacionais (Auth, Capture, Refund) utilizando arquitetura `x-www-form-urlencoded`.
- **PayPal:** Implementação robusta de integração via **OAuth2**, incluindo a geração dinâmica de *Access Tokens* e encadeamento de ordens (Order Creation -> Order Capture).

## 🧪 Casos de Teste Mapeados
1. **Segurança e Autenticação:** Handshake via OAuth2 (Client Credentials Grant) com gestão dinâmica de escopos (Scopes).
2. **Fluxo de Autorização:** Simulação de transações aprovadas e negadas (validação de payloads JSON e status codes).
3. **Gestão de Transações:** Encadeamento de requisições (*API Request Chaining*) para extração de IDs de ordens e processamento de capturas.
4. **Data Integrity:** Injeção de dados randomizados (random amount) em payloads, garantindo a validação de tipos de dados.

## 🚀 Como Executar Localmente
Para rodar esta suite de testes na sua máquina, certifique-se de ter o [Node.js](https://nodejs.org/) instalado.

1. Instale o Newman globalmente:
   npm install -g newman
Execute a coleção:
newman run nome_do_arquivo_da_colecao.json