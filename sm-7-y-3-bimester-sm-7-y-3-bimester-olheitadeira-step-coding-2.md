### @diffs true
# Colheitadeira

## Passo 1
Nesse tutorial, vamos programar uma colheitadeira que inicia seu movimento 
ao pressionarmos o botão A do micro:bit. A cada 3 segundos o valor de uma
variável que indica a quantidade de trigo coletada é incrementado caso os motores estejam ligados. O botão B do micro:bit
deve parar a colheitadeira e, ao tocarmos o logotipo, vamos exibir a quantidade
total de trigo colhida até aquele momento.

## Passo 2
Para começar, verifique se a biblioteca da Smart Makers já está importada 
em seu MakeCode. Se não estiver, clique na aba **+ Extensões**, 
copie o endereço "https://github.com/FuzzyMakers/pxt-smartMakers",
cole-o no campo de pesquisa da janela que se abriu e selecione a biblioteca.

## Passo 3
Acesse o menu ``||input:Entrada||`` e adicione dois blocos 
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
Em seguida, acesse a aba ``||actuators:Atuadores||`` e adicione dois blocos
``||actuators:Motor CC, definir velocidade 0 na porta P8||`` dentro do bloco
``||input:no botão A pressionado||``.

```blocks
input.onButtonPressed(Button.A, function () {
    actuators.SetSpeedMotor(0, OutputPorts.P8)
    actuators.SetSpeedMotor(0, OutputPorts.P8)
})
input.onButtonPressed(Button.B, function () {
	
})
```

## Passo 5
Edite o valor de velocidade de ambos os blocos de **0** para **1023** e a 
porta de somente um deles de **P8** para **P16**.

```blocks
input.onButtonPressed(Button.A, function () {
    actuators.SetSpeedMotor(1023, OutputPorts.P8)
    actuators.SetSpeedMotor(1023, OutputPorts.P16)
})
input.onButtonPressed(Button.B, function () {
	
})
```

## Passo 6

Vá até a categoria ``||variables:Variáveis||``, clique em **Fazer uma variável:**
e defina seu nome para **ligado**. Agora volte ao menu ``||variables:Variáveis||``
e arraste o bloco ``||variables:Definir ligado para 0||`` para o final do código.


```blocks
let ligado = 0
input.onButtonPressed(Button.A, function () {
    actuators.SetSpeedMotor(1023, OutputPorts.P8)
    actuators.SetSpeedMotor(1023, OutputPorts.P16)
    ligado = 0
})
input.onButtonPressed(Button.B, function () {
	
})

```

## Passo 7
Modifique o valor da variável de **0** para **1**.
```blocks
let ligado = 0
input.onButtonPressed(Button.A, function () {
    actuators.SetSpeedMotor(1023, OutputPorts.P8)
    actuators.SetSpeedMotor(1023, OutputPorts.P16)
    ligado = 1
})
input.onButtonPressed(Button.B, function () {
	
})


```


## Passo 8
Retorne ao menu de ``||actuators:Atuadores||`` e adicione dois blocos
``||actuators:Motor CC, parar motor na porta P8||`` dentro do outro bloco
``||input:no botão B pressionado||``.

```blocks
let ligado = 0
input.onButtonPressed(Button.A, function () {
    actuators.SetSpeedMotor(1023, OutputPorts.P8)
    actuators.SetSpeedMotor(1023, OutputPorts.P16)
    ligado = 1
})
input.onButtonPressed(Button.B, function () {
    actuators.StopMotor(OutputPorts.P8)
    actuators.StopMotor(OutputPorts.P8)
})


```

## Passo 9
Altere a porta de um deles de **P8** para **P16**.

```blocks
let ligado = 0
input.onButtonPressed(Button.A, function () {
    actuators.SetSpeedMotor(1023, OutputPorts.P8)
    actuators.SetSpeedMotor(1023, OutputPorts.P16)
    ligado = 1
})
input.onButtonPressed(Button.B, function () {
    actuators.StopMotor(OutputPorts.P8)
    actuators.StopMotor(OutputPorts.P16)
})


```

## Passo 10

