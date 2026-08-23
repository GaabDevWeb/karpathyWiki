---
id: xray-spec-known-issues
tipo: problema
status: atual
atualizado: 2026-08-23
---

# Problemas, lacunas e dívidas conhecidas

## 1) Ausência de testes automatizados evidentes

### Observação

Não foi encontrado diretório `tests/` nem ficheiros de teste explícitos no repositório.

### Status

**não confirmado** para a qualidade geral, mas claramente **não evidenciado** no snapshot analisado.

## 2) Dependência de API key do provedor activo

### Observação

O sistema só funciona com chave válida no provider escolhido. Se não houver configuração, o backend reporta `config_error` e o health fica em `degraded`.

### Risco

Qualquer operação real depende do ambiente correto.

### Status

Atual.

## 3) CORS e origem do frontend

### Observação

O README documenta que o erro comum é CORS bloqueado; `XRAY_CORS_ORIGINS` precisa corresponder exatamente à origem do frontend.

### Status

Atual.

## 4) Histórico sem persistência no backend

### Observação

O histórico fica em `localStorage` do navegador; o backend não persiste análises em banco ou arquivo.

### Impacto

A análise histórica não sobrevive a limpar dados do navegador nem a múltiplos dispositivos.

### Status

Atual.

## 5) Infraestrutura de produção não evidenciada

### Observação

O projecto parece ser um app local de inspeção e pesquisa em especificações, sem serviços de autenticação, filas, banco, observabilidade ou deploy explícito.

### Status

**não confirmado** como ausência definitiva, mas não observada no repositório.

## 6) Não há branches paralelas relevantes

### Observação

A análise Git não encontrou feature branches relevantes.

### Status

Atual; não é um problema funcional, mas limita a visão de evolução paralela.
