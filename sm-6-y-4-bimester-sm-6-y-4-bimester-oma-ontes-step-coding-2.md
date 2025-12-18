### @diffs true
# Ponte Elevatória

## Passo 1
Neste tutorial, vamos programar a elevação de uma ponte. Utilizaremos
o sensor infravermelho para acionar o motor CC que erguerá a estrutura.

## Passo 2
Para começar, verifique se a biblioteca da Smart Makers já está importada 
em seu MakeCode. Se não estiver, clique na aba **+ Extensões**, 
copie o endereço "https://github.com/FuzzyMakers/pxt-smartMakers",
cole-o no campo de pesquisa da janela que se abriu e selecione a biblioteca.

## Passo 3
Acesse a aba ``||logic:Lógica||`` e adicione o bloco
``||logic:se então||`` dentro do laço ``||basic:sempre||``.

```blocks
basic.forever(function () {
    if (true) {
    	
    }
})


```

## Passo 4
Retorne ao menu ``||logic:Lógica||`` e selecione um bloco comparador
``||logic:0 < 0||`` para substituir o campo **verdadeiro**.

```blocks
basic.forever(function () {
    if (0 < 0) {
    	
    }
})
```

## Passo 5
Altere o sinal do comparador de **<** para **>**.


```blocks
basic.forever(function () {
    if (0 > 0) {
    	
    }
})


```

## Passo 6
Clique na aba ``||sensors:Sensores||`` e selecione o bloco 
``||sensors:Valor do sensor infravermelho na porta P2||``. Ele deve ser posicionado no primeiro campo do comparador, substituindo o valor **0**.

```blocks
basic.forever(function () {
    if (sensors.infraredValue(InputPorts.P2) > 0) {
    	
    }
})


```

## Passo 7

Mude o valor do segundo campo de **0** para **200**.

```blocks
basic.forever(function () {
    if (sensors.infraredValue(InputPorts.P2) > 200) {
    	
    }
})

```

## Passo 8
Acesse a categoria ``||music:Música||`` e adicione o bloco 
``||music:toque (Hz) C Médio||`` dentro do ``||logic:então||``.

```blocks
basic.forever(function () {
    if (sensors.infraredValue(InputPorts.P2) > 200) {
        music.ringTone(262)
    }
})


```

## Passo 9
Vá até a aba ``||actuators:Atuadores||``, selecione o bloco 
``||actuators:Motor CC, definir velocidade 0 na porta P8||`` e coloque-o abaixo do bloco anterior.

```blocks
basic.forever(function () {
    if (sensors.infraredValue(InputPorts.P2) > 200) {
        music.ringTone(262)
        actuators.SetSpeedMotor(0, OutputPorts.P8)
    }
})
```
## Passo 10

Modifique a velocidade de **0** para **1023** e a porta de 
``||actuators:P8||`` para ``||actuators:P16||``.

```blocks
basic.forever(function () {
    if (sensors.infraredValue(InputPorts.P2) > 200) {
        music.ringTone(262)
        actuators.SetSpeedMotor(1023, OutputPorts.P16)
    }
})

```

## Passo 11
Volte ao menu ``||actuators:Atuadores||``, selecione o bloco 
``||actuators:Motor CC, definir direção para Sentido horário na porta P8||`` e coloque-o abaixo do bloco anterior.

```blocks
basic.forever(function () {
    if (sensors.infraredValue(InputPorts.P2) > 200) {
        music.ringTone(262)
        actuators.SetSpeedMotor(1023, OutputPorts.P16)
        actuators.SetDirectionMotor(MotorDirection.clockwise, OutputPorts.P8)
    }
})

```

## Passo 12

Altere a porta de ``||actuators:P8||`` para ``||actuators:P12||``.

```blocks
basic.forever(function () {
    if (sensors.infraredValue(InputPorts.P2) > 200) {
        music.ringTone(262)
        actuators.SetSpeedMotor(1023, OutputPorts.P16)
        actuators.SetDirectionMotor(MotorDirection.clockwise, OutputPorts.P12)
    }
})


```

## Passo 13
Acesse a seção ``||basic:Básico||``, adicone uma
``||basic:pausa (ms) 100 ||`` e coloque-a abaixo do bloco anterior. Modifique o valor da pausa de **100 ms** para **1000 ms**.

