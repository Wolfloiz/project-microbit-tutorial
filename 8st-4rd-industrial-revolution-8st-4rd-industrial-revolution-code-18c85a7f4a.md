### @diffs true
# Quarta Revolução Industrial - Internet das Coisas

## Passo 1
Nesta atividade, vamos continuar a evolução do sistema da esteira transportadora, adicionando:

✅ Um mecanismo de descarte com servo motor para peças fora do padrão.

✅ Uma função de erro capaz de detectar vibrações na esteira.

✅ O registro de variáveis em uma tabela, permitindo armazenar os dados de contagem de peças e descartes.

Certifique-se de utilizar o código construído na atividade anterior para começarmos.

```template
function Erro () {
    actuators.StopMotor(OutputPorts.P16)
    basic.showIcon(IconNames.No)
    while (!(input.buttonIsPressed(Button.A))) {
        music.play(music.tonePlayable(988, music.beat(BeatFraction.Whole)), music.PlaybackMode.UntilDone)
    }
    basic.clearScreen()
}
input.onLogoEvent(TouchButtonEvent.Pressed, function () {
    basic.showNumber(Bits)
    basic.showNumber(Descarte)
    basic.clearScreen()
})
input.onButtonPressed(Button.A, function () {
    Ligado = !(Ligado)
    if (Ligado) {
        actuators.SetSpeedMotor(450, OutputPorts.P16)
    } else {
        actuators.StopMotor(OutputPorts.P16)
    }
})
function Teste () {
    if (Tempo < 250 || Tempo > 750) {
        Descarte += 1
        Erro()
    } else {
        Bits += 1
    }
}
let Saída = 0
let Entrada = 0
let Tempo = 0
let Descarte = 0
let Bits = 0
let Ligado = false
basic.showIcon(IconNames.Heart)
basic.pause(1000)
basic.clearScreen()
Ligado = false
basic.forever(function () {
    if (sensors.infraredValue(InputPorts.P1) >= 120) {
        Entrada = input.runningTime()
        while (sensors.infraredValue(InputPorts.P1) >= 120) {
            music.play(music.tonePlayable(262, music.beat(BeatFraction.Whole)), music.PlaybackMode.UntilDone)
        }
        Saída = input.runningTime()
        Tempo = Saída - Entrada
        Teste()
    }
})
```

## Passo 2

Como de costume, verifique se a biblioteca da Fuzzy Makers já está importada em seu MakeCode.
Se não estiver, clique na aba **+ Extensões**, copie o endereço "https://github.com/FuzzyMakers/pxt-fuzzyMakers",
cole-o no campo de pesquisa da janela que se abriu e selecione a biblioteca.

## Passo 3:

Primeiramente, vamos adicionar alguns blocos no laço ``||Basic:no iniciar|``.
Precisamos estabelecer a posição inicial do servo motor e inicializar a tabela de registros de dados.
Então, acesse o menu ``||Actuators:Atuadores||`` e adicione o bloco ``||Actuators:Servo, definir posição 0 porta P8 modo Knob||`` dentro do laço ``||Basic:no iniciar|``.
Modifique a posição de ``||Actuators:0||`` para ``||Actuators:125||``.

```blocks
actuators.SetAngleServoKnob(125, OutputPorts.P8)
basic.showIcon(IconNames.Heart)
basic.pause(1000)
basic.clearScreen()
```

## Passo 4
Em seguida, acesse o menu ``||Table:Registro de dados||`` e insira o bloco ``||Table:Adicionar colunas ao registro de dados||`` no laço ``||Basic:no iniciar|``.
Nomeie a primeira coluna como "Bits", depois clique no sinal de **+** para adicionar uma segunda coluna denominada "Descarte".

```blocks
actuators.SetAngleServoKnob(125, OutputPorts.P8)
table.setColumnTitles(
"Bits",
"Descarte"
)
basic.showIcon(IconNames.Heart)
basic.pause(1000)
basic.clearScreen()
```

## Passo 5

Agora, vamos modificar a função ``||Functions:Teste||`` para que, quando identificar um Bit fora do padrão,
toque um ``||music:som||`` de erro e acione o ``||Actuators:servo motor||`` que fará o descarte da peça,
além de atualizar a ``||Table:tabela de registro||`` dos ``||variables:Bits||`` conformes e ``||variables:descartados||``.
No próximo passo começaremos a editar a função ``||Functions:Teste||`` herdada da atividade anterior.

