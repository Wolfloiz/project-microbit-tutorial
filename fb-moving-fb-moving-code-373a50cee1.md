### @diffs true
# FuzzyBoT em Movimento

## Passo 1
Neste tutorial, vamos iniciar a programação das funções dos movimentos básicos do FuzzyBoT. Em seguida,
vamos entender como combinar esses movimentos para que ele percorra trajetos específicos. Por fim, usaremos os Botões A e B 
do Micro:bit para ligar e desligar o deslocamento do nosso robô. Antes de prosseguir, veja a lista de funções que vamos criar:
1. Avançar;
2. Virar para esquerda;
3. Virar para direita;
4. Virar para esquerda bruscamente;
5. Virar para direita bruscamente;
6. Marcha ré. 
## Passo 2
Para começar, verifique se a biblioteca da Fuzzy Makers já está importada em seu MakeCode.
Se não estiver, clique na aba **+ Extensões**, copie o endereço "https://github.com/FuzzyMakers/pxt-fuzzyMakers",
cole-o no campo de pesquisa da janela que se abriu e selecione a biblioteca. Se estiver compartilhando a aula dentro do ambiente da plataforma desconsidere esse passo.

## Passo 3
Vamos iniciar a programação criando a variável ``||variables:Ligar||``.
Para isso, acesse o menu ``||variables:Variáveis||`` e clique em **"Fazer uma variável..."**. Nomeie sua variável como ``||variables:Ligar||``.

```blocks
```

## Passo 4 
Ao fazer isso, o bloco de definição dessa variável aparecerá no menu ``||variables:Variáveis||``. Adicione o bloco ``||variables:Definir Ligar para 0||`` dentro
do laço ``||basic:no iniciar||``. 
**Dica:** se o laço ``||basic:no iniciar||`` não estiver presente no seu código automaticamente, você pode encontrá-lo na aba ``||basic:Básico||``.


```blocks

let Ligar = 0
```



## Passo 5
Agora, acesse a aba ``||input:Entrada||`` e adicione dois laços ``||input:no botão A pressionado||``. Clique em um dos laços para 
modificar o botão de ``||input:Botão A||`` para ``||input:Botão B||``.  

```blocks
input.onButtonPressed(Button.A, function () {
	
})
input.onButtonPressed(Button.B, function () {
	
})
let Ligar = 0
basic.forever(function () {
	
})

```
## Passo 6
Duplique o bloco ``||variables:Definir Ligar para 0||``, que criamos no laço ``||basic:no iniciar||``, clicando com o botão direito do mouse sobre o bloco. 
Posicione um dentro do laço do ``||input:Botão A||`` e outro no laço do ``||input:Botão B||``. Modifique o valor dessa variável de **0** para **1**
no bloco dentro do ``||input:Botão A||``. 

```blocks
input.onButtonPressed(Button.A, function () {
    Ligar = 1
})
input.onButtonPressed(Button.B, function () {
    Ligar = 0
})
let Ligar = 0
Ligar = 0
basic.forever(function () {
	
})

```

## Passo 7
Feito isso, presseguimos para a criação das  ``||Functions:Funções||``.
Então, clique no menu ``||Advanced:Avançado||``, acesse ``||Functions:Funções||`` e clique em **Fazer uma função...**.
Clique no campo editável do laço azul para criar uma função chamada ``||Functions:frente||``. Um novo laço referente à função criada é adicionado automaticamente ao código.

```blocks

function frente () {
	
}


```

## Passo 8
Dentro deste laço, vamos adicionar os comandos para execução do movimento desejado. Nesse caso, acesse a aba
``||fuzzyBot:FuzzyBoT||`` e adicione o bloco ``||fuzzyBot:Motor esquerdo mover para frente com a velocidade 0||`` dentro
do laço da função ``||Functions:frente||``.

```blocks

function frente () {
    fuzzyBot.motorRun(fuzzyBot.Motors.M1, fuzzyBot.Dir.CW, 0)
}


```

## Passo 9
Clique no bloco para alterar o motor de ``||fuzzyBot:esquerdo||`` para ``||fuzzyBot:todos||``. Em seguida, 
 substituia o valor **0** por **50**. 

```blocks

function frente () {
    fuzzyBot.motorRun(fuzzyBot.Motors.All, fuzzyBot.Dir.CW, 50)
}


```

## Passo 10
Agora, vamos repetir o processo de criação de  ``||Functions:Funções||`` para criar a função ``||Functions:esquerda||``.

```blocks
function esquerda () {
	
}

```

