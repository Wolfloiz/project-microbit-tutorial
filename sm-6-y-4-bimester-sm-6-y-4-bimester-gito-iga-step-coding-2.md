### @diffs true
# Biga Egípcia

## Passo 1
Neste tutorial, vamos programar a movimentação da biga egípcia. Utilizaremos
o sensor infravermelho para acionar o motor CC.

## Passo 2
Para começar, verifique se a biblioteca da Smart Makers já está importada 
em seu MakeCode. Se não estiver, clique na aba **+ Extensões**, 
copie o endereço "https://github.com/FuzzyMakers/pxt-smartMakers",
cole-o no campo de pesquisa da janela que se abriu e selecione a biblioteca.

## Passo 3
Acesse a aba ``||actuators:Atuadores||`` e adicione o bloco
``||actuators:Motor CC, definir direção para Sentido horário na porta P8||`` dentro do laço ``||basic:no iniciar||``.

```blocks
actuators.SetDirectionMotor(MotorDirection.clockwise, OutputPorts.P8)

```
## Passo 4
Modifique o sentido de ``||actuators:horário||`` para ``||actuators:anti-horário||`` 
e a porta de ``||actuators:P8||`` para ``||actuators:P12||``.

```blocks
actuators.SetDirectionMotor(MotorDirection.antiClockwise, OutputPorts.P12)

```

## Passo 5
Acesse a aba ``||logic:Lógica||`` e adicione o bloco
``||logic:se então senão||`` dentro do laço ``||basic:sempre||``.

```blocks
actuators.SetDirectionMotor(MotorDirection.antiClockwise, OutputPorts.P12)
basic.forever(function () {
    if (true) {
    	
    } else {
    	
    }
})

```

## Passo 6
Retorne ao menu de ``||logic:Lógica||`` e selecione um bloco comparador
``||logic:0 < 0||`` para substituir o campo **verdadeiro**.

```blocks
actuators.SetDirectionMotor(MotorDirection.antiClockwise, OutputPorts.P12)
basic.forever(function () {
    if (0 < 0) {
    	
    } else {
    	
    }
})

```
## Passo 7
Altere o sinal do comparador de **<** para **>**.


```blocks
actuators.SetDirectionMotor(MotorDirection.antiClockwise, OutputPorts.P12)
basic.forever(function () {
    if (0 > 0) {
    	
    } else {
    	
    }
})

```
## Passo 8
Clique na aba ``||sensors:Sensores||`` e selecione o bloco 
``||sensors:Valor do sensor infravermelho na porta P2||``. Ele deve ser posicionado no primeiro campo do comparador, substituindo o valor **0**.

```blocks
actuators.SetDirectionMotor(MotorDirection.antiClockwise, OutputPorts.P12)
basic.forever(function () {
    if (sensors.infraredValue(InputPorts.P2) > 0) {
    	
    } else {
    	
    }
})

```
## Passo 9

Mude a porta de ``||sensors:P2||`` para ``||sensors:P1||`` e o valor do segundo comparador de **0** para **300**.

```blocks
actuators.SetDirectionMotor(MotorDirection.antiClockwise, OutputPorts.P12)
basic.forever(function () {
    if (sensors.infraredValue(InputPorts.P1) > 300) {
    	
    } else {
    	
    }
})
```

## Passo 10
Acesse a categoria ``||actuators:Atuadores||`` e adicione o bloco 
``||actuators:Motor CC, definir velocidade 0 na porta P8||`` dentro do ``||logic:então||``.

```blocks
actuators.SetDirectionMotor(MotorDirection.antiClockwise, OutputPorts.P12)
basic.forever(function () {
    if (sensors.infraredValue(InputPorts.P1) > 300) {
        actuators.SetSpeedMotor(0, OutputPorts.P8)
    } else {
    	
    }
})

```

## Passo 11

Modifique a velocidade de **0** para **600** e a porta de 
``||actuators:P8||`` para ``||actuators:P16||``.

```blocks
actuators.SetDirectionMotor(MotorDirection.antiClockwise, OutputPorts.P12)
basic.forever(function () {
    if (sensors.infraredValue(InputPorts.P1) > 300) {
        actuators.SetSpeedMotor(600, OutputPorts.P16)
    } else {
    	
    }
})
```

## Passo 12
Volte ao menu ``||actuators:Atuadores||`` e adicione o bloco 
``||actuators:Motor CC, parar motor na porta P8||`` dentro do ``||logic:senão||``.

```blocks
actuators.SetDirectionMotor(MotorDirection.antiClockwise, OutputPorts.P12)
basic.forever(function () {
    if (sensors.infraredValue(InputPorts.P1) > 300) {
        actuators.SetSpeedMotor(600, OutputPorts.P16)
    } else {
        actuators.StopMotor(OutputPorts.P8)
    }
})
```

## Passo 13

Altere a porta de ``||actuators:P8||`` para ``||actuators:P16||``.

```blocks
actuators.SetDirectionMotor(MotorDirection.antiClockwise, OutputPorts.P12)
basic.forever(function () {
    if (sensors.infraredValue(InputPorts.P1) > 300) {
        actuators.SetSpeedMotor(600, OutputPorts.P16)
    } else {
        actuators.StopMotor(OutputPorts.P16)
    }
})

```


## Passo 14

Seu código está pronto! Baixe-o para o micro:bit e teste-o. 
Aproxime algo do sensor infravermelho para movimentar a biga.

```blocks
```

## Passo 15
Se necessário, confira o seu código clicando na lâmpada de dica.

```blocks
actuators.SetDirectionMotor(MotorDirection.antiClockwise, OutputPorts.P12)
basic.forever(function () {
    if (sensors.infraredValue(InputPorts.P1) > 300) {
        actuators.SetSpeedMotor(600, OutputPorts.P16)
    } else {
        actuators.StopMotor(OutputPorts.P16)
    }
})

```

```package
fuzzyBot=github:FuzzyMakers/pxt-fuzzyMakers
```
