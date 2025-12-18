### @diffs true
# Microscópio

## Passo 1
Neste tutorial, vamos explorar o mundo invisível aos nossos olhos ao construir
um protótipo de um microscópio. Utilizaremos o potenciômetro para movimentar o
servo e ajustar o nível de zoom do aparelho. Ao pressionar o botão A do 
micro:bit vamos exibir o valor do amplificação e ao pressionar o botão B, 
mostraremos qual tipo de organismo estamos teoricamente observando.

## Passo 2
Para começar, verifique se a biblioteca da Smart Makers já está importada 
em seu MakeCode. Se não estiver, clique na aba **+ Extensões**, 
copie o endereço "https://github.com/FuzzyMakers/pxt-smartMakers",
cole-o no campo de pesquisa da janela que se abriu e selecione a biblioteca.

## Passo 3
Acesse o menu ``||input:Entrada||`` e adicione dois blocos 
``||input:no botão A pressionado||`` à sua área de programação.
Altere um dos blocos de ``||input:botão A||`` para ``||input:botão B||``.

```blocks
input.onButtonPressed(Button.A, function () {
	
})
input.onButtonPressed(Button.B, function () {
	
})
basic.forever(function () {
	
})
```

## Passo 4
Acesse a aba ``||basic:Básico||`` e adicione o comando ``||basic:mostrar string||`` 
dentro do bloco ``||input:no botão A pressionado||``.

```blocks
input.onButtonPressed(Button.A, function () {
    basic.showString("Hello!")
})
input.onButtonPressed(Button.B, function () {
	
})
basic.forever(function () {
	
})
```

## Passo 5
Clique em **Avançado** para abrir novas categorias. Clique em ``||text:Texto||``
e selecione o comando ``||text:unir "Olá" "Mundo"||`` para substituir o texto 
"Hello" do bloco ``||basic:mostrar string||``.

```blocks
input.onButtonPressed(Button.A, function () {
    basic.showString("Olá" + "Mundo")
})
input.onButtonPressed(Button.B, function () {
	
})
basic.forever(function () {
	
})
```

## Passo 6
Em seguida, acesse o menu ``||sensors:Sensores||`` e adicione o bloco ``||sensors:Valor do potenciômetro na porta P2||``
dentro do primeiro campo do bloco ``||text:unir||``,
substituindo o "Olá". Antes de prosseguir, altere o segundo texto de "Mundo"
para "X", indicando a amplificação do microscópio.

```blocks
input.onButtonPressed(Button.A, function () {
    basic.showString("" + sensors.dimmerValue(InputPorts.P2) + "X")
})
input.onButtonPressed(Button.B, function () {
	
})
basic.forever(function () {
	
})

```

## Passo 7
Agora, prosseguimos para o ``||input:no botão B pressionado||``. Acesse a 
categoria ``||logic:Lógica||`` e insira um bloco ``||logic:se então senão||`` 
no bloco ``||input:no botão B pressionado||``.

```blocks
input.onButtonPressed(Button.A, function () {
    basic.showString("" + sensors.dimmerValue(InputPorts.P2) + "X")
})
input.onButtonPressed(Button.B, function () {
    if (true) {
    	
    } else {
    	
    }
})
basic.forever(function () {
	
})


```

## Passo 8
Retorne à categoria ``||logic:Lógica||`` e utilize um bloco comparador
``||logic:0 < 0||`` para substituir o campo **verdadeiro** do bloco 
``||logic:se então senão||``. Altere o valor do sinal **<** para **>**.

```blocks
input.onButtonPressed(Button.A, function () {
    basic.showString("" + sensors.dimmerValue(InputPorts.P2) + "X")
})
input.onButtonPressed(Button.B, function () {
    if (0 > 0) {
    	
    } else {
    	
    }
})
basic.forever(function () {
	
})

```

