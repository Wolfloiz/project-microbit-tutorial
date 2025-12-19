### @diffs true
# Ônibus espacial

## Passo 1
Neste tutorial, vamos programar um ônibus espacial para que ele seja um seguidor de linha.
Assim ele conseguirá segui trajetos demarcados depois da contagem regressiva inicial.


## Passo 2
Para começar, verifique se a biblioteca da Smart Makers já está importada 
em seu MakeCode. Se não estiver, clique na aba **+ Extensões**, 
copie o endereço "https://github.com/FuzzyMakers/pxt-smartMakers", 
cole-o no campo de pesquisa da janela que se abriu e selecione a biblioteca. 

## Passo 3
No menu ``||actuators:Atuadores||`` busque o bloco ``||actuators:Motor CC, definir direção para Sentido horário na porta P8||`` e adicione-o
dentro do ``||basic:no iniciar||``.
Mude o sentido para ``||actuators:anti-horário||``.
```blocks
actuators.SetDirectionMotor(MotorDirection.antiClockwise, OutputPorts.P8)
```

## Passo 4
Acesse o menu ``||variables:Variáveis||`` e clique em 
**"Fazer uma variável..."**. Crie uma variável chamada
``||variables:contagem||``. Em seguida, arraste o bloco ``||variables:definir contagem para 0||`` 
para o bloco ``||basic:no iniciar||``.
Ajuste o valor da variável para **10**.

```blocks
actuators.SetDirectionMotor(MotorDirection.antiClockwise, OutputPorts.P8)
let contagem = 10
```

## Passo 5


No fim do bloco ``||basic:no iniciar||`` coloque um comando ``||basic:mostrar ícone||``, que pode ser retirado da categoria
``||basic:Básico||``. Altere o ícone do coração para um **quadrado pequeno**.


```blocks
actuators.SetDirectionMotor(MotorDirection.antiClockwise, OutputPorts.P8)
let contagem = 10
basic.showIcon(IconNames.SmallSquare)
```

## Passo 6
Clique no menu ``||Advanced:Avançado||``, acesse ``||Functions:Funções||`` e 
clique em **Fazer uma função...**.
Clique no campo editável do laço azul para criar uma função chamada 
``||functions:contagem_regressiva||``. 
Um novo laço referente à função criada é adicionado automaticamente à área de programação.

```blocks
function contagem_regressiva () {
	
}
actuators.SetDirectionMotor(MotorDirection.antiClockwise, OutputPorts.P8)
let contagem = 10
basic.showIcon(IconNames.SmallSquare)

```

## Passo 7
Acesse a categoria ``||loops:Loops||``, pegue o laço ``||loops:enquanto executar||``
e insira-o dentro da função ``||functions:contagem_regressiva||``. 


```blocks
function contagem_regressiva () {
    while (false) {
    	
    }
}
actuators.SetDirectionMotor(MotorDirection.antiClockwise, OutputPorts.P8)
let contagem = 10
basic.showIcon(IconNames.SmallSquare)

```

## Passo 8

Acesse a categoria ``||logic:Lógica||``, pegue um comparador ``||logic: 0 < 0||``
para colocar na condição **falso** do laço.
Modifique o sinal do comparador para **>**.
```blocks
function contagem_regressiva () {
    while (0 > 0) {
    	
    }
}
actuators.SetDirectionMotor(MotorDirection.antiClockwise, OutputPorts.P8)
let contagem = 10
basic.showIcon(IconNames.SmallSquare)
```

## Passo 9
Agora atualize o primeiro campo do comparador.
Pegue a variável ``||variables:contagem||``  para colocá-la no lugar do **0**.

```blocks
function contagem_regressiva () {
    while (contagem > 0) {
    	
    }
}
let contagem = 0
actuators.SetDirectionMotor(MotorDirection.antiClockwise, OutputPorts.P8)
contagem = 10
basic.showIcon(IconNames.SmallSquare)

```

## Passo 10
Volte ao menu ``||basic:Básico||`` e arraste um comando ``||basic:mostrar número 0||``
para dentro do laço ``||loops:enquanto executar||``.
Substitua o valor **0** da exibição do número pela variável ``||variables:contagem||``.
```blocks
function contagem_regressiva () {
    while (contagem > 0) {
        basic.showNumber(contagem)
    }
}
let contagem = 0
actuators.SetDirectionMotor(MotorDirection.antiClockwise, OutputPorts.P8)
contagem = 10
basic.showIcon(IconNames.SmallSquare)
```


