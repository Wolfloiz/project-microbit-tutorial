### @diffs true
# Cintilômetro

## Passo 1
Nessa atividade, vamos programar uma réplica lúdica de um cintilômetro para detectar ondas eletromagnéticas. 
Ele funciona em dois modos: luz e radiação. 
No modo luz, vamos obter e exibir dados de luminosidade usando o sensor de luz do micro:bit. 
No modo radiação, vamos medir a intensidade da radiação através da reflexão de ondas infravermelhas pelo 
respectivo sensor posicionado na extremidade da estrutura do medidor.

## Passo 2
Para começar, verifique se a biblioteca da Smart Makers já está importada em seu MakeCode.
Se não estiver, clique na aba **+ Extensões**, copie o endereço "https://github.com/FuzzyMakers/pxt-smartMakers",
cole-o no campo de pesquisa da janela que se abriu e selecione a biblioteca.

## Passo 3
Acesse o menu ``||logic:Lógica||`` e adicione um bloco ``||logic:se então||`` dentro do laço
``||basic:sempre||``.

```blocks
basic.forever(function () {
    if (true) {
    	
    }
})
```

## Passo 4
Retorne à categoria ``||logic:Lógica||`` e adicione um bloco comparador ``||logic:0 = 0||`` para 
substituir o campo **verdadeiro** do bloco ``||logic:se então||``.

```blocks
basic.forever(function () {
    if (0 == 0) {
    	
    }
})
```

## Passo 5
Vá ao menu ``||sensors:Sensores||`` e altere o primeiro campo do comparador de **0** para ``||sensors:Valor do Botão na porta P2||``.
Clique na seta desse bloco e troque a porta de **P2** para **P1**. Em seguida, modifique o valor do
segundo campo do comparador de **1** para **0**.

```blocks
basic.forever(function () {
    if (sensors.buttonValue(InputPorts.P1) == 1) {
    	
    }
})
```

## Passo 6
Prosseguindo para dentro do ``||logic:então||``, insira o comando ``||music:stop all sounds||`` presente na categoria
``||music:Música||``.   

```blocks
basic.forever(function () {
    if (sensors.buttonValue(InputPorts.P1) == 1) {
        music.stopAllSounds()
    }
})
```

## Passo 7
Abaixo desse bloco, adicione o comando ``||actuators:LED de alto brilho, brilho 0 na porta P8||`` 
localizado no menu de ``||actuators:Atuadores||``.

```blocks
basic.forever(function () {
    if (sensors.buttonValue(InputPorts.P1) == 1) {
        music.stopAllSounds()
        actuators.SetBrightLED(0, OutputPorts.P8)
    }
})
```

## Passo 8
Altere o valor de brilho de **0** para **1023** e a porta de **P8** para **P12**.

```blocks
basic.forever(function () {
    if (sensors.buttonValue(InputPorts.P1) == 1) {
        music.stopAllSounds()
        actuators.SetBrightLED(1023, OutputPorts.P12)
    }
})
```

## Passo 9
Em seguida, acesse a aba ``||led:Led||`` e adicione o bloco ``||led:plot bar graph of 0 up to 0||`` ainda dentro 
do ``||logic:então||``. 

```blocks
basic.forever(function () {
    if (sensors.buttonValue(InputPorts.P1) == 1) {
        music.stopAllSounds()
        actuators.SetBrightLED(1023, OutputPorts.P12)
        led.plotBarGraph(
        0,
        0
        )
    }
})
```

## Passo 10
Modifique o valor do primeiro campo desse bloco de **0** para ``||input:nível de luz||``
localizado na aba ``||input:Entrada||``. Em seguida, altere o segundo campo de **0** para **100**.

```blocks
basic.forever(function () {
    if (sensors.buttonValue(InputPorts.P1) == 1) {
        music.stopAllSounds()
        actuators.SetBrightLED(1023, OutputPorts.P12)
        led.plotBarGraph(
        input.lightLevel(),
        100
        )
    }
})
```

## Passo 11
Acesse a aba ``||basic:Básico||`` e adicione um segundo laço ``||basic:sempre||``
ao seu código.

```blocks
basic.forever(function () {
    if (sensors.buttonValue(InputPorts.P1) == 1) {
        music.stopAllSounds()
        actuators.SetBrightLED(1023, OutputPorts.P12)
        led.plotBarGraph(
        input.lightLevel(),
        100
        )
    }
})
basic.forever(function () {
	
})
```

## Passo 12
Adicione um bloco ``||logic:se então||`` com o comparador igual ao do outro laço ``||basic:sempre||``.
Ou seja, com o bloco ``||sensors:Valor do Botão na porta P1||`` igual a **1**.

