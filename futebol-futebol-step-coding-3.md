### @diffs true
# Futebol

## Passo 1
Neste tutorial, vamos programar um robô jogador de futebol. Serão criados comandos de um controle virtual 
que vai acionar o robô. A comunicação entre a interface e o micro:bit será feita via Bluetooth.

## Passo 2
Para começar, verifique se a biblioteca da Smart Makers já está importada 
em seu MakeCode. Se não estiver, clique na aba **+ Extensões**, 
copie o endereço "https://github.com/FuzzyMakers/pxt-smartMakers",
cole-o no campo de pesquisa da janela que se abriu e selecione a biblioteca.

## Passo 3
Este projeto exige que importemos outra biblioteca, portanto clique outra vez na aba **+ Extensões**.
Use a barra de pesquisa para buscar o termo **bluetooth** e selecione a biblioteca de mesmo nome.
Se a extensão Rádio estiver adicionada ao seu projeto o MakeCode exibirá uma mensagem avisando que removerá-la, apenas confimre clicando em **"Remover extensão(ões) e adicionar bluetooth"".

## Passo 4
Acesse a aba ``||bluetooth:Bluetooth||``, clique em **mais** e adicione o bloco
``||bluetooth:serviço uart bluetooth||`` dentro do bloco ``||basic:no iniciar||``.

```blocks
bluetooth.startUartService()

```

## Passo 5

Volte à categoria ``||bluetooth:Bluetooth||``, clique em **mais** e pegue o comando ``||bluetooth:definir energia de transmissão bluetooth 7||``
e insira-o abaixo do bloco anterior.

```blocks
bluetooth.startUartService()
bluetooth.setTransmitPower(7)
```
## Passo 6
Acesse o menu ``||variables:Variáveis||`` e clique em 
**"Fazer uma variável..."**. Crie uma variável chamada
``||variables:velocidade||``. Em seguida, arraste o bloco ``||variables:definir velocidade para 0||`` 
para o código e altere o valor **0** para **600**.

```blocks
bluetooth.startUartService()
bluetooth.setTransmitPower(7)
let velocidade = 600
```



## Passo 7

Na aba ``||basic:Básico||``, clique em ``||basic:mostrar ícone||``, 
altere o símbolo de um **coração** para um **quadrado**.

```blocks
bluetooth.startUartService()
bluetooth.setTransmitPower(7)
let velocidade = 600
basic.showIcon(IconNames.Square)
```


## Passo 8

Acesse o menu ``||bluetooth:Bluetooth||`` e adicione dois blocos:
``||bluetooth:ao conectar bluetooth||`` e ``||bluetooth:ao desconectar bluetooth||``.

```blocks
bluetooth.onBluetoothConnected(function () {
	
})
bluetooth.onBluetoothDisconnected(function () {
	
})
bluetooth.startUartService()
bluetooth.setTransmitPower(7)
let velocidade = 600
basic.showIcon(IconNames.Square)
```

## Passo 9

Volte à aba ``||basic:Básico||`` e adicione o bloco
``||basic:mostrar ícone||`` dentro de ``||bluetooth:ao conectar bluetooth||``.
Altere o ícone de um **coração** para uma **cara feliz**.

```blocks
bluetooth.onBluetoothConnected(function () {
    basic.showIcon(IconNames.Happy)
})
bluetooth.onBluetoothDisconnected(function () {
	
})
bluetooth.startUartService()
bluetooth.setTransmitPower(7)
let velocidade = 600
basic.showIcon(IconNames.Square)
```

## Passo 10

Volte à aba ``||basic:Básico||`` e adicione o bloco
``||basic:mostrar ícone||`` dentro de ``||bluetooth:ao desconectar bluetooth||``.
Altere o ícone de um **coração** para um **X**.

```blocks
bluetooth.onBluetoothConnected(function () {
    basic.showIcon(IconNames.Happy)
})
bluetooth.onBluetoothDisconnected(function () {
    basic.showIcon(IconNames.No)
})
bluetooth.startUartService()
bluetooth.setTransmitPower(7)
let velocidade = 600
basic.showIcon(IconNames.Square)

```

