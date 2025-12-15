### @diffs true
# Classificação de Triângulos

## Passo 1
Nessa atividade, vamos programar o aparelho que utiliza um potenciômetro e um servomotor 
para medir os três ângulos de um triângulo e exibir sua classificação na tela do micro:bit.
Depois de salvar os ângulos em um vetor, o programa classifica o triângulo como acutângulo ou obtusângulo.

## Passo 2
Para começar, verifique se a biblioteca da Smart Makers já está importada em seu MakeCode.
Se não estiver, clique na aba **+ Extensões**, copie o endereço "https://github.com/FuzzyMakers/pxt-smartMakers",
cole-o no campo de pesquisa da janela que se abriu e selecione a biblioteca.

## Passo 3
Acesse o menu ``||variables:Variáveis||`` e clique em **"Fazer uma variável..."**.
Vamos criar três variáveis chamadas: ``||variables:graus||``, ``||variables:estado||`` e ``||variables:angulos||``. 
Por fim, adicione o bloco ``||variables:definir angulos para 0||`` que
aparecerá ao criá-la, dentro do laço ``||basic:sempre||``.  

```blocks
let angulos = 0
basic.forever(function () {
    angulos = 0
})
```

## Passo 4
Em seguida, clique em **Avançado** para abrir novas categorias. Acesse 
a aba ``||arrays:Matriz||`` e selecione o bloco ``||arrays:matriz vazia||`` para substituir
o **0** do bloco de definição da variável ``||variables:angulos||``.  

```blocks
let angulos: number[] = []
basic.forever(function () {
    angulos = []
})
```

## Passo 5
Agora, acesse a categoria ``||loops:Loops||`` e adicione o laço ``||loops:repetir 4 vezes executar||``
dentro do laço ``||basic:sempre||``. Altere a quantidade de repetições de **4** para **3**.

```blocks
let angulos: number[] = []
basic.forever(function () {
    angulos = []
    for (let index = 0; index < 3; index++) {
    	
    }
})
```

## Passo 6
Dentro desse ``||loops:executar||``, adicione um bloco ``||variables:definir estado para 0||``
localizado na categoria ``||variables:Variáveis||``. Se o seu bloco de definição estiver com outra variável,
basta adicioná-lo, clicar na seta e alterar para a variável desejada, neste caso, ``||variables:estado||``.

```blocks
let angulos: number[] = []
let estado = 0
basic.forever(function () {
    angulos = []
    for (let index = 0; index < 3; index++) {
        estado = 0
    }
})
```

## Passo 7
Agora, acesse o menu ``||sensors:Sensores||`` e insira o bloco ``||sensors:Valor do Botão na porta P2||``
no campo do bloco de definição da variável, substituindo o valor **0**.

```blocks
let angulos: number[] = []
let estado = 0
basic.forever(function () {
    angulos = []
    for (let index = 0; index < 3; index++) {
        estado = sensors.buttonValue(InputPorts.P2)
    }
})
```

## Passo 8
Retorne à categoria ``||loops:Loops||`` e adicione um bloco ``||loops:enquanto falso executar||``
abaixo do bloco de definição da variável ``||variables:estado||``, ainda dentro do ``||loops:repetir 3 vezes||``.

```blocks
let angulos: number[] = []
let estado = 0
basic.forever(function () {
    angulos = []
    for (let index = 0; index < 3; index++) {
        estado = sensors.buttonValue(InputPorts.P2)
        while (false) {
        	
        }
    }
})
```

## Passo 9
Acesse a aba ``||logic:Lógica||`` e utilize um bloco comparador ``||logic:0 = 0||``
para substituir o campo ``||logic:falso||`` do bloco ``||loops:enquanto executar||``.

```blocks
let angulos: number[] = []
let estado = 0
basic.forever(function () {
    angulos = []
    for (let index = 0; index < 3; index++) {
        estado = sensors.buttonValue(InputPorts.P2)
        while (0 == 0) {
        	
        }
    }
})
```

## Passo 10
No primeiro campo desse comparador, deve ser inserido o bloco ``||sensors:Valor do Botão na porta P2||``
localizado na aba ``||sensors:Sensores||``. Enquanto isso, o segundo campo deve ser o bloco 
``||variables:estado||``, localizado na aba ``||variables:Variáveis||``.

