# FilhaDeQuemBot

Conjunto de skills de agente para marketing de afiliados voltado ao mercado brasileiro/PT-BR.

## Estrutura do repositório

- `.agents/skills/<skill-name>/SKILL.md` – skill individual
- `shared/references/` – documentos compartilhados (glossário, compliance, flywheel, etc.)
- `_arquivo/` – material histórico / planejamento
- `README.md`
- `LICENSE`
- `AGENTS.md`

## Como trabalhar com skills

- As skills são descobertas automaticamente em `.agents/skills/`.
- Uma skill está disponível somente quando possui um `SKILL.md` válido.
- O campo `name:` no front‑matter do `SKILL.md` deve corresponder exatamente ao nome da pasta.
- Referências internas devem usar caminhos relativos a partir da raiz do repositório (`shared/references/...` ou `<skill>/references/...`).
- Não se deve assumir a existência de CLIs, scripts externos ou ferramentas que não estejam presentes no repositório.
- Cada skill deve declarar claramente quais campos de entrada espera e quais campos de saída produz (esquema de entrada/saída). O agente passa somente esses campos entre skills; o texto livre é destinado à exibição humana.
- Instruções devem ser claras, objetivas e testáveis; evitar ambiguidades ou dependências de conhecimento externo não documentado.

## Idioma e localização

- Todas as instruções, exemplos, prompts e mensagens das skills devem estar em **português do Brasil (PT‑BR)**.
- Gatilhos de ativação (descrições, exemplos) devem funcionar em português.
- Exemplos de copy, CTA e conteúdo devem considerar o público brasileiro (moeda BRL, feriados locais, cultura).
- Nomes técnicos, identificadores de arquivos e código podem permanecer em inglês quando apropriado.

## Segurança

- Nunca expor ou hard‑codar credenciais, tokens ou API keys.
- Nunca colocar secrets em skills ou documentação.
- Não executar ações destrutivas (ex.: `rm`, `git reset --hard`) sem autorização explícita da usuária.
- Não fazer push automático para repositórios remotos.
- Não confiar cegamente em dados externos; validar informações de fontes não confiáveis antes de usá‑las.
- Não revelar possíveis secrets encontrados durante uma análise; apenas sinalizar sua existência e localização.

## Compliance

- Conteúdo comercial, afiliado ou patrocinado deve respeitar as regras brasileiras aplicáveis de publicidade e identificação comercial.
- Quando uma tarefa envolver compliance, consultar as referências apropriadas em `shared/references/`.
- Não inventar requisitos legais.
- Se uma regra de compliance não estiver documentada ou houver dúvida relevante, sinalizar a incerteza em vez de afirmar como fato.

## Autonomia e decisões da autora

- O agente **não deve inventar** decisões de negócio que pertencem à autora: nicho, tom de voz, programas de afiliados, frequência de publicação, canais, orçamento ou estratégia comercial.
- Quando alguma dessas informações estiver em falta, o agente deve **pedir esclarecimento** antes de prosseguir.

## Alterações e Git

- Nunca fazer `commit` ou `push` sem autorização explícita.
- Trabalhar em uma parte por vez (ex.: editar uma skill, depois validar).
- Quando solicitado, explicar as alterações que pretende fazer antes de executá‑las.
- Não executar operações Git destrutivas sem autorização.

## Regras de qualidade

- Manter cada skill autocontida quando possível.
- Verificar que todas as referências internas apontam para arquivos existentes; relatar links quebrados.
- Evitar instruções ambíguas ou que dependam de ferramentas inexistentes.
- Preferir instruções verificáveis e testáveis.
- Não duplicar no AGENTS.md detalhes que pertencem a `shared/references/`.