## Passo 11
No menu ``||bluetooth:Bluetooth||`` busque o bloco ``||bluetooth:bluetooth ao receber dados new line()||`` e adicione-o
à área de programação.

```blocks
bluetooth.onBluetoothConnected(function () {
    basic.showIcon(IconNames.Happy)
})
bluetooth.onBluetoothDisconnected(function () {
    basic.showIcon(IconNames.No)
})
bluetooth.onUartDataReceived(serial.delimiters(Delimiters.NewLine), function () {
	
})
bluetooth.startUartService()
bluetooth.setTransmitPower(7)
let velocidade = 600
basic.showIcon(IconNames.Square)
```

## Passo 12

Acesse o menu ``||variables:Variáveis||`` e clique em 
**"Fazer uma variável..."**. Crie uma variável chamada
``||variables:comando||``. Em seguida, arraste o bloco ``||variables:definir comando para 0||`` 
para dentro do bloco ``||bluetooth:bluetooth ao receber dados new line()||``

```blocks
bluetooth.onBluetoothConnected(function () {
    basic.showIcon(IconNames.Happy)
})
bluetooth.onBluetoothDisconnected(function () {
    basic.showIcon(IconNames.No)
})
bluetooth.onUartDataReceived(serial.delimiters(Delimiters.NewLine), function () {
    comando = 0
})
let comando = 0
bluetooth.startUartService()
bluetooth.setTransmitPower(7)
let velocidade = 600
basic.showIcon(IconNames.Square)
```

## Passo 13

Volte ao menu ``||bluetooth:Bluetooth||``, clique em 
**mais...** e pegue o bloco ``||bluetooth:uart bluetooth ler até new line()||`` para substituir
o valor **0** da variável ``||variables:comando||``.

```blocks
bluetooth.onBluetoothConnected(function () {
    basic.showIcon(IconNames.Happy)
})
bluetooth.onBluetoothDisconnected(function () {
    basic.showIcon(IconNames.No)
})
bluetooth.onUartDataReceived(serial.delimiters(Delimiters.NewLine), function () {
    comando = bluetooth.uartReadUntil(serial.delimiters(Delimiters.NewLine))
})
let comando = ""
bluetooth.startUartService()
bluetooth.setTransmitPower(7)
let velocidade = 600
basic.showIcon(IconNames.Square)

```

## Passo 14

Acesse a categoria ``||logic:Lógica||``, clique na condicional ``||logic:se então||``
e insira-a abaixo do bloco anterior.

```blocks
bluetooth.onBluetoothConnected(function () {
    basic.showIcon(IconNames.Happy)
})
bluetooth.onBluetoothDisconnected(function () {
    basic.showIcon(IconNames.No)
})
bluetooth.onUartDataReceived(serial.delimiters(Delimiters.NewLine), function () {
    comando = bluetooth.uartReadUntil(serial.delimiters(Delimiters.NewLine))
    if (true) {
    	
    }
})
let comando = ""
bluetooth.startUartService()
bluetooth.setTransmitPower(7)
let velocidade = 600
basic.showIcon(IconNames.Square)
```
## Passo 15
Volte ao menu ``||logic:Lógica||``, pegue o comparador ``||logic:"" = ""||``
e substitua a condição **verdadeiro** da condicional.

```blocks
bluetooth.onBluetoothConnected(function () {
    basic.showIcon(IconNames.Happy)
})
bluetooth.onBluetoothDisconnected(function () {
    basic.showIcon(IconNames.No)
})
bluetooth.onUartDataReceived(serial.delimiters(Delimiters.NewLine), function () {
    comando = bluetooth.uartReadUntil(serial.delimiters(Delimiters.NewLine))
    if ("" == "") {
    	
    }
})
let comando = ""
bluetooth.startUartService()
bluetooth.setTransmitPower(7)
let velocidade = 600
basic.showIcon(IconNames.Square)
```

