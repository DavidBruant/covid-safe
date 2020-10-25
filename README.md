# covid-safe

Ce document est un **brouillon**
Première rédaction : fin octobre 2020 
Auteur : David Bruant
Licence : CC-0
Attentes (non-légales) : être crédité comme auteur

## Exploration de problèmes avec StopCovid/TousAntiCovid

### Contexte

Il y a une [pandémie mondiale](https://fr.wikipedia.org/wiki/Pand%C3%A9mie_de_Covid-19) avec une poignée de caractéristiques qui la rendent bien efficace en terme de contaminations dans notre société rapide et mondialisée : 
- elle ne tue pas beaucoup en proportion (de l'ordre de ~1% des personnes infectées)
- elle se répand par voies respiratoires (via des goutellettes balistiques et sûrement par "aérosols", mais cette voie est encore en débat)
- environ un tiers des personnes infectées sont asymptomatiques (et donc n'ont pas vraiment de moyens de savoir qu'elles sont malades sans faire un test dédié)

À ses débuts en décembre 2019/janvier 2020, ce virus a été sous-estimé, ce qui amené, en France et dans beaucoup de pays à une saturation rapide des services de santé (hopitaux) et une mesure drastique d'urgence : un confinement de quelques mois

En France, après le confinement, le gouvernement a mis en place une série de mesures afin de limiter la propagation du virus, notamment (liste non-exhaustive) : 
- port du masque obligatoire dans certaines circonstances
- interdictions de rassemblements de plus de X personnes
- incitation au télétravail
- généralisation de tests pour détecter les malades et prévenir les personnes avec qui iels ont été en contact ; isolement des personnes testées positivement

Une de ces mesures est aussi la mise en place d'une application, StopCovid


### StopCovid

StopCovid est une application de *contact tracing* : elle enregistre avec quel.le.s autres utilisateur.rice.s de l'application, une personne a été en proximité prolongée
Si une personne informe l'application qu'elle a été contaminée, l'application informe automatiquement les personnes avec qui elle a été en contact récemment

L'espoir derrière est que ces personnes se fassent tester à leur tour et s'isolent si positives

D'après les mots du Président de la République, "StopCovid n'a pas marché". Le gouvernement sort une nouvelle version de l'application nommée TousAntiCovid. La partie *contact tracing* de l'application fonctionne de manière complètement similaire

Pour la suite, cet article va accepter comme hypothèse de départ, le fait qu'une application de *contact tracing* est un morceau de solution utile dans la lutte contre la propagation du Covid-19
Cette hypothèse est vraie sous condition que l'application soit massivement installée et utilisée
L'article va donc se concentrer sur l'adoption de cette application


## Aboutir à une utilisation massive d'une application de *contact tracing*

La [page du ministère de la santé](https://solidarites-sante.gouv.fr/soins-et-maladies/maladies/maladies-infectieuses/coronavirus/tousanticovid) parle du taux d'équipement des français.e.s en smartphone : 

> Le taux d’équipement en smartphone (...) était de 77% en 2019. Il reste toutefois un nombre considérable de Français qui ne sont pas équipés, notamment parmi les personnes âgées. L’équipe de recherche Inria étudie diverses possibilités afin de rendre TousAntiCovid accessible au plus grand nombre grâce à des solutions alternatives au smartphone. Nous travaillons avec les collectivités territoriales et les associations pour que des personnes peu à l’aise avec le numérique et volontaires pour télécharger l’application puissent être accompagnées.

D'autres articles ont déjà couverts [d'autres contraintes](https://www.ladepeche.fr/2020/06/01/stopcovid-lapplication-de-tracage-du-gouvernement-sera-t-elle-vraiment-efficace,8911922.php) : 
- les français.e.s n'ont pas vraiment envie d'installer StopCovid
- le bluetooth n'est pas très fiable
- le bluetooth n'est pas facile à activer correctement sur iPhone (~20% des français.e.s équipé.e.s d'un smartphone ont un iPhone)

Ça fait beaucoup de critères qui se cumulent sur le chemin d'une application vraiment efficace

Même en résolvant les problèmes techniques, il resterait [que les français.e.s n'ont pas envie d'installer l'application](https://www.lefigaro.fr/sciences/sondage-les-francais-approuvent-le-couvre-feu-20201022)


## Installer l'application

Quand [le ministère de la santé se pose à lui-même la question](https://solidarites-sante.gouv.fr/soins-et-maladies/maladies/maladies-infectieuses/coronavirus/tousanticovid) : 

> Est-il envisagé de rendre cette application obligatoire ?

il choisit de ne pas y répondre directement par "oui" ou "non", mais par : 

> Conformément aux lois et aux valeurs de la République française, seule l’hypothèse d’une application installée volontairement a été retenue. **C’est un enjeu de liberté publique.**

On choisira d'interpréter par nous-même que c'est "non", j'imagine... pour le moment

L'installation de TousAntiCovid est donc volontaire en France.


### Un enjeu de confiance

L'installation d'une application sur son téléphone est un acte de confiance. L'application aura certains droits sur les données du téléphone. Ai-je confiance dans le fait de partager cette accès avec cette application ?
L'application est créée et distribuée par l'état français. Ai-je envie de partager ces accès avec l'état français ?

Il n'y a pas une bonne réponse ou une réponse juste à ces questions. Il n'y a que des réponses individuelles, chaque réponse bonne pour la personne qui la prend.

Le gouvernement a mis en œuvre des mesures afin de créer de la confiance dans l'application : 
- Les codes sources de l'application des applications Android et iOS et du serveur [sont ouverts](https://gitlab.inria.fr/stopcovid19/accueil)
- L'application suit le protocole [ROBERT](https://github.com/ROBERT-proximity-tracing/documents/raw/master/ROBERT-infography-FR.pdf) qui fournit, en isolation, les garanties suivantes :
    - les noms des personnes qui téléchargent l'application ne sont jamais connus (ni par l'État ni par les autres utilisateur.rices)
    - les noms des personnes rencontrées ne sont jamais connus (ni par l'État ni par les autres utilisateur.rices)
    - les noms des personnes qui se déclarent contaminées ne sont jamais connus (ni par l'État ni par les autres utilisateur.rices)
    - le serveur central de l'État n'a accès à des informations anonymisées de rencontres uniquement quand une personne se déclare positive ; si on ne se déclare jamais malade, les données anonymisées de rencontres ne quittent pas notre téléphone
- [la CNIL a rendu un avis favorable](https://www.cnil.fr/fr/publication-de-lavis-de-la-cnil-sur-le-projet-dapplication-mobile-stopcovid)

L'espoir est que ces éléments aident à créer de la confiance des citoyens envers l'application


### Des limites en angles morts

#### "en isolation"

Plus haut : 

> L'application suit le protocole [ROBERT](https://github.com/ROBERT-proximity-tracing/documents/raw/master/ROBERT-infography-FR.pdf) qui fournit, **en isolation**, les garanties suivantes

L'état a accès à beaucoup beaucoup de données sur les citoyen.ne.s français.e.s dans ses différentes administrations

Aussi, les données du serveur central TousAntiCovid pourrait faire l'objet d'une attaque et d'une fuite de données. Il semble très improbable (car très difficile), mais pas impossible que les données du serveur central TousAntiCovid soient recoupables avec d'autres données et permettre une dés-anonymisation. 

Ce sujet est mentionné par le rapport CNIL, mais aucune analyse sérieuse du risque n'est disponible à ma connaissance. Que le gouvernement produise et partage une telle analyse aiderait à améliorer la confiance en l'utilisation de cette application. Sous réserve de bien comprendre quelles données personnelles le gouvernement a sur ses citoyens, une telle analyse pourrait être produites hors de l'état.


#### Le code qui tourne sur mon téléphone est-il le même que celui disponible en open source ?

Entre le [code open source que je peux trouver sur internet](https://gitlab.inria.fr/stopcovid19/stopcovid-android) et [l'application que je peux télécharger sur mon téléphone](https://play.google.com/store/apps/details?id=fr.gouv.android.stopcovid&hl=fr&gl=US), il y a une étape que l'on appelle usuellement *étape de build*. Il s'agit typiquement d'un programme que l'on lance et qui transforme le code source en une application téléchageable

Cette étape est habituellement effectuée par l'entité qui distribue l'application, ici l'état français

Peut-être que le code est open source, mais quelle garantie a-t-on que l'application *buildée* est fidèle à celle dont le code est distribué ?
La réponse est la même dans toutes les circonstances : aucune

Peut-être que l'application que je télécharge a du code supplémentaire caché

Le [même problème](https://brendaneich.com/2014/01/trust-but-verify/) a été rencontré par Mozilla qui a réalisé que légalement, le gouvernement US pouvait :
1. demander à Mozilla de rajouter du code pendant le process de *build* pour espionner les personnes qui utilisent Firefox
2. interdire à Mozilla de communiquer sur la différence entre le code open source et le logiciel téléchargeable *buildé*

La solution qu'a trouvé Mozilla est de [travailler à rendre Firefox "reproductible"](https://bugzilla.mozilla.org/show_bug.cgi?id=885777), c'est à dire fournir publiquement tous les outils de l'étape de *build* afin que **n'importe quelle personne extérieure** puisse :
- *rebuilder* Firefox
- constater que la version téléchargeable de Firefox sur le site mozilla.org et celle *buildée* indépendamment sont similaire à l'octet près

Ainsi, Mozilla remplirait ses obligations légales de modification et de non-communication, mais des personnes extérieures pourraient communiquer sur le fait que du code étrange se cache dans Firefox

En plus de partager le code source, il serait utile que le gouvernement français aide à démontrer que les applications mobiles sont reproductibles... et que des personnes se saisissent du sujet pour démontrer que les applications disponibles sur les stores sont fidèle au code open source

Je me permets de préciser que le sujet des "[reproducible *builds*](https://reproducible-builds.org/)" n'est pas très connu, même au sein des communautés libristes/open source, et donc je ne suis pas surpris que le gouvernement français n'ai pas été proactif sur ce front-ci, même de bonne foi


#### Les mises à jour















