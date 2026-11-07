# 🛒 Organiza Reclamação do Consumidor

> **Fale a sua dor que eu organizo a reclamação.**

Skill para o **Claude** (assistente de IA da Anthropic) que ajuda o **consumidor leigo** com problemas em **produtos** comprados. A pessoa conta o que aconteceu do jeito dela, e a skill devolve:

- quem é **responsável** pelo problema;
- quais são os **direitos** e os **prazos**;
- um **texto pronto para copiar e colar** no [consumidor.gov.br](https://www.consumidor.gov.br) ou no Reclame Aqui.

Desenvolvida para a disciplina de **Direito do Consumidor**, com base no **Código de Defesa do Consumidor** (Lei nº 8.078/1990).

---

## 🎯 Qual problema ela resolve

Quem tem problema com uma compra costuma ficar perdido:

- **"A loja disse que é com a fábrica, a fábrica diz que é com a loja."**
- **"Não sei se ainda estou no prazo."**
- **"Não sei escrever a reclamação nem o que posso pedir."**

A skill resolve isso em uma conversa. Ela identifica a **cadeia de fornecedores** que responde pelo problema, explica que o consumidor **escolhe de quem cobrar** e **não pode ser jogado de um para o outro**, e transforma o relato em uma reclamação objetiva e fundamentada.

---

## ⚙️ Como funciona

```
 1. Consumidor conta o problema    →  do jeito dele, sem formulário
 2. Skill pergunta só o que faltou  →  em uma única mensagem
 3. Skill pergunta o que ele quer   →  mostrando só as opções que a lei garante
 4. Skill analisa o caso            →  vício ou fato? quem responde? qual o prazo?
 5. Skill entrega a resposta        →  em linguagem simples + texto da reclamação
```

### 1. Entrada: o relato
O consumidor escreve livremente. A skill pergunta **só o que faltou**:
- produto (marca, modelo, número de série);
- onde comprou e quem vendeu (loja física, site da marca, marketplace);
- data da compra e da entrega;
- valor pago e forma de pagamento;
- nota fiscal;
- **quando o defeito começou**: o prazo para reclamar de defeito oculto começa nesse momento;
- se alguém se machucou;
- se já procurou a loja, o fabricante ou a assistência técnica (com data e protocolo).

> 🔒 A skill orienta o consumidor a **não** enviar CPF, endereço ou dados de cartão.

### 2. O que o consumidor quer
A skill mostra **apenas as opções que a lei garante para o caso concreto** e pede que ele escolha:

| Situação | Opções |
|---|---|
| Defeito não resolvido em 30 dias | Troca, dinheiro de volta corrigido ou desconto (art. 18, §1º) |
| Produto essencial | Os mesmos direitos, **imediatamente** (art. 18, §3º) |
| Não entregue ou diferente do pedido | Entrega, produto equivalente ou cancelamento com reembolso (art. 35) |
| Compra online em até 7 dias | Desistência com devolução de tudo, inclusive o frete (art. 49) |
| Cobrança em dobro | Estorno ou devolução em dobro (art. 42) |
| Produto causou acidente | Reparação dos danos (art. 12) |

### 3. Análise jurídica
- **Vício ou fato do produto?**
  - **Vício**: o produto não funciona. **Todos da cadeia respondem juntos.**
  - **Fato**: o produto causou um acidente. Respondem fabricante e importador; a loja só nas hipóteses do art. 13.
- **Cadeia de fornecedores:** vendedor, fabricante, importador, marketplace, assistência técnica.
- **Marketplace:** responde quando participa da venda (pagamento, entrega, garantia). Não responde por golpe feito **fora** da plataforma.
- **Nota fiscal:** deve ser pedida ao vendedor. Se ele não emitir, a plataforma também é responsável pela solução.
- **Prazos:**
  - 30 dias para reclamar de produto não durável e 90 dias para durável;
  - 5 anos para pedir indenização por acidente;
  - 7 dias para o arrependimento em compra online;
  - a garantia do fabricante se soma à garantia da lei.

### 4. Saída
```
📝 Resumo do seu caso
🏢 Quem é responsável
⚖️ Seus direitos
⏰ Prazos
📋 Texto pronto para a reclamação   ← até 1000 caracteres + categoria do consumidor.gov.br
👣 Próximos passos
```

Os **próximos passos** sempre incluem:
- colar o texto no **consumidor.gov.br** (com a conta gov.br);
- a empresa tem **até 10 dias para responder**;
- **guardar o protocolo**, porque a reclamação suspende o prazo;
- **avaliar sempre a empresa**, em até 20 dias após a resposta;
- se a empresa não estiver cadastrada, usar o **Reclame Aqui** (site privado);
- se não resolver, procurar o **Procon** ou o **Juizado Especial Cível** (até 20 salários mínimos sem advogado).

---

## 💬 Exemplo

**Consumidor:**
> Comprei uma air fryer na Shopee, paguei 389 no cartão, quem vendeu foi a loja CasaFácil. Chegou dia 8 e no dia 20 parou de esquentar. A loja disse que eu tenho que procurar a fábrica. Quero meu dinheiro de volta.

**A skill responde (trecho):**

> 🏢 **Quem é responsável**
> - **CasaFácil** (vendedora), **Mondial** (fabricante) e **Shopee** (plataforma).
> - Em caso de defeito, **todos respondem juntos**, e **você escolhe de quem cobrar**. A loja não pode mandar você procurar a fábrica.
>
> 📋 **Texto pronto para a reclamação**
> *Categoria: Vício de Qualidade › Produto danificado / não funciona*
> > Em 02/09/2026 comprei uma air fryer Mondial AF-30 por R$ 389,00, paga com cartão de crédito, na Shopee, vendida pela loja CasaFácil, pedido nº 2409ABC. Recebi o produto em 08/09/2026 e, em 20/09/2026, ele parou de esquentar. Em 21/09/2026 informei o defeito à loja, que se recusou a resolver e me mandou procurar o fabricante. Pelo CDC, todos os fornecedores da cadeia respondem solidariamente pelo defeito (art. 18)… Solicito a restituição imediata do valor pago, corrigido, conforme art. 18, §1º, II, do CDC.

---

## 📁 Estrutura

```
SKILL.md                      ← instruções e fluxo da conversa
references/
├── arvore-decisao.md         ← vício x fato do produto; quem responde
├── artigos-cdc.md            ← artigos e prazos do CDC
├── casos-especiais.md        ← marketplace, nota fiscal, bancos, assistência técnica
└── modelos-reclamacao.md     ← modelos e categorias do consumidor.gov.br
evals/                        ← casos de teste
```

## 📥 Como instalar

- **Claude.ai:** baixe o arquivo `.skill` na [página de Releases](../../releases/latest) e envie em *Configurações › Recursos › Skills*.
- **Claude Code:** copie esta pasta para `~/.claude/skills/organiza-reclamacao-consumidor/`.

Depois, basta contar o problema ao Claude. A skill é acionada automaticamente.

## 🧪 Testes

A skill foi testada em 4 casos, todos aprovados:

| Caso | O que verifica |
|---|---|
| Air fryer com defeito comprada em marketplace | Vício, solidariedade, "a loja não pode empurrar para a fábrica", nota fiscal |
| Tênis comprado no site da marca | Arrependimento de 7 dias (art. 49) |
| Celular que queimou a mão do consumidor | Fato do produto: o fabricante responde, a loja só no art. 13 |
| Negativa de plano de saúde | Fora do escopo: encaminha ao Procon e à ANS |

## 🚧 Escopo e limites

- Voltada a **produtos**. Serviços (plano de saúde, telefonia, voos) são encaminhados ao Procon e à agência reguladora (ANS, Anatel, ANAC…).
- Bancos e meios de pagamento entram só quando ligados à compra de um produto: estorno, cobrança em dobro, pagamento sem entrega.
- Jurisprudência de referência: STF, Temas 987 e 533; STJ, REsp 1.880.344/SP. Ela orienta o raciocínio da skill, mas **não aparece** na resposta ao consumidor.

> ⚠️ **Aviso:** a orientação gerada é informativa e **não substitui** a consulta a um advogado ou à Defensoria Pública. Confira a legislação e a jurisprudência atualizadas antes de uso profissional.
