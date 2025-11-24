# Análise de Sentimentos IMDB com HMM (Implementação do Zero)

Este repositório contém a implementação de um classificador de sentimentos (Positivo vs. Negativo) utilizando **Modelos Ocultos de Markov (Hidden Markov Models - HMM)** aplicados ao dataset de críticas de filmes do IMDB.

> **Destaque:** O foco deste projeto é didático. Todos os algoritmos do HMM (**Forward, Backward e Baum-Welch**) foram implementados manualmente em Python usando apenas `numpy`, sem a utilização de bibliotecas de "caixa preta" (como `hmmlearn` ou camadas prontas de Deep Learning) para o treinamento do modelo.

## 🧠 Arquitetura do Projeto

O projeto utiliza uma abordagem de **Classificação Bayesiana Generativa**, baseada na arquitetura de Máxima Verossimilhança (Maximum Likelihood):

1.  **Dois Modelos Especialistas:**
    * **$\lambda_{pos}$**: Um HMM treinado exclusivamente com reviews positivas.
    * **$\lambda_{neg}$**: Um HMM treinado exclusivamente com reviews negativas.
2.  **Decisão:** Para classificar uma nova frase, calculamos o *Log-Likelihood* (score) da frase em ambos os modelos. Aquele que resultar no maior score define a classe.

### Algoritmos Implementados
* **Forward Algorithm:** Para cálculo da verossimilhança da observação.
* **Backward Algorithm:** Auxiliar para o passo de treinamento.
* **Baum-Welch (EM):** Algoritmo Expectation-Maximization para ajuste não-supervisionado das matrizes de Transição ($A$), Emissão ($B$) e Inicialização ($\pi$).
* **Scaling:** Implementação de fatores de escala para evitar *underflow* numérico em sequências longas.

## 🛠️ Dependências

O núcleo do HMM utiliza apenas álgebra linear básica. O TensorFlow/Keras é utilizado **apenas** para o carregamento e tokenização do dataset IMDB.

* Python 3.x
* `numpy`
* `tensorflow` (apenas para `keras.datasets.imdb`)

## 🚀 Como Rodar

### 1. Clonar o repositório
```bash
git clone [https://github.com/seu-usuario/nome-do-repo.git](https://github.com/seu-usuario/nome-do-repo.git)
cd nome-do-repo
````

### 2\. Instalar requisitos

```bash
pip install numpy tensorflow
```

### 3\. Executar o Notebook

Abra o arquivo `.ipynb` (por exemplo, `HMM_trabalho.ipynb`) no Jupyter Notebook, VS Code ou Google Colab.

O notebook está estruturado da seguinte forma:

1.  **Carregamento dos dados:** Download do IMDB e padronização das sequências.
2.  **Definição da Classe `HMMManual`:** Onde está a lógica matemática.
3.  **Treinamento:** Loop de iterações do Baum-Welch para os dois modelos.
4.  **Avaliação:** Teste de acurácia no conjunto de teste.
5.  **Teste Manual:** Célula interativa para digitar frases em inglês e ver a classificação.

## 📊 Resultados

Com a configuração atual (Vocabulário de 1.000 palavras, 300 amostras de treino e 30 iterações), o modelo manual atingiu uma acurácia de **\~84%** no conjunto de teste, demonstrando convergência e aprendizado efetivo dos padrões de sentimento sem uso de bibliotecas prontas.

## ✒️ Autor

  * **[João Victor Andrade, Eduardo Marinho, Jefferson, Vlad]** - Desenvolvimento e Implementação Algorítmica.

-----

*Este projeto foi desenvolvido como parte da disciplina de Inteligência Artificial.*

```
```
