### @diffs true
# Observatório astronômico

## Passo 1
Neste tutorial, vamos carregar os dados das posições das constelações para um 
telescópio. Usaremos a **Bússola** do Micro:bit e o **Potenciômetro** para 
simular a direção que o telescópio aponta. Dessa forma, poderemos verificar qual 
é a constelação que será visualizada naquele momento.

## Passo 2
Caso você esteja utilizando o MakeCode fora da plataforma, é necessário 
garantir que a biblioteca da **Smart Makers** esteja importada. Para isso, copie 
o link **https://github.com/FuzzyMakers/pxt-smartMakers**, clique na aba 
``||+ Extensões||`` e depois cole o link no campo de pesquisa. Pressione a 
tecla Enter e, em seguida, selecione a biblioteca. 

## Passo 3
Ao iniciar a programação, você já encontra dois blocos no espaço de trabalho: 
o ``||basic:no iniciar||`` e o ``||basic:sempre||``. Caso você não os encontre, 
acesse a aba ``||basic:Básico||`` e posicione cada um livremente no espaço de trabalho.

## Passo 4
Acesse a aba ``||Avançado||`` para abrir novas opções 
de abas. Clique na opção ``||smart:Smart||`` e arraste o bloco 
``||smart:Definir constelações||`` para dentro do bloco ``||basic:no iniciar||``.

```blocks
Smart.startConstellation()
```

## Passo 5
Acesse a aba ``||logic:Lógica||``, selecione o bloco condicional
``||logic:se <verdadeiro> então, senão||`` e arraste-o para dentro do bloco 
``||basic:sempre||``. 

```blocks
Smart.startConstellation()
basic.forever(function () {
    if (true) {
    	
    } else {
    	
    }
})
```

## Passo 6
Acesse novamente a aba ``||logic:Lógica||``, selecione o bloco comparador ``||logic:<'0' = '0'>||`` 
e arraste-o para substituir o campo ``||logic:<verdadeiro>||`` do bloco condicional adicionado 
no passo anterior.

```blocks
Smart.startConstellation()
basic.forever(function () {
    if (0 == 0) {
    	
    } else {
    	
    }
})
```

## Passo 7
Acesse a aba ``||sensors:Sensores||``, selecione o bloco ``||sensors:Valor do Botão na porta [P2]||`` e 
arraste-o para substituir o primeiro **0** do bloco comparador adicionado no passo anterior. 
Em seguida, clique em cima do valor da porta e altere de ``||sensors:P2||`` para ``||sensors:P0||``.

```blocks
Smart.startConstellation()
basic.forever(function () {
    if (sensors.buttonValue(InputPorts.P0) == 0) {
    	
    } else {
    	
    }
})
```

## Passo 8
Acesse a aba ``||variables:Variáveis||`` e clique na opção **Fazer uma variável...**. 
Em seguida, defina o nome da variável para ``||variables:y||`` e, na mesma aba, arraste o bloco 
``||variables:definir [y] para '0'||`` para dentro do campo ``||logic:então||`` do bloco 
condicional adicionado no **Passo 5**.

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

## Passo 9
Acesse a aba ``||math:Matemática||``, selecione o bloco ``||math:[arredonda] '0'||`` e 
arraste-o para substituir o **0** do bloco de definição de variável adicionado 
no passo anterior.

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

## Passo 10
Acesse novamente a aba ``||math:Matemática||``, selecione o bloco 
``||math:mapear '0' de baixo '0' de alto '1023' até baixo '0' até alto '4'||`` e 
arraste-o para substituir o **0** do bloco de arredondamento adicionado no passo anterior.

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

## Passo 11
Acesse a aba ``||sensors:Sensores||``, selecione o bloco ``||sensors:Valor do potenciômetro na porta [P2]||`` e 
arraste-o para substituir o primeiro **0** do bloco de mapeamento adicionado no passo anterior. 
Em seguida, clique em cima do valor da porta e altere de ``||sensors:P2||`` para ``||sensors:P1||``.

```blocks
let y = 0
Smart.startConstellation()
basic.forever(function () {
    if (sensors.buttonValue(InputPorts.P0) == 0) {
        y = Math.round(Math.map(sensors.dimmerValue(InputPorts.P1), 0, 1023, 0, 4))
    } else {
    	
    }
})
```

