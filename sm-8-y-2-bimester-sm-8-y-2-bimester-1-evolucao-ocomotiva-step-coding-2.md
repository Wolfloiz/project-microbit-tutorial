### @diffs true
# Locomotiva

## Passo 1
Nesse tutorial, vamos programar o movimento da locomotiva, bem como seu apito
característico.

## Passo 2
Para começar, verifique se a biblioteca da Smart Makers já está importada 
em seu MakeCode. Se não estiver, clique na aba **+ Extensões**, 
copie o endereço "https://github.com/FuzzyMakers/pxt-smartMakers",
cole-o no campo de pesquisa da janela que se abriu e selecione a biblioteca.

## Passo 3
Acesse a aba ``||actuators:Atuadores||`` e adicione o bloco
``||actuators:Motor CC, definir velocidade 0 na porta P8||`` dentro do laço
``||basic:no iniciar||``.

```blocks
actuators.SetSpeedMotor(0, OutputPorts.P8)
```

## Passo 4
Altere o valor da velocidade de **0** para **1023**.

```blocks
actuators.SetSpeedMotor(1023, OutputPorts.P8)
```

## Passo 5
Acesse a categoria ``||Loops:Loops||`` e adicione um laço 
``||Loops:every 500 ms||`` ao seu código.

```blocks
actuators.SetSpeedMotor(1023, OutputPorts.P8)
loops.everyInterval(500, function () {
	
})
```

## Passo 6
Clique no campo numérico para alterar o intervalo de tempo de **500 ms** para
**5000 ms** (5 segundos). 

```blocks
actuators.SetSpeedMotor(1023, OutputPorts.P8)
loops.everyInterval(5000, function () {
	
})
```

## Passo 7
Volte ao menu ``||Loops:Loops||`` e insira um bloco 
``||Loops:repetir 4 vezes executar||`` dentro do laço ``||Loops:every 5000 ms||``.

```blocks
actuators.SetSpeedMotor(1023, OutputPorts.P8)
loops.everyInterval(5000, function () {
    for (let index = 0; index < 4; index++) {
    	
    }
})
```

## Passo 8
Altere o número de vezes a serem repetidas de **4** para **2**.

```blocks
actuators.SetSpeedMotor(1023, OutputPorts.P8)
loops.everyInterval(5000, function () {
    for (let index = 0; index < 2; index++) {
    	
    }
})
```

## Passo 9
Acesse a categoria ``||music:Música||`` e insira o bloco 
``||music:play tone C Médio for 1 batida until done||`` dentro do laço
``||Loops:repetir 2 vezes executar||``.

```blocks
actuators.SetSpeedMotor(1023, OutputPorts.P8)
loops.everyInterval(5000, function () {
    for (let index = 0; index < 2; index++) {
        music.play(music.tonePlayable(262, music.beat(BeatFraction.Whole)), music.PlaybackMode.UntilDone)
    }
})
```

## Passo 10
Clique no campo do tom para alterar a nota de **C Médio** para **B Agudo**. Essa
nota é a tecla na extremidade direita do teclado que se abre. Se preferir, você
pode digitar o valor da frequência desejada diretamente **(988)**.

```blocks
actuators.SetSpeedMotor(1023, OutputPorts.P8)
loops.everyInterval(5000, function () {
    for (let index = 0; index < 2; index++) {
        music.play(music.tonePlayable(988, music.beat(BeatFraction.Whole)), music.PlaybackMode.UntilDone)
    }
})
```

## Passo 11
Vá à categoria ``||basic:Básico||`` e adicione um bloco de 
``||basic:pausa (ms) 100||`` abaixo do comando musical, ainda dentro do 
``||Loops:executar||``.

```blocks
actuators.SetSpeedMotor(1023, OutputPorts.P8)
loops.everyInterval(5000, function () {
    for (let index = 0; index < 2; index++) {
        music.play(music.tonePlayable(988, music.beat(BeatFraction.Whole)), music.PlaybackMode.UntilDone)
        basic.pause(100)
    }
})
```

## Passo 12
Altere a duração dessa ``||basic:pausa||`` de **100 ms** para **200 ms**.

```blocks
actuators.SetSpeedMotor(1023, OutputPorts.P8)
loops.everyInterval(5000, function () {
    for (let index = 0; index < 2; index++) {
        music.play(music.tonePlayable(988, music.beat(BeatFraction.Whole)), music.PlaybackMode.UntilDone)
        basic.pause(200)
    }
})
```

## Passo 13

Agora seu código está pronto! Baixe-o para o micro:bit e teste-o. 
Ao ligar o circuito, a locomotiva vai começar a movimentar-se e apitar a cada 
5 segundos. Experimente alterar o intervalo entre os apitos, a frequência (nota)
do som ou a velocidade da sua locomotiva.

```blocks
```

## Passo 14
Se necessário, confira o seu código clicando na lâmpada de dica.

```blocks
actuators.SetSpeedMotor(1023, OutputPorts.P8)
loops.everyInterval(5000, function () {
    for (let index = 0; index < 2; index++) {
        music.play(music.tonePlayable(988, music.beat(BeatFraction.Whole)), music.PlaybackMode.UntilDone)
        basic.pause(200)
    }
})
```

```package
fuzzyBot=github:FuzzyMakers/pxt-fuzzyMakers
```
