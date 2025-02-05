# Eight-Queens-Genetic-Algorithm

O projeto criado para disciplina de Computação Bioinspirada implementa uma solução para o problema das Oito Rainhas utilizando um Algoritmo Genético. O objetivo é posicionar oito rainhas em um tabuleiro de xadrez 8x8 de forma que nenhuma rainha ataque outra.

## Visão Geral do Projeto

O problema das Oito Rainhas é um problema de restrição que pode ser resolvido com diversas abordagens. Neste projeto, exploramos o uso de um Algoritmo Genético (AG) para encontrar uma solução otimizada. O AG é uma técnica de busca inspirada no processo de seleção natural, onde uma população de soluções candidatas (cromossomos) evolui ao longo de várias gerações através de operações de seleção, crossover e mutação.

## Algoritmo Genético Implementado

Nosso Algoritmo Genético segue as seguintes etapas:

1.  **Inicialização:**

    - Geração de uma população inicial de cromossomos, onde cada cromossomo representa um possível posicionamento das rainhas no tabuleiro.
    - Um cromossomo é representado como uma permutação de strings de bits de tamanho 3, onde o valor representa a linha e a posição representa a coluna. Ex: `['110', '100', '001', '011', '101', '111', '010', '000']`

2.  **Avaliação (Fitness):**

    - Cálculo do _fitness_ de cada cromossomo na população.
    - O _fitness_ é inversamente proporcional ao número de conflitos entre as rainhas (quanto menos conflitos, melhor o _fitness_).

3.  **Seleção:**

    - Seleção dos cromossomos pais para a próxima geração, dando preferência aos cromossomos com melhor _fitness_.
    - Foi utilizada a seleção por torneio, onde um subconjunto da população é selecionado aleatoriamente e os dois melhores indivíduos são escolhidos como pais.

4.  **Crossover (Recombinação):**

    - Geração de novos cromossomos filhos a partir dos pais selecionados.
    - Foi utilizado um crossover baseado em um ponto de corte aleatório, combinando genes dos dois pais. Os filhos são criados a partir de um ponto de corte e preenchidos com os genes faltantes do outro pai, mantendo a ordem relativa.

5.  **Mutação:**

    - Introdução de pequenas alterações aleatórias nos cromossomos filhos.
    - Foi implementada a mutação por troca, onde duas posições no cromossomo são selecionadas aleatoriamente e seus valores são trocados.

6.  **Seleção de Sobreviventes:**

    - Seleção dos cromossomos que farão parte da próxima geração, combinando os cromossomos pais e filhos e mantendo os melhores indivíduos.
    - A nova população é formada pelos melhores cromossomos da união da população anterior e dos filhos, garantindo que o tamanho da população se mantenha constante.

7.  **Critério de Parada:**
    - O algoritmo é interrompido quando uma solução ideal é encontrada (fitness = 0, indicando ausência de conflitos), o número máximo de gerações é atingido ou atinge-se convergência total.

## Bibliotecas Utilizadas

- `random`: Para geração de números aleatórios (inicialização da população, seleção, crossover, mutação).
- `numpy`: Para operações numéricas (cálculo de fitness médio e desvio padrão).
- `matplotlib`: Para visualização de dados (gráficos de convergência).
- `rich`: Para uma exibição mais elegante dos dados na tabela.

## Como Executar

1.  **Ambiente:** Este projeto foi desenvolvido utilizando Python 3.
2.  **Instalação das Dependências:**

    ```bash
    pip install numpy matplotlib rich
    ```

3.  **Execução:**

    - O projeto é implementado em um arquivo Jupyter Notebook chamado `Oito_Rainha_Algoritmo_Genetico.ipynb`.
    - Para executar o notebook, você pode usar o Jupyter Notebook, JupyterLab ou o Google Colab.
    - Basta abrir o arquivo `.ipynb` no ambiente escolhido e executar as células em sequência.

## Ajustes e Parâmetros

Os seguintes parâmetros do algoritmo genético podem ser ajustados para otimizar o desempenho:

- `population_size`: Tamanho da população de cromossomos.
- `board_size`: Tamanho do tabuleiro (neste caso, 8).
- `max_generations`: Número máximo de gerações para a execução do algoritmo.
- `mutation_rate`: Probabilidade de mutação de um cromossomo.
- `crossover_rate`: Probabilidade de crossover entre dois pais.
- `full_convergence`: Booleano que indica se deve ser feita uma busca por convergência total.

Esses parâmetros são definidos na criação da instância da classe `Nqueens` no notebook.

## Análise dos Resultados

O notebook inclui seções para análise dos resultados, com visualizações do progresso do _fitness_ ao longo das gerações e estatísticas sobre a convergência do algoritmo. Há duas formas de obter os dados para análise:

- **Análise de 30 Populações:** Executa o algoritmo 30 vezes, permitindo analisar o sucesso e o número de iterações de cada execução.
- **Análise de uma População:** Executa o algoritmo uma única vez, permitindo analisar o progresso do melhor indivíduo, o _fitness_ médio da população e o desvio padrão do _fitness_ a cada iteração.
