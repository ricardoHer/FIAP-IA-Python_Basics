# FIAP-IA-Python_Basics — Glossário de Domínio

> Termos e conceitos usados neste repositório e seus significados no contexto do negócio (aprendizado/exercícios em Python).
> Use este glossário ao ler o código, escrever testes ou comunicar com outros times.

## Termos de Negócio

### Soma
**Definição:** Cálculo do resultado da operação `a + b`, representando a “funcionalidade” demonstrada no repositório.  
**No código:** Função `soma(a, b)` (conforme descrito na análise); também coberta por `test_soma.py` (casos de teste).  
**Não confundir com:** “Somatório” genérico (p. ex., soma de uma lista). Aqui é explicitamente soma de *dois* valores.

---

### Parâmetros de Entrada (a, b)
**Definição:** Valores recebidos pela função `soma` que determinam o resultado final.  
**No código:** Assinatura da função `soma(a, b)`.  
**Não confundir com:** Entradas de outros exercícios/notebooks que possam existir em `exemplo-*.ipynb` (não especificados na análise).

---

### Resultado da Soma
**Definição:** Valor retornado pela função `soma(a, b)` após aplicar a operação `a + b`.  
**No código:** Retorno de `soma(a, b)`; validado em `test_soma.py`.  
**Não confundir com:** qualquer “estado” persistido em arquivo; neste repositório, trata-se do valor calculado em tempo de execução.

---

## Termos Técnicos do Domínio

### `soma(a, b)`
**Definição:** Função Python que retorna a soma de dois parâmetros usando a expressão `a + b`.  
**Contexto de uso:** Implementação principal do conceito demonstrado; chamada pelos testes em `test_soma.py` e possivelmente por notebooks/scripts.

---

### Regras de Negócio da Soma
**Definição:** Conjunto de condições que a função deve cumprir: “a função soma deve retornar a expressão `a + b` para os parâmetros informados”.  
**Contexto de uso:** Expectativa formalizada pelos testes unitários (ex.: `test_soma.py`).

---

### `SomaDeDoisNumeros`
**Definição:** Modelo conceitual (entidade de dados) que representa o resultado do cálculo da soma de dois valores.  
**No código:** **PREENCHER** (não foi encontrado mapeamento explícito em classe/arquivo; a análise menciona como entidade de dados a ser considerada no domínio).  
**Não confundir com:** uma classe real inexistente no repositório, caso não tenha sido implementada.

---

### Teste Unitário de Soma
**Definição:** Verificação automatizada do comportamento de `soma`, assegurando que o retorno corresponda a `a + b`.  
**Contexto de uso:** `test_soma.py` (inferido por análise como testes com pytest).

---

### `pytest`
**Definição:** Framework de testes usado para executar e reportar resultados dos testes unitários.  
**Contexto de uso:** `test_soma.py` (inferido).

---

### `pacotes.py`
**Definição:** Arquivo Python auxiliar que provavelmente agrupa/centraliza funções e/ou exemplos para serem importados em outros arquivos.  
**Contexto de uso:** Integração simples entre definição de função e consumo pelos testes/notebooks (conforme descrito na análise).

---

### Notebooks de Exemplos (`exemplo-1.ipynb` a `exemplo-4.ipynb`)
**Definição:** Materiais educacionais com execuções e demonstrações de conceitos Python.  
**Contexto de uso:** Podem conter chamadas à função `soma` e/ou exemplos relacionados; **PREENCHER** quais exatamente, pois não foi detalhado na análise.

---

### Arquivo Auxiliar (`arquivo.txt`)
**Definição:** Conteúdo textual usado como instrução/observação simples do repositório.  
**Contexto de uso:** Guia/documentação leve; **PREENCHER** se contém detalhes sobre `soma`, execução de testes ou importação.

---

## Acrônimos e Abreviações

| Sigla | Significado | Contexto |
|---|---|---|
| PREENCHER | PREENCHER | PREENCHER |