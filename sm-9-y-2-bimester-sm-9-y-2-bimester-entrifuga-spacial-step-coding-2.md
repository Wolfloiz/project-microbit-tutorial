### @diffs true
# Centrífuga Espacial

## Passo 1
Nesse tutorial, vamos criar um código de programação capaz de calcular e nos
indicar a aceleração experimentada por astronautas em uma centrífuga espacial.
O potenciômetro vai definir a velocidade de rotação da centrífuga. Os botões
A e B do micro:bit serão responsáveis por selecionar o tipo de exibição dessa
aceleração: numérica ou gráfica.

## Passo 2
Para começar, verifique se a biblioteca da Smart Makers já está importada 
em seu MakeCode. Se não estiver, clique na aba **+ Extensões**, 
copie o endereço "https://github.com/FuzzyMakers/pxt-smartMakers",
cole-o no campo de pesquisa da janela que se abriu e selecione a biblioteca.

## Passo 3
Acesse a aba ``||input:Entrada||`` e adicione dois laços 
``||input:no botão A pressionado||`` em sua área de programação.
Clique na seta para alterar o botão de um deles de ``||input:botão A||`` 
para ``||input:botão B||``.

```blocks
input.onButtonPressed(Button.A, function () {
	
})
input.onButtonPressed(Button.B, function () {
	
})
```

## Passo 4
Acesse o menu ``||variables:Variáveis||`` e clique em **"Fazer uma variável..."**.
Crie uma variável chamada: ``||variables:opção||``. 
Por fim, adicione o bloco ``||variables:definir opção para 0||`` que
aparecerá ao criá-la, dentro dos laços ``||input:no botão A pressionado||``
e ``||input:no botão B pressionado||``. 

```blocks
let opção = 0
input.onButtonPressed(Button.A, function () {
    opção = 0
})
input.onButtonPressed(Button.B, function () {
    opção = 0
})
```

## Passo 5
Altere o valor de definição dessa variável de **0** para **1** dentro do laço
``||input:no botão A pressionado||``. Em seguida, modifique o valor de **0** 
para **2** dentro do outro laço ``||input:no botão B pressionado||``. 

```blocks
let opção = 0
input.onButtonPressed(Button.A, function () {
    opção = 1
})
input.onButtonPressed(Button.B, function () {
    opção = 2
})
```

## Passo 6
Acesse o menu ``||Logic:Lógica||`` e adicione um bloco ``||Logic:se então senão||`` 
dentro do ``||basic:sempre||``.

```blocks
let opção = 0
input.onButtonPressed(Button.A, function () {
    opção = 1
})
input.onButtonPressed(Button.B, function () {
    opção = 2
})
basic.forever(function () {
    if (true) {
    	
    } else {
    	
    }
})
```

## Passo 7
Retorne ao menu ``||Logic:Lógica||`` e adicione um bloco comparador 
``||Logic:0 = 0||`` para substituir o campo de bordas triangulares 
**verdadeiro** do ``||Logic:se então senão||``.

```blocks
let opção = 0
input.onButtonPressed(Button.A, function () {
    opção = 1
})
input.onButtonPressed(Button.B, function () {
    opção = 2
})
basic.forever(function () {
    if (0 == 0) {
    	
    } else {
    	
    }
})
```

## Passo 8
Acesse a aba ``||variables:Variáveis||`` e adicione o bloco 
``||variables:opção||`` no primeiro campo desse comparador.

```blocks
let opção = 0
input.onButtonPressed(Button.A, function () {
    opção = 1
})
input.onButtonPressed(Button.B, function () {
    opção = 2
})
basic.forever(function () {
    if (opção == 0) {
    	
    } else {
    	
    }
})
```

## Passo 9
Altere o segundo valor desse comparador de **0** para **1**.

```blocks
let opção = 0
input.onButtonPressed(Button.A, function () {
    opção = 1
})
input.onButtonPressed(Button.B, function () {
    opção = 2
})
basic.forever(function () {
    if (opção == 1) {
    	
    } else {
    	
    }
})
```

