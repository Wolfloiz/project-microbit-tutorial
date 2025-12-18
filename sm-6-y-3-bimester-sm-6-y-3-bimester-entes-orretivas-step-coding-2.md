### @diffs true
# Lentes Corretivas

## Passo 1
Neste tutorial, vamos programar o funcionamento do modelo de foróptero, 
um instrumento utilizado para testar a acuidade visual. Seremos capazes de 
ajustar suas lentes com o potenciômetro controlando o servomotor. O botão A 
do micro:bit será responsável por verificar a lente usada, enquanto o botão B
verifica o tipo de falha visual (hipermetropia ou miopia). Por fim, o logotipo
será usado para testar a combinação de lente e falha visual nos indicando se 
a associação está correta ou não.

## Passo 2
Para começar, verifique se a biblioteca da Smart Makers já está importada 
em seu MakeCode. Se não estiver, clique na aba **+ Extensões**, 
copie o endereço "https://github.com/FuzzyMakers/pxt-smartMakers",
cole-o no campo de pesquisa da janela que se abriu e selecione a biblioteca.

## Passo 3
Acesse o menu ``||input:Entrada||`` e adicione o bloco 
``||input:no botão A pressionado||`` na área de programação.

```blocks
input.onButtonPressed(Button.A, function () {
	
})
basic.forever(function () {
	
})
```

## Passo 4
Acesse a aba ``||logic:Lógica||`` e adicione o bloco ``||logic:se então senão||`` 
dentro do bloco ``||input:no botão A pressionado||``.

```blocks
input.onButtonPressed(Button.A, function () {
    if (true) {
    	
    } else {
    	
    }
})
basic.forever(function () {
	
})
```

## Passo 5
Retorne à ``||logic:Lógica||`` e utilize o bloco comparador 
``||logic:0 < 0||`` para substituir o campo **verdadeiro** do bloco 
``||logic:se então senão||``.

```blocks
input.onButtonPressed(Button.A, function () {
    if (0 < 0) {
    	
    } else {
    	
    }
})
basic.forever(function () {
	
})
```

## Passo 6
Acesse o menu ``||sensors:Sensores||`` e selecione o bloco 
``||sensors:Valor do potenciômetro na porta P2||`` para substituir o valor **0**
do primeiro campo do comparador. Antes de prosseguir, altere a porta de **P2** 
para **P1**.

```blocks
input.onButtonPressed(Button.A, function () {
    if (sensors.dimmerValue(InputPorts.P1) < 0) {
    	
    } else {
    	
    }
})
basic.forever(function () {
	
})
```

## Passo 7
Clique na seta do comparador para modificar o sinal de **<** para **<=**. Em 
seguida, altere o segundo campo do comparador de **0** para **500**.

```blocks
input.onButtonPressed(Button.A, function () {
    if (sensors.dimmerValue(InputPorts.P1) <= 500) {
    	
    } else {
    	
    }
})
basic.forever(function () {
	
})
```

## Passo 8
Agora, dentro do ``||logic:então||``, adicione os comandos 
``||basic:mostrar leds||``, ``||basic:pausa (ms) 100||`` e 
``||basic:limpar tela||``, todos presentes na categoria ``||basic:Básico||``.

```blocks
input.onButtonPressed(Button.A, function () {
    if (sensors.dimmerValue(InputPorts.P1) <= 500) {
        basic.showLeds(`
            . . . . .
            . . . . .
            . . . . .
            . . . . .
            . . . . .
            `)
        basic.pause(100)
        basic.clearScreen()
    } else {
    	
    }
})
basic.forever(function () {
	
})
```

## Passo 9
Clique nos LEDs que devem acender no bloco ``||basic:mostrar leds||`` para exibir
uma letra **"O"**. Em seguida, altere a duração da ``||basic:pausa||`` de 
**100ms** para **2000ms** (2 segundos).

```blocks
input.onButtonPressed(Button.A, function () {
    if (sensors.dimmerValue(InputPorts.P1) <= 500) {
        basic.showLeds(`
            . . # . .
            . # # # .
            . # # # .
            . # # # .
            . . # . .
            `)
        basic.pause(2000)
        basic.clearScreen()
    } else {
    	
    }
})
basic.forever(function () {
	
})
```

## Passo 10
Agora, dentro do ``||logic:senão||``, também adicione os três comandos 
``||basic:mostrar leds||``, ``||basic:pausa (ms)||`` e 
``||basic:limpar tela||``, todos presentes na categoria ``||basic:Básico||``.

```blocks
input.onButtonPressed(Button.A, function () {
    if (sensors.dimmerValue(InputPorts.P1) <= 500) {
        basic.showLeds(`
            . . # . .
            . # # # .
            . # # # .
            . # # # .
            . . # . .
            `)
        basic.pause(2000)
        basic.clearScreen()
    } else {
        basic.showLeds(`
            . . . . .
            . . . . .
            . . . . .
            . . . . .
            . . . . .
            `)
        basic.pause(100)
        basic.clearScreen()
    }
})
basic.forever(function () {
	
})
```

## Passo 11
Edite quais LEDs devem acender no bloco ``||basic:mostrar leds||`` para exibir
uma letra **"I"**. Em seguida, altere a duração da ``||basic:pausa||`` de 
**100ms** para **2000ms** (2 segundos).

```blocks
input.onButtonPressed(Button.A, function () {
    if (sensors.dimmerValue(InputPorts.P1) <= 500) {
        basic.showLeds(`
            . . # . .
            . # # # .
            . # # # .
            . # # # .
            . . # . .
            `)
        basic.pause(2000)
        basic.clearScreen()
    } else {
        basic.showLeds(`
            . # # # .
            . . # . .
            . . # . .
            . . # . .
            . # # # .
            `)
        basic.pause(2000)
        basic.clearScreen()
    }
})
basic.forever(function () {
	
})
```

## Passo 12
Retorne ao menu ``||input:Entrada||`` e adicione o bloco 
``||input:no botão A pressionado||`` na área de programação. Clique na seta 
desse bloco para alterar de ``||input:botão A||`` para ``||input:botão B||``.  

