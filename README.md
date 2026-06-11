# 💳 Payment Gateway API Automation Suite

## 🎯 Objetivo do Projeto
Este repositório contém uma suite de testes automatizados desenvolvida para validar fluxos críticos em ecossistemas de pagamentos e adquirência. O foco é garantir a integridade dos dados, segurança e resiliência em operações financeiras (Autorização, Captura, Tokenização e Estorno).

## 🛠️ Arquitetura e Tecnologias
- **Postman:** Estruturação das coleções e requisições HTTP.
- **JavaScript:** Scripts de pré-requisição e validação (Test Scripts).
- **Newman:** Execução automatizada da suite via linha de comando (CLI).
- **Node.js:** Ambiente de execução.

## 🧪 Casos de Teste Mapeados
1. **Health Check & Autenticação:** Validação da geração de tokens OAuth2.0 / Bearer.
2. **Fluxo de Autorização:** Simulação de transações aprovadas e negadas (validação de *status codes* e *payloads* de resposta).
3. **Estorno (Refund):** Validação de regras de negócio para devoluções parciais e totais.
4. **Segurança:** Testes de injeção de dados inválidos (Data Type Validation) e validação de cabeçalhos de segurança (OWASP).

## 🚀 Como Executar Localmente
*(Instruções a serem adicionadas após configurarmos o Newman)*