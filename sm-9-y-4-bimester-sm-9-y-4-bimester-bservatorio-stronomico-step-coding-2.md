### @diffs true
# Observatório astronômico

## Passo 1
Neste tutorial, vamos carregar os dados das posições das constelações para um telescópio.
Usaremos a bússola do micro:bit e o potenciômetro para simular a direção que o telescópio aponta, assim poderemos verificar a constelação visualizada no momento.

## Passo 2
Para começar, verifique se a biblioteca da Smart Makers já está importada 
em seu MakeCode. Se não estiver, clique na aba **+ Extensões**, 
copie o endereço "https://github.com/FuzzyMakers/pxt-smartMakers", 
cole-o no campo de pesquisa da janela que se abriu e selecione a biblioteca. 

## Passo 3
Clique em **Avançado** para abrir novas categorias. Clique em ``||smart:Smart||``
e arraste o comando ``||smart:Definir constelações||`` para dentro do bloco ``||basic:no iniciar||``.

```blocks
Smart.startConstellation()
```

## Passo 4
Acesse a categoria ``||logic:Lógica||``, pegue a condicional ``||logic:se então senão||``
e insira-a dentro do laço ``||basic:sempre||``. 


```blocks
Smart.startConstellation()
basic.forever(function () {
    if (true) {
    	
    } else {
    	
    }
})

```

## Passo 5

Volte ao menu ``||logic:Lógica||``, pegue o comparador ``||logic:0 = 0||``
e substitua a condição **verdadeiro** da condicional.

```blocks
Smart.startConstellation()
basic.forever(function () {
    if (0 == 0) {
    	
    } else {
    	
    }
})
```

## Passo 6
Agora atualize os campos do comparador. Vá até a aba ``||sensors:Sensores||``,
clique no bloco ``||sensors:Valor do Botão na porta P2||`` e troque 
o primeiro **0** do comparador. 
Mude a porta de ``||sensors:P2||`` para ``||sensors:P0||``.

```blocks
Smart.startConstellation()
basic.forever(function () {
    if (sensors.buttonValue(InputPorts.P0) == 0) {
    	
    } else {
    	
    }
})

```

## Passo 7
Acesse o menu ``||variables:Variáveis||`` e clique em 
**"Fazer uma variável..."**. Crie uma variável chamada
``||variables:y||``. Em seguida, arraste o bloco ``||variables:definir y para 0||`` 
para dentro do ``||logic:então||``.


```blocks
let y = 0
Smart.startConstellation()
basic.forever(function () {
    if (sensors.buttonValue(InputPorts.P0) == 0) {
        y = 0
    } else {
    	
    }
})
```

## Passo 8

Acesse a categoria ``||math:Matemática||``, pegue o comando ``||math:arredonda 0||``
para colocar no valor de definição da variável.
```blocks
let y = 0
Smart.startConstellation()
basic.forever(function () {
    if (sensors.buttonValue(InputPorts.P0) == 0) {
        y = Math.round(0)
    } else {
    	
    }
})
```

## Passo 9
Volte à seção ``||math:Matemática||`` e selecione o comando ``||math:map 0 from low 0 high 1023 to low 0 high 4||``.
Substitua o **0** de ``||math:arredonda 0||`` por esse novo bloco.
```blocks
let y = 0
Smart.startConstellation()
basic.forever(function () {
    if (sensors.buttonValue(InputPorts.P0) == 0) {
        y = Math.round(Math.map(0, 0, 1023, 0, 4))
    } else {
    	
    }
})

```

## Passo 10
Atualize os valores do ``||math:map||``.
Volte ao menu ``||sensors:Sensores||``, pegue o bloco ``||sensors:Valor do potenciômetro na porta P2||`` e troque
o primeiro campo **0** do mapeamento.
Mude a porta de ``||sensors:P2||`` para ``||sensors:P1||``.
O úlitmo valor do mapeamento deve ser editado de **4** para **90**.
```blocks
let y = 0
Smart.startConstellation()
basic.forever(function () {
    if (sensors.buttonValue(InputPorts.P0) == 0) {
        y = Math.round(Math.map(sensors.dimmerValue(InputPorts.P1), 0, 1023, 0, 90))
    } else {
    	
    }
})

```


## Passo 11
Acesse a aba ``||actuators:Atuadores||`` e posicione o bloco ``||actuators:Servo, definir posição 0 porta P8 modo Knob||`` 
abaixo do último comando adicionado.

