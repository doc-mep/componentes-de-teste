---
title: Alteracoes DAQ-2.0
tags: JG_STD, DAQ, DAQ_2.0
description: Documento que reune as alterações necessárias para o melhor funcionamento do DAQ-2.0.
---

# Alterações DAQ-2.0

## Firmware

Obter o firmware **mais recente** no Git Inova, [clique aqui](https://git.inova.ind.br/Inova/_FW_RENESAS_R5F52316ADFM_INV-133_133v02/releases).

Utilize um gravador renesas E2-lite e conecte ao CN2 conforme a imagem a seguir:

![](https://i.imgur.com/rak7WOp.png)


## Alterações Elétricas

### Isolar CI31

O dissipador do CI fecha curto nos componentes que estão logo abaixo.

![](https://i.imgur.com/tkjuV50.png)


### Cortar trilha USB

> É muito importante corta a trilha indicada na imagem


Conforme a imagem:

![](https://i.imgur.com/oF2bVDU.png)


### Simulador de temperaturas

> Substituir o CI40 pelo CI TS272CDT NHC

* Romper trilha que interliga o terminal 1 com o terminal 5 do CI40;
* Interligar o terminal 3 com o terminal 5 do CI40;
* Interligar o terminal 1 com o terminal 7 do CI40;
* Remover R296;
* Substituir R238 por um jumper.

![](https://i.imgur.com/ELrbtT0.png)


## Circuito saída analógica 0~10 V
Para maximizar a compatibilidade do novo DAQ com o antigo, deve-se alterar o ganho do amplificador (CI42) para evitar que a tensão gerada ultrapasse os 10 V
* Trocar o resistor R260 de 15kΩ para um resistor de 10kΩ para mudar o ganho do CI42
* Trocar o resistor R280 de 15kΩ para um resistor de 10kΩ para mudar o ganho do CI43

![](https://i.imgur.com/UarG6Eq.png)

* Soldar um resistor de 1MΩ em paralelo aos diodos D82 e D86

![](https://i.imgur.com/D6oTtT4.png)

## Circuito entrada analógica 0~10 V
A fim de evitar flutuações no valor de leitura, deve-se soldar um capacitor de 100nF em paralelo ao resistor existente na *label* C104

![](https://i.imgur.com/ppFV5oP.png)



## Driver para relés

Devido a sensibilidade da peça com relação à ruídos no GND, foi identificada a necessidade de montagem dos capacitores C8 e C9

* Remover os capacitores C5 e C6 da etapa V

![](https://i.imgur.com/5HEFGVc.png)

* Colocar os capacitores removidos no lugar de C8 e C9

![](https://i.imgur.com/KnDfqVL.png)

# Equalização entradas analógicas

Alteração que "transforma" a entrada analógica 1 que possue originalmente um range de leitura de 0 a 10V, em uma similar as demais, com range de 0 a 60V.

* Romper trilha entre pad do capacitor C104 e pino 3 do ampop, e inserir resistor de 10K em série.
* Adição de um resistor de 13K em paralelo com o capacitor C104
* Alteração do valor do resistor R229 de 10K para 150K
* Retirar o resistor R235

![](https://i.imgur.com/WYLPCLa.png)

Indicação/sugestão de alterações em placa:

![](https://i.imgur.com/YdeXXtH.png)

