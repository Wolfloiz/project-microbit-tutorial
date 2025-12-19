### @diffs true
# Bipedismo

## Passo 1
Neste tutorial, vamos programar um animal que pode andar para frente e para trás sobre dois apoios.
No display, é exibida a intensidade da velocidade.

## Passo 2
Para começar, verifique se a biblioteca da Smart Makers já está importada 
em seu MakeCode. Se não estiver, clique na aba **+ Extensões**, 
copie o endereço "https://github.com/FuzzyMakers/pxt-smartMakers",
cole-o no campo de pesquisa da janela que se abriu e selecione a biblioteca.

## Passo 3
Acesse o menu ``||variables:Variáveis||`` e clique em 
**"Fazer uma variável..."**. Crie uma variável chamada
``||variables:velocidade||``. Em seguida, arraste o bloco ``||variables:definir velocidade para 0||`` 
para o bloco ``||basic:no iniciar||``.

```blocks
let velocidade = 0

```


## Passo 4
Vá até a aba ``||led:Led||``, clique no bloco ``||led:plot bar graph of 0 up to 0||`` 
e insira-o no laço ``||basic:sempre||``.
```blocks
let velocidade = 0
basic.forever(function () {
    led.plotBarGraph(
    0,
    0
    )
})

```

## Passo 5

Em seguida, atualize os campos do bloco:
na categoria ``||variables:Variáveis||``,
pegue a variável ``||variables:velocidade||`` e coloque-a no primeiro campo. 
Depois, atualize o valor do segundo campo para **1000**.

```blocks
let velocidade = 0
basic.forever(function () {
    led.plotBarGraph(
    velocidade,
    1000
    )
})

```

## Passo 6
No menu ``||input:Entrada||`` busque o bloco ``||input:no logotipo pressionado||`` e adicione-o
à área de programação. 



```blocks
input.onLogoEvent(TouchButtonEvent.Pressed, function () {
	
})
let velocidade = 0
basic.forever(function () {
    led.plotBarGraph(
    velocidade,
    1000
    )
})

```

## Passo 7
Acesse a categoria ``||logic:Lógica||``, pegue a condicional ``||logic:se então||``
e insira-a dentro do bloco ``||input:no logotipo pressionado||``. 

```blocks
input.onLogoEvent(TouchButtonEvent.Pressed, function () {
    if (true) {
    	
    }
})
let velocidade = 0
basic.forever(function () {
    led.plotBarGraph(
    velocidade,
    1000
    )
})

```

## Passo 8

Volte ao menu ``||logic:Lógica||``, pegue o comparador ``||logic:0 < 0||``
e substitua a condição **verdadeiro** da condicional.

```blocks
input.onLogoEvent(TouchButtonEvent.Pressed, function () {
    if (0 < 0) {
    	
    }
})
let velocidade = 0
basic.forever(function () {
    led.plotBarGraph(
    velocidade,
    1000
    )
})

```

## Passo 9
Agora atualize os campos do comparador. Vá até a aba ``||variables:Variáveis||``,
clique no bloco ``||variables:velocidade||`` e troque 
o primeiro **0** do comparador. Mude o valor do segundo **0** para **400** 
e o sinal da comparação para **>=**.

```blocks
input.onLogoEvent(TouchButtonEvent.Pressed, function () {
    if (velocidade >= 400) {
    	
    }
})
let velocidade = 0
basic.forever(function () {
    led.plotBarGraph(
    velocidade,
    1000
    )
})
```

## Passo 10
Na categoria ``||variables:Variáveis||``, pegue o bloco ``||variables:alterar velocidade por 1||``
e posicione-o dentro do ``||logic:se então||``.
Mude o incremento da variável de **1** para **-100**.

```blocks
input.onLogoEvent(TouchButtonEvent.Pressed, function () {
    if (velocidade >= 400) {
        velocidade += -100
    }
})
let velocidade = 0
basic.forever(function () {
    led.plotBarGraph(
    velocidade,
    1000
    )
})

```


## Passo 11

Acesse o menu ``||actuators:Atuadores||``, adicione o bloco
``||actuators:Motor CC, definir velocidade 0 na porta P8||``
dentro do ``||logic:se então||``.


```blocks
input.onLogoEvent(TouchButtonEvent.Pressed, function () {
    if (velocidade >= 400) {
        velocidade += -100
        actuators.SetSpeedMotor(0, OutputPorts.P8)
    }
})
let velocidade = 0
basic.forever(function () {
    led.plotBarGraph(
    velocidade,
    1000
    )
})

```

## Passo 12

Em seguida, atualize o valor da velocidade nesse bloco de **0** para a própria 
variável ``||variables:velocidade||`` e altere a porta de ``||actuators:P8||``
para ``||actuators:P12||``.

