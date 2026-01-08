### @diffs true
# Alerta de asteroides

## Passo 1
Neste tutorial, vamos programar um satélite em órbita que patrulha o espaço 
em busca de asteroides. A matriz de LEDs do micro:bit indicará o ponto que o “satélite” 
percorre, enquanto um sensor analógico 
monitora a presença de objetos. Ao detectar algo, o micro:bit exibirá um alerta 
visual e emitirá um aviso sonoro.


## Passo 2
Para começar, verifique se a biblioteca da Smart Makers já está importada 
em seu MakeCode. Se não estiver, clique na aba **+ Extensões**, 
copie o endereço "https://github.com/FuzzyMakers/pxt-smartMakers", 
cole-o no campo de pesquisa da janela que se abriu e selecione a biblioteca. 

## Passo 3
Acesse o menu ``||variables:Variáveis||`` e clique em 
**"Fazer uma variável..."**. Crie uma variável chamada
``||variables:bateria||``. Em seguida, arraste o bloco ``||variables:definir bateria para 0||`` 
para o bloco ``||basic:no iniciar||``.
Refaça o mesmo processo anterior para criar e definir mais duas variáveis: ``||variables:x||`` e ``||variables:y||``.

```blocks
let bateria = 0
let x = 0
let y = 0
```

## Passo 4
Acerte os valores das variáveis ``||variables:bateria||``, ``||variables:x||``
respectivamente para **30** e **3**.

```blocks
let bateria = 30
let x = 3
let y = 0

```

## Passo 5


No menu ``||actuators:Atuadores||`` busque o bloco ``||actuators:Motor CC, definir velocidade 0 na porta P8||`` e adicione-o
dentro do ``||basic:no iniciar||``.
Mude o valor da velocidade para **400** e a porta para ``||actuators:P12||``.


```blocks
let bateria = 30
let x = 3
let y = 0
actuators.SetSpeedMotor(400, OutputPorts.P12)

```

## Passo 6
Clique no menu ``||Advanced:Avançado||``, acesse ``||Functions:Funções||`` e 
clique em **Fazer uma função...**.
Clique no campo editável do laço azul para criar uma função chamada 
``||functions:atualizar_posição||``. 
Um novo laço referente à função criada é adicionado automaticamente à área de programação.



```blocks
function atualizar_posição () {
	
}
let bateria = 30
let x = 3
let y = 0
actuators.SetSpeedMotor(400, OutputPorts.P12)
```

## Passo 7
Acesse a categoria ``||logic:Lógica||``, pegue a condicional ``||logic:se então senão||``
e insira-a dentro da função ``||functions:atualizar_posição||``. 
Clique no botão **+** **três** vezes para criar outras condições
``||logic:senão se então||``.

```blocks
function atualizar_posição () {
    if (true) {
    	
    } else if (false) {
    	
    } else if (false) {
    	
    } else if (false) {
    	
    } else {
    	
    }
}
let bateria = 30
let x = 3
let y = 0
actuators.SetSpeedMotor(400, OutputPorts.P12)
```

## Passo 8

Volte ao menu ``||logic:Lógica||``, selecione o operador booleano ``||logic: e ||``
e substitua a condição **verdadeiro** da primeira condicional.
```blocks
function atualizar_posição () {
    if (false && false) {
    	
    } else if (false) {
    	
    } else if (false) {
    	
    } else if (false) {
    	
    } else {
    	
    }
}
let bateria = 30
let x = 3
let y = 0
actuators.SetSpeedMotor(400, OutputPorts.P12)

```

## Passo 9
Ainda na categoria ``||logic:Lógica||``, pegue **dois** comparadores ``||logic: 0 = 0||``
para colocar nos campos vazios do operador booleano.
Modifique o sinal do segundo comparador para **!=** (diferente).

```blocks
function atualizar_posição () {
    if (0 == 0 && 0 != 0) {
    	
    } else if (false) {
    	
    } else if (false) {
    	
    } else if (false) {
    	
    } else {
    	
    }
}
let bateria = 30
let x = 3
let y = 0
actuators.SetSpeedMotor(400, OutputPorts.P12)
```

## Passo 10
Agora atualize os campos dos comparadores.
Pegue a variável ``||variables:y||``  para colocá-la no primeiro campo do primeiro comparador.
No segundo campo do primeiro comparador, mantenha o valor **0**.
Volte até a aba ``||variables:Variáveis||``,
troque o primeiro **0** do segundo comparador por ``||variables:x||`` e o segundo por **4**.

