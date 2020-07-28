1. Como dar pesos na entrada do seu modelo de proagnóstico? (Como por exemplo o chads vasc score, para calcular o score de um paciênte ter derrame)

2. Quais são os valores padroẽs do CHADS VASC?

3. Definir um baseline para o C-index? Não usamos outras métricas de avaliação do modelo?
R: Geralemnte é usado para bater o valor ouro, benchmark usado até o momento, encontrado em papers e afins

4. Qual é a tradução correta para censuring nos dados de sobrevivência?

5. Não ficou claro o conceito de right censoring e o pq sempre adotamos que o evento ocorrerá quando deixamos de monitorar, mão não chegamos ao fim da fase de monitoramento?
R: Na realidade nós fazemos duas suposições, que acontece determinado evento imediatamente e que não ocorre determinado evento imediatamente!

6. Qual é a implicação de usar o C-index? Pq não usar realmente uma medida como acurácia?

7. O que p MCAR, MAR, MNAR?

8. Por o LOG, remove o desvio da distribuição?
