### @diffs true
# Perfuratriz

## Passo 1
Neste tutorial, vamos programar uma perfuratriz que tem a profundidade ajustada e é acionada pelo micro:bit. No display, podem ser exibidos o minério a ser extraído ou o nível da profundidade.
## Passo 2
Para começar, verifique se a biblioteca da Smart Makers já está importada 
em seu MakeCode. Se não estiver, clique na aba **+ Extensões**, 
copie o endereço "https://github.com/FuzzyMakers/pxt-smartMakers",
cole-o no campo de pesquisa da janela que se abriu e selecione a biblioteca.

## Passo 3
Acesse o menu ``||variables:Variáveis||`` e clique em 
**"Fazer uma variável..."**. Crie uma variável chamada
``||variables:profundidade||``. Em seguida, arraste o bloco ``||variables:definir profundidade para 0||`` 
para o bloco ``||basic:sempre||``.

```blocks
let profundidade = 0
basic.forever(function () {
    profundidade = 0
})
```


## Passo 4
Vá à categoria ``||math:Matemática||``, pegue o bloco ``||math:arredonda 0||``
e substitua o valor **0** na definição da variável.
```blocks
let profundidade = 0
basic.forever(function () {
    profundidade = Math.round(0)
})
```

## Passo 5

Volte à aba ``||math:Matemática||``, pegue o bloco ``||math:map 0 from low 0 high 1023 to low 0 high 4||``
e edite o valor **0** da operação ``||math:arredonda 0||``.
```blocks
let profundidade = 0
basic.forever(function () {
    profundidade = Math.round(Math.map(0, 0, 1023, 0, 4))
})
```

## Passo 6
Agora atualize os valores do mapeamento. Acesse a categoria ``||sensors:Sensores||`` e atualize o primeiro campo com
o bloco ``||sensors:Valor do sensor infravermelho na porta P2||``. 
Edite a porta de ``||sensors:P2||`` para ``||sensors:P1||``.
Modifique o último campo de **4** para **250**.



```blocks
let profundidade = 0
basic.forever(function () {
    profundidade = Math.round(Math.map(sensors.infraredValue(InputPorts.P1), 0, 1023, 0, 250))
})
```

## Passo 7
Acesse a categoria ``||logic:Lógica||``, pegue a condicional ``||logic:se então senão||``
e insira-a dentro do bloco ``||basic:sempre||``. 

```blocks
let profundidade = 0
basic.forever(function () {
    profundidade = Math.round(Math.map(sensors.infraredValue(InputPorts.P1), 0, 1023, 0, 250))
    if (true) {
    	
    } else {
    	
    }
})
```

## Passo 8

Volte ao menu ``||logic:Lógica||``, pegue o comparador ``||logic:0 = 0||``
e substitua a condição **verdadeiro** da condicional.

```blocks
let profundidade = 0
basic.forever(function () {
    profundidade = Math.round(Math.map(sensors.infraredValue(InputPorts.P1), 0, 1023, 0, 250))
    if (0 == 0) {
    	
    } else {
    	
    }
})

```

## Passo 9
Agora atualize os campos do comparador. Vá até a aba ``||sensors:Sensores||``,
clique no bloco ``||sensors:Valor do Botão na porta P2||`` e troque 
o primeiro **0** do comparador.

```blocks
let profundidade = 0
basic.forever(function () {
    profundidade = Math.round(Math.map(sensors.infraredValue(InputPorts.P1), 0, 1023, 0, 250))
    if (sensors.buttonValue(InputPorts.P2) == 0) {
    	
    } else {
    	
    }
})
```

## Passo 10
Acesse a categoria ``||logic:Lógica||``, pegue outra condicional ``||logic:se então senão||``
e insira-a dentro do bloco ``||logic:se Valor do Botão na porta P2 = 0 então||``. 
Clique **duas** vezes no botão **+** para criar mais duas condições.

```blocks
let profundidade = 0
basic.forever(function () {
    profundidade = Math.round(Math.map(sensors.infraredValue(InputPorts.P1), 0, 1023, 0, 250))
    if (sensors.buttonValue(InputPorts.P2) == 0) {
        if (true) {
        	
        } else if (false) {
        	
        } else if (false) {
        	
        } else {
        	
        }
    } else {
    	
    }
})
```


