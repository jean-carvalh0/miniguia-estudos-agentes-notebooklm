# 🤖 Miniguia: Engenharia de Prompts e Agentes de IA para Triagem de Leads

Este repositório contém o desafio de projeto do bootcamp da DIO, focado no uso do NotebookLM para organizar documentações técnicas sobre construção de Assistentes Virtuais e integrações via API.

## 🎯 Contexto e Objetivos

O tema escolhido é a **Construção de Agentes de IA para Qualificação de Leads**. O foco é entender como parametrizar o comportamento de um LLM para atendimento, evitando falhas comuns em produção.

**Objetivos de Estudo:**
1. Dominar técnicas de Engenharia de Prompts (System Prompts) para assistentes multidisciplinares.
2. Entender os princípios de conexão de IA com a API Oficial do WhatsApp Cloud.
3. Utilizar o NotebookLM para mapear soluções de mitigação de alucinações.

---

## 📚 Curadoria de Fontes

Para alimentar o NotebookLM com dados técnicos e regras de negócio sólidas para a construção do agente, foram selecionados e processados os seguintes materiais (em formato PDF):

1. **Guia Oficial de Prompt Engineering (OpenAI)**: Documentação técnica com as melhores práticas para guiar modelos de linguagem e evitar alucinações.
2. **Documentação da WhatsApp Cloud API (Meta)**: Regras estruturais e de integração para conectar o assistente virtual à mensageria oficial.
3. **Guia de Qualificação de Leads (RD Station)**: Material focado em negócios para instruir a IA sobre os critérios de "Lead Scoring", garantindo que o agente saiba identificar e classificar a intenção do usuário antes do transbordo para um humano.

---

## 🧠 Engenharia de Prompts e "Cicatrizes" (Troubleshooting)

Durante o desenvolvimento e estudo no NotebookLM, documentei a evolução dos comandos para resolver problemas reais de um agente em produção:

### Teste 1: Prevenção de Loops de Mensagens e Alucinação Financeira
* **O Problema/Cicatriz:** Em configurações iniciais, a IA sofria "alucinações", inventando valores financeiros irreais durante o processamento de documentos, além de entrar em loops de mensagens repetindo as mesmas perguntas para o usuário.
* **Prompt Refinado (Estratégico):** *"Antes de gerar qualquer resposta, revise todo o histórico da conversa desde a primeira mensagem do lead. Analise cada entrada anterior para identificar informações que respondam às suas próximas perguntas. Se a resposta já estiver no histórico, use essa informação. Nunca repita perguntas já respondidas. Armazene toda fala do lead, mesmo que aparentemente irrelevante."*
* **Resultado Obtido:** A IA interrompeu a geração do loop contínuo de perguntas, melhorou a retenção do contexto do usuário e eliminou a projeção de valores financeiros incorretos, permitindo uma triagem linear e assertiva.

### Teste 2: Estruturando o Agente
* **Prompt no NotebookLM:** *"Baseado nos documentos fornecidos, resuma em bullet points as 3 principais regras que um desenvolvedor deve seguir ao configurar as instruções de sistema de um assistente de IA."*
* **Resultado Obtido:** A ferramenta extraiu com precisão regras sobre clareza, definição de restrições (boundaries) e a importância de fornecer exemplos (few-shot prompting).

---

## 📖 Miniguia de Estudo (Entrega Final)

### 1. Resumo Estruturado: Boas Práticas para Agentes de Triagem
* **Contexto Histórico:** A IA deve ser instruída a ler sempre o log anterior para não frustrar o usuário repetindo perguntas.
* **Integração de Mensageria:** Ao conectar a IA ao WhatsApp, é vital prever limites de taxa (rate limits) e garantir que as respostas geradas pela IA sejam curtas e adaptadas para leitura em telas de celular.

### 2. Glossário de Conceitos
* **System Prompt:** A instrução oculta que define a "personalidade" e as regras de negócio do seu agente de IA.
* **Alucinação:** Quando a IA gera uma informação factualmente incorreta ou inventa dados (como valores ou cláusulas que não existem no contexto) com muita convicção.
* **WhatsApp Cloud API:** A infraestrutura oficial da Meta hospedada na nuvem que permite a comunicação programática em larga escala entre sistemas (como nosso agente de IA) e usuários finais.

### 3. Prompts Reutilizáveis para Revisão (NotebookLM)
* *"Analise o documento da API da Meta e liste quais são os erros mais comuns de restrição de conta que podem interromper o fluxo do meu agente."*
* *"A partir do guia da OpenAI, crie um template de System Prompt ideal para qualificar clientes antes de repassá-los a um atendente humano."*

---
*Projeto desenvolvido para o Bootcamp de Agentes e IA da DIO.*
