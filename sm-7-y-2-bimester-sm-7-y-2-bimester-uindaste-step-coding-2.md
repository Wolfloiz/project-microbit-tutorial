### @diffs true
# Guindaste

## Passo 1
Nesse tutorial, vamos programar o guindaste para ser capaz de girar ao redor 
de seu próprio eixo, além de levantar e abaixar as cargas. O potenciômetro 
será responsável por girar a estrutura, o botão interruptor definirá o 
sentido de movimento da corda, enquanto a chave fim de curso acionará ou desligará
o motor de içamento.


## Passo 2
Para começar, verifique se a biblioteca da Smart Makers já está importada 
em seu MakeCode. Se não estiver, clique na aba **+ Extensões**, 
copie o endereço "https://github.com/FuzzyMakers/pxt-smartMakers",
cole-o no campo de pesquisa da janela que se abriu e selecione a biblioteca.

## Passo 3
Acesse a aba ``||actuators:Atuadores||`` e adicione o bloco
``||actuators:Servo, definir posição 0 porta P8 modo Knob||`` dentro do laço
``||basic:sempre||``.

```blocks
basic.forever(function () {
    actuators.SetAngleServoKnob(0, OutputPorts.P8)
})
```

## Passo 4
Vá à aba ``||sensors:Sensores||`` e utilize o bloco 
``||sensors:Valor do potenciômetro na porta P2||`` para substituir o valor **0**
da posição do servomotor.

```blocks
basic.forever(function () {
    actuators.SetAngleServoKnob(sensors.dimmerValue(InputPorts.P2), OutputPorts.P8)
})
```

## Passo 5
Altere a porta desse bloco do potenciômetro de **P2** para **P1**.

```blocks
basic.forever(function () {
    actuators.SetAngleServoKnob(sensors.dimmerValue(InputPorts.P1), OutputPorts.P8)
})
```

## Passo 6
Acesse a aba ``||basic:Básico||`` e adicione outro laço ``||basic:sempre||``
ao seu código.

```blocks
basic.forever(function () {
    actuators.SetAngleServoKnob(sensors.dimmerValue(InputPorts.P1), OutputPorts.P8)
})
basic.forever(function () {
	
})
```

## Passo 7
Vá ao menu ``||logic:Lógica||`` e adicione um bloco ``||logic:se então senão||``
dentro do bloco ``||basic:sempre||``.

```blocks
basic.forever(function () {
    actuators.SetAngleServoKnob(sensors.dimmerValue(InputPorts.P1), OutputPorts.P8)
})
basic.forever(function () {
    if (true) {
    	
    } else {
    	
    }
})
```

## Passo 8
Retorne ao menu de ``||logic:Lógica||`` e selecione um bloco comparador
``||logic:0 = 0||`` para substituir o campo **verdadeiro** do 
``||logic:se então senão||``.

```blocks
basic.forever(function () {
    actuators.SetAngleServoKnob(sensors.dimmerValue(InputPorts.P1), OutputPorts.P8)
})
basic.forever(function () {
    if (0 == 0) {
    	
    } else {
    	
    }
})
```

## Passo 9
Volte à aba ``||sensors:Sensores||`` para substituir o primeiro **0**
desse comparador pelo bloco 
``||sensors:Valor da chave fim de curso na porta P2||``. 
Já no segundo campo, modifique o valor de **0** para **1**.

```blocks
basic.forever(function () {
    actuators.SetAngleServoKnob(sensors.dimmerValue(InputPorts.P1), OutputPorts.P8)
})
basic.forever(function () {
    if (sensors.endstopValue(InputPorts.P2) == 1) {
    	
    } else {
    	
    }
})
```

## Passo 10
Acesse o menu ``||actuators:Atuadores||`` e insira o bloco 
``||actuators:Motor CC, definir velocidade 0 na porta P8||`` dentro do 
``||logic:então||``. Modifique o valor de velocidade de **0** para **1023** e 
a porta de **P8** para **P16**.

```blocks
basic.forever(function () {
    actuators.SetAngleServoKnob(sensors.dimmerValue(InputPorts.P1), OutputPorts.P8)
})
basic.forever(function () {
    if (sensors.endstopValue(InputPorts.P2) == 1) {
        actuators.SetSpeedMotor(1023, OutputPorts.P16)
    } else {
    	
    }
})
```

## Passo 11
Volte à ``||actuators:Atuadores||`` e insira o bloco 
``||actuators:Motor CC, parar motor na porta P8||`` dentro do 
``||logic:senão||``. Altere a porta de **P8** para **P16**.

```blocks
basic.forever(function () {
    actuators.SetAngleServoKnob(sensors.dimmerValue(InputPorts.P1), OutputPorts.P8)
})
basic.forever(function () {
    if (sensors.endstopValue(InputPorts.P2) == 1) {
        actuators.SetSpeedMotor(1023, OutputPorts.P16)
    } else {
        actuators.StopMotor(OutputPorts.P16)
    }
})
```

## Passo 12
Acesse a aba ``||basic:Básico||`` e adicione um terceiro laço ``||basic:sempre||``
ao seu código.

```blocks
basic.forever(function () {
    actuators.SetAngleServoKnob(sensors.dimmerValue(InputPorts.P1), OutputPorts.P8)
})
basic.forever(function () {
    if (sensors.endstopValue(InputPorts.P2) == 1) {
        actuators.SetSpeedMotor(1023, OutputPorts.P16)
    } else {
        actuators.StopMotor(OutputPorts.P16)
    }
})
basic.forever(function () {
	
})
```

