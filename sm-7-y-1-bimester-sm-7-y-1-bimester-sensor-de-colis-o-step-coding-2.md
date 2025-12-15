### @diffs true
# Sensor de Colisão

## Passo 1
Nesse tutorial, vamos programar um veículo que usa o sensor infravermelho como um detector de colisões.
Ao identificar um obstáculo à frente, o veículo deve parar e tocar um som através do micro:bit.
Será uma boa oportunidade para entendermos como criar, modificar e reaproveitar variáveis em nossos códigos de programação.

## Passo 2
Para começar, verifique se a biblioteca da Smart Makers já está importada em seu MakeCode.
Se não estiver, clique na aba **+ Extensões**, copie o endereço "https://github.com/FuzzyMakers/pxt-smartMakers",
cole-o no campo de pesquisa da janela que se abriu e selecione a biblioteca.

## Passo 3
Acesse a aba ``||input:Entrada||`` e adicione dois laços ``||input:no botão A pressionado||`` em sua área de programação.
Clique na seta para alterar o botão de um deles de ``||input:botão A||`` para ``||input:botão B||``.

```blocks
input.onButtonPressed(Button.A, function () {
	
})
input.onButtonPressed(Button.B, function () {
	
})
basic.forever(function () {
	
})
```

## Passo 4
Acesse o menu ``||variables:Variáveis||`` e clique em **"Fazer uma variável..."**.
Vamos criar três variáveis chamadas: ``||variables:proximidade||``, ``||variables:som||`` e ``||variables:velocidade||``. 
Por fim, adicione o bloco ``||variables:definir velocidade para 0||`` que
aparecerá ao criá-la, dentro do laço ``||basic:no iniciar||``.  

```blocks
input.onButtonPressed(Button.A, function () {
	
})
input.onButtonPressed(Button.B, function () {
	
})
let velocidade = 0
basic.forever(function () {
	
})
```

## Passo 5
Altere o valor da variável ``||variables:velocidade||`` nesse bloco de definição de **0** para **300**.

```blocks
input.onButtonPressed(Button.A, function () {
	
})
input.onButtonPressed(Button.B, function () {
	
})
let velocidade = 300
basic.forever(function () {
	
})
```

## Passo 6
Retorne ao menu de ``||variables:Variáveis||`` e adicione um bloco ``||variables:alterar velocidade por 1||``
dentro dos laços ``||input:no botão A pressionado||`` e ``||input:no botão B pressionado||``. 


```blocks
input.onButtonPressed(Button.A, function () {
    velocidade += 1
})
input.onButtonPressed(Button.B, function () {
    velocidade += 1
})
let velocidade = 300
basic.forever(function () {
	
})
```

## Passo 7
No bloco ``||input:no botão A pressionado||``, edite o valor de alteração da variável de **1** para **50**.
Enquanto isso, no bloco ``||input:no botão B pressionado||``, edite o valor de **1** para **-50**.

```blocks
input.onButtonPressed(Button.A, function () {
    velocidade += 50
})
input.onButtonPressed(Button.B, function () {
    velocidade += -50
})
let velocidade = 300
basic.forever(function () {
	
})
```

## Passo 8
Agora, prosseguindo para dentro do laço ``||basic:sempre||``, adicione dois blocos ``||variables:definir proximidade para 0||`` e 
``||variables:definir som para 0||`` em sequência. Esse bloco é encontrado na aba ``||variables:Variáveis||``. Se a variável estiver diferente em seu bloco,
basta adicioná-lo normalmente, clicar na seta e alterar para a variável desejada. 

```blocks
input.onButtonPressed(Button.A, function () {
    velocidade += 50
})
input.onButtonPressed(Button.B, function () {
    velocidade += -50
})
let som = 0
let proximidade = 0
let velocidade = 300
basic.forever(function () {
    proximidade = 0
    som = 0
})
```

