### @diffs true
# Polinização

## Passo 1
Neste tutorial, vamos programar o voo de uma abelha durante o processo de polinização.
Ela deve girar e parar em uma flor especial, onde está o Sensor Infravermelho. Quando ela 
estiver sobre essa flor, vamos exibir um ícone e tocar um som para simbolizar a polinização, antes que ela continue seu voo.

## Passo 2
Para começar, verifique se a biblioteca da Smart Makers já está importada em seu MakeCode.
Se não estiver, clique na aba **+ Extensões**, copie o endereço "https://github.com/FuzzyMakers/pxt-smartMakers",
cole-o no campo de pesquisa da janela que se abriu e selecione a biblioteca.

## Passo 3
Acesse o menu ``||logic:Lógica||`` e adicione o laço ``||logic:se verdadeiro então||`` dentro do seu laço ``||basic:sempre||``.

**Dica:** se o laço ``||basic:sempre||`` não estiver presente no seu código automaticamente, você pode encontrá-lo na aba ``||basic:Básico||``.

```blocks
basic.forever(function () {
    if (true) {
    	
    }
})
```

## Passo 4 
Retorne à aba ``||logic:Lógica||`` e selecione o bloco comparador ``||logic:0 < 0||``. Ele deve substituir
o campo ``||logic:verdadeiro||`` do laço ``||logic:se então||``.

```blocks
basic.forever(function () {
    if (0 < 0) {
    	
    }
})
```

## Passo 5
Altere o sinal do comparador de **<** para **>**. Em seguida, acesse a aba ``||sensors:Sensores||`` e selecione o bloco 
``||sensors:Valor do sensor infravermelho na porta P2||``. Ele deve ser posicionado no primeiro campo do comparador, substituindo o valor **0**.

```blocks
basic.forever(function () {
    if (sensors.infraredValue(InputPorts.P2) > 0) {
    	
    }
})
```

## Passo 6
Em seguida, modifique o segundo valor do comparador de **0** para **400**.

```blocks
basic.forever(function () {
    if (sensors.infraredValue(InputPorts.P2) > 400) {
    	
    }
})
```

## Passo 7
Feito isso, vamos configurar o que deve acontecer caso a condição do comparador seja atendida, ou seja, quando a abelha chega na flor especial. 
Para isso, acesse a aba ``||actuators:Atuadores||`` e adicione o comando ``||actuators:Motor CC, parar motor na porta P8||`` dentro do ``||logic:então||``.

```blocks
basic.forever(function () {
    if (sensors.infraredValue(InputPorts.P2) > 400) {
        actuators.StopMotor(OutputPorts.P8)
    }
})
```

## Passo 8
Abaixo desse bloco, adicione o comando ``||basic:mostrar leds||``, localizado no menu ``||basic:Básico||``. 
Clique em cada LED que você deseja acender para exibir uma flor na tela do Micro:bit.

```blocks
basic.forever(function () {
    if (sensors.infraredValue(InputPorts.P2) > 400) {
        actuators.StopMotor(OutputPorts.P8)
        basic.showLeds(`
            . . . . .
            . . # . .
            . # # # .
            . . # . .
            . . . . .
            `)
    }
})
```

## Passo 9
Feito isso, acesse o menu ``||music:Música||`` e adicione o bloco ``||music:play melody dadadum in background||``.
Clique na primeira seta do bloco para alterar a melodia de ``||music:dadadum||`` para ``||music:ba ding||``. 

```blocks
basic.forever(function () {
    if (sensors.infraredValue(InputPorts.P2) > 400) {
        actuators.StopMotor(OutputPorts.P8)
        basic.showLeds(`
            . . . . .
            . . # . .
            . # # # .
            . . # . .
            . . . . .
            `)
        music._playDefaultBackground(music.builtInPlayableMelody(Melodies.BaDing), music.PlaybackMode.InBackground)
    }
})
```

## Passo 10
Acesse a aba ``||basic:Básico||`` e adicione o comando ``||basic:pausa (ms) 100||`` abaixo do bloco musical.
Modifique a duração da pausa de **100 ms** para **2000 ms** (2 segundos).

```blocks
basic.forever(function () {
    if (sensors.infraredValue(InputPorts.P2) > 400) {
        actuators.StopMotor(OutputPorts.P8)
        basic.showLeds(`
            . . . . .
            . . # . .
            . # # # .
            . . # . .
            . . . . .
            `)
        music._playDefaultBackground(music.builtInPlayableMelody(Melodies.BaDing), music.PlaybackMode.InBackground)
        basic.pause(2000)
    }
})
```

## Passo 11
Retorne à aba ``||basic:Básico||`` e adicione o comando para ``||basic:limpar tela||``.

```blocks
basic.forever(function () {
    if (sensors.infraredValue(InputPorts.P2) > 400) {
        actuators.StopMotor(OutputPorts.P8)
        basic.showLeds(`
            . . . . .
            . . # . .
            . # # # .
            . . # . .
            . . . . .
            `)
        music._playDefaultBackground(music.builtInPlayableMelody(Melodies.BaDing), music.PlaybackMode.InBackground)
        basic.pause(2000)
        basic.clearScreen()
    }
})
```

