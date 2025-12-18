### @diffs true
# Basquete

## Passo 1
Neste tutorial, vamos programar um dispositivo que arremessa uma bola até a cesta
de basquete ao pressionarmos o logotipo do micro:bit. Os botões A e B serão usados para 
definir a posição do arremesso e sempre será exibida a quantidade de pontos já marcados.

## Passo 2
Para começar, verifique se a biblioteca da Smart Makers já está importada 
em seu MakeCode. Se não estiver, clique na aba **+ Extensões**, 
copie o endereço "https://github.com/FuzzyMakers/pxt-smartMakers",
cole-o no campo de pesquisa da janela que se abriu e selecione a biblioteca.

## Passo 3
Acesse a aba ``||actuators:Atuadores||`` e adicione o bloco
``||actuators:Servo Definir posição 0 porta P8 modo Knob||`` dentro da função ``||basic:no iniciar||``.
Modifique a posição do servo de **0** para **100**.

```blocks
actuators.SetAngleServoKnob(100, OutputPorts.P8)

```
## Passo 4
Na categoria ``||basic:Básico||`` coloque **três** blocos  ``||basic:sempre||``
dentro da área de programação.
```blocks
actuators.SetAngleServoKnob(100, OutputPorts.P8)
basic.forever(function () {
	
})
basic.forever(function () {
	
})
basic.forever(function () {
	
})

```

## Passo 5
Volte ao menu ``||basic:Básico||`` e arraste um comando ``||basic:mostrar número 0||``
para dentro de um bloco ``||basic:sempre||``.

```blocks
actuators.SetAngleServoKnob(100, OutputPorts.P8)
basic.forever(function () {
    basic.showNumber(0)
})
basic.forever(function () {
	
})
basic.forever(function () {
	
})


```

## Passo 6
Acesse o menu ``||variables:Variáveis||`` e clique em 
**"Fazer uma variável..."**. Crie uma variável chamada
``||variables:pontos||``. Em seguida, utilize o bloco
dessa variável ``||variables:pontos||`` para substituir 
o valor **0** da exibição do número.

```blocks
actuators.SetAngleServoKnob(100, OutputPorts.P8)
basic.forever(function () {
    let pontos = 0
    basic.showNumber(pontos)
})
basic.forever(function () {
	
})
basic.forever(function () {
	
})
```

## Passo 7

Acesse a categoria ``||logic:Lógica||``, clique na condicional ``||logic:se então||``
e insira-a dentro de outro bloco ``||basic:sempre||``.

```blocks
actuators.SetAngleServoKnob(100, OutputPorts.P8)
basic.forever(function () {
    let pontos = 0
    basic.showNumber(pontos)
})
basic.forever(function () {
    if (true) {
    	
    }
})
basic.forever(function () {
	
})

```

## Passo 8

Volte ao menu ``||logic:Lógica||``, pegue o comparador ``||logic:0 < 0||``
e substitua a condição **verdadeiro** da condicional.

```blocks
actuators.SetAngleServoKnob(100, OutputPorts.P8)
basic.forever(function () {
    let pontos = 0
    basic.showNumber(pontos)
})
basic.forever(function () {
    if (0 < 0) {
    	
    }
})
basic.forever(function () {
	
})


```
## Passo 9

Agora atualize os campos do comparador. Vá até a aba ``||sensors:Sensores||``,
clique no bloco ``||sensors:Valor do sensor infravermelho na porta P2||`` e troque 
o primeiro **0** do comparador.

```blocks
actuators.SetAngleServoKnob(100, OutputPorts.P8)
basic.forever(function () {
    let pontos = 0
    basic.showNumber(pontos)
})
basic.forever(function () {
    if (sensors.infraredValue(InputPorts.P2) < 0) {
    	
    }
})
basic.forever(function () {
	
})
```

## Passo 10

Em seguida, modifique o segundo campo de **0** para **300**, a porta de ``||sensors:P2||`` para ``||sensors:P1||``
e o sinal de **<** para **>**.