```blocks
function atualizar_posição () {
    if (y == 0 && x != 4) {
    	
    } else if (false) {
    	
    } else if (false) {
    	
    } else if (false) {
    	
    } else {
    	
    }
}
let bateria = 30
let x = 3
let y = 0
actuators.SetSpeedMotor(400, OutputPorts.P12)
```


## Passo 11
Acesse mais uma vez a seção ``||variables:Variáveis||``, pegue o comando
``||variables:Alterar y por 1||`` e posicione-o no primeiro ``||logic:se então||``.
Modifique a variável de ``||variables:y||`` para ``||variables:x||``.

```blocks
function atualizar_posição () {
    if (y == 0 && x != 4) {
        x += 1
    } else if (false) {
    	
    } else if (false) {
    	
    } else if (false) {
    	
    } else {
    	
    }
}
let bateria = 30
let x = 3
let y = 0
actuators.SetSpeedMotor(400, OutputPorts.P12)
```

## Passo 12

Duplique toda a operação booleana e coloque-a no lugar da primeira condição **falso**.
Altere o primeiro comparador para ``||logic:x=4||`` e o segundo para ``||logic:y!=4||`` .

```blocks
function atualizar_posição () {
    if (y == 0 && x != 4) {
        x += 1
    } else if (x == 4 && y != 4) {
    	
    } else if (false) {
    	
    } else if (false) {
    	
    } else {
    	
    }
}
let bateria = 30
let x = 3
let y = 0
actuators.SetSpeedMotor(400, OutputPorts.P12)
```

## Passo 13

Acesse mais uma vez a seção ``||variables:Variáveis||``, pegue o comando
``||variables:Alterar y por 1||`` e posicione-o no primeiro ``||logic:senão se então||``.

```blocks
function atualizar_posição () {
    if (y == 0 && x != 4) {
        x += 1
    } else if (x == 4 && y != 4) {
        y += 1
    } else if (false) {
    	
    } else if (false) {
    	
    } else {
    	
    }
}
let bateria = 30
let x = 3
let y = 0
actuators.SetSpeedMotor(400, OutputPorts.P12)


```


## Passo 14

Duplique novamente toda a operação booleana e coloque-a no lugar da segunda condição **falso**.
Altere o primeiro comparador para ``||logic:y=4||`` e o segundo para ``||logic:x!=0||`` .
```blocks
function atualizar_posição () {
    if (y == 0 && x != 4) {
        x += 1
    } else if (x == 4 && y != 4) {
        y += 1
    } else if (y == 4 && x != 0) {
    	
    } else if (false) {
    	
    } else {
    	
    }
}
let bateria = 30
let x = 3
let y = 0
actuators.SetSpeedMotor(400, OutputPorts.P12)

```

## Passo 15

Copie o comando ``||variables:Alterar x por 1||`` e cole-o dentro da condicional.
Altere o valor de **1** para **-1**.
```blocks
function atualizar_posição () {
    if (y == 0 && x != 4) {
        x += 1
    } else if (x == 4 && y != 4) {
        y += 1
    } else if (y == 4 && x != 0) {
        x += -1
    } else if (false) {
    	
    } else {
    	
    }
}
let bateria = 30
let x = 3
let y = 0
actuators.SetSpeedMotor(400, OutputPorts.P12)

```

## Passo 16

Pela última vez duplique toda a operação booleana e coloque-a no lugar da última condição **falso**.
Altere o primeiro comparador para ``||logic:x=0||`` e o segundo para ``||logic:y!=0||`` .
```blocks
function atualizar_posição () {
    if (y == 0 && x != 4) {
        x += 1
    } else if (x == 4 && y != 4) {
        y += 1
    } else if (y == 4 && x != 0) {
        x += -1
    } else if (y == 0 && x != 0) {
    	
    } else {
    	
    }
}
let bateria = 30
let x = 3
let y = 0
actuators.SetSpeedMotor(400, OutputPorts.P12)


```

## Passo 17

Copie o comando ``||variables:Alterar y por 1||`` e cole-o dentro da condicional.
Altere o valor de **1** para **-1**.

```blocks
function atualizar_posição () {
    if (y == 0 && x != 4) {
        x += 1
    } else if (x == 4 && y != 4) {
        y += 1
    } else if (y == 4 && x != 0) {
        x += -1
    } else if (y == 0 && x != 0) {
        y += -1
    } else {
    	
    }
}
let bateria = 30
let x = 3
let y = 0
actuators.SetSpeedMotor(400, OutputPorts.P12)
```