## Passo 9
Modifique o primeiro valor desse comparador de **0** para o
``||sensors:Valor do potenciômetro na porta P2||`` e o segundo campo do comparador de **0** para **1000**.

```blocks
input.onButtonPressed(Button.A, function () {
    basic.showString("" + sensors.dimmerValue(InputPorts.P2) + "X")
})
input.onButtonPressed(Button.B, function () {
    if (sensors.dimmerValue(InputPorts.P2) > 1000) {
    	
    } else {
    	
    }
})
basic.forever(function () {
	
})

```

## Passo 10
Clique **três** vezes no sinal de **"+"** do bloco ``||logic:se então senão||`` 
para abrir novas condições ``||logic:senão se||``.

```blocks
input.onButtonPressed(Button.A, function () {
    basic.showString("" + sensors.dimmerValue(InputPorts.P2) + "X")
})
input.onButtonPressed(Button.B, function () {
    if (sensors.dimmerValue(InputPorts.P2) > 1000) {
    	
    } else if (false) {
    	
    } else if (false) {
    	
    } else if (false) {
    	
    } else {
    	
    }
})
basic.forever(function () {
	
})

```

## Passo 11
Substitua todos os campos **falsos** desses novos ``||logic:senão se||`` por 
comparadores similares ao anterior, com o primeiro campo sendo o 
``||sensors:Valor do potenciômetro na porta P2||``  e o segundo sendo maiores que os números **"600"**, **"100"**,
**"40"**, respectivamente.

```blocks
input.onButtonPressed(Button.A, function () {
    basic.showString("" + sensors.dimmerValue(InputPorts.P2) + "X")
})
input.onButtonPressed(Button.B, function () {
    if (sensors.dimmerValue(InputPorts.P2) > 1000) {
    	
    } else if (sensors.dimmerValue(InputPorts.P2) > 600) {
    	
    } else if (sensors.dimmerValue(InputPorts.P2) > 100) {
    	
    } else if (sensors.dimmerValue(InputPorts.P2) > 40) {
    	
    } else {
    	
    }
})
basic.forever(function () {
	
})

```

## Passo 12
Agora, acesse a categoria ``||basic:Básico||`` e adicione quatro blocos 
``||basic:mostrar string||``, um dentro de cada ``||logic:então||``. 

```blocks
input.onButtonPressed(Button.A, function () {
    basic.showString("" + sensors.dimmerValue(InputPorts.P2) + "X")
})
input.onButtonPressed(Button.B, function () {
    if (sensors.dimmerValue(InputPorts.P2) > 1000) {
        basic.showString("Hello!")
    } else if (sensors.dimmerValue(InputPorts.P2) > 600) {
        basic.showString("Hello!")
    } else if (sensors.dimmerValue(InputPorts.P2) > 100) {
        basic.showString("Hello!")
    } else if (sensors.dimmerValue(InputPorts.P2) > 40) {
        basic.showString("Hello!")
    } else {
    	
    }
})
basic.forever(function () {
	
})

```

## Passo 13
Em seguida, modifique as palavras exibidas de **"Hello"** para as respectivas strings:
- **Bactérias**;
- **Hemáceas**;
- **Amebas**;
- **Ácaros**.

```blocks
input.onButtonPressed(Button.A, function () {
    basic.showString("" + sensors.dimmerValue(InputPorts.P2) + "X")
})
input.onButtonPressed(Button.B, function () {
    if (sensors.dimmerValue(InputPorts.P2) > 1000) {
        basic.showString("Bactérias")
    } else if (sensors.dimmerValue(InputPorts.P2) > 600) {
        basic.showString("Hemácias")
    } else if (sensors.dimmerValue(InputPorts.P2) > 100) {
        basic.showString("Amebas")
    } else if (sensors.dimmerValue(InputPorts.P2) > 40) {
        basic.showString("Ácaros")
    } else {
    	
    }
})
basic.forever(function () {
	
})

```