## Passo 11
Acesse a aba ``||music:Música||`` e posicione o bloco ``||music:play tone C Médio for 1 batida until done||`` 
abaixo do último comando adicionado.

```blocks
function contagem_regressiva () {
    while (contagem > 0) {
        basic.showNumber(contagem)
        music.play(music.tonePlayable(262, music.beat(BeatFraction.Whole)), music.PlaybackMode.UntilDone)
    }
}
let contagem = 0
actuators.SetDirectionMotor(MotorDirection.antiClockwise, OutputPorts.P8)
contagem = 10
basic.showIcon(IconNames.SmallSquare)
```

## Passo 12

Na categoria ``||basic:Básico||`` arraste uma pausa ``||basic:pausa (ms) 100||`` para o código,
altere o valor para **1000**.
```blocks
function contagem_regressiva () {
    while (contagem > 0) {
        basic.showNumber(contagem)
        music.play(music.tonePlayable(262, music.beat(BeatFraction.Whole)), music.PlaybackMode.UntilDone)
        basic.pause(1000)
    }
}
let contagem = 0
actuators.SetDirectionMotor(MotorDirection.antiClockwise, OutputPorts.P8)
contagem = 10
basic.showIcon(IconNames.SmallSquare)
```

## Passo 13

Acesse mais uma vez a seção ``||variables:Variáveis||``, pegue o comando
``||variables:Alterar contagem por 1||`` e posicione-o no fim do laço
``||loops:enquanto executar||``. Corrija o valor do incremento de **1** para **-1**.

```blocks
function contagem_regressiva () {
    while (contagem > 0) {
        basic.showNumber(contagem)
        music.play(music.tonePlayable(262, music.beat(BeatFraction.Whole)), music.PlaybackMode.UntilDone)
        basic.pause(1000)
        contagem += -1
    }
}
let contagem = 0
actuators.SetDirectionMotor(MotorDirection.antiClockwise, OutputPorts.P8)
contagem = 10
basic.showIcon(IconNames.SmallSquare)
```


## Passo 14

Copie o comando ``||music:play tone C Médio for 1 batida until done||`` e cole-o 
depois do loop. Altere o número de ``||music:batidas||`` para **2**.
```blocks
function contagem_regressiva () {
    while (contagem > 0) {
        basic.showNumber(contagem)
        music.play(music.tonePlayable(262, music.beat(BeatFraction.Whole)), music.PlaybackMode.UntilDone)
        basic.pause(1000)
        contagem += -1
    }
    music.play(music.tonePlayable(262, music.beat(BeatFraction.Double)), music.PlaybackMode.UntilDone)
}
let contagem = 0
actuators.SetDirectionMotor(MotorDirection.antiClockwise, OutputPorts.P8)
contagem = 10
basic.showIcon(IconNames.SmallSquare)
```

## Passo 15

Na categoria ``||basic:Básico||`` arraste um bloco ``||basic:mostrar leds||`` para o fim da função,
depois, preencha as células do display com um símbolo para representar a "decolagem". Use o botão da dica para ver nossa sugestão.

```blocks
function contagem_regressiva () {
    while (contagem > 0) {
        basic.showNumber(contagem)
        music.play(music.tonePlayable(262, music.beat(BeatFraction.Whole)), music.PlaybackMode.UntilDone)
        basic.pause(1000)
        contagem += -1
    }
    music.play(music.tonePlayable(262, music.beat(BeatFraction.Double)), music.PlaybackMode.UntilDone)
    basic.showLeds(`
        . . # . .
        . # # # .
        # # # # #
        . # # # .
        . # # # .
        `)
}
let contagem = 0
actuators.SetDirectionMotor(MotorDirection.antiClockwise, OutputPorts.P8)
contagem = 10
basic.showIcon(IconNames.SmallSquare)
```

## Passo 16

