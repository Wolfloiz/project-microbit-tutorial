### @diffs true
# Radar Semafórico

## Passo 1
Nesse tutorial, vamos programar um radar semáfórico! Os sinais do semáforo variam de acordo com o tempo.
Vamos usar um sensor infravermelho para detectar a passagem de carros e, quando o motorista passar no sinal vermelho, 
uma buzina será acionada.

## Passo 2
Para começar, verifique se a biblioteca da Smart Makers já está importada em seu MakeCode.
Se não estiver, clique na aba **+ Extensões**, copie o endereço "https://github.com/FuzzyMakers/pxt-smartMakers",
cole-o no campo de pesquisa da janela que se abriu e selecione a biblioteca.

## Passo 3
Acesse o menu ``||variables:Variáveis||`` e clique em **"Fazer uma variável..."**.
Crie uma variável chamada: ``||variables:semaforo||``. 
Por fim, adicione o bloco ``||variables:definir semaforo para 0||`` que
aparecerá ao criá-la, dentro do laço ``||basic:no iniciar||``.  

```blocks
let semaforo = 0
basic.forever(function () {
	
})
```

## Passo 4
Altere o valor de definição dessa variável de **0** para **1**.

```blocks
let semaforo = 1
basic.forever(function () {
	
})
```

## Passo 5
Acesse o menu ``||Logic:Lógica||`` e adicione um bloco ``||Logic:se então senão||`` 
dentro do ``||basic:sempre||``. Clique no sinal de **+** desse bloco para adicionar um novo caso 
``||Logic:senão se||``.

```blocks
let semaforo = 1
basic.forever(function () {
    if (true) {
    	
    } else if (false) {
    	
    } else {
    	
    }
})
```

## Passo 6
Retorne ao menu ``||Logic:Lógica||`` e adicione um bloco comparador ``||Logic:0 = 0||`` em ambos
os campos de bordas triangulares (**verdadeiro** e **falso**) condicional.

```blocks
let semaforo = 1
basic.forever(function () {
    if (0 == 0) {
    	
    } else if (0 == 0) {
    	
    } else {
    	
    }
})
```

## Passo 7
Acesse a aba ``||variables:Variáveis||`` e adicione o bloco ``||variables:semaforo||`` no primeiro campo 
de ambos os comparadores.

```blocks
 let semaforo = 1
basic.forever(function () {
    if (semaforo == 0) {
    	
    } else if (semaforo == 0) {
    	
    } else {
    	
    }
})
```

## Passo 8
Altere o valor do primeiro comparador de **0** para **1**, enquanto o segundo comparador deve ter o valor igual a **2**.

```blocks
let semaforo = 1
basic.forever(function () {
    if (semaforo == 1) {
    	
    } else if (semaforo == 2) {
    	
    } else {
    	
    }
})
```

## Passo 9
Agora, vamos para dentro do primeiro ``||Logic:então||``, quando ``||variables:semaforo||`` é igual a **1**.
Esse será o nosso sinal verde... Para isso, acesse a aba ``||basic:Básico||`` e adicione o bloco  
``||basic:mostrar ícone||``. Clique na seta para alterar o ícone de coração para um "sim" (check).

```blocks
let semaforo = 1
basic.forever(function () {
    if (semaforo == 1) {
        basic.showIcon(IconNames.Yes)
    } else if (semaforo == 2) {
    	
    } else {
    	
    }
})
```

## Passo 10
Em seguida, acesse a categoria ``||music:Música||`` e adicione o comando ``||music:stop all sounds||``
abaixo do ``||basic:mostrar ícone||``. 

```blocks
let semaforo = 1
basic.forever(function () {
    if (semaforo == 1) {
        basic.showIcon(IconNames.Yes)
        music.stopAllSounds()
    } else if (semaforo == 2) {
    	
    } else {
    	
    }
})
```

## Passo 11
Prosseguimos agora para o segundo caso, o ``||Logic:então||`` de quando ``||variables:semaforo||`` é igual a **2**.
Retorne à categoria ``||basic:Básico||`` e adicione o comando ``||basic:mostrar leds||``.
Clique nos quadrados dos LEDs para desenhar um símbolo de exclamação (!) para indicar o sinal amarelo.

```blocks
let semaforo = 1
basic.forever(function () {
    if (semaforo == 1) {
        basic.showIcon(IconNames.Yes)
        music.stopAllSounds()
    } else if (semaforo == 2) {
        basic.showLeds(`
            . . # . .
            . . # . .
            . . # . .
            . . . . .
            . . # . .
            `)
    } else {
    	
    }
})
```

