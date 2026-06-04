# FIAP-IA-Python_Basics — Arquitetura

## Visão Geral
O repositório `FIAP-IA-Python_Basics` adota uma abordagem **monolítica e orientada a aprendizado**, baseada em **scripts Python e notebooks Jupyter**. O objetivo principal não é servir como produto distribuído (sem API, filas ou orquestração), mas sim **facilitar execução local, experimentação e validação rápida**. A separação existente é intencionalmente mínima: existe uma função simples (ex.: `soma`) exposta em arquivo `.py` para permitir **importação** e **testabilidade**, enquanto os notebooks ficam como materiais de demonstração/execução.

## Stack Tecnológico
| Camada | Tecnologia | Motivo |
|---|---|---|
| Linguagem | Python | Compatibilidade com o ecossistema de notebooks, simplicidade para exemplos e facilidade para testes unitários. |
| Ambiente de execução / documentação executável | Jupyter Notebook (`.ipynb`) | Permite demonstrar conceitos com passo a passo, mantendo resultados visíveis durante a aprendizagem. |
| Testes automatizados | pytest (inferido por `test_soma.py`) | Garante regressão mínima para a lógica central (ex.: `soma`), sem complexidade adicional. |
| Código utilitário / organização mínima | `pacotes.py` | Centraliza funções reutilizáveis para que possam ser importadas pelos testes (e, potencialmente, pelos notebooks). |

## Padrões Adotados
- **Importação simples de módulo (separação por convenção):** a lógica (ex.: `soma`) é colocada em um arquivo Python para ser importada por outros componentes (como `test_soma.py`). Isso reduz acoplamento entre notebook e testes e melhora a reprodutibilidade.
- **Testes unitários como contrato mínimo:** o `pytest` atua como “contrato” para a regra de negócio `soma(a, b) = a + b`, permitindo verificar rapidamente se a implementação continua correta.

## Decisões de Arquitetura (ADRs)

### Centralização da lógica em arquivo Python para ser importada
- **Contexto:** notebooks Jupyter são ideais para exploração, mas não são a melhor unidade para testes automatizados e validação consistente.
- **Decisão:** manter a lógica em um arquivo Python (ex.: `pacotes.py`) e importar essa lógica no teste (`test_soma.py`), em vez de testar diretamente o conteúdo de notebooks.
- **Consequências:**  
  - ✅ Facilita execução automatizada e reduz flakiness comum de notebooks (estado global, ordem de execução).
  - ✅ Permite que a função seja reutilizada por notebooks e testes.
  - ❌ Menor organização formal (por pastas/módulos) do que uma arquitetura de produto; limites para evolução além do escopo educacional.
  - ❌ Se a lógica continuar crescendo, pode haver necessidade futura de refatoração para estrutura modular.

## Dependências Externas
| Dependência | Tipo | Propósito |
|---|---|---|
| pytest | `test` (biblioteca Python) | Executar e validar testes unitários (ex.: validação da função `soma`). |
| Jupyter Notebook | `runtime/ambiente` | Executar e documentar experimentos e exemplos (`.ipynb`). |
| PREENCHER | PREENCHER | PREENCHER |

## Pontos de Atenção
- **Escopo educacional vs. escalabilidade:** a estrutura atual é propositalmente simples (notebooks + um ou poucos módulos .py). Caso o repositório evolua para mais funcionalidades, pode ser necessário introduzir **estrutura de pacotes**, organização por módulos e padronização de entrada/saída.
- **Estado de notebooks:** notebooks dependem da ordem de execução e do estado da kernel; como mitigação, a lógica testável deve permanecer fora deles (como já ocorre via `pacotes.py`).
- **Cobertura limitada ao exemplo:** os testes inferidos focam em `soma`. Se houver mais regras/funções, é necessário ampliar a suíte de testes para manter confiabilidade.

---
> ⚠️ Rascunho gerado automaticamente pelo Alicerce by Malha. Valide com o time antes de mergear.