## Passo 11
Dentro dessa função, precisaremos de dois blocos de controle dos motores do FuzzyBoT: ``||fuzzyBot:Motor esquerdo mover para frente com a velocidade 0||``. 
Edite um dos blocos para que um deles controle o motor ``||fuzzyBot:esquerdo||`` e outro o ``||fuzzyBot:direito||``.

```blocks
function esquerda () {
    fuzzyBot.motorRun(fuzzyBot.Motors.M1, fuzzyBot.Dir.CW, 0)
    fuzzyBot.motorRun(fuzzyBot.Motors.M2, fuzzyBot.Dir.CW, 0)
}


```

## Passo 12
Para realizar esse movimento para esquerda, vamos deixar o motor ``||fuzzyBot:esquerdo||`` com velocidade **30** e o ``||fuzzyBot:direito||`` movimentando
com o velocidade **50**

```blocks
function esquerda () {
    fuzzyBot.motorRun(fuzzyBot.Motors.M1, fuzzyBot.Dir.CW, 30)
    fuzzyBot.motorRun(fuzzyBot.Motors.M2, fuzzyBot.Dir.CW, 50)
}

```

## Passo 13
Agora, vamos replicar o processo para a função ``||Functions:direita||``. O modo mais prático é
simplesmente duplicar o laço da função ``||Functions:esquerda||`` e renomeá-lo. Feito isso, inverta os 
motores ``||fuzzyBot:esquerdo||`` e ``||fuzzyBot:direito||`` para que o direito fique com velocidade **30** enquanto o esquerdo fique com velocidade **50**.
```blocks

function direita () {
    fuzzyBot.motorRun(fuzzyBot.Motors.M2, fuzzyBot.Dir.CW, 30)
    fuzzyBot.motorRun(fuzzyBot.Motors.M1, fuzzyBot.Dir.CW, 50)
}

```

## Passo 14
Para as funções das curvas bruscas, vamos fazer com que o motor que ficava com velocidade menor, fique parado.
Assim, o raio da curva diminuirá. Vamos começar pela função ``||Functions:esquerda_brusca||``. Duplique todo o laço 
``||Functions:esquerda||`` e altere seu nome.

```blocks

function esquerda_brusca () {
    fuzzyBot.motorRun(fuzzyBot.Motors.M1, fuzzyBot.Dir.CW, 30)
    fuzzyBot.motorRun(fuzzyBot.Motors.M2, fuzzyBot.Dir.CW, 50)
}


```

## Passo 15
Em seguida, edite o bloco do motor ``||fuzzyBot:esquerdo||`` para que ele fique parado com velocidade **0**.

```blocks

function esquerda_brusca () {
    fuzzyBot.motorRun(fuzzyBot.Motors.M1, fuzzyBot.Dir.CW, 0)
    fuzzyBot.motorRun(fuzzyBot.Motors.M2, fuzzyBot.Dir.CW, 50)
}


```

## Passo 16
Agora, vamos duplicar o laço ``||Functions:direita||``, renomeá-lo para ``||Functions:direita_brusca||`` e alterar o bloco do motor 
``||fuzzyBot:direito||`` para que ele fique parado.

```blocks

function direita_brusca () {
    fuzzyBot.motorRun(fuzzyBot.Motors.M2, fuzzyBot.Dir.CW, 0)
    fuzzyBot.motorRun(fuzzyBot.Motors.M1, fuzzyBot.Dir.CW, 50)
}

```

## Passo 17
Por fim, vamos criar a última função: ``||Functions:tras||``. O método mais rápido é simplesmente
duplicar a função ``||Functions:frene||``, renomeá-la e alterar o sentido do motor para ``||fuzzyBot:trás||``.

```blocks

function tras () {
    fuzzyBot.motorRun(fuzzyBot.Motors.All, fuzzyBot.Dir.CCW, 50)
}

function frente () {
    fuzzyBot.motorRun(fuzzyBot.Motors.All, fuzzyBot.Dir.CW, 50)
}
	
})

```

## Passo 18
Com todas as funções de movimento prontas, podemos prosseguir para combiná-las dentro de um laço ``||basic:sempre||``, localizado
na aba ``||basic:Básico||``.

```blocks
basic.forever(function () {
    
})
```



## Passo 19
Acesse o menu ``||logic:Lógica||`` e insira o laço condicional ``||logic:se-então-senão||`` dentro do ``||basic:sempre||``.

```blocks
basic.forever(function () {
    if (true) {
    	
    } else {
    	
    }
})
```