```blocks
function Teste () {
    if (Tempo < 250 || Tempo > 750) {
        Descarte += 1
        Erro()
    } else {
        Bits += 1
    }
}
function Erro () {
    actuators.StopMotor(OutputPorts.P16)
    basic.showIcon(IconNames.No)
    while (!(input.buttonIsPressed(Button.A))) {
        music.play(music.tonePlayable(988, music.beat(BeatFraction.Whole)), music.PlaybackMode.UntilDone)
    }
    basic.clearScreen()
}
```

## Passo 6
Comece acessando a aba ``||music:Música||`` e adicionando o comando ``||Music:play tone C Médio for 1 batida until done||`` 
dentro do  ``||Logic:então||``. Altere o tom desse bloco de ``||Music:C Médio||`` para ``||Music:B agudo||`` para diferenciarmos o som de descarte. 
Essa nota é a última tecla à direita do teclado. 

```blocks
function Teste () {
    if (Tempo < 250 || Tempo > 750) {
        music.play(music.tonePlayable(988, music.beat(BeatFraction.Whole)), music.PlaybackMode.UntilDone)
        Descarte += 1
        Erro()
    } else {
        Bits += 1
    }
}
function Erro () {
    actuators.StopMotor(OutputPorts.P16)
    basic.showIcon(IconNames.No)
    while (!(input.buttonIsPressed(Button.A))) {
        music.play(music.tonePlayable(988, music.beat(BeatFraction.Whole)), music.PlaybackMode.UntilDone)
    }
    basic.clearScreen()
}
```

## Passo 7
Agora, vamos definir o movimento do servo. Para isso, vá até ``||Actuators:Atuadores||`` e adicione o bloco ``||Actuators:Servo, definir posição 0 porta P8 modo Knob||`` 
abaixo do bloco de ``||music:Música||`` do passo anterior. Ajuste a posição de ``||Actuators:0||`` para ``||Actuators:1023||``.

```blocks
function Teste () {
    if (Tempo < 250 || Tempo > 750) {
        music.play(music.tonePlayable(988, music.beat(BeatFraction.Whole)), music.PlaybackMode.UntilDone)
        actuators.SetAngleServoKnob(1023, OutputPorts.P8)
        Descarte += 1
        Erro()
    } else {
        Bits += 1
    }
}
function Erro () {
    actuators.StopMotor(OutputPorts.P16)
    basic.showIcon(IconNames.No)
    while (!(input.buttonIsPressed(Button.A))) {
        music.play(music.tonePlayable(988, music.beat(BeatFraction.Whole)), music.PlaybackMode.UntilDone)
    }
    basic.clearScreen()
}
```

## Passo 8
Agora, acesse a aba ``||basic:Básico||`` e adicione uma ``||basic:pausa (ms)||`` alterando a duração para **500ms** após o bloco do servo.
Em seguida, duplique o bloco ``||Actuators:Servo, definir posição 0 porta P8 modo Knob||`` 
modificando a posição de ``||Actuators:1023||`` para ``||Actuators:125||``.

```blocks
function Teste () {
    if (Tempo < 250 || Tempo > 750) {
        music.play(music.tonePlayable(988, music.beat(BeatFraction.Whole)), music.PlaybackMode.UntilDone)
        actuators.SetAngleServoKnob(1023, OutputPorts.P8)
        basic.pause(500)
        actuators.SetAngleServoKnob(125, OutputPorts.P8)
        Descarte += 1
        Erro()
    } else {
        Bits += 1
    }
}
function Erro () {
    actuators.StopMotor(OutputPorts.P16)
    basic.showIcon(IconNames.No)
    while (!(input.buttonIsPressed(Button.A))) {
        music.play(music.tonePlayable(988, music.beat(BeatFraction.Whole)), music.PlaybackMode.UntilDone)
    }
    basic.clearScreen()
}
```

## Passo 9
Feito isso, exclua o bloco ``||Functions:ligar Erro||`` dentro deste laço, pois ele não será mais necessário nessa situação.

```blocks
function Teste () {
    if (Tempo < 250 || Tempo > 750) {
        music.play(music.tonePlayable(988, music.beat(BeatFraction.Whole)), music.PlaybackMode.UntilDone)
        actuators.SetAngleServoKnob(1023, OutputPorts.P8)
        basic.pause(500)
        actuators.SetAngleServoKnob(125, OutputPorts.P8)
        Descarte += 1
    } else {
        Bits += 1
    }
}
```

