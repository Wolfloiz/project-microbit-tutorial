### @diffs true
# Energia Fóssil

## Passo 1
Neste tutorial, vamos programar a usina baseada em combustíveis fósseis para 
que, ao posicionarmos o carvão na fornalha, identificado pelo sensor
infravermelho, o movimento do pistão se inicie com a rotação do motor.

## Passo 2
Para começar, verifique se a biblioteca da Smart Makers já está importada 
em seu MakeCode. Se não estiver, clique na aba **+ Extensões**, 
copie o endereço "https://github.com/FuzzyMakers/pxt-smartMakers",
cole-o no campo de pesquisa da janela que se abriu e selecione a biblioteca.

## Passo 3
Acesse o menu ``||variables:Variáveis||`` e clique em 
**"Fazer uma variável..."**. Crie uma variável chamada 
``||variables:combustível||`` e, depois de criá-la, adicione o bloco 
``||variables:definir combustível para 0||`` dentro do ``||basic:sempre||``.

```blocks
let combustível = 0
basic.forever(function () {
    combustível = 0
})
```

## Passo 4
Vá à categoria ``||sensors:Sensores||`` e utilize o bloco 
``||sensors:Valor do sensor infravermelho na porta P2||`` para substituir o 
valor **0** do bloco de definição da variável ``||variables:combustível||``.

```blocks
let combustível = 0
basic.forever(function () {
    combustível = sensors.infraredValue(InputPorts.P2)
})
```

## Passo 5
Acesse a aba ``||logic:Lógica||`` e adicione o bloco ``||logic:se então senão||`` 
dentro do laço ``||basic:sempre||``.

```blocks
let combustível = 0
basic.forever(function () {
    combustível = sensors.infraredValue(InputPorts.P2)
    if (true) {
    	
    } else {
    	
    }
})
```

## Passo 6
Clique uma vez no sinal de **+** desse bloco para adicionar uma nova condição
``||logic:senão se||``.

```blocks
let combustível = 0
basic.forever(function () {
    combustível = sensors.infraredValue(InputPorts.P2)
    if (true) {
    	
    } else if (false) {
    	
    } else {
    	
    }
})
```

## Passo 7
Retorne à ``||logic:Lógica||`` e utilize o bloco comparador 
``||logic:0 < 0||`` para substituir os campos **verdadeiro** e **falso** 
de cada condição ``||logic:se então||``.

```blocks
let combustível = 0
basic.forever(function () {
    combustível = sensors.infraredValue(InputPorts.P2)
    if (0 < 0) {
    	
    } else if (0 < 0) {
    	
    } else {
    	
    }
})
```

## Passo 8
Altere o sinal de ambos os comparadores de **<** para **>**.

```blocks
let combustível = 0
basic.forever(function () {
    combustível = sensors.infraredValue(InputPorts.P2)
    if (0 > 0) {
    	
    } else if (0 > 0) {
    	
    } else {
    	
    }
})
```

## Passo 9
Acesse a categoria ``||variables:Variáveis||`` e utilize o bloco da variável 
``||variables:combustível||`` para substituir o primeiro campo de ambos os 
comparadores.

```blocks
let combustível = 0
basic.forever(function () {
    combustível = sensors.infraredValue(InputPorts.P2)
    if (combustível > 0) {
    	
    } else if (combustível > 0) {
    	
    } else {
    	
    }
})
```

## Passo 10
Modifique os valores dos segundos campos dos comparadores de **0** para 
**400** e **150**, respectivamente.

```blocks
let combustível = 0
basic.forever(function () {
    combustível = sensors.infraredValue(InputPorts.P2)
    if (combustível > 400) {
    	
    } else if (combustível > 150) {
    	
    } else {
    	
    }
})
```

## Passo 11
Acesse o menu ``||actuators:Atuadores||`` e adicione um comando 
``||actuators:Motor CC, definir velocidade 0 na porta P8||`` dentro de cada
condição ``||logic:então||`` e ``||logic:senão||``. 

```blocks
let combustível = 0
basic.forever(function () {
    combustível = sensors.infraredValue(InputPorts.P2)
    if (combustível > 400) {
        actuators.SetSpeedMotor(0, OutputPorts.P8)
    } else if (combustível > 150) {
        actuators.SetSpeedMotor(0, OutputPorts.P8)
    } else {
        actuators.SetSpeedMotor(0, OutputPorts.P8)
    }
})
```

## Passo 12
Altere os valores de velocidade dos dois primeiros blocos de **0** para **650**
e **200**, respectivamente.

```blocks
let combustível = 0
basic.forever(function () {
    combustível = sensors.infraredValue(InputPorts.P2)
    if (combustível > 400) {
        actuators.SetSpeedMotor(650, OutputPorts.P8)
    } else if (combustível > 150) {
        actuators.SetSpeedMotor(200, OutputPorts.P8)
    } else {
        actuators.SetSpeedMotor(0, OutputPorts.P8)
    }
})
```

## Passo 13
Vá à aba ``||basic:Básico||`` e adicione um comando ``||basic:mostrar ícone||`` 
dentro de cada condição ``||logic:então||`` e ``||logic:senão||``, após os 
blocos ``||actuators:Motor CC, definir velocidade||``.

```blocks
let combustível = 0
basic.forever(function () {
    combustível = sensors.infraredValue(InputPorts.P2)
    if (combustível > 400) {
        actuators.SetSpeedMotor(650, OutputPorts.P8)
        basic.showIcon(IconNames.Heart)
    } else if (combustível > 150) {
        actuators.SetSpeedMotor(200, OutputPorts.P8)
        basic.showIcon(IconNames.Heart)
    } else {
        actuators.SetSpeedMotor(0, OutputPorts.P8)
        basic.showIcon(IconNames.Heart)
    }
})
```

## Passo 14
Altere o ícone a ser exibido nos dois últimos comandos ``||basic:mostrar ícone||`` 
para um **coração pequeno** e um **X**.

```blocks
let combustível = 0
basic.forever(function () {
    combustível = sensors.infraredValue(InputPorts.P2)
    if (combustível > 400) {
        actuators.SetSpeedMotor(650, OutputPorts.P8)
        basic.showIcon(IconNames.Heart)
    } else if (combustível > 150) {
        actuators.SetSpeedMotor(200, OutputPorts.P8)
        basic.showIcon(IconNames.SmallHeart)
    } else {
        actuators.SetSpeedMotor(0, OutputPorts.P8)
        basic.showIcon(IconNames.No)
    }
})
```

## Passo 15
Agora, seu código está pronto! Baixe-o para o micro:bit, abasteça a usina
com o carvão e observe o movimento do motor.

```blocks
```

## Passo 16
Se necessário, confira o seu código clicando na lâmpada de dica.

```blocks
let combustível = 0
basic.forever(function () {
    combustível = sensors.infraredValue(InputPorts.P2)
    if (combustível > 400) {
        actuators.SetSpeedMotor(650, OutputPorts.P8)
        basic.showIcon(IconNames.Heart)
    } else if (combustível > 150) {
        actuators.SetSpeedMotor(200, OutputPorts.P8)
        basic.showIcon(IconNames.SmallHeart)
    } else {
        actuators.SetSpeedMotor(0, OutputPorts.P8)
        basic.showIcon(IconNames.No)
    }
})
```

```package
fuzzyBot=github:FuzzyMakers/pxt-fuzzyMakers
```