### @diffs true
# Circuitos Elétricos

## Passo 1
Neste tutorial, vamos programar o chuveiro que funciona em duas configurações:
inverno e verão. O potenciômetro servirá como o registro de água, ligando 
o chuveiro ao ser aberto e desligando ao ser fechado. Se o registro estiver 
aberto, o botão funcionará como chave comutadora para alternar entre inverno
e verão. Vamos usar o visor do micro:bit para exibir a posição dessa chave.

## Passo 2
Adicionalmente, na posição verão, ambos os motores (atuando como resistências)
devem funcionar. Na posição inverno, apenas o segundo motor vai girar. Por fim,
vamos representar a energia que atravessa o circuito através do LED de alto 
brilho, ajustando sua potência de acordo com a posição da chave seletora do chuveiro.

## Passo 3
Para começar, verifique se a biblioteca da Smart Makers já está importada 
em seu MakeCode. Se não estiver, clique na aba **+ Extensões**, 
copie o endereço "https://github.com/FuzzyMakers/pxt-smartMakers",
cole-o no campo de pesquisa da janela que se abriu e selecione a biblioteca.

## Passo 4
Clique no menu ``||Advanced:Avançado||``, acesse ``||Functions:Funções||`` e 
clique em **Fazer uma função...**.
Clique no campo editável do laço azul para criar uma função chamada 
``||functions:chuveiro||``. 
Um novo laço referente à função criada é adicionado automaticamente ao código.

```blocks
function chuveiro () {
	
}
basic.forever(function () {
	
})
```

## Passo 5
Acesse a aba ``||logic:Lógica||`` e adicione o bloco ``||logic:se então senão||`` 
dentro dessa nova ``||functions:função chuveiro||``.

```blocks
function chuveiro () {
    if (true) {
    	
    } else {
    	
    }
}
basic.forever(function () {
	
})
```

## Passo 6
Retorne à ``||logic:Lógica||`` e utilize o bloco comparador 
``||logic:0 = 0||`` para substituir o campo **verdadeiro** do bloco 
``||logic:se então senão||``.

```blocks
function chuveiro () {
    if (0 == 0) {
    	
    } else {
    	
    }
}
basic.forever(function () {
	
})
```

## Passo 7
Acesse a categoria ``||sensors:Sensores||`` e utilize o bloco  
``||sensors:valor do botão na porta P2||`` para substituir o primeiro campo do 
comparador.

```blocks
function chuveiro () {
    if (sensors.buttonValue(InputPorts.P2) == 0) {
    	
    } else {
    	
    }
}
basic.forever(function () {
	
})
```

## Passo 8
Altere a porta de ``||sensors:P2||`` para ``||sensors:P1||``.

```blocks
function chuveiro () {
    if (sensors.buttonValue(InputPorts.P1) == 0) {
    	
    } else {
    	
    }
}
basic.forever(function () {
	
})
```

## Passo 9
Acesse a categoria ``||basic:Básico||`` e adicione um comando 
``||basic:mostrar leds||`` dentro do ``||logic:então||``. Em seguida, 
clique nos quadrados para determinar quais LEDs acenderão. Selecione os 
terceiros LEDs das três primeiras colunas, seguidos do quarto LED da quarta
coluna e, por fim, o quinto LED da última coluna. 

 **Dica:** se precisar de ajuda, clique na lâmpada para visualizar melhor. 

```blocks
function chuveiro () {
    if (sensors.buttonValue(InputPorts.P1) == 0) {
        basic.showLeds(`
            . . . . .
            . . . . .
            # # # . .
            . . . # .
            . . . . #
            `)
    } else {
    	
    }
}
basic.forever(function () {
	
})
```function abastecer () {
    music.stopAllSounds()
    actuators.StopMotor(OutputPorts.P8)
    while (sensors.endstopValue(InputPorts.P2) == 1) {
        music.play(music.createSoundExpression(WaveShape.Sine, 188, 584, 255, 0, 200, SoundExpressionEffect.None, InterpolationCurve.Linear), music.PlaybackMode.UntilDone)
    }
}
let consumo = 100 + (20 * input.temperature() + 15 * input.lightLevel())


## Passo 10
Vá ao menu ``||actuators:Atuadores||`` e adicione um comando 
``||actuators:Motor CC, parar motor na porta P8||`` ainda dentro do
``||logic:então||``. Antes de prosseguir, altere a porta de ``||actuators:P8||`` 
para ``||actuators:P16||``.

```blocks
function chuveiro () {
    if (sensors.buttonValue(InputPorts.P1) == 0) {
        basic.showLeds(`
            . . . . .
            . . . . .
            # # # . .
            . . . # .
            . . . . #
            `)
        actuators.StopMotor(OutputPorts.P16)
    } else {
    	
    }
}
basic.forever(function () {
	
})
```