## Passo 14
Dentro do ``||logic:senão||``, adicione um comando ``||basic:mostrar ícone||``
localizado na categoria ``||basic:Básico||``. Clique na seta para alterar o 
símbolo que será exibido para um **"X"**.


```blocks
input.onButtonPressed(Button.A, function () {
    basic.showString("" + sensors.dimmerValue(InputPorts.P2) + "X")
})
input.onButtonPressed(Button.B, function () {
    if (sensors.dimmerValue(InputPorts.P2) > 1000) {
        basic.showString("Bactérias")
    } else if (sensors.dimmerValue(InputPorts.P2) > 600) {
        basic.showString("Hemácias")
    } else if (sensors.dimmerValue(InputPorts.P2) > 100) {
        basic.showString("Amebas")
    } else if (sensors.dimmerValue(InputPorts.P2) > 40) {
        basic.showString("Ácaros")
    } else {
        basic.showIcon(IconNames.No)
    }
})
basic.forever(function () {
	
})

```

## Passo 15
Acesse o menu ``||actuators:Atuadores||`` e adicione o comando 
``||actuators:Servo, definir posição 0 porta P8 modo Knob||`` dentro do laço
``||basic:sempre||``.

```blocks
input.onButtonPressed(Button.A, function () {
    basic.showString("" + sensors.dimmerValue(InputPorts.P2) + "X")
})
input.onButtonPressed(Button.B, function () {
    if (sensors.dimmerValue(InputPorts.P2) > 1000) {
        basic.showString("Bactérias")
    } else if (sensors.dimmerValue(InputPorts.P2) > 600) {
        basic.showString("Hemácias")
    } else if (sensors.dimmerValue(InputPorts.P2) > 100) {
        basic.showString("Amebas")
    } else if (sensors.dimmerValue(InputPorts.P2) > 40) {
        basic.showString("Ácaros")
    } else {
        basic.showIcon(IconNames.No)
    }
})
basic.forever(function () {
    actuators.SetAngleServoKnob(0, OutputPorts.P8)
})

```

## Passo 16
Clique na seta desse bloco para alterar a porta de ``||actuators:P8||`` para 
``||actuators:P16||``.

```blocks
input.onButtonPressed(Button.A, function () {
    basic.showString("" + sensors.dimmerValue(InputPorts.P2) + "X")
})
input.onButtonPressed(Button.B, function () {
    if (sensors.dimmerValue(InputPorts.P2) > 1000) {
        basic.showString("Bactérias")
    } else if (sensors.dimmerValue(InputPorts.P2) > 600) {
        basic.showString("Hemácias")
    } else if (sensors.dimmerValue(InputPorts.P2) > 100) {
        basic.showString("Amebas")
    } else if (sensors.dimmerValue(InputPorts.P2) > 40) {
        basic.showString("Ácaros")
    } else {
        basic.showIcon(IconNames.No)
    }
})
basic.forever(function () {
    actuators.SetAngleServoKnob(0, OutputPorts.P16)
})

```

## Passo 17
Acesse a categoria ``||math:Matemática||`` e utilize o bloco 
``||math:map 0 from low 0 high 1023 to low 0 high 4||`` para substituir o campo
do valor de posição do bloco ``||actuators:Servo, definir posição||``. 

```blocks
input.onButtonPressed(Button.A, function () {
    basic.showString("" + sensors.dimmerValue(InputPorts.P2) + "X")
})
input.onButtonPressed(Button.B, function () {
    if (sensors.dimmerValue(InputPorts.P2) > 1000) {
        basic.showString("Bactérias")
    } else if (sensors.dimmerValue(InputPorts.P2) > 600) {
        basic.showString("Hemácias")
    } else if (sensors.dimmerValue(InputPorts.P2) > 100) {
        basic.showString("Amebas")
    } else if (sensors.dimmerValue(InputPorts.P2) > 40) {
        basic.showString("Ácaros")
    } else {
        basic.showIcon(IconNames.No)
    }
})
basic.forever(function () {
    actuators.SetAngleServoKnob(Math.map(0, 0, 1023, 0, 4), OutputPorts.P16)
})

```