## Passo 18

Clique no botão **-** da condição ``||logic:senão -||`` para removê-la.

```blocks
function atualizar_posição () {
    if (y == 0 && x != 4) {
        x += 1
    } else if (x == 4 && y != 4) {
        y += 1
    } else if (y == 4 && x != 0) {
        x += -1
    } else if (y == 0 && x != 0) {
        y += -1
    }
}
let bateria = 30
let x = 3
let y = 0
actuators.SetSpeedMotor(400, OutputPorts.P12)
```

## Passo 19

Na categoria ``||basic:Básico||``, arraste uma pausa ``||basic:pausa (ms) 100||`` para o código,
depois, acesse o menu ``||math:Matemática||`` e pegue uma operação de multiplicação ``||math:0 x 0||`` para preencher o valor da pausa.

```blocks
function atualizar_posição () {
    if (y == 0 && x != 4) {
        x += 1
    } else if (x == 4 && y != 4) {
        y += 1
    } else if (y == 4 && x != 0) {
        x += -1
    } else if (y == 0 && x != 0) {
        y += -1
    }
    basic.pause(0 * 0)
}
let bateria = 30
let x = 3
let y = 0
actuators.SetSpeedMotor(400, OutputPorts.P12)

```

## Passo 20

Atualize os campos da multiplicação para **9.5** e **62.5**.
```blocks
function atualizar_posição () {
    if (y == 0 && x != 4) {
        x += 1
    } else if (x == 4 && y != 4) {
        y += 1
    } else if (y == 4 && x != 0) {
        x += -1
    } else if (y == 0 && x != 0) {
        y += -1
    }
    basic.pause(9.5 * 62.5)
}
let bateria = 30
let x = 3
let y = 0
actuators.SetSpeedMotor(400, OutputPorts.P12)
```

## Passo 21

Clique no menu ``||Advanced:Avançado||``, acesse ``||Functions:Funções||`` e 
clique em **Fazer uma função...**.
Clique no campo editável do laço azul para criar uma função chamada 
``||functions:carregar||``. 
Um novo laço referente à função criada é adicionado automaticamente à área de programação.
```blocks
function atualizar_posição () {
    if (y == 0 && x != 4) {
        x += 1
    } else if (x == 4 && y != 4) {
        y += 1
    } else if (y == 4 && x != 0) {
        x += -1
    } else if (y == 0 && x != 0) {
        y += -1
    }
    basic.pause(9.5 * 62.5)
}
function carregar () {
	
}
let bateria = 30
let x = 3
let y = 0
actuators.SetSpeedMotor(400, OutputPorts.P12)


```
## Passo 22

Acesse a categoria ``||logic:Lógica||``, clique na condicional ``||logic:se então||``
e insira-a dentro da função ``||functions:carregar||``.

```blocks
function atualizar_posição () {
    if (y == 0 && x != 4) {
        x += 1
    } else if (x == 4 && y != 4) {
        y += 1
    } else if (y == 4 && x != 0) {
        x += -1
    } else if (y == 0 && x != 0) {
        y += -1
    }
    basic.pause(9.5 * 62.5)
}
function carregar () {
    if (true) {
    	
    }
}
let bateria = 30
let x = 3
let y = 0
actuators.SetSpeedMotor(400, OutputPorts.P12)
```

## Passo 23

Volte ao menu ``||logic:Lógica||``, selecione o operador booleano ``||logic: e ||``
e substitua a condição **verdadeiro** da condicional.

```blocks
function atualizar_posição () {
    if (y == 0 && x != 4) {
        x += 1
    } else if (x == 4 && y != 4) {
        y += 1
    } else if (y == 4 && x != 0) {
        x += -1
    } else if (y == 0 && x != 0) {
        y += -1
    }
    basic.pause(9.5 * 62.5)
}
function carregar () {
    if (false && false) {
    	
    }
}
let bateria = 30
let x = 3
let y = 0
actuators.SetSpeedMotor(400, OutputPorts.P12)

```
## Passo 24

Ainda na categoria ``||logic:Lógica||``, pegue **dois** comparadores ``||logic: 0 < 0||``
para colocar nos campos vazios do operador booleano.
Modifique o sinal do segundo comparador para **>=**.