```blocks
input.onButtonPressed(Button.A, function () {
    if (sensors.dimmerValue(InputPorts.P1) <= 500) {
        basic.showLeds(`
            . . # . .
            . # # # .
            . # # # .
            . # # # .
            . . # . .
            `)
        basic.pause(2000)
        basic.clearScreen()
    } else {
        basic.showLeds(`
            . # # # .
            . . # . .
            . . # . .
            . . # . .
            . # # # .
            `)
        basic.pause(2000)
        basic.clearScreen()
    }
})
input.onButtonPressed(Button.B, function () {
	
})
basic.forever(function () {
	
})
```

## Passo 13
Acesse a aba ``||logic:Lógica||`` e adicione o bloco ``||logic:se então senão||`` 
dentro desse novo bloco ``||input:no botão B pressionado||``.

```blocks
input.onButtonPressed(Button.A, function () {
    if (sensors.dimmerValue(InputPorts.P1) <= 500) {
        basic.showLeds(`
            . . # . .
            . # # # .
            . # # # .
            . # # # .
            . . # . .
            `)
        basic.pause(2000)
        basic.clearScreen()
    } else {
        basic.showLeds(`
            . # # # .
            . . # . .
            . . # . .
            . . # . .
            . # # # .
            `)
        basic.pause(2000)
        basic.clearScreen()
    }
})
input.onButtonPressed(Button.B, function () {
    if (true) {
    	
    } else {
    	
    }
})
basic.forever(function () {
	
})
```

## Passo 14
Retorne à ``||logic:Lógica||`` e utilize o bloco comparador 
``||logic:0 < 0||`` para substituir o campo **verdadeiro** do bloco 
``||logic:se então senão||``.

```blocks
input.onButtonPressed(Button.A, function () {
    if (sensors.dimmerValue(InputPorts.P1) <= 500) {
        basic.showLeds(`
            . . # . .
            . # # # .
            . # # # .
            . # # # .
            . . # . .
            `)
        basic.pause(2000)
        basic.clearScreen()
    } else {
        basic.showLeds(`
            . # # # .
            . . # . .
            . . # . .
            . . # . .
            . # # # .
            `)
        basic.pause(2000)
        basic.clearScreen()
    }
})
input.onButtonPressed(Button.B, function () {
    if (0 < 0) {
    	
    } else {
    	
    }
})
basic.forever(function () {
	
})
```

## Passo 15
Acesse o menu ``||sensors:Sensores||`` e selecione o bloco 
``||sensors:Valor do sensor infravermelho na porta P2||`` para substituir o 
valor **0** no primeiro campo do comparador.

```blocks
input.onButtonPressed(Button.A, function () {
    if (sensors.dimmerValue(InputPorts.P1) <= 500) {
        basic.showLeds(`
            . . # . .
            . # # # .
            . # # # .
            . # # # .
            . . # . .
            `)
        basic.pause(2000)
        basic.clearScreen()
    } else {
        basic.showLeds(`
            . # # # .
            . . # . .
            . . # . .
            . . # . .
            . # # # .
            `)
        basic.pause(2000)
        basic.clearScreen()
    }
})
input.onButtonPressed(Button.B, function () {
    if (sensors.infraredValue(InputPorts.P2) < 0) {
    	
    } else {
    	
    }
})
basic.forever(function () {
	
})
```

## Passo 16
Clique na seta do comparador para modificar o sinal de **<** para **>=**. Em 
seguida, altere o segundo campo do comparador de **0** para **250**.

```blocks
input.onButtonPressed(Button.A, function () {
    if (sensors.dimmerValue(InputPorts.P1) <= 500) {
        basic.showLeds(`
            . . # . .
            . # # # .
            . # # # .
            . # # # .
            . . # . .
            `)
        basic.pause(2000)
        basic.clearScreen()
    } else {
        basic.showLeds(`
            . # # # .
            . . # . .
            . . # . .
            . . # . .
            . # # # .
            `)
        basic.pause(2000)
        basic.clearScreen()
    }
})
input.onButtonPressed(Button.B, function () {
    if (sensors.infraredValue(InputPorts.P2) >= 250) {
    	
    } else {
    	
    }
})
basic.forever(function () {
	
})
```

## Passo 17
Feito isso, adicione um comando ``||basic:mostrar string||`` dentro do 
``||logic:então||`` e outro dentro do ``||logic:senão||``. 

```blocks
input.onButtonPressed(Button.A, function () {
    if (sensors.dimmerValue(InputPorts.P1) <= 500) {
        basic.showLeds(`
            . . # . .
            . # # # .
            . # # # .
            . # # # .
            . . # . .
            `)
        basic.pause(2000)
        basic.clearScreen()
    } else {
        basic.showLeds(`
            . # # # .
            . . # . .
            . . # . .
            . . # . .
            . # # # .
            `)
        basic.pause(2000)
        basic.clearScreen()
    }
})
input.onButtonPressed(Button.B, function () {
    if (sensors.infraredValue(InputPorts.P2) >= 250) {
        basic.showString("Hello!")
    } else {
        basic.showString("Hello!")
    }
})
basic.forever(function () {
	
})
```

## Passo 18
Modifique os textos exibidos de **"Hello!"** para **"Hipermetropia"** dentro do
``||logic:então||`` e **"Miopia"** dentro do ``||logic:senão||``. 

```blocks
input.onButtonPressed(Button.A, function () {
    if (sensors.dimmerValue(InputPorts.P1) <= 500) {
        basic.showLeds(`
            . . # . .
            . # # # .
            . # # # .
            . # # # .
            . . # . .
            `)
        basic.pause(2000)
        basic.clearScreen()
    } else {
        basic.showLeds(`
            . # # # .
            . . # . .
            . . # . .
            . . # . .
            . # # # .
            `)
        basic.pause(2000)
        basic.clearScreen()
    }
})
input.onButtonPressed(Button.B, function () {
    if (sensors.infraredValue(InputPorts.P2) >= 250) {
        basic.showString("Hipermetropia")
    } else {
        basic.showString("Miopia")
    }
})
basic.forever(function () {
	
})
```

## Passo 19
Retorne ao menu ``||input:Entrada||`` e adicione o bloco 
``||input:no logotipo pressionado||`` na área de programação.

