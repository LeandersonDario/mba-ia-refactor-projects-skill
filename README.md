# MBA IA — Refatoração arquitetural com Skills

Desafio de criação de uma **Skill `refactor-arch`** para o Claude Code que analisa, audita e refatora projetos legados para o padrão MVC de forma automática e agnóstica de tecnologia.

## Onde está o trabalho

| Artefato | Caminho |
|----------|---------|
| Documentação completa (análise, skill, resultados, como executar) | [`desafio-skills/README.md`](desafio-skills/README.md) |
| Enunciado do curso | [`desafio-skills/ENUNCIADO.md`](desafio-skills/ENUNCIADO.md) |
| Skill `refactor-arch` | `desafio-skills/<projeto>/.claude/skills/refactor-arch/` |
| Relatórios de auditoria | [`desafio-skills/reports/`](desafio-skills/reports/) |
| Projeto 1 — Python/Flask e-commerce | [`desafio-skills/code-smells-project/`](desafio-skills/code-smells-project/) |
| Projeto 2 — Node.js/Express LMS | [`desafio-skills/ecommerce-api-legacy/`](desafio-skills/ecommerce-api-legacy/) |
| Projeto 3 — Python/Flask Task Manager | [`desafio-skills/task-manager-api/`](desafio-skills/task-manager-api/) |

## Pré-requisitos

- [Claude Code](https://docs.anthropic.com/en/docs/claude-code/overview) instalado e autenticado
- Python 3.10+ e Node.js 18+

## Executar a Skill

```powershell
# Projeto 1 — Python/Flask e-commerce
cd desafio-skills\code-smells-project
claude "/refactor-arch"

# Projeto 2 — Node.js/Express LMS
cd ..\ecommerce-api-legacy
claude "/refactor-arch"

# Projeto 3 — Python/Flask Task Manager
cd ..\task-manager-api
claude "/refactor-arch"
```

## Validar os projetos refatorados (smoke tests)

```powershell
# Projeto 1 (porta 5000)
cd desafio-skills\code-smells-project
pip install -r requirements.txt
python app.py
# Em outro terminal:
curl http://localhost:5000/health
curl http://localhost:5000/produtos

# Projeto 2 (porta 3000)
cd desafio-skills\ecommerce-api-legacy
npm install
npm start
# Em outro terminal:
curl http://localhost:3000/api/admin/financial-report

# Projeto 3 (porta 5000)
cd desafio-skills\task-manager-api
pip install -r requirements.txt
python app.py
# Em outro terminal:
curl http://localhost:5000/health
curl http://localhost:5000/tasks
```

Todos os endpoints devem retornar **HTTP 200**. Consulte [`desafio-skills/README.md`](desafio-skills/README.md) para o checklist de validação completo por projeto.
