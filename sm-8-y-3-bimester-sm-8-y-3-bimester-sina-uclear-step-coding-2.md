### @diffs true
# Energia Nuclear

## Passo 1
Neste tutorial, vamos programar a usina nuclear em que o micro:bit atuará como 
reator e medirá o calor gerado através da luminosidade detectada. O motor 
ligará se houver luminosidade suficiente, com uma velocidade proporcional
ao nível de luz captado, representando a ativação das turbinas 
e do gerador. Além disso, precisamos garantir que a luminosidade natural não
ative as turbinas, sendo necessária uma fonte de iluminação extra, 
como lanterna, celular etc. 

## Passo 2
Adicionalmente, se a usina estiver operando, a luz da rede elétrica deve acender;
caso contrário, deve permanecer apagada. Por fim, vamos implementar um sistema
de segurança, para caso a iluminação (calor) for excessiva, um alarme sonoro 
e um aviso visual de perigo serão acionados.

## Passo 3
Para começar, verifique se a biblioteca da Smart Makers já está importada 
em seu MakeCode. Se não estiver, clique na aba **+ Extensões**, 
copie o endereço "https://github.com/FuzzyMakers/pxt-smartMakers",
cole-o no campo de pesquisa da janela que se abriu e selecione a biblioteca.

## Passo 4
Acesse a aba ``||logic:Lógica||`` e adicione o bloco ``||logic:se então senão||`` 
dentro do laço ``||basic:sempre||``.

```blocks
basic.forever(function () {
    if (true) {
    	
    } else {
    	
    }
})
```

## Passo 5
Retorne à ``||logic:Lógica||`` e utilize o bloco comparador 
``||logic:0 < 0||`` para substituir o campo **verdadeiro** do bloco 
``||logic:se então senão||``.

```blocks
basic.forever(function () {
    if (0 < 0) {
    	
    } else {
    	
    }
})
```

## Passo 6
Altere o sinal do comparador de **<** para **>** e o valor do segundo campo 
de **0** para **100**.

```blocks
basic.forever(function () {
    if (0 > 100) {
    	
    } else {
    	
    }
})

```

## Passo 7
Acesse a categoria ``||input:Entrada||`` e utilize o bloco  
``||input:nível de luz||`` para substituir o primeiro campo do comparador.

```blocks
basic.forever(function () {
    if (input.lightLevel() > 100) {
    	
    } else {
    	
    }
})
```

## Passo 8
Vá ao menu ``||actuators:Atuadores||`` e adicione um comando 
``||actuators:Motor CC, definir velocidade 0 na porta P8||`` dentro de cada
condição ``||logic:então||`` e ``||logic:senão||``. 

```blocks
basic.forever(function () {
    if (input.lightLevel() > 100) {
        actuators.SetSpeedMotor(0, OutputPorts.P8)
    } else {
        actuators.SetSpeedMotor(0, OutputPorts.P8)
    }
})
```

## Passo 9
Altere a porta de ambos esses blocos de ``||actuators:P8||`` para 
``||actuators:P16||``.

```blocks
basic.forever(function () {
    if (input.lightLevel() > 100) {
        actuators.SetSpeedMotor(0, OutputPorts.P16)
    } else {
        actuators.SetSpeedMotor(0, OutputPorts.P16)
    }
})
```

## Passo 10
Substitua o valor de velocidade **0** do comando 
``||actuators:Motor CC, definir velocidade||`` dentro do ``||logic:então||`` pelo
bloco ``||input:nível de luz||``, localizado na aba ``||input:Entrada||``. 

```blocks
basic.forever(function () {
    if (input.lightLevel() > 100) {
        actuators.SetSpeedMotor(input.lightLevel(), OutputPorts.P16)
    } else {
        actuators.SetSpeedMotor(0, OutputPorts.P16)
    }
})
```

## Passo 11
Retorne ao menu ``||actuators:Atuadores||`` e adicione um comando 
``||actuators:LED de alto brilho, definir brilho 0 na porta P8||`` dentro de cada
condição ``||logic:então||`` e ``||logic:senão||``. 

```blocks
basic.forever(function () {
    if (input.lightLevel() > 100) {
        actuators.SetSpeedMotor(input.lightLevel(), OutputPorts.P16)
        actuators.SetBrightLED(0, OutputPorts.P8)
    } else {
        actuators.SetSpeedMotor(0, OutputPorts.P16)
        actuators.SetBrightLED(0, OutputPorts.P8)
    }
})
```

