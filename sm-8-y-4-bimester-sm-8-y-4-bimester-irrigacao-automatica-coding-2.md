### @diffs true
# Moenda

## Passo 1
Neste tutorial, vamos programar uma moenda que tem sua abertura controlada por um potenciômetro; 
quando o controle de entrada de cana está fechado e há material na máquina, o motor é acionado e a moagem iniciada. Pode-se armazenar
a quantidade de insumos utilizados e produtos extraídos. 
## Passo 2
Para começar, verifique se a biblioteca da Smart Makers já está importada 
em seu MakeCode. Se não estiver, clique na aba **+ Extensões**, 
copie o endereço "https://github.com/FuzzyMakers/pxt-smartMakers",
cole-o no campo de pesquisa da janela que se abriu e selecione a biblioteca.

## Passo 3
Acesse o menu ``||variables:Variáveis||`` e clique em 
**"Fazer uma variável..."**. Crie uma variável chamada
``||variables:total||``. Em seguida, arraste o bloco ``||variables:definir total para 0||`` 
para o bloco ``||basic:no iniciar||``.

```blocks
let total = 0
```


## Passo 4
Refaça o mesmo processo anterior para criar e definir mais duas variáveis: ``||variables:etanol||`` e ``||variables:açúcar||``, 
porém define-as no laço ``||basic:sempre||``.

```blocks
let etanol = 0
let açúcar = 0
let total = 0
basic.forever(function () {
    açúcar = 0
    etanol = 0
})


```


## Passo 5

Vá à categoria ``||math:Matemática||``, pegue duas operações multiplicação ``||math:0 x 0||``
e substitua o valor **0** da definição das variáveis **açúcar** e **etanol**.
```blocks
let etanol = 0
let açúcar = 0
let total = 0
basic.forever(function () {
    açúcar = 0 * 0
    etanol = 0 * 0
})
```

## Passo 6
Agora atualize os campos das multiplicações. Defina ``||variables:açúcar||`` para ser o produto 
entre a variável ``||variables:total||`` e o valor **120**. Depois, defina ``||variables:etanol||`` para ser o produto 
entre a variável ``||variables:total||`` e o valor **25**.


```blocks
let etanol = 0
let açúcar = 0
let total = 0
basic.forever(function () {
    açúcar = total * 120
    etanol = total * 25
})
```

## Passo 7
No menu ``||input:Entrada||``, busque o bloco ``||input:no logotipo pressionado||`` e adicione-o
à área de programação.

```blocks
input.onLogoEvent(TouchButtonEvent.Pressed, function () {
	
})
let etanol = 0
let açúcar = 0
let total = 0
basic.forever(function () {
    açúcar = total * 120
    etanol = total * 25
})
```


## Passo 8

Clique no menu ``||Advanced:Avançado||``, acesse ``||serial:Serial||`` e 
insira **três** blocos ``||serial:serial gravar linha ""||`` 
no comando ``||input:no logotipo pressionado||``.

```blocks
input.onLogoEvent(TouchButtonEvent.Pressed, function () {
    serial.writeLine("")
    serial.writeLine("")
    serial.writeLine("")
})
let etanol = 0
let açúcar = 0
let total = 0
basic.forever(function () {
    açúcar = total * 120
    etanol = total * 25
})
```

## Passo 9
Clique no menu ``||Advanced:Avançado||``, acesse ``||text:Texto||`` e 
busque **três** blocos ``||text:unir Olá Mundo - +||`` para substituir
os campos **""** do registro de linha serial.

```blocks
input.onLogoEvent(TouchButtonEvent.Pressed, function () {
    serial.writeLine("Olá" + "Mundo")
    serial.writeLine("Olá" + "Mundo")
    serial.writeLine("Olá" + "Mundo")
})
let etanol = 0
let açúcar = 0
let total = 0
basic.forever(function () {
    açúcar = total * 120
    etanol = total * 25
})
```

## Passo 10
Clique no botão **+** do texto ``||text:unir Olá Mundo - +||`` para adicionar um campo de texto
dentro de cada bloco.

```blocks
input.onLogoEvent(TouchButtonEvent.Pressed, function () {
    serial.writeLine("Olá" + "Mundo" + "")
    serial.writeLine("Olá" + "Mundo" + "")
    serial.writeLine("Olá" + "Mundo" + "")
})
let etanol = 0
let açúcar = 0
let total = 0
basic.forever(function () {
    açúcar = total * 120
    etanol = total * 25
})
```


## Passo 11