```blocks
function atualizar_posição () {
    if (y == 0 && x != 4) {
        x += 1
    } else if (x == 4 && y != 4) {
        y += 1
    } else if (y == 4 && x != 0) {
        x += -1
    } else if (y == 0 && x != 0) {
        y += -1
    }
    basic.pause(9.5 * 62.5)
}
function carregar () {
    if (0 < 0 && 0 >= 0) {
    	
    }
}
let bateria = 30
let x = 3
let y = 0
actuators.SetSpeedMotor(400, OutputPorts.P12)
```

## Passo 25

Agora atualize os campos dos comparadores.
Pegue a variável ``||variables:bateria||``  para colocá-la no primeiro campo do primeiro comparador.
Edite o segundo campo do primeiro comparador de **0** para **100**.
Vá até a aba ``||input:Entrada||``,
troque o primeiro **0** do segundo comparador por ``||input:nível de luz||`` e o segundo por **60**.


```blocks
function atualizar_posição () {
    if (y == 0 && x != 4) {
        x += 1
    } else if (x == 4 && y != 4) {
        y += 1
    } else if (y == 4 && x != 0) {
        x += -1
    } else if (y == 0 && x != 0) {
        y += -1
    }
    basic.pause(9.5 * 62.5)
}
function carregar () {
    if (bateria < 100 && input.lightLevel() >= 60) {
    	
    }
}
let bateria = 30
let x = 3
let y = 0
actuators.SetSpeedMotor(400, OutputPorts.P12)
```

## Passo 26

Retorne ao menu ``||variables:Variáveis||`` e arraste o comando
``||variables:alterar y por 1||`` para a condicional. 
Modifique a variável ``||variables:y||`` por ``||variables:bateria||``.


```blocks
function atualizar_posição () {
    if (y == 0 && x != 4) {
        x += 1
    } else if (x == 4 && y != 4) {
        y += 1
    } else if (y == 4 && x != 0) {
        x += -1
    } else if (y == 0 && x != 0) {
        y += -1
    }
    basic.pause(9.5 * 62.5)
}
function carregar () {
    if (bateria < 100 && input.lightLevel() >= 60) {
        bateria += 1
    }
}
let bateria = 30
let x = 3
let y = 0
actuators.SetSpeedMotor(400, OutputPorts.P12)

```

## Passo 27

Duplique a condicional ``||logic:se então||`` e posicione-a embaixo da outra 
condicional dentro da função ``||functions:carregar||``.

```blocks
function atualizar_posição () {
    if (y == 0 && x != 4) {
        x += 1
    } else if (x == 4 && y != 4) {
        y += 1
    } else if (y == 4 && x != 0) {
        x += -1
    } else if (y == 0 && x != 0) {
        y += -1
    }
    basic.pause(9.5 * 62.5)
}
function carregar () {
    if (bateria < 100 && input.lightLevel() >= 60) {
        bateria += 1
    }
    if (bateria < 100 && input.lightLevel() >= 60) {
        bateria += 1
    }
}
let bateria = 30
let x = 3
let y = 0
actuators.SetSpeedMotor(400, OutputPorts.P12)


```

## Passo 28

Edite o primeiro comparador da segunda condicional para ``||logic:bateria>0||``.
Modifique o segundo comparador para ``||logic:nível de luz<60||``.
Por fim, altere o valor do comando de incremento da variável de **1** para **-1**.

```blocks
function atualizar_posição () {
    if (y == 0 && x != 4) {
        x += 1
    } else if (x == 4 && y != 4) {
        y += 1
    } else if (y == 4 && x != 0) {
        x += -1
    } else if (y == 0 && x != 0) {
        y += -1
    }
    basic.pause(9.5 * 62.5)
}
function carregar () {
    if (bateria < 100 && input.lightLevel() >= 60) {
        bateria += 1
    }
    if (bateria > 0 && input.lightLevel() < 60) {
        bateria += -1
    }
}
let bateria = 30
let x = 3
let y = 0
actuators.SetSpeedMotor(400, OutputPorts.P12)
```

## Passo 29

No menu ``||functions:Funções||`` arraste os comandos  ``||functions:ligar carregar||`` e ``||functions:ligar atualizar_posição||``
para dentro do laço ``||basic:sempre||``.

