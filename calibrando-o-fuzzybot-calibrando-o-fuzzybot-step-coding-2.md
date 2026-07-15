### @diffs true
# Calibrando o FuzzyBot

## Passo 1

Neste tutorial, vamos criar um código para calibrar os sensores infravermelhos 
do FuzzyBot. Para isso, vamos utilizar os LEDs laterais e a matriz de LEDs do 
micro:bit para responderem ao valor de cada um dos três sensores infravermelhos 
localizados na parte de baixo do chassi do FuzzyBot. 

**Obs.:** Caso necessário, utilize a **lâmpada** próxima a seleção de passos do 
tutorial para vizualizar o código durante a construção.

```blocks
```

## Passo 2

Para inicializar o código, adicione o comando ``||Basic:mostrar ícone [♡]||`` dentro 
do laço ``||Basic:no iniciar||`` e em seguida adicione o comando 
``||Basic:pausa (ms) (100)||`` logo abaixo. Mantenha o ícone de coração e 
altere o valor do bloco ``||Basic:pausa (ms) (100)||`` de **100ms** para 
**1000ms**.

 **Obs.:** Se o laço ``||basic:no iniciar||`` não estiver em seu código de forma
 automatica, você pode encontrá-lo na aba ``||Basic:Básico||``.

```blocks
basic.showIcon(IconNames.Heart)
basic.pause(1000)
```

## Passo 3

Para limpar a tela logo em seguida, vá até a aba ``||basic:no iniciar||`` 
adicione o comando ``||Basic:limpar tela||`` dentro do laço 
``||Basic:no iniciar||`` abaixo dos blocos colocados no passo anterior.

```blocks
basic.showIcon(IconNames.Heart)
basic.pause(1000)
basic.clearScreen()
```

## Passo 4

Agora precisamos armazenar o valor de cada sensor infravermelho em uma 
**variável** que será manipulada durante o código. Para isso, vá até a aba 
``||variables:Variáveis||`` e clique no botão **"Fazer uma variável..."**. 
Dê o nome da primeira variável de **sensor_esq**, e em seguida o bloco 
``||variables:definir [sensor_esq] para (0)||`` irá aparecer. Arraste esse bloco
para dentro do laço ``||basic:sempre|`` .

 **Obs.:** Se o laço ``||basic:sempre||`` não estiver em seu código de forma
 automatica, você pode encontrá-lo na aba ``||Basic:Básico||``.

 ```blocks
let sensor_esq = 0
basic.showIcon(IconNames.Heart)
basic.pause(1000)
basic.clearScreen()
basic.forever(function () {
    sensor_esq = 0
})
```

## Passo 5

Vamos criar três variáveis, uma para cada sensor infravermelho. Já criamos a 
variável referente ao sensor esquerdo (**sensor_esq**) e agora vamos criar uma 
referente ao sensor direito. Para isso, vá até a aba ``||variables:Variáveis||`` 
e clique no botão **"Fazer uma variável..."**. Dê o nome da segunda variável de 
**sensor_dir** e, em seguida, encaixe o bloco 
``||variables:definir [sensor_dir] para (0)||`` logo abaixo do bloco colocado no 
passo anterior.

 **Obs.:** Você pode clicar no botão de nome da variável dentro do bloco 
 ``||variables:definir [sensor_dir] para (0)||`` para altera-la caso necessário.

 ```blocks
let sensor_dir = 0
let sensor_esq = 0
basic.showIcon(IconNames.Heart)
basic.pause(1000)
basic.clearScreen()
basic.forever(function () {
    sensor_esq = 0
    sensor_dir = 0
})
```

## Passo 6

Por fim, vamos criar uma variável referente ao sensor do meio. Para isso, vá até a aba 
``||variables:Variáveis||`` e clique no botão **"Fazer uma variável..."**. 
Dê o nome da terceira variável de **sensor_meio** e, em seguida, encaixe o bloco 
``||variables:definir [sensor_meio] para (0)||`` logo abaixo do bloco colocado no 
passo anterior.

 ```blocks
let sensor_dir = 0
let sensor_esq = 0
let sensor_meio = 0
basic.showIcon(IconNames.Heart)
basic.pause(1000)
basic.clearScreen()
basic.forever(function () {
    sensor_esq = 0
    sensor_dir = 0
    sensor_meio = 0
})
```

