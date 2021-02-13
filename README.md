# Módulo “Redes de infraestructuras Críticas: Estimación de costos y defensa de ataques” #

## Introducción ##

**Las infraestructuras críticas son sistemas que proveen servicios vitales a la sociedad, como los suministros de agua potable, electricidad, o transporte. Cualquier interrupción o ruptura significativa de estos servicios, amenaza directamente a la seguridad y al sistema económico de la sociedad, salud y seguridad pública, o cualquier combinación de los mismos**. Incluso pequeñas interrupciones y fallas de componentes pueden reducir considerablemente el rendimiento y causar importantes daños económicos. Por lo tanto, un ataque físico o cibernético a una Infraestructura Crítica genera masivas externalidades negativas, especialmente debido a la creciente interdependencia e interconexión técnica entre diferentes infraestructuras críticas. Particularmente, ***los fallos en efecto cascada entre las IC podrían representar una seria amenaza para la sociedad***. Es por esto, que las Infraestructuras Críticas son un objetivo ideal para ataques terroristas, por motivos políticos o criminales. De ahí la necesidad de desarrollar modelos aplicados que puedan evaluar los costos y las consecuencias de los ataques intencionales a las ICs.

## Contexto ##

El modelo se basa en un sólido trabajo científico del dominio de la investigación de operaciones. Este se construye en base a trabajos anteriores de Brown, Golany y Alderson que han modelado y evaluado los ataques a las ICs.  Emplea programación lineal, teoría del flujo de red y aplica investigaciones previas sobre interdicción en las redes de IC. Por ejemplo, tanto la Oficina Federal Suiza de Protección Civil, el Departamento de Defensa de los Estados Unidos, y el Departamento de Seguridad Nacional de EE. UU. han priorizado los elementos de las infraestructuras críticas en un intento de generar una protección integral.


### 3.Métodos ### 

#### 3.1 Método Operativo #### 

**El modelo asume que un bien o servicio homogéneo se transporta a través de una red. Esta contiene nodos de suministro que brindan el bien o servicio, nodos de demanda que consumen el bien o servicio y nodos de tránsito que lo transfieren a otros nodos**. Para representar gráficamente el modelo, se da un gráfico simplificado **G = (V, E)**, donde V representa un conjunto de nodos (los círculos en la Fig.1 y en todas las siguientes figuras), y E un conjunto de arcos (las flechas en la figura 1 y todas las figuras siguientes). El conjunto de nodos se divide en **V = VA ∪ VN ∪ VT**, donde VA es el conjunto de ***"nodos de suministro”, VN el conjunto de “nodos de demanda” y VT el conjunto de “nodos de tránsito”***. El conjunto de arcos E representa las conexiones entre los objetos. En este informe, un arco e ∈ E es indicado como e o por sus nodos finales **e = (v, w).** 



FIGURA 1



Para cada nodo v ∈ V, si v ∈ VA, puede proporcionar un suministro (no negativo) av, y si v ∈ VN, tiene una demanda (no negativa) nv. **Cada arco e ∈ E tiene una capacidad ue, que es el flujo máximo de un bien o servicio a través del arco (durante un tiempo dado), y costo ce por cada unidad del bien o servicio transportado por este arco.**
La Figura 1 ilustra una determinada configuración para un sistema con cinco nodos. En este ejemplo específico, el nodo 1 es un nodo de suministro con un suministro de av = 7 y el nodo 5 es un nodo de demanda con una demanda de nv = 5. Todos los demás nodos son nodos de tránsito. Cada arco e ∈ E está representado por una flecha y un par de números ue; ce que indican la capacidad y el costo unitario del arco.
**Se busca una solución para un flujo factible x ∈ IRE que minimice el costo total (llamado flujo de costo óptimo).** Por lo tanto, se debe encontrar un flujo xe respectivo para cada arco e ∈ E. Para un nodo dado v ∈ V, la entrada neta fx (v) se define como la entrada total menos salida total, formalmente:


<img src="imagenes/FOR%20(1).PNG" width="300">


