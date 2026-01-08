### @diffs true
# Irrigação automática

## Passo 1
Neste tutorial, vamos programar um dispositivo de irrigação automática. O veículo andará até 
encontrar uma planta, em seguida, vai regá-la caso esteja abastecido. Quando o tanque de água estiver vazio, deve-se 
apertar a chave de fim de curso para abastecer a máquina. O display do micro:bit indicará o nível de água.
## Passo 2
Para começar, verifique se a biblioteca da Smart Makers já está importada 
em seu MakeCode. Se não estiver, clique na aba **+ Extensões**, 
copie o endereço "https://github.com/FuzzyMakers/pxt-smartMakers",
cole-o no campo de pesquisa da janela que se abriu e selecione a biblioteca.

## Passo 3
Acesse o menu ``||variables:Variáveis||`` e clique em 
**"Fazer uma variável..."**. Crie uma variável chamada
``||variables:consumo||``. Em seguida, arraste o bloco ``||variables:definir consumo para 0||`` 
para o bloco ``||basic:no iniciar||``.

```blocks
let consumo = 0
```


## Passo 4

Vá à categoria ``||math:Matemática||``, pegue a operação soma ``||math:0 + 0||``
e substitua o valor **0** da definição da variável.
```blocks
let consumo = 0 + 0
```
## Passo 5
Agora atualize os campos da soma. Substitua o primeiro campo com o valor **100**. 
Em seguida, vá até a aba ``||math:Matemática||``,
clique outra vez em ``||math: 0 + 0||`` e troque o segundo campo por esta nova soma.

```blocks
let consumo = 100 + (0 + 0)
```



## Passo 6

Acesse mais uma vez a aba ``||math:Matemática||``,  pegue duas operações de multiplicação ``||math:0 x 0||`` e
atualize os campos da segunda soma.

```blocks
let consumo = 100 + (0 * 0 + 0 * 0)
```


## Passo 7

Altere os quatro campos das multiplicações: O primeiro receberá o valor **20**,
o segundo a ``||input:temperatura °C||`` retirada do menu ``||input:Entrada||``,
o terceiro o valor **15** e o quarto o ``||input:nível de luz||`` retirado também do menu ``||input:Entrada||``.

```blocks
let consumo = 100 + (20 * input.temperature() + 15 * input.lightLevel())
```

## Passo 8
Clique no menu ``||Advanced:Avançado||``, acesse ``||Functions:Funções||`` e 
clique em **Fazer uma função...**.
Clique no campo editável do laço azul para criar uma função chamada 
``||functions:abastecer||``. 
Um novo laço referente à função criada é adicionado automaticamente à área de programação.

```blocks
function abastecer () {
	
}
let consumo = 100 + (20 * input.temperature() + 15 * input.lightLevel())

```

## Passo 9
Acesse a aba ``||music:Música||`` e adicione o bloco ``||music:stop all sounds||`` 
dentro dessa função ``||functions:abastecer||``.

```blocks
function abastecer () {
    music.stopAllSounds()
}
let consumo = 100 + (20 * input.temperature() + 15 * input.lightLevel())

```

## Passo 10

Acesse a categoria ``||actuators:Atuadores||`` e adicione um comando 
``||actuators:Motor CC, parar motor na porta P8||`` dentro da função ``||functions:abastecer||``.

```blocks
function abastecer () {
    music.stopAllSounds()
    actuators.StopMotor(OutputPorts.P8)
}
let consumo = 100 + (20 * input.temperature() + 15 * input.lightLevel())

```

## Passo 11
Vá ao menu ``||loops:Loops||`` e arraste um laço ``||loops:enquanto executar||`` para a função.

```blocks
function abastecer () {
    music.stopAllSounds()
    actuators.StopMotor(OutputPorts.P8)
    while (false) {
    	
    }
}
let consumo = 100 + (20 * input.temperature() + 15 * input.lightLevel())


```

## Passo 12

Na aba ``||logic:Lógica||`` pegue o comparador ``||logic:0 = 0||``
e substitua a condição **falso** do laço.

```blocks
function abastecer () {
    music.stopAllSounds()
    actuators.StopMotor(OutputPorts.P8)
    while (0 == 0) {
    	
    }
}
let consumo = 100 + (20 * input.temperature() + 15 * input.lightLevel())
```
## Passo 13

Agora atualize os campos do comparador. Vá até a aba ``||sensors:Sensores||``,
clique em ``||sensors:Valor da chave de fim de curso na porta P2||`` e troque o primeiro **0** do comparador.
Em seguida, mude o segundo campo para **1**. 
```blocks
function abastecer () {
    music.stopAllSounds()
    actuators.StopMotor(OutputPorts.P8)
    while (sensors.endstopValue(InputPorts.P2) == 1) {
    	
    }
}
let consumo = 100 + (20 * input.temperature() + 15 * input.lightLevel())
```

## Passo 14

Acesse a categoria ``||music:Múscia||`` e busque pelo comando ``||music:play (onda sonora) until done||`` 
para inseri-lo no laço. 
Clique na onda sonora, edite a duração para **200 ms** e a frequência para começar próxima de **200 Hz** e terminar próxima de **600 Hz**.

```blocks
function abastecer () {
    music.stopAllSounds()
    actuators.StopMotor(OutputPorts.P8)
    while (sensors.endstopValue(InputPorts.P2) == 1) {
        music.play(music.createSoundExpression(WaveShape.Sine, 188, 584, 255, 0, 200, SoundExpressionEffect.None, InterpolationCurve.Linear), music.PlaybackMode.UntilDone)
    }
}
let consumo = 100 + (20 * input.temperature() + 15 * input.lightLevel())

```