Na aba ``||input:Entrada||``, selecione **dois** blocos ``||input:no botão A pressionado||`` 
e coloque-os na área de programação.
Antes de prosseguir, altere a segunda condição para ``||input:no botão B pressionado||``.
```blocks
input.onButtonPressed(Button.A, function () {
	
})
function contagem_regressiva () {
    while (contagem > 0) {
        basic.showNumber(contagem)
        music.play(music.tonePlayable(262, music.beat(BeatFraction.Whole)), music.PlaybackMode.UntilDone)
        basic.pause(1000)
        contagem += -1
    }
    music.play(music.tonePlayable(262, music.beat(BeatFraction.Double)), music.PlaybackMode.UntilDone)
    basic.showLeds(`
        . . # . .
        . # # # .
        # # # # #
        . # # # .
        . # # # .
        `)
}
input.onButtonPressed(Button.B, function () {
	
})
let contagem = 0
actuators.SetDirectionMotor(MotorDirection.antiClockwise, OutputPorts.P8)
contagem = 10
basic.showIcon(IconNames.SmallSquare)
```

## Passo 17

No menu ``||functions:Funções||`` arraste os comandos  ``||functions:ligar contagem_regressiva||``
para dentro do bloco ``||input:no botão A pressionado||``.

```blocks
input.onButtonPressed(Button.A, function () {
    contagem_regressiva()
})
function contagem_regressiva () {
    while (contagem > 0) {
        basic.showNumber(contagem)
        music.play(music.tonePlayable(262, music.beat(BeatFraction.Whole)), music.PlaybackMode.UntilDone)
        basic.pause(1000)
        contagem += -1
    }
    music.play(music.tonePlayable(262, music.beat(BeatFraction.Double)), music.PlaybackMode.UntilDone)
    basic.showLeds(`
        . . # . .
        . # # # .
        # # # # #
        . # # # .
        . # # # .
        `)
}
input.onButtonPressed(Button.B, function () {
	
})
let contagem = 0
actuators.SetDirectionMotor(MotorDirection.antiClockwise, OutputPorts.P8)
contagem = 10
basic.showIcon(IconNames.SmallSquare)

```

## Passo 18

Duplique os comandos ``||variables:definir contagem para 10||`` e ``||basic:mostrar ícone||``  contido no bloco
``||basic:no iniciar||`` e coloque-os no bloco ``||input:no botão B pressionado||``.

```blocks
input.onButtonPressed(Button.A, function () {
    contagem_regressiva()
})
function contagem_regressiva () {
    while (contagem > 0) {
        basic.showNumber(contagem)
        music.play(music.tonePlayable(262, music.beat(BeatFraction.Whole)), music.PlaybackMode.UntilDone)
        basic.pause(1000)
        contagem += -1
    }
    music.play(music.tonePlayable(262, music.beat(BeatFraction.Double)), music.PlaybackMode.UntilDone)
    basic.showLeds(`
        . . # . .
        . # # # .
        # # # # #
        . # # # .
        . # # # .
        `)
}
input.onButtonPressed(Button.B, function () {
    contagem = 10
    basic.showIcon(IconNames.SmallSquare)
})
let contagem = 0
actuators.SetDirectionMotor(MotorDirection.antiClockwise, OutputPorts.P8)
contagem = 10
basic.showIcon(IconNames.SmallSquare)

```

## Passo 19

Clique no menu ``||Advanced:Avançado||``, acesse ``||Functions:Funções||`` e 
clique em **Fazer uma função...**.
Clique no campo editável do laço azul para criar uma função chamada 
``||functions:parar||``. 
Um novo laço referente à função criada é adicionado automaticamente à área de programação.


```blocks
input.onButtonPressed(Button.A, function () {
    contagem_regressiva()
})
function contagem_regressiva () {
    while (contagem > 0) {
        basic.showNumber(contagem)
        music.play(music.tonePlayable(262, music.beat(BeatFraction.Whole)), music.PlaybackMode.UntilDone)
        basic.pause(1000)
        contagem += -1
    }
    music.play(music.tonePlayable(262, music.beat(BeatFraction.Double)), music.PlaybackMode.UntilDone)
    basic.showLeds(`
        . . # . .
        . # # # .
        # # # # #
        . # # # .
        . # # # .
        `)
}
input.onButtonPressed(Button.B, function () {
    contagem = 10
    basic.showIcon(IconNames.SmallSquare)
})
function parar () {
	
}
let contagem = 0
actuators.SetDirectionMotor(MotorDirection.antiClockwise, OutputPorts.P8)
contagem = 10
basic.showIcon(IconNames.SmallSquare)
```