```blocks
function atualizar_posição () {
    if (y == 0 && x != 4) {
        x += 1
    } else if (x == 4 && y != 4) {
        y += 1
    } else if (y == 4 && x != 0) {
        x += -1
    } else if (y == 0 && x != 0) {
        y += -1
    }
    basic.pause(9.5 * 62.5)
}
function carregar () {
    if (bateria < 100 && input.lightLevel() >= 60) {
        bateria += 1
    }
    if (bateria > 0 && input.lightLevel() < 60) {
        bateria += -1
    }
}
let bateria = 30
let x = 3
let y = 0
actuators.SetSpeedMotor(400, OutputPorts.P12)
basic.forever(function () {
    carregar()
    atualizar_posição()
})

```

## Passo 30

Na aba ``||basic:Básico||`` arraste outro laço ``||basic:sempre||`` 
para a área de programação.

```blocks
function atualizar_posição () {
    if (y == 0 && x != 4) {
        x += 1
    } else if (x == 4 && y != 4) {
        y += 1
    } else if (y == 4 && x != 0) {
        x += -1
    } else if (y == 0 && x != 0) {
        y += -1
    }
    basic.pause(9.5 * 62.5)
}
function carregar () {
    if (bateria < 100 && input.lightLevel() >= 60) {
        bateria += 1
    }
    if (bateria > 0 && input.lightLevel() < 60) {
        bateria += -1
    }
}
let bateria = 30
let x = 3
let y = 0
actuators.SetSpeedMotor(400, OutputPorts.P12)
basic.forever(function () {
    carregar()
    atualizar_posição()
})
basic.forever(function () {
	
})
```

## Passo 31

Acesse a categoria ``||logic:Lógica||``, clique na condicional ``||logic:se então senão||``
e insira-a no novo laço ``||basic:sempre||``.

```blocks
function atualizar_posição () {
    if (y == 0 && x != 4) {
        x += 1
    } else if (x == 4 && y != 4) {
        y += 1
    } else if (y == 4 && x != 0) {
        x += -1
    } else if (y == 0 && x != 0) {
        y += -1
    }
    basic.pause(9.5 * 62.5)
}
function carregar () {
    if (bateria < 100 && input.lightLevel() >= 60) {
        bateria += 1
    }
    if (bateria > 0 && input.lightLevel() < 60) {
        bateria += -1
    }
}
let bateria = 30
let x = 3
let y = 0
actuators.SetSpeedMotor(400, OutputPorts.P12)
basic.forever(function () {
    carregar()
    atualizar_posição()
})
basic.forever(function () {
    if (true) {
    	
    } else {
    	
    }
})

```

## Passo 32

Volte ao menu ``||logic:Lógica||``, pegue o comparador ``||logic:0 < 0||``
e substitua a condição **verdadeiro** da condicional.

```blocks
function atualizar_posição () {
    if (y == 0 && x != 4) {
        x += 1
    } else if (x == 4 && y != 4) {
        y += 1
    } else if (y == 4 && x != 0) {
        x += -1
    } else if (y == 0 && x != 0) {
        y += -1
    }
    basic.pause(9.5 * 62.5)
}
function carregar () {
    if (bateria < 100 && input.lightLevel() >= 60) {
        bateria += 1
    }
    if (bateria > 0 && input.lightLevel() < 60) {
        bateria += -1
    }
}
let bateria = 30
let x = 3
let y = 0
actuators.SetSpeedMotor(400, OutputPorts.P12)
basic.forever(function () {
    carregar()
    atualizar_posição()
})
basic.forever(function () {
    if (0 < 0) {
    	
    } else {
    	
    }
})
```

## Passo 33

Agora atualize os campos do comparador. Vá até a aba ``||variables:Variáveis||``,
clique no bloco ``||variables:bateria||`` e troque 
o primeiro **0** do comparador. Edite o sinal do comparador para **>**.

```blocks
function atualizar_posição () {
    if (y == 0 && x != 4) {
        x += 1
    } else if (x == 4 && y != 4) {
        y += 1
    } else if (y == 4 && x != 0) {
        x += -1
    } else if (y == 0 && x != 0) {
        y += -1
    }
    basic.pause(9.5 * 62.5)
}
function carregar () {
    if (bateria < 100 && input.lightLevel() >= 60) {
        bateria += 1
    }
    if (bateria > 0 && input.lightLevel() < 60) {
        bateria += -1
    }
}
let bateria = 30
let x = 3
let y = 0
actuators.SetSpeedMotor(400, OutputPorts.P12)
basic.forever(function () {
    carregar()
    atualizar_posição()
})
basic.forever(function () {
    if (bateria > 0) {
    	
    } else {
    	
    }
})

```