## Passo 15
Acesse o menu ``||variables:Variáveis||`` e clique em 
**"Fazer uma variável..."**. Crie uma variável chamada 
``||variables:água||`` e, depois de criá-la, adicione o bloco 
``||variables:alterar água por 1||`` dentro do ``||loops:enquanto||``.
Altere o valor do incremento da ``||variables:água||`` de **1** para **200**.

```blocks
let água = 0
function abastecer () {
    music.stopAllSounds()
    actuators.StopMotor(OutputPorts.P8)
    while (sensors.endstopValue(InputPorts.P2) == 1) {
        music.play(music.createSoundExpression(WaveShape.Sine, 188, 584, 255, 0, 200, SoundExpressionEffect.None, InterpolationCurve.Linear), music.PlaybackMode.UntilDone)
        água += 200
    }
}
let consumo = 100 + (20 * input.temperature() + 15 * input.lightLevel())
```

## Passo 16

Depois do laço, coloque um comando ``||actuators:Motor CC, definir velocidade 0 na porta P8||`` encontrado na aba ``||actuators:Atuadores||``. 
Modifique o valor da velocidade para **1023**.
```blocks
function abastecer () {
    music.stopAllSounds()
    actuators.StopMotor(OutputPorts.P8)
    while (sensors.endstopValue(InputPorts.P2) == 1) {
        music.play(music.createSoundExpression(WaveShape.Sine, 188, 584, 255, 0, 200, SoundExpressionEffect.None, InterpolationCurve.Linear), music.PlaybackMode.UntilDone)
        água += 200
    }
    actuators.SetSpeedMotor(1023, OutputPorts.P8)
}
let água = 0
let consumo = 100 + (20 * input.temperature() + 15 * input.lightLevel())
```

## Passo 17
Clique no menu ``||Advanced:Avançado||``, acesse ``||Functions:Funções||`` e 
clique em **Fazer uma função...**.
Clique no campo editável do laço azul para criar uma função chamada 
``||functions:regar||``. 
Um novo laço referente à função criada é adicionado automaticamente à área de programação.


```blocks
function abastecer () {
    music.stopAllSounds()
    actuators.StopMotor(OutputPorts.P8)
    while (sensors.endstopValue(InputPorts.P2) == 1) {
        music.play(music.createSoundExpression(WaveShape.Sine, 188, 584, 255, 0, 200, SoundExpressionEffect.None, InterpolationCurve.Linear), music.PlaybackMode.UntilDone)
        água += 200
    }
    actuators.SetSpeedMotor(1023, OutputPorts.P8)
}
function regar () {
    }
let água = 0
let consumo = 100 + (20 * input.temperature() + 15 * input.lightLevel())
```

## Passo 18

Duplique o comando ``||actuators:Motor CC, parar motor na porta P8||`` da função
``||Functions:abastecer||`` a coloque também na função ``||Functions:regar||``.


```blocks
function abastecer () {
    music.stopAllSounds()
    actuators.StopMotor(OutputPorts.P8)
    while (sensors.endstopValue(InputPorts.P2) == 1) {
        music.play(music.createSoundExpression(WaveShape.Sine, 188, 584, 255, 0, 200, SoundExpressionEffect.None, InterpolationCurve.Linear), music.PlaybackMode.UntilDone)
        água += 200
    }
    actuators.SetSpeedMotor(1023, OutputPorts.P8)
}
function regar () {
    actuators.StopMotor(OutputPorts.P8)
}
let água = 0
let consumo = 100 + (20 * input.temperature() + 15 * input.lightLevel())
```
## Passo 19

Acesse o menu ``||variables:Variáveis||`` e clique em 
**"Fazer uma variável..."**. Crie uma variável chamada 
``||variables:água distribuída||`` e, depois de criá-la, adicione o bloco 
``||variables:definir água distribuída para 0||`` dentro de ``||Functions:regar||``.

```blocks
function abastecer () {
    music.stopAllSounds()
    actuators.StopMotor(OutputPorts.P8)
    while (sensors.endstopValue(InputPorts.P2) == 1) {
        music.play(music.createSoundExpression(WaveShape.Sine, 188, 584, 255, 0, 200, SoundExpressionEffect.None, InterpolationCurve.Linear), music.PlaybackMode.UntilDone)
        água += 200
    }
    actuators.SetSpeedMotor(1023, OutputPorts.P8)
}
function regar () {
    actuators.StopMotor(OutputPorts.P8)
    agua_distribuída = 0
}
let agua_distribuída = 0
let água = 0
let consumo = 100 + (20 * input.temperature() + 15 * input.lightLevel())

```

## Passo 20

Acesse a categoria ``||logic:Lógica||``, clique na condicional ``||logic:se então senão||``
e insira-a na função ``||Functions:regar||``.

```blocks
function abastecer () {
    music.stopAllSounds()
    actuators.StopMotor(OutputPorts.P8)
    while (sensors.endstopValue(InputPorts.P2) == 1) {
        music.play(music.createSoundExpression(WaveShape.Sine, 188, 584, 255, 0, 200, SoundExpressionEffect.None, InterpolationCurve.Linear), music.PlaybackMode.UntilDone)
        água += 200
    }
    actuators.SetSpeedMotor(1023, OutputPorts.P8)
}
function regar () {
    actuators.StopMotor(OutputPorts.P8)
    agua_distribuída = 0
    if (true) {
    	
    } else {
    	
    }
}
let agua_distribuída = 0
let água = 0
let consumo = 100 + (20 * input.temperature() + 15 * input.lightLevel())


```
## Passo 21
Volte ao menu ``||logic:Lógica||``, pegue o comparador ``||logic:0 < 0||``
e substitua a condição **verdadeiro** da condicional.