```blocks
input.onLogoEvent(TouchButtonEvent.Pressed, function () {
	
})
input.onButtonPressed(Button.A, function () {
    if (sensors.dimmerValue(InputPorts.P1) <= 500) {
        basic.showLeds(`
            . . # . .
            . # # # .
            . # # # .
            . # # # .
            . . # . .
            `)
        basic.pause(2000)
        basic.clearScreen()
    } else {
        basic.showLeds(`
            . # # # .
            . . # . .
            . . # . .
            . . # . .
            . # # # .
            `)
        basic.pause(2000)
        basic.clearScreen()
    }
})
input.onButtonPressed(Button.B, function () {
    if (sensors.infraredValue(InputPorts.P2) >= 250) {
        basic.showString("Hipermetropia")
    } else {
        basic.showString("Miopia")
    }
})
basic.forever(function () {
	
})
```

## Passo 20
Acesse a aba ``||logic:Lógica||`` e adicione o bloco ``||logic:se então senão||`` 
dentro desse novo bloco ``||input:no logotipo pressionado||``.

```blocks
input.onLogoEvent(TouchButtonEvent.Pressed, function () {
    if (true) {
    	
    } else {
    	
    }
})
input.onButtonPressed(Button.A, function () {
    if (sensors.dimmerValue(InputPorts.P1) <= 500) {
        basic.showLeds(`
            . . # . .
            . # # # .
            . # # # .
            . # # # .
            . . # . .
            `)
        basic.pause(2000)
        basic.clearScreen()
    } else {
        basic.showLeds(`
            . # # # .
            . . # . .
            . . # . .
            . . # . .
            . # # # .
            `)
        basic.pause(2000)
        basic.clearScreen()
    }
})
input.onButtonPressed(Button.B, function () {
    if (sensors.infraredValue(InputPorts.P2) >= 250) {
        basic.showString("Hipermetropia")
    } else {
        basic.showString("Miopia")
    }
})
basic.forever(function () {
	
})
```

## Passo 21
Retorne à ``||logic:Lógica||`` e utilize o bloco comparador 
``||logic:0 = 0||`` para substituir o campo **verdadeiro** do bloco 
``||logic:se então senão||``.

```blocks
input.onLogoEvent(TouchButtonEvent.Pressed, function () {
    if (0 == 0) {
    	
    } else {
    	
    }
})
input.onButtonPressed(Button.A, function () {
    if (sensors.dimmerValue(InputPorts.P1) <= 500) {
        basic.showLeds(`
            . . # . .
            . # # # .
            . # # # .
            . # # # .
            . . # . .
            `)
        basic.pause(2000)
        basic.clearScreen()
    } else {
        basic.showLeds(`
            . # # # .
            . . # . .
            . . # . .
            . . # . .
            . # # # .
            `)
        basic.pause(2000)
        basic.clearScreen()
    }
})
input.onButtonPressed(Button.B, function () {
    if (sensors.infraredValue(InputPorts.P2) >= 250) {
        basic.showString("Hipermetropia")
    } else {
        basic.showString("Miopia")
    }
})
basic.forever(function () {
	
})
```

## Passo 22
Acesse o menu ``||variables:Variáveis||`` e clique em 
**"Fazer uma variável..."**. Crie duas variáveis chamadas 
``||variables:falha||`` e ``||variables:lente||``. Em seguida, utilize os blocos
dessas variáveis ``||variables:falha||`` e ``||variables:lente||`` para 
substituir ambos os campos do comparador.

```blocks
input.onLogoEvent(TouchButtonEvent.Pressed, function () {
    let lente = 0
    let falha = 0
    if (falha == lente) {
    	
    } else {
    	
    }
})
input.onButtonPressed(Button.A, function () {
    if (sensors.dimmerValue(InputPorts.P1) <= 500) {
        basic.showLeds(`
            . . # . .
            . # # # .
            . # # # .
            . # # # .
            . . # . .
            `)
        basic.pause(2000)
        basic.clearScreen()
    } else {
        basic.showLeds(`
            . # # # .
            . . # . .
            . . # . .
            . . # . .
            . # # # .
            `)
        basic.pause(2000)
        basic.clearScreen()
    }
})
input.onButtonPressed(Button.B, function () {
    if (sensors.infraredValue(InputPorts.P2) >= 250) {
        basic.showString("Hipermetropia")
    } else {
        basic.showString("Miopia")
    }
})
basic.forever(function () {
	
})
```

## Passo 23
Agora, dentro do ``||logic:então||``, adicione um comando 
``||basic:mostrar ícone||``, localizado na categoria ``||basic:Básico||``.
Clique na seta para alterar o símbolo de um **coração** para um **check**.

```blocks
input.onLogoEvent(TouchButtonEvent.Pressed, function () {
    let lente = 0
    let falha = 0
    if (falha == lente) {
        basic.showIcon(IconNames.Yes)
    } else {
    	
    }
})
input.onButtonPressed(Button.A, function () {
    if (sensors.dimmerValue(InputPorts.P1) <= 500) {
        basic.showLeds(`
            . . # . .
            . # # # .
            . # # # .
            . # # # .
            . . # . .
            `)
        basic.pause(2000)
        basic.clearScreen()
    } else {
        basic.showLeds(`
            . # # # .
            . . # . .
            . . # . .
            . . # . .
            . # # # .
            `)
        basic.pause(2000)
        basic.clearScreen()
    }
})
input.onButtonPressed(Button.B, function () {
    if (sensors.infraredValue(InputPorts.P2) >= 250) {
        basic.showString("Hipermetropia")
    } else {
        basic.showString("Miopia")
    }
})
basic.forever(function () {
	
})
```

## Passo 24
Acesse o menu ``||music:Música||`` e adicione o bloco  
``||music:play risadinha until done||`` dentro do ``||logic:então||``. Clique
na seta para alterar a canção de **risadinha** para **feliz**.