## Passo 10
Agora, ainda dentro do laço da função ``||Functions:Teste||``, mas fora do teste condicional ``||Logic:Se então||``,
adicione o bloco ``||Table:Registrar dados coluna " " valor 0||``. Clique no sinal de **+** para abrir outro registro.

```blocks
function Teste () {
    if (Tempo < 250 || Tempo > 750) {
        music.play(music.tonePlayable(988, music.beat(BeatFraction.Whole)), music.PlaybackMode.UntilDone)
        actuators.SetAngleServoKnob(1023, OutputPorts.P8)
        basic.pause(500)
        actuators.SetAngleServoKnob(125, OutputPorts.P8)
        Descarte += 1
    } else {
        Bits += 1
    }
    table.log(
    table.createCell("", 0),
    table.createCell("", 0)
    )
}
```

## Passo 11
Entre o primeiro par de aspas duplas, escolha "Bits" e, no segundo, digite "Descarte".
Dentro dos respectivos valores, inclua as variáveis ``||variables:Bits||`` e ``||variables:Descarte||`` relacionadas.

```blocks
function Teste () {
    if (Tempo < 250 || Tempo > 750) {
        music.play(music.tonePlayable(988, music.beat(BeatFraction.Whole)), music.PlaybackMode.UntilDone)
        actuators.SetAngleServoKnob(1023, OutputPorts.P8)
        basic.pause(500)
        actuators.SetAngleServoKnob(125, OutputPorts.P8)
        Descarte += 1
    } else {
        Bits += 1
    }
    table.log(
    table.createCell("Bits", Bits),
    table.createCell("Descarte", Descarte)
    )
}
```

## Passo 12
Nessa nova etapa, vamos reutilizar a função ``||Functions:Erro||`` da atividade anterior para ser acionada quando 
forem identificadas vibrações na esteira pelo sensor de movimento do Micro:bit.
Para isso, vá até ``||Input:Entrada||`` e adicione o laço ``||Input:em agitar||`` ao código.

```blocks
input.onGesture(Gesture.Shake, function () {
	
})
function Erro () {
    actuators.StopMotor(OutputPorts.P16)
    basic.showIcon(IconNames.No)
    while (!(input.buttonIsPressed(Button.A))) {
        music.play(music.tonePlayable(988, music.beat(BeatFraction.Whole)), music.PlaybackMode.UntilDone)
    }
    basic.clearScreen()
}
```

## Passo 13
Clique no menu ``||Advanced:Avançado||``, acesse ``||Functions:Funções||`` e adicione o comando ``||Functions:ligar Erro||``
dentro do laço ``||Input:em agitar||``.

```blocks
input.onGesture(Gesture.Shake, function () {
	Erro()
})
function Erro () {
    actuators.StopMotor(OutputPorts.P16)
    basic.showIcon(IconNames.No)
    while (!(input.buttonIsPressed(Button.A))) {
        music.play(music.tonePlayable(988, music.beat(BeatFraction.Whole)), music.PlaybackMode.UntilDone)
    }
    basic.clearScreen()
}
```

## Passo 14
Feito isso, vamos criar um processo que permita limpar os registros de contagem da tabela de dados. Esse processo será responsável por:

✔️ Apagar todos os registros da tabela, removendo os valores de Bits e Descarte.

✔️ Zerar as variáveis de contagem, reiniciando o contador de peças processadas.

✔️ Exibir um ícone de "casa" na matriz de LEDs para indicar que o sistema foi reiniciado.

✔️ Após 1 segundo, limpa a tela e o sistema volta ao funcionamento normal.

## Passo 15

Primeiramente, vá até ``||Input:Entrada||`` e adicione o bloco ``||Input:no botão A pressionado||``. Altere de 
``||Input:Botão A||`` para ``||Input:Botão B||``.
Em seguida, acesse o menu ``||Basic:Básico||`` e adicione o bloco ``||Basic:mostrar ícone||`` dentro desse laço.
Escolha o ícone de casa 🏠.

```blocks
input.onButtonPressed(Button.B, function () {
    basic.showIcon(IconNames.House)
})
```

## Passo 16

Vá até ``||Table:Registro de dados||`` e adicione o bloco ``||Table:Deletar registros||``. Clique no símbolo **"+"** e selecione a opção **"completo"**.

```blocks
input.onButtonPressed(Button.B, function () {
    basic.showIcon(IconNames.House)
    table.deleteLog(table.DeleteType.Full)
})
```

## Passo 17

Acesse o menu ``||Variables:Variáveis||`` e adicione ``||Variables:definir Bits para 0||`` e ``||Variables:definir Descarte para 0||``.
Certifique-se de que esteja zerando as variáveis corretas.

