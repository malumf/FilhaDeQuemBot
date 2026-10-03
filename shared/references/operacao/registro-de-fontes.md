# Registro de fontes

## Objetivo

Padrão simples para documentar informação externa usada em decisões e skills do projeto: de onde veio, quando foi verificada e quanto se pode confiar. Serve a qualquer skill que cite dado volátil (regra de plataforma, termo de programa, comportamento de mercado, exigência jurídica).

## Por que existe

Dado externo sem registro vira duas falhas: (1) apresentar como fato algo que foi estimativa ou palpite, e (2) continuar usando informação que já venceu. A regra do projeto: **nenhum dado volátil entra em skill sem linha de registro.** Informação sem fonte é hipótese, e hipótese se declara como hipótese, não se vira fato.

## Campos

Cada registro usa estes campos:

| Campo | O que é |
|---|---|
| `assunto` | Tema ao qual a informação pertence (ex.: "programa Shopee", "regras Instagram") |
| `afirmacao` | A informação, em uma frase específica e verificável |
| `fonte` | Quem afirma (nome da página/documento oficial) |
| `url` | Endereço onde foi verificada |
| `data_verificacao` | Quando você conferiu (AAAA-MM-DD) |
| `tipo_fonte` | `oficial` / `imprensa` / `estudo` / `mercado` / `testemunhal` |
| `confianca` | `verificada` / `estimada` / `nao_verificada` (ver níveis abaixo) |
| `revisar_em` | Data recomendada de re-verificação (AAAA-MM-DD) |

## Níveis de confiança

- **verificada:** conferida em fonte oficial, na data registrada. Pode ser usada como fato até `revisar_em`.
- **estimada:** aproximada, de fonte secundária ou de leitura indireta. Pode orientar decisão, sempre com o "estimada" visível.
- **nao_verificada:** tudo que circula sem fonte. Tratada como hipótese; nunca apresentada como fato em skill ou conteúdo.

## Regras

1. A frase do campo `afirmacao` é específica. "A Shopee paga bem" não é afirmacao; "a comissão da categoria X do programa Y era Z% em [data]" é.
2. Fonte oficial vem antes de imprensa, imprensa antes de blog, blog antes de testemunho. Para termos de programa e regras de plataforma, só fonte oficial vale como `verificada`.
3. `revisar_em` é obrigatório para dado volátil: regra de plataforma (revisar em 1 a 3 meses), termo de programa (a cada mudança anunciada ou semestral), exigência jurídica (anual, ou quando houver notícia de mudança).
4. Quando a verificação falha ou a fonte desaparece, o registro não é apagado: o nível muda para `nao_verificada` com a data da mudança. Histórico de informação errada também é informação.
5. Nada de segredo: registro serve para skill e para conversa com a autora. Se a fonte não pode ser compartilhada, o dado não entra.

## Exemplo

```yaml
- assunto: "programa-afiliados-shopee"
  afirmacao: "A comissão da categoria Moda Acessórios do Programa de Afiliados Shopee Brasil é de X%."
  fonte: "Página oficial do Programa de Afiliados Shopee"
  url: "https://..."
  data_verificacao: "2026-10-02"
  tipo_fonte: "oficial"
  confianca: "verificada"
  revisar_em: "2027-04-02"
```

## Onde os registros vivem

Enquanto não houver arquivo dedicado de registros, os registros entram em bloco YAML no final do arquivo temático correspondente (ex.: termos verificados de programa entram no final de [programas-afiliados-br.md](programas-afiliados-br.md)), sempre com os campos acima. Quando o volume justificar, a criação de um arquivo dedicado de registros é decisão da autora.

## Relação com o resto da base

- Tudo marcado **PRECISA DE VERIFICAÇÃO EXTERNA** em [../brasil/compliance-br.md](../brasil/compliance-br.md), [../plataformas/instagram.md](../plataformas/instagram.md), [../plataformas/tiktok.md](../plataformas/tiktok.md) e [programas-afiliados-br.md](programas-afiliados-br.md) vira registro aqui quando for verificado.
- Métricas dos próprios perfis do projeto não precisam de registro externo; precisam de data e de separação entre observação e interpretação ([../nucleo/experimentacao-metricas.md](../nucleo/experimentacao-metricas.md)).
