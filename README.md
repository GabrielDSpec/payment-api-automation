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


## 💳 PayPal Integration Status

A integração com a API do PayPal (`v2/checkout/orders`) está implementada e validada para o fluxo de **Autorização**.

### ⚠️ Limitações do Ambiente Sandbox
Devido às políticas de segurança do PayPal Sandbox (que exigem consentimento do pagador via interface/browser para a captura), o ambiente de testes automatizados (CI/CD) não possui a permissão *Advanced Credit and Debit Card Payments* ativa para realizar capturas sem intervenção manual.

### 🛡️ Estratégia de Testes (Security-First)
Como a automação não realiza login interativo, a suíte de testes valida a **integridade da segurança da API**:
- **Create Order:** Valida a criação bem-sucedida da ordem com `intent: "AUTHORIZE"`.
- **Capture Authorization:** O teste valida que a tentativa de captura de uma ordem não aprovada retorna o erro `ORDER_NOT_APPROVED` (HTTP 422). 
- **Conclusão:** O pipeline valida que a API está operando corretamente ao rejeitar transações não autorizadas, garantindo que a regra de segurança do PayPal está sendo respeitada.



### 🚀 Roadmap de Evolução
* **Migração de API:** Em futuras sprints, o projeto migrará a integração de pagamentos para provedores mais flexíveis (como **Mercado Pago** ou **PagBank**), que disponibilizam *mocking* nativo e cartões de teste de fácil manipulação, permitindo fluxos E2E de captura sem as restrições de *Payer Consent* do PayPal.