## Passo 18
Agora, vamos editar os campos desse bloco ``||math:Map||``. Comece acessando 
a categoria ``||sensors:Sensores||`` e selecionando o bloco 
``||sensors:Valor do potenciômetro na porta P2||`` para substituir o primeiro
campo com o valor **0**.

```blocks
input.onButtonPressed(Button.A, function () {
    basic.showString("" + sensors.dimmerValue(InputPorts.P2) + "X")
})
input.onButtonPressed(Button.B, function () {
    if (sensors.dimmerValue(InputPorts.P2) > 1000) {
        basic.showString("Bactérias")
    } else if (sensors.dimmerValue(InputPorts.P2) > 600) {
        basic.showString("Hemácias")
    } else if (sensors.dimmerValue(InputPorts.P2) > 100) {
        basic.showString("Amebas")
    } else if (sensors.dimmerValue(InputPorts.P2) > 40) {
        basic.showString("Ácaros")
    } else {
        basic.showIcon(IconNames.No)
    }
})
basic.forever(function () {
    actuators.SetAngleServoKnob(Math.map(sensors.dimmerValue(InputPorts.P2), 0, 1023, 0, 4), OutputPorts.P16)
})

```

## Passo 19
Feito isso, altere os dois últimos campos do comando ``||math:Map||`` de 
**0** e **4** para **140** e **530**.

```blocks
input.onButtonPressed(Button.A, function () {
    basic.showString("" + sensors.dimmerValue(InputPorts.P2) + "X")
})
input.onButtonPressed(Button.B, function () {
    if (sensors.dimmerValue(InputPorts.P2) > 1000) {
        basic.showString("Bactérias")
    } else if (sensors.dimmerValue(InputPorts.P2) > 600) {
        basic.showString("Hemácias")
    } else if (sensors.dimmerValue(InputPorts.P2) > 100) {
        basic.showString("Amebas")
    } else if (sensors.dimmerValue(InputPorts.P2) > 40) {
        basic.showString("Ácaros")
    } else {
        basic.showIcon(IconNames.No)
    }
})
basic.forever(function () {
    actuators.SetAngleServoKnob(Math.map(sensors.dimmerValue(InputPorts.P2), 0, 1023, 140, 530), OutputPorts.P16)
})

```



## Passo 20
Agora seu código está pronto! Baixe-o para o micro:bit e utilize o potenciômetro
para ajustar o nível de zoom do microscópio. Pressione o botão B para exibir 
o tipo de organismo sendo observado e o botão A para indicar o nível de 
ampliação atual.


```blocks
```

## Passo 21
Se necessário, confira o seu código clicando na lâmpada de dica.

```blocks
input.onButtonPressed(Button.A, function () {
    basic.showString("" + sensors.dimmerValue(InputPorts.P2) + "X")
})
input.onButtonPressed(Button.B, function () {
    if (sensors.dimmerValue(InputPorts.P2) > 1000) {
        basic.showString("Bactérias")
    } else if (sensors.dimmerValue(InputPorts.P2) > 600) {
        basic.showString("Hemácias")
    } else if (sensors.dimmerValue(InputPorts.P2) > 100) {
        basic.showString("Amebas")
    } else if (sensors.dimmerValue(InputPorts.P2) > 40) {
        basic.showString("Ácaros")
    } else {
        basic.showIcon(IconNames.No)
    }
})
basic.forever(function () {
    actuators.SetAngleServoKnob(Math.map(sensors.dimmerValue(InputPorts.P2), 0, 1023, 140, 530), OutputPorts.P16)
})

```

```package
fuzzyBot=github:FuzzyMakers/pxt-fuzzyMakers
```