```blocks
let angulos: number[] = []
let estado = 0
basic.forever(function () {
    angulos = []
    for (let index = 0; index < 3; index++) {
        estado = sensors.buttonValue(InputPorts.P2)
        while (sensors.buttonValue(InputPorts.P2) == estado) {
        	
        }
    }
})
```

## Passo 11
Dentro do ``||loops:executar||`` deste laço ``||loops:enquanto||``, adicione o comando
``||basic:mostrar número||`` localizado na aba ``||basic:Básico||``. Altere o campo do valor 
desse bloco de **0** para a variável ``||variables:graus||``.  

```blocks
let angulos: number[] = []
let estado = 0
basic.forever(function () {
    angulos = []
    for (let index = 0; index < 3; index++) {
        estado = sensors.buttonValue(InputPorts.P2)
        while (sensors.buttonValue(InputPorts.P2) == estado) {
            let graus = 0
            basic.showNumber(graus)
        }
    }
})
```

## Passo 12
Agora, clique em **Avançado** para abrir a categoria ``||arrays:Matriz||`` e selecionar o bloco
``||arrays:list adicionar valor () no final||``. Posicione-o abaixo do ``||loops:enquanto executar||``,
mas ainda dentro de ``||loops:repetir 3 vezes||``. 
Antes de prosseguir, clique na seta para alterar de variável ``||variables:list||`` para a variável ``||variables:angulos||``.

```blocks
let angulos: number[] = []
let estado = 0
basic.forever(function () {
    angulos = []
    for (let index = 0; index < 3; index++) {
        estado = sensors.buttonValue(InputPorts.P2)
        while (sensors.buttonValue(InputPorts.P2) == estado) {
            let graus = 0
            basic.showNumber(graus)
        }
        angulos.push(0)
    }
})
```

## Passo 13
Em seguida, preencha o campo de valor com a variável ``||variables:graus||``.

```blocks
let angulos: number[] = []
let estado = 0
basic.forever(function () {
    angulos = []
    for (let index = 0; index < 3; index++) {
        let graus = 0
        estado = sensors.buttonValue(InputPorts.P2)
        while (sensors.buttonValue(InputPorts.P2) == estado) {
            basic.showNumber(graus)
        }
        angulos.push(graus)
    }
})
```

## Passo 14
Exatamente abaixo desse bloco, adicione um ``||music:play tone C Médio for 1 batida until done||``
localizado na aba ``||music:Música||``. Assim finalizamos o bloco ``||loops:repetir 3 vezes||``. 

```blocks
let angulos: number[] = []
let estado = 0
basic.forever(function () {
    angulos = []
    for (let index = 0; index < 3; index++) {
        let graus = 0
        estado = sensors.buttonValue(InputPorts.P2)
        while (sensors.buttonValue(InputPorts.P2) == estado) {
            basic.showNumber(graus)
        }
        angulos.push(graus)
        music.play(music.tonePlayable(262, music.beat(BeatFraction.Whole)), music.PlaybackMode.UntilDone)
    }
})
```

## Passo 15
Agora, abaixo do bloco ``||loops:repetir 3 vezes||``, dentro do laço ``||basic:sempre||``, adicione um bloco
``||logic:se então senão||``.  

```blocks
let angulos: number[] = []
let estado = 0
basic.forever(function () {
    angulos = []
    for (let index = 0; index < 3; index++) {
        let graus = 0
        estado = sensors.buttonValue(InputPorts.P2)
        while (sensors.buttonValue(InputPorts.P2) == estado) {
            basic.showNumber(graus)
        }
        angulos.push(graus)
        music.play(music.tonePlayable(262, music.beat(BeatFraction.Whole)), music.PlaybackMode.UntilDone)
    }
    if (true) {
    	
    } else {
    	
    }
})
```

## Passo 16
Retorne à aba ``||logic:Lógica||`` e adicione um operador booleano ``||logic:() ou ()||`` 
para substituir o campo **verdadeiro** do ``||logic:se então senão||``. 