```blocks
actuators.SetAngleServoKnob(100, OutputPorts.P8)
basic.forever(function () {
    let pontos = 0
    basic.showNumber(pontos)
})
basic.forever(function () {
    if (sensors.infraredValue(InputPorts.P1) > 300) {
    	
    }
})
basic.forever(function () {
	
})

```
## Passo 11

Na categoria ``||variables:Variáveis||`` pegue o bloco ``||variables:alterar pontos por 1||``
e posicione-o dentro da condicional ``||logic:se então||``.

```blocks
let pontos = 0
actuators.SetAngleServoKnob(100, OutputPorts.P8)
basic.forever(function () {
    basic.showNumber(pontos)
})
basic.forever(function () {
    if (sensors.infraredValue(InputPorts.P1) > 300) {
        pontos += 1
    }
})
basic.forever(function () {
	
})
```
## Passo 12

Adicione uma pausa ``||basic:pausa (ms) 100||`` abaixo do último bloco e altere seu valor para **2000**.

```blocks
let pontos = 0
actuators.SetAngleServoKnob(100, OutputPorts.P8)
basic.forever(function () {
	
})
basic.forever(function () {
    basic.showNumber(pontos)
})
basic.forever(function () {
    if (sensors.infraredValue(InputPorts.P1) > 300) {
        pontos += 1
        basic.pause(2000)
    }
})
```

## Passo 13

Acesse a categoria ``||logic:Lógica||``, pegue a condicional ``||logic:se então senão||``
e insira-a dentro do bloco ``||basic:sempre||`` ainda vazio. 
Clique no botão **+** para criar mais uma condição ``||logic:senão se||``. 

```blocks
let pontos = 0
actuators.SetAngleServoKnob(100, OutputPorts.P8)
basic.forever(function () {
    if (true) {
    	
    } else if (false) {
    	
    } else {
    	
    }
})
basic.forever(function () {
    basic.showNumber(pontos)
})
basic.forever(function () {
    if (sensors.infraredValue(InputPorts.P1) > 300) {
        pontos += 1
        basic.pause(2000)
    }
})

```

## Passo 14

Na aba ``||input:Entrada||`` selecione **dois** blocos ``||input:botão A é pressionado||`` 
para substituir as condições ``||logic:verdadeiro||`` e ``||logic:falso||``.
Antes de prosseguir, altere a segunda condição para ``||input:botão B é pressionado||``.


```blocks
let pontos = 0
actuators.SetAngleServoKnob(100, OutputPorts.P8)
basic.forever(function () {
    if (input.buttonIsPressed(Button.A)) {
    	
    } else if (input.buttonIsPressed(Button.B)) {
    	
    } else {
    	
    }
})
basic.forever(function () {
    basic.showNumber(pontos)
})
basic.forever(function () {
    if (sensors.infraredValue(InputPorts.P1) > 300) {
        pontos += 1
        basic.pause(2000)
    }
})
```

## Passo 15

Acesse o menu ``||actuators:Atuadores||`` e adicione o bloco
``||actuators:Motor CC, definir direção para Sentido horário na porta P8||``
dentro do ``||logic:se botão A é pressionado então||``.

```blocks
let pontos = 0
actuators.SetAngleServoKnob(100, OutputPorts.P8)
basic.forever(function () {
    if (input.buttonIsPressed(Button.A)) {
        actuators.SetDirectionMotor(MotorDirection.clockwise, OutputPorts.P8)
    } else if (input.buttonIsPressed(Button.B)) {
    	
    } else {
    	
    }
})
basic.forever(function () {
    basic.showNumber(pontos)
})
basic.forever(function () {
    if (sensors.infraredValue(InputPorts.P1) > 300) {
        pontos += 1
        basic.pause(2000)
    }
})

```
## Passo 16

Mude a porta de ``||actuators:P8||`` para ``||actuators:P12||``.

