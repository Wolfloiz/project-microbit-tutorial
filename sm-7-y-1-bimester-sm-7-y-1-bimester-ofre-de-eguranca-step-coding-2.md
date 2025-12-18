### @diffs true
# Cofre

## Passo 1
	Nesse tutorial, vamos programar um código para trancar e destrancar um cofre.
	A senha é definida na programação e a posição de um potenciômetro vai servir como
	o mecanismo para inserir a senha para destrancar o cofre. Depois de destrancado, 
	o logotipo do micro:bit é usado para trancá-lo novamente.

## Passo 2
Para começar, verifique se a biblioteca da Smart Makers já está importada em seu MakeCode.
Se não estiver, clique na aba **+ Extensões**, copie o endereço "https://github.com/FuzzyMakers/pxt-smartMakers",
cole-o no campo de pesquisa da janela que se abriu e selecione a biblioteca.

## Passo 3
Acesse o menu ``||actuators:Atuadores||`` e insira o bloco ``||actuators:Servo, definir posição 0 porta P8 modo knob||``
dentro do laço ``||basic:no iniciar||``. 

```blocks
actuators.SetAngleServoKnob(0, OutputPorts.P8)
basic.forever(function () {
	
})
```

## Passo 4
Altere o valor da posição de **0** para **500** e a porta de **P8** para **P16**.

```blocks
actuators.SetAngleServoKnob(500, OutputPorts.P16)
basic.forever(function () {
	
})
```

## Passo 5
Acesse o menu ``||variables:Variáveis||`` e clique em **"Fazer uma variável..."**.
Crie uma variável chamada: ``||variables:senha||``. 
Por fim, adicione o bloco ``||variables:definir senha para 0||`` que
aparecerá ao criá-la, dentro do laço ``||basic:sempre||``.  

```blocks
let senha = 0
actuators.SetAngleServoKnob(500, OutputPorts.P16)
basic.forever(function () {
    senha = 0
})
```

## Passo 6
Acesse a categoria ``||math:Matemática||`` e selecione o bloco ``||math:arredonda||``
para substituir o valor **0** do bloco de definição da variável ``||variables:senha||``.    

```blocks
let senha = 0
actuators.SetAngleServoKnob(500, OutputPorts.P16)
basic.forever(function () {
    senha = Math.round(0)
})
```

## Passo 7
Retorne à ``||math:Matemática||`` e insira o bloco ``||math:map 0 from low 0 high 1023 to low 0 high 4||``
dentro do bloco ``||math:arredonda||``.

```blocks
let senha = 0
actuators.SetAngleServoKnob(500, OutputPorts.P16)
basic.forever(function () {
    senha = Math.round(Math.map(0, 0, 1023, 0, 4))
})
```

## Passo 8
Vamos preencher os campos desse bloco ``||math:map||``. Primeiramente,
acesse o menu ``||sensors:Sensores||`` e adicione o bloco ``||sensors:Valor do potenciômetro na porta P2||``
no primeiro campo, substituindo o **0**. Em seguida, altere o último campo (``||math:high||``)
de **4** para **9**.

```blocks
let senha = 0
actuators.SetAngleServoKnob(500, OutputPorts.P16)
basic.forever(function () {
    senha = Math.round(Math.map(sensors.dimmerValue(InputPorts.P2), 0, 1023, 0, 9))
})
```

## Passo 9
Esse bloco ``||math:map||`` vai transformar a posição do potenciômetro em um número de **0** a **9**.
Então, devemos exibir esse número para o usuário conseguir definir a senha. Para isso,
acesse a aba ``||basic:Básico||`` e adicione o bloco ``||basic:mostrar número 0||`` ainda dentro do laço ``||basic:sempre||``.

```blocks
let senha = 0
actuators.SetAngleServoKnob(500, OutputPorts.P16)
basic.forever(function () {
    senha = Math.round(Math.map(sensors.dimmerValue(InputPorts.P2), 0, 1023, 0, 9))
    basic.showNumber(0)
})
```

## Passo 10
Acesse a aba ``||variables:Variáveis||`` e selecione o bloco ``||variables:senha||``
para substituir o valor **0** de ``||basic:mostrar número||``.

```blocks
let senha = 0
actuators.SetAngleServoKnob(500, OutputPorts.P16)
basic.forever(function () {
    senha = Math.round(Math.map(sensors.dimmerValue(InputPorts.P2), 0, 1023, 0, 9))
    basic.showNumber(senha)
})
```

