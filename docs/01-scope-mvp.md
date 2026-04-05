# Escopo do MVP (MVP0 → MVP2)

Este documento define o que entra e o que não entra em cada fase do produto, alinhado à visão:
**recuperação por linguagem natural (caixa única)** como foco, suportada por
**catalogação → indexação (tradicional ou avançada/DIEL) → classificação/curadoria**.

---

## MVP0 — Fundamentos: catálogo mínimo + recuperação básica (texto)
**Objetivo:** colocar o sistema em uso rapidamente com o fluxo mínimo e uma primeira versão da “caixa única”.

Inclui:
- **Página inicial com input único** (caixa única) para consulta em linguagem natural (texto).
- **CRUD de obras (cadastro mínimo)**:
  - autor(es) (obrigatório)
  - títuto (obrigatório)
  - subtítulo (opcional no MVP0)
  - ano_publicacao (opcional)
- **Recuperação/busca básica** (matching textual):
  - por title e autor(es) (no mínimo)
  - resultados em lista com acesso ao detalhe da obra
- Persistência em MongoDB.
- Documentação mínima do contrato de API para CRUD.

Não inclui:
- Catalogação tradicional completa (campos bibliográficos completos)
- Indexação (tradicional e DIEL)
- Classificação / ficha catalográfica
- Tesauro / agente validador
- Busca semântica assistida
- Autenticação/controle de acesso

Critérios de aceite (MVP0):
- Usuário cadastra, edita e exclui obra.
- Usuário pesquisa via caixa única e encontra obras por texto em title/autor(es).
- Sistema roda localmente (dev) com frontend+backend.

---

## MVP1 — Catalogação tradicional completa + Indexação (DIEL mínimo) + Classificação (manual) + Ficha (tela + PDF)
**Objetivo:** consolidar o fluxo completo do stakeholder:
**catalogar → indexar → classificar → gerar ficha**.

Inclui:

### 1) Catalogação (modelo tradicional completo)
Campos do livro:
- autor(es)
- título
- subtítulo
- edição (obrigatório a partir da segunda edição)
- local
- editora
- ano_publicacao

> Observação: no MVP0 o cadastro pode ser mínimo; no MVP1 o formulário passa a contemplar o conjunto tradicional completo.

### 2) Indexação (modo avançado — DIEL mínimo útil)
- Forma composicional (mínimo viável, a ser detalhado no documento de regras/modelo):
  - suporte
  - gênero do discurso
  - língua
- Indexação final:
  - conceitos identificados (linguagem natural)
  - termos controlados (lista simples no MVP)
- status da indexação: `draft` / `reviewed`

### 3) Classificação/curadoria (manual)
- Seleção e consolidação dos termos indexados.
- Validação manual por **CDU ou CDD** (quando aplicável).
- Registro do resultado da classificação no sistema.

### 4) Ficha catalográfica
- Geração a partir dos dados cadastrados + classificação.
- Exibição em tela (copiável).
- Exportação em **PDF** (layout simples e evolutivo).

### 5) Recuperação (incremental)
- Caixa única permanece como ponto principal de consulta.
- Busca passa a considerar também termos controlados (quando presentes).
- (Opcional) filtros por termos controlados, se fizer sentido na UI.

Não inclui (ainda):
- Tesauro real (interno ou externo) como fonte de validação automática/assistida
- Busca semântica assistida
- Importação de registros (MARC etc.)
- Permissões por usuário

Critérios de aceite (MVP1):
- Usuário consegue preencher catalogação tradicional completa.
- Usuário consegue preencher indexação DIEL mínima e salvar como rascunho/revisado.
- Usuário consegue classificar manualmente e registrar validação CDU/CDD (quando aplicável).
- Usuário consegue gerar ficha catalográfica na tela e baixar PDF.
- Usuário consegue recuperar obra usando caixa única, incluindo match por termos controlados (quando existirem).

---

## MVP2 — Recuperação avançada + validações plugáveis (capacidade evolutiva)
**Objetivo:** aproximar o produto do “core” desejado: melhor recuperação por linguagem natural e maior consistência dos termos.

Inclui (direções possíveis, a confirmar com stakeholder):
- **Validação por tesauro (plugável)**:
  - integração com um tesauro existente OU suporte a um módulo/serviço de tesauro
  - tesauro atua como agente validador/normalizador de termos controlados
- **Busca semântica assistida** (capacidade futura):
  - melhorar o ranqueamento e a recuperação a partir de sentenças em linguagem natural
  - manter mecanismos de explicabilidade (por que este resultado apareceu)

Não inclui (por padrão, a menos que surja como necessidade):
- Multiusuário com permissões complexas
- Auditoria completa e histórico de revisões versionado
- Curadoria colaborativa em tempo real

Critérios de aceite (MVP2):
- Usuário comum recupera obras com maior precisão usando sentença livre.
- Curador observa melhora de consistência ao validar termos com tesauro (quando disponível).
- O sistema mantém transparência do motivo dos resultados.

---

## Fora de escopo (por enquanto)
- Construção garantida de um tesauro nacional completo (depende de disponibilidade/curadoria do domínio).
- Requisitos normativos formais completos para ficha catalográfica no primeiro corte (layout evolui por validação).
- Integrações externas (goodreads, openlibrary, etc.).