```blocks
input.onLogoEvent(TouchButtonEvent.Pressed, function () {
    if (velocidade >= 400) {
        velocidade += -100
        actuators.SetSpeedMotor(velocidade, OutputPorts.P12)
    }
})
let velocidade = 0
basic.forever(function () {
    led.plotBarGraph(
    velocidade,
    1000
    )
})
```

## Passo 13

Duplique o bloco ``||input:no logotipo pressionado||`` alterando o comando para 
``||input:no logotipo toque longo||``.

```blocks
input.onLogoEvent(TouchButtonEvent.Pressed, function () {
    if (velocidade >= 400) {
        velocidade += -100
        actuators.SetSpeedMotor(velocidade, OutputPorts.P12)
    }
})
input.onLogoEvent(TouchButtonEvent.LongPressed, function () {
    if (velocidade >= 400) {
        velocidade += -100
        actuators.SetSpeedMotor(velocidade, OutputPorts.P12)
    }
})
let velocidade = 0
basic.forever(function () {
    led.plotBarGraph(
    velocidade,
    1000
    )
})


```
## Passo 14

Em seguida, altere o sinal e o valor da condicional para **<=** e **800** respectivamente.
Depois transforme o valor negativo **-100** para **100** positivo no bloco de 
alteração da ``||variables:variável||``. 

```blocks
input.onLogoEvent(TouchButtonEvent.Pressed, function () {
    if (velocidade >= 400) {
        velocidade += -100
        actuators.SetSpeedMotor(velocidade, OutputPorts.P12)
    }
})
input.onLogoEvent(TouchButtonEvent.LongPressed, function () {
    if (velocidade <= 800) {
        velocidade += 100
        actuators.SetSpeedMotor(velocidade, OutputPorts.P12)
    }
})
let velocidade = 0
basic.forever(function () {
    led.plotBarGraph(
    velocidade,
    1000
    )
})
```

## Passo 15

Na aba ``||input:Entrada||`` clique em um bloco ``||input: no botão A pressionado||``, 
adicione-o ao código.

```blocks
input.onLogoEvent(TouchButtonEvent.Pressed, function () {
    if (velocidade >= 400) {
        velocidade += -100
        actuators.SetSpeedMotor(velocidade, OutputPorts.P12)
    }
})
input.onButtonPressed(Button.A, function () {
	
})
input.onLogoEvent(TouchButtonEvent.LongPressed, function () {
    if (velocidade <= 800) {
        velocidade += 100
        actuators.SetSpeedMotor(velocidade, OutputPorts.P12)
    }
})
let velocidade = 0
basic.forever(function () {
    led.plotBarGraph(
    velocidade,
    1000
    )
})

```

## Passo 16

Copie a definição de variável ``||variables:definir velocidade para 0||`` 
inserida no bloco ``||basic:no iniciar||`` anteriormente. Cole essa cópia 
dentro do bloco ``||input: no botão A pressionado||``.
Edite seu valor de **0** para **400**.


```blocks
input.onLogoEvent(TouchButtonEvent.Pressed, function () {
    if (velocidade >= 400) {
        velocidade += -100
        actuators.SetSpeedMotor(velocidade, OutputPorts.P12)
    }
})
input.onButtonPressed(Button.A, function () {
    velocidade = 400
})
input.onLogoEvent(TouchButtonEvent.LongPressed, function () {
    if (velocidade <= 800) {
        velocidade += 100
        actuators.SetSpeedMotor(velocidade, OutputPorts.P12)
    }
})
let velocidade = 0
basic.forever(function () {
    led.plotBarGraph(
    velocidade,
    1000
    )
})

```

## Passo 17

Acesse o menu ``||actuators:Atuadores||``, adicione os blocos
``||actuators:Motor CC, definir velocidade 0 na porta P8||`` e 
``||actuators:Motor CC, definir direção para Sentido horário na porta P8||``
dentro do ``||input:no botão A pressionado||``.

```blocks
input.onLogoEvent(TouchButtonEvent.Pressed, function () {
    if (velocidade >= 400) {
        velocidade += -100
        actuators.SetSpeedMotor(velocidade, OutputPorts.P12)
    }
})
input.onButtonPressed(Button.A, function () {
    velocidade = 400
    actuators.SetSpeedMotor(0, OutputPorts.P8)
    actuators.SetDirectionMotor(MotorDirection.clockwise, OutputPorts.P8)
})
input.onLogoEvent(TouchButtonEvent.LongPressed, function () {
    if (velocidade <= 800) {
        velocidade += 100
        actuators.SetSpeedMotor(velocidade, OutputPorts.P12)
    }
})
let velocidade = 0
basic.forever(function () {
    led.plotBarGraph(
    velocidade,
    1000
    )
})


```

