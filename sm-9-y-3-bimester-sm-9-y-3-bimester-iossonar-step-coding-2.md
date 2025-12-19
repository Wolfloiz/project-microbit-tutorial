### @diffs true
# Biossonar

## Passo 1
Neste tutorial, vamos programar uma simulação do sistema biossonar dos morcegos, utilizando o sensor infravermelho
e o micro:bit.

## Passo 2
Para começar, verifique se a biblioteca da Smart Makers já está importada 
em seu MakeCode. Se não estiver, clique na aba **+ Extensões**, 
copie o endereço "https://github.com/FuzzyMakers/pxt-smartMakers", 
cole-o no campo de pesquisa da janela que se abriu e selecione a biblioteca. 

## Passo 3
Acesse o menu ``||variables:Variáveis||`` e clique em 
**"Fazer uma variável..."**. Crie uma variável chamada
``||variables:direção||``.
Repita o processo para criar outras duas variáveis: ``||variables:índice||`` e ``||variables:sentido||``.


```blocks
```

## Passo 4
Em seguida, arraste dois blocos ``||variables:definir sentido para 0||`` 
para o bloco ``||basic:no iniciar||``. 
Altere o valor da variável sentido de **0** para **1** e mude o outro bloco para 
``||variables:definir índice para 0||``.

```blocks
let índice = 0
let sentido = 1
```

## Passo 5


Clique no menu ``||Advanced:Avançado||``, acesse a aba ``||array:Matriz||``, pegue o bloco 
``||variables:definir lista para matriz de 0 1 - +||`` 
e insira-o no bloco ``||basic:no iniciar||``.
Selecione a variável ``||variables:direção||`` no lugar de ``||variables:lista||``, 
clique no botão **+** para abrir mais um campo na matriz, por fim troque os valores da matriz para **0**, **500** e **1000**.

```blocks
let índice = 0
let sentido = 1
let direção = [0, 500, 1000]
```

## Passo 6
No menu ``||actuators:Atuadores||`` busque o bloco ``||actuators:Motor CC, definir velocidade 0 na porta P8||`` e adicione-o
dentro do ``||basic:no iniciar||``.
Mude o valor da velocidade para **500** e a porta para ``||actuators:P16||``.


```blocks
let índice = 0
let sentido = 1
let direção = [0, 500, 1000]
actuators.SetSpeedMotor(500, OutputPorts.P16)

```

## Passo 7
Volte à categoria ``||actuators:Atuadores||``, pegue o bloco ``||actuators:Servo, definir posição 0 porta P8 modo Knob||``
e insira-o no final do bloco ``||basic:no iniciar||``.

```blocks
let índice = 0
let sentido = 1
let direção = [0, 500, 1000]
actuators.SetSpeedMotor(500, OutputPorts.P16)
actuators.SetAngleServoKnob(0, OutputPorts.P8)
```

## Passo 8

Clique no menu ``||Advanced:Avançado||``, acesse ``||Functions:Funções||`` e 
clique em **Fazer uma função...**.
Clique no campo editável do laço azul para criar uma função chamada 
``||functions:desviar||``. 
Um novo laço referente à função criada é adicionado automaticamente à área de programação.


```blocks
function desviar () {
	
}
let índice = 0
let sentido = 1
let direção = [0, 500, 1000]
actuators.SetSpeedMotor(500, OutputPorts.P16)
actuators.SetAngleServoKnob(0, OutputPorts.P8)
```

## Passo 9
Na categoria ``||variables:Variáveis||``, selecione o bloco ``||variables:alterar sentido por 1||``
e posicione-o na função ``||functions:desviar||``.
Mude a variável que será alterada de ``||variables:sentido||`` para ``||variables:índice||``  e ajuste o valor de 
seu incremento de **1** para ``||variables:sentido||``.
```blocks
function desviar () {
    índice += sentido
}
let sentido = 0
let índice = 0
sentido = 1
let direção = [0, 500, 1000]
actuators.SetSpeedMotor(500, OutputPorts.P16)
actuators.SetAngleServoKnob(0, OutputPorts.P8)
```

## Passo 10
Acesse a categoria ``||logic:Lógica||``, pegue a condicional ``||logic:se então senão||``
e insira-a dentro da função ``||functions:desviar||``. 
Clique no botão **+** para criar mais uma condição ``||logic:senão se||``. 

```blocks
function desviar () {
    índice += sentido
    if (true) {
    	
    } else if (false) {
    	
    } else {
    	
    }
}
let sentido = 0
let índice = 0
sentido = 1
let direção = [0, 500, 1000]
actuators.SetSpeedMotor(500, OutputPorts.P16)
actuators.SetAngleServoKnob(0, OutputPorts.P8)
```


## Passo 11
Volte ao menu ``||logic:Lógica||``, pegue dois comparadores ``||logic:0 < 0||``
e substitua as condições **verdadeiro** e **falso** da condicional.



