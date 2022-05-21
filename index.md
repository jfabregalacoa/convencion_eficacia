---
title: "¿Han emitido su voto todas las señoras y señores convencionales? Estimación de la eficacia relativa al momento de votar de cada miembro de la Convención Constitucional"
author: "Jorge Fábrega - CICS - Facultad de Gobierno - UDD"
date: "20-05-2022"
output: html_document
---

# Introducción

Cada convencional va dejando huellas de su desempeño como miembro del cuerpo colegiado a medida que va votando $a$ $favor$, $en$ $contra$ o $abstención$ frente a cada artículo o inciso. Cabe entonces preguntarse ¿quiénes son los que al final logran un mejor desempeño o, dicho de otro modo, quiénes son los que demuestran un rol más relevante en las decisiones tomadas por la convención? 

Esta disyuntiva se puede enfrentar con un análisis ex-ante o un análisis ex-post. En un análisis ex-ante, lo que hacemos es identificar a los actores pivotales a partir de sus preferencias ideológicas y dadas las reglas de votación. Para un ejercicio de ese tipo aplicado a la Convención Constitucional véase [aquí](https://www.researchgate.net/project/Polarizacion-en-Chile/update/61211191181c2e4f4a8236fa). Ese tipo de análisis entrega una idea general de la distribución de poder dentro de un cuerpo colegiado como la Convención. Y es relevante para entender la dirección general que tomarán las decisiones colectivas que se den en dicha instancia (más al respecto puede verse en Fábrega 2022, [aqui](http://rda.uc.cl/index.php/rcp/article/view/50189).

En un análisis ex-post, observamos las votaciones y calculamos quienes una vez consumados los hechos tuvieron una posición de mayor relevancia. Los resultados en términos generales deberían coincidir con los obtenidos mediante un análisis ex-ante, pero no serán necesariamente iguales porque si bien es cierto que el votante pivotal es central en el resultado, no es menos cierto que no todas las reglas aprobadas obtienen exactamente el mínimo quórum requerido. 

En particular, la decisión de un convencional (pivotal o no) de votar a favor o en contra en el debate de normas específicas no está completamente explicado por su preferencia ideológica. Por ejemplo, el intercambio de favores puede llevar a dos convencionales a apoyar mutuamente ideas que, en principio, están más alejadas de sus preferencias ideológicas en un intercambio mutuamente beneficioso ("voto por tu idea en X, pero tú votas por mi idea en Y"). Así mismo, abstenerse de apoyar una iniciativa presentada por los miembros de tu propia lista o coalición puede deberse, por ejemplo, a un comportamiento estratégico que desea evitar un costo político individual. Alternativamente, un convencional podría decidir abstenerse para quedar en una mejor posición negociadora en la siguiente etapa de evaluación de una propuesta de norma. Y también es posible imaginar otras variantes respecto del voto de abstención, introduciendo nuevas fuentes de variación para explicar cómo votan los convencionales. 

Para explorar estos aspectos, y dado que ha culminado la etapa de generación de contenidos de la Convención Constitucional, en el presente documento calculo lo que denominaré la $eficacia$ $relativa$ $al$ $votar$ de cada convencional. 

Sea $j$ un convencional, $V_j = ('A Favor','En contra', 'Abstención')$ sus opciones de votación y $S = ('Aprobado', 'Rechazado')$ los posibles resultados de la votación. Entonces, $V_j = 'A Favor'$ cuando $S='Aprobado'$ y $V_j = 'En Contra'$ cuando $S='Rechazado'$ contribuyen a la eficacia del convencional al votar porque habría votado alineado con el resultado de la votación. 

$NOTA$: Hago el hincapié que es una métrica de eficacia $al$ $votar$ para distinguirla de la eficacia legislativa que se refiere a la capacidad de cada convencional de lograr que las normas que él o ella impulsó sean finalmente aprobadas. 

El caso en el que el convencional se haya abstenido amerita un trato especial. Los motivos para abstenerse pueden variar desde (i) no estar convencido sobre el articulado, (ii) no tener una opinión formada sobre el mismo o incluso (iii) el que decidir apoyarlo o rechazarlo explícitamente puede ir en contra de las propias declaraciones o acciones pasadas y, por lo tanto, el o la convencional preferiría no aparecer tomando una acción contradictoria. En el primer y segundo caso, el abstenerse se ajusta al significado explícito de la opción “Abstención”, pero en el último estamos frente a un comportamiento estratégico. La relevancia de esta distinción es que, cuando un convencional se abstiene con el objeto de evitar que se apruebe una norma en su actual formulación, su abstención no sólo es estratégica, sino que también es eficaz (en el caso de que ésta sea rechazada). Por ende, tal abstención debería considerarse como parte del cálculo de su eficacia al votar. Esto impone un desafío sobre cómo distinguir cuáles abstenciones son estratégicas y cuáles no.

Para identificar abstenciones estratégicas, supongamos que $F$ y $C$ representan a los votantes medianos entre los que votaron 'A Favor' y 'En Contra', respectivamente. Además, definamos $I_j$ como la preferencia ideológica del individuo $j$. 

Entonces, consideraremos como abstención estratégica a aquella acción del convencional $j$ tal que $|I_F - I_j| < |I_C - I_j|$. Es decir, el convencional $j$ decide abstenerse pese a que la posición mediana a favor de la propuesta de norma está más cerca de su ideal, que la posición mediana que está en contra. En este caso particular, el o la convencional no estará apoyando una norma que, en principio, mueve los resultados más cerca de su propia postura y, por ende, puede ser un buen proxy de comportamiento estratégico. De este modo, si en $100$ votos, un convencional estuvo en el bando ganador $70$ veces y en 5 ocasiones se abstuvo, pero sólo en 2 de ellas lo hizo por razones estatrégicas, entonces su eficacia estimada es de $(70 + 2)/100 = 72\%$.  

# Datos
Para implementar la métrica de $eficacia$ $al$ $votar$ indicada en la sección anterior, hacemos uso de los datos de votaciones de los plenos de la Convención Constitucional disponibles en [Sala Constituyente](https://sala.cconstituyente.cl/). Para el presente ejercicio se han usado todas las votaciones plenarias hasta el 14 de mayo del 2022 (fecha en que se dio por finalizada la etapa de deliberación en torno a los contenidos del texto). Se consideraron todas las votaciones en que las alternativas eran votar "A favor", "En Contra" o "Abstención". (Nota: las únicas votaciones que no cumplen con este criterio son las relacionadas a la elección de la mesa directiva de la convención en las que se votaba por personas). 

# Resultados
El resultado se resume en la figura 1; se ordenan los convencionales en forma ascendente desde el que tuvo una menor eficacia (Jorge Arancibia) al que tuvo la mayor (Ricardo Montero). 


![Eficacia](https://github.com/jfabregalacoa/convencion_eficacia/blob/main/plots/eficacia_todos.png)

Una rápida inspección de la figura permite constatar que la eficacia al votar de los convencionales vinculados a la derecha ideológica es sistemáticamente menor que la de los convencionales vinculados a la izquierda ideológica, lo cual es consistente con el desarrollo general que ha mostrado la Convención Constitucional. De hecho, el resultado presenta una alta pero no perfecta correlación inversa con la posición ideológica ($\rho$ = -0.7570558). Sin perjuicio de lo anterior, la figura también muestra que la relación no es lineal sino que hay dispersión de la eficacia, particularmente en la izquierda de la Convención. Ello amerita que se haga una indagación más específica al interior de cada grupo de convencionales.

![Ideología y Eficacia](https://github.com/jfabregalacoa/convencion_eficacia/blob/main/plots/efic_ideol.png)

## Una mirada a la eficacia en grupos seleccionados

En el funcionamiento de la Convención Constitucional han tenido un rol gravitante los miembros del Colectivo Socialista y el Frente Amplio. Ello era esperable puesto que estos grupos son los que se encuentran en posiciones ideológicas pivotales. Focalicemos el análisis en estos grupos ¿cómo ha sido su eficacia al votar en relación con la de otros grupos?  

En la tabla siguiente se comparan las eficacias promedios de grupos seleccionados al votar. Como puede verse, la mayor eficacia al votar recae precisamente sobre el Frente Amplio y el Colectivo Socialista que el análisis pivotal ex-ante destacaba como los grupos que serían más gravitantes en la Convención.  

               Grupo              Eficacia al votar
         Frente Amplio                75.835
         Colectivo Socialista         72.865
         No Neutrales                 68.045
         Movimientos Sociales         66.3
         Pueblo Constituyente         65.299
         Chile Digno                  63.304
         Coor. Plurinacional          61.724
         Derecha                      42.704

Si bien como grupos el Frente Amplio y el Colectivo Socialista tienen la mayor eficacia, hay diferencias relevantes entre sus miembros. Estas se ven resumidas en los gráficos siguientes. 

![Colectivo Socialista](https://github.com/jfabregalacoa/convencion_eficacia/blob/main/plots/g_csoc.png)

![Frente Amplio](https://github.com/jfabregalacoa/convencion_eficacia/blob/main/plots/g_fa.png)

# Conclusiones

El análisis ex-ante y el análisis ex-post de los procesos de votación entregan información complementaria para entender las dinámicas de un cuerpo colegiado. En el caso de la Convención Constitucional se puede constatar que a medida que ésta se fue desplegando, los convencionales con mejor desempeño coinciden con los ubicados en posiciones de privilegio de acuerdo con un análisis de actores pivotales. Siendo consistente con lo anterior, el análisis ex-post permite además diferenciar entre actores más y menos relevantes dentro de sus grupos de pertenencia en la Convención. 