```blocks
basic.forever(function () {
    if (sensors.infraredValue(InputPorts.P2) > 200) {
        music.ringTone(262)
        actuators.SetSpeedMotor(1023, OutputPorts.P16)
        actuators.SetDirectionMotor(MotorDirection.clockwise, OutputPorts.P12)
        basic.pause(1000)
    }
})


```

## Passo 14
Na aba ``||actuators:Atuadores||``, pegue o bloco 
``||actuators:Motor CC, definir velocidade 0 na porta P8||`` e coloque-o abaixo do bloco anterior.

```blocks
basic.forever(function () {
    if (sensors.infraredValue(InputPorts.P2) > 200) {
        music.ringTone(262)
        actuators.SetSpeedMotor(1023, OutputPorts.P16)
        actuators.SetDirectionMotor(MotorDirection.clockwise, OutputPorts.P12)
        basic.pause(1000)
        actuators.SetSpeedMotor(0, OutputPorts.P8)
    }
})

```
## Passo 15

Modifique a porta de ``||actuators:P8||`` para ``||actuators:P16||``.

```blocks
basic.forever(function () {
    if (sensors.infraredValue(InputPorts.P2) > 200) {
        music.ringTone(262)
        actuators.SetSpeedMotor(1023, OutputPorts.P16)
        actuators.SetDirectionMotor(MotorDirection.clockwise, OutputPorts.P12)
        basic.pause(1000)
        actuators.SetSpeedMotor(0, OutputPorts.P16)
    }
})


```

## Passo 16
Acesse a categoria ``||music:Música||`` e adicione o bloco 
``||music:stop all sounds||`` dentro do ``||logic:então||``.

```blocks
basic.forever(function () {
    if (sensors.infraredValue(InputPorts.P2) > 200) {
        music.ringTone(262)
        actuators.SetSpeedMotor(1023, OutputPorts.P16)
        actuators.SetDirectionMotor(MotorDirection.clockwise, OutputPorts.P12)
        basic.pause(1000)
        actuators.SetSpeedMotor(0, OutputPorts.P16)
        music.stopAllSounds()
    }
})


```

## Passo 17
Vá até o menu ``||loops:Loops||`` e arraste um bloco ``||loops:enquanto executar||``
 para o código.

 ```blocks
basic.forever(function () {
    if (sensors.infraredValue(InputPorts.P2) > 200) {
        music.ringTone(262)
        actuators.SetSpeedMotor(1023, OutputPorts.P16)
        actuators.SetDirectionMotor(MotorDirection.clockwise, OutputPorts.P12)
        basic.pause(1000)
        actuators.SetSpeedMotor(0, OutputPorts.P16)
        music.stopAllSounds()
        while (false) {
        	
        }
    }
})


```

## Passo 18

Copie o comparador ``||sensors:Valor do sensor infravermelho na porta P2||`` 
**> 200** do bloco ``||logic:se então||``
para substituir o campo **falso** do loop ``||loops:enquanto executar||``.

 ```blocks
basic.forever(function () {
    if (sensors.infraredValue(InputPorts.P2) > 200) {
        music.ringTone(262)
        actuators.SetSpeedMotor(1023, OutputPorts.P16)
        actuators.SetDirectionMotor(MotorDirection.clockwise, OutputPorts.P12)
        basic.pause(1000)
        actuators.SetSpeedMotor(0, OutputPorts.P16)
        music.stopAllSounds()
        while (sensors.infraredValue(InputPorts.P2) > 200) {
        	
        }
    }
})
```

## Passo 19
Acesse a seção ``||basic:Básico||`` e adicione uma
``||basic:pausa (ms) 100 ||`` dentro do bloco ``||loops:enquanto executar||``.

```blocks
basic.forever(function () {
    if (sensors.infraredValue(InputPorts.P2) > 200) {
        music.ringTone(262)
        actuators.SetSpeedMotor(1023, OutputPorts.P16)
        actuators.SetDirectionMotor(MotorDirection.clockwise, OutputPorts.P12)
        basic.pause(1000)
        actuators.SetSpeedMotor(0, OutputPorts.P16)
        music.stopAllSounds()
        while (sensors.infraredValue(InputPorts.P2) > 200) {
            basic.pause(100)
        }
    }
})



```
## Passo 20

