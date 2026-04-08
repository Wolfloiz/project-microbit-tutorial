### @diffs true
# Obedeça a Sinalização

## Passo 1
Neste tutorial, vamos combinar a lógica do seguidor de linha com as funções de identificação de símbolos do sensor
de visão. Vamos partir do código do seguidor que está pronto e implementar a leitura das cartas de sinalização. O robô iniciará 
o movimento com uma velocidade e vai reduzir de acordo com as placas até parar.

```template
let Iniciar = 0
let status_SL = 0
function esquerda () {
    fuzzyBot.motorRun(fuzzyBot.Motors.M1, fuzzyBot.Dir.CW, 30)
    fuzzyBot.motorRun(fuzzyBot.Motors.M2, fuzzyBot.Dir.CW, 50)
}
input.onButtonPressed(Button.A, function () {
    Iniciar = 0
    basic.showIcon(IconNames.Heart)
})
function esquerda_brusca () {
    fuzzyBot.motorRun(fuzzyBot.Motors.M1, fuzzyBot.Dir.CW, 0)
    fuzzyBot.motorRun(fuzzyBot.Motors.M2, fuzzyBot.Dir.CW, 50)
}
function direita () {
    fuzzyBot.motorRun(fuzzyBot.Motors.M1, fuzzyBot.Dir.CW, 50)
    fuzzyBot.motorRun(fuzzyBot.Motors.M2, fuzzyBot.Dir.CW, 30)
}
input.onButtonPressed(Button.B, function () {
    Iniciar = 1
    basic.showIcon(IconNames.Happy)
})
function frente () {
    fuzzyBot.motorRun(fuzzyBot.Motors.All, fuzzyBot.Dir.CW, 50)
}
function direita_brusca () {
    fuzzyBot.motorRun(fuzzyBot.Motors.M1, fuzzyBot.Dir.CW, 50)
    fuzzyBot.motorRun(fuzzyBot.Motors.M2, fuzzyBot.Dir.CW, 0)
}
function seguidor_linha () {
    if (fuzzyBot.readPatrol(fuzzyBot.Patrol.PatrolLeft) == 0 && fuzzyBot.readPatrol(fuzzyBot.Patrol.PatrolMiddle) == 0 && fuzzyBot.readPatrol(fuzzyBot.Patrol.PatrolRight) == 0) {
        status_SL = 0
    } else if (fuzzyBot.readPatrol(fuzzyBot.Patrol.PatrolLeft) == 0 && fuzzyBot.readPatrol(fuzzyBot.Patrol.PatrolMiddle) == 0 && fuzzyBot.readPatrol(fuzzyBot.Patrol.PatrolRight) == 1) {
        status_SL = 1
    } else if (fuzzyBot.readPatrol(fuzzyBot.Patrol.PatrolLeft) == 0 && fuzzyBot.readPatrol(fuzzyBot.Patrol.PatrolMiddle) == 1 && fuzzyBot.readPatrol(fuzzyBot.Patrol.PatrolRight) == 0) {
        status_SL = 2
    } else if (fuzzyBot.readPatrol(fuzzyBot.Patrol.PatrolLeft) == 0 && fuzzyBot.readPatrol(fuzzyBot.Patrol.PatrolMiddle) == 1 && fuzzyBot.readPatrol(fuzzyBot.Patrol.PatrolRight) == 1) {
        status_SL = 3
    } else if (fuzzyBot.readPatrol(fuzzyBot.Patrol.PatrolLeft) == 1 && fuzzyBot.readPatrol(fuzzyBot.Patrol.PatrolMiddle) == 0 && fuzzyBot.readPatrol(fuzzyBot.Patrol.PatrolRight) == 0) {
        status_SL = 4
    } else if (fuzzyBot.readPatrol(fuzzyBot.Patrol.PatrolLeft) == 1 && fuzzyBot.readPatrol(fuzzyBot.Patrol.PatrolMiddle) == 0 && fuzzyBot.readPatrol(fuzzyBot.Patrol.PatrolRight) == 1) {
        status_SL = 5
    } else if (fuzzyBot.readPatrol(fuzzyBot.Patrol.PatrolLeft) == 1 && fuzzyBot.readPatrol(fuzzyBot.Patrol.PatrolMiddle) == 1 && fuzzyBot.readPatrol(fuzzyBot.Patrol.PatrolRight) == 0) {
        status_SL = 6
    } else if (fuzzyBot.readPatrol(fuzzyBot.Patrol.PatrolLeft) == 1 && fuzzyBot.readPatrol(fuzzyBot.Patrol.PatrolMiddle) == 1 && fuzzyBot.readPatrol(fuzzyBot.Patrol.PatrolRight) == 1) {
        status_SL = 7
    }
}
basic.forever(function () {
    seguidor_linha()
    if (Iniciar == 1) {
        if (status_SL == 0) {
            frente()
        } else if (status_SL == 1) {
            esquerda()
        } else if (status_SL == 3) {
            esquerda_brusca()
        } else if (status_SL == 4) {
            direita()
        } else if (status_SL == 6) {
            direita_brusca()
        }
    } else {
        fuzzyBot.motorStop(fuzzyBot.Motors.All)
    }
})

```

## Passo 2
Como de costume, verifique se a biblioteca da Fuzzy Makers já está importada em seu MakeCode.
Se não estiver, clique na aba **+ Extensões**, copie o endereço "https://github.com/FuzzyMakers/pxt-fuzzyMakers",
cole-o no campo de pesquisa da janela que se abriu e selecione a biblioteca.

## Passo 3
Primeiramente, acesse o menu ``||basic:Básico||`` e adicione o bloco ``||basic:no iniciar||``
na área de programação.

```blocks
let Iniciar = 0
let status_SL = 0
function esquerda () {
    fuzzyBot.motorRun(fuzzyBot.Motors.M1, fuzzyBot.Dir.CW, 30)
    fuzzyBot.motorRun(fuzzyBot.Motors.M2, fuzzyBot.Dir.CW, 50)
}
input.onButtonPressed(Button.A, function () {
    Iniciar = 0
    basic.showIcon(IconNames.Heart)
})
function esquerda_brusca () {
    fuzzyBot.motorRun(fuzzyBot.Motors.M1, fuzzyBot.Dir.CW, 0)
    fuzzyBot.motorRun(fuzzyBot.Motors.M2, fuzzyBot.Dir.CW, 50)
}
function direita () {
    fuzzyBot.motorRun(fuzzyBot.Motors.M1, fuzzyBot.Dir.CW, 50)
    fuzzyBot.motorRun(fuzzyBot.Motors.M2, fuzzyBot.Dir.CW, 30)
}
input.onButtonPressed(Button.B, function () {
    Iniciar = 1
    basic.showIcon(IconNames.Happy)
})
function frente () {
    fuzzyBot.motorRun(fuzzyBot.Motors.All, fuzzyBot.Dir.CW, 50)
}
function direita_brusca () {
    fuzzyBot.motorRun(fuzzyBot.Motors.M1, fuzzyBot.Dir.CW, 50)
    fuzzyBot.motorRun(fuzzyBot.Motors.M2, fuzzyBot.Dir.CW, 0)
}
function seguidor_linha () {
    if (fuzzyBot.readPatrol(fuzzyBot.Patrol.PatrolLeft) == 0 && fuzzyBot.readPatrol(fuzzyBot.Patrol.PatrolMiddle) == 0 && fuzzyBot.readPatrol(fuzzyBot.Patrol.PatrolRight) == 0) {
        status_SL = 0
    } else if (fuzzyBot.readPatrol(fuzzyBot.Patrol.PatrolLeft) == 0 && fuzzyBot.readPatrol(fuzzyBot.Patrol.PatrolMiddle) == 0 && fuzzyBot.readPatrol(fuzzyBot.Patrol.PatrolRight) == 1) {
        status_SL = 1
    } else if (fuzzyBot.readPatrol(fuzzyBot.Patrol.PatrolLeft) == 0 && fuzzyBot.readPatrol(fuzzyBot.Patrol.PatrolMiddle) == 1 && fuzzyBot.readPatrol(fuzzyBot.Patrol.PatrolRight) == 0) {
        status_SL = 2
    } else if (fuzzyBot.readPatrol(fuzzyBot.Patrol.PatrolLeft) == 0 && fuzzyBot.readPatrol(fuzzyBot.Patrol.PatrolMiddle) == 1 && fuzzyBot.readPatrol(fuzzyBot.Patrol.PatrolRight) == 1) {
        status_SL = 3
    } else if (fuzzyBot.readPatrol(fuzzyBot.Patrol.PatrolLeft) == 1 && fuzzyBot.readPatrol(fuzzyBot.Patrol.PatrolMiddle) == 0 && fuzzyBot.readPatrol(fuzzyBot.Patrol.PatrolRight) == 0) {
        status_SL = 4
    } else if (fuzzyBot.readPatrol(fuzzyBot.Patrol.PatrolLeft) == 1 && fuzzyBot.readPatrol(fuzzyBot.Patrol.PatrolMiddle) == 0 && fuzzyBot.readPatrol(fuzzyBot.Patrol.PatrolRight) == 1) {
        status_SL = 5
    } else if (fuzzyBot.readPatrol(fuzzyBot.Patrol.PatrolLeft) == 1 && fuzzyBot.readPatrol(fuzzyBot.Patrol.PatrolMiddle) == 1 && fuzzyBot.readPatrol(fuzzyBot.Patrol.PatrolRight) == 0) {
        status_SL = 6
    } else if (fuzzyBot.readPatrol(fuzzyBot.Patrol.PatrolLeft) == 1 && fuzzyBot.readPatrol(fuzzyBot.Patrol.PatrolMiddle) == 1 && fuzzyBot.readPatrol(fuzzyBot.Patrol.PatrolRight) == 1) {
        status_SL = 7
    }
}
basic.forever(function () {
    seguidor_linha()
    if (Iniciar == 1) {
        if (status_SL == 0) {
            frente()
        } else if (status_SL == 1) {
            esquerda()
        } else if (status_SL == 3) {
            esquerda_brusca()
        } else if (status_SL == 4) {
            direita()
        } else if (status_SL == 6) {
            direita_brusca()
        }
    } else {
        fuzzyBot.motorStop(fuzzyBot.Motors.All)
    }
})

```

## Passo 4
Acesse a aba ``||basic:Básico||`` e adicione um bloco ``||basic:pausa (ms) 100||`` no laço ``||basic:no iniciar||``.
Modifique a duração da pausa de **100ms** para **2000ms** (2 segundos).

```blocks
function esquerda () {
    fuzzyBot.motorRun(fuzzyBot.Motors.M1, fuzzyBot.Dir.CW, 30)
    fuzzyBot.motorRun(fuzzyBot.Motors.M2, fuzzyBot.Dir.CW, 50)
}
input.onButtonPressed(Button.A, function () {
    Iniciar = 0
    basic.showIcon(IconNames.Heart)
})
function esquerda_brusca () {
    fuzzyBot.motorRun(fuzzyBot.Motors.M1, fuzzyBot.Dir.CW, 0)
    fuzzyBot.motorRun(fuzzyBot.Motors.M2, fuzzyBot.Dir.CW, 50)
}
function direita () {
    fuzzyBot.motorRun(fuzzyBot.Motors.M1, fuzzyBot.Dir.CW, 50)
    fuzzyBot.motorRun(fuzzyBot.Motors.M2, fuzzyBot.Dir.CW, 30)
}
input.onButtonPressed(Button.B, function () {
    Iniciar = 1
    basic.showIcon(IconNames.Happy)
})
function frente () {
    fuzzyBot.motorRun(fuzzyBot.Motors.All, fuzzyBot.Dir.CW, 50)
}
function direita_brusca () {
    fuzzyBot.motorRun(fuzzyBot.Motors.M1, fuzzyBot.Dir.CW, 50)
    fuzzyBot.motorRun(fuzzyBot.Motors.M2, fuzzyBot.Dir.CW, 0)
}
function seguidor_linha () {
    if (fuzzyBot.readPatrol(fuzzyBot.Patrol.PatrolLeft) == 0 && fuzzyBot.readPatrol(fuzzyBot.Patrol.PatrolMiddle) == 0 && fuzzyBot.readPatrol(fuzzyBot.Patrol.PatrolRight) == 0) {
        status_SL = 0
    } else if (fuzzyBot.readPatrol(fuzzyBot.Patrol.PatrolLeft) == 0 && fuzzyBot.readPatrol(fuzzyBot.Patrol.PatrolMiddle) == 0 && fuzzyBot.readPatrol(fuzzyBot.Patrol.PatrolRight) == 1) {
        status_SL = 1
    } else if (fuzzyBot.readPatrol(fuzzyBot.Patrol.PatrolLeft) == 0 && fuzzyBot.readPatrol(fuzzyBot.Patrol.PatrolMiddle) == 1 && fuzzyBot.readPatrol(fuzzyBot.Patrol.PatrolRight) == 0) {
        status_SL = 2
    } else if (fuzzyBot.readPatrol(fuzzyBot.Patrol.PatrolLeft) == 0 && fuzzyBot.readPatrol(fuzzyBot.Patrol.PatrolMiddle) == 1 && fuzzyBot.readPatrol(fuzzyBot.Patrol.PatrolRight) == 1) {
        status_SL = 3
    } else if (fuzzyBot.readPatrol(fuzzyBot.Patrol.PatrolLeft) == 1 && fuzzyBot.readPatrol(fuzzyBot.Patrol.PatrolMiddle) == 0 && fuzzyBot.readPatrol(fuzzyBot.Patrol.PatrolRight) == 0) {
        status_SL = 4
    } else if (fuzzyBot.readPatrol(fuzzyBot.Patrol.PatrolLeft) == 1 && fuzzyBot.readPatrol(fuzzyBot.Patrol.PatrolMiddle) == 0 && fuzzyBot.readPatrol(fuzzyBot.Patrol.PatrolRight) == 1) {
        status_SL = 5
    } else if (fuzzyBot.readPatrol(fuzzyBot.Patrol.PatrolLeft) == 1 && fuzzyBot.readPatrol(fuzzyBot.Patrol.PatrolMiddle) == 1 && fuzzyBot.readPatrol(fuzzyBot.Patrol.PatrolRight) == 0) {
        status_SL = 6
    } else if (fuzzyBot.readPatrol(fuzzyBot.Patrol.PatrolLeft) == 1 && fuzzyBot.readPatrol(fuzzyBot.Patrol.PatrolMiddle) == 1 && fuzzyBot.readPatrol(fuzzyBot.Patrol.PatrolRight) == 1) {
        status_SL = 7
    }
}
let status_SL = 0
let Iniciar = 0
basic.pause(2000)
basic.forever(function () {
    seguidor_linha()
    if (Iniciar == 1) {
        if (status_SL == 0) {
            frente()
        } else if (status_SL == 1) {
            esquerda()
        } else if (status_SL == 3) {
            esquerda_brusca()
        } else if (status_SL == 4) {
            direita()
        } else if (status_SL == 6) {
            direita_brusca()
        }
    } else {
        fuzzyBot.motorStop(fuzzyBot.Motors.All)
    }
})

```

## Passo 5
Vá ao menu ``||Advanced:Avançado||``, acesse ``||Camera:Sensor Câmera||`` e selecione o bloco
``||Camera:Inicializar câmera - Porta I2C - Endereço 0x60||``. Posicione o bloco abaixo
da ``||basic:pausa||``. 
```blocks
function esquerda () {
    fuzzyBot.motorRun(fuzzyBot.Motors.M1, fuzzyBot.Dir.CW, 30)
    fuzzyBot.motorRun(fuzzyBot.Motors.M2, fuzzyBot.Dir.CW, 50)
}
input.onButtonPressed(Button.A, function () {
    Iniciar = 0
    basic.showIcon(IconNames.Heart)
})
function esquerda_brusca () {
    fuzzyBot.motorRun(fuzzyBot.Motors.M1, fuzzyBot.Dir.CW, 0)
    fuzzyBot.motorRun(fuzzyBot.Motors.M2, fuzzyBot.Dir.CW, 50)
}
function direita () {
    fuzzyBot.motorRun(fuzzyBot.Motors.M1, fuzzyBot.Dir.CW, 50)
    fuzzyBot.motorRun(fuzzyBot.Motors.M2, fuzzyBot.Dir.CW, 30)
}
input.onButtonPressed(Button.B, function () {
    Iniciar = 1
    basic.showIcon(IconNames.Happy)
})
function frente () {
    fuzzyBot.motorRun(fuzzyBot.Motors.All, fuzzyBot.Dir.CW, 50)
}
function direita_brusca () {
    fuzzyBot.motorRun(fuzzyBot.Motors.M1, fuzzyBot.Dir.CW, 50)
    fuzzyBot.motorRun(fuzzyBot.Motors.M2, fuzzyBot.Dir.CW, 0)
}
function seguidor_linha () {
    if (fuzzyBot.readPatrol(fuzzyBot.Patrol.PatrolLeft) == 0 && fuzzyBot.readPatrol(fuzzyBot.Patrol.PatrolMiddle) == 0 && fuzzyBot.readPatrol(fuzzyBot.Patrol.PatrolRight) == 0) {
        status_SL = 0
    } else if (fuzzyBot.readPatrol(fuzzyBot.Patrol.PatrolLeft) == 0 && fuzzyBot.readPatrol(fuzzyBot.Patrol.PatrolMiddle) == 0 && fuzzyBot.readPatrol(fuzzyBot.Patrol.PatrolRight) == 1) {
        status_SL = 1
    } else if (fuzzyBot.readPatrol(fuzzyBot.Patrol.PatrolLeft) == 0 && fuzzyBot.readPatrol(fuzzyBot.Patrol.PatrolMiddle) == 1 && fuzzyBot.readPatrol(fuzzyBot.Patrol.PatrolRight) == 0) {
        status_SL = 2
    } else if (fuzzyBot.readPatrol(fuzzyBot.Patrol.PatrolLeft) == 0 && fuzzyBot.readPatrol(fuzzyBot.Patrol.PatrolMiddle) == 1 && fuzzyBot.readPatrol(fuzzyBot.Patrol.PatrolRight) == 1) {
        status_SL = 3
    } else if (fuzzyBot.readPatrol(fuzzyBot.Patrol.PatrolLeft) == 1 && fuzzyBot.readPatrol(fuzzyBot.Patrol.PatrolMiddle) == 0 && fuzzyBot.readPatrol(fuzzyBot.Patrol.PatrolRight) == 0) {
        status_SL = 4
    } else if (fuzzyBot.readPatrol(fuzzyBot.Patrol.PatrolLeft) == 1 && fuzzyBot.readPatrol(fuzzyBot.Patrol.PatrolMiddle) == 0 && fuzzyBot.readPatrol(fuzzyBot.Patrol.PatrolRight) == 1) {
        status_SL = 5
    } else if (fuzzyBot.readPatrol(fuzzyBot.Patrol.PatrolLeft) == 1 && fuzzyBot.readPatrol(fuzzyBot.Patrol.PatrolMiddle) == 1 && fuzzyBot.readPatrol(fuzzyBot.Patrol.PatrolRight) == 0) {
        status_SL = 6
    } else if (fuzzyBot.readPatrol(fuzzyBot.Patrol.PatrolLeft) == 1 && fuzzyBot.readPatrol(fuzzyBot.Patrol.PatrolMiddle) == 1 && fuzzyBot.readPatrol(fuzzyBot.Patrol.PatrolRight) == 1) {
        status_SL = 7
    }
}
let status_SL = 0
let Iniciar = 0
basic.pause(2000)
Camera.Begin(sentry_mode_e.kI2CMode, sengo2_addr_e.ADDR1)
basic.forever(function () {
    seguidor_linha()
    if (Iniciar == 1) {
        if (status_SL == 0) {
            frente()
        } else if (status_SL == 1) {
            esquerda()
        } else if (status_SL == 3) {
            esquerda_brusca()
        } else if (status_SL == 4) {
            direita()
        } else if (status_SL == 6) {
            direita_brusca()
        }
    } else {
        fuzzyBot.motorStop(fuzzyBot.Motors.All)
    }
})

```