## Passo 11

Volte ao menu ``||logic:Lógica||``, pegue o comparador ``||logic:0 < 0||``
e substitua a condição **verdadeiro** da primeira condicional.


```blocks
let profundidade = 0
basic.forever(function () {
    profundidade = Math.round(Math.map(sensors.infraredValue(InputPorts.P1), 0, 1023, 0, 250))
    if (sensors.buttonValue(InputPorts.P2) == 0) {
        if (0 < 0) {
        	
        } else if (false) {
        	
        } else if (false) {
        	
        } else {
        	
        }
    } else {
    	
    }
})
```

## Passo 12

Agora atualize os campos do comparador. Vá até a aba ``||variables:Variáveis||``,
pegue o bloco ``||variables:profundidade||`` e edite o primeiro **0** do comparador.
Mude o sinal de **<** para **>** e o segundo valor para **200**.

```blocks
let profundidade = 0
basic.forever(function () {
    profundidade = Math.round(Math.map(sensors.infraredValue(InputPorts.P1), 0, 1023, 0, 250))
    if (sensors.buttonValue(InputPorts.P2) == 0) {
        if (profundidade > 200) {
        	
        } else if (false) {
        	
        } else if (false) {
        	
        } else {
        	
        }
    } else {
    	
    }
})
```

## Passo 13

Copie e cole duas vezes o comparador ``||logic:profundidade > 200||`` e altere 
as duas condicionais seguintes ``||logic:falso||`` utilizando os 
valores após o sinal de **100** e **50** respectivamente.

```blocks
let profundidade = 0
basic.forever(function () {
    profundidade = Math.round(Math.map(sensors.infraredValue(InputPorts.P1), 0, 1023, 0, 250))
    if (sensors.buttonValue(InputPorts.P2) == 0) {
        if (profundidade > 200) {
        	
        } else if (profundidade > 100) {
        	
        } else if (profundidade > 50) {
        	
        } else {
        	
        }
    } else {
    	
    }
})

```
## Passo 14

Acesse a categoria ``||basic:Básico||``, preencha as quatro condições com o bloco ``||basic:mostrar string "Hello"||``.

```blocks
let profundidade = 0
basic.forever(function () {
    profundidade = Math.round(Math.map(sensors.infraredValue(InputPorts.P1), 0, 1023, 0, 250))
    if (sensors.buttonValue(InputPorts.P2) == 0) {
        if (profundidade > 200) {
            basic.showString("Hello!")
        } else if (profundidade > 100) {
            basic.showString("Hello!")
        } else if (profundidade > 50) {
            basic.showString("Hello!")
        } else {
            basic.showString("Hello!")
        }
    } else {
    	
    }
})
```

## Passo 15

Edite os textos para os nomes dos minérios na sequência: "cobre", "ferro", "ouro" e "bauxita".

```blocks
let profundidade = 0
basic.forever(function () {
    profundidade = Math.round(Math.map(sensors.infraredValue(InputPorts.P1), 0, 1023, 0, 250))
    if (sensors.buttonValue(InputPorts.P2) == 0) {
        if (profundidade > 200) {
            basic.showString("cobre")
        } else if (profundidade > 100) {
            basic.showString("ferro")
        } else if (profundidade > 50) {
            basic.showString("ouro")
        } else {
            basic.showString("bauxita")
        }
    } else {
    	
    }
})
```

## Passo 16

Dentro do ``||logic:senão||`` do bloco maior, coloque um comando ``||basic:mostrar número 0||`` direto do menu ``||basic:Básico||``.
Mude o valor do número para a variável ``||variables:profundidade||``.


```blocks
let profundidade = 0
basic.forever(function () {
    profundidade = Math.round(Math.map(sensors.infraredValue(InputPorts.P1), 0, 1023, 0, 250))
    if (sensors.buttonValue(InputPorts.P2) == 0) {
        if (profundidade > 200) {
            basic.showString("cobre")
        } else if (profundidade > 100) {
            basic.showString("ferro")
        } else if (profundidade > 50) {
            basic.showString("ouro")
        } else {
            basic.showString("bauxita")
        }
    } else {
        basic.showNumber(profundidade)
    }
})
```

