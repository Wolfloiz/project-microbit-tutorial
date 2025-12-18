### @diffs true
# Violino

## Passo 1
Neste tutorial, vamos programar o violino para tocar uma música predefinida
ao passarmos o arco pelo cavalete. O sensor infravermelho será responsável por 
identificar esse movimento.

## Passo 2
Para começar, verifique se a biblioteca da Smart Makers já está importada 
em seu MakeCode. Se não estiver, clique na aba **+ Extensões**, 
copie o endereço "https://github.com/FuzzyMakers/pxt-smartMakers",
cole-o no campo de pesquisa da janela que se abriu e selecione a biblioteca.

## Passo 3
Clique em **Avançado** para abrir novas categorias. Acesse a aba 
``||matrix:Matriz||`` e adicione o bloco 
``||matrix:definir lista para matriz de 0 1 -+||`` dentro do bloco 
``||basic:no iniciar||``.

```blocks
let lista = [0, 1]
basic.forever(function () {
	
})
```

## Passo 4
Acesse o menu ``||variables:Variáveis||`` e clique em **"Fazer uma variável..."**.
Vamos criar duas variáveis chamadas ``||variables:ultima_nota||`` e  
``||variables:musica||``. Por fim, clique na seta do bloco do passo anterior,
``||variables:definir lista para matriz||``, para alterar de 
``||variables:lista||`` para ``||variables:musica||``.

```blocks
let musica = [0, 1]
basic.forever(function () {
	
})
```

## Passo 5
Clique no sinal de **+** desse bloco **13 vezes** para adicionar novos números
à matriz, totalizando 15 campos numéricos que serão modificados posteriormente.

```blocks
let musica = [
0,
1,
0,
0,
0,
0,
0,
0,
0,
0,
0,
0,
0,
0,
0
]
basic.forever(function () {
	
})
```

## Passo 6
Vamos determinar a melodia tocada com os valores das frequências de cada nota 
musical. Para isso, edite os valores dessa matriz para exatamente essa sequência:
- 330,
- 330,
- 349,
- 392,
- 392,
- 349,
- 330,
- 294,
- 262,
- 262,
- 294,
- 330,
- 330,
- 294,
- 294

```blocks
let musica = [
330,
330,
349,
392,
392,
349,
330,
294,
262,
262,
294,
330,
330,
294,
294
]
basic.forever(function () {
	
})
```

## Passo 7
Clique no menu ``||Advanced:Avançado||``, acesse ``||Functions:Funções||`` e 
selecione **Fazer uma função...**.
Clique no campo editável do laço azul para criar uma função chamada 
``||Functions:movimenta_arco||``. 
Um novo laço referente à função criada é adicionado automaticamente ao código.


```blocks
function movimenta_arco () {
	
}
let musica = [
330,
330,
349,
392,
392,
349,
330,
294,
262,
262,
294,
330,
330,
294,
294
]
basic.forever(function () {
	
})
```

## Passo 8
Acesse a aba ``||logic:Lógica||`` e adicione o bloco ``||logic:se então senão||`` 
dentro do bloco ``||functions:movimenta_arco||``.

```blocks
function movimenta_arco () {
    if (true) {
    	
    } else {
    	
    }
}
let musica = [
330,
330,
349,
392,
392,
349,
330,
294,
262,
262,
294,
330,
330,
294,
294
]
basic.forever(function () {
	
})
```

## Passo 9
Retorne à ``||logic:Lógica||`` e utilize o bloco comparador 
``||logic:0 < 0||`` para substituir o campo **verdadeiro** do bloco 
``||logic:se então senão||``.

```blocks
function movimenta_arco () {
    if (0 < 0) {
    	
    } else {
    	
    }
}
let musica = [
330,
330,
349,
392,
392,
349,
330,
294,
262,
262,
294,
330,
330,
294,
294
]
basic.forever(function () {
	
})
```

## Passo 10
Acesse o menu ``||sensors:Sensores||`` e selecione o bloco 
``||sensors:Valor do sensor infravermelho na porta P2||`` para substituir o valor **0**
do primeiro campo do comparador. Antes de prosseguir, altere a porta de **P2** 
para **P1**.