```blocks
let angulos: number[] = []
let estado = 0
basic.forever(function () {
    angulos = []
    for (let index = 0; index < 3; index++) {
        let graus = 0
        estado = sensors.buttonValue(InputPorts.P2)
        while (sensors.buttonValue(InputPorts.P2) == estado) {
            basic.showNumber(graus)
        }
        angulos.push(graus)
        music.play(music.tonePlayable(262, music.beat(BeatFraction.Whole)), music.PlaybackMode.UntilDone)
    }
    if (false || false) {
    	
    } else {
    	
    }
})
```

## Passo 17
Adicione um segundo operador ``||logic:() ou ()||``, ampliando para três condições.

```blocks
let angulos: number[] = []
let estado = 0
basic.forever(function () {
    angulos = []
    for (let index = 0; index < 3; index++) {
        let graus = 0
        estado = sensors.buttonValue(InputPorts.P2)
        while (sensors.buttonValue(InputPorts.P2) == estado) {
            basic.showNumber(graus)
        }
        angulos.push(graus)
        music.play(music.tonePlayable(262, music.beat(BeatFraction.Whole)), music.PlaybackMode.UntilDone)
    }
    if (false || (false || false)) {
    	
    } else {
    	
    }
})
```

## Passo 18
Agora, dentro de cada um desses campos, insira blocos comparadores ``||logic:0 < 0||``.
Altere todos os sinais desses comparadores de **<** para **>**.

 **Dica:** verifique se seu código possui **seis** campos com o valor **0** nos comparadores.


```blocks
let angulos: number[] = []
let estado = 0
basic.forever(function () {
    angulos = []
    for (let index = 0; index < 3; index++) {
        let graus = 0
        estado = sensors.buttonValue(InputPorts.P2)
        while (sensors.buttonValue(InputPorts.P2) == estado) {
            basic.showNumber(graus)
        }
        angulos.push(graus)
        music.play(music.tonePlayable(262, music.beat(BeatFraction.Whole)), music.PlaybackMode.UntilDone)
    }
    if (0 > 0 || (0 > 0 || 0 > 0)) {
    	
    } else {
    	
    }
})
```

## Passo 19
Agora, acesse a categoria ``||arrays:Matriz||`` e insira o bloco ``||arrays:list obter valor em 0||`` 
nos primeiros campos de cada um dos três comparadores.

```blocks
let angulos: number[] = []
let estado = 0
basic.forever(function () {
    let lista: number[] = []
    angulos = []
    for (let index = 0; index < 3; index++) {
        let graus = 0
        estado = sensors.buttonValue(InputPorts.P2)
        while (sensors.buttonValue(InputPorts.P2) == estado) {
            basic.showNumber(graus)
        }
        angulos.push(graus)
        music.play(music.tonePlayable(262, music.beat(BeatFraction.Whole)), music.PlaybackMode.UntilDone)
    }
    if (lista[0] > 0 || (lista[0] > 0 || lista[0] > 0)) {
    	
    } else {
    	
    }
})
```

## Passo 20
Clique na seta desses blocos para alterar da variável ``||variables:list||``
para a variável ``||variables:angulos||``.

```blocks
let angulos: number[] = []
let estado = 0
basic.forever(function () {
    angulos = []
    for (let index = 0; index < 3; index++) {
        let graus = 0
        estado = sensors.buttonValue(InputPorts.P2)
        while (sensors.buttonValue(InputPorts.P2) == estado) {
            basic.showNumber(graus)
        }
        angulos.push(graus)
        music.play(music.tonePlayable(262, music.beat(BeatFraction.Whole)), music.PlaybackMode.UntilDone)
    }
    if (angulos[0] > 0 || (angulos[0] > 0 || angulos[0] > 0)) {
    	
    } else {
    	
    }
})
```

## Passo 21
Agora, edite o campo do valor apenas do segundo e terceiro bloco ``||arrays:angulos obter valor em 0||``
para que se tornem **1** e **2** respectivamente.

```blocks
let angulos: number[] = []
let estado = 0
basic.forever(function () {
    angulos = []
    for (let index = 0; index < 3; index++) {
        let graus = 0
        estado = sensors.buttonValue(InputPorts.P2)
        while (sensors.buttonValue(InputPorts.P2) == estado) {
            basic.showNumber(graus)
        }
        angulos.push(graus)
        music.play(music.tonePlayable(262, music.beat(BeatFraction.Whole)), music.PlaybackMode.UntilDone)
    }
    if (angulos[0] > 0 || (angulos[1] > 0 || angulos[2] > 0)) {
    	
    } else {
    	
    }
})
```