## Passo 7

Para atribuir valor a cada uma das variáveis, vá até a aba 
``||fuzzyBot:FuzzyBoT||`` e arraste um bloco 
``||fuzzyBot:ler sensor de linha [esquerdo]||`` para dentro do campo **(0)** do 
bloco ``||variables:definir [sensor_esq] para (0)||``. Repita esse mesmo 
processo para os blocos referentes as variáveis **sensor_dir** e **sensor_meio**, 
porém alterando o valor dos blocos para 
``||fuzzyBot:ler sensor de linha [direito]||`` e 
``||fuzzyBot:ler sensor de linha [meio]||``.

 ```blocks
let sensor_meio = 0
let sensor_dir = 0
let sensor_esq = 0
basic.showIcon(IconNames.Heart)
basic.pause(1000)
basic.clearScreen()
basic.forever(function () {
    sensor_esq = fuzzyBot.readPatrol(fuzzyBot.Patrol.PatrolLeft)
    sensor_dir = fuzzyBot.readPatrol(fuzzyBot.Patrol.PatrolRight)
    sensor_meio = fuzzyBot.readPatrol(fuzzyBot.Patrol.PatrolMiddle)
})
```

## Passo 8

Agora vamos criar condições para definir o que acontece caso cada um dos sensores 
seja acionado, ou seja, caso eles identifiquem uma superfície clara e lisa. Vá 
até a aba ``||logic:Lógica||`` e adicione o bloco condicional
``||logic:se <verdadeiro> então||`` dentro do laço ``||basic:sempre||`` 
e abaixo dos blocos colocados no passo anterior. Em seguida, coloque mais 
dois blocos ``||logic:se <verdadeiro> então||`` logo abaixo dele.

 ```blocks
let sensor_meio = 0
let sensor_dir = 0
let sensor_esq = 0
basic.showIcon(IconNames.Heart)
basic.pause(1000)
basic.clearScreen()
basic.forever(function () {
    sensor_esq = fuzzyBot.readPatrol(fuzzyBot.Patrol.PatrolLeft)
    sensor_dir = fuzzyBot.readPatrol(fuzzyBot.Patrol.PatrolRight)
    sensor_meio = fuzzyBot.readPatrol(fuzzyBot.Patrol.PatrolMiddle)
    if (true) {
    	
    }
    if (true) {
    	
    }
    if (true) {
    	
    }
})
```

## Passo 9

Para  garantirmos que o comando vai funcionar quando os sensores forem acionados, 
precisamos fazer uma comparação como valor desse sensor. Para isso, vá até a aba 
``||logic:Lógica||`` e adicione um bloco de comparação ``||logic:(0) = (0)||`` 
dentro do campo **<verdadeiro>** de cada um dos blocos 
``||logic:se <verdadeiro> então||``.

 ```blocks
let sensor_meio = 0
let sensor_dir = 0
let sensor_esq = 0
basic.showIcon(IconNames.Heart)
basic.pause(1000)
basic.clearScreen()
basic.forever(function () {
    sensor_esq = fuzzyBot.readPatrol(fuzzyBot.Patrol.PatrolLeft)
    sensor_dir = fuzzyBot.readPatrol(fuzzyBot.Patrol.PatrolRight)
    sensor_meio = fuzzyBot.readPatrol(fuzzyBot.Patrol.PatrolMiddle)
    if (0 == 0) {
    	
    }
    if (0 == 0) {
    	
    }
    if (0 == 0) {
    	
    }
})
```

## Passo 10