## Passo 16

Agora atualize os campos do comparador. Vá até a aba ``||variables:Variáveis||``,
clique na variável ``||variables:comando||`` e troque o primeiro **" "** do comparador.
Em seguida, escreva a letra **"A"** no segundo campo. 
```blocks
bluetooth.onBluetoothConnected(function () {
    basic.showIcon(IconNames.Happy)
})
bluetooth.onBluetoothDisconnected(function () {
    basic.showIcon(IconNames.No)
})
bluetooth.onUartDataReceived(serial.delimiters(Delimiters.NewLine), function () {
    comando = bluetooth.uartReadUntil(serial.delimiters(Delimiters.NewLine))
    if (comando == "A") {
    	
    }
})
let comando = ""
bluetooth.startUartService()
bluetooth.setTransmitPower(7)
let velocidade = 600
basic.showIcon(IconNames.Square)

```
## Passo 17
Acesse a aba ``||actuators:Atuadores||`` e adicione **dois** blocos
``||actuators:Motor CC, definir direção para Sentido horário na porta P8||`` dentro da condicional 
``||logic:se comando ="A" então||``.


```blocks
bluetooth.onBluetoothConnected(function () {
    basic.showIcon(IconNames.Happy)
})
bluetooth.onBluetoothDisconnected(function () {
    basic.showIcon(IconNames.No)
})
bluetooth.onUartDataReceived(serial.delimiters(Delimiters.NewLine), function () {
    comando = bluetooth.uartReadUntil(serial.delimiters(Delimiters.NewLine))
    if (comando == "A") {
        actuators.SetDirectionMotor(MotorDirection.clockwise, OutputPorts.P8)
        actuators.SetDirectionMotor(MotorDirection.clockwise, OutputPorts.P8)
    }
})
let comando = ""
bluetooth.startUartService()
bluetooth.setTransmitPower(7)
let velocidade = 600
basic.showIcon(IconNames.Square)
```

## Passo 18

Em seguida, modifique a direção do primeiro bloco para **anti-horário**
e a porta do segundo de **P8** para **P16**.

```blocks
bluetooth.onBluetoothConnected(function () {
    basic.showIcon(IconNames.Happy)
})
bluetooth.onBluetoothDisconnected(function () {
    basic.showIcon(IconNames.No)
})
bluetooth.onUartDataReceived(serial.delimiters(Delimiters.NewLine), function () {
    comando = bluetooth.uartReadUntil(serial.delimiters(Delimiters.NewLine))
    if (comando == "A") {
        actuators.SetDirectionMotor(MotorDirection.antiClockwise, OutputPorts.P8)
        actuators.SetDirectionMotor(MotorDirection.clockwise, OutputPorts.P16)
    }
})
let comando = ""
bluetooth.startUartService()
bluetooth.setTransmitPower(7)
let velocidade = 600
basic.showIcon(IconNames.Square)
```
## Passo 19
Volte à aba ``||actuators:Atuadores||`` e adicione um bloco
``||actuators:Motor CC, definir velocidade 0 na porta P8||`` também dentro da condicional.

```blocks
bluetooth.onBluetoothConnected(function () {
    basic.showIcon(IconNames.Happy)
})
bluetooth.onBluetoothDisconnected(function () {
    basic.showIcon(IconNames.No)
})
bluetooth.onUartDataReceived(serial.delimiters(Delimiters.NewLine), function () {
    comando = bluetooth.uartReadUntil(serial.delimiters(Delimiters.NewLine))
    if (comando == "A") {
        actuators.SetDirectionMotor(MotorDirection.antiClockwise, OutputPorts.P8)
        actuators.SetDirectionMotor(MotorDirection.clockwise, OutputPorts.P16)
        actuators.SetSpeedMotor(0, OutputPorts.P8)
    }
})
let comando = ""
bluetooth.startUartService()
bluetooth.setTransmitPower(7)
let velocidade = 600
basic.showIcon(IconNames.Square)

```
## Passo 20

