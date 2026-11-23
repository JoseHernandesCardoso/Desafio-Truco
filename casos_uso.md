# Casos de Uso do Jogo de Truco
## Alunos:
- José Henrique Hernandes Cardoso (RA143470)
- Henrique Possetti Calvo (RA145097)

## UC-01: Inicio de Rodada
- Objetivo: Distribuir as cartas para os jogadores e iniciar a rodada
- Ator Principal: Sistema de Gerenciamento de Partida
- Atores Secundários: Jogador, BOTs
- Pré-Condições: Não estar em uma rodada
- Pós-Condições: O jogador e os BOTs recebem 3 cartas
- Gatilho: inicio de uma nova rodada
### Fluxo Principal
1. Rodada Inicia
2. O gerenciador de partida distribui 3 cartas aleatórias para cada jogador na mesa
3. Todos têm 3 cartas na mão
4. O gerenciador de partida mostra a vira da rodada.
5. Nova rodada inicia

### Fluxos Alternativos
1. Se algum time possui 12 ou mais pontos, o jogo encerra automaticamente

### Regras de Negócio
1. Um time vence com 12 pontos



## UC-02: Jogar Carta
- Objetivo: O jogador lança uma carta
- Ator Principal: Jogador/BOT
- Atores Secundários: pilha de descarte
- Pré-Condições: é a vez do jogador/BOT jogar
- Pós-Condições: a carta escolhida é lançada na pilha de descarte
- Gatilho: selecionar uma carta
### Fluxo Principal
1. O jogador/BOT escolhe uma carta
2. A carta sai da mão do jogador/BOT e é adicionada na pilha de descarte

### Fluxos Alternativos
1. A partir do segundo turno, o jogador/BOT pode abaixar uma carta virada para baixo e ela não possui valor nenhum

2. Antes de jogar, o jogador/BOT pode pedir Truco, aumenteando o valor da rodada para 3 pontos. O próximo jogador tem direito de resposta

### Regras de Negócio
1. Só uma carta pode ser jogada por um jogador/BOT por turno
2. Um BOT escolhe sua carta aleatóriamente



## UC-03: Responder Truco
- Objetivo: Permitir um jogador reagir a um pedido de Truco
- Ator Principal: Jogador/BOT
- Atores Secundários: Nenhum
- Pré-Condições: O jogador anterior pediu Truco
- Pós-Condições: O valor da rodada aumenta
- Gatilho: Inicio do turno do jogador/BOT após o jogador anterior pedir Truco
### Fluxo Principal
1. O Jogador aceita o Truco
2. O valor da rodada aumenta para 3 e volta a vez para o jogador anterior que pediu o Truco

### Fluxos Alternativos
1. Se alguém da dupla adversária já pediu truco ou aumento na rodada, o jogador pode pedir para aumentar o Truco em mais 3 pontos, com limite de 12 pontos

2. O jogador pode correr e perder a rodada, dando os pontos da rodada sem o aumento para os adversários.

### Regras de Negócio
1. Limite de valor de uma rodada pedindo truco é 12


## UC-04: Fim de turno
- Objetivo: Encerrar um turno
- Ator Principal: Gerenciador de partida
- Atores Secundários: Jogador/BOT
- Pré-Condições: todos jogaram 1 carta
- Pós-Condições: a dupla vencedora do turno recebe um ponto de turno um novo turno ou rodada se inicia
- Gatilho: último jogador do turno jogou sua carta
### Fluxo Principal
1. Cada um dos jogadores faz sua jogada do turno
2. A dupla cujo jogador jogou a carta mais forte vence o turno
2. Um novo turno se inicia

### Fluxos Alternativos
1. Se um dupla atingir 2 pontos de turno, os pontos de turno são zerados, a dupla recebe os pontos da rodada e uma nova rodada se inicia

### Regras de Negócio
1. Uma rodada possui no máximo 3 turnos
2. Vence um turno a dupla que jogar a carta mais forte
3. A ordem de força das cartas segue o modelo de Truco Paulista


## UC-05: Fim de Rodada
- Objetivo: Encerrar uma rodada
- Ator Principal: Gerenciador de partida
- Atores Secundários: Jogadores
- Pré-Condições: nenhuma
- Pós-Condições: A dupla vencedora da rodada recebe os pontos
- Gatilho: Alguma dupla ganha 2 turnos
### Fluxo Principal
1. Uma dupla vence 2 turnos
2. Os pontos da rodada são dados a dupla