```blocks
let pontos = 0
actuators.SetAngleServoKnob(100, OutputPorts.P8)
basic.forever(function () {
    if (input.buttonIsPressed(Button.A)) {
        actuators.SetDirectionMotor(MotorDirection.clockwise, OutputPorts.P12)
    } else if (input.buttonIsPressed(Button.B)) {
    	
    } else {
    	
    }
})
basic.forever(function () {
    basic.showNumber(pontos)
})
basic.forever(function () {
    if (sensors.infraredValue(InputPorts.P1) > 300) {
        pontos += 1
        basic.pause(2000)
    }
})
```

## Passo 17

Volte á aba ``||actuators:Atuadores||`` e adicione o bloco
``||actuators:Motor CC, definir velocidade 0 na porta P8||``
abaixo do último bloco.

```blocks
let pontos = 0
actuators.SetAngleServoKnob(100, OutputPorts.P8)
basic.forever(function () {
    if (input.buttonIsPressed(Button.A)) {
        actuators.SetDirectionMotor(MotorDirection.clockwise, OutputPorts.P12)
        actuators.SetSpeedMotor(0, OutputPorts.P8)
    } else if (input.buttonIsPressed(Button.B)) {
    	
    } else {
    	
    }
})
basic.forever(function () {
    basic.showNumber(pontos)
})
basic.forever(function () {
    if (sensors.infraredValue(InputPorts.P1) > 300) {
        pontos += 1
        basic.pause(2000)
    }
})


```

## Passo 18

Modifique a porta de ``||actuators:P8||`` para ``||actuators:P16||`` e 
a velocidade de **0** para **600**.

```blocks
let pontos = 0
actuators.SetAngleServoKnob(100, OutputPorts.P8)
basic.forever(function () {
    if (input.buttonIsPressed(Button.A)) {
        actuators.SetDirectionMotor(MotorDirection.clockwise, OutputPorts.P12)
        actuators.SetSpeedMotor(600, OutputPorts.P16)
    } else if (input.buttonIsPressed(Button.B)) {
    	
    } else {
    	
    }
})
basic.forever(function () {
    basic.showNumber(pontos)
})
basic.forever(function () {
    if (sensors.infraredValue(InputPorts.P1) > 300) {
        pontos += 1
        basic.pause(2000)
    }
})

```


## Passo 19

Duplique os blocos que definem a velocidade e orientação do motor no ``||logic:se botão A é pressionado então||``
e coloque as cópias dentro da condição ``||logic:senão se botão B é pressionado então||``. 
Altere o sentido de ``||actuators:horário||`` para ``||actuators:anti-horário||``.

```blocks
let pontos = 0
actuators.SetAngleServoKnob(100, OutputPorts.P8)
basic.forever(function () {
    if (input.buttonIsPressed(Button.A)) {
        actuators.SetDirectionMotor(MotorDirection.clockwise, OutputPorts.P12)
        actuators.SetSpeedMotor(600, OutputPorts.P16)
    } else if (input.buttonIsPressed(Button.B)) {
        actuators.SetDirectionMotor(MotorDirection.antiClockwise, OutputPorts.P12)
        actuators.SetSpeedMotor(600, OutputPorts.P16)
    } else {
    	
    }
})
basic.forever(function () {
    basic.showNumber(pontos)
})
basic.forever(function () {
    if (sensors.infraredValue(InputPorts.P1) > 300) {
        pontos += 1
        basic.pause(2000)
    }
})
```

## Passo 20

Acesse o menu ``||actuators:Atuadores||`` e arraste o bloco
``||actuators:Motor CC, definir velocidade 0 na porta P8||``
para dentro do ``||logic:senão||``. 
Mude a porta de ``||actuators:P8||`` para ``||actuators:P16||``. 

