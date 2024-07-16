---
title: Un algoritmo de optimización inspirado en bacterias
published: 2024-05-01
description: 'Esta entrada se centra en el algoritmo de optimización inspirado en bacterias *Escherichia coli* propuesto por Ying Chu et al. (2008). El contenido está basada en el proyecto semestral realizado por mí y Carlos Desideiro para la materia de Cómputo Evolutivo (enero a junio del 2024) impartida por el profesor Oscar Hernández Constantino. '
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

No obstante, **BFA es computacionalmente costoso** y su convergencia puede mejorarse. Ying Chu *et al.* (2008) propusieron el **algoritmo Fast Bacterial Swarming Algorithm (FBSA)**, que integra Particle Swarming Algorithm (PSO) a BFA para **solucionar estas limitaciones**. 

Por tal motivo, en este proyecto se tuvo por objetivo **implementar los algoritmos** de Bacterial Foraging Algorithm (**BFA**), Fast Bacterial Swarming Algorithm (**FBSA**), y Particle Swarming Algorithm (**PSO**), para posteriormente **evaluar y comparar su desempeño** en funciones de referencia de optimización continua.

## Implementación de FBSA

::github{repo="Fabrizz/MMM-OnSpotify"}

Create a GitHub repository card with the code `::github{repo="<owner>/<repo>"}`.

```markdown
::github{repo="saicaca/fuwari"}


```
### 1. BFA

Las bacterias son organismos biológicos microscópicos que necesitan encontrar y aprovechar los nutrientes
disponibles en su entorno para su supervivencia, crecimiento y reproducción. Las bacterias *E. coli*, en su proceso de forrajeo, siguen un comportamiento básico denominado quimiotaxis que les permite detectar y moverse hacia sitios ricos en nutrientes. 

BFA se inspira en estos procesos biológicos y plantea cuatro etapas importantes en el proceso de optimización: 
- quimiotaxis
- enjambre o *swarming* 
- reproducción, y
- eliminación-dispersión.

Al estar dentro del marco del Cómputo Evolutivo, el objetivo de BFA es **encontrar una solución óptima** para un problema de optimización específico (función objetivo) a partir de **evolucionar una población de bacterias** que, en cada generación, intentan **aumentar** su **aptitud** o **fitness**. El valor de fitness de una bacteria dependerá si la zona en la que se encuentra es **rica en nutrientes o no**. Por lo tanto, para cada bacteria en la población es necesario registrar su posición actual y su fitness correspondiente.



#### 1.1 Quimiotaxis

La bacteria *E. coli* se desplaza utilizando dos maneras distintas de movimiento: **tumble** y **run**. Un **tumble** consiste en elegir una dirección aleatoria para moverse, mientras que un **run** consiste en nado en una dirección específica. Así, un proceso de quimiotaxis para una bacteria comienza con un movimiento tipo tumble, seguido de un nado (run) en la dirección aleatoria que se definió en el tumble. 