## Passo 12
Feito isso, temos que programar a abelha para sair de cima do sensor e evitar uma detecção dupla.
Então, retorne ao menu de ``||actuators:Atuadores||`` e adicione o comando ``||actuators:Motor CC, definir velocidade 0 na porta P8||``.

```blocks
basic.forever(function () {
    if (sensors.infraredValue(InputPorts.P2) > 400) {
        actuators.StopMotor(OutputPorts.P8)
        basic.showLeds(`
            . . . . .
            . . # . .
            . # # # .
            . . # . .
            . . . . .
            `)
        music._playDefaultBackground(music.builtInPlayableMelody(Melodies.BaDing), music.PlaybackMode.InBackground)
        basic.pause(2000)
        basic.clearScreen()
        actuators.SetSpeedMotor(0, OutputPorts.P8)
    }
})
```

## Passo 13
Altere o valor de velocidade desse comando de **0** para **65**.

**Dica:** Se, eventualmente, seu motor não estiver girando, teste aumentar um pouco o valor de velocidade. Mas não exagere,
esse valor deve ser o mais baixo possível para facilitar a detecção da abelha pelo Sensor Infravermelho.

```blocks
basic.forever(function () {
    if (sensors.infraredValue(InputPorts.P2) > 400) {
        actuators.StopMotor(OutputPorts.P8)
        basic.showLeds(`
            . . . . .
            . . # . .
            . # # # .
            . . # . .
            . . . . .
            `)
        music._playDefaultBackground(music.builtInPlayableMelody(Melodies.BaDing), music.PlaybackMode.InBackground)
        basic.pause(2000)
        basic.clearScreen()
        actuators.SetSpeedMotor(65, OutputPorts.P8)
    }
})
```

## Passo 14
Retorne à aba ``||basic:Básico||`` e adicione outra ``||basic:pausa (ms) 100||``.
Modifique a duração da pausa de **100 ms** para **500 ms**.

```blocks
basic.forever(function () {
    if (sensors.infraredValue(InputPorts.P2) > 400) {
        actuators.StopMotor(OutputPorts.P8)
        basic.showLeds(`
            . . . . .
            . . # . .
            . # # # .
            . . # . .
            . . . . .
            `)
        music._playDefaultBackground(music.builtInPlayableMelody(Melodies.BaDing), music.PlaybackMode.InBackground)
        basic.pause(2000)
        basic.clearScreen()
        actuators.SetSpeedMotor(65, OutputPorts.P8)
        basic.pause(500)
    }
})
```

## Passo 15
Agora, vamos garantir que a abelha continue seu voo, adicionando os blocos de acionamento do motor fora do laço 
``||logic:se então||``. Para isso, replique os blocos ``||actuators:Motor CC, definir velocidade 0 na porta P8||``
e ``||basic:pausa (ms) 100||`` fora do laço.

```blocks
basic.forever(function () {
    if (sensors.infraredValue(InputPorts.P2) > 400) {
        actuators.StopMotor(OutputPorts.P8)
        basic.showLeds(`
            . . . . .
            . . # . .
            . # # # .
            . . # . .
            . . . . .
            `)
        music._playDefaultBackground(music.builtInPlayableMelody(Melodies.BaDing), music.PlaybackMode.InBackground)
        basic.pause(2000)
        basic.clearScreen()
        actuators.SetSpeedMotor(65, OutputPorts.P8)
        basic.pause(500)
    }
    actuators.SetSpeedMotor(0, OutputPorts.P8)
    basic.pause(100)
})
```

## Passo 16
Por fim, altere o valor da ``||actuators:velocidade||`` de **0** para **65** e da ``||basic:pausa||`` de **100** para **400**.

```blocks
basic.forever(function () {
    if (sensors.infraredValue(InputPorts.P2) > 400) {
        actuators.StopMotor(OutputPorts.P8)
        basic.showLeds(`
            . . . . .
            . . # . .
            . # # # .
            . . # . .
            . . . . .
            `)
        music._playDefaultBackground(music.builtInPlayableMelody(Melodies.BaDing), music.PlaybackMode.InBackground)
        basic.pause(2000)
        basic.clearScreen()
        actuators.SetSpeedMotor(65, OutputPorts.P8)
        basic.pause(500)
    }
    actuators.SetSpeedMotor(65, OutputPorts.P8)
    basic.pause(400)
})
```

## Passo 17
Assim, sua abelha polinizadora está pronta para voar! Transfira o código para o micro:bit e ajuste os valores
de velocidade, pausa ou detecção do sensor de acordo com sua necessidade!

```blocks

```

## Passo 18
Se necessário, confira o seu código clicando na lâmpada de dica.

```blocks
basic.forever(function () {
    if (sensors.infraredValue(InputPorts.P2) > 400) {
        actuators.StopMotor(OutputPorts.P8)
        basic.showLeds(`
            . . . . .
            . . # . .
            . # # # .
            . . # . .
            . . . . .
            `)
        music._playDefaultBackground(music.builtInPlayableMelody(Melodies.BaDing), music.PlaybackMode.InBackground)
        basic.pause(2000)
        basic.clearScreen()
        actuators.SetSpeedMotor(65, OutputPorts.P8)
        basic.pause(500)
    }
    actuators.SetSpeedMotor(65, OutputPorts.P8)
    basic.pause(400)
})
```

```package
fuzzyBot=github:Wolfloiz/pxt-fuzzyMakers
```