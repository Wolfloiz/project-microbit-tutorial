### @diffs true
# Telégrafo

## Passo 1
Nesse tutorial, vamos criar o código para que o telégrafo emita sons ao 
pressionarmos a alavanca da chave de fim de curso.

## Passo 2
Para começar, verifique se a biblioteca da Smart Makers já está importada 
em seu MakeCode. Se não estiver, clique na aba **+ Extensões**, 
copie o endereço "https://github.com/FuzzyMakers/pxt-smartMakers",
cole-o no campo de pesquisa da janela que se abriu e selecione a biblioteca.

## Passo 3
Acesse a aba ``||logic:Lógica||`` e adicione o bloco
``||logic:se então senão||`` dentro do laço ``||basic:sempre||``.

```blocks
basic.forever(function () {
    if (true) {
    	
    } else {
    	
    }
})
```

## Passo 4
Retorne ao menu de ``||logic:Lógica||`` e selecione um bloco comparador
``||logic:0 = 0||`` para substituir o campo **verdadeiro** do 
``||logic:se então senão||``.

```blocks
basic.forever(function () {
    if (0 == 0) {
    	
    } else {
    	
    }
})
```

## Passo 5
Acesse a aba ``||sensors:Sensores||`` e utilize o bloco 
``||sensors:Valor da chave fim de curso na porta P2||`` para substituir 
o primeiro **0** desse comparador. Já no segundo campo, modifique o valor 
para **1**.

```blocks
basic.forever(function () {
    if (sensors.endstopValue(InputPorts.P2) == 1) {
    	
    } else {
    	
    }
})
```

## Passo 6
Acesse a categoria ``||music:Música||`` e insira o bloco 
``||music:toque (Hz) C Médio||`` dentro do ``||logic:então||``.

```blocks
basic.forever(function () {
    if (sensors.endstopValue(InputPorts.P2) == 1) {
        music.ringTone(262)
    } else {
    	
    }
})
```

## Passo 7
Clique no campo do tom para alterar a nota de **C Médio** para **B Agudo**. Essa
nota corresponde à tecla na extremidade direita do teclado que se abre. Se 
preferir, você pode digitar o valor da frequência desejada diretamente **(988)**.

```blocks
basic.forever(function () {
    if (sensors.endstopValue(InputPorts.P2) == 1) {
        music.ringTone(988)
    } else {
    	
    }
})
```

## Passo 8
Retorne à categoria ``||music:Música||`` e insira o bloco 
``||music:stop all sounds||`` dentro do ``||logic:senão||``.

```blocks
basic.forever(function () {
    if (sensors.endstopValue(InputPorts.P2) == 1) {
        music.ringTone(988)
    } else {
        music.stopAllSounds()
    }
})
```

## Passo 9

Seu código está pronto! Baixe-o para o micro:bit e teste-o. 
Verifique se o telégrafo emite som ao pressionar a alavanca da chave 
de fim de curso. Experimente alterar a frequência (nota)
do som do telégrafo.

```blocks
```

## Passo 10
Se necessário, confira o seu código clicando na lâmpada de dica.

```blocks
basic.forever(function () {
    if (sensors.endstopValue(InputPorts.P2) == 1) {
        music.ringTone(988)
    } else {
        music.stopAllSounds()
    }
})
```

```package
fuzzyBot=github:FuzzyMakers/pxt-fuzzyMakers
```