```blocks
let pontos = 0
actuators.SetAngleServoKnob(100, OutputPorts.P8)
basic.forever(function () {
    if (input.buttonIsPressed(Button.A)) {
        actuators.SetDirectionMotor(MotorDirection.clockwise, OutputPorts.P12)
        actuators.SetSpeedMotor(600, OutputPorts.P16)
    } else if (input.buttonIsPressed(Button.B)) {
        actuators.SetDirectionMotor(MotorDirection.antiClockwise, OutputPorts.P12)
        actuators.SetSpeedMotor(600, OutputPorts.P16)
    } else {
        actuators.SetSpeedMotor(0, OutputPorts.P16)
    }
})
basic.forever(function () {
    basic.showNumber(pontos)
})
basic.forever(function () {
    if (sensors.infraredValue(InputPorts.P1) > 300) {
        pontos += 1
        basic.pause(2000)
    }
})
```

## Passo 21
No menu ``||input:Entrada||`` busque o bloco ``||input:no logotipo pressionado||`` e adicione-o
à área de programação. Selecione o evento ``||input:tocado||`` ao invés de ``||input:pressionado||``.

```blocks
let pontos = 0
actuators.SetAngleServoKnob(100, OutputPorts.P8)
basic.forever(function () {
    if (input.buttonIsPressed(Button.A)) {
        actuators.SetDirectionMotor(MotorDirection.clockwise, OutputPorts.P12)
        actuators.SetSpeedMotor(600, OutputPorts.P16)
    } else if (input.buttonIsPressed(Button.B)) {
        actuators.SetDirectionMotor(MotorDirection.antiClockwise, OutputPorts.P12)
        actuators.SetSpeedMotor(600, OutputPorts.P16)
    } else {
        actuators.SetSpeedMotor(0, OutputPorts.P16)
    }
})
basic.forever(function () {
    basic.showNumber(pontos)
})
basic.forever(function () {
    if (sensors.infraredValue(InputPorts.P1) > 300) {
        pontos += 1
        basic.pause(2000)
    }
})
input.onLogoEvent(TouchButtonEvent.Touched, function () {
	
})
```
## Passo 22

Copie o bloco ``||actuators:Servo Definir posição 100 porta P8 modo Knob||`` dentro da função ``||basic:no iniciar||``
e cole-o três vezes dentro do ``||input:no logotipo tocado||``. 
```blocks
let pontos = 0
actuators.SetAngleServoKnob(100, OutputPorts.P8)
basic.forever(function () {
    if (input.buttonIsPressed(Button.A)) {
        actuators.SetDirectionMotor(MotorDirection.clockwise, OutputPorts.P12)
        actuators.SetSpeedMotor(600, OutputPorts.P16)
    } else if (input.buttonIsPressed(Button.B)) {
        actuators.SetDirectionMotor(MotorDirection.antiClockwise, OutputPorts.P12)
        actuators.SetSpeedMotor(600, OutputPorts.P16)
    } else {
        actuators.SetSpeedMotor(0, OutputPorts.P16)
    }
})
basic.forever(function () {
    basic.showNumber(pontos)
})
basic.forever(function () {
    if (sensors.infraredValue(InputPorts.P1) > 300) {
        pontos += 1
        basic.pause(2000)
    }
})
input.onLogoEvent(TouchButtonEvent.Touched, function () {
    actuators.SetAngleServoKnob(100, OutputPorts.P8)
    actuators.SetAngleServoKnob(100, OutputPorts.P8)
    actuators.SetAngleServoKnob(100, OutputPorts.P8)
})
```

## Passo 23

Mude a posição do bloco do meio de **100** para **350**.

