### @diffs true
# Velocidade Média

## Passo 1
Nesta atividade, depois de montar um carrinho e o percurso com um sensor infravermelho, 
vamos programar a lógica de cálculo da velocidade média do veículo durante o experimento.
Para isso, vamos usar o botão A do micro:bit para iniciar a contagem de tempo. O sensor
infravermelho será responsável por identificar quando o veículo passa da linha de chegada, 
cujo tempo será salvo em uma variável e então calcularemos a velocidade média através de fórmulas matemáticas.


## Passo 2
Para começar, verifique se a biblioteca da Smart Makers já está importada em seu MakeCode.
Se não estiver, clique na aba **+ Extensões**, copie o endereço "https://github.com/FuzzyMakers/pxt-smartMakers",
cole-o no campo de pesquisa da janela que se abriu e selecione a biblioteca.

## Passo 3
Acesse o menu ``||Input:Entrada||`` e adicione um bloco``||Input:no botão A pressionado||`` à sua área de programação.
Aproveite e certifique-se de que seu código tenha um laço ``||basic:sempre||``. Caso não tenha,
acesse a aba ``||basic:Básico||`` e adicione-o.

```blocks
input.onButtonPressed(Button.A, function () {
	
})
basic.forever(function () {
	
})
```

## Passo 4
Acesse o menu ``||variables:Variáveis||`` e clique em **"Fazer uma variável..."**.
Vamos criar duas variáveis chamadas: ``||variables:tempo||`` e ``||variables:inicio||``.
Por fim, adicione o bloco ``||variables:definir inicio para 0||`` que
aparecerá ao criá-la, dentro do laço ``||Input:no botão A pressionado||``.  

```blocks
let inicio = 0
input.onButtonPressed(Button.A, function () {
    inicio = 0
})
basic.forever(function () {
	
})
```

## Passo 5
Agora, acesse o menu ``||math:Matemática||`` e use o bloco de divisão ``||math:0 / 0||`` 
para substituir o valor **0** do bloco ``||variables:definir inicio para 0||``.

```blocks
let inicio = 0
input.onButtonPressed(Button.A, function () {
    inicio = 0 / 0
})
basic.forever(function () {
	
})
```

## Passo 6
Clique na aba ``||Input:Entrada||``. Ao fazer isso, acesse o submenu ``||Input:... mais||`` que vai se abrir abaixo de ``||Input:Entrada||``.
Nesse submenu, selecione o bloco ``||Input:tempo de execução (ms)||`` para substituir o primeiro campo da divisão.

```blocks
let inicio = 0
input.onButtonPressed(Button.A, function () {
    inicio = input.runningTime() / 0
})
basic.forever(function () {
	
})
```

## Passo 7
Altere o segundo campo do bloco de divisão de **0** para **1000**.

```blocks
let inicio = 0
input.onButtonPressed(Button.A, function () {
    inicio = input.runningTime() / 1000
})
basic.forever(function () {
	
})
```

## Passo 8
Agora, dentro do laço ``||basic:sempre||``, adicione um ``||logic:se então||``, 
localizado na aba ``||logic:Lógica||``.

```blocks
let inicio = 0
input.onButtonPressed(Button.A, function () {
    inicio = input.runningTime() / 1000
})
basic.forever(function () {
    if (true) {
    	
    }
})
```

## Passo 9
Retorne à aba ``||logic:Lógica||`` e substitua o **verdadeiro** pelo comparador ``||logic:0 < 0||``.
Altere o seu sinal de **<** para **>**.

```blocks
let inicio = 0
input.onButtonPressed(Button.A, function () {
    inicio = input.runningTime() / 1000
})
basic.forever(function () {
    if (0 > 0) {
    	
    }
})
```

## Passo 10
Acesse o menu ``||sensors:Sensores||`` e use o bloco ``||sensors:Valor do sensor infravermelho na porta P2||`` 
para substituir o primeiro **0** do comparador. Em seguida, altere a porta desse bloco 
de **P2** para **P1** e o segundo campo do comparador de **0** para **300**.

```blocks
let inicio = 0
input.onButtonPressed(Button.A, function () {
    inicio = input.runningTime() / 1000
})
basic.forever(function () {
    if (sensors.infraredValue(InputPorts.P1) > 300) {
    	
    }
})
```

## Passo 11
Dentro do ``||logic:então||``, adicione o bloco ``||variables:definir tempo para 0||``,
localizado no menu  ``||variables:Variáveis||``. Se o seu bloco estiver com a variável ``||variables:inicio||``, 
basta clicar na seta para alterar para ``||variables:tempo||``.

