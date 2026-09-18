# Delivery Truck Pallet Packing Optimization

[English Version](README_EN.md)

> Ferramenta em C++ para otimizar o carregamento de paletes num camião de entregas, uma variante do problema da Mochila 0/1 (0/1 Knapsack).

## Autores

| Nome                           | E-Mail                   |
| ------------------------------ | ------------------------ |
| Ana Catarina Monteiro de Sousa | up202306419@edu.fe.up.pt |

## Contexto Académico

- **Unidade Curricular:** Desenho de Algoritmos
- **Instituição:** FEUP — Faculdade de Engenharia da Universidade do Porto
- **Ano/Semestre:** 2024/2025 — 2.º semestre
- **Nota obtida:** 18.5/20

## Descrição

O objetivo é resolver o **Delivery Truck Pallet Packing Optimization Problem**, uma variante real do **Problema da Mochila 0/1**. O objetivo é maximizar o lucro total das paletes carregadas num camião de entregas sem exceder a sua capacidade máxima de peso.

### Algoritmos Implementados

A ferramenta disponibiliza quatro abordagens algorítmicas diferentes para resolver o problema:

1. **Brute-Force (Pesquisa Exaustiva)**
   - Explora todos os subconjuntos possíveis de paletes para encontrar a solução ótima absoluta.
   - **Complexidade temporal:** O(2ⁿ), onde n é o número de paletes.
   - **Complexidade espacial:** O(n) (profundidade da recursão).

2. **Dynamic Programming (Programação Dinâmica)**
   - Usa uma tabela 2D para guardar o lucro máximo de subproblemas.
   - **Regras de tie-breaking:** se duas combinações têm o mesmo lucro, prefere a com menos paletes; se ainda houver empate, prefere a com a menor soma dos índices originais.
   - **Complexidade temporal:** O(n · W), onde W é a capacidade do camião.
   - **Complexidade espacial:** O(n · W) para a tabela de DP.

3. **Greedy (Algoritmo Voraz)**
   - Algoritmo de aproximação que seleciona paletes com base na razão **lucro/peso**.
   - **Complexidade temporal:** O(n log n) devido à ordenação.
   - **Complexidade espacial:** O(n).

4. **Híbrido**
   - Combina a abordagem Greedy com a Programação Dinâmica.
   - Calcula primeiro uma base com a heurística Greedy e depois executa a DP para encontrar a solução ótima, permitindo comparações de desempenho.

## Tecnologias Utilizadas

- C++ (C++14)
- CMake (≥ 3.29)
- Doxygen (documentação)
- Ficheiros CSV para input/output

## Estrutura do Projeto

```text
.
├── code/                       # Código-fonte
│   ├── algorithms/             # Implementação dos algoritmos de otimização
│   ├── input_output/           # Leitura de CSV e impressão de resultados
│   ├── menu/                   # Implementação do menu CLI
│   ├── structs/                # Estruturas de dados (palete, camião)
│   ├── functions.h             # Header principal com prototypes das funções
│   └── main.cpp                # Ponto de entrada do programa
├── datasets/                   # Ficheiros CSV de input (capacidade do camião e dados das paletes)
├── documentation/              # Documentação gerada com Doxygen (HTML/LaTeX)
├── Project_2_Description.pdf   # Enunciado oficial do projeto
├── presentation.pdf            # Apresentação e demonstração de resultados
├── CMakeLists.txt              # Configuração de build
└── Doxyfile                    # Configuração do Doxygen
```

## Requisitos

- **CMake** (versão 3.29 ou superior)
- **Compilador C++** com suporte para C++14

## Como Compilar / Executar

### Compilação

Para compilar o projeto, executar os seguintes comandos na raiz do repositório:

```bash
mkdir build
cd build
cmake ..
make
```

### Execução

Depois de compilado, executar o programa:

```bash
./DA_project2
```

## Como Usar

A aplicação disponibiliza uma interface de linha de comandos:

1. **Selecionar dataset:** introduzir o número do dataset a testar (ex.: `1` para `datasets/Pallets_01.csv`).
2. **Escolher algoritmo:** selecionar um dos quatro algoritmos disponíveis para processar os dados.
3. **Ver resultados:** o programa apresenta o lucro máximo, o número de paletes selecionadas, o tempo de execução e os detalhes de cada palete selecionada.

### Datasets

Os dados de input são fornecidos em dois ficheiros CSV por dataset:

- `TruckAndPallets_<X>.csv` — contém a `Capacity` (capacidade) e o número total de `Pallets` (paletes).
- `Pallets_<X>.csv` — contém o `Pallet` (ID), `Weight` (peso) e `Profit` (lucro) de cada item.

## Notas Adicionais

O código está totalmente documentado com **Doxygen**. A documentação gerada encontra-se em `documentation/html/` — para a consultar, abrir `documentation/html/index.html` num browser.