## Passo 12
Abaixo desse bloco, adicione outro ``||music:stop all sounds||`` localizado na aba ``||music:Música||``.

```blocks
let semaforo = 1
basic.forever(function () {
    if (semaforo == 1) {
        basic.showIcon(IconNames.Yes)
        music.stopAllSounds()
    } else if (semaforo == 2) {
        basic.showLeds(`
            . . # . .
            . . # . .
            . . # . .
            . . . . .
            . . # . .
            `)
        music.stopAllSounds()
    } else {
    	
    }
})
```

## Passo 13
Agora, dentro do ``||Logic:senão||``, adicione um bloco ``||basic:mostrar ícone||`` para indicar o sinal vermelho.
Clique na seta para alterar o símbolo para um **X**.

```blocks
let semaforo = 1
basic.forever(function () {
    if (semaforo == 1) {
        basic.showIcon(IconNames.Yes)
        music.stopAllSounds()
    } else if (semaforo == 2) {
        basic.showLeds(`
            . . # . .
            . . # . .
            . . # . .
            . . . . .
            . . # . .
            `)
        music.stopAllSounds()
    } else {
        basic.showIcon(IconNames.No)
    }
})
```

## Passo 14
Volte ao menu ``||Logic:Lógica||`` e adicione um novo ``||Logic:se então senão||`` ainda dentro do ``||Logic:senão||``, 
exatamente abaixo do bloco ``||basic:mostrar ícone||``.

```blocks
let semaforo = 1
basic.forever(function () {
    if (semaforo == 1) {
        basic.showIcon(IconNames.Yes)
        music.stopAllSounds()
    } else if (semaforo == 2) {
        basic.showLeds(`
            . . # . .
            . . # . .
            . . # . .
            . . . . .
            . . # . .
            `)
        music.stopAllSounds()
    } else {
        basic.showIcon(IconNames.No)
        if (true) {
        	
        } else {
        	
        }
    }
})
```

## Passo 15
Retorne à aba ``||Logic:Lógica||`` e adicione um bloco comparador ``||Logic:0 < 0||`` nesse novo condicional.
Altere o sinal desse comparador de **<** para **>**.

```blocks
let semaforo = 1
basic.forever(function () {
    if (semaforo == 1) {
        basic.showIcon(IconNames.Yes)
        music.stopAllSounds()
    } else if (semaforo == 2) {
        basic.showLeds(`
            . . # . .
            . . # . .
            . . # . .
            . . . . .
            . . # . .
            `)
        music.stopAllSounds()
    } else {
        basic.showIcon(IconNames.No)
        if (0 > 0) {
        	
        } else {
        	
        }
    }
})
```

## Passo 16
Agora, acesse o menu de ``||sensors:Sensores||`` e adicione o bloco ``||sensors:Valor do sensor infravermelho na porta P2||``
dentro do primeiro campo do comparador. Antes de prosseguir, altere o segundo valor do comparador de **0** para **300**.

```blocks
let semaforo = 1
basic.forever(function () {
    if (semaforo == 1) {
        basic.showIcon(IconNames.Yes)
        music.stopAllSounds()
    } else if (semaforo == 2) {
        basic.showLeds(`
            . . # . .
            . . # . .
            . . # . .
            . . . . .
            . . # . .
            `)
        music.stopAllSounds()
    } else {
        basic.showIcon(IconNames.No)
        if (sensors.infraredValue(InputPorts.P2) > 300) {
        	
        } else {
        	
        }
    }
})
```

## Passo 17
Dentro do ``||Logic:então||`` desse bloco, adicione um comando ``||music:toque (Hz) C Médio||``, 
encontrado no menu ``||music:Música||``. 

```blocks
let semaforo = 1
basic.forever(function () {
    if (semaforo == 1) {
        basic.showIcon(IconNames.Yes)
        music.stopAllSounds()
    } else if (semaforo == 2) {
        basic.showLeds(`
            . . # . .
            . . # . .
            . . # . .
            . . . . .
            . . # . .
            `)
        music.stopAllSounds()
    } else {
        basic.showIcon(IconNames.No)
        if (sensors.infraredValue(InputPorts.P2) > 300) {
            music.ringTone(262)
        } else {
        	
        }
    }
})
```

## Passo 18
Agora, dentro do ``||Logic:senão||`` desse bloco, adicione o comando ``||music:stop all sounds||``, também do menu ``||music:Música||``. 