```blocks
function desviar () {
    índice += sentido
    if (0 < 0) {
    	
    } else if (0 < 0) {
    	
    } else {
    	
    }
}
let sentido = 0
let índice = 0
sentido = 1
let direção = [0, 500, 1000]
actuators.SetSpeedMotor(500, OutputPorts.P16)
actuators.SetAngleServoKnob(0, OutputPorts.P8)


```

## Passo 12

Agora atualize os campos do primeiro comparador. Vá até a aba ``||variables:Variáveis||``,
clique no bloco ``||variables:índice||`` e troque o primeiro **0** do comparador. 
No menu ``||math:Matemática||`` pegue uma operação de subtração ``||math:0 - 0||`` e substitua o segundo **0** do comparador.
Altere o sinal do comparador para **>**.
```blocks
function desviar () {
    índice += sentido
    if (índice > 0 - 0) {
    	
    } else if (0 < 0) {
    	
    } else {
    	
    }
}
let sentido = 0
let índice = 0
índice = 0
sentido = 1
let direção = [0, 500, 1000]
actuators.SetSpeedMotor(500, OutputPorts.P16)
actuators.SetAngleServoKnob(0, OutputPorts.P8)

```

## Passo 13

Em seguida, atualize os números da subtração. Volte à categoria ``||array:Matriz||``, clique
no bloco ``||array:comprimento da matriz lista||`` e substitua o primeiro campo da subtração. Mude a variável de 
``||variables:lista||`` para ``||variables:direção||``. Antes de prosseguir, 
edite o segundo campo da subtração para **1**.

```blocks
function desviar () {
    índice += sentido
    if (índice > direção.length - 1) {
    	
    } else if (0 < 0) {
    	
    } else {
    	
    }
}
let direção: number[] = []
let sentido = 0
let índice = 0
índice = 0
sentido = 1
direção = [0, 500, 1000]
actuators.SetSpeedMotor(500, OutputPorts.P16)
actuators.SetAngleServoKnob(0, OutputPorts.P8)
```
## Passo 14

Copie e cole as definições das variáveis ``||variables:índice||`` e ``||variables:sentido||`` 
do bloco ``||basic:no iniciar||`` na condicional ``||logic:se então||``.


```blocks
function desviar () {
    índice += sentido
    if (índice > direção.length - 1) {
        índice = 0
        sentido = 1
    } else if (0 < 0) {
    	
    } else {
    	
    }
}
let direção: number[] = []
let sentido = 0
let índice = 0
índice = 0
sentido = 1
direção = [0, 500, 1000]
actuators.SetSpeedMotor(500, OutputPorts.P16)
actuators.SetAngleServoKnob(0, OutputPorts.P8)

```

## Passo 15

Duplique a operação de subtração do comparador e coloque-a no valor da definição 
da variável ``||variables:índice||``, edite o segundo campo da subtração para **2**.
Altere o valor de ``||variables:sentido||`` de **1** para **-1**.
```blocks
function desviar () {
    índice += sentido
    if (índice > direção.length - 1) {
        índice = direção.length - 2
        sentido = -1
    } else if (0 < 0) {
    	
    } else {
    	
    }
}
let direção: number[] = []
let sentido = 0
let índice = 0
índice = 0
sentido = 1
direção = [0, 500, 1000]
actuators.SetSpeedMotor(500, OutputPorts.P16)
actuators.SetAngleServoKnob(0, OutputPorts.P8)

```

## Passo 16

Atualize os campos do outro comparador. Vá até a aba ``||variables:Variáveis||``,
clique no bloco ``||variables:índice||`` e troque o primeiro **0** do comparador. 


```blocks
function desviar () {
    índice += sentido
    if (índice > direção.length - 1) {
        índice = direção.length - 2
        sentido = -1
    } else if (índice < 0) {
    	
    } else {
    	
    }
}
let direção: number[] = []
let sentido = 0
let índice = 0
índice = 0
sentido = 1
direção = [0, 500, 1000]
actuators.SetSpeedMotor(500, OutputPorts.P16)
actuators.SetAngleServoKnob(0, OutputPorts.P8)


```

## Passo 17

Copie e cole as definições das variáveis ``||variables:índice||`` e ``||variables:sentido||`` 
do bloco ``||basic:no iniciar||`` na condicional ``||logic:senão se então||``.
Edite o valor de índice de **0** para **1**.

```blocks
function desviar () {
    índice += sentido
    if (índice > direção.length - 1) {
        índice = direção.length - 2
        sentido = -1
    } else if (índice < 0) {
        índice = 1
        sentido = 1
    } else {
    	
    }
}
let direção: number[] = []
let sentido = 0
let índice = 0
índice = 0
sentido = 1
direção = [0, 500, 1000]
actuators.SetSpeedMotor(500, OutputPorts.P16)
actuators.SetAngleServoKnob(0, OutputPorts.P8)
```