## Passo 9
A variável ``||variables:proximidade||`` deve ser definida para o ``||sensors:Valor do Sensor Infravermelho na porta P1||``.
Esse bloco está localizado na categoria ``||sensors:Sensores||``*(com a porta P2)*, porém certifique-se de alterar a porta de **P2** para **P1**.

```blocks
input.onButtonPressed(Button.A, function () {
    velocidade += 50
})
input.onButtonPressed(Button.B, function () {
    velocidade += -50
})
let som = 0
let proximidade = 0
let velocidade = 300
basic.forever(function () {
    proximidade = sensors.infraredValue(InputPorts.P1)
    som = 0
})
```

## Passo 10
Já a variável ``||variables:som||`` deve ser definida como o ``||sensors:Valor do potenciômetro na porta P2||``, 
também localizado na categoria ``||sensors:Sensores||``.

```blocks
input.onButtonPressed(Button.A, function () {
    velocidade += 50
})
input.onButtonPressed(Button.B, function () {
    velocidade += -50
})
let som = 0
let proximidade = 0
let velocidade = 300
basic.forever(function () {
    proximidade = sensors.infraredValue(InputPorts.P1)
    som = sensors.dimmerValue(InputPorts.P2)
})
```

## Passo 11
Feito isso, acesse a aba ``||Logic:Lógica||`` e insira o bloco ``||Logic:se verdadeiro então||``
dentro do ``||basic:sempre||``.  

```blocks
input.onButtonPressed(Button.A, function () {
    velocidade += 50
})
input.onButtonPressed(Button.B, function () {
    velocidade += -50
})
let som = 0
let proximidade = 0
let velocidade = 300
basic.forever(function () {
    proximidade = sensors.infraredValue(InputPorts.P1)
    som = sensors.dimmerValue(InputPorts.P2)
    if (true) {
    	
    } else {
    	
    }
})
```

## Passo 12
Retorne ao menu de ``||Logic:Lógica||`` e use o bloco comparador ``||Logic:0 < 0||``
para substituir o campo **verdadeiro** do ``||Logic:se então||``. Antes de avançar, modifique o 
sinal do comparador de **<** para **>**.

```blocks
input.onButtonPressed(Button.A, function () {
    velocidade += 50
})
input.onButtonPressed(Button.B, function () {
    velocidade += -50
})
let som = 0
let proximidade = 0
let velocidade = 300
basic.forever(function () {
    proximidade = sensors.infraredValue(InputPorts.P1)
    som = sensors.dimmerValue(InputPorts.P2)
    if (0 > 0) {
    	
    } else {
    	
    }
})
```

## Passo 13
Acesse a aba ``||variables:Variáveis||`` e use o bloco ``||variables:proximidade||`` para substituir 
o primeiro **0** do comparador. Em seguida, altere o segundo campo de **0** para **400**. 

```blocks
input.onButtonPressed(Button.A, function () {
    velocidade += 50
})
input.onButtonPressed(Button.B, function () {
    velocidade += -50
})
let som = 0
let proximidade = 0
let velocidade = 300
basic.forever(function () {
    proximidade = sensors.infraredValue(InputPorts.P1)
    som = sensors.dimmerValue(InputPorts.P2)
    if (proximidade > 400) {
    	
    } else {
    	
    }
})
```

## Passo 14
Dentro do ``||Logic:então||``, adicione um bloco ``||variables:definir velocidade para 0||``. 
Esse bloco vai garantir que o valor de ``||variables:velocidade||`` seja nulo no momento que 
o veículo identificar um obstáculo.

```blocks
input.onButtonPressed(Button.A, function () {
    velocidade += 50
})
input.onButtonPressed(Button.B, function () {
    velocidade += -50
})
let som = 0
let proximidade = 0
let velocidade = 300
basic.forever(function () {
    proximidade = sensors.infraredValue(InputPorts.P1)
    som = sensors.dimmerValue(InputPorts.P2)
    if (proximidade > 400) {
        velocidade = 0
    } else {
    	
    }
})
```