## Passo 10
Acesse a categoria ``||basic:Básico||`` e insira o bloco 
``||basic:mostrar número 0||`` dentro do ``||Logic:então||``.


```blocks
let opção = 0
input.onButtonPressed(Button.A, function () {
    opção = 1
})
input.onButtonPressed(Button.B, function () {
    opção = 2
})
basic.forever(function () {
    if (opção == 1) {
        basic.showNumber(0)
    } else {
    	
    }
})

```

## Passo 11
No menu ``||variables:Variáveis||``, crie outra variável chamada: 
``||variables:aceleração||``. Depois disso, adicione o bloco 
``||variables:aceleração||`` que aparecerá ao criá-la, dentro do campo  
do valor do comando ``||basic:mostrar número 0||``.

```blocks
let opção = 0
input.onButtonPressed(Button.A, function () {
    opção = 1
})
input.onButtonPressed(Button.B, function () {
    opção = 2
})
basic.forever(function () {
    if (opção == 1) {
        let aceleração = 0
        basic.showNumber(aceleração)
    } else {
    	
    }
})
```

## Passo 12
Acesse a categoria ``||led:Led||`` e adicione o bloco 
``||led:plot bar graph of 0 up to 0||`` dentro do ``||Logic:senão||``.

```blocks
let opção = 0
input.onButtonPressed(Button.A, function () {
    opção = 1
})
input.onButtonPressed(Button.B, function () {
    opção = 2
})
basic.forever(function () {
    if (opção == 1) {
        let aceleração = 0
        basic.showNumber(aceleração)
    } else {
        led.plotBarGraph(
        0,
        0
        )
    }
})
```

## Passo 13
Substitua o primeiro **0** desse bloco pela variável ``||variables:aceleração||``.
Em seguida, altere o outro **0** para **2**.

```blocks
let opção = 0
input.onButtonPressed(Button.A, function () {
    opção = 1
})
input.onButtonPressed(Button.B, function () {
    opção = 2
})
basic.forever(function () {
    let aceleração = 0
    if (opção == 1) {
        basic.showNumber(aceleração)
    } else {
        led.plotBarGraph(
        aceleração,
        2
        )
    }
})
```

## Passo 14
Volte à aba ``||basic:Básico||`` e adicione um segundo laço ``||basic:sempre||``
ao seu código.

```blocks
let opção = 0
input.onButtonPressed(Button.A, function () {
    opção = 1
})
input.onButtonPressed(Button.B, function () {
    opção = 2
})
basic.forever(function () {
    let aceleração = 0
    if (opção == 1) {
        basic.showNumber(aceleração)
    } else {
        led.plotBarGraph(
        aceleração,
        2
        )
    }
})
basic.forever(function () {
	
})
```

## Passo 15
Acesse a categoria ``||actuators:Atuadores||`` e insira o comando 
``||actuators:Motor CC, definir velocidade 0 na porta P8||`` nesse novo laço
``||basic:sempre||``.

```blocks
let opção = 0
input.onButtonPressed(Button.A, function () {
    opção = 1
})
input.onButtonPressed(Button.B, function () {
    opção = 2
})
basic.forever(function () {
    let aceleração = 0
    if (opção == 1) {
        basic.showNumber(aceleração)
    } else {
        led.plotBarGraph(
        aceleração,
        2
        )
    }
})
basic.forever(function () {
    actuators.SetSpeedMotor(0, OutputPorts.P8)
})
```

## Passo 16
Altere a porta desse bloco de ``||actuators:P8||`` para ``||actuators:P12||``.

```blocks
let opção = 0
input.onButtonPressed(Button.A, function () {
    opção = 1
})
input.onButtonPressed(Button.B, function () {
    opção = 2
})
basic.forever(function () {
    let aceleração = 0
    if (opção == 1) {
        basic.showNumber(aceleração)
    } else {
        led.plotBarGraph(
        aceleração,
        2
        )
    }
})
basic.forever(function () {
    actuators.SetSpeedMotor(0, OutputPorts.P12)
})
```

## Passo 17
Vá ao menu ``||sensors:Sensores||`` e utilize o bloco
``||sensors:Valor do potenciômetro na porta P2||`` dentro do campo para o valor
da velocidade do Motor CC. 

