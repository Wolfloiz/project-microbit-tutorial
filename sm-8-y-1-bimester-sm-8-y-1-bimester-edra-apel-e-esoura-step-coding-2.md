### @diffs true
# Pedra, Papel e Tesoura

## Passo 1
Nesse tutorial, vamos aprender como programar um "robô" capaz de jogar Pedra, Papel e Tesoura conosco.
Vamos usar o sensor infravermelho para identificar quando jogamos e os LEDs do próprio micro:bit para exibir os 
símbolos da jogada do robô.

## Passo 2
Para começar, verifique se a biblioteca da Smart Makers já está importada em seu MakeCode.
Se não estiver, clique na aba **+ Extensões**, copie o endereço "https://github.com/FuzzyMakers/pxt-smartMakers",
cole-o no campo de pesquisa da janela que se abriu e selecione a biblioteca.

## Passo 3
Acesse a aba ``||input:Entrada||`` e adicione dois laços ``||input:no botão A pressionado||`` em sua área de programação.
Clique na seta para alterar o botão de um deles de ``||input:botão A||`` para ``||input:botão B||``.

```blocks
input.onButtonPressed(Button.A, function () {
	
})
input.onButtonPressed(Button.B, function () {
	
})
basic.forever(function () {
	
})
```

## Passo 4
Acesse o menu ``||variables:Variáveis||`` e clique em **"Fazer uma variável..."**.
Vamos criar três variáveis chamadas: ``||variables:jogada||``, ``||variables:robo||`` e ``||variables:jogador||``. 
Por fim, adicione o bloco ``||variables:definir jogador para 0||`` que
aparecerá ao criá-la, dentro do laço ``||input:no botão A pressionado||``.  

```blocks
let jogador = 0
input.onButtonPressed(Button.A, function () {
    jogador = 0
})
input.onButtonPressed(Button.B, function () {
	
})
basic.forever(function () {
	
})
```

## Passo 5
Volte à ``||variables:Variáveis||`` e adicione o ``||variables:definir jogador para 0||`` dentro do outro bloco
``||input:no botão B pressionado||``. Entretanto, clique na seta para modificar a variável de ``||variables:jogador||`` 
para ``||variables:robo||``.

```blocks
let jogador = 0
let robo = 0
input.onButtonPressed(Button.A, function () {
    jogador = 0
})
input.onButtonPressed(Button.B, function () {
    robo = 0
})
basic.forever(function () {
	
})
```

## Passo 6
Altere os valores de definição de ambas as variáveis de **0** para **1**. Esses botões 
deverão ser pressionados para indicar ao micro:bit quem ganhou aquela rodada. Ou seja, se você
ganhar, pressione o ``||input:botão A||`` e, se o robô ganhar, pressione o ``||input:botão B||``.

```blocks
let jogador = 0
let robo = 0
input.onButtonPressed(Button.A, function () {
    jogador = 1
})
input.onButtonPressed(Button.B, function () {
    robo = 1
})
basic.forever(function () {
	
})
```

## Passo 7
Retorne à categoria ``||input:Entrada||`` e adicione o bloco ``||input:no logotipo pressionado||``.  

```blocks
let jogador = 0
let robo = 0
input.onLogoEvent(TouchButtonEvent.Pressed, function () {
	
})
input.onButtonPressed(Button.A, function () {
    jogador = 1
})
input.onButtonPressed(Button.B, function () {
    robo = 1
})
basic.forever(function () {
	
})
```

## Passo 8
Acesse a aba ``||basic:Básico||`` e adicione o comando ``||basic:mostrar string||`` dentro do bloco 
``||input:no logotipo pressionado||``.

```blocks
let jogador = 0
let robo = 0
input.onLogoEvent(TouchButtonEvent.Pressed, function () {
    basic.showString("Hello!")
})
input.onButtonPressed(Button.A, function () {
    jogador = 1
})
input.onButtonPressed(Button.B, function () {
    robo = 1
})
basic.forever(function () {
	
})
```

## Passo 9
Em seguida, clique em **Avançado** para abrir outras categorias. Acesse 
``||text:Texto||`` e selecione o bloco ``||text:unir||`` para substituir o texto *"Hello!"* do comando
``||basic:mostrar string||``.

