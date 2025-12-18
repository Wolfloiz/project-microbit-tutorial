### @diffs true
# Beisebol

## Passo 1
Neste tutorial, vamos programar um robô rebatedor. Os botões A e B do micro:bit serão usados para 
posicionar os braços do jogador de beisebol, e o logotipo irá disparar a rebatida.

## Passo 2
Para começar, verifique se a biblioteca da Smart Makers já está importada 
em seu MakeCode. Se não estiver, clique na aba **+ Extensões**, 
copie o endereço "https://github.com/FuzzyMakers/pxt-smartMakers",
cole-o no campo de pesquisa da janela que se abriu e selecione a biblioteca.

## Passo 3
Acesse a aba ``||actuators:Atuadores||`` e adicione o bloco
``||actuators:Servo Definir posição 0 porta P8 modo Knob||`` dentro da função ``||basic:no iniciar||``.
Modifique a posição do servo de **0** para **500**.

```blocks
actuators.SetAngleServoKnob(500, OutputPorts.P8)

```

## Passo 4

Acesse a categoria ``||logic:Lógica||``, pegue a condicional ``||logic:se então senão||``
e insira-a dentro do bloco ``||basic:sempre||``. 
Clique no botão **+** para criar mais uma condição ``||logic:senão se||``.

```blocks
actuators.SetAngleServoKnob(500, OutputPorts.P8)
basic.forever(function () {
    if (true) {
    	
    } else if (false) {
    	
    } else {
    	
    }
})

```

## Passo 5

Na aba ``||input:Entrada||``, selecione **dois** blocos ``||input:botão A é pressionado||`` para 
substituir as condições ``||logic:verdadeiro||`` e ``||logic:falso||``.
Altere a segunda condição para ``||input:botão B é pressionado||``.


```blocks
actuators.SetAngleServoKnob(500, OutputPorts.P8)
basic.forever(function () {
    if (input.buttonIsPressed(Button.A)) {
    	
    } else if (input.buttonIsPressed(Button.B)) {
    	
    } else {
    	
    }
})

```

## Passo 6

Acesse o menu ``||actuators:Atuadores||`` e adicione o bloco
``||actuators:Motor CC, definir direção para Sentido horário na porta P8||``
dentro do ``||logic:se botão A é pressionado então||``.

```blocks
actuators.SetAngleServoKnob(500, OutputPorts.P8)
basic.forever(function () {
    if (input.buttonIsPressed(Button.A)) {
        actuators.SetDirectionMotor(MotorDirection.clockwise, OutputPorts.P8)
    } else if (input.buttonIsPressed(Button.B)) {
    	
    } else {
    	
    }
})
```
## Passo 7

Mude a porta de ``||actuators:P8||`` para ``||actuators:P12||``.

```blocks
actuators.SetAngleServoKnob(500, OutputPorts.P8)
basic.forever(function () {
    if (input.buttonIsPressed(Button.A)) {
        actuators.SetDirectionMotor(MotorDirection.clockwise, OutputPorts.P12)
    } else if (input.buttonIsPressed(Button.B)) {
    	
    } else {
    	
    }
})
```
## Passo 8

Volte à aba ``||actuators:Atuadores||`` e adicione o bloco
``||actuators:Motor CC, definir velocidade 0 na porta P8||``
abaixo do último bloco.

```blocks
actuators.SetAngleServoKnob(500, OutputPorts.P8)
basic.forever(function () {
    if (input.buttonIsPressed(Button.A)) {
        actuators.SetDirectionMotor(MotorDirection.clockwise, OutputPorts.P12)
        actuators.SetSpeedMotor(0, OutputPorts.P8)
    } else if (input.buttonIsPressed(Button.B)) {
    	
    } else {
    	
    }
})
```

## Passo 9

Modifique a porta de ``||actuators:P8||`` para ``||actuators:P16||`` 
e a velocidade de **0** para **1023**.