```blocks
function movimenta_arco () {
    if (sensors.infraredValue(InputPorts.P1) < 0) {
    	
    } else {
    	
    }
}
let musica = [
330,
330,
349,
392,
392,
349,
330,
294,
262,
262,
294,
330,
330,
294,
294
]
basic.forever(function () {
	
})
```

## Passo 11
Clique na seta do comparador para modificar o sinal de **<** para **>**. Em 
seguida, altere o segundo campo do comparador de **0** para **300**.

```blocks
function movimenta_arco () {
    if (sensors.infraredValue(InputPorts.P1) > 300) {
    	
    } else {
    	
    }
}
let musica = [
330,
330,
349,
392,
392,
349,
330,
294,
262,
262,
294,
330,
330,
294,
294
]
basic.forever(function () {
	
})
```

## Passo 12
Feito isso, adicione um comando ``||functions:retornar 0||`` dentro do 
``||logic:então||`` e outro dentro do ``||logic:senão||``. Esses blocos estão
localizados na aba ``||functions:Funções||``. 

```blocks
function movimenta_arco () {
    if (sensors.infraredValue(InputPorts.P1) > 300) {
        return 0
    } else {
        return 0
    }
}
let musica = [
330,
330,
349,
392,
392,
349,
330,
294,
262,
262,
294,
330,
330,
294,
294
]
basic.forever(function () {
	
})
```

## Passo 13
Altere o valor do primeiro bloco ``||functions:retornar 0||`` dentro do 
``||logic:então||`` de **0** para **1**.

```blocks
function movimenta_arco () {
    if (sensors.infraredValue(InputPorts.P1) > 300) {
        return 1
    } else {
        return 0
    }
}
let musica = [
330,
330,
349,
392,
392,
349,
330,
294,
262,
262,
294,
330,
330,
294,
294
]
basic.forever(function () {
	
})
```

## Passo 14
Retorne ao menu ``||Functions:Funções||`` e clique em **Fazer uma função...**.
Clique no campo editável do laço azul para criar uma função chamada 
``||Functions:proxima_nota||``. 
Um novo laço referente à função criada é adicionado automaticamente ao código.

```blocks
function proxima_nota () {
	
}
function movimenta_arco () {
    if (sensors.infraredValue(InputPorts.P1) > 300) {
        return 1
    } else {
        return 0
    }
}
let musica = [
330,
330,
349,
392,
392,
349,
330,
294,
262,
262,
294,
330,
330,
294,
294
]
basic.forever(function () {
	
})
```

## Passo 15
Acesse a categoria ``||loops:Loops||`` e adicione o bloco 
``||loops:enquanto falso executar||`` dentro da função 
``||Functions:proxima_nota||``. 

```blocks
function proxima_nota () {
    while (false) {
    	
    }
}
function movimenta_arco () {
    if (sensors.infraredValue(InputPorts.P1) > 300) {
        return 1
    } else {
        return 0
    }
}
let musica = [
330,
330,
349,
392,
392,
349,
330,
294,
262,
262,
294,
330,
330,
294,
294
]
basic.forever(function () {
	
})
```

## Passo 16
Retorne à ``||logic:Lógica||`` e utilize o bloco comparador 
``||logic:0 = 0||`` para substituir o campo **falso** do bloco 
``||loops:enquanto executar||``.

```blocks
function proxima_nota () {
    while (0 == 0) {
    	
    }
}
function movimenta_arco () {
    if (sensors.infraredValue(InputPorts.P1) > 300) {
        return 1
    } else {
        return 0
    }
}
let musica = [
330,
330,
349,
392,
392,
349,
330,
294,
262,
262,
294,
330,
330,
294,
294
]
basic.forever(function () {
	
})
```

## Passo 17
Retorne à categoria ``||functions:Funções||`` e adicione o bloco de 
**bordas arredondadas** ``||functions:ligar movimenta_arco||`` dentro do 
primeiro campo do comparador.

```blocks
function proxima_nota () {
    while (movimenta_arco() == 0) {
    	
    }
}
function movimenta_arco () {
    if (sensors.infraredValue(InputPorts.P1) > 300) {
        return 1
    } else {
        return 0
    }
}
let musica = [
330,
330,
349,
392,
392,
349,
330,
294,
262,
262,
294,
330,
330,
294,
294
]
basic.forever(function () {
	
})
```

## Passo 18
Já no segundo campo do comparador, insira o bloco da variável 
``||variables:ultima_nota||``.

