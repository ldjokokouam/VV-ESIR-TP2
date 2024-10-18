# Extending PMD

Use XPath to define a new rule for PMD to prevent complex code. The rule should detect the use of three or more nested `if` statements in Java programs so it can detect patterns like the following:

```Java
if (...) {
    ...
    if (...) {
        ...
        if (...) {
            ....
        }
    }

}
```
Notice that the nested `if`s may not be direct children of the outer `if`s. They may be written, for example, inside a `for` loop or any other statement.
Write below the XML definition of your rule.

You can find more information on extending PMD in the following link: https://pmd.github.io/latest/pmd_userdocs_extending_writing_rules_intro.html, as well as help for using `pmd-designer` [here](./designer-help.md).

Use your rule with different projects and describe you findings below. See the [instructions](../sujet.md) for suggestions on the projects to use.

## Answer

### **Commandes uilisées pour lancer pmd designer**
export JAVAFX_HOME=/Users/djoko-kouam/Documents/Université_Rennes_1/ESIR/ESIR2_SI/Semestre_7/VV/TP/TP2/VV-ESIR-TP2/exercises/javafx-sdk-23.0.1/
    
    pmd designer
    
### **Écriture de la règle pour détecter les if imbriqués**

<?xml version="1.0"?>
<ruleset name="ComplexityRules"
         xmlns="http://pmd.sourceforge.net/ruleset_2.0.0"
         xmlns:xsi="http://www.w3.org/2001/XMLSchema-instance"
         xsi:schemaLocation="http://pmd.sourceforge.net/ruleset_2.0.0 http://pmd.sourceforge.net/ruleset_2.0.0.xsd">

    <description>
        This rule detects complex code by finding three or more nested 'if' statements.
    </description>

    <rule name="NestedIfRule"
          language="java"
          message="Évitez d'utiliser des instructions « if » profondément imbriquées. Envisagez de remanier le code pour en améliorer la lisibilité et la maintenance."
          class="net.sourceforge.pmd.lang.rule.xpath.XPathRule">
        
        <description>
            Detects three or more nested 'if' statements.
        </description>
        
        <properties>
            <property name="xpath">
                <value>
<![CDATA[
//IfStatement[count(ancestor::IfStatement) >= 2]
]]>
                </value>
            </property>
        </properties>
        
        <priority>3</priority>
    </rule>
</ruleset>

Ce code a été généré à l'aide de pmd designer.
    
### **Test d'un règle sur MapUtils.java**
**Commande utilisée :**

pmd check -d /Users/djoko-kouam/Documents/Université_Rennes_1/ESIR/ESIR2_SI/Semestre_7/VV/TP/TP2/VV-ESIR-TP2/exercises/commons-collections/src/main/java/org/apache/commons/collections4/MapUtils.java -R /Users/djoko-kouam/Documents/Université_Rennes_1/ESIR/ESIR2_SI/Semestre_7/VV/TP/TP2/VV-ESIR-TP2/exercises/complexity-rules.xml -f text -r resultMap.txt
    
**Résultat stocké dans resultMap :**

/Users/djoko-kouam/Documents/Université_Rennes_1/ESIR/ESIR2_SI/Semestre_7/VV/TP/TP2/VV-ESIR-TP2/exercises/commons-collections/src/main/java/org/apache/commons/collections4/MapUtils.java:230:    NestedIfRule:    Évitez dutiliser des instructions « if » profondément imbriquées. Envisagez de remanier le code pour en améliorer la lisibilité et la maintenance.

/Users/djoko-kouam/Documents/Université_Rennes_1/ESIR/ESIR2_SI/Semestre_7/VV/TP/TP2/VV-ESIR-TP2/exercises/commons-collections/src/main/java/org/apache/commons/collections4/MapUtils.java:233:    NestedIfRule:    Évitez dutiliser des instructions « if » profondément imbriquées. Envisagez de remanier le code pour en améliorer la lisibilité et la maintenance.

/Users/djoko-kouam/Documents/Université_Rennes_1/ESIR/ESIR2_SI/Semestre_7/VV/TP/TP2/VV-ESIR-TP2/exercises/commons-collections/src/main/java/org/apache/commons/collections4/MapUtils.java:236:    NestedIfRule:    Évitez dutiliser des instructions « if » profondément imbriquées. Envisagez de remanier le code pour en améliorer la lisibilité et la maintenance.

/Users/djoko-kouam/Documents/Université_Rennes_1/ESIR/ESIR2_SI/Semestre_7/VV/TP/TP2/VV-ESIR-TP2/exercises/commons-collections/src/main/java/org/apache/commons/collections4/MapUtils.java:930:    NestedIfRule:    Évitez dutiliser des instructions « if » profondément imbriquées. Envisagez de remanier le code pour en améliorer la lisibilité et la maintenance.

/Users/djoko-kouam/Documents/Université_Rennes_1/ESIR/ESIR2_SI/Semestre_7/VV/TP/TP2/VV-ESIR-TP2/exercises/commons-collections/src/main/java/org/apache/commons/collections4/MapUtils.java:933:    NestedIfRule:    Évitez dutiliser des instructions « if » profondément imbriquées. Envisagez de remanier le code pour en améliorer la lisibilité et la maintenance.

/Users/djoko-kouam/Documents/Université_Rennes_1/ESIR/ESIR2_SI/Semestre_7/VV/TP/TP2/VV-ESIR-TP2/exercises/commons-collections/src/main/java/org/apache/commons/collections4/MapUtils.java:1674:    NestedIfRule:    Évitez dutiliser des instructions « if » profondément imbriquées. Envisagez de remanier le code pour en améliorer la lisibilité et la maintenance.

/Users/djoko-kouam/Documents/Université_Rennes_1/ESIR/ESIR2_SI/Semestre_7/VV/TP/TP2/VV-ESIR-TP2/exercises/commons-collections/src/main/java/org/apache/commons/collections4/MapUtils.java:1677:    NestedIfRule:    Évitez dutiliser des instructions « if » profondément imbriquées. Envisagez de remanier le code pour en améliorer la lisibilité et la maintenance.

/Users/djoko-kouam/Documents/Université_Rennes_1/ESIR/ESIR2_SI/Semestre_7/VV/TP/TP2/VV-ESIR-TP2/exercises/commons-collections/src/main/java/org/apache/commons/collections4/MapUtils.java:1995:    NestedIfRule:    Évitez dutiliser des instructions « if » profondément imbriquées. Envisagez de remanier le code pour en améliorer la lisibilité et la maintenance.

    
