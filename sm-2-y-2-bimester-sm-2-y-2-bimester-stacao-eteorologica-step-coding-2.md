### @diffs true
# Estação Meteorológica

## Passo 1
Nesse tutorial, vamos programar uma estação meteorológica 
capaz de fazer a coleta e apresentação de dados de temperatura, 
luminosidade e vento. A temperatura será exibida ao pressionar
o botão A do micro:bit, a luminosidade será indicada ao pressionar o botão B,
e o vento ao tocar o logotipo no centro da placa.

## Passo 2
Para começar, verifique se a biblioteca da Smart Makers já está importada 
em seu MakeCode. Se não estiver, clique na aba **+ Extensões**, 
copie o endereço "https://github.com/FuzzyMakers/pxt-smartMakers",
cole-o no campo de pesquisa da janela que se abriu e selecione a biblioteca.

## Passo 3
Acesse o menu ``||input:Entrada||`` e adicione dois laços 
``||input:no botão A pressionado||`` em sua área de programação.
Clique na seta para alterar o botão de um deles de ``||input:botão A||`` 
para ``||input:botão B||``.

```blocks
input.onButtonPressed(Button.A, function () {
	
})
input.onButtonPressed(Button.B, function () {
	
})
basic.forever(function () {
	
})
```

## Passo 4
Vá à categoria ``||basic:Básico||`` e insira o comando ``||basic:limpar tela||``
dentro do bloco ``||input:no botão A pressionado||``.

```blocks
input.onButtonPressed(Button.A, function () {
    basic.clearScreen()
})
input.onButtonPressed(Button.B, function () {
	
})
basic.forever(function () {
	
})
```

## Passo 5
Retorne à ``||basic:Básico||`` e adicione o comando ``||basic:mostrar número 0||``
dentro de ``||input:no botão A pressionado||``.

```blocks
input.onButtonPressed(Button.A, function () {
    basic.clearScreen()
    basic.showNumber(0)
})
input.onButtonPressed(Button.B, function () {
	
})
basic.forever(function () {
	
})
```

## Passo 6
Clique na categoria ``||input:Entrada||`` e utilize o bloco
``||input:temperatura °C||`` para substituir o valor **0** do bloco
``||basic:mostrar número 0||``.

```blocks
input.onButtonPressed(Button.A, function () {
    basic.clearScreen()
    basic.showNumber(input.temperature())
})
input.onButtonPressed(Button.B, function () {
	
})
basic.forever(function () {
	
})
```

## Passo 7
Acesse a aba ``||basic:Básico||`` e adicione uma ``||basic:pausa (ms) 100||`` 
dentro do bloco ``||input:no botão A pressionado||``. Altere sua duração de
**100ms** para **1000ms** (1 segundo).

```blocks
input.onButtonPressed(Button.A, function () {
    basic.clearScreen()
    basic.showNumber(input.temperature())
    basic.pause(1000)
})
input.onButtonPressed(Button.B, function () {
	
})
basic.forever(function () {
	
})
```

## Passo 8
Vá à categoria ``||led:Led||`` e insira o bloco 
``||led:plot bar graph of 0 up to 0||`` dentro do outro bloco 
``||input:no botão B pressionado||``.

```blocks
input.onButtonPressed(Button.A, function () {
    basic.clearScreen()
    basic.showNumber(input.temperature())
    basic.pause(1000)
})
input.onButtonPressed(Button.B, function () {
    led.plotBarGraph(
    0,
    0
    )
})
basic.forever(function () {
	
})
```

## Passo 9
Volte à ``||input:Entrada||`` e selecione o bloco
``||input:nível de luz||`` para substituir o primeiro valor **0** do bloco
``||led:plot bar graph of 0 up to 0||``.

```blocks
input.onButtonPressed(Button.A, function () {
    basic.clearScreen()
    basic.showNumber(input.temperature())
    basic.pause(1000)
})
input.onButtonPressed(Button.B, function () {
    led.plotBarGraph(
    input.lightLevel(),
    0
    )
})
basic.forever(function () {
	
})
```

## Passo 10
Altere o segundo valor **0** desse bloco ``||led:plot bar graph of 0 up to 0||``
para **255**.