## Passo 13
Vá ao menu ``||logic:Lógica||`` e adicione um bloco ``||logic:se então senão||``
dentro desse novo ``||basic:sempre||``.

```blocks
basic.forever(function () {
    actuators.SetAngleServoKnob(sensors.dimmerValue(InputPorts.P1), OutputPorts.P8)
})
basic.forever(function () {
    if (sensors.endstopValue(InputPorts.P2) == 1) {
        actuators.SetSpeedMotor(1023, OutputPorts.P16)
    } else {
        actuators.StopMotor(OutputPorts.P16)
    }
})
basic.forever(function () {
    if (true) {
    	
    } else {
    	
    }
})
```

## Passo 14
Retorne ao menu de ``||logic:Lógica||`` e selecione um bloco comparador
``||logic:0 = 0||`` para substituir o campo **verdadeiro** do 
``||logic:se então senão||``.

```blocks
basic.forever(function () {
    actuators.SetAngleServoKnob(sensors.dimmerValue(InputPorts.P1), OutputPorts.P8)
})
basic.forever(function () {
    if (sensors.endstopValue(InputPorts.P2) == 1) {
        actuators.SetSpeedMotor(1023, OutputPorts.P16)
    } else {
        actuators.StopMotor(OutputPorts.P16)
    }
})
basic.forever(function () {
    if (0 == 0) {
    	
    } else {
    	
    }
})
```

## Passo 15
Volte à aba ``||sensors:Sensores||`` para substituir o primeiro **0**
desse comparador pelo bloco 
``||sensors:Valor do Botão na porta P2||``. Altere a porta desse bloco de **P2**
para **P0**. Já no segundo campo, modifique o valor de **0** para **1**.

```blocks
basic.forever(function () {
    actuators.SetAngleServoKnob(sensors.dimmerValue(InputPorts.P1), OutputPorts.P8)
})
basic.forever(function () {
    if (sensors.endstopValue(InputPorts.P2) == 1) {
        actuators.SetSpeedMotor(1023, OutputPorts.P16)
    } else {
        actuators.StopMotor(OutputPorts.P16)
    }
})
basic.forever(function () {
    if (sensors.buttonValue(InputPorts.P0) == 1) {
    	
    } else {
    	
    }
})
```

## Passo 16
Acesse o menu ``||actuators:Atuadores||`` e insira o bloco 
``||actuators:Motor CC, definir direção para sentido horário na porta P8||`` 
dentro do ``||logic:então||``. Modifique a porta de **P8** para **P12**.

```blocks
basic.forever(function () {
    actuators.SetAngleServoKnob(sensors.dimmerValue(InputPorts.P1), OutputPorts.P8)
})
basic.forever(function () {
    if (sensors.endstopValue(InputPorts.P2) == 1) {
        actuators.SetSpeedMotor(1023, OutputPorts.P16)
    } else {
        actuators.StopMotor(OutputPorts.P16)
    }
})
basic.forever(function () {
    if (sensors.buttonValue(InputPorts.P0) == 1) {
        actuators.SetDirectionMotor(MotorDirection.clockwise, OutputPorts.P12)
    } else {
    	
    }
})
```

## Passo 17
Volte à ``||actuators:Atuadores||`` e insira outro bloco 
``||actuators:Motor CC, definir direção para sentido horário na porta P8||`` 
dentro do ``||logic:senão||``. Altere a porta de **P8** para **P12** e o sentido
de rotação de ``||actuators:horário||`` para ``||actuators:anti-horário||``.  

```blocks
basic.forever(function () {
    actuators.SetAngleServoKnob(sensors.dimmerValue(InputPorts.P1), OutputPorts.P8)
})
basic.forever(function () {
    if (sensors.endstopValue(InputPorts.P2) == 1) {
        actuators.SetSpeedMotor(1023, OutputPorts.P16)
    } else {
        actuators.StopMotor(OutputPorts.P16)
    }
})
basic.forever(function () {
    if (sensors.buttonValue(InputPorts.P0) == 1) {
        actuators.SetDirectionMotor(MotorDirection.clockwise, OutputPorts.P12)
    } else {
        actuators.SetDirectionMotor(MotorDirection.antiClockwise, OutputPorts.P12)
    }
})
```

## Passo 18

Agora seu código está pronto! Baixe-o para o micro:bit e teste-o. 
Use o potenciômetro para girar o guindaste, o botão interruptor para alterar o 
sentido de movimento da corda e a chave fim de curso para acionar ou desligar
o motor de içamento.

```blocks
```

## Passo 19
Se necessário, confira o seu código clicando na lâmpada de dica.

```blocks
basic.forever(function () {
    actuators.SetAngleServoKnob(sensors.dimmerValue(InputPorts.P1), OutputPorts.P8)
})
basic.forever(function () {
    if (sensors.endstopValue(InputPorts.P2) == 1) {
        actuators.SetSpeedMotor(1023, OutputPorts.P16)
    } else {
        actuators.StopMotor(OutputPorts.P16)
    }
})
basic.forever(function () {
    if (sensors.buttonValue(InputPorts.P0) == 1) {
        actuators.SetDirectionMotor(MotorDirection.clockwise, OutputPorts.P12)
    } else {
        actuators.SetDirectionMotor(MotorDirection.antiClockwise, OutputPorts.P12)
    }
})
```

```package
fuzzyBot=github:FuzzyMakers/pxt-fuzzyMakers
```