## Passo 20

Repita o passo anterior para criar outra função chamada ``||functions:seguir_linha||``.

```blocks
function seguir_linha () {
	
}
input.onButtonPressed(Button.A, function () {
    contagem_regressiva()
})
function contagem_regressiva () {
    while (contagem > 0) {
        basic.showNumber(contagem)
        music.play(music.tonePlayable(262, music.beat(BeatFraction.Whole)), music.PlaybackMode.UntilDone)
        basic.pause(1000)
        contagem += -1
    }
    music.play(music.tonePlayable(262, music.beat(BeatFraction.Double)), music.PlaybackMode.UntilDone)
    basic.showLeds(`
        . . # . .
        . # # # .
        # # # # #
        . # # # .
        . # # # .
        `)
}
input.onButtonPressed(Button.B, function () {
    contagem = 10
    basic.showIcon(IconNames.SmallSquare)
})
function parar () {
	
}
let contagem = 0
actuators.SetDirectionMotor(MotorDirection.antiClockwise, OutputPorts.P8)
contagem = 10
basic.showIcon(IconNames.SmallSquare)
```

## Passo 21

Acesse o menu ``||actuators:Atuadores||``, adicione dois blocos
``||actuators:Motor CC, definir velocidade 0 na porta P8||``
dentro da função ``||functions:parar||``. 
Mude uma das portas de ``||actuators:P8||`` para ``||actuators:P12||`` e outra para ``||actuators:P16||``.
```blocks
function seguir_linha () {
	
}
input.onButtonPressed(Button.A, function () {
    contagem_regressiva()
})
function contagem_regressiva () {
    while (contagem > 0) {
        basic.showNumber(contagem)
        music.play(music.tonePlayable(262, music.beat(BeatFraction.Whole)), music.PlaybackMode.UntilDone)
        basic.pause(1000)
        contagem += -1
    }
    music.play(music.tonePlayable(262, music.beat(BeatFraction.Double)), music.PlaybackMode.UntilDone)
    basic.showLeds(`
        . . # . .
        . # # # .
        # # # # #
        . # # # .
        . # # # .
        `)
}
input.onButtonPressed(Button.B, function () {
    contagem = 10
    basic.showIcon(IconNames.SmallSquare)
})
function parar () {
    actuators.SetSpeedMotor(0, OutputPorts.P12)
    actuators.SetSpeedMotor(0, OutputPorts.P16)
}
let contagem = 0
actuators.SetDirectionMotor(MotorDirection.antiClockwise, OutputPorts.P8)
contagem = 10
basic.showIcon(IconNames.SmallSquare)
```
## Passo 22

Acesse a categoria ``||logic:Lógica||``, clique na condicional ``||logic:se então senão||``
e insira-a dentro da função ``||functions:seguir linha||``.

```blocks
function seguir_linha () {
    if (true) {
    	
    } else {
    	
    }
}
input.onButtonPressed(Button.A, function () {
    contagem_regressiva()
})
function contagem_regressiva () {
    while (contagem > 0) {
        basic.showNumber(contagem)
        music.play(music.tonePlayable(262, music.beat(BeatFraction.Whole)), music.PlaybackMode.UntilDone)
        basic.pause(1000)
        contagem += -1
    }
    music.play(music.tonePlayable(262, music.beat(BeatFraction.Double)), music.PlaybackMode.UntilDone)
    basic.showLeds(`
        . . # . .
        . # # # .
        # # # # #
        . # # # .
        . # # # .
        `)
}
input.onButtonPressed(Button.B, function () {
    contagem = 10
    basic.showIcon(IconNames.SmallSquare)
})
function parar () {
    actuators.SetSpeedMotor(0, OutputPorts.P12)
    actuators.SetSpeedMotor(0, OutputPorts.P16)
}
let contagem = 0
actuators.SetDirectionMotor(MotorDirection.antiClockwise, OutputPorts.P8)
contagem = 10
basic.showIcon(IconNames.SmallSquare)

```