## Passo 22
Feito isso, altere os segundos valores de todos os três comparadores de **0** para **90**.

```blocks
let angulos: number[] = []
let estado = 0
basic.forever(function () {
    angulos = []
    for (let index = 0; index < 3; index++) {
        let graus = 0
        estado = sensors.buttonValue(InputPorts.P2)
        while (sensors.buttonValue(InputPorts.P2) == estado) {
            basic.showNumber(graus)
        }
        angulos.push(graus)
        music.play(music.tonePlayable(262, music.beat(BeatFraction.Whole)), music.PlaybackMode.UntilDone)
    }
    if (angulos[0] > 90 || (angulos[1] > 90 || angulos[2] > 90)) {
    	
    } else {
    	
    }
})
```

## Passo 23
Depois de definidos os testes condicionais, prossiga para o ``||logic:então||``.
Adicione um comando ``||basic:mostrar string "Hello!"||``, localizado na aba ``||basic:Básico||``.
Altere o texto a ser exibido de *"Hello!"* para *Obtusângulo*.

```blocks
let angulos: number[] = []
let estado = 0
basic.forever(function () {
    angulos = []
    for (let index = 0; index < 3; index++) {
        let graus = 0
        estado = sensors.buttonValue(InputPorts.P2)
        while (sensors.buttonValue(InputPorts.P2) == estado) {
            basic.showNumber(graus)
        }
        angulos.push(graus)
        music.play(music.tonePlayable(262, music.beat(BeatFraction.Whole)), music.PlaybackMode.UntilDone)
    }
    if (angulos[0] > 90 || (angulos[1] > 90 || angulos[2] > 90)) {
        basic.showString("Obtusângulo")
    } else {
    	
    }
})
```

## Passo 24
Agora, dentro do ``||logic:senão||``, adicione outro bloco ``||basic:mostrar string||``, porém 
com a mensagem *Acutângulo*.

```blocks
let angulos: number[] = []
let estado = 0
basic.forever(function () {
    angulos = []
    for (let index = 0; index < 3; index++) {
        let graus = 0
        estado = sensors.buttonValue(InputPorts.P2)
        while (sensors.buttonValue(InputPorts.P2) == estado) {
            basic.showNumber(graus)
        }
        angulos.push(graus)
        music.play(music.tonePlayable(262, music.beat(BeatFraction.Whole)), music.PlaybackMode.UntilDone)
    }
    if (angulos[0] > 90 || (angulos[1] > 90 || angulos[2] > 90)) {
        basic.showString("Obtusângulo")
    } else {
        basic.showString("Acutângulo")
    }
})
```

## Passo 25
Agora, retorne à aba ``||basic:Básico||`` e adicione um segundo laço
``||basic:sempre||`` ao seu código.

```blocks
let angulos: number[] = []
let estado = 0
basic.forever(function () {
    angulos = []
    for (let index = 0; index < 3; index++) {
        let graus = 0
        estado = sensors.buttonValue(InputPorts.P2)
        while (sensors.buttonValue(InputPorts.P2) == estado) {
            basic.showNumber(graus)
        }
        angulos.push(graus)
        music.play(music.tonePlayable(262, music.beat(BeatFraction.Whole)), music.PlaybackMode.UntilDone)
    }
    if (angulos[0] > 90 || (angulos[1] > 90 || angulos[2] > 90)) {
        basic.showString("Obtusângulo")
    } else {
        basic.showString("Acutângulo")
    }
})
basic.forever(function () {
	
})
```

## Passo 26
Acesse o menu de ``||actuators:Atuadores||`` e insira o bloco ``||actuators:Servo, definir posição 0 porta P8 modo Knob||``
dentro do novo laço ``||basic:sempre||``. Altere a porta de **P8** para **P16**.

```blocks
let angulos: number[] = []
let estado = 0
basic.forever(function () {
    angulos = []
    for (let index = 0; index < 3; index++) {
        let graus = 0
        estado = sensors.buttonValue(InputPorts.P2)
        while (sensors.buttonValue(InputPorts.P2) == estado) {
            basic.showNumber(graus)
        }
        angulos.push(graus)
        music.play(music.tonePlayable(262, music.beat(BeatFraction.Whole)), music.PlaybackMode.UntilDone)
    }
    if (angulos[0] > 90 || (angulos[1] > 90 || angulos[2] > 90)) {
        basic.showString("Obtusângulo")
    } else {
        basic.showString("Acutângulo")
    }
})
basic.forever(function () {
    actuators.SetAngleServoKnob(0, OutputPorts.P16)
})
```