Un flujo es factible si se satisfacen tanto las restricciones de flujo, como las restricciones de capacidad. **Las restricciones de flujo establecen que un nodo de suministro no puede entregar a otro nodo más que su oferta, un nodo de demanda debe satisfacer propiamente la demanda, y un nodo de tránsito tiene que transmitir el flujo sin pérdidas:**




<img src="imagenes/FOR%20(2).PNG" width="300">




Las limitaciones de la capacidad garantizan que no se supere la capacidad de los arcos:



<img src="imagenes/FOR%20(3).PNG" width="300">



Entre todos los flujos factibles, buscamos encontrar un flujo x de costo mínimo


<img src="imagenes/FOR%20(4).PNG" width="300">


Juntas, estas condiciones producen el siguiente problema de flujo de costo mínimo (P1):


<img src="imagenes/FOR%20(5).PNG" width="200">


Sujeto a: 



<img src="imagenes/FOR%20(6).PNG" width="300">






FIGURA 2





La figura 2 da una solución óptima para el ejemplo especificado por la figura 1. Para cada arco con un flujo positivo, el valor de flujo calculado se da junto al arco y antes de la barra oblicua. Por ejemplo, el flujo del nodo 1 al nodo 2 es igual a  x12. En este ejemplo, el costo total de esta solución óptima es 12.


#### 3.2 Inclusión de escasez y formulación estándar ####



**El modelo anterior ahora se extiende y se aplica a una situación en la que la red no puede satisfacer completamente todas las demandas.** Esto se hace asignando un costo de penalización pv a cada nodo de demanda v ∈ V. Además, todas las restricciones de flujo son ahora descritas por ecuaciones para formular el problema en una forma estándar. Por lo tanto, se agregan los siguientes elementos al gráfico G = (V, E):


**Un pseudo nodo de suministro va con suministroava=v∈VNnv**

Para cada nodo de demanda v ∈ VN, un arco (va, v) con un costo pv y una capacidad nv

**Un pseudo nodo de demanda vn con demanda nvn= v∈VAav**

Para cada nodo de suministro v∈VA ∪ {va}, un arco (v,vn ) con costo 0 y capacidad av


El pseudo nodo de suministro puede entregar las unidades faltantes a los nodos de demanda con un costo de penalización pv. El gráfico resultante se denota por G ′ = (V ′, E ′). Para cada nodo v′ ∈ V′ la demanda bv se define como:

bv=


<img src="imagenes/FOR%20(7).PNG" width="300">



La Figura 3 ilustra estas modificaciones con un costo de penalización unitario de 100. Este problema extendido ahora se puede describir como se muestra en G ′ = (V ′, E ′):


<img src="imagenes/FOR%20(8).PNG" width="250">




FIGURA 3




Sujeto a:



<img src="imagenes/FOR%20(9).PNG" width="300">




Se supone que el operador opera la red a un costo óptimo. En este caso el valor de la solución optimizada de este modelo indica los costos operativos regulares.


#### 3.3 Modelado de un escenario de ataque ####


**Se supone que un ataque a una red puede tener como objetivo tanto nodos como arcos. Si un arco es atacado, se vuelve inoperante, es decir, su capacidad se reduce a cero. Si un nodo es atacado, no puede entregar la oferta ni servir de nodo de tránsito, pero su demanda permanece inalterada. Esta situación se modela reduciendo a cero la capacidad de todos los arcos interrumpidos como consecuencia del ataque.**
Un escenario de ataque **U = (Vu,Eu)** se define por los conjuntos de nodos atacados Vu ⊆ V y arcos Eu ⊆ E. Los pseudo nodos y los pseudo arcos no pueden ser atacados. Una solución válida para este escenario de ataque debe satisfacer las siguientes restricciones:


<img src="imagenes/FOR%20(10).PNG" width="300">



Una vez que estas restricciones se añaden al modelo, un determinado escenario de ataque U = (Vu, Eu) se puede describir como: 



<img src="imagenes/FOR%20(11).PNG" width="200">



sujeto a:



<img src="imagenes/FOR%20(12).PNG" width="350">