## Passo 18
Modifique o valor de velocidade do primeiro bloco para ``||variables:velocidade||`` 
e a porta para ``||actuators:P12||``.

```blocks
input.onLogoEvent(TouchButtonEvent.Pressed, function () {
    if (velocidade >= 400) {
        velocidade += -100
        actuators.SetSpeedMotor(velocidade, OutputPorts.P12)
    }
})
input.onButtonPressed(Button.A, function () {
    velocidade = 400
    actuators.SetSpeedMotor(velocidade, OutputPorts.P12)
    actuators.SetDirectionMotor(MotorDirection.clockwise, OutputPorts.P8)
})
input.onLogoEvent(TouchButtonEvent.LongPressed, function () {
    if (velocidade <= 800) {
        velocidade += 100
        actuators.SetSpeedMotor(velocidade, OutputPorts.P12)
    }
})
let velocidade = 0
basic.forever(function () {
    led.plotBarGraph(
    velocidade,
    1000
    )
})

```

## Passo 19

Duplique o bloco ``||input:no Botão A pressionado||`` alterando o comando para 
``||input:no Botão B pressionado||``.

```blocks
input.onLogoEvent(TouchButtonEvent.Pressed, function () {
    if (velocidade >= 400) {
        velocidade += -100
        actuators.SetSpeedMotor(velocidade, OutputPorts.P12)
    }
})
input.onButtonPressed(Button.A, function () {
    velocidade = 400
    actuators.SetSpeedMotor(velocidade, OutputPorts.P12)
    actuators.SetDirectionMotor(MotorDirection.clockwise, OutputPorts.P8)
})
input.onLogoEvent(TouchButtonEvent.LongPressed, function () {
    if (velocidade <= 800) {
        velocidade += 100
        actuators.SetSpeedMotor(velocidade, OutputPorts.P12)
    }
})
let velocidade = 0
basic.forever(function () {
    led.plotBarGraph(
    velocidade,
    1000
    )
})
input.onButtonPressed(Button.B, function () {
    velocidade = 400
    actuators.SetSpeedMotor(velocidade, OutputPorts.P12)
    actuators.SetDirectionMotor(MotorDirection.clockwise, OutputPorts.P8)
})
```
## Passo 20
Em seguida, altere o sentido da rotação do motor nesse novo bloco para 
``||actuators:anti-horário||``.

```blocks
input.onLogoEvent(TouchButtonEvent.Pressed, function () {
    if (velocidade >= 400) {
        velocidade += -100
        actuators.SetSpeedMotor(velocidade, OutputPorts.P12)
    }
})
input.onButtonPressed(Button.A, function () {
    velocidade = 400
    actuators.SetSpeedMotor(velocidade, OutputPorts.P12)
    actuators.SetDirectionMotor(MotorDirection.clockwise, OutputPorts.P8)
})
input.onLogoEvent(TouchButtonEvent.LongPressed, function () {
    if (velocidade <= 800) {
        velocidade += 100
        actuators.SetSpeedMotor(velocidade, OutputPorts.P12)
    }
})
let velocidade = 0
basic.forever(function () {
    led.plotBarGraph(
    velocidade,
    1000
    )
})
input.onButtonPressed(Button.B, function () {
    velocidade = 400
    actuators.SetSpeedMotor(velocidade, OutputPorts.P12)
    actuators.SetDirectionMotor(MotorDirection.antiClockwise, OutputPorts.P8)
})
```

## Passo 21

Volte ao menu ``||input:Entrada||`` e busque o bloco ``||input:ao som do alto||``
para colocar na área de programação.


```blocks
input.onLogoEvent(TouchButtonEvent.Pressed, function () {
    if (velocidade >= 400) {
        velocidade += -100
        actuators.SetSpeedMotor(velocidade, OutputPorts.P12)
    }
})
input.onButtonPressed(Button.A, function () {
    velocidade = 400
    actuators.SetSpeedMotor(velocidade, OutputPorts.P12)
    actuators.SetDirectionMotor(MotorDirection.clockwise, OutputPorts.P8)
})
input.onLogoEvent(TouchButtonEvent.LongPressed, function () {
    if (velocidade <= 800) {
        velocidade += 100
        actuators.SetSpeedMotor(velocidade, OutputPorts.P12)
    }
})
input.onSound(DetectedSound.Loud, function () {
	
})
let velocidade = 0
basic.forever(function () {
    led.plotBarGraph(
    velocidade,
    1000
    )
})
input.onButtonPressed(Button.B, function () {
    velocidade = 400
    actuators.SetSpeedMotor(velocidade, OutputPorts.P12)
    actuators.SetDirectionMotor(MotorDirection.antiClockwise, OutputPorts.P8)
})
```

