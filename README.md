#CLEAN Architecture

En los últimos años hemos visto gran cantidad de ideas sobre arquitectura de sistemas. Algunas son:
* Hexagonal Architecture (también conocida como Ports and Adapters) de Alistair Cockburny adoptada por Steve Freman y Nat Pryce en su libro Growing Object Oriented Software.
* Onion Architecture de Jeffrey Palermo.
* Screaming Architecture de Uncle Bob.
* DCI de James Coplien y Trygve Reenskaug.
* BCE de Ivar Jacobson expuesto en su libro “Object Oriented Software Engineering: A Use-Case Driven Approach”.

Aunque todas estas arquitecturas pueden variar, algunos detalles son muy similares. Todos tienen el mismo objetivo, que es la separación de intereses o principios (separation of concerns). Todos los frameworks descritos cumplen esta separación dividiendo la aplicación en capas. Cada una de estas arquitecturas produce sistemas con las siguientes características:
* Independiente de frameworks.
* Testeable.
* Independiente de la UI.
* Independiente de la base de datos.
* Independiente de factores externos.

###La regla de dependencia
Esta regla dice que las dependencias a nivel de código fuente sólo pueden apuntar hacia dentro. Nada que se encuentre en un circulo interior puede saber algo sobre lo que hay en un círculo exterior. Particularmente, algo declarado en un círculo externo no puede ser mencionado desde el código situado en un círculo interno. Eso incluye funciones, clases, variables o cualquier otra entidad software. Por la misma razón, los formatos de datos usados en un círculo exterior no deberían usarse por un círculo interior, especialmente si esos formatos son generados por algún framework en un círculo situado al exterior.

###Entidades
Las entidades encapsulan la lógica de negocio de la empresa (hablamos de software empresarial). Una entidad puede ser un objeto con métodos, o puede ser un conjunto de estructuras de datos y funciones. No importa mientras las entidades se puedan re/utilizar desde diferentes aplicaciones de la empresa. Si no tenemos una empresa, estaremos escribiendo una sola aplicación, entonces esas entidades son los objetos de negocio de solo esa aplicación y no de la empresa. Encapsulan la mayoría de la lógica general y de alto nivel.

###Casos de uso
El software de esta capa contiene reglas de negocio específicas de la aplicación. Encapsula e implementa todos los casos de uso del sistema. Estos casos de uso dirigen el flujo de datos hacía y desde las entidades y hacen que las entidades usen su lógica de negocio empresarial para conseguir el objetivo del caso de uso. Los cambios en esta capa no deberían afectar a las entidades.

###Interface Adapters (adaptadores de interfaz)
El software de esta capa es un conjunto de adaptadores que convierten datos desde el formato mas conveniente para el caso de uso y entidades al formato mas conveniente o aceptado por elementos externos como la base de datos o la web. Es esta capa, por ejemplo, la que contendrá toda la arquitectura MVC de una interfaz gráfica. Los presentadores, vistas y controladores pertenecen a esta capa.

###Frameworks y Drivers
El círculo o capa más externa se compone generalmente de frameworks y herramientas como la base de datos, el framework web, etc. Normalmente en esta capa sólo se escribe código que actúa de pegamento con los círculos o capas interiores. En esta capa es donde van todos los detalles. La web es un detalle. La base de datos es un detalle. Mantenemos estas cosas fuera del alcance donde no pueden hacer mucho daño.

![alt text](https://github.com/EmilioSalgado/CLEAN-Architecture/blob/master/clean_architecture.jpg "CLEAN Architecture")
