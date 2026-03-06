### @diffs true
# Corrida Por Aplicativo

## Passo 1
Depois de construir um carro para simular uma corrida por aplicativo, vamos programar o cálculo de preço 
de corridas por aplicativo, relacionando esse cálculo a uma função matemática de primeiro grau. 
Conseguiremos alterar os parâmetros da função e observar a flutuação dos preços das corridas, 
como ocorre na realidade devido às variações na demanda decorrente de condições climáticas, horários, etc.

## Passo 2
Para começar, verifique se a biblioteca da Smart Makers já está importada em seu MakeCode.
Se não estiver, clique na aba **+ Extensões**, copie o endereço "https://github.com/FuzzyMakers/pxt-smartMakers",
cole-o no campo de pesquisa da janela que se abriu e selecione a biblioteca.

## Passo 3
Primeiramente, verifique se seu código possui um laço ``||basic:sempre||``. Caso não tenha,
acesse a aba ``||basic:Básico||`` e adicione-o. Em seguida, acesse o menu de ``||Loops:Loops||`` e
adicione o bloco ``||Loops:enquanto falso executar||`` dentro do ``||basic:sempre||``.

```blocks
basic.forever(function () {
    while (false) {
    	
    }
})
```

## Passo 4
Vá à categoria ``||input:Entrada||`` e adicione o bloco de bordas triangulares ``||input:botão A é pressionado||``
para substituir o campo **falso** do bloco ``||Loops:enquanto falso executar||``.  

```blocks
basic.forever(function () {
    while (input.buttonIsPressed(Button.A)) {
    	
    }
})
```

## Passo 5
Acesse o menu ``||variables:Variáveis||`` e clique em **"Fazer uma variável..."**.
Vamos criar três variáveis chamadas: ``||variables:valor_final||``, ``||variables:tempo||`` e ``||variables:taxa||``. 
Por fim, adicione o bloco ``||variables:definir taxa para 0||`` que
aparecerá ao criá-la, dentro do laço ``||Loops:enquanto executar||``.  

```blocks
let taxa = 0
basic.forever(function () {
    while (input.buttonIsPressed(Button.A)) {
        taxa = 0
    }
})
```

## Passo 6
Agora, acesse o menu ``||math:Matemática||`` e use o bloco ``||math:arredonda 0||`` 
para substituir o valor **0** do bloco ``||variables:definir taxa para 0||``.

```blocks
let taxa = 0
basic.forever(function () {
    while (input.buttonIsPressed(Button.A)) {
        taxa = Math.round(0)
    }
})
```

## Passo 7
Retorne à categoria ``||math:Matemática||`` e adicione o bloco de divisão ``||math:0 / 0||`` 
para substituir o valor **0** do bloco ``||math:arredonda 0||``.

```blocks
let taxa = 0
basic.forever(function () {
    while (input.buttonIsPressed(Button.A)) {
        taxa = Math.round(0 / 0)
    }
})
```

## Passo 8
Acesse o menu ``||sensors:Sensores||`` e adicione o bloco ``||sensors:Valor do potenciômetro na porta P2||``
no primeiro campo da divisão.

```blocks
let taxa = 0
basic.forever(function () {
    while (input.buttonIsPressed(Button.A)) {
        taxa = Math.round(sensors.dimmerValue(InputPorts.P2) / 0)
    }
})
```

## Passo 9
Altere o segundo campo da divisão de **0** para **100**.

```blocks
let taxa = 0
basic.forever(function () {
    while (input.buttonIsPressed(Button.A)) {
        taxa = Math.round(sensors.dimmerValue(InputPorts.P2) / 100)
    }
})
```

## Passo 10
Vá à aba ``||basic:Básico||`` e adicione o bloco ``||basic:mostrar número||`` abaixo do 
bloco ``||variables:definir taxa||``, ainda dentro do bloco ``||Loops:enquanto executar||``.

```blocks
let taxa = 0
basic.forever(function () {
    while (input.buttonIsPressed(Button.A)) {
        taxa = Math.round(sensors.dimmerValue(InputPorts.P2) / 100)
        basic.showNumber(0)
    }
})
```

## Passo 11
Acesse o menu ``||variables:Variáveis||`` e selecione o bloco ``||variables:taxa||``
para substituir o valor **0** do bloco ``||basic:mostrar número||``.   

```blocks
let taxa = 0
basic.forever(function () {
    while (input.buttonIsPressed(Button.A)) {
        taxa = Math.round(sensors.dimmerValue(InputPorts.P2) / 100)
        basic.showNumber(taxa)
    }
})
```

## Passo 12
Duplique todo o bloco ``||Loops:enquanto executar||`` e posicione o novo bloco copiado abaixo do anterior
ainda dentro do laço ``||basic:sempre||``. Para duplicar, mantenha pressionado sobre o bloco desejado 
para aparecer a opção "duplicar".