## Passo 11
Agora, acesse a categoria ``||input:Entrada||`` e adicione um bloco ``||input:no logotipo pressionado||``.

```blocks
input.onLogoEvent(TouchButtonEvent.Pressed, function () {
	
})
let senha = 0
actuators.SetAngleServoKnob(500, OutputPorts.P16)
basic.forever(function () {
    senha = Math.round(Math.map(sensors.dimmerValue(InputPorts.P2), 0, 1023, 0, 9))
    basic.showNumber(senha)
})
```

## Passo 12
Ao pressionar o logotipo, o cofre deve ser trancado. Portanto, adicione o bloco 
``||actuators:Servo, definir posição 500 porta P16 modo knob||``, igual ao que estava 
inserido no bloco ``||basic:no iniciar||``, com o valor de posição **500** e a porta **P16**.


```blocks
input.onLogoEvent(TouchButtonEvent.Pressed, function () {
    actuators.SetAngleServoKnob(500, OutputPorts.P16)
})
let senha = 0
actuators.SetAngleServoKnob(500, OutputPorts.P16)
basic.forever(function () {
    senha = Math.round(Math.map(sensors.dimmerValue(InputPorts.P2), 0, 1023, 0, 9))
    basic.showNumber(senha)
})
```

## Passo 13
Retorne à ``||input:Entrada||`` e adicione o bloco ``||input:no botão A pressionado||`` ao seu código.

```blocks
input.onLogoEvent(TouchButtonEvent.Pressed, function () {
    actuators.SetAngleServoKnob(500, OutputPorts.P16)
})
input.onButtonPressed(Button.A, function () {
	
})
let senha = 0
actuators.SetAngleServoKnob(500, OutputPorts.P16)
basic.forever(function () {
    senha = Math.round(Math.map(sensors.dimmerValue(InputPorts.P2), 0, 1023, 0, 9))
    basic.showNumber(senha)
})
```

## Passo 14
Clique no menu ``||logic:Lógica||`` e selecione o bloco ``||logic:se então senão||`` dentro
de ``||input:no botão A pressionado||``. 

```blocks
input.onLogoEvent(TouchButtonEvent.Pressed, function () {
    actuators.SetAngleServoKnob(500, OutputPorts.P16)
})
input.onButtonPressed(Button.A, function () {
    if (true) {
    	
    } else {
    	
    }
})
let senha = 0
actuators.SetAngleServoKnob(500, OutputPorts.P16)
basic.forever(function () {
    senha = Math.round(Math.map(sensors.dimmerValue(InputPorts.P2), 0, 1023, 0, 9))
    basic.showNumber(senha)
})
```

## Passo 15
Retorne ao menu ``||logic:Lógica||`` e adicione o bloco comparador ``||logic:0 = 0||``
dentro do campo **verdadeiro** do ``||logic:se então senão||``.

```blocks
input.onLogoEvent(TouchButtonEvent.Pressed, function () {
    actuators.SetAngleServoKnob(500, OutputPorts.P16)
})
input.onButtonPressed(Button.A, function () {
    if (0 == 0) {
    	
    } else {
    	
    }
})
let senha = 0
actuators.SetAngleServoKnob(500, OutputPorts.P16)
basic.forever(function () {
    senha = Math.round(Math.map(sensors.dimmerValue(InputPorts.P2), 0, 1023, 0, 9))
    basic.showNumber(senha)
})
```

## Passo 16
Altere o primeiro campo desse comparador para o bloco ``||variables:senha||``, localizado
em ``||variables:Variáveis||``. Em seguida, modifique o segundo campo de **0** para **9**.

```blocks
input.onLogoEvent(TouchButtonEvent.Pressed, function () {
    actuators.SetAngleServoKnob(500, OutputPorts.P16)
})
input.onButtonPressed(Button.A, function () {
    if (senha == 9) {
    	
    } else {
    	
    }
})
let senha = 0
actuators.SetAngleServoKnob(500, OutputPorts.P16)
basic.forever(function () {
    senha = Math.round(Math.map(sensors.dimmerValue(InputPorts.P2), 0, 1023, 0, 9))
    basic.showNumber(senha)
})
```

## Passo 17
Agora, dentro do ``||logic:então||``, insira um bloco ``||basic:mostrar ícone||``.
Clique na seta para alterar o ícone de coração para um "sim" (check), indicando ao 
usuário que ele acertou a senha.

