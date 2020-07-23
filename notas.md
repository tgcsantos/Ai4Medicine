# Notas de Estudos e Leitura

## Curso AI for Medical Prognosis

### Proagnóstico (Risk Model)

#### O que é proagnóstico?

**Prognóstico** é a área da medicina que especializada em fazer previsões sobre a saúde futura dos paciêntes. Por exemplo, dado o exame de um paciênte qual o risco dele ter um ataque do coração nos próximos 5 anos, ou morrer em 10? O proagnóstico tbm pode ajudar a guiar o tratamento de, se há risco de morte nos próximos 6 meses, como deve ser o tratamento final deste paciênte!

Em resumo, proagnóstico é um termo médico que se refere a previsões de risco de um futuro risco!

Um modelo de proagnóstico recebe como entrada caracteríticas do paciênte, histórico médico, aspéctos físicos e exames e retorna uma pontuação ou probabilidade de ter determinada doença. Além disso cada atributo da entrada pode ter pesos diferentes no momento de criar seu modelo de proagnóstico. PS. a equação de risco é praticamente um polinômio (**Risk Equation**).

Alguns exemplos de modelos proagnóstico são:

- Atrial Fibrillation (CHADS-VASC)

- Ricos de morte em 3 meses de pessoas esperando um transplante de Fígado (MELD)

- Risco de ter um ataque cardiaco nos próximos 10 anos (ASCVD)


#### Avaliação dos modelos de Risco

A ideia de avaliar um modelo de risco é uma comparação entre pares, dado os paciêntes A e B onde o paciênte A tem uma morreu nos próximos 10 anos e o paciênte B não. O modelo de risco deve atribuir uma pontuação mais alta para A do que B, independente da escala utilizada. Um par de pacêntes onde a "saída" é diferente é chamado de **permissible pair**!

| Avaliação do Modelo                                	| A morreu? 	| B morreu? 	| risk score A 	| Risk Score B 	| Peso 	|
|----------------------------------------------------	|-----------	|-----------	|--------------	|--------------	|------	|
| Concordant                                         	| Sim       	| Não       	| 0.95         	| 0.92         	| +1   	|
| Not Concordant                                     	| Sim       	| Não       	| 0.75         	| 0.80         	| -    	|
| Risk Ties                                          	| Sim       	| Não       	| 0.6          	| 0.6          	| +0.5 	|
| Outcome Ties (Nunca é usado na avaliação de Risco) 	| Sim       	| Sim       	| ERRO         	| ERRO         	| ERRO 	|

A métrica que avalia a qualidade de um modelo de Risco é o C-index, que é calculada da seguinte maneira.

C-index = (n_concordante + (0.5 * n_risk_ties))/ n_pemissible



Ao lidar com dados do mundo real temos um problema comum que é chamado de missing value, essa falta de dados pode ter diversos motivos e suas soluções tbm são variadas. Podendo ser desde a eliminação dos dados que não tem informação, repetição da última inferência, até a criação de uma regressão para determinar os valores faltantes.

### Survival models

#### Estimativas de um modelo de sobrevivência

Diferente de um modelo de proagnóstico onde queremos saber qual é a chance de um paciênte morrer nos próximos 5 anos, queremos inverter a pergunta! Qual é a chance do paciênte sobreviver nos próximos 5 anos?

Modelada pela equação:

>                      **S(t) = Pr(T>t)**

As propriedades de um modelo de sobrevivência é sempre iniciar com propabilidade máxima e ao quando t:->infinito a probabilidade tende a Zero. 

Outro fator que muda do modelos de sobrevicência para o modelo de proagnóstico, é aa forma de coletar os dados! Em proagnóstico temos uma escala binária para o diagnóstico de uma doença (yes/no). Mas para um modelo de sobrevivência temos uma escala de "tempo" onde monitoramos o paciênte e verificamos se há ou não o acontecimento de determinado evento. Entretando não é tão simples, pois temos o que chamamos de censuring (censura), é quando deixamos de monitorar o paciênte por algum motivo e não sabemos o que ocorre com ele nesse tempo posterior! Ou seja monitamos por 3 meses e por algum motivo qualquer deixamos de monitorá-lo!

Quando isso acontece podemos considerar duas situações, uma em que ocorre determinado evento logo após a perda de contato e outra na qual nunca ocorre. Assim teremos dois extremos e valores relativamente diferentes entre as partes e para resolver essa diferença aplicamos conceitos de cadêias de markov e chagamos em algo chamado de **Kaplan Meier Estimate** que gera um melhor resultado entre os extremos. 
