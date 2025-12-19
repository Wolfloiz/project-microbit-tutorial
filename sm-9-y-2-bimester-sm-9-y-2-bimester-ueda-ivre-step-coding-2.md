### @diffs true
# Queda Livre

## Passo 1
Nesse tutorial, vamos criar um código de programação para calcular a aceleração 
da gravidade a partir do experimento da torre de queda livre construída. O 
botão A do micro:bit vai acionar o servomotor para iniciar o movimento de queda,
enquanto o sensor infravermelho identifica quando o objeto chegou à base da torre.
Com os dados temporais desses momentos armazenados pelo micro:bit, aplicaremos
a fórmula para calcular a aceleração do movimento.

## Passo 2
Para começar, verifique se a biblioteca da Smart Makers já está importada 
em seu MakeCode. Se não estiver, clique na aba **+ Extensões**, 
copie o endereço "https://github.com/FuzzyMakers/pxt-smartMakers",
cole-o no campo de pesquisa da janela que se abriu e selecione a biblioteca.

## Passo 3
Acesse a aba ``||actuators:Atuadores||`` e adicione o comando 
``||actuators:Servo, definir posição 0 porta P8 modo Knob||`` dentro do bloco 
``||basic:no iniciar||``.  

```blocks
actuators.SetAngleServoKnob(0, OutputPorts.P8)
basic.forever(function () {
	
})
```

## Passo 4
Altere o valor da posição de **0** para **400** e a porta de ``||actuators:P8|``
para ``||actuators:P16||``.

```blocks
actuators.SetAngleServoKnob(400, OutputPorts.P16)
basic.forever(function () {
	
})
```

## Passo 5
Acesse o menu ``||input:Entrada||`` e adicione o bloco 
``||input:no botão A pressionado||`` ao código. 

```blocks
input.onButtonPressed(Button.A, function () {
	
})
actuators.SetAngleServoKnob(400, OutputPorts.P16)
basic.forever(function () {
	
})
```

## Passo 6
Volte à ``||actuators:Atuadores||`` e adicione outro comando 
``||actuators:Servo, definir posição 0 porta P8 modo Knob||`` dentro do bloco 
``||input:no botão A pressionado||``. 

```blocks
input.onButtonPressed(Button.A, function () {
    actuators.SetAngleServoKnob(0, OutputPorts.P8)
})
actuators.SetAngleServoKnob(400, OutputPorts.P16)
basic.forever(function () {
	
})
```

## Passo 7
Altere a porta de ``||actuators:P8|`` para ``||actuators:P16||``.

```blocks
input.onButtonPressed(Button.A, function () {
    actuators.SetAngleServoKnob(0, OutputPorts.P16)
})
actuators.SetAngleServoKnob(400, OutputPorts.P16)
basic.forever(function () {
	
})
```

## Passo 8
Vá à categoria ``||basic:Básico||`` e adicione uma ``||basic:pausa (ms) 100||``
dentro do ``||input:no botão A pressionado||``.    

```blocks
input.onButtonPressed(Button.A, function () {
    actuators.SetAngleServoKnob(0, OutputPorts.P16)
    basic.pause(100)
})
actuators.SetAngleServoKnob(400, OutputPorts.P16)
basic.forever(function () {
	
})
```

## Passo 9
Altere a duração dessa ``||basic:pausa||`` de **100 ms** para **200 ms**.

```blocks
input.onButtonPressed(Button.A, function () {
    actuators.SetAngleServoKnob(0, OutputPorts.P16)
    basic.pause(200)
})
actuators.SetAngleServoKnob(400, OutputPorts.P16)
basic.forever(function () {
	
})
```

## Passo 10
Acesse o menu ``||variables:Variáveis||`` e clique em **"Fazer uma variável..."**.
Vamos criar três variáveis chamadas: ``||variables:tempo_de_queda||``, 
``||variables:tempo_final||`` e ``||variables:tempo_inicial||``. 
Por fim, adicione o bloco ``||variables:definir tempo_inicial para 0||`` que
aparecerá ao criá-la, após o bloco de ``||basic:pausa||``.  

