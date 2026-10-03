# Experimentação e métricas

## Objetivo

Base para testar estratégias de conteúdo e oferta com método: formular hipótese, definir variável, medir, comparar com baseline e registrar aprendizado. Serve a qualquer skill que produza ou avalie conteúdo, oferta ou estratégia.

## Regra de ouro

**Métrica observada não é interpretação.** "O vídeo teve 40 mil views" é observação. "O vídeo foi um sucesso" é interpretação, e pode estar errada (40 mil views com 12 cliques e zero venda é vídeo que entreteniu e não vendeu). Sempre registre o número primeiro, a leitura depois, separados.

## Ciclo de experimento

1. **Hipótese:** uma frase testável. "Achadinhos abaixo de R$ 30 geram mais comentário pedindo link que achadinhos acima de R$ 100."
2. **Variável:** o que muda entre os testes. Só uma variável por vez (preço, no exemplo). Se você muda preço, formato e horário juntos, nenhum aprendizado sobrevive.
3. **Teste:** o conteúdo ou conjunto de conteúdos que expõe a variável.
4. **Métrica:** o que você mede, definido antes de publicar (não depois, escolhendo o número que ficou bonito).
5. **Baseline:** o desempenho atual da mesma métrica no mesmo formato. Sem baseline não existe "melhor que antes".
6. **Comparação:** resultado vs baseline, com volume suficiente para não ser ruído (3 curtidas a mais num vídeo não prova nada).
7. **Aprendizado:** o que a hipótese ganhou ou perdeu, registrado para a próxima pauta.

### Limitações

- Volume pequeno gera falso positivo. Com poucas publicações, trate todo resultado como indício, não conclusão.
- Sem grupo de controle perfeito em redes sociais (você não publica "o mesmo vídeo sem a variável" para a mesma audiência), o que você tem é comparação aproximada. É o suficiente para decidir pauta; não é o suficiente para afirmar causalidade.

## Métricas por etapa do funil

Cada métrica diz respeito a uma etapa (veja [social-commerce.md](social-commerce.md)); nenhuma conta a história sozinha.

| Métrica | O que observa | Etapa |
|---|---|---|
| Views / alcance | Quantas pessoas viram | Interesse |
| Retenção / tempo assistido | Quantas ficaram até o fim | Interesse |
| Curtidas, comentários, salvamentos, compartilhamentos | Interação com o conteúdo | Interesse |
| Cliques no link (CTR) | Quantas foram até a loja | Clique |
| Conversão (clique → compra) | Quantas compraram | Compra |
| Vendas / comissão em R$ | Resultado comercial | Compra |

### Princípio

Salvamento e compartilhamento pesam mais que curtida como sinal de intenção: salvar é a pessoa dizendo "quero isso depois"; compartilhar é a pessoa colocando o próprio nome na recomendação.

## Engajamento ponderado

Fórmula herdada do material do projeto, útil para comparar conteúdos entre si:

```
engajamento = (curtidas × 2 + comentários × 3 + compartilhamentos × 5) ÷ views × 1000
```

A lógica dos pesos: comentário exige mais esforço que curtida; compartilhamento expõe a pessoa que compartilha, então é o sinal mais forte. A divisão por views normaliza para conteúdo novo e antigo serem comparáveis.

### Limitações

- Os pesos são convenção, não lei natural. Servem para comparar seus próprios conteúdos entre si, não para benchmark externo.
- Salvamentos não entram na fórmula original e, em social commerce, são sinal forte de intenção de compra. Considere acompanhar salvamentos separadamente.
- Score alto não é venda. É sinal de que o conteúdo prendeu; a etapa seguinte (clique, compra) é medida por fora.

## Métricas de vaidade vs comerciais

### Princípio

Métrica de vaidade agrada o ego (views, seguidoras, curtidas); métrica comercial paga as contas (cliques, conversão, comissão em R$). As duas importam, mas para perguntas diferentes: vaidade indica alcance futuro; comercial indica dinheiro hoje.

### Aplicação

Nunca reporte só a vaidade. "O vídeo bombou" sem cliques é entretenimento gratuito. O relatório mínimo útil: views → cliques → vendas, para ver onde o funil está vazando.

## Atribuição

### Princípio

Atribuição é a resposta para "qual conteúdo gerou esta venda?". A maioria dos programas de afiliados usa último clique: a comissão vai para o último link clicado antes da compra.

### Limitações

- A pessoa viu 5 vídeos seus, clicou uma vez. O último clique leva a comissão, mas os 4 vídeos anteriores fizeram a venda. Atribuição por último clique subestima conteúdo de descoberta e superestima conteúdo de conversão.
- Venda em loja física, indicação boca a boca e compra direta (sem clicar no seu link) são invisíveis para a atribuição. Exista consciência de que o número medido é o mínimo, não o total.
- Ferramentas de rastreio por publicação (Sub-ID, cupom por conteúdo) melhoram a leitura quando o programa aceitar (veja [glossario-afiliados-br.md](../operacao/glossario-afiliados-br.md)).

## Benchmarks

### Heurística

Do material legado do projeto (casos de produtos digitais, mercado americano): taxas de clique→conversão na faixa de 1 a 5% eram típicas, e prazos de meses para renda consistente eram realistas. Use como referência de expectativa (nada é "da noite para o dia"), não como meta: produto físico, público brasileiro e social commerce podem ter faixas diferentes.

### Hipótese

Em social commerce de produto físico barato, conversão clique→compra pode ser maior que em produto digital caro (fricção de decisão menor), mas comissão por venda menor. Precisa ser observado nos próprios números antes de qualquer decisão de portfólio.

## O que este arquivo não promete

- Nenhuma métrica prova causalidade sozinha. "Postei às 19h e foi bem" não significa "19h é o melhor horário"; significa que aquele conteúdo, naquele dia, foi bem.
- Nenhum teste substitui consistência. Testar 10 formatos em 10 dias com volume baixo ensina menos que observar 3 formatos em 30 dias.
