---
title: "¿Han emitido su voto todas las señoras y señores convencionales? Estimación de la eficacia relativa al momento de votar de cada miembro de la Convención Constitucional"
author: "Jorge Fábrega - CICS - Facultad de Gobierno - UDD \n Borrador"
date: "20-05-2022"
output: html_document
---

Nota: Este manuscrito está aún en desarrollo.

# Introducción

Cada convencional va dejando huellas de su desempeño como miembro del cuerpo colegiado a medida que va votando $a$ $favor$, $en$ $contra$ o $abstención$ frente a cada artículo o inciso. Cabe entonces preguntarse ¿quiénes son los que al final logran un mejor desempeño o, dicho de otro modo, quiénes son los que demuestran un rol más relevante en las decisiones tomadas por la convención? 

Esta disyuntiva se puede enfrentar con un análisis ex-ante o un análisis ex-post. En un análisis ex-ante, lo que hacemos es identificar a los actores pivotales a partir de sus preferencias ideológicas y dadas las reglas de votación. Así, por ejemplo, podemos identificar a quienes se encuentran en la mediana de la distribución ideológica en las comisiones y quienes se encuentan en torno a los 2/3 en la distribución del plenario. Esas personas son actores pivotales y estudiar lo que dicen y hacen debería ser, ex-ante, un buen uso de herramientas analíticas para prospectar los resultados a los que llegue el cuerpo colegiado. Para un ejercicio de ese tipo aplicado a la Convención Constitucional véase [aquí](https://www.researchgate.net/project/Polarizacion-en-Chile/update/61211191181c2e4f4a8236fa). Ese tipo de análisis entrega una idea general de la distribución de poder dentro de un cuerpo colegiado como la Convención. Y es relevante para entender la dirección general que tomarán las decisiones colectivas que se den en dicha instancia (más al respecto puede verse en Fábrega (2022), [aqui](http://rda.uc.cl/index.php/rcp/article/view/50189).

Por otro lado, en un análisis ex-post, observamos las votaciones y calculamos quienes una vez consumados los hechos tuvieron una posición de mayor relevancia. Los resultados en términos generales deberían coincidir con los obtenidos mediante un análisis ex-ante, pero no serán necesariamente iguales porque si bien es cierto que el votante pivotal es central en el resultado, no es menos cierto que no todas las reglas aprobadas obtienen exactamente el mínimo quórum requerido en la instancia correspondiente (sea éste uno de mayoría simple o alguna regla supermayoritaria). 

En particular, la decisión de un convencional (pivotal o no) de votar a favor o en contra en el debate de normas específicas no está completamente explicado por su preferencia ideológica. Por ejemplo, el intercambio de favores puede llevar a dos convencionales a apoyar mutuamente ideas que, en principio, están más alejadas de sus preferencias ideológicas en un intercambio mutuamente beneficioso ("voto por tu idea en X, pero tú votas por mi idea en Y"). Así mismo, abstenerse de apoyar una iniciativa presentada por los miembros de tu propia lista o coalición puede deberse, por ejemplo, a un comportamiento estratégico que desea evitar un costo político individual. Alternativamente, un convencional podría decidir abstenerse para quedar en una mejor posición negociadora en la siguiente etapa de evaluación de una propuesta de norma. Y también es posible imaginar otras variantes respecto del voto de abstención, introduciendo nuevas fuentes de variación para explicar cómo votan los convencionales. 

Para explorar estos aspectos, y dado que ha culminado la etapa de generación de contenidos de la Convención Constitucional, en el presente documento calculo lo que denominaré la $eficacia$ $relativa$ $al$ $votar$ de cada convencional. 

Formalmente: Sea $j$ un convencional, $V_j = ('A Favor','En contra', 'Abstención')$ sus opciones de votación y $S = ('Aprobado', 'Rechazado')$ los posibles resultados de la votación. Entonces, $V_j = 'A Favor'$ cuando $S='Aprobado'$ y $V_j = 'En Contra'$ cuando $S='Rechazado'$ contribuyen a la eficacia del convencional al votar (EV) porque habría votado alineado con el resultado de la votación. 

$NOTA$: Hago el hincapié que es una métrica de eficacia $al$ $votar$ para distinguirla de la eficacia legislativa que se refiere a la capacidad de cada convencional de lograr que las normas que él o ella impulsó sean finalmente aprobadas. 

El caso en el que el convencional se haya abstenido amerita un trato especial. Los motivos para abstenerse pueden variar desde (i) no estar convencido sobre el articulado, (ii) no tener una opinión formada sobre el mismo o incluso (iii) el que decidir apoyarlo o rechazarlo explícitamente puede ir en contra de las propias declaraciones o acciones pasadas y, por lo tanto, el o la convencional preferiría no aparecer tomando una acción contradictoria. En el primer y segundo caso, el abstenerse se ajusta al significado explícito de la opción “Abstención”, pero en el último estamos frente a un comportamiento estratégico. La relevancia de esta distinción es que, cuando un convencional se abstiene con el objeto de evitar que se apruebe una norma en su actual formulación, su abstención no sólo es estratégica, sino que también es eficaz (en el caso de que ésta sea rechazada). Por ende, tal abstención debería considerarse como parte del cálculo de su eficacia al votar. Esto impone un desafío sobre cómo distinguir cuáles abstenciones son estratégicas y cuáles no.

Para identificar abstenciones estratégicas, supongamos que $F$ y $C$ representan a los votantes medianos entre los que votaron 'A Favor' y 'En Contra', respectivamente. Además, definamos $I_j$ como la preferencia ideológica del individuo $j$. 

Entonces, consideraremos como abstención estratégica a aquella acción del convencional $j$ tal que $|I_F - I_j| < |I_C - I_j|$. Es decir, el convencional $j$ decide abstenerse pese a que la posición mediana a favor de la propuesta de norma está más cerca de su ideal, que la posición mediana que está en contra. En este caso particular, el o la convencional no estará apoyando una norma que, en principio, mueve los resultados más cerca de su propia postura y, por ende, puede ser un buen proxy de comportamiento estratégico. De este modo, si en $100$ votos, un convencional estuvo en el bando ganador $70$ veces y en 5 ocasiones se abstuvo, pero sólo en 2 de ellas lo hizo por razones estatrégicas, entonces su eficacia estimada es de $(70 + 2)/100 = 72\%$.  

En suma, para un total de $N$ votaciones: 
$EV = (\sum(V_j= "A Favor"|APROBADO) + (V_j= "En contra"|RECHAZADO) + V_j=("Abstención estratégica"|RECHAZADO)/N$


# Datos
Para implementar la métrica de $eficacia$ $al$ $votar$ indicada en la sección anterior, hacemos uso de los datos de votaciones de los plenos de la Convención Constitucional disponibles en [Sala Constituyente](https://sala.cconstituyente.cl/). Para el presente ejercicio se han usado todas las votaciones plenarias hasta el 14 de mayo del 2022 (fecha en que se dio por finalizada la etapa de deliberación en torno a los contenidos del texto). Se consideraron todas las votaciones en que las alternativas eran votar "A favor", "En Contra" o "Abstención". (Nota: las únicas votaciones que no cumplen con este criterio son las relacionadas a la elección de la mesa directiva de la convención en las que se votaba por personas). 


# Resultados  
El resultado se resume en la figura 1; se ordenan los convencionales en forma ascendente desde el que tuvo una menor eficacia (Jorge Arancibia) al que tuvo la mayor (Ricardo Montero). 


![](https://github.com/jfabregalacoa/convencion_eficacia/blob/main/plots/eficacia_todos.png)


# Eficacia y preferencias ideológicas  
Una rápida inspección de la figura anterior permite constatar que la eficacia al votar de los convencionales vinculados a la derecha ideológica es sistemáticamente menor que la de los convencionales vinculados a la izquierda ideológica, lo cual es consistente con el desarrollo general que ha mostrado la Convención Constitucional. Para indagar en estas diferencias se reproduce abajo la figura 2 en Fábrega (2022, p. 137). Allí se puede ver cómo era la distribución de preferencias en la Convención al finalizar la etapa de aprobación del reglamento (hasta octubre del 2021). Donde CV,A, NN, AD, PPOO, P y O se refieren a las listas originales de Chile Vamos, Lista del Apruebo, Independientes No Neutrales, Apruebo Dignidad, Pueblos Originarios, Lista del Pueblo y Otros independendientes fuera de lista, respectivamente. 

Como se puede ver, para lograr 2/3 en la Convención, los colectivos de izquierda sólo necesitan algunos votos de lo que originalmente era la Lista del Apruebo y de Independientes No-Neutrales. Con el desarrollo de la Convención, esos votos llegaron desde el Colectivo Socialista. Este grupo junto con el Frente Amplio pasaron a delimitar sustantivamente el espacio de lo posible al interior del cuerpo colegiado.  

![](https://github.com/jfabregalacoa/convencion_eficacia/blob/main/plots/RCPpaper_porlistas_ideologia.png)

Siguiendo el análisis en Fabrega (2022) sobre la formación de preferencias en etapas iniciales de la Convención, pero con los datos de votaciones actualizadas hasta el 14 de mayo del 2022 puede verse que fue aumentando la coordinación y acuerdos en el grupo mayoritario (izquierda de la Convención) gracias a un desplazamiento relativo hacia la izquierda del Colectivo SOcialista (mayor dispersión del grupo A) y los Independientes No Neutrales. Mientras que los integrantes que permanecieron en la Lista del Apruebo fueron perdiendo gravitancia, a la vez que ganaron esa relevancia los integrantes de Independientes No Neutrales. El resultado se resume en el gráfico siguiente. El gráfico incluye una línea vertical donde está ubicada la mediana de la distribución (Isabella Mamani) y otra donde están los dos tercios del cuerpo colegiado (Ricardo Montero).

![](https://github.com/jfabregalacoa/convencion_eficacia/blob/main/plots/listas_ideologia.png)

Al comparar la distribución ideológica con la eficacia al votar, el resultado presenta una alta pero no perfecta correlación negativa ($\rho$ = -0.7570558). Ello se resume en el gráfico siguiente. La figura también muestra que la relación entre Eficacia al Votar y Preferencia Ideológica no es lineal sino que hay dispersión de la eficacia, particularmente en la izquierda de la Convención. 

Esas diferencias en la eficacia al votar dentro de grupos o listas pueden ser indicativos de diferencias en capacidades de negociación política intragrupo. Ello amerita una indagación más específica al interior de cada grupo de convencionales.

![](https://github.com/jfabregalacoa/convencion_eficacia/blob/main/plots/efic_ideol.png)

## Una mirada a la eficacia en grupos seleccionados

En el funcionamiento de la Convención Constitucional han tenido un rol gravitante los miembros del Colectivo Socialista y el Frente Amplio. Ello era esperable puesto que estos grupos son los que se encontraban en posiciones ideológicas pivotales en el desarrollo de la Convención. Focalicemos la mirada en estos grupos ¿cómo ha sido su eficacia al votar en relación con la de otros grupos?  

En la tabla siguiente se comparan las eficacias promedios de grupos seleccionados al votar. Como puede verse, la mayor eficacia al votar recae precisamente sobre el Frente Amplio y el Colectivo Socialista que el análisis pivotal ex-ante destacaba como los grupos que serían más gravitantes en la Convención. Y tras ellos, Independientes No Neutrales se erige como el tercer grupo de mayor gravitación en el cuerpo colegiado, lo cual es consistente con el sistemático aumento de relevancia de sus miembros en los debates, las solicitudes desde la prensa y las instancias formales de la propia Convención. 

                 Grupo Eficacia al votar
                 Frente Amplio                   75.835
                 Colectivo Socialista            72.865
                 No Neutrales                    68.045
                 Movimientos Sociales              66.3
                 Pueblo Constituyente            65.299
                 Chile Digno                     63.304
                 Coor. Plurinacional             61.724
                 Derecha                         42.704

Si bien como grupos el Frente Amplio y el Colectivo Socialista tienen la mayor eficacia, hay diferencias relevantes entre sus miembros. Estas se ven resumidas en los gráficos siguientes. 

![](https://github.com/jfabregalacoa/convencion_eficacia/blob/main/plots/g_csoc.png)

![](https://github.com/jfabregalacoa/convencion_eficacia/blob/main/plots/g_fa.png)

# Conclusiones

Los análisis ex-ante y ex-post de los procesos de votación entregan información complementaria para entender las dinámicas de un cuerpo colegiado. En el caso de la Convención Constitucional se puede constatar que a medida que ésta se fue desplegando, los convencionales con mejor desempeño coinciden con los ubicados en posiciones estratégicas de acuerdo con un análisis de actores pivotales dadas las normas de votación. Siendo consistente con lo anterior, el análisis ex-post permite además diferenciar entre actores más y menos relevantes dentro de sus grupos de pertenencia en la Convención. 