## Passo 17

Vá até o menu ``||basic:Básico||`` e puxe outro laço ``||basic:sempre||`` para a área de programação. 

```blocks
let profundidade = 0
basic.forever(function () {
    profundidade = Math.round(Math.map(sensors.infraredValue(InputPorts.P1), 0, 1023, 0, 250))
    if (sensors.buttonValue(InputPorts.P2) == 0) {
        if (profundidade > 200) {
            basic.showString("cobre")
        } else if (profundidade > 100) {
            basic.showString("ferro")
        } else if (profundidade > 50) {
            basic.showString("ouro")
        } else {
            basic.showString("bauxita")
        }
    } else {
        basic.showNumber(profundidade)
    }
})
basic.forever(function () {
	
})

```

## Passo 18
Acesse a categoria ``||logic:Lógica||``, pegue a condicional ``||logic:se então senão||``
e insira-a dentro do bloco ``||basic:sempre||`` ainda vazio. 
Clique no botão **+** para criar mais uma condição.

```blocks
let profundidade = 0
basic.forever(function () {
    profundidade = Math.round(Math.map(sensors.infraredValue(InputPorts.P1), 0, 1023, 0, 250))
    if (sensors.buttonValue(InputPorts.P2) == 0) {
        if (profundidade > 200) {
            basic.showString("cobre")
        } else if (profundidade > 100) {
            basic.showString("ferro")
        } else if (profundidade > 50) {
            basic.showString("ouro")
        } else {
            basic.showString("bauxita")
        }
    } else {
        basic.showNumber(profundidade)
    }
})
basic.forever(function () {
    if (true) {
    	
    } else if (false) {
    	
    } else {
    	
    }
})
```

## Passo 19

Na aba ``||input:Entrada||`` clique em **dois** blocos ``||input:botão A é pressionado||``, 
substitua as condições ``||logic:verdadeiro||`` e ``||logic:falso||`` pelos
blocos, altere a segunda condição para ``||input:botão B é pressionado||``.

```blocks
let profundidade = 0
basic.forever(function () {
    profundidade = Math.round(Math.map(sensors.infraredValue(InputPorts.P1), 0, 1023, 0, 250))
    if (sensors.buttonValue(InputPorts.P2) == 0) {
        if (profundidade > 200) {
            basic.showString("cobre")
        } else if (profundidade > 100) {
            basic.showString("ferro")
        } else if (profundidade > 50) {
            basic.showString("ouro")
        } else {
            basic.showString("bauxita")
        }
    } else {
        basic.showNumber(profundidade)
    }
})
basic.forever(function () {
    if (input.buttonIsPressed(Button.A)) {
    	
    } else if (input.buttonIsPressed(Button.B)) {
    	
    } else {
    	
    }
})

```
## Passo 20
Acesse o menu ``||actuators:Atuadores||``, adicione os blocos
``||actuators:Motor CC, definir velocidade 0 na porta P8||``
e ``||actuators:Motor CC, definir direção para Sentido horário na porta P8||``
dentro do ``||logic:se botão A é pressionado então||``.

```blocks
let profundidade = 0
basic.forever(function () {
    profundidade = Math.round(Math.map(sensors.infraredValue(InputPorts.P1), 0, 1023, 0, 250))
    if (sensors.buttonValue(InputPorts.P2) == 0) {
        if (profundidade > 200) {
            basic.showString("cobre")
        } else if (profundidade > 100) {
            basic.showString("ferro")
        } else if (profundidade > 50) {
            basic.showString("ouro")
        } else {
            basic.showString("bauxita")
        }
    } else {
        basic.showNumber(profundidade)
    }
})
basic.forever(function () {
    if (input.buttonIsPressed(Button.A)) {
        actuators.SetSpeedMotor(0, OutputPorts.P8)
        actuators.SetDirectionMotor(MotorDirection.clockwise, OutputPorts.P8)
    } else if (input.buttonIsPressed(Button.B)) {
    	
    } else {
    	
    }
})

```

## Passo 21

