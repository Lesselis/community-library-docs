# Visão do Produto — Community Library

## 1. Problema
Pessoas (leitores em geral, estudantes, pesquisadores e também bibliotecários) frequentemente querem
encontrar obras literárias a partir de **uma lembrança incompleta** (um verso, uma frase, um trecho ouvido)
ou a partir de **uma intenção de descoberta** (“quero ler sobre X”, “quero entender melhor Y”, “quais autores são referência nesse tema?”).

Soluções tradicionais de catálogo/biblioteca normalmente pressupõem que o usuário já saiba “o que procurar”
(título, autor, assunto formal). Isso restringe a descoberta e dificulta a recuperação quando a consulta parte de linguagem natural e memória fragmentada.

## 2. Objetivo
Criar uma aplicação em que o ponto central de uso seja a **recuperação e descoberta** por meio de uma
**única caixa de busca** na página principal, com sugestões no placeholder indicando as possibilidades de consulta em linguagem natural (versos, temas, descrições, intenções).

Exemplos:
- “um verso sobre saudade e mar”
- “livros sobre crise existencial”
- “poemas que falem de autoritarismo”
- “quero conhecer autores centrais do romantismo brasileiro”

Para que essa recuperação seja possível e confiável, a aplicação também deve permitir:
- **Catalogação** de obras (base do acervo)
- **Indexação** (em modo tradicional e/ou avançado — DIEL), enriquecendo a recuperabilidade
- **Classificação/curadoria** (pós-indexação), consolidando e validando os termos utilizados

## 3. Públicos-alvo (MVP)
### P1 — Usuário/leitor (principal para recuperação)
- Quer encontrar obras por linguagem natural com mínimo esforço.
- Não domina vocabulário técnico de catalogação.
- Quer resultados e também caminhos de descoberta (autores, obras relacionadas, temas).

### P2 — Bibliotecário(a) / Curador(a) (principal para qualidade e consistência)
- Cadastra obras e realiza indexação (tradicional e/ou DIEL) de forma progressiva.
- Consolida e valida a classificação, melhorando a qualidade da recuperação ao longo do tempo.
- Atua como “feedback loop” do sistema: ao observar falhas de recuperação, ajusta indexação/classificação.

## 4. Proposta de valor
- **Recuperação por linguagem natural com um único input**: o usuário descreve o que lembra ou o que procura
  sem precisar conhecer campos técnicos.
- **Indexação flexível (tradicional e avançada)**:
  - modo tradicional para viabilizar fluxo rápido
  - modo avançado (DIEL) para capturar elementos literários e dialógicos quando necessário
- **Classificação como etapa obrigatória de consolidação (curadoria)**: após indexar, o curador seleciona e
  consolida termos e pode validar por esquemas de classificação (ex.: CDU/CDD), quando aplicável.
- **Ficha catalográfica gerada**: a partir dos dados cadastrados e da classificação, o sistema deve permitir
  gerar ficha catalográfica **na tela (copiável)** e **exportável (PDF)**.
- **Validação de termos por tesauro (capacidade evolutiva, não compromisso do MVP)**: a aplicação pode, no futuro,
  incorporar um tesauro (existente ou a ser construído) operando como um **agente validador** para normalizar termos
  e melhorar consistência e recuperação.

## 5. Princípios do produto
1. **A recuperação vem primeiro**: o sistema deve ser útil para usuários comuns, não apenas para bibliotecários.
2. **Curadoria incrementa qualidade**: a precisão melhora continuamente por indexação, classificação e revisão.
3. **Iteração orientada a stakeholder**: UX, critérios de recuperação e formato da ficha devem ser validados com uso real.
4. **Evolução por camadas**:
   - iniciar com catalogação + busca textual e filtros (MVP0/MVP1)
   - evoluir para busca semântica e/ou assistida (MVP2+), conforme maturidade e necessidade
5. **Transparência**: quando houver ranqueamento avançado/recomendações, o usuário deve conseguir entender
   “por que” uma obra apareceu (explicabilidade).

## 6. Métricas de sucesso (iniciais)
- Usuário comum consegue recuperar ao menos uma obra relevante a partir de uma sentença em linguagem natural (meta do produto).
- Usuário consegue refinar resultados sem aprender “como biblioteca funciona” (experiência simples).
- Curador consegue melhorar resultados ajustando indexação/classificação (feedback loop observável).
- Geração de ficha catalográfica atende ao fluxo do stakeholder (visual + PDF).

## 7. Premissas e restrições
- O MVP pode começar com recuperação simples (texto/termos) e evoluir para semântica/assistida.
- Tesauro não é requisito do MVP inicial; é uma capacidade evolutiva (integração plugável) para validação/normalização.
- Persistência em MongoDB.
- Frontend em React (Vite) + RSuite.
- Backend em JAVA (Spring Boot).