**Si Vu = ∅ y Eu = ∅ entonces (P3) es equivalente a (P2). El problema (P3) es también un problema de flujo de costo mínimo, lo que implica que puede ser resuelto eficientemente y que los vectores de entrada enteros b y u producen soluciones enteras.** Esta es una importante característica de los problemas de flujo de la red.
Una vez más, se supone que la red funciona a un costo óptimo después de un ataque. Por lo tanto, la variable objetivo zU de una solución óptima de (P3) indica el costo de operación después de un ataque U = (Vu, Eu). Para cada ataque U, los costos KU se definen como:


<img src="imagenes/FOR%20(13).PNG" width="200">


Por lo tanto, los costos operativos después de un ataque exceden los de las operaciones normales, es decir, zU ≥ z y por lo tanto KU ≥ 0 para cualquier ataque U. La figura 4 ilustra un escenario de ataque **U = (Vu, Eu) con Vu = {4} y Eu = {(1, 3)}.** Sólo se muestra el gráfico G en lugar de G′. Los arcos discontinuos no están disponibles después del ataque. Los arcos con un flujo positivo son subrayados. La demanda del nodo 5 todavía puede ser satisfecha. El costo total de operación después del ataque es de 27, lo que implica que el costo KU del ataque es KU = 27 - 12 = 15.

FIGURA 4

La figura 5 ilustra un escenario de ataque en el que sólo se ataca el nodo 2, es decir, **U2 = (Vu2,Eu2 ) con Vu2 = {2} y Eu2 = ∅.** 
La demanda en el nodo 5 no puede ser satisfecha en su totalidad. Una unidad no puede ser entregada, lo que implica un costo de penalización de 100. El costo total de funcionamiento de la red es ahora de 106, de tal manera que ***el ataque ha causado un daño de 106 – 12 = 94 unidades monetarias.***


#### 3.4  El modelo de atacante-defensor ####

Si bien los operadores de IC pueden no saber exactamente cómo se atacará la red en el futuro, pueden asumir que un atacante bien informado probablemente intentará el costo total de operación de la red. A continuación, se modifica el modelo para reflejar esta intención. Un atacante tiene un presupuesto determinado B. Cada elemento de la red tiene una cierta fuerza, que representa los recursos que un atacante debe invertir para desactivar este elemento. Específicamente, el atacante incurre en un costo de unidades pv para un ataque a cualquier nodo v ∈ V , y un costo de unidades pe para un ataque a cualquier arco e ∈ E. Las siguientes variables de decisión se introducen para modelar la decisión de ataque:


**ye para todo e ∈ E : ye es 1 si el arco e es atacado y 0 en caso contrario,**

**yv para todo v ∈ V : yv es 1 si el nodo v es atacado y 0 en caso contrario.**



Además, el atacante está sujeto a la restricción del presupuesto:


<img src="imagenes/FOR%20(14).PNG" width="200">


En un primer paso, el ataque se modela ajustando las capacidades del arco:



<img src="imagenes/FOR%20(15).PNG" width="350">



Las limitaciones de la primera línea se refieren a los seudo arcos cuyas capacidades permanecen inalteradas. Para un arco e = (v, w) ∈ E, la capacidad es ue a menos que se ataque el arco e o el nodo v o w. En cualquiera de estos casos, las restricciones de las líneas 2 a 4 especifican que la capacidad de cualquiera de esos nodos o arcos se reduce a cero. Por lo tanto, el siguiente modelo resulta:


<img src="imagenes/FOR%20(16).PNG" width="250">



sujeto a:


<img src="imagenes/FOR%20(17).PNG" width="400">


**El problema (P4) es un problema de optimización de dos niveles al que no se pueden aplicar directamente los solucionadores matemáticos estándar como CPLEX o Gurobi.** Para transformar este bi-nivel en un problema de optimización de un solo nivel, (P4) se reformula siguiendo el enfoque descrito en Brown et al. [6]. Los flujos sobre los arcos atacados son penalizados, dejando que M denote un costo de penalización suficientemente alto. Por lo tanto, (P4) puede ser reescrito como:


<img src="imagenes/FOR%20(18).PNG" width="500">


