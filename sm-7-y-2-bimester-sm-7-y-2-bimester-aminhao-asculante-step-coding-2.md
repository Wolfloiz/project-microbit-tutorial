### @diffs true
# Caminhão Basculante

## Passo 1
Nesse tutorial, vamos programar um caminhão que pode se movimentar para frente,
para trás e parar, além de levantar ou abaixar uma caçamba. Portanto, deveremos 
controlar o motor CC em uma das rodas e o servomotor responsável por alterar
o ângulo da caçamba. 

## Passo 2
Para começar, verifique se a biblioteca da Smart Makers já está importada 
em seu MakeCode. Se não estiver, clique na aba **+ Extensões**, 
copie o endereço "https://github.com/FuzzyMakers/pxt-smartMakers",
cole-o no campo de pesquisa da janela que se abriu e selecione a biblioteca.

## Passo 3
Acesse o menu ``||variables:Variáveis||`` e clique em **"Fazer uma variável..."**.
Crie duas variáveis chamadas: ``||variables:cacamba||`` e ``||variables:motor||``. 
Por fim, adicione dois blocos ``||variables:definir motor para 0||`` que
aparecerão ao criá-las, dentro do laço ``||basic:no iniciar||``. 
Clique na seta de um dos blocos para alterar a variável de ``||variables:motor||`` 
para ``||variables:cacamba||``. 

```blocks
let motor = 0
let cacamba = 0
basic.forever(function () {
	
})
```

## Passo 4
Em seguida, altere o valor de definição de 
``||variables:motor||`` para **1023** e de  ``||variables:cacamba||`` para
**60**.

```blocks
let motor = 1023
let cacamba = 60
basic.forever(function () {
	
})
```

## Passo 5
Acesse a categoria ``||actuators:Atuadores||`` e adicione o bloco
``||actuators:Servo, definir posição 0 porta P8 modo Knob||`` 
dentro do laço ``||basic:no iniciar||``. 

```blocks
let motor = 1023
let cacamba = 60
actuators.SetAngleServoKnob(0, OutputPorts.P8)
basic.forever(function () {
	
})
```

## Passo 6
Altere a porta do bloco do servo de **P8** para **P16**. Em seguida, acesse 
o menu ``||variables:Variáveis||`` e utilize o bloco ``||variables:cacamba||`` 
para substituir o valor **0** da posição do servo.

```blocks
let motor = 1023
let cacamba = 60
actuators.SetAngleServoKnob(cacamba, OutputPorts.P16)
basic.forever(function () {
	
})
```

## Passo 7
Acesse o menu ``||input:Entrada||`` e adicione o bloco 
``||input:no logotipo pressionado||`` ao seu código.

```blocks
input.onLogoEvent(TouchButtonEvent.Pressed, function () {
	
})
let motor = 1023
let cacamba = 60
actuators.SetAngleServoKnob(cacamba, OutputPorts.P16)
basic.forever(function () {
	
})
```

## Passo 8
Vá à aba ``||logic:Lógica||`` e adicione um bloco ``||logic:se então senão||``
dentro do bloco ``||input:no logotipo pressionado||``.

```blocks
input.onLogoEvent(TouchButtonEvent.Pressed, function () {
    if (true) {
    	
    } else {
    	
    }
})
let motor = 1023
let cacamba = 60
actuators.SetAngleServoKnob(cacamba, OutputPorts.P16)
basic.forever(function () {
	
})
```

## Passo 9
Retorne ao menu de ``||logic:Lógica||`` e selecione um bloco comparador
``||logic:0 = 0||`` para substituir o campo **verdadeiro** do 
``||logic:se então senão||``.

```blocks
input.onLogoEvent(TouchButtonEvent.Pressed, function () {
    if (0 == 0) {
    	
    } else {
    	
    }
})
let motor = 1023
let cacamba = 60
actuators.SetAngleServoKnob(cacamba, OutputPorts.P16)
basic.forever(function () {
	
})
```

## Passo 10
Utilize a variável ``||variables:motor||`` para substituir o primeiro **0**
desse comparador. Já no segundo campo, modifique o valor para **1023**.

```blocks
input.onLogoEvent(TouchButtonEvent.Pressed, function () {
    if (motor == 1023) {
    	
    } else {
    	
    }
})
let motor = 0
motor = 1023
let cacamba = 60
actuators.SetAngleServoKnob(cacamba, OutputPorts.P16)
basic.forever(function () {
	
})
```

## Passo 11
Retorne ao menu ``||variables:Variáveis||`` e adicione dois blocos 
``||variables:definir motor para 0||``. Um deles deve ficar dentro do 
``||logic:então||`` e o outro dentro do ``||logic:senão||``.