```blocks
let taxa = 0
basic.forever(function () {
    while (input.buttonIsPressed(Button.A)) {
        taxa = Math.round(sensors.dimmerValue(InputPorts.P2) / 100)
        basic.showNumber(taxa)
    }
    while (input.buttonIsPressed(Button.A)) {
        taxa = Math.round(sensors.dimmerValue(InputPorts.P2) / 100)
        basic.showNumber(taxa)
    }
})
```

## Passo 13
Clique na seta do bloco de bordas triangulares ``||input:botão A é pressionado||`` e altere de 
``||input:botão A||`` para ``||input:botão B||``.

```blocks
let taxa = 0
basic.forever(function () {
    while (input.buttonIsPressed(Button.A)) {
        taxa = Math.round(sensors.dimmerValue(InputPorts.P2) / 100)
        basic.showNumber(taxa)
    }
    while (input.buttonIsPressed(Button.B)) {
        taxa = Math.round(sensors.dimmerValue(InputPorts.P2) / 100)
        basic.showNumber(taxa)
    }
})
```

## Passo 14
Em seguida, clique nas setas de ambos os blocos ``||variables:definir taxa||`` e ``||basic:mostrar número||`` ``||variables:taxa||``
para alterar para a variável ``||variables:tempo||``.

```blocks
let taxa = 0
let tempo = 0
basic.forever(function () {
    while (input.buttonIsPressed(Button.A)) {
        taxa = Math.round(sensors.dimmerValue(InputPorts.P2) / 100)
        basic.showNumber(taxa)
    }
    while (input.buttonIsPressed(Button.B)) {
        tempo = Math.round(sensors.dimmerValue(InputPorts.P2) / 100)
        basic.showNumber(tempo)
    }
})
```

## Passo 15
Acesse a categoria ``||input:Entrada||`` e adicione o bloco ``||input:no logotipo pressionado||``.

```blocks
let taxa = 0
let tempo = 0
input.onLogoEvent(TouchButtonEvent.Pressed, function () {
	
})
basic.forever(function () {
    while (input.buttonIsPressed(Button.A)) {
        taxa = Math.round(sensors.dimmerValue(InputPorts.P2) / 100)
        basic.showNumber(taxa)
    }
    while (input.buttonIsPressed(Button.B)) {
        tempo = Math.round(sensors.dimmerValue(InputPorts.P2) / 100)
        basic.showNumber(tempo)
    }
})
```

## Passo 16
Clique no menu ``||actuators:Atuadores||`` e adicione o bloco ``||actuators:Motor CC, definir velocidade 0 na porta P8||``
dentro desse novo laço.

```blocks
let taxa = 0
let tempo = 0
input.onLogoEvent(TouchButtonEvent.Pressed, function () {
    actuators.SetSpeedMotor(0, OutputPorts.P8)
})
basic.forever(function () {
    while (input.buttonIsPressed(Button.A)) {
        taxa = Math.round(sensors.dimmerValue(InputPorts.P2) / 100)
        basic.showNumber(taxa)
    }
    while (input.buttonIsPressed(Button.B)) {
        tempo = Math.round(sensors.dimmerValue(InputPorts.P2) / 100)
        basic.showNumber(tempo)
    }
})
```

## Passo 17
Altere o valor de velocidade de **0** para **1023** e a porta de **P8** para **P16**.

```blocks
let taxa = 0
let tempo = 0
input.onLogoEvent(TouchButtonEvent.Pressed, function () {
    actuators.SetSpeedMotor(1023, OutputPorts.P16)
})
basic.forever(function () {
    while (input.buttonIsPressed(Button.A)) {
        taxa = Math.round(sensors.dimmerValue(InputPorts.P2) / 100)
        basic.showNumber(taxa)
    }
    while (input.buttonIsPressed(Button.B)) {
        tempo = Math.round(sensors.dimmerValue(InputPorts.P2) / 100)
        basic.showNumber(tempo)
    }
})
```

## Passo 18
Depois desse bloco, adicione uma ``||basic:pausa (ms) 100||``, que pode ser encontrada
na categoria ``||basic:Básico||``.

```blocks
let taxa = 0
let tempo = 0
input.onLogoEvent(TouchButtonEvent.Pressed, function () {
    actuators.SetSpeedMotor(1023, OutputPorts.P16)
    basic.pause(100)
})
basic.forever(function () {
    while (input.buttonIsPressed(Button.A)) {
        taxa = Math.round(sensors.dimmerValue(InputPorts.P2) / 100)
        basic.showNumber(taxa)
    }
    while (input.buttonIsPressed(Button.B)) {
        tempo = Math.round(sensors.dimmerValue(InputPorts.P2) / 100)
        basic.showNumber(tempo)
    }
})
```