Em seguida, atualize os campos de texto para nossa aplicação:
O primeiro bloco deve registrar **"total de cana: "** ``||variables:total||`` **" toneladas"**,
o segundo  deve registrar **"açúcar: "** ``||variables:açúcar||`` **" kg"** e o 
terceiro deve registrar **"etanol: "** ``||variables:etanol||`` **" litros"**.


```blocks
input.onLogoEvent(TouchButtonEvent.Pressed, function () {
    serial.writeLine("total de cana: " + total + " toneladas")
    serial.writeLine("açúcar: " + açúcar + " kg")
    serial.writeLine("etanol: " + etanol + " litros")
})
let etanol = 0
let açúcar = 0
let total = 0
total = 0
basic.forever(function () {
    açúcar = total * 120
    etanol = total * 25
})
```

## Passo 12

Clique no menu ``||Advanced:Avançado||``, acesse ``||Functions:Funções||`` e 
clique em **Fazer uma função...**.
Clique no campo editável do laço azul para criar uma função chamada 
``||functions:parar||``. 
Um novo laço referente à função criada é adicionado automaticamente à área de programação.

```blocks
input.onLogoEvent(TouchButtonEvent.Pressed, function () {
    serial.writeLine("total de cana: " + total + " toneladas")
    serial.writeLine("açúcar: " + açúcar + " kg")
    serial.writeLine("etanol: " + etanol + " litros")
})
function parar () {
	
}
let etanol = 0
let açúcar = 0
let total = 0
total = 0
basic.forever(function () {
    açúcar = total * 120
    etanol = total * 25
})


```

## Passo 13

Acesse a aba ``||actuators:Atuadores||`` e adicione o bloco
``||actuators:Motor CC, parar motor na porta P8||`` dentro da função ``||functions: parar||``.
Modifique a porta de ``||actuators:P8||`` para ``||actuators:P16||``.

```blocks
input.onLogoEvent(TouchButtonEvent.Pressed, function () {
    serial.writeLine("total de cana: " + total + " toneladas")
    serial.writeLine("açúcar: " + açúcar + " kg")
    serial.writeLine("etanol: " + etanol + " litros")
})
function parar () {
    actuators.StopMotor(OutputPorts.P16)
}
let etanol = 0
let açúcar = 0
let total = 0
total = 0
basic.forever(function () {
    açúcar = total * 120
    etanol = total * 25
})
```
## Passo 14

Clique no menu ``||Advanced:Avançado||``, acesse ``||Functions:Funções||`` e 
clique em **Fazer uma função...**.
Clique no campo editável do laço azul para criar uma função chamada 
``||functions:moer||``. 
Um novo laço referente à função criada é adicionado automaticamente à área de programação.

```blocks
input.onLogoEvent(TouchButtonEvent.Pressed, function () {
    serial.writeLine("total de cana: " + total + " toneladas")
    serial.writeLine("açúcar: " + açúcar + " kg")
    serial.writeLine("etanol: " + etanol + " litros")
})
function parar () {
    actuators.StopMotor(OutputPorts.P16)
}
function moer () {
	
}
let etanol = 0
let açúcar = 0
let total = 0
total = 0
basic.forever(function () {
    açúcar = total * 120
    etanol = total * 25
})
```

## Passo 15

Acesse a aba ``||actuators:Atuadores||`` e adicione o bloco
``||actuators:Motor CC, definir velocidade 0 na porta P8||`` dentro da função ``||functions:moer||``.
Modifique a porta de ``||actuators:P8||`` para ``||actuators:P16||`` e a velocidade para **1023**.

```blocks
input.onLogoEvent(TouchButtonEvent.Pressed, function () {
    serial.writeLine("total de cana: " + total + " toneladas")
    serial.writeLine("açúcar: " + açúcar + " kg")
    serial.writeLine("etanol: " + etanol + " litros")
})
function parar () {
    actuators.StopMotor(OutputPorts.P16)
}
function moer () {
    actuators.SetSpeedMotor(1023, OutputPorts.P16)
}
let etanol = 0
let açúcar = 0
let total = 0
total = 0
basic.forever(function () {
    açúcar = total * 120
    etanol = total * 25
})
```

## Passo 16

Na categoria ``||basic:Básico||`` arraste uma pausa ``||basic:pausa (ms) 100||`` para a função,
depois mude seu valor para **500**.