```blocks
actuators.SetAngleServoKnob(500, OutputPorts.P8)
basic.forever(function () {
    if (input.buttonIsPressed(Button.A)) {
        actuators.SetDirectionMotor(MotorDirection.clockwise, OutputPorts.P12)
        actuators.SetSpeedMotor(1023, OutputPorts.P16)
    } else if (input.buttonIsPressed(Button.B)) {
    	
    } else {
    	
    }
})
```
## Passo 10

Duplique os blocos que definem a velocidade e orientação do motor no ``||logic:se botão A é pressionado então||``
e coloque as cópias dentro da condição ``||logic:senão se botão B é pressionado então||``. 
Altere o sentido de ``||actuators:horário||`` para ``||actuators:anti-horário||``.

```blocks
actuators.SetAngleServoKnob(500, OutputPorts.P8)
basic.forever(function () {
    if (input.buttonIsPressed(Button.A)) {
        actuators.SetDirectionMotor(MotorDirection.clockwise, OutputPorts.P12)
        actuators.SetSpeedMotor(1023, OutputPorts.P16)
    } else if (input.buttonIsPressed(Button.B)) {
        actuators.SetDirectionMotor(MotorDirection.antiClockwise, OutputPorts.P12)
        actuators.SetSpeedMotor(1023, OutputPorts.P16)
    } else {
    	
    }
})
```

## Passo 11

Mais uma vez duplique os blocos que definem a velocidade e orientação do motor no ``||logic:se botão A é pressionado então||``,
mas agora adicione as cópias dentro da condição ``||logic:senão||``. 
Altere a velocidade do motor de **1023** para **0**.

```blocks
actuators.SetAngleServoKnob(500, OutputPorts.P8)
basic.forever(function () {
    if (input.buttonIsPressed(Button.A)) {
        actuators.SetDirectionMotor(MotorDirection.clockwise, OutputPorts.P12)
        actuators.SetSpeedMotor(1023, OutputPorts.P16)
    } else if (input.buttonIsPressed(Button.B)) {
        actuators.SetDirectionMotor(MotorDirection.antiClockwise, OutputPorts.P12)
        actuators.SetSpeedMotor(1023, OutputPorts.P16)
    } else {
        actuators.SetDirectionMotor(MotorDirection.clockwise, OutputPorts.P12)
        actuators.SetSpeedMotor(0, OutputPorts.P16)
    }
})

```
## Passo 12
No menu ``||input:Entrada||`` busque o bloco ``||input:no logotipo pressionado||`` e adicione-o
à área de programação.

```blocks
input.onLogoEvent(TouchButtonEvent.Pressed, function () {
	
})
actuators.SetAngleServoKnob(500, OutputPorts.P8)
basic.forever(function () {
    if (input.buttonIsPressed(Button.A)) {
        actuators.SetDirectionMotor(MotorDirection.clockwise, OutputPorts.P12)
        actuators.SetSpeedMotor(1023, OutputPorts.P16)
    } else if (input.buttonIsPressed(Button.B)) {
        actuators.SetDirectionMotor(MotorDirection.antiClockwise, OutputPorts.P12)
        actuators.SetSpeedMotor(1023, OutputPorts.P16)
    } else {
        actuators.SetDirectionMotor(MotorDirection.clockwise, OutputPorts.P12)
        actuators.SetSpeedMotor(0, OutputPorts.P16)
    }
})
```

## Passo 13

Copie o bloco ``||actuators:Servo Definir posição 500 porta P8 modo Knob||`` dentro da função ``||basic:no iniciar||``
e cole-o duas vezes dentro do ``||input:no logotipo pressionado||``. 
```blocks
input.onLogoEvent(TouchButtonEvent.Pressed, function () {
    actuators.SetAngleServoKnob(500, OutputPorts.P8)
    actuators.SetAngleServoKnob(500, OutputPorts.P8)
})
actuators.SetAngleServoKnob(500, OutputPorts.P8)
basic.forever(function () {
    if (input.buttonIsPressed(Button.A)) {
        actuators.SetDirectionMotor(MotorDirection.clockwise, OutputPorts.P12)
        actuators.SetSpeedMotor(1023, OutputPorts.P16)
    } else if (input.buttonIsPressed(Button.B)) {
        actuators.SetDirectionMotor(MotorDirection.antiClockwise, OutputPorts.P12)
        actuators.SetSpeedMotor(1023, OutputPorts.P16)
    } else {
        actuators.SetDirectionMotor(MotorDirection.clockwise, OutputPorts.P12)
        actuators.SetSpeedMotor(0, OutputPorts.P16)
    }
})
```