```blocks
input.onButtonPressed(Button.B, function () {
    basic.showIcon(IconNames.House)
    table.deleteLog(table.DeleteType.Full)
    Bits = 0
    Descarte = 0
})
```

## Passo 18
Em seguida, retorne à aba  ``||Basic:Básico||`` e adicione o bloco ``||Basic:pausa (ms)||`` com o valor **1000ms** (1 segundo).

```blocks
input.onButtonPressed(Button.B, function () {
    basic.showIcon(IconNames.House)
    table.deleteLog(table.DeleteType.Full)
    Bits = 0
    Descarte = 0
    basic.pause(1000)
})
```

## Passo 19
Por fim, ainda no menu ``||Basic:Básico||`` e adicione o bloco ``||Basic:limpar tela||``.

```blocks
input.onButtonPressed(Button.B, function () {
    basic.showIcon(IconNames.House)
    table.deleteLog(table.DeleteType.Full)
    Bits = 0
    Descarte = 0
    basic.pause(1000)
    basic.clearScreen()
})
```

## Passo 20
Agora que todas as funcionalidades foram implementadas, é hora de testar o código completo e garantir que tudo funcione corretamente.

📌 **O que devemos testar?**

✅ Ligar e desligar a esteira pressionando o botão A.

✅ Registrar a passagem das peças pelo sensor infravermelho.

✅ Desviar peças fora do padrão com o servo motor.

✅ Registrar os dados na tabela (número de peças aceitas e descartadas).

✅ Detectar vibrações na esteira e exibir o alerta de erro ao agitar o Micro:bit.

✅ Limpar os registros de dados pressionando o botão B.

✅ Exibir os valores de Bits e Descarte tocando no logotipo do Micro:bit.

```blocks

```

## Passo 21

Para facilitar, confira todo o seu código clicando na lâmpada de dica.

```blocks
function Erro () {
    actuators.StopMotor(OutputPorts.P16)
    basic.showIcon(IconNames.No)
    while (!(input.buttonIsPressed(Button.A))) {
        music.play(music.tonePlayable(988, music.beat(BeatFraction.Whole)), music.PlaybackMode.UntilDone)
    }
    basic.clearScreen()
}
input.onLogoEvent(TouchButtonEvent.Pressed, function () {
    basic.showNumber(Bits)
    basic.showNumber(Descarte)
    basic.clearScreen()
})
input.onButtonPressed(Button.A, function () {
    Ligado = !(Ligado)
    if (Ligado) {
        actuators.SetSpeedMotor(450, OutputPorts.P16)
    } else {
        actuators.StopMotor(OutputPorts.P16)
    }
})
input.onGesture(Gesture.Shake, function () {
    Erro()
})
input.onButtonPressed(Button.B, function () {
    basic.showIcon(IconNames.House)
    table.deleteLog(table.DeleteType.Full)
    Bits = 0
    Descarte = 0
    basic.pause(1000)
    basic.clearScreen()
})
function Teste () {
    if (Tempo < 250 || Tempo > 750) {
        music.play(music.tonePlayable(988, music.beat(BeatFraction.Whole)), music.PlaybackMode.UntilDone)
        actuators.SetAngleServoKnob(1023, OutputPorts.P8)
        basic.pause(500)
        actuators.SetAngleServoKnob(125, OutputPorts.P8)
        Descarte += 1
    } else {
        Bits += 1
    }
    table.log(
    table.createCell("Bits", Bits),
    table.createCell("Descarte", Descarte)
    )
}
let Saída = 0
let Entrada = 0
let Tempo = 0
let Descarte = 0
let Bits = 0
let Ligado = false
actuators.SetAngleServoKnob(125, OutputPorts.P8)
table.setColumnTitles(
"Bits",
"Descarte"
)
basic.showIcon(IconNames.Heart)
basic.pause(1000)
basic.clearScreen()
Ligado = false
basic.forever(function () {
    if (sensors.infraredValue(InputPorts.P1) >= 120) {
        Entrada = input.runningTime()
        while (sensors.infraredValue(InputPorts.P1) >= 120) {
            music.play(music.tonePlayable(262, music.beat(BeatFraction.Whole)), music.PlaybackMode.UntilDone)
        }
        Saída = input.runningTime()
        Tempo = Saída - Entrada
        Teste()
    }
})

```

```package
fuzzyBot=github:Wolfloiz/pxt-fuzzyMakers
```