```blocks
let y = 0
Smart.startConstellation()
basic.forever(function () {
    if (sensors.buttonValue(InputPorts.P0) == 0) {
        y = Math.round(Math.map(sensors.dimmerValue(InputPorts.P1), 0, 1023, 0, 90))
        actuators.SetAngleServoKnob(0, OutputPorts.P8)
    } else {
    	
    }
})
```

## Passo 12

Duplique o bloco ``||sensors:Valor do potenciômetro na porta P1||`` e coloque-o no valor da posição do servo.
```blocks
let y = 0
Smart.startConstellation()
basic.forever(function () {
    if (sensors.buttonValue(InputPorts.P0) == 0) {
        y = Math.round(Math.map(sensors.dimmerValue(InputPorts.P1), 0, 1023, 0, 90))
        actuators.SetAngleServoKnob(sensors.dimmerValue(InputPorts.P1), OutputPorts.P8)
    } else {
    	
    }
})
```

## Passo 13

Acesse o menu ``||variables:Variáveis||`` e clique em 
**"Fazer uma variável..."**. Crie uma variável chamada
``||variables:x||``. Em seguida, arraste o bloco ``||variables:definir x para 0||`` 
para a condicional ``||logic:senão||``.

```blocks
let x = 0
let y = 0
Smart.startConstellation()
basic.forever(function () {
    if (sensors.buttonValue(InputPorts.P0) == 0) {
        y = Math.round(Math.map(sensors.dimmerValue(InputPorts.P1), 0, 1023, 0, 90))
        actuators.SetAngleServoKnob(sensors.dimmerValue(InputPorts.P1), OutputPorts.P8)
    } else {
        x = 0
    }
})
```


## Passo 14

Acesse a categoria ``||math:Matemática||``, pegue o comando ``||math:arredonda 0||``
para colocar no valor da definição da variável.
```blocks
let x = 0
let y = 0
Smart.startConstellation()
basic.forever(function () {
    if (sensors.buttonValue(InputPorts.P0) == 0) {
        y = Math.round(Math.map(sensors.dimmerValue(InputPorts.P1), 0, 1023, 0, 90))
        actuators.SetAngleServoKnob(sensors.dimmerValue(InputPorts.P1), OutputPorts.P8)
    } else {
        x = Math.round(0)
    }
})

```

## Passo 15
Vá ao menu ``||input:Entrada||`` e selecione o bloco ``||input:direção da bússola (°)||`` 
para substituir o valor **0** do bloco ``||math:arredonda||``.

```blocks
let x = 0
let y = 0
Smart.startConstellation()
basic.forever(function () {
    if (sensors.buttonValue(InputPorts.P0) == 0) {
        y = Math.round(Math.map(sensors.dimmerValue(InputPorts.P1), 0, 1023, 0, 90))
        actuators.SetAngleServoKnob(sensors.dimmerValue(InputPorts.P1), OutputPorts.P8)
    } else {
        x = Math.round(input.compassHeading())
    }
})
```

## Passo 16

Acesse a categoria ``||logic:Lógica||``, pegue a condicional ``||logic:se então senão||``
e insira-o abaixo do último comando adicionado. 

```blocks
let x = 0
let y = 0
Smart.startConstellation()
basic.forever(function () {
    if (sensors.buttonValue(InputPorts.P0) == 0) {
        y = Math.round(Math.map(sensors.dimmerValue(InputPorts.P1), 0, 1023, 0, 90))
        actuators.SetAngleServoKnob(sensors.dimmerValue(InputPorts.P1), OutputPorts.P8)
    } else {
        x = Math.round(input.compassHeading())
        if (true) {
        	
        } else {
        	
        }
    }
})

```

## Passo 17

Volte ao menu ``||logic:Lógica||``, pegue o comparador ``||logic:0 < 0||``
e substitua a condição **verdadeiro** da condicional.

```blocks
let x = 0
let y = 0
Smart.startConstellation()
basic.forever(function () {
    if (sensors.buttonValue(InputPorts.P0) == 0) {
        y = Math.round(Math.map(sensors.dimmerValue(InputPorts.P1), 0, 1023, 0, 90))
        actuators.SetAngleServoKnob(sensors.dimmerValue(InputPorts.P1), OutputPorts.P8)
    } else {
        x = Math.round(input.compassHeading())
        if (0 < 0) {
        	
        } else {
        	
        }
    }
})

```

## Passo 18

Agora atualize os campos do comparador. Vá até a aba ``||sensors:Sensores||``,
copie o bloco ``||sensors:Valor do potenciômetro na porta P1||`` e troque 
o primeiro **0** do comparador.
Troque o sinal do comparador de **<** para **>** e o segundo valor do comparador para **512**.