## Passo 6
Retorne à categoria ``||Camera:Sensor Câmera||`` e adicione o bloco ``||Camera:Habilitar modo Cor||`` 
no laço ``||basic:no iniciar||``, altere o modo ``||Camera:Cor||`` para ``||Camera:Cartão||`` .


```blocks
function esquerda () {
    fuzzyBot.motorRun(fuzzyBot.Motors.M1, fuzzyBot.Dir.CW, 30)
    fuzzyBot.motorRun(fuzzyBot.Motors.M2, fuzzyBot.Dir.CW, 50)
}
input.onButtonPressed(Button.A, function () {
    Iniciar = 0
    basic.showIcon(IconNames.Heart)
})
function esquerda_brusca () {
    fuzzyBot.motorRun(fuzzyBot.Motors.M1, fuzzyBot.Dir.CW, 0)
    fuzzyBot.motorRun(fuzzyBot.Motors.M2, fuzzyBot.Dir.CW, 50)
}
function direita () {
    fuzzyBot.motorRun(fuzzyBot.Motors.M1, fuzzyBot.Dir.CW, 50)
    fuzzyBot.motorRun(fuzzyBot.Motors.M2, fuzzyBot.Dir.CW, 30)
}
input.onButtonPressed(Button.B, function () {
    Iniciar = 1
    basic.showIcon(IconNames.Happy)
})
function frente () {
    fuzzyBot.motorRun(fuzzyBot.Motors.All, fuzzyBot.Dir.CW, 50)
}
function direita_brusca () {
    fuzzyBot.motorRun(fuzzyBot.Motors.M1, fuzzyBot.Dir.CW, 50)
    fuzzyBot.motorRun(fuzzyBot.Motors.M2, fuzzyBot.Dir.CW, 0)
}
function seguidor_linha () {
    if (fuzzyBot.readPatrol(fuzzyBot.Patrol.PatrolLeft) == 0 && fuzzyBot.readPatrol(fuzzyBot.Patrol.PatrolMiddle) == 0 && fuzzyBot.readPatrol(fuzzyBot.Patrol.PatrolRight) == 0) {
        status_SL = 0
    } else if (fuzzyBot.readPatrol(fuzzyBot.Patrol.PatrolLeft) == 0 && fuzzyBot.readPatrol(fuzzyBot.Patrol.PatrolMiddle) == 0 && fuzzyBot.readPatrol(fuzzyBot.Patrol.PatrolRight) == 1) {
        status_SL = 1
    } else if (fuzzyBot.readPatrol(fuzzyBot.Patrol.PatrolLeft) == 0 && fuzzyBot.readPatrol(fuzzyBot.Patrol.PatrolMiddle) == 1 && fuzzyBot.readPatrol(fuzzyBot.Patrol.PatrolRight) == 0) {
        status_SL = 2
    } else if (fuzzyBot.readPatrol(fuzzyBot.Patrol.PatrolLeft) == 0 && fuzzyBot.readPatrol(fuzzyBot.Patrol.PatrolMiddle) == 1 && fuzzyBot.readPatrol(fuzzyBot.Patrol.PatrolRight) == 1) {
        status_SL = 3
    } else if (fuzzyBot.readPatrol(fuzzyBot.Patrol.PatrolLeft) == 1 && fuzzyBot.readPatrol(fuzzyBot.Patrol.PatrolMiddle) == 0 && fuzzyBot.readPatrol(fuzzyBot.Patrol.PatrolRight) == 0) {
        status_SL = 4
    } else if (fuzzyBot.readPatrol(fuzzyBot.Patrol.PatrolLeft) == 1 && fuzzyBot.readPatrol(fuzzyBot.Patrol.PatrolMiddle) == 0 && fuzzyBot.readPatrol(fuzzyBot.Patrol.PatrolRight) == 1) {
        status_SL = 5
    } else if (fuzzyBot.readPatrol(fuzzyBot.Patrol.PatrolLeft) == 1 && fuzzyBot.readPatrol(fuzzyBot.Patrol.PatrolMiddle) == 1 && fuzzyBot.readPatrol(fuzzyBot.Patrol.PatrolRight) == 0) {
        status_SL = 6
    } else if (fuzzyBot.readPatrol(fuzzyBot.Patrol.PatrolLeft) == 1 && fuzzyBot.readPatrol(fuzzyBot.Patrol.PatrolMiddle) == 1 && fuzzyBot.readPatrol(fuzzyBot.Patrol.PatrolRight) == 1) {
        status_SL = 7
    }
}
let status_SL = 0
let Iniciar = 0
basic.pause(2000)
Camera.Begin(sentry_mode_e.kI2CMode, sengo2_addr_e.ADDR1)
Camera.VisionSetStatus(sengo2_status.Enable, sengo_vision_e.kVisionCard)
basic.forever(function () {
    seguidor_linha()
    if (Iniciar == 1) {
        if (status_SL == 0) {
            frente()
        } else if (status_SL == 1) {
            esquerda()
        } else if (status_SL == 3) {
            esquerda_brusca()
        } else if (status_SL == 4) {
            direita()
        } else if (status_SL == 6) {
            direita_brusca()
        }
    } else {
        fuzzyBot.motorStop(fuzzyBot.Motors.All)
    }
})

```

## Passo 7
Adicione o bloco ``||basic:mostrar ícone||`` depois da configuração da câmera.

```blocks
function esquerda () {
    fuzzyBot.motorRun(fuzzyBot.Motors.M1, fuzzyBot.Dir.CW, 30)
    fuzzyBot.motorRun(fuzzyBot.Motors.M2, fuzzyBot.Dir.CW, 50)
}
input.onButtonPressed(Button.A, function () {
    Iniciar = 0
    basic.showIcon(IconNames.Heart)
})
function esquerda_brusca () {
    fuzzyBot.motorRun(fuzzyBot.Motors.M1, fuzzyBot.Dir.CW, 0)
    fuzzyBot.motorRun(fuzzyBot.Motors.M2, fuzzyBot.Dir.CW, 50)
}
function direita () {
    fuzzyBot.motorRun(fuzzyBot.Motors.M1, fuzzyBot.Dir.CW, 50)
    fuzzyBot.motorRun(fuzzyBot.Motors.M2, fuzzyBot.Dir.CW, 30)
}
input.onButtonPressed(Button.B, function () {
    Iniciar = 1
    basic.showIcon(IconNames.Happy)
})
function frente () {
    fuzzyBot.motorRun(fuzzyBot.Motors.All, fuzzyBot.Dir.CW, 50)
}
function direita_brusca () {
    fuzzyBot.motorRun(fuzzyBot.Motors.M1, fuzzyBot.Dir.CW, 50)
    fuzzyBot.motorRun(fuzzyBot.Motors.M2, fuzzyBot.Dir.CW, 0)
}
function seguidor_linha () {
    if (fuzzyBot.readPatrol(fuzzyBot.Patrol.PatrolLeft) == 0 && fuzzyBot.readPatrol(fuzzyBot.Patrol.PatrolMiddle) == 0 && fuzzyBot.readPatrol(fuzzyBot.Patrol.PatrolRight) == 0) {
        status_SL = 0
    } else if (fuzzyBot.readPatrol(fuzzyBot.Patrol.PatrolLeft) == 0 && fuzzyBot.readPatrol(fuzzyBot.Patrol.PatrolMiddle) == 0 && fuzzyBot.readPatrol(fuzzyBot.Patrol.PatrolRight) == 1) {
        status_SL = 1
    } else if (fuzzyBot.readPatrol(fuzzyBot.Patrol.PatrolLeft) == 0 && fuzzyBot.readPatrol(fuzzyBot.Patrol.PatrolMiddle) == 1 && fuzzyBot.readPatrol(fuzzyBot.Patrol.PatrolRight) == 0) {
        status_SL = 2
    } else if (fuzzyBot.readPatrol(fuzzyBot.Patrol.PatrolLeft) == 0 && fuzzyBot.readPatrol(fuzzyBot.Patrol.PatrolMiddle) == 1 && fuzzyBot.readPatrol(fuzzyBot.Patrol.PatrolRight) == 1) {
        status_SL = 3
    } else if (fuzzyBot.readPatrol(fuzzyBot.Patrol.PatrolLeft) == 1 && fuzzyBot.readPatrol(fuzzyBot.Patrol.PatrolMiddle) == 0 && fuzzyBot.readPatrol(fuzzyBot.Patrol.PatrolRight) == 0) {
        status_SL = 4
    } else if (fuzzyBot.readPatrol(fuzzyBot.Patrol.PatrolLeft) == 1 && fuzzyBot.readPatrol(fuzzyBot.Patrol.PatrolMiddle) == 0 && fuzzyBot.readPatrol(fuzzyBot.Patrol.PatrolRight) == 1) {
        status_SL = 5
    } else if (fuzzyBot.readPatrol(fuzzyBot.Patrol.PatrolLeft) == 1 && fuzzyBot.readPatrol(fuzzyBot.Patrol.PatrolMiddle) == 1 && fuzzyBot.readPatrol(fuzzyBot.Patrol.PatrolRight) == 0) {
        status_SL = 6
    } else if (fuzzyBot.readPatrol(fuzzyBot.Patrol.PatrolLeft) == 1 && fuzzyBot.readPatrol(fuzzyBot.Patrol.PatrolMiddle) == 1 && fuzzyBot.readPatrol(fuzzyBot.Patrol.PatrolRight) == 1) {
        status_SL = 7
    }
}
let status_SL = 0
let Iniciar = 0
basic.pause(2000)
Camera.Begin(sentry_mode_e.kI2CMode, sengo2_addr_e.ADDR1)
Camera.VisionSetStatus(sengo2_status.Enable, sengo_vision_e.kVisionCard)
basic.showIcon(IconNames.Heart)

basic.forever(function () {
    seguidor_linha()
    if (Iniciar == 1) {
        if (status_SL == 0) {
            frente()
        } else if (status_SL == 1) {
            esquerda()
        } else if (status_SL == 3) {
            esquerda_brusca()
        } else if (status_SL == 4) {
            direita()
        } else if (status_SL == 6) {
            direita_brusca()
        }
    } else {
        fuzzyBot.motorStop(fuzzyBot.Motors.All)
    }
})
```

## Passo 8
Acesse o menu ``||variables:Variáveis||`` e clique em 
**"Fazer uma variável..."**. Crie uma variável chamada
``||variables:velocidade||``.
```blocks
function esquerda () {
    fuzzyBot.motorRun(fuzzyBot.Motors.M1, fuzzyBot.Dir.CW, 30)
    fuzzyBot.motorRun(fuzzyBot.Motors.M2, fuzzyBot.Dir.CW, 50)
}
input.onButtonPressed(Button.A, function () {
    Iniciar = 0
    basic.showIcon(IconNames.Heart)
})
function esquerda_brusca () {
    fuzzyBot.motorRun(fuzzyBot.Motors.M1, fuzzyBot.Dir.CW, 0)
    fuzzyBot.motorRun(fuzzyBot.Motors.M2, fuzzyBot.Dir.CW, 50)
}
function direita () {
    fuzzyBot.motorRun(fuzzyBot.Motors.M1, fuzzyBot.Dir.CW, 50)
    fuzzyBot.motorRun(fuzzyBot.Motors.M2, fuzzyBot.Dir.CW, 30)
}
input.onButtonPressed(Button.B, function () {
    Iniciar = 1
    basic.showIcon(IconNames.Happy)
})
function frente () {
    fuzzyBot.motorRun(fuzzyBot.Motors.All, fuzzyBot.Dir.CW, 50)
}
function direita_brusca () {
    fuzzyBot.motorRun(fuzzyBot.Motors.M1, fuzzyBot.Dir.CW, 50)
    fuzzyBot.motorRun(fuzzyBot.Motors.M2, fuzzyBot.Dir.CW, 0)
}
function seguidor_linha () {
    if (fuzzyBot.readPatrol(fuzzyBot.Patrol.PatrolLeft) == 0 && fuzzyBot.readPatrol(fuzzyBot.Patrol.PatrolMiddle) == 0 && fuzzyBot.readPatrol(fuzzyBot.Patrol.PatrolRight) == 0) {
        status_SL = 0
    } else if (fuzzyBot.readPatrol(fuzzyBot.Patrol.PatrolLeft) == 0 && fuzzyBot.readPatrol(fuzzyBot.Patrol.PatrolMiddle) == 0 && fuzzyBot.readPatrol(fuzzyBot.Patrol.PatrolRight) == 1) {
        status_SL = 1
    } else if (fuzzyBot.readPatrol(fuzzyBot.Patrol.PatrolLeft) == 0 && fuzzyBot.readPatrol(fuzzyBot.Patrol.PatrolMiddle) == 1 && fuzzyBot.readPatrol(fuzzyBot.Patrol.PatrolRight) == 0) {
        status_SL = 2
    } else if (fuzzyBot.readPatrol(fuzzyBot.Patrol.PatrolLeft) == 0 && fuzzyBot.readPatrol(fuzzyBot.Patrol.PatrolMiddle) == 1 && fuzzyBot.readPatrol(fuzzyBot.Patrol.PatrolRight) == 1) {
        status_SL = 3
    } else if (fuzzyBot.readPatrol(fuzzyBot.Patrol.PatrolLeft) == 1 && fuzzyBot.readPatrol(fuzzyBot.Patrol.PatrolMiddle) == 0 && fuzzyBot.readPatrol(fuzzyBot.Patrol.PatrolRight) == 0) {
        status_SL = 4
    } else if (fuzzyBot.readPatrol(fuzzyBot.Patrol.PatrolLeft) == 1 && fuzzyBot.readPatrol(fuzzyBot.Patrol.PatrolMiddle) == 0 && fuzzyBot.readPatrol(fuzzyBot.Patrol.PatrolRight) == 1) {
        status_SL = 5
    } else if (fuzzyBot.readPatrol(fuzzyBot.Patrol.PatrolLeft) == 1 && fuzzyBot.readPatrol(fuzzyBot.Patrol.PatrolMiddle) == 1 && fuzzyBot.readPatrol(fuzzyBot.Patrol.PatrolRight) == 0) {
        status_SL = 6
    } else if (fuzzyBot.readPatrol(fuzzyBot.Patrol.PatrolLeft) == 1 && fuzzyBot.readPatrol(fuzzyBot.Patrol.PatrolMiddle) == 1 && fuzzyBot.readPatrol(fuzzyBot.Patrol.PatrolRight) == 1) {
        status_SL = 7
    }
}
let status_SL = 0
let Iniciar = 0
basic.pause(2000)
Camera.Begin(sentry_mode_e.kI2CMode, sengo2_addr_e.ADDR1)
Camera.VisionSetStatus(sengo2_status.Enable, sengo_vision_e.kVisionCard)
basic.showIcon(IconNames.Heart)

basic.forever(function () {
    seguidor_linha()
    if (Iniciar == 1) {
        if (status_SL == 0) {
            frente()
        } else if (status_SL == 1) {
            esquerda()
        } else if (status_SL == 3) {
            esquerda_brusca()
        } else if (status_SL == 4) {
            direita()
        } else if (status_SL == 6) {
            direita_brusca()
        }
    } else {
        fuzzyBot.motorStop(fuzzyBot.Motors.All)
    }
})
```

## Passo 9
Em seguida, arraste um bloco ``||variables:definir velocidade para 0||`` 
para o bloco ``||basic:no iniciar||``. 
Altere o valor da variável velocidade de **0** para **80**.

