# Qualificação de leads no chat do n8n

Jhonny é um assistente de pré-vendas que conversa com quem demonstrou interesse nas soluções de uma empresa. Ele pergunta o nome, procura entender o desafio da equipe e levanta duas informações comerciais: quantos leads a empresa atende por dia e qual é seu faturamento médio mensal.

## Como funciona

O Chat Trigger recebe a mensagem e inicia o AI Agent. O agente usa o GPT-4o-mini para conduzir a conversa, a Simple Memory para recuperar as respostas anteriores da sessão e uma calculadora que pode acionar quando necessário. O prompt orienta o assistente a fazer uma pergunta por vez.

A quantidade diária de leads dá contexto à conversa. O critério de qualificação definido no prompt é o faturamento mensal.

| Faturamento mensal informado | Resposta esperada |
| --- | --- |
| Abaixo de R$ 50.000 | Agradecer pelas informações e encerrar o atendimento. |
| R$ 50.000 ou mais | Qualificar o lead e informar que o próximo passo é o contato comercial. |

O exemplo termina com a resposta no chat. O encaminhamento citado na mensagem final é simulado. Cadastro em CRM e notificação a vendedores ficam fora do escopo desta versão.

## Como testar

1. Importe [agente-sdr.json](workflows/agente-sdr.json) em um workflow novo do n8n.
2. Selecione sua credencial da OpenAI no nó **OpenAI Chat Model**.
3. Abra o chat de teste, envie uma saudação e responda às perguntas com dados fictícios.
4. Faça duas conversas em sessões separadas: informe R$ 49.999 na primeira e R$ 50.000 na segunda. Compare o encerramento com a tabela acima.

O nome da empresa, o roteiro e o limite de faturamento podem ser ajustados na mensagem de sistema do nó **AI Agent**.

## Crédito

Workflow de exemplo identificado no arquivo original como **Agente SDR Exemplo - By Ric Neves**. Edição organizada para estudo e demonstração em portfólio.
