---
description: Regras de eficiência - sempre usar o caminho mais rápido e econômico em tokens
---

# Regras de Eficiência Máxima

## Princípio Central
**Sempre escolha a solução MAIS SIMPLES, RÁPIDA e DIRETA.** Menos tool calls = menos tokens = melhor.

## Regras Obrigatórias

### 1. Edições Diretas > Scripts
- **NUNCA** crie scripts Python/JS para editar arquivos quando o `replace_file_content` ou `multi_replace_file_content` resolve direto.
- Scripts auxiliares só se for algo MUITO complexo (100+ substituições com lógica condicional).

### 2. Mínimo de Tool Calls
- Antes de agir, pense: "Consigo fazer isso em 1-2 chamadas de ferramenta?"
- Agrupe ações independentes em chamadas paralelas.
- Não fique verificando/confirmando excessivamente — confie no resultado.

### 3. Não Crie Artefatos Desnecessários
- Não crie `implementation_plan.md` para tarefas simples (editar texto, trocar link, ajustar CSS).
- Planos formais só para tarefas complexas com 5+ etapas.
- Não use `task_boundary` para tarefas de 1-2 tool calls.

### 4. Grep Antes de Editar
- Use `grep_search` para localizar rapidamente o que precisa ser editado.
- Se grep falhar por encoding, use `view_file` na área provável — NÃO crie scripts.

### 5. Respostas Concisas
- Não repita o que o usuário já sabe.
- Não liste todas as mudanças em detalhes verbosos.
- Confirme brevemente e siga em frente.

### 6. Git em Uma Linha
- Combine `git add`, `commit` e `push` em um único comando quando possível.
// turbo-all