Mude o valor da velocidade de **0** para a variável ``||variables:velocidade||``
e a porta de **P8** para **P12**.

```blocks
bluetooth.onBluetoothConnected(function () {
    basic.showIcon(IconNames.Happy)
})
bluetooth.onBluetoothDisconnected(function () {
    basic.showIcon(IconNames.No)
})
bluetooth.onUartDataReceived(serial.delimiters(Delimiters.NewLine), function () {
    comando = bluetooth.uartReadUntil(serial.delimiters(Delimiters.NewLine))
    if (comando == "A") {
        actuators.SetDirectionMotor(MotorDirection.antiClockwise, OutputPorts.P8)
        actuators.SetDirectionMotor(MotorDirection.clockwise, OutputPorts.P16)
        actuators.SetSpeedMotor(velocidade, OutputPorts.P12)
    }
})
let comando = ""
let velocidade = 0
bluetooth.startUartService()
bluetooth.setTransmitPower(7)
velocidade = 600
basic.showIcon(IconNames.Square)
```

## Passo 21

Selecione o bloco ``||logic:se comando ="A" então||`` e copie-o. Cole 3 cópias do bloco
abaixo dele.

```blocks
bluetooth.onBluetoothConnected(function () {
    basic.showIcon(IconNames.Happy)
})
bluetooth.onBluetoothDisconnected(function () {
    basic.showIcon(IconNames.No)
})
bluetooth.onUartDataReceived(serial.delimiters(Delimiters.NewLine), function () {
    comando = bluetooth.uartReadUntil(serial.delimiters(Delimiters.NewLine))
    if (comando == "A") {
        actuators.SetDirectionMotor(MotorDirection.antiClockwise, OutputPorts.P8)
        actuators.SetDirectionMotor(MotorDirection.clockwise, OutputPorts.P16)
        actuators.SetSpeedMotor(velocidade, OutputPorts.P12)
    }
    if (comando == "A") {
        actuators.SetDirectionMotor(MotorDirection.antiClockwise, OutputPorts.P8)
        actuators.SetDirectionMotor(MotorDirection.clockwise, OutputPorts.P16)
        actuators.SetSpeedMotor(velocidade, OutputPorts.P12)
    }
    if (comando == "A") {
        actuators.SetDirectionMotor(MotorDirection.antiClockwise, OutputPorts.P8)
        actuators.SetDirectionMotor(MotorDirection.clockwise, OutputPorts.P16)
        actuators.SetSpeedMotor(velocidade, OutputPorts.P12)
    }
    if (comando == "A") {
        actuators.SetDirectionMotor(MotorDirection.antiClockwise, OutputPorts.P8)
        actuators.SetDirectionMotor(MotorDirection.clockwise, OutputPorts.P16)
        actuators.SetSpeedMotor(velocidade, OutputPorts.P12)
    }
})
let comando = ""
let velocidade = 0
bluetooth.startUartService()
bluetooth.setTransmitPower(7)
velocidade = 600
basic.showIcon(IconNames.Square)

```
## Passo 22
Modifique os parâmetros do **segundo** bloco condicional: O comparador será alterado
para ``||logic:comando ="B"||`` e o sentido do **primeiro** bloco passará a ser **horário**.
```blocks
bluetooth.onBluetoothConnected(function () {
    basic.showIcon(IconNames.Happy)
})
bluetooth.onBluetoothDisconnected(function () {
    basic.showIcon(IconNames.No)
})
bluetooth.onUartDataReceived(serial.delimiters(Delimiters.NewLine), function () {
    comando = bluetooth.uartReadUntil(serial.delimiters(Delimiters.NewLine))
    if (comando == "A") {
        actuators.SetDirectionMotor(MotorDirection.antiClockwise, OutputPorts.P8)
        actuators.SetDirectionMotor(MotorDirection.clockwise, OutputPorts.P16)
        actuators.SetSpeedMotor(velocidade, OutputPorts.P12)
    }
    if (comando == "B") {
        actuators.SetDirectionMotor(MotorDirection.clockwise, OutputPorts.P8)
        actuators.SetDirectionMotor(MotorDirection.clockwise, OutputPorts.P16)
        actuators.SetSpeedMotor(velocidade, OutputPorts.P12)
    }
    if (comando == "A") {
        actuators.SetDirectionMotor(MotorDirection.antiClockwise, OutputPorts.P8)
        actuators.SetDirectionMotor(MotorDirection.clockwise, OutputPorts.P16)
        actuators.SetSpeedMotor(velocidade, OutputPorts.P12)
    }
    if (comando == "A") {
        actuators.SetDirectionMotor(MotorDirection.antiClockwise, OutputPorts.P8)
        actuators.SetDirectionMotor(MotorDirection.clockwise, OutputPorts.P16)
        actuators.SetSpeedMotor(velocidade, OutputPorts.P12)
    }
})
let comando = ""
let velocidade = 0
bluetooth.startUartService()
bluetooth.setTransmitPower(7)
velocidade = 600
basic.showIcon(IconNames.Square)


```
## Passo 23
Modifique os parâmetros do **terceiro** bloco condicional: O comparador será alterado
para ``||logic:comando ="C"||`` e o sentido do **segundo** bloco passará a ser **anti-horário**.
```blocks
bluetooth.onBluetoothConnected(function () {
    basic.showIcon(IconNames.Happy)
})
bluetooth.onBluetoothDisconnected(function () {
    basic.showIcon(IconNames.No)
})
bluetooth.onUartDataReceived(serial.delimiters(Delimiters.NewLine), function () {
    comando = bluetooth.uartReadUntil(serial.delimiters(Delimiters.NewLine))
    if (comando == "A") {
        actuators.SetDirectionMotor(MotorDirection.antiClockwise, OutputPorts.P8)
        actuators.SetDirectionMotor(MotorDirection.clockwise, OutputPorts.P16)
        actuators.SetSpeedMotor(velocidade, OutputPorts.P12)
    }
    if (comando == "B") {
        actuators.SetDirectionMotor(MotorDirection.clockwise, OutputPorts.P8)
        actuators.SetDirectionMotor(MotorDirection.clockwise, OutputPorts.P16)
        actuators.SetSpeedMotor(velocidade, OutputPorts.P12)
    }
    if (comando == "C") {
        actuators.SetDirectionMotor(MotorDirection.antiClockwise, OutputPorts.P8)
        actuators.SetDirectionMotor(MotorDirection.antiClockwise, OutputPorts.P16)
        actuators.SetSpeedMotor(velocidade, OutputPorts.P12)
    }
    if (comando == "A") {
        actuators.SetDirectionMotor(MotorDirection.antiClockwise, OutputPorts.P8)
        actuators.SetDirectionMotor(MotorDirection.clockwise, OutputPorts.P16)
        actuators.SetSpeedMotor(velocidade, OutputPorts.P12)
    }
})
let comando = ""
let velocidade = 0
bluetooth.startUartService()
bluetooth.setTransmitPower(7)
velocidade = 600
basic.showIcon(IconNames.Square)
```
## Passo 24
Modifique os parâmetros do **quarto** bloco condicional: O comparador será alterado
para ``||logic:comando ="D"||``, o sentido do **primeiro** bloco passará a ser **horário** e
o sentido do **segundo** bloco passará a ser **anti-horário**.
```blocks
bluetooth.onBluetoothConnected(function () {
    basic.showIcon(IconNames.Happy)
})
bluetooth.onBluetoothDisconnected(function () {
    basic.showIcon(IconNames.No)
})
bluetooth.onUartDataReceived(serial.delimiters(Delimiters.NewLine), function () {
    comando = bluetooth.uartReadUntil(serial.delimiters(Delimiters.NewLine))
    if (comando == "A") {
        actuators.SetDirectionMotor(MotorDirection.antiClockwise, OutputPorts.P8)
        actuators.SetDirectionMotor(MotorDirection.clockwise, OutputPorts.P16)
        actuators.SetSpeedMotor(velocidade, OutputPorts.P12)
    }
    if (comando == "B") {
        actuators.SetDirectionMotor(MotorDirection.clockwise, OutputPorts.P8)
        actuators.SetDirectionMotor(MotorDirection.clockwise, OutputPorts.P16)
        actuators.SetSpeedMotor(velocidade, OutputPorts.P12)
    }
    if (comando == "C") {
        actuators.SetDirectionMotor(MotorDirection.antiClockwise, OutputPorts.P8)
        actuators.SetDirectionMotor(MotorDirection.antiClockwise, OutputPorts.P16)
        actuators.SetSpeedMotor(velocidade, OutputPorts.P12)
    }
    if (comando == "D") {
        actuators.SetDirectionMotor(MotorDirection.clockwise, OutputPorts.P8)
        actuators.SetDirectionMotor(MotorDirection.antiClockwise, OutputPorts.P16)
        actuators.SetSpeedMotor(velocidade, OutputPorts.P12)
    }
})
let comando = ""
let velocidade = 0
bluetooth.startUartService()
bluetooth.setTransmitPower(7)
velocidade = 600
basic.showIcon(IconNames.Square)
```