Vá novamente até a seção ``||basic:Básico||`` e adicione uma
``||basic:pausa (ms) 100 ||`` e coloque-a abaixo do loop. Modifique o valor da pausa de **100 ms** para **1000 ms**.

```blocks
basic.forever(function () {
    if (sensors.infraredValue(InputPorts.P2) > 200) {
        music.ringTone(262)
        actuators.SetSpeedMotor(1023, OutputPorts.P16)
        actuators.SetDirectionMotor(MotorDirection.clockwise, OutputPorts.P12)
        basic.pause(1000)
        actuators.SetSpeedMotor(0, OutputPorts.P16)
        music.stopAllSounds()
        while (sensors.infraredValue(InputPorts.P2) > 200) {
            basic.pause(100)
        }
        basic.pause(1000)
    }
})



```

## Passo 21
Duplique o bloco ``||music:toque (Hz) C Médio||`` e insira-o após a pausa.

```blocks
basic.forever(function () {
    if (sensors.infraredValue(InputPorts.P2) > 200) {
        music.ringTone(262)
        actuators.SetSpeedMotor(1023, OutputPorts.P16)
        actuators.SetDirectionMotor(MotorDirection.clockwise, OutputPorts.P12)
        basic.pause(1000)
        actuators.SetSpeedMotor(0, OutputPorts.P16)
        music.stopAllSounds()
        while (sensors.infraredValue(InputPorts.P2) > 200) {
            basic.pause(100)
        }
        basic.pause(1000)
        music.ringTone(262)
    }
})


```

## Passo 22

Duplique o bloco ``||actuators:Motor CC, definir velocidade 1023 na porta P16||``  e mova-o até o fim do ``||logic:se então||``.

```blocks
basic.forever(function () {
    if (sensors.infraredValue(InputPorts.P2) > 200) {
        music.ringTone(262)
        actuators.SetSpeedMotor(1023, OutputPorts.P16)
        actuators.SetDirectionMotor(MotorDirection.clockwise, OutputPorts.P12)
        basic.pause(1000)
        actuators.SetSpeedMotor(0, OutputPorts.P16)
        music.stopAllSounds()
        while (sensors.infraredValue(InputPorts.P2) > 200) {
            basic.pause(100)
        }
        basic.pause(1000)
        music.ringTone(262)
        actuators.SetSpeedMotor(1023, OutputPorts.P16)
    }
})



```

## Passo 23

Duplique o bloco ``||actuators:Motor CC, definir direção para Sentido horário na porta P12||`` e coloque-o depois da definição de velocidade do motor.

```blocks
basic.forever(function () {
    if (sensors.infraredValue(InputPorts.P2) > 200) {
        music.ringTone(262)
        actuators.SetSpeedMotor(1023, OutputPorts.P16)
        actuators.SetDirectionMotor(MotorDirection.clockwise, OutputPorts.P12)
        basic.pause(1000)
        actuators.SetSpeedMotor(0, OutputPorts.P16)
        music.stopAllSounds()
        while (sensors.infraredValue(InputPorts.P2) > 200) {
            basic.pause(100)
        }
        basic.pause(1000)
        music.ringTone(262)
        actuators.SetSpeedMotor(1023, OutputPorts.P16)
        actuators.SetDirectionMotor(MotorDirection.clockwise, OutputPorts.P12)
    }
})
```

## Passo 24

Modifique o campo do sentido de ``||actuators:horário||`` para ``||actuators:anti-horário||``.

```blocks
basic.forever(function () {
    if (sensors.infraredValue(InputPorts.P2) > 200) {
        music.ringTone(262)
        actuators.SetSpeedMotor(1023, OutputPorts.P16)
        actuators.SetDirectionMotor(MotorDirection.clockwise, OutputPorts.P12)
        basic.pause(1000)
        actuators.SetSpeedMotor(0, OutputPorts.P16)
        music.stopAllSounds()
        while (sensors.infraredValue(InputPorts.P2) > 200) {
            basic.pause(100)
        }
        basic.pause(1000)
        music.ringTone(262)
        actuators.SetSpeedMotor(1023, OutputPorts.P16)
        actuators.SetDirectionMotor(MotorDirection.antiClockwise, OutputPorts.P12)
    }
})

```

## Passo 25