```blocks
let x = 0
let y = 0
Smart.startConstellation()
basic.forever(function () {
    if (sensors.buttonValue(InputPorts.P0) == 0) {
        y = Math.round(Math.map(sensors.dimmerValue(InputPorts.P1), 0, 1023, 0, 90))
        actuators.SetAngleServoKnob(sensors.dimmerValue(InputPorts.P1), OutputPorts.P8)
    } else {
        x = Math.round(input.compassHeading())
        if (sensors.dimmerValue(InputPorts.P1) > 512) {
        	
        } else {
        	
        }
    }
})
```

## Passo 19

Acesse o menu ``||actuators:Atuadores||``, adicione o bloco
``||actuators:Motor CC, definir direção para Sentido horário na porta P8||``
dentro desse novo ``||logic:então||``.
Antes de presseguir, ajuste a porta para ``||actuators:P12||``.

```blocks
let x = 0
let y = 0
Smart.startConstellation()
basic.forever(function () {
    if (sensors.buttonValue(InputPorts.P0) == 0) {
        y = Math.round(Math.map(sensors.dimmerValue(InputPorts.P1), 0, 1023, 0, 90))
        actuators.SetAngleServoKnob(sensors.dimmerValue(InputPorts.P1), OutputPorts.P8)
    } else {
        x = Math.round(input.compassHeading())
        if (sensors.dimmerValue(InputPorts.P1) > 512) {
            actuators.SetDirectionMotor(MotorDirection.clockwise, OutputPorts.P12)
        } else {
        	
        }
    }
})
```

## Passo 20

Copie o bloco
``||actuators:Motor CC, definir direção para Sentido horário na porta P12||`` e cole-o
dentro do ``||logic:senão||``.
Modifique o sentido para ``||actuators:anti-horário||``.

```blocks
let x = 0
let y = 0
Smart.startConstellation()
basic.forever(function () {
    if (sensors.buttonValue(InputPorts.P0) == 0) {
        y = Math.round(Math.map(sensors.dimmerValue(InputPorts.P1), 0, 1023, 0, 90))
        actuators.SetAngleServoKnob(sensors.dimmerValue(InputPorts.P1), OutputPorts.P8)
    } else {
        x = Math.round(input.compassHeading())
        if (sensors.dimmerValue(InputPorts.P1) > 512) {
            actuators.SetDirectionMotor(MotorDirection.clockwise, OutputPorts.P12)
        } else {
            actuators.SetDirectionMotor(MotorDirection.antiClockwise, OutputPorts.P12)
        }
    }
})
```

## Passo 21

Acesse a categoria ``||logic:Lógica||``, pegue a condicional ``||logic:se então senão||``
e insira-a **abaixo** do ``||logic:senão||`` mais interno. 

```blocks
let x = 0
let y = 0
Smart.startConstellation()
basic.forever(function () {
    if (sensors.buttonValue(InputPorts.P0) == 0) {
        y = Math.round(Math.map(sensors.dimmerValue(InputPorts.P1), 0, 1023, 0, 90))
        actuators.SetAngleServoKnob(sensors.dimmerValue(InputPorts.P1), OutputPorts.P8)
    } else {
        x = Math.round(input.compassHeading())
        if (sensors.dimmerValue(InputPorts.P1) > 512) {
            actuators.SetDirectionMotor(MotorDirection.clockwise, OutputPorts.P12)
        } else {
            actuators.SetDirectionMotor(MotorDirection.antiClockwise, OutputPorts.P12)
        }
        if (true) {
        	
        } else {
        	
        }
    }
})
```

## Passo 22

Volte ao menu ``||logic:Lógica||``, pegue o comparador ``||logic:0 = 0||``
e substitua a condição **verdadeiro** da condicional.
```blocks
let x = 0
let y = 0
Smart.startConstellation()
basic.forever(function () {
    if (sensors.buttonValue(InputPorts.P0) == 0) {
        y = Math.round(Math.map(sensors.dimmerValue(InputPorts.P1), 0, 1023, 0, 90))
        actuators.SetAngleServoKnob(sensors.dimmerValue(InputPorts.P1), OutputPorts.P8)
    } else {
        x = Math.round(input.compassHeading())
        if (sensors.dimmerValue(InputPorts.P1) > 512) {
            actuators.SetDirectionMotor(MotorDirection.clockwise, OutputPorts.P12)
        } else {
            actuators.SetDirectionMotor(MotorDirection.antiClockwise, OutputPorts.P12)
        }
        if (0 == 0) {
        	
        } else {
        	
        }
    }
})

```
## Passo 23