```blocks
let opção = 0
input.onButtonPressed(Button.A, function () {
    opção = 1
})
input.onButtonPressed(Button.B, function () {
    opção = 2
})
basic.forever(function () {
    let aceleração = 0
    if (opção == 1) {
        basic.showNumber(aceleração)
    } else {
        led.plotBarGraph(
        aceleração,
        2
        )
    }
})
basic.forever(function () {
    actuators.SetSpeedMotor(sensors.dimmerValue(InputPorts.P2), OutputPorts.P12)
})
```

## Passo 18
Volte à categoria ``||variables:Variáveis||`` e adicione o bloco
``||variables:definir aceleração para 0||`` dentro do laço ``||basic:sempre||``.

```blocks
let opção = 0
let aceleração = 0
input.onButtonPressed(Button.A, function () {
    opção = 1
})
input.onButtonPressed(Button.B, function () {
    opção = 2
})
basic.forever(function () {
    if (opção == 1) {
        basic.showNumber(aceleração)
    } else {
        led.plotBarGraph(
        aceleração,
        2
        )
    }
})
basic.forever(function () {
    actuators.SetSpeedMotor(sensors.dimmerValue(InputPorts.P2), OutputPorts.P12)
    aceleração = 0
})
```

## Passo 19
Agora, vamos iniciar a programação do cálculo da aceleração. Para isso, clique 
no menu ``||math:Matemática||`` e insira o bloco ``||math:raiz quadrada||``
dentro do campo de definição do valor da variável ``||variables:aceleração||``.

```blocks
let opção = 0
let aceleração = 0
input.onButtonPressed(Button.A, function () {
    opção = 1
})
input.onButtonPressed(Button.B, function () {
    opção = 2
})
basic.forever(function () {
    if (opção == 1) {
        basic.showNumber(aceleração)
    } else {
        led.plotBarGraph(
        aceleração,
        2
        )
    }
})
basic.forever(function () {
    actuators.SetSpeedMotor(sensors.dimmerValue(InputPorts.P2), OutputPorts.P12)
    aceleração =  Math.sqrt(0)
})
```

## Passo 20
Retorne à ``||math:Matemática||`` e insira o bloco de divisão 
``||math:0 / 0||`` dentro do bloco de ``||math:raiz quadrada||``.

```blocks
let opção = 0
let aceleração = 0
input.onButtonPressed(Button.A, function () {
    opção = 1
})
input.onButtonPressed(Button.B, function () {
    opção = 2
})
basic.forever(function () {
    if (opção == 1) {
        basic.showNumber(aceleração)
    } else {
        led.plotBarGraph(
        aceleração,
        2
        )
    }
})
basic.forever(function () {
    actuators.SetSpeedMotor(sensors.dimmerValue(InputPorts.P2), OutputPorts.P12)
    aceleração = Math.sqrt(0 / 0)
})
```

## Passo 21
Altere o segundo **0** da divisão para **1000000** (1 milhão, com seis zeros).

```blocks
let opção = 0
let aceleração = 0
input.onButtonPressed(Button.A, function () {
    opção = 1
})
input.onButtonPressed(Button.B, function () {
    opção = 2
})
basic.forever(function () {
    if (opção == 1) {
        basic.showNumber(aceleração)
    } else {
        led.plotBarGraph(
        aceleração,
        2
        )
    }
})
basic.forever(function () {
    actuators.SetSpeedMotor(sensors.dimmerValue(InputPorts.P2), OutputPorts.P12)
    aceleração = Math.sqrt(0 / 1000000)
})
```

## Passo 22
Substitua o primeiro **0** da divisão por um bloco de adição ``||math:0 + 0||``,
também localizado na aba ``||math:Matemática||``. 

```blocks
let opção = 0
let aceleração = 0
input.onButtonPressed(Button.A, function () {
    opção = 1
})
input.onButtonPressed(Button.B, function () {
    opção = 2
})
basic.forever(function () {
    if (opção == 1) {
        basic.showNumber(aceleração)
    } else {
        led.plotBarGraph(
        aceleração,
        2
        )
    }
})
basic.forever(function () {
    actuators.SetSpeedMotor(sensors.dimmerValue(InputPorts.P2), OutputPorts.P12)
    aceleração = Math.sqrt((0 + 0) / 1000000)
})
```