```blocks
input.onLogoEvent(TouchButtonEvent.Pressed, function () {
    actuators.SetAngleServoKnob(500, OutputPorts.P16)
})
input.onButtonPressed(Button.A, function () {
    if (senha == 9) {
        basic.showIcon(IconNames.Yes)
    } else {
    	
    }
})
let senha = 0
actuators.SetAngleServoKnob(500, OutputPorts.P16)
basic.forever(function () {
    senha = Math.round(Math.map(sensors.dimmerValue(InputPorts.P2), 0, 1023, 0, 9))
    basic.showNumber(senha)
})
```

## Passo 18
Adicione um bloco ``||actuators:Servo, definir posição 0 porta P16 modo knob||``, com o valor de 
posição **0** e porta **P16**, ainda dentro do ``||logic:então||``, para abrir o cofre. 

```blocks
input.onLogoEvent(TouchButtonEvent.Pressed, function () {
    actuators.SetAngleServoKnob(500, OutputPorts.P16)
})
input.onButtonPressed(Button.A, function () {
    if (senha == 9) {
        basic.showIcon(IconNames.Yes)
        actuators.SetAngleServoKnob(0, OutputPorts.P16)
    } else {
    	
    }
})
let senha = 0
actuators.SetAngleServoKnob(500, OutputPorts.P16)
basic.forever(function () {
    senha = Math.round(Math.map(sensors.dimmerValue(InputPorts.P2), 0, 1023, 0, 9))
    basic.showNumber(senha)
})
```

## Passo 19
Agora, dentro do ``||logic:senão||``, adicione um bloco ``||basic:mostrar ícone||`` para indicar a senha incorreta.
Clique na seta para alterar o símbolo para um **X**.

```blocks
input.onLogoEvent(TouchButtonEvent.Pressed, function () {
    actuators.SetAngleServoKnob(500, OutputPorts.P16)
})
input.onButtonPressed(Button.A, function () {
    if (senha == 9) {
        basic.showIcon(IconNames.Yes)
        actuators.SetAngleServoKnob(0, OutputPorts.P16)
    } else {
        basic.showIcon(IconNames.No)
    }
})
let senha = 0
actuators.SetAngleServoKnob(500, OutputPorts.P16)
basic.forever(function () {
    senha = Math.round(Math.map(sensors.dimmerValue(InputPorts.P2), 0, 1023, 0, 9))
    basic.showNumber(senha)
})
```

## Passo 20
Por fim, retorne à categoria ``||basic:Básico||`` e adicione um bloco ``||basic:limpar tela||``
após o ``||basic:mostrar ícone||``, ainda dentro do ``||logic:senão||``.   

```blocks
input.onLogoEvent(TouchButtonEvent.Pressed, function () {
    actuators.SetAngleServoKnob(500, OutputPorts.P16)
})
input.onButtonPressed(Button.A, function () {
    if (senha == 9) {
        basic.showIcon(IconNames.Yes)
        actuators.SetAngleServoKnob(0, OutputPorts.P16)
    } else {
        basic.showIcon(IconNames.No)
        basic.clearScreen()
    }
})
let senha = 0
actuators.SetAngleServoKnob(500, OutputPorts.P16)
basic.forever(function () {
    senha = Math.round(Math.map(sensors.dimmerValue(InputPorts.P2), 0, 1023, 0, 9))
    basic.showNumber(senha)
})
```

## Passo 21

Agora seu código está pronto! Baixe-o para o micro:bit e teste-o. 
Utilize o potenciômetro para ajustar a senha inserida e pressione o botão A para confirmar.
Use o logotipo do micro:bit para fechar o cofre depois de aberto.
Se desejar, modifique o valor da sua senha de **9** no comparador lógico para outro número entre **0** e **9**.

```blocks
```

## Passo 22
Se necessário, confira o seu código clicando na lâmpada de dica.

```blocks
input.onLogoEvent(TouchButtonEvent.Pressed, function () {
    actuators.SetAngleServoKnob(500, OutputPorts.P16)
})
input.onButtonPressed(Button.A, function () {
    if (senha == 9) {
        basic.showIcon(IconNames.Yes)
        actuators.SetAngleServoKnob(0, OutputPorts.P16)
    } else {
        basic.showIcon(IconNames.No)
        basic.clearScreen()
    }
})
let senha = 0
actuators.SetAngleServoKnob(500, OutputPorts.P16)
basic.forever(function () {
    senha = Math.round(Math.map(sensors.dimmerValue(InputPorts.P2), 0, 1023, 0, 9))
    basic.showNumber(senha)
})
```

```package
fuzzyBot=github:FuzzyMakers/pxt-fuzzyMakers
```