## Passo 23

Volte ao menu ``||logic:Lógica||``, selecione o comparador ``||logic: 0 = 0||``
e substitua a condição **verdadeiro** da condicional.

```blocks
function seguir_linha () {
    if (0 == 0) {
    	
    } else {
    	
    }
}
input.onButtonPressed(Button.A, function () {
    contagem_regressiva()
})
function contagem_regressiva () {
    while (contagem > 0) {
        basic.showNumber(contagem)
        music.play(music.tonePlayable(262, music.beat(BeatFraction.Whole)), music.PlaybackMode.UntilDone)
        basic.pause(1000)
        contagem += -1
    }
    music.play(music.tonePlayable(262, music.beat(BeatFraction.Double)), music.PlaybackMode.UntilDone)
    basic.showLeds(`
        . . # . .
        . # # # .
        # # # # #
        . # # # .
        . # # # .
        `)
}
input.onButtonPressed(Button.B, function () {
    contagem = 10
    basic.showIcon(IconNames.SmallSquare)
})
function parar () {
    actuators.SetSpeedMotor(0, OutputPorts.P12)
    actuators.SetSpeedMotor(0, OutputPorts.P16)
}
let contagem = 0
actuators.SetDirectionMotor(MotorDirection.antiClockwise, OutputPorts.P8)
contagem = 10
basic.showIcon(IconNames.SmallSquare)


```
## Passo 24

Agora atualize os campos do comparador.
Nos menus avançados acesse a aba ``||pins:Pins||`` e arraste o bloco 
``||pins:leitura digital pin P0||``
para o lugar do primeiro **0** do comparador. 
Altere a porta de ``||pins:P0||`` para ``||pins:P1||``.
Ajuste o segundo valor de **0** para **1**.


```blocks
function seguir_linha () {
    if (pins.digitalReadPin(DigitalPin.P1) == 1) {
    	
    } else {
    	
    }
}
input.onButtonPressed(Button.A, function () {
    contagem_regressiva()
})
function contagem_regressiva () {
    while (contagem > 0) {
        basic.showNumber(contagem)
        music.play(music.tonePlayable(262, music.beat(BeatFraction.Whole)), music.PlaybackMode.UntilDone)
        basic.pause(1000)
        contagem += -1
    }
    music.play(music.tonePlayable(262, music.beat(BeatFraction.Double)), music.PlaybackMode.UntilDone)
    basic.showLeds(`
        . . # . .
        . # # # .
        # # # # #
        . # # # .
        . # # # .
        `)
}
input.onButtonPressed(Button.B, function () {
    contagem = 10
    basic.showIcon(IconNames.SmallSquare)
})
function parar () {
    actuators.SetSpeedMotor(0, OutputPorts.P12)
    actuators.SetSpeedMotor(0, OutputPorts.P16)
}
let contagem = 0
actuators.SetDirectionMotor(MotorDirection.antiClockwise, OutputPorts.P8)
contagem = 10
basic.showIcon(IconNames.SmallSquare)

```

## Passo 25

Duplique os **dois** comandos que definem a velocidade dos motores da função 
``||functions:parar||`` e coloque-os dentro desse novo ``||logic:então||``.
Modifique a velocidade do motor conectado à porta ``||actuators:P16||`` para **300**.

```blocks
function seguir_linha () {
    if (pins.digitalReadPin(DigitalPin.P1) == 1) {
        actuators.SetSpeedMotor(0, OutputPorts.P12)
        actuators.SetSpeedMotor(300, OutputPorts.P16)
    } else {
    	
    }
}
input.onButtonPressed(Button.A, function () {
    contagem_regressiva()
})
function contagem_regressiva () {
    while (contagem > 0) {
        basic.showNumber(contagem)
        music.play(music.tonePlayable(262, music.beat(BeatFraction.Whole)), music.PlaybackMode.UntilDone)
        basic.pause(1000)
        contagem += -1
    }
    music.play(music.tonePlayable(262, music.beat(BeatFraction.Double)), music.PlaybackMode.UntilDone)
    basic.showLeds(`
        . . # . .
        . # # # .
        # # # # #
        . # # # .
        . # # # .
        `)
}
input.onButtonPressed(Button.B, function () {
    contagem = 10
    basic.showIcon(IconNames.SmallSquare)
})
function parar () {
    actuators.SetSpeedMotor(0, OutputPorts.P12)
    actuators.SetSpeedMotor(0, OutputPorts.P16)
}
let contagem = 0
actuators.SetDirectionMotor(MotorDirection.antiClockwise, OutputPorts.P8)
contagem = 10
basic.showIcon(IconNames.SmallSquare)

```