## Passo 15
Abaixo da definição de ``||variables:velocidade||``, adicione um bloco ``||music:toque (Hz) C Médio||`` localizado
na categoria ``||music:Música||``.

```blocks
input.onButtonPressed(Button.A, function () {
    velocidade += 50
})
input.onButtonPressed(Button.B, function () {
    velocidade += -50
})
let som = 0
let proximidade = 0
let velocidade = 300
basic.forever(function () {
    proximidade = sensors.infraredValue(InputPorts.P1)
    som = sensors.dimmerValue(InputPorts.P2)
    if (proximidade > 400) {
        velocidade = 0
        music.ringTone(262)
    } else {
    	
    }
})
```

## Passo 16
Retorne à aba ``||variables:Variáveis||`` e use o bloco da variável ``||variables:som||`` para
substituir o **C Médio** dentro do bloco ``||music:toque (Hz)||``.

```blocks
input.onButtonPressed(Button.A, function () {
    velocidade += 50
})
input.onButtonPressed(Button.B, function () {
    velocidade += -50
})
let som = 0
let proximidade = 0
let velocidade = 300
basic.forever(function () {
    proximidade = sensors.infraredValue(InputPorts.P1)
    som = sensors.dimmerValue(InputPorts.P2)
    if (proximidade > 400) {
        velocidade = 0
        music.ringTone(som)
    } else {
    	
    }
})
```

## Passo 17
Prosseguindo para dentro do ``||logic:senão||``, adicione um bloco ``||music:stop all sounds||``, 
localizado na categoria ``||music:Música||``.

```blocks
input.onButtonPressed(Button.A, function () {
    velocidade += 50
})
input.onButtonPressed(Button.B, function () {
    velocidade += -50
})
let som = 0
let proximidade = 0
let velocidade = 300
basic.forever(function () {
    proximidade = sensors.infraredValue(InputPorts.P1)
    som = sensors.dimmerValue(InputPorts.P2)
    if (proximidade > 400) {
        velocidade = 0
        music.ringTone(som)
    } else {
        music.stopAllSounds()
    }
})
```

## Passo 18
Agora, fora do bloco ``||Logic:se então senão||``, adicione um comando ``||actuators:Motor CC, definir velocidade 0 na porta P8||`` dentro do 
``||basic:sempre||``. Altere o valor de **0** para a variável ``||variables:velocidade||`` e a porta de **P8** para **P16**.

```blocks
input.onButtonPressed(Button.A, function () {
    velocidade += 50
})
input.onButtonPressed(Button.B, function () {
    velocidade += -50
})
let som = 0
let proximidade = 0
let velocidade = 300
basic.forever(function () {
    proximidade = sensors.infraredValue(InputPorts.P1)
    som = sensors.dimmerValue(InputPorts.P2)
    if (proximidade > 400) {
        velocidade = 0
        music.ringTone(som)
    } else {
        music.stopAllSounds()
    }
    actuators.SetSpeedMotor(velocidade, OutputPorts.P16)
})
```

## Passo 19

Agora seu código está pronto! Baixe-o para o micro:bit e teste-o. 
- O botão A aumenta a velocidade;
- O botão B reduz a velocidade.
- O potenciômetro vai ajustar a frequência do som que é tocado ao identificar um obstáculo.
```blocks
```

## Passo 20
Se necessário, confira o seu código clicando na lâmpada de dica.

```blocks
input.onButtonPressed(Button.A, function () {
    velocidade += 50
})
input.onButtonPressed(Button.B, function () {
    velocidade += -50
})
let som = 0
let proximidade = 0
let velocidade = 300
basic.forever(function () {
    proximidade = sensors.infraredValue(InputPorts.P1)
    som = sensors.dimmerValue(InputPorts.P2)
    if (proximidade > 400) {
        velocidade = 0
        music.ringTone(som)
    } else {
        music.stopAllSounds()
    }
    actuators.SetSpeedMotor(velocidade, OutputPorts.P16)
})
```

```package
fuzzyBot=github:FuzzyMakers/pxt-fuzzyMakers
```