```blocks
function proxima_nota () {
    let ultima_nota = 0
    while (movimenta_arco() == ultima_nota) {
    	
    }
}
function movimenta_arco () {
    if (sensors.infraredValue(InputPorts.P1) > 300) {
        return 1
    } else {
        return 0
    }
}
let musica = [
330,
330,
349,
392,
392,
349,
330,
294,
262,
262,
294,
330,
330,
294,
294
]
basic.forever(function () {
	
})
```

## Passo 19
Dentro do ``||loops:executar||``, adicione um bloco ``||basic:pausa (ms) 100||``.
Antes de prosseguir, altere a duração dessa ``||basic:pausa||`` para **20 ms**.

```blocks
function proxima_nota () {
    let ultima_nota = 0
    while (movimenta_arco() == ultima_nota) {
    	
    }
}
function movimenta_arco () {
    if (sensors.infraredValue(InputPorts.P1) > 300) {
        return 1
    } else {
        return 0
    }
}
let musica = [
330,
330,
349,
392,
392,
349,
330,
294,
262,
262,
294,
330,
330,
294,
294
]
basic.forever(function () {
	
})
```

## Passo 20
**Abaixo** do bloco ``||loops:enquanto executar||``, adicione um comando
``||variables:definir ultima_nota para 0||``, localizado na aba 
``||variables:Variáveis||``. Se esse bloco aparecer com outro nome em seu menu,
adicione-o e clique na seta para alterar a variável a ser definida.

```blocks
function proxima_nota () {
    while (movimenta_arco() == ultima_nota) {
        basic.pause(20)
    }
    ultima_nota = 0
}
function movimenta_arco () {
    if (sensors.infraredValue(InputPorts.P1) > 300) {
        return 1
    } else {
        return 0
    }
}
let ultima_nota = 0
let musica = [
330,
330,
349,
392,
392,
349,
330,
294,
262,
262,
294,
330,
330,
294,
294
]
basic.forever(function () {
	
})
```

## Passo 21
Substitua o valor **0** desse bloco pelo comando 
``||functions:ligar movimenta_arco||``, localizado no menu 
``||functions:Funções||``. Utilize o bloco de bordas arredondadas.

```blocks
function proxima_nota () {
    while (movimenta_arco() == ultima_nota) {
        basic.pause(20)
    }
    ultima_nota = movimenta_arco()
}
function movimenta_arco () {
    if (sensors.infraredValue(InputPorts.P1) > 300) {
        return 1
    } else {
        return 0
    }
}
let ultima_nota = 0
let musica = [
330,
330,
349,
392,
392,
349,
330,
294,
262,
262,
294,
330,
330,
294,
294
]
basic.forever(function () {
	
})
```

## Passo 22
Agora, prosseguimos para a programação do laço ``||basic:sempre||``. Acesse a 
categoria ``||loops:Loops||`` e adicione o bloco 
``||loops:para índice de 0 a 4 executar||`` dentro do ``||basic:sempre||``.

```blocks
function proxima_nota () {
    while (movimenta_arco() == ultima_nota) {
        basic.pause(20)
    }
    ultima_nota = movimenta_arco()
}
function movimenta_arco () {
    if (sensors.infraredValue(InputPorts.P1) > 300) {
        return 1
    } else {
        return 0
    }
}
let ultima_nota = 0
let musica = [
330,
330,
349,
392,
392,
349,
330,
294,
262,
262,
294,
330,
330,
294,
294
]
basic.forever(function () {
    for (let índice = 0; índice <= 4; índice++) {
    	
    }
})
```

## Passo 23
Modifique o intervalo do ``||variables:índice||`` de **0** a **4** para de **0**
a **14**. Em seguida, insira o comando ``||functions:ligar proxima_nota||`` 
dentro do ``||loops:executar||``. 

```blocks
function proxima_nota () {
    while (movimenta_arco() == ultima_nota) {
        basic.pause(20)
    }
    ultima_nota = movimenta_arco()
}
function movimenta_arco () {
    if (sensors.infraredValue(InputPorts.P1) > 300) {
        return 1
    } else {
        return 0
    }
}
let ultima_nota = 0
let musica = [
330,
330,
349,
392,
392,
349,
330,
294,
262,
262,
294,
330,
330,
294,
294
]
basic.forever(function () {
    for (let índice = 0; índice <= 14; índice++) {
        proxima_nota()
    }
})
```

