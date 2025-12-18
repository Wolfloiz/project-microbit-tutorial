### @diffs true
# Jukebox

## Passo 1
Neste tutorial, vamos programar o jukebox para que ele toque várias músicas. 
O Bit Botão será responsável por ligar e desligar a jukebox. Ao ligá-la, a música
deve começar a tocar junto ao giro do disco, enquanto os botões A e B do micro:bit 
alteram qual música toca.

## Passo 2
Para começar, verifique se a biblioteca da Smart Makers já está importada 
em seu MakeCode. Se não estiver, clique na aba **+ Extensões**, 
copie o endereço "https://github.com/FuzzyMakers/pxt-smartMakers",
cole-o no campo de pesquisa da janela que se abriu e selecione a biblioteca.

## Passo 3
Acesse o menu ``||variables:Variáveis||`` e clique em 
**"Fazer uma variável..."**. Crie uma variável chamada 
``||variables:musica||`` e, depois de criá-la, adicione o bloco 
``||variables:definir musica para 0||`` dentro do ``||basic:no iniciar||``.

```blocks
let musica = 0
basic.forever(function () {
	
})
```

## Passo 4
Edite o valor de definição da variável ``||variables:musica||`` de **0** para 
**1**.

```blocks
let musica = 1
basic.forever(function () {
	
})
```

## Passo 5
Acesse a categoria ``||basic:Básico||`` e adicione um comando 
``||basic:mostrar número||`` dentro do laço ``||basic:sempre||``.

```blocks
let musica = 1
basic.forever(function () {
    basic.showNumber(0)
```

## Passo 6
Retorne à aba ``||variables:Variáveis||`` e utilize o bloco da variável 
``||variables:musica||`` para substituir o valor **0** do bloco 
``||basic:mostrar número||``.

```blocks
let musica = 1
basic.forever(function () {
    basic.showNumber(0)
})
```

## Passo 7
Abaixo do ``||basic:mostrar número||``, adicione o comando 
``||music:definir volume 127||``, localizado na aba ``||music:Música||``.

```blocks
let musica = 1
basic.forever(function () {
    basic.showNumber(musica)
    music.setVolume(127)
})
```

## Passo 8
Acesse a categoria ``||math:Matemática||`` e insira o bloco 
``||math:map 0 from low 0 high 1023 to low 0 high 4||`` dentro do comando 
``||music:definir volume 127||``, substituindo o valor **127**.

```blocks
let musica = 1
basic.forever(function () {
    basic.showNumber(musica)
    music.setVolume(Math.map(0, 0, 1023, 0, 4))
})

```

## Passo 9
Vá ao menu ``||sensors:Sensores||`` e utilize o bloco 
``||sensors:Valor do potenciômetro na porta P2||`` para substituir o primeiro 
**0** do comando ``||math:map||``.

```blocks
let musica = 1
basic.forever(function () {
    basic.showNumber(musica)
    music.setVolume(Math.map(sensors.dimmerValue(InputPorts.P2), 0, 1023, 0, 4))
})
```

## Passo 10
Clique na seta do bloco ``||sensors:Valor do potenciômetro na porta P2||`` para
alterar a porta de ``||sensors:P2||`` para ``||sensors:P1||``. Em seguida, 
modifique o último campo desse comando de **4** para **255**.

```blocks
let musica = 1
basic.forever(function () {
    basic.showNumber(musica)
    music.setVolume(Math.map(sensors.dimmerValue(InputPorts.P1), 0, 1023, 0, 255))
})
```

## Passo 11
Retorne à categoria ``||basic:Básico||`` e adicione um segundo bloco 
``||basic:sempre||`` ao seu código.

```blocks
let musica = 1
basic.forever(function () {
    basic.showNumber(musica)
    music.setVolume(Math.map(sensors.dimmerValue(InputPorts.P1), 0, 1023, 0, 255))
})
basic.forever(function () {
	
})
```

## Passo 12
Acesse a aba ``||logic:Lógica||`` e adicione o bloco ``||logic:se então||`` 
dentro desse novo bloco ``||basic:sempre||``.

```blocks
let musica = 1
basic.forever(function () {
    basic.showNumber(musica)
    music.setVolume(Math.map(sensors.dimmerValue(InputPorts.P1), 0, 1023, 0, 255))
})
basic.forever(function () {
    if (true) {
    	
    }
})
```

