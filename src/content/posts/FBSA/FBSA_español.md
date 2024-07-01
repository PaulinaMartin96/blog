---
title: Un algoritmo de optimización inspirado en bacterias
published: 2024-05-01
description: 'Este trabajo está basado en el proyecto semestral realizado por mí, Paulina Martín, y Carlos Desideiro en el semestre 2024-1 (enero a junio del 2024) para la materia de Cómputo Evolutivo impartida por M. en C. Oscar Hernández Constantino. Esta entrada se centra en el algoritmo de optimización inspirado en bacterias *Escherichia coli* propuesto por Ying Chu *et al.* (2008)'
image: ''
tags: [Cómputo evolutivo, algoritmos bio-inspirados, FBSA, español]
category: 'Ciencias de la computación y Biología'
draft: false 
---

> Cover image source: ![alt text]("cdc-7tgIlnxj2bM-unsplash.jpg")

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