## Passo 14

Mude a posição do primeiro bloco de **500** para **0** e a do segundo de **500** para **400**.

```blocks
input.onLogoEvent(TouchButtonEvent.Pressed, function () {
    actuators.SetAngleServoKnob(0, OutputPorts.P8)
    actuators.SetAngleServoKnob(400, OutputPorts.P8)
})
actuators.SetAngleServoKnob(500, OutputPorts.P8)
basic.forever(function () {
    if (input.buttonIsPressed(Button.A)) {
        actuators.SetDirectionMotor(MotorDirection.clockwise, OutputPorts.P12)
        actuators.SetSpeedMotor(1023, OutputPorts.P16)
    } else if (input.buttonIsPressed(Button.B)) {
        actuators.SetDirectionMotor(MotorDirection.antiClockwise, OutputPorts.P12)
        actuators.SetSpeedMotor(1023, OutputPorts.P16)
    } else {
        actuators.SetDirectionMotor(MotorDirection.clockwise, OutputPorts.P12)
        actuators.SetSpeedMotor(0, OutputPorts.P16)
    }
})
```
## Passo 15
Insira uma pausa ``||basic:pausa (ms) 100||`` depois do primeiro posicionamento do servo motor
e outra após o segundo posicionamento. Altere o valor da ``||basic:pausa||`` para **1000ms**.

```blocks
input.onLogoEvent(TouchButtonEvent.Pressed, function () {
    actuators.SetAngleServoKnob(0, OutputPorts.P8)
    basic.pause(1000)
    actuators.SetAngleServoKnob(400, OutputPorts.P8)
    basic.pause(1000)
})
actuators.SetAngleServoKnob(500, OutputPorts.P8)
basic.forever(function () {
    if (input.buttonIsPressed(Button.A)) {
        actuators.SetDirectionMotor(MotorDirection.clockwise, OutputPorts.P12)
        actuators.SetSpeedMotor(1023, OutputPorts.P16)
    } else if (input.buttonIsPressed(Button.B)) {
        actuators.SetDirectionMotor(MotorDirection.antiClockwise, OutputPorts.P12)
        actuators.SetSpeedMotor(1023, OutputPorts.P16)
    } else {
        actuators.SetDirectionMotor(MotorDirection.clockwise, OutputPorts.P12)
        actuators.SetSpeedMotor(0, OutputPorts.P16)
    }
})
```

## Passo 16

Agora seu código está pronto! Baixe-o para o micro:bit e teste-o. 
Os botões A e B preparam o rebatedor, enquanto 
o logotipo do micro:bit é o gatilho para a rebatida.

```blocks
```


## Passo 17
Se necessário, confira o seu código clicando na lâmpada de dica.

```blocks
input.onLogoEvent(TouchButtonEvent.Pressed, function () {
    actuators.SetAngleServoKnob(0, OutputPorts.P8)
    basic.pause(1000)
    actuators.SetAngleServoKnob(400, OutputPorts.P8)
    basic.pause(1000)
})
actuators.SetAngleServoKnob(500, OutputPorts.P8)
basic.forever(function () {
    if (input.buttonIsPressed(Button.A)) {
        actuators.SetDirectionMotor(MotorDirection.clockwise, OutputPorts.P12)
        actuators.SetSpeedMotor(1023, OutputPorts.P16)
    } else if (input.buttonIsPressed(Button.B)) {
        actuators.SetDirectionMotor(MotorDirection.antiClockwise, OutputPorts.P12)
        actuators.SetSpeedMotor(1023, OutputPorts.P16)
    } else {
        actuators.SetDirectionMotor(MotorDirection.clockwise, OutputPorts.P12)
        actuators.SetSpeedMotor(0, OutputPorts.P16)
    }
})
```

```package
fuzzyBot=github:FuzzyMakers/pxt-fuzzyMakers
```