![Alt Text](https://mhrussel.wordpress.com/wp-content/uploads/2013/02/attractant-swim.gif)

Inspirado en este proceso biológico, el algoritmo BFA plantea una etapa de quimiotaxis en la que la bacteria primero da un paso unitario en una dirección aleatoria $\angle \varphi$ y posteriormente realiza un nado o run en esa dirección. El número máximo de pasos que puede dar una bacteria en el nado está delimitado por el parámetro $N_s$. 

La notación para representar la forma en la que se actualiza la posición de una bacteria con un movimiento tumble o run es la siguiente:
$$
\theta^i(j+1, k, l)=\theta^i(j, k, l)+C \times \angle \varphi
$$
donde $\theta^i(j, k, l)$ es la posición de la $i$-ésima bacteria de la población, en el $j$-ésimo paso de quimiotaxis, sobre el $k$-ésimo cíclo de reproducción, del $l$-ésimo evento de eliminación-dispersión,
$C$ es el tamaño de paso al que se mueve la bacteria y $\angle \varphi$ es la dirección aleatoria que se generó sobre el espacio de búsqueda.

Cada vez que la bacteria cambia de posición, es necesario actualizar su fitness. Dicho fitness resultará de aplicar la función objetivo sobre la posición de la bacteria $\theta(j, k, l)$. El fitness se denota como $J^i(j, k, l)$ y el mejor fitness en toda la población será representado por $J_{m i n}$. Una vez que la bacteria da el tumble y comienza el nado, la bacteria se moverá paso a paso, actualizando su fitness y verificando si mejora o no. Si el fitness empeora, la bacteria detiene su nado y su paso de quimiotaxis estará terminado. Si el fitness mejora, la bacteria continuará moviéndose hasta completar los $N_s$ pasos. 




 

```markdown
## BACTERIAL FORAGING ALGORITHM (BFA)

# inicializar y seleccionar bacteria mejor fitness
pop = inicializar_población_aleatoria() 
best = mejor_bacteria_de_la_población()

## inicializar ciclos:
for l = 1 to Ned: # ciclos eliminacióm-dispersión
   for k = 1 to Nre: # ciclos de reproducción
      for j = 1 to Nc: # ciclos de quimiotaxis
         # aplicar quimiotaxis en cada bacteria de la población
         for i = 1 to S:
         
            # quimiotaxis para la bacteria bi en pop
            #calcular fitness y efecto combinado (J_cc)
            Jlast = J(bi) + J_cc(bi,b)
            
            # movimieto tumble
            Vd = generar_direccion_aleatoria
            Nueva_posicion_bacteria = posición_anterior + (C * Vd)
            
            #swarm
            # calcular nuevo fitness y J_cc, y asignarlo como Jcurrent
            Jcurrent = J(bi) + J_cc(bi,b)
            
            # nado (run)
            Si Jcurrent < Jlast:  # nadará más en esa dirección
               
               # inicia nado de la bacteria (run)
               m=0 # contador de pasos de nado 
               
               mientras Jcurrent < Jlast y también m < Ns:
                  Jlast = Jcurrent  # modificar criterio de nado
                  Nueva_posicion_bacteria = posición_aterior + (C*Vd)
                  
                  #swarm
                  # calcular nuevo fitness y J_cc de su nueva posición
                  Jcurrent = J(bi) + J_cc(bi,b)
                  
            # después de que termina el nado de bi sumar salud
            Jhealth(bi) += Jcurrent
            
         # termina quimiotaxis de cada bacteria bi
        
         # si la bacteria bi ahora es mejor que best, es la mejor encontrada
         if Jcurrent < J(best): 
            best = bi 
         
      # termina ciclo de quimiotaxis
      
      # reproducir bacterias con mejor salud
      pop = reproducir(bacterias_ordenadas_por_mejor_salud) 
      
      # restaurar salud de las bacterias de la nueva población
   
   # fin de ciclo de reproducción
   for bi in pop:
      Dispersar(bi) # con probabilidad Ped 

Regresar mejor bacteria encontrada
```

### FBSA

```markdown
## FAST BACTERIAL SWARMING ALGORITHM

# inicializar población y seleccionar bacteria mejor fitness
pop = inicializar_población_aleatoria() 
best = mejor_bacteria_de_la_población()
C = Lred

## inicializar ciclos:
for l = 1 to Ned: # ciclos eliminacióm-dispersión
   for k = 1 to Nre: # ciclos de reproducción
      for j = 1 to Nc: # ciclos de quimiotaxis
         # aplicar quimiotaxis en cada bacteria de la población
         for i = 1 to S:
            
            # quimiotaxis para la bacteria bi en pop
            #calcular fitness 
            Jlast = J(bi) 
            
            # movimieto tumble
            Vd = generar_direccion_aleatoria
            nueva_posicion = posición_anterior + (C * Vd)
            Jcurrent = J(nueva_posicion)
            
            # swarm principio de enjembre nuevo
            #Mover la nueva posición hacia la mejor bacteria
            nueva_posicion =  nueva_posicion + C_cc (posición anterior – mejor posición)
            
            # volver a calcular fitnes de la nueva posición 
            Jcurrent = J(nueva_posicion)
            Si Jcurrent < Jlast:  # nadará más en esa dirección
               # inicia nado de la bacteria (run)
               m=0 # contador de pasos de nado 
               
               mientras Jcurrent < Jlast y también m < Ns:
                  Jlast = Jcurrent  # modificar criterio de nado
                  nueva_posicion = posición_aterior + (C*Vd)
                  # calcular nuevo fitness de su nueva posición
                  Jcurrent = J(bi)
               
               # recalcular posición respecto a la mejor bacteria
               nueva_posicion =  nueva_posicion + C_cc (posición anterior – mejor posición)
              
               # volver a calcular fitnes de la nueva posición 
               Jcurrent = J(nueva_posicion)
               
               # después de que termina el nado sumar salud
               Jhealth(bi) += Jcurrent
         
         # termina quimiotaxis de cada bacteria bi
         best = calcular _mejor_bacteria _de_quimiotaxis()
         # termina ciclo de quimiotaxis
      
      # reproducir bacterias con mejor salud
      pop = reproducir(bacterias_ordenadas_por_mejor_salud) 
      # restaurar salud de las bacterias de la nueva población
      C = actualizar_Ckl() # paso adaptativo
   
   # fin de ciclo de reproducción
   Para cada bi en pop:
      Dispersar(bi) # con probabilidad Ped 
   C = actualizar_Ckl() # paso adaptativo
Regresar mejor bacteria encontrada

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