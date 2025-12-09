# Respostas dos Exercícios de Regressão Linear

## Exercício 1
**Para cada um dos conjuntos de treinamento, utilize a função fit múltiplas vezes considerando apenas um atributo preditor.**

### 1. O modelo aprendido muda a cada vez que a função fit é utilizada?
* **LinearRegression (OLS):** **Não.** O método dos Mínimos Quadrados Ordinários é uma solução analítica fechada (determinística). Dado o mesmo conjunto de dados, ele sempre calculará exatamente os mesmos coeficientes e intercepto.
* **SGDRegressor:** **Sim.** Como este algoritmo utiliza Descida de Gradiente Estocástica, ele inicia com pesos aleatórios e atualiza os pesos iterativamente. Se o parâmetro `random_state` não for fixado, o caminho de otimização varia ligeiramente a cada execução, resultando em modelos finais levemente diferentes.

### 2. Os modelos finais aprendidos são os mesmos da outra implementação de regressão linear?
**R:** Eles são **muito próximos**, mas não idênticos.
* A `LinearRegression` encontra o valor ótimo exato global.
* O `SGDRegressor` encontra uma aproximação desse valor. Com número suficiente de iterações e dados normalizados, o SGD converge para valores extremamente próximos aos da regressão linear clássica.

---

## Exercício 2
**Aprenda modelos utilizando todos os atributos de entrada.**

### 1. Baseado no RSS e no R^2, é possível obter um modelo melhor utilizando todos os dados?
**R: Sim.**
* Ao utilizar as três variáveis (TV, Radio, Newspaper), o $R^2$ sobe para aproximadamente **0.897** (explicando quase 90% da variância das vendas).
* Comparativamente, modelos com apenas uma variável (ex: apenas TV) costumam ter um $R^2$ bem menor (em torno de 0.61). Adicionar informações relevantes diminui o RSS (erro residual) e melhora o ajuste.

### 2. Existem atributos que poderiam ser desconsiderados sem que fosse afetada a precisão?
**R: Sim, o atributo "Newspaper".**
* Ao analisar os coeficientes ou remover a variável, observa-se que o $R^2$ praticamente não se altera (cai de ~0.8972 para ~0.8971). Isso sugere que o investimento em jornal não traz poder preditivo adicional significativo quando já sabemos o investimento em TV e Rádio.

### 3. Qual implementação treina mais rápido? A com método dos mínimos quadrados ou a com descida de gradiente?
**R:** Para bases de dados pequenas como esta (*Advertising* tem 200 linhas), o **Método dos Mínimos Quadrados (`LinearRegression`)** é mais rápido.
* A descida de gradiente (`SGDRegressor`) é vantajosa computacionalmente apenas quando o número de dados é massivo (milhões de exemplos), onde a inversão de matrizes do método clássico se torna inviável.

---

## Exercício 3
**Realizar a análise da qualidade dos preditores utilizados no modelo construído.**

### 1. Construir o plot de resíduos. Será que os resíduos estão aleatoriamente distribuídos ao redor de 0?
![Plot de Resíduos](plot_residuos.png)
*(Nota: Certifique-se de que a imagem gerada pelo código esteja na mesma pasta)*

**R:** Os resíduos estão distribuídos em torno de 0, o que é bom, mas **não são perfeitamente aleatórios**. No dataset *Advertising*, é comum observar uma forma leve de "U" (curvatura) no gráfico de resíduos x preditos. Isso indica que, embora o modelo linear seja bom, ainda existe alguma não-linearidade nos dados (interação entre TV e Rádio) que o modelo linear simples não capturou perfeitamente.

### 2. Calcular os valores p para os preditores. Comparar desempenho removendo variáveis.
**R:**
* **TV e Radio:** Possuem valores-p extremamente baixos (p < 0.000), indicando alta significância estatística.
* **Newspaper:** Possui um valor-p alto (geralmente acima de 0.05 ou até 0.8), indicando que não é estatisticamente significativo para o modelo na presença das outras variáveis.
* **Comparação:** O modelo treinado apenas com **TV e Radio** (excluindo Newspaper) mantém praticamente o mesmo desempenho ($R^2 \approx 0.897$), confirmando que *Newspaper* é redundante e pode ser removido para simplificar o modelo.

---

## Exercício 4 (Extra)
**Realizar o teste para descobrir multicolinearidade entre variáveis preditivas (VIF).**

### 1. Existe alguma evidência de multicolinearidade entre as variáveis preditivas?
**R:** **Não há evidência de multicolinearidade severa.**
* Os valores de VIF (Variance Inflation Factor) para TV, Radio e Newspaper costumam ficar baixos (geralmente entre **1.0 e 1.5**).
* Como regra prática, preocupamo-nos com multicolinearidade quando o VIF excede 5 ou 10. Valores próximos de 1 indicam que as variáveis são independentes entre si, o que é ideal para a regressão linear.