```blocks
input.onLogoEvent(TouchButtonEvent.Pressed, function () {
    serial.writeLine("total de cana: " + total + " toneladas")
    serial.writeLine("açúcar: " + açúcar + " kg")
    serial.writeLine("etanol: " + etanol + " litros")
})
function parar () {
    actuators.StopMotor(OutputPorts.P16)
}
function moer () {
    actuators.SetSpeedMotor(1023, OutputPorts.P16)
    basic.pause(500)
}
let etanol = 0
let açúcar = 0
let total = 0
total = 0
basic.forever(function () {
    açúcar = total * 120
    etanol = total * 25
})


```

## Passo 17

Na categoria ``||variables:Variáveis||``, selecione o bloco ``||variables:alterar total por 1||``
e posicione-o no final da função ``||functions:moer||``.
Mude o incremento da variável de **1** para **2**.
```blocks
input.onLogoEvent(TouchButtonEvent.Pressed, function () {
    serial.writeLine("total de cana: " + total + " toneladas")
    serial.writeLine("açúcar: " + açúcar + " kg")
    serial.writeLine("etanol: " + etanol + " litros")
})
function parar () {
    actuators.StopMotor(OutputPorts.P16)
}
function moer () {
    actuators.SetSpeedMotor(1023, OutputPorts.P16)
    basic.pause(500)
    total += 2
}
let etanol = 0
let açúcar = 0
let total = 0
total = 0
basic.forever(function () {
    açúcar = total * 120
    etanol = total * 25
})
```

## Passo 18
Vá até o menu ``||basic:Básico||`` e acrescente outro laço ``||basic:sempre||`` na área de programação. 

```blocks
input.onLogoEvent(TouchButtonEvent.Pressed, function () {
    serial.writeLine("total de cana: " + total + " toneladas")
    serial.writeLine("açúcar: " + açúcar + " kg")
    serial.writeLine("etanol: " + etanol + " litros")
})
function parar () {
    actuators.StopMotor(OutputPorts.P16)
}
function moer () {
    actuators.SetSpeedMotor(1023, OutputPorts.P16)
    basic.pause(500)
    total += 2
}
let etanol = 0
let açúcar = 0
let total = 0
total = 0
basic.forever(function () {
    açúcar = total * 120
    etanol = total * 25
})
basic.forever(function () {
	
})

```

## Passo 19

Acesse a categoria ``||actuators:Atuadores||`` e adicione um comando 
``||actuators:Servo definir posição 0 porta P8 modo knob||`` dentro do laço ``||basic:sempre||``.

```blocks
input.onLogoEvent(TouchButtonEvent.Pressed, function () {
    serial.writeLine("total de cana: " + total + " toneladas")
    serial.writeLine("açúcar: " + açúcar + " kg")
    serial.writeLine("etanol: " + etanol + " litros")
})
function parar () {
    actuators.StopMotor(OutputPorts.P16)
}
function moer () {
    actuators.SetSpeedMotor(1023, OutputPorts.P16)
    basic.pause(500)
    total += 2
}
let etanol = 0
let açúcar = 0
let total = 0
total = 0
basic.forever(function () {
    açúcar = total * 120
    etanol = total * 25
})
basic.forever(function () {
    actuators.SetAngleServoKnob(0, OutputPorts.P8)
})


```
## Passo 20
Mude a porta para ``||actuators:P12||`` e substitua o valor **0** da posição por uma
operação ``||math:0 / 0||`` retirada da categoria ``||math:Matemática||``.

```blocks
input.onLogoEvent(TouchButtonEvent.Pressed, function () {
    serial.writeLine("total de cana: " + total + " toneladas")
    serial.writeLine("açúcar: " + açúcar + " kg")
    serial.writeLine("etanol: " + etanol + " litros")
})
function parar () {
    actuators.StopMotor(OutputPorts.P16)
}
function moer () {
    actuators.SetSpeedMotor(1023, OutputPorts.P16)
    basic.pause(500)
    total += 2
}
let etanol = 0
let açúcar = 0
let total = 0
total = 0
basic.forever(function () {
    açúcar = total * 120
    etanol = total * 25
})
basic.forever(function () {
    actuators.SetAngleServoKnob(0 / 0, OutputPorts.P12)
})
```

## Passo 21

Agora devemos atualizar o dividendo e o divisor da operação. 
Para isso, acesse a categoria ``||sensors:Sensores||`` e atualize o primeiro campo da divisão com
o bloco ``||sensors:Valor do potenciômetro na porta P2||``. 
Altere a porta de ``||sensors:P2||`` para ``||sensors:P1||``.
O segundo campo da divisão passará a ser o número **2**.