## Passo 25

Acesse a categoria ``||logic:Lógica||``, clique na condicional ``||logic:se então||``
e insira-a abaixo dos blocos condicionais já editados.

```blocks
bluetooth.onBluetoothConnected(function () {
    basic.showIcon(IconNames.Happy)
})
bluetooth.onBluetoothDisconnected(function () {
    basic.showIcon(IconNames.No)
})
bluetooth.onUartDataReceived(serial.delimiters(Delimiters.NewLine), function () {
    comando = bluetooth.uartReadUntil(serial.delimiters(Delimiters.NewLine))
    if (comando == "A") {
        actuators.SetDirectionMotor(MotorDirection.antiClockwise, OutputPorts.P8)
        actuators.SetDirectionMotor(MotorDirection.clockwise, OutputPorts.P16)
        actuators.SetSpeedMotor(velocidade, OutputPorts.P12)
    }
    if (comando == "B") {
        actuators.SetDirectionMotor(MotorDirection.clockwise, OutputPorts.P8)
        actuators.SetDirectionMotor(MotorDirection.clockwise, OutputPorts.P16)
        actuators.SetSpeedMotor(velocidade, OutputPorts.P12)
    }
    if (comando == "C") {
        actuators.SetDirectionMotor(MotorDirection.antiClockwise, OutputPorts.P8)
        actuators.SetDirectionMotor(MotorDirection.antiClockwise, OutputPorts.P16)
        actuators.SetSpeedMotor(velocidade, OutputPorts.P12)
    }
    if (comando == "D") {
        actuators.SetDirectionMotor(MotorDirection.clockwise, OutputPorts.P8)
        actuators.SetDirectionMotor(MotorDirection.antiClockwise, OutputPorts.P16)
        actuators.SetSpeedMotor(velocidade, OutputPorts.P12)
    }
    if (true) {
    	
    }
})
let comando = ""
let velocidade = 0
bluetooth.startUartService()
bluetooth.setTransmitPower(7)
velocidade = 600
basic.showIcon(IconNames.Square)

```
## Passo 26
Duplique o comparador ``||logic:"comando" = "D"||``
e substitua a condição **verdadeiro** da condicional. 
Edite o valor do comando de **"D"** para **"parar"**.