Cada condição será referente a um dos sensores, e para definir isso vá até a aba 
``||variables:Variáveis||`` e arraste o bloco ``||variables:sensor_esq||`` para 
dentro do primeiro **(0)** da condição ``||logic:se <(0) = (0)> então||``. 
Repita esse processo para as outras condições, utilizando os blocos 
``||variables:sensor_dir||`` e ``||variables:sensor_meio||``. 

 ```blocks
let sensor_meio = 0
let sensor_dir = 0
let sensor_esq = 0
basic.showIcon(IconNames.Heart)
basic.pause(1000)
basic.clearScreen()
basic.forever(function () {
    sensor_esq = fuzzyBot.readPatrol(fuzzyBot.Patrol.PatrolLeft)
    sensor_dir = fuzzyBot.readPatrol(fuzzyBot.Patrol.PatrolRight)
    sensor_meio = fuzzyBot.readPatrol(fuzzyBot.Patrol.PatrolMiddle)
    if (sensor_esq == 0) {
    	
    }
    if (sensor_dir == 0) {
    	
    }
    if (sensor_meio == 0) {
    	
    }
})
 ```

## Passo 11

 Depois de realizar esse processo, altere o segundo **(0)** de todos os blocos 
 ``||logic:se <(0) = (0)> então||`` para **(1)**.

 ```blocks
let sensor_meio = 0
let sensor_dir = 0
let sensor_esq = 0
basic.showIcon(IconNames.Heart)
basic.pause(1000)
basic.clearScreen()
basic.forever(function () {
    sensor_esq = fuzzyBot.readPatrol(fuzzyBot.Patrol.PatrolLeft)
    sensor_dir = fuzzyBot.readPatrol(fuzzyBot.Patrol.PatrolRight)
    sensor_meio = fuzzyBot.readPatrol(fuzzyBot.Patrol.PatrolMiddle)
    if (sensor_esq == 1) {
    	
    }
    if (sensor_dir == 1) {
    	
    }
    if (sensor_meio == 1) {
    	
    }
})
 ```

## Passo 12

 Caso o **sensor esquerdo** seja ativado por uma superfície clara e lisa, vamos 
 fazer com que o **LED esquerdo** do FuzzyBoT ascenda. Caso contrário (se a 
 superfície for escura) vamos fazer com que o LED esquerdo apague. Para isso, vá até a 
 aba ``||fuzzyBot:FuzzyBoT||`` e arraste um bloco 
 ``||fuzzyBot:LED [esquerdo] definir para [Ligado]||`` para dentro do bloco 
 ``||logic:se <(sensor_esq) = (1)> então||``. Em seguida, clique no ícone de **+** 
 na parte inferior do bloco para adicionar um bloco ``||logic:senão||`` a essa 
 condição.

 ```blocks
let sensor_meio = 0
let sensor_dir = 0
let sensor_esq = 0
basic.showIcon(IconNames.Heart)
basic.pause(1000)
basic.clearScreen()
basic.forever(function () {
    sensor_esq = fuzzyBot.readPatrol(fuzzyBot.Patrol.PatrolLeft)
    sensor_dir = fuzzyBot.readPatrol(fuzzyBot.Patrol.PatrolRight)
    sensor_meio = fuzzyBot.readPatrol(fuzzyBot.Patrol.PatrolMiddle)
    if (sensor_esq == 1) {
        fuzzyBot.writeLED(fuzzyBot.LED.LEDLeft, fuzzyBot.LEDswitch.turnOn)
    } else {
    	
    }
    if (sensor_dir == 1) {
    	
    }
    if (sensor_meio == 1) {
    	
    }
})
 ```

## Passo 13

Vá até a aba ``||fuzzyBot:FuzzyBoT||`` e arraste um bloco 
``||fuzzyBot:LED [esquerdo] definir para [Ligado]||`` para dentro do bloco 
``||logic:senão||`` criado no passo anterior. Clique em cima do botão 
``||fuzzyBot:[Ligado]||`` do bloco e altere-o para ``||fuzzyBot:[Desligado]||``. 

 ```blocks
let sensor_meio = 0
let sensor_dir = 0
let sensor_esq = 0
basic.showIcon(IconNames.Heart)
basic.pause(1000)
basic.clearScreen()
basic.forever(function () {
    sensor_esq = fuzzyBot.readPatrol(fuzzyBot.Patrol.PatrolLeft)
    sensor_dir = fuzzyBot.readPatrol(fuzzyBot.Patrol.PatrolRight)
    sensor_meio = fuzzyBot.readPatrol(fuzzyBot.Patrol.PatrolMiddle)
    if (sensor_esq == 1) {
        fuzzyBot.writeLED(fuzzyBot.LED.LEDLeft, fuzzyBot.LEDswitch.turnOn)
    } else {
        fuzzyBot.writeLED(fuzzyBot.LED.LEDLeft, fuzzyBot.LEDswitch.turnOff)
    }
    if (sensor_dir == 1) {
    	
    }
    if (sensor_meio == 1) {
    	
    }
})
 ```

