# FIAP-IA-Python_Basics — Runbook Operacional

## Informações Básicas
| Item | Valor |
|---|---|
| Porta padrão | PREENCHER |
| Health check | PREENCHER |
| Logs | PREENCHER |
| Métricas | PREENCHER |
| Alertas críticos | PREENCHER |

## Health Check e Monitoramento

### Verificar se o “serviço” está saudável
> Este repositório é educacional (scripts/notebooks) e não foi identificado como um serviço HTTP com health check. Use os checks abaixo como “health” do projeto/execução.

1) **Validar testes unitários (pytest)**
```bash
pytest -q
```

**Resposta esperada:** `OK` (sem falhas) — saída sem `FAILED`.

2) **Validar import da implementação**
```bash
python -c "from pacotes import soma; print(soma(2, 3))"
```

**Resposta esperada:** `5` (para exemplo fixo).

### Indicadores de problema
- `pytest` falha (ex.: `FAILED`, erros de import, erro de asserção na função `soma`)
- Erro ao importar `soma` via `pacotes.py` (ex.: `ImportError`, `ModuleNotFoundError`)
- `soma(a, b)` não retorna `a + b` (ex.: retornando tipo incorreto, ordem trocada, coerção inesperada)
- Erros específicos nos notebooks (ex.: traceback em células que importam `pacotes.py`)

## Procedimentos Comuns

### Rodar a suíte de testes (diagnóstico rápido)
```bash
pytest -q
```

### Executar diretamente o “caso soma” (diagnóstico rápido)
```bash
python -c "from pacotes import soma; assert soma(1, 2) == 3; assert soma(-1, 1) == 0; print('soma OK')"
```

### Verificar logs/erros de execução
Como o projeto não tem “logs de runtime” definidos, o artefato principal é a **saída do terminal** e o **traceback** ao executar:
- `pytest` (falhas)
- `python -c ...` (import e execução)
- execução de células no Jupyter (`.ipynb`)

> Se o ambiente estiver configurado para salvar logs, verifique onde o projeto foi instruído a gravar (PREENCHER).

### Executar notebooks (reprodução do erro)
1) Rode em modo notebook (interativo) ou escolha a abordagem recomendada do seu ambiente.
2) Para reproduzir com traceback “limpo”, execute o conteúdo diretamente via execução do notebook (conforme seu fluxo local).

**Observação 3h:** se o erro acontece em notebook, comece pelo primeiro ponto onde a célula falha e verifique se o notebook está importando corretamente `pacotes.py`.

### Atualizar dependências do ambiente (quando falha por ambiente)
```bash
pip install -r PREENCHER
```
Se não houver `requirements.txt`, então:
```bash
pip install pytest
```

## Troubleshooting

### Problema: `pytest` falha com `ImportError`/`ModuleNotFoundError` ao importar `soma`
**Causa provável:** nome do arquivo/módulo diferente do esperado, erro no `pacotes.py`, diretório atual incorreto, ou ausência de `soma` exportada/importável.

**Como diagnosticar:**
1) Confirme que `pacotes.py` existe na raiz:
```bash
ls -la
```
2) Tente importar e imprimir a função:
```bash
python -c "import pacotes; print(dir(pacotes)); print(getattr(pacotes, 'soma', None))"
```
3) Rode `pytest` com detalhes:
```bash
pytest -vv
```

**Como resolver:**
- Corrigir `pacotes.py` para definir/expôr `soma` com a assinatura esperada (ex.: `def soma(a, b): ...`).
- Garantir que `test_soma.py` faça import correto (ex.: `from pacotes import soma`) e que a execução do `pytest` ocorra na pasta raiz do projeto.
- Se o projeto usa outro caminho, ajustar `PYTHONPATH` no seu ambiente (PREENCHER).

---

### Problema: `pytest` falha por asserção (ex.: `soma(1,2) != 3`)
**Causa provável:** implementação de `soma` incorreta (erro de lógica), troca de parâmetros, tratamento indevido de tipos, ou retorno de outro valor.

**Como diagnosticar:**
1) Rode uma bateria mínima:
```bash
python -c "from pacotes import soma; print('1+2=', soma(1,2)); print('-1+1=', soma(-1,1)); print('2+0=', soma(2,0))"
```
2) Abra `test_soma.py` e verifique exatamente o que ele espera (casos de teste).

**Como resolver:**
- Ajustar `soma` para retornar exatamente `a + b`:
```python
def soma(a, b):
    return a + b
```
- Reexecutar:
```bash
pytest -q
```

---

### Problema: Notebook quebra ao executar célula que importa `pacotes.py`
**Causa provável:** diferença entre o diretório de execução do notebook e a raiz do projeto; mudanças recentes no arquivo; kernel iniciado em pasta diferente.

**Como diagnosticar:**
1) No notebook, verifique o erro completo (traceback).
2) Em uma célula do notebook, rode:
```python
import os, sys
print(os.getcwd())
print(sys.path[:5])
import pacotes
print(hasattr(pacotes, 'soma'))
```

**Como resolver:**
- Garantir que o notebook esteja sendo executado com o working directory do projeto (raiz onde está `pacotes.py`).
- Reorganizar imports no notebook para usar a mesma forma do `test_soma.py` (ex.: `from pacotes import soma`).
- Reiniciar kernel e reexecutar células em ordem (Start/Kernel restart).

---

### Problema: testes passam, mas o resultado no notebook está errado
**Causa provável:** o notebook não está usando a mesma função/versão (import de módulo antigo), ou existe uma redefinição local de `soma` no notebook.

**Como diagnosticar:**
1) No notebook, imprima a origem do módulo:
```python
import pacotes, inspect
print(pacotes.__file__)
print(inspect.getsource(pacotes.soma))
```
2) Verifique se há outra definição de `soma` em células do notebook.

**Como resolver:**
- Remover/evitar redefinições locais.
- Reiniciar kernel e reexecutar do zero.
- Garantir que `pacotes.py` salvo está consistente com o que o notebook importa (mesmo caminho).

## Dependências Críticas
| Dependência | O que acontece se cair | Fallback |
|---|---|---|
| `pacotes.py` (definição/import de `soma`) | `test_soma.py` falha com import/asserção | Corrigir `soma` em `pacotes.py` e reexecutar `pytest -q` |
| Ambiente Python com `pytest` disponível | não consegue validar testes | Instalar `pytest` (`pip install pytest`) e rerodar suíte |
| Ambiente do Jupyter (kernel/pasta de execução) | notebooks falham por imports/localização | Restart do kernel e ajuste do working directory |

## Contatos de Escalação
- **Primeiro:** PREENCHER
- **Segundo:** PREENCHER