# Classificação de lançamentos contábeis

## Descrição do Problema
### Problema geral
Classificação de lançamentos contábeis para determinar a forma de tributação a ser aplicada. Neste caso, são analisados os lançamentos na contabilidade do contribuinte, dados protegidos por sigilo fiscal.
### Problema específico
Classificação de lançamentos na contabilidade de órgãos públicos, disponíveis em portais de transparência.
### Objetivo do projeto
Classificar a despesa pública com natureza de despesa 339036 (outros serviços - pessoa física) com base na descrição da nota de empenho como fato gerador, ou não, das contribuições previdenciárias. Caso seja fato gerador, determinar a categoria do segurado (empregado, contribuinte individual, condutor autônomo).
<br><br>

## Fonte de dados
Os dados das notas de empenho estão disponíveis em portais da transparência de diversos órgãos públicos, por exemplo, https://www.governotransparente.com.br/acessoinfo/44529487/empenhoportipo<br>
Utilizamos uma base de dados rotulados a partir desses dados públicos.
### Variável independente (preditora ou “feature”):
Texto com a descrição da nota de empenho.
### Variável dependente (resposta ou “target”):
Forma de tributação:
> - Não é fato gerador
> - É fato gerador – categoria segurado empregado (SE)
> - É fato gerador – categoria contribuinte individual (CI)
> - É fato gerador – condutor autônomo (CA)
<br>

## Abordagem utilizada para solucionar o problema.
Como a classificação é feita com base na descrição da nota de empenho, que é um campo textual, foi necessário utilizar técnicas de extração de características numéricas do texto para treinamento do modelo de classificação.
### Transformações:
#### BAG OF WORDS > TF-IDF > EMBEDDING BERT > EMBEDDING GEMINI
### Classificadores:
- 1 classificador multiclasses: Não, CA, CI, SE
- 2 classificadores sucessivos:
> - fato gerador (binário): Sim, Não (binário)
> - categoria (multiclasses): CA, CI, SE 