```blocks
input.onButtonPressed(Button.A, function () {
    actuators.SetAngleServoKnob(0, OutputPorts.P16)
    basic.pause(200)
    tempo_inicial = 0
})
let tempo_inicial = 0
actuators.SetAngleServoKnob(400, OutputPorts.P16)
basic.forever(function () {
	
})
```

## Passo 11
Vá à ``||math:Matemática||`` e insira o bloco de divisão 
``||math:0 / 0||`` dentro do bloco ``||variables:definir tempo_inicial para 0||``.

```blocks
input.onButtonPressed(Button.A, function () {
    actuators.SetAngleServoKnob(0, OutputPorts.P16)
    basic.pause(200)
    tempo_inicial = 0 / 0
})
let tempo_inicial = 0
actuators.SetAngleServoKnob(400, OutputPorts.P16)
basic.forever(function () {
	
})
```

## Passo 12
Clique em ``||input:Entrada||``. Em seguida, acesse o submenu ``||input:...mais||``
que se abrirá, para acessar blocos adicionais de ``||input:Entrada||``. Insira
o bloco ``||input:tempo de execução (ms)||`` no primeiro campo da divisão.

```blocks
input.onButtonPressed(Button.A, function () {
    actuators.SetAngleServoKnob(0, OutputPorts.P16)
    basic.pause(200)
    tempo_inicial = input.runningTime() / 0
})
let tempo_inicial = 0
actuators.SetAngleServoKnob(400, OutputPorts.P16)
basic.forever(function () {
	
})
```

## Passo 13
Altere o segundo campo da divisão de **0** para **1000**.

```blocks
input.onButtonPressed(Button.A, function () {
    actuators.SetAngleServoKnob(0, OutputPorts.P16)
    basic.pause(200)
    tempo_inicial = input.runningTime() / 1000
})
let tempo_inicial = 0
actuators.SetAngleServoKnob(400, OutputPorts.P16)
basic.forever(function () {
	
})
```

## Passo 14
Volte à aba ``||actuators:Atuadores||`` e adicione outro comando 
``||actuators:Servo, definir posição 0 porta P8 modo Knob||`` dentro do bloco 
``||input:no botão A pressionado||``. 

```blocks
input.onButtonPressed(Button.A, function () {
    actuators.SetAngleServoKnob(0, OutputPorts.P16)
    basic.pause(200)
    tempo_inicial = input.runningTime() / 1000
    actuators.SetAngleServoKnob(0, OutputPorts.P8)
})
let tempo_inicial = 0
actuators.SetAngleServoKnob(400, OutputPorts.P16)
basic.forever(function () {
	
})
```

## Passo 15
Altere o valor da posição de **0** para **400** e a porta de ``||actuators:P8|``
para ``||actuators:P16||``.

```blocks
input.onButtonPressed(Button.A, function () {
    actuators.SetAngleServoKnob(0, OutputPorts.P16)
    basic.pause(200)
    tempo_inicial = input.runningTime() / 1000
    actuators.SetAngleServoKnob(400, OutputPorts.P16)
})
let tempo_inicial = 0
actuators.SetAngleServoKnob(400, OutputPorts.P16)
basic.forever(function () {
	
})
```

## Passo 16
Acesse o menu ``||Logic:Lógica||`` e adicione um bloco ``||Logic:se então||`` 
dentro do laço ``||basic:sempre||``. 

```blocks
input.onButtonPressed(Button.A, function () {
    actuators.SetAngleServoKnob(0, OutputPorts.P16)
    basic.pause(200)
    tempo_inicial = input.runningTime() / 1000
    actuators.SetAngleServoKnob(400, OutputPorts.P16)
})
let tempo_inicial = 0
actuators.SetAngleServoKnob(400, OutputPorts.P16)
basic.forever(function () {
    if (true) {
    	
    }
})
```

## Passo 17
Retorne à ``||Logic:Lógica||`` e adicione um bloco comparador 
``||Logic:0 < 0||`` para substituir o campo **verdadeiro** do bloco 
``||Logic:se então||``.

```blocks
input.onButtonPressed(Button.A, function () {
    actuators.SetAngleServoKnob(0, OutputPorts.P16)
    basic.pause(200)
    tempo_inicial = input.runningTime() / 1000
    actuators.SetAngleServoKnob(400, OutputPorts.P16)
})
let tempo_inicial = 0
actuators.SetAngleServoKnob(400, OutputPorts.P16)
basic.forever(function () {
    if (0 < 0) {
    	
    }
})
```

