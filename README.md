# batch-job-pattern
Le modèle de tâche par lots est adapté à la gestion d'unités de travail atomiques isolées. Il est basé sur la
ressource Job, qui exécute de manière fiable des pods à courte durée de vie jusqu'à leur achèvement dans un
environnement distribué.

## Problem
La principale primitive de Kubernetes pour la gestion et l'exécution des conteneurs est le Pod.
Il existe différentes manières de créer des Pods avec des caractéristiques variées :

### Bare Pod (Pod nu)
Il est possible de créer manuellement un Pod pour exécuter des conteneurs. Cependant, lorsque le nœud sur lequel un tel Pod est exécuté tombe en panne, le Pod n'est pas redémarré. L'exécution de Pods de cette manière est déconseillée, sauf à des fins de développement ou de test. Ce mécanisme est également connu sous le nom de Pods non gérés ou Pods nus.
### ReplicaSet

Ce contrôleur est utilisé pour créer et gérer le cycle de vie des pods censés s'exécuter en continu (par
exemple, pour exécuter un conteneur de serveur Web). Il maintient un ensemble stable de pods répliqués
exécutés à un moment donné et garantit la disponibilité d'un nombre spécifié de pods identiques. 
Les ReplicaSets sont décrits en détail dans le chapitre 11, « Service sans état ».

### DaemonSet
Ce contrôleur exécute un seul Pod sur chaque nœud et est utilisé pour gérer les fonctionnalités de la
plateforme telles que la surveillance, l'agrégation de journaux, les conteneurs de stockage et autres. 
Pourune discussion plus détaillée, reportez­vous au chapitre 9, « Service Daemon » .