Agora atualize os campos do comparador. Vá até a aba ``||sensors:Sensores||``, 
selecione o bloco ``||sensors:Valor da chave de fim de curso na porta P2||`` e troque 
o primeiro **0** do comparador.
Mude o segundo valor do comparador para **1**.


```blocks
let x = 0
let y = 0
Smart.startConstellation()
basic.forever(function () {
    if (sensors.buttonValue(InputPorts.P0) == 0) {
        y = Math.round(Math.map(sensors.dimmerValue(InputPorts.P1), 0, 1023, 0, 90))
        actuators.SetAngleServoKnob(sensors.dimmerValue(InputPorts.P1), OutputPorts.P8)
    } else {
        x = Math.round(input.compassHeading())
        if (sensors.dimmerValue(InputPorts.P1) > 512) {
            actuators.SetDirectionMotor(MotorDirection.clockwise, OutputPorts.P12)
        } else {
            actuators.SetDirectionMotor(MotorDirection.antiClockwise, OutputPorts.P12)
        }
        if (sensors.endstopValue(InputPorts.P2) == 1) {
        	
        } else {
        	
        }
    }
})
```

## Passo 24


Acesse o menu ``||actuators:Atuadores||``, adicione o bloco
``||actuators:Motor CC, definir velocidade na porta P8||``
dentro desse novo ``||logic:então||``.
Ajuste a porta para ``||actuators:P16||`` e a velocidade para **150**.

```blocks
let x = 0
let y = 0
Smart.startConstellation()
basic.forever(function () {
    if (sensors.buttonValue(InputPorts.P0) == 0) {
        y = Math.round(Math.map(sensors.dimmerValue(InputPorts.P1), 0, 1023, 0, 90))
        actuators.SetAngleServoKnob(sensors.dimmerValue(InputPorts.P1), OutputPorts.P8)
    } else {
        x = Math.round(input.compassHeading())
        if (sensors.dimmerValue(InputPorts.P1) > 512) {
            actuators.SetDirectionMotor(MotorDirection.clockwise, OutputPorts.P12)
        } else {
            actuators.SetDirectionMotor(MotorDirection.antiClockwise, OutputPorts.P12)
        }
        if (sensors.endstopValue(InputPorts.P2) == 1) {
            actuators.SetSpeedMotor(150, OutputPorts.P16)
        } else {
        	
        }
    }
})
```


## Passo 25

Volte à seção ``||actuators:Atuadores||`` e arraste o comando ``||actuators:Motor CC, parar motor na porta P8||``
para dentro do ``||logic:senão||``.
Edite a porta de ``||actuators:P8||`` para ``||actuators:P16||``.

```blocks
let x = 0
let y = 0
Smart.startConstellation()
basic.forever(function () {
    if (sensors.buttonValue(InputPorts.P0) == 0) {
        y = Math.round(Math.map(sensors.dimmerValue(InputPorts.P1), 0, 1023, 0, 90))
        actuators.SetAngleServoKnob(sensors.dimmerValue(InputPorts.P1), OutputPorts.P8)
    } else {
        x = Math.round(input.compassHeading())
        if (sensors.dimmerValue(InputPorts.P1) > 512) {
            actuators.SetDirectionMotor(MotorDirection.clockwise, OutputPorts.P12)
        } else {
            actuators.SetDirectionMotor(MotorDirection.antiClockwise, OutputPorts.P12)
        }
        if (sensors.endstopValue(InputPorts.P2) == 1) {
            actuators.SetSpeedMotor(150, OutputPorts.P16)
        } else {
            actuators.StopMotor(OutputPorts.P16)
        }
    }
})


```


## Passo 26

Vá até o menu ``||basic:Básico||`` e puxe outro laço ``||basic:sempre||`` para a área de programação. 

```blocks
let x = 0
let y = 0
Smart.startConstellation()
basic.forever(function () {
    if (sensors.buttonValue(InputPorts.P0) == 0) {
        y = Math.round(Math.map(sensors.dimmerValue(InputPorts.P1), 0, 1023, 0, 90))
        actuators.SetAngleServoKnob(sensors.dimmerValue(InputPorts.P1), OutputPorts.P8)
    } else {
        x = Math.round(input.compassHeading())
        if (sensors.dimmerValue(InputPorts.P1) > 512) {
            actuators.SetDirectionMotor(MotorDirection.clockwise, OutputPorts.P12)
        } else {
            actuators.SetDirectionMotor(MotorDirection.antiClockwise, OutputPorts.P12)
        }
        if (sensors.endstopValue(InputPorts.P2) == 1) {
            actuators.SetSpeedMotor(150, OutputPorts.P16)
        } else {
            actuators.StopMotor(OutputPorts.P16)
        }
    }
})
basic.forever(function () {
	
})
```