```blocks
function abastecer () {
    music.stopAllSounds()
    actuators.StopMotor(OutputPorts.P8)
    while (sensors.endstopValue(InputPorts.P2) == 1) {
        music.play(music.createSoundExpression(WaveShape.Sine, 188, 584, 255, 0, 200, SoundExpressionEffect.None, InterpolationCurve.Linear), music.PlaybackMode.UntilDone)
        água += 200
    }
    actuators.SetSpeedMotor(1023, OutputPorts.P8)
}
function regar () {
    actuators.StopMotor(OutputPorts.P8)
    agua_distribuída = 0
    if (0 < 0) {
    	
    } else {
    	
    }
}
let agua_distribuída = 0
let água = 0
let consumo = 100 + (20 * input.temperature() + 15 * input.lightLevel())

```

## Passo 22

Agora atualize os campos do comparador. Vá até a aba ``||variables:Variáveis||``,
troque o primeiro **0** do comparador por ``||variables:água||`` e o segundo por ``||variables:consumo||``.
Antes de prosseguir, altere o sinal **<** para **>**.
```blocks
function abastecer () {
    music.stopAllSounds()
    actuators.StopMotor(OutputPorts.P8)
    while (sensors.endstopValue(InputPorts.P2) == 1) {
        music.play(music.createSoundExpression(WaveShape.Sine, 188, 584, 255, 0, 200, SoundExpressionEffect.None, InterpolationCurve.Linear), music.PlaybackMode.UntilDone)
        água += 200
    }
    actuators.SetSpeedMotor(1023, OutputPorts.P8)
}
function regar () {
    actuators.StopMotor(OutputPorts.P8)
    agua_distribuída = 0
    if (água > consumo) {
    	
    } else {
    	
    }
}
let agua_distribuída = 0
let água = 0
let consumo = 0
consumo = 100 + (20 * input.temperature() + 15 * input.lightLevel())
```

## Passo 23
Acesse a aba ``||music:Música||`` e adicione o bloco ``||music:stop all sounds||`` 
dentro da condicional ``||logic:se água > consumo||``.

```blocks
function abastecer () {
    music.stopAllSounds()
    actuators.StopMotor(OutputPorts.P8)
    while (sensors.endstopValue(InputPorts.P2) == 1) {
        music.play(music.createSoundExpression(WaveShape.Sine, 188, 584, 255, 0, 200, SoundExpressionEffect.None, InterpolationCurve.Linear), music.PlaybackMode.UntilDone)
        água += 200
    }
    actuators.SetSpeedMotor(1023, OutputPorts.P8)
}
function regar () {
    actuators.StopMotor(OutputPorts.P8)
    agua_distribuída = 0
    if (água > consumo) {
        music.stopAllSounds()
    } else {
    	
    }
}
let agua_distribuída = 0
let água = 0
let consumo = 0
consumo = 100 + (20 * input.temperature() + 15 * input.lightLevel())


```

## Passo 24
Copie o laço ``||loops:enquanto executar||`` da função ``||functions:abastecer||``
para a função ``||functions:regar||`` abaixo do último bloco adicionado.

```blocks
function abastecer () {
    music.stopAllSounds()
    actuators.StopMotor(OutputPorts.P8)
    while (sensors.endstopValue(InputPorts.P2) == 1) {
        music.play(music.createSoundExpression(WaveShape.Sine, 188, 584, 255, 0, 200, SoundExpressionEffect.None, InterpolationCurve.Linear), music.PlaybackMode.UntilDone)
        água += 200
    }
    actuators.SetSpeedMotor(1023, OutputPorts.P8)
}
function regar () {
    actuators.StopMotor(OutputPorts.P8)
    agua_distribuída = 0
    if (água > consumo) {
        music.stopAllSounds()
        while (sensors.endstopValue(InputPorts.P2) == 1) {
            água += 200
            music.play(music.createSoundExpression(WaveShape.Sine, 188, 584, 255, 0, 200, SoundExpressionEffect.None, InterpolationCurve.Linear), music.PlaybackMode.UntilDone)
            
        }
    } else {
    	
    }
}
let agua_distribuída = 0
let água = 0
let consumo = 0
consumo = 100 + (20 * input.temperature() + 15 * input.lightLevel())

```

## Passo 25

Edite os valores do comparador do novo ``||loops:enquanto executar||``. Busque
a variável ``||variables:água distribuída||`` para colocar no lugar de
``||sensors:Valor da chave de fim de curso na porta P2||`` e a variável ``||variables:consumo||``
no lugar do valor **1**. 
Antes de prosseguir, modifique o sinal **=** para **<**.

```blocks
function abastecer () {
    music.stopAllSounds()
    actuators.StopMotor(OutputPorts.P8)
    while (sensors.endstopValue(InputPorts.P2) == 1) {
        music.play(music.createSoundExpression(WaveShape.Sine, 188, 584, 255, 0, 200, SoundExpressionEffect.None, InterpolationCurve.Linear), music.PlaybackMode.UntilDone)
        água += 200
    }
    actuators.SetSpeedMotor(1023, OutputPorts.P8)
}
function regar () {
    actuators.StopMotor(OutputPorts.P8)
    agua_distribuída = 0
    if (água > consumo) {
        music.stopAllSounds()
        while (agua_distribuída < consumo) {
            água += 200
            music.play(music.createSoundExpression(WaveShape.Sine, 188, 584, 255, 0, 200, SoundExpressionEffect.None, InterpolationCurve.Linear), music.PlaybackMode.UntilDone)
            
        }
    } else {
    	
    }
}
let agua_distribuída = 0
let água = 0
let consumo = 0
consumo = 100 + (20 * input.temperature() + 15 * input.lightLevel())


```

## Passo 26

No conteúdo do novo laço ``||loops:enquanto executar||`` clique na onda sonora e altere seu formato de 
senóide (sine) para serrote (sawtooth).
Modifique o incremento de ``||variables:água||`` de **200** para **-200**.

