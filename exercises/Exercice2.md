
# Using PMD


Pick a Java project from Github (see the [instructions](../sujet.md) for suggestions). Run PMD on its source code using any ruleset (see the [pmd install instruction](./pmd-help.md)). Describe below an issue found by PMD that you think should be solved (true positive) and include below the changes you would add to the source code. Describe below an issue found by PMD that is not worth solving (false positive). Explain why you would not solve this issue.


## Answer

**Choix du projet :** Common Collections

**Analyse avec PMD :**
On a exécuté la commande suivante : 
pmd check -f text -R rulesets/java/quickstart.xml -d [CHEMIN_DU_PROJET] -r [CHEMIN_DU_RAPPORT]

avec : [CHEMIN_DU_PROJET] == "C:\Users\nourc_3okniz2\Documents\ESIR 2\SEM 1\VV\TP\VV-ESIR-TP2\exercises\commons-collections"
et : [CHEMIN_DU_RAPPORT] == "C:\Users\nourc_3okniz2\Documents\ESIR 2\SEM 1\VV\TP\VV-ESIR-TP2\exercises\report.txt"

-- J'ai exécuté la commande :
pmd check -f text -R rulesets/java/quickstart.xml -d "C:\Users\nourc_3okniz2\Documents\ESIR 2\SEM 1\VV\TP\VV-ESIR-TP2\exercises\commons-collections" -r "C:\Users\nourc_3okniz2\Documents\ESIR 2\SEM 1\VV\TP\VV-ESIR-TP2\exercises\report.txt"

→ il a trouvé 1095 violations de règles.

**Vrai positif :**  (Problème pertinent)
Le PMD a détecté que la classe IterableUtils a un constructeur par défaut non privé alors qu'elle devrait être non instanciable 
(ligne 53 du fichier IterableUtils.java)

→  il est important de corriger cette erreur ! 
Les classes utilitaires ne sont pas destinées à être instanciées !! 

→ Correction : 
Il faut ajouter un constructeur privé pour rendre la classe non instanciable :

    public class IterableUtils {
        private IterableUtils() {
            // Constructeur privé pour empêcher l'instanciation
        }
        // Méthodes utilitaires statiques...
    }


**Faux positif :**  (Problème qui peut être ignoré)
Un exemple de faux positif trouvé par PMD : la règle LooseCoupling:	Avoid using implementation types like 'ArrayList'; use the interface instead

→ L'alerte LooseCoupling recommande d'utiliser l'interface List plutôt qu'une ArrayList directement, pour rendre le code plus flexible

- Pourquoi ça ne mérite pas d'être corrigé : 
L'utilisation des ArrayList est intentionnelle et n'a pas de réel impact négatif.