Volte até a categoria ``||variables:Variáveis||`` e arraste o bloco
``||variables:Definir ligado para 0||`` para o final do bloco ``||input:no botão B pressionado||``.


```blocks
let ligado = 0
input.onButtonPressed(Button.A, function () {
    actuators.SetSpeedMotor(1023, OutputPorts.P8)
    actuators.SetSpeedMotor(1023, OutputPorts.P16)
    ligado = 1
})
input.onButtonPressed(Button.B, function () {
    actuators.StopMotor(OutputPorts.P8)
    actuators.StopMotor(OutputPorts.P16)
    ligado = 0
})

```



## Passo 11
Volte à aba ``||input:Entrada||`` e adicione um bloco 
``||input:no logotipo pressionado||`` ao seu código.

```blocks
let ligado = 0
input.onLogoEvent(TouchButtonEvent.Pressed, function () {
	
})
input.onButtonPressed(Button.A, function () {
    actuators.SetSpeedMotor(1023, OutputPorts.P8)
    actuators.SetSpeedMotor(1023, OutputPorts.P16)
    ligado = 1
})
input.onButtonPressed(Button.B, function () {
    actuators.StopMotor(OutputPorts.P8)
    actuators.StopMotor(OutputPorts.P16)
    ligado = 0
})


```

## Passo 12
Clique na aba ``||basic:Básico||`` e insira o comando 
``||basic:mostrar número 0||`` dentro de ``||input:no logotipo pressionado||``.

```blocks
let ligado = 0
input.onLogoEvent(TouchButtonEvent.Pressed, function () {
    basic.showNumber(0)
})
input.onButtonPressed(Button.A, function () {
    actuators.SetSpeedMotor(1023, OutputPorts.P8)
    actuators.SetSpeedMotor(1023, OutputPorts.P16)
    ligado = 1
})
input.onButtonPressed(Button.B, function () {
    actuators.StopMotor(OutputPorts.P8)
    actuators.StopMotor(OutputPorts.P16)
    ligado = 0
})


```

## Passo 13
Acesse o menu ``||variables:Variáveis||`` e clique em **"Fazer uma variável:"**.
Crie uma variável chamada: ``||variables:trigo||``. 
Em seguida, insira o bloco de bordas redondas ``||variables:trigo||`` dentro do 
``||basic:mostrar número||``, substituindo o **0**.

```blocks
let ligado = 0
input.onLogoEvent(TouchButtonEvent.Pressed, function () {
    let trigo = 0
    basic.showNumber(trigo)
})
input.onButtonPressed(Button.A, function () {
    actuators.SetSpeedMotor(1023, OutputPorts.P8)
    actuators.SetSpeedMotor(1023, OutputPorts.P16)
    ligado = 1
})
input.onButtonPressed(Button.B, function () {
    actuators.StopMotor(OutputPorts.P8)
    actuators.StopMotor(OutputPorts.P16)
    ligado = 0
})


```

## Passo 14
Acesse a aba ``||Loops:Loops||`` e adicione um laço  
``||Loops:every 500 ms||`` ao seu código. Clique no campo para alterar o valor 
de **500 ms** para **3000 ms**

```blocks
let ligado = 0
input.onLogoEvent(TouchButtonEvent.Pressed, function () {
    let trigo = 0
    basic.showNumber(trigo)
})
input.onButtonPressed(Button.A, function () {
    actuators.SetSpeedMotor(1023, OutputPorts.P8)
    actuators.SetSpeedMotor(1023, OutputPorts.P16)
    ligado = 1
})
input.onButtonPressed(Button.B, function () {
    actuators.StopMotor(OutputPorts.P8)
    actuators.StopMotor(OutputPorts.P16)
    ligado = 0
})
loops.everyInterval(3000, function () {
	
})


```

## Passo 15
Navegue até o menu ``||logic:Lógica||`` e insira um bloco ``||logic:se então||`` no loop.