## Passo 12
No bloco de mapeamento (adicionado no **Passo 10**), altere o valor de 
``||math:até baixo '0'||`` de **0** para **90** e de ``||math:até alto '4'||`` 
de **4** para **0**.

```blocks
let y = 0
Smart.startConstellation()
basic.forever(function () {
    if (sensors.buttonValue(InputPorts.P0) == 0) {
        y = Math.round(Math.map(sensors.dimmerValue(InputPorts.P1), 0, 1023, 90, 0))
    } else {
    	
    }
})
```

## Passo 13
Acesse a aba ``||actuators:Atuadores||``, selecione o bloco 
``||actuators:Servo, definir posição '0' porta [P8] modo Knob||`` e 
posicione logo abaixo do bloco de definição de variável adicionado no **Passo 8**.

```blocks
let y = 0
Smart.startConstellation()
basic.forever(function () {
    if (sensors.buttonValue(InputPorts.P0) == 0) {
        y = Math.round(Math.map(sensors.dimmerValue(InputPorts.P1), 0, 1023, 90, 0))
        actuators.SetAngleServoKnob(0, OutputPorts.P8)
    } else {
    	
    }
})
```

## Passo 14
Clique com o botão direito em cima do bloco ``||sensors:Valor do potenciômetro na porta [P1]||`` 
(adicionado no **Passo 11**) e depois clique em **Duplicar**. Em seguida, arraste 
o bloco duplicado para substituir o **0** do bloco de posicionamento do servo 
adicionado no passo anterior.

```blocks
let y = 0
Smart.startConstellation()
basic.forever(function () {
    if (sensors.buttonValue(InputPorts.P0) == 0) {
        y = Math.round(Math.map(sensors.dimmerValue(InputPorts.P1), 0, 1023, 90, 0))
        actuators.SetAngleServoKnob(sensors.dimmerValue(InputPorts.P1), OutputPorts.P8)
    } else {
    	
    }
})
```

## Passo 15
Acesse a aba ``||variables:Variáveis||`` e clique na opção **Fazer uma variável...**. 
Em seguida defina o nome da variável para ``||variables:x||`` e, na mesma aba, arraste o bloco 
``||variables:definir [x] para '0'||`` para dentro do campo ``||logic:senão||`` do bloco 
condicional adicionado no **Passo 5**.

```blocks
let x = 0
let y = 0
Smart.startConstellation()
basic.forever(function () {
    if (sensors.buttonValue(InputPorts.P0) == 0) {
        y = Math.round(Math.map(sensors.dimmerValue(InputPorts.P1), 0, 1023, 90, 0))
        actuators.SetAngleServoKnob(sensors.dimmerValue(InputPorts.P1), OutputPorts.P8)
    } else {
        x = 0
    }
})
```

## Passo 16
Acesse a aba ``||math:Matemática||``, selecione o bloco ``||math:[arredonda] '0'||`` e 
arraste-o para substituir o **0** do bloco de definição de variável adicionado 
no passo anterior.

```blocks
let x = 0
let y = 0
Smart.startConstellation()
basic.forever(function () {
    if (sensors.buttonValue(InputPorts.P0) == 0) {
        y = Math.round(Math.map(sensors.dimmerValue(InputPorts.P1), 0, 1023, 90, 0))
        actuators.SetAngleServoKnob(sensors.dimmerValue(InputPorts.P1), OutputPorts.P8)
    } else {
        x = Math.round(0)
    }
})
```

## Passo 17
Acesse a aba ``||input:Entrada||``, selecione o bloco ``||input:direção da bússola (°)||`` e 
arraste-o para substituir o **0** do bloco de arredondamento adicionado no passo 
anterior.

```blocks
let x = 0
let y = 0
Smart.startConstellation()
basic.forever(function () {
    if (sensors.buttonValue(InputPorts.P0) == 0) {
        y = Math.round(Math.map(sensors.dimmerValue(InputPorts.P1), 0, 1023, 90, 0))
        actuators.SetAngleServoKnob(sensors.dimmerValue(InputPorts.P1), OutputPorts.P8)
    } else {
        x = Math.round(input.compassHeading())
    }
})
```

