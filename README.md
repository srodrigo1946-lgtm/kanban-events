# 🔄 kanban-events

Event log para sincronização em tempo real do **Funil Kanban** do [dashboard-vcre](https://github.com/srodrigo1946-lgtm/dashboard-vcre).

## Como funciona

Quando um Gerente arrasta um card no Kanban do painel, o navegador dele faz um commit que adiciona um evento ao `events.json`. O Diretor faz polling do raw URL a cada ~10s e exibe um toast pop-up quando há eventos novos.

## events.json schema

```json
[
  {
    "id": "uuid",
    "ts": "2026-06-24T20:30:00Z",
    "user": "Helen Cristina",
    "papel": "Gerente",
    "tipo": "move",
    "num": "4291",
    "cliente": "GABRIEL BATISTA",
    "from": "2.2 Documentos Pendentes",
    "to": "3.1 Aguardando Análise"
  }
]
```

Mantém só os últimos 50 eventos (truncado em cada commit).

## Token

O navegador usa um Fine-grained PAT escopado **somente a este repo** (Contents: read+write). Se vazar, o pior caso é encher esse arquivo de lixo — o dashboard principal não é afetado.