```blocks
input.onLogoEvent(TouchButtonEvent.Pressed, function () {
    let lente = 0
    let falha = 0
    if (falha == lente) {
        basic.showIcon(IconNames.Yes)
        music.play(music.builtinPlayableSoundEffect(soundExpression.happy), music.PlaybackMode.UntilDone)
    } else {
    	
    }
})
input.onButtonPressed(Button.A, function () {
    if (sensors.dimmerValue(InputPorts.P1) <= 500) {
        basic.showLeds(`
            . . # . .
            . # # # .
            . # # # .
            . # # # .
            . . # . .
            `)
        basic.pause(2000)
        basic.clearScreen()
    } else {
        basic.showLeds(`
            . # # # .
            . . # . .
            . . # . .
            . . # . .
            . # # # .
            `)
        basic.pause(2000)
        basic.clearScreen()
    }
})
input.onButtonPressed(Button.B, function () {
    if (sensors.infraredValue(InputPorts.P2) >= 250) {
        basic.showString("Hipermetropia")
    } else {
        basic.showString("Miopia")
    }
})
basic.forever(function () {
	
})
```

## Passo 25
Retorne à categoria ``||basic:Básico||`` e adicione os comandos 
``||basic:pausa (ms)||`` e ``||basic:limpar tela||``. Altere a duração da 
``||basic:pausa||`` de **100ms** para **2000ms**.

```blocks
input.onLogoEvent(TouchButtonEvent.Pressed, function () {
    let lente = 0
    let falha = 0
    if (falha == lente) {
        basic.showIcon(IconNames.Yes)
        music.play(music.builtinPlayableSoundEffect(soundExpression.happy), music.PlaybackMode.UntilDone)
        basic.pause(2000)
        basic.clearScreen()
    } else {
    	
    }
})
input.onButtonPressed(Button.A, function () {
    if (sensors.dimmerValue(InputPorts.P1) <= 500) {
        basic.showLeds(`
            . . # . .
            . # # # .
            . # # # .
            . # # # .
            . . # . .
            `)
        basic.pause(2000)
        basic.clearScreen()
    } else {
        basic.showLeds(`
            . # # # .
            . . # . .
            . . # . .
            . . # . .
            . # # # .
            `)
        basic.pause(2000)
        basic.clearScreen()
    }
})
input.onButtonPressed(Button.B, function () {
    if (sensors.infraredValue(InputPorts.P2) >= 250) {
        basic.showString("Hipermetropia")
    } else {
        basic.showString("Miopia")
    }
})
basic.forever(function () {
	
})
```

## Passo 26
Dentro do ``||logic:senão||``, insira os mesmos comandos que programamos no 
``||logic:então||``: ``||basic:mostrar ícone||``, 
``||music:play risadinha until done||``, ``||basic:pausa (ms)||`` e 
``||basic:limpar tela||``. 

```blocks
input.onLogoEvent(TouchButtonEvent.Pressed, function () {
    let lente = 0
    let falha = 0
    if (falha == lente) {
        basic.showIcon(IconNames.Yes)
        music.play(music.builtinPlayableSoundEffect(soundExpression.happy), music.PlaybackMode.UntilDone)
        basic.pause(2000)
        basic.clearScreen()
    } else {
        basic.showIcon(IconNames.Heart)
        music.play(music.builtinPlayableSoundEffect(soundExpression.giggle), music.PlaybackMode.UntilDone)
        basic.pause(100)
        basic.clearScreen()
    }
})
input.onButtonPressed(Button.A, function () {
    if (sensors.dimmerValue(InputPorts.P1) <= 500) {
        basic.showLeds(`
            . . # . .
            . # # # .
            . # # # .
            . # # # .
            . . # . .
            `)
        basic.pause(2000)
        basic.clearScreen()
    } else {
        basic.showLeds(`
            . # # # .
            . . # . .
            . . # . .
            . . # . .
            . # # # .
            `)
        basic.pause(2000)
        basic.clearScreen()
    }
})
input.onButtonPressed(Button.B, function () {
    if (sensors.infraredValue(InputPorts.P2) >= 250) {
        basic.showString("Hipermetropia")
    } else {
        basic.showString("Miopia")
    }
})
basic.forever(function () {
	
})
```

## Passo 27
Altere o ícone para exibir um **"X"**, modifique a canção para **"triste"** e 
edite a duração da ``||basic:pausa||`` para **2000ms** (2 segundos).

```blocks
input.onLogoEvent(TouchButtonEvent.Pressed, function () {
    let lente = 0
    let falha = 0
    if (falha == lente) {
        basic.showIcon(IconNames.Yes)
        music.play(music.builtinPlayableSoundEffect(soundExpression.happy), music.PlaybackMode.UntilDone)
        basic.pause(2000)
        basic.clearScreen()
    } else {
        basic.showIcon(IconNames.No)
        music.play(music.builtinPlayableSoundEffect(soundExpression.sad), music.PlaybackMode.UntilDone)
        basic.pause(2000)
        basic.clearScreen()
    }
})
input.onButtonPressed(Button.A, function () {
    if (sensors.dimmerValue(InputPorts.P1) <= 500) {
        basic.showLeds(`
            . . # . .
            . # # # .
            . # # # .
            . # # # .
            . . # . .
            `)
        basic.pause(2000)
        basic.clearScreen()
    } else {
        basic.showLeds(`
            . # # # .
            . . # . .
            . . # . .
            . . # . .
            . # # # .
            `)
        basic.pause(2000)
        basic.clearScreen()
    }
})
input.onButtonPressed(Button.B, function () {
    if (sensors.infraredValue(InputPorts.P2) >= 250) {
        basic.showString("Hipermetropia")
    } else {
        basic.showString("Miopia")
    }
})
basic.forever(function () {
	
})
```

## Passo 28
Agora, vamos programar o que será executado dentro do laço ``||basic:sempre||``.
Acesse a aba ``||logic:Lógica||`` e adicione o bloco ``||logic:se então senão||`` 
dentro do bloco ``||basic:sempre||``.

```blocks
input.onLogoEvent(TouchButtonEvent.Pressed, function () {
    let lente = 0
    let falha = 0
    if (falha == lente) {
        basic.showIcon(IconNames.Yes)
        music.play(music.builtinPlayableSoundEffect(soundExpression.happy), music.PlaybackMode.UntilDone)
        basic.pause(2000)
        basic.clearScreen()
    } else {
        basic.showIcon(IconNames.No)
        music.play(music.builtinPlayableSoundEffect(soundExpression.sad), music.PlaybackMode.UntilDone)
        basic.pause(2000)
        basic.clearScreen()
    }
})
input.onButtonPressed(Button.A, function () {
    if (sensors.dimmerValue(InputPorts.P1) <= 500) {
        basic.showLeds(`
            . . # . .
            . # # # .
            . # # # .
            . # # # .
            . . # . .
            `)
        basic.pause(2000)
        basic.clearScreen()
    } else {
        basic.showLeds(`
            . # # # .
            . . # . .
            . . # . .
            . . # . .
            . # # # .
            `)
        basic.pause(2000)
        basic.clearScreen()
    }
})
input.onButtonPressed(Button.B, function () {
    if (sensors.infraredValue(InputPorts.P2) >= 250) {
        basic.showString("Hipermetropia")
    } else {
        basic.showString("Miopia")
    }
})
basic.forever(function () {
    if (true) {
    	
    } else {
    	
    }
})
```