## Passo 27
Acesse o menu ``||sensors:Sensores||`` e use o bloco ``||sensors:Valor do potenciômetro na porta P2||``
dentro do campo de posição do Servo. Modifique a porta desse bloco de **P2** para **P1**.

```blocks
let angulos: number[] = []
let estado = 0
basic.forever(function () {
    angulos = []
    for (let index = 0; index < 3; index++) {
        let graus = 0
        estado = sensors.buttonValue(InputPorts.P2)
        while (sensors.buttonValue(InputPorts.P2) == estado) {
            basic.showNumber(graus)
        }
        angulos.push(graus)
        music.play(music.tonePlayable(262, music.beat(BeatFraction.Whole)), music.PlaybackMode.UntilDone)
    }
    if (angulos[0] > 90 || (angulos[1] > 90 || angulos[2] > 90)) {
        basic.showString("Obtusângulo")
    } else {
        basic.showString("Acutângulo")
    }
})
basic.forever(function () {
    actuators.SetAngleServoKnob(sensors.dimmerValue(InputPorts.P1), OutputPorts.P16)
})
```

## Passo 28
Acesse a aba ``||variables:Variáveis||`` e adicione um bloco ``||variables:definir graus para 0||``
dentro do ``||basic:sempre||``. 

```blocks
let angulos: number[] = []
let estado = 0
let graus = 0
basic.forever(function () {
    angulos = []
    for (let index = 0; index < 3; index++) {
        estado = sensors.buttonValue(InputPorts.P2)
        while (sensors.buttonValue(InputPorts.P2) == estado) {
            basic.showNumber(graus)
        }
        angulos.push(graus)
        music.play(music.tonePlayable(262, music.beat(BeatFraction.Whole)), music.PlaybackMode.UntilDone)
    }
    if (angulos[0] > 90 || (angulos[1] > 90 || angulos[2] > 90)) {
        basic.showString("Obtusângulo")
    } else {
        basic.showString("Acutângulo")
    }
})
basic.forever(function () {
    actuators.SetAngleServoKnob(sensors.dimmerValue(InputPorts.P1), OutputPorts.P16)
    graus = 0
})
```

## Passo 29
Acesse a categoria ``||math:Matemática||`` e adicione o bloco ``||math:arredonda||`` dentro do 
valor de definição da variável, substituindo o **0**.

```blocks
let angulos: number[] = []
let estado = 0
let graus = 0
basic.forever(function () {
    angulos = []
    for (let index = 0; index < 3; index++) {
        estado = sensors.buttonValue(InputPorts.P2)
        while (sensors.buttonValue(InputPorts.P2) == estado) {
            basic.showNumber(graus)
        }
        angulos.push(graus)
        music.play(music.tonePlayable(262, music.beat(BeatFraction.Whole)), music.PlaybackMode.UntilDone)
    }
    if (angulos[0] > 90 || (angulos[1] > 90 || angulos[2] > 90)) {
        basic.showString("Obtusângulo")
    } else {
        basic.showString("Acutângulo")
    }
})
basic.forever(function () {
    actuators.SetAngleServoKnob(sensors.dimmerValue(InputPorts.P1), OutputPorts.P16)
    graus = Math.round(1)
})
```

## Passo 30
Retorne à ``||math:Matemática||`` e adicione o bloco de divisão ``||math:0 / 0||`` dentro do bloco 
``||math:arredonda||``. Modifique o segundo campo dessa divisão de **0** para o valor **780**.