```blocks
input.onLogoEvent(TouchButtonEvent.Pressed, function () {
    if (motor == 1023) {
        motor = 0
    } else {
        motor = 0
    }
})
let motor = 0
motor = 1023
let cacamba = 60
actuators.SetAngleServoKnob(cacamba, OutputPorts.P16)
basic.forever(function () {
	
})
```

## Passo 12
Altere o valor do bloco dentro do ``||logic:senão||`` de **0** para **1023**.
Assim, garantimos que, ao pressionarmos o logotipo, a variável motor vai alterar
seu valor de 0 para 1023 e vice-versa.

```blocks
input.onLogoEvent(TouchButtonEvent.Pressed, function () {
    if (motor == 1023) {
        motor = 0
    } else {
        motor = 1023
    }
})
let motor = 0
motor = 1023
let cacamba = 60
actuators.SetAngleServoKnob(cacamba, OutputPorts.P16)
basic.forever(function () {
	
})
```

## Passo 13
Agora, prosseguimos para a programação do laço ``||basic:sempre||``. 
Acesse o menu ``||actuators:Atuadores||`` e adicione o comando 
``||actuators:Motor CC, definir velocidade 0 na porta P8||`` dentro 
do laço ``||basic:sempre||``.

```blocks
input.onLogoEvent(TouchButtonEvent.Pressed, function () {
    if (motor == 1023) {
        motor = 0
    } else {
        motor = 1023
    }
})
let motor = 0
motor = 1023
let cacamba = 60
actuators.SetAngleServoKnob(cacamba, OutputPorts.P16)
basic.forever(function () {
    actuators.SetSpeedMotor(0, OutputPorts.P8)
})
```

## Passo 14
Altere a porta de **P8** para **P12** e o valor da velocidade desse bloco 
de **0** para a variável ``||variables:motor||``.

```blocks
input.onLogoEvent(TouchButtonEvent.Pressed, function () {
    if (motor == 1023) {
        motor = 0
    } else {
        motor = 1023
    }
})
let motor = 0
motor = 1023
let cacamba = 60
actuators.SetAngleServoKnob(cacamba, OutputPorts.P16)
basic.forever(function () {
    actuators.SetSpeedMotor(motor, OutputPorts.P12)
})
```

## Passo 15
Volte à aba ``||logic:Lógica||`` e adicione um bloco ``||logic:se então senão||``
dentro do bloco ``||basic:sempre||``.

```blocks
input.onLogoEvent(TouchButtonEvent.Pressed, function () {
    if (motor == 1023) {
        motor = 0
    } else {
        motor = 1023
    }
})
let motor = 0
motor = 1023
let cacamba = 60
actuators.SetAngleServoKnob(cacamba, OutputPorts.P16)
basic.forever(function () {
    actuators.SetSpeedMotor(motor, OutputPorts.P12)
    if (true) {
    	
    } else {
    	
    }
})
```

## Passo 16
Retorne ao menu de ``||logic:Lógica||`` e selecione um bloco comparador
``||logic:0 = 0||`` para substituir o campo **verdadeiro** do 
``||logic:se então senão||``.

```blocks
input.onLogoEvent(TouchButtonEvent.Pressed, function () {
    if (motor == 1023) {
        motor = 0
    } else {
        motor = 1023
    }
})
let motor = 0
motor = 1023
let cacamba = 60
actuators.SetAngleServoKnob(cacamba, OutputPorts.P16)
basic.forever(function () {
    actuators.SetSpeedMotor(motor, OutputPorts.P12)
    if (0 == 0) {
    	
    } else {
    	
    }
})
```

## Passo 17
Acesse a categoria ``||sensors:Sensores||`` e posicione o bloco
``||sensors:Valor do Botão na porta P2||`` no primeiro campo do comparador.
**Atenção:** Altere a porta desse bloco de **P2** para **P1**.

```blocks
input.onLogoEvent(TouchButtonEvent.Pressed, function () {
    if (motor == 1023) {
        motor = 0
    } else {
        motor = 1023
    }
})
let motor = 0
motor = 1023
let cacamba = 60
actuators.SetAngleServoKnob(cacamba, OutputPorts.P16)
basic.forever(function () {
    actuators.SetSpeedMotor(motor, OutputPorts.P12)
    if (sensors.buttonValue(InputPorts.P1) == 0) {
    	
    } else {
    	
    }
})
```