Los espacios de solución de (P4) y (P5) no son idénticos, pero si se elige correctamente M, las soluciones óptimas y los valores objetivos óptimos son los mismos en ambos problemas. (P5) sigue siendo un problema de optimización a dos niveles, pero el problema de optimización interna puede ser transformado usando la teoría de la dualidad [8]. Hablando informalmente, el problema de optimización interna (P5) se transforma en un problema de maximización mientras que el valor de la solución óptima permanece igual. Dos tipos de variables duales son introducidos: αv para cada limitación de flujo del nodo v ∈ V ′ en (P5) y βvw para cada limitación de capacidad del arco (v, w) ∈ E′ en (P5). Desarrollando las correspondientes restricciones duales para todas las variables primarias y la función de doble objetivo, lo siguiente se obtiene un doble problema:


<img src="imagenes/FOR%20(19).PNG" width="250">



sujeto a:


<img src="imagenes/FOR%20(20).PNG" width="500">


El problema de optimización interna de (P5) siempre tiene una solución y la óptima es limitada ya que todos los factores de costo ce son positivos. En este caso, el valor objetivo de la solución óptima de (P6) es igual al valor objetivo de (P5). Por lo tanto, el problema de optimización interna (P5) puede ser sustituido por (P6), lo que da lugar a la siguiente reformulación de (P5):


<img src="imagenes/FOR%20(21).PNG" width="250">



Sujeto a:


<img src="imagenes/FOR%20(22).PNG" width="500">


El problema (P7) es un programa lineal de números enteros mixtos. Aunque especificamos este problema aquí, **también observamos que los actuales solucionadores de optimización, como CPLEX y GUROBI, no son capaces de encontrar soluciones óptimas para instancias de gran tamaño de este problema programa lineal.**


#### 3.5 Aplicación a un pequeño ejemplo ####

El modelo de atacante-defensor se aplica ahora al ejemplo de la red del operador. La fuerza pe de cada arco e ∈ E se indica en la tercera posición de las respectivas líneas de datos junto a los arcos. Los nodos se consideran infinitamente resistentes, es decir, pv = ∞ para todos los v ∈ V :
La tabla 1 a continuación da las estrategias de ataque óptimas para los diferentes presupuestos de ataque B. Demuestra que no hay una correlación directa entre el presupuesto de ataque y el número de arcos atacados.
Para ilustrar este hecho, las Figuras 6, 7 y 8 muestran los respectivos gráficos de los presupuestos de ataque de B = 1 y B = 13. Aunque el coste del ataque aumenta en un factor de más de 81 en este último escenario, sólo se atacan dos arcos más.


FIGURA 5


FIGURA 6


FIGURA 7


Además, un arco en particular ya no tiene por qué constituir un objetivo atractivo en una estrategia óptima a medida que aumenta el presupuesto de ataque. Este efecto se muestra al aumentar B de 1 a 2 y de 9 a 10. Por lo tanto, las estrategias de ataque óptimas no se anidan con respecto a un aumento de B. Esto implica que los elementos de la red no pueden ser priorizados por la criticidad, lo que confirma la crítica inicial de [3].



### 4. Conclusión y perspectivas ###

En este capítulo, el costo de un ataque a las redes de infraestructura crítica se evaluó con un modelo genérico. Este modelo se implementó como un programa lineal de números enteros mixtos y se aplicó a varios ejemplos a pequeña escala. **Los trabajos futuros podrían utilizar esta operacionalización para analizar las infraestructuras reales, como la energía o redes de agua potable.**

Si bien los desafíos de modelar esas redes reales son cualquier cosa menos trivial, el trabajo relacionado puede basarse en algunas de las ideas presentadas aquí.
Además, el modelo de atacante-defensor considerado aquí podría extenderse a los escenarios en los que el operador intente proteger la infraestructura en cuestión invirtiendo en la fortaleza de la red. Dicho operador utilizará un presupuesto de defensa particular para invertir en medidas que reduzcan al mínimo los costos máximos de un ataque (por ejemplo, aumentando la robustez o la redundancia de los componentes críticos). ***En futuros trabajos se podrán analizar las estrategias de inversión óptimas para este presupuesto de defensa.*** Si bien el análisis de esos modelos de defensa-atacante-defensor [4, 6] se basa en los escenarios básicos que hemos ilustrado aquí, es significativamente más complejo.