```blocks
basic.forever(function () {
    if (sensors.buttonValue(InputPorts.P1) == 1) {
        music.stopAllSounds()
        actuators.SetBrightLED(1023, OutputPorts.P12)
        led.plotBarGraph(
        input.lightLevel(),
        100
        )
    }
})
basic.forever(function () {
    if (sensors.buttonValue(InputPorts.P1) == 1) {
    	
    }
})
```

## Passo 13
Certifique-se de que a porta do ``||sensors:Botão||`` seja a **P1**. Em seguida, altere o segundo 
valor de **1** para **0**.

```blocks
basic.forever(function () {
    if (sensors.buttonValue(InputPorts.P1) == 1) {
        music.stopAllSounds()
        actuators.SetBrightLED(1023, OutputPorts.P12)
        led.plotBarGraph(
        input.lightLevel(),
        100
        )
    }
})
basic.forever(function () {
    if (sensors.buttonValue(InputPorts.P1) == 0) {
    	
    }
})
```

## Passo 14
Dentro do ``||logic:então||`` desse bloco, também adicione o comando de controle 
do LED de alto brilho com a porta **P12**: ``||actuators:LED de alto brilho, brilho 0 na porta P12||``.
Certifique-se de modificar o brilho de **1023** para **0**.

```blocks
basic.forever(function () {
    if (sensors.buttonValue(InputPorts.P1) == 1) {
        music.stopAllSounds()
        actuators.SetBrightLED(1023, OutputPorts.P12)
        led.plotBarGraph(
        input.lightLevel(),
        100
        )
    }
})
basic.forever(function () {
    if (sensors.buttonValue(InputPorts.P1) == 0) {
        actuators.SetBrightLED(0, OutputPorts.P12)
    }
})
```

## Passo 15
Também teremos o bloco ``||led:plot bar graph of 0 up to 0||``, mas com o bloco 
``||sensors:Valor do sensor infravermelho na porta P2||`` no lugar do ``||input:nível de luz||``.
O segundo campo pode ser mantido com o valor **100**.

```blocks
basic.forever(function () {
    if (sensors.buttonValue(InputPorts.P1) == 1) {
        music.stopAllSounds()
        actuators.SetBrightLED(1023, OutputPorts.P12)
        led.plotBarGraph(
        input.lightLevel(),
        100
        )
    }
})
basic.forever(function () {
    if (sensors.buttonValue(InputPorts.P1) == 0) {
        actuators.SetBrightLED(0, OutputPorts.P12)
        led.plotBarGraph(
        sensors.infraredValue(InputPorts.P2),
        100
        )
    }
})
```

## Passo 16
Retorne ao menu ``||logic:Lógica||``, e adicione um bloco ``||logic:se então senão||`` ainda dentro do antigo ``||logic:então||``,
imediatamente abaixo do bloco ``||led:plot bar graph||``.

```blocks
basic.forever(function () {
    if (sensors.buttonValue(InputPorts.P1) == 1) {
        music.stopAllSounds()
        actuators.SetBrightLED(1023, OutputPorts.P12)
        led.plotBarGraph(
        input.lightLevel(),
        100
        )
    }
})
basic.forever(function () {
    if (sensors.buttonValue(InputPorts.P1) == 0) {
        actuators.SetBrightLED(0, OutputPorts.P12)
        led.plotBarGraph(
        sensors.infraredValue(InputPorts.P2),
        100
        )
        if (true) {
        	
        } else {
        	
        }
    }
})
```

## Passo 17
Em seguida, adicione um bloco comparador ``||logic:0 < 0||``, porém, altere o sinal
de **<** para **>**.

```blocks
basic.forever(function () {
    if (sensors.buttonValue(InputPorts.P1) == 1) {
        music.stopAllSounds()
        actuators.SetBrightLED(1023, OutputPorts.P12)
        led.plotBarGraph(
        input.lightLevel(),
        100
        )
    }
})
basic.forever(function () {
    if (sensors.buttonValue(InputPorts.P1) == 0) {
        actuators.SetBrightLED(0, OutputPorts.P12)
        led.plotBarGraph(
        sensors.infraredValue(InputPorts.P2),
        100
        )
        if (0 > 0) {
        	
        } else {
        	
        }
    }
})
```

## Passo 18
O primeiro campo desse comparador será o bloco ``||sensors:Valor do sensor infravermelho na porta P2||``.
Em seguida, edite o segundo campo de **0** para **50**.