## Passo 24
Vá ao menu ``||music:Música||`` e insira o bloco 
``||music:play tone C Médio for 1 batida until done||`` dentro do 
``||loops:executar||``. 

```blocks
function proxima_nota () {
    while (movimenta_arco() == ultima_nota) {
        basic.pause(20)
    }
    ultima_nota = movimenta_arco()
}
function movimenta_arco () {
    if (sensors.infraredValue(InputPorts.P1) > 300) {
        return 1
    } else {
        return 0
    }
}
let ultima_nota = 0
let musica = [
330,
330,
349,
392,
392,
349,
330,
294,
262,
262,
294,
330,
330,
294,
294
]
basic.forever(function () {
    for (let índice = 0; índice <= 14; índice++) {
        proxima_nota()
        music.play(music.tonePlayable(262, music.beat(BeatFraction.Whole)), music.PlaybackMode.UntilDone)
    }
})
```

## Passo 25
Vá a **Avançado** e acesse o menu ``||matrix:Matriz||``. Selecione o bloco
de bordas arredondadas ``||matrix:lista obter valor em 0||``. Ele deve ser
inserido dentro do campo **C Médio** do bloco ``||music:play tone||``.
 **Atenção:** não substitua o bloco maior ``||music:tone||``, apenas o campo
 em branco onde está escrito **C Médio**.

```blocks
function proxima_nota () {
    while (movimenta_arco() == ultima_nota) {
        basic.pause(20)
    }
    ultima_nota = movimenta_arco()
}
function movimenta_arco () {
    if (sensors.infraredValue(InputPorts.P1) > 300) {
        return 1
    } else {
        return 0
    }
}
let ultima_nota = 0
let musica = [
330,
330,
349,
392,
392,
349,
330,
294,
262,
262,
294,
330,
330,
294,
294
]
basic.forever(function () {
    for (let índice = 0; índice <= 14; índice++) {
        let lista: number[] = []
        proxima_nota()
        music.play(music.tonePlayable(lista[0], music.beat(BeatFraction.Whole)), music.PlaybackMode.UntilDone)
    }
})
```

## Passo 26
Clique na seta desse bloco para alterar da variável ``||variables:lista||``
para a variável ``||variables:musica||``. Em seguida, substitua o valor **0**
pela variável ``||variables:índice||``.

```blocks
function proxima_nota () {
    while (movimenta_arco() == ultima_nota) {
        basic.pause(20)
    }
    ultima_nota = movimenta_arco()
}
function movimenta_arco () {
    if (sensors.infraredValue(InputPorts.P1) > 300) {
        return 1
    } else {
        return 0
    }
}
let ultima_nota = 0
let musica = [
330,
330,
349,
392,
392,
349,
330,
294,
262,
262,
294,
330,
330,
294,
294
]
basic.forever(function () {
    for (let índice = 0; índice <= 14; índice++) {
        proxima_nota()
        music.play(music.tonePlayable(musica[índice], music.beat(BeatFraction.Whole)), music.PlaybackMode.UntilDone)
    }
})

```

## Passo 27
Agora, seu código está pronto! Baixe-o para o micro:bit e utilize o movimento 
do arco para tocar a melodia com o violino.

```blocks
```

## Passo 28
Se necessário, confira o seu código clicando na lâmpada de dica.

```blocks
function proxima_nota () {
    while (movimenta_arco() == ultima_nota) {
        basic.pause(20)
    }
    ultima_nota = movimenta_arco()
}
function movimenta_arco () {
    if (sensors.infraredValue(InputPorts.P1) > 300) {
        return 1
    } else {
        return 0
    }
}
let ultima_nota = 0
let musica = [
330,
330,
349,
392,
392,
349,
330,
294,
262,
262,
294,
330,
330,
294,
294
]
basic.forever(function () {
    for (let índice = 0; índice <= 14; índice++) {
        proxima_nota()
        music.play(music.tonePlayable(musica[índice], music.beat(BeatFraction.Whole)), music.PlaybackMode.UntilDone)
    }
})

```

```package
fuzzyBot=github:FuzzyMakers/pxt-fuzzyMakers
```