## Passo 18
Acesse a aba ``||logic:Lógica||``, selecione o bloco condicional
``||logic:se <verdadeiro> então, senão||`` e posicione logo abaixo do bloco de 
definição de variável adicionado no **Passo 15**.

```blocks
let x = 0
let y = 0
Smart.startConstellation()
basic.forever(function () {
    if (sensors.buttonValue(InputPorts.P0) == 0) {
        y = Math.round(Math.map(sensors.dimmerValue(InputPorts.P1), 0, 1023, 90, 0))
        actuators.SetAngleServoKnob(sensors.dimmerValue(InputPorts.P1), OutputPorts.P8)
    } else {
        x = Math.round(input.compassHeading())
        if (true) {
        	
        } else {
        	
        }
    }
})
```

## Passo 19
Acesse novamente a aba ``||logic:Lógica||``, selecione o bloco comparador ``||logic:<'0' < '0'>||`` 
e arraste-o para substituir o campo ``||logic:<verdadeiro>||`` do bloco condicional adicionado 
no passo anterior.

```blocks
let x = 0
let y = 0
Smart.startConstellation()
basic.forever(function () {
    if (sensors.buttonValue(InputPorts.P0) == 0) {
        y = Math.round(Math.map(sensors.dimmerValue(InputPorts.P1), 0, 1023, 90, 0))
        actuators.SetAngleServoKnob(sensors.dimmerValue(InputPorts.P1), OutputPorts.P8)
    } else {
        x = Math.round(input.compassHeading())
        if (0 < 0) {
        	
        } else {
        	
        }
    }
})
```

## Passo 20
Clique com o botão direito em cima do bloco ``||sensors:Valor do potenciômetro na porta [P1]||`` 
(adicionado no **Passo 14**) e depois clique em **Duplicar**. Em seguida, arraste 
o bloco duplicado para substituir o primeiro **0** do bloco comparador adicionado no 
passo anterior.

```blocks
let x = 0
let y = 0
Smart.startConstellation()
basic.forever(function () {
    if (sensors.buttonValue(InputPorts.P0) == 0) {
        y = Math.round(Math.map(sensors.dimmerValue(InputPorts.P1), 0, 1023, 90, 0))
        actuators.SetAngleServoKnob(sensors.dimmerValue(InputPorts.P1), OutputPorts.P8)
    } else {
        x = Math.round(input.compassHeading())
        if (sensors.dimmerValue(InputPorts.P1) < 0) {
        	
        } else {
        	
        }
    }
})
```

## Passo 21
Ainda no mesmo bloco, clique em cima do sinal do bloco comparador (adicionado no **Passo 19**) 
e altere de ``||logic:<||`` para ``||logic:>||``. Altere também o segundo **0** 
do bloco comparador para **512**.

```blocks
let x = 0
let y = 0
Smart.startConstellation()
basic.forever(function () {
    if (sensors.buttonValue(InputPorts.P0) == 0) {
        y = Math.round(Math.map(sensors.dimmerValue(InputPorts.P1), 0, 1023, 90, 0))
        actuators.SetAngleServoKnob(sensors.dimmerValue(InputPorts.P1), OutputPorts.P8)
    } else {
        x = Math.round(input.compassHeading())
        if (sensors.dimmerValue(InputPorts.P1) > 512) {
        	
        } else {
        	
        }
    }
})
```

## Passo 22
Acesse a aba ``||actuators:Atuadores||``, selecione o bloco 
``||actuators:Motor CC, definir direção para Sentido [horário] na porta [P8]||`` 
e arraste-o para dentro do campo ``||logic:então||`` do bloco condicional 
adicionado no **Passo 18**. Em seguida, clique em cima do valor da porta e 
altere de ``||actuators:P8||`` para ``||actuators:P12||``.