## Passo 12
Altere a porta de ambos os blocos de ``||actuators:P8||`` para 
``||actuators:P12||``. Em seguida, modifique o valor do brilho desse comando 
para **1023**, apenas no bloco dentro do ``||logic:então||``.

```blocks
basic.forever(function () {
    if (input.lightLevel() > 100) {
        actuators.SetSpeedMotor(input.lightLevel(), OutputPorts.P16)
        actuators.SetBrightLED(1023, OutputPorts.P12)
    } else {
        actuators.SetSpeedMotor(0, OutputPorts.P16)
        actuators.SetBrightLED(0, OutputPorts.P12)
    }
})
```

## Passo 13
Adicione um segundo laço ``||basic:sempre||`` ao seu código. Esse bloco está
localizado na aba ``||basic:Básico||``. 

```blocks
basic.forever(function () {
    if (input.lightLevel() > 100) {
        actuators.SetSpeedMotor(input.lightLevel(), OutputPorts.P16)
        actuators.SetBrightLED(1023, OutputPorts.P12)
    } else {
        actuators.SetSpeedMotor(0, OutputPorts.P16)
        actuators.SetBrightLED(0, OutputPorts.P12)
    }
})
basic.forever(function () {
	
})
```

## Passo 14
Acesse a aba ``||logic:Lógica||`` e adicione o bloco ``||logic:se então senão||`` 
dentro desse novo laço ``||basic:sempre||``.

```blocks
basic.forever(function () {
    if (input.lightLevel() > 100) {
        actuators.SetSpeedMotor(input.lightLevel(), OutputPorts.P16)
        actuators.SetBrightLED(1023, OutputPorts.P12)
    } else {
        actuators.SetSpeedMotor(0, OutputPorts.P16)
        actuators.SetBrightLED(0, OutputPorts.P12)
    }
})
basic.forever(function () {
    if (true) {
    	
    } else {
    	
    }
})
```

## Passo 15
Retorne à ``||logic:Lógica||`` e utilize o bloco comparador 
``||logic:0 < 0||`` para substituir o campo **verdadeiro** do bloco 
``||logic:se então senão||``.

```blocks
basic.forever(function () {
    if (input.lightLevel() > 100) {
        actuators.SetSpeedMotor(input.lightLevel(), OutputPorts.P16)
        actuators.SetBrightLED(1023, OutputPorts.P12)
    } else {
        actuators.SetSpeedMotor(0, OutputPorts.P16)
        actuators.SetBrightLED(0, OutputPorts.P12)
    }
})
basic.forever(function () {
    if (0 < 0) {
    	
    } else {
    	
    }
})
```

## Passo 16
Altere o sinal do comparador de **<** para **>** e o valor do segundo campo 
de **0** para **200**.

```blocks
basic.forever(function () {
    if (input.lightLevel() > 100) {
        actuators.SetSpeedMotor(input.lightLevel(), OutputPorts.P16)
        actuators.SetBrightLED(1023, OutputPorts.P12)
    } else {
        actuators.SetSpeedMotor(0, OutputPorts.P16)
        actuators.SetBrightLED(0, OutputPorts.P12)
    }
})
basic.forever(function () {
    if (0 > 200) {
    	
    } else {
    	
    }
})
```

## Passo 17
Acesse a categoria ``||input:Entrada||`` e utilize o bloco  
``||input:nível de luz||`` para substituir o primeiro campo do comparador.

```blocks
basic.forever(function () {
    if (input.lightLevel() > 100) {
        actuators.SetSpeedMotor(input.lightLevel(), OutputPorts.P16)
        actuators.SetBrightLED(1023, OutputPorts.P12)
    } else {
        actuators.SetSpeedMotor(0, OutputPorts.P16)
        actuators.SetBrightLED(0, OutputPorts.P12)
    }
})
basic.forever(function () {
    if (input.lightLevel() > 200) {
    	
    } else {
    	
    }
})
```

## Passo 18
Acesse a categoria ``||music:Música||`` e adicione um comando 
``||music:play melody at tempo 120 (bpm) until done||`` dentro do 
``||logic:então||``.

