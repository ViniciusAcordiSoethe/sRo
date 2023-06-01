# Movimentação basica 

Para movimentar precisamos saber o nome dos componentes que vamos usar similiar ao Spike 

é possivel descobrir o nome dos componentes pelo simulador sBotics na aba robô

vou deixar uma lista com os Robos e seus componentes

## Robôs

##### Trekker

    Motor Esquerdo: "l"
    Motor Direito: "r"

##### Obsidian

    Motor Esquerdo: "backLeftMotor"
    Motor Direito: "backRightMotor"

##### Bruna

    Motor Esquerdo: "leftMotor"
    Motor Direito: "rightMotor"
    Motor Esquerdo Frontal: "frontLeftMotor"
    Motor Direito Frontal: "frontLeftMotor"

##### Boryszin

    Motor 1 : "E"
    Motor 2 : "D"
    Motor 3 : "E2"
    Motor 4 : "a"
    Motor 5 : "D2"
    Motor 6 : "T"
    Motor 7 : "G"
    Motor 8 : "V1"
    Motor 9 : "G2"

## Andar para frente

Para andar para frente temos que primeiro destravar o motor  e depois definir a velocidade que ele deve andar 
Para isso vamos usar 2 funções do rEduc a Travarmotor() e a Motor()

### TravarMotor

Para usar a TravaMotor() precisamos passar o nome do motor e se ele deve ser travado ou destravado

    TravarMotor( var1, var2)

aonde 

    Prefix: var1
    Nome: Nome do Componente
    Tipo: Texto
    Descrição: Nome do Componente do Robô

    Prefix: var2
    Nome: Travar Motor
    Tipo: Booleano
    Descrição: Booleano que define o estado de trava do motor informado.



### Motor
então usando a função Motor() passamos o nome do motor e a velocidade que ele deve andar

    Motor( var1 , var2 )

aonde 

    Prefix: var1
    Nome: Nome do Componente
    Tipo: Texto
    Descrição: Nome do Componente do Robô

    Prefix: var2
    Nome: Força e Velocidade
    Tipo: Número
    Descrição: Força e Velocidade a ser aplicada no motor informado.


### Exemplo

```rEduc
inicio
TravarMotor("Nome do Motor",falso)
TravarMotor("Nome do Motor",falso)
Motor("Nome do Motor", 100)
Motor("Nome do Motor", 100)
fim
```
