# organiza-reclamacao-consumidor

Skill para o Claude que **organiza a reclamação do consumidor** que teve problema com um **produto** comprado. A partir do relato da pessoa, escrito do jeito dela, a skill:

1. pergunta só as informações que faltaram (produto, onde comprou, datas, valor, forma de pagamento, nota fiscal, quando começou o defeito, contatos anteriores);
2. pergunta o que o consumidor quer, mostrando só as opções que a lei garante para o caso: conserto, troca, devolução do dinheiro, abatimento ou arrependimento;
3. identifica a **cadeia de fornecedores responsáveis** (vendedor, fabricante, importador, marketplace) e explica se respondem juntos (solidariamente) ou não;
4. entrega um **texto de até 1000 caracteres pronto para colar** no [consumidor.gov.br](https://www.consumidor.gov.br) ou no Reclame Aqui, com a categoria sugerida;
5. explica direitos, prazos e próximos passos em linguagem simples:
   - a empresa tem até 10 dias para responder;
   - o consumidor deve avaliar a empresa;
   - se não resolver, procurar o Procon ou o Juizado Especial.

Desenvolvida para a disciplina de **Direito do Consumidor**, com base no Código de Defesa do Consumidor (Lei nº 8.078/1990).

## Estrutura

```
SKILL.md                      ← instruções e fluxo da conversa
references/
├── arvore-decisao.md         ← vício x fato do produto; quem responde
├── artigos-cdc.md            ← artigos e prazos do CDC
├── casos-especiais.md        ← marketplace, nota fiscal, bancos, assistência técnica
└── modelos-reclamacao.md     ← modelos e categorias do consumidor.gov.br
evals/                        ← casos de teste
```

## Como instalar

- **Claude.ai**: compacte a pasta (ou baixe o `.skill` na aba Releases, se disponível) e envie em *Configurações › Recursos › Skills*.
- **Claude Code**: copie a pasta para `~/.claude/skills/organiza-reclamacao-consumidor/`.

## Como usar

Basta contar o problema, por exemplo:

> "Comprei uma air fryer na Shopee, parou de esquentar em 12 dias e a loja diz para eu procurar a fábrica."

## Escopo e limites

- Voltada a **produtos**. Problemas com serviços (plano de saúde, telefonia, voos) são encaminhados ao Procon e à agência reguladora do setor.
- Bancos e meios de pagamento entram só quando o problema está ligado à compra de um produto: estorno, cobrança em dobro, pagamento sem entrega.
- A jurisprudência de referência (STF, Temas 987 e 533; STJ, REsp 1.880.344/SP) orienta o raciocínio, mas não aparece na resposta ao consumidor.

> **Aviso:** a orientação gerada é informativa e não substitui a consulta a um advogado ou à Defensoria Pública. Confira a legislação e a jurisprudência atualizadas antes de uso profissional.