## Passo 18
Clique no botão **-** da condição ``||logic:senão -||`` para removê-la.
```blocks
function desviar () {
    índice += sentido
    if (índice > direção.length - 1) {
        índice = direção.length - 2
        sentido = -1
    } else if (índice < 0) {
        índice = 1
        sentido = 1
    }
}
let direção: number[] = []
let sentido = 0
let índice = 0
índice = 0
sentido = 1
direção = [0, 500, 1000]
actuators.SetSpeedMotor(500, OutputPorts.P16)
actuators.SetAngleServoKnob(0, OutputPorts.P8)
```

## Passo 19

Acesse a categoria ``||actuators:Atuadores||`` e adicione um comando 
``||actuators:Servo, definir posição 0 porta P8 modo Knob||`` no fim da função ``||functions:desviar||``.

```blocks
function desviar () {
    índice += sentido
    if (índice > direção.length - 1) {
        índice = direção.length - 2
        sentido = -1
    } else if (índice < 0) {
        índice = 1
        sentido = 1
    }
    actuators.SetAngleServoKnob(0, OutputPorts.P8)
}
let direção: number[] = []
let sentido = 0
let índice = 0
índice = 0
sentido = 1
direção = [0, 500, 1000]
actuators.SetSpeedMotor(500, OutputPorts.P16)
actuators.SetAngleServoKnob(0, OutputPorts.P8)

```


## Passo 20
No menu ``||array:Matriz||`` arraste um bloco ``||array:lista obter valor em 0||`` para o campo do valor da posição do servo motor.
Mude a variável ``||variables:lista||`` para ``||variables:direção||`` e o campo **0** para a variável ``||variables:índice||``.
```blocks
function desviar () {
    índice += sentido
    if (índice > direção.length - 1) {
        índice = direção.length - 2
        sentido = -1
    } else if (índice < 0) {
        índice = 1
        sentido = 1
    }
    actuators.SetAngleServoKnob(direção[índice], OutputPorts.P8)
}
let direção: number[] = []
let sentido = 0
let índice = 0
índice = 0
sentido = 1
direção = [0, 500, 1000]
actuators.SetSpeedMotor(500, OutputPorts.P16)
actuators.SetAngleServoKnob(0, OutputPorts.P8)
```

## Passo 21

Acesse a categoria ``||logic:Lógica||``, pegue a condicional ``||logic:se então||``
e insira-a dentro do bloco ``||basic:sempre||``. 


```blocks
function desviar () {
    índice += sentido
    if (índice > direção.length - 1) {
        índice = direção.length - 2
        sentido = -1
    } else if (índice < 0) {
        índice = 1
        sentido = 1
    }
    actuators.SetAngleServoKnob(direção[índice], OutputPorts.P8)
}
let direção: number[] = []
let sentido = 0
let índice = 0
índice = 0
sentido = 1
direção = [0, 500, 1000]
actuators.SetSpeedMotor(500, OutputPorts.P16)
actuators.SetAngleServoKnob(0, OutputPorts.P8)
basic.forever(function () {
    if (true) {
    	
    }
})
```

## Passo 22
Volte ao menu ``||logic:Lógica||``, pegue o comparador ``||logic:0 < 0||``
e substitua a condição **verdadeiro** da condicional.

```blocks
function desviar () {
    índice += sentido
    if (índice > direção.length - 1) {
        índice = direção.length - 2
        sentido = -1
    } else if (índice < 0) {
        índice = 1
        sentido = 1
    }
    actuators.SetAngleServoKnob(direção[índice], OutputPorts.P8)
}
let direção: number[] = []
let sentido = 0
let índice = 0
índice = 0
sentido = 1
direção = [0, 500, 1000]
actuators.SetSpeedMotor(500, OutputPorts.P16)
actuators.SetAngleServoKnob(0, OutputPorts.P8)
basic.forever(function () {
    if (0 < 0) {
    	
    }
})
```

## Passo 23
Agora atualize os campos do comparador. Vá até a aba ``||sensors:Sensores||``,
clique no bloco ``||sensors:Valor do sensor infravermelho na porta P2||`` e troque 
o primeiro **0** do comparador.
Em seguida, modifique o segundo campo de **0** para **500**, a porta de ``||sensors:P2||`` para ``||sensors:P1||``
e o sinal de **<** para **>**.