```blocks
basic.forever(function () {
    if (input.lightLevel() > 100) {
        actuators.SetSpeedMotor(input.lightLevel(), OutputPorts.P16)
        actuators.SetBrightLED(1023, OutputPorts.P12)
    } else {
        actuators.SetSpeedMotor(0, OutputPorts.P16)
        actuators.SetBrightLED(0, OutputPorts.P12)
    }
})
basic.forever(function () {
    if (input.lightLevel() > 200) {
        music.play(music.stringPlayable("- - - - - - - - ", 120), music.PlaybackMode.UntilDone)
    } else {
    	
    }
})
```

## Passo 19
Altere o tempo desse bloco de **120 bpm** para **400 bpm** e clique na seta 
para alterar o modo de reprodução de **until done** para **looping in background**.

```blocks
basic.forever(function () {
    if (input.lightLevel() > 100) {
        actuators.SetSpeedMotor(input.lightLevel(), OutputPorts.P16)
        actuators.SetBrightLED(1023, OutputPorts.P12)
    } else {
        actuators.SetSpeedMotor(0, OutputPorts.P16)
        actuators.SetBrightLED(0, OutputPorts.P12)
    }
})
basic.forever(function () {
    if (input.lightLevel() > 200) {
        music.play(music.stringPlayable("- - - - - - - - ", 400), music.PlaybackMode.LoopingInBackground)
    } else {
    	
    }
})
```

## Passo 20
Agora, vamos definir qual melodia deve tocar, ou seja, o som do alarme. 
Clique nos retângulos 
do bloco ``||music:play melody||`` para abrir o quadro do editor 
de melodias. Esse editor é dividido em colunas, que são tocadas em sequência. 
Cada linha dessas colunas representa uma nota, que pode ser selecionada ao 
clicar sobre seu quadrado correspondente.
A melodia que devemos programar segue o seguinte padrão:

*(clique na lâmpada de dica para facilitar a visualização)*
- 1ª coluna: 1ª linha;
- 2ª coluna: 1ª linha;
- 3ª coluna: 4ª linha;
- 4ª coluna: 4ª linha; 
- 5ª coluna: 1ª linha; 
- 6ª coluna: 1ª linha; 
- 7ª coluna: 4ª linha; 
- 8ª coluna: 4ª linha; 

```blocks
basic.forever(function () {
    if (input.lightLevel() > 100) {
        actuators.SetSpeedMotor(input.lightLevel(), OutputPorts.P16)
        actuators.SetBrightLED(1023, OutputPorts.P12)
    } else {
        actuators.SetSpeedMotor(0, OutputPorts.P16)
        actuators.SetBrightLED(0, OutputPorts.P12)
    }
})
basic.forever(function () {
    if (input.lightLevel() > 200) {
        music.play(music.stringPlayable("C5 C5 G G C5 C5 G G ", 400), music.PlaybackMode.LoopingInBackground)
    } else {
    	
    }
})
```

## Passo 21
Acesse a categoria ``||basic:Básico||`` e adicione um comando 
``||basic:mostrar ícone||`` dentro do ``||logic:então||``, após o comando
musical. Clique na seta desse
bloco para alterar o símbolo de um coração para um **X**.

```blocks
basic.forever(function () {
    if (input.lightLevel() > 100) {
        actuators.SetSpeedMotor(input.lightLevel(), OutputPorts.P16)
        actuators.SetBrightLED(1023, OutputPorts.P12)
    } else {
        actuators.SetSpeedMotor(0, OutputPorts.P16)
        actuators.SetBrightLED(0, OutputPorts.P12)
    }
})
basic.forever(function () {
    if (input.lightLevel() > 200) {
        music.play(music.stringPlayable("C5 C5 G G C5 C5 G G ", 400), music.PlaybackMode.LoopingInBackground)
        basic.showIcon(IconNames.Heart)
    } else {
    	
    }
})
```

## Passo 22
Prosseguindo ao ``||logic:senão||``, retorne à categoria ``||music:Música||`` 
e insira o bloco ``||music:stop all sounds||`` dentro do ``||logic:senão||``.

```blocks
basic.forever(function () {
    if (input.lightLevel() > 100) {
        actuators.SetSpeedMotor(input.lightLevel(), OutputPorts.P16)
        actuators.SetBrightLED(1023, OutputPorts.P12)
    } else {
        actuators.SetSpeedMotor(0, OutputPorts.P16)
        actuators.SetBrightLED(0, OutputPorts.P12)
    }
})
basic.forever(function () {
    if (input.lightLevel() > 200) {
        music.play(music.stringPlayable("C5 C5 G G C5 C5 G G ", 400), music.PlaybackMode.LoopingInBackground)
        basic.showIcon(IconNames.No)
    } else {
        music.stopAllSounds()
    }
})
```