```blocks
function abastecer () {
    music.stopAllSounds()
    actuators.StopMotor(OutputPorts.P8)
    while (sensors.endstopValue(InputPorts.P2) == 1) {
        music.play(music.createSoundExpression(WaveShape.Sine, 188, 584, 255, 0, 200, SoundExpressionEffect.None, InterpolationCurve.Linear), music.PlaybackMode.UntilDone)
        água += 200
    }
    actuators.SetSpeedMotor(1023, OutputPorts.P8)
}
function regar () {
    actuators.StopMotor(OutputPorts.P8)
    agua_distribuída = 0
    if (água > consumo) {
        music.stopAllSounds()
        while (agua_distribuída < consumo) {
            água += -200
            music.play(music.createSoundExpression(WaveShape.Sawtooth, 188, 584, 255, 0, 200, SoundExpressionEffect.None, InterpolationCurve.Linear), music.PlaybackMode.UntilDone)
            
        }
    } else {
    	
    }
}
let agua_distribuída = 0
let água = 0
let consumo = 0
consumo = 100 + (20 * input.temperature() + 15 * input.lightLevel())

```

## Passo 27

Ainda dentro do novo laço ``||loop:enquanto executar||`` adicione um 
``||variables:alterar água distribuída por 1||`` retirado da categoria ``||variables:Variáveis||``.
Modifique o valor do incremento de **1** para **200**.

```blocks
function abastecer () {
    music.stopAllSounds()
    actuators.StopMotor(OutputPorts.P8)
    while (sensors.endstopValue(InputPorts.P2) == 1) {
        music.play(music.createSoundExpression(WaveShape.Sine, 188, 584, 255, 0, 200, SoundExpressionEffect.None, InterpolationCurve.Linear), music.PlaybackMode.UntilDone)
        água += 200
    }
    actuators.SetSpeedMotor(1023, OutputPorts.P8)
}
function regar () {
    actuators.StopMotor(OutputPorts.P8)
    agua_distribuída = 0
    if (água > consumo) {
        music.stopAllSounds()
        while (agua_distribuída < consumo) {
            água += -200
            agua_distribuída += 200
            music.play(music.createSoundExpression(WaveShape.Sawtooth, 188, 584, 255, 0, 200, SoundExpressionEffect.None, InterpolationCurve.Linear), music.PlaybackMode.UntilDone)
            
        }
    } else {
    	
    }
}
let agua_distribuída = 0
let água = 0
let consumo = 0
consumo = 100 + (20 * input.temperature() + 15 * input.lightLevel())


```
## Passo 28

Duplique o comando ``||actuators:Motor CC, definir velocidade 1023 na porta P8||``
e adicione-o após o laço ``||loops:enquanto executar||``.

```blocks
function abastecer () {
    music.stopAllSounds()
    actuators.StopMotor(OutputPorts.P8)
    while (sensors.endstopValue(InputPorts.P2) == 1) {
        music.play(music.createSoundExpression(WaveShape.Sine, 188, 584, 255, 0, 200, SoundExpressionEffect.None, InterpolationCurve.Linear), music.PlaybackMode.UntilDone)
        água += 200
    }
    actuators.SetSpeedMotor(1023, OutputPorts.P8)
}
function regar () {
    actuators.StopMotor(OutputPorts.P8)
    agua_distribuída = 0
    if (água > consumo) {
        music.stopAllSounds()
        while (agua_distribuída < consumo) {
            água += -200
            agua_distribuída += 200
            music.play(music.createSoundExpression(WaveShape.Sawtooth, 188, 584, 255, 0, 200, SoundExpressionEffect.None, InterpolationCurve.Linear), music.PlaybackMode.UntilDone)
        }
        actuators.SetSpeedMotor(1023, OutputPorts.P8)
    } else {
    	
    }
}
let agua_distribuída = 0
let água = 0
let consumo = 0
consumo = 100 + (20 * input.temperature() + 15 * input.lightLevel())
```

## Passo 29

Na categoria ``||basic:Básico||`` arraste uma pausa ``||basic:pausa (ms) 100||`` para o código,
depois mude seu valor para **2000**.

```blocks
function abastecer () {
    music.stopAllSounds()
    actuators.StopMotor(OutputPorts.P8)
    while (sensors.endstopValue(InputPorts.P2) == 1) {
        music.play(music.createSoundExpression(WaveShape.Sine, 188, 584, 255, 0, 200, SoundExpressionEffect.None, InterpolationCurve.Linear), music.PlaybackMode.UntilDone)
        água += 200
    }
    actuators.SetSpeedMotor(1023, OutputPorts.P8)
}
function regar () {
    actuators.StopMotor(OutputPorts.P8)
    agua_distribuída = 0
    if (água > consumo) {
        music.stopAllSounds()
        while (agua_distribuída < consumo) {
            água += -200
            agua_distribuída += 200
            music.play(music.createSoundExpression(WaveShape.Sawtooth, 188, 584, 255, 0, 200, SoundExpressionEffect.None, InterpolationCurve.Linear), music.PlaybackMode.UntilDone)
        }
        actuators.SetSpeedMotor(1023, OutputPorts.P8)
        basic.pause(2000)
    } else {
    	
    }
}
let agua_distribuída = 0
let água = 0
let consumo = 0
consumo = 100 + (20 * input.temperature() + 15 * input.lightLevel())

```
## Passo 30

Volte ao menu ``||music:Música||`` e clique no comando ``||music:toque (Hz) C Médio||``
para inseri-lo na condicional ``||logic:senão||``.