```blocks
let ligado = 0
input.onLogoEvent(TouchButtonEvent.Pressed, function () {
    let trigo = 0
    basic.showNumber(trigo)
})
input.onButtonPressed(Button.A, function () {
    actuators.SetSpeedMotor(1023, OutputPorts.P8)
    actuators.SetSpeedMotor(1023, OutputPorts.P16)
    ligado = 1
})
input.onButtonPressed(Button.B, function () {
    actuators.StopMotor(OutputPorts.P8)
    actuators.StopMotor(OutputPorts.P16)
    ligado = 0
})
loops.everyInterval(3000, function () {
    if (true) {
    	
    }
})


```
## Passo 16
Volte à categoria ``||logic:Lógica||``, pegue o comparador ``||logic:0 = 0||``  e substitua
o campo ``||logic:verdadeiro||``. Altere o primeiro campo para a variável ``||variables:ligado||``
e o segundo para 1.

```blocks
let ligado = 0
input.onLogoEvent(TouchButtonEvent.Pressed, function () {
    let trigo = 0
    basic.showNumber(trigo)
})
input.onButtonPressed(Button.A, function () {
    actuators.SetSpeedMotor(1023, OutputPorts.P8)
    actuators.SetSpeedMotor(1023, OutputPorts.P16)
    ligado = 1
})
input.onButtonPressed(Button.B, function () {
    actuators.StopMotor(OutputPorts.P8)
    actuators.StopMotor(OutputPorts.P16)
    ligado = 0
})
loops.everyInterval(3000, function () {
    if (ligado == 1) {
    	
    }
})



```

## Passo 17
Volte ao menu ``||variables:Variáveis||`` e adicione o bloco 
``||variables:alterar trigo por 1||`` dentro da condição
``||logic:se ligado = 1 então||``.

```blocks
let trigo = 0
let ligado = 0
input.onLogoEvent(TouchButtonEvent.Pressed, function () {
    basic.showNumber(trigo)
})
input.onButtonPressed(Button.A, function () {
    actuators.SetSpeedMotor(1023, OutputPorts.P8)
    actuators.SetSpeedMotor(1023, OutputPorts.P16)
    ligado = 1
})
input.onButtonPressed(Button.B, function () {
    actuators.StopMotor(OutputPorts.P8)
    actuators.StopMotor(OutputPorts.P16)
    ligado = 0
})
loops.everyInterval(3000, function () {
    if (ligado == 1) {
        trigo += 1
    }
})



```

## Passo 18
Edite o valor de alteração da variável ``||variables:trigo||`` de **1** para
**10**.

```blocks
let trigo = 0
let ligado = 0
input.onLogoEvent(TouchButtonEvent.Pressed, function () {
    basic.showNumber(trigo)
})
input.onButtonPressed(Button.A, function () {
    actuators.SetSpeedMotor(1023, OutputPorts.P8)
    actuators.SetSpeedMotor(1023, OutputPorts.P16)
    ligado = 1
})
input.onButtonPressed(Button.B, function () {
    actuators.StopMotor(OutputPorts.P8)
    actuators.StopMotor(OutputPorts.P16)
    ligado = 0
})
loops.everyInterval(3000, function () {
    if (ligado == 1) {
        trigo += 10
    }
})

```

## Passo 19

Agora seu código está pronto! Baixe-o para o micro:bit e teste-o. 
Os botões A e B iniciam ou param o movimento da colheitadeira, enquanto 
o logotipo do micro:bit é usado para exibir a quantidade de trigo coletada.

```blocks
```

## Passo 20
Se necessário, confira o seu código clicando na lâmpada de dica.

```blocks
let trigo = 0
let ligado = 0
input.onLogoEvent(TouchButtonEvent.Pressed, function () {
    basic.showNumber(trigo)
})
input.onButtonPressed(Button.A, function () {
    actuators.SetSpeedMotor(1023, OutputPorts.P8)
    actuators.SetSpeedMotor(1023, OutputPorts.P16)
    ligado = 1
})
input.onButtonPressed(Button.B, function () {
    actuators.StopMotor(OutputPorts.P8)
    actuators.StopMotor(OutputPorts.P16)
    ligado = 0
})
loops.everyInterval(3000, function () {
    if (ligado == 1) {
        trigo += 10
    }
})


```

```package
fuzzyBot=github:FuzzyMakers/pxt-fuzzyMakers
```