## Passo 11
Retorne ao menu ``||actuators:Atuadores||`` e adicione um comando 
``||actuators:Motor CC, definir velocidade 0 na porta P8||`` dentro do 
``||logic:então||``. Altere o valor de velocidade de **0** para **100** e a 
porta de ``||actuators:P8||`` para ``||actuators:P12||``.

```blocks
function chuveiro () {
    if (sensors.buttonValue(InputPorts.P1) == 0) {
        basic.showLeds(`
            . . . . .
            . . . . .
            # # # . .
            . . . # .
            . . . . #
            `)
        actuators.StopMotor(OutputPorts.P16)
        actuators.SetSpeedMotor(100, OutputPorts.P12)
    } else {
    	
    }
}
basic.forever(function () {
	
})
```

## Passo 12
Por fim, retorne ao menu ``||actuators:Atuadores||`` e adicione um comando 
``||actuators:LED de alto brilho, definir brilho 0 na porta P8||`` dentro do 
``||logic:então||``. Altere o valor do brilho de **0** para **1023**.

```blocks
function chuveiro () {
    if (sensors.buttonValue(InputPorts.P1) == 0) {
        basic.showLeds(`
            . . . . .
            . . . . .
            # # # . .
            . . . # .
            . . . . #
            `)
        actuators.StopMotor(OutputPorts.P16)
        actuators.SetSpeedMotor(100, OutputPorts.P12)
        actuators.SetBrightLED(1023, OutputPorts.P8)
    } else {
    	
    }
}
basic.forever(function () {
	
})
```

## Passo 13
Agora, prosseguindo para o ``||logic:senão||``, adicione um comando 
``||basic:mostrar leds||``, localizado na aba ``||basic:Básico||``.
Acenda os mesmos três primeiros LEDs que acendemos no outro bloco, porém,
modifique para acender o segundo LED da quarta coluna e o primeiro da quinta.

```blocks
function chuveiro () {
    if (sensors.buttonValue(InputPorts.P1) == 0) {
        basic.showLeds(`
            . . . . .
            . . . . .
            # # # . .
            . . . # .
            . . . . #
            `)
        actuators.StopMotor(OutputPorts.P16)
        actuators.SetSpeedMotor(100, OutputPorts.P12)
        actuators.SetBrightLED(1023, OutputPorts.P8)
    } else {
        basic.showLeds(`
            . . . . #
            . . . # .
            # # # . .
            . . . . .
            . . . . .
            `)
    }
}
basic.forever(function () {
	
})
```

## Passo 14
Retorne ao menu ``||actuators:Atuadores||`` e adicione dois comandos 
``||actuators:Motor CC, definir velocidade 0 na porta P8||`` dentro do 
``||logic:senão||``. Altere o valor de velocidade de ambos os blocos 
de **0** para **100**, e a porta de ``||actuators:P8||`` para 
``||actuators:P12||`` e ``||actuators:P16||``, respectivamente. 

```blocks
function chuveiro () {
    if (sensors.buttonValue(InputPorts.P1) == 0) {
        basic.showLeds(`
            . . . . .
            . . . . .
            # # # . .
            . . . # .
            . . . . #
            `)
        actuators.StopMotor(OutputPorts.P16)
        actuators.SetSpeedMotor(100, OutputPorts.P12)
        actuators.SetBrightLED(1023, OutputPorts.P8)
    } else {
        basic.showLeds(`
            . . . . #
            . . . # .
            # # # . .
            . . . . .
            . . . . .
            `)
        actuators.SetSpeedMotor(100, OutputPorts.P12)
        actuators.SetSpeedMotor(100, OutputPorts.P16)
    }
}
basic.forever(function () {
	
})
```

## Passo 15
Finalizando essa função, retorne ao menu ``||actuators:Atuadores||`` e adicione 
um comando ``||actuators:LED de alto brilho, definir brilho 0 na porta P8||`` 
dentro do ``||logic:senão||``. Altere o valor do brilho de **0** para **500**.

```blocks
function chuveiro () {
    if (sensors.buttonValue(InputPorts.P1) == 0) {
        basic.showLeds(`
            . . . . .
            . . . . .
            # # # . .
            . . . # .
            . . . . #
            `)
        actuators.StopMotor(OutputPorts.P16)
        actuators.SetSpeedMotor(100, OutputPorts.P12)
        actuators.SetBrightLED(1023, OutputPorts.P8)
    } else {
        basic.showLeds(`
            . . . . #
            . . . # .
            # # # . .
            . . . . .
            . . . . .
            `)
        actuators.SetSpeedMotor(100, OutputPorts.P12)
        actuators.SetSpeedMotor(100, OutputPorts.P16)
        actuators.SetBrightLED(500, OutputPorts.P8)
    }
}
basic.forever(function () {
	
})
```