```blocks
let x = 0
let y = 0
Smart.startConstellation()
basic.forever(function () {
    if (sensors.buttonValue(InputPorts.P0) == 0) {
        y = Math.round(Math.map(sensors.dimmerValue(InputPorts.P1), 0, 1023, 90, 0))
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

## Passo 23
Clique com o botão direito em cima do bloco ``||actuators:Motor CC, definir direção para Sentido [horário] na porta [P12]||`` 
(adicionado no passo anterior) e depois clique em **Duplicar**. Em seguida, arraste 
o bloco duplicado para dentro do campo ``||logic:senão||`` da condicional 
criada no **Passo 18**. Em seguida, clique em cima do sentido do motor e 
altere de ``||actuators:horário||`` para ``||actuators:anti-horário||``.

```blocks
let x = 0
let y = 0
Smart.startConstellation()
basic.forever(function () {
    if (sensors.buttonValue(InputPorts.P0) == 0) {
        y = Math.round(Math.map(sensors.dimmerValue(InputPorts.P1), 0, 1023, 90, 0))
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

## Passo 24
Acesse a aba ``||logic:Lógica||``, selecione o bloco condicional
``||logic:se <verdadeiro> então, senão||`` e posicione logo abaixo do outro bloco 
condicional adicionado no **Passo 18**.

```blocks
let x = 0
let y = 0
Smart.startConstellation()
basic.forever(function () {
    if (sensors.buttonValue(InputPorts.P0) == 0) {
        y = Math.round(Math.map(sensors.dimmerValue(InputPorts.P1), 0, 1023, 90, 0))
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

## Passo 25
Acesse novamente a aba ``||logic:Lógica||``, selecione o bloco comparador ``||logic:<'0' = '0'>||`` 
e arraste-o para substituir o campo ``||logic:<verdadeiro>||`` do bloco condicional adicionado 
no passo anterior.

```blocks
let x = 0
let y = 0
Smart.startConstellation()
basic.forever(function () {
    if (sensors.buttonValue(InputPorts.P0) == 0) {
        y = Math.round(Math.map(sensors.dimmerValue(InputPorts.P1), 0, 1023, 90, 0))
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

## Passo 26
Acesse a aba ``||sensors:Sensores||``, selecione o bloco ``||sensors:Valor da chave fim de curso na porta [P2]||`` e 
arraste-o para substituir o primeiro **0** do bloco comparador adicionado no passo anterior. Em seguida, 
altere o segundo **0** do bloco comparador para **1**.

```blocks
let x = 0
let y = 0
Smart.startConstellation()
basic.forever(function () {
    if (sensors.buttonValue(InputPorts.P0) == 0) {
        y = Math.round(Math.map(sensors.dimmerValue(InputPorts.P1), 0, 1023, 90, 0))
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

## Passo 27
Acesse a aba ``||actuators:Atuadores||``, selecione o bloco 
``||actuators:Motor CC, definir velocidade '0' na porta [P8]||`` e arraste-o 
para dentro do campo ``||logic:então||`` do bloco condicional adicionado no 
**Passo 24**. Em seguida, clique em cima do valor da porta e altere de ``||actuators:P8||`` 
para ``||actuators:P16||``. Altere também o valor da velocidade do motor de **0** para **150**.

```blocks
let x = 0
let y = 0
Smart.startConstellation()
basic.forever(function () {
    if (sensors.buttonValue(InputPorts.P0) == 0) {
        y = Math.round(Math.map(sensors.dimmerValue(InputPorts.P1), 0, 1023, 90, 0))
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

## Passo 28
Acesse novamente a aba ``||actuators:Atuadores||``, selecione o bloco 
``||actuators:Motor CC, parar motor na porta [P8]||`` e arraste-o 
para dentro do campo ``||logic:senão||`` do bloco condicional adicionado no 
**Passo 24**. Em seguida, clique em cima do valor da porta e altere de ``||actuators:P8||`` 
para ``||actuators:P16||``.

```blocks
let x = 0
let y = 0
Smart.startConstellation()
basic.forever(function () {
    if (sensors.buttonValue(InputPorts.P0) == 0) {
        y = Math.round(Math.map(sensors.dimmerValue(InputPorts.P1), 0, 1023, 90, 0))
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

## Passo 29
Acesse a aba ``||basic:Básico||``, selecione o bloco ``||basic:sempre||`` e 
solte-o livremente no espaço de trabalho, sem encaixá-lo em nenhum outro bloco. 

```blocks
let x = 0
let y = 0
Smart.startConstellation()
basic.forever(function () {
    if (sensors.buttonValue(InputPorts.P0) == 0) {
        y = Math.round(Math.map(sensors.dimmerValue(InputPorts.P1), 0, 1023, 90, 0))
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

## Passo 30
Acesse a aba ``||variables:Variáveis||`` e clique na opção **Fazer uma variável...**. 
Em seguida, defina o nome da variável para ``||variables:constelacao||`` e, na mesma aba, 
arraste o bloco ``||variables:definir [constelacao] para '0'||`` para dentro do bloco 
``||basic:sempre||`` adicionado no passo anterior.

```blocks
let constelacao = 0
let x = 0
let y = 0
Smart.startConstellation()
basic.forever(function () {
    if (sensors.buttonValue(InputPorts.P0) == 0) {
        y = Math.round(Math.map(sensors.dimmerValue(InputPorts.P1), 0, 1023, 90, 0))
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
    constelacao = 0
})
```

## Passo 31
Acesse a aba ``||Avançado||`` para abrir novas opções de abas. Clique na opção 
``||smart:Smart||``, selecione o bloco ``||smart:Buscar constelação em x '0' y '0'||`` 
e arraste-o para substituir o **0** do bloco de definição de variável adicionado 
no passo anterior.

```blocks
let constelacao = ""
let x = 0
let y = 0
Smart.startConstellation()
basic.forever(function () {
    if (sensors.buttonValue(InputPorts.P0) == 0) {
        y = Math.round(Math.map(sensors.dimmerValue(InputPorts.P1), 0, 1023, 90, 0))
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
    constelacao = Smart.findConstellation(0, 0)
})
```

## Passo 32
Acesse a aba ``||variables:Variáveis||``, selecione o bloco da variável 
``||variables:x||`` e arraste-o para substituir o primeiro **0** do bloco de 
constelação adicionado no passo anterior. Em seguida, acesse novamente a aba 
``||variables:Variáveis||``, selecione o bloco da variável ``||variables:y||`` 
e arraste-o para substituir o segundo **0** do mesmo bloco. 

```blocks
let constelacao = ""
let x = 0
let y = 0
Smart.startConstellation()
basic.forever(function () {
    if (sensors.buttonValue(InputPorts.P0) == 0) {
        y = Math.round(Math.map(sensors.dimmerValue(InputPorts.P1), 0, 1023, 90, 0))
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
    constelacao = Smart.findConstellation(x, y)
})
```

## Passo 33
Acesse a aba ``||logic:Lógica||``, selecione o bloco condicional
``||logic:se <verdadeiro> então, senão||`` e posicione logo abaixo 
do bloco de definição de variável adicionado no **Passo 30**.

```blocks
let constelacao = ""
let x = 0
let y = 0
Smart.startConstellation()
basic.forever(function () {
    if (sensors.buttonValue(InputPorts.P0) == 0) {
        y = Math.round(Math.map(sensors.dimmerValue(InputPorts.P1), 0, 1023, 90, 0))
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
    constelacao = Smart.findConstellation(x, y)
    if (true) {
    	
    } else {
    	
    }
})
```

## Passo 34
Acesse novamente a aba ``||logic:Lógica||``, selecione o bloco comparador ``||logic:<'0' = '0'>||`` 
e arraste-o para substituir o campo ``||logic:<verdadeiro>||`` do bloco condicional adicionado 
no passo anterior.

```blocks
let constelacao = ""
let x = 0
let y = 0
Smart.startConstellation()
basic.forever(function () {
    if (sensors.buttonValue(InputPorts.P0) == 0) {
        y = Math.round(Math.map(sensors.dimmerValue(InputPorts.P1), 0, 1023, 90, 0))
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
    constelacao = Smart.findConstellation(x, y)
    if (0 == 0) {
    	
    } else {
    	
    }
})
```

## Passo 35
Acesse a aba ``||variables:Variáveis||``, selecione o bloco da variável 
``||variables:constelacao||`` e arraste-o para substituir o primeiro **0** do 
bloco comparador adicionado no passo anterior.

**Obs.:** Caso você observe alguma mensagem de erro no código, ignore e siga 
para o próximo passo.

```blocks
let constelacao = ""
let x = 0
let y = 0
Smart.startConstellation()
basic.forever(function () {
    if (sensors.buttonValue(InputPorts.P0) == 0) {
        y = Math.round(Math.map(sensors.dimmerValue(InputPorts.P1), 0, 1023, 90, 0))
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
    constelacao = Smart.findConstellation(x, y)
    if (constelacao == 0) {
    	
    } else {
    	
    }
})
```

## Passo 36
Acesse a aba ``||Avançado||`` para abrir novas opções de abas. Clique na opção 
``||text:Texto||``, selecione o bloco vazio ``||text:" "||`` e arraste-o para 
substituir o segundo **0** do bloco comparador adicionado no **Passo 34**. Em seguida, 
clique em cima do bloco vazio e digite ``||text:"nenhuma"||``.

```blocks
let constelacao = ""
let x = 0
let y = 0
Smart.startConstellation()
basic.forever(function () {
    if (sensors.buttonValue(InputPorts.P0) == 0) {
        y = Math.round(Math.map(sensors.dimmerValue(InputPorts.P1), 0, 1023, 90, 0))
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
    constelacao = Smart.findConstellation(x, y)
    if (constelacao == "nenhuma") {
    	
    } else {
    	
    }
})
```

## Passo 37
Acesse a aba ``||basic:Básico||``, selecione o bloco ``||basic:mostrar ícone [♡]||`` e 
arraste-o para dentro do campo ``||logic:então||`` do bloco condicional adicionado no **Passo 33**. 
Em seguida, clique em cima do ícone e altere de ``||basic:♡||`` para ``||basic:x||``.

```blocks
let constelacao = ""
let x = 0
let y = 0
Smart.startConstellation()
basic.forever(function () {
    if (sensors.buttonValue(InputPorts.P0) == 0) {
        y = Math.round(Math.map(sensors.dimmerValue(InputPorts.P1), 0, 1023, 90, 0))
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
    constelacao = Smart.findConstellation(x, y)
    if (constelacao == "nenhuma") {
        basic.showIcon(IconNames.No)
    } else {
    	
    }
})
```

## Passo 38
Clique com o botão direito em cima do bloco ``||basic:mostrar ícone [x]||`` 
(adicionado no passo anterior) e depois clique em **Duplicar**. Em seguida, arraste 
o bloco duplicado para dentro do campo ``||logic:senão||`` da condicional 
criada no **Passo 33**. Por fim, clique em cima do ícone e altere de ``||basic:x||`` para ``||basic:✓||``.

```blocks
let constelacao = ""
let x = 0
let y = 0
Smart.startConstellation()
basic.forever(function () {
    if (sensors.buttonValue(InputPorts.P0) == 0) {
        y = Math.round(Math.map(sensors.dimmerValue(InputPorts.P1), 0, 1023, 90, 0))
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
    constelacao = Smart.findConstellation(x, y)
    if (constelacao == "nenhuma") {
        basic.showIcon(IconNames.No)
    } else {
        basic.showIcon(IconNames.Yes)
    }
})
```

## Passo 39
Acesse a aba ``||input:Entrada||``, selecione o bloco ``||input:no logotipo [pressionado]||`` e 
solte-o livremente no espaço de trabalho, sem encaixá-lo em nenhum outro bloco. 

```blocks
input.onLogoEvent(TouchButtonEvent.Pressed, function () {
	
})
let constelacao = ""
let x = 0
let y = 0
Smart.startConstellation()
basic.forever(function () {
    if (sensors.buttonValue(InputPorts.P0) == 0) {
        y = Math.round(Math.map(sensors.dimmerValue(InputPorts.P1), 0, 1023, 90, 0))
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
    constelacao = Smart.findConstellation(x, y)
    if (constelacao == "nenhuma") {
        basic.showIcon(IconNames.No)
    } else {
        basic.showIcon(IconNames.Yes)
    }
})
```

## Passo 40
Acesse a aba ``||basic:Básico||``, selecione o bloco ``||basic:limpar tela||`` e 
arraste-o para dentro do bloco do logotipo adicionado no passo anterior. 
Ainda na mesma aba, selecione o bloco ``||basic:mostrar string "Olá!"||`` 
e posicione logo abaixo do bloco de limpeza da tela. 

```blocks
input.onLogoEvent(TouchButtonEvent.Pressed, function () {
    basic.clearScreen()
    basic.showString("Olá!")
})
let constelacao = ""
let x = 0
let y = 0
Smart.startConstellation()
basic.forever(function () {
    if (sensors.buttonValue(InputPorts.P0) == 0) {
        y = Math.round(Math.map(sensors.dimmerValue(InputPorts.P1), 0, 1023, 90, 0))
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
    constelacao = Smart.findConstellation(x, y)
    if (constelacao == "nenhuma") {
        basic.showIcon(IconNames.No)
    } else {
        basic.showIcon(IconNames.Yes)
    }
})
```

## Passo 41
Acesse a aba ``||variables:Variáveis||``, selecione o bloco da variável 
``||variables:constelacao||`` e arraste-o para substituir o ``||basic:"Olá!"||`` 
do bloco de string adicionado no passo anterior.

```blocks
input.onLogoEvent(TouchButtonEvent.Pressed, function () {
    basic.clearScreen()
    basic.showString(constelacao)
})
let x = 0
let y = 0
let constelacao = ""
Smart.startConstellation()
basic.forever(function () {
    if (sensors.buttonValue(InputPorts.P0) == 0) {
        y = Math.round(Math.map(sensors.dimmerValue(InputPorts.P1), 0, 1023, 90, 0))
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
    constelacao = Smart.findConstellation(x, y)
    if (constelacao == "nenhuma") {
        basic.showIcon(IconNames.No)
    } else {
        basic.showIcon(IconNames.Yes)
    }
})
```

## Passo 42
Acesse a aba ``||input:Entrada||``, selecione o bloco ``||input:no botão [A] pressionado||`` e 
solte-o livremente no espaço de trabalho, sem encaixá-lo em nenhum outro bloco. 

```blocks
input.onLogoEvent(TouchButtonEvent.Pressed, function () {
    basic.clearScreen()
    basic.showString(constelacao)
})
input.onButtonPressed(Button.A, function () {
	
})
let x = 0
let y = 0
let constelacao = ""
Smart.startConstellation()
basic.forever(function () {
    if (sensors.buttonValue(InputPorts.P0) == 0) {
        y = Math.round(Math.map(sensors.dimmerValue(InputPorts.P1), 0, 1023, 90, 0))
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
    constelacao = Smart.findConstellation(x, y)
    if (constelacao == "nenhuma") {
        basic.showIcon(IconNames.No)
    } else {
        basic.showIcon(IconNames.Yes)
    }
})
```

## Passo 43
Acesse a aba ``||basic:Básico||``, selecione o bloco ``||basic:limpar tela||`` e 
arraste-o para dentro do bloco do botão A adicionado no passo anterior. 
Ainda na mesma aba, selecione o bloco ``||basic:mostrar número '0'||`` e posicione 
logo abaixo do bloco de limpeza da tela. 

```blocks
input.onLogoEvent(TouchButtonEvent.Pressed, function () {
    basic.clearScreen()
    basic.showString(constelacao)
})
input.onButtonPressed(Button.A, function () {
    basic.clearScreen()
    basic.showNumber(0)
})
let x = 0
let y = 0
let constelacao = ""
Smart.startConstellation()
basic.forever(function () {
    if (sensors.buttonValue(InputPorts.P0) == 0) {
        y = Math.round(Math.map(sensors.dimmerValue(InputPorts.P1), 0, 1023, 90, 0))
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
    constelacao = Smart.findConstellation(x, y)
    if (constelacao == "nenhuma") {
        basic.showIcon(IconNames.No)
    } else {
        basic.showIcon(IconNames.Yes)
    }
})
```

## Passo 44
Acesse a aba ``||variables:Variáveis||``, selecione o bloco da variável 
``||variables:x||`` e arraste-o para substituir o **0** do bloco de número 
adicionado no passo anterior.

```blocks
input.onLogoEvent(TouchButtonEvent.Pressed, function () {
    basic.clearScreen()
    basic.showString(constelacao)
})
input.onButtonPressed(Button.A, function () {
    basic.clearScreen()
    basic.showNumber(x)
})
let y = 0
let x = 0
let constelacao = ""
Smart.startConstellation()
basic.forever(function () {
    if (sensors.buttonValue(InputPorts.P0) == 0) {
        y = Math.round(Math.map(sensors.dimmerValue(InputPorts.P1), 0, 1023, 90, 0))
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
    constelacao = Smart.findConstellation(x, y)
    if (constelacao == "nenhuma") {
        basic.showIcon(IconNames.No)
    } else {
        basic.showIcon(IconNames.Yes)
    }
})
```

## Passo 45
Clique com o botão direito em cima do bloco  ``||input:no botão [A] pressionado||`` 
(adicionado no **Passo 42**) e depois clique em **Duplicar**. No bloco duplicado, 
clique em cima do valor do botão e altere de ``||input:A||`` para ``||input:B||``.

```blocks
input.onLogoEvent(TouchButtonEvent.Pressed, function () {
    basic.clearScreen()
    basic.showString(constelacao)
})
input.onButtonPressed(Button.A, function () {
    basic.clearScreen()
    basic.showNumber(x)
})
input.onButtonPressed(Button.B, function () {
    basic.clearScreen()
    basic.showNumber(x)
})
let y = 0
let x = 0
let constelacao = ""
Smart.startConstellation()
basic.forever(function () {
    if (sensors.buttonValue(InputPorts.P0) == 0) {
        y = Math.round(Math.map(sensors.dimmerValue(InputPorts.P1), 0, 1023, 90, 0))
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
    constelacao = Smart.findConstellation(x, y)
    if (constelacao == "nenhuma") {
        basic.showIcon(IconNames.No)
    } else {
        basic.showIcon(IconNames.Yes)
    }
})
```

## Passo 46
Ainda no mesmo bloco, clique em cima do valor da variável e altere de ``||variables:x||`` 
para ``||variables:y||``.

```blocks
input.onLogoEvent(TouchButtonEvent.Pressed, function () {
    basic.clearScreen()
    basic.showString(constelacao)
})
input.onButtonPressed(Button.A, function () {
    basic.clearScreen()
    basic.showNumber(x)
})
input.onButtonPressed(Button.B, function () {
    basic.clearScreen()
    basic.showNumber(y)
})
let y = 0
let x = 0
let constelacao = ""
Smart.startConstellation()
basic.forever(function () {
    if (sensors.buttonValue(InputPorts.P0) == 0) {
        y = Math.round(Math.map(sensors.dimmerValue(InputPorts.P1), 0, 1023, 90, 0))
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
    constelacao = Smart.findConstellation(x, y)
    if (constelacao == "nenhuma") {
        basic.showIcon(IconNames.No)
    } else {
        basic.showIcon(IconNames.Yes)
    }
})
```

## Passo 47
Agora a sua programação já está pronta! Conecte o seu Micro:bit ao seu dispositivo e faça o download 
do código através do botão **Baixar**, localizado no canto inferior esquerdo dessa janela.
Utilize o **Chave Fim de Curso** e o **Potenciômetro** para direcionar 
o telescópio. Confira, através do simulador do MakeCode, o nome da constelação identificada.

**Obs.:** Se necessário, confira o seu código clicando na lâmpada de dica abaixo!

```blocks
input.onLogoEvent(TouchButtonEvent.Pressed, function () {
    basic.clearScreen()
    basic.showString(constelacao)
})
input.onButtonPressed(Button.A, function () {
    basic.clearScreen()
    basic.showNumber(x)
})
input.onButtonPressed(Button.B, function () {
    basic.clearScreen()
    basic.showNumber(y)
})
let y = 0
let x = 0
let constelacao = ""
Smart.startConstellation()
basic.forever(function () {
    if (sensors.buttonValue(InputPorts.P0) == 0) {
        y = Math.round(Math.map(sensors.dimmerValue(InputPorts.P1), 0, 1023, 90, 0))
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
    constelacao = Smart.findConstellation(x, y)
    if (constelacao == "nenhuma") {
        basic.showIcon(IconNames.No)
    } else {
        basic.showIcon(IconNames.Yes)
    }
})
```

```package
fuzzyBot=github:FuzzyMakers/pxt-smartMakers
``` 
