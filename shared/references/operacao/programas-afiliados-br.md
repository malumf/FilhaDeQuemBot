# Programas de afiliados no Brasil

## Objetivo

Referência operacional dos programas de afiliados relevantes para o projeto (marketplaces e varejo brasileiro): o que é conceito estável, o que depende do programa e o que é volátil. Serve às skills de escolha de produto, cadastro de programa e cálculo de comissão.

## Como ler este arquivo

**Nenhuma comissão, prazo, requisito, atribuição ou regra de programa está afirmada aqui.** Esses termos mudam por programa, por categoria e por época. O padrão deste arquivo é: conceito estável explicado, e para todo o resto, o que verificar e onde. Quando a verificação for feita, registrar em [registro-de-fontes.md](registro-de-fontes.md).

## Conceitos estáveis

### Princípio

- **Programa de afiliado:** você divulga o produto com um link único; se a pessoa comprar passando pelo seu link, você recebe comissão. O link carrega seu identificador; a loja faz o rastreio.
- **Atribuição:** a regra que decide qual afiliado recebe a comissão. A forma mais comum é último clique (o último link clicado antes da compra leva a comissão). As limitações disso estão em [../nucleo/experimentacao-metricas.md](../nucleo/experimentacao-metricas.md).
- **Janela de atribuição (cookie):** o período após o clique em que a compra ainda conta para você. Vai de horas a dias conforme o programa.
- **Comissão por categoria:** marketplaces costumam pagar percentuais diferentes por categoria de produto; a comissão do seu nicho é a que importa, não a "comissão do programa".
- **Comissão em R$ > percentual:** 10% de R$ 30 são R$ 3; 2% de R$ 800 são R$ 16. Sempre calcule o real por venda antes de escolher produto (a lista de avaliação está em [../nucleo/formatos-produto.md](../nucleo/formatos-produto.md)).
- **Validação e cancelamento:** pedidos podem ser cancelados (desistência, fraude, troca) e a comissão, estornada. Comissão confirmada é a que sobrevive ao prazo de validação do programa.
- **Pagamento:** existe valor mínimo de saque e prazo entre a validação e o pagamento. Fluxo de caixa de afiliado é atrasado por natureza.

## Programas a considerar

Os três marketplaces abaixo operam programas de afiliados no Brasil. **Tudo que segue sobre cada um é o que verificar, não o que afirmar.**

### Shopee (Programa de Afiliados Shopee)

- **Conceito estável:** marketplace com forte cultura de cupom e preço baixo, ambiente natural para o formato "achadinhos" (veja [../brasil/consumidor-brasileiro.md](../brasil/consumidor-brasileiro.md)).
- **PRECISA DE VERIFICAÇÃO EXTERNA (verificar na página oficial do programa):** comissão por categoria; janela de atribuição; formas de cadastro e requisitos de conta; regras de uso de cupom em conteúdo; política sobre divulgação em Instagram/TikTok; limite e prazo de pagamento; se aceita Sub-ID por conteúdo.
- **Heurística:** produto de ticket baixo pede volume; a comissão unitária tende a ser pequena, então o cálculo em R$ por venda decide se vale conteúdo.

### Mercado Livre (programa de afiliados)

- **Conceito estável:** maior marketplace brasileiro, com confiança de marca emprestada à recomendação; o programa de afiliados opera com links gerados pela própria plataforma.
- **PRECISA DE VERIFICAÇÃO EXTERNA:** comissão por categoria; janela de atribuição; requisitos de cadastro; regras de link (onde pode e não pode ser usado); tratamento de vendas de lojas terceiras vs. produtos do marketplace; pagamento mínimo e prazo; estorno por cancelamento.
- **Heurística:** a confiança da marca reduz objeção de loja desconhecida; o conteúdo foca mais no produto e menos em provar a loja.

### Amazon Brasil (Programa de Associados da Amazon)

- **Conceito estável:** a Amazon opera programa de afiliados global com versão brasileira; a comissão historicamente varia por categoria e o volume de produto é enorme.
- **PRECISA DE VERIFICAÇÃO EXTERNA:** comissão por categoria no Brasil; janela de atribuição (o prazo de cookie mudou ao longo da história do programa); regras operativas (o programa historicamente tem regras restritivas sobre o que o afiliado pode dizer sobre preço e disponibilidade); limite de saque e forma de pagamento; política de uso de imagem de marca.
- **Heurística:** bom catálogo para review e comparação (produto técnico, livro, eletro), pela profundidade de oferta.

### Outros programas

Varejistas brasileiros (magazines, lojas de nicho, plataformas de beauty) também operam programas próprios ou via redes de afiliados. O mesmo padrão vale: **verificar termos na fonte oficial antes de afirmar qualquer coisa.**

## Checklist antes de entrar em qualquer programa

1. Comissão por categoria do seu nicho (percentual e R$ por venda típica).
2. Janela de atribuição (cookie).
3. Regra de atribuição (último clique? outras?).
4. Prazo de validação e política de estorno.
5. Valor mínimo de saque, forma e prazo de pagamento.
6. Requisitos de cadastro e motivos de banimento (leia a lista; ela existe e é aplicada).
7. Regras de divulgação: o que o programa exige que você diga ou proíbe que você diga.
8. Suporte a Sub-ID ou cupom próprio por conteúdo (para medir o que converte).
9. Política de uso de imagem, marca e dados do produto.

Cada resposta vai para [registro-de-fontes.md](registro-de-fontes.md) com fonte, URL e data. Sem isso, a skill que usar o programa está chutando.