```blocks
function abastecer () {
    music.stopAllSounds()
    actuators.StopMotor(OutputPorts.P8)
    while (sensors.endstopValue(InputPorts.P2) == 1) {
        music.play(music.createSoundExpression(WaveShape.Sine, 188, 584, 255, 0, 200, SoundExpressionEffect.None, InterpolationCurve.Linear), music.PlaybackMode.UntilDone)
        água += 200
    }
    actuators.SetSpeedMotor(1023, OutputPorts.P8)
}
function regar () {
    actuators.StopMotor(OutputPorts.P8)
    agua_distribuída = 0
    if (água > consumo) {
        music.stopAllSounds()
        while (agua_distribuída < consumo) {
            água += -200
            agua_distribuída += 200
            music.play(music.createSoundExpression(WaveShape.Sawtooth, 188, 584, 255, 0, 200, SoundExpressionEffect.None, InterpolationCurve.Linear), music.PlaybackMode.UntilDone)
        }
        actuators.SetSpeedMotor(1023, OutputPorts.P8)
        basic.pause(2000)
    } else {
        music.ringTone(262)
    }
}
let agua_distribuída = 0
let água = 0
let consumo = 0
consumo = 100 + (20 * input.temperature() + 15 * input.lightLevel())


```
## Passo 31

Acesse a categoria ``||logic:Lógica||``, clique na condicional ``||logic:se então senão||``
e insira-a dentro do bloco ``||basic:sempre||``.

```blocks
function abastecer () {
    music.stopAllSounds()
    actuators.StopMotor(OutputPorts.P8)
    while (sensors.endstopValue(InputPorts.P2) == 1) {
        music.play(music.createSoundExpression(WaveShape.Sine, 188, 584, 255, 0, 200, SoundExpressionEffect.None, InterpolationCurve.Linear), music.PlaybackMode.UntilDone)
        água += 200
    }
    actuators.SetSpeedMotor(1023, OutputPorts.P8)
}
function regar () {
    actuators.StopMotor(OutputPorts.P8)
    agua_distribuída = 0
    if (água > consumo) {
        music.stopAllSounds()
        while (agua_distribuída < consumo) {
            água += -200
            agua_distribuída += 200
            music.play(music.createSoundExpression(WaveShape.Sawtooth, 188, 584, 255, 0, 200, SoundExpressionEffect.None, InterpolationCurve.Linear), music.PlaybackMode.UntilDone)
        }
        actuators.SetSpeedMotor(1023, OutputPorts.P8)
        basic.pause(2000)
    } else {
        music.ringTone(262)
    }
}
let agua_distribuída = 0
let água = 0
let consumo = 0
consumo = 100 + (20 * input.temperature() + 15 * input.lightLevel())
basic.forever(function () {
    if (true) {
    	
    } else {
    	
    }
})


```

## Passo 32
Volte ao menu ``||logic:Lógica||``, pegue o comparador ``||logic:0 = 0||``
e substitua a condição **verdadeiro** da condicional.

```blocks
function abastecer () {
    music.stopAllSounds()
    actuators.StopMotor(OutputPorts.P8)
    while (sensors.endstopValue(InputPorts.P2) == 1) {
        music.play(music.createSoundExpression(WaveShape.Sine, 188, 584, 255, 0, 200, SoundExpressionEffect.None, InterpolationCurve.Linear), music.PlaybackMode.UntilDone)
        água += 200
    }
    actuators.SetSpeedMotor(1023, OutputPorts.P8)
}
function regar () {
    actuators.StopMotor(OutputPorts.P8)
    agua_distribuída = 0
    if (água > consumo) {
        music.stopAllSounds()
        while (agua_distribuída < consumo) {
            água += -200
            agua_distribuída += 200
            music.play(music.createSoundExpression(WaveShape.Sawtooth, 188, 584, 255, 0, 200, SoundExpressionEffect.None, InterpolationCurve.Linear), music.PlaybackMode.UntilDone)
        }
        actuators.SetSpeedMotor(1023, OutputPorts.P8)
        basic.pause(2000)
    } else {
        music.ringTone(262)
    }
}
let agua_distribuída = 0
let água = 0
let consumo = 0
consumo = 100 + (20 * input.temperature() + 15 * input.lightLevel())
basic.forever(function () {
    if (0 == 0) {
    	
    } else {
    	
    }
})

```

## Passo 33

Agora atualize os campos do comparador. Vá até a aba ``||sensors:Sensores||``,
clique em ``||sensors:Valor da chave de fim de curso na porta P2||`` e troque o primeiro **0** do comparador.
Em seguida, mude o segundo campo para **1**. 
```blocks
function abastecer () {
    music.stopAllSounds()
    actuators.StopMotor(OutputPorts.P8)
    while (sensors.endstopValue(InputPorts.P2) == 1) {
        music.play(music.createSoundExpression(WaveShape.Sine, 188, 584, 255, 0, 200, SoundExpressionEffect.None, InterpolationCurve.Linear), music.PlaybackMode.UntilDone)
        água += 200
    }
    actuators.SetSpeedMotor(1023, OutputPorts.P8)
}
function regar () {
    actuators.StopMotor(OutputPorts.P8)
    agua_distribuída = 0
    if (água > consumo) {
        music.stopAllSounds()
        while (agua_distribuída < consumo) {
            água += -200
            agua_distribuída += 200
            music.play(music.createSoundExpression(WaveShape.Sawtooth, 188, 584, 255, 0, 200, SoundExpressionEffect.None, InterpolationCurve.Linear), music.PlaybackMode.UntilDone)
        }
        actuators.SetSpeedMotor(1023, OutputPorts.P8)
        basic.pause(2000)
    } else {
        music.ringTone(262)
    }
}
let agua_distribuída = 0
let água = 0
let consumo = 0
consumo = 100 + (20 * input.temperature() + 15 * input.lightLevel())
basic.forever(function () {
    if (sensors.endstopValue(InputPorts.P2) == 1) {
    	
    } else {
    	
    }
})


```

## Passo 34

No menu ``||functions:Funções||`` arraste o comando  ``||functions:ligar abastecer||``
para dentro da condição ``||logic:se então||``.