```blocks
let semaforo = 1
basic.forever(function () {
    if (semaforo == 1) {
        basic.showIcon(IconNames.Yes)
        music.stopAllSounds()
    } else if (semaforo == 2) {
        basic.showLeds(`
            . . # . .
            . . # . .
            . . # . .
            . . . . .
            . . # . .
            `)
        music.stopAllSounds()
    } else {
        basic.showIcon(IconNames.No)
        if (sensors.infraredValue(InputPorts.P2) > 300) {
            music.ringTone(262)
        } else {
            music.stopAllSounds()
        }
    }
})
```

## Passo 19
Depois disso, retorne à categoria ``||basic:Básico||`` e adicione um segundo laço ``||basic:sempre||``
ao código.

```blocks
let semaforo = 1
basic.forever(function () {
	
})
basic.forever(function () {
    if (semaforo == 1) {
        basic.showIcon(IconNames.Yes)
        music.stopAllSounds()
    } else if (semaforo == 2) {
        basic.showLeds(`
            . . # . .
            . . # . .
            . . # . .
            . . . . .
            . . # . .
            `)
        music.stopAllSounds()
    } else {
        basic.showIcon(IconNames.No)
        if (sensors.infraredValue(InputPorts.P2) > 300) {
            music.ringTone(262)
        } else {
            music.stopAllSounds()
        }
    }
})
```

## Passo 20
Dentro desse novo ``||basic:sempre||``, adicione mais um bloco ``||logic:se então senão||``
com um comparador ``||logic:0 < 0||``.

```blocks
let semaforo = 1
basic.forever(function () {
    if (0 < 0) {
    	
    } else {
    	
    }
})
basic.forever(function () {
    if (semaforo == 1) {
        basic.showIcon(IconNames.Yes)
        music.stopAllSounds()
    } else if (semaforo == 2) {
        basic.showLeds(`
            . . # . .
            . . # . .
            . . # . .
            . . . . .
            . . # . .
            `)
        music.stopAllSounds()
    } else {
        basic.showIcon(IconNames.No)
        if (sensors.infraredValue(InputPorts.P2) > 300) {
            music.ringTone(262)
        } else {
            music.stopAllSounds()
        }
    }
})
```

## Passo 21
Insira o bloco da variável ``||variables:semaforo||`` dentro do primeiro campo do comparador.
Em seguida, modifique o valor do segundo campo de **0** para **3**.

```blocks
let semaforo = 1
basic.forever(function () {
    if (semaforo < 3) {
    	
    } else {
    	
    }
})
basic.forever(function () {
    if (semaforo == 1) {
        basic.showIcon(IconNames.Yes)
        music.stopAllSounds()
    } else if (semaforo == 2) {
        basic.showLeds(`
            . . # . .
            . . # . .
            . . # . .
            . . . . .
            . . # . .
            `)
        music.stopAllSounds()
    } else {
        basic.showIcon(IconNames.No)
        if (sensors.infraredValue(InputPorts.P2) > 300) {
            music.ringTone(262)
        } else {
            music.stopAllSounds()
        }
    }
})
```

## Passo 22
Dentro do ``||logic:então||``, adicione um bloco de ``||basic:pausa (ms) 100||``. Altere
o valor dessa pausa de **100 ms** para **5000 ms** (5 segundos). 

```blocks
let semaforo = 1
basic.forever(function () {
    if (semaforo < 3) {
        basic.pause(5000)
    } else {
    	
    }
})
basic.forever(function () {
    if (semaforo == 1) {
        basic.showIcon(IconNames.Yes)
        music.stopAllSounds()
    } else if (semaforo == 2) {
        basic.showLeds(`
            . . # . .
            . . # . .
            . . # . .
            . . . . .
            . . # . .
            `)
        music.stopAllSounds()
    } else {
        basic.showIcon(IconNames.No)
        if (sensors.infraredValue(InputPorts.P2) > 300) {
            music.ringTone(262)
        } else {
            music.stopAllSounds()
        }
    }
})
```

## Passo 23
Retorne à categoria ``||variables:Variáveis||`` e adicione o comando ``||variables:alterar semaforo por 1||``, imediatamente
abaixo da ``||basic:pausa (ms)||``, ainda dentro do ``||logic:então||``.

