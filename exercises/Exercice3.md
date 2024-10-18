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
<![CDATA[//IfStatement[count(ancestor::IfStatement) >= 2]]]>
                </value>
            </property>
        </properties>
        
        <priority>3</priority>
    </rule>
</ruleset>

Ce code a été généré à l'aide de pmd designer.
    
### **Test de la règle sur MapUtils.java**
**Commande utilisée :**

pmd check -d ./ -R /Users/djoko-kouam/Documents/Université_Rennes_1/ESIR/ESIR2_SI/Semestre_7/VV/TP/TP2/VV-ESIR-TP2/exercises/complexity-rules.xml -f text -r resultCommonscollections.txt
    
**Test de la règle sur le projet commons-collections :**

./CollectionUtils.java:1866:    NestedIfRule:    Évitez dutiliser des instructions « if » profondément imbriquées. Envisagez de remanier le code pour en améliorer la lisibilité et la maintenance.
./CollectionUtils.java:1868:    NestedIfRule:    Évitez dutiliser des instructions « if » profondément imbriquées. Envisagez de remanier le code pour en améliorer la lisibilité et la maintenance.
./CollectionUtils.java:1870:    NestedIfRule:    Évitez dutiliser des instructions « if » profondément imbriquées. Envisagez de remanier le code pour en améliorer la lisibilité et la maintenance.
./CollectionUtils.java:1872:    NestedIfRule:    Évitez dutiliser des instructions « if » profondément imbriquées. Envisagez de remanier le code pour en améliorer la lisibilité et la maintenance.
./MapUtils.java:230:    NestedIfRule:    Évitez dutiliser des instructions « if » profondément imbriquées. Envisagez de remanier le code pour en améliorer la lisibilité et la maintenance.
./MapUtils.java:233:    NestedIfRule:    Évitez dutiliser des instructions « if » profondément imbriquées. Envisagez de remanier le code pour en améliorer la lisibilité et la maintenance.
./MapUtils.java:236:    NestedIfRule:    Évitez dutiliser des instructions « if » profondément imbriquées. Envisagez de remanier le code pour en améliorer la lisibilité et la maintenance.
./MapUtils.java:930:    NestedIfRule:    Évitez dutiliser des instructions « if » profondément imbriquées. Envisagez de remanier le code pour en améliorer la lisibilité et la maintenance.
./MapUtils.java:933:    NestedIfRule:    Évitez dutiliser des instructions « if » profondément imbriquées. Envisagez de remanier le code pour en améliorer la lisibilité et la maintenance.
./MapUtils.java:1674:    NestedIfRule:    Évitez dutiliser des instructions « if » profondément imbriquées. Envisagez de remanier le code pour en améliorer la lisibilité et la maintenance.
./MapUtils.java:1677:    NestedIfRule:    Évitez dutiliser des instructions « if » profondément imbriquées. Envisagez de remanier le code pour en améliorer la lisibilité et la maintenance.
./MapUtils.java:1995:    NestedIfRule:    Évitez dutiliser des instructions « if » profondément imbriquées. Envisagez de remanier le code pour en améliorer la lisibilité et la maintenance.
./bidimap/TreeBidiMap.java:1175:    NestedIfRule:    Évitez dutiliser des instructions « if » profondément imbriquées. Envisagez de remanier le code pour en améliorer la lisibilité et la maintenance.
./bidimap/TreeBidiMap.java:1188:    NestedIfRule:    Évitez dutiliser des instructions « if » profondément imbriquées. Envisagez de remanier le code pour en améliorer la lisibilité et la maintenance.
./bidimap/TreeBidiMap.java:1227:    NestedIfRule:    Évitez dutiliser des instructions « if » profondément imbriquées. Envisagez de remanier le code pour en améliorer la lisibilité et la maintenance.
./bidimap/TreeBidiMap.java:1250:    NestedIfRule:    Évitez dutiliser des instructions « if » profondément imbriquées. Envisagez de remanier le code pour en améliorer la lisibilité et la maintenance.
./bidimap/TreeBidiMap.java:1254:    NestedIfRule:    Évitez dutiliser des instructions « if » profondément imbriquées. Envisagez de remanier le code pour en améliorer la lisibilité et la maintenance.
./bidimap/TreeBidiMap.java:1255:    NestedIfRule:    Évitez dutiliser des instructions « if » profondément imbriquées. Envisagez de remanier le code pour en améliorer la lisibilité et la maintenance.
./bidimap/TreeBidiMap.java:1299:    NestedIfRule:    Évitez dutiliser des instructions « if » profondément imbriquées. Envisagez de remanier le code pour en améliorer la lisibilité et la maintenance.
./bidimap/TreeBidiMap.java:1331:    NestedIfRule:    Évitez dutiliser des instructions « if » profondément imbriquées. Envisagez de remanier le code pour en améliorer la lisibilité et la maintenance.
./bidimap/TreeBidiMap.java:1377:    NestedIfRule:    Évitez dutiliser des instructions « if » profondément imbriquées. Envisagez de remanier le code pour en améliorer la lisibilité et la maintenance.
./bidimap/TreeBidiMap.java:1386:    NestedIfRule:    Évitez dutiliser des instructions « if » profondément imbriquées. Envisagez de remanier le code pour en améliorer la lisibilité et la maintenance.
./bidimap/TreeBidiMap.java:1403:    NestedIfRule:    Évitez dutiliser des instructions « if » profondément imbriquées. Envisagez de remanier le code pour en améliorer la lisibilité et la maintenance.
./bidimap/TreeBidiMap.java:1412:    NestedIfRule:    Évitez dutiliser des instructions « if » profondément imbriquées. Envisagez de remanier le code pour en améliorer la lisibilité et la maintenance.
./bidimap/TreeBidiMap.java:2127:    NestedIfRule:    Évitez dutiliser des instructions « if » profondément imbriquées. Envisagez de remanier le code pour en améliorer la lisibilité et la maintenance.
./bidimap/TreeBidiMap.java:2152:    NestedIfRule:    Évitez dutiliser des instructions « if » profondément imbriquées. Envisagez de remanier le code pour en améliorer la lisibilité et la maintenance.
./bloomfilter/BloomFilter.java:163:    NestedIfRule:    Évitez dutiliser des instructions « if » profondément imbriquées. Envisagez de remanier le code pour en améliorer la lisibilité et la maintenance.
./comparators/ComparatorChain.java:208:    NestedIfRule:    Évitez dutiliser des instructions « if » profondément imbriquées. Envisagez de remanier le code pour en améliorer la lisibilité et la maintenance.
./iterators/CollatingIterator.java:277:    NestedIfRule:    Évitez dutiliser des instructions « if » profondément imbriquées. Envisagez de remanier le code pour en améliorer la lisibilité et la maintenance.
./iterators/ObjectGraphIterator.java:238:    NestedIfRule:    Évitez dutiliser des instructions « if » profondément imbriquées. Envisagez de remanier le code pour en améliorer la lisibilité et la maintenance.
./list/CursorableLinkedList.java:198:    NestedIfRule:    Évitez dutiliser des instructions « if » profondément imbriquées. Envisagez de remanier le code pour en améliorer la lisibilité et la maintenance.
./map/AbstractReferenceMap.java:322:    NestedIfRule:    Évitez dutiliser des instructions « if » profondément imbriquées. Envisagez de remanier le code pour en améliorer la lisibilité et la maintenance.
./map/CompositeMap.java:199:    NestedIfRule:    Évitez dutiliser des instructions « if » profondément imbriquées. Envisagez de remanier le code pour en améliorer la lisibilité et la maintenance.
./map/ConcurrentReferenceHashMap.java:839:    NestedIfRule:    Évitez dutiliser des instructions « if » profondément imbriquées. Envisagez de remanier le code pour en améliorer la lisibilité et la maintenance.
./map/ConcurrentReferenceHashMap.java:969:    NestedIfRule:    Évitez dutiliser des instructions « if » profondément imbriquées. Envisagez de remanier le code pour en améliorer la lisibilité et la maintenance.
./map/ConcurrentReferenceHashMap.java:979:    NestedIfRule:    Évitez dutiliser des instructions « if » profondément imbriquées. Envisagez de remanier le code pour en améliorer la lisibilité et la maintenance.
./map/ConcurrentReferenceHashMap.java:1033:    NestedIfRule:    Évitez dutiliser des instructions « if » profondément imbriquées. Envisagez de remanier le code pour en améliorer la lisibilité et la maintenance.
./map/Flat3Map.java:621:    NestedIfRule:    Évitez dutiliser des instructions « if » profondément imbriquées. Envisagez de remanier le code pour en améliorer la lisibilité et la maintenance.
./map/Flat3Map.java:625:    NestedIfRule:    Évitez dutiliser des instructions « if » profondément imbriquées. Envisagez de remanier le code pour en améliorer la lisibilité et la maintenance.
./map/Flat3Map.java:629:    NestedIfRule:    Évitez dutiliser des instructions « if » profondément imbriquées. Envisagez de remanier le code pour en améliorer la lisibilité et la maintenance.
./map/Flat3Map.java:823:    NestedIfRule:    Évitez dutiliser des instructions « if » profondément imbriquées. Envisagez de remanier le code pour en améliorer la lisibilité et la maintenance.
./map/Flat3Map.java:827:    NestedIfRule:    Évitez dutiliser des instructions « if » profondément imbriquées. Envisagez de remanier le code pour en améliorer la lisibilité et la maintenance.
./map/Flat3Map.java:831:    NestedIfRule:    Évitez dutiliser des instructions « if » profondément imbriquées. Envisagez de remanier le code pour en améliorer la lisibilité et la maintenance.
./map/Flat3Map.java:950:    NestedIfRule:    Évitez dutiliser des instructions « if » profondément imbriquées. Envisagez de remanier le code pour en améliorer la lisibilité et la maintenance.
./map/Flat3Map.java:956:    NestedIfRule:    Évitez dutiliser des instructions « if » profondément imbriquées. Envisagez de remanier le code pour en améliorer la lisibilité et la maintenance.
./map/Flat3Map.java:962:    NestedIfRule:    Évitez dutiliser des instructions « if » profondément imbriquées. Envisagez de remanier le code pour en améliorer la lisibilité et la maintenance.
./map/Flat3Map.java:1124:    NestedIfRule:    Évitez dutiliser des instructions « if » profondément imbriquées. Envisagez de remanier le code pour en améliorer la lisibilité et la maintenance.
./map/Flat3Map.java:1132:    NestedIfRule:    Évitez dutiliser des instructions « if » profondément imbriquées. Envisagez de remanier le code pour en améliorer la lisibilité et la maintenance.
./map/Flat3Map.java:1143:    NestedIfRule:    Évitez dutiliser des instructions « if » profondément imbriquées. Envisagez de remanier le code pour en améliorer la lisibilité et la maintenance.
./map/Flat3Map.java:1156:    NestedIfRule:    Évitez dutiliser des instructions « if » profondément imbriquées. Envisagez de remanier le code pour en améliorer la lisibilité et la maintenance.
./map/Flat3Map.java:1164:    NestedIfRule:    Évitez dutiliser des instructions « if » profondément imbriquées. Envisagez de remanier le code pour en améliorer la lisibilité et la maintenance.
./map/Flat3Map.java:1177:    NestedIfRule:    Évitez dutiliser des instructions « if » profondément imbriquées. Envisagez de remanier le code pour en améliorer la lisibilité et la maintenance.
./map/LRUMap.java:243:    NestedIfRule:    Évitez dutiliser des instructions « if » profondément imbriquées. Envisagez de remanier le code pour en améliorer la lisibilité et la maintenance.
./map/LRUMap.java:249:    NestedIfRule:    Évitez dutiliser des instructions « if » profondément imbriquées. Envisagez de remanier le code pour en améliorer la lisibilité et la maintenance.
./map/LRUMap.java:260:    NestedIfRule:    Évitez dutiliser des instructions « if » profondément imbriquées. Envisagez de remanier le code pour en améliorer la lisibilité et la maintenance.
./sequence/SequencesComparator.java:198:    NestedIfRule:    Évitez dutiliser des instructions « if » profondément imbriquées. Envisagez de remanier le code pour en améliorer la lisibilité et la maintenance.
./set/CompositeSet.java:197:    NestedIfRule:    Évitez dutiliser des instructions « if » profondément imbriquées. Envisagez de remanier le code pour en améliorer la lisibilité et la maintenance.
./set/CompositeSet.java:202:    NestedIfRule:    Évitez dutiliser des instructions « if » profondément imbriquées. Envisagez de remanier le code pour en améliorer la lisibilité et la maintenance.
./trie/AbstractPatriciaTrie.java:1643:    NestedIfRule:    Évitez dutiliser des instructions « if » profondément imbriquées. Envisagez de remanier le code pour en améliorer la lisibilité et la maintenance.
./trie/AbstractPatriciaTrie.java:1991:    NestedIfRule:    Évitez dutiliser des instructions « if » profondément imbriquées. Envisagez de remanier le code pour en améliorer la lisibilité et la maintenance.
./trie/AbstractPatriciaTrie.java:2054:    NestedIfRule:    Évitez dutiliser des instructions « if » profondément imbriquées. Envisagez de remanier le code pour en améliorer la lisibilité et la maintenance.


    
### **Test de la règle sur le projet commons-cli**
**Commande utilisée :**

pmd check -d ./ -R /Users/djoko-kouam/Documents/Université_Rennes_1/ESIR/ESIR2_SI/Semestre_7/VV/TP/TP2/VV-ESIR-TP2/exercises/complexity-rules.xml -f text -r resultCommonscli.txt

**Résultat stocké dans resultCommonscli.txt**

./DefaultParser.java:404:    NestedIfRule:    Évitez dutiliser des instructions « if » profondément imbriquées. Envisagez de remanier le code pour en améliorer la lisibilité et la maintenance.
./DefaultParser.java:465:    NestedIfRule:    Évitez dutiliser des instructions « if » profondément imbriquées. Envisagez de remanier le code pour en améliorer la lisibilité et la maintenance.
./DefaultParser.java:468:    NestedIfRule:    Évitez dutiliser des instructions « if » profondément imbriquées. Envisagez de remanier le code pour en améliorer la lisibilité et la maintenance.
./DefaultParser.java:499:    NestedIfRule:    Évitez dutiliser des instructions « if » profondément imbriquées. Envisagez de remanier le code pour en améliorer la lisibilité et la maintenance.
./DefaultParser.java:501:    NestedIfRule:    Évitez dutiliser des instructions « if » profondément imbriquées. Envisagez de remanier le code pour en améliorer la lisibilité et la maintenance.
./DefaultParser.java:508:    NestedIfRule:    Évitez dutiliser des instructions « if » profondément imbriquées. Envisagez de remanier le code pour en améliorer la lisibilité et la maintenance.
./DefaultParser.java:512:    NestedIfRule:    Évitez dutiliser des instructions « if » profondément imbriquées. Envisagez de remanier le code pour en améliorer la lisibilité et la maintenance.
./DefaultParser.java:527:    NestedIfRule:    Évitez dutiliser des instructions « if » profondément imbriquées. Envisagez de remanier le code pour en améliorer la lisibilité et la maintenance.
./DefaultParser.java:530:    NestedIfRule:    Évitez dutiliser des instructions « if » profondément imbriquées. Envisagez de remanier le code pour en améliorer la lisibilité et la maintenance.
./DefaultParser.java:537:    NestedIfRule:    Évitez dutiliser des instructions « if » profondément imbriquées. Envisagez de remanier le code pour en améliorer la lisibilité et la maintenance.
./DefaultParser.java:561:    NestedIfRule:    Évitez dutiliser des instructions « if » profondément imbriquées. Envisagez de remanier le code pour en améliorer la lisibilité et la maintenance.
./DefaultParser.java:563:    NestedIfRule:    Évitez dutiliser des instructions « if » profondément imbriquées. Envisagez de remanier le code pour en améliorer la lisibilité et la maintenance.
./DefaultParser.java:565:    NestedIfRule:    Évitez dutiliser des instructions « if » profondément imbriquées. Envisagez de remanier le code pour en améliorer la lisibilité et la maintenance.
./DefaultParser.java:567:    NestedIfRule:    Évitez dutiliser des instructions « if » profondément imbriquées. Envisagez de remanier le code pour en améliorer la lisibilité et la maintenance.
./GnuParser.java:55:    NestedIfRule:    Évitez dutiliser des instructions « if » profondément imbriquées. Envisagez de remanier le code pour en améliorer la lisibilité et la maintenance.
./GnuParser.java:57:    NestedIfRule:    Évitez dutiliser des instructions « if » profondément imbriquées. Envisagez de remanier le code pour en améliorer la lisibilité et la maintenance.
./GnuParser.java:59:    NestedIfRule:    Évitez dutiliser des instructions « if » profondément imbriquées. Envisagez de remanier le code pour en améliorer la lisibilité et la maintenance.
./GnuParser.java:63:    NestedIfRule:    Évitez dutiliser des instructions « if » profondément imbriquées. Envisagez de remanier le code pour en améliorer la lisibilité et la maintenance.
./GnuParser.java:67:    NestedIfRule:    Évitez dutiliser des instructions « if » profondément imbriquées. Envisagez de remanier le code pour en améliorer la lisibilité et la maintenance.
./Parser.java:163:    NestedIfRule:    Évitez dutiliser des instructions « if » profondément imbriquées. Envisagez de remanier le code pour en améliorer la lisibilité et la maintenance.
./Parser.java:165:    NestedIfRule:    Évitez dutiliser des instructions « if » profondément imbriquées. Envisagez de remanier le code pour en améliorer la lisibilité et la maintenance.
./Parser.java:170:    NestedIfRule:    Évitez dutiliser des instructions « if » profondément imbriquées. Envisagez de remanier le code pour en améliorer la lisibilité et la maintenance.
./Parser.java:172:    NestedIfRule:    Évitez dutiliser des instructions « if » profondément imbriquées. Envisagez de remanier le code pour en améliorer la lisibilité et la maintenance.
./Parser.java:181:    NestedIfRule:    Évitez dutiliser des instructions « if » profondément imbriquées. Envisagez de remanier le code pour en améliorer la lisibilité et la maintenance.
./Parser.java:190:    NestedIfRule:    Évitez dutiliser des instructions « if » profondément imbriquées. Envisagez de remanier le code pour en améliorer la lisibilité et la maintenance.
./Parser.java:281:    NestedIfRule:    Évitez dutiliser des instructions « if » profondément imbriquées. Envisagez de remanier le code pour en améliorer la lisibilité et la maintenance.
./Parser.java:288:    NestedIfRule:    Évitez dutiliser des instructions « if » profondément imbriquées. Envisagez de remanier le code pour en améliorer la lisibilité et la maintenance.
./PosixParser.java:132:    NestedIfRule:    Évitez dutiliser des instructions « if » profondément imbriquées. Envisagez de remanier le code pour en améliorer la lisibilité et la maintenance.
./PosixParser.java:139:    NestedIfRule:    Évitez dutiliser des instructions « if » profondément imbriquées. Envisagez de remanier le code pour en améliorer la lisibilité et la maintenance.
./PosixParser.java:141:    NestedIfRule:    Évitez dutiliser des instructions « if » profondément imbriquées. Envisagez de remanier le code pour en améliorer la lisibilité et la maintenance.
./PosixParser.java:147:    NestedIfRule:    Évitez dutiliser des instructions « if » profondément imbriquées. Envisagez de remanier le code pour en améliorer la lisibilité et la maintenance.
./PosixParser.java:151:    NestedIfRule:    Évitez dutiliser des instructions « if » profondément imbriquées. Envisagez de remanier le code pour en améliorer la lisibilité et la maintenance.
./PosixParser.java:152:    NestedIfRule:    Évitez dutiliser des instructions « if » profondément imbriquées. Envisagez de remanier le code pour en améliorer la lisibilité et la maintenance.
./PosixParser.java:154:    NestedIfRule:    Évitez dutiliser des instructions « if » profondément imbriquées. Envisagez de remanier le code pour en améliorer la lisibilité et la maintenance.
./PosixParser.java:156:    NestedIfRule:    Évitez dutiliser des instructions « if » profondément imbriquées. Envisagez de remanier le code pour en améliorer la lisibilité et la maintenance.