```blocks
bluetooth.onBluetoothConnected(function () {
    basic.showIcon(IconNames.Happy)
})
bluetooth.onBluetoothDisconnected(function () {
    basic.showIcon(IconNames.No)
})
bluetooth.onUartDataReceived(serial.delimiters(Delimiters.NewLine), function () {
    comando = bluetooth.uartReadUntil(serial.delimiters(Delimiters.NewLine))
    if (comando == "A") {
        actuators.SetDirectionMotor(MotorDirection.antiClockwise, OutputPorts.P8)
        actuators.SetDirectionMotor(MotorDirection.clockwise, OutputPorts.P16)
        actuators.SetSpeedMotor(velocidade, OutputPorts.P12)
    }
    if (comando == "B") {
        actuators.SetDirectionMotor(MotorDirection.clockwise, OutputPorts.P8)
        actuators.SetDirectionMotor(MotorDirection.clockwise, OutputPorts.P16)
        actuators.SetSpeedMotor(velocidade, OutputPorts.P12)
    }
    if (comando == "C") {
        actuators.SetDirectionMotor(MotorDirection.antiClockwise, OutputPorts.P8)
        actuators.SetDirectionMotor(MotorDirection.antiClockwise, OutputPorts.P16)
        actuators.SetSpeedMotor(velocidade, OutputPorts.P12)
    }
    if (comando == "D") {
        actuators.SetDirectionMotor(MotorDirection.clockwise, OutputPorts.P8)
        actuators.SetDirectionMotor(MotorDirection.antiClockwise, OutputPorts.P16)
        actuators.SetSpeedMotor(velocidade, OutputPorts.P12)
    }
    if (comando == "parar") {
    	
    }
})
let comando = ""
let velocidade = 0
bluetooth.startUartService()
bluetooth.setTransmitPower(7)
velocidade = 600
basic.showIcon(IconNames.Square)
```