```blocks
let jogador = 0
let robo = 0
input.onLogoEvent(TouchButtonEvent.Pressed, function () {
    basic.showString(" " + " ")
})
input.onButtonPressed(Button.A, function () {
    jogador = 1
})
input.onButtonPressed(Button.B, function () {
    robo = 1
})
basic.forever(function () {
	
})
```

## Passo 10
No primeiro campo desse bloco, adicione o bloco da variável ``||variables:jogador||`` localizado na aba ``||variables:Variáveis||``.
Em seguida, escreva um **"X"** no outro campo e clique em **+** para adicionar um terceiro.
Nesse terceiro campo, insira a variável ``||variables:robo||``. Assim, ao tocar no logotipo do micro:bit
vamos exibir a pontuação da partida.

```blocks
let jogador = 0
let robo = 0
input.onLogoEvent(TouchButtonEvent.Pressed, function () {
    basic.showString("" + jogador + " X " + robo)
})
input.onButtonPressed(Button.A, function () {
    jogador = 1
})
input.onButtonPressed(Button.B, function () {
    robo = 1
})
basic.forever(function () {
	
})
```

## Passo 11
Acesse a aba ``||logic:Lógica||`` e adicione um bloco ``||logic:se então||``
dentro do laço ``||basic:sempre||``.

```blocks
let jogador = 0
let robo = 0
input.onLogoEvent(TouchButtonEvent.Pressed, function () {
    basic.showString("" + jogador + " X " + robo)
})
input.onButtonPressed(Button.A, function () {
    jogador = 1
})
input.onButtonPressed(Button.B, function () {
    robo = 1
})
basic.forever(function () {
    if (true) {
    	
    }
})
```

## Passo 12
Retorne à ``||logic:Lógica||`` e adicione um bloco comparador ``||logic:0 < 0||``
dentro do campo ***verdadeiro** do ``||logic:se então||``. Antes de continuar,
altere o sinal desse comparador de **<** para **>**.

```blocks
let jogador = 0
let robo = 0
input.onLogoEvent(TouchButtonEvent.Pressed, function () {
    basic.showString("" + jogador + " X " + robo)
})
input.onButtonPressed(Button.A, function () {
    jogador = 1
})
input.onButtonPressed(Button.B, function () {
    robo = 1
})
basic.forever(function () {
    if (0 > 0) {
    	
    }
})
```

## Passo 13
Altere o primeiro campo desse comparador para o bloco ``||sensors:Valor do sensor infravermelho na porta P2||``
localizado na aba ``||sensors:Sensores||``. Em seguida, altere o segundo campo do comparador de **0** para **300**.

```blocks
let jogador = 0
let robo = 0
input.onLogoEvent(TouchButtonEvent.Pressed, function () {
    basic.showString("" + jogador + " X " + robo)
})
input.onButtonPressed(Button.A, function () {
    jogador = 1
})
input.onButtonPressed(Button.B, function () {
    robo = 1
})
basic.forever(function () {
    if (sensors.infraredValue(InputPorts.P2) > 300) {
    	
    }
})
```

## Passo 14
Agora, dentro do ``||logic:então||``, adicione um comando ``||basic:limpar tela||``, encontrado
na aba ``||basic:Básico||``.

```blocks
let jogador = 0
let robo = 0
input.onLogoEvent(TouchButtonEvent.Pressed, function () {
    basic.showString("" + jogador + " X " + robo)
})
input.onButtonPressed(Button.A, function () {
    jogador = 1
})
input.onButtonPressed(Button.B, function () {
    robo = 1
})
basic.forever(function () {
    if (sensors.infraredValue(InputPorts.P2) > 300) {
        basic.clearScreen()
    }
})
```

## Passo 15
Retorne à ``||variables:Variáveis||`` e adicione o bloco ``||variables:definir jogada para 0||``
dentro do ``||logic:então||``.
Se o seu bloco de definição estiver com uma variável diferente, adicione-o assim mesmo, 
depois clique na seta para modificar a variável para ``||variables:jogada||``.

```blocks
let jogador = 0
let robo = 0
input.onLogoEvent(TouchButtonEvent.Pressed, function () {
    basic.showString("" + jogador + " X " + robo)
})
input.onButtonPressed(Button.A, function () {
    jogador = 1
})
input.onButtonPressed(Button.B, function () {
    robo = 1
})
basic.forever(function () {
    if (sensors.infraredValue(InputPorts.P2) > 300) {
        basic.clearScreen()
    }
})
```