```blocks
input.onButtonPressed(Button.A, function () {
    basic.clearScreen()
    basic.showNumber(input.temperature())
    basic.pause(1000)
})
input.onButtonPressed(Button.B, function () {
    led.plotBarGraph(
    input.lightLevel(),
    255
    )
})
basic.forever(function () {
	
})
```

## Passo 11
Agora, certifique-se de que seu código tenha um laço ``||basic:sempre||``,
localizado no menu ``||basic:Básico||``. Em seguida, acesse a categoria 
``||loops:Loops||`` e adicione o bloco ``||loops:enquanto falso executar||``
dentro do ``||basic:sempre||``.

```blocks
input.onButtonPressed(Button.A, function () {
    basic.clearScreen()
    basic.showNumber(input.temperature())
    basic.pause(1000)
})
input.onButtonPressed(Button.B, function () {
    led.plotBarGraph(
    input.lightLevel(),
    255
    )
})
basic.forever(function () {
    while (false) {
    	
    }
})
```

## Passo 12
Volte à ``||input:Entrada||`` e selecione o bloco de bordas triangulares
``||input:logotipo é pressionado||`` para substituir o campo **falso** do bloco
``||loops:enquanto falso executar||``.

```blocks
input.onButtonPressed(Button.A, function () {
    basic.clearScreen()
    basic.showNumber(input.temperature())
    basic.pause(1000)
})
input.onButtonPressed(Button.B, function () {
    led.plotBarGraph(
    input.lightLevel(),
    255
    )
})
basic.forever(function () {
    while (input.logoIsPressed()) {
    	
    }
})
```

## Passo 13
Dentro do ``||loops:executar||``, adicione outro 
``||led:plot bar graph of 0 up to 0||``.

```blocks
input.onButtonPressed(Button.A, function () {
    basic.clearScreen()
    basic.showNumber(input.temperature())
    basic.pause(1000)
})
input.onButtonPressed(Button.B, function () {
    led.plotBarGraph(
    input.lightLevel(),
    255
    )
})
basic.forever(function () {
    while (input.logoIsPressed()) {
        led.plotBarGraph(
        0,
        0
        )
    }
})
```

## Passo 14
Clique na aba ``||sensors:Sensores||`` e selecione o bloco 
``||sensors:Valor do sensor de som na porta P2||`` para substituir o primeiro
valor **0** do bloco ``||led:plot bar graph||``.

```blocks
input.onButtonPressed(Button.A, function () {
    basic.clearScreen()
    basic.showNumber(input.temperature())
    basic.pause(1000)
})
input.onButtonPressed(Button.B, function () {
    led.plotBarGraph(
    input.lightLevel(),
    255
    )
})
basic.forever(function () {
    while (input.logoIsPressed()) {
        led.plotBarGraph(
        sensors.soundSensorValue(InputPorts.P2),
        0
        )
    }
})
```

## Passo 15
Altere a porta desse bloco de **P2** para **P1** e o segundo valor **0**
para **1023**.

```blocks
input.onButtonPressed(Button.A, function () {
    basic.clearScreen()
    basic.showNumber(input.temperature())
    basic.pause(1000)
})
input.onButtonPressed(Button.B, function () {
    led.plotBarGraph(
    input.lightLevel(),
    255
    )
})
basic.forever(function () {
    while (input.logoIsPressed()) {
        led.plotBarGraph(
        sensors.soundSensorValue(InputPorts.P1),
        1023
        )
    }
})
```

## Passo 16

Agora seu código está pronto! Baixe-o para o micro:bit e teste-o. 
Pressione o botão A para visualizar a temperatura, o botão B para acompanhar
a luminosidade e o logotipo para medir o vento através do sensor de som.

```blocks
```

## Passo 17
Se necessário, confira o seu código clicando na lâmpada de dica.

```blocks
input.onButtonPressed(Button.A, function () {
    basic.clearScreen()
    basic.showNumber(input.temperature())
    basic.pause(1000)
})
input.onButtonPressed(Button.B, function () {
    led.plotBarGraph(
    input.lightLevel(),
    255
    )
})
basic.forever(function () {
    while (input.logoIsPressed()) {
        led.plotBarGraph(
        sensors.soundSensorValue(InputPorts.P1),
        1023
        )
    }
})
```

```package
fuzzyBot=github:FuzzyMakers/pxt-fuzzyMakers
```
