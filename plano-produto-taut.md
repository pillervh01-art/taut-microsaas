# Plano de Produto — Plataforma Taut
**Victor + Claude | Março 2026 — v2**

---

## O que estamos construindo

Uma plataforma web baseada em IA que leva o advogado por uma jornada completa: do diagnóstico de nicho à publicação de conteúdo — com IA agindo em cada etapa do caminho.

O produto tem três camadas:

**Estratégia** → descobre quem você é, para quem você fala, e como se posicionar
**Execução** → organiza e produz o conteúdo de forma inteligente e contínua
**Crescimento** → aprende com o histórico e mostra o progresso de forma tangível

Cada módulo usa a Claude API com prompts baseados na metodologia já destrinchada nos agentes da Taut. O produto é, essencialmente, a versão self-serve da consultoria — sem Victor precisar estar presente.

---

## O que já existe (não recomece do zero)

| Arquivo | O que contém | Onde entra no produto |
|---|---|---|
| `contexto-taut.md` | Identidade, público, voz | System prompt base de todos os módulos |
| `intake.md` | Coleta estruturada de info do cliente | Onboarding do usuário no app |
| `caleb.md` | Brand Journey, posicionamento, pilares | Módulo 3 completo |
| `personal-branding.md` | Versão simplificada do caleb | Complementa o Módulo 3 |
| `ideacao.md` | Geração de ideias com pesquisa | Módulo 4 — Motor de Conteúdo |
| `roteiro-curto.md` | Roteirização em 3 formatos | Módulo 6 — Roteirizador |

---

## Arquitetura do produto (v2)

### Fluxo completo

```
CADASTRO
   ↓
ONBOARDING RÁPIDO (5 min)
   → Nome, escritório, área atual, objetivo principal
   ↓
━━━━━━━━━━━━━━ CAMADA: ESTRATÉGIA ━━━━━━━━━━━━━━
   ↓
MÓDULO 1 — DIAGNÓSTICO DE NICHO ✅ (protótipo pronto)
   → 8 perguntas guiadas
   → IA entrega 3 opções de nicho com análise detalhada
   → Usuário escolhe e confirma o nicho
   ↓
MÓDULO 2 — PERFIL DO CLIENTE IDEAL (ICP)  ← NOVO
   → Quem é o cliente dos sonhos (cargo, momento de vida, problema)
   → Como ele pesquisa um advogado
   → O que o faz contratar / O que o faz desistir
   → Medos, objeções e vocabulário que ele usa
   → IA entrega avatar detalhado + mapa de empatia
   ↓
MÓDULO 3 — ESTRATÉGIA DE PERSONAL BRANDING
   → Brand Journey Framework (4 perguntas, contextualizado com nicho + ICP)
   → Exercício das Duas Colunas (posicionamento)
   → Mapa de associação
   → Pilares de conteúdo
   → IA entrega estratégia completa + pitch de posicionamento + plano 90 dias
   ↓
━━━━━━━━━━━━━━ CAMADA: EXECUÇÃO ━━━━━━━━━━━━━━
   ↓
MÓDULO 4 — MOTOR DE CONTEÚDO
   → Geração semanal de ideias por canal (Reels, LinkedIn, Blog)
   → Calendário editorial do mês
   → Briefing de cada conteúdo com ângulo, gancho e formato sugerido
   → Sistema aprende com o que o usuário aprova/descarta
   ↓
MÓDULO 5 — KANBAN DE CONTEÚDO  ← NOVO
   → Pipeline visual: Ideia → Roteiro → Gravação → Edição → Publicado
   → IA age em cada transição de coluna (ver detalhe abaixo)
   → Cards gerados automaticamente pelo Motor (Módulo 4)
   → Histórico de publicados alimenta o Módulo 4 nas semanas seguintes
   ↓
MÓDULO 6 — ROTEIRIZADOR
   → Usuário abre um card do Kanban
   → IA gera roteiro pronto para gravar (Talking Head / Lofi / React)
   → Roteiro usa o avatar do ICP como destinatário
   ↓
━━━━━━━━━━━━━━ CAMADA: CRESCIMENTO ━━━━━━━━━━━━━━
   ↓
AUTHORITY SCORE — PAINEL DE PROGRESSO  ← NOVO
   → Score gamificado que cresce com cada ação concluída
   → Visualização do progresso na jornada de autoridade
   → Desbloqueios por milestone (ex: "100 pts — Nicho definido 🎯")
   ↓
[PÓS-MVP] MEMÓRIA EVOLUTIVA
   → IA aprende quais temas geram mais engajamento
   → Ajusta automaticamente o tom e ângulo das próximas sugestões
   → Relatório mensal de performance com insights estratégicos
```

