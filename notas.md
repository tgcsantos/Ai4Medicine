# Notas de Estudos e Leitura

## Curso AI for Medical Prognosis


### O que é proagnóstico?

**Prognóstico** é a área da medicina que especializada em fazer previsões sobre a saúde futura dos paciêntes. Por exemplo, dado o exame de um paciênte qual o risco dele ter um ataque do coração nos próximos 5 anos, ou morrer em 10? O proagnóstico tbm pode ajudar a guiar o tratamento de, se há risco de morte nos próximos 6 meses, como deve ser o tratamento final deste paciênte!

Em resumo, proagnóstico é um termo médico que se refere a previsões de risco de um futuro risco!

Um modelo de proagnóstico recebe como entrada caracteríticas do paciênte, histórico médico, aspéctos físicos e exames e retorna uma pontuação ou probabilidade de ter determinada doença. Além disso cada atributo da entrada pode ter pesos diferentes no momento de criar seu modelo de proagnóstico. PS. a equação de risco é praticamente um polinômio.

Alguns exemplos de modelos proagnóstico são:

- Atrial Fibrillation (CHADS-VASC)

- Ricos de morte em 3 meses de pessoas esperando um transplante de Fígado (MELD)

- Risco de ter um ataque cardiaco nos próximos 10 anos (ASCVD)