## Passo 23
Substitua ambos os campos dessa adição por blocos de multiplicação 
``||math:0 x 0||``. Antes de prosseguir, clique nas setas desses blocos e 
altere da multiplicação para a potenciação, cujo símbolo é "**".

```blocks
let opção = 0
let aceleração = 0
input.onButtonPressed(Button.A, function () {
    opção = 1
})
input.onButtonPressed(Button.B, function () {
    opção = 2
})
basic.forever(function () {
    if (opção == 1) {
        basic.showNumber(aceleração)
    } else {
        led.plotBarGraph(
        aceleração,
        2
        )
    }
})
basic.forever(function () {
    actuators.SetSpeedMotor(sensors.dimmerValue(InputPorts.P2), OutputPorts.P12)
    aceleração = Math.sqrt((0 ** 0 + 0 ** 0) / 1000000)
})
```

## Passo 24
Acesse a aba ``||input:Entrada||`` e insira dois blocos 
``||input:aceleração (mg) x||``, que devem ser pocionados no primeiro campo 
de cada potenciação.

```blocks
let opção = 0
let aceleração = 0
input.onButtonPressed(Button.A, function () {
    opção = 1
})
input.onButtonPressed(Button.B, function () {
    opção = 2
})
basic.forever(function () {
    if (opção == 1) {
        basic.showNumber(aceleração)
    } else {
        led.plotBarGraph(
        aceleração,
        2
        )
    }
})
basic.forever(function () {
    actuators.SetSpeedMotor(sensors.dimmerValue(InputPorts.P2), OutputPorts.P12)
    aceleração = Math.sqrt((input.acceleration(Dimension.X) ** 0 + input.acceleration(Dimension.X) ** 0) / 1000000)
})
```

## Passo 25
Clique na seta do primeiro bloco ``||input:aceleração (mg) x||`` para alterar 
de **x** para **y**. Em seguida, altere o segundo campo de ambas as potências
de **0** para **2**.

```blocks
let opção = 0
let aceleração = 0
input.onButtonPressed(Button.A, function () {
    opção = 1
})
input.onButtonPressed(Button.B, function () {
    opção = 2
})
basic.forever(function () {
    if (opção == 1) {
        basic.showNumber(aceleração)
    } else {
        led.plotBarGraph(
        aceleração,
        2
        )
    }
})
basic.forever(function () {
    actuators.SetSpeedMotor(sensors.dimmerValue(InputPorts.P2), OutputPorts.P12)
    aceleração = Math.sqrt((input.acceleration(Dimension.Y) ** 2 + input.acceleration(Dimension.X) ** 2) / 1000000)
})
```

## Passo 26

Seu código está pronto! Baixe-o para o micro:bit e teste-o. 
Utilize o potenciômetro para aumentar ou reduzir a velocidade de rotação
e observe a variação do resultado do cálculo na matriz de LEDs do micro:bit.
Você pode alterar entre visualização numérica ou gráfica utilizando os botões
A e B do próprio micro:bit.

```blocks
```

## Passo 27
Se necessário, confira o seu código clicando na lâmpada de dica.

```blocks
let opção = 0
let aceleração = 0
input.onButtonPressed(Button.A, function () {
    opção = 1
})
input.onButtonPressed(Button.B, function () {
    opção = 2
})
basic.forever(function () {
    if (opção == 1) {
        basic.showNumber(aceleração)
    } else {
        led.plotBarGraph(
        aceleração,
        2
        )
    }
})
basic.forever(function () {
    actuators.SetSpeedMotor(sensors.dimmerValue(InputPorts.P2), OutputPorts.P12)
    aceleração = Math.sqrt((input.acceleration(Dimension.Y) ** 2 + input.acceleration(Dimension.X) ** 2) / 1000000)
})
```

```package
fuzzyBot=github:FuzzyMakers/pxt-fuzzyMakers
```
