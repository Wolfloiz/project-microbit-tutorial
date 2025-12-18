### @diffs true
# Braço Robótico

## Passo 1
Nesse tutorial, vamos programar os movimentos do braço robótico. Utilizaremos
os botões A e B do micro:bit para abrir e fechar a garra, enquanto o servomotor
rotaciona a estrutura. 

## Passo 2
Para começar, verifique se a biblioteca da Smart Makers já está importada 
em seu MakeCode. Se não estiver, clique na aba **+ Extensões**, 
copie o endereço "https://github.com/FuzzyMakers/pxt-smartMakers",
cole-o no campo de pesquisa da janela que se abriu e selecione a biblioteca.

## Passo 3
Acesse a aba ``||logic:Lógica||`` e adicione o bloco
``||logic:se então senão||`` dentro do laço ``||basic:sempre||``.

```blocks
basic.forever(function () {
    if (true) {
    	
    } else {
    	
    }
})
```

## Passo 4
Clique no sinal de **+** desse bloco para abrir um segundo condicional 
``||logic:senão se||``.

```blocks
basic.forever(function () {
    if (true) {
    	
    } else if (false) {
    	
    } else {
    	
    }
})
```

## Passo 5
Acesse a aba ``||input:Entrada||`` e utilize o bloco de bordas triangulares 
``||input:botão A é pressionado||`` para substituir o **verdadeiro** e o 
**falso** da segunda condição. Clique na seta desse segundo para alterar de
``||input:botão A||`` para ``||input:botão B||``.  

```blocks
basic.forever(function () {
    if (input.buttonIsPressed(Button.A)) {
    	
    } else if (input.buttonIsPressed(Button.B)) {
    	
    } else {
    	
    }
})
```

## Passo 6
Acesse a categoria ``||actuators:Atuadores||`` e adicione o bloco 
``||actuators:Motor CC, definir velocidade 0 na porta P8||`` 
dentro do ``||logic:então||``.

```blocks
basic.forever(function () {
    if (input.buttonIsPressed(Button.A)) {
        actuators.SetSpeedMotor(0, OutputPorts.P8)
    } else if (input.buttonIsPressed(Button.B)) {
    	
    } else {
    	
    }
})
```

## Passo 7
Altere o valor da velocidade de **0** para **1023** e a porta de 
``||actuators:P8||`` para ``||actuators:P16||``.

```blocks
basic.forever(function () {
    if (input.buttonIsPressed(Button.A)) {
        actuators.SetSpeedMotor(1023, OutputPorts.P16)
    } else if (input.buttonIsPressed(Button.B)) {
    	
    } else {
    	
    }
})
```

## Passo 8
Retorne à categoria ``||actuators:Atuadores||`` e insira o bloco 
``||actuators:Motor CC, definir direção para sentido horário na porta P8||`` 
ainda dentro do ``||logic:então||``.

```blocks
basic.forever(function () {
    if (input.buttonIsPressed(Button.A)) {
        actuators.SetSpeedMotor(1023, OutputPorts.P16)
        actuators.SetDirectionMotor(MotorDirection.clockwise, OutputPorts.P8)
    } else if (input.buttonIsPressed(Button.B)) {
    	
    } else {
    	
    }
})
```

## Passo 9
Modifique a porta de ``||actuators:P8||`` para ``||actuators:P12||``.

```blocks
basic.forever(function () {
    if (input.buttonIsPressed(Button.A)) {
        actuators.SetSpeedMotor(1023, OutputPorts.P16)
        actuators.SetDirectionMotor(MotorDirection.clockwise, OutputPorts.P12)
    } else if (input.buttonIsPressed(Button.B)) {
    	
    } else {
    	
    }
})
```

## Passo 10
Agora, no condicional em que o ``||input:botão B é pressionado||``, 
teremos os mesmos dois blocos, com as mesmas portas,
porém o sentido de rotação deve ser alterado para 
``||actuators:anti-horário||``. 

```blocks
basic.forever(function () {
    if (input.buttonIsPressed(Button.A)) {
        actuators.SetSpeedMotor(1023, OutputPorts.P16)
        actuators.SetDirectionMotor(MotorDirection.clockwise, OutputPorts.P12)
    } else if (input.buttonIsPressed(Button.B)) {
        actuators.SetSpeedMotor(1023, OutputPorts.P16)
        actuators.SetDirectionMotor(MotorDirection.antiClockwise, OutputPorts.P12)
    } else {
    	
    }
})
```

## Passo 11
Volte ao menu ``||actuators:Atuadores||`` e insira o bloco 
``||actuators:Motor CC, parar motor na porta P8||`` dentro do ``||logic:senão||``.

```blocks
basic.forever(function () {
    if (input.buttonIsPressed(Button.A)) {
        actuators.SetSpeedMotor(1023, OutputPorts.P16)
        actuators.SetDirectionMotor(MotorDirection.clockwise, OutputPorts.P12)
    } else if (input.buttonIsPressed(Button.B)) {
        actuators.SetSpeedMotor(1023, OutputPorts.P16)
        actuators.SetDirectionMotor(MotorDirection.antiClockwise, OutputPorts.P12)
    } else {
        actuators.StopMotor(OutputPorts.P8)
    }
})
```

## Passo 12
Altere a porta de ``||actuators:P8||`` para ``||actuators:P16||``.

```blocks
basic.forever(function () {
    if (input.buttonIsPressed(Button.A)) {
        actuators.SetSpeedMotor(1023, OutputPorts.P16)
        actuators.SetDirectionMotor(MotorDirection.clockwise, OutputPorts.P12)
    } else if (input.buttonIsPressed(Button.B)) {
        actuators.SetSpeedMotor(1023, OutputPorts.P16)
        actuators.SetDirectionMotor(MotorDirection.antiClockwise, OutputPorts.P12)
    } else {
        actuators.StopMotor(OutputPorts.P16)
    }
})
```

