# Arquitetura — Fluxo FCG

Este documento descreve o fluxo da arquitetura de microsserviços com AWS API Gateway e Lambda, conforme o modelo FCG.

---

## 🧭 Fluxo de Requisição

1. **Cliente inicia a requisição**  
   O usuário acessa via navegador (desktop ou móvel) e envia uma requisição HTTP.

2. **API Gateway recebe e roteia a requisição**  
   O Amazon API Gateway intercepta a requisição e a encaminha para o serviço adequado.

3. **Autenticação via AWS Lambda**  
   Uma função Lambda é acionada para validar a autenticação da requisição.  
   Se a autenticação for aprovada, a requisição segue para o serviço solicitado.

4. **Execução do serviço requisitado**  
   O serviço demandado processa a requisição e interage com seu próprio banco de dados (isolamento por microserviço).

5. **Comunicação entre microsserviços**  
   Quando necessário, os microsserviços se comunicam entre si por meio de requisições HTTP.

---

## 🏗️ Componentes da Arquitetura

| Componente | Responsabilidade |
|------------|-------------------|
| **Cliente (web / mobile)** | Inicia as requisições HTTP |
| **API Gateway (AWS)** | Recebe e roteia as requisições para os serviços |
| **Lambda de Autorização** | Faz a validação/autenticação da requisição |
| **Serviços (Usuários / Pagamentos / Jogos, etc.)** | Processam a lógica específica e operam sobre seu próprio banco |
| **Bancos de dados (isolados por serviço)** | Cada microsserviço tem seu próprio armazenamento de dados |
| **Comunicação entre serviços** | Realizada via requisições HTTP entre Lambdas / APIs internas |

---

## ✅ Benefícios dessa abordagem

- **Isolamento e independência** de cada serviço  
- **Escalabilidade granular** (cada serviço pode escalar separadamente)  
- **Responsabilidade bem definida** entre autenticação e lógica de negócio  
- **Facilidade para manutenção e evolução** dos serviços de forma modular  

---
<img width="5564" height="4612" alt="image" src="https://github.com/user-attachments/assets/8c42352c-4e99-43c3-8154-8f0a7bd5c387" />


