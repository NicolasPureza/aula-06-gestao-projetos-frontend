# Gestão de Projeto Front-End — NEXA (Projeto Integrador)

**Projeto:** NEXA — Sistema de Monitoramento do Desempenho Acadêmico de Estudantes  
**Metodologia:** Scrum + Kanban + Git Flow simplificado

---

## 1. Visão do Produto e Requisitos

O **NEXA** tem como objetivo permitir que docentes, coordenação e estudantes acompanhem indicadores de desempenho acadêmico (notas, frequência, entregas de atividades e alertas de risco de evasão/reprovação) de forma visual e centralizada.

### Requisitos Funcionais Principais
- **RF01:** Autenticação e perfis de acesso (Estudante, Professor, Coordenação).
- **RF02:** Painel (Dashboard) com indicadores gerais de notas, frequência e evolução por disciplina.
- **RF03:** Cadastro e lançamento de avaliações, notas e faltas por turma/disciplina.
- **RF04:** Sistema de alertas automáticos para estudantes com média abaixo do esperado ou baixa frequência.
- **RF05:** Relatórios individuais e por turma com filtros por período e disciplina.

---

## 2. Product Backlog (User Stories, Prioridades e Estimativas)

Escala de estimativa utilizada: **Story Points (Fibonacci: 1, 2, 3, 5, 8, 13)**.

| ID | User Story | Prioridade | Estimativa (SP) | Sprint |
| :--- | :--- | :---: | :---: | :---: |
| **US01** | Como usuário, quero fazer login com meu perfil para acessar apenas as funcionalidades do meu nível. | Alta | 5 | Sprint 1 |
| **US02** | Como estudante, quero visualizar meu painel com médias, frequência e status por disciplina. | Alta | 8 | Sprint 1 |
| **US03** | Como professor, quero listar minhas turmas e lançar notas/frequência dos estudantes. | Alta | 8 | Sprint 2 |
| **US04** | Como coordenador, quero visualizar alertas de estudantes em situação de risco acadêmico. | Média | 5 | Sprint 2 |
| **US05** | Como usuário, quero filtrar o histórico acadêmico por semestre e disciplina. | Média | 3 | Sprint 3 |
| **US06** | Como coordenador, quero exportar um resumo de desempenho da turma em formato legível. | Baixa | 5 | Sprint 3 |

---

## 3. Quebra em Tarefas Técnicas (Exemplo da Sprint 1)

### US01 — Autenticação e Perfis
- **T1.1:** Criar componente de formulário de login controlado (`email`, `senha`) — *2h*
- **T1.2:** Validar campos obrigatórios e exibir mensagens de erro — *1h*
- **T1.3:** Integrar chamada `POST /api/auth/login` com tratamento de erro HTTP — *2h*
- **T1.4:** Configurar rotas protegidas por perfil no React Router — *3h*

### US02 — Dashboard do Estudante
- **T2.1:** Estruturar layout responsivo com cards de resumo (média geral, frequência, disciplinas) — *3h*
- **T2.2:** Criar componente reutilizável `CardDisciplina` recebendo dados via `props` — *2h*
- **T2.3:** Consumir endpoint `GET /api/estudante/desempenho` com `useEffect` e estados de carregamento/vazio — *3h*
- **T2.4:** Revisar responsividade em telas mobile e desktop — *2h*

---

## 4. Planejamento das Sprints

- **Duração da Sprint:** 2 semanas (10 dias úteis).
- **Cerimônias:**
  - *Sprint Planning:* definição do escopo da Sprint a partir das prioridades do Backlog.
  - *Daily Stand-up (15 min):* o que foi feito, o que será feito hoje e impedimentos.
  - *Sprint Review:* demonstração funcional das telas entregues.
  - *Sprint Retrospective:* lições aprendidas e melhorias no processo da equipe.

---

## 5. Estratégia de Branches no Git

- `main`: código estável e pronto para produção (deploy automático).
- `develop`: integração das funcionalidades concluídas na Sprint.
- `feature/<id>-<nome>`: branches individuais por tarefa/história (ex.: `feature/us01-tela-login`, `feature/us02-dashboard-estudante`).
- `fix/<descricao>`: correções pontuais de bugs identificados em revisão/teste.

**Regra de fluxo:** toda `feature/*` é integrada em `develop` via Pull Request após revisão de código e validação dos critérios de conclusão.

---

## 6. Definition of Done (DoD — Critérios de Conclusão)

Uma tarefa ou User Story só é considerada **Concluída (Done)** quando atender a todos os critérios abaixo:
1. Código implementado seguindo os padrões de componentização e nomenclatura do projeto.
2. Interface validada em layout responsivo (mobile e desktop) sem quebras visuais.
3. Integração com API testada (incluindo estados de carregamento, erro e lista vazia).
4. Sem erros ou alertas críticos no console do navegador e no build (`npm run build`).
5. Código revisado por pelo menos um integrante da equipe via Pull Request.
6. Branch mesclada em `develop` e card atualizado para a coluna **Concluído** no quadro Kanban.