## Passo 29
Retorne à ``||logic:Lógica||`` e utilize o bloco comparador 
``||logic:0 < 0||`` para substituir o campo **verdadeiro** do bloco 
``||logic:se então senão||``.

```blocks
input.onLogoEvent(TouchButtonEvent.Pressed, function () {
    let lente = 0
    let falha = 0
    if (falha == lente) {
        basic.showIcon(IconNames.Yes)
        music.play(music.builtinPlayableSoundEffect(soundExpression.happy), music.PlaybackMode.UntilDone)
        basic.pause(2000)
        basic.clearScreen()
    } else {
        basic.showIcon(IconNames.No)
        music.play(music.builtinPlayableSoundEffect(soundExpression.sad), music.PlaybackMode.UntilDone)
        basic.pause(2000)
        basic.clearScreen()
    }
})
input.onButtonPressed(Button.A, function () {
    if (sensors.dimmerValue(InputPorts.P1) <= 500) {
        basic.showLeds(`
            . . # . .
            . # # # .
            . # # # .
            . # # # .
            . . # . .
            `)
        basic.pause(2000)
        basic.clearScreen()
    } else {
        basic.showLeds(`
            . # # # .
            . . # . .
            . . # . .
            . . # . .
            . # # # .
            `)
        basic.pause(2000)
        basic.clearScreen()
    }
})
input.onButtonPressed(Button.B, function () {
    if (sensors.infraredValue(InputPorts.P2) >= 250) {
        basic.showString("Hipermetropia")
    } else {
        basic.showString("Miopia")
    }
})
basic.forever(function () {
    if (0 < 0) {
    	
    } else {
    	
    }
})
```

## Passo 30
Acesse o menu ``||sensors:Sensores||`` e selecione o bloco 
``||sensors:Valor do sensor infravermelho na porta P2||`` para substituir o 
valor **0** no primeiro campo do comparador. Clique na seta do comparador para modificar o sinal de **<** para **>=**. Em 
seguida, altere o segundo campo do comparador de **0** para **250**.

```blocks
input.onLogoEvent(TouchButtonEvent.Pressed, function () {
    let lente = 0
    let falha = 0
    if (falha == lente) {
        basic.showIcon(IconNames.Yes)
        music.play(music.builtinPlayableSoundEffect(soundExpression.happy), music.PlaybackMode.UntilDone)
        basic.pause(2000)
        basic.clearScreen()
    } else {
        basic.showIcon(IconNames.No)
        music.play(music.builtinPlayableSoundEffect(soundExpression.sad), music.PlaybackMode.UntilDone)
        basic.pause(2000)
        basic.clearScreen()
    }
})
input.onButtonPressed(Button.A, function () {
    if (sensors.dimmerValue(InputPorts.P1) <= 500) {
        basic.showLeds(`
            . . # . .
            . # # # .
            . # # # .
            . # # # .
            . . # . .
            `)
        basic.pause(2000)
        basic.clearScreen()
    } else {
        basic.showLeds(`
            . # # # .
            . . # . .
            . . # . .
            . . # . .
            . # # # .
            `)
        basic.pause(2000)
        basic.clearScreen()
    }
})
input.onButtonPressed(Button.B, function () {
    if (sensors.infraredValue(InputPorts.P2) >= 250) {
        basic.showString("Hipermetropia")
    } else {
        basic.showString("Miopia")
    }
})
basic.forever(function () {
    if (sensors.infraredValue(InputPorts.P2) >= 250) {
    	
    } else {
    	
    }
})
```

## Passo 31
Feito isso, acesse a categoria ``||variables:Variáveis||`` e adicione um comando 
``||variables:definir (variável) para 0||`` dentro do ``||logic:então||`` 
e outro dentro do ``||logic:senão||``. Clique na seta desse bloco para 
certificar-se de que a variável selecionada seja a ``||variables:falha||``.

```blocks
let falha = 0
input.onLogoEvent(TouchButtonEvent.Pressed, function () {
    let lente = 0
    if (falha == lente) {
        basic.showIcon(IconNames.Yes)
        music.play(music.builtinPlayableSoundEffect(soundExpression.happy), music.PlaybackMode.UntilDone)
        basic.pause(2000)
        basic.clearScreen()
    } else {
        basic.showIcon(IconNames.No)
        music.play(music.builtinPlayableSoundEffect(soundExpression.sad), music.PlaybackMode.UntilDone)
        basic.pause(2000)
        basic.clearScreen()
    }
})
input.onButtonPressed(Button.A, function () {
    if (sensors.dimmerValue(InputPorts.P1) <= 500) {
        basic.showLeds(`
            . . # . .
            . # # # .
            . # # # .
            . # # # .
            . . # . .
            `)
        basic.pause(2000)
        basic.clearScreen()
    } else {
        basic.showLeds(`
            . # # # .
            . . # . .
            . . # . .
            . . # . .
            . # # # .
            `)
        basic.pause(2000)
        basic.clearScreen()
    }
})
input.onButtonPressed(Button.B, function () {
    if (sensors.infraredValue(InputPorts.P2) >= 250) {
        basic.showString("Hipermetropia")
    } else {
        basic.showString("Miopia")
    }
})
basic.forever(function () {
    if (sensors.infraredValue(InputPorts.P2) >= 250) {
        falha = 0
    } else {
        falha = 0
    }
})
```

## Passo 32
Altere o valor de definição dessa variável para **1** dentro do 
``||logic:então||`` e para **2** dentro do ``||logic:senão||``. 

