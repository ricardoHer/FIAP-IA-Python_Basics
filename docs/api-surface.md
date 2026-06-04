# FIAP-IA-Python_Basics — Superfície de API

## Visão Geral
- **Tipo:** PREENCHER *(não há evidência de API HTTP/GraphQL/gRPC no repositório; apenas função Python e testes unitários)*
- **Base URL:** PREENCHER
- **Autenticação:** sem auth
- **Formato:** N/A *(contrato via função Python)*

## “EndPoints” (Contratos Públicos em Python)

### `soma(a, b)` (função Python)
**Descrição:** Calcula a soma de dois valores numéricos e retorna o resultado da expressão `a + b`.

**Request (chamada da função):**
```python
resultado = soma(a, b)
```

**Parâmetros:**
- `a` (número): primeiro valor para soma
- `b` (número): segundo valor para soma

**Response (retorno):**
```python
return a + b
```

**Erros comuns:**
| Cenário | Quando ocorre |
|---|---|
| PREENCHER | PREENCHER |
| PREENCHER | PREENCHER |

> Observação: o repositório indica testes para a função `soma` (ex.: `test_soma.py`), porém não foram fornecidos os cenários de erro/validações (tipos, limites, exceções). Portanto, os comportamentos de erro não podem ser documentados com precisão.

## Autenticação e Autorização
- **N/A** — não existe camada de API remota. A “integração” ocorre via importação e execução local em Python (ex.: `test_soma.py` importando de `pacotes.py`).

## Rate Limiting
- **N/A** — não existe serviço HTTP.

## Versionamento
- **N/A** — não foi identificado versionamento de API (sem endpoints/servidor).  
- **Sugestão (para quando houver empacotamento):** seguir SemVer para a função/código, mantendo retrocompatibilidade quando possível.