## Passo 18
Retorne ao menu de ``||actuators:Atuadores||`` e adicione um bloco
``||actuators:Motor CC, definir direção para Sentido horário na porta P8||`` 
dentro do ``||logic:então||`` e outro igual dentro do ``||logic:senão||``. 

```blocks
input.onLogoEvent(TouchButtonEvent.Pressed, function () {
    if (motor == 1023) {
        motor = 0
    } else {
        motor = 1023
    }
})
let motor = 0
motor = 1023
let cacamba = 60
actuators.SetAngleServoKnob(cacamba, OutputPorts.P16)
basic.forever(function () {
    actuators.SetSpeedMotor(motor, OutputPorts.P12)
    if (sensors.buttonValue(InputPorts.P1) == 0) {
        actuators.SetDirectionMotor(MotorDirection.clockwise, OutputPorts.P8)
    } else {
        actuators.SetDirectionMotor(MotorDirection.clockwise, OutputPorts.P8)
    }
})
```

## Passo 19
Clique na seta do bloco dentro do ``||logic:senão||`` para alterar o sentido de 
rotação de ``||actuators:horário||`` para ``||actuators:anti-horário||``. 

```blocks
input.onLogoEvent(TouchButtonEvent.Pressed, function () {
    if (motor == 1023) {
        motor = 0
    } else {
        motor = 1023
    }
})
let motor = 0
motor = 1023
let cacamba = 60
actuators.SetAngleServoKnob(cacamba, OutputPorts.P16)
basic.forever(function () {
    actuators.SetSpeedMotor(motor, OutputPorts.P12)
    if (sensors.buttonValue(InputPorts.P1) == 0) {
        actuators.SetDirectionMotor(MotorDirection.clockwise, OutputPorts.P8)
    } else {
        actuators.SetDirectionMotor(MotorDirection.antiClockwise, OutputPorts.P8)
    }
})
```

## Passo 20
Agora, acesse a aba ``||basic:Básico||`` e adicione um segundo laço 
``||basic:sempre||`` em seu código.

```blocks
input.onLogoEvent(TouchButtonEvent.Pressed, function () {
    if (motor == 1023) {
        motor = 0
    } else {
        motor = 1023
    }
})
let motor = 0
motor = 1023
let cacamba = 60
actuators.SetAngleServoKnob(cacamba, OutputPorts.P16)
basic.forever(function () {
    actuators.SetSpeedMotor(motor, OutputPorts.P12)
    if (sensors.buttonValue(InputPorts.P1) == 0) {
        actuators.SetDirectionMotor(MotorDirection.clockwise, OutputPorts.P8)
    } else {
        actuators.SetDirectionMotor(MotorDirection.antiClockwise, OutputPorts.P8)
    }
})
basic.forever(function () {
	
})
```

## Passo 21
Vá à categoria ``||logic:Lógica||`` e adicione um bloco ``||logic:se então||`` 
dentro desse novo laço ``||basic:sempre||``.

```blocks
input.onLogoEvent(TouchButtonEvent.Pressed, function () {
    if (motor == 1023) {
        motor = 0
    } else {
        motor = 1023
    }
})
let motor = 0
motor = 1023
let cacamba = 60
actuators.SetAngleServoKnob(cacamba, OutputPorts.P16)
basic.forever(function () {
    actuators.SetSpeedMotor(motor, OutputPorts.P12)
    if (sensors.buttonValue(InputPorts.P1) == 0) {
        actuators.SetDirectionMotor(MotorDirection.clockwise, OutputPorts.P8)
    } else {
        actuators.SetDirectionMotor(MotorDirection.antiClockwise, OutputPorts.P8)
    }
})
basic.forever(function () {
    if (true) {
    	
    }
})
```

## Passo 22
Acesse o menu ``||input:Entrada||`` e utilize o bloco de bordas triangulares
``||input:botão A é pressionado||`` para substituir o campo **verdadeiro**
do bloco ``||logic:se então||``. 

```blocks
input.onLogoEvent(TouchButtonEvent.Pressed, function () {
    if (motor == 1023) {
        motor = 0
    } else {
        motor = 1023
    }
})
let motor = 0
motor = 1023
let cacamba = 60
actuators.SetAngleServoKnob(cacamba, OutputPorts.P16)
basic.forever(function () {
    actuators.SetSpeedMotor(motor, OutputPorts.P12)
    if (sensors.buttonValue(InputPorts.P1) == 0) {
        actuators.SetDirectionMotor(MotorDirection.clockwise, OutputPorts.P8)
    } else {
        actuators.SetDirectionMotor(MotorDirection.antiClockwise, OutputPorts.P8)
    }
})
basic.forever(function () {
    if (input.buttonIsPressed(Button.A)) {
    	
    }
})
```