```blocks
function abastecer () {
    music.stopAllSounds()
    actuators.StopMotor(OutputPorts.P8)
    while (sensors.endstopValue(InputPorts.P2) == 1) {
        music.play(music.createSoundExpression(WaveShape.Sine, 188, 584, 255, 0, 200, SoundExpressionEffect.None, InterpolationCurve.Linear), music.PlaybackMode.UntilDone)
        água += 200
    }
    actuators.SetSpeedMotor(1023, OutputPorts.P8)
}
function regar () {
    actuators.StopMotor(OutputPorts.P8)
    agua_distribuída = 0
    if (água > consumo) {
        music.stopAllSounds()
        while (agua_distribuída < consumo) {
            água += -200
            agua_distribuída += 200
            music.play(music.createSoundExpression(WaveShape.Sawtooth, 188, 584, 255, 0, 200, SoundExpressionEffect.None, InterpolationCurve.Linear), music.PlaybackMode.UntilDone)
        }
        actuators.SetSpeedMotor(1023, OutputPorts.P8)
        basic.pause(2000)
    } else {
        music.ringTone(262)
    }
}
let agua_distribuída = 0
let água = 0
let consumo = 0
consumo = 100 + (20 * input.temperature() + 15 * input.lightLevel())
basic.forever(function () {
    if (sensors.endstopValue(InputPorts.P2) == 1) {
        abastecer()
    } else {
    	
    }
})
```
## Passo 35

Volte à categoria ``||logic:Lógica||`` e pegue outra condicional ``||logic:se então senão||``
que irá ser inserida dentro do ``||logic:senão||`` anterior.

```blocks
function abastecer () {
    music.stopAllSounds()
    actuators.StopMotor(OutputPorts.P8)
    while (sensors.endstopValue(InputPorts.P2) == 1) {
        music.play(music.createSoundExpression(WaveShape.Sine, 188, 584, 255, 0, 200, SoundExpressionEffect.None, InterpolationCurve.Linear), music.PlaybackMode.UntilDone)
        água += 200
    }
    actuators.SetSpeedMotor(1023, OutputPorts.P8)
}
function regar () {
    actuators.StopMotor(OutputPorts.P8)
    agua_distribuída = 0
    if (água > consumo) {
        music.stopAllSounds()
        while (agua_distribuída < consumo) {
            água += -200
            agua_distribuída += 200
            music.play(music.createSoundExpression(WaveShape.Sawtooth, 188, 584, 255, 0, 200, SoundExpressionEffect.None, InterpolationCurve.Linear), music.PlaybackMode.UntilDone)
        }
        actuators.SetSpeedMotor(1023, OutputPorts.P8)
        basic.pause(2000)
    } else {
        music.ringTone(262)
    }
}
let agua_distribuída = 0
let água = 0
let consumo = 0
consumo = 100 + (20 * input.temperature() + 15 * input.lightLevel())
basic.forever(function () {
    if (sensors.endstopValue(InputPorts.P2) == 1) {
        abastecer()
    } else {
        if (true) {
        	
        } else {
        	
        }
    }
})

```

## Passo 36
Volte ao menu ``||logic:Lógica||``, pegue o comparador ``||logic:0 < 0||``
e substitua a condição **verdadeiro** da condicional.

```blocks
function abastecer () {
    music.stopAllSounds()
    actuators.StopMotor(OutputPorts.P8)
    while (sensors.endstopValue(InputPorts.P2) == 1) {
        music.play(music.createSoundExpression(WaveShape.Sine, 188, 584, 255, 0, 200, SoundExpressionEffect.None, InterpolationCurve.Linear), music.PlaybackMode.UntilDone)
        água += 200
    }
    actuators.SetSpeedMotor(1023, OutputPorts.P8)
}
function regar () {
    actuators.StopMotor(OutputPorts.P8)
    agua_distribuída = 0
    if (água > consumo) {
        music.stopAllSounds()
        while (agua_distribuída < consumo) {
            água += -200
            agua_distribuída += 200
            music.play(music.createSoundExpression(WaveShape.Sawtooth, 188, 584, 255, 0, 200, SoundExpressionEffect.None, InterpolationCurve.Linear), music.PlaybackMode.UntilDone)
        }
        actuators.SetSpeedMotor(1023, OutputPorts.P8)
        basic.pause(2000)
    } else {
        music.ringTone(262)
    }
}
consumo = 100 + (20 * input.temperature() + 15 * input.lightLevel())
basic.forever(function () {
    if (sensors.endstopValue(InputPorts.P2) == 1) {
        abastecer()
    } else {
        if (0 < 0) {
        	
        } else {
        	
        }
    }
})
let agua_distribuída = 0
let água = 0
let consumo = 0
```

## Passo 37

Agora atualize os campos do comparador. Vá até a aba ``||sensors:Sensores||``,
clique em ``||sensors:Valor do sensor infravermelho na porta P2||`` e troque o primeiro **0** do comparador.
Atualize a porta para ``||sensors:P1||``. Em seguida, mude o segundo campo para **200**. 

```blocks
function abastecer () {
    music.stopAllSounds()
    actuators.StopMotor(OutputPorts.P8)
    while (sensors.endstopValue(InputPorts.P2) == 1) {
        music.play(music.createSoundExpression(WaveShape.Sine, 188, 584, 255, 0, 200, SoundExpressionEffect.None, InterpolationCurve.Linear), music.PlaybackMode.UntilDone)
        água += 200
    }
    actuators.SetSpeedMotor(1023, OutputPorts.P8)
}
function regar () {
    actuators.StopMotor(OutputPorts.P8)
    agua_distribuída = 0
    if (água > consumo) {
        music.stopAllSounds()
        while (agua_distribuída < consumo) {
            água += -200
            agua_distribuída += 200
            music.play(music.createSoundExpression(WaveShape.Sawtooth, 188, 584, 255, 0, 200, SoundExpressionEffect.None, InterpolationCurve.Linear), music.PlaybackMode.UntilDone)
        }
        actuators.SetSpeedMotor(1023, OutputPorts.P8)
        basic.pause(2000)
    } else {
        music.ringTone(262)
    }
}
consumo = 100 + (20 * input.temperature() + 15 * input.lightLevel())
basic.forever(function () {
    if (sensors.endstopValue(InputPorts.P2) == 1) {
        abastecer()
    } else {
        if (sensors.infraredValue(InputPorts.P1) < 200) {
        	
        } else {
        	
        }
    }
})
let agua_distribuída = 0
let água = 0
let consumo = 0
```
## Passo 38