```blocks
let falha = 0
input.onLogoEvent(TouchButtonEvent.Pressed, function () {
    let lente = 0
    if (falha == lente) {
        basic.showIcon(IconNames.Yes)
        music.play(music.builtinPlayableSoundEffect(soundExpression.happy), music.PlaybackMode.UntilDone)
        basic.pause(2000)
        basic.clearScreen()
    } else {
        basic.showIcon(IconNames.No)
        music.play(music.builtinPlayableSoundEffect(soundExpression.sad), music.PlaybackMode.UntilDone)
        basic.pause(2000)
        basic.clearScreen()
    }
})
input.onButtonPressed(Button.A, function () {
    if (sensors.dimmerValue(InputPorts.P1) <= 500) {
        basic.showLeds(`
            . . # . .
            . # # # .
            . # # # .
            . # # # .
            . . # . .
            `)
        basic.pause(2000)
        basic.clearScreen()
    } else {
        basic.showLeds(`
            . # # # .
            . . # . .
            . . # . .
            . . # . .
            . # # # .
            `)
        basic.pause(2000)
        basic.clearScreen()
    }
})
input.onButtonPressed(Button.B, function () {
    if (sensors.infraredValue(InputPorts.P2) >= 250) {
        basic.showString("Hipermetropia")
    } else {
        basic.showString("Miopia")
    }
})
basic.forever(function () {
    if (sensors.infraredValue(InputPorts.P2) >= 250) {
        falha = 1
    } else {
        falha = 2
    }
})
```

## Passo 33
Agora, adicione um segundo bloco ``||logic:se então senão||`` **abaixo** do anterior,
dentro do ``||basic:sempre||``. Certifique-se de **não** posicionar dentro do 
``||logic:se então||`` anterior.

```blocks
let falha = 0
input.onLogoEvent(TouchButtonEvent.Pressed, function () {
    let lente = 0
    if (falha == lente) {
        basic.showIcon(IconNames.Yes)
        music.play(music.builtinPlayableSoundEffect(soundExpression.happy), music.PlaybackMode.UntilDone)
        basic.pause(2000)
        basic.clearScreen()
    } else {
        basic.showIcon(IconNames.No)
        music.play(music.builtinPlayableSoundEffect(soundExpression.sad), music.PlaybackMode.UntilDone)
        basic.pause(2000)
        basic.clearScreen()
    }
})
input.onButtonPressed(Button.A, function () {
    if (sensors.dimmerValue(InputPorts.P1) <= 500) {
        basic.showLeds(`
            . . # . .
            . # # # .
            . # # # .
            . # # # .
            . . # . .
            `)
        basic.pause(2000)
        basic.clearScreen()
    } else {
        basic.showLeds(`
            . # # # .
            . . # . .
            . . # . .
            . . # . .
            . # # # .
            `)
        basic.pause(2000)
        basic.clearScreen()
    }
})
input.onButtonPressed(Button.B, function () {
    if (sensors.infraredValue(InputPorts.P2) >= 250) {
        basic.showString("Hipermetropia")
    } else {
        basic.showString("Miopia")
    }
})
basic.forever(function () {
    if (sensors.infraredValue(InputPorts.P2) >= 250) {
        falha = 1
    } else {
        falha = 2
    }
    if (true) {
    	
    } else {
    	
    }
})
```

## Passo 34
Retorne à ``||logic:Lógica||`` e utilize o bloco comparador 
``||logic:0 < 0||`` para substituir o campo **verdadeiro** do bloco 
``||logic:se então senão||``.

```blocks
let falha = 0
input.onLogoEvent(TouchButtonEvent.Pressed, function () {
    let lente = 0
    if (falha == lente) {
        basic.showIcon(IconNames.Yes)
        music.play(music.builtinPlayableSoundEffect(soundExpression.happy), music.PlaybackMode.UntilDone)
        basic.pause(2000)
        basic.clearScreen()
    } else {
        basic.showIcon(IconNames.No)
        music.play(music.builtinPlayableSoundEffect(soundExpression.sad), music.PlaybackMode.UntilDone)
        basic.pause(2000)
        basic.clearScreen()
    }
})
input.onButtonPressed(Button.A, function () {
    if (sensors.dimmerValue(InputPorts.P1) <= 500) {
        basic.showLeds(`
            . . # . .
            . # # # .
            . # # # .
            . # # # .
            . . # . .
            `)
        basic.pause(2000)
        basic.clearScreen()
    } else {
        basic.showLeds(`
            . # # # .
            . . # . .
            . . # . .
            . . # . .
            . # # # .
            `)
        basic.pause(2000)
        basic.clearScreen()
    }
})
input.onButtonPressed(Button.B, function () {
    if (sensors.infraredValue(InputPorts.P2) >= 250) {
        basic.showString("Hipermetropia")
    } else {
        basic.showString("Miopia")
    }
})
basic.forever(function () {
    if (sensors.infraredValue(InputPorts.P2) >= 250) {
        falha = 1
    } else {
        falha = 2
    }
    if (0 < 0) {
    	
    } else {
    	
    }
})
```

## Passo 35
Acesse o menu ``||sensors:Sensores||`` e selecione o bloco 
``||sensors:Valor do potenciômetro na porta P2||`` para substituir o valor **0**
do primeiro campo do comparador. Antes de prosseguir, altere a porta de **P2** 
para **P1**.

```blocks
let falha = 0
input.onLogoEvent(TouchButtonEvent.Pressed, function () {
    let lente = 0
    if (falha == lente) {
        basic.showIcon(IconNames.Yes)
        music.play(music.builtinPlayableSoundEffect(soundExpression.happy), music.PlaybackMode.UntilDone)
        basic.pause(2000)
        basic.clearScreen()
    } else {
        basic.showIcon(IconNames.No)
        music.play(music.builtinPlayableSoundEffect(soundExpression.sad), music.PlaybackMode.UntilDone)
        basic.pause(2000)
        basic.clearScreen()
    }
})
input.onButtonPressed(Button.A, function () {
    if (sensors.dimmerValue(InputPorts.P1) <= 500) {
        basic.showLeds(`
            . . # . .
            . # # # .
            . # # # .
            . # # # .
            . . # . .
            `)
        basic.pause(2000)
        basic.clearScreen()
    } else {
        basic.showLeds(`
            . # # # .
            . . # . .
            . . # . .
            . . # . .
            . # # # .
            `)
        basic.pause(2000)
        basic.clearScreen()
    }
})
input.onButtonPressed(Button.B, function () {
    if (sensors.infraredValue(InputPorts.P2) >= 250) {
        basic.showString("Hipermetropia")
    } else {
        basic.showString("Miopia")
    }
})
basic.forever(function () {
    if (sensors.infraredValue(InputPorts.P2) >= 250) {
        falha = 1
    } else {
        falha = 2
    }
    if (sensors.dimmerValue(InputPorts.P1) < 0) {
    	
    } else {
    	
    }
})
```

