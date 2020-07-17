# Notas de Estudos e Leitura

## Curso AI for Medical Prognosis


### O que é proagnóstico?

**Prognóstico** é a área da medicina que especializada em fazer previsões sobre a saúde futura dos paciêntes. Por exemplo, dado o exame de um paciênte qual o risco dele ter um ataque do coração nos próximos 5 anos, ou morrer em 10? O proagnóstico tbm pode ajudar a guiar o tratamento de, se há risco de morte nos próximos 6 meses, como deve ser o tratamento final deste paciênte!

Em resumo, proagnóstico é um termo médico que se refere a previsões de risco de um futuro risco!

Um modelo de proagnóstico recebe como entrada caracteríticas do paciênte, histórico médico, aspéctos físicos e exames e retorna uma pontuação ou probabilidade de ter determinada doença. Além disso cada atributo da entrada pode ter pesos diferentes no momento de criar seu modelo de proagnóstico. PS. a equação de risco é praticamente um polinômio (**Risk Equation**).

Alguns exemplos de modelos proagnóstico são:

- Atrial Fibrillation (CHADS-VASC)

- Ricos de morte em 3 meses de pessoas esperando um transplante de Fígado (MELD)

- Risco de ter um ataque cardiaco nos próximos 10 anos (ASCVD)


### Avaliação dos modelos de Risco

A ideia de avaliar um modelo de risco é uma comparação entre pares, dado os paciêntes A e B onde o paciênte A tem uma morreu nos próximos 10 anos e o paciênte B não. O modelo de risco deve atribuir uma pontuação mais alta para A do que B, independente da escala utilizada. Um par de pacêntes onde a "saída" é diferente é chamado de **permissible pair**!

| Avaliação do Modelo                                	| A morreu? 	| B morreu? 	| risk score A 	| Risk Score B 	| Peso 	|
|----------------------------------------------------	|-----------	|-----------	|--------------	|--------------	|------	|
| Concordant                                         	| Sim       	| Não       	| 0.95         	| 0.92         	| +1   	|
| Not Concordant                                     	| Sim       	| Não       	| 0.75         	| 0.80         	| -    	|
| Risk Ties                                          	| Sim       	| Não       	| 0.6          	| 0.6          	| +0.5 	|
| Outcome Ties (Nunca é usado na avaliação de Risco) 	| Sim       	| Sim       	| ERRO         	| ERRO         	| ERRO 	|

A métrica que avalia a qualidade de um modelo de Risco é o C-index, que é calculada da seguinte maneira.

C-index = (n_concordante + (0.5 * n_risk_ties))/ n_pemissible