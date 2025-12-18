### @diffs true
# Gramofone

## Passo 1
Neste tutorial, vamos programar o protótipo do gramofone para reproduzir músicas.
A chave fim de curso deve fazer o motor CC girar o disco. Enquanto isso, 
o sensor infrevermelho é usado para identificar se a agulha está sobre o disco.
Se a agulha estiver sobre o disco e o ele girar, a música deve começar a tocar.

## Passo 2
Para começar, verifique se a biblioteca da Smart Makers já está importada 
em seu MakeCode. Se não estiver, clique na aba **+ Extensões**, 
copie o endereço "https://github.com/FuzzyMakers/pxt-smartMakers",
cole-o no campo de pesquisa da janela que se abriu e selecione a biblioteca.

## Passo 3
Acesse a aba ``||logic:Lógica||`` e adicione o bloco ``||logic:se então||`` 
dentro do bloco ``||basic:sempre||``.

```blocks
basic.forever(function () {
    if (true) {
    	
    }
})
```

## Passo 4
Retorne à ``||logic:Lógica||`` e utilize o bloco comparador 
``||logic:0 = 0||`` para substituir o campo **verdadeiro** do bloco 
``||logic:se então||``.

```blocks
basic.forever(function () {
    if (0 == 0) {
    	
    }
})
```

## Passo 5
Acesse o menu ``||sensors:Sensores||`` e selecione o bloco 
``||sensors:Valor da chave fim de curso na porta P2||`` para substituir o 
valor **0** do primeiro campo do comparador. 
Antes de prosseguir, altere a porta de **P2** para **P1** e o valor do segundo
campo do comparador de **0** para **1**.

```blocks
basic.forever(function () {
    if (sensors.endstopValue(InputPorts.P1) == 1) {
    	
    }
})
```

## Passo 6
Agora, dentro do ``||logic:então||``, adicione o comando 
``||actuators:Motor CC, definir velocidade 0 na porta P8||``, localizado na 
aba ``||actuators:Atuadores||``.

```blocks
basic.forever(function () {
    if (sensors.endstopValue(InputPorts.P1) == 1) {
        actuators.SetSpeedMotor(0, OutputPorts.P8)
    }
})
```

## Passo 7
Altere o valor de velocidade de **0** para **100** e a porta de 
``||actuators:P8||`` para ``||actuators:P16||``.

```blocks
basic.forever(function () {
    if (sensors.endstopValue(InputPorts.P1) == 1) {
        actuators.SetSpeedMotor(100, OutputPorts.P16)
    }
})
```

## Passo 8
Acesse o menu ``||variables:Variáveis||`` e clique em 
**"Fazer uma variável..."**. Crie uma variável chamada 
``||variables:girando||`` e, depois de criá-la, adicione o bloco 
``||variables:definir girando para 0||`` dentro do ``||logic:então||``.

```blocks
let girando = 0
basic.forever(function () {
    if (sensors.endstopValue(InputPorts.P1) == 1) {
        actuators.SetSpeedMotor(100, OutputPorts.P16)
        girando = 0
    }
})
```

## Passo 9
Altere o valor de definição de **0** para **1**. Em seguida, adicione um bloco 
``||basic:pausa (ms) 100||`` dentro do ``||logic:então||``. Antes de prosseguir, 
altere a duração dessa ``||basic:pausa||`` de **100 ms** para **30000 ms** 
(30 segundos). 

```blocks
let girando = 0
basic.forever(function () {
    if (sensors.endstopValue(InputPorts.P1) == 1) {
        actuators.SetSpeedMotor(100, OutputPorts.P16)
        girando = 1
        basic.pause(30000)
    }
})
```

## Passo 10
Feito isso, adicione outro bloco ``||variables:definir girando para 0||``
após a ``||basic:pausa||``.

```blocks
let girando = 0
basic.forever(function () {
    if (sensors.endstopValue(InputPorts.P1) == 1) {
        actuators.SetSpeedMotor(100, OutputPorts.P16)
        girando = 1
        basic.pause(30000)
        girando = 0
    }
})
```

## Passo 11
Retorne à categoria ``||actuators:Atuadores||`` e adicione o bloco 
``||actuators:Motor CC, parar motor na porta P8||``. Altere a porta de 
``||actuators:P8||`` para ``||actuators:P16||``. 

