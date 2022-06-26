# breizh-camp-java-operator
Source code for Breizh Camp for Java operator demo

## 🎉 Init project
 - la branche `01-init-project` contient le résultat de cette étape
 - [installer / mettre](https://sdk.operatorframework.io/docs/installation/) à jour la dernière version du [Operator SDK](https://sdk.operatorframework.io/) (v1.20.1 au moment de l'écriture du readme)
 - créer le répertoire `breizh-camp-java-operator`
 - dans le répertoire `breizh-camp-java-operator`, scaffolding du projet avec Quarkus : `operator-sdk init --plugins quarkus --domain fr.wilda --project-name breizh-camp-java-operator`
 - l'arborescence générée est la suivante:
```bash
.
├── LICENSE
├── Makefile
├── PROJECT
├── README.md
├── pom.xml
├── src
│   └── main
│       ├── java
│       └── resources
│           └── application.properties
```
 - ⚠️ Au moment de l'écriture de ce tuto il est nécessaire de changer manuellement les versions de Quarkus et du SDK dans le `pom.xml`:
    - passer la propriété `quarkus.version` à `2.10.0.Final`
    - passer la propriété `quarkus-sdk.version` à `3.0.8`
 - supprimer le `-operator` dans le nom du fichier `application.properties`:
```yaml
    quarkus.container-image.build=true
    #quarkus.container-image.group=
    quarkus.container-image.name=breizh-camp-java-operator
    # set to true to automatically apply CRDs to the cluster when they get regenerated
    quarkus.operator-sdk.crd.apply=false
    # set to true to automatically generate CSV from your code
    quarkus.operator-sdk.generate-csv=false
```
 - vérification que cela compile : `mvn clean compile`
 - tester le lancement: `mvn quarkus:dev`:
```bash
__  ____  __  _____   ___  __ ____  ______ 
 --/ __ \/ / / / _ | / _ \/ //_/ / / / __/ 
 -/ /_/ / /_/ / __ |/ , _/ ,< / /_/ /\ \   
--\___\_\____/_/ |_/_/|_/_/|_|\____/___/   
2022-06-20 16:46:52,069 WARN  [io.fab.kub.cli.Config] (Quarkus Main Thread) Found multiple Kubernetes config files [[/Users/stef/Config/k8s/ovh-example-2.yml, /Users/stef/.kube/config]], using the first one: [/Users/stef/Config/k8s/ovh-example-2.yml]. If not desired file, please change it by doing `export KUBECONFIG=/path/to/kubeconfig` on Unix systems or `$Env:KUBECONFIG=/path/to/kubeconfig` on Windows.

2022-06-20 16:46:52,129 WARN  [io.fab.kub.cli.Config] (Quarkus Main Thread) Found multiple Kubernetes config files [[/Users/stef/Config/k8s/ovh-example-2.yml, /Users/stef/.kube/config]], using the first one: [/Users/stef/Config/k8s/ovh-example-2.yml]. If not desired file, please change it by doing `export KUBECONFIG=/path/to/kubeconfig` on Unix systems or `$Env:KUBECONFIG=/path/to/kubeconfig` on Windows.
2022-06-20 16:46:52,329 INFO  [io.qua.ope.run.AppEventListener] (Quarkus Main Thread) Quarkus Java Operator SDK extension 3.0.8 (commit: ef221b3 on branch: ef221b39cd8eb90fdc88fe85d742d669195727c0) built on Wed Jun 08 15:55:41 CEST 2022
2022-06-20 16:46:52,329 WARN  [io.qua.ope.run.AppEventListener] (Quarkus Main Thread) No Reconciler implementation was found so the Operator was not started.
2022-06-20 16:46:52,388 INFO  [io.quarkus] (Quarkus Main Thread) breizh-camp-java-operator 0.0.1-SNAPSHOT on JVM (powered by Quarkus 2.7.6.Final) started in 1.913s. Listening on: http://localhost:8080
2022-06-20 16:46:52,389 INFO  [io.quarkus] (Quarkus Main Thread) Profile dev activated. Live Coding activated.
2022-06-20 16:46:52,389 INFO  [io.quarkus] (Quarkus Main Thread) Installed features: [cdi, kubernetes, kubernetes-client, micrometer, openshift-client, operator-sdk, smallrye-context-propagation, smallrye-health, vertx]
```