## Passo 18
Clique na seta desse comparador para alterar o sinal de **<** para **>**.

```blocks
input.onButtonPressed(Button.A, function () {
    actuators.SetAngleServoKnob(0, OutputPorts.P16)
    basic.pause(200)
    tempo_inicial = input.runningTime() / 1000
    actuators.SetAngleServoKnob(400, OutputPorts.P16)
})
let tempo_inicial = 0
actuators.SetAngleServoKnob(400, OutputPorts.P16)
basic.forever(function () {
    if (0 > 0) {
    	
    }
})
```

## Passo 19
Acesse o menu de ``||sensors:Sensores||`` e insira o bloco  
``||sensors:Valor do sensor infravermelho na porta P2||`` no primeiro campo
do comparador, substituindo o valor **0**. 

```blocks
input.onButtonPressed(Button.A, function () {
    actuators.SetAngleServoKnob(0, OutputPorts.P16)
    basic.pause(200)
    tempo_inicial = input.runningTime() / 1000
    actuators.SetAngleServoKnob(400, OutputPorts.P16)
})
let tempo_inicial = 0
actuators.SetAngleServoKnob(400, OutputPorts.P16)
basic.forever(function () {
    if (sensors.infraredValue(InputPorts.P2) > 0) {
    	
    }
})
```

## Passo 20
Altere a porta do sensor de ``||sensors:P2||`` para ``||sensors:P1||`` e o valor
do segundo campo do comparador de **0** para **900**.

```blocks
input.onButtonPressed(Button.A, function () {
    actuators.SetAngleServoKnob(0, OutputPorts.P16)
    basic.pause(200)
    tempo_inicial = input.runningTime() / 1000
    actuators.SetAngleServoKnob(400, OutputPorts.P16)
})
let tempo_inicial = 0
actuators.SetAngleServoKnob(400, OutputPorts.P16)
basic.forever(function () {
    if (sensors.infraredValue(InputPorts.P1) > 900) {
    	
    }
})
```

## Passo 21
Retorne ao menu ``||variables:Variáveis||`` e adicione um bloco 
``||variables:definir tempo_final para 0||`` dentro do ``||logic:então||``.

 **Dica:** Se no seu menu aparacer o bloco de definição com outra variável,
 basta adicioná-los e clicar na seta para alterar para a variável desejada.

```blocks
input.onButtonPressed(Button.A, function () {
    actuators.SetAngleServoKnob(0, OutputPorts.P16)
    basic.pause(200)
    tempo_inicial = input.runningTime() / 1000
    actuators.SetAngleServoKnob(400, OutputPorts.P16)
})
let tempo_final = 0
let tempo_inicial = 0
actuators.SetAngleServoKnob(400, OutputPorts.P16)
basic.forever(function () {
    if (sensors.infraredValue(InputPorts.P1) > 900) {
        tempo_final = 0
    }
})
```

## Passo 22
Substitua o **0** desse bloco de definição por um bloco de divisão 
``||math:0 / 0||``, localizado na aba ``||math:Matemática||``. 

```blocks
input.onButtonPressed(Button.A, function () {
    actuators.SetAngleServoKnob(0, OutputPorts.P16)
    basic.pause(200)
    tempo_inicial = input.runningTime() / 1000
    actuators.SetAngleServoKnob(400, OutputPorts.P16)
})
let tempo_final = 0
let tempo_inicial = 0
actuators.SetAngleServoKnob(400, OutputPorts.P16)
basic.forever(function () {
    if (sensors.infraredValue(InputPorts.P1) > 900) {
        tempo_final = (0 / 0)
    }
})
```

## Passo 23
Retorne ao submenu ``||input:...mais||`` da categoria ``||input:Entrada||``
e insira o bloco ``||input:tempo de execução (ms)||`` no primeiro campo da 
divisão.