```blocks
function desviar () {
    índice += sentido
    if (índice > direção.length - 1) {
        índice = direção.length - 2
        sentido = -1
    } else if (índice < 0) {
        índice = 1
        sentido = 1
    }
    actuators.SetAngleServoKnob(direção[índice], OutputPorts.P8)
}
let direção: number[] = []
let sentido = 0
let índice = 0
índice = 0
sentido = 1
direção = [0, 500, 1000]
actuators.SetSpeedMotor(500, OutputPorts.P16)
actuators.SetAngleServoKnob(0, OutputPorts.P8)
basic.forever(function () {
    if (sensors.infraredValue(InputPorts.P1) > 500) {
    	
    }
})
```

## Passo 24
Acesse a aba ``||music:Música||`` e adicione o bloco ``||music:play tone C Medio for 1 batida until done||`` 
dentro da condicional ``||logic:se então||``.
Edite o tom de ``||music:C Médio||`` para ``||music:B Agudo||`` selecionando a tecla correspondente 
e coloque o som para tocar por **2 batidas**.


```blocks
function desviar () {
    índice += sentido
    if (índice > direção.length - 1) {
        índice = direção.length - 2
        sentido = -1
    } else if (índice < 0) {
        índice = 1
        sentido = 1
    }
    actuators.SetAngleServoKnob(direção[índice], OutputPorts.P8)
}
let direção: number[] = []
let sentido = 0
let índice = 0
índice = 0
sentido = 1
direção = [0, 500, 1000]
actuators.SetSpeedMotor(500, OutputPorts.P16)
actuators.SetAngleServoKnob(0, OutputPorts.P8)
basic.forever(function () {
    if (sensors.infraredValue(InputPorts.P1) > 500) {
        music.play(music.tonePlayable(988, music.beat(BeatFraction.Double)), music.PlaybackMode.UntilDone)
    }
})

```


## Passo 25
No menu ``||functions:Funções||`` arraste o comando  ``||functions:ligar desviar||``
para dentro da condição ``||logic:se então||``.

```blocks
function desviar () {
    índice += sentido
    if (índice > direção.length - 1) {
        índice = direção.length - 2
        sentido = -1
    } else if (índice < 0) {
        índice = 1
        sentido = 1
    }
    actuators.SetAngleServoKnob(direção[índice], OutputPorts.P8)
}
let direção: number[] = []
let sentido = 0
let índice = 0
índice = 0
sentido = 1
direção = [0, 500, 1000]
actuators.SetSpeedMotor(500, OutputPorts.P16)
actuators.SetAngleServoKnob(0, OutputPorts.P8)
basic.forever(function () {
    if (sensors.infraredValue(InputPorts.P1) > 500) {
        music.play(music.tonePlayable(988, music.beat(BeatFraction.Double)), music.PlaybackMode.UntilDone)
        desviar()
    }
})

```

## Passo 26
Na categoria ``||basic:Básico||`` arraste uma pausa ``||basic:pausa (ms) 100||`` para dentro do 
``||logic:então||`` e depois, mude seu valor para **1000**.

```blocks
function desviar () {
    índice += sentido
    if (índice > direção.length - 1) {
        índice = direção.length - 2
        sentido = -1
    } else if (índice < 0) {
        índice = 1
        sentido = 1
    }
    actuators.SetAngleServoKnob(direção[índice], OutputPorts.P8)
}
let direção: number[] = []
let sentido = 0
let índice = 0
índice = 0
sentido = 1
direção = [0, 500, 1000]
actuators.SetSpeedMotor(500, OutputPorts.P16)
actuators.SetAngleServoKnob(0, OutputPorts.P8)
basic.forever(function () {
    if (sensors.infraredValue(InputPorts.P1) > 500) {
        music.play(music.tonePlayable(988, music.beat(BeatFraction.Double)), music.PlaybackMode.UntilDone)
        desviar()
        basic.pause(1000)
    }
})

```

## Passo 27

Agora seu código está pronto! Baixe-o para o micro:bit e teste-o. Aproxime objetos do sensor infravermelho e observe o morcego desviar-se.
```blocks
```


## Passo 28
Se necessário, confira o seu código clicando na lâmpada de dica.

```blocks
function desviar () {
    índice += sentido
    if (índice > direção.length - 1) {
        índice = direção.length - 2
        sentido = -1
    } else if (índice < 0) {
        índice = 1
        sentido = 1
    }
    actuators.SetAngleServoKnob(direção[índice], OutputPorts.P8)
}
let direção: number[] = []
let sentido = 0
let índice = 0
índice = 0
sentido = 1
direção = [0, 500, 1000]
actuators.SetSpeedMotor(500, OutputPorts.P16)
actuators.SetAngleServoKnob(0, OutputPorts.P8)
basic.forever(function () {
    if (sensors.infraredValue(InputPorts.P1) > 500) {
        music.play(music.tonePlayable(988, music.beat(BeatFraction.Double)), music.PlaybackMode.UntilDone)
        desviar()
        basic.pause(1000)
    }
})

```



```package
fuzzyBot=github:FuzzyMakers/pxt-fuzzyMakers
```