## Passo 36
Clique na seta do comparador para modificar o sinal de **<** para **<=**. Em 
seguida, altere o segundo campo do comparador de **0** para **500**.

```blocks
let falha = 0
input.onLogoEvent(TouchButtonEvent.Pressed, function () {
    let lente = 0
    if (falha == lente) {
        basic.showIcon(IconNames.Yes)
        music.play(music.builtinPlayableSoundEffect(soundExpression.happy), music.PlaybackMode.UntilDone)
        basic.pause(2000)
        basic.clearScreen()
    } else {
        basic.showIcon(IconNames.No)
        music.play(music.builtinPlayableSoundEffect(soundExpression.sad), music.PlaybackMode.UntilDone)
        basic.pause(2000)
        basic.clearScreen()
    }
})
input.onButtonPressed(Button.A, function () {
    if (sensors.dimmerValue(InputPorts.P1) <= 500) {
        basic.showLeds(`
            . . # . .
            . # # # .
            . # # # .
            . # # # .
            . . # . .
            `)
        basic.pause(2000)
        basic.clearScreen()
    } else {
        basic.showLeds(`
            . # # # .
            . . # . .
            . . # . .
            . . # . .
            . # # # .
            `)
        basic.pause(2000)
        basic.clearScreen()
    }
})
input.onButtonPressed(Button.B, function () {
    if (sensors.infraredValue(InputPorts.P2) >= 250) {
        basic.showString("Hipermetropia")
    } else {
        basic.showString("Miopia")
    }
})
basic.forever(function () {
    if (sensors.infraredValue(InputPorts.P2) >= 250) {
        falha = 1
    } else {
        falha = 2
    }
    if (sensors.dimmerValue(InputPorts.P1) <= 500) {
    	
    } else {
    	
    }
})
```

## Passo 37
Acesse o menu ``||actuators:Atuadores||`` e adicione o comando 
``||actuators:Servo, definir posição 0 porta P8 modo Knob||`` dentro do 
``||logic:então||`` e do ``||logic:senão||``.

```blocks
let falha = 0
input.onLogoEvent(TouchButtonEvent.Pressed, function () {
    let lente = 0
    if (falha == lente) {
        basic.showIcon(IconNames.Yes)
        music.play(music.builtinPlayableSoundEffect(soundExpression.happy), music.PlaybackMode.UntilDone)
        basic.pause(2000)
        basic.clearScreen()
    } else {
        basic.showIcon(IconNames.No)
        music.play(music.builtinPlayableSoundEffect(soundExpression.sad), music.PlaybackMode.UntilDone)
        basic.pause(2000)
        basic.clearScreen()
    }
})
input.onButtonPressed(Button.A, function () {
    if (sensors.dimmerValue(InputPorts.P1) <= 500) {
        basic.showLeds(`
            . . # . .
            . # # # .
            . # # # .
            . # # # .
            . . # . .
            `)
        basic.pause(2000)
        basic.clearScreen()
    } else {
        basic.showLeds(`
            . # # # .
            . . # . .
            . . # . .
            . . # . .
            . # # # .
            `)
        basic.pause(2000)
        basic.clearScreen()
    }
})
input.onButtonPressed(Button.B, function () {
    if (sensors.infraredValue(InputPorts.P2) >= 250) {
        basic.showString("Hipermetropia")
    } else {
        basic.showString("Miopia")
    }
})
basic.forever(function () {
    if (sensors.infraredValue(InputPorts.P2) >= 250) {
        falha = 1
    } else {
        falha = 2
    }
    if (sensors.dimmerValue(InputPorts.P1) <= 500) {
        actuators.SetAngleServoKnob(0, OutputPorts.P8)
    } else {
        actuators.SetAngleServoKnob(0, OutputPorts.P8)
    }
})
```

## Passo 38
Altere a porta de ambos os blocos de ``||actuators:P8||`` para ``||actuators:P16||``
e a posição de **0** para **100** e **525**, respectivamente.

```blocks
let falha = 0
input.onLogoEvent(TouchButtonEvent.Pressed, function () {
    let lente = 0
    if (falha == lente) {
        basic.showIcon(IconNames.Yes)
        music.play(music.builtinPlayableSoundEffect(soundExpression.happy), music.PlaybackMode.UntilDone)
        basic.pause(2000)
        basic.clearScreen()
    } else {
        basic.showIcon(IconNames.No)
        music.play(music.builtinPlayableSoundEffect(soundExpression.sad), music.PlaybackMode.UntilDone)
        basic.pause(2000)
        basic.clearScreen()
    }
})
input.onButtonPressed(Button.A, function () {
    if (sensors.dimmerValue(InputPorts.P1) <= 500) {
        basic.showLeds(`
            . . # . .
            . # # # .
            . # # # .
            . # # # .
            . . # . .
            `)
        basic.pause(2000)
        basic.clearScreen()
    } else {
        basic.showLeds(`
            . # # # .
            . . # . .
            . . # . .
            . . # . .
            . # # # .
            `)
        basic.pause(2000)
        basic.clearScreen()
    }
})
input.onButtonPressed(Button.B, function () {
    if (sensors.infraredValue(InputPorts.P2) >= 250) {
        basic.showString("Hipermetropia")
    } else {
        basic.showString("Miopia")
    }
})
basic.forever(function () {
    if (sensors.infraredValue(InputPorts.P2) >= 250) {
        falha = 1
    } else {
        falha = 2
    }
    if (sensors.dimmerValue(InputPorts.P1) <= 500) {
        actuators.SetAngleServoKnob(100, OutputPorts.P16)
    } else {
        actuators.SetAngleServoKnob(525, OutputPorts.P16)
    }
})
```