```blocks
input.onLogoEvent(TouchButtonEvent.Pressed, function () {
    serial.writeLine("total de cana: " + total + " toneladas")
    serial.writeLine("açúcar: " + açúcar + " kg")
    serial.writeLine("etanol: " + etanol + " litros")
})
function parar () {
    actuators.StopMotor(OutputPorts.P16)
}
function moer () {
    actuators.SetSpeedMotor(1023, OutputPorts.P16)
    basic.pause(500)
    total += 2
}
let etanol = 0
let açúcar = 0
let total = 0
total = 0
basic.forever(function () {
    açúcar = total * 120
    etanol = total * 25
})
basic.forever(function () {
    actuators.SetAngleServoKnob(sensors.dimmerValue(InputPorts.P1) / 2, OutputPorts.P12)
})
```

## Passo 22
Acesse a categoria ``||logic:Lógica||``, clique na condicional ``||logic:se então senão||``
e insira-a abaixo do bloco anterior.

```blocks
input.onLogoEvent(TouchButtonEvent.Pressed, function () {
    serial.writeLine("total de cana: " + total + " toneladas")
    serial.writeLine("açúcar: " + açúcar + " kg")
    serial.writeLine("etanol: " + etanol + " litros")
})
function parar () {
    actuators.StopMotor(OutputPorts.P16)
}
function moer () {
    actuators.SetSpeedMotor(1023, OutputPorts.P16)
    basic.pause(500)
    total += 2
}
let etanol = 0
let açúcar = 0
let total = 0
total = 0
basic.forever(function () {
    açúcar = total * 120
    etanol = total * 25
})
basic.forever(function () {
    actuators.SetAngleServoKnob(sensors.dimmerValue(InputPorts.P1) / 2, OutputPorts.P12)
    if (true) {
    	
    } else {
    	
    }
})
```
## Passo 23
Volte ao menu ``||logic:Lógica||``, selecione o operador booleano ``||logic: e ||``
e substitua a condição **verdadeiro** da condicional.

```blocks
input.onLogoEvent(TouchButtonEvent.Pressed, function () {
    serial.writeLine("total de cana: " + total + " toneladas")
    serial.writeLine("açúcar: " + açúcar + " kg")
    serial.writeLine("etanol: " + etanol + " litros")
})
function parar () {
    actuators.StopMotor(OutputPorts.P16)
}
function moer () {
    actuators.SetSpeedMotor(1023, OutputPorts.P16)
    basic.pause(500)
    total += 2
}
let etanol = 0
let açúcar = 0
let total = 0
total = 0
basic.forever(function () {
    açúcar = total * 120
    etanol = total * 25
})
basic.forever(function () {
    actuators.SetAngleServoKnob(sensors.dimmerValue(InputPorts.P1) / 2, OutputPorts.P12)
    if (false && false) {
    	
    } else {
    	
    }
})


```

## Passo 24
Ainda na categoria ``||logic:Lógica||``, pegue **dois** comparadores ``||logic: 0 < 0||``
para colocar nos campos vazios do operador booleano.
Modifique o sinal do primeiro comparador para **>=** e o do segundo para **>**.
```blocks
input.onLogoEvent(TouchButtonEvent.Pressed, function () {
    serial.writeLine("total de cana: " + total + " toneladas")
    serial.writeLine("açúcar: " + açúcar + " kg")
    serial.writeLine("etanol: " + etanol + " litros")
})
function parar () {
    actuators.StopMotor(OutputPorts.P16)
}
function moer () {
    actuators.SetSpeedMotor(1023, OutputPorts.P16)
    basic.pause(500)
    total += 2
}
let etanol = 0
let açúcar = 0
let total = 0
total = 0
basic.forever(function () {
    açúcar = total * 120
    etanol = total * 25
})
basic.forever(function () {
    actuators.SetAngleServoKnob(sensors.dimmerValue(InputPorts.P1) / 2, OutputPorts.P12)
    if (0 >= 0 && 0 > 0) {
    	
    } else {
    	
    }
})

```

## Passo 25

Agora atualize os campos dos comparadores.
Duplique o bloco ``||sensors:Valor do potenciômetro na porta P1||`` para colocá-lo no primeiro campo do primeiro comparador.
No segundo campo do primeiro comparador, use o número **512**.
Vá até a aba ``||sensors:Sensores||``,
troque o primeiro **0** do segundo comparador por ``||sensors:Valor do sensor infravermelho na porta P2||`` e o segundo por **200**.