## Passo 13
Retorne à ``||logic:Lógica||`` e utilize o bloco comparador 
``||logic:0 = 0||`` para substituir o campo **verdadeiro** do bloco 
``||logic:se então||``.

```blocks
let musica = 1
basic.forever(function () {
    basic.showNumber(musica)
    music.setVolume(Math.map(sensors.dimmerValue(InputPorts.P1), 0, 1023, 0, 255))
})
basic.forever(function () {
    if (0 == 0) {
    	
    }
})
```

## Passo 14
Acesse o menu ``||sensors:Sensores||`` e selecione o bloco 
``||sensors:Valor do Botão na porta P2||`` para substituir o 
valor **0** do primeiro campo do comparador.

```blocks
let musica = 1
basic.forever(function () {
    basic.showNumber(musica)
    music.setVolume(Math.map(sensors.dimmerValue(InputPorts.P1), 0, 1023, 0, 255))
})
basic.forever(function () {
    if (sensors.buttonValue(InputPorts.P2) == 0) {
    	
    }
})
```

## Passo 15
Acesse o menu ``||actuators:Atuadores||`` e insira o comando 
``||actuators:Motor CC, parar motor na porta P8||`` dentro do ``||logic:então||``.

```blocks
let musica = 1
basic.forever(function () {
    basic.showNumber(musica)
    music.setVolume(Math.map(sensors.dimmerValue(InputPorts.P1), 0, 1023, 0, 255))
})
basic.forever(function () {
    if (sensors.buttonValue(InputPorts.P2) == 0) {
        actuators.StopMotor(OutputPorts.P8)
    }
})
```

## Passo 16
Retorne à categoria ``||music:Música||`` e insira o bloco 
``||music:stop all sounds||`` dentro do ``||logic:então||``.

```blocks
let musica = 1
basic.forever(function () {
    basic.showNumber(musica)
    music.setVolume(Math.map(sensors.dimmerValue(InputPorts.P1), 0, 1023, 0, 255))
})
basic.forever(function () {
    if (sensors.buttonValue(InputPorts.P2) == 0) {
        actuators.StopMotor(OutputPorts.P8)
        music.stopAllSounds()
    }
})
```

## Passo 17
Acesse o menu ``||input:Entrada||`` e adicione dois blocos 
``||input:no botão A pressionado||`` na área de programação. Clique na seta de 
um desses blocos para alterar de ``||input:botão A||`` para ``||input:botão B||``.

```blocks
input.onButtonPressed(Button.A, function () {
	
})
input.onButtonPressed(Button.B, function () {
	
})
let musica = 1
basic.forever(function () {
    basic.showNumber(musica)
    music.setVolume(Math.map(sensors.dimmerValue(InputPorts.P1), 0, 1023, 0, 255))
})
basic.forever(function () {
    if (sensors.buttonValue(InputPorts.P2) == 0) {
        actuators.StopMotor(OutputPorts.P8)
        music.stopAllSounds()
    }
})
```

## Passo 18
Acesse a aba ``||logic:Lógica||`` e adicione o bloco ``||logic:se então||`` 
dentro de ambos os blocos ``||input:no botão pressionado||``.

```blocks
input.onButtonPressed(Button.A, function () {
    if (true) {
    	
    }
})
input.onButtonPressed(Button.B, function () {
    if (true) {
    	
    }
})
let musica = 1
basic.forever(function () {
    basic.showNumber(musica)
    music.setVolume(Math.map(sensors.dimmerValue(InputPorts.P1), 0, 1023, 0, 255))
})
basic.forever(function () {
    if (sensors.buttonValue(InputPorts.P2) == 0) {
        actuators.StopMotor(OutputPorts.P8)
        music.stopAllSounds()
    }
})
```

## Passo 19
Retorne à ``||logic:Lógica||`` e utilize blocos comparadores 
``||logic:0 < 0||`` para substituir o campo **verdadeiro** dos dois blocos 
``||logic:se então||``.

```blocks
input.onButtonPressed(Button.A, function () {
    if (0 < 0) {
    	
    }
})
input.onButtonPressed(Button.B, function () {
    if (0 < 0) {
    	
    }
})
let musica = 1
basic.forever(function () {
    basic.showNumber(musica)
    music.setVolume(Math.map(sensors.dimmerValue(InputPorts.P1), 0, 1023, 0, 255))
})
basic.forever(function () {
    if (sensors.buttonValue(InputPorts.P2) == 0) {
        actuators.StopMotor(OutputPorts.P8)
        music.stopAllSounds()
    }
})
```

