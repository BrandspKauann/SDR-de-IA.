# 🤖 SDR de IA — Workflow N8N

Um **SDR Conversacional Automatizado**, desenvolvido em **N8N**, capaz de qualificar leads, interpretar diferentes formatos de mensagem e **agendar reuniões automaticamente** usando IA e integrações nativas.

---

## 📌 Visão Geral

Este workflow atua como um **Sales Development Representative (SDR) de IA**, realizando:

- Atendimento inicial via WhatsApp  
- Entendimento de **texto, áudio, imagens e PDF**  
- Processamento com **LLM** (IA generativa)  
- **Memória conversacional** via Redis  
- Sugestão e captura de horários  
- **Criação automática de eventos** no Google Calendar  
- Envio de confirmação estruturada ao usuário  

Tudo de forma 100% automatizada, sem intervenção humana.

---

## 🔁 Arquitetura do Fluxo

```mermaid
flowchart TD

A[📥 Recebimento via WhatsApp] --> B{🔀 Tipo de Mensagem?}

B -->|Texto| C1[📝 Processamento de Texto]
B -->|Áudio| C2[🎧 Transcrição (Whisper)]
B -->|Imagem| C3[🖼️ OCR / Resposta Padrão]
B -->|PDF| C4[📄 Extração / Resposta Padrão]
B -->|Outro| C5[⚠️ Aviso de Formato Inválido]

C1 --> D[🤖 Agente de IA]
C2 --> D
C3 --> D
C4 --> D

D --> E[🧠 Memória (Redis)]
E --> F[📩 Enviar Resposta ao Lead]

F --> G{📅 Lead forneceu horário e e-mail?}

G -->|Sim| H[🗓️ Verificar Agenda - Google Calendar]
H --> I[📅 Criar Evento]
I --> J[🤖 IA de Confirmação]
J --> K[📩 Enviar Confirmação]

G -->|Não| L[⏳ Seguir Fluxo Conversacional]