Modifique a velocidade do primeiro bloco para **1023** e a porta para ``||actuators:P16||``.
Selecione o sentido ``||actuators:anti-horário||``, no segundo bloco e a porta ``||actuators:P12||``.


```blocks
let profundidade = 0
basic.forever(function () {
    profundidade = Math.round(Math.map(sensors.infraredValue(InputPorts.P1), 0, 1023, 0, 250))
    if (sensors.buttonValue(InputPorts.P2) == 0) {
        if (profundidade > 200) {
            basic.showString("cobre")
        } else if (profundidade > 100) {
            basic.showString("ferro")
        } else if (profundidade > 50) {
            basic.showString("ouro")
        } else {
            basic.showString("bauxita")
        }
    } else {
        basic.showNumber(profundidade)
    }
})
basic.forever(function () {
    if (input.buttonIsPressed(Button.A)) {
        actuators.SetSpeedMotor(1023, OutputPorts.P16)
        actuators.SetDirectionMotor(MotorDirection.antiClockwise, OutputPorts.P12)
    } else if (input.buttonIsPressed(Button.B)) {
    	
    } else {
    	
    }
})
```

## Passo 22
Duplique os blocos que definem a velocidade e orientação do motor no ``||logic:se botão A é pressionado então||``
e coloque as cópias dentro da condição ``||logic:senão se botão B é pressionado então||``. 
Altere o sentido de ``||actuators:anti-horário||`` para  ``||actuators:horário||``.

```blocks
let profundidade = 0
basic.forever(function () {
    profundidade = Math.round(Math.map(sensors.infraredValue(InputPorts.P1), 0, 1023, 0, 250))
    if (sensors.buttonValue(InputPorts.P2) == 0) {
        if (profundidade > 200) {
            basic.showString("cobre")
        } else if (profundidade > 100) {
            basic.showString("ferro")
        } else if (profundidade > 50) {
            basic.showString("ouro")
        } else {
            basic.showString("bauxita")
        }
    } else {
        basic.showNumber(profundidade)
    }
})
basic.forever(function () {
    if (input.buttonIsPressed(Button.A)) {
        actuators.SetSpeedMotor(1023, OutputPorts.P16)
        actuators.SetDirectionMotor(MotorDirection.antiClockwise, OutputPorts.P12)
    } else if (input.buttonIsPressed(Button.B)) {
        actuators.SetSpeedMotor(1023, OutputPorts.P16)
        actuators.SetDirectionMotor(MotorDirection.clockwise, OutputPorts.P12)
    } else {
    	
    }
})
```

## Passo 23
Acesse o menu ``||actuators:Atuadores||`` e arraste o bloco
``||actuators:Motor CC, parar na porta P8||``
para dentro do ``||logic:senão||``. Mude a porta de ``||actuators:P8||`` para  ``||actuators:P16||``.

```blocks
let profundidade = 0
basic.forever(function () {
    profundidade = Math.round(Math.map(sensors.infraredValue(InputPorts.P1), 0, 1023, 0, 250))
    if (sensors.buttonValue(InputPorts.P2) == 0) {
        if (profundidade > 200) {
            basic.showString("cobre")
        } else if (profundidade > 100) {
            basic.showString("ferro")
        } else if (profundidade > 50) {
            basic.showString("ouro")
        } else {
            basic.showString("bauxita")
        }
    } else {
        basic.showNumber(profundidade)
    }
})
basic.forever(function () {
    if (input.buttonIsPressed(Button.A)) {
        actuators.SetSpeedMotor(1023, OutputPorts.P16)
        actuators.SetDirectionMotor(MotorDirection.antiClockwise, OutputPorts.P12)
    } else if (input.buttonIsPressed(Button.B)) {
        actuators.SetSpeedMotor(1023, OutputPorts.P16)
        actuators.SetDirectionMotor(MotorDirection.clockwise, OutputPorts.P12)
    } else {
        actuators.StopMotor(OutputPorts.P16)
    }
})
```