## Passo 13
Acesse a aba ``||basic:Básico||`` e adicione um segundo laço 
``||basic:sempre||`` ao seu código.

```blocks
basic.forever(function () {
    if (input.buttonIsPressed(Button.A)) {
        actuators.SetSpeedMotor(1023, OutputPorts.P16)
        actuators.SetDirectionMotor(MotorDirection.clockwise, OutputPorts.P12)
    } else if (input.buttonIsPressed(Button.B)) {
        actuators.SetSpeedMotor(1023, OutputPorts.P16)
        actuators.SetDirectionMotor(MotorDirection.antiClockwise, OutputPorts.P12)
    } else {
        actuators.StopMotor(OutputPorts.P16)
    }
})
basic.forever(function () {
	
})
```

## Passo 14
Retorne ao menu ``||actuators:Atuadores||`` e insira o bloco 
``||actuators:Servo, definir posição 0 porta P8 modo Knob||`` dentro desse novo
``||basic:sempre||``.

```blocks
basic.forever(function () {
    if (input.buttonIsPressed(Button.A)) {
        actuators.SetSpeedMotor(1023, OutputPorts.P16)
        actuators.SetDirectionMotor(MotorDirection.clockwise, OutputPorts.P12)
    } else if (input.buttonIsPressed(Button.B)) {
        actuators.SetSpeedMotor(1023, OutputPorts.P16)
        actuators.SetDirectionMotor(MotorDirection.antiClockwise, OutputPorts.P12)
    } else {
        actuators.StopMotor(OutputPorts.P16)
    }
})
basic.forever(function () {
    actuators.SetAngleServoKnob(0, OutputPorts.P8)
})
```

## Passo 15
Acesse a categoria ``||sensors:Sensores||`` e insira o bloco 
``||sensors:Valor do potenciômetro na porta P2||`` substituindo o valor de
posição do bloco do servomotor.

```blocks
basic.forever(function () {
    if (input.buttonIsPressed(Button.A)) {
        actuators.SetSpeedMotor(1023, OutputPorts.P16)
        actuators.SetDirectionMotor(MotorDirection.clockwise, OutputPorts.P12)
    } else if (input.buttonIsPressed(Button.B)) {
        actuators.SetSpeedMotor(1023, OutputPorts.P16)
        actuators.SetDirectionMotor(MotorDirection.antiClockwise, OutputPorts.P12)
    } else {
        actuators.StopMotor(OutputPorts.P16)
    }
})
basic.forever(function () {
    actuators.SetAngleServoKnob(sensors.dimmerValue(InputPorts.P2), OutputPorts.P8)
})
```

## Passo 16
Altere a porta do potenciômetro de ``||sensors:P2||`` para ``||sensors:P1||``.

```blocks
basic.forever(function () {
    if (input.buttonIsPressed(Button.A)) {
        actuators.SetSpeedMotor(1023, OutputPorts.P16)
        actuators.SetDirectionMotor(MotorDirection.clockwise, OutputPorts.P12)
    } else if (input.buttonIsPressed(Button.B)) {
        actuators.SetSpeedMotor(1023, OutputPorts.P16)
        actuators.SetDirectionMotor(MotorDirection.antiClockwise, OutputPorts.P12)
    } else {
        actuators.StopMotor(OutputPorts.P16)
    }
})
basic.forever(function () {
    actuators.SetAngleServoKnob(sensors.dimmerValue(InputPorts.P1), OutputPorts.P8)
})
```

## Passo 17
Volte à ``||basic:Básico||`` e adicione um bloco de ``||basic:pausa (ms) 100||``
dentro desse laço ``||basic:sempre||``. 

```blocks
basic.forever(function () {
    if (input.buttonIsPressed(Button.A)) {
        actuators.SetSpeedMotor(1023, OutputPorts.P16)
        actuators.SetDirectionMotor(MotorDirection.clockwise, OutputPorts.P12)
    } else if (input.buttonIsPressed(Button.B)) {
        actuators.SetSpeedMotor(1023, OutputPorts.P16)
        actuators.SetDirectionMotor(MotorDirection.antiClockwise, OutputPorts.P12)
    } else {
        actuators.StopMotor(OutputPorts.P16)
    }
})
basic.forever(function () {
    actuators.SetAngleServoKnob(sensors.dimmerValue(InputPorts.P1), OutputPorts.P8)
    basic.pause(100)
})
```

## Passo 18

Seu código está pronto! Baixe-o para o micro:bit e teste-o. 
Utilize os botões A e B do micro:bit para abrir e fechar a garra. O potenciômetro
é responsável por girar o braço robótico a partir da posição do ponteiro.

```blocks
```

## Passo 19
Se necessário, confira o seu código clicando na lâmpada de dica.

```blocks
basic.forever(function () {
    if (input.buttonIsPressed(Button.A)) {
        actuators.SetSpeedMotor(1023, OutputPorts.P16)
        actuators.SetDirectionMotor(MotorDirection.clockwise, OutputPorts.P12)
    } else if (input.buttonIsPressed(Button.B)) {
        actuators.SetSpeedMotor(1023, OutputPorts.P16)
        actuators.SetDirectionMotor(MotorDirection.antiClockwise, OutputPorts.P12)
    } else {
        actuators.StopMotor(OutputPorts.P16)
    }
})
basic.forever(function () {
    actuators.SetAngleServoKnob(sensors.dimmerValue(InputPorts.P1), OutputPorts.P8)
    basic.pause(100)
})
```

```package
fuzzyBot=github:FuzzyMakers/pxt-fuzzyMakers
```