```blocks
let girando = 0
basic.forever(function () {
    if (sensors.endstopValue(InputPorts.P1) == 1) {
        actuators.SetSpeedMotor(100, OutputPorts.P16)
        girando = 1
        basic.pause(30000)
        girando = 0
        actuators.StopMotor(OutputPorts.P16)
    }
})
```

## Passo 12
Acesse a aba ``||basic:Básico||`` e adicione um segundo laço ``||basic:sempre||``
ao seu código.

```blocks
let girando = 0
basic.forever(function () {
    if (sensors.endstopValue(InputPorts.P1) == 1) {
        actuators.SetSpeedMotor(100, OutputPorts.P16)
        girando = 1
        basic.pause(30000)
        girando = 0
        actuators.StopMotor(OutputPorts.P16)
    }
})
basic.forever(function () {
	
})
```

## Passo 13
Acesse a aba ``||logic:Lógica||`` e adicione o bloco ``||logic:se então||`` 
dentro desse novo laço ``||basic:sempre||``.

```blocks
let girando = 0
basic.forever(function () {
    if (sensors.endstopValue(InputPorts.P1) == 1) {
        actuators.SetSpeedMotor(100, OutputPorts.P16)
        girando = 1
        basic.pause(30000)
        girando = 0
        actuators.StopMotor(OutputPorts.P16)
    }
})
basic.forever(function () {
    if (true) {
    	
    }
})
```

## Passo 14
Retorne à ``||logic:Lógica||`` e utilize o bloco comparador 
``||logic:0 < 0||`` para substituir o campo **verdadeiro** do bloco 
``||logic:se então||``.

```blocks
let girando = 0
basic.forever(function () {
    if (sensors.endstopValue(InputPorts.P1) == 1) {
        actuators.SetSpeedMotor(100, OutputPorts.P16)
        girando = 1
        basic.pause(30000)
        girando = 0
        actuators.StopMotor(OutputPorts.P16)
    }
})
basic.forever(function () {
    if (0 < 0) {
    	
    }
})
```

## Passo 15
Acesse o menu ``||sensors:Sensores||`` e selecione o bloco 
``||sensors:Valor do sensor infravermelho na porta P2||`` para substituir o valor **0**
do primeiro campo do comparador. Antes de prosseguir, altere a o valor do 
segundo campo do comparador de **0** para **300**.

```blocks
let girando = 0
basic.forever(function () {
    if (sensors.endstopValue(InputPorts.P1) == 1) {
        actuators.SetSpeedMotor(100, OutputPorts.P16)
        girando = 1
        basic.pause(30000)
        girando = 0
        actuators.StopMotor(OutputPorts.P16)
    }
})
basic.forever(function () {
    if (sensors.infraredValue(InputPorts.P2) < 300) {
    	
    }
})
```

## Passo 16
Acesse a categoria ``||music:Música||`` e insira o bloco 
``||music:stop all sounds||`` dentro do ``||logic:então||``.

```blocks
let girando = 0
basic.forever(function () {
    if (sensors.endstopValue(InputPorts.P1) == 1) {
        actuators.SetSpeedMotor(100, OutputPorts.P16)
        girando = 1
        basic.pause(30000)
        girando = 0
        actuators.StopMotor(OutputPorts.P16)
    }
})
basic.forever(function () {
    if (sensors.infraredValue(InputPorts.P2) < 300) {
        music.stopAllSounds()
    }
})
```

## Passo 17
Retorne à aba ``||basic:Básico||`` e adicione um terceiro laço ``||basic:sempre||``
ao seu código.

```blocks
let girando = 0
basic.forever(function () {
    if (sensors.endstopValue(InputPorts.P1) == 1) {
        actuators.SetSpeedMotor(100, OutputPorts.P16)
        girando = 1
        basic.pause(30000)
        girando = 0
        actuators.StopMotor(OutputPorts.P16)
    }
})
basic.forever(function () {
    if (sensors.infraredValue(InputPorts.P2) < 300) {
        music.stopAllSounds()
    }
})
basic.forever(function () {
	
})
```

## Passo 18
Acesse a aba ``||logic:Lógica||`` e adicione o bloco ``||logic:se então||`` 
dentro desse novo laço ``||basic:sempre||``.