## Passo 39
Feito isso, acesse a categoria ``||variables:Variáveis||`` e adicione um comando 
``||variables:definir (variável) para 0||`` dentro do ``||logic:então||`` 
e outro dentro do ``||logic:senão||``. Clique na seta desse bloco para 
certificar-se de que a variável selecionada seja ``||variables:lente||``.

```blocks
let falha = 0
input.onLogoEvent(TouchButtonEvent.Pressed, function () {
    if (falha == lente) {
        basic.showIcon(IconNames.Yes)
        music.play(music.builtinPlayableSoundEffect(soundExpression.happy), music.PlaybackMode.UntilDone)
        basic.pause(2000)
        basic.clearScreen()
    } else {
        basic.showIcon(IconNames.No)
        music.play(music.builtinPlayableSoundEffect(soundExpression.sad), music.PlaybackMode.UntilDone)
        basic.pause(2000)
        basic.clearScreen()
    }
})
input.onButtonPressed(Button.A, function () {
    if (sensors.dimmerValue(InputPorts.P1) <= 500) {
        basic.showLeds(`
            . . # . .
            . # # # .
            . # # # .
            . # # # .
            . . # . .
            `)
        basic.pause(2000)
        basic.clearScreen()
    } else {
        basic.showLeds(`
            . # # # .
            . . # . .
            . . # . .
            . . # . .
            . # # # .
            `)
        basic.pause(2000)
        basic.clearScreen()
    }
})
input.onButtonPressed(Button.B, function () {
    if (sensors.infraredValue(InputPorts.P2) >= 250) {
        basic.showString("Hipermetropia")
    } else {
        basic.showString("Miopia")
    }
})
basic.forever(function () {
    if (sensors.infraredValue(InputPorts.P2) >= 250) {
        falha = 1
    } else {
        falha = 2
    }
    if (sensors.dimmerValue(InputPorts.P1) <= 500) {
        actuators.SetAngleServoKnob(100, OutputPorts.P16)
        lente = 0
    } else {
        actuators.SetAngleServoKnob(525, OutputPorts.P16)
        lente = 0
    }
})
```

## Passo 40
Altere o valor de definição dessa variável para **1** dentro do 
``||logic:então||`` e para **2** dentro do ``||logic:senão||``. 

```blocks
let falha = 0
let lente = 0
input.onLogoEvent(TouchButtonEvent.Pressed, function () {
    if (falha == lente) {
        basic.showIcon(IconNames.Yes)
        music.play(music.builtinPlayableSoundEffect(soundExpression.happy), music.PlaybackMode.UntilDone)
        basic.pause(2000)
        basic.clearScreen()
    } else {
        basic.showIcon(IconNames.No)
        music.play(music.builtinPlayableSoundEffect(soundExpression.sad), music.PlaybackMode.UntilDone)
        basic.pause(2000)
        basic.clearScreen()
    }
})
input.onButtonPressed(Button.A, function () {
    if (sensors.dimmerValue(InputPorts.P1) <= 500) {
        basic.showLeds(`
            . . # . .
            . # # # .
            . # # # .
            . # # # .
            . . # . .
            `)
        basic.pause(2000)
        basic.clearScreen()
    } else {
        basic.showLeds(`
            . # # # .
            . . # . .
            . . # . .
            . . # . .
            . # # # .
            `)
        basic.pause(2000)
        basic.clearScreen()
    }
})
input.onButtonPressed(Button.B, function () {
    if (sensors.infraredValue(InputPorts.P2) >= 250) {
        basic.showString("Hipermetropia")
    } else {
        basic.showString("Miopia")
    }
})
basic.forever(function () {
    if (sensors.infraredValue(InputPorts.P2) >= 250) {
        falha = 1
    } else {
        falha = 2
    }
    if (sensors.dimmerValue(InputPorts.P1) <= 500) {
        actuators.SetAngleServoKnob(100, OutputPorts.P16)
        lente = 1
    } else {
        actuators.SetAngleServoKnob(525, OutputPorts.P16)
        lente = 2
    }
})
```

## Passo 41
Agora, seu código está pronto! Baixe-o para o micro:bit e utilize o potenciômetro
para ajustar as lentes, o botão A para verificar a lente e o botão B para verificar
a falha visual. Com o logotipo, você testa a combinação de lente e falha visual.

```blocks
```

## Passo 42
Se necessário, confira o seu código clicando na lâmpada de dica.

```blocks
let falha = 0
let lente = 0
input.onLogoEvent(TouchButtonEvent.Pressed, function () {
    if (falha == lente) {
        basic.showIcon(IconNames.Yes)
        music.play(music.builtinPlayableSoundEffect(soundExpression.happy), music.PlaybackMode.UntilDone)
        basic.pause(2000)
        basic.clearScreen()
    } else {
        basic.showIcon(IconNames.No)
        music.play(music.builtinPlayableSoundEffect(soundExpression.sad), music.PlaybackMode.UntilDone)
        basic.pause(2000)
        basic.clearScreen()
    }
})
input.onButtonPressed(Button.A, function () {
    if (sensors.dimmerValue(InputPorts.P1) <= 500) {
        basic.showLeds(`
            . . # . .
            . # # # .
            . # # # .
            . # # # .
            . . # . .
            `)
        basic.pause(2000)
        basic.clearScreen()
    } else {
        basic.showLeds(`
            . # # # .
            . . # . .
            . . # . .
            . . # . .
            . # # # .
            `)
        basic.pause(2000)
        basic.clearScreen()
    }
})
input.onButtonPressed(Button.B, function () {
    if (sensors.infraredValue(InputPorts.P2) >= 250) {
        basic.showString("Hipermetropia")
    } else {
        basic.showString("Miopia")
    }
})
basic.forever(function () {
    if (sensors.infraredValue(InputPorts.P2) >= 250) {
        falha = 1
    } else {
        falha = 2
    }
    if (sensors.dimmerValue(InputPorts.P1) <= 500) {
        actuators.SetAngleServoKnob(100, OutputPorts.P16)
        lente = 1
    } else {
        actuators.SetAngleServoKnob(525, OutputPorts.P16)
        lente = 2
    }
})
```

```package
fuzzyBot=github:FuzzyMakers/pxt-fuzzyMakers
```