## Passo 14

Vamos repetir o processo caso **sensor direito** seja ativado, porémm vamos 
fazer com que o **LED direito** do FuzzyBoT ascenda. Para isso, vá até a 
 aba ``||fuzzyBot:FuzzyBoT||`` e arraste um bloco 
 ``||fuzzyBot:LED [esquerdo] definir para [Ligado]||`` para dentro do bloco 
 ``||logic:se <(sensor_dir) = (1)> então||``. Clique em cima do botão 
``||fuzzyBot:[esquerdo]||`` do bloco e altere-o para ``||fuzzyBot:[direito]||``.
 Em seguida, clique no ícone de **+** na parte inferior do bloco para adicionar 
 um bloco ``||logic:senão||`` a essa condição.

 ```blocks
let sensor_meio = 0
let sensor_dir = 0
let sensor_esq = 0
basic.showIcon(IconNames.Heart)
basic.pause(1000)
basic.clearScreen()
basic.forever(function () {
    sensor_esq = fuzzyBot.readPatrol(fuzzyBot.Patrol.PatrolLeft)
    sensor_dir = fuzzyBot.readPatrol(fuzzyBot.Patrol.PatrolRight)
    sensor_meio = fuzzyBot.readPatrol(fuzzyBot.Patrol.PatrolMiddle)
    if (sensor_esq == 1) {
        fuzzyBot.writeLED(fuzzyBot.LED.LEDLeft, fuzzyBot.LEDswitch.turnOn)
    } else {
        fuzzyBot.writeLED(fuzzyBot.LED.LEDLeft, fuzzyBot.LEDswitch.turnOff)
    }
    if (sensor_dir == 1) {
        fuzzyBot.writeLED(fuzzyBot.LED.LEDRight, fuzzyBot.LEDswitch.turnOn)
    } else {
    	
    }
    if (sensor_meio == 1) {
    	
    }
})
 ```

## Passo 15

Vá até a aba ``||fuzzyBot:FuzzyBoT||`` e arraste um bloco 
``||fuzzyBot:LED [esquerdo] definir para [Ligado]||`` para dentro do bloco 
``||logic:senão||`` criado no passo anterior. Clique em cima do botão 
``||fuzzyBot:[esquerdo]||`` do bloco e altere-o para ``||fuzzyBot:[direito]||`` 
e, em seguida, clique em cima do botão ``||fuzzyBot:[Ligado]||`` 
do bloco e altere-o para ``||fuzzyBot:[Desligado]||``. 

 ```blocks
let sensor_meio = 0
let sensor_dir = 0
let sensor_esq = 0
basic.showIcon(IconNames.Heart)
basic.pause(1000)
basic.clearScreen()
basic.forever(function () {
    sensor_esq = fuzzyBot.readPatrol(fuzzyBot.Patrol.PatrolLeft)
    sensor_dir = fuzzyBot.readPatrol(fuzzyBot.Patrol.PatrolRight)
    sensor_meio = fuzzyBot.readPatrol(fuzzyBot.Patrol.PatrolMiddle)
    if (sensor_esq == 1) {
        fuzzyBot.writeLED(fuzzyBot.LED.LEDLeft, fuzzyBot.LEDswitch.turnOn)
    } else {
        fuzzyBot.writeLED(fuzzyBot.LED.LEDLeft, fuzzyBot.LEDswitch.turnOff)
    }
    if (sensor_dir == 1) {
        fuzzyBot.writeLED(fuzzyBot.LED.LEDRight, fuzzyBot.LEDswitch.turnOn)
    } else {
        fuzzyBot.writeLED(fuzzyBot.LED.LEDRight, fuzzyBot.LEDswitch.turnOff)
    }
    if (sensor_meio == 1) {
    	
    }
})
 ```