```blocks
let girando = 0
basic.forever(function () {
    if (sensors.endstopValue(InputPorts.P1) == 1) {
        actuators.SetSpeedMotor(100, OutputPorts.P16)
        girando = 1
        basic.pause(30000)
        girando = 0
        actuators.StopMotor(OutputPorts.P16)
    }
})
basic.forever(function () {
    if (sensors.infraredValue(InputPorts.P2) < 300) {
        music.stopAllSounds()
    }
})
basic.forever(function () {
    if (true) {
    	
    }
})
```

## Passo 19
Retorne à ``||logic:Lógica||`` e utilize o operador booleano 
``||logic:E||`` para substituir o campo **verdadeiro** do bloco 
``||logic:se então||``.

```blocks
let girando = 0
basic.forever(function () {
    if (sensors.endstopValue(InputPorts.P1) == 1) {
        actuators.SetSpeedMotor(100, OutputPorts.P16)
        girando = 1
        basic.pause(30000)
        girando = 0
        actuators.StopMotor(OutputPorts.P16)
    }
})
basic.forever(function () {
    if (sensors.infraredValue(InputPorts.P2) < 300) {
        music.stopAllSounds()
    }
})
basic.forever(function () {
    if (false && false) {
    	
    }
})
```

## Passo 20
Retorne à ``||logic:Lógica||`` e adicione blocos comparadores 
``||logic:0 < 0||`` em cada lado do operador Booleano ``||logic:E||``.
Certifique-se de ter um total de quatro campos com o valor **0** nesse 
bloco ``||logic:se então||``.

```blocks
let girando = 0
basic.forever(function () {
    if (sensors.endstopValue(InputPorts.P1) == 1) {
        actuators.SetSpeedMotor(100, OutputPorts.P16)
        girando = 1
        basic.pause(30000)
        girando = 0
        actuators.StopMotor(OutputPorts.P16)
    }
})
basic.forever(function () {
    if (sensors.infraredValue(InputPorts.P2) < 300) {
        music.stopAllSounds()
    }
})
basic.forever(function () {
    if (0 < 0 && 0 < 0) {
    	
    }
})
```

## Passo 21
Acesse o menu ``||sensors:Sensores||`` e selecione o bloco 
``||sensors:Valor do sensor infravermelho na porta P2||`` para substituir o 
valor **0** do primeiro campo do primeiro comparador.

```blocks
let girando = 0
basic.forever(function () {
    if (sensors.endstopValue(InputPorts.P1) == 1) {
        actuators.SetSpeedMotor(100, OutputPorts.P16)
        girando = 1
        basic.pause(30000)
        girando = 0
        actuators.StopMotor(OutputPorts.P16)
    }
})
basic.forever(function () {
    if (sensors.infraredValue(InputPorts.P2) < 300) {
        music.stopAllSounds()
    }
})
basic.forever(function () {
    if (sensors.infraredValue(InputPorts.P2) < 0 && 0 < 0) {
    	
    }
})
```

## Passo 22
Altere o sinal do primeiro comparador de **<** para **>=**. Em seguida, modifique
o segundo valor desse comparador de **0** para **300**.

```blocks
let girando = 0
basic.forever(function () {
    if (sensors.endstopValue(InputPorts.P1) == 1) {
        actuators.SetSpeedMotor(100, OutputPorts.P16)
        girando = 1
        basic.pause(30000)
        girando = 0
        actuators.StopMotor(OutputPorts.P16)
    }
})
basic.forever(function () {
    if (sensors.infraredValue(InputPorts.P2) < 300) {
        music.stopAllSounds()
    }
})
basic.forever(function () {
    if (sensors.infraredValue(InputPorts.P2) >= 300 && 0 < 0) {
    	
    }
})
```

## Passo 23
Acesse a categoria ``||variables:Variáveis||`` e utilize o bloco da variável
``||variables:girando||`` para substituir o primeiro campo do segundo comparador.

