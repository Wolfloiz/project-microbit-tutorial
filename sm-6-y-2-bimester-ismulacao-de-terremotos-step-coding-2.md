### @diffs true
# Simulação de Terremotos

## Passo 1
Nesse tutorial, vamos programar um simulador de terremotos, que permite 
criar abalos sísmicos de intensidades variáveis sobre o modelo de cidade
construído.

## Passo 2
Para começar, verifique se a biblioteca da Smart Makers já está importada 
em seu MakeCode. Se não estiver, clique na aba **+ Extensões**, 
copie o endereço "https://github.com/FuzzyMakers/pxt-smartMakers",
cole-o no campo de pesquisa da janela que se abriu e selecione a biblioteca.

## Passo 3
Acesse o menu ``||actuators:Atuadores||`` e adicione o bloco
``||actuators:Servo, definir posição 0 porta P8 modo Knob||`` 
dentro do laço ``||basic:sempre||``.

```blocks
basic.forever(function () {
    actuators.SetAngleServoKnob(0, OutputPorts.P8)
})
```

## Passo 4
Altere o valor da posição de **0** para **150** 
e a porta de **P8** para **P16**.

```blocks
basic.forever(function () {
    actuators.SetAngleServoKnob(150, OutputPorts.P16)
})
```

## Passo 5
Clique na categoria ``||basic:Básico||`` e adicione o bloco
``||basic:pausa (ms) 100||`` dentro de ``||basic:sempre||``.

```blocks
basic.forever(function () {
    actuators.SetAngleServoKnob(150, OutputPorts.P16)
    basic.pause(100)
})
```

## Passo 6
Acesse o menu ``||math:Matemática||`` e utilize o bloco
``||math:map 0 from low 0 high 1023 to low 0 high 4||`` 
para substituir o valor **100** dentro do bloco ``||basic:pausa||``.

```blocks
basic.forever(function () {
    actuators.SetAngleServoKnob(150, OutputPorts.P16)
    basic.pause(Math.map(0, 0, 1023, 0, 4))
})
```

## Passo 7
Clique na aba ``||sensors:Sensores||`` e insira o bloco 
``||sensors:Valor do potenciômetro na porta P2||`` no primeiro campo 
do bloco ``||math:map||`` substituindo o valor **0**.

```blocks
basic.forever(function () {
    actuators.SetAngleServoKnob(150, OutputPorts.P16)
    basic.pause(Math.map(sensors.dimmerValue(InputPorts.P2), 0, 1023, 0, 4))
})
```

## Passo 8
Altere o último valor desse bloco de **4** para **70**.

```blocks
basic.forever(function () {
    actuators.SetAngleServoKnob(150, OutputPorts.P16)
    basic.pause(Math.map(sensors.dimmerValue(InputPorts.P2), 0, 1023, 0, 70))
})
```

## Passo 9
Agora, adicione um segundo bloco 
``||actuators:Servo, definir posição 0 porta P8 modo Knob||``. 
Certifique-se de alterar a porta de **P8** para **P16**, enquanto o valor 
de posição deve ser mantido em **0**.

```blocks
basic.forever(function () {
    actuators.SetAngleServoKnob(150, OutputPorts.P16)
    basic.pause(Math.map(sensors.dimmerValue(InputPorts.P2), 0, 1023, 0, 70))
    actuators.SetAngleServoKnob(0, OutputPorts.P16)
})
```

## Passo 10
Abaixo desse bloco, teremos outro comando de ``||basic:pausa||`` com o 
``||math:map||`` dentro, idêntico ao anterior. 

**Dica:** Para facilitar, você pode duplicar o anterior, 
mantendo-o pressionado para abrir as opções de duplicação.

```blocks
basic.forever(function () {
    actuators.SetAngleServoKnob(150, OutputPorts.P16)
    basic.pause(Math.map(sensors.dimmerValue(InputPorts.P2), 0, 1023, 0, 70))
    actuators.SetAngleServoKnob(0, OutputPorts.P16)
    basic.pause(Math.map(sensors.dimmerValue(InputPorts.P2), 0, 1023, 0, 70))
})
```

## Passo 11

Agora seu código está pronto! Baixe-o para o micro:bit e teste-o. 
Gire o ponteiro do potenciômetro para variar a intensidade de seus terremotos!

```blocks
```

## Passo 12
Se necessário, confira o seu código clicando na lâmpada de dica.

```blocks
basic.forever(function () {
    actuators.SetAngleServoKnob(150, OutputPorts.P16)
    basic.pause(Math.map(sensors.dimmerValue(InputPorts.P2), 0, 1023, 0, 70))
    actuators.SetAngleServoKnob(0, OutputPorts.P16)
    basic.pause(Math.map(sensors.dimmerValue(InputPorts.P2), 0, 1023, 0, 70))
})
```

```package
fuzzyBot=github:FuzzyMakers/pxt-fuzzyMakers
```