## Passo 23
Clique na aba ``||variables:Variáveis||`` e adicione o bloco 
``||variables:alterar motor por 1||`` dentro do ``||logic:então||``.
Clique na seta para alterar da variável ``||variables:motor||`` 
para ``||variables:cacamba||``. Por fim, edite o valor de **1** para **20**. 

```blocks
input.onLogoEvent(TouchButtonEvent.Pressed, function () {
    if (motor == 1023) {
        motor = 0
    } else {
        motor = 1023
    }
})
let motor = 0
motor = 1023
let cacamba = 60
actuators.SetAngleServoKnob(cacamba, OutputPorts.P16)
basic.forever(function () {
    actuators.SetSpeedMotor(motor, OutputPorts.P12)
    if (sensors.buttonValue(InputPorts.P1) == 0) {
        actuators.SetDirectionMotor(MotorDirection.clockwise, OutputPorts.P8)
    } else {
        actuators.SetDirectionMotor(MotorDirection.antiClockwise, OutputPorts.P8)
    }
})
basic.forever(function () {
    if (input.buttonIsPressed(Button.A)) {
        cacamba += 20
    }
})
```

## Passo 24
Abaixo desse bloco, adicione o comando 
``||actuators:Servo, definir posição 0 porta P8 modo Knob||``. Altere a porta de
**P8** para **P16** e o valor da posição de **0** para a variável 
``||variables:cacamba||``.

```blocks
input.onLogoEvent(TouchButtonEvent.Pressed, function () {
    if (motor == 1023) {
        motor = 0
    } else {
        motor = 1023
    }
})
let motor = 0
motor = 1023
let cacamba = 60
actuators.SetAngleServoKnob(cacamba, OutputPorts.P16)
basic.forever(function () {
    actuators.SetSpeedMotor(motor, OutputPorts.P12)
    if (sensors.buttonValue(InputPorts.P1) == 0) {
        actuators.SetDirectionMotor(MotorDirection.clockwise, OutputPorts.P8)
    } else {
        actuators.SetDirectionMotor(MotorDirection.antiClockwise, OutputPorts.P8)
    }
})
basic.forever(function () {
    if (input.buttonIsPressed(Button.A)) {
        cacamba += 20
        actuators.SetAngleServoKnob(cacamba, OutputPorts.P16)
    }
})
```

## Passo 25
Vá até a aba ``||basic:Básico||`` e adicione um bloco 
``||basic:pausa (ms) 100||`` dentro do ``||logic:então||``.

```blocks
input.onLogoEvent(TouchButtonEvent.Pressed, function () {
    if (motor == 1023) {
        motor = 0
    } else {
        motor = 1023
    }
})
let motor = 0
motor = 1023
let cacamba = 60
actuators.SetAngleServoKnob(cacamba, OutputPorts.P16)
basic.forever(function () {
    actuators.SetSpeedMotor(motor, OutputPorts.P12)
    if (sensors.buttonValue(InputPorts.P1) == 0) {
        actuators.SetDirectionMotor(MotorDirection.clockwise, OutputPorts.P8)
    } else {
        actuators.SetDirectionMotor(MotorDirection.antiClockwise, OutputPorts.P8)
    }
})
basic.forever(function () {
    if (input.buttonIsPressed(Button.A)) {
        cacamba += 20
        actuators.SetAngleServoKnob(cacamba, OutputPorts.P16)
        basic.pause(100)
    }
})
```

## Passo 26
Agora, devemos criar um terceiro laço ``||basic:sempre||`` idêntico ao anterior.
Você pode selecionar todo o laço e duplicá-lo ou simplesmente adicionar todos os 
comando manualmente.

```blocks
input.onLogoEvent(TouchButtonEvent.Pressed, function () {
    if (motor == 1023) {
        motor = 0
    } else {
        motor = 1023
    }
})
let motor = 0
motor = 1023
let cacamba = 60
actuators.SetAngleServoKnob(cacamba, OutputPorts.P16)
basic.forever(function () {
    actuators.SetSpeedMotor(motor, OutputPorts.P12)
    if (sensors.buttonValue(InputPorts.P1) == 0) {
        actuators.SetDirectionMotor(MotorDirection.clockwise, OutputPorts.P8)
    } else {
        actuators.SetDirectionMotor(MotorDirection.antiClockwise, OutputPorts.P8)
    }
})
basic.forever(function () {
    if (input.buttonIsPressed(Button.A)) {
        cacamba += 20
        actuators.SetAngleServoKnob(cacamba, OutputPorts.P16)
        basic.pause(100)
    }
})
basic.forever(function () {
    if (input.buttonIsPressed(Button.A)) {
        cacamba += 20
        actuators.SetAngleServoKnob(cacamba, OutputPorts.P16)
        basic.pause(100)
    }
})
```