---

## O Kanban em detalhe — IA em cada coluna

O Kanban não é só um board visual. A diferença está nas **ações automáticas de IA** que disparam em cada transição de coluna.

| Coluna | Quando a IA age | O que ela faz |
|---|---|---|
| **Ideia** | Card criado | Gera título, ângulo, gancho e formato sugerido (já vem do Motor) |
| **Roteiro** | Card movido para cá | Oferece gerar o roteiro completo (Talking Head / Lofi / React) usando o ICP |
| **Gravação** | Card movido para cá | Gera checklist de produção personalizado pro formato (roupas, cenário, tom) |
| **Edição** | Card movido para cá | Sugere legenda, hashtags, CTA baseado no objetivo do post |
| **Publicado** | Card movido para cá | Registra no histórico, pergunta se performou bem para calibrar o Motor |

O Card tem: título do conteúdo, formato (Reels/LinkedIn/Blog), pilar de conteúdo associado, data prevista de publicação, e campo de notas livres.

---

## Authority Score — lógica de pontuação

| Ação | Pontos |
|---|---|
| Completar onboarding | +10 |
| Confirmar nicho (Módulo 1) | +20 |
| Completar ICP (Módulo 2) | +20 |
| Completar Personal Branding (Módulo 3) | +25 |
| Gerar primeiro calendário (Módulo 4) | +15 |
| Publicar primeiro conteúdo via Kanban | +30 |
| Publicar 5 conteúdos | +50 |
| Publicar 20 conteúdos | +100 |
| Receber primeiro lead via conteúdo (self-reportado) | +100 |

**Milestones desbloqueáveis:**
- 0–50 pts → "Advogado Invisível" (alerta, mas não humilhante)
- 51–100 pts → "Advogado em Construção"
- 101–200 pts → "Advogado Posicionado"
- 201–350 pts → "Referência no Nicho"
- 350+ pts → "Autoridade Consolidada"

Esses milestones podem ser o gancho de conteúdo da Taut: "chegou no nível Referência — compartilhe."

---

## Stack técnica (simples e funcional)

Para a fase de MVP, ficamos em HTML/CSS/JavaScript puro com chamadas diretas à Claude API. Sem frameworks pesados, sem backend próprio por enquanto.

| Componente | Solução MVP |
|---|---|
| Interface | HTML + CSS + JS vanilla |
| Chamadas à IA | Claude API (Anthropic) — direto do browser |
| Persistência de dados | localStorage (estruturado por módulo) |
| Drag & drop no Kanban | Biblioteca SortableJS (leve, sem dependências) |
| Hospedagem | GitHub Pages ou Netlify (gratuito, deploy em minutos) |
| Autenticação | Nenhuma no MVP — API key do próprio usuário |

**Nota sobre autenticação:** no MVP, cada usuário usa a própria API key. Isso elimina a necessidade de backend agora. No produto final, você teria uma assinatura mensal que te dá acesso ao sistema (e você paga a API internamente).

---

## Roadmap semanal (v2)

### ✅ SEMANA 0 — Feito
- [x] Pesquisa de mercado completa
- [x] Protótipo funcional do Módulo 1 (Diagnóstico de Nicho)
- [x] Planejamento completo do produto v1 e v2
- [x] Wireframe do Kanban de Conteúdo