## Passo 22
Copie a definição de variável ``||variables:definir velocidade para 0||`` 
inserida no bloco ``||basic:no iniciar||`` anteriormente. 
Cole essa cópia no bloco ``||input: ao som do alto||``.

```blocks
input.onLogoEvent(TouchButtonEvent.Pressed, function () {
    if (velocidade >= 400) {
        velocidade += -100
        actuators.SetSpeedMotor(velocidade, OutputPorts.P12)
    }
})
input.onButtonPressed(Button.A, function () {
    velocidade = 400
    actuators.SetSpeedMotor(velocidade, OutputPorts.P12)
    actuators.SetDirectionMotor(MotorDirection.clockwise, OutputPorts.P8)
})
input.onLogoEvent(TouchButtonEvent.LongPressed, function () {
    if (velocidade <= 800) {
        velocidade += 100
        actuators.SetSpeedMotor(velocidade, OutputPorts.P12)
    }
})
input.onSound(DetectedSound.Loud, function () {
    velocidade = 0
})
input.onButtonPressed(Button.B, function () {
    velocidade = 400
    actuators.SetSpeedMotor(velocidade, OutputPorts.P12)
    actuators.SetDirectionMotor(MotorDirection.antiClockwise, OutputPorts.P8)
})
let velocidade = 0
basic.forever(function () {
    led.plotBarGraph(
    velocidade,
    1000
    )
})
```

## Passo 23
Acesse o menu ``||actuators:Atuadores||`` e arraste o bloco
``||actuators:Motor CC, parar na porta P8||``
para dentro do bloco ``||input: ao som do alto||``. 
Modifique a porta de ``||actuators:P8||`` para ``||actuators:P12||``.

```blocks
input.onLogoEvent(TouchButtonEvent.Pressed, function () {
    if (velocidade >= 400) {
        velocidade += -100
        actuators.SetSpeedMotor(velocidade, OutputPorts.P12)
    }
})
input.onButtonPressed(Button.A, function () {
    velocidade = 400
    actuators.SetSpeedMotor(velocidade, OutputPorts.P12)
    actuators.SetDirectionMotor(MotorDirection.clockwise, OutputPorts.P8)
})
input.onLogoEvent(TouchButtonEvent.LongPressed, function () {
    if (velocidade <= 800) {
        velocidade += 100
        actuators.SetSpeedMotor(velocidade, OutputPorts.P12)
    }
})
input.onSound(DetectedSound.Loud, function () {
    velocidade = 0
    actuators.StopMotor(OutputPorts.P12)
})
input.onButtonPressed(Button.B, function () {
    velocidade = 400
    actuators.SetSpeedMotor(velocidade, OutputPorts.P12)
    actuators.SetDirectionMotor(MotorDirection.antiClockwise, OutputPorts.P8)
})
let velocidade = 0
basic.forever(function () {
    led.plotBarGraph(
    velocidade,
    1000
    )
})

```


## Passo 24

Agora seu código está pronto! Baixe-o para o micro:bit e teste-o. Use os botões A e B do micro:bit para mover o bípede para frente e para trás,
ao pressionar o logotipo a velocidade do animal diminui, enquanto ao segurar o logotipo por mais tempo a velocidade aumenta. 
Bata palmas perto do micro:bit para interromper o movimento.
```blocks
```


## Passo 25
Se necessário, confira o seu código clicando na lâmpada de dica.

```blocks
input.onLogoEvent(TouchButtonEvent.Pressed, function () {
    if (velocidade >= 400) {
        velocidade += -100
        actuators.SetSpeedMotor(velocidade, OutputPorts.P12)
    }
})
input.onButtonPressed(Button.A, function () {
    velocidade = 400
    actuators.SetSpeedMotor(velocidade, OutputPorts.P12)
    actuators.SetDirectionMotor(MotorDirection.clockwise, OutputPorts.P8)
})
input.onLogoEvent(TouchButtonEvent.LongPressed, function () {
    if (velocidade <= 800) {
        velocidade += 100
        actuators.SetSpeedMotor(velocidade, OutputPorts.P12)
    }
})
input.onSound(DetectedSound.Loud, function () {
    velocidade = 0
    actuators.StopMotor(OutputPorts.P12)
})
input.onButtonPressed(Button.B, function () {
    velocidade = 400
    actuators.SetSpeedMotor(velocidade, OutputPorts.P12)
    actuators.SetDirectionMotor(MotorDirection.antiClockwise, OutputPorts.P8)
})
let velocidade = 0
velocidade = 0
basic.forever(function () {
    led.plotBarGraph(
    velocidade,
    1000
    )
})

```



```package
fuzzyBot=github:FuzzyMakers/pxt-fuzzyMakers
```
