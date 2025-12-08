📊 EXERCÍCIO 1 - Portland House Prices

AtributoR²RSSTamanho0.7310193 bilhõesQuartos0.1956578 bilhões
Resposta: O TAMANHO é claramente melhor. O R² (0.73) indica que 73% da variância do preço é explicada pelo tamanho, enquanto quartos explica apenas 19.5%. O RSS confirma isso (menor erro).


📊 EXERCÍCIO 2 - Advertising

AtributoR²RSSTV0.61192,102Radio0.33203,618Newspaper0.05215,134
Resposta: TV é o melhor preditor de vendas (R² = 61%), seguido de Radio (33%) e Newspaper praticamente não tem relação (5%).


📊 EXERCÍCIO 3 - Comparação LR vs KNN

DatasetModeloR² CompletoR² TreinoR² TestePortlandLR0.730.770.59PortlandKNN0.760.690.31AdvertisingLR0.610.570.67AdvertisingKNN0.660.620.64
Respostas:

O desempenho no dataset completo deveria ser melhor ou pior? → Tende a ser "melhor" (otimista) porque avalia nos mesmos dados de treino
Os modelos generalizam? → Não podemos afirmar sem split. O R² no teste é a métrica honesta de generalização
