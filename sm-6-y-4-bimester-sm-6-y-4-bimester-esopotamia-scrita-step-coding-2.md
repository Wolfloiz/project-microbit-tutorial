### @diffs true
# Robô Escriba

## Passo 1
Neste tutorial, vamos programar os movimentos do robô escriba para escrever a letra **"R"**.
## Passo 2
Para começar, verifique se a biblioteca da Smart Makers já está importada 
em seu MakeCode. Se não estiver, clique na aba **+ Extensões**, 
copie o endereço "https://github.com/FuzzyMakers/pxt-smartMakers",
cole-o no campo de pesquisa da janela que se abriu e selecione a biblioteca.

## Passo 3
Clique em **Avançado** para abrir novas categorias. Clique em ``||smart:Smart||``
e arraste o comando ``||smart:Iniciar robô escriba||`` para dentro do laço ``||basic:no iniciar||``.

```blocks
Smart.robotScribe()

```
## Passo 4

No menu ``||loops:Loops||`` pegue o bloco ``||loops:enquanto executar||`` 
e coloque-o após a inicialização do robô.

```blocks
Smart.robotScribe()
while (false) {
	
}

```

## Passo 5
Vá até a aba ``||logic:Lógica||``, selecione a condição ``||logic:não||``
e substitua o campo preenchido como **falso**.

```blocks
Smart.robotScribe()
while (!(false)) {
	
}

```

## Passo 6

Acesse a categoria ``||input:Entrada||`` e arraste a condição  ``||input:botão A é pressionado||``
para o espaço vazio à frente do ``||logic:não||``.  

```blocks
Smart.robotScribe()
while (!(input.buttonIsPressed(Button.A))) {
	
}


```
## Passo 7

No menu ``||basic:Básico||`` selecione uma ``||basic:pausa (ms) 100||``
e insira-a dentro do loop ``||loops:enquanto executar||``.

```blocks
Smart.robotScribe()
while (!(input.buttonIsPressed(Button.A))) {
    basic.pause(100)
}


```
## Passo 8

Volte à categoria ``||smart:Smart||`` clique no bloco ``||smart:Mover caneta para cima 1||``
e posicione-o depois do loop, altere o valor do passo de **1** para **2**.

```blocks
Smart.robotScribe()
while (!(input.buttonIsPressed(Button.A))) {
    basic.pause(100)
}
Smart.upServo(2)


```
## Passo 9

Ainda na categoria ``||smart:Smart||`` clique no bloco ``||smart:Mover caneta para direita 1||``
e posicione-o após a movimentação vertical.

```blocks
Smart.robotScribe()
while (!(input.buttonIsPressed(Button.A))) {
    basic.pause(100)
}
Smart.upServo(2)
Smart.moveRight(1)

```
## Passo 10
Continue acessando o menu ``||smart:Smart||``, clique no bloco ``||smart:Mover caneta para baixo 1||``
e coloque-o abaixo do último bloco.

```blocks
Smart.robotScribe()
while (!(input.buttonIsPressed(Button.A))) {
    basic.pause(100)
}
Smart.upServo(2)
Smart.moveRight(1)
Smart.downServo(1)


```

## Passo 11
Volte à categoria ``||smart:Smart||`` clique no bloco ``||smart:Mover caneta para esquerda 1||``
e coloque-o abaixo do último bloco.

```blocks
Smart.robotScribe()
while (!(input.buttonIsPressed(Button.A))) {
    basic.pause(100)
}
Smart.upServo(2)
Smart.moveRight(1)
Smart.downServo(1)
Smart.moveLeft(1)

```

## Passo 12
Para terminar a escrita, vá até aba ``||smart:Smart||`` clique no bloco ``||smart:Subir caneta na diagonal para frente 1||``
e insira-o no fim da função.

```blocks
Smart.robotScribe()
while (!(input.buttonIsPressed(Button.A))) {
    basic.pause(100)
}
Smart.upServo(2)
Smart.moveRight(1)
Smart.downServo(1)
Smart.moveLeft(1)
Smart.moveDiagonal(DiagonalWay.Up, DiagonalDirection.Front, 1)

```
## Passo 13
Modifique o movimento de ``||smart:Subir||`` para ``||smart:Descer||``.

```blocks
Smart.robotScribe()
while (!(input.buttonIsPressed(Button.A))) {
    basic.pause(100)
}
Smart.upServo(2)
Smart.moveRight(1)
Smart.downServo(1)
Smart.moveLeft(1)
Smart.moveDiagonal(DiagonalWay.Down, DiagonalDirection.Front, 1)


```

## Passo 14

Seu código está pronto! Baixe-o para o micro:bit e teste-o. 
Espere o robô posicionar a caneta e depois aperte o botão A do micro:bit para que ele escreva a letra programada.

```blocks
```

## Passo 15
Se necessário, confira o seu código clicando na lâmpada de dica.

```blocks
Smart.robotScribe()
while (!(input.buttonIsPressed(Button.A))) {
    basic.pause(100)
}
Smart.upServo(2)
Smart.moveRight(1)
Smart.downServo(1)
Smart.moveLeft(1)
Smart.moveDiagonal(DiagonalWay.Down, DiagonalDirection.Front, 1)


```

```package
fuzzyBot=github:FuzzyMakers/pxt-fuzzyMakers
```
