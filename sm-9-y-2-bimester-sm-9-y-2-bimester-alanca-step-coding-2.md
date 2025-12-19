### @diffs true
# Balança

## Passo 1
Nesse tutorial, vamos programar o micro:bit para nos indicar para qual lado
a balança está inclinada, ou se ela está em sua posição de equilíbrio.

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
Clique no sinal de **+** desse bloco para abrir um segundo condicional 
``||logic:senão se||``.

```blocks
basic.forever(function () {
    if (true) {
    	
    } else if (false) {
    	
    } else {
    	
    }
})
```

## Passo 5
Retorne ao menu de ``||logic:Lógica||`` e selecione um bloco comparador
``||logic:0 < 0||`` para substituir o **verdadeiro** e o 
**falso** da segunda condição.

```blocks
basic.forever(function () {
    if (0 < 0) {
    	
    } else if (0 < 0) {
    	
    } else {
    	
    }
})
```

## Passo 6
Altere o sinal do primeiro comparador de **<** para **>**.

```blocks
basic.forever(function () {
    if (0 > 0) {
    	
    } else if (0 < 0) {
    	
    } else {
    	
    }
})
```

## Passo 7
Clique na aba ``||input:Entrada||``. Acesse o submenu ``||input:...mais||``
que vai aparecer embaixo dessa categoria. Insira o bloco  
``||input:rotação (°) ajuste||`` no primeiro campo de ambos os comparadores.
Clique na seta desses blocos para alterar de
``||input:ajuste||`` para ``||input:rotação||``.  

```blocks
basic.forever(function () {
    if (input.rotation(Rotation.Roll) > 0) {
    	
    } else if (input.rotation(Rotation.Roll) < 0) {
    	
    } else {
    	
    }
})
```

## Passo 8
Agora, modifique o valor no segundo campo de cada comparador. Na primeira
condição, o valor deve ser alterado de **0** para **5**, enquanto na segunda condição
substituiremos o **0** por **-5**.

```blocks
basic.forever(function () {
    if (input.rotation(Rotation.Roll) > 5) {
    	
    } else if (input.rotation(Rotation.Roll) < -5) {
    	
    } else {
    	
    }
})
```

## Passo 9
Acesse a categoria ``||basic:Básico||`` e adicione blocos 
``||basic:mostrar leds||`` dentro do primeiro e do segundo ``||logic:então||``.

```blocks
basic.forever(function () {
    if (input.rotation(Rotation.Roll) > 5) {
        basic.showLeds(`
            . . . . .
            . . . . .
            . . . . .
            . . . . .
            . . . . .
            `)
    } else if (input.rotation(Rotation.Roll) < -5) {
        basic.showLeds(`
            . . . . .
            . . . . .
            . . . . .
            . . . . .
            . . . . .
            `)
    } else {
    	
    }
})
```

## Passo 10
Clique nos quadrados para selecionar os LEDs que devem se acender. No primeiro 
``||logic:então||``, desenhe uma seta para a direita. Já no segundo 
``||logic:então||``, desenhe uma seta para a esquerda.

```blocks
basic.forever(function () {
    if (input.rotation(Rotation.Roll) > 5) {
        basic.showLeds(`
            . . . . .
            . . . # .
            # # # # #
            . . . # .
            . . . . .
            `)
    } else if (input.rotation(Rotation.Roll) < -5) {
        basic.showLeds(`
            . . . . .
            . # . . .
            # # # # #
            . # . . .
            . . . . .
            `)
    } else {
    	
    }
})
```

## Passo 11
Retorne à aba ``||basic:Básico||`` e insira um comando ``||basic:mostrar ícone||``
dentro do ``||logic:senão||``. Clique na seta desse bloco para alterar o símbolo
exibido, de um coração para um check, indicando que a balança está em sua posição
de equilíbrio.

```blocks
basic.forever(function () {
    if (input.rotation(Rotation.Roll) > 5) {
        basic.showLeds(`
            . . . . .
            . . . # .
            # # # # #
            . . . # .
            . . . . .
            `)
    } else if (input.rotation(Rotation.Roll) < -5) {
        basic.showLeds(`
            . . . . .
            . # . . .
            # # # # #
            . # . . .
            . . . . .
            `)
    } else {
    	basic.showIcon(IconNames.Yes)
    }
})
```

## Passo 12

Seu código está pronto! Baixe-o para o micro:bit e teste-o. 
Incline levemente as hastes da balança e observe o símbolo que está sendo
exibido no micro:bit. Considere adicionar mais condições para diferenciar
os níveis de inclinação ou mesmo indicar os valores de rotação na tela.

```blocks
```

## Passo 13
Se necessário, confira o seu código clicando na lâmpada de dica.

```blocks
basic.forever(function () {
    if (input.rotation(Rotation.Roll) > 5) {
        basic.showLeds(`
            . . . . .
            . . . # .
            # # # # #
            . . . # .
            . . . . .
            `)
    } else if (input.rotation(Rotation.Roll) < -5) {
        basic.showLeds(`
            . . . . .
            . # . . .
            # # # # #
            . # . . .
            . . . . .
            `)
    } else {
    	basic.showIcon(IconNames.Yes)
    }
})
```

```package
fuzzyBot=github:FuzzyMakers/pxt-fuzzyMakers
```