### Fluxos Alternativos
1. Se alguma dupla pontuar 12 pontos ou mais no total, ela vence o jogo

### Regras de Negócio
1. Vence a dupla que fizer 12 pontos ou mais primeiro.



## UC-06: Determinar Manilhas
- Objetivo: Definir quais cartas são as manilhas da rodada
- Ator Principal: Gerenciador de partida
- Atores Secundários: Nenhum
- Pré-Condições: A vira foi definida
- Pós-Condições: A manilha da rodada foi identificada
- Gatilho: Vira revelada
### Fluxo Principal
1. O gerenciador identifica a carta seguinte à vira na sequência de valores
2. Todas as cartas desse valor são definidas como manilhas
3. O gerenciador registra a ordem de força das manilhas

### Regras de Negócio
1. As manilhas são determinadas pela vira
2. Entre manilhas, os naipes seguem a ordem definida pelo Truco Paulista



## UC-07: Controlar Vez de Jogada
- Objetivo: Definir qual jogador deve jogar uma carta
- Ator Principal: Gerenciador de partida
- Atores Secundários: Jogador/BOT
- Pré-Condições: A rodada está em andamento
- Pós-Condições: O próximo jogador apto a jogar é definido
- Gatilho: Início da rodada ou fim de uma jogada
### Fluxo Principal
1. O gerenciador identifica o jogador que deve jogar
2. O jogador/BOT realiza sua jogada
3. O gerenciador passa a vez para o próximo jogador

### Fluxos Alternativos
1. Se o jogador tentar jogar fora de sua vez, a jogada é recusada

### Regras de Negócio
1. Os jogadores jogam em uma ordem fixa
2. Cada jogador joga no máximo uma carta por turno



## UC-08: Resolver Empate de Turno
- Objetivo: Definir a dupla vencedora quando houver empate
- Ator Principal: Gerenciador de partida
- Atores Secundários: Nenhum
- Pré-Condições: Todos os jogadores do turno jogaram suas cartas
- Pós-Condições: O vencedor do turno ou da rodada é definido
- Gatilho: Duas ou mais cartas possuem a mesma força
### Fluxo Principal
1. O gerenciador identifica o empate
2. O gerenciador verifica o resultado dos turnos anteriores
3. O gerenciador define a dupla vencedora conforme as regras do Truco Paulista

### Regras de Negócio
1. O empate no primeiro turno deve ser resolvido pelo resultado do turno seguinte
2. Se uma dupla já venceu um turno, ela pode ser declarada vencedora em caso de novo empate, conforme a regra aplicável
3. A regra para empate nos três turnos deve ser definida pelo jogo



## UC-09: Solicitar Aumento da Rodada
- Objetivo: Aumentar o valor da rodada
- Ator Principal: Jogador/BOT
- Atores Secundários: Dupla adversária
- Pré-Condições: A rodada está em andamento e ainda pode ser aumentada
- Pós-Condições: Um pedido de aumento aguarda resposta
- Gatilho: Jogador/BOT solicita Truco, Seis, Nove ou Doze
### Fluxo Principal
1. O jogador/BOT solicita um aumento
2. O gerenciador informa o novo valor da rodada à dupla adversária
3. A dupla adversária responde ao pedido

### Fluxos Alternativos
1. Se o valor já for 12, o pedido de aumento é recusado
2. Se a dupla adversária recusar, ela perde a rodada pelo valor atual

### Regras de Negócio
1. Os valores possíveis são 1, 3, 6, 9 e 12 pontos
2. Apenas a dupla adversária pode responder ao pedido



## UC-10: Atualizar Pontuação
- Objetivo: Registrar os pontos ganhos por uma dupla
- Ator Principal: Gerenciador de partida
- Atores Secundários: Nenhum
- Pré-Condições: A rodada foi encerrada
- Pós-Condições: A pontuação das duplas foi atualizada
- Gatilho: Definição da dupla vencedora da rodada
### Fluxo Principal
1. O gerenciador identifica a dupla vencedora
2. O valor da rodada é somado à pontuação da dupla
3. O gerenciador verifica se alguma dupla alcançou 12 pontos

### Fluxos Alternativos
1. Se alguma dupla alcançar 12 pontos, o jogo é encerrado
2. Caso contrário, uma nova rodada é iniciada

### Regras de Negócio
1. A dupla vencedora recebe o valor atual da rodada
2. A partida termina quando uma dupla alcança 12 pontos