```blocks
function esquerda () {
    fuzzyBot.motorRun(fuzzyBot.Motors.M1, fuzzyBot.Dir.CW, 30)
    fuzzyBot.motorRun(fuzzyBot.Motors.M2, fuzzyBot.Dir.CW, 50)
}
input.onButtonPressed(Button.A, function () {
    Iniciar = 0
    basic.showIcon(IconNames.Heart)
})
function esquerda_brusca () {
    fuzzyBot.motorRun(fuzzyBot.Motors.M1, fuzzyBot.Dir.CW, 0)
    fuzzyBot.motorRun(fuzzyBot.Motors.M2, fuzzyBot.Dir.CW, 50)
}
function direita () {
    fuzzyBot.motorRun(fuzzyBot.Motors.M1, fuzzyBot.Dir.CW, 50)
    fuzzyBot.motorRun(fuzzyBot.Motors.M2, fuzzyBot.Dir.CW, 30)
}
input.onButtonPressed(Button.B, function () {
    Iniciar = 1
    basic.showIcon(IconNames.Happy)
})
function frente () {
    fuzzyBot.motorRun(fuzzyBot.Motors.All, fuzzyBot.Dir.CW, 50)
}
function direita_brusca () {
    fuzzyBot.motorRun(fuzzyBot.Motors.M1, fuzzyBot.Dir.CW, 50)
    fuzzyBot.motorRun(fuzzyBot.Motors.M2, fuzzyBot.Dir.CW, 0)
}
function seguidor_linha () {
    if (fuzzyBot.readPatrol(fuzzyBot.Patrol.PatrolLeft) == 0 && fuzzyBot.readPatrol(fuzzyBot.Patrol.PatrolMiddle) == 0 && fuzzyBot.readPatrol(fuzzyBot.Patrol.PatrolRight) == 0) {
        status_SL = 0
    } else if (fuzzyBot.readPatrol(fuzzyBot.Patrol.PatrolLeft) == 0 && fuzzyBot.readPatrol(fuzzyBot.Patrol.PatrolMiddle) == 0 && fuzzyBot.readPatrol(fuzzyBot.Patrol.PatrolRight) == 1) {
        status_SL = 1
    } else if (fuzzyBot.readPatrol(fuzzyBot.Patrol.PatrolLeft) == 0 && fuzzyBot.readPatrol(fuzzyBot.Patrol.PatrolMiddle) == 1 && fuzzyBot.readPatrol(fuzzyBot.Patrol.PatrolRight) == 0) {
        status_SL = 2
    } else if (fuzzyBot.readPatrol(fuzzyBot.Patrol.PatrolLeft) == 0 && fuzzyBot.readPatrol(fuzzyBot.Patrol.PatrolMiddle) == 1 && fuzzyBot.readPatrol(fuzzyBot.Patrol.PatrolRight) == 1) {
        status_SL = 3
    } else if (fuzzyBot.readPatrol(fuzzyBot.Patrol.PatrolLeft) == 1 && fuzzyBot.readPatrol(fuzzyBot.Patrol.PatrolMiddle) == 0 && fuzzyBot.readPatrol(fuzzyBot.Patrol.PatrolRight) == 0) {
        status_SL = 4
    } else if (fuzzyBot.readPatrol(fuzzyBot.Patrol.PatrolLeft) == 1 && fuzzyBot.readPatrol(fuzzyBot.Patrol.PatrolMiddle) == 0 && fuzzyBot.readPatrol(fuzzyBot.Patrol.PatrolRight) == 1) {
        status_SL = 5
    } else if (fuzzyBot.readPatrol(fuzzyBot.Patrol.PatrolLeft) == 1 && fuzzyBot.readPatrol(fuzzyBot.Patrol.PatrolMiddle) == 1 && fuzzyBot.readPatrol(fuzzyBot.Patrol.PatrolRight) == 0) {
        status_SL = 6
    } else if (fuzzyBot.readPatrol(fuzzyBot.Patrol.PatrolLeft) == 1 && fuzzyBot.readPatrol(fuzzyBot.Patrol.PatrolMiddle) == 1 && fuzzyBot.readPatrol(fuzzyBot.Patrol.PatrolRight) == 1) {
        status_SL = 7
    }
}
let status_SL = 0
let Iniciar = 0
basic.pause(2000)
Camera.Begin(sentry_mode_e.kI2CMode, sengo2_addr_e.ADDR1)
Camera.VisionSetStatus(sengo2_status.Enable, sengo_vision_e.kVisionCard)
basic.showIcon(IconNames.Heart)
let velocidade = 80


basic.forever(function () {
    seguidor_linha()
    if (Iniciar == 1) {
        if (status_SL == 0) {
            frente()
        } else if (status_SL == 1) {
            esquerda()
        } else if (status_SL == 3) {
            esquerda_brusca()
        } else if (status_SL == 4) {
            direita()
        } else if (status_SL == 6) {
            direita_brusca()
        }
    } else {
        fuzzyBot.motorStop(fuzzyBot.Motors.All)
    }
})

```

## Passo 10
Volte ao menu ``||basic:Básico||``, e adicione outro bloco ``||basic:sempre||``
na área de programação. A rotina implementada neste bloco funcionará de forma paralela à detecção de linha.

```blocks
function esquerda () {
    fuzzyBot.motorRun(fuzzyBot.Motors.M1, fuzzyBot.Dir.CW, 30)
    fuzzyBot.motorRun(fuzzyBot.Motors.M2, fuzzyBot.Dir.CW, 50)
}
input.onButtonPressed(Button.A, function () {
    Iniciar = 0
    basic.showIcon(IconNames.Heart)
})
function esquerda_brusca () {
    fuzzyBot.motorRun(fuzzyBot.Motors.M1, fuzzyBot.Dir.CW, 0)
    fuzzyBot.motorRun(fuzzyBot.Motors.M2, fuzzyBot.Dir.CW, 50)
}
function direita () {
    fuzzyBot.motorRun(fuzzyBot.Motors.M1, fuzzyBot.Dir.CW, 50)
    fuzzyBot.motorRun(fuzzyBot.Motors.M2, fuzzyBot.Dir.CW, 30)
}
input.onButtonPressed(Button.B, function () {
    Iniciar = 1
    basic.showIcon(IconNames.Happy)
})
function frente () {
    fuzzyBot.motorRun(fuzzyBot.Motors.All, fuzzyBot.Dir.CW, 50)
}
function direita_brusca () {
    fuzzyBot.motorRun(fuzzyBot.Motors.M1, fuzzyBot.Dir.CW, 50)
    fuzzyBot.motorRun(fuzzyBot.Motors.M2, fuzzyBot.Dir.CW, 0)
}
function seguidor_linha () {
    if (fuzzyBot.readPatrol(fuzzyBot.Patrol.PatrolLeft) == 0 && fuzzyBot.readPatrol(fuzzyBot.Patrol.PatrolMiddle) == 0 && fuzzyBot.readPatrol(fuzzyBot.Patrol.PatrolRight) == 0) {
        status_SL = 0
    } else if (fuzzyBot.readPatrol(fuzzyBot.Patrol.PatrolLeft) == 0 && fuzzyBot.readPatrol(fuzzyBot.Patrol.PatrolMiddle) == 0 && fuzzyBot.readPatrol(fuzzyBot.Patrol.PatrolRight) == 1) {
        status_SL = 1
    } else if (fuzzyBot.readPatrol(fuzzyBot.Patrol.PatrolLeft) == 0 && fuzzyBot.readPatrol(fuzzyBot.Patrol.PatrolMiddle) == 1 && fuzzyBot.readPatrol(fuzzyBot.Patrol.PatrolRight) == 0) {
        status_SL = 2
    } else if (fuzzyBot.readPatrol(fuzzyBot.Patrol.PatrolLeft) == 0 && fuzzyBot.readPatrol(fuzzyBot.Patrol.PatrolMiddle) == 1 && fuzzyBot.readPatrol(fuzzyBot.Patrol.PatrolRight) == 1) {
        status_SL = 3
    } else if (fuzzyBot.readPatrol(fuzzyBot.Patrol.PatrolLeft) == 1 && fuzzyBot.readPatrol(fuzzyBot.Patrol.PatrolMiddle) == 0 && fuzzyBot.readPatrol(fuzzyBot.Patrol.PatrolRight) == 0) {
        status_SL = 4
    } else if (fuzzyBot.readPatrol(fuzzyBot.Patrol.PatrolLeft) == 1 && fuzzyBot.readPatrol(fuzzyBot.Patrol.PatrolMiddle) == 0 && fuzzyBot.readPatrol(fuzzyBot.Patrol.PatrolRight) == 1) {
        status_SL = 5
    } else if (fuzzyBot.readPatrol(fuzzyBot.Patrol.PatrolLeft) == 1 && fuzzyBot.readPatrol(fuzzyBot.Patrol.PatrolMiddle) == 1 && fuzzyBot.readPatrol(fuzzyBot.Patrol.PatrolRight) == 0) {
        status_SL = 6
    } else if (fuzzyBot.readPatrol(fuzzyBot.Patrol.PatrolLeft) == 1 && fuzzyBot.readPatrol(fuzzyBot.Patrol.PatrolMiddle) == 1 && fuzzyBot.readPatrol(fuzzyBot.Patrol.PatrolRight) == 1) {
        status_SL = 7
    }
}
let status_SL = 0
let Iniciar = 0
basic.pause(2000)
Camera.Begin(sentry_mode_e.kI2CMode, sengo2_addr_e.ADDR1)
Camera.VisionSetStatus(sengo2_status.Enable, sengo_vision_e.kVisionCard)
basic.showIcon(IconNames.Heart)
let velocidade = 80
basic.forever(function () {
    
})
basic.forever(function () {
    seguidor_linha()
    if (Iniciar == 1) {
        if (status_SL == 0) {
            frente()
        } else if (status_SL == 1) {
            esquerda()
        } else if (status_SL == 3) {
            esquerda_brusca()
        } else if (status_SL == 4) {
            direita()
        } else if (status_SL == 6) {
            direita_brusca()
        }
    } else {
        fuzzyBot.motorStop(fuzzyBot.Motors.All)
    }
})


```

## Passo 11
Acesse a categoria ``||logic:Lógica||``, pegue a condicional ``||logic:se então||``
e insira-a dentro do laço ``||basic:sempre||``. 
```blocks
function esquerda () {
    fuzzyBot.motorRun(fuzzyBot.Motors.M1, fuzzyBot.Dir.CW, 30)
    fuzzyBot.motorRun(fuzzyBot.Motors.M2, fuzzyBot.Dir.CW, 50)
}
input.onButtonPressed(Button.A, function () {
    Iniciar = 0
    basic.showIcon(IconNames.Heart)
})
function esquerda_brusca () {
    fuzzyBot.motorRun(fuzzyBot.Motors.M1, fuzzyBot.Dir.CW, 0)
    fuzzyBot.motorRun(fuzzyBot.Motors.M2, fuzzyBot.Dir.CW, 50)
}
function direita () {
    fuzzyBot.motorRun(fuzzyBot.Motors.M1, fuzzyBot.Dir.CW, 50)
    fuzzyBot.motorRun(fuzzyBot.Motors.M2, fuzzyBot.Dir.CW, 30)
}
input.onButtonPressed(Button.B, function () {
    Iniciar = 1
    basic.showIcon(IconNames.Happy)
})
function frente () {
    fuzzyBot.motorRun(fuzzyBot.Motors.All, fuzzyBot.Dir.CW, 50)
}
function direita_brusca () {
    fuzzyBot.motorRun(fuzzyBot.Motors.M1, fuzzyBot.Dir.CW, 50)
    fuzzyBot.motorRun(fuzzyBot.Motors.M2, fuzzyBot.Dir.CW, 0)
}
function seguidor_linha () {
    if (fuzzyBot.readPatrol(fuzzyBot.Patrol.PatrolLeft) == 0 && fuzzyBot.readPatrol(fuzzyBot.Patrol.PatrolMiddle) == 0 && fuzzyBot.readPatrol(fuzzyBot.Patrol.PatrolRight) == 0) {
        status_SL = 0
    } else if (fuzzyBot.readPatrol(fuzzyBot.Patrol.PatrolLeft) == 0 && fuzzyBot.readPatrol(fuzzyBot.Patrol.PatrolMiddle) == 0 && fuzzyBot.readPatrol(fuzzyBot.Patrol.PatrolRight) == 1) {
        status_SL = 1
    } else if (fuzzyBot.readPatrol(fuzzyBot.Patrol.PatrolLeft) == 0 && fuzzyBot.readPatrol(fuzzyBot.Patrol.PatrolMiddle) == 1 && fuzzyBot.readPatrol(fuzzyBot.Patrol.PatrolRight) == 0) {
        status_SL = 2
    } else if (fuzzyBot.readPatrol(fuzzyBot.Patrol.PatrolLeft) == 0 && fuzzyBot.readPatrol(fuzzyBot.Patrol.PatrolMiddle) == 1 && fuzzyBot.readPatrol(fuzzyBot.Patrol.PatrolRight) == 1) {
        status_SL = 3
    } else if (fuzzyBot.readPatrol(fuzzyBot.Patrol.PatrolLeft) == 1 && fuzzyBot.readPatrol(fuzzyBot.Patrol.PatrolMiddle) == 0 && fuzzyBot.readPatrol(fuzzyBot.Patrol.PatrolRight) == 0) {
        status_SL = 4
    } else if (fuzzyBot.readPatrol(fuzzyBot.Patrol.PatrolLeft) == 1 && fuzzyBot.readPatrol(fuzzyBot.Patrol.PatrolMiddle) == 0 && fuzzyBot.readPatrol(fuzzyBot.Patrol.PatrolRight) == 1) {
        status_SL = 5
    } else if (fuzzyBot.readPatrol(fuzzyBot.Patrol.PatrolLeft) == 1 && fuzzyBot.readPatrol(fuzzyBot.Patrol.PatrolMiddle) == 1 && fuzzyBot.readPatrol(fuzzyBot.Patrol.PatrolRight) == 0) {
        status_SL = 6
    } else if (fuzzyBot.readPatrol(fuzzyBot.Patrol.PatrolLeft) == 1 && fuzzyBot.readPatrol(fuzzyBot.Patrol.PatrolMiddle) == 1 && fuzzyBot.readPatrol(fuzzyBot.Patrol.PatrolRight) == 1) {
        status_SL = 7
    }
}
let status_SL = 0
let Iniciar = 0
basic.pause(2000)
Camera.Begin(sentry_mode_e.kI2CMode, sengo2_addr_e.ADDR1)
Camera.VisionSetStatus(sengo2_status.Enable, sengo_vision_e.kVisionCard)
basic.showIcon(IconNames.Heart)
let velocidade = 80
basic.forever(function () {
    if (true) {
    	
    }
})
basic.forever(function () {
    seguidor_linha()
    if (Iniciar == 1) {
        if (status_SL == 0) {
            frente()
        } else if (status_SL == 1) {
            esquerda()
        } else if (status_SL == 3) {
            esquerda_brusca()
        } else if (status_SL == 4) {
            direita()
        } else if (status_SL == 6) {
            direita_brusca()
        }
    } else {
        fuzzyBot.motorStop(fuzzyBot.Motors.All)
    }
})
```

## Passo 12
Volte ao menu ``||logic:Lógica||``, pegue o comparador ``||logic:0 = 0||``
e substitua a condição **verdadeiro** da condicional.

```blocks
function esquerda () {
    fuzzyBot.motorRun(fuzzyBot.Motors.M1, fuzzyBot.Dir.CW, 30)
    fuzzyBot.motorRun(fuzzyBot.Motors.M2, fuzzyBot.Dir.CW, 50)
}
input.onButtonPressed(Button.A, function () {
    Iniciar = 0
    basic.showIcon(IconNames.Heart)
})
function esquerda_brusca () {
    fuzzyBot.motorRun(fuzzyBot.Motors.M1, fuzzyBot.Dir.CW, 0)
    fuzzyBot.motorRun(fuzzyBot.Motors.M2, fuzzyBot.Dir.CW, 50)
}
function direita () {
    fuzzyBot.motorRun(fuzzyBot.Motors.M1, fuzzyBot.Dir.CW, 50)
    fuzzyBot.motorRun(fuzzyBot.Motors.M2, fuzzyBot.Dir.CW, 30)
}
input.onButtonPressed(Button.B, function () {
    Iniciar = 1
    basic.showIcon(IconNames.Happy)
})
function frente () {
    fuzzyBot.motorRun(fuzzyBot.Motors.All, fuzzyBot.Dir.CW, 50)
}
function direita_brusca () {
    fuzzyBot.motorRun(fuzzyBot.Motors.M1, fuzzyBot.Dir.CW, 50)
    fuzzyBot.motorRun(fuzzyBot.Motors.M2, fuzzyBot.Dir.CW, 0)
}
function seguidor_linha () {
    if (fuzzyBot.readPatrol(fuzzyBot.Patrol.PatrolLeft) == 0 && fuzzyBot.readPatrol(fuzzyBot.Patrol.PatrolMiddle) == 0 && fuzzyBot.readPatrol(fuzzyBot.Patrol.PatrolRight) == 0) {
        status_SL = 0
    } else if (fuzzyBot.readPatrol(fuzzyBot.Patrol.PatrolLeft) == 0 && fuzzyBot.readPatrol(fuzzyBot.Patrol.PatrolMiddle) == 0 && fuzzyBot.readPatrol(fuzzyBot.Patrol.PatrolRight) == 1) {
        status_SL = 1
    } else if (fuzzyBot.readPatrol(fuzzyBot.Patrol.PatrolLeft) == 0 && fuzzyBot.readPatrol(fuzzyBot.Patrol.PatrolMiddle) == 1 && fuzzyBot.readPatrol(fuzzyBot.Patrol.PatrolRight) == 0) {
        status_SL = 2
    } else if (fuzzyBot.readPatrol(fuzzyBot.Patrol.PatrolLeft) == 0 && fuzzyBot.readPatrol(fuzzyBot.Patrol.PatrolMiddle) == 1 && fuzzyBot.readPatrol(fuzzyBot.Patrol.PatrolRight) == 1) {
        status_SL = 3
    } else if (fuzzyBot.readPatrol(fuzzyBot.Patrol.PatrolLeft) == 1 && fuzzyBot.readPatrol(fuzzyBot.Patrol.PatrolMiddle) == 0 && fuzzyBot.readPatrol(fuzzyBot.Patrol.PatrolRight) == 0) {
        status_SL = 4
    } else if (fuzzyBot.readPatrol(fuzzyBot.Patrol.PatrolLeft) == 1 && fuzzyBot.readPatrol(fuzzyBot.Patrol.PatrolMiddle) == 0 && fuzzyBot.readPatrol(fuzzyBot.Patrol.PatrolRight) == 1) {
        status_SL = 5
    } else if (fuzzyBot.readPatrol(fuzzyBot.Patrol.PatrolLeft) == 1 && fuzzyBot.readPatrol(fuzzyBot.Patrol.PatrolMiddle) == 1 && fuzzyBot.readPatrol(fuzzyBot.Patrol.PatrolRight) == 0) {
        status_SL = 6
    } else if (fuzzyBot.readPatrol(fuzzyBot.Patrol.PatrolLeft) == 1 && fuzzyBot.readPatrol(fuzzyBot.Patrol.PatrolMiddle) == 1 && fuzzyBot.readPatrol(fuzzyBot.Patrol.PatrolRight) == 1) {
        status_SL = 7
    }
}
let status_SL = 0
let Iniciar = 0
basic.pause(2000)
Camera.Begin(sentry_mode_e.kI2CMode, sengo2_addr_e.ADDR1)
Camera.VisionSetStatus(sengo2_status.Enable, sengo_vision_e.kVisionCard)
basic.showIcon(IconNames.Heart)
let velocidade = 80
basic.forever(function () {
    if (0==0) {
    	
    }
})
basic.forever(function () {
    seguidor_linha()
    if (Iniciar == 1) {
        if (status_SL == 0) {
            frente()
        } else if (status_SL == 1) {
            esquerda()
        } else if (status_SL == 3) {
            esquerda_brusca()
        } else if (status_SL == 4) {
            direita()
        } else if (status_SL == 6) {
            direita_brusca()
        }
    } else {
        fuzzyBot.motorStop(fuzzyBot.Motors.All)
    }
})

```

