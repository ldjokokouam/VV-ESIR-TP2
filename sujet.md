# Static analysis

## Instructions

Some of the exercises in this practical session use PMD, JavaParser or require a full project as input.

To obtain and use PMD, consult the instructions given in https://pmd.github.io/pmd/pmd_userdocs_installation.html

The folder [javaparser-starter](code/javaparser-starter) contains the code of an application that uses JavaParser to print all public classes and public methods from a given project. You can use this example as a template for all exercises using JavaParser. 

We recommend you use the following projects as input for the exercises:

- [Apache Commons Collections](https://github.com/apache/commons-collections)
- [Apache Commons CLI](https://github.com/apache/commons-cli)
- [Apache Commons Math](https://github.com/apache/commons-math)
- [Apache Commons Lang](https://github.com/apache/commons-lang)

Feel free to use any other project you want.

## Exercises

1. [TCC *vs* LCC](exercises/Exercice1.md)

2. [Using PMD](exercises/Exercice2.md)

3. [Extending PMD](exercises/Exercice3.md)

4. [No getter!](exercises/Exercice4.md)

5. [Cyclomatic Complexity with JavaParser](exercises/jp-cc.md) 

6. [Class cohesion with JavaParser](exercises/jp-tcc.md) (bonus)

=======
# Practical Session #3: Dynamic Testing

Each programming exercise comes with a template project that you can use. Those templates have all the dependencies already configured. You can find those project in the `code` folder.

## Exercises

1. [On assertions](exercises/assertions.md)
2. [Detecting test smells with PMD](exercises/pmd-test-smells.md)
3. [Balanced strings](exercises/balanced-strings.md)
4. [Test the Date class](exercises/test-date-class.md)
6. [Mocks to the rescue](exercises/mocks.md)
