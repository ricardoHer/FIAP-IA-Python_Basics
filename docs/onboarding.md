# FIAP-IA-Python_Basics — Guia de Onboarding

## O que você precisa saber primeiro
Este repositório **é educacional e simples**, pensado para você rodar exemplos de Python em **notebooks (.ipynb)** e também validar uma funcionalidade mínima com **testes unitários (pytest)**. Não existe uma “arquitetura de aplicação” complexa aqui — o objetivo é aprender e executar localmente.

O foco funcional identificado é a função **`soma(a, b)`**, que retorna **`a + b`**. Ela aparece/é usada via arquivos Python (principalmente **`pacotes.py`**) e é exercitada pelos testes em **`test_soma.py`**. Os notebooks (`exemplo-1.ipynb` a `exemplo-4.ipynb`) servem como camadas de demonstração de conceitos (provavelmente importação, execução de funções, variáveis etc.), mas o comportamento crítico para validação automática está nos testes.

---

## Como rodar localmente

### Pré-requisitos
- **Python 3.9+** (recomendado)
- **pytest**
  - Instale com:
    ```bash
    pip install -U pytest
    ```

> Se existir `requirements.txt` ou configuração de ambiente no repositório, use-o. Caso não exista, o onboarding acima já cobre o mínimo para rodar os testes.

### Passos
```bash
# 1) Clone
git clone <URL_DO_REPOSITORIO>
cd FIAP-IA-Python_Basics

# 2) Rodar testes
pytest -q

# 3) (Opcional) Abrir notebooks
# - Use Jupyter local: jupyter notebook
# - ou via seu ambiente/IDE
```

### Configurações necessárias
| Variável | Valor local | Para que serve |
|---|---|---|
| PREENCHER | PREENCHER | PREENCHER |

---

## Arquitetura em 5 minutos
Pensa aqui como um “mini-projeto”:
- **`pacotes.py`**: concentra funções/exemplos (incluindo a **`soma`**) que você importa em outros lugares.
- **`test_soma.py`**: contém os testes unitários para validar a regra de negócio: **`soma(a, b)` retorna `a + b`**.
- **`exemplo-1.ipynb` … exemplo-4.ipynb`**: notebooks para executar/observar comportamento.

Não há separação por camadas (controllers/services/domain) — se você quiser entender o comportamento, a regra está essencialmente entre **`pacotes.py`** e **`test_soma.py`**. Os notebooks são “lado a lado” para aprendizado e ver execuções manuais.

---

## Onde está cada coisa
| O que procuro | Onde encontro |
|---|---|
| Função `soma(a, b)` | `pacotes.py` |
| Testes automatizados (pytest) | `test_soma.py` |
| Exemplos/demonstrações em Jupyter | `exemplo-1.ipynb`, `exemplo-2.ipynb`, `exemplo-3.ipynb`, `exemplo-4.ipynb` |
| Alguma observação/instruções extras | `arquivo.txt` |
| Código auxiliar de “pacotes”/importações | `pacotes.py` |

---

## Fluxos principais para entender primeiro
1. **Validação da regra `soma` (pytest)** — começa em `test_soma.py`, chama/importa a função em `pacotes.py`, e termina quando o resultado esperado bate com `a + b`.
2. **Execução manual dos exemplos** — começa em um notebook (`exemplo-*.ipynb`) e termina com a observação/execução de chamadas (provavelmente incluindo import da `soma`).

---

## Armadilhas comuns
- **Import quebrado por caminho**: como é um repo simples, dependendo de como você roda os testes/notebooks, pode dar erro de import se o Python não enxergar o diretório certo. Se o `pytest` reclamar de `ModuleNotFoundError`, ajuste sua forma de execução (rode sempre na raiz do repo) ou corrija o import em `test_soma.py`.
- **Diferença entre execução no notebook e no pytest**: notebooks muitas vezes “funcionam” por causa do estado do kernel (variáveis já carregadas/importações feitas antes). Para validar regra de negócio, confie nos testes (`pytest`), não só no notebook.
- **Assinatura/retorno da função**: se alguém modificar `soma` para retornar algo diferente (ex.: string, tipo diferente, conversão), o teste vai falhar. O contrato esperado é estritamente `a + b`.

---

## Quem perguntar
- **Dúvidas de negócio:** PREENCHER  
- **Dúvidas técnicas:** PREENCHER  

---
> ⚠️ Rascunho gerado automaticamente pelo Alicerce by Malha. Adicione os passos reais de setup antes de mergear.