```blocks
input.onButtonPressed(Button.A, function () {
    actuators.SetAngleServoKnob(0, OutputPorts.P16)
    basic.pause(200)
    tempo_inicial = input.runningTime() / 1000
    actuators.SetAngleServoKnob(400, OutputPorts.P16)
})
let tempo_final = 0
let tempo_inicial = 0
actuators.SetAngleServoKnob(400, OutputPorts.P16)
basic.forever(function () {
    if (sensors.infraredValue(InputPorts.P1) > 900) {
        tempo_final = input.runningTime() / 0
    }
})
```

## Passo 24
Altere o segundo campo da divisão de **0** para **1000**.

```blocks
input.onButtonPressed(Button.A, function () {
    actuators.SetAngleServoKnob(0, OutputPorts.P16)
    basic.pause(200)
    tempo_inicial = input.runningTime() / 1000
    actuators.SetAngleServoKnob(400, OutputPorts.P16)
})
let tempo_final = 0
let tempo_inicial = 0
actuators.SetAngleServoKnob(400, OutputPorts.P16)
basic.forever(function () {
    if (sensors.infraredValue(InputPorts.P1) > 900) {
        tempo_final = input.runningTime() / 1000
    }
})
```

## Passo 25
Volte ao menu ``||variables:Variáveis||`` e adicione um bloco 
``||variables:definir tempo_de_queda para 0||`` abaixo do bloco de definição
posicionado anteriormente. Certifique-se de alterar para a variável 
``||variables:tempo_de_queda||``.

```blocks
input.onButtonPressed(Button.A, function () {
    actuators.SetAngleServoKnob(0, OutputPorts.P16)
    basic.pause(200)
    tempo_inicial = input.runningTime() / 1000
    actuators.SetAngleServoKnob(400, OutputPorts.P16)
})
let tempo_de_queda = 0
let tempo_final = 0
let tempo_inicial = 0
actuators.SetAngleServoKnob(400, OutputPorts.P16)
basic.forever(function () {
    if (sensors.infraredValue(InputPorts.P1) > 900) {
        tempo_final = input.runningTime() / 1000
        tempo_de_queda = 0
    }
})
```

## Passo 26
Substitua o **0** desse bloco de definição por um bloco de subtração 
``||math:0 - 0||``, localizado na aba ``||math:Matemática||``. 

```blocks
input.onButtonPressed(Button.A, function () {
    actuators.SetAngleServoKnob(0, OutputPorts.P16)
    basic.pause(200)
    tempo_inicial = input.runningTime() / 1000
    actuators.SetAngleServoKnob(400, OutputPorts.P16)
})
let tempo_de_queda = 0
let tempo_final = 0
let tempo_inicial = 0
actuators.SetAngleServoKnob(400, OutputPorts.P16)
basic.forever(function () {
    if (sensors.infraredValue(InputPorts.P1) > 900) {
        tempo_final = input.runningTime() / 1000
        tempo_de_queda = 0 - 0
    }
})
```

## Passo 27
Substitua os campos dessa subtração pelas variáveis 
``||variables:tempo_final||`` e ``||variables:tempo_inicial||`` respectivamente.

```blocks
input.onButtonPressed(Button.A, function () {
    actuators.SetAngleServoKnob(0, OutputPorts.P16)
    basic.pause(200)
    tempo_inicial = input.runningTime() / 1000
    actuators.SetAngleServoKnob(400, OutputPorts.P16)
})
let tempo_de_queda = 0
let tempo_final = 0
let tempo_inicial = 0
actuators.SetAngleServoKnob(400, OutputPorts.P16)
basic.forever(function () {
    if (sensors.infraredValue(InputPorts.P1) > 900) {
        tempo_final = input.runningTime() / 1000
        tempo_de_queda = tempo_final - tempo_inicial
    }
})
```

## Passo 28
Acesse a aba ``||basic:Básico||`` e adicione o comando ``||basic:mostrar número||``
dentro do ``||logic:então||``.

```blocks
input.onButtonPressed(Button.A, function () {
    actuators.SetAngleServoKnob(0, OutputPorts.P16)
    basic.pause(200)
    tempo_inicial = input.runningTime() / 1000
    actuators.SetAngleServoKnob(400, OutputPorts.P16)
})
let tempo_de_queda = 0
let tempo_final = 0
let tempo_inicial = 0
actuators.SetAngleServoKnob(400, OutputPorts.P16)
basic.forever(function () {
    if (sensors.infraredValue(InputPorts.P1) > 900) {
        tempo_final = input.runningTime() / 1000
        tempo_de_queda = tempo_final - tempo_inicial
        basic.showNumber(0)
    }
})
```

