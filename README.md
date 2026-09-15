# Automação de Atendimento e Agendamento com IA

Essa é a automação que eu uso hoje em produção com clientes reais. Ela atende, agenda e resolve dúvidas de ponta a ponta no WhatsApp, sem intervenção humana na maioria dos casos.

Não é um bot de FAQ. Ela entende o contexto do negócio, decide sozinha e sabe quando (e como) passar o atendimento pra um humano.

## O que ela faz

**Atendimento por áudio e imagem**
Os clientes não precisam digitar. A automação transcreve e entende áudios, e analisa imagens enviadas (documentos, fotos, comprovantes). A conversa flui como se fosse com uma pessoa.

**Conhecimento do negócio via RAG (Supabase)**
A IA tem acesso a um banco vetorial com documentos da empresa: serviços, preços, procedimentos, políticas. Qualquer dúvida sobre o negócio é respondida com base nesses documentos, não com resposta genérica. O cliente pergunta, a IA consulta e responde certo.

**Segue o padrão de atendimento da empresa**
Antes de qualquer coisa, a automação carrega as instruções de atendimento do negócio — tom de voz, regras, scripts. Ela não atende do jeito que "achar certo", atende do jeito que a empresa atende.

**Leitura de urgência**
Ela identifica quando algo é urgente (dor aguda, emergência, problema sério) e prioriza o atendimento, acelerando o agendamento ou direcionando pro profissional adequado.

**Agendamento inteligente**
- Verifica a disponibilidade real na agenda
- Sugere horários pro cliente
- Marca e desmarca agendamentos
- **Aloca no profissional mais disponível:** ela checa quem está de plantão naquele dia e calcula automaticamente qual profissional tem a agenda mais vazia, priorizando o agendamento com ele. Isso equilibra a carga de trabalho da equipe sem ninguém precisar fazer nada.

**Transferência invisível pra humano**
Quando a IA percebe que a conversa precisa de um humano (caso complexo, cliente irritado, situação fora do padrão), ela transfere o atendimento de forma transparente — o cliente nem percebe que estava falando com uma IA até ali. Muitos clientes dessas empresas simplesmente não sabem.

## Onde ela está rodando

Em produção, hoje, em negócios de nichos diferentes:

- **Clínica Updents** — clínica de saúde com 8+ especialidades (odontologia, medicina, raio-x, acupuntura, biomedicina...). Aqui o foco é triagem, agendamento entre especialidades e alocação de profissionais.
- **Autoescola Duarte** — agendamento de aulas e tirada de dúvidas sobre processos, documentação e pacotes.
- **Petshops** — agendamento de banho, tosa e consultas, com a IA respondendo dúvidas sobre serviços e cuidados.

O core é o mesmo em todos. O que muda é o foco: a configuração, os documentos do RAG e as regras de atendimento se adaptam ao nicho — e é isso que permite escalar a solução pra qualquer negócio que atenda por WhatsApp.

## Stack

- n8n (orquestração do fluxo)
- LLM via API (interpretação, transcrição e visão)
- Supabase (banco vetorial — RAG)
-  API DentailNet - (plataforma de agendamento de clinicas)
- Google Calendar (agendas)
- Webhooks + Evolution API (WhatsApp)