Duplique a ``||basic:pausa (ms) 1000 ||`` e coloque-a após a alteração do sentido de rotação do motor.

```blocks
basic.forever(function () {
    if (sensors.infraredValue(InputPorts.P2) > 200) {
        music.ringTone(262)
        actuators.SetSpeedMotor(1023, OutputPorts.P16)
        actuators.SetDirectionMotor(MotorDirection.clockwise, OutputPorts.P12)
        basic.pause(1000)
        actuators.SetSpeedMotor(0, OutputPorts.P16)
        music.stopAllSounds()
        while (sensors.infraredValue(InputPorts.P2) > 200) {
            basic.pause(100)
        }
        basic.pause(1000)
        music.ringTone(262)
        actuators.SetSpeedMotor(1023, OutputPorts.P16)
        actuators.SetDirectionMotor(MotorDirection.antiClockwise, OutputPorts.P12)
        basic.pause(1000)
    }
})


```

## Passo 26

Copie o bloco ``||actuators:Motor CC, definir velocidade 0 na porta P16||`` e adicione-o depois da pausa.

```blocks
basic.forever(function () {
    if (sensors.infraredValue(InputPorts.P2) > 200) {
        music.ringTone(262)
        actuators.SetSpeedMotor(1023, OutputPorts.P16)
        actuators.SetDirectionMotor(MotorDirection.clockwise, OutputPorts.P12)
        basic.pause(1000)
        actuators.SetSpeedMotor(0, OutputPorts.P16)
        music.stopAllSounds()
        while (sensors.infraredValue(InputPorts.P2) > 200) {
            basic.pause(100)
        }
        basic.pause(1000)
        music.ringTone(262)
        actuators.SetSpeedMotor(1023, OutputPorts.P16)
        actuators.SetDirectionMotor(MotorDirection.antiClockwise, OutputPorts.P12)
        basic.pause(1000)
        actuators.SetSpeedMotor(0, OutputPorts.P16)
    }
})



```
## Passo 27

Duplique o bloco ``||music:stop all sounds||`` e coloque-o no fim do ``||logic:se então||``.
```blocks
basic.forever(function () {
    if (sensors.infraredValue(InputPorts.P2) > 200) {
        music.ringTone(262)
        actuators.SetSpeedMotor(1023, OutputPorts.P16)
        actuators.SetDirectionMotor(MotorDirection.clockwise, OutputPorts.P12)
        basic.pause(1000)
        actuators.SetSpeedMotor(0, OutputPorts.P16)
        music.stopAllSounds()
        while (sensors.infraredValue(InputPorts.P2) > 200) {
            basic.pause(100)
        }
        basic.pause(1000)
        music.ringTone(262)
        actuators.SetSpeedMotor(1023, OutputPorts.P16)
        actuators.SetDirectionMotor(MotorDirection.antiClockwise, OutputPorts.P12)
        basic.pause(1000)
        actuators.SetSpeedMotor(0, OutputPorts.P16)
        music.stopAllSounds()
    }
})

```

## Passo 28

Seu código está pronto! Baixe-o para o micro:bit e teste-o. 
Movimente o navio até que ele acione a ponte, aguarde a abertura e termine a travessia.

```blocks
```

## Passo 29
Se necessário, confira o seu código clicando na lâmpada de dica.

```blocks
basic.forever(function () {
    if (sensors.infraredValue(InputPorts.P2) > 200) {
        music.ringTone(262)
        actuators.SetSpeedMotor(1023, OutputPorts.P16)
        actuators.SetDirectionMotor(MotorDirection.clockwise, OutputPorts.P12)
        basic.pause(1000)
        actuators.SetSpeedMotor(0, OutputPorts.P16)
        music.stopAllSounds()
        while (sensors.infraredValue(InputPorts.P2) > 200) {
            basic.pause(100)
        }
        basic.pause(1000)
        music.ringTone(262)
        actuators.SetSpeedMotor(1023, OutputPorts.P16)
        actuators.SetDirectionMotor(MotorDirection.antiClockwise, OutputPorts.P12)
        basic.pause(1000)
        actuators.SetSpeedMotor(0, OutputPorts.P16)
        music.stopAllSounds()
    }
})

```


```package
fuzzyBot=github:FuzzyMakers/pxt-fuzzyMakers
```