## Passo 16
Agora, acesse a aba ``||logic:Lógica||`` e adicione o bloco ``||logic:se então senão||`` 
dentro do laço ``||basic:sempre||``.

```blocks
function chuveiro () {
    if (sensors.buttonValue(InputPorts.P1) == 0) {
        basic.showLeds(`
            . . . . .
            . . . . .
            # # # . .
            . . . # .
            . . . . #
            `)
        actuators.StopMotor(OutputPorts.P16)
        actuators.SetSpeedMotor(100, OutputPorts.P12)
        actuators.SetBrightLED(1023, OutputPorts.P8)
    } else {
        basic.showLeds(`
            . . . . #
            . . . # .
            # # # . .
            . . . . .
            . . . . .
            `)
        actuators.SetSpeedMotor(100, OutputPorts.P12)
        actuators.SetSpeedMotor(100, OutputPorts.P16)
        actuators.SetBrightLED(500, OutputPorts.P8)
    }
}
basic.forever(function () {
    if (true) {
    	
    } else {
    	
    }
})
```

## Passo 17
Retorne à ``||logic:Lógica||`` e utilize o bloco comparador 
``||logic:0 < 0||`` para substituir o campo **verdadeiro** do bloco 
``||logic:se então senão||``.

```blocks
function chuveiro () {
    if (sensors.buttonValue(InputPorts.P1) == 0) {
        basic.showLeds(`
            . . . . .
            . . . . .
            # # # . .
            . . . # .
            . . . . #
            `)
        actuators.StopMotor(OutputPorts.P16)
        actuators.SetSpeedMotor(100, OutputPorts.P12)
        actuators.SetBrightLED(1023, OutputPorts.P8)
    } else {
        basic.showLeds(`
            . . . . #
            . . . # .
            # # # . .
            . . . . .
            . . . . .
            `)
        actuators.SetSpeedMotor(100, OutputPorts.P12)
        actuators.SetSpeedMotor(100, OutputPorts.P16)
        actuators.SetBrightLED(500, OutputPorts.P8)
    }
}
basic.forever(function () {
    if (0 < 0) {
    	
    } else {
    	
    }
})
```

## Passo 18
Altere o sinal desse comparador de **<** para **>** e o valor do segundo 
campo de **0** para **10**.

```blocks
function chuveiro () {
    if (sensors.buttonValue(InputPorts.P1) == 0) {
        basic.showLeds(`
            . . . . .
            . . . . .
            # # # . .
            . . . # .
            . . . . #
            `)
        actuators.StopMotor(OutputPorts.P16)
        actuators.SetSpeedMotor(100, OutputPorts.P12)
        actuators.SetBrightLED(1023, OutputPorts.P8)
    } else {
        basic.showLeds(`
            . . . . #
            . . . # .
            # # # . .
            . . . . .
            . . . . .
            `)
        actuators.SetSpeedMotor(100, OutputPorts.P12)
        actuators.SetSpeedMotor(100, OutputPorts.P16)
        actuators.SetBrightLED(500, OutputPorts.P8)
    }
}
basic.forever(function () {
    if (0 > 10) {
    	
    } else {
    	
    }
})
```

## Passo 19
Acesse a categoria ``||sensors:Sensores||`` e utilize o bloco  
``||sensors:valor do potenciômetro na porta P2||`` para substituir o primeiro 
campo do comparador.

```blocks
function chuveiro () {
    if (sensors.buttonValue(InputPorts.P1) == 0) {
        basic.showLeds(`
            . . . . .
            . . . . .
            # # # . .
            . . . # .
            . . . . #
            `)
        actuators.StopMotor(OutputPorts.P16)
        actuators.SetSpeedMotor(100, OutputPorts.P12)
        actuators.SetBrightLED(1023, OutputPorts.P8)
    } else {
        basic.showLeds(`
            . . . . #
            . . . # .
            # # # . .
            . . . . .
            . . . . .
            `)
        actuators.SetSpeedMotor(100, OutputPorts.P12)
        actuators.SetSpeedMotor(100, OutputPorts.P16)
        actuators.SetBrightLED(500, OutputPorts.P8)
    }
}
basic.forever(function () {
    if (sensors.dimmerValue(InputPorts.P2) > 10) {
    	
    } else {
    	
    }
})
```

## Passo 20
Clique em **Avançado**, acesse a aba ``||functions:Funções||`` e adicione o 
comando ``||functions:ligar chuveiro||`` dentro do ``||logic:então||``.