## Passo 13
Agora atualize os campos do comparador. Vá até a aba ``||variables:Variáveis||``,
clique no bloco ``||variables:Iniciar||`` e troque o primeiro **0** do comparador. 

Altere o segundo campo para **1**. Assim garantimos que a leitura das cartas só comece depois de acionarmos o botão.

```blocks
function esquerda () {
    fuzzyBot.motorRun(fuzzyBot.Motors.M1, fuzzyBot.Dir.CW, 30)
    fuzzyBot.motorRun(fuzzyBot.Motors.M2, fuzzyBot.Dir.CW, 50)
}
input.onButtonPressed(Button.A, function () {
    Iniciar = 0
    basic.showIcon(IconNames.Heart)
})
function esquerda_brusca () {
    fuzzyBot.motorRun(fuzzyBot.Motors.M1, fuzzyBot.Dir.CW, 0)
    fuzzyBot.motorRun(fuzzyBot.Motors.M2, fuzzyBot.Dir.CW, 50)
}
function direita () {
    fuzzyBot.motorRun(fuzzyBot.Motors.M1, fuzzyBot.Dir.CW, 50)
    fuzzyBot.motorRun(fuzzyBot.Motors.M2, fuzzyBot.Dir.CW, 30)
}
input.onButtonPressed(Button.B, function () {
    Iniciar = 1
    basic.showIcon(IconNames.Happy)
})
function frente () {
    fuzzyBot.motorRun(fuzzyBot.Motors.All, fuzzyBot.Dir.CW, 50)
}
function direita_brusca () {
    fuzzyBot.motorRun(fuzzyBot.Motors.M1, fuzzyBot.Dir.CW, 50)
    fuzzyBot.motorRun(fuzzyBot.Motors.M2, fuzzyBot.Dir.CW, 0)
}
function seguidor_linha () {
    if (fuzzyBot.readPatrol(fuzzyBot.Patrol.PatrolLeft) == 0 && fuzzyBot.readPatrol(fuzzyBot.Patrol.PatrolMiddle) == 0 && fuzzyBot.readPatrol(fuzzyBot.Patrol.PatrolRight) == 0) {
        status_SL = 0
    } else if (fuzzyBot.readPatrol(fuzzyBot.Patrol.PatrolLeft) == 0 && fuzzyBot.readPatrol(fuzzyBot.Patrol.PatrolMiddle) == 0 && fuzzyBot.readPatrol(fuzzyBot.Patrol.PatrolRight) == 1) {
        status_SL = 1
    } else if (fuzzyBot.readPatrol(fuzzyBot.Patrol.PatrolLeft) == 0 && fuzzyBot.readPatrol(fuzzyBot.Patrol.PatrolMiddle) == 1 && fuzzyBot.readPatrol(fuzzyBot.Patrol.PatrolRight) == 0) {
        status_SL = 2
    } else if (fuzzyBot.readPatrol(fuzzyBot.Patrol.PatrolLeft) == 0 && fuzzyBot.readPatrol(fuzzyBot.Patrol.PatrolMiddle) == 1 && fuzzyBot.readPatrol(fuzzyBot.Patrol.PatrolRight) == 1) {
        status_SL = 3
    } else if (fuzzyBot.readPatrol(fuzzyBot.Patrol.PatrolLeft) == 1 && fuzzyBot.readPatrol(fuzzyBot.Patrol.PatrolMiddle) == 0 && fuzzyBot.readPatrol(fuzzyBot.Patrol.PatrolRight) == 0) {
        status_SL = 4
    } else if (fuzzyBot.readPatrol(fuzzyBot.Patrol.PatrolLeft) == 1 && fuzzyBot.readPatrol(fuzzyBot.Patrol.PatrolMiddle) == 0 && fuzzyBot.readPatrol(fuzzyBot.Patrol.PatrolRight) == 1) {
        status_SL = 5
    } else if (fuzzyBot.readPatrol(fuzzyBot.Patrol.PatrolLeft) == 1 && fuzzyBot.readPatrol(fuzzyBot.Patrol.PatrolMiddle) == 1 && fuzzyBot.readPatrol(fuzzyBot.Patrol.PatrolRight) == 0) {
        status_SL = 6
    } else if (fuzzyBot.readPatrol(fuzzyBot.Patrol.PatrolLeft) == 1 && fuzzyBot.readPatrol(fuzzyBot.Patrol.PatrolMiddle) == 1 && fuzzyBot.readPatrol(fuzzyBot.Patrol.PatrolRight) == 1) {
        status_SL = 7
    }
}
let status_SL = 0
let Iniciar = 0
basic.pause(2000)
Camera.Begin(sentry_mode_e.kI2CMode, sengo2_addr_e.ADDR1)
Camera.VisionSetStatus(sengo2_status.Enable, sengo_vision_e.kVisionCard)
basic.showIcon(IconNames.Heart)
let velocidade = 80
basic.forever(function () {
    if (Iniciar == 1) {
    
    }
})
basic.forever(function () {
    seguidor_linha()
    if (Iniciar == 1) {
        if (status_SL == 0) {
            frente()
        } else if (status_SL == 1) {
            esquerda()
        } else if (status_SL == 3) {
            esquerda_brusca()
        } else if (status_SL == 4) {
            direita()
        } else if (status_SL == 6) {
            direita_brusca()
        }
    } else {
        fuzzyBot.motorStop(fuzzyBot.Motors.All)
    }
})
```

## Passo 14
Acesse a categoria ``||logic:Lógica||``, pegue a condicional ``||logic:se então||``
e insira-a dentro da condicional criada nos passos anteriores. 

```blocks
function esquerda () {
    fuzzyBot.motorRun(fuzzyBot.Motors.M1, fuzzyBot.Dir.CW, 30)
    fuzzyBot.motorRun(fuzzyBot.Motors.M2, fuzzyBot.Dir.CW, 50)
}
input.onButtonPressed(Button.A, function () {
    Iniciar = 0
    basic.showIcon(IconNames.Heart)
})
function esquerda_brusca () {
    fuzzyBot.motorRun(fuzzyBot.Motors.M1, fuzzyBot.Dir.CW, 0)
    fuzzyBot.motorRun(fuzzyBot.Motors.M2, fuzzyBot.Dir.CW, 50)
}
function direita () {
    fuzzyBot.motorRun(fuzzyBot.Motors.M1, fuzzyBot.Dir.CW, 50)
    fuzzyBot.motorRun(fuzzyBot.Motors.M2, fuzzyBot.Dir.CW, 30)
}
input.onButtonPressed(Button.B, function () {
    Iniciar = 1
    basic.showIcon(IconNames.Happy)
})
function frente () {
    fuzzyBot.motorRun(fuzzyBot.Motors.All, fuzzyBot.Dir.CW, 50)
}
function direita_brusca () {
    fuzzyBot.motorRun(fuzzyBot.Motors.M1, fuzzyBot.Dir.CW, 50)
    fuzzyBot.motorRun(fuzzyBot.Motors.M2, fuzzyBot.Dir.CW, 0)
}
function seguidor_linha () {
    if (fuzzyBot.readPatrol(fuzzyBot.Patrol.PatrolLeft) == 0 && fuzzyBot.readPatrol(fuzzyBot.Patrol.PatrolMiddle) == 0 && fuzzyBot.readPatrol(fuzzyBot.Patrol.PatrolRight) == 0) {
        status_SL = 0
    } else if (fuzzyBot.readPatrol(fuzzyBot.Patrol.PatrolLeft) == 0 && fuzzyBot.readPatrol(fuzzyBot.Patrol.PatrolMiddle) == 0 && fuzzyBot.readPatrol(fuzzyBot.Patrol.PatrolRight) == 1) {
        status_SL = 1
    } else if (fuzzyBot.readPatrol(fuzzyBot.Patrol.PatrolLeft) == 0 && fuzzyBot.readPatrol(fuzzyBot.Patrol.PatrolMiddle) == 1 && fuzzyBot.readPatrol(fuzzyBot.Patrol.PatrolRight) == 0) {
        status_SL = 2
    } else if (fuzzyBot.readPatrol(fuzzyBot.Patrol.PatrolLeft) == 0 && fuzzyBot.readPatrol(fuzzyBot.Patrol.PatrolMiddle) == 1 && fuzzyBot.readPatrol(fuzzyBot.Patrol.PatrolRight) == 1) {
        status_SL = 3
    } else if (fuzzyBot.readPatrol(fuzzyBot.Patrol.PatrolLeft) == 1 && fuzzyBot.readPatrol(fuzzyBot.Patrol.PatrolMiddle) == 0 && fuzzyBot.readPatrol(fuzzyBot.Patrol.PatrolRight) == 0) {
        status_SL = 4
    } else if (fuzzyBot.readPatrol(fuzzyBot.Patrol.PatrolLeft) == 1 && fuzzyBot.readPatrol(fuzzyBot.Patrol.PatrolMiddle) == 0 && fuzzyBot.readPatrol(fuzzyBot.Patrol.PatrolRight) == 1) {
        status_SL = 5
    } else if (fuzzyBot.readPatrol(fuzzyBot.Patrol.PatrolLeft) == 1 && fuzzyBot.readPatrol(fuzzyBot.Patrol.PatrolMiddle) == 1 && fuzzyBot.readPatrol(fuzzyBot.Patrol.PatrolRight) == 0) {
        status_SL = 6
    } else if (fuzzyBot.readPatrol(fuzzyBot.Patrol.PatrolLeft) == 1 && fuzzyBot.readPatrol(fuzzyBot.Patrol.PatrolMiddle) == 1 && fuzzyBot.readPatrol(fuzzyBot.Patrol.PatrolRight) == 1) {
        status_SL = 7
    }
}
let status_SL = 0
let Iniciar = 0
basic.pause(2000)
Camera.Begin(sentry_mode_e.kI2CMode, sengo2_addr_e.ADDR1)
Camera.VisionSetStatus(sengo2_status.Enable, sengo_vision_e.kVisionCard)
basic.showIcon(IconNames.Heart)
let velocidade = 80
basic.forever(function () {
    if (Iniciar == 1) {
        if (true) {
        	
        }
    }
})
basic.forever(function () {
    seguidor_linha()
    if (Iniciar == 1) {
        if (status_SL == 0) {
            frente()
        } else if (status_SL == 1) {
            esquerda()
        } else if (status_SL == 3) {
            esquerda_brusca()
        } else if (status_SL == 4) {
            direita()
        } else if (status_SL == 6) {
            direita_brusca()
        }
    } else {
        fuzzyBot.motorStop(fuzzyBot.Motors.All)
    }
})

```

## Passo 15
Ainda no menu ``||logic:Lógica||`` , pegue o bloco comparador ``||logic:0 < 0||`` e substitua a condição **verdadeiro**.

```blocks
function esquerda () {
    fuzzyBot.motorRun(fuzzyBot.Motors.M1, fuzzyBot.Dir.CW, 30)
    fuzzyBot.motorRun(fuzzyBot.Motors.M2, fuzzyBot.Dir.CW, 50)
}
input.onButtonPressed(Button.A, function () {
    Iniciar = 0
    basic.showIcon(IconNames.Heart)
})
function esquerda_brusca () {
    fuzzyBot.motorRun(fuzzyBot.Motors.M1, fuzzyBot.Dir.CW, 0)
    fuzzyBot.motorRun(fuzzyBot.Motors.M2, fuzzyBot.Dir.CW, 50)
}
function direita () {
    fuzzyBot.motorRun(fuzzyBot.Motors.M1, fuzzyBot.Dir.CW, 50)
    fuzzyBot.motorRun(fuzzyBot.Motors.M2, fuzzyBot.Dir.CW, 30)
}
input.onButtonPressed(Button.B, function () {
    Iniciar = 1
    basic.showIcon(IconNames.Happy)
})
function frente () {
    fuzzyBot.motorRun(fuzzyBot.Motors.All, fuzzyBot.Dir.CW, 50)
}
function direita_brusca () {
    fuzzyBot.motorRun(fuzzyBot.Motors.M1, fuzzyBot.Dir.CW, 50)
    fuzzyBot.motorRun(fuzzyBot.Motors.M2, fuzzyBot.Dir.CW, 0)
}
function seguidor_linha () {
    if (fuzzyBot.readPatrol(fuzzyBot.Patrol.PatrolLeft) == 0 && fuzzyBot.readPatrol(fuzzyBot.Patrol.PatrolMiddle) == 0 && fuzzyBot.readPatrol(fuzzyBot.Patrol.PatrolRight) == 0) {
        status_SL = 0
    } else if (fuzzyBot.readPatrol(fuzzyBot.Patrol.PatrolLeft) == 0 && fuzzyBot.readPatrol(fuzzyBot.Patrol.PatrolMiddle) == 0 && fuzzyBot.readPatrol(fuzzyBot.Patrol.PatrolRight) == 1) {
        status_SL = 1
    } else if (fuzzyBot.readPatrol(fuzzyBot.Patrol.PatrolLeft) == 0 && fuzzyBot.readPatrol(fuzzyBot.Patrol.PatrolMiddle) == 1 && fuzzyBot.readPatrol(fuzzyBot.Patrol.PatrolRight) == 0) {
        status_SL = 2
    } else if (fuzzyBot.readPatrol(fuzzyBot.Patrol.PatrolLeft) == 0 && fuzzyBot.readPatrol(fuzzyBot.Patrol.PatrolMiddle) == 1 && fuzzyBot.readPatrol(fuzzyBot.Patrol.PatrolRight) == 1) {
        status_SL = 3
    } else if (fuzzyBot.readPatrol(fuzzyBot.Patrol.PatrolLeft) == 1 && fuzzyBot.readPatrol(fuzzyBot.Patrol.PatrolMiddle) == 0 && fuzzyBot.readPatrol(fuzzyBot.Patrol.PatrolRight) == 0) {
        status_SL = 4
    } else if (fuzzyBot.readPatrol(fuzzyBot.Patrol.PatrolLeft) == 1 && fuzzyBot.readPatrol(fuzzyBot.Patrol.PatrolMiddle) == 0 && fuzzyBot.readPatrol(fuzzyBot.Patrol.PatrolRight) == 1) {
        status_SL = 5
    } else if (fuzzyBot.readPatrol(fuzzyBot.Patrol.PatrolLeft) == 1 && fuzzyBot.readPatrol(fuzzyBot.Patrol.PatrolMiddle) == 1 && fuzzyBot.readPatrol(fuzzyBot.Patrol.PatrolRight) == 0) {
        status_SL = 6
    } else if (fuzzyBot.readPatrol(fuzzyBot.Patrol.PatrolLeft) == 1 && fuzzyBot.readPatrol(fuzzyBot.Patrol.PatrolMiddle) == 1 && fuzzyBot.readPatrol(fuzzyBot.Patrol.PatrolRight) == 1) {
        status_SL = 7
    }
}
let status_SL = 0
let Iniciar = 0
basic.pause(2000)
Camera.Begin(sentry_mode_e.kI2CMode, sengo2_addr_e.ADDR1)
Camera.VisionSetStatus(sengo2_status.Enable, sengo_vision_e.kVisionCard)
basic.showIcon(IconNames.Heart)
let velocidade = 80
basic.forever(function () {
    if (Iniciar == 1) {
        if (0 < 0) {
        	
        }
    }
})
basic.forever(function () {
    seguidor_linha()
    if (Iniciar == 1) {
        if (status_SL == 0) {
            frente()
        } else if (status_SL == 1) {
            esquerda()
        } else if (status_SL == 3) {
            esquerda_brusca()
        } else if (status_SL == 4) {
            direita()
        } else if (status_SL == 6) {
            direita_brusca()
        }
    } else {
        fuzzyBot.motorStop(fuzzyBot.Motors.All)
    }
})

```

## Passo 16
Modifique o sinal do comparador de **<** para **>**. Em seguida, volte à aba do ``||Camera:Sensor Câmera||``,
na seção de operações, e use o bloco verde de bordas arredondadas ``||Camera:Resultados detectados no modo Cor||``
no primeiro campo do comparador, substituindo o valor **0**. Altere o modo **cor** para o modo **cartão**.

