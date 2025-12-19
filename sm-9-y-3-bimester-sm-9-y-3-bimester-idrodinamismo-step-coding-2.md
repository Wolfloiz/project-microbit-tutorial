### @diffs true
# Hidrodinamismo

## Passo 1
Neste tutorial, vamos programar o movimento de um tubarão e sua mordida.
## Passo 2
Para começar, verifique se a biblioteca da Smart Makers já está importada 
em seu MakeCode. Se não estiver, clique na aba **+ Extensões**, 
copie o endereço "https://github.com/FuzzyMakers/pxt-smartMakers", 
cole-o no campo de pesquisa da janela que se abriu e selecione a biblioteca. 

## Passo 3
No menu ``||actuators:Atuadores||`` busque o bloco ``||actuators:Motor CC, definir velocidade 0 na porta P8||`` e adicione-o
dentro do bloco ``||basic:no iniciar||``.
Mude o valor da velocidade para **500**.


```blocks
actuators.SetSpeedMotor(500, OutputPorts.P8)
```

## Passo 4
Volte à categoria ``||actuators:Atuadores||``, pegue o bloco ``||actuators:Servo, definir posição 0 porta P8 modo Knob||``
e insira-o no final do bloco ``||basic:no iniciar||``.
Altere a porta para ``||actuators:P16||``.

```blocks
actuators.SetSpeedMotor(500, OutputPorts.P8)
actuators.SetAngleServoKnob(0, OutputPorts.P16)
```

## Passo 5


Clique no menu ``||Advanced:Avançado||``, acesse ``||Functions:Funções||`` e 
clique em **Fazer uma função...**.
Clique no campo editável do laço azul para criar uma função chamada 
``||functions:morder||``. 
Um novo laço referente à função criada é adicionado automaticamente à área de programação.


```blocks
function morder () {
	
}
actuators.SetSpeedMotor(500, OutputPorts.P8)
actuators.SetAngleServoKnob(0, OutputPorts.P16)
```

## Passo 6
Acesse a categoria ``||logic:Lógica||``, pegue a condicional ``||logic:se então||``
e insira-a dentro da função ``||functions:morder||``. 


```blocks
function morder () {
    if (true) {
    	
    }
}
actuators.SetSpeedMotor(500, OutputPorts.P8)
actuators.SetAngleServoKnob(0, OutputPorts.P16)


```

## Passo 7
Volte ao menu ``||logic:Lógica||``, pegue o comparador ``||logic:0 < 0||``
e substitua a condição **verdadeiro** da condicional.

```blocks
function morder () {
    if (0 < 0) {
    	
    }
}
actuators.SetSpeedMotor(500, OutputPorts.P8)
actuators.SetAngleServoKnob(0, OutputPorts.P16)

```

## Passo 8

Agora atualize os campos do comparador. Vá até a aba ``||sensors:Sensores||``,
clique no bloco ``||sensors:Valor do sensor infravermelho na porta P2||`` e troque 
o primeiro **0** do comparador.
Em seguida, modifique o segundo campo de **0** para **600** e o sinal de **<** para **>**.

```blocks
function morder () {
    if (sensors.infraredValue(InputPorts.P2) > 600) {
    	
    }
}
actuators.SetSpeedMotor(500, OutputPorts.P8)
actuators.SetAngleServoKnob(0, OutputPorts.P16)
```

## Passo 9
Duplique o bloco ``||actuators:Servo, definir posição 0 porta P16 modo Knob||`` usado no
bloco ``||basic:no iniciar||`` e coloque-o na condicional ``||logic:se então||``. 
Altere o valor da posição para **300**. Certifique-se de manter a porta como 
``||actuators:P16||``.

```blocks
function morder () {
    if (sensors.infraredValue(InputPorts.P2) > 600) {
        actuators.SetAngleServoKnob(300, OutputPorts.P16)
    }
}
actuators.SetSpeedMotor(500, OutputPorts.P8)
actuators.SetAngleServoKnob(0, OutputPorts.P16)
```

## Passo 10
Na categoria ``||basic:Básico||``, arraste uma pausa ``||basic:pausa (ms) 100||`` para o código,
depois, mude seu valor para **500**.

```blocks
function morder () {
    if (sensors.infraredValue(InputPorts.P2) > 600) {
        actuators.SetAngleServoKnob(300, OutputPorts.P16)
        basic.pause(500)
    }
}
actuators.SetSpeedMotor(500, OutputPorts.P8)
actuators.SetAngleServoKnob(0, OutputPorts.P16)
```


## Passo 11
Duplique o bloco ``||actuators:Servo, definir posição 0 porta P16 modo Knob||`` usado no
bloco ``||basic:no iniciar||`` e coloque-o após a pausa. Certifique-se de manter a porta como 
``||actuators:P16||``.

```blocks
function morder () {
    if (sensors.infraredValue(InputPorts.P2) > 600) {
        actuators.SetAngleServoKnob(300, OutputPorts.P16)
        basic.pause(500)
        actuators.SetAngleServoKnob(0, OutputPorts.P16)
    }
}
actuators.SetSpeedMotor(500, OutputPorts.P8)
actuators.SetAngleServoKnob(0, OutputPorts.P16)
```

## Passo 12

Copie a pausa ``||basic:pausa (ms) 500||`` para colá-la depois da movimentação do servo.
```blocks
function morder () {
    if (sensors.infraredValue(InputPorts.P2) > 600) {
        actuators.SetAngleServoKnob(300, OutputPorts.P16)
        basic.pause(500)
        actuators.SetAngleServoKnob(0, OutputPorts.P16)
        basic.pause(500)
    }
}
actuators.SetSpeedMotor(500, OutputPorts.P8)
actuators.SetAngleServoKnob(0, OutputPorts.P16)
```

## Passo 13

No menu ``||functions:Funções||`` arraste o comando  ``||functions:ligar morder||``
para dentro do laço ``||basic:sempre||``.

```blocks
function morder () {
    if (sensors.infraredValue(InputPorts.P2) > 600) {
        actuators.SetAngleServoKnob(300, OutputPorts.P16)
        basic.pause(500)
        actuators.SetAngleServoKnob(0, OutputPorts.P16)
        basic.pause(500)
    }
}
actuators.SetSpeedMotor(500, OutputPorts.P8)
actuators.SetAngleServoKnob(0, OutputPorts.P16)
basic.forever(function () {
    morder()
})

```

## Passo 14

Agora seu código está pronto! Baixe-o para o micro:bit e teste-o. Aproxime objetos do sensor infravermelho e observe a mordida do tubarão.
```blocks
```


## Passo 15
Se necessário, confira o seu código clicando na lâmpada de dica.

```blocks
function morder () {
    if (sensors.infraredValue(InputPorts.P2) > 600) {
        actuators.SetAngleServoKnob(300, OutputPorts.P16)
        basic.pause(500)
        actuators.SetAngleServoKnob(0, OutputPorts.P16)
        basic.pause(500)
    }
}
actuators.SetSpeedMotor(500, OutputPorts.P8)
actuators.SetAngleServoKnob(0, OutputPorts.P16)
basic.forever(function () {
    morder()
})


```



```package
fuzzyBot=github:FuzzyMakers/pxt-fuzzyMakers
```