```blocks
basic.forever(function () {
    if (sensors.buttonValue(InputPorts.P1) == 1) {
        music.stopAllSounds()
        actuators.SetBrightLED(1023, OutputPorts.P12)
        led.plotBarGraph(
        input.lightLevel(),
        100
        )
    }
})
basic.forever(function () {
    if (sensors.buttonValue(InputPorts.P1) == 0) {
        actuators.SetBrightLED(0, OutputPorts.P12)
        led.plotBarGraph(
        sensors.infraredValue(InputPorts.P2),
        100
        )
        if (sensors.infraredValue(InputPorts.P2) > 50) {
        	
        } else {
        	
        }
    }
})
```

## Passo 19
Agora, dentro do ``||logic:então||``, adicione o bloco ``||music:toque (Hz) C Médio||``, 
encontrado na categoria ``||music:Música||``.

```blocks
basic.forever(function () {
    if (sensors.buttonValue(InputPorts.P1) == 1) {
        music.stopAllSounds()
        actuators.SetBrightLED(1023, OutputPorts.P12)
        led.plotBarGraph(
        input.lightLevel(),
        100
        )
    }
})
basic.forever(function () {
    if (sensors.buttonValue(InputPorts.P1) == 0) {
        actuators.SetBrightLED(0, OutputPorts.P12)
        led.plotBarGraph(
        sensors.infraredValue(InputPorts.P2),
        100
        )
        if (sensors.infraredValue(InputPorts.P2) > 50) {
            music.ringTone(262)
        } else {
        	
        }
    }
})
```

## Passo 20
Altere a frequência desse bloco de ``||music:C Médio||`` para o próprio 
``||sensors:Valor do sensor infravermelho na porta P2||``.

```blocks
basic.forever(function () {
    if (sensors.buttonValue(InputPorts.P1) == 1) {
        music.stopAllSounds()
        actuators.SetBrightLED(1023, OutputPorts.P12)
        led.plotBarGraph(
        input.lightLevel(),
        100
        )
    }
})
basic.forever(function () {
    if (sensors.buttonValue(InputPorts.P1) == 0) {
        actuators.SetBrightLED(0, OutputPorts.P12)
        led.plotBarGraph(
        sensors.infraredValue(InputPorts.P2),
        100
        )
        if (sensors.infraredValue(InputPorts.P2) > 50) {
            music.ringTone(sensors.infraredValue(InputPorts.P2))
        } else {
        	
        }
    }
})
```

## Passo 21
Por fim, adicione o comando ``||music:stop all sounds||`` dentro do ``||logic:senão||``.
Ele também está localizado no menu ``||music:Música||``.

```blocks
basic.forever(function () {
    if (sensors.buttonValue(InputPorts.P1) == 1) {
        music.stopAllSounds()
        actuators.SetBrightLED(1023, OutputPorts.P12)
        led.plotBarGraph(
        input.lightLevel(),
        100
        )
    }
})
basic.forever(function () {
    if (sensors.buttonValue(InputPorts.P1) == 0) {
        actuators.SetBrightLED(0, OutputPorts.P12)
        led.plotBarGraph(
        sensors.infraredValue(InputPorts.P2),
        100
        )
        if (sensors.infraredValue(InputPorts.P2) > 50) {
            music.ringTone(sensors.infraredValue(InputPorts.P2))
        } else {
            music.stopAllSounds()
        }
    }
})
```

## Passo 22

Agora seu código está pronto! Baixe-o para o micro:bit e teste-o. 
O botão é usado para alterar entre o modo luz e radiação. Para variar a luz, aproxime 
fontes luminosas dos LEDs do micro:bit e, no modo radiação, aproxime objetos claros
do sensor infravermelho. Verifique as medições nos gráficos exibidos nos LEDs do micro:bit.

```blocks
```

## Passo 23
Se necessário, confira o seu código clicando na lâmpada de dica.

```blocks
basic.forever(function () {
    if (sensors.buttonValue(InputPorts.P1) == 1) {
        music.stopAllSounds()
        actuators.SetBrightLED(1023, OutputPorts.P12)
        led.plotBarGraph(
        input.lightLevel(),
        100
        )
    }
})
basic.forever(function () {
    if (sensors.buttonValue(InputPorts.P1) == 0) {
        actuators.SetBrightLED(0, OutputPorts.P12)
        led.plotBarGraph(
        sensors.infraredValue(InputPorts.P2),
        100
        )
        if (sensors.infraredValue(InputPorts.P2) > 50) {
            music.ringTone(sensors.infraredValue(InputPorts.P2))
        } else {
            music.stopAllSounds()
        }
    }
})
```

```package
fuzzyBot=github:FuzzyMakers/pxt-fuzzyMakers
```