## Passo 20
Retorne à ``||variables:Variáveis||`` e utilize o bloco 
``||variables:musica||`` para substituir o valor **0** do primeiro campo de 
ambos os comparadores.

```blocks
input.onButtonPressed(Button.A, function () {
    if (musica < 0) {
    	
    }
})
input.onButtonPressed(Button.B, function () {
    if (musica < 0) {
    	
    }
})
let musica = 0
musica = 1
basic.forever(function () {
    basic.showNumber(musica)
    music.setVolume(Math.map(sensors.dimmerValue(InputPorts.P1), 0, 1023, 0, 255))
})
basic.forever(function () {
    if (sensors.buttonValue(InputPorts.P2) == 0) {
        actuators.StopMotor(OutputPorts.P8)
        music.stopAllSounds()
    }
})
```

## Passo 21
Altere o sinal do comparador do ``||input:Botão A||`` para **>=** e o do 
``||input:Botão B||`` para **<=**. Em seguida, modifique o segundo valor de 
ambos os comparadores de **0** para **2**.

```blocks
input.onButtonPressed(Button.A, function () {
    if (musica >= 2) {
    	
    }
})
input.onButtonPressed(Button.B, function () {
    if (musica <= 2) {
    	
    }
})
let musica = 0
musica = 1
basic.forever(function () {
    basic.showNumber(musica)
    music.setVolume(Math.map(sensors.dimmerValue(InputPorts.P1), 0, 1023, 0, 255))
})
basic.forever(function () {
    if (sensors.buttonValue(InputPorts.P2) == 0) {
        actuators.StopMotor(OutputPorts.P8)
        music.stopAllSounds()
    }
})
```

## Passo 22
Dentro do ``||logic:então||`` de ambos os blocos, insira o comando
``||variables:alterar musica por 1||``. No entanto, altere o valor do bloco 
dentro do ``||input:Botão A||`` de **1** para **-1**.

```blocks
input.onButtonPressed(Button.A, function () {
    if (musica >= 2) {
        musica += -1
    }
})
input.onButtonPressed(Button.B, function () {
    if (musica <= 2) {
        musica += 1
    }
})
let musica = 0
musica = 1
basic.forever(function () {
    basic.showNumber(musica)
    music.setVolume(Math.map(sensors.dimmerValue(InputPorts.P1), 0, 1023, 0, 255))
})
basic.forever(function () {
    if (sensors.buttonValue(InputPorts.P2) == 0) {
        actuators.StopMotor(OutputPorts.P8)
        music.stopAllSounds()
    }
})
```

## Passo 23
Retorne à categoria ``||basic:Básico||`` e adicione um terceiro laço 
``||basic:sempre||`` ao seu código.

```blocks
input.onButtonPressed(Button.A, function () {
    if (musica >= 2) {
        musica += -1
    }
})
input.onButtonPressed(Button.B, function () {
    if (musica <= 2) {
        musica += 1
    }
})
let musica = 0
musica = 1
basic.forever(function () {
    basic.showNumber(musica)
    music.setVolume(Math.map(sensors.dimmerValue(InputPorts.P1), 0, 1023, 0, 255))
})
basic.forever(function () {
    if (sensors.buttonValue(InputPorts.P2) == 0) {
        actuators.StopMotor(OutputPorts.P8)
        music.stopAllSounds()
    }
})
basic.forever(function () {
	
})
```

## Passo 24
Acesse a aba ``||logic:Lógica||`` e adicione o bloco ``||logic:se então||`` 
dentro desse novo bloco ``||basic:sempre||``.

```blocks
input.onButtonPressed(Button.A, function () {
    if (musica >= 2) {
        musica += -1
    }
})
input.onButtonPressed(Button.B, function () {
    if (musica <= 2) {
        musica += 1
    }
})
let musica = 0
musica = 1
basic.forever(function () {
    basic.showNumber(musica)
    music.setVolume(Math.map(sensors.dimmerValue(InputPorts.P1), 0, 1023, 0, 255))
})
basic.forever(function () {
    if (sensors.buttonValue(InputPorts.P2) == 0) {
        actuators.StopMotor(OutputPorts.P8)
        music.stopAllSounds()
    }
})
basic.forever(function () {
    if (true) {
    	
    }
})
```