## Passo 27

Clique no menu ``||Advanced:Avançado||``, acesse ``||serial:Serial||`` e 
insira **três** blocos ``||serial:serial gravar linha ""||`` 
no laço ``||basic:sempre||`` que está vazio.

```blocks
let x = 0
let y = 0
Smart.startConstellation()
basic.forever(function () {
    if (sensors.buttonValue(InputPorts.P0) == 0) {
        y = Math.round(Math.map(sensors.dimmerValue(InputPorts.P1), 0, 1023, 0, 90))
        actuators.SetAngleServoKnob(sensors.dimmerValue(InputPorts.P1), OutputPorts.P8)
    } else {
        x = Math.round(input.compassHeading())
        if (sensors.dimmerValue(InputPorts.P1) > 512) {
            actuators.SetDirectionMotor(MotorDirection.clockwise, OutputPorts.P12)
        } else {
            actuators.SetDirectionMotor(MotorDirection.antiClockwise, OutputPorts.P12)
        }
        if (sensors.endstopValue(InputPorts.P2) == 1) {
            actuators.SetSpeedMotor(150, OutputPorts.P16)
        } else {
            actuators.StopMotor(OutputPorts.P16)
        }
    }
})
basic.forever(function () {
    serial.writeLine("")
    serial.writeLine("")
    serial.writeLine("")
})

```

## Passo 28

Clique no menu ``||Advanced:Avançado||``, acesse ``||text:Texto||`` e 
busque **dois** blocos ``||text:unir Olá Mundo - +||`` para substituir
os campos **""** dos **dois** primeiros registros de linha serial.

```blocks
let x = 0
let y = 0
Smart.startConstellation()
basic.forever(function () {
    if (sensors.buttonValue(InputPorts.P0) == 0) {
        y = Math.round(Math.map(sensors.dimmerValue(InputPorts.P1), 0, 1023, 0, 90))
        actuators.SetAngleServoKnob(sensors.dimmerValue(InputPorts.P1), OutputPorts.P8)
    } else {
        x = Math.round(input.compassHeading())
        if (sensors.dimmerValue(InputPorts.P1) > 512) {
            actuators.SetDirectionMotor(MotorDirection.clockwise, OutputPorts.P12)
        } else {
            actuators.SetDirectionMotor(MotorDirection.antiClockwise, OutputPorts.P12)
        }
        if (sensors.endstopValue(InputPorts.P2) == 1) {
            actuators.SetSpeedMotor(150, OutputPorts.P16)
        } else {
            actuators.StopMotor(OutputPorts.P16)
        }
    }
})
basic.forever(function () {
    serial.writeLine("Olá" + "Mundo")
    serial.writeLine("Olá" + "Mundo")
    serial.writeLine("")
})
```
## Passo 29

Em seguida, atualize os campos de texto para nossa aplicação:
O primeiro bloco deve registrar **"x: "** e ``||variables:x||``
e o segundo **"y: "** e ``||variables:y||``.
```blocks
let x = 0
let y = 0
Smart.startConstellation()
basic.forever(function () {
    if (sensors.buttonValue(InputPorts.P0) == 0) {
        y = Math.round(Math.map(sensors.dimmerValue(InputPorts.P1), 0, 1023, 0, 90))
        actuators.SetAngleServoKnob(sensors.dimmerValue(InputPorts.P1), OutputPorts.P8)
    } else {
        x = Math.round(input.compassHeading())
        if (sensors.dimmerValue(InputPorts.P1) > 512) {
            actuators.SetDirectionMotor(MotorDirection.clockwise, OutputPorts.P12)
        } else {
            actuators.SetDirectionMotor(MotorDirection.antiClockwise, OutputPorts.P12)
        }
        if (sensors.endstopValue(InputPorts.P2) == 1) {
            actuators.SetSpeedMotor(150, OutputPorts.P16)
        } else {
            actuators.StopMotor(OutputPorts.P16)
        }
    }
})
basic.forever(function () {
    serial.writeLine("x:" + x)
    serial.writeLine("y:" + y)
    serial.writeLine("")
})
```