```blocks
let pontos = 0
actuators.SetAngleServoKnob(100, OutputPorts.P8)
basic.forever(function () {
    if (input.buttonIsPressed(Button.A)) {
        actuators.SetDirectionMotor(MotorDirection.clockwise, OutputPorts.P12)
        actuators.SetSpeedMotor(600, OutputPorts.P16)
    } else if (input.buttonIsPressed(Button.B)) {
        actuators.SetDirectionMotor(MotorDirection.antiClockwise, OutputPorts.P12)
        actuators.SetSpeedMotor(600, OutputPorts.P16)
    } else {
        actuators.SetSpeedMotor(0, OutputPorts.P16)
    }
})
basic.forever(function () {
    basic.showNumber(pontos)
})
basic.forever(function () {
    if (sensors.infraredValue(InputPorts.P1) > 300) {
        pontos += 1
        basic.pause(2000)
    }
})
input.onLogoEvent(TouchButtonEvent.Touched, function () {
    actuators.SetAngleServoKnob(100, OutputPorts.P8)
    actuators.SetAngleServoKnob(350, OutputPorts.P8)
    actuators.SetAngleServoKnob(100, OutputPorts.P8)
})
```
## Passo 24
Insira uma pausa ``||basic:pausa (ms) 100||`` entre o primeiro e o segundo posicionamento do servo motor
e outra entre o segundo e terceiro posicionamentos. Altere o valor da primeira pausa para **1000** e o da segunda para **500**.

```blocks
let pontos = 0
actuators.SetAngleServoKnob(100, OutputPorts.P8)
basic.forever(function () {
    if (input.buttonIsPressed(Button.A)) {
        actuators.SetDirectionMotor(MotorDirection.clockwise, OutputPorts.P12)
        actuators.SetSpeedMotor(600, OutputPorts.P16)
    } else if (input.buttonIsPressed(Button.B)) {
        actuators.SetDirectionMotor(MotorDirection.antiClockwise, OutputPorts.P12)
        actuators.SetSpeedMotor(600, OutputPorts.P16)
    } else {
        actuators.SetSpeedMotor(0, OutputPorts.P16)
    }
})
basic.forever(function () {
    basic.showNumber(pontos)
})
basic.forever(function () {
    if (sensors.infraredValue(InputPorts.P1) > 300) {
        pontos += 1
        basic.pause(2000)
    }
})
input.onLogoEvent(TouchButtonEvent.Touched, function () {
    actuators.SetAngleServoKnob(100, OutputPorts.P8)
    basic.pause(1000)
    actuators.SetAngleServoKnob(350, OutputPorts.P8)
    basic.pause(500)
    actuators.SetAngleServoKnob(100, OutputPorts.P8)
})
```
## Passo 25

Agora seu código está pronto! Baixe-o para o micro:bit e teste-o. 
Os botões A e B avançam ou recuam o lançador, enquanto 
o logotipo do micro:bit aciona a ação de arremessar. No display será exibida o número de cestas já efetuadas.

```blocks
```


## Passo 26
Se necessário, confira o seu código clicando na lâmpada de dica.

```blocks
let pontos = 0
actuators.SetAngleServoKnob(100, OutputPorts.P8)
basic.forever(function () {
    if (input.buttonIsPressed(Button.A)) {
        actuators.SetDirectionMotor(MotorDirection.clockwise, OutputPorts.P12)
        actuators.SetSpeedMotor(600, OutputPorts.P16)
    } else if (input.buttonIsPressed(Button.B)) {
        actuators.SetDirectionMotor(MotorDirection.antiClockwise, OutputPorts.P12)
        actuators.SetSpeedMotor(600, OutputPorts.P16)
    } else {
        actuators.SetSpeedMotor(0, OutputPorts.P16)
    }
})
basic.forever(function () {
    basic.showNumber(pontos)
})
basic.forever(function () {
    if (sensors.infraredValue(InputPorts.P1) > 300) {
        pontos += 1
        basic.pause(2000)
    }
})
input.onLogoEvent(TouchButtonEvent.Touched, function () {
    actuators.SetAngleServoKnob(100, OutputPorts.P8)
    basic.pause(1000)
    actuators.SetAngleServoKnob(350, OutputPorts.P8)
    basic.pause(500)
    actuators.SetAngleServoKnob(100, OutputPorts.P8)
})
```



```package
fuzzyBot=github:FuzzyMakers/pxt-fuzzyMakers
```