## Passo 34

Acesse a categoria ``||logic:Lógica||``, pegue outra condicional ``||logic:se então senão||``
e insira-a dentro do bloco ``||logic:se bateria > 0 então||``. 

```blocks
function atualizar_posição () {
    if (y == 0 && x != 4) {
        x += 1
    } else if (x == 4 && y != 4) {
        y += 1
    } else if (y == 4 && x != 0) {
        x += -1
    } else if (y == 0 && x != 0) {
        y += -1
    }
    basic.pause(9.5 * 62.5)
}
function carregar () {
    if (bateria < 100 && input.lightLevel() >= 60) {
        bateria += 1
    }
    if (bateria > 0 && input.lightLevel() < 60) {
        bateria += -1
    }
}
let bateria = 30
let x = 3
let y = 0
actuators.SetSpeedMotor(400, OutputPorts.P12)
basic.forever(function () {
    carregar()
    atualizar_posição()
})
basic.forever(function () {
    if (bateria > 0) {
        if (true) {
        	
        } else {
        	
        }
    } else {
    	
    }
})
```

## Passo 35

Volte ao menu ``||logic:Lógica||``, pegue o comparador ``||logic:0 < 0||``
e substitua a condição **verdadeiro** da primeira condicional.

```blocks
function atualizar_posição () {
    if (y == 0 && x != 4) {
        x += 1
    } else if (x == 4 && y != 4) {
        y += 1
    } else if (y == 4 && x != 0) {
        x += -1
    } else if (y == 0 && x != 0) {
        y += -1
    }
    basic.pause(9.5 * 62.5)
}
function carregar () {
    if (bateria < 100 && input.lightLevel() >= 60) {
        bateria += 1
    }
    if (bateria > 0 && input.lightLevel() < 60) {
        bateria += -1
    }
}
let bateria = 30
let x = 3
let y = 0
actuators.SetSpeedMotor(400, OutputPorts.P12)
basic.forever(function () {
    carregar()
    atualizar_posição()
})
basic.forever(function () {
    if (bateria > 0) {
        if (0 < 0) {
        	
        } else {
        	
        }
    } else {
    	
    }
})
```

## Passo 36

Agora atualize os campos do comparador. Vá até a aba ``||sensors:Sensores||``,
pegue o bloco ``||sensors:Valor do sensor infravermelho na porta P2||`` e edite o primeiro **0** do comparador.
Altere a porta de ``||sensors:P2||`` para ``||sensors:P1||``.
Mude o sinal de **<** para **>** e o segundo valor para **400**.


```blocks
function atualizar_posição () {
    if (y == 0 && x != 4) {
        x += 1
    } else if (x == 4 && y != 4) {
        y += 1
    } else if (y == 4 && x != 0) {
        x += -1
    } else if (y == 0 && x != 0) {
        y += -1
    }
    basic.pause(9.5 * 62.5)
}
function carregar () {
    if (bateria < 100 && input.lightLevel() >= 60) {
        bateria += 1
    }
    if (bateria > 0 && input.lightLevel() < 60) {
        bateria += -1
    }
}
let bateria = 30
let x = 3
let y = 0
actuators.SetSpeedMotor(400, OutputPorts.P12)
basic.forever(function () {
    carregar()
    atualizar_posição()
})
basic.forever(function () {
    if (bateria > 0) {
        if (sensors.infraredValue(InputPorts.P1) > 400) {
        	
        } else {
        	
        }
    } else {
    	
    }
})

```

## Passo 37

Acesse a categoria ``||basic:Básico||``, pegue o comando ``||basic:limpar tela||`` 
e coloque-o dentro desse novo ``||logic:então||``.



```blocks
function atualizar_posição () {
    if (y == 0 && x != 4) {
        x += 1
    } else if (x == 4 && y != 4) {
        y += 1
    } else if (y == 4 && x != 0) {
        x += -1
    } else if (y == 0 && x != 0) {
        y += -1
    }
    basic.pause(9.5 * 62.5)
}
function carregar () {
    if (bateria < 100 && input.lightLevel() >= 60) {
        bateria += 1
    }
    if (bateria > 0 && input.lightLevel() < 60) {
        bateria += -1
    }
}
let bateria = 30
let x = 3
let y = 0
actuators.SetSpeedMotor(400, OutputPorts.P12)
basic.forever(function () {
    carregar()
    atualizar_posição()
})
basic.forever(function () {
    if (bateria > 0) {
        if (sensors.infraredValue(InputPorts.P1) > 400) {
            basic.clearScreen()
        } else {
        	
        }
    } else {
    	
    }
})
```