## Passo 27
Clique na seta do bloco de bordas triangulares ``||input:botão A é pressionado||``
desse novo laço para alterar de ``||input:botão A||`` para ``||input:botão B||``.

```blocks
input.onLogoEvent(TouchButtonEvent.Pressed, function () {
    if (motor == 1023) {
        motor = 0
    } else {
        motor = 1023
    }
})
let motor = 0
motor = 1023
let cacamba = 60
actuators.SetAngleServoKnob(cacamba, OutputPorts.P16)
basic.forever(function () {
    actuators.SetSpeedMotor(motor, OutputPorts.P12)
    if (sensors.buttonValue(InputPorts.P1) == 0) {
        actuators.SetDirectionMotor(MotorDirection.clockwise, OutputPorts.P8)
    } else {
        actuators.SetDirectionMotor(MotorDirection.antiClockwise, OutputPorts.P8)
    }
})
basic.forever(function () {
    if (input.buttonIsPressed(Button.A)) {
        cacamba += 20
        actuators.SetAngleServoKnob(cacamba, OutputPorts.P16)
        basic.pause(100)
    }
})
basic.forever(function () {
    if (input.buttonIsPressed(Button.B)) {
        cacamba += 20
        actuators.SetAngleServoKnob(cacamba, OutputPorts.P16)
        basic.pause(100)
    }
})
```

## Passo 28
Por fim, modifique o valor do bloco ``||variables:alterar cacamba por 20||`` de
**20** para **-20**.

```blocks
input.onLogoEvent(TouchButtonEvent.Pressed, function () {
    if (motor == 1023) {
        motor = 0
    } else {
        motor = 1023
    }
})
let motor = 0
motor = 1023
let cacamba = 60
actuators.SetAngleServoKnob(cacamba, OutputPorts.P16)
basic.forever(function () {
    actuators.SetSpeedMotor(motor, OutputPorts.P12)
    if (sensors.buttonValue(InputPorts.P1) == 0) {
        actuators.SetDirectionMotor(MotorDirection.clockwise, OutputPorts.P8)
    } else {
        actuators.SetDirectionMotor(MotorDirection.antiClockwise, OutputPorts.P8)
    }
})
basic.forever(function () {
    if (input.buttonIsPressed(Button.A)) {
        cacamba += 20
        actuators.SetAngleServoKnob(cacamba, OutputPorts.P16)
        basic.pause(100)
    }
})
basic.forever(function () {
    if (input.buttonIsPressed(Button.B)) {
        cacamba += -20
        actuators.SetAngleServoKnob(cacamba, OutputPorts.P16)
        basic.pause(100)
    }
})
```

## Passo 29

Agora seu código está pronto! Baixe-o para o micro:bit e teste-o. 
O logotipo do micro:bit é usado para parar ou movimentar o caminhão.
O Bit Botão altera o sentido de movimento do veículo, enquanto os botões A e 
B do micro:bit sobem e descem a caçamba.

```blocks
```

## Passo 30
Se necessário, confira o seu código clicando na lâmpada de dica.

```blocks
input.onLogoEvent(TouchButtonEvent.Pressed, function () {
    if (motor == 1023) {
        motor = 0
    } else {
        motor = 1023
    }
})
let motor = 0
motor = 1023
let cacamba = 60
actuators.SetAngleServoKnob(cacamba, OutputPorts.P16)
basic.forever(function () {
    actuators.SetSpeedMotor(motor, OutputPorts.P12)
    if (sensors.buttonValue(InputPorts.P1) == 0) {
        actuators.SetDirectionMotor(MotorDirection.clockwise, OutputPorts.P8)
    } else {
        actuators.SetDirectionMotor(MotorDirection.antiClockwise, OutputPorts.P8)
    }
})
basic.forever(function () {
    if (input.buttonIsPressed(Button.A)) {
        cacamba += 20
        actuators.SetAngleServoKnob(cacamba, OutputPorts.P16)
        basic.pause(100)
    }
})
basic.forever(function () {
    if (input.buttonIsPressed(Button.B)) {
        cacamba += -20
        actuators.SetAngleServoKnob(cacamba, OutputPorts.P16)
        basic.pause(100)
    }
})
```

```package
fuzzyBot=github:FuzzyMakers/pxt-fuzzyMakers
```