**Victor faz:** criar conta na Anthropic e gerar API key em [console.anthropic.com](https://console.anthropic.com)

---

### SEMANA 1 — Testar e afinar o Módulo 1

**Objetivo:** ter o Módulo 1 testado com casos reais e os prompts calibrados.

**Construímos juntos:**
- Testar o protótipo com 2–3 perfis de advogado reais
- Ajustar as perguntas do questionário com base no que ficou solto
- Refinar o system prompt do diagnóstico de nicho com base nos outputs gerados
- Adicionar tela de "confirmar nicho escolhido" antes de prosseguir

**Victor faz:**
- Passar pelo fluxo como se fosse um cliente (preencha com dados reais ou fictícios realistas)
- Anotar: o que ficou bom nos resultados? O que ficou genérico demais?
- Listar os 3–5 nichos jurídicos mais comuns dos seus clientes reais

**Entrega:** Módulo 1 testado, ajustado e pronto para encadear com o Módulo 2.

---

### SEMANA 2 — Construir o Módulo 2 (ICP — Perfil do Cliente Ideal)

**Objetivo:** o advogado sai com um avatar de cliente detalhado que vai alimentar tudo: branding, conteúdo, roteiro.

**Construímos juntos:**
- Flow guiado de 6–8 perguntas sobre o cliente dos sonhos
- Sistema de construção progressiva do avatar (IA sintetiza ao final)
- Mapa de empatia visual na tela de resultado
- Armazenamento do ICP para uso nos módulos seguintes

**Victor faz:**
- Trazer 2–3 exemplos reais de cliente ideal dos seus clientes atuais (sem identificar)
- Marcar quais perguntas você faz no diagnóstico de consultoria sobre o cliente ideal
- Validar se o avatar gerado soa como uma pessoa real

**Entrega:** Módulo 2 funcional conectado ao Módulo 1.

---

### SEMANA 3 — Construir o Módulo 3 (Personal Branding)

**Objetivo:** o advogado tem nicho + ICP definidos e constrói sua estratégia de marca.

**Construímos juntos:**
- Brand Journey Framework com contexto do nicho + ICP (não genérico)
- Exercício das Duas Colunas — interface interativa
- Mapa de associação
- Pilares de conteúdo gerados com base no ICP
- Gerador de pitch de posicionamento (bio, proposta de valor, frase de introdução)
- System prompt baseado no `caleb.md` + `personal-branding.md`

**Victor faz:**
- Reler `caleb.md` e marcar as 5–10 perguntas mais críticas
- Trazer exemplos de frases de posicionamento que já gerou para clientes
- Validar o output com o próprio posicionamento da Taut como teste

**Entrega:** Módulo 3 funcional. Fluxo 1+2+3 rodando do início ao fim.

---

### SEMANA 4 — Construir o Módulo 4 (Motor de Conteúdo) + Authority Score

**Objetivo:** o motor gera ideias reais (não genéricas) e o Authority Score começa a funcionar.

**Construímos juntos:**
- Tela de configuração do motor: frequência, canais ativos
- Geração de ideias com structure baseada no `ideacao.md`
- Calendário editorial mensal
- Briefing completo de cada conteúdo
- Dashboard do Authority Score com milestones visuais

**Victor faz:**
- Listar os 10 temas/ângulos que funcionam MELHOR para advogados no Instagram e LinkedIn
- Listar os 5 erros de conteúdo mais comuns que você vê advogados cometendo
- Validar os outputs do motor com olho de consultor

**Entrega:** Módulo 4 funcional + Authority Score básico.

---

### SEMANA 5 — Construir o Módulo 5 (Kanban) + Módulo 6 (Roteirizador)

**Objetivo:** fechar o loop de execução. O usuário vai da ideia ao roteiro gravável em um fluxo contínuo.

**Construímos juntos:**
- Kanban drag-and-drop com 5 colunas
- IA que age em cada transição de coluna
- Integração com o Motor (cards gerados automaticamente)
- Roteirizador baseado no `roteiro-curto.md` (Talking Head / Lofi / React)
- Roteiro usa o ICP como destinatário implícito

**Victor faz:**
- Decidir o nome do produto
- Escrever o texto da landing page
- Pensar no modelo de preço (sugestão: R$ 297–497/mês)

**Entrega:** plataforma funcional de ponta a ponta.

---

### SEMANA 6 — Landing page + primeiros usuários beta

**Objetivo:** o produto está ao vivo e recebendo os primeiros 5–10 usuários.

**Construímos juntos:**
- Landing page direta (construímos aqui, sem agência)
- Fluxo de pagamento (Stripe ou Hotmart)
- E-mail de boas-vindas
- Exportação da estratégia completa em PDF

**Victor faz:**
- Identificar 5 contatos no mercado jurídico para beta teste
- Gravar vídeo curto (2–3 min) apresentando o produto
- Fazer call de 30 min com cada beta tester após uma semana de uso

**Entrega:** produto ao vivo, feedback real na mão.

---

## Decisões a tomar (e quando)

| Decisão | Prazo | O que precisa antes |
|---|---|---|
| Nome do produto | Semana 5 | Testar e ver se quer separar da marca Taut |
| Modelo de preço | Semana 5 | Ver quanto tempo o usuário leva no produto |
| Autenticação própria vs. API key do usuário | Semana 5–6 | Depende do volume esperado |
| Backend real vs. localStorage | Semana 6 | Depende da escala dos primeiros usuários |
| Incluir Memória Evolutiva no MVP | Semana 6 | Depende do feedback dos betas |

---

## Separação de responsabilidades

### O que construímos juntos (Claude + Victor no Cowork)
- Toda a interface do produto (HTML, CSS, JS)
- System prompts de cada módulo
- Integração com a Claude API
- Kanban com drag-and-drop e IA por coluna
- Authority Score
- Landing page e fluxo de pagamento

### O que só Victor pode fazer
- Calibrar se os outputs estão estrategicamente corretos
- Trazer exemplos reais de posicionamento de clientes
- Definir tom, nome, preço
- Gravar vídeos de divulgação
- Conversar com os primeiros usuários

### O que precisamos de terceiros (mínimo)
- Domínio (R$ ~50/ano — Registro.br)
- Conta Stripe ou Hotmart para pagamentos
- Conta Anthropic com créditos de API

---

## Métricas que vamos acompanhar

**Semanas 1–5 (build):**
- Quantas perguntas o usuário abandona por módulo
- Tempo médio por módulo
- Qualidade subjetiva dos outputs (Victor avalia)
- Número de cards criados no Kanban por sessão

**Semana 6+ (produto ao vivo):**
- Taxa de conclusão do Módulo 1 (meta: >70%)
- Taxa de avanço entre módulos (meta: >50% de M1 para M2)
- Cards movidos até "Publicado" por semana por usuário
- Authority Score médio dos usuários ativos
- Retenção mensal (meta: >60%)
- NPS dos primeiros usuários

---

## O que torna esse produto defensável

1. **Os prompts são o IP** — qualquer dev pode chamar a Claude API. Ninguém tem o método da Taut destrinchado como lógica de sistema. Isso não é replicável facilmente.

2. **Contexto acumulado** — quanto mais o usuário usa, mais personalizado fica. Nicho → ICP → Branding → Conteúdo → Roteiro: tudo encadeado. Switching cost real.

3. **O loop de execução fecha** — a maioria das ferramentas de conteúdo para na ideia. Aqui o usuário vai da ideia ao roteiro gravável em um único sistema.

4. **Authority Score como hábito** — o score gamificado cria razão para voltar toda semana. Não é só uma ferramenta de setup, é uma plataforma de acompanhamento.

5. **Autoridade do Victor** — o produto é distribuído pela audiência que está sendo construída. Quem assiste o conteúdo da Taut vai naturalmente querer o produto.

6. **Funil para consultoria** — o produto não canibaliza a Taut. Quem quer mais compra a consultoria. São dois produtos para dois momentos diferentes do mesmo cliente.

---

*v2 — atualizado em março de 2026 com os módulos ICP, Kanban de Conteúdo e Authority Score.*
*Atualizar ao final de cada semana com o que foi concluído e o que mudou.*