## Passo 16
Acesse a categoria ``||math:Matemática||`` e insira o bloco ``||math:escolher aleatório 0 até 10||``
dentro do campo de valor do bloco de definição da variável. Antes de prosseguir, altere o segundo número 
do intervalo de **10** para **3**.

```blocks
let jogador = 0
let robo = 0
let jogada = 0
input.onLogoEvent(TouchButtonEvent.Pressed, function () {
    basic.showString("" + jogador + " X " + robo)
})
input.onButtonPressed(Button.A, function () {
    jogador = 1
})
input.onButtonPressed(Button.B, function () {
    robo = 1
})
basic.forever(function () {
    if (sensors.infraredValue(InputPorts.P2) > 300) {
        basic.clearScreen()
        jogada = randint(0, 3)
    }
})
```

## Passo 17
Abaixo desse bloco, mas ainda dentro do ``||logic:então||``, adicione um bloco 
``||logic:se então senão||``. Clique no sinal **+** desse bloco para adicionar outra condição ``||logic:senão se||``.

```blocks
let jogador = 0
let robo = 0
let jogada = 0
input.onLogoEvent(TouchButtonEvent.Pressed, function () {
    basic.showString("" + jogador + " X " + robo)
})
input.onButtonPressed(Button.A, function () {
    jogador = 1
})
input.onButtonPressed(Button.B, function () {
    robo = 1
})
basic.forever(function () {
    if (sensors.infraredValue(InputPorts.P2) > 300) {
        basic.clearScreen()
        jogada = randint(0, 3)
        if (true) {
        	
        } else if (false) {
        	
        } else {
        	
        }
    }
})
```

## Passo 18
Insira blocos comparadores ``||logic:0 = 0||`` nos campos **verdadeiro** e **falso** desses blocos 
condicionais.

```blocks
let jogador = 0
let robo = 0
let jogada = 0
input.onLogoEvent(TouchButtonEvent.Pressed, function () {
    basic.showString("" + jogador + " X " + robo)
})
input.onButtonPressed(Button.A, function () {
    jogador = 1
})
input.onButtonPressed(Button.B, function () {
    robo = 1
})
basic.forever(function () {
    if (sensors.infraredValue(InputPorts.P2) > 300) {
        basic.clearScreen()
        jogada = randint(0, 3)
        if (0 == 0) {
        	
        } else if (0 == 0) {
        	
        } else {
        	
        }
    }
})
```

## Passo 19
O primeiro campo de ambos os comparadores deve ser a variável ``||variables:jogada||``.
Enquanto isso, o segundo campo dos comparadores serão **1** e **2** respectivamente.

```blocks
let jogador = 0
let robo = 0
let jogada = 0
input.onLogoEvent(TouchButtonEvent.Pressed, function () {
    basic.showString("" + jogador + " X " + robo)
})
input.onButtonPressed(Button.A, function () {
    jogador = 1
})
input.onButtonPressed(Button.B, function () {
    robo = 1
})
basic.forever(function () {
    if (sensors.infraredValue(InputPorts.P2) > 300) {
        basic.clearScreen()
        jogada = randint(0, 3)
        if (jogada == 1) {
        	
        } else if (jogada == 2) {
        	
        } else {
        	
        }
    }
})
```

## Passo 20
Agora, dentro de cada ``||logic:então||`` e do ``||logic:senão||``, adicione blocos 
``||basic:mostrar ícone||``, localizados na categoria ``||basic:Básico||``.

```blocks
let jogador = 0
let robo = 0
let jogada = 0
input.onLogoEvent(TouchButtonEvent.Pressed, function () {
    basic.showString("" + jogador + " X " + robo)
})
input.onButtonPressed(Button.A, function () {
    jogador = 1
})
input.onButtonPressed(Button.B, function () {
    robo = 1
})
basic.forever(function () {
    if (sensors.infraredValue(InputPorts.P2) > 300) {
        basic.clearScreen()
        jogada = randint(0, 3)
        if (jogada == 1) {
            basic.showIcon(IconNames.Heart)
        } else if (jogada == 2) {
            basic.showIcon(IconNames.Heart)
        } else {
            basic.showIcon(IconNames.Heart)
        }
    }
})
```