## Passo 23
Clique no menu ``||leds:Led||`` e adicione o bloco 
``||leds:plot bar graph of 0 up to 0||`` dentro do ``||logic:senão||``.

```blocks
basic.forever(function () {
    if (input.lightLevel() > 100) {
        actuators.SetSpeedMotor(input.lightLevel(), OutputPorts.P16)
        actuators.SetBrightLED(1023, OutputPorts.P12)
    } else {
        actuators.SetSpeedMotor(0, OutputPorts.P16)
        actuators.SetBrightLED(0, OutputPorts.P12)
    }
})
basic.forever(function () {
    if (input.lightLevel() > 200) {
        music.play(music.stringPlayable("C5 C5 G G C5 C5 G G ", 400), music.PlaybackMode.LoopingInBackground)
        basic.showIcon(IconNames.No)
    } else {
        music.stopAllSounds()
        led.plotBarGraph(
        0,
        0
        )
    }
})
```

## Passo 24
Acesse a categoria ``||input:Entrada||`` e utilize o bloco  
``||input:nível de luz||`` para substituir o primeiro campo de valor **0** desse
comando ``||leds:plot bar graph||``.

```blocks
basic.forever(function () {
    if (input.lightLevel() > 100) {
        actuators.SetSpeedMotor(input.lightLevel(), OutputPorts.P16)
        actuators.SetBrightLED(1023, OutputPorts.P12)
    } else {
        actuators.SetSpeedMotor(0, OutputPorts.P16)
        actuators.SetBrightLED(0, OutputPorts.P12)
    }
})
basic.forever(function () {
    if (input.lightLevel() > 200) {
        music.play(music.stringPlayable("C5 C5 G G C5 C5 G G ", 400), music.PlaybackMode.LoopingInBackground)
        basic.showIcon(IconNames.No)
    } else {
        music.stopAllSounds()
        led.plotBarGraph(
        input.lightLevel(),
        0
        )
    }
})
```

## Passo 25
Altere o segundo campo com o valor **0** desse bloco para **255**.

```blocks
basic.forever(function () {
    if (input.lightLevel() > 100) {
        actuators.SetSpeedMotor(input.lightLevel(), OutputPorts.P16)
        actuators.SetBrightLED(1023, OutputPorts.P12)
    } else {
        actuators.SetSpeedMotor(0, OutputPorts.P16)
        actuators.SetBrightLED(0, OutputPorts.P12)
    }
})
basic.forever(function () {
    if (input.lightLevel() > 200) {
        music.play(music.stringPlayable("C5 C5 G G C5 C5 G G ", 400), music.PlaybackMode.LoopingInBackground)
        basic.showIcon(IconNames.No)
    } else {
        music.stopAllSounds()
        led.plotBarGraph(
        input.lightLevel(),
        255
        )
    }
})
```

## Passo 26
Agora, seu código está pronto! Baixe-o para o micro:bit e aproxime uma fonte de 
luz ao micro:bit, como um celular ou uma lanterna. Observe se a rede elétrica e 
o motor serão acionados, além do alarme de emergência, caso a luminosidade 
(calor) seja muito alta.

```blocks
```

## Passo 27
Se necessário, confira o seu código clicando na lâmpada de dica.

```blocks
basic.forever(function () {
    if (input.lightLevel() > 100) {
        actuators.SetSpeedMotor(input.lightLevel(), OutputPorts.P16)
        actuators.SetBrightLED(1023, OutputPorts.P12)
    } else {
        actuators.SetSpeedMotor(0, OutputPorts.P16)
        actuators.SetBrightLED(0, OutputPorts.P12)
    }
})
basic.forever(function () {
    if (input.lightLevel() > 200) {
        music.play(music.stringPlayable("C5 C5 G G C5 C5 G G ", 400), music.PlaybackMode.LoopingInBackground)
        basic.showIcon(IconNames.No)
    } else {
        music.stopAllSounds()
        led.plotBarGraph(
        input.lightLevel(),
        255
        )
    }
})
```

```package
fuzzyBot=github:FuzzyMakers/pxt-fuzzyMakers
```