```blocks
function chuveiro () {
    if (sensors.buttonValue(InputPorts.P1) == 0) {
        basic.showLeds(`
            . . . . .
            . . . . .
            # # # . .
            . . . # .
            . . . . #
            `)
        actuators.StopMotor(OutputPorts.P16)
        actuators.SetSpeedMotor(100, OutputPorts.P12)
        actuators.SetBrightLED(1023, OutputPorts.P8)
    } else {
        basic.showLeds(`
            . . . . #
            . . . # .
            # # # . .
            . . . . .
            . . . . .
            `)
        actuators.SetSpeedMotor(100, OutputPorts.P12)
        actuators.SetSpeedMotor(100, OutputPorts.P16)
        actuators.SetBrightLED(500, OutputPorts.P8)
    }
}
basic.forever(function () {
    if (sensors.dimmerValue(InputPorts.P2) > 10) {
        chuveiro()
    } else {
    	
    }
})
```

## Passo 21
Dentro do ``||logic:senão||``, adicione dois blocos 
``||actuators:Motor CC, parar motor na porta P8||``. Antes de prosseguir,
altere as portas de ``||actuators:P8||`` para  ``||actuators:P12||`` e 
``||actuators:P16||``, respectivamente.

```blocks
function chuveiro () {
    if (sensors.buttonValue(InputPorts.P1) == 0) {
        basic.showLeds(`
            . . . . .
            . . . . .
            # # # . .
            . . . # .
            . . . . #
            `)
        actuators.StopMotor(OutputPorts.P16)
        actuators.SetSpeedMotor(100, OutputPorts.P12)
        actuators.SetBrightLED(1023, OutputPorts.P8)
    } else {
        basic.showLeds(`
            . . . . #
            . . . # .
            # # # . .
            . . . . .
            . . . . .
            `)
        actuators.SetSpeedMotor(100, OutputPorts.P12)
        actuators.SetSpeedMotor(100, OutputPorts.P16)
        actuators.SetBrightLED(500, OutputPorts.P8)
    }
}
basic.forever(function () {
    if (sensors.dimmerValue(InputPorts.P2) > 10) {
        chuveiro()
    } else {
        actuators.StopMotor(OutputPorts.P12)
        actuators.StopMotor(OutputPorts.P16)
    }
})
```

## Passo 22
Retorne ao menu ``||actuators:Atuadores||`` e adicione 
um comando ``||actuators:LED de alto brilho, definir brilho 0 na porta P8||`` 
dentro do ``||logic:senão||``.


```blocks
function chuveiro () {
    if (sensors.buttonValue(InputPorts.P1) == 0) {
        basic.showLeds(`
            . . . . .
            . . . . .
            # # # . .
            . . . # .
            . . . . #
            `)
        actuators.StopMotor(OutputPorts.P16)
        actuators.SetSpeedMotor(100, OutputPorts.P12)
        actuators.SetBrightLED(1023, OutputPorts.P8)
    } else {
        basic.showLeds(`
            . . . . #
            . . . # .
            # # # . .
            . . . . .
            . . . . .
            `)
        actuators.SetSpeedMotor(100, OutputPorts.P12)
        actuators.SetSpeedMotor(100, OutputPorts.P16)
        actuators.SetBrightLED(500, OutputPorts.P8)
    }
}
basic.forever(function () {
    if (sensors.dimmerValue(InputPorts.P2) > 10) {
        chuveiro()
    } else {
        actuators.StopMotor(OutputPorts.P12)
        actuators.StopMotor(OutputPorts.P16)
        actuators.SetBrightLED(0, OutputPorts.P8)
    }
})
```


## Passo 23
Agora, seu código está pronto! Baixe-o para o micro:bit e teste ligar o chuveiro
com o potenciômetro e alterar sua potência com o botão. Observe se os motores
foram acionados nos momentos corretos e se o brilho do LED está indicando 
a potência do chuveiro corretamente.

```blocks
```

## Passo 24
Se necessário, confira o seu código clicando na lâmpada de dica.

```blocks
function chuveiro () {
    if (sensors.buttonValue(InputPorts.P1) == 0) {
        basic.showLeds(`
            . . . . .
            . . . . .
            # # # . .
            . . . # .
            . . . . #
            `)
        actuators.StopMotor(OutputPorts.P16)
        actuators.SetSpeedMotor(100, OutputPorts.P12)
        actuators.SetBrightLED(1023, OutputPorts.P8)
    } else {
        basic.showLeds(`
            . . . . #
            . . . # .
            # # # . .
            . . . . .
            . . . . .
            `)
        actuators.SetSpeedMotor(100, OutputPorts.P12)
        actuators.SetSpeedMotor(100, OutputPorts.P16)
        actuators.SetBrightLED(500, OutputPorts.P8)
    }
}
basic.forever(function () {
    if (sensors.dimmerValue(InputPorts.P2) > 10) {
        chuveiro()
    } else {
        actuators.StopMotor(OutputPorts.P12)
        actuators.StopMotor(OutputPorts.P16)
        actuators.SetBrightLED(0, OutputPorts.P8)
    }
})
```

```package
fuzzyBot=github:FuzzyMakers/pxt-fuzzyMakers
```