## Passo 38

Vá até o menu ``||led:Led||`` e leve um bloco ``||led:plotar x 0 y 0||`` para dentro desse novo ``||logic:então||``.
Substitua os valores **0** por ``||variables:x||`` e ``||variables:y||``.

```blocks
function atualizar_posição () {
    if (y == 0 && x != 4) {
        x += 1
    } else if (x == 4 && y != 4) {
        y += 1
    } else if (y == 4 && x != 0) {
        x += -1
    } else if (y == 0 && x != 0) {
        y += -1
    }
    basic.pause(9.5 * 62.5)
}
function carregar () {
    if (bateria < 100 && input.lightLevel() >= 60) {
        bateria += 1
    }
    if (bateria > 0 && input.lightLevel() < 60) {
        bateria += -1
    }
}
let bateria = 30
let x = 3
let y = 0
actuators.SetSpeedMotor(400, OutputPorts.P12)
basic.forever(function () {
    carregar()
    atualizar_posição()
})
basic.forever(function () {
    if (bateria > 0) {
        if (sensors.infraredValue(InputPorts.P1) > 400) {
            basic.clearScreen()
            led.plot(x, y)
        } else {
        	
        }
    } else {
    	
    }
})
```

## Passo 39

Acesse a aba ``||music:Música||`` e adicione o bloco ``||music:play tone C Médio for 1 batida until done||`` 
dentro da condicional ``||logic:se então||``.

```blocks
function atualizar_posição () {
    if (y == 0 && x != 4) {
        x += 1
    } else if (x == 4 && y != 4) {
        y += 1
    } else if (y == 4 && x != 0) {
        x += -1
    } else if (y == 0 && x != 0) {
        y += -1
    }
    basic.pause(9.5 * 62.5)
}
function carregar () {
    if (bateria < 100 && input.lightLevel() >= 60) {
        bateria += 1
    }
    if (bateria > 0 && input.lightLevel() < 60) {
        bateria += -1
    }
}
let bateria = 30
let x = 3
let y = 0
actuators.SetSpeedMotor(400, OutputPorts.P12)
basic.forever(function () {
    carregar()
    atualizar_posição()
})
basic.forever(function () {
    if (bateria > 0) {
        if (sensors.infraredValue(InputPorts.P1) > 400) {
            basic.clearScreen()
            led.plot(x, y)
            music.play(music.tonePlayable(262, music.beat(BeatFraction.Whole)), music.PlaybackMode.UntilDone)
        } else {
        	
        }
    } else {
    	
    }
})
```

## Passo 40

Na categoria ``||basic:Básico||`` arraste uma pausa ``||basic:pausa (ms) 100||`` para o código,
depois, mude seu valor para **200**.

```blocks
function atualizar_posição () {
    if (y == 0 && x != 4) {
        x += 1
    } else if (x == 4 && y != 4) {
        y += 1
    } else if (y == 4 && x != 0) {
        x += -1
    } else if (y == 0 && x != 0) {
        y += -1
    }
    basic.pause(9.5 * 62.5)
}
function carregar () {
    if (bateria < 100 && input.lightLevel() >= 60) {
        bateria += 1
    }
    if (bateria > 0 && input.lightLevel() < 60) {
        bateria += -1
    }
}
let bateria = 30
let x = 3
let y = 0
actuators.SetSpeedMotor(400, OutputPorts.P12)
basic.forever(function () {
    carregar()
    atualizar_posição()
})
basic.forever(function () {
    if (bateria > 0) {
        if (sensors.infraredValue(InputPorts.P1) > 400) {
            basic.clearScreen()
            led.plot(x, y)
            music.play(music.tonePlayable(262, music.beat(BeatFraction.Whole)), music.PlaybackMode.UntilDone)
            basic.pause(200)
        } else {
        	
        }
    } else {
    	
    }
})
```

## Passo 41

Volte à aba ``||led:Led||`` e pegue o bloco ``||led:plot bar graph of 0 up to 0||``, posicione-o dentro do ``||logic:senão||`` mais interno.
Substitua os valores **0** por ``||variables:bateria||`` e **100**.