## Passo 20
Retorne à aba ``||logic:Lógica||`` e adicione o bloco comparador ``||logic:0 = 0||`` dentro do campo **verdadeiro** do ``||logic:se-então-senão||``.
Altere o primeiro valor da comparação de **0** para a variável ``||variables:Ligar||``, e o segundo valor de **0** para **1**.

```blocks
basic.forever(function () {
    if (Ligar == 1) {
    	
    } else {
    	
    }
})
```

## Passo 21
Agora, dentro do ``||logic:então||``, podemos combinar os movimentos desejados. Para isso, comece acessando 
``||Advanced:Avançado||``, clique em ``||Functions:Funções||`` e selecione o comando ``||Functions:ligar frente||``.

```blocks
basic.forever(function () {
    if (Ligar == 1) {
        frente()
    } else {
    	
    }
})
function frente () {
    fuzzyBot.motorRun(fuzzyBot.Motors.All, fuzzyBot.Dir.CW, Velocidade)
}
```

## Passo 22
Em seguida, acesse a aba ``||basic:Básico||`` e adicione um bloco ``||basic:pausa (ms) 100||`` após a chamada da função para 
determinar por quanto tempo ela será executada antes do próximo movimento. Altere seu valor de **100 ms** para **1000 ms** (1 segundo).
```blocks
basic.forever(function () {
    if (Ligar == 1) {
        frente()
        basic.pause(1000)
    } else {
    	
    }
})
function frente () {
    fuzzyBot.motorRun(fuzzyBot.Motors.All, fuzzyBot.Dir.CW, Velocidade)
}
```

## Passo 23
Vamos replicar essa lógica para chamar a função ``||Functions:esquerda||`` por ``||basic: 1000 (ms)||``.

```blocks
basic.forever(function () {
    if (Ligar == 1) {
        frente()
        basic.pause(1000)
        esquerda()
        basic.pause(1000)
    } else {
    	
    }
})
function frente () {
    fuzzyBot.motorRun(fuzzyBot.Motors.All, fuzzyBot.Dir.CW, Velocidade)
}
function esquerda () {
    fuzzyBot.motorRun(fuzzyBot.Motors.M1, fuzzyBot.Dir.CW, 30)
    fuzzyBot.motorRun(fuzzyBot.Motors.M2, fuzzyBot.Dir.CW, 50)
}
```

## Passo 24
Agora, adicione outro movimento ``||Functions:frente||`` por ``||basic: 1000 (ms)||``.

```blocks
basic.forever(function () {
    if (Ligar == 1) {
        frente()
        basic.pause(1000)
        esquerda()
        basic.pause(10000)
        frente()
        basic.pause(1000)
    } else {
    	
    }
})
function frente () {
    fuzzyBot.motorRun(fuzzyBot.Motors.All, fuzzyBot.Dir.CW, Velocidade)
}
function esquerda () {
    fuzzyBot.motorRun(fuzzyBot.Motors.M1, fuzzyBot.Dir.CW, 30)
    fuzzyBot.motorRun(fuzzyBot.Motors.M2, fuzzyBot.Dir.CW, 50)
}
```

## Passo 25
Vamos aproveitar para incluir um movimento de curva brusca, como o ``||Functions:direita_brusca||`` por ``||basic: 1000 (ms)||``.

```blocks
basic.forever(function () {
    if (Ligar == 1) {
        frente()
        basic.pause(1000)
        esquerda()
        basic.pause(600)
        frente()
        basic.pause(1000)
        direita_brusca()
        basic.pause(200)
    } else {
    	
    }
})
function frente () {
    fuzzyBot.motorRun(fuzzyBot.Motors.All, fuzzyBot.Dir.CW, Velocidade)
}
function esquerda () {
    fuzzyBot.motorRun(fuzzyBot.Motors.M1, fuzzyBot.Dir.CW, 30)
    fuzzyBot.motorRun(fuzzyBot.Motors.M2, fuzzyBot.Dir.CW, 50)
}
function direita_brusca () {
    fuzzyBot.motorRun(fuzzyBot.Motors.M2, fuzzyBot.Dir.CW, 0)
    fuzzyBot.motorRun(fuzzyBot.Motors.M1, fuzzyBot.Dir.CW, 50)
}
```

## Passo 26
Adicione mais um movimento ``||Functions:frente||`` por ``||basic: 1000 (ms)||`` após a curva brusca.