## Passo 16

Por fim, caso o **sensor do meio** seja ativado, vamos programar a **matriz de LED** 
do micro:bit para mostrar um **ícone de diamante**. Caso contrário (se identificar 
a linha) vamos limpar a matriz de LED. Para isso, vá até a aba 
``||basic:Básico||`` e arraste um bloco  ``||Basic:mostrar ícone [♡]||`` 
para dentro do bloco ``||logic:se <(sensor_meio) = (1)> então||``. Altere o 
ícone de coração para um ícone de diamante pequeno e, em seguida, clique no 
ícone de **+** na parte inferior do bloco para adicionar um bloco 
``||logic:senão||`` a essa condição.

 ```blocks
let sensor_meio = 0
let sensor_dir = 0
let sensor_esq = 0
basic.showIcon(IconNames.Heart)
basic.pause(1000)
basic.clearScreen()
basic.forever(function () {
    sensor_esq = fuzzyBot.readPatrol(fuzzyBot.Patrol.PatrolLeft)
    sensor_dir = fuzzyBot.readPatrol(fuzzyBot.Patrol.PatrolRight)
    sensor_meio = fuzzyBot.readPatrol(fuzzyBot.Patrol.PatrolMiddle)
    if (sensor_esq == 1) {
        fuzzyBot.writeLED(fuzzyBot.LED.LEDLeft, fuzzyBot.LEDswitch.turnOn)
    } else {
        fuzzyBot.writeLED(fuzzyBot.LED.LEDLeft, fuzzyBot.LEDswitch.turnOff)
    }
    if (sensor_dir == 1) {
        fuzzyBot.writeLED(fuzzyBot.LED.LEDRight, fuzzyBot.LEDswitch.turnOn)
    } else {
        fuzzyBot.writeLED(fuzzyBot.LED.LEDRight, fuzzyBot.LEDswitch.turnOff)
    }
    if (sensor_meio == 1) {
        basic.showIcon(IconNames.SmallDiamond)
    } else {
    	
    }
})
 ```

## Passo 17

Para finalizar, vá até a aba ``||basic:Básico||`` e arraste um bloco 
``||basic:limpar tela||`` para dentro do bloco 
``||logic:senão||`` criado no passo anterior.

 ```blocks
let sensor_meio = 0
let sensor_dir = 0
let sensor_esq = 0
basic.showIcon(IconNames.Heart)
basic.pause(1000)
basic.clearScreen()
basic.forever(function () {
    sensor_esq = fuzzyBot.readPatrol(fuzzyBot.Patrol.PatrolLeft)
    sensor_dir = fuzzyBot.readPatrol(fuzzyBot.Patrol.PatrolRight)
    sensor_meio = fuzzyBot.readPatrol(fuzzyBot.Patrol.PatrolMiddle)
    if (sensor_esq == 1) {
        fuzzyBot.writeLED(fuzzyBot.LED.LEDLeft, fuzzyBot.LEDswitch.turnOn)
    } else {
        fuzzyBot.writeLED(fuzzyBot.LED.LEDLeft, fuzzyBot.LEDswitch.turnOff)
    }
    if (sensor_dir == 1) {
        fuzzyBot.writeLED(fuzzyBot.LED.LEDRight, fuzzyBot.LEDswitch.turnOn)
    } else {
        fuzzyBot.writeLED(fuzzyBot.LED.LEDRight, fuzzyBot.LEDswitch.turnOff)
    }
    if (sensor_meio == 1) {
        basic.showIcon(IconNames.SmallDiamond)
    } else {
        basic.clearScreen()
    }
})
 ```

## Passo 18

Código finalizado! Agora transfira o código para o seu micro:bit e siga a partir do **passo 8** 
do tutorial de montagem para realizar a calibração dos sensores infravermelhos. 
Sempre realize a calibração antes de projetos que utilizam o seguidor de linha, isso garante o 
funcionamento correto nas superfícies em que a calibração está sendo realizada.

```package
fuzzyBot=github:FuzzyMakers/pxt-fuzzyMakers
```

