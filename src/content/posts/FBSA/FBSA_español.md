---
title: Un algoritmo de optimización inspirado en bacterias
published: 2024-05-01
description: 'Esta entrada está basado en el proyecto semestral realizado por mí y Carlos Desideiro para la materia de Cómputo Evolutivo (enero a junio del 2024) impartida por el profesor Oscar Hernández Constantino. Esta entrada se centra en el algoritmo de optimización inspirado en bacterias *Escherichia coli* propuesto por Ying Chu et al. (2008).'
image: './cdc-7tgIlnxj2bM-unsplash.jpg'
tags: [Cómputo evolutivo, algoritmos bio-inspirados, FBSA, español]
category: 'Ciencias de la computación y Biología'
draft: false 
---

> Cover image source: [Source](https://images.unsplash.com/photo-1631824683860-9a7aa1fe0713?q=80&w=3438&auto=format&fit=crop&ixlib=rb-4.0.3&ixid=M3wxMjA3fDB8MHxwaG90by1wYWdlfHx8fGVufDB8fHx8fA%3D%3D)

## Fast Bacterial Swarming Algorithm (FBSA) como un algoritmo de optimización bio-inspirado

En los últimos años, se han propuesto **algoritmos bio-inspirados** que representan un enfoque prometedor para resolver problemas de optimización complejos, no lineales y de alta dimensionalidad. 

Un algoritmo que ha sido bastante exitoso es el **algoritmo de forrajeo bacteriano (BFA)**, que se inspira en el comportamiento de las bacterias *Escherichia coli* cuando buscan alimento en los intestinos humanos.

BFA se ha aplicado a **diversos tipos de problemas de optimización** como el control adaptativo, la estimación de señales armónicas, el diseño óptimo de estabilizadores de sistemas de potencia y el flujo de potencia óptimo.

No obstante, **BFA es computacionalmente costoso** y su convergencia puede mejorarse. Ying Chu *et al.* (2008) propusieron el **algoritmo Fast Bacterial Swarming Algorithm (FBSA)**, que integra Particle Swarming Algorithm (PSO) a BFA para solucionar estas limitaciones. 

Por tal motivo, en este proyecto nos propusimos **implementar los algoritmos** de Bacterial Foraging Algorithm (**BFA**), Fast Bacterial Swarming Algorithm (**FBSA**), y Particle Swarming Algorithm (**PSO**), para posteriormente **evaluar y comparar su desempeño** en funciones de referencia de optimización continua.

## Implementación de FBSA

::github{repo="Fabrizz/MMM-OnSpotify"}

Create a GitHub repository card with the code `::github{repo="<owner>/<repo>"}`.

```markdown
::github{repo="saicaca/fuwari"}


```

### Pseudocódigo

```markdown
## Algoritmo para seleccionar un individuo de una población (Roulette)
Entrada: s  población sobre la que seleccionará un individuo (arreglo de individuos).
Salida:  individuo seleccionado 

## se calcula la suma de fitness
w = suma de los fitness de todos los individuos de la población

## inicializar el vector que guardara las probabilidades de cada individuo
p = f_i / w, para cada individuo en la población 

## inicializamos el arreglo que guardara las probabilidades acumuladas
 q = suma de p[0] hasta p[i] para cada individuo s[i] en la población
 
## generar aleatorio (girar ruleta)
r = aleatorio entre cero y uno

## generar variables para iterar i buscar el vecino que se seleccionó con la ruleta
índice = 0
acumulación = p[0] (acumulación del primer individuo)

## proceso iterativo para buscar al individuo seleccionado 
Mientras que acumulación sea menor que el aleatorio r:

     Si r es mayor que la acumulación de probabilidades:
          índice ++  (cambiar al siguiente índice de probabilidad acumulativa)
          acumulación = la siguiente entrada del arreglo de acumulaciones q[índice]
          
cuando se encuentra que la acumulación es mayor o igual se devuelve el individuo s[índice]    
```

## Referencias

- Y. Shi and R. Eberhart, "A modified particle swarm optimizer," 1998 IEEE International Conference on Evolutionary Computation Proceedings. IEEE World Congress on Computational Intelligence (Cat. No.98TH8360), Anchorage, AK, USA, 1998, pp. 69-73, doi: 10.1109/ICEC.1998.699146.

- K. M. Passino, "Biomimicry of bacterial foraging for distributed optimization and control," in IEEE Control Systems Magazine, vol. 22, no. 3, pp. 52-67, June 2002, doi: 10.1109/MCS.2002.1004010.

- Chu,Z. Ji, H. Liao, Y. Wang and Q. H. Wu, "A novel intelligent particle optimizer for global optimization of multimodal functions," 2007 IEEE Congress on Evolutionary Computation, Singapore, 2007, pp. 3272-3275, doi: 10.1109/CEC.2007.4424892.

- Ying Mi, H. Ji, Zhuolin Wu, Q. (2010). Fast bacterial swarming algorithm based on particle swarm optimization. 25. 442-448.

- Mengshi, L. (2009). Bacteria-inspired Algorithms and Their Applications to Power System Optimisation [Doctoral Dissertation, University of Liverpool]. https://livrepository.liverpool.ac.uk/3062721/1/U566269.pdf.

- Agrawal, Vivek Sharma, Harish Bansal, Jagdish. (2012). Bacterial Foraging Optimization: A Survey. Proceedings of the International Conference on Soft Computing for Problem Solving (SocProS 2011) December 20-22, 2011. 130. 227-242. 10.1007/978-81-322-0487-923.

- Chen, Guo Tang, Heng Niu, Ben Lee, Chang. (2021). A survey of bacterial foraging optimization. Neuro-computing. 452. 10.1016/j.neucom.2020.06.142

## Admonitions

Following types of admonitions are supported: `note` `tip` `important` `warning` `caution`

:::note
Highlights information that users should take into account, even when skimming.
:::

:::tip
Optional information to help a user be more successful.
:::

:::important
Crucial information necessary for users to succeed.
:::

:::warning
Critical content demanding immediate user attention due to potential risks.
:::

:::caution
Negative potential consequences of an action.
:::

```markdown
:::note
Highlights information that users should take into account, even when skimming.
:::

:::tip
Optional information to help a user be more successful.
:::
```

The title of the admonition can be customized.

:::note[MY CUSTOM TITLE]
This is a note with a custom title.
:::

```markdown
:::note[MY CUSTOM TITLE]
This is a note with a custom title.
:::
```