```blocks
function esquerda () {
    fuzzyBot.motorRun(fuzzyBot.Motors.M1, fuzzyBot.Dir.CW, 30)
    fuzzyBot.motorRun(fuzzyBot.Motors.M2, fuzzyBot.Dir.CW, 50)
}
input.onButtonPressed(Button.A, function () {
    Iniciar = 0
    basic.showIcon(IconNames.Heart)
})
function esquerda_brusca () {
    fuzzyBot.motorRun(fuzzyBot.Motors.M1, fuzzyBot.Dir.CW, 0)
    fuzzyBot.motorRun(fuzzyBot.Motors.M2, fuzzyBot.Dir.CW, 50)
}
function direita () {
    fuzzyBot.motorRun(fuzzyBot.Motors.M1, fuzzyBot.Dir.CW, 50)
    fuzzyBot.motorRun(fuzzyBot.Motors.M2, fuzzyBot.Dir.CW, 30)
}
input.onButtonPressed(Button.B, function () {
    Iniciar = 1
    basic.showIcon(IconNames.Happy)
})
function frente () {
    fuzzyBot.motorRun(fuzzyBot.Motors.All, fuzzyBot.Dir.CW, 50)
}
function direita_brusca () {
    fuzzyBot.motorRun(fuzzyBot.Motors.M1, fuzzyBot.Dir.CW, 50)
    fuzzyBot.motorRun(fuzzyBot.Motors.M2, fuzzyBot.Dir.CW, 0)
}
function seguidor_linha () {
    if (fuzzyBot.readPatrol(fuzzyBot.Patrol.PatrolLeft) == 0 && fuzzyBot.readPatrol(fuzzyBot.Patrol.PatrolMiddle) == 0 && fuzzyBot.readPatrol(fuzzyBot.Patrol.PatrolRight) == 0) {
        status_SL = 0
    } else if (fuzzyBot.readPatrol(fuzzyBot.Patrol.PatrolLeft) == 0 && fuzzyBot.readPatrol(fuzzyBot.Patrol.PatrolMiddle) == 0 && fuzzyBot.readPatrol(fuzzyBot.Patrol.PatrolRight) == 1) {
        status_SL = 1
    } else if (fuzzyBot.readPatrol(fuzzyBot.Patrol.PatrolLeft) == 0 && fuzzyBot.readPatrol(fuzzyBot.Patrol.PatrolMiddle) == 1 && fuzzyBot.readPatrol(fuzzyBot.Patrol.PatrolRight) == 0) {
        status_SL = 2
    } else if (fuzzyBot.readPatrol(fuzzyBot.Patrol.PatrolLeft) == 0 && fuzzyBot.readPatrol(fuzzyBot.Patrol.PatrolMiddle) == 1 && fuzzyBot.readPatrol(fuzzyBot.Patrol.PatrolRight) == 1) {
        status_SL = 3
    } else if (fuzzyBot.readPatrol(fuzzyBot.Patrol.PatrolLeft) == 1 && fuzzyBot.readPatrol(fuzzyBot.Patrol.PatrolMiddle) == 0 && fuzzyBot.readPatrol(fuzzyBot.Patrol.PatrolRight) == 0) {
        status_SL = 4
    } else if (fuzzyBot.readPatrol(fuzzyBot.Patrol.PatrolLeft) == 1 && fuzzyBot.readPatrol(fuzzyBot.Patrol.PatrolMiddle) == 0 && fuzzyBot.readPatrol(fuzzyBot.Patrol.PatrolRight) == 1) {
        status_SL = 5
    } else if (fuzzyBot.readPatrol(fuzzyBot.Patrol.PatrolLeft) == 1 && fuzzyBot.readPatrol(fuzzyBot.Patrol.PatrolMiddle) == 1 && fuzzyBot.readPatrol(fuzzyBot.Patrol.PatrolRight) == 0) {
        status_SL = 6
    } else if (fuzzyBot.readPatrol(fuzzyBot.Patrol.PatrolLeft) == 1 && fuzzyBot.readPatrol(fuzzyBot.Patrol.PatrolMiddle) == 1 && fuzzyBot.readPatrol(fuzzyBot.Patrol.PatrolRight) == 1) {
        status_SL = 7
    }
}
let status_SL = 0
let Iniciar = 0
basic.pause(2000)
Camera.Begin(sentry_mode_e.kI2CMode, sengo2_addr_e.ADDR1)
Camera.VisionSetStatus(sengo2_status.Enable, sengo_vision_e.kVisionCard)
basic.showIcon(IconNames.Heart)
let velocidade = 80
basic.forever(function () {
    if (Iniciar == 1) {
        if (Camera.Detected(sengo_vision_e.kVisionCard) > 0) {
        	
        }
    }
})
basic.forever(function () {
    seguidor_linha()
    if (Iniciar == 1) {
        if (status_SL == 0) {
            frente()
        } else if (status_SL == 1) {
            esquerda()
        } else if (status_SL == 3) {
            esquerda_brusca()
        } else if (status_SL == 4) {
            direita()
        } else if (status_SL == 6) {
            direita_brusca()
        }
    } else {
        fuzzyBot.motorStop(fuzzyBot.Motors.All)
    }
})

```

## Passo 17
Dentro do ``||logic:então||``, insira uma nova condição ``||logic:se então||``.
```blocks
function esquerda () {
    fuzzyBot.motorRun(fuzzyBot.Motors.M1, fuzzyBot.Dir.CW, 30)
    fuzzyBot.motorRun(fuzzyBot.Motors.M2, fuzzyBot.Dir.CW, 50)
}
input.onButtonPressed(Button.A, function () {
    Iniciar = 0
    basic.showIcon(IconNames.Heart)
})
function esquerda_brusca () {
    fuzzyBot.motorRun(fuzzyBot.Motors.M1, fuzzyBot.Dir.CW, 0)
    fuzzyBot.motorRun(fuzzyBot.Motors.M2, fuzzyBot.Dir.CW, 50)
}
function direita () {
    fuzzyBot.motorRun(fuzzyBot.Motors.M1, fuzzyBot.Dir.CW, 50)
    fuzzyBot.motorRun(fuzzyBot.Motors.M2, fuzzyBot.Dir.CW, 30)
}
input.onButtonPressed(Button.B, function () {
    Iniciar = 1
    basic.showIcon(IconNames.Happy)
})
function frente () {
    fuzzyBot.motorRun(fuzzyBot.Motors.All, fuzzyBot.Dir.CW, 50)
}
function direita_brusca () {
    fuzzyBot.motorRun(fuzzyBot.Motors.M1, fuzzyBot.Dir.CW, 50)
    fuzzyBot.motorRun(fuzzyBot.Motors.M2, fuzzyBot.Dir.CW, 0)
}
function seguidor_linha () {
    if (fuzzyBot.readPatrol(fuzzyBot.Patrol.PatrolLeft) == 0 && fuzzyBot.readPatrol(fuzzyBot.Patrol.PatrolMiddle) == 0 && fuzzyBot.readPatrol(fuzzyBot.Patrol.PatrolRight) == 0) {
        status_SL = 0
    } else if (fuzzyBot.readPatrol(fuzzyBot.Patrol.PatrolLeft) == 0 && fuzzyBot.readPatrol(fuzzyBot.Patrol.PatrolMiddle) == 0 && fuzzyBot.readPatrol(fuzzyBot.Patrol.PatrolRight) == 1) {
        status_SL = 1
    } else if (fuzzyBot.readPatrol(fuzzyBot.Patrol.PatrolLeft) == 0 && fuzzyBot.readPatrol(fuzzyBot.Patrol.PatrolMiddle) == 1 && fuzzyBot.readPatrol(fuzzyBot.Patrol.PatrolRight) == 0) {
        status_SL = 2
    } else if (fuzzyBot.readPatrol(fuzzyBot.Patrol.PatrolLeft) == 0 && fuzzyBot.readPatrol(fuzzyBot.Patrol.PatrolMiddle) == 1 && fuzzyBot.readPatrol(fuzzyBot.Patrol.PatrolRight) == 1) {
        status_SL = 3
    } else if (fuzzyBot.readPatrol(fuzzyBot.Patrol.PatrolLeft) == 1 && fuzzyBot.readPatrol(fuzzyBot.Patrol.PatrolMiddle) == 0 && fuzzyBot.readPatrol(fuzzyBot.Patrol.PatrolRight) == 0) {
        status_SL = 4
    } else if (fuzzyBot.readPatrol(fuzzyBot.Patrol.PatrolLeft) == 1 && fuzzyBot.readPatrol(fuzzyBot.Patrol.PatrolMiddle) == 0 && fuzzyBot.readPatrol(fuzzyBot.Patrol.PatrolRight) == 1) {
        status_SL = 5
    } else if (fuzzyBot.readPatrol(fuzzyBot.Patrol.PatrolLeft) == 1 && fuzzyBot.readPatrol(fuzzyBot.Patrol.PatrolMiddle) == 1 && fuzzyBot.readPatrol(fuzzyBot.Patrol.PatrolRight) == 0) {
        status_SL = 6
    } else if (fuzzyBot.readPatrol(fuzzyBot.Patrol.PatrolLeft) == 1 && fuzzyBot.readPatrol(fuzzyBot.Patrol.PatrolMiddle) == 1 && fuzzyBot.readPatrol(fuzzyBot.Patrol.PatrolRight) == 1) {
        status_SL = 7
    }
}
let status_SL = 0
let Iniciar = 0
basic.pause(2000)
Camera.Begin(sentry_mode_e.kI2CMode, sengo2_addr_e.ADDR1)
Camera.VisionSetStatus(sengo2_status.Enable, sengo_vision_e.kVisionCard)
basic.showIcon(IconNames.Heart)
let velocidade = 80
basic.forever(function () {
    if (Iniciar == 1) {
        if (Camera.Detected(sengo_vision_e.kVisionCard) > 0) {
            if (true) {
            	
            }
        }
    }
})
basic.forever(function () {
    seguidor_linha()
    if (Iniciar == 1) {
        if (status_SL == 0) {
            frente()
        } else if (status_SL == 1) {
            esquerda()
        } else if (status_SL == 3) {
            esquerda_brusca()
        } else if (status_SL == 4) {
            direita()
        } else if (status_SL == 6) {
            direita_brusca()
        }
    } else {
        fuzzyBot.motorStop(fuzzyBot.Motors.All)
    }
})

```

