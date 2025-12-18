### @diffs true
# Prótese

## Passo 1
Neste tutorial, vamos programar a prótese de uma mão movimentada pelo servomotor.
Aprenderemos como usar o sensor infravermelho para identificar quando existe 
algum objeto sobre a palma da mão para acionar o movimento do motor.

## Passo 2
Para começar, verifique se a biblioteca da Smart Makers já está importada 
em seu MakeCode. Se não estiver, clique na aba **+ Extensões**, 
copie o endereço "https://github.com/FuzzyMakers/pxt-smartMakers",
cole-o no campo de pesquisa da janela que se abriu e selecione a biblioteca.

## Passo 3
Acesse a aba ``||logic:Lógica||`` e adicione o bloco ``||logic:se então senão||`` 
dentro do bloco ``||basic:sempre||``.

```blocks
basic.forever(function () {
    if (true) {
    	
    } else {
    	
    }
})
```

## Passo 4
Retorne à ``||logic:Lógica||`` e utilize o bloco comparador 
``||logic:0 < 0||`` para substituir o campo **verdadeiro** do bloco 
``||logic:se então senão||``.

```blocks
basic.forever(function () {
    if (0 < 0) {
    	
    } else {
    	
    }
})
```

## Passo 5
Acesse o menu ``||sensors:Sensores||`` e selecione o bloco 
``||sensors:Valor do sensor infravermelho na porta P2||`` para substituir o valor 
**0** do primeiro campo do comparador. 

```blocks
basic.forever(function () {
    if (sensors.infraredValue(InputPorts.P2) < 0) {
    	
    } else {
    	
    }
})
```

## Passo 6
Clique na seta para alterar a porta de ``||sensors:P2||`` para 
``||sensors:P1||``. Em seguida, altere o segundo campo do comparador de 
**0** para **500**.

```blocks
basic.forever(function () {
    if (sensors.infraredValue(InputPorts.P1) < 500) {
    	
    } else {
    	
    }
})
```

## Passo 7
Acesse a categoria ``||actuators:Atuadores||`` e adicione o comando 
``||actuators:Servo, definir posição 0 porta P8 modo Knob||`` dentro do 
``||logic:então||`` e ``||logic:senão||``.

```blocks
basic.forever(function () {
    if (sensors.infraredValue(InputPorts.P1) < 500) {
        actuators.SetAngleServoKnob(0, OutputPorts.P8)
    } else {
        actuators.SetAngleServoKnob(0, OutputPorts.P8)
    }
})
```

## Passo 8
Modifique a porta de ambos os blocos de ``||actuators:P8||`` para 
``||actuators:P16||``. Em seguida, edite o valor de posição do primeiro bloco,
dentro do ``||logic:então||`` para **320**.

```blocks
basic.forever(function () {
    if (sensors.infraredValue(InputPorts.P1) < 500) {
        actuators.SetAngleServoKnob(320, OutputPorts.P16)
    } else {
        actuators.SetAngleServoKnob(0, OutputPorts.P16)
    }
})
```

## Passo 9
Agora, também devemos garantir que a prótese se inicie na posição correta.
Para isso, acesse a categoria ``||basic:Básico||`` e adicione o bloco
``||basic:no iniciar||`` ao código. Em seguida, adicione o comando 
``||actuators:Servo, definir posição 0 porta P8 modo Knob||`` dentro do 
``||basic:no iniciar||``.

```blocks
actuators.SetAngleServoKnob(0, OutputPorts.P8)
basic.forever(function () {
    if (sensors.infraredValue(InputPorts.P1) < 500) {
        actuators.SetAngleServoKnob(320, OutputPorts.P16)
    } else {
        actuators.SetAngleServoKnob(0, OutputPorts.P16)
    }
})
```

## Passo 10
Também altere a porta de ``||actuators:P8||`` para ``||actuators:P16||`` e 
o valor de posição de **0** para **320**.

```blocks
actuators.SetAngleServoKnob(320, OutputPorts.P16)
basic.forever(function () {
    if (sensors.infraredValue(InputPorts.P1) < 500) {
        actuators.SetAngleServoKnob(320, OutputPorts.P16)
    } else {
        actuators.SetAngleServoKnob(0, OutputPorts.P16)
    }
})
```

## Passo 11
Retorne à aba ``||basic:Básico||`` e adicione o bloco
``||basic:pausa (ms) 100||`` dentro do ``||basic:no iniciar||``.

```blocks
actuators.SetAngleServoKnob(320, OutputPorts.P16)
basic.pause(100)
basic.forever(function () {
    if (sensors.infraredValue(InputPorts.P1) < 500) {
        actuators.SetAngleServoKnob(320, OutputPorts.P16)
    } else {
        actuators.SetAngleServoKnob(0, OutputPorts.P16)
    }
})
```

## Passo 12
Altere a duração dessa ``||basic:pausa||`` de **100 ms** para **1000 ms** 
(1 segundo).

```blocks
actuators.SetAngleServoKnob(320, OutputPorts.P16)
basic.pause(1000)
basic.forever(function () {
    if (sensors.infraredValue(InputPorts.P1) < 500) {
        actuators.SetAngleServoKnob(320, OutputPorts.P16)
    } else {
        actuators.SetAngleServoKnob(0, OutputPorts.P16)
    }
})
```

## Passo 13
Agora, seu código está pronto! Baixe-o para o micro:bit e aproxime sua mão do
sensor infravermelho para observar o movimento da prótese.

```blocks
```

## Passo 14
Se necessário, confira o seu código clicando na lâmpada de dica.

```blocks
actuators.SetAngleServoKnob(320, OutputPorts.P16)
basic.pause(1000)
basic.forever(function () {
    if (sensors.infraredValue(InputPorts.P1) < 500) {
        actuators.SetAngleServoKnob(320, OutputPorts.P16)
    } else {
        actuators.SetAngleServoKnob(0, OutputPorts.P16)
    }
})
```

```package
fuzzyBot=github:FuzzyMakers/pxt-fuzzyMakers
```