## Passo 24
No menu ``||input:Entrada||`` busque o bloco ``||input:no logotipo pressionado||`` e adicione-o
à área de programação. 
```blocks
let profundidade = 0
input.onLogoEvent(TouchButtonEvent.Pressed, function () {
	
})
basic.forever(function () {
    profundidade = Math.round(Math.map(sensors.infraredValue(InputPorts.P1), 0, 1023, 0, 250))
    if (sensors.buttonValue(InputPorts.P2) == 0) {
        if (profundidade > 200) {
            basic.showString("cobre")
        } else if (profundidade > 100) {
            basic.showString("ferro")
        } else if (profundidade > 50) {
            basic.showString("ouro")
        } else {
            basic.showString("bauxita")
        }
    } else {
        basic.showNumber(profundidade)
    }
})
basic.forever(function () {
    if (input.buttonIsPressed(Button.A)) {
        actuators.SetSpeedMotor(1023, OutputPorts.P16)
        actuators.SetDirectionMotor(MotorDirection.antiClockwise, OutputPorts.P12)
    } else if (input.buttonIsPressed(Button.B)) {
        actuators.SetSpeedMotor(1023, OutputPorts.P16)
        actuators.SetDirectionMotor(MotorDirection.clockwise, OutputPorts.P12)
    } else {
        actuators.StopMotor(OutputPorts.P16)
    }
})
```

## Passo 25

Acesse a categoria ``||logic:Lógica||``, clique na condicional ``||logic:se então senão||``
e insira-a dentro de ``||input:no logotipo pressionado||``.

```blocks
let profundidade = 0
input.onLogoEvent(TouchButtonEvent.Pressed, function () {
    if (true) {
    	
    } else {
    	
    }
})
basic.forever(function () {
    profundidade = Math.round(Math.map(sensors.infraredValue(InputPorts.P1), 0, 1023, 0, 250))
    if (sensors.buttonValue(InputPorts.P2) == 0) {
        if (profundidade > 200) {
            basic.showString("cobre")
        } else if (profundidade > 100) {
            basic.showString("ferro")
        } else if (profundidade > 50) {
            basic.showString("ouro")
        } else {
            basic.showString("bauxita")
        }
    } else {
        basic.showNumber(profundidade)
    }
})
basic.forever(function () {
    if (input.buttonIsPressed(Button.A)) {
        actuators.SetSpeedMotor(1023, OutputPorts.P16)
        actuators.SetDirectionMotor(MotorDirection.antiClockwise, OutputPorts.P12)
    } else if (input.buttonIsPressed(Button.B)) {
        actuators.SetSpeedMotor(1023, OutputPorts.P16)
        actuators.SetDirectionMotor(MotorDirection.clockwise, OutputPorts.P12)
    } else {
        actuators.StopMotor(OutputPorts.P16)
    }
})
```

## Passo 26
Agora atualize os campos do comparador.
Acesse o menu ``||variables:Variáveis||`` e clique em 
**"Fazer uma variável..."**. Crie uma variável chamada
``||variables:broca||``. Substitua o primeiro valor do comparador pela variável criada.


```blocks
let broca = 0
let profundidade = 0
input.onLogoEvent(TouchButtonEvent.Pressed, function () {
    if (broca == 0) {
    	
    } else {
    	
    }
})
basic.forever(function () {
    profundidade = Math.round(Math.map(sensors.infraredValue(InputPorts.P1), 0, 1023, 0, 250))
    if (sensors.buttonValue(InputPorts.P2) == 0) {
        if (profundidade > 200) {
            basic.showString("cobre")
        } else if (profundidade > 100) {
            basic.showString("ferro")
        } else if (profundidade > 50) {
            basic.showString("ouro")
        } else {
            basic.showString("bauxita")
        }
    } else {
        basic.showNumber(profundidade)
    }
})
basic.forever(function () {
    if (input.buttonIsPressed(Button.A)) {
        actuators.SetSpeedMotor(1023, OutputPorts.P16)
        actuators.SetDirectionMotor(MotorDirection.antiClockwise, OutputPorts.P12)
    } else if (input.buttonIsPressed(Button.B)) {
        actuators.SetSpeedMotor(1023, OutputPorts.P16)
        actuators.SetDirectionMotor(MotorDirection.clockwise, OutputPorts.P12)
    } else {
        actuators.StopMotor(OutputPorts.P16)
    }
})
```


