# FIAP-IA-Python_Basics — Contexto de Negócio

## Propósito
O repositório **FIAP-IA-Python_Basics** existe para apoiar o aprendizado e a prática de conceitos fundamentais em Python por meio de **notebooks Jupyter** e **scripts executáveis**. O objetivo de negócio é oferecer um ponto de referência simples e rápido para quem quer entender e exercitar fluxos básicos da linguagem, com exemplos que podem ser executados localmente.

Além disso, o repositório inclui **testes automatizados** (ex.: teste de soma) para validar o comportamento esperado de funções ensinadas no material. Isso melhora a confiabilidade do aprendizado: o estudante consegue verificar rapidamente se os exemplos estão corretos e se mudanças não quebram resultados básicos.

## Conceitos-chave
- **Função `soma(a, b)`:** função em Python que retorna a soma de dois valores a partir dos parâmetros de entrada.
- **Teste automatizado (pytest):** verificação que confirma se a função `soma` entrega o resultado esperado para entradas definidas.

## Regras de Negócio Críticas
- **`soma(a, b)` deve retornar exatamente `a + b`** para os parâmetros informados.
- **Testes devem permanecer válidos**: alterações em arquivos que definem ou exportam a função `soma` não podem fazer o teste unitário falhar.
- **Notebooks devem ser coerentes com as funções ensinadas**: os exemplos demonstrados não devem contradizer o comportamento esperado da função de soma.

## Integrações Principais
### Publica (eventos que emite)
- Nenhuma integração/evento de negócio identificado. **PREENCHER**

### Consome (eventos que processa)
- Nenhum consumo de eventos identificado. **PREENCHER**

### Chamadas HTTP
- Nenhuma chamada HTTP identificada (repositório educacional local). **PREENCHER**

## O que este serviço NÃO faz
- **Não é uma aplicação de produção** com infraestrutura de backend, filas, banco de dados ou integrações externas.
- **Não processa pagamentos, autenticação, nem integrações com sistemas externos**.
- **Não oferece APIs HTTP** ou endpoints de negócio.
- **Não implementa lógica complexa de IA**: o foco é aprendizado básico em Python (com suporte por notebooks).

## Decisões de Arquitetura Relevantes
- **Estrutura monolítica/organizada de forma simples** (scripts/notebooks), para reduzir barreiras de entrada e facilitar execução local.
- **Uso de função em arquivo separado (ex.: `pacotes.py`) e validação por teste (`test_soma.py`)**, para ensinar boas práticas mínimas: separação de código reutilizável e validação automática do comportamento.

## Owner
- Time: **PREENCHER**
- Contato: **PREENCHER**

---  
> ⚠️ Rascunho gerado automaticamente pelo Alicerce by Malha. Revise e enriqueça com contexto tácito antes de mergear.