```blocks
let inicio = 0
let tempo = 0
input.onButtonPressed(Button.A, function () {
    inicio = input.runningTime() / 1000
})
basic.forever(function () {
    if (sensors.infraredValue(InputPorts.P1) > 300) {
        tempo = 0
    }
})
```

## Passo 12
Retorne ao menu ``||math:Matemática||`` e insira o bloco de subtração ``||math:0 - 0||`` substituindo o campo **0**
do bloco ``||variables:definir tempo para 0||``.

```blocks
let inicio = 0
let tempo = 0
input.onButtonPressed(Button.A, function () {
    inicio = input.runningTime() / 1000
})
basic.forever(function () {
    if (sensors.infraredValue(InputPorts.P1) > 300) {
        tempo = 0 - 0
    }
})
```

## Passo 13
Volte ao menu ``||math:Matemática||`` e insira um bloco de divisão ``||math:0 / 0||``
no primeiro campo da subtração do passo anterior.

```blocks
let inicio = 0
let tempo = 0
input.onButtonPressed(Button.A, function () {
    inicio = input.runningTime() / 1000
})
basic.forever(function () {
    if (sensors.infraredValue(InputPorts.P1) > 300) {
        tempo = 0 / 0 - 0
    }
})
```

## Passo 14
O primeiro campo da divisão será o bloco ``||Input:tempo de execução (ms)||``, encontrado 
no submenu ``||Input:...mais||`` da aba ``||Input:Entrada||``.  

```blocks
let inicio = 0
let tempo = 0
input.onButtonPressed(Button.A, function () {
    inicio = input.runningTime() / 1000
})
basic.forever(function () {
    if (sensors.infraredValue(InputPorts.P1) > 300) {
        tempo = input.runningTime() / 0 - 0
    }
})
```

## Passo 15
Altere o segundo campo da divisão de **0** para **1000**. Em seguida, acesse a aba ``||variables:Variáveis||``
e selecione o bloco de bordas redondas da variável ``||variables:inicio||`` para substituir o último campo da subtração.

```blocks
let inicio = 0
let tempo = 0
input.onButtonPressed(Button.A, function () {
    inicio = input.runningTime() / 1000
})
basic.forever(function () {
    if (sensors.infraredValue(InputPorts.P1) > 300) {
        tempo = input.runningTime() / 1000 - inicio
    }
})
```

## Passo 16
Acesse a aba ``||basic:Básico||`` e adicione o comando ``||basic:mostrar número||`` dentro do 
laço ``||logic:então||``.

```blocks
let inicio = 0
let tempo = 0
input.onButtonPressed(Button.A, function () {
    inicio = input.runningTime() / 1000
})
basic.forever(function () {
    if (sensors.infraredValue(InputPorts.P1) > 300) {
        tempo = input.runningTime() / 1000 - inicio
        basic.showNumber(0)
    }
})
```

## Passo 17
Volte à aba ``||math:Matemática||`` e adicione um bloco de divisão ``||math:0 / 0||`` para substituir
o campo **0** do ``||basic:mostrar número||``.

```blocks
let inicio = 0
let tempo = 0
input.onButtonPressed(Button.A, function () {
    inicio = input.runningTime() / 1000
})
basic.forever(function () {
    if (sensors.infraredValue(InputPorts.P1) > 300) {
        tempo = input.runningTime() / 1000 - inicio
        basic.showNumber(0 / 0)
    }
})
```

## Passo 18
Edite o primeiro campo da divisão inserindo o valor **0.15** (com ponto mesmo!) e o segundo
campo com o valor da variável ``||variables:tempo||``. 

```blocks
let inicio = 0
let tempo = 0
input.onButtonPressed(Button.A, function () {
    inicio = input.runningTime() / 1000
})
basic.forever(function () {
    if (sensors.infraredValue(InputPorts.P1) > 300) {
        tempo = input.runningTime() / 1000 - inicio
        basic.showNumber(0.15 / tempo)
    }
})
```

## Passo 19
Agora seu código está pronto! Baixe-o para o micro:bit e 
teste-o. Use o botão A para iniciar a contagem de tempo, passe com o carrinho 
em frente ao sensor infravermelho e veja o valor da velocidade média ser exibida nos
LEDs do micro:bit.

```blocks
```

## Passo 20
Se necessário, confira o seu código clicando na lâmpada de dica.

```blocks
let inicio = 0
let tempo = 0
input.onButtonPressed(Button.A, function () {
    inicio = input.runningTime() / 1000
})
basic.forever(function () {
    if (sensors.infraredValue(InputPorts.P1) > 300) {
        tempo = input.runningTime() / 1000 - inicio
        basic.showNumber(0.15 / tempo)
    }
})
```

```package
fuzzyBot=github:FuzzyMakers/pxt-fuzzyMakers
```