## Passo 25
Retorne à ``||logic:Lógica||`` e utilize o bloco comparador 
``||logic:0 = 0||`` para substituir o campo **verdadeiro** do bloco 
``||logic:se então||``.

```blocks
input.onButtonPressed(Button.A, function () {
    if (musica >= 2) {
        musica += -1
    }
})
input.onButtonPressed(Button.B, function () {
    if (musica <= 2) {
        musica += 1
    }
})
let musica = 0
musica = 1
basic.forever(function () {
    basic.showNumber(musica)
    music.setVolume(Math.map(sensors.dimmerValue(InputPorts.P1), 0, 1023, 0, 255))
})
basic.forever(function () {
    if (sensors.buttonValue(InputPorts.P2) == 0) {
        actuators.StopMotor(OutputPorts.P8)
        music.stopAllSounds()
    }
})
basic.forever(function () {
    if (0 == 0) {
    	
    }
})
```

## Passo 26
Acesse o menu ``||sensors:Sensores||`` e selecione o bloco 
``||sensors:Valor do Botão na porta P2||`` para substituir o 
valor **0** do primeiro campo do comparador. Antes de prosseguir, 
altere o segundo valor do comparador de **0** para **1**.

```blocks
input.onButtonPressed(Button.A, function () {
    if (musica >= 2) {
        musica += -1
    }
})
input.onButtonPressed(Button.B, function () {
    if (musica <= 2) {
        musica += 1
    }
})
let musica = 0
musica = 1
basic.forever(function () {
    basic.showNumber(musica)
    music.setVolume(Math.map(sensors.dimmerValue(InputPorts.P1), 0, 1023, 0, 255))
})
basic.forever(function () {
    if (sensors.buttonValue(InputPorts.P2) == 0) {
        actuators.StopMotor(OutputPorts.P8)
        music.stopAllSounds()
    }
})
basic.forever(function () {
    if (sensors.buttonValue(InputPorts.P2) == 1) {
    	
    }
})
```

## Passo 27
Acesse o menu ``||actuators:Atuadores||`` e insira o comando 
``||actuators:Motor CC, definir velocidade 0 na porta P8||`` 
dentro do ``||logic:então||``.

```blocks
input.onButtonPressed(Button.A, function () {
    if (musica >= 2) {
        musica += -1
    }
})
input.onButtonPressed(Button.B, function () {
    if (musica <= 2) {
        musica += 1
    }
})
let musica = 0
musica = 1
basic.forever(function () {
    basic.showNumber(musica)
    music.setVolume(Math.map(sensors.dimmerValue(InputPorts.P1), 0, 1023, 0, 255))
})
basic.forever(function () {
    if (sensors.buttonValue(InputPorts.P2) == 0) {
        actuators.StopMotor(OutputPorts.P8)
        music.stopAllSounds()
    }
})
basic.forever(function () {
    if (sensors.buttonValue(InputPorts.P2) == 1) {
        actuators.SetSpeedMotor(0, OutputPorts.P8)
    }
})
```

## Passo 28
Altere o valor de velocidade de **0** para **100**.

```blocks
input.onButtonPressed(Button.A, function () {
    if (musica >= 2) {
        musica += -1
    }
})
input.onButtonPressed(Button.B, function () {
    if (musica <= 2) {
        musica += 1
    }
})
let musica = 0
musica = 1
basic.forever(function () {
    basic.showNumber(musica)
    music.setVolume(Math.map(sensors.dimmerValue(InputPorts.P1), 0, 1023, 0, 255))
})
basic.forever(function () {
    if (sensors.buttonValue(InputPorts.P2) == 0) {
        actuators.StopMotor(OutputPorts.P8)
        music.stopAllSounds()
    }
})
basic.forever(function () {
    if (sensors.buttonValue(InputPorts.P2) == 1) {
        actuators.SetSpeedMotor(100, OutputPorts.P8)
    }
})
```

## Passo 29
Abaixo do comando ``||actuators:Motor CC, definir velocidade||``, ainda dentro
do ``||logic:se então||``, insira um bloco ``||logic:se então senão||`` com
o comparador ``||logic:0 = 0||``.