## Passo 30

Acesse mais uma vez o menu ``||smart:Smart||``, pegue o comando
``||smart:Buscar constelação em x 0 y 0||`` e substitua o espaço vazio para gravar linha
do terceiro bloco serial.
Modifique os valores do comando para as variáveis ``||variables:x||`` e ``||variables:y||`` nesta ordem.


```blocks
let x = 0
let y = 0
Smart.startConstellation()
basic.forever(function () {
    if (sensors.buttonValue(InputPorts.P0) == 0) {
        y = Math.round(Math.map(sensors.dimmerValue(InputPorts.P1), 0, 1023, 0, 90))
        actuators.SetAngleServoKnob(sensors.dimmerValue(InputPorts.P1), OutputPorts.P8)
    } else {
        x = Math.round(input.compassHeading())
        if (sensors.dimmerValue(InputPorts.P1) > 512) {
            actuators.SetDirectionMotor(MotorDirection.clockwise, OutputPorts.P12)
        } else {
            actuators.SetDirectionMotor(MotorDirection.antiClockwise, OutputPorts.P12)
        }
        if (sensors.endstopValue(InputPorts.P2) == 1) {
            actuators.SetSpeedMotor(150, OutputPorts.P16)
        } else {
            actuators.StopMotor(OutputPorts.P16)
        }
    }
})
basic.forever(function () {
    serial.writeLine("x:" + x)
    serial.writeLine("y:" + y)
    serial.writeLine(Smart.findConstellation(x, y))
})
```

## Passo 31

Na categoria ``||basic:Básico||``, arraste uma pausa ``||basic:pausa (ms) 100||`` para o código e
altere sua duração para **1000**.


```blocks
let x = 0
let y = 0
Smart.startConstellation()
basic.forever(function () {
    if (sensors.buttonValue(InputPorts.P0) == 0) {
        y = Math.round(Math.map(sensors.dimmerValue(InputPorts.P1), 0, 1023, 0, 90))
        actuators.SetAngleServoKnob(sensors.dimmerValue(InputPorts.P1), OutputPorts.P8)
    } else {
        x = Math.round(input.compassHeading())
        if (sensors.dimmerValue(InputPorts.P1) > 512) {
            actuators.SetDirectionMotor(MotorDirection.clockwise, OutputPorts.P12)
        } else {
            actuators.SetDirectionMotor(MotorDirection.antiClockwise, OutputPorts.P12)
        }
        if (sensors.endstopValue(InputPorts.P2) == 1) {
            actuators.SetSpeedMotor(150, OutputPorts.P16)
        } else {
            actuators.StopMotor(OutputPorts.P16)
        }
    }
})
basic.forever(function () {
    serial.writeLine("x:" + x)
    serial.writeLine("y:" + y)
    serial.writeLine(Smart.findConstellation(x, y))
    basic.pause(1000)
})
```

## Passo 32

Agora seu código está pronto! Baixe-o para o micro:bit e teste-o.
Use a chave de fim de curso e o potenciômetro para direcionar o telescópio, no simulador do MakeCode confira o nome da constelação vista no momento.
```blocks
```
## Passo 33
Se necessário, confira o seu código clicando na lâmpada de dica.

```blocks
let x = 0
let y = 0
Smart.startConstellation()
basic.forever(function () {
    if (sensors.buttonValue(InputPorts.P0) == 0) {
        y = Math.round(Math.map(sensors.dimmerValue(InputPorts.P1), 0, 1023, 0, 90))
        actuators.SetAngleServoKnob(sensors.dimmerValue(InputPorts.P1), OutputPorts.P8)
    } else {
        x = Math.round(input.compassHeading())
        if (sensors.dimmerValue(InputPorts.P1) > 512) {
            actuators.SetDirectionMotor(MotorDirection.clockwise, OutputPorts.P12)
        } else {
            actuators.SetDirectionMotor(MotorDirection.antiClockwise, OutputPorts.P12)
        }
        if (sensors.endstopValue(InputPorts.P2) == 1) {
            actuators.SetSpeedMotor(150, OutputPorts.P16)
        } else {
            actuators.StopMotor(OutputPorts.P16)
        }
    }
})
basic.forever(function () {
    serial.writeLine("x:" + x)
    serial.writeLine("y:" + y)
    serial.writeLine(Smart.findConstellation(x, y))
    basic.pause(1000)
})


```



```package
fuzzyBot=github:FuzzyMakers/pxt-fuzzyMakers
```
