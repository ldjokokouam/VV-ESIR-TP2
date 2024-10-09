# On assertions

Answer the following questions:

1. The following assertion fails `assertTrue(3 * .4 == 1.2)`. Explain why and describe how this type of check should be done.

2. What is the difference between `assertEquals` and `assertSame`? Show scenarios where they produce the same result and scenarios where they do not produce the same result.

3. In classes we saw that `fail` is useful to mark code that should not be executed because an exception was expected before. Find other uses for `fail`. Explain the use case and add an example.

4. In JUnit 4, an exception was expected using the `@Test` annotation, while in JUnit 5 there is a special assertion method `assertThrows`. In your opinion, what are the advantages of this new way of checking expected exceptions?

## Answer

**1.** L'assertion `assertTrue(3 * .4 == 1.2)` ne marche pas car les nombres à virgule flottante ne sont pas représentés de manière exacte. Par conséquent, il peut y avoir des erreurs d'arrondi comme ici. Cela s'explique par le fait que les flotants sont stockés en mémoire avec une précision limitée. Donc le résultat de `3 * .4` ne peut pas être égal à 1.2.
    
    De plus, utiliser le comparateur == peut être trompeur à cause des arrondi. La meilleure approche est d'utiliser une marge d'erreur ε :
    
    
    double result = 3 * .4;
    double expected = 1.2;
    double epsilon = 10E-5;
    
    assertTrue(Math.abs(result - expected) < epsilon);

**2.**