```blocks
input.onButtonPressed(Button.A, function () {
    if (musica >= 2) {
        musica += -1
    }
})
input.onButtonPressed(Button.B, function () {
    if (musica <= 2) {
        musica += 1
    }
})
let musica = 0
musica = 1
basic.forever(function () {
    basic.showNumber(musica)
    music.setVolume(Math.map(sensors.dimmerValue(InputPorts.P1), 0, 1023, 0, 255))
})
basic.forever(function () {
    if (sensors.buttonValue(InputPorts.P2) == 0) {
        actuators.StopMotor(OutputPorts.P8)
        music.stopAllSounds()
    }
})
basic.forever(function () {
    if (sensors.buttonValue(InputPorts.P2) == 1) {
        actuators.SetSpeedMotor(100, OutputPorts.P8)
        if (0 == 0) {
        	
        } else {
        	
        }
    }
})
```

## Passo 30
Clique **duas vezes** no sinal de **+** para adicionar dois 
``||logic:senão se||`` e, em seguida, clique no sinal de **-** ao lado do 
último ``||logic:senão||`` para deletar essa condição.

```blocks
input.onButtonPressed(Button.A, function () {
    if (musica >= 2) {
        musica += -1
    }
})
input.onButtonPressed(Button.B, function () {
    if (musica <= 2) {
        musica += 1
    }
})
let musica = 0
musica = 1
basic.forever(function () {
    basic.showNumber(musica)
    music.setVolume(Math.map(sensors.dimmerValue(InputPorts.P1), 0, 1023, 0, 255))
})
basic.forever(function () {
    if (sensors.buttonValue(InputPorts.P2) == 0) {
        actuators.StopMotor(OutputPorts.P8)
        music.stopAllSounds()
    }
})
basic.forever(function () {
    if (sensors.buttonValue(InputPorts.P2) == 1) {
        actuators.SetSpeedMotor(100, OutputPorts.P8)
        if (0 == 0) {
        	
        } else if (false) {
        	
        } else if (false) {
        	
        }
    }
})
```

## Passo 31
Adicione comparadores ``||logic:0 = 0||`` em ambos os ``||logic:senão se||``.

```blocks
input.onButtonPressed(Button.A, function () {
    if (musica >= 2) {
        musica += -1
    }
})
input.onButtonPressed(Button.B, function () {
    if (musica <= 2) {
        musica += 1
    }
})
let musica = 0
musica = 1
basic.forever(function () {
    basic.showNumber(musica)
    music.setVolume(Math.map(sensors.dimmerValue(InputPorts.P1), 0, 1023, 0, 255))
})
basic.forever(function () {
    if (sensors.buttonValue(InputPorts.P2) == 0) {
        actuators.StopMotor(OutputPorts.P8)
        music.stopAllSounds()
    }
})
basic.forever(function () {
    if (sensors.buttonValue(InputPorts.P2) == 1) {
        actuators.SetSpeedMotor(100, OutputPorts.P8)
        if (0 == 0) {
        	
        } else if (0 == 0) {
        	
        } else if (0 == 0) {
        	
        }
    }
})
```

## Passo 32
Insira o bloco da variável ``||variables:musica||`` no primeiro campo dos três 
comparadores. Em seguida, altere o segundo campo desses comparadores para **1**,
**2** e **3**, respectivamente.

```blocks
input.onButtonPressed(Button.A, function () {
    if (musica >= 2) {
        musica += -1
    }
})
input.onButtonPressed(Button.B, function () {
    if (musica <= 2) {
        musica += 1
    }
})
let musica = 0
musica = 1
basic.forever(function () {
    basic.showNumber(musica)
    music.setVolume(Math.map(sensors.dimmerValue(InputPorts.P1), 0, 1023, 0, 255))
})
basic.forever(function () {
    if (sensors.buttonValue(InputPorts.P2) == 0) {
        actuators.StopMotor(OutputPorts.P8)
        music.stopAllSounds()
    }
})
basic.forever(function () {
    if (sensors.buttonValue(InputPorts.P2) == 1) {
        actuators.SetSpeedMotor(100, OutputPorts.P8)
        if (musica == 1) {
        	
        } else if (musica == 2) {
        	
        } else if (musica == 3) {
        	
        }
    }
})
```

## Passo 33
Acesse a categoria ``||music:Música||`` e adicione um comando 
``||music:play melody at tempo 120 (bpm) until done||`` dentro de cada 
``||logic:então||``.