## Passo 18
Volte à categoria do ``||Camera:Sensor Câmera||``,
na seção de operações, e use o bloco verde de bordas triangulares ``||Camera:Cartão frente detectado do resultado 1||``
para substituir o **verdadeiro** deste novo laço ``||logic:se então||``.
Modifique o cartão **frente** para **velocidade 60**.
```blocks
function esquerda () {
    fuzzyBot.motorRun(fuzzyBot.Motors.M1, fuzzyBot.Dir.CW, 30)
    fuzzyBot.motorRun(fuzzyBot.Motors.M2, fuzzyBot.Dir.CW, 50)
}
input.onButtonPressed(Button.A, function () {
    Iniciar = 0
    basic.showIcon(IconNames.Heart)
})
function esquerda_brusca () {
    fuzzyBot.motorRun(fuzzyBot.Motors.M1, fuzzyBot.Dir.CW, 0)
    fuzzyBot.motorRun(fuzzyBot.Motors.M2, fuzzyBot.Dir.CW, 50)
}
function direita () {
    fuzzyBot.motorRun(fuzzyBot.Motors.M1, fuzzyBot.Dir.CW, 50)
    fuzzyBot.motorRun(fuzzyBot.Motors.M2, fuzzyBot.Dir.CW, 30)
}
input.onButtonPressed(Button.B, function () {
    Iniciar = 1
    basic.showIcon(IconNames.Happy)
})
function frente () {
    fuzzyBot.motorRun(fuzzyBot.Motors.All, fuzzyBot.Dir.CW, 50)
}
function direita_brusca () {
    fuzzyBot.motorRun(fuzzyBot.Motors.M1, fuzzyBot.Dir.CW, 50)
    fuzzyBot.motorRun(fuzzyBot.Motors.M2, fuzzyBot.Dir.CW, 0)
}
function seguidor_linha () {
    if (fuzzyBot.readPatrol(fuzzyBot.Patrol.PatrolLeft) == 0 && fuzzyBot.readPatrol(fuzzyBot.Patrol.PatrolMiddle) == 0 && fuzzyBot.readPatrol(fuzzyBot.Patrol.PatrolRight) == 0) {
        status_SL = 0
    } else if (fuzzyBot.readPatrol(fuzzyBot.Patrol.PatrolLeft) == 0 && fuzzyBot.readPatrol(fuzzyBot.Patrol.PatrolMiddle) == 0 && fuzzyBot.readPatrol(fuzzyBot.Patrol.PatrolRight) == 1) {
        status_SL = 1
    } else if (fuzzyBot.readPatrol(fuzzyBot.Patrol.PatrolLeft) == 0 && fuzzyBot.readPatrol(fuzzyBot.Patrol.PatrolMiddle) == 1 && fuzzyBot.readPatrol(fuzzyBot.Patrol.PatrolRight) == 0) {
        status_SL = 2
    } else if (fuzzyBot.readPatrol(fuzzyBot.Patrol.PatrolLeft) == 0 && fuzzyBot.readPatrol(fuzzyBot.Patrol.PatrolMiddle) == 1 && fuzzyBot.readPatrol(fuzzyBot.Patrol.PatrolRight) == 1) {
        status_SL = 3
    } else if (fuzzyBot.readPatrol(fuzzyBot.Patrol.PatrolLeft) == 1 && fuzzyBot.readPatrol(fuzzyBot.Patrol.PatrolMiddle) == 0 && fuzzyBot.readPatrol(fuzzyBot.Patrol.PatrolRight) == 0) {
        status_SL = 4
    } else if (fuzzyBot.readPatrol(fuzzyBot.Patrol.PatrolLeft) == 1 && fuzzyBot.readPatrol(fuzzyBot.Patrol.PatrolMiddle) == 0 && fuzzyBot.readPatrol(fuzzyBot.Patrol.PatrolRight) == 1) {
        status_SL = 5
    } else if (fuzzyBot.readPatrol(fuzzyBot.Patrol.PatrolLeft) == 1 && fuzzyBot.readPatrol(fuzzyBot.Patrol.PatrolMiddle) == 1 && fuzzyBot.readPatrol(fuzzyBot.Patrol.PatrolRight) == 0) {
        status_SL = 6
    } else if (fuzzyBot.readPatrol(fuzzyBot.Patrol.PatrolLeft) == 1 && fuzzyBot.readPatrol(fuzzyBot.Patrol.PatrolMiddle) == 1 && fuzzyBot.readPatrol(fuzzyBot.Patrol.PatrolRight) == 1) {
        status_SL = 7
    }
}
let status_SL = 0
let Iniciar = 0
basic.pause(2000)
Camera.Begin(sentry_mode_e.kI2CMode, sengo2_addr_e.ADDR1)
Camera.VisionSetStatus(sengo2_status.Enable, sengo_vision_e.kVisionCard)
basic.showIcon(IconNames.Heart)
let velocidade = 80
basic.forever(function () {
    if (Iniciar == 1) {
        if (Camera.Detected(sengo_vision_e.kVisionCard) > 0) {
            if (Camera.DetectedCard(card_label_e.kCardSpeed60, 1)) {
            	
            }
        }
    }
})
basic.forever(function () {
    seguidor_linha()
    if (Iniciar == 1) {
        if (status_SL == 0) {
            frente()
        } else if (status_SL == 1) {
            esquerda()
        } else if (status_SL == 3) {
            esquerda_brusca()
        } else if (status_SL == 4) {
            direita()
        } else if (status_SL == 6) {
            direita_brusca()
        }
    } else {
        fuzzyBot.motorStop(fuzzyBot.Motors.All)
    }
})

```
## Passo 19
Dentro do último ``||logic:se então||`` coloque um bloco ``||variables:definir velocidade para 0||``,
altere o valor da velocidade para **60**.
```blocks
function esquerda () {
    fuzzyBot.motorRun(fuzzyBot.Motors.M1, fuzzyBot.Dir.CW, 30)
    fuzzyBot.motorRun(fuzzyBot.Motors.M2, fuzzyBot.Dir.CW, 50)
}
input.onButtonPressed(Button.A, function () {
    Iniciar = 0
    basic.showIcon(IconNames.Heart)
})
function esquerda_brusca () {
    fuzzyBot.motorRun(fuzzyBot.Motors.M1, fuzzyBot.Dir.CW, 0)
    fuzzyBot.motorRun(fuzzyBot.Motors.M2, fuzzyBot.Dir.CW, 50)
}
function direita () {
    fuzzyBot.motorRun(fuzzyBot.Motors.M1, fuzzyBot.Dir.CW, 50)
    fuzzyBot.motorRun(fuzzyBot.Motors.M2, fuzzyBot.Dir.CW, 30)
}
input.onButtonPressed(Button.B, function () {
    Iniciar = 1
    basic.showIcon(IconNames.Happy)
})
function frente () {
    fuzzyBot.motorRun(fuzzyBot.Motors.All, fuzzyBot.Dir.CW, 50)
}
function direita_brusca () {
    fuzzyBot.motorRun(fuzzyBot.Motors.M1, fuzzyBot.Dir.CW, 50)
    fuzzyBot.motorRun(fuzzyBot.Motors.M2, fuzzyBot.Dir.CW, 0)
}
function seguidor_linha () {
    if (fuzzyBot.readPatrol(fuzzyBot.Patrol.PatrolLeft) == 0 && fuzzyBot.readPatrol(fuzzyBot.Patrol.PatrolMiddle) == 0 && fuzzyBot.readPatrol(fuzzyBot.Patrol.PatrolRight) == 0) {
        status_SL = 0
    } else if (fuzzyBot.readPatrol(fuzzyBot.Patrol.PatrolLeft) == 0 && fuzzyBot.readPatrol(fuzzyBot.Patrol.PatrolMiddle) == 0 && fuzzyBot.readPatrol(fuzzyBot.Patrol.PatrolRight) == 1) {
        status_SL = 1
    } else if (fuzzyBot.readPatrol(fuzzyBot.Patrol.PatrolLeft) == 0 && fuzzyBot.readPatrol(fuzzyBot.Patrol.PatrolMiddle) == 1 && fuzzyBot.readPatrol(fuzzyBot.Patrol.PatrolRight) == 0) {
        status_SL = 2
    } else if (fuzzyBot.readPatrol(fuzzyBot.Patrol.PatrolLeft) == 0 && fuzzyBot.readPatrol(fuzzyBot.Patrol.PatrolMiddle) == 1 && fuzzyBot.readPatrol(fuzzyBot.Patrol.PatrolRight) == 1) {
        status_SL = 3
    } else if (fuzzyBot.readPatrol(fuzzyBot.Patrol.PatrolLeft) == 1 && fuzzyBot.readPatrol(fuzzyBot.Patrol.PatrolMiddle) == 0 && fuzzyBot.readPatrol(fuzzyBot.Patrol.PatrolRight) == 0) {
        status_SL = 4
    } else if (fuzzyBot.readPatrol(fuzzyBot.Patrol.PatrolLeft) == 1 && fuzzyBot.readPatrol(fuzzyBot.Patrol.PatrolMiddle) == 0 && fuzzyBot.readPatrol(fuzzyBot.Patrol.PatrolRight) == 1) {
        status_SL = 5
    } else if (fuzzyBot.readPatrol(fuzzyBot.Patrol.PatrolLeft) == 1 && fuzzyBot.readPatrol(fuzzyBot.Patrol.PatrolMiddle) == 1 && fuzzyBot.readPatrol(fuzzyBot.Patrol.PatrolRight) == 0) {
        status_SL = 6
    } else if (fuzzyBot.readPatrol(fuzzyBot.Patrol.PatrolLeft) == 1 && fuzzyBot.readPatrol(fuzzyBot.Patrol.PatrolMiddle) == 1 && fuzzyBot.readPatrol(fuzzyBot.Patrol.PatrolRight) == 1) {
        status_SL = 7
    }
}
let status_SL = 0
let Iniciar = 0
basic.pause(2000)
Camera.Begin(sentry_mode_e.kI2CMode, sengo2_addr_e.ADDR1)
Camera.VisionSetStatus(sengo2_status.Enable, sengo_vision_e.kVisionCard)
basic.showIcon(IconNames.Heart)
let velocidade = 80
basic.forever(function () {
    if (Iniciar == 1) {
        if (Camera.Detected(sengo_vision_e.kVisionCard) > 0) {
            if (Camera.DetectedCard(card_label_e.kCardSpeed60, 1)) {
                velocidade = 60
            }
        }
    }
})
basic.forever(function () {
    seguidor_linha()
    if (Iniciar == 1) {
        if (status_SL == 0) {
            frente()
        } else if (status_SL == 1) {
            esquerda()
        } else if (status_SL == 3) {
            esquerda_brusca()
        } else if (status_SL == 4) {
            direita()
        } else if (status_SL == 6) {
            direita_brusca()
        }
    } else {
        fuzzyBot.motorStop(fuzzyBot.Motors.All)
    }
})

```
## Passo 20
Clique três vezes no botão **+** da condicional ``||logic:se então||``para criar mais duas condições
``||logic:senão se então||``.
```blocks
function esquerda () {
    fuzzyBot.motorRun(fuzzyBot.Motors.M1, fuzzyBot.Dir.CW, 30)
    fuzzyBot.motorRun(fuzzyBot.Motors.M2, fuzzyBot.Dir.CW, 50)
}
input.onButtonPressed(Button.A, function () {
    Iniciar = 0
    basic.showIcon(IconNames.Heart)
})
function esquerda_brusca () {
    fuzzyBot.motorRun(fuzzyBot.Motors.M1, fuzzyBot.Dir.CW, 0)
    fuzzyBot.motorRun(fuzzyBot.Motors.M2, fuzzyBot.Dir.CW, 50)
}
function direita () {
    fuzzyBot.motorRun(fuzzyBot.Motors.M1, fuzzyBot.Dir.CW, 50)
    fuzzyBot.motorRun(fuzzyBot.Motors.M2, fuzzyBot.Dir.CW, 30)
}
input.onButtonPressed(Button.B, function () {
    Iniciar = 1
    basic.showIcon(IconNames.Happy)
})
function frente () {
    fuzzyBot.motorRun(fuzzyBot.Motors.All, fuzzyBot.Dir.CW, 50)
}
function direita_brusca () {
    fuzzyBot.motorRun(fuzzyBot.Motors.M1, fuzzyBot.Dir.CW, 50)
    fuzzyBot.motorRun(fuzzyBot.Motors.M2, fuzzyBot.Dir.CW, 0)
}
function seguidor_linha () {
    if (fuzzyBot.readPatrol(fuzzyBot.Patrol.PatrolLeft) == 0 && fuzzyBot.readPatrol(fuzzyBot.Patrol.PatrolMiddle) == 0 && fuzzyBot.readPatrol(fuzzyBot.Patrol.PatrolRight) == 0) {
        status_SL = 0
    } else if (fuzzyBot.readPatrol(fuzzyBot.Patrol.PatrolLeft) == 0 && fuzzyBot.readPatrol(fuzzyBot.Patrol.PatrolMiddle) == 0 && fuzzyBot.readPatrol(fuzzyBot.Patrol.PatrolRight) == 1) {
        status_SL = 1
    } else if (fuzzyBot.readPatrol(fuzzyBot.Patrol.PatrolLeft) == 0 && fuzzyBot.readPatrol(fuzzyBot.Patrol.PatrolMiddle) == 1 && fuzzyBot.readPatrol(fuzzyBot.Patrol.PatrolRight) == 0) {
        status_SL = 2
    } else if (fuzzyBot.readPatrol(fuzzyBot.Patrol.PatrolLeft) == 0 && fuzzyBot.readPatrol(fuzzyBot.Patrol.PatrolMiddle) == 1 && fuzzyBot.readPatrol(fuzzyBot.Patrol.PatrolRight) == 1) {
        status_SL = 3
    } else if (fuzzyBot.readPatrol(fuzzyBot.Patrol.PatrolLeft) == 1 && fuzzyBot.readPatrol(fuzzyBot.Patrol.PatrolMiddle) == 0 && fuzzyBot.readPatrol(fuzzyBot.Patrol.PatrolRight) == 0) {
        status_SL = 4
    } else if (fuzzyBot.readPatrol(fuzzyBot.Patrol.PatrolLeft) == 1 && fuzzyBot.readPatrol(fuzzyBot.Patrol.PatrolMiddle) == 0 && fuzzyBot.readPatrol(fuzzyBot.Patrol.PatrolRight) == 1) {
        status_SL = 5
    } else if (fuzzyBot.readPatrol(fuzzyBot.Patrol.PatrolLeft) == 1 && fuzzyBot.readPatrol(fuzzyBot.Patrol.PatrolMiddle) == 1 && fuzzyBot.readPatrol(fuzzyBot.Patrol.PatrolRight) == 0) {
        status_SL = 6
    } else if (fuzzyBot.readPatrol(fuzzyBot.Patrol.PatrolLeft) == 1 && fuzzyBot.readPatrol(fuzzyBot.Patrol.PatrolMiddle) == 1 && fuzzyBot.readPatrol(fuzzyBot.Patrol.PatrolRight) == 1) {
        status_SL = 7
    }
}
let status_SL = 0
let Iniciar = 0
basic.pause(2000)
Camera.Begin(sentry_mode_e.kI2CMode, sengo2_addr_e.ADDR1)
Camera.VisionSetStatus(sengo2_status.Enable, sengo_vision_e.kVisionCard)
basic.showIcon(IconNames.Heart)
let velocidade = 80
basic.forever(function () {
    if (Iniciar == 1) {
        if (Camera.Detected(sengo_vision_e.kVisionCard) > 0) {
            if (Camera.DetectedCard(card_label_e.kCardSpeed60, 1)) {
                velocidade = 60
            } else if (false) {
            	
            } else if (false) {
            	
            } else {
            	
            }
        }
    }
})
basic.forever(function () {
    seguidor_linha()
    if (Iniciar == 1) {
        if (status_SL == 0) {
            frente()
        } else if (status_SL == 1) {
            esquerda()
        } else if (status_SL == 3) {
            esquerda_brusca()
        } else if (status_SL == 4) {
            direita()
        } else if (status_SL == 6) {
            direita_brusca()
        }
    } else {
        fuzzyBot.motorStop(fuzzyBot.Motors.All)
    }
})

```

## Passo 21
Duplique o bloco ``||Camera:Cartão Velocidade 60 detectado do resultado 1||``
e coloque a cópia no lugar da condição ``||logic:falso||`` do primeiro ``||logic:senão se então||``.
Troque o cartão **Velocidade 60** por **Velocidade 40**.


```blocks
function esquerda () {
    fuzzyBot.motorRun(fuzzyBot.Motors.M1, fuzzyBot.Dir.CW, 30)
    fuzzyBot.motorRun(fuzzyBot.Motors.M2, fuzzyBot.Dir.CW, 50)
}
input.onButtonPressed(Button.A, function () {
    Iniciar = 0
    basic.showIcon(IconNames.Heart)
})
function esquerda_brusca () {
    fuzzyBot.motorRun(fuzzyBot.Motors.M1, fuzzyBot.Dir.CW, 0)
    fuzzyBot.motorRun(fuzzyBot.Motors.M2, fuzzyBot.Dir.CW, 50)
}
function direita () {
    fuzzyBot.motorRun(fuzzyBot.Motors.M1, fuzzyBot.Dir.CW, 50)
    fuzzyBot.motorRun(fuzzyBot.Motors.M2, fuzzyBot.Dir.CW, 30)
}
input.onButtonPressed(Button.B, function () {
    Iniciar = 1
    basic.showIcon(IconNames.Happy)
})
function frente () {
    fuzzyBot.motorRun(fuzzyBot.Motors.All, fuzzyBot.Dir.CW, 50)
}
function direita_brusca () {
    fuzzyBot.motorRun(fuzzyBot.Motors.M1, fuzzyBot.Dir.CW, 50)
    fuzzyBot.motorRun(fuzzyBot.Motors.M2, fuzzyBot.Dir.CW, 0)
}
function seguidor_linha () {
    if (fuzzyBot.readPatrol(fuzzyBot.Patrol.PatrolLeft) == 0 && fuzzyBot.readPatrol(fuzzyBot.Patrol.PatrolMiddle) == 0 && fuzzyBot.readPatrol(fuzzyBot.Patrol.PatrolRight) == 0) {
        status_SL = 0
    } else if (fuzzyBot.readPatrol(fuzzyBot.Patrol.PatrolLeft) == 0 && fuzzyBot.readPatrol(fuzzyBot.Patrol.PatrolMiddle) == 0 && fuzzyBot.readPatrol(fuzzyBot.Patrol.PatrolRight) == 1) {
        status_SL = 1
    } else if (fuzzyBot.readPatrol(fuzzyBot.Patrol.PatrolLeft) == 0 && fuzzyBot.readPatrol(fuzzyBot.Patrol.PatrolMiddle) == 1 && fuzzyBot.readPatrol(fuzzyBot.Patrol.PatrolRight) == 0) {
        status_SL = 2
    } else if (fuzzyBot.readPatrol(fuzzyBot.Patrol.PatrolLeft) == 0 && fuzzyBot.readPatrol(fuzzyBot.Patrol.PatrolMiddle) == 1 && fuzzyBot.readPatrol(fuzzyBot.Patrol.PatrolRight) == 1) {
        status_SL = 3
    } else if (fuzzyBot.readPatrol(fuzzyBot.Patrol.PatrolLeft) == 1 && fuzzyBot.readPatrol(fuzzyBot.Patrol.PatrolMiddle) == 0 && fuzzyBot.readPatrol(fuzzyBot.Patrol.PatrolRight) == 0) {
        status_SL = 4
    } else if (fuzzyBot.readPatrol(fuzzyBot.Patrol.PatrolLeft) == 1 && fuzzyBot.readPatrol(fuzzyBot.Patrol.PatrolMiddle) == 0 && fuzzyBot.readPatrol(fuzzyBot.Patrol.PatrolRight) == 1) {
        status_SL = 5
    } else if (fuzzyBot.readPatrol(fuzzyBot.Patrol.PatrolLeft) == 1 && fuzzyBot.readPatrol(fuzzyBot.Patrol.PatrolMiddle) == 1 && fuzzyBot.readPatrol(fuzzyBot.Patrol.PatrolRight) == 0) {
        status_SL = 6
    } else if (fuzzyBot.readPatrol(fuzzyBot.Patrol.PatrolLeft) == 1 && fuzzyBot.readPatrol(fuzzyBot.Patrol.PatrolMiddle) == 1 && fuzzyBot.readPatrol(fuzzyBot.Patrol.PatrolRight) == 1) {
        status_SL = 7
    }
}
let status_SL = 0
let Iniciar = 0
basic.pause(2000)
Camera.Begin(sentry_mode_e.kI2CMode, sengo2_addr_e.ADDR1)
Camera.VisionSetStatus(sengo2_status.Enable, sengo_vision_e.kVisionCard)
basic.showIcon(IconNames.Heart)
let velocidade = 80
basic.forever(function () {
    if (Iniciar == 1) {
        if (Camera.Detected(sengo_vision_e.kVisionCard) > 0) {
            if (Camera.DetectedCard(card_label_e.kCardSpeed60, 1)) {
                velocidade = 60
            } else if (Camera.DetectedCard(card_label_e.kCardSpeed40, 1)) {
            	
            } else if (false) {
            	
            } else {
            	
            }
        }
    }
})
basic.forever(function () {
    seguidor_linha()
    if (Iniciar == 1) {
        if (status_SL == 0) {
            frente()
        } else if (status_SL == 1) {
            esquerda()
        } else if (status_SL == 3) {
            esquerda_brusca()
        } else if (status_SL == 4) {
            direita()
        } else if (status_SL == 6) {
            direita_brusca()
        }
    } else {
        fuzzyBot.motorStop(fuzzyBot.Motors.All)
    }
})

```
## Passo 22
Copie a definição ``||variables:definir velocidade para 60||`` e cole dentro do
``||logic:senão se então||``. Modifique o valor de **60** para **40**.

```blocks
function esquerda () {
    fuzzyBot.motorRun(fuzzyBot.Motors.M1, fuzzyBot.Dir.CW, 30)
    fuzzyBot.motorRun(fuzzyBot.Motors.M2, fuzzyBot.Dir.CW, 50)
}
input.onButtonPressed(Button.A, function () {
    Iniciar = 0
    basic.showIcon(IconNames.Heart)
})
function esquerda_brusca () {
    fuzzyBot.motorRun(fuzzyBot.Motors.M1, fuzzyBot.Dir.CW, 0)
    fuzzyBot.motorRun(fuzzyBot.Motors.M2, fuzzyBot.Dir.CW, 50)
}
function direita () {
    fuzzyBot.motorRun(fuzzyBot.Motors.M1, fuzzyBot.Dir.CW, 50)
    fuzzyBot.motorRun(fuzzyBot.Motors.M2, fuzzyBot.Dir.CW, 30)
}
input.onButtonPressed(Button.B, function () {
    Iniciar = 1
    basic.showIcon(IconNames.Happy)
})
function frente () {
    fuzzyBot.motorRun(fuzzyBot.Motors.All, fuzzyBot.Dir.CW, 50)
}
function direita_brusca () {
    fuzzyBot.motorRun(fuzzyBot.Motors.M1, fuzzyBot.Dir.CW, 50)
    fuzzyBot.motorRun(fuzzyBot.Motors.M2, fuzzyBot.Dir.CW, 0)
}
function seguidor_linha () {
    if (fuzzyBot.readPatrol(fuzzyBot.Patrol.PatrolLeft) == 0 && fuzzyBot.readPatrol(fuzzyBot.Patrol.PatrolMiddle) == 0 && fuzzyBot.readPatrol(fuzzyBot.Patrol.PatrolRight) == 0) {
        status_SL = 0
    } else if (fuzzyBot.readPatrol(fuzzyBot.Patrol.PatrolLeft) == 0 && fuzzyBot.readPatrol(fuzzyBot.Patrol.PatrolMiddle) == 0 && fuzzyBot.readPatrol(fuzzyBot.Patrol.PatrolRight) == 1) {
        status_SL = 1
    } else if (fuzzyBot.readPatrol(fuzzyBot.Patrol.PatrolLeft) == 0 && fuzzyBot.readPatrol(fuzzyBot.Patrol.PatrolMiddle) == 1 && fuzzyBot.readPatrol(fuzzyBot.Patrol.PatrolRight) == 0) {
        status_SL = 2
    } else if (fuzzyBot.readPatrol(fuzzyBot.Patrol.PatrolLeft) == 0 && fuzzyBot.readPatrol(fuzzyBot.Patrol.PatrolMiddle) == 1 && fuzzyBot.readPatrol(fuzzyBot.Patrol.PatrolRight) == 1) {
        status_SL = 3
    } else if (fuzzyBot.readPatrol(fuzzyBot.Patrol.PatrolLeft) == 1 && fuzzyBot.readPatrol(fuzzyBot.Patrol.PatrolMiddle) == 0 && fuzzyBot.readPatrol(fuzzyBot.Patrol.PatrolRight) == 0) {
        status_SL = 4
    } else if (fuzzyBot.readPatrol(fuzzyBot.Patrol.PatrolLeft) == 1 && fuzzyBot.readPatrol(fuzzyBot.Patrol.PatrolMiddle) == 0 && fuzzyBot.readPatrol(fuzzyBot.Patrol.PatrolRight) == 1) {
        status_SL = 5
    } else if (fuzzyBot.readPatrol(fuzzyBot.Patrol.PatrolLeft) == 1 && fuzzyBot.readPatrol(fuzzyBot.Patrol.PatrolMiddle) == 1 && fuzzyBot.readPatrol(fuzzyBot.Patrol.PatrolRight) == 0) {
        status_SL = 6
    } else if (fuzzyBot.readPatrol(fuzzyBot.Patrol.PatrolLeft) == 1 && fuzzyBot.readPatrol(fuzzyBot.Patrol.PatrolMiddle) == 1 && fuzzyBot.readPatrol(fuzzyBot.Patrol.PatrolRight) == 1) {
        status_SL = 7
    }
}
let status_SL = 0
let Iniciar = 0
basic.pause(2000)
Camera.Begin(sentry_mode_e.kI2CMode, sengo2_addr_e.ADDR1)
Camera.VisionSetStatus(sengo2_status.Enable, sengo_vision_e.kVisionCard)
basic.showIcon(IconNames.Heart)
let velocidade = 80
basic.forever(function () {
    if (Iniciar == 1) {
        if (Camera.Detected(sengo_vision_e.kVisionCard) > 0) {
            if (Camera.DetectedCard(card_label_e.kCardSpeed60, 1)) {
                velocidade = 60
            } else if (Camera.DetectedCard(card_label_e.kCardSpeed40, 1)) {
                velocidade = 40
            } else if (false) {
            	
            } else {
            	
            }
        }
    }
})
basic.forever(function () {
    seguidor_linha()
    if (Iniciar == 1) {
        if (status_SL == 0) {
            frente()
        } else if (status_SL == 1) {
            esquerda()
        } else if (status_SL == 3) {
            esquerda_brusca()
        } else if (status_SL == 4) {
            direita()
        } else if (status_SL == 6) {
            direita_brusca()
        }
    } else {
        fuzzyBot.motorStop(fuzzyBot.Motors.All)
    }
})

```