```blocks
let girando = 0
basic.forever(function () {
    if (sensors.endstopValue(InputPorts.P1) == 1) {
        actuators.SetSpeedMotor(100, OutputPorts.P16)
        girando = 1
        basic.pause(30000)
        girando = 0
        actuators.StopMotor(OutputPorts.P16)
    }
})
basic.forever(function () {
    if (sensors.infraredValue(InputPorts.P2) < 300) {
        music.stopAllSounds()
    }
})
basic.forever(function () {
    if (sensors.infraredValue(InputPorts.P2) >= 300 && girando < 0) {
    	
    }
})
```

## Passo 24
Clique na seta desse segundo comparador para alterar o sinal de **<** para **=**.
Em seguida, altere o segundo campo desse comparador de **0** para **1**.

```blocks
let girando = 0
basic.forever(function () {
    if (sensors.endstopValue(InputPorts.P1) == 1) {
        actuators.SetSpeedMotor(100, OutputPorts.P16)
        girando = 1
        basic.pause(30000)
        girando = 0
        actuators.StopMotor(OutputPorts.P16)
    }
})
basic.forever(function () {
    if (sensors.infraredValue(InputPorts.P2) < 300) {
        music.stopAllSounds()
    }
})
basic.forever(function () {
    if (sensors.infraredValue(InputPorts.P2) >= 300 && girando == 1) {
    	
    }
})
```

## Passo 25
Dentro do ``||logic:então||``, adicione um bloco 
``||music:play melody at tempo 120 bpm until done||``, localizado na aba 
``||music:Música||``.

```blocks
let girando = 0
basic.forever(function () {
    if (sensors.endstopValue(InputPorts.P1) == 1) {
        actuators.SetSpeedMotor(100, OutputPorts.P16)
        girando = 1
        basic.pause(30000)
        girando = 0
        actuators.StopMotor(OutputPorts.P16)
    }
})
basic.forever(function () {
    if (sensors.infraredValue(InputPorts.P2) < 300) {
        music.stopAllSounds()
    }
})
basic.forever(function () {
    if (sensors.infraredValue(InputPorts.P2) >= 300 && girando == 1) {
        music.play(music.stringPlayable("- - - - - - - - ", 120), music.PlaybackMode.UntilDone)
    }
})
```

## Passo 26
Clique nos retângulos desse bloco para abrir o quadro do editor de melodias.
Esse editor é dividido em colunas, que são tocadas em sequência. Cada linha dessas
colunas representa uma nota, que podem ser selecionadas ao clicar sobre seu quadrado.
A melodia que devemos programar segue o seguinte padrão:
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
let girando = 0
basic.forever(function () {
    if (sensors.endstopValue(InputPorts.P1) == 1) {
        actuators.SetSpeedMotor(100, OutputPorts.P16)
        girando = 1
        basic.pause(30000)
        girando = 0
        actuators.StopMotor(OutputPorts.P16)
    }
})
basic.forever(function () {
    if (sensors.infraredValue(InputPorts.P2) < 300) {
        music.stopAllSounds()
    }
})
basic.forever(function () {
    if (sensors.infraredValue(InputPorts.P2) >= 300 && girando == 1) {
        music.play(music.stringPlayable("E B C5 A B G A F ", 120), music.PlaybackMode.UntilDone)
    }
})
```

## Passo 27
Agora, seu código está pronto! Baixe-o para o micro:bit, coloque a agulha sobre
o disco e utilize a chave fim de curso para girar o disco e escutar a música.
Experimente criar diferentes melodias para o seu gramofone!

```blocks
```

## Passo 28
Se necessário, confira o seu código clicando na lâmpada de dica.

```blocks
let girando = 0
basic.forever(function () {
    if (sensors.endstopValue(InputPorts.P1) == 1) {
        actuators.SetSpeedMotor(100, OutputPorts.P16)
        girando = 1
        basic.pause(30000)
        girando = 0
        actuators.StopMotor(OutputPorts.P16)
    }
})
basic.forever(function () {
    if (sensors.infraredValue(InputPorts.P2) < 300) {
        music.stopAllSounds()
    }
})
basic.forever(function () {
    if (sensors.infraredValue(InputPorts.P2) >= 300 && girando == 1) {
        music.play(music.stringPlayable("E B C5 A B G A F ", 120), music.PlaybackMode.UntilDone)
    }
})
```

```package
fuzzyBot=github:FuzzyMakers/pxt-fuzzyMakers
```