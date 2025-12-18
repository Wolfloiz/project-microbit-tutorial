### @diffs true
# Rotação e Translação

## Passo 1
Nesse tutorial, vamos criar um simples código para controlar a velocidade
do Motor CC que determina os movimentos dos astros na estrutura a partir
da posição do potenciômetro.

## Passo 2
Para começar, verifique se a biblioteca da Smart Makers já está importada 
em seu MakeCode. Se não estiver, clique na aba **+ Extensões**, 
copie o endereço "https://github.com/FuzzyMakers/pxt-smartMakers",
cole-o no campo de pesquisa da janela que se abriu e selecione a biblioteca.

## Passo 3
Acesse o menu ``||actuators:Atuadores||`` e adicione o bloco
``||actuators:Motor CC definir velocidade 0 na porta P8||`` 
dentro do laço ``||basic:sempre||``.

```blocks
basic.forever(function () {
    actuators.SetSpeedMotor(0, OutputPorts.P8)
})
```

## Passo 4
Altere a porta de **P8** para **P12**.

```blocks
basic.forever(function () {
    actuators.SetSpeedMotor(0, OutputPorts.P12)
})
```

## Passo 5
Clique na categoria ``||sensors:Sensores||`` e utilize o bloco
``||sensors:Valor do potenciômetro na porta P2||`` para substituir o valor
**0** da velocidade no bloco 
``||actuators:Motor CC definir velocidade 0 na porta P12||``.

```blocks
basic.forever(function () {
    actuators.SetSpeedMotor(sensors.dimmerValue(InputPorts.P2), OutputPorts.P12)
})
```

## Passo 6
Altere a porta do bloco do potenciômetro de **P2** para **P1**.

```blocks
basic.forever(function () {
    actuators.SetSpeedMotor(sensors.dimmerValue(InputPorts.P1), OutputPorts.P12)
})
```

## Passo 7

Agora seu código está pronto! Baixe-o para o micro:bit e teste-o. 
Gire o ponteiro do potenciômetro para controlar a velocidade
dos movimentos de rotação e translação da Terra.

```blocks
```

## Passo 8
Se necessário, confira o seu código clicando na lâmpada de dica.

```blocks
basic.forever(function () {
    actuators.SetSpeedMotor(sensors.dimmerValue(InputPorts.P1), OutputPorts.P12)
})
```

```package
fuzzyBot=github:FuzzyMakers/pxt-fuzzyMakers
```