## Passo 23
Duplique o bloco ``||Camera:Cartão Velocidade 60 detectado do resultado 1||``
e coloque a cópia no lugar da condição ``||logic:falso||`` do segundo ``||logic:senão se então||``.
Troque o cartão **Velocidade 60** por **Luz Vermelha**.

```blocks
function esquerda () {
    fuzzyBot.motorRun(fuzzyBot.Motors.M1, fuzzyBot.Dir.CW, 30)
    fuzzyBot.motorRun(fuzzyBot.Motors.M2, fuzzyBot.Dir.CW, 50)
}
input.onButtonPressed(Button.A, function () {
    Iniciar = 0
    basic.showIcon(IconNames.Heart)
})
function esquerda_brusca () {
    fuzzyBot.motorRun(fuzzyBot.Motors.M1, fuzzyBot.Dir.CW, 0)
    fuzzyBot.motorRun(fuzzyBot.Motors.M2, fuzzyBot.Dir.CW, 50)
}
function direita () {
    fuzzyBot.motorRun(fuzzyBot.Motors.M1, fuzzyBot.Dir.CW, 50)
    fuzzyBot.motorRun(fuzzyBot.Motors.M2, fuzzyBot.Dir.CW, 30)
}
input.onButtonPressed(Button.B, function () {
    Iniciar = 1
    basic.showIcon(IconNames.Happy)
})
function frente () {
    fuzzyBot.motorRun(fuzzyBot.Motors.All, fuzzyBot.Dir.CW, 50)
}
function direita_brusca () {
    fuzzyBot.motorRun(fuzzyBot.Motors.M1, fuzzyBot.Dir.CW, 50)
    fuzzyBot.motorRun(fuzzyBot.Motors.M2, fuzzyBot.Dir.CW, 0)
}
function seguidor_linha () {
    if (fuzzyBot.readPatrol(fuzzyBot.Patrol.PatrolLeft) == 0 && fuzzyBot.readPatrol(fuzzyBot.Patrol.PatrolMiddle) == 0 && fuzzyBot.readPatrol(fuzzyBot.Patrol.PatrolRight) == 0) {
        status_SL = 0
    } else if (fuzzyBot.readPatrol(fuzzyBot.Patrol.PatrolLeft) == 0 && fuzzyBot.readPatrol(fuzzyBot.Patrol.PatrolMiddle) == 0 && fuzzyBot.readPatrol(fuzzyBot.Patrol.PatrolRight) == 1) {
        status_SL = 1
    } else if (fuzzyBot.readPatrol(fuzzyBot.Patrol.PatrolLeft) == 0 && fuzzyBot.readPatrol(fuzzyBot.Patrol.PatrolMiddle) == 1 && fuzzyBot.readPatrol(fuzzyBot.Patrol.PatrolRight) == 0) {
        status_SL = 2
    } else if (fuzzyBot.readPatrol(fuzzyBot.Patrol.PatrolLeft) == 0 && fuzzyBot.readPatrol(fuzzyBot.Patrol.PatrolMiddle) == 1 && fuzzyBot.readPatrol(fuzzyBot.Patrol.PatrolRight) == 1) {
        status_SL = 3
    } else if (fuzzyBot.readPatrol(fuzzyBot.Patrol.PatrolLeft) == 1 && fuzzyBot.readPatrol(fuzzyBot.Patrol.PatrolMiddle) == 0 && fuzzyBot.readPatrol(fuzzyBot.Patrol.PatrolRight) == 0) {
        status_SL = 4
    } else if (fuzzyBot.readPatrol(fuzzyBot.Patrol.PatrolLeft) == 1 && fuzzyBot.readPatrol(fuzzyBot.Patrol.PatrolMiddle) == 0 && fuzzyBot.readPatrol(fuzzyBot.Patrol.PatrolRight) == 1) {
        status_SL = 5
    } else if (fuzzyBot.readPatrol(fuzzyBot.Patrol.PatrolLeft) == 1 && fuzzyBot.readPatrol(fuzzyBot.Patrol.PatrolMiddle) == 1 && fuzzyBot.readPatrol(fuzzyBot.Patrol.PatrolRight) == 0) {
        status_SL = 6
    } else if (fuzzyBot.readPatrol(fuzzyBot.Patrol.PatrolLeft) == 1 && fuzzyBot.readPatrol(fuzzyBot.Patrol.PatrolMiddle) == 1 && fuzzyBot.readPatrol(fuzzyBot.Patrol.PatrolRight) == 1) {
        status_SL = 7
    }
}
let status_SL = 0
let Iniciar = 0
basic.pause(2000)
Camera.Begin(sentry_mode_e.kI2CMode, sengo2_addr_e.ADDR1)
Camera.VisionSetStatus(sengo2_status.Enable, sengo_vision_e.kVisionCard)
basic.showIcon(IconNames.Heart)
let velocidade = 80
basic.forever(function () {
    if (Iniciar == 1) {
        if (Camera.Detected(sengo_vision_e.kVisionCard) > 0) {
            if (Camera.DetectedCard(card_label_e.kCardSpeed60, 1)) {
                velocidade = 60
            } else if (Camera.DetectedCard(card_label_e.kCardSpeed40, 1)) {
                velocidade = 40
            } else if (Camera.DetectedCard(card_label_e.kCardRedLight, 1)) {
            	
            } else {
            	
            }
        }
    }
})
basic.forever(function () {
    seguidor_linha()
    if (Iniciar == 1) {
        if (status_SL == 0) {
            frente()
        } else if (status_SL == 1) {
            esquerda()
        } else if (status_SL == 3) {
            esquerda_brusca()
        } else if (status_SL == 4) {
            direita()
        } else if (status_SL == 6) {
            direita_brusca()
        }
    } else {
        fuzzyBot.motorStop(fuzzyBot.Motors.All)
    }
})

```
## Passo 24
Copie a definição ``||variables:definir velocidade para 60||`` e cole dentro do
``||logic:senão se então||``. Modifique o valor de **60** para **0**.
```blocks
function esquerda () {
    fuzzyBot.motorRun(fuzzyBot.Motors.M1, fuzzyBot.Dir.CW, 30)
    fuzzyBot.motorRun(fuzzyBot.Motors.M2, fuzzyBot.Dir.CW, 50)
}
input.onButtonPressed(Button.A, function () {
    Iniciar = 0
    basic.showIcon(IconNames.Heart)
})
function esquerda_brusca () {
    fuzzyBot.motorRun(fuzzyBot.Motors.M1, fuzzyBot.Dir.CW, 0)
    fuzzyBot.motorRun(fuzzyBot.Motors.M2, fuzzyBot.Dir.CW, 50)
}
function direita () {
    fuzzyBot.motorRun(fuzzyBot.Motors.M1, fuzzyBot.Dir.CW, 50)
    fuzzyBot.motorRun(fuzzyBot.Motors.M2, fuzzyBot.Dir.CW, 30)
}
input.onButtonPressed(Button.B, function () {
    Iniciar = 1
    basic.showIcon(IconNames.Happy)
})
function frente () {
    fuzzyBot.motorRun(fuzzyBot.Motors.All, fuzzyBot.Dir.CW, 50)
}
function direita_brusca () {
    fuzzyBot.motorRun(fuzzyBot.Motors.M1, fuzzyBot.Dir.CW, 50)
    fuzzyBot.motorRun(fuzzyBot.Motors.M2, fuzzyBot.Dir.CW, 0)
}
function seguidor_linha () {
    if (fuzzyBot.readPatrol(fuzzyBot.Patrol.PatrolLeft) == 0 && fuzzyBot.readPatrol(fuzzyBot.Patrol.PatrolMiddle) == 0 && fuzzyBot.readPatrol(fuzzyBot.Patrol.PatrolRight) == 0) {
        status_SL = 0
    } else if (fuzzyBot.readPatrol(fuzzyBot.Patrol.PatrolLeft) == 0 && fuzzyBot.readPatrol(fuzzyBot.Patrol.PatrolMiddle) == 0 && fuzzyBot.readPatrol(fuzzyBot.Patrol.PatrolRight) == 1) {
        status_SL = 1
    } else if (fuzzyBot.readPatrol(fuzzyBot.Patrol.PatrolLeft) == 0 && fuzzyBot.readPatrol(fuzzyBot.Patrol.PatrolMiddle) == 1 && fuzzyBot.readPatrol(fuzzyBot.Patrol.PatrolRight) == 0) {
        status_SL = 2
    } else if (fuzzyBot.readPatrol(fuzzyBot.Patrol.PatrolLeft) == 0 && fuzzyBot.readPatrol(fuzzyBot.Patrol.PatrolMiddle) == 1 && fuzzyBot.readPatrol(fuzzyBot.Patrol.PatrolRight) == 1) {
        status_SL = 3
    } else if (fuzzyBot.readPatrol(fuzzyBot.Patrol.PatrolLeft) == 1 && fuzzyBot.readPatrol(fuzzyBot.Patrol.PatrolMiddle) == 0 && fuzzyBot.readPatrol(fuzzyBot.Patrol.PatrolRight) == 0) {
        status_SL = 4
    } else if (fuzzyBot.readPatrol(fuzzyBot.Patrol.PatrolLeft) == 1 && fuzzyBot.readPatrol(fuzzyBot.Patrol.PatrolMiddle) == 0 && fuzzyBot.readPatrol(fuzzyBot.Patrol.PatrolRight) == 1) {
        status_SL = 5
    } else if (fuzzyBot.readPatrol(fuzzyBot.Patrol.PatrolLeft) == 1 && fuzzyBot.readPatrol(fuzzyBot.Patrol.PatrolMiddle) == 1 && fuzzyBot.readPatrol(fuzzyBot.Patrol.PatrolRight) == 0) {
        status_SL = 6
    } else if (fuzzyBot.readPatrol(fuzzyBot.Patrol.PatrolLeft) == 1 && fuzzyBot.readPatrol(fuzzyBot.Patrol.PatrolMiddle) == 1 && fuzzyBot.readPatrol(fuzzyBot.Patrol.PatrolRight) == 1) {
        status_SL = 7
    }
}
let status_SL = 0
let Iniciar = 0
basic.pause(2000)
Camera.Begin(sentry_mode_e.kI2CMode, sengo2_addr_e.ADDR1)
Camera.VisionSetStatus(sengo2_status.Enable, sengo_vision_e.kVisionCard)
basic.showIcon(IconNames.Heart)
let velocidade = 80
basic.forever(function () {
    if (Iniciar == 1) {
        if (Camera.Detected(sengo_vision_e.kVisionCard) > 0) {
            if (Camera.DetectedCard(card_label_e.kCardSpeed60, 1)) {
                velocidade = 60
            } else if (Camera.DetectedCard(card_label_e.kCardSpeed40, 1)) {
                velocidade = 40
            } else if (Camera.DetectedCard(card_label_e.kCardRedLight, 1)) {
                velocidade = 0
            } else {
            	
            }
        }
    }
})
basic.forever(function () {
    seguidor_linha()
    if (Iniciar == 1) {
        if (status_SL == 0) {
            frente()
        } else if (status_SL == 1) {
            esquerda()
        } else if (status_SL == 3) {
            esquerda_brusca()
        } else if (status_SL == 4) {
            direita()
        } else if (status_SL == 6) {
            direita_brusca()
        }
    } else {
        fuzzyBot.motorStop(fuzzyBot.Motors.All)
    }
})

```

## Passo 25
Agora precisamos revisitar as funções ``||functions:direita||``, ``||functions:direita_brusca||``,
``||functions:esquerda||``, ``||functions:esquerda_brusca||`` e ``||functions:frente||``.

Onde houver o comando ``||fuzzyBot:Motor esquerdo/direito mover para frente com a velocidade 50||``
modifique o valor **50** pela variável ``||variables:Velocidade||``.

```blocks
function esquerda () {
    fuzzyBot.motorRun(fuzzyBot.Motors.M1, fuzzyBot.Dir.CW, 30)
    fuzzyBot.motorRun(fuzzyBot.Motors.M2, fuzzyBot.Dir.CW, velocidade)
}
input.onButtonPressed(Button.A, function () {
    Iniciar = 0
    basic.showIcon(IconNames.Heart)
})
function esquerda_brusca () {
    fuzzyBot.motorRun(fuzzyBot.Motors.M1, fuzzyBot.Dir.CW, 0)
    fuzzyBot.motorRun(fuzzyBot.Motors.M2, fuzzyBot.Dir.CW, velocidade)
}
function direita () {
    fuzzyBot.motorRun(fuzzyBot.Motors.M1, fuzzyBot.Dir.CW, velocidade)
    fuzzyBot.motorRun(fuzzyBot.Motors.M2, fuzzyBot.Dir.CW, 30)
}
input.onButtonPressed(Button.B, function () {
    Iniciar = 1
    basic.showIcon(IconNames.Happy)
})
function frente () {
    fuzzyBot.motorRun(fuzzyBot.Motors.All, fuzzyBot.Dir.CW, velocidade)
}
function direita_brusca () {
    fuzzyBot.motorRun(fuzzyBot.Motors.M1, fuzzyBot.Dir.CW, velocidade)
    fuzzyBot.motorRun(fuzzyBot.Motors.M2, fuzzyBot.Dir.CW, 0)
}
function seguidor_linha () {
    if (fuzzyBot.readPatrol(fuzzyBot.Patrol.PatrolLeft) == 0 && fuzzyBot.readPatrol(fuzzyBot.Patrol.PatrolMiddle) == 0 && fuzzyBot.readPatrol(fuzzyBot.Patrol.PatrolRight) == 0) {
        status_SL = 0
    } else if (fuzzyBot.readPatrol(fuzzyBot.Patrol.PatrolLeft) == 0 && fuzzyBot.readPatrol(fuzzyBot.Patrol.PatrolMiddle) == 0 && fuzzyBot.readPatrol(fuzzyBot.Patrol.PatrolRight) == 1) {
        status_SL = 1
    } else if (fuzzyBot.readPatrol(fuzzyBot.Patrol.PatrolLeft) == 0 && fuzzyBot.readPatrol(fuzzyBot.Patrol.PatrolMiddle) == 1 && fuzzyBot.readPatrol(fuzzyBot.Patrol.PatrolRight) == 0) {
        status_SL = 2
    } else if (fuzzyBot.readPatrol(fuzzyBot.Patrol.PatrolLeft) == 0 && fuzzyBot.readPatrol(fuzzyBot.Patrol.PatrolMiddle) == 1 && fuzzyBot.readPatrol(fuzzyBot.Patrol.PatrolRight) == 1) {
        status_SL = 3
    } else if (fuzzyBot.readPatrol(fuzzyBot.Patrol.PatrolLeft) == 1 && fuzzyBot.readPatrol(fuzzyBot.Patrol.PatrolMiddle) == 0 && fuzzyBot.readPatrol(fuzzyBot.Patrol.PatrolRight) == 0) {
        status_SL = 4
    } else if (fuzzyBot.readPatrol(fuzzyBot.Patrol.PatrolLeft) == 1 && fuzzyBot.readPatrol(fuzzyBot.Patrol.PatrolMiddle) == 0 && fuzzyBot.readPatrol(fuzzyBot.Patrol.PatrolRight) == 1) {
        status_SL = 5
    } else if (fuzzyBot.readPatrol(fuzzyBot.Patrol.PatrolLeft) == 1 && fuzzyBot.readPatrol(fuzzyBot.Patrol.PatrolMiddle) == 1 && fuzzyBot.readPatrol(fuzzyBot.Patrol.PatrolRight) == 0) {
        status_SL = 6
    } else if (fuzzyBot.readPatrol(fuzzyBot.Patrol.PatrolLeft) == 1 && fuzzyBot.readPatrol(fuzzyBot.Patrol.PatrolMiddle) == 1 && fuzzyBot.readPatrol(fuzzyBot.Patrol.PatrolRight) == 1) {
        status_SL = 7
    }
}
let status_SL = 0
let Iniciar = 0
let velocidade = 0
basic.pause(2000)
Camera.Begin(sentry_mode_e.kI2CMode, sengo2_addr_e.ADDR1)
Camera.VisionSetStatus(sengo2_status.Enable, sengo_vision_e.kVisionCard)
basic.showIcon(IconNames.Heart)
velocidade = 80
basic.forever(function () {
    if (Iniciar == 1) {
        if (Camera.Detected(sengo_vision_e.kVisionCard) > 0) {
            if (Camera.DetectedCard(card_label_e.kCardSpeed60, 1)) {
                velocidade = 60
            } else if (Camera.DetectedCard(card_label_e.kCardSpeed40, 1)) {
                velocidade = 40
            } else if (Camera.DetectedCard(card_label_e.kCardRedLight, 1)) {
                velocidade = 0
            } else {
            	
            }
        }
    }
})
basic.forever(function () {
    seguidor_linha()
    if (Iniciar == 1) {
        if (status_SL == 0) {
            frente()
        } else if (status_SL == 1) {
            esquerda()
        } else if (status_SL == 3) {
            esquerda_brusca()
        } else if (status_SL == 4) {
            direita()
        } else if (status_SL == 6) {
            direita_brusca()
        }
    } else {
        fuzzyBot.motorStop(fuzzyBot.Motors.All)
    }
})

```
## Passo 26
Acesse o menu ``||math:Matemática||``, pegue a operação de multiplicação ``||math:0 x 0||``
e substitua o valor **30** no comando ``||fuzzyBot:Motor esquerdo mover para frente com a velocidade 50||``
da função ``||functions:esquerda||``. Repita o processo na função ``||functions:direita||`` para o motor direito.

