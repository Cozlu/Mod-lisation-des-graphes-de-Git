# Modélisation des graphes de Git

## 1. Présentation

L'intérêt de ce dépôt Git est de compiler tous les résultats et morceaux de code que j'ai utilisé dans le cadre de mon stage de M1 informatique au LIGM qui portait sur la modélisation des graphes issus de projets Git.

Le principal objet d'étude est le graphe acyclique orienté. C'est un cas particulier de graphe orienté qui permet de représenter fidèlement les commit d'un projet Git et leur dépendances. On a donc les noeuds du graphes qui correspondent aux commit et les arcs qui permettent de hiérarchiser les commits.

Une des premères étapes du stage a été de comparer la complexité moyenne de l'algorithme natif de git Git Bisect et un autre algorithme Golden Bisect *(voir Références)* qui servent tout deux à trouver le commit qui a introduit un bug dans un projet Git.

La deuxième étape du stage a été de regarder s'il existe des caractérisitiques sur les graphes de projet Git issus de GitHub afin de pouvoir potentiellement créer un modèle. Les différentes caractéristiques que j'ai pu trouver sont présentes dans ce dépôt Git.

## 2. Documents et résultats disponibles

Dans ce dépôt, vous avez accès à cinq notebook qui compilent par thème les différentes analyses sur les graphes :
- Stats_structure_graphes contient les premières analyses sur les enfants et parents des noeuds des graphes ainsi que la proportion de noeuds dans la branche main.
- Loi_geom est une analyse approfondie sur une caractéristique des enfants d'un noeud : la présence d'une loi géométrique sur les fréquences de noeuds à $e$ enfants.
- Largeur_graphes regarde la largeur maximale et l'évolution de la largeur des graphes en terme de timestamps.
- Graphes_gen s'intéresse à des modèles simplifiés de génération de graphe et aux différences avec les graphe de projet réels.
- Git-Golden_Bisect contient le comparaison de la complexité moyenne des algorithmes de Git et Golden Bisect.

## Références

**Golden Bisect** :
Julien Courtiel, Paul Dorbec, and Romain Lecoq. Theoretical analysis of git bisect. Algorithmica,
86(5):1365–1399, December 2023.

**Modèle simplifié de génération de graphes** : Julien Courtiel and Martin Pépin. Random generation of git graphs, 2024

Pour réaliser les différentes analyses, j'ai utilisé  110 graphes issus de projets GitHub public, extraits à l'aide de commandes Git. Les graphes extraits vont de 100 à 1 000 000 de nœud. Chaque projet a été converti en trois fichiers :
- Un fichier **.tdag** qui contient la structure du graphe avec, pour chaque ligne, l'identifiant d'un nœud suivi des identifiants de ses parents (s'il n'y en a aucun, alors le nœud n'a pas de parent). De plus les nœuds sont dans l'ordre topologique.
- Un fichier **.main**, qui contient, un nœud par ligne, les nœuds composant la branche principale (ou main) du projet, dans leur ordre d’apparition.
- Un fichier **.ts** contenant à chaque ligne, un nœud et son timestamp, c'est-à-dire la date à laquelle il a été créé. Chaque timestamp est un entier représentant le nombre de secondes écoulées depuis le 1er janvier 1970.

Projets utilisés : 
| Noms 1 | Noms 2 | Noms 3 |
|-------|-------|-------|
| apache_flink-cdc | apache_guacamole-server | apache_incubator-age |
| apache_incubator-answer | apache_incubator-fury | apache_incubator-hivemall |
| apache_incubator-horaedb | apache_incubator-kvrocks | apache_incubator-livy |
| apache_incubator-pagespeed-ngx | apache_incubator-sdap-ingester | apache_incubator-sedona |
| apache_incubator-teaclave | apache_incubator-toree | apache_incubator-wayang |
| microsoft_WSL | apache_apisix | apache_cassandra |
| apache_couchdb | apache_dolphinscheduler | apache_druid |
| apache_hbase | apache_hive | apache_incubator-celeborn |
| apache_incubator-devlake | apache_incubator-eventmesh | apache_incubator-linkis |
| apache_incubator-opendal | apache_incubator-openwhisk | apache_incubator-pagespeed-mod |
| apache_incubator-paimon | apache_incubator-pegasus | apache_incubator-seata |
| apache_incubator-seatunnel | apache_incubator-streampark | apache_lucene-solr |
| apache_mesos | apache_nifi | apache_pulsar |
| apache_rocketmq | apache_shenyu | apache_skywalking |
| apache_storm | apache_tvm | apache_zookeeper |
| django_django | docker_docker-ce | eclipse-platform_eclipse.platform.swt |
| eclipse-platform_eclipse.platform | eclipse-platform_eclipse.platform.ui | electron_electron |
| facebook_react | GNOME_gimp | hashicorp_terraform |
| inkscape_inkscape | laravel_laravel | microsoft_PowerToys |
| microsoft_terminal | microsoft_TypeScript | moby_moby |
| nim-lang_Nim | opencv_opencv | openwrt_packages |
| postgres_postgres | PowerShell_PowerShell | spring-projects_spring-boot |
| spring-projects_spring-framework | angular_angular | ansible_ansible |
| apache_airflow | apache_arrow | apache_beam |
| apache_camel | apache_flink | apache_hadoop |
| apache_ignite | apache_incubator-doris | apache_incubator-superset |
| apache_kafka | apache_shardingsphere | apache_spark |
| apple_swift | bitcoin_bitcoin | dotnet_aspnetcore |
| dotnet_roslyn | dotnet_runtime | facebook_react-native |
| fdroid_fdroiddata | flutter_flutter | git_git |
| gitlab-org_gitlab | godotengine_godot | golang_go |
| Homebrew_homebrew-cask | Homebrew_homebrew-core | JetBrains_kotlin |
| kubernetes_kubernetes | llvm_llvm-project | microsoft_vscode |
| nodejs_node | openjdk_jdk | pandas-dev_pandas |
| python_cpython | pytorch_pytorch | rails_rails |
| ruby_ruby | rust-lang_rust | scikit-learn_scikit-learn |
| swiftlang_swift | symfony_symfony | tensorflow_tensorflow |