```blocks
input.onButtonPressed(Button.A, function () {
    if (musica >= 2) {
        musica += -1
    }
})
input.onButtonPressed(Button.B, function () {
    if (musica <= 2) {
        musica += 1
    }
})
let musica = 0
musica = 1
basic.forever(function () {
    basic.showNumber(musica)
    music.setVolume(Math.map(sensors.dimmerValue(InputPorts.P1), 0, 1023, 0, 255))
})
basic.forever(function () {
    if (sensors.buttonValue(InputPorts.P2) == 0) {
        actuators.StopMotor(OutputPorts.P8)
        music.stopAllSounds()
    }
})
basic.forever(function () {
    if (sensors.buttonValue(InputPorts.P2) == 1) {
        actuators.SetSpeedMotor(100, OutputPorts.P8)
        if (musica == 1) {
            music.play(music.stringPlayable("- - - - - - - - ", 120), music.PlaybackMode.UntilDone)
        } else if (musica == 2) {
            music.play(music.stringPlayable("- - - - - - - - ", 120), music.PlaybackMode.UntilDone)
        } else if (musica == 3) {
            music.play(music.stringPlayable("- - - - - - - - ", 120), music.PlaybackMode.UntilDone)
        }
    }
})
```

## Passo 34
Agora, vamos definir as melodias de cada caso. Clique nos retângulos 
do primeiro bloco ``||music:play melody||`` para abrir o quadro do editor 
de melodias. Esse editor é dividido em colunas, que são tocadas em sequência. 
Cada linha dessas colunas representa uma nota, que pode ser selecionada ao 
clicar sobre seu quadrado correspondente.
A melodia que devemos programar segue o seguinte padrão:

*(clique na lâmpada de dica para facilitar a visualização)*
- 1ª coluna: 1ª linha;
- 2ª coluna: 2ª linha;
- 3ª coluna: 3ª linha;
- 4ª coluna: 4ª linha; 
- 5ª coluna: 5ª linha; 
- 6ª coluna: 6ª linha; 
- 7ª coluna: 7ª linha; 
- 8ª coluna: 8ª linha; 

```blocks
input.onButtonPressed(Button.A, function () {
    if (musica >= 2) {
        musica += -1
    }
})
input.onButtonPressed(Button.B, function () {
    if (musica <= 2) {
        musica += 1
    }
})
let musica = 0
musica = 1
basic.forever(function () {
    basic.showNumber(musica)
    music.setVolume(Math.map(sensors.dimmerValue(InputPorts.P1), 0, 1023, 0, 255))
})
basic.forever(function () {
    if (sensors.buttonValue(InputPorts.P2) == 0) {
        actuators.StopMotor(OutputPorts.P8)
        music.stopAllSounds()
    }
})
basic.forever(function () {
    if (sensors.buttonValue(InputPorts.P2) == 1) {
        actuators.SetSpeedMotor(100, OutputPorts.P8)
        if (musica == 1) {
            music.play(music.stringPlayable("C5 B A G F E D C ", 120), music.PlaybackMode.UntilDone)
        } else if (musica == 2) {
            music.play(music.stringPlayable("- - - - - - - - ", 120), music.PlaybackMode.UntilDone)
        } else if (musica == 3) {
            music.play(music.stringPlayable("- - - - - - - - ", 120), music.PlaybackMode.UntilDone)
        }
    }
})
```

## Passo 35
Agora, clique nos retângulos do segundo bloco ``||music:play melody||`` 
para abrir o quadro do editor de melodias. A melodia que devemos programar 
segue o seguinte padrão:

*(clique na lâmpada de dica para facilitar a visualização)*
- 1ª coluna: 8ª linha;
- 2ª coluna: 7ª linha;
- 3ª coluna: 6ª linha;
- 4ª coluna: 5ª linha; 
- 5ª coluna: 4ª linha; 
- 6ª coluna: 3ª linha; 
- 7ª coluna: 2ª linha; 
- 8ª coluna: 1ª linha; 