```blocks
function esquerda () {
    fuzzyBot.motorRun(fuzzyBot.Motors.M1, fuzzyBot.Dir.CW, 0 * 0)
    fuzzyBot.motorRun(fuzzyBot.Motors.M2, fuzzyBot.Dir.CW, velocidade)
}
input.onButtonPressed(Button.A, function () {
    Iniciar = 0
    basic.showIcon(IconNames.Heart)
})
function esquerda_brusca () {
    fuzzyBot.motorRun(fuzzyBot.Motors.M1, fuzzyBot.Dir.CW, 0)
    fuzzyBot.motorRun(fuzzyBot.Motors.M2, fuzzyBot.Dir.CW, velocidade)
}
function direita () {
    fuzzyBot.motorRun(fuzzyBot.Motors.M1, fuzzyBot.Dir.CW, velocidade)
    fuzzyBot.motorRun(fuzzyBot.Motors.M2, fuzzyBot.Dir.CW, 0 * 0)
}
input.onButtonPressed(Button.B, function () {
    Iniciar = 1
    basic.showIcon(IconNames.Happy)
})
function frente () {
    fuzzyBot.motorRun(fuzzyBot.Motors.All, fuzzyBot.Dir.CW, velocidade)
}
function direita_brusca () {
    fuzzyBot.motorRun(fuzzyBot.Motors.M1, fuzzyBot.Dir.CW, velocidade)
    fuzzyBot.motorRun(fuzzyBot.Motors.M2, fuzzyBot.Dir.CW, 0)
}
function seguidor_linha () {
    if (fuzzyBot.readPatrol(fuzzyBot.Patrol.PatrolLeft) == 0 && fuzzyBot.readPatrol(fuzzyBot.Patrol.PatrolMiddle) == 0 && fuzzyBot.readPatrol(fuzzyBot.Patrol.PatrolRight) == 0) {
        status_SL = 0
    } else if (fuzzyBot.readPatrol(fuzzyBot.Patrol.PatrolLeft) == 0 && fuzzyBot.readPatrol(fuzzyBot.Patrol.PatrolMiddle) == 0 && fuzzyBot.readPatrol(fuzzyBot.Patrol.PatrolRight) == 1) {
        status_SL = 1
    } else if (fuzzyBot.readPatrol(fuzzyBot.Patrol.PatrolLeft) == 0 && fuzzyBot.readPatrol(fuzzyBot.Patrol.PatrolMiddle) == 1 && fuzzyBot.readPatrol(fuzzyBot.Patrol.PatrolRight) == 0) {
        status_SL = 2
    } else if (fuzzyBot.readPatrol(fuzzyBot.Patrol.PatrolLeft) == 0 && fuzzyBot.readPatrol(fuzzyBot.Patrol.PatrolMiddle) == 1 && fuzzyBot.readPatrol(fuzzyBot.Patrol.PatrolRight) == 1) {
        status_SL = 3
    } else if (fuzzyBot.readPatrol(fuzzyBot.Patrol.PatrolLeft) == 1 && fuzzyBot.readPatrol(fuzzyBot.Patrol.PatrolMiddle) == 0 && fuzzyBot.readPatrol(fuzzyBot.Patrol.PatrolRight) == 0) {
        status_SL = 4
    } else if (fuzzyBot.readPatrol(fuzzyBot.Patrol.PatrolLeft) == 1 && fuzzyBot.readPatrol(fuzzyBot.Patrol.PatrolMiddle) == 0 && fuzzyBot.readPatrol(fuzzyBot.Patrol.PatrolRight) == 1) {
        status_SL = 5
    } else if (fuzzyBot.readPatrol(fuzzyBot.Patrol.PatrolLeft) == 1 && fuzzyBot.readPatrol(fuzzyBot.Patrol.PatrolMiddle) == 1 && fuzzyBot.readPatrol(fuzzyBot.Patrol.PatrolRight) == 0) {
        status_SL = 6
    } else if (fuzzyBot.readPatrol(fuzzyBot.Patrol.PatrolLeft) == 1 && fuzzyBot.readPatrol(fuzzyBot.Patrol.PatrolMiddle) == 1 && fuzzyBot.readPatrol(fuzzyBot.Patrol.PatrolRight) == 1) {
        status_SL = 7
    }
}
let status_SL = 0
let Iniciar = 0
let velocidade = 0
basic.pause(2000)
Camera.Begin(sentry_mode_e.kI2CMode, sengo2_addr_e.ADDR1)
Camera.VisionSetStatus(sengo2_status.Enable, sengo_vision_e.kVisionCard)
basic.showIcon(IconNames.Heart)
velocidade = 80
basic.forever(function () {
    if (Iniciar == 1) {
        if (Camera.Detected(sengo_vision_e.kVisionCard) > 0) {
            if (Camera.DetectedCard(card_label_e.kCardSpeed60, 1)) {
                velocidade = 60
            } else if (Camera.DetectedCard(card_label_e.kCardSpeed40, 1)) {
                velocidade = 40
            } else if (Camera.DetectedCard(card_label_e.kCardRedLight, 1)) {
                velocidade = 0
            } else {
            	
            }
        }
    }
})
basic.forever(function () {
    seguidor_linha()
    if (Iniciar == 1) {
        if (status_SL == 0) {
            frente()
        } else if (status_SL == 1) {
            esquerda()
        } else if (status_SL == 3) {
            esquerda_brusca()
        } else if (status_SL == 4) {
            direita()
        } else if (status_SL == 6) {
            direita_brusca()
        }
    } else {
        fuzzyBot.motorStop(fuzzyBot.Motors.All)
    }
})

```

## Passo 27

Atualize os campos das operações de multiplicação. 
O primeiro campo deve ser a variável ``||variables:velocidade||`` e o segundo 
deve ser o valor de **0.6**. Dessa forma um dos motores gira com 60% da velocidade do oposto,
permitindo o deslocamento do robô para um dos lados.

```blocks
function esquerda () {
    fuzzyBot.motorRun(fuzzyBot.Motors.M1, fuzzyBot.Dir.CW, velocidade * 0.6)
    fuzzyBot.motorRun(fuzzyBot.Motors.M2, fuzzyBot.Dir.CW, velocidade)
}
input.onButtonPressed(Button.A, function () {
    Iniciar = 0
    basic.showIcon(IconNames.Heart)
})
function esquerda_brusca () {
    fuzzyBot.motorRun(fuzzyBot.Motors.M1, fuzzyBot.Dir.CW, 0)
    fuzzyBot.motorRun(fuzzyBot.Motors.M2, fuzzyBot.Dir.CW, velocidade)
}
function direita () {
    fuzzyBot.motorRun(fuzzyBot.Motors.M1, fuzzyBot.Dir.CW, velocidade)
    fuzzyBot.motorRun(fuzzyBot.Motors.M2, fuzzyBot.Dir.CW, velocidade * 0.6)
}
input.onButtonPressed(Button.B, function () {
    Iniciar = 1
    basic.showIcon(IconNames.Happy)
})
function frente () {
    fuzzyBot.motorRun(fuzzyBot.Motors.All, fuzzyBot.Dir.CW, velocidade)
}
function direita_brusca () {
    fuzzyBot.motorRun(fuzzyBot.Motors.M1, fuzzyBot.Dir.CW, velocidade)
    fuzzyBot.motorRun(fuzzyBot.Motors.M2, fuzzyBot.Dir.CW, 0)
}
function seguidor_linha () {
    if (fuzzyBot.readPatrol(fuzzyBot.Patrol.PatrolLeft) == 0 && fuzzyBot.readPatrol(fuzzyBot.Patrol.PatrolMiddle) == 0 && fuzzyBot.readPatrol(fuzzyBot.Patrol.PatrolRight) == 0) {
        status_SL = 0
    } else if (fuzzyBot.readPatrol(fuzzyBot.Patrol.PatrolLeft) == 0 && fuzzyBot.readPatrol(fuzzyBot.Patrol.PatrolMiddle) == 0 && fuzzyBot.readPatrol(fuzzyBot.Patrol.PatrolRight) == 1) {
        status_SL = 1
    } else if (fuzzyBot.readPatrol(fuzzyBot.Patrol.PatrolLeft) == 0 && fuzzyBot.readPatrol(fuzzyBot.Patrol.PatrolMiddle) == 1 && fuzzyBot.readPatrol(fuzzyBot.Patrol.PatrolRight) == 0) {
        status_SL = 2
    } else if (fuzzyBot.readPatrol(fuzzyBot.Patrol.PatrolLeft) == 0 && fuzzyBot.readPatrol(fuzzyBot.Patrol.PatrolMiddle) == 1 && fuzzyBot.readPatrol(fuzzyBot.Patrol.PatrolRight) == 1) {
        status_SL = 3
    } else if (fuzzyBot.readPatrol(fuzzyBot.Patrol.PatrolLeft) == 1 && fuzzyBot.readPatrol(fuzzyBot.Patrol.PatrolMiddle) == 0 && fuzzyBot.readPatrol(fuzzyBot.Patrol.PatrolRight) == 0) {
        status_SL = 4
    } else if (fuzzyBot.readPatrol(fuzzyBot.Patrol.PatrolLeft) == 1 && fuzzyBot.readPatrol(fuzzyBot.Patrol.PatrolMiddle) == 0 && fuzzyBot.readPatrol(fuzzyBot.Patrol.PatrolRight) == 1) {
        status_SL = 5
    } else if (fuzzyBot.readPatrol(fuzzyBot.Patrol.PatrolLeft) == 1 && fuzzyBot.readPatrol(fuzzyBot.Patrol.PatrolMiddle) == 1 && fuzzyBot.readPatrol(fuzzyBot.Patrol.PatrolRight) == 0) {
        status_SL = 6
    } else if (fuzzyBot.readPatrol(fuzzyBot.Patrol.PatrolLeft) == 1 && fuzzyBot.readPatrol(fuzzyBot.Patrol.PatrolMiddle) == 1 && fuzzyBot.readPatrol(fuzzyBot.Patrol.PatrolRight) == 1) {
        status_SL = 7
    }
}
let status_SL = 0
let Iniciar = 0
let velocidade = 0
basic.pause(2000)
Camera.Begin(sentry_mode_e.kI2CMode, sengo2_addr_e.ADDR1)
Camera.VisionSetStatus(sengo2_status.Enable, sengo_vision_e.kVisionCard)
basic.showIcon(IconNames.Heart)
velocidade = 80
basic.forever(function () {
    if (Iniciar == 1) {
        if (Camera.Detected(sengo_vision_e.kVisionCard) > 0) {
            if (Camera.DetectedCard(card_label_e.kCardSpeed60, 1)) {
                velocidade = 60
            } else if (Camera.DetectedCard(card_label_e.kCardSpeed40, 1)) {
                velocidade = 40
            } else if (Camera.DetectedCard(card_label_e.kCardRedLight, 1)) {
                velocidade = 0
            } else {
            	
            }
        }
    }
})
basic.forever(function () {
    seguidor_linha()
    if (Iniciar == 1) {
        if (status_SL == 0) {
            frente()
        } else if (status_SL == 1) {
            esquerda()
        } else if (status_SL == 3) {
            esquerda_brusca()
        } else if (status_SL == 4) {
            direita()
        } else if (status_SL == 6) {
            direita_brusca()
        }
    } else {
        fuzzyBot.motorStop(fuzzyBot.Motors.All)
    }
})

```

## Passo 28
Agora seu código está pronto! Baixe-o para o micro:bit e posicione o FuzzyBoT sobre o início
do caminho definido pela linha. Pressione o botão B para ele iniciar o movimento.
Repare que durante o percurso o robô reduzirá a velocidade até parar ao fazer a leitura da última carta.

```blocks
```

## Passo 29
Se necessário, confira o seu código clicando na lâmpada de dica.

```blocks
function esquerda () {
    fuzzyBot.motorRun(fuzzyBot.Motors.M1, fuzzyBot.Dir.CW, velocidade * 0.6)
    fuzzyBot.motorRun(fuzzyBot.Motors.M2, fuzzyBot.Dir.CW, velocidade)
}
input.onButtonPressed(Button.A, function () {
    Iniciar = 0
    basic.showIcon(IconNames.Heart)
})
function esquerda_brusca () {
    fuzzyBot.motorRun(fuzzyBot.Motors.M1, fuzzyBot.Dir.CW, 0)
    fuzzyBot.motorRun(fuzzyBot.Motors.M2, fuzzyBot.Dir.CW, velocidade)
}
function direita () {
    fuzzyBot.motorRun(fuzzyBot.Motors.M1, fuzzyBot.Dir.CW, velocidade)
    fuzzyBot.motorRun(fuzzyBot.Motors.M2, fuzzyBot.Dir.CW, velocidade * 0.6)
}
input.onButtonPressed(Button.B, function () {
    Iniciar = 1
    basic.showIcon(IconNames.Happy)
})
function frente () {
    fuzzyBot.motorRun(fuzzyBot.Motors.All, fuzzyBot.Dir.CW, velocidade)
}
function direita_brusca () {
    fuzzyBot.motorRun(fuzzyBot.Motors.M1, fuzzyBot.Dir.CW, velocidade)
    fuzzyBot.motorRun(fuzzyBot.Motors.M2, fuzzyBot.Dir.CW, 0)
}
function seguidor_linha () {
    if (fuzzyBot.readPatrol(fuzzyBot.Patrol.PatrolLeft) == 0 && fuzzyBot.readPatrol(fuzzyBot.Patrol.PatrolMiddle) == 0 && fuzzyBot.readPatrol(fuzzyBot.Patrol.PatrolRight) == 0) {
        status_SL = 0
    } else if (fuzzyBot.readPatrol(fuzzyBot.Patrol.PatrolLeft) == 0 && fuzzyBot.readPatrol(fuzzyBot.Patrol.PatrolMiddle) == 0 && fuzzyBot.readPatrol(fuzzyBot.Patrol.PatrolRight) == 1) {
        status_SL = 1
    } else if (fuzzyBot.readPatrol(fuzzyBot.Patrol.PatrolLeft) == 0 && fuzzyBot.readPatrol(fuzzyBot.Patrol.PatrolMiddle) == 1 && fuzzyBot.readPatrol(fuzzyBot.Patrol.PatrolRight) == 0) {
        status_SL = 2
    } else if (fuzzyBot.readPatrol(fuzzyBot.Patrol.PatrolLeft) == 0 && fuzzyBot.readPatrol(fuzzyBot.Patrol.PatrolMiddle) == 1 && fuzzyBot.readPatrol(fuzzyBot.Patrol.PatrolRight) == 1) {
        status_SL = 3
    } else if (fuzzyBot.readPatrol(fuzzyBot.Patrol.PatrolLeft) == 1 && fuzzyBot.readPatrol(fuzzyBot.Patrol.PatrolMiddle) == 0 && fuzzyBot.readPatrol(fuzzyBot.Patrol.PatrolRight) == 0) {
        status_SL = 4
    } else if (fuzzyBot.readPatrol(fuzzyBot.Patrol.PatrolLeft) == 1 && fuzzyBot.readPatrol(fuzzyBot.Patrol.PatrolMiddle) == 0 && fuzzyBot.readPatrol(fuzzyBot.Patrol.PatrolRight) == 1) {
        status_SL = 5
    } else if (fuzzyBot.readPatrol(fuzzyBot.Patrol.PatrolLeft) == 1 && fuzzyBot.readPatrol(fuzzyBot.Patrol.PatrolMiddle) == 1 && fuzzyBot.readPatrol(fuzzyBot.Patrol.PatrolRight) == 0) {
        status_SL = 6
    } else if (fuzzyBot.readPatrol(fuzzyBot.Patrol.PatrolLeft) == 1 && fuzzyBot.readPatrol(fuzzyBot.Patrol.PatrolMiddle) == 1 && fuzzyBot.readPatrol(fuzzyBot.Patrol.PatrolRight) == 1) {
        status_SL = 7
    }
}
let status_SL = 0
let Iniciar = 0
let velocidade = 0
basic.pause(2000)
Camera.Begin(sentry_mode_e.kI2CMode, sengo2_addr_e.ADDR1)
Camera.VisionSetStatus(sengo2_status.Enable, sengo_vision_e.kVisionCard)
basic.showIcon(IconNames.Heart)
velocidade = 80
basic.forever(function () {
    if (Iniciar == 1) {
        if (Camera.Detected(sengo_vision_e.kVisionCard) > 0) {
            if (Camera.DetectedCard(card_label_e.kCardSpeed60, 1)) {
                velocidade = 60
            } else if (Camera.DetectedCard(card_label_e.kCardSpeed40, 1)) {
                velocidade = 40
            } else if (Camera.DetectedCard(card_label_e.kCardRedLight, 1)) {
                velocidade = 0
            } else {
            	
            }
        }
    }
})
basic.forever(function () {
    seguidor_linha()
    if (Iniciar == 1) {
        if (status_SL == 0) {
            frente()
        } else if (status_SL == 1) {
            esquerda()
        } else if (status_SL == 3) {
            esquerda_brusca()
        } else if (status_SL == 4) {
            direita()
        } else if (status_SL == 6) {
            direita_brusca()
        }
    } else {
        fuzzyBot.motorStop(fuzzyBot.Motors.All)
    }
})

```

```package
fuzzyBot=github:FuzzyMakers/pxt-fuzzyMakers
```