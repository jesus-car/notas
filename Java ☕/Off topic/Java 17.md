# Java 17
## SEALED CLASS

- Syntax:
```Java
public sealed class Person permits Student, Teacher { // Solo Las clases 'permits' podran heredar de la sealed class Person
}

public final class Student extends Person {}
```

## New Switch

- Syntax
```Java
switch (option){
	case "A" -> System.out.println("Case A");
	case "B","C" -> System.out.println("Case B o C");
	case null -> System.out.println("Case Null");
	default -> System.out.println("Default");
}
```

- JEP(JDK Enhancement proposal) : Proposiciones de mejora de Java

## Pattern Matching for instanceof

- Remueve el casteo al usar instanceof
```Java
    public static double getPerimeter(Shape shape) throws IllegalArgumentException {
        if (shape instanceof Rectangle r) {
            return 2 * r.length() + 2 * r.width();
        } else if (shape instanceof Circle c) {
            return 2 * c.radius() * Math.PI;
        } else {
            throw new IllegalArgumentException("Unrecognized shape");
        }
    }
```

- Puedes usar la nueva variable para una segunda condicion solo si la primera es true, Solo con &&
```JAva
	if (shape instanceof Rectangle r && r.length() > 5) {
		// ...
	}
```

## RECORDS

- Clase que agrupa multiples variables (Data clases)
- Las variables que se declaren como parametros seran declaradas como *final* y Java se le creara un constructor, getter, toString, hashCode y equals. Dentro de las llaves podemos usarlas para crear metodos u otro constructor pero siempre llamando al que se crea por defecto.
- Y se usa como una clase cualquiera, que sus campos seran inmutables
- Puede que la informacion dentro de un arrayList se pueda modificar
```Java
public record Cuenta(String nombre, String clave, boolean privilegiada){
	public Cuenta(String nombre, String clave){
		this(nombre,clave,false);
	}
}
```