```blocks
let angulos: number[] = []
let estado = 0
let graus = 0
basic.forever(function () {
    angulos = []
    for (let index = 0; index < 3; index++) {
        estado = sensors.buttonValue(InputPorts.P2)
        while (sensors.buttonValue(InputPorts.P2) == estado) {
            basic.showNumber(graus)
        }
        angulos.push(graus)
        music.play(music.tonePlayable(262, music.beat(BeatFraction.Whole)), music.PlaybackMode.UntilDone)
    }
    if (angulos[0] > 90 || (angulos[1] > 90 || angulos[2] > 90)) {
        basic.showString("Obtusângulo")
    } else {
        basic.showString("Acutângulo")
    }
})
basic.forever(function () {
    actuators.SetAngleServoKnob(sensors.dimmerValue(InputPorts.P1), OutputPorts.P16)
    graus = Math.round(0 / 780)
})
```

## Passo 31
Em seguida, adicione um bloco de multiplicação ``||math:0 x 0||`` dentro do primeiro campo da divisão.
Altere o primeiro campo dessa multiplicação de **0** para **180**.

```blocks
let angulos: number[] = []
let estado = 0
let graus = 0
basic.forever(function () {
    angulos = []
    for (let index = 0; index < 3; index++) {
        estado = sensors.buttonValue(InputPorts.P2)
        while (sensors.buttonValue(InputPorts.P2) == estado) {
            basic.showNumber(graus)
        }
        angulos.push(graus)
        music.play(music.tonePlayable(262, music.beat(BeatFraction.Whole)), music.PlaybackMode.UntilDone)
    }
    if (angulos[0] > 90 || (angulos[1] > 90 || angulos[2] > 90)) {
        basic.showString("Obtusângulo")
    } else {
        basic.showString("Acutângulo")
    }
})
basic.forever(function () {
    actuators.SetAngleServoKnob(sensors.dimmerValue(InputPorts.P1), OutputPorts.P16)
    graus = Math.round(180 * 1 / 780)
})
```

## Passo 32
Por fim, altere o segundo campo da multiplicação para o ``||sensors:Valor do potenciômetro na porta P1||``,
que pode ser encontrado na aba ``||sensors:Sensores||``, mas deve ter a porta modificada de **P2** para **P1**.

```blocks
let angulos: number[] = []
let estado = 0
let graus = 0
basic.forever(function () {
    angulos = []
    for (let index = 0; index < 3; index++) {
        estado = sensors.buttonValue(InputPorts.P2)
        while (sensors.buttonValue(InputPorts.P2) == estado) {
            basic.showNumber(graus)
        }
        angulos.push(graus)
        music.play(music.tonePlayable(262, music.beat(BeatFraction.Whole)), music.PlaybackMode.UntilDone)
    }
    if (angulos[0] > 90 || (angulos[1] > 90 || angulos[2] > 90)) {
        basic.showString("Obtusângulo")
    } else {
        basic.showString("Acutângulo")
    }
})
basic.forever(function () {
    actuators.SetAngleServoKnob(sensors.dimmerValue(InputPorts.P1), OutputPorts.P16)
    graus = Math.round(180 * sensors.dimmerValue(InputPorts.P1) / 780)
})
```

## Passo 33

Agora seu código está pronto! Baixe-o para o micro:bit e teste-o. 
Utilize o potenciômetro para ajustrar o ângulo e pressione o botão para salvar o valor.
Repita o procedimento para os três ângulos do triângulo. Ao finalizar o terceiro, o micro:bit
irá exibir a classificação do triângulo medido.

```blocks
```

## Passo 34
Se necessário, confira o seu código clicando na lâmpada de dica.

```blocks
let angulos: number[] = []
let estado = 0
let graus = 0
basic.forever(function () {
    angulos = []
    for (let index = 0; index < 3; index++) {
        estado = sensors.buttonValue(InputPorts.P2)
        while (sensors.buttonValue(InputPorts.P2) == estado) {
            basic.showNumber(graus)
        }
        angulos.push(graus)
        music.play(music.tonePlayable(262, music.beat(BeatFraction.Whole)), music.PlaybackMode.UntilDone)
    }
    if (angulos[0] > 90 || (angulos[1] > 90 || angulos[2] > 90)) {
        basic.showString("Obtusângulo")
    } else {
        basic.showString("Acutângulo")
    }
})
basic.forever(function () {
    actuators.SetAngleServoKnob(sensors.dimmerValue(InputPorts.P1), OutputPorts.P16)
    graus = Math.round(180 * sensors.dimmerValue(InputPorts.P1) / 780)
})
```

```package
fuzzyBot=github:FuzzyMakers/pxt-fuzzyMakers
```
