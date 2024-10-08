# On assertions

Answer the following questions:

1. The following assertion fails `assertTrue(3 * .4 == 1.2)`. Explain why and describe how this type of check should be done.

2. What is the difference between `assertEquals` and `assertSame`? Show scenarios where they produce the same result and scenarios where they do not produce the same result.

3. In classes we saw that `fail` is useful to mark code that should not be executed because an exception was expected before. Find other uses for `fail`. Explain the use case and add an example.

4. In JUnit 4, an exception was expected using the `@Test` annotation, while in JUnit 5 there is a special assertion method `assertThrows`. In your opinion, what are the advantages of this new way of checking expected exceptions?

## Answer
 **1.** L'assertion (3 * .4 == 1.2) ne fonctionne pas car les nombres à virgule flottante ne sont pas représentés de manière exacte. Par conséquent, des erreurs d'arrondi peuvent se produire. De plus, les flottants sont stockés en mémoire avec une précision limitée. Le calcul 3 * .4 ne pourra on pas être égal à 1.2.
 
    Pour résoudre ce problème, on peut utiliser une marge d'erreur ε :
    
    double result = 3 * .4;
    double expected = 1.2;
    double epsilon = 10E-5;
    
    assertTrue(Math.abs(result - expected) < epsilon);
    