## Passo 27
Volte à aba ``||variables:Variáveis||`` e busque o comando  ``||variables:definir broca para 0||``
para usá-lo dentro da condição ``||logic:se broca = 0 então||``.
Modifique o valor de ``||variables:broca||`` para **1**.

```blocks
let broca = 0
let profundidade = 0
input.onLogoEvent(TouchButtonEvent.Pressed, function () {
    if (broca == 0) {
        broca = 1
    } else {
    	
    }
})
basic.forever(function () {
    profundidade = Math.round(Math.map(sensors.infraredValue(InputPorts.P1), 0, 1023, 0, 250))
    if (sensors.buttonValue(InputPorts.P2) == 0) {
        if (profundidade > 200) {
            basic.showString("cobre")
        } else if (profundidade > 100) {
            basic.showString("ferro")
        } else if (profundidade > 50) {
            basic.showString("ouro")
        } else {
            basic.showString("bauxita")
        }
    } else {
        basic.showNumber(profundidade)
    }
})
basic.forever(function () {
    if (input.buttonIsPressed(Button.A)) {
        actuators.SetSpeedMotor(1023, OutputPorts.P16)
        actuators.SetDirectionMotor(MotorDirection.antiClockwise, OutputPorts.P12)
    } else if (input.buttonIsPressed(Button.B)) {
        actuators.SetSpeedMotor(1023, OutputPorts.P16)
        actuators.SetDirectionMotor(MotorDirection.clockwise, OutputPorts.P12)
    } else {
        actuators.StopMotor(OutputPorts.P16)
    }
})
```

## Passo 28

Acesse a aba ``||actuators:Atuadores||`` e adicione o bloco
``||actuators:Motor CC, definir velocidade 0 na porta P8||`` abaixo do último bloco adicionado.
Modifique a velocidade para **1023**.

```blocks
let broca = 0
let profundidade = 0
input.onLogoEvent(TouchButtonEvent.Pressed, function () {
    if (broca == 0) {
        broca = 1
        actuators.SetSpeedMotor(1023, OutputPorts.P8)
    } else {
    	
    }
})
basic.forever(function () {
    profundidade = Math.round(Math.map(sensors.infraredValue(InputPorts.P1), 0, 1023, 0, 250))
    if (sensors.buttonValue(InputPorts.P2) == 0) {
        if (profundidade > 200) {
            basic.showString("cobre")
        } else if (profundidade > 100) {
            basic.showString("ferro")
        } else if (profundidade > 50) {
            basic.showString("ouro")
        } else {
            basic.showString("bauxita")
        }
    } else {
        basic.showNumber(profundidade)
    }
})
basic.forever(function () {
    if (input.buttonIsPressed(Button.A)) {
        actuators.SetSpeedMotor(1023, OutputPorts.P16)
        actuators.SetDirectionMotor(MotorDirection.antiClockwise, OutputPorts.P12)
    } else if (input.buttonIsPressed(Button.B)) {
        actuators.SetSpeedMotor(1023, OutputPorts.P16)
        actuators.SetDirectionMotor(MotorDirection.clockwise, OutputPorts.P12)
    } else {
        actuators.StopMotor(OutputPorts.P16)
    }
})
```
## Passo 29

Acesse o menu ``||variables:Variáveis||``, pegue o comando ``||variables:definir broca para 0||``
e use-o dentro do ``||logic:senão||``.

```blocks
let broca = 0
let profundidade = 0
input.onLogoEvent(TouchButtonEvent.Pressed, function () {
    if (broca == 0) {
        broca = 1
        actuators.SetSpeedMotor(1023, OutputPorts.P8)
    } else {
        broca = 0
    }
})
basic.forever(function () {
    profundidade = Math.round(Math.map(sensors.infraredValue(InputPorts.P1), 0, 1023, 0, 250))
    if (sensors.buttonValue(InputPorts.P2) == 0) {
        if (profundidade > 200) {
            basic.showString("cobre")
        } else if (profundidade > 100) {
            basic.showString("ferro")
        } else if (profundidade > 50) {
            basic.showString("ouro")
        } else {
            basic.showString("bauxita")
        }
    } else {
        basic.showNumber(profundidade)
    }
})
basic.forever(function () {
    if (input.buttonIsPressed(Button.A)) {
        actuators.SetSpeedMotor(1023, OutputPorts.P16)
        actuators.SetDirectionMotor(MotorDirection.antiClockwise, OutputPorts.P12)
    } else if (input.buttonIsPressed(Button.B)) {
        actuators.SetSpeedMotor(1023, OutputPorts.P16)
        actuators.SetDirectionMotor(MotorDirection.clockwise, OutputPorts.P12)
    } else {
        actuators.StopMotor(OutputPorts.P16)
    }
})

```