```blocks
let semaforo = 1
basic.forever(function () {
    if (semaforo < 3) {
        basic.pause(5000)
        semaforo += 1
    } else {
    	
    }
})
basic.forever(function () {
    if (semaforo == 1) {
        basic.showIcon(IconNames.Yes)
        music.stopAllSounds()
    } else if (semaforo == 2) {
        basic.showLeds(`
            . . # . .
            . . # . .
            . . # . .
            . . . . .
            . . # . .
            `)
        music.stopAllSounds()
    } else {
        basic.showIcon(IconNames.No)
        if (sensors.infraredValue(InputPorts.P2) > 300) {
            music.ringTone(262)
        } else {
            music.stopAllSounds()
        }
    }
})
```

## Passo 24
Dentro do ``||logic:senão||`` deste bloco, adicione uma ``||basic:pausa (ms)||``, também com a duração
de 5 segundos (**5000 ms**).

```blocks
let semaforo = 1
basic.forever(function () {
    if (semaforo < 3) {
        basic.pause(5000)
        semaforo += 1
    } else {
        basic.pause(5000)
    }
})
basic.forever(function () {
    if (semaforo == 1) {
        basic.showIcon(IconNames.Yes)
        music.stopAllSounds()
    } else if (semaforo == 2) {
        basic.showLeds(`
            . . # . .
            . . # . .
            . . # . .
            . . . . .
            . . # . .
            `)
        music.stopAllSounds()
    } else {
        basic.showIcon(IconNames.No)
        if (sensors.infraredValue(InputPorts.P2) > 300) {
            music.ringTone(262)
        } else {
            music.stopAllSounds()
        }
    }
})
```

## Passo 25
Por fim, retorne ao menu ``||variables:Variáveis||`` e adicione o comando ``||variables:definir semaforo para 0||``, imediatamente
abaixo da ``||basic:pausa (ms)||``, ainda dentro do ``||logic:senão||``.

```blocks
let semaforo = 1
basic.forever(function () {
    if (semaforo < 3) {
        basic.pause(5000)
        semaforo += 1
    } else {
        basic.pause(5000)
        semaforo = 0
    }
})
basic.forever(function () {
    if (semaforo == 1) {
        basic.showIcon(IconNames.Yes)
        music.stopAllSounds()
    } else if (semaforo == 2) {
        basic.showLeds(`
            . . # . .
            . . # . .
            . . # . .
            . . . . .
            . . # . .
            `)
        music.stopAllSounds()
    } else {
        basic.showIcon(IconNames.No)
        if (sensors.infraredValue(InputPorts.P2) > 300) {
            music.ringTone(262)
        } else {
            music.stopAllSounds()
        }
    }
})
```

## Passo 26
Altere o valor desse bloco de definição de **0** para **1**.

```blocks
let semaforo = 1
basic.forever(function () {
    if (semaforo < 3) {
        basic.pause(5000)
        semaforo += 1
    } else {
        basic.pause(5000)
        semaforo = 1
    }
})
basic.forever(function () {
    if (semaforo == 1) {
        basic.showIcon(IconNames.Yes)
        music.stopAllSounds()
    } else if (semaforo == 2) {
        basic.showLeds(`
            . . # . .
            . . # . .
            . . # . .
            . . . . .
            . . # . .
            `)
        music.stopAllSounds()
    } else {
        basic.showIcon(IconNames.No)
        if (sensors.infraredValue(InputPorts.P2) > 300) {
            music.ringTone(262)
        } else {
            music.stopAllSounds()
        }
    }
})
```

## Passo 27

Agora seu código está pronto! Baixe-o para o micro:bit e teste-o. Observe a mudança dos sinais 
do semáforo e passe com o veículo na frente do sensor quando estiver no sinal vermelho (**X**).
Verifique se o som do radar vai tocar.

```blocks
```

## Passo 28
Se necessário, confira o seu código clicando na lâmpada de dica.

```blocks
let semaforo = 1
basic.forever(function () {
    if (semaforo < 3) {
        basic.pause(5000)
        semaforo += 1
    } else {
        basic.pause(5000)
        semaforo = 1
    }
})
basic.forever(function () {
    if (semaforo == 1) {
        basic.showIcon(IconNames.Yes)
        music.stopAllSounds()
    } else if (semaforo == 2) {
        basic.showLeds(`
            . . # . .
            . . # . .
            . . # . .
            . . . . .
            . . # . .
            `)
        music.stopAllSounds()
    } else {
        basic.showIcon(IconNames.No)
        if (sensors.infraredValue(InputPorts.P2) > 300) {
            music.ringTone(262)
        } else {
            music.stopAllSounds()
        }
    }
})
```

```package
fuzzyBot=github:FuzzyMakers/pxt-fuzzyMakers
```