```blocks
input.onButtonPressed(Button.A, function () {
    if (musica >= 2) {
        musica += -1
    }
})
input.onButtonPressed(Button.B, function () {
    if (musica <= 2) {
        musica += 1
    }
})
let musica = 0
musica = 1
basic.forever(function () {
    basic.showNumber(musica)
    music.setVolume(Math.map(sensors.dimmerValue(InputPorts.P1), 0, 1023, 0, 255))
})
basic.forever(function () {
    if (sensors.buttonValue(InputPorts.P2) == 0) {
        actuators.StopMotor(OutputPorts.P8)
        music.stopAllSounds()
    }
})
basic.forever(function () {
    if (sensors.buttonValue(InputPorts.P2) == 1) {
        actuators.SetSpeedMotor(100, OutputPorts.P8)
        if (musica == 1) {
            music.play(music.stringPlayable("C5 B A G F E D C ", 120), music.PlaybackMode.UntilDone)
        } else if (musica == 2) {
            music.play(music.stringPlayable("C D E F G A B C5 ", 120), music.PlaybackMode.UntilDone)
        } else if (musica == 3) {
            music.play(music.stringPlayable("- - - - - - - - ", 120), music.PlaybackMode.UntilDone)
        }
    }
})
```

## Passo 36
Por fim, clique nos retângulos do terceiro bloco ``||music:play melody||`` 
para abrir o quadro do editor de melodias. A melodia que devemos programar 
segue o seguinte padrão:

*(clique na lâmpada de dica para facilitar a visualização)*
- 1ª coluna: 6ª linha;
- 2ª coluna: 2ª linha;
- 3ª coluna: 1ª linha;
- 4ª coluna: 3ª linha; 
- 5ª coluna: 2ª linha; 
- 6ª coluna: 4ª linha; 
- 7ª coluna: 3ª linha; 
- 8ª coluna: 5ª linha; 

```blocks
input.onButtonPressed(Button.A, function () {
    if (musica >= 2) {
        musica += -1
    }
})
input.onButtonPressed(Button.B, function () {
    if (musica <= 2) {
        musica += 1
    }
})
let musica = 0
musica = 1
basic.forever(function () {
    basic.showNumber(musica)
    music.setVolume(Math.map(sensors.dimmerValue(InputPorts.P1), 0, 1023, 0, 255))
})
basic.forever(function () {
    if (sensors.buttonValue(InputPorts.P2) == 0) {
        actuators.StopMotor(OutputPorts.P8)
        music.stopAllSounds()
    }
})
basic.forever(function () {
    if (sensors.buttonValue(InputPorts.P2) == 1) {
        actuators.SetSpeedMotor(100, OutputPorts.P8)
        if (musica == 1) {
            music.play(music.stringPlayable("C5 B A G F E D C ", 120), music.PlaybackMode.UntilDone)
        } else if (musica == 2) {
            music.play(music.stringPlayable("C D E F G A B C5 ", 120), music.PlaybackMode.UntilDone)
        } else if (musica == 3) {
            music.play(music.stringPlayable("E B C5 A B G A F ", 120), music.PlaybackMode.UntilDone)
        }
    }
})
```

## Passo 37
Agora, seu código está pronto! Baixe-o para o micro:bit, use o botão para 
ligar e desligar a jukebox. Os botões A e B do micro:bit alternam as músicas, 
enquanto o potenciômetro ajusta o volume de reprodução.

```blocks
```

## Passo 38
Se necessário, confira o seu código clicando na lâmpada de dica.

```blocks
input.onButtonPressed(Button.A, function () {
    if (musica >= 2) {
        musica += -1
    }
})
input.onButtonPressed(Button.B, function () {
    if (musica <= 2) {
        musica += 1
    }
})
let musica = 0
musica = 1
basic.forever(function () {
    basic.showNumber(musica)
    music.setVolume(Math.map(sensors.dimmerValue(InputPorts.P1), 0, 1023, 0, 255))
})
basic.forever(function () {
    if (sensors.buttonValue(InputPorts.P2) == 0) {
        actuators.StopMotor(OutputPorts.P8)
        music.stopAllSounds()
    }
})
basic.forever(function () {
    if (sensors.buttonValue(InputPorts.P2) == 1) {
        actuators.SetSpeedMotor(100, OutputPorts.P8)
        if (musica == 1) {
            music.play(music.stringPlayable("C5 B A G F E D C ", 120), music.PlaybackMode.UntilDone)
        } else if (musica == 2) {
            music.play(music.stringPlayable("C D E F G A B C5 ", 120), music.PlaybackMode.UntilDone)
        } else if (musica == 3) {
            music.play(music.stringPlayable("E B C5 A B G A F ", 120), music.PlaybackMode.UntilDone)
        }
    }
})
```

```package
fuzzyBot=github:FuzzyMakers/pxt-fuzzyMakers
```