```blocks
function atualizar_posição () {
    if (y == 0 && x != 4) {
        x += 1
    } else if (x == 4 && y != 4) {
        y += 1
    } else if (y == 4 && x != 0) {
        x += -1
    } else if (y == 0 && x != 0) {
        y += -1
    }
    basic.pause(9.5 * 62.5)
}
function carregar () {
    if (bateria < 100 && input.lightLevel() >= 60) {
        bateria += 1
    }
    if (bateria > 0 && input.lightLevel() < 60) {
        bateria += -1
    }
}
let bateria = 30
let x = 3
let y = 0
actuators.SetSpeedMotor(400, OutputPorts.P12)
basic.forever(function () {
    carregar()
    atualizar_posição()
})
basic.forever(function () {
    if (bateria > 0) {
        if (sensors.infraredValue(InputPorts.P1) > 400) {
            basic.clearScreen()
            led.plot(x, y)
            music.play(music.tonePlayable(262, music.beat(BeatFraction.Whole)), music.PlaybackMode.UntilDone)
            basic.pause(200)
        } else {
            led.plotBarGraph(
            bateria,
            100
            )
        }
    } else {
    	
    }
})
```

## Passo 42

No outro ``||logic:senão||`` coloque um comando ``||basic:mostrar ícone||``, que pode ser retirado da categoria
``||basic:Básico||``. Altere o ícone do coração para **"X"**.

```blocks
function atualizar_posição () {
    if (y == 0 && x != 4) {
        x += 1
    } else if (x == 4 && y != 4) {
        y += 1
    } else if (y == 4 && x != 0) {
        x += -1
    } else if (y == 0 && x != 0) {
        y += -1
    }
    basic.pause(9.5 * 62.5)
}
function carregar () {
    if (bateria < 100 && input.lightLevel() >= 60) {
        bateria += 1
    }
    if (bateria > 0 && input.lightLevel() < 60) {
        bateria += -1
    }
}
let bateria = 30
let x = 3
let y = 0
actuators.SetSpeedMotor(400, OutputPorts.P12)
basic.forever(function () {
    carregar()
    atualizar_posição()
})
basic.forever(function () {
    if (bateria > 0) {
        if (sensors.infraredValue(InputPorts.P1) > 400) {
            basic.clearScreen()
            led.plot(x, y)
            music.play(music.tonePlayable(262, music.beat(BeatFraction.Whole)), music.PlaybackMode.UntilDone)
            basic.pause(200)
        } else {
            led.plotBarGraph(
            bateria,
            100
            )
        }
    } else {
        basic.showIcon(IconNames.No)
    }
})

```

## Passo 43

Agora seu código está pronto! Baixe-o para o micro:bit e teste-o.
Ao ligar o projeto, observe o movimento circular da estação espacial, ao aproximar algo do sensor infravermelho um alerta é emitido com a posição
do "asteroide" indicada no display. Se a tela mostrar o ícone **X** é porque a carga chegou ao final, direcione uma fonte de luz para o micro:bit para carregar o sistema.
```blocks
```


## Passo 44
Se necessário, confira o seu código clicando na lâmpada de dica.

```blocks
function atualizar_posição () {
    if (y == 0 && x != 4) {
        x += 1
    } else if (x == 4 && y != 4) {
        y += 1
    } else if (y == 4 && x != 0) {
        x += -1
    } else if (y == 0 && x != 0) {
        y += -1
    }
    basic.pause(9.5 * 62.5)
}
function carregar () {
    if (bateria < 100 && input.lightLevel() >= 60) {
        bateria += 1
    }
    if (bateria > 0 && input.lightLevel() < 60) {
        bateria += -1
    }
}
let bateria = 30
let x = 3
let y = 0
y = 0
actuators.SetSpeedMotor(400, OutputPorts.P12)
basic.forever(function () {
    carregar()
    atualizar_posição()
})
basic.forever(function () {
    if (bateria > 0) {
        if (sensors.infraredValue(InputPorts.P1) > 400) {
            basic.clearScreen()
            led.plot(x, y)
            music.play(music.tonePlayable(262, music.beat(BeatFraction.Whole)), music.PlaybackMode.UntilDone)
            basic.pause(200)
        } else {
            led.plotBarGraph(
            bateria,
            100
            )
        }
    } else {
        basic.showIcon(IconNames.No)
    }
})
```



```package
fuzzyBot=github:FuzzyMakers/pxt-fuzzyMakers
```