## Passo 29
Substitua o **0** desse comando por um bloco de divisão 
``||math:0 / 0||``, localizado na aba ``||math:Matemática||``. 

```blocks
input.onButtonPressed(Button.A, function () {
    actuators.SetAngleServoKnob(0, OutputPorts.P16)
    basic.pause(200)
    tempo_inicial = input.runningTime() / 1000
    actuators.SetAngleServoKnob(400, OutputPorts.P16)
})
let tempo_de_queda = 0
let tempo_final = 0
let tempo_inicial = 0
actuators.SetAngleServoKnob(400, OutputPorts.P16)
basic.forever(function () {
    if (sensors.infraredValue(InputPorts.P1) > 900) {
        tempo_final = input.runningTime() / 1000
        tempo_de_queda = tempo_final - tempo_inicial
        basic.showNumber(0 / 0)
    }
})
```

## Passo 30
Altere o primeiro campo da divisão de **0** para **0.48** (com ponto). Em seguida,
insira um bloco de multiplicação ``||math:0 x 0||`` no segundo campo da divisão. 

```blocks
input.onButtonPressed(Button.A, function () {
    actuators.SetAngleServoKnob(0, OutputPorts.P16)
    basic.pause(200)
    tempo_inicial = input.runningTime() / 1000
    actuators.SetAngleServoKnob(400, OutputPorts.P16)
})
let tempo_de_queda = 0
let tempo_final = 0
let tempo_inicial = 0
actuators.SetAngleServoKnob(400, OutputPorts.P16)
basic.forever(function () {
    if (sensors.infraredValue(InputPorts.P1) > 900) {
        tempo_final = input.runningTime() / 1000
        tempo_de_queda = tempo_final - tempo_inicial
        basic.showNumber(0.48 / (0 * 0))
    }
})
```

## Passo 31
Modifique ambos os campos da multiplicação para a variável 
``||variables:tempo_de_queda||``, substituindo os valores **0**.

```blocks
input.onButtonPressed(Button.A, function () {
    actuators.SetAngleServoKnob(0, OutputPorts.P16)
    basic.pause(200)
    tempo_inicial = input.runningTime() / 1000
    actuators.SetAngleServoKnob(400, OutputPorts.P16)
})
let tempo_de_queda = 0
let tempo_final = 0
let tempo_inicial = 0
actuators.SetAngleServoKnob(400, OutputPorts.P16)
basic.forever(function () {
    if (sensors.infraredValue(InputPorts.P1) > 900) {
        tempo_final = input.runningTime() / 1000
        tempo_de_queda = tempo_final - tempo_inicial
        basic.showNumber(0.48 / (tempo_de_queda * tempo_de_queda))
    }
})
```

## Passo 32

Seu código está pronto! Baixe-o para o micro:bit e teste-o. 
Pressione o botão A do micro:bit para soltar o objeto e observe o valor da 
aceleração sendo indicado na matriz de LEDs.

```blocks
```

## Passo 33
Se necessário, confira o seu código clicando na lâmpada de dica.

```blocks
input.onButtonPressed(Button.A, function () {
    actuators.SetAngleServoKnob(0, OutputPorts.P16)
    basic.pause(200)
    tempo_inicial = input.runningTime() / 1000
    actuators.SetAngleServoKnob(400, OutputPorts.P16)
})
let tempo_de_queda = 0
let tempo_final = 0
let tempo_inicial = 0
actuators.SetAngleServoKnob(400, OutputPorts.P16)
basic.forever(function () {
    if (sensors.infraredValue(InputPorts.P1) > 900) {
        tempo_final = input.runningTime() / 1000
        tempo_de_queda = tempo_final - tempo_inicial
        basic.showNumber(0.48 / (tempo_de_queda * tempo_de_queda))
    }
})
```

```package
fuzzyBot=github:FuzzyMakers/pxt-fuzzyMakers
```
