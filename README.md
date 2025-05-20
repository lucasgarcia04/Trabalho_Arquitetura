# Documentação dos Serviços 

# Integrantes:
Gabriel Faria, João Victor Salim, Lucas Garcia, Maisa Pires, Maria Eduarda Gonçalves, Miguel Vieira e Pedro Lucas Sousa

## 1. Serviços

- **Criar Conta On-line**
- **Pagar Boleto**
- **Solicitação de Cartão de Crédito**

---

## 2. Modelagem de Serviços

### Criar Conta On-line

**Objetivo:**  
Permitir que novos usuários abram uma conta digital de forma totalmente remota, com validação automática.

**Consumidores:**  
- App mobile  
- APIs de parceiros (ex: canais de indicação)

**Dados/Sistemas acessados:**  
- Base de dados cadastrais do Nubank  
- Serviço de validação de documentos (OCR, selfie com prova de vida)  
- APIs externas (ex: Serpro, Receita Federal para validação de CPF)  
- Motor de decisão para aprovação automática

---

### Pagar Boleto

**Objetivo:**  
Permitir o pagamento de boletos bancários por meio da conta digital do usuário.

**Consumidores:**  
- App mobile  
- APIs integradas com assistentes (ex: Alexa, Google Assistant)

**Dados/Sistemas acessados:**  
- Validador de código de barras  
- Sistema de saldo e movimentação financeira  
- Integração com sistema de compensação bancária (via SPI, Febraban)  
- Registro do pagamento na base de transações do cliente

---

### Solicitação de Cartão de Crédito

**Objetivo:**  
Permitir que o cliente solicite um cartão de crédito, com avaliação de perfil de crédito e limite inicial.

**Consumidores:**  
- App mobile  
- APIs internas do time de atendimento ou onboarding

**Dados/Sistemas acessados:**  
- Dados cadastrais do cliente  
- Histórico de uso (se já for cliente Nubank)  
- Bureaus de crédito (Serasa, Boa Vista, SPC)  
- Motor de decisão para concessão de crédito  
- Sistema de emissão de cartões (virtual e físico)

---

## 3. Diagrama

![image](https://github.com/user-attachments/assets/33c784c1-1b84-4aff-9139-936bee9021c7)


## 4. Considerações Finais

# Benefícios do uso de SOA:
- Reutilização: Serviços como o de verificação de documentos podem ser reaproveitados em múltiplas jornadas (conta, cartão, reemissão etc.).
- Escalabilidade: Cada serviço pode escalar independentemente conforme o volume de requisições.
- Flexibilidade e Agilidade: Novos canais ou funcionalidades podem reutilizar os serviços já existentes sem reescrita de lógica.

# Desafios para produção:
- Baixa latência: Garantir desempenho mesmo com múltiplas chamadas em cadeia.
- Monitoramento e logs distribuídos: Essencial para rastrear falhas em serviços encadeados.
- Segurança e autenticação: Proteção de dados sensíveis e validação robusta de identidade.
- Versionamento de APIs: Para permitir evolução sem quebrar integrações existentes.