```blocks
basic.forever(function () {
    if (Ligar == 1) {
        frente()
        basic.pause(1000)
        esquerda()
        basic.pause(600)
        frente()
        basic.pause(1000)
        direita_brusca()
        basic.pause(1000)
        frente()
        basic.pause(1000)
    } else {
    	
    }
})
function frente () {
    fuzzyBot.motorRun(fuzzyBot.Motors.All, fuzzyBot.Dir.CW, Velocidade)
}
function esquerda () {
    fuzzyBot.motorRun(fuzzyBot.Motors.M1, fuzzyBot.Dir.CW, 30)
    fuzzyBot.motorRun(fuzzyBot.Motors.M2, fuzzyBot.Dir.CW, 50)
}
function direita_brusca () {
    fuzzyBot.motorRun(fuzzyBot.Motors.M2, fuzzyBot.Dir.CW, 0)
    fuzzyBot.motorRun(fuzzyBot.Motors.M1, fuzzyBot.Dir.CW, 50)
}
```

## Passo 27
Para finalizar, acesse a aba ``||fuzzyBot:FuzzyBoT||`` e insira o comando ``||fuzzyBot:parar motor esquerdo||`` dentro do ``||logic:senão||`` do laço ``||logic:se-então-senão||``.
Modifique o controle de motor ``||fuzzyBot:esquerdo||`` para ``||fuzzyBot:todos||``.

```blocks
basic.forever(function () {
    if (Ligar == 1) {
        frente()
        basic.pause(1000)
        esquerda()
        basic.pause(600)
        frente()
        basic.pause(1000)
        direita_brusca()
        basic.pause(1000)
        frente()
        basic.pause(1000)
    } else {
    	        fuzzyBot.motorStop(fuzzyBot.Motors.All)
    }
})
function frente () {
    fuzzyBot.motorRun(fuzzyBot.Motors.All, fuzzyBot.Dir.CW, Velocidade)
}
function esquerda () {
    fuzzyBot.motorRun(fuzzyBot.Motors.M1, fuzzyBot.Dir.CW, 30)
    fuzzyBot.motorRun(fuzzyBot.Motors.M2, fuzzyBot.Dir.CW, 50)
}
function direita_brusca () {
    fuzzyBot.motorRun(fuzzyBot.Motors.M2, fuzzyBot.Dir.CW, 0)
    fuzzyBot.motorRun(fuzzyBot.Motors.M1, fuzzyBot.Dir.CW, 50)
}
```

## Passo 28
Agora seu código está pronto! Baixe-o para o micro:bit, e teste a movimentação pressionando o botão A para inciar o trajeto.
Fique à vontade para testar outras combinações de movimentos ou ajustar as temporizações de cada um deles.
Pense nas funções de movimento como ingredientes que podem ser combinados de infinitas formas para percorrer seus trajetos.

```blocks
```

## Passo 29
Se necessário, confira o seu código clicando na lâmpada de dica.

```blocks
function tras () {
    fuzzyBot.motorRun(fuzzyBot.Motors.All, fuzzyBot.Dir.CCW, 50)
}
function esquerda () {
    fuzzyBot.motorRun(fuzzyBot.Motors.M1, fuzzyBot.Dir.CW, 30)
    fuzzyBot.motorRun(fuzzyBot.Motors.M2, fuzzyBot.Dir.CW, 50)
}
input.onButtonPressed(Button.A, function () {
    Ligar = 1
})
function esquerda_brusca () {
    fuzzyBot.motorRun(fuzzyBot.Motors.M1, fuzzyBot.Dir.CW, 0)
    fuzzyBot.motorRun(fuzzyBot.Motors.M2, fuzzyBot.Dir.CW, 50)
}
function direita () {
    fuzzyBot.motorRun(fuzzyBot.Motors.M2, fuzzyBot.Dir.CW, 30)
    fuzzyBot.motorRun(fuzzyBot.Motors.M1, fuzzyBot.Dir.CW, 50)
}
input.onButtonPressed(Button.B, function () {
    Ligar = 0
})
function frente () {
    fuzzyBot.motorRun(fuzzyBot.Motors.All, fuzzyBot.Dir.CW, 50)
}
function direita_brusca () {
    fuzzyBot.motorRun(fuzzyBot.Motors.M2, fuzzyBot.Dir.CW, 0)
    fuzzyBot.motorRun(fuzzyBot.Motors.M1, fuzzyBot.Dir.CW, 50)
}
let Ligar = 0
Ligar = 0
basic.forever(function () {
    if (Ligar == 1) {
        frente()
        basic.pause(1000)
        esquerda()
        basic.pause(1000)
        frente()
        basic.pause(1000)
        direita_brusca()
        basic.pause(1000)
        frente()
        basic.pause(1000)
    } else {
        fuzzyBot.motorStop(fuzzyBot.Motors.All)
    }
})

```

```package
fuzzyBot=github:FuzzyMakers/pxt-fuzzyMakers
```