## Passo 27
Acesse a aba ``||actuators:Atuadores||`` e adicione um bloco
``||actuators:Motor CC, definir velocidade 0 na porta P8||`` dentro da condicional
``||logic:se comando =v"parar" então||``.


```blocks
bluetooth.onBluetoothConnected(function () {
    basic.showIcon(IconNames.Happy)
})
bluetooth.onBluetoothDisconnected(function () {
    basic.showIcon(IconNames.No)
})
bluetooth.onUartDataReceived(serial.delimiters(Delimiters.NewLine), function () {
    comando = bluetooth.uartReadUntil(serial.delimiters(Delimiters.NewLine))
    if (comando == "A") {
        actuators.SetDirectionMotor(MotorDirection.antiClockwise, OutputPorts.P8)
        actuators.SetDirectionMotor(MotorDirection.clockwise, OutputPorts.P16)
        actuators.SetSpeedMotor(velocidade, OutputPorts.P12)
    }
    if (comando == "B") {
        actuators.SetDirectionMotor(MotorDirection.clockwise, OutputPorts.P8)
        actuators.SetDirectionMotor(MotorDirection.clockwise, OutputPorts.P16)
        actuators.SetSpeedMotor(velocidade, OutputPorts.P12)
    }
    if (comando == "C") {
        actuators.SetDirectionMotor(MotorDirection.antiClockwise, OutputPorts.P8)
        actuators.SetDirectionMotor(MotorDirection.antiClockwise, OutputPorts.P16)
        actuators.SetSpeedMotor(velocidade, OutputPorts.P12)
    }
    if (comando == "D") {
        actuators.SetDirectionMotor(MotorDirection.clockwise, OutputPorts.P8)
        actuators.SetDirectionMotor(MotorDirection.antiClockwise, OutputPorts.P16)
        actuators.SetSpeedMotor(velocidade, OutputPorts.P12)
    }
    if (comando == "parar") {
        actuators.SetSpeedMotor(0, OutputPorts.P8)
    }
})
let comando = ""
let velocidade = 0
bluetooth.startUartService()
bluetooth.setTransmitPower(7)
velocidade = 600
basic.showIcon(IconNames.Square)

```

## Passo 28

Em seguida, modifique a porta de **P8** para **P12**.