## Passo 26

Duplique os **dois** comandos que definem a velocidade dos motores da função 
``||functions:parar||`` e coloque-os dentro da condicional ``||logic:senão||``.
Modifique a velocidade do motor conectado à porta ``||actuators:P12||`` para **300**.


```blocks
function seguir_linha () {
    if (pins.digitalReadPin(DigitalPin.P1) == 1) {
        actuators.SetSpeedMotor(0, OutputPorts.P12)
        actuators.SetSpeedMotor(300, OutputPorts.P16)
    } else {
        actuators.SetSpeedMotor(300, OutputPorts.P12)
        actuators.SetSpeedMotor(0, OutputPorts.P16)
    }
}
input.onButtonPressed(Button.A, function () {
    contagem_regressiva()
})
function contagem_regressiva () {
    while (contagem > 0) {
        basic.showNumber(contagem)
        music.play(music.tonePlayable(262, music.beat(BeatFraction.Whole)), music.PlaybackMode.UntilDone)
        basic.pause(1000)
        contagem += -1
    }
    music.play(music.tonePlayable(262, music.beat(BeatFraction.Double)), music.PlaybackMode.UntilDone)
    basic.showLeds(`
        . . # . .
        . # # # .
        # # # # #
        . # # # .
        . # # # .
        `)
}
input.onButtonPressed(Button.B, function () {
    contagem = 10
    basic.showIcon(IconNames.SmallSquare)
})
function parar () {
    actuators.SetSpeedMotor(0, OutputPorts.P12)
    actuators.SetSpeedMotor(0, OutputPorts.P16)
}
let contagem = 0
actuators.SetDirectionMotor(MotorDirection.antiClockwise, OutputPorts.P8)
contagem = 10
basic.showIcon(IconNames.SmallSquare)
```


## Passo 27

Agora seu código está pronto! Baixe-o para o micro:bit e teste-o.
Pressione o botão "A" do micro:bit e aguarde a contagem regressiva. Observe se o ônibus espacial seguirá a trajetória determinada. 
Use o botão "B" do micro:bit para interromper a viagem e redefinir o contador.
```blocks
```


## Passo 28
Se necessário, confira o seu código clicando na lâmpada de dica.

```blocks
function seguir_linha () {
    if (pins.digitalReadPin(DigitalPin.P1) == 1) {
        actuators.SetSpeedMotor(0, OutputPorts.P12)
        actuators.SetSpeedMotor(300, OutputPorts.P16)
    } else {
        actuators.SetSpeedMotor(300, OutputPorts.P12)
        actuators.SetSpeedMotor(0, OutputPorts.P16)
    }
}
input.onButtonPressed(Button.A, function () {
    contagem_regressiva()
})
function contagem_regressiva () {
    while (contagem > 0) {
        basic.showNumber(contagem)
        music.play(music.tonePlayable(262, music.beat(BeatFraction.Whole)), music.PlaybackMode.UntilDone)
        basic.pause(1000)
        contagem += -1
    }
    music.play(music.tonePlayable(262, music.beat(BeatFraction.Double)), music.PlaybackMode.UntilDone)
    basic.showLeds(`
        . . # . .
        . # # # .
        # # # # #
        . # # # .
        . # # # .
        `)
}
input.onButtonPressed(Button.B, function () {
    contagem = 10
    basic.showIcon(IconNames.SmallSquare)
})
function parar () {
    actuators.SetSpeedMotor(0, OutputPorts.P12)
    actuators.SetSpeedMotor(0, OutputPorts.P16)
}
let contagem = 0
actuators.SetDirectionMotor(MotorDirection.antiClockwise, OutputPorts.P8)
contagem = 10
basic.showIcon(IconNames.SmallSquare)

```



```package
fuzzyBot=github:FuzzyMakers/pxt-fuzzyMakers
```