## Passo 30

Volte para a aba ``||actuators:Atuadores||``, busque o comando ``||actuators:Motor CC, parar motor na porta P8||``
e coloque-o no fim da condicional.
```blocks
let broca = 0
let profundidade = 0
input.onLogoEvent(TouchButtonEvent.Pressed, function () {
    if (broca == 0) {
        broca = 1
        actuators.SetSpeedMotor(1023, OutputPorts.P8)
    } else {
        broca = 0
        actuators.StopMotor(OutputPorts.P8)
    }
})
basic.forever(function () {
    profundidade = Math.round(Math.map(sensors.infraredValue(InputPorts.P1), 0, 1023, 0, 250))
    if (sensors.buttonValue(InputPorts.P2) == 0) {
        if (profundidade > 200) {
            basic.showString("cobre")
        } else if (profundidade > 100) {
            basic.showString("ferro")
        } else if (profundidade > 50) {
            basic.showString("ouro")
        } else {
            basic.showString("bauxita")
        }
    } else {
        basic.showNumber(profundidade)
    }
})
basic.forever(function () {
    if (input.buttonIsPressed(Button.A)) {
        actuators.SetSpeedMotor(1023, OutputPorts.P16)
        actuators.SetDirectionMotor(MotorDirection.antiClockwise, OutputPorts.P12)
    } else if (input.buttonIsPressed(Button.B)) {
        actuators.SetSpeedMotor(1023, OutputPorts.P16)
        actuators.SetDirectionMotor(MotorDirection.clockwise, OutputPorts.P12)
    } else {
        actuators.StopMotor(OutputPorts.P16)
    }
})

```
## Passo 31

Agora seu código está pronto! Baixe-o para o micro:bit e teste-o. Use os botões A e B do micro:bit para avançar e recuar a broca,
com a broca posicionada, ao pressionar o logotipo, será iniciada a perfuração. Alterne o clique sobre o Bit Botão para observar a profundidade e o minério extraído no display.
```blocks
```


## Passo 32
Se necessário, confira o seu código clicando na lâmpada de dica.

```blocks
let broca = 0
let profundidade = 0
input.onLogoEvent(TouchButtonEvent.Pressed, function () {
    if (broca == 0) {
        broca = 1
        actuators.SetSpeedMotor(1023, OutputPorts.P8)
    } else {
        broca = 0
        actuators.StopMotor(OutputPorts.P8)
    }
})
basic.forever(function () {
    profundidade = Math.round(Math.map(sensors.infraredValue(InputPorts.P1), 0, 1023, 0, 250))
    if (sensors.buttonValue(InputPorts.P2) == 0) {
        if (profundidade > 200) {
            basic.showString("cobre")
        } else if (profundidade > 100) {
            basic.showString("ferro")
        } else if (profundidade > 50) {
            basic.showString("ouro")
        } else {
            basic.showString("bauxita")
        }
    } else {
        basic.showNumber(profundidade)
    }
})
basic.forever(function () {
    if (input.buttonIsPressed(Button.A)) {
        actuators.SetSpeedMotor(1023, OutputPorts.P16)
        actuators.SetDirectionMotor(MotorDirection.antiClockwise, OutputPorts.P12)
    } else if (input.buttonIsPressed(Button.B)) {
        actuators.SetSpeedMotor(1023, OutputPorts.P16)
        actuators.SetDirectionMotor(MotorDirection.clockwise, OutputPorts.P12)
    } else {
        actuators.StopMotor(OutputPorts.P16)
    }
})


```



```package
fuzzyBot=github:FuzzyMakers/pxt-fuzzyMakers
```
