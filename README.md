# 🤖 SDR de IA Brandsp – Atendimento e Qualificação via WhatsApp

> **SDR inteligente, consultivo e orientado a agendamento**, operando 100% via WhatsApp com IA, memória de contexto e integração com agenda.

---

## 🧭 Visão Geral

Este workflow implementa o **SDR de IA da Brandsp**, responsável por:

* 📥 Receber mensagens via WhatsApp
* 🔀 Identificar o tipo de conteúdo (texto, áudio, imagem, PDF)
* 🧠 Interpretar e contextualizar mensagens com IA
* 💬 Conduzir conversas de vendas consultivas
* 📅 Agendar reuniões automaticamente
* ✅ Confirmar reuniões em tempo real

O SDR atua como **pré-vendas (Sales Development Representative)**, qualificando leads e encaminhando apenas oportunidades reais para o closer.

---

## 🏗️ Arquitetura Geral

```
[ Lead no WhatsApp ]
          |
          v
[ Webhook WhatsApp ]
          |
          v
[ Separação de Formato ]
  |    |    |    |
 Texto Áudio Img  PDF
  |    |    |    |
  +----+----+----+
          |
          v
[ SDR IA (Contexto + Memória) ]
          |
          v
[ Envio de Resposta ]
          |
          v
[ Verifica Agendamento ]
      |          |
     Não        Sim
      |          |
      v          v
 [ Continua ] [ Google Calendar ]
                     |
                     v
            [ Confirmação WhatsApp ]
```

---

## 🧰 Tecnologias Utilizadas

| Camada       | Tecnologia             | Função                       |
| ------------ | ---------------------- | ---------------------------- |
| Orquestração | **n8n**                | Backend conversacional       |
| Canal        | **WhatsApp (Z-API)**   | Entrada e saída de mensagens |
| IA           | **OpenAI (LangChain)** | Conversa e qualificação      |
| IA Auxiliar  | **DeepSeek**           | Confirmação de reunião       |
| Memória      | **Redis**              | Histórico de conversa        |
| Agenda       | **Google Calendar**    | Agendamento automático       |

---

## 🔌 Entrada – Webhook WhatsApp

**Endpoint:**

```
POST /webhook/sdrbrandsp
```

Recebe eventos do WhatsApp contendo:

* Texto
* Áudio
* Imagem
* Documento (PDF)

---

## 🔀 Separação Inteligente de Formato

**Node:** `Separar Formato do Recebimento`

Identifica automaticamente o tipo de mensagem:

* 📝 Texto
* 🎤 Áudio
* 🖼️ Imagem
* 📄 Documento

Cada formato segue um fluxo específico até ser convertido em **texto interpretável pela IA**.

---

## 🎤 Processamento de Áudio

Fluxo:

```
WhatsApp → Download do áudio → Transcrição (OpenAI) → Texto
```

Permite que o lead fale por áudio normalmente, mantendo a fluidez da conversa.

---

## 🖼️ / 📄 Imagem e PDF

Mensagens com imagem ou documento:

* São identificadas
* Processadas
* Respondidas de forma contextual

> O SDR orienta o lead caso o formato não seja adequado.

---

## 🧠 SDR BRANDSP (Coração do Sistema)

**Node:** `SDR BRANDSP`

A IA assume o papel de **SDR consultivo sênior**, com:

* Persona definida (Brandsp IA)
* Tom profissional, simpático e humano
* Roteiro de vendas estruturado
* Tabela completa de serviços e valores

### Estratégia Conversacional

1. **Mapear dor**
2. **Entender maturidade digital**
3. **Relacionar dor → solução Brandsp**
4. **Apresentar orçamento quando houver interesse**
5. **Propor reunião**

---

## 🧠 Memória Conversacional

**Node:** `Memória REDIS`

* Armazena histórico por número de telefone
* Mantém contexto entre mensagens
* Evita perguntas repetidas
* Permite conversas longas e naturais

---

## 💬 Envio de Respostas

**Node:** `Enviar Mensagem`

* Retorna a resposta da IA via WhatsApp
* Comunicação em tempo real
* Linguagem natural

---

## 📅 Detecção de Agendamento

**Node:** `Agendou reunião?`

Analisa a resposta da IA procurando:

* `start_datetime`
* `end_datetime`
* `email`

Se detectado, o fluxo segue para agendamento automático.

---

## 📆 Agendamento Automático

**Node:** `Agendar Reunião`

* Cria evento no Google Calendar
* Gera link do Google Meet
* Adiciona o e-mail do lead

---

## ✅ Confirmação da Reunião

**Nodes:**

* `IA Confirmação de Reunião`
* `Envio da confirmação`

A IA gera uma mensagem clara contendo:

* Data
* Horário
* Link da reunião

Tudo enviado automaticamente pelo WhatsApp.

---

## 📐 Formulação do Problema

### 🎯 Objetivo

Converter conversas no WhatsApp em **reuniões qualificadas**, sem esforço humano.

---

### 🔢 Variáveis

* **N** = número de conversas
* **M** = mensagens por conversa
* **Cᵢ** = custo por interação de IA
* **R** = taxa de agendamento

---

### ⏱️ Complexidade

* Temporal: **O(N × M)**
* Cada mensagem é processada uma vez

---

### 💰 Custo estimado

```
Custo ≈ N × M × Cᵢ
```

---

## 🌟 Diferenciais do SDR de IA

* Atendimento 24/7
* Zero esquecimento
* Conversa humanizada
* Memória persistente
* Multimodal (texto, áudio, imagem, PDF)
* Agendamento automático

---

## ✅ Conclusão

Este workflow transforma o **n8n em um SDR de IA completo**, capaz de atender, qualificar, vender e agendar reuniões via WhatsApp, com eficiência comparável a times de pré-vendas enterprise.