Duplique o comando ``||actuators:Motor CC, definir velocidade 1023 na porta P8||``
e o adicione na condicional ``||logic:se Valor do sensor infravermelho na porta P1 < 200 então||``.

```blocks
function abastecer () {
    music.stopAllSounds()
    actuators.StopMotor(OutputPorts.P8)
    while (sensors.endstopValue(InputPorts.P2) == 1) {
        music.play(music.createSoundExpression(WaveShape.Sine, 188, 584, 255, 0, 200, SoundExpressionEffect.None, InterpolationCurve.Linear), music.PlaybackMode.UntilDone)
        água += 200
    }
    actuators.SetSpeedMotor(1023, OutputPorts.P8)
}
function regar () {
    actuators.StopMotor(OutputPorts.P8)
    agua_distribuída = 0
    if (água > consumo) {
        music.stopAllSounds()
        while (agua_distribuída < consumo) {
            água += -200
            agua_distribuída += 200
            music.play(music.createSoundExpression(WaveShape.Sawtooth, 188, 584, 255, 0, 200, SoundExpressionEffect.None, InterpolationCurve.Linear), music.PlaybackMode.UntilDone)
        }
        actuators.SetSpeedMotor(1023, OutputPorts.P8)
        basic.pause(2000)
    } else {
        music.ringTone(262)
    }
}
consumo = 100 + (20 * input.temperature() + 15 * input.lightLevel())
basic.forever(function () {
    if (sensors.endstopValue(InputPorts.P2) == 1) {
        abastecer()
    } else {
        if (sensors.infraredValue(InputPorts.P1) < 200) {
            actuators.SetSpeedMotor(1023, OutputPorts.P8)
        } else {
        	
        }
    }
})
let agua_distribuída = 0
let água = 0
let consumo = 0
```
## Passo 39

No menu ``||functions:Funções||`` arraste o comando  ``||functions:ligar regar||``
para dentro da condição ``||logic:senão||``.

```blocks
function abastecer () {
    music.stopAllSounds()
    actuators.StopMotor(OutputPorts.P8)
    while (sensors.endstopValue(InputPorts.P2) == 1) {
        music.play(music.createSoundExpression(WaveShape.Sine, 188, 584, 255, 0, 200, SoundExpressionEffect.None, InterpolationCurve.Linear), music.PlaybackMode.UntilDone)
        água += 200
    }
    actuators.SetSpeedMotor(1023, OutputPorts.P8)
}
function regar () {
    actuators.StopMotor(OutputPorts.P8)
    agua_distribuída = 0
    if (água > consumo) {
        music.stopAllSounds()
        while (agua_distribuída < consumo) {
            água += -200
            agua_distribuída += 200
            music.play(music.createSoundExpression(WaveShape.Sawtooth, 188, 584, 255, 0, 200, SoundExpressionEffect.None, InterpolationCurve.Linear), music.PlaybackMode.UntilDone)
        }
        actuators.SetSpeedMotor(1023, OutputPorts.P8)
        basic.pause(2000)
    } else {
        music.ringTone(262)
    }
}
consumo = 100 + (20 * input.temperature() + 15 * input.lightLevel())
basic.forever(function () {
    if (sensors.endstopValue(InputPorts.P2) == 1) {
        abastecer()
    } else {
        if (sensors.infraredValue(InputPorts.P1) < 200) {
            actuators.SetSpeedMotor(1023, OutputPorts.P8)
        } else {
            regar()
        }
    }
})
let agua_distribuída = 0
let água = 0
let consumo = 0
```
## Passo 40

Acesse a categoria ``||basic:Básico||``, pegue outro laço ``||basic:sempre||`` e coloque-o na área de programação.
```blocks
function abastecer () {
    music.stopAllSounds()
    actuators.StopMotor(OutputPorts.P8)
    while (sensors.endstopValue(InputPorts.P2) == 1) {
        music.play(music.createSoundExpression(WaveShape.Sine, 188, 584, 255, 0, 200, SoundExpressionEffect.None, InterpolationCurve.Linear), music.PlaybackMode.UntilDone)
        água += 200
    }
    actuators.SetSpeedMotor(1023, OutputPorts.P8)
}
function regar () {
    actuators.StopMotor(OutputPorts.P8)
    agua_distribuída = 0
    if (água > consumo) {
        music.stopAllSounds()
        while (agua_distribuída < consumo) {
            água += -200
            agua_distribuída += 200
            music.play(music.createSoundExpression(WaveShape.Sawtooth, 188, 584, 255, 0, 200, SoundExpressionEffect.None, InterpolationCurve.Linear), music.PlaybackMode.UntilDone)
        }
        actuators.SetSpeedMotor(1023, OutputPorts.P8)
        basic.pause(2000)
    } else {
        music.ringTone(262)
    }
}
consumo = 100 + (20 * input.temperature() + 15 * input.lightLevel())
basic.forever(function () {
    if (sensors.endstopValue(InputPorts.P2) == 1) {
        abastecer()
    } else {
        if (sensors.infraredValue(InputPorts.P1) < 200) {
            actuators.SetSpeedMotor(1023, OutputPorts.P8)
        } else {
            regar()
        }
    }
})
basic.forever(function () {
	
})
let agua_distribuída = 0
let água = 0
let consumo = 0
```
## Passo 41