## Passo 21
Clique nas setas desses blocos para alterar os ícones exibidos para simbolizar o papel (losango/alvo), a pedra (quadrado) e 
a tesoura. 

```blocks
let jogador = 0
let robo = 0
let jogada = 0
input.onLogoEvent(TouchButtonEvent.Pressed, function () {
    basic.showString("" + jogador + " X " + robo)
})
input.onButtonPressed(Button.A, function () {
    jogador = 1
})
input.onButtonPressed(Button.B, function () {
    robo = 1
})
basic.forever(function () {
    if (sensors.infraredValue(InputPorts.P2) > 300) {
        basic.clearScreen()
        jogada = randint(0, 3)
        if (jogada == 1) {
            basic.showIcon(IconNames.Target)
        } else if (jogada == 2) {
            basic.showIcon(IconNames.Square)
        } else {
            basic.showIcon(IconNames.Scissors)
        }
    }
})
```

## Passo 22
Agora, adicione um bloco de ``||basic:pausa (ms) 100||`` fora do ``||logic:se então senão se||`` dos blocos de 
``||basic:mostrar ícone||``, mas ainda dentro do ``||logic:se então||`` antigo. Antes de continuar, altere
a duração dessa ``||basic:pausa||`` de **100 ms** para **2000 ms** (2 segundos).     

```blocks
let jogador = 0
let robo = 0
let jogada = 0
input.onLogoEvent(TouchButtonEvent.Pressed, function () {
    basic.showString("" + jogador + " X " + robo)
})
input.onButtonPressed(Button.A, function () {
    jogador = 1
})
input.onButtonPressed(Button.B, function () {
    robo = 1
})
basic.forever(function () {
    if (sensors.infraredValue(InputPorts.P2) > 300) {
        basic.clearScreen()
        jogada = randint(0, 3)
        if (jogada == 1) {
            basic.showIcon(IconNames.Target)
        } else if (jogada == 2) {
            basic.showIcon(IconNames.Square)
        } else {
            basic.showIcon(IconNames.Scissors)
        }
        basic.pause(2000)
    }
})
```

## Passo 23
Imediatamente abaixo da ``||basic:pausa||``, adicione outro bloco ``||basic:limpar tela||``,
localizado na categoria  ``||basic:Básico||``.  

```blocks
let jogador = 0
let robo = 0
let jogada = 0
input.onLogoEvent(TouchButtonEvent.Pressed, function () {
    basic.showString("" + jogador + " X " + robo)
})
input.onButtonPressed(Button.A, function () {
    jogador = 1
})
input.onButtonPressed(Button.B, function () {
    robo = 1
})
basic.forever(function () {
    if (sensors.infraredValue(InputPorts.P2) > 300) {
        basic.clearScreen()
        jogada = randint(0, 3)
        if (jogada == 1) {
            basic.showIcon(IconNames.Target)
        } else if (jogada == 2) {
            basic.showIcon(IconNames.Square)
        } else {
            basic.showIcon(IconNames.Scissors)
        }
        basic.pause(2000)
        basic.clearScreen()
    }
})
```

## Passo 24

Agora seu código está pronto! Baixe-o para o micro:bit e teste-o. 
- O botão A marca o ponto para o jogador (usuário);
- O botão B marca o ponto para o robô.
- Pressione o logotipo para visualizar o placar.
- E, para jogar, aproxime do sensor infravermelho a sua mão com sua jogada. 
```blocks
```

## Passo 25
Se necessário, confira o seu código clicando na lâmpada de dica.

```blocks
let jogador = 0
let robo = 0
let jogada = 0
input.onLogoEvent(TouchButtonEvent.Pressed, function () {
    basic.showString("" + jogador + " X " + robo)
})
input.onButtonPressed(Button.A, function () {
    jogador = 1
})
input.onButtonPressed(Button.B, function () {
    robo = 1
})
basic.forever(function () {
    if (sensors.infraredValue(InputPorts.P2) > 300) {
        basic.clearScreen()
        jogada = randint(0, 3)
        if (jogada == 1) {
            basic.showIcon(IconNames.Target)
        } else if (jogada == 2) {
            basic.showIcon(IconNames.Square)
        } else {
            basic.showIcon(IconNames.Scissors)
        }
        basic.pause(2000)
        basic.clearScreen()
    }
})
```

```package
fuzzyBot=github:FuzzyMakers/pxt-fuzzyMakers
```
