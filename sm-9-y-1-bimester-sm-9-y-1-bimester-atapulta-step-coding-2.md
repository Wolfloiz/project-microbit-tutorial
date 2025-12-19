### @diffs true
# Catapulta

## Passo 1
Nesta atividade, vamos programar o acionamento do servomotor acoplado à catapulta.
A lógica consiste apenas em manter o servomotor em seu ângulo inicial ao ligar o micro:bit e,
ao pressionarmos o botão B, fazer um movimento que muda esse ângulo rapidamente antes de retornar 
à posição inicial.

## Passo 2
Para começar, verifique se a biblioteca da Smart Makers já está importada em seu MakeCode.
Se não estiver, clique na aba **+ Extensões**, copie o endereço "https://github.com/FuzzyMakers/pxt-smartMakers",
cole-o no campo de pesquisa da janela que se abriu e selecione a biblioteca.

## Passo 3
Certifique-se de que seu código tenha um bloco ``||basic:no iniciar||``. Caso não tenha,
acesse a aba ``||basic:Básico||`` e adicione-o. Em seguida, acesse o menu de ``||actuators:Atuadores||`` e 
adicione o comando ``||actuators:Servo, definir posição 0 porta P8 modo knob||`` no laço ``||basic:no iniciar||``. 

```blocks
actuators.SetAngleServoKnob(0, OutputPorts.P8)
```

## Passo 4
Altere o valor da posição de **0** para **150** e a porta de **P8** para **P16**.

```blocks
actuators.SetAngleServoKnob(150, OutputPorts.P16)
```

## Passo 5
Acesse o menu ``||Input:Entrada||`` e adicione um bloco ``||Input:no botão A pressionado||`` à sua área de programação.
Clique na seta desse bloco para alterar de ``||Input:botão A||`` para ``||Input:botão B||``.  

```blocks
actuators.SetAngleServoKnob(150, OutputPorts.P16)
input.onButtonPressed(Button.B, function () {
	
})
```

## Passo 6
Dentro desse novo laço, adicione outro bloco ``||actuators:Servo, definir posição 0 porta P8 modo knob||``.
Antes de prosseguir, modifique a posição de **0** para **700** e a porta de **P8** para **P16**.

```blocks
input.onButtonPressed(Button.B, function () {
    actuators.SetAngleServoKnob(700, OutputPorts.P16)
})
actuators.SetAngleServoKnob(150, OutputPorts.P16)
```

## Passo 7
Em seguida, acesse a aba ``||basic:Básico||`` e adicione um bloco de ``||basic:pausa (ms) 100||``.
Altere a duração da pausa de **100 ms** para **1000 ms** (1 segundo).

```blocks
input.onButtonPressed(Button.B, function () {
    actuators.SetAngleServoKnob(700, OutputPorts.P16)
    basic.pause(1000)
})
actuators.SetAngleServoKnob(150, OutputPorts.P16)
```

## Passo 8
Finalize esse laço com outro bloco ``||actuators:Servo, definir posição 0 porta P8 modo knob||``.
Esse deve ter os mesmos parâmetros que inserimos no laço ``||basic:no iniciar||``, ou seja,
posição de **150** e porta **P16**. 

```blocks
input.onButtonPressed(Button.B, function () {
    actuators.SetAngleServoKnob(700, OutputPorts.P16)
    basic.pause(1000)
    actuators.SetAngleServoKnob(150, OutputPorts.P16)
})
actuators.SetAngleServoKnob(150, OutputPorts.P16)
```

## Passo 9
Seu programa já está pronto! Baixe-o para o micro:bit e 
teste-o pressionando o botão B do micro:bit para acionar sua catapulta.

```blocks
```

## Passo 10
Se necessário, confira o seu código clicando na lâmpada de dica.

```blocks
input.onButtonPressed(Button.B, function () {
    actuators.SetAngleServoKnob(700, OutputPorts.P16)
    basic.pause(1000)
    actuators.SetAngleServoKnob(150, OutputPorts.P16)
})
actuators.SetAngleServoKnob(150, OutputPorts.P16)
```

```package
fuzzyBot=github:FuzzyMakers/pxt-fuzzyMakers
```