Vá até a aba ``||led:Led||``, clique no bloco ``||led:plot bar graph of 0 up to 0||`` 
e insira-o no laço ``||basic:sempre||``.

```blocks
function abastecer () {
    music.stopAllSounds()
    actuators.StopMotor(OutputPorts.P8)
    while (sensors.endstopValue(InputPorts.P2) == 1) {
        music.play(music.createSoundExpression(WaveShape.Sine, 188, 584, 255, 0, 200, SoundExpressionEffect.None, InterpolationCurve.Linear), music.PlaybackMode.UntilDone)
        água += 200
    }
    actuators.SetSpeedMotor(1023, OutputPorts.P8)
}
function regar () {
    actuators.StopMotor(OutputPorts.P8)
    agua_distribuída = 0
    if (água > consumo) {
        music.stopAllSounds()
        while (agua_distribuída < consumo) {
            água += -200
            agua_distribuída += 200
            music.play(music.createSoundExpression(WaveShape.Sawtooth, 188, 584, 255, 0, 200, SoundExpressionEffect.None, InterpolationCurve.Linear), music.PlaybackMode.UntilDone)
        }
        actuators.SetSpeedMotor(1023, OutputPorts.P8)
        basic.pause(2000)
    } else {
        music.ringTone(262)
    }
}
consumo = 100 + (20 * input.temperature() + 15 * input.lightLevel())
basic.forever(function () {
    if (sensors.endstopValue(InputPorts.P2) == 1) {
        abastecer()
    } else {
        if (sensors.infraredValue(InputPorts.P1) < 200) {
            actuators.SetSpeedMotor(1023, OutputPorts.P8)
        } else {
            regar()
        }
    }
})
basic.forever(function () {
    led.plotBarGraph(
    0,
    0
    )
})
let agua_distribuída = 0
let água = 0
let consumo = 0
```

## Passo 42

Em seguida, atualize os campos do bloco ``||led:plot bar graph||``. Na categoria ``||variables:Variáveis||``
pegue a variável ``||variables:água||`` e coloque-a no primeiro campo. Finalmente, atualize o valor do segundo campo para **10000**.

```blocks
function abastecer () {
    music.stopAllSounds()
    actuators.StopMotor(OutputPorts.P8)
    while (sensors.endstopValue(InputPorts.P2) == 1) {
        music.play(music.createSoundExpression(WaveShape.Sine, 188, 584, 255, 0, 200, SoundExpressionEffect.None, InterpolationCurve.Linear), music.PlaybackMode.UntilDone)
        água += 200
    }
    actuators.SetSpeedMotor(1023, OutputPorts.P8)
}
function regar () {
    actuators.StopMotor(OutputPorts.P8)
    agua_distribuída = 0
    if (água > consumo) {
        music.stopAllSounds()
        while (agua_distribuída < consumo) {
            água += -200
            agua_distribuída += 200
            music.play(music.createSoundExpression(WaveShape.Sawtooth, 188, 584, 255, 0, 200, SoundExpressionEffect.None, InterpolationCurve.Linear), music.PlaybackMode.UntilDone)
        }
        actuators.SetSpeedMotor(1023, OutputPorts.P8)
        basic.pause(2000)
    } else {
        music.ringTone(262)
    }
}
consumo = 100 + (20 * input.temperature() + 15 * input.lightLevel())
basic.forever(function () {
    if (sensors.endstopValue(InputPorts.P2) == 1) {
        abastecer()
    } else {
        if (sensors.infraredValue(InputPorts.P1) < 200) {
            actuators.SetSpeedMotor(1023, OutputPorts.P8)
        } else {
            regar()
        }
    }
})
basic.forever(function () {
    led.plotBarGraph(
    água,
    10000
    )
})
let agua_distribuída = 0
let água = 0
let consumo = 0
```

## Passo 43

Agora seu código está pronto! Baixe-o para o micro:bit e teste-o.
Direcione o veículo para uma planta e observe a rega; após a água acabar, abasteça usando a chave de fim de curso. 
Vigie o nível de água no display do micro:bit.
```blocks
```

## Passo 44
Se necessário, confira o seu código clicando na lâmpada de dica.

```blocks
function abastecer () {
    music.stopAllSounds()
    actuators.StopMotor(OutputPorts.P8)
    while (sensors.endstopValue(InputPorts.P2) == 1) {
        music.play(music.createSoundExpression(WaveShape.Sine, 188, 584, 255, 0, 200, SoundExpressionEffect.None, InterpolationCurve.Linear), music.PlaybackMode.UntilDone)
        água += 200
    }
    actuators.SetSpeedMotor(1023, OutputPorts.P8)
}
function regar () {
    actuators.StopMotor(OutputPorts.P8)
    agua_distribuída = 0
    if (água > consumo) {
        music.stopAllSounds()
        while (agua_distribuída < consumo) {
            água += -200
            agua_distribuída += 200
            music.play(music.createSoundExpression(WaveShape.Sawtooth, 188, 584, 255, 0, 200, SoundExpressionEffect.None, InterpolationCurve.Linear), music.PlaybackMode.UntilDone)
        }
        actuators.SetSpeedMotor(1023, OutputPorts.P8)
        basic.pause(2000)
    } else {
        music.ringTone(262)
    }
}
consumo = 100 + (20 * input.temperature() + 15 * input.lightLevel())
basic.forever(function () {
    if (sensors.endstopValue(InputPorts.P2) == 1) {
        abastecer()
    } else {
        if (sensors.infraredValue(InputPorts.P1) < 200) {
            actuators.SetSpeedMotor(1023, OutputPorts.P8)
        } else {
            regar()
        }
    }
})
basic.forever(function () {
    led.plotBarGraph(
    água,
    10000
    )
})
let agua_distribuída = 0
let água = 0
let consumo = 0
```

```package
fuzzyBot=github:FuzzyMakers/pxt-fuzzyMakers
```