🌐 SDR de IA — Workflow N8N

Um SDR Conversacional de IA desenvolvido em N8N, capaz de qualificar leads, entender diferentes formatos de mensagem, manter contexto e agendar reuniões automaticamente no Google Calendar.

⚡ Visão Geral

Este workflow atua como um SDR automatizado, realizando:

Atendimento inicial via WhatsApp

Interpretação de texto, áudio, imagem e PDF

Respostas inteligentes usando LLM

Memória conversacional (Redis)

Sugestão e captura de horários

Agendamento automático no Google Calendar

Envio de confirmação estruturada ao usuário

Tudo orquestrado sem intervenção humana.

🔁 Fluxo (Resumo)
📥 WhatsApp → 🔀 Identificação do Formato → 🎧 Transcrição/OCR
     → 🤖 Agente de IA (LLM) → 🧠 Memória (Redis)
     → 🗓️ Verificação de Agenda → 📅 Criação do Evento
     → 📩 Confirmação via WhatsApp

🧱 Componentes Principais
1. Recepção de Mensagens

Webhook N8N para receber mensagens do WhatsApp

Suporte a texto, áudio, imagem, PDF

2. Processamento Multimodal

Áudio → transcrição (OpenAI Whisper)

Documentos → retorno padronizado

Texto → enviado direto ao LLM

3. Agente de IA (LLM)

Analisa intenção

Qualifica lead

Identifica informações de reunião

Mantém coerência e fluxo conversacional

4. Memória Conversacional

Redis com chave por número do lead

Mantém contexto de últimas mensagens

5. Agendamento Automático

Verificação de disponibilidade no Calendar

Criação do evento com:

horário

descrição

participante

link de reunião

6. Confirmação via WhatsApp

IA gera mensagem de confirmação

Envio automático pelo provedor WhatsApp API

🛠 Tecnologias Utilizadas

N8N

OpenAI Whisper / LLM

DeepSeek (respostas auxiliares)

Redis

Google Calendar API

Z-API / WhatsApp API

🚀 Destaques do Workflow

Conversa fluida com memória

Totalmente multimodal

Agendamento sem intervenção manual

Arquitetura limpa e modular

Fácil de adaptar para qualquer empresa ou contexto