```blocks
input.onLogoEvent(TouchButtonEvent.Pressed, function () {
    serial.writeLine("total de cana: " + total + " toneladas")
    serial.writeLine("açúcar: " + açúcar + " kg")
    serial.writeLine("etanol: " + etanol + " litros")
})
function parar () {
    actuators.StopMotor(OutputPorts.P16)
}
function moer () {
    actuators.SetSpeedMotor(1023, OutputPorts.P16)
    basic.pause(500)
    total += 2
}
let etanol = 0
let açúcar = 0
let total = 0
total = 0
basic.forever(function () {
    açúcar = total * 120
    etanol = total * 25
})
basic.forever(function () {
    actuators.SetAngleServoKnob(sensors.dimmerValue(InputPorts.P1) / 2, OutputPorts.P12)
    if (sensors.dimmerValue(InputPorts.P1) >= 512 && sensors.infraredValue(InputPorts.P2) > 200) {
    	
    } else {
    	
    }
})

```

## Passo 26
No menu ``||functions:Funções||`` arraste o comando  ``||functions:ligar moer||``
para dentro da condição ``||logic:se então||``.


```blocks
input.onLogoEvent(TouchButtonEvent.Pressed, function () {
    serial.writeLine("total de cana: " + total + " toneladas")
    serial.writeLine("açúcar: " + açúcar + " kg")
    serial.writeLine("etanol: " + etanol + " litros")
})
function parar () {
    actuators.StopMotor(OutputPorts.P16)
}
function moer () {
    actuators.SetSpeedMotor(1023, OutputPorts.P16)
    basic.pause(500)
    total += 2
}
let etanol = 0
let açúcar = 0
let total = 0
total = 0
basic.forever(function () {
    açúcar = total * 120
    etanol = total * 25
})
basic.forever(function () {
    actuators.SetAngleServoKnob(sensors.dimmerValue(InputPorts.P1) / 2, OutputPorts.P12)
    if (sensors.dimmerValue(InputPorts.P1) >= 512 && sensors.infraredValue(InputPorts.P2) > 200) {
        moer()
    } else {
    	
    }
})
```

## Passo 27
Volte à aba ``||functions:Funções||`` e busque o comando  ``||functions:ligar parar||``
para usá-lo dentro da condição ``||logic:senão||``.


```blocks
input.onLogoEvent(TouchButtonEvent.Pressed, function () {
    serial.writeLine("total de cana: " + total + " toneladas")
    serial.writeLine("açúcar: " + açúcar + " kg")
    serial.writeLine("etanol: " + etanol + " litros")
})
function parar () {
    actuators.StopMotor(OutputPorts.P16)
}
function moer () {
    actuators.SetSpeedMotor(1023, OutputPorts.P16)
    basic.pause(500)
    total += 2
}
let etanol = 0
let açúcar = 0
let total = 0
total = 0
basic.forever(function () {
    açúcar = total * 120
    etanol = total * 25
})
basic.forever(function () {
    actuators.SetAngleServoKnob(sensors.dimmerValue(InputPorts.P1) / 2, OutputPorts.P12)
    if (sensors.dimmerValue(InputPorts.P1) >= 512 && sensors.infraredValue(InputPorts.P2) > 200) {
        moer()
    } else {
        parar()
    }
})
```

## Passo 28

Agora seu código está pronto! Baixe-o para o micro:bit e teste-o.
Use o potenciômetro para fechar a entrada do material e deixe algo próximo do sensor infravermelho.
Mantenha o micro:bit conectado a porta USB para quando pressionar o logotipo
visualizar os dados na interface serial.
```blocks
```


## Passo 29
Se necessário, confira o seu código clicando na lâmpada de dica.

```blocks
input.onLogoEvent(TouchButtonEvent.Pressed, function () {
    serial.writeLine("total de cana: " + total + " toneladas")
    serial.writeLine("açúcar: " + açúcar + " kg")
    serial.writeLine("etanol: " + etanol + " litros")
})
function parar () {
    actuators.StopMotor(OutputPorts.P16)
}
function moer () {
    actuators.SetSpeedMotor(1023, OutputPorts.P16)
    basic.pause(500)
    total += 2
}
let etanol = 0
let açúcar = 0
let total = 0
total = 0
basic.forever(function () {
    açúcar = total * 120
    etanol = total * 25
})
basic.forever(function () {
    actuators.SetAngleServoKnob(sensors.dimmerValue(InputPorts.P1) / 2, OutputPorts.P12)
    if (sensors.dimmerValue(InputPorts.P1) >= 512 && sensors.infraredValue(InputPorts.P2) > 200) {
        moer()
    } else {
        parar()
    }
})
```

```package
fuzzyBot=github:FuzzyMakers/pxt-fuzzyMakers
```