## Passo 19
Volte ao menu ``||math:Matemática||`` e adicione um bloco de multiplicação ``||math:0 x 0||`` no campo
de duração dessa ``||basic:pausa||``.

```blocks
let taxa = 0
let tempo = 0
input.onLogoEvent(TouchButtonEvent.Pressed, function () {
    actuators.SetSpeedMotor(1023, OutputPorts.P16)
    basic.pause(0 * 0)
})
basic.forever(function () {
    while (input.buttonIsPressed(Button.A)) {
        taxa = Math.round(sensors.dimmerValue(InputPorts.P2) / 100)
        basic.showNumber(taxa)
    }
    while (input.buttonIsPressed(Button.B)) {
        tempo = Math.round(sensors.dimmerValue(InputPorts.P2) / 100)
        basic.showNumber(tempo)
    }
})
```

## Passo 20
No primeiro campo dessa multiplicação, insira a variável ``||variables:tempo||``. Já no segundo
campo, altere o valor de **0** para **1000**.

```blocks
let tempo = 0
let taxa = 0
input.onLogoEvent(TouchButtonEvent.Pressed, function () {
    actuators.SetSpeedMotor(1023, OutputPorts.P16)
    basic.pause(tempo * 1000)
})
basic.forever(function () {
    while (input.buttonIsPressed(Button.A)) {
        taxa = Math.round(sensors.dimmerValue(InputPorts.P2) / 100)
        basic.showNumber(taxa)
    }
    while (input.buttonIsPressed(Button.B)) {
        tempo = Math.round(sensors.dimmerValue(InputPorts.P2) / 100)
        basic.showNumber(tempo)
    }
})
```

## Passo 21
Retorne à categoria ``||actuators:Atuadores||`` e adicione o bloco ``||actuators:Motor CC, parar motor na porta P8||``.

```blocks
let tempo = 0
let taxa = 0
input.onLogoEvent(TouchButtonEvent.Pressed, function () {
    actuators.SetSpeedMotor(1023, OutputPorts.P16)
    basic.pause(tempo * 1000)
    actuators.StopMotor(OutputPorts.P8)
})
basic.forever(function () {
    while (input.buttonIsPressed(Button.A)) {
        taxa = Math.round(sensors.dimmerValue(InputPorts.P2) / 100)
        basic.showNumber(taxa)
    }
    while (input.buttonIsPressed(Button.B)) {
        tempo = Math.round(sensors.dimmerValue(InputPorts.P2) / 100)
        basic.showNumber(tempo)
    }
})
```

## Passo 22
Altere a porta desse bloco de **P8** para **P16**.

```blocks
let tempo = 0
let taxa = 0
input.onLogoEvent(TouchButtonEvent.Pressed, function () {
    actuators.SetSpeedMotor(1023, OutputPorts.P16)
    basic.pause(tempo * 1000)
    actuators.StopMotor(OutputPorts.P16)
})
basic.forever(function () {
    while (input.buttonIsPressed(Button.A)) {
        taxa = Math.round(sensors.dimmerValue(InputPorts.P2) / 100)
        basic.showNumber(taxa)
    }
    while (input.buttonIsPressed(Button.B)) {
        tempo = Math.round(sensors.dimmerValue(InputPorts.P2) / 100)
        basic.showNumber(tempo)
    }
})
```

## Passo 23
Abaixo desse bloco, adicione um comando ``||variables:definir valor_final para 0||``, localizado na aba ``||variables:Variáveis||``. 
Se esse bloco não estiver aparecendo para você, basta selecionar o bloco de definição de outra variável
e apenas alterar para aquela que você deseja clicando em sua seta.

```blocks
let tempo = 0
let valor_final = 0
let taxa = 0
input.onLogoEvent(TouchButtonEvent.Pressed, function () {
    actuators.SetSpeedMotor(1023, OutputPorts.P16)
    basic.pause(tempo * 1000)
    actuators.StopMotor(OutputPorts.P16)
    valor_final = 0
})
basic.forever(function () {
    while (input.buttonIsPressed(Button.A)) {
        taxa = Math.round(sensors.dimmerValue(InputPorts.P2) / 100)
        basic.showNumber(taxa)
    }
    while (input.buttonIsPressed(Button.B)) {
        tempo = Math.round(sensors.dimmerValue(InputPorts.P2) / 100)
        basic.showNumber(tempo)
    }
})
```

## Passo 24
Volte ao menu ``||math:Matemática||`` e adicione um bloco de multiplicação ``||math:0 x 0||`` no campo
do valor de definição dessa variável.

```blocks
let tempo = 0
let valor_final = 0
let taxa = 0
input.onLogoEvent(TouchButtonEvent.Pressed, function () {
    actuators.SetSpeedMotor(1023, OutputPorts.P16)
    basic.pause(tempo * 1000)
    actuators.StopMotor(OutputPorts.P16)
    valor_final = 0 * 0
})
basic.forever(function () {
    while (input.buttonIsPressed(Button.A)) {
        taxa = Math.round(sensors.dimmerValue(InputPorts.P2) / 100)
        basic.showNumber(taxa)
    }
    while (input.buttonIsPressed(Button.B)) {
        tempo = Math.round(sensors.dimmerValue(InputPorts.P2) / 100)
        basic.showNumber(tempo)
    }
})
```

## Passo 25
Modifique os dois campos dessa multiplicação de **0** para as variáveis ``||variables:taxa||`` e ``||variables:tempo||``.

```blocks
let tempo = 0
let valor_final = 0
let taxa = 0
input.onLogoEvent(TouchButtonEvent.Pressed, function () {
    actuators.SetSpeedMotor(1023, OutputPorts.P16)
    basic.pause(tempo * 1000)
    actuators.StopMotor(OutputPorts.P16)
    valor_final = taxa * tempo
})
basic.forever(function () {
    while (input.buttonIsPressed(Button.A)) {
        taxa = Math.round(sensors.dimmerValue(InputPorts.P2) / 100)
        basic.showNumber(taxa)
    }
    while (input.buttonIsPressed(Button.B)) {
        tempo = Math.round(sensors.dimmerValue(InputPorts.P2) / 100)
        basic.showNumber(tempo)
    }
})
```

## Passo 26
Depois disso, adicione um comando para ``||basic:mostrar número||``, localizado na aba ``||basic:Básico||``.

```blocks
let tempo = 0
let valor_final = 0
let taxa = 0
input.onLogoEvent(TouchButtonEvent.Pressed, function () {
    actuators.SetSpeedMotor(1023, OutputPorts.P16)
    basic.pause(tempo * 1000)
    actuators.StopMotor(OutputPorts.P16)
    valor_final = taxa * tempo
    basic.showNumber(0)
})
basic.forever(function () {
    while (input.buttonIsPressed(Button.A)) {
        taxa = Math.round(sensors.dimmerValue(InputPorts.P2) / 100)
        basic.showNumber(taxa)
    }
    while (input.buttonIsPressed(Button.B)) {
        tempo = Math.round(sensors.dimmerValue(InputPorts.P2) / 100)
        basic.showNumber(tempo)
    }
})
```

## Passo 27
Altere o valor desse bloco de **0** para a variável ``||variables:valor_final||``.

```blocks
let tempo = 0
let valor_final = 0
let taxa = 0
input.onLogoEvent(TouchButtonEvent.Pressed, function () {
    actuators.SetSpeedMotor(1023, OutputPorts.P16)
    basic.pause(tempo * 1000)
    actuators.StopMotor(OutputPorts.P16)
    valor_final = taxa * tempo
    basic.showNumber(valor_final)
})
basic.forever(function () {
    while (input.buttonIsPressed(Button.A)) {
        taxa = Math.round(sensors.dimmerValue(InputPorts.P2) / 100)
        basic.showNumber(taxa)
    }
    while (input.buttonIsPressed(Button.B)) {
        tempo = Math.round(sensors.dimmerValue(InputPorts.P2) / 100)
        basic.showNumber(tempo)
    }
})
```

## Passo 28

Agora seu código está pronto! Baixe-o para o micro:bit e teste-o. 
- Pressione o botão A e use o potenciômetro para definir o valor da taxa.
- Em seguida, pressione o botão B e ajuste o potenciômetro para definir o valor do tempo.
- Pressione o logotipo para iniciar a viagem.
- Depois que o veículo parar, ele vai calcular e exibir o valor final da viagem.

```blocks
```

## Passo 29
Se necessário, confira o seu código clicando na lâmpada de dica.

```blocks
let tempo = 0
let valor_final = 0
let taxa = 0
input.onLogoEvent(TouchButtonEvent.Pressed, function () {
    actuators.SetSpeedMotor(1023, OutputPorts.P16)
    basic.pause(tempo * 1000)
    actuators.StopMotor(OutputPorts.P16)
    valor_final = taxa * tempo
    basic.showNumber(valor_final)
})
basic.forever(function () {
    while (input.buttonIsPressed(Button.A)) {
        taxa = Math.round(sensors.dimmerValue(InputPorts.P2) / 100)
        basic.showNumber(taxa)
    }
    while (input.buttonIsPressed(Button.B)) {
        tempo = Math.round(sensors.dimmerValue(InputPorts.P2) / 100)
        basic.showNumber(tempo)
    }
})
```

```package
fuzzyBot=github:FuzzyMakers/pxt-fuzzyMakers
```
