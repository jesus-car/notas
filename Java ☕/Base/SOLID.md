- Hacer un codigo legible, mantenible y escalable

Single responsability Principal: Cada clase tiene una sola responsabilidad, solo se debe encargar de una parte del sistema

Open closed: Una entidad de software debe quedar abierta para su extension y cerrada para su modificacion( La funcionalidad base debe estar protegida)
  + Una forma de hacer esto es usando el polimorfismo e interfaces para extender clases que apliquen esta interfaz sin modificar las clases ya existentes

Liskov Substitution principal(LSP): En herencia, las subclases deben comportarse como su padre, no modificar su comportamiento, quizas extenderlo super.metodo
  + Una forma de no violar este principio es aplicando interfaces que se implementan a objetos segun sus necesidades y ya no usar la herencia que usara un conjunto de metodos, aun asi no los use. Con esto evitamos validaciones innecesarias si un objeto que hereda de otro puede hacer una u otra cosa.

Interface Segregation(ISP): Es mejor tener muchas clases peque;as pero especializadas, que una clase enorme que demorara en buscar la opcion que necesite usar
  + Las interfaces que se usaran deben de ser justas y necesarias para que las clases que lo implementen usen los metodos establecidos en la interfaz y no terminen sobrando metodos que no se usara.
  + Se debe detectar donde sobran metodos para poder crear interfaces de manera critica

Dependecy Inversion: Una clase no debe depender exclusivamente de otra, es mejor usar abstracciones, osea interfaces de las cuales actuara dependiendo de que objeto que aplique esa interfaz sea usado