```blocks
bluetooth.onBluetoothConnected(function () {
    basic.showIcon(IconNames.Happy)
})
bluetooth.onBluetoothDisconnected(function () {
    basic.showIcon(IconNames.No)
})
bluetooth.onUartDataReceived(serial.delimiters(Delimiters.NewLine), function () {
    comando = bluetooth.uartReadUntil(serial.delimiters(Delimiters.NewLine))
    if (comando == "A") {
        actuators.SetDirectionMotor(MotorDirection.antiClockwise, OutputPorts.P8)
        actuators.SetDirectionMotor(MotorDirection.clockwise, OutputPorts.P16)
        actuators.SetSpeedMotor(velocidade, OutputPorts.P12)
    }
    if (comando == "B") {
        actuators.SetDirectionMotor(MotorDirection.clockwise, OutputPorts.P8)
        actuators.SetDirectionMotor(MotorDirection.clockwise, OutputPorts.P16)
        actuators.SetSpeedMotor(velocidade, OutputPorts.P12)
    }
    if (comando == "C") {
        actuators.SetDirectionMotor(MotorDirection.antiClockwise, OutputPorts.P8)
        actuators.SetDirectionMotor(MotorDirection.antiClockwise, OutputPorts.P16)
        actuators.SetSpeedMotor(velocidade, OutputPorts.P12)
    }
    if (comando == "D") {
        actuators.SetDirectionMotor(MotorDirection.clockwise, OutputPorts.P8)
        actuators.SetDirectionMotor(MotorDirection.antiClockwise, OutputPorts.P16)
        actuators.SetSpeedMotor(velocidade, OutputPorts.P12)
    }
    if (comando == "parar") {
        actuators.SetSpeedMotor(0, OutputPorts.P12)
    }
})
let comando = ""
let velocidade = 0
bluetooth.startUartService()
bluetooth.setTransmitPower(7)
velocidade = 600
basic.showIcon(IconNames.Square)

```

## Passo 29

Agora seu código está pronto! Baixe-o para o micro:bit e teste-o.
Acesse a url "https://aula.fuzzymakers.com.br/microbit/joystick" para utilizar o controle depois de conectá-lo com o micro:bit.
“Os botões A, B, C e D movem o robô; o A move o robô para a frente, o B para a esquerda, o C para a direita e o D para trás.”
```blocks
```


## Passo 30
Se necessário, confira o seu código clicando na lâmpada de dica.

```blocks
bluetooth.onBluetoothConnected(function () {
    basic.showIcon(IconNames.Happy)
})
bluetooth.onBluetoothDisconnected(function () {
    basic.showIcon(IconNames.No)
})
bluetooth.onUartDataReceived(serial.delimiters(Delimiters.NewLine), function () {
    comando = bluetooth.uartReadUntil(serial.delimiters(Delimiters.NewLine))
    if (comando == "A") {
        actuators.SetDirectionMotor(MotorDirection.antiClockwise, OutputPorts.P8)
        actuators.SetDirectionMotor(MotorDirection.clockwise, OutputPorts.P16)
        actuators.SetSpeedMotor(velocidade, OutputPorts.P12)
    }
    if (comando == "B") {
        actuators.SetDirectionMotor(MotorDirection.clockwise, OutputPorts.P8)
        actuators.SetDirectionMotor(MotorDirection.clockwise, OutputPorts.P16)
        actuators.SetSpeedMotor(velocidade, OutputPorts.P12)
    }
    if (comando == "C") {
        actuators.SetDirectionMotor(MotorDirection.antiClockwise, OutputPorts.P8)
        actuators.SetDirectionMotor(MotorDirection.antiClockwise, OutputPorts.P16)
        actuators.SetSpeedMotor(velocidade, OutputPorts.P12)
    }
    if (comando == "D") {
        actuators.SetDirectionMotor(MotorDirection.clockwise, OutputPorts.P8)
        actuators.SetDirectionMotor(MotorDirection.antiClockwise, OutputPorts.P16)
        actuators.SetSpeedMotor(velocidade, OutputPorts.P12)
    }
    if (comando == "parar") {
        actuators.SetSpeedMotor(0, OutputPorts.P12)
    }
})
let comando = ""
let velocidade = 0
bluetooth.startUartService()
bluetooth.setTransmitPower(7)
velocidade = 600
basic.showIcon(IconNames.Square)
```



```package
fuzzyBot=github:FuzzyMakers/pxt-fuzzyMakers
```
