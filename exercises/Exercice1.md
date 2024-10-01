# TCC *vs* LCC

Explain under which circumstances *Tight Class Cohesion* (TCC) and *Loose Class Cohesion* (LCC) metrics produce the same value for a given Java class. Build an example of such as class and include the code below or find one example in an open-source project from Github and include the link to the class below. Could LCC be lower than TCC for any given class? Explain.

A refresher on TCC and LCC is available in the [course notes](https://oscarlvp.github.io/vandv-classes/#cohesion-graph).

## Answer

**1.** Quand TCC et LCC produisent-ils la même valeur ? 

TCC et LCC produisent la même valeur pour une classe lorsque toutes les méthodes de cette classe accèdent directement au mêmes attributs. Ainsi, toutes les paires de méthodes de cette classe accèdent directement aux mêmes attributs.

**Exemple de classe Java**

public class Rectangle {
    private float x;
    private float y;
    
    public void perimetre() {
        return (x+y) 2;
    }
      
    public void aire() {
        return x*y;
    }
    
}

 Dans cet exemple, les méthodes prerimetre() et aire() accèdent aux mêmes attributs, à savoir x et y. Ici, TCC et LCC auront la même valeur (toutes les paires de méthodes sont connectées).

**Est-ce que LCC peut-être inférieur à TCC**

LCC ne peut pas être inférieur à TCC car TCC compte uniquement les connexions directes entre les méthodes via des attributs communs. De son côté, LCC compte les connexions directes et indirectes.
