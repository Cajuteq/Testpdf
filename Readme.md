<html><head>
<meta http-equiv="Content-Type" content="text/html; charset=utf-8">
</head><body>
<span style="font-family: SFBX2488;  font-size:30.5px">
Projet Interdisciplinaire ou de Découverte<br>de la Recherche<br>
<br>Smart City Lights<br>
<br></span>
<span style="font-family: SFBX1440;  font-size:17.5px">
supervisé par :<br></span>
<span style="font-family: SFBX1728;  font-size:21.0px">
CHOLEZ Thibault<br>&amp;<br>
<br>FESTOR Olivier<br>
<br></span>
<span style="font-family: SFBX1440;  font-size:17.5px">
réalisé par :<br></span>
<span style="font-family: SFBX1728;  font-size:21.0px">
GAUBE Aurélien<br>&amp;<br>
<br>JACQUET Corentin<br>
<br>4 juin 2018<br>
<br></span>
<span style="font-family: SFSX2074;  font-size:25.0px">
Table des matières<br></span>
<span style="font-family: SFSX1095;  font-size:13.5px">
1 Introduction<br>2 Étude des besoins<br>
<br>3 État de l’art<br>
<br></span>
<span style="font-family: SFRM1095;  font-size:14.0px">
3.1 Composants possibles <br>3.2 Technologies sans-ﬁl possibles <br>
<br>3.2.1 Portée et consommation <br>
<br>3.2.2 Autres critères <br>
<br>3.2.3 Solution retenue <br>
<br></span>
<span style="font-family: SFSX1095;  font-size:13.5px">
4 Mise en œuvre<br>4.1 Architecture générale de Smart-City Lights <br>
<br>4.2 Architecture matérielle du contrôle-projecteur <br>
<br>4.3 Micro-code développé <br>
<br>4.3.1 SKY-mote twizy <br>
<br>4.3.2 SKY-mote Lampadaire <br>
<br>4.4 Tests <br>
<br>4.5 Diﬃcultés rencontrées <br>
<br>5 Conclusion<br></span>
<span style="font-family: SFRM1095;  font-size:14.0px">
Glossaire <br></span>
<span style="font-family: SFSX2074;  font-size:25.0px">
1 Introduction<br></span>
<span style="font-family: SFRM1095;  font-size:14.0px">
Ce rapport s’inscrit dans le cadre du Projet Interdisciplinaire ou de Découverte de la Recherche<br>(PIDR) de notre formation à Télécom Nancy. Il vise à nous faire réﬂéchir sur un sujet très précis et<br>
<br>limité dans le cadre du thème étudié. Notre projet Smart City Lights a pour thème la ville intelligente<br>
<br>et plus précisément la gestion intelligente de l’éclairage public sur les parkings. Dans ce contexte, nous<br>
<br>devons concevoir et réaliser une infrastructure de lampadaires intelligents pour le parking du site de<br>
<br>Remicourt. Ceux-ci doivent s’allumer dynamiquement lorsque le parking est parcouru par un véhicule,<br>
<br>dans notre projet, incarné par la Twizy de Télécom Nancy. L’installation devra être autonome et pos-<br>
<br>siblement extensible à de nouveaux éléments voire à d’autres contextes.<br>
<br>La problématique de la ville intelligente est une problématique clé de la ville du futur. En eﬀet, l’en-<br>
<br>jeu est à la fois de réduire la consommation globale d’énergie, notamment en éteignant les éclairages<br>
<br>publique, sans pour autant augmenté l’insécurité lié à l’absence de lumière. La gestion des éclairages est<br>
<br>un enjeu majeur de la lutte contre le réchauﬀement climatique car la quasi totalité des villes utilisent un<br>
<br>éclairage publique et l’utilisation d’éclairages intelligents permet de réduire de 70% la consommation<br>
<br>électrique pour l’éclairage publique d’une ville. L’utilisation de luminaires intelligents pourrait<br>
<br>donc aider à résoudre une problématique énergétique mondiale et ainsi améliorer le futur de l’humanité.<br>
<br>Mais pour atteindre cet objectif, il faut garantir aux villes un éclairage autonome peu consommateur,<br>
<br>ﬁable quel que soit les circonstances, et qui s’adapte eﬃcacement à la présence humaine dans sa zone<br>
<br>de contrôle.<br>
<br>La suite du rapport détaille l’étude des besoins dans le chapitre 2, puis l’état de l’art des technologies<br>
<br>possibles dans le chapitre 3. La solution technique que nous avons retenue et sa mise en oeuvre pour<br>
<br>répondre à la problématique sont décrites dans le chapitre 4. Nous nous sommes particulièrement at-<br>
<br>taché à la réalisation technique et notamment informatique, mais il ne faut pas perdre de vue l’aspect<br>
<br>économique et écologique, notamment dans le choix des équipements.<br>
<br></span>
<span style="font-family: SFSX2074;  font-size:25.0px">
2 Étude des besoins<br></span>
<span style="font-family: SFRM1095;  font-size:14.0px">
Notre cas d’étude est le parking de l’école. Celui-ci comporte un certain nombre de lampadaires<br>classiques qui s’allument selon l’horaire de la journée. Ils seront dans le cadre de ce projet complétés<br>
<br>par des projecteurs à LEDs qui interagirons avec le passage d’un véhicule connecté : la Twizy.<br>
<br>Le besoin exprimé par l’équipe encadrante comporte deux modes d’éclairage :<br>
<br>— Le premier, d’usage courant, qui allume les lampadaires devant le véhicule et éteint ceux derrière<br>
<br>lui.<br>
<br>— Le second, synonyme d’alerte, qui fait clignoter les lampadaires dans un certain périmètre autour<br>
<br>du véhicule ayant déclenché l’alerte.<br>
<br>Le système devra être suﬃsamment réactif pour être mis en place dans le cadre d’une conduite<br>
<br>de nuit à vitesse modérée. Il devra de plus prendre en compte que plusieurs véhicules peuvent rouler<br>
<br>simultanément sur le réseau. Des délais courts, un dispositif sécurisé et une anticipation dynamique<br>
<br>des déplacements seront des compléments appréciables.<br>
<br></span>
<span style="font-family: SFCC1095;  font-size:13.0px">
Figure </span>
<span style="font-family: SFRM1095;  font-size:14.0px">
2.1 – Parking d’expérimentation<br>Dans le but de réduire le champs de développement, nous avons d’abord concentré nos eﬀort sur<br>
<br>une simulation représentant un déplacement linéaire du véhicule selon un axe parallèle à la rangée<br>
<br>de lampadaires. Ce cadre de recherche restreint nous a notamment permis d’éviter les calculs liés à<br>
<br>l’ordinateur de bord et au GPS de la twizy. Dans un second temps, nous nous sommes appliqués<br>
<br>à permettre l’usage du mode alerte, la présence simultanée de plusieurs véhicules et les trajectoires<br>
<br>complexes.<br>
<br></span>
<span style="font-family: SFSX2074;  font-size:25.0px">
3 État de l’art<br></span>
<span style="font-family: SFRM1095;  font-size:14.0px">
La première étape de notre recherche est la réalisation d’un état de l’art dans le domaine des tech-<br>nologies de communications sans ﬁl courtes et moyennes portées. Nous avons donc établis une liste des<br>
<br>matériels, technologies et protocoles utilisés pour ce type d’application, et choisi des critères permet-<br>
<br>tant de les comparer.<br>
<br>Nous envisagerons dans un premier temps les composants matériels disponibles, puis nous compare-<br>
<br>rons les diﬀérentes technologies sans ﬁl. Nous étudierons ensuite les diﬀérents protocoles réseaux qui<br>
<br>répondront à nos besoins. Nous conclurons alors sur la solution que nous aurons choisie.<br>
<br></span>
<span style="font-family: SFSX1440;  font-size:17.5px">
3.1 Composants possibles<br></span>
<span style="font-family: SFRM1095;  font-size:14.0px">
Il existe actuellement une grande variété de composants matériels permettant de faire communiquer<br>des objets, dont une grande partie est expérimental et donc non disponible à l’achat. Les deux princi-<br>
<br>paux actuellement disponible sur le marché sont les Raspberry Pi et les Arduino, tous deux existants<br>
<br>en de multiple version et variantes, et possédant des modules d’extensions très divers. Il existe d’autres<br>
<br>types de cartes, moins orientées vers le tous public, et souvent développer dans le cadre de recherche<br>
<br>par des université. Une des plus courante est la TelosB aussi connu sous le nom de carte SKY-mote,<br>
<br>terme que nous emploierons dans ce rapport. Il est possible de rajouter des modules sur ces cartes,<br>
<br>dans le but de les rendre réceptives à leur environnement (capteurs luminosité, ...) ou d’augmenter<br>
<br>leurs capacités existantes (antennes, batteries, ...). Dans le cadre de cet état de l’art, nous n’essayerons<br>
<br>pas de comparer toutes les conﬁgurations, et nous contenterons des caractéristiques générales, car les<br>
<br>modules coûtent souvent plus cher que la carte sur laquelle ils se ﬁxent.<br>
<br>Nous avons donc restreint ce comparatif aux trois modèles les plus courant et avons essayé de les<br>
<br>comparer en fonction de leur autonomie, puissance, coût, fréquences et protocoles supportés mais aussi<br>
<br>de leur disponibilité à l’école. Il s’est avérer très compliqué d’obtenir des informations précises, en de-<br>
<br>hors du coût et de la fréquence, car d’une part, l’autonomie dépends quasi-exclusivement de la source<br>
<br>d’alimentation et il est donc plus logique de dimensionner correctement la batterie utilisé que de choisir<br>
<br>sur cette valeur, d’autre part, les protocoles supportés dépendent uniquement du software déployé, et<br>
<br>cette valeur ne permet donc pas de choisir entre les matériels.<br>
<br>Les ﬁgures suivantes (3.1, 3.2 et 3.3) illustrent ces composants matériels et le tableau 3.1 leurs prin-<br>
<br>cipales caractéristiques.<br>
<br></span>
<span style="font-family: SFCC1095;  font-size:13.0px">
Figure </span>
<span style="font-family: SFRM1095;  font-size:14.0px">
3.1 – Raspberry 3<br></span>
<span style="font-family: SFCC1095;  font-size:13.0px">
Figure </span>
<span style="font-family: SFRM1095;  font-size:14.0px">
3.2 – Arduino<br></span>
<span style="font-family: SFCC1095;  font-size:13.0px">
Figure </span>
<span style="font-family: SFRM1095;  font-size:14.0px">
3.3 – SKY-mote<br>Technologie<br>
<br>Rasberry Pi 3<br>
<br>Arduino<br>
<br>Telos-B (SKY-Mote) 8MHz<br>
<br>Cadence<br>
<br>1200Mhz 6.2 Gﬂops 40</span>
<span style="font-family: TeX-feymr10;  font-size:11.5px">
e</span>
<span style="font-family: SFRM1095;  font-size:14.0px">
* Toutes*<br>16Mhz 0.1 Mﬂops 20</span>
<span style="font-family: TeX-feymr10;  font-size:11.5px">
e</span>
<span style="font-family: SFRM1095;  font-size:14.0px">
* Toutes*<br>80</span>
<span style="font-family: TeX-feymr10;  font-size:11.5px">
e</span>
<span style="font-family: SFRM1095;  font-size:14.0px">
** 2,4GHz<br>?<br>
<br>Puissance<br>
<br>Coûts Fréquences Protocoles Supportés<br>
<br>Tous<br>
<br>Tous<br>
<br>Tous<br>
<br>*Selon modules d’extensions **Telecom Nancy possède déjà des Telos-B<br>
<br></span>
<span style="font-family: SFCC1095;  font-size:13.0px">
Table </span>
<span style="font-family: SFRM1095;  font-size:14.0px">
3.1 – Composants matériels possibles<br>Ce tableau montre bien la diﬀérence de puissance entre les Raspberry Pi 3, qui sont de véritables<br>
<br>ordinateurs, et les TelosB SKY-Mote, qui sont des puces connectés. Si le choix se limitait aux caractéris-<br>
<br>tiques décrites ici, le choix se porterait probablement sur les Raspberry Pi 3 qui sont les plus puissants,<br>
<br>mais il faut aussi pensez à la consommation horaire, et bien sur au coût, car l’école possède déjà les<br>
<br>SKY-Mote nécessaire. En outre, la fréquence utilisé n’est pas primordiale, tant qu’elle n’interfère pas<br>
<br>avec les équipements traditionnelles déjà présent, tels que le réseau wiﬁ.<br>
<br>Ces informations, ont portée notre choix vers les TelosB SKY-Mote développé par l’université de<br>
<br>Berkeley.<br>
<br></span>
<span style="font-family: SFSX1440;  font-size:17.5px">
3.2 Technologies sans-ﬁl possibles<br></span>
<span style="font-family: SFSX1200;  font-size:15.0px">
3.2.1 Portée et consommation<br></span>
<span style="font-family: SFRM1095;  font-size:14.0px">
Conjointement avec le choix du matériel, il est nécessaire d’identiﬁer la technologie qui répond le<br>mieux à nos besoins. Nous nous sommes restreints aux technologies sans ﬁl, car une installation ﬁlaire<br>
<br>n’est pas envisageable sans travaux importants. De plus, nous avons classés les technologies en fonction<br>
<br>de leur portée, en éliminant directement les technologies aux portées trop faibles (Bluetooth, NFC, ...)<br>
<br>et celles aux portées trop longues pour notre utilisation, car celles-ci ne permettent pas une communi-<br>
<br>cation suﬃsamment précise ou sont alors trop énergivores.<br>
<br>La ﬁgure 3.4 permet d’observer les principales technologies sans ﬁls, d’après leur porté et leur débit,<br>
<br>on y constate notamment le faible recouvrement des technologies, chacune ayant son usage propre et<br>
<br>ses caractéristiques uniques.<br>
<br>Le tableau 3.2 synthétise les principales caractéristiques des protocoles sans ﬁl en terme de consom-<br>
<br>mation et de portée. Il en ressort que les technologies qui correspondent le plus à la topologie de notre<br>
<br>milieu d’étude sont le Wiﬁ et le 802.15.4, car ils ont tous les deux une portée d’environ 100m en terrain<br>
<br>ouvert. La technologie LORA est quand à elle possible, mais pourrait donner lieu à des imprécisions. Le<br>
<br>Bluetooth pourrait être utiliser, si les lampadaires communiquent entre eux pour diﬀuser l’information<br>
<br>de l’arrivée d’un véhicule.<br>
<br>On peut aussi constater que les consommations électriques de ces technologies sont loin d’être toutes<br>
<br>équivalentes, avec de fortes variations d’échelles puisqu’on passe de 1550mW à 36.9mW en transmis-<br>
<br>sion entre le Wiﬁ et le 802.15.4. La diﬀérence lorsque les antennes sont au repos est encore plus forte,<br>
<br>avec une consommation de 0.06µW pour le 802.15.4 et une de 6mW pour le LORA, soit 100 000 fois plus.<br>
<br>A la lumière de ce comparatif, il a été choisi de mettre en place le protocole 802.15.4, qui répond à<br>
<br>la fois à nos exigences de portée et de faible consommation.<br>
<br>Technologie<br>
<br>Wiﬁ<br>
<br>Bluetooth<br>
<br>802.15.4<br>
<br>LORA<br>
<br>Portée Conso. Transmission Conso. endormi<br>
<br>100m<br>
<br>10m<br>
<br>100m<br>
<br>5km<br>
<br>1550mW<br>
<br>215mW<br>
<br>36.9mW<br>
<br>400mW<br>
<br>6600µW<br>
<br>330µW<br>
<br>0.06µW<br>
<br>6mW<br>
<br></span>
<span style="font-family: SFCC1095;  font-size:13.0px">
Table </span>
<span style="font-family: SFRM1095;  font-size:14.0px">
3.2 – Comparatif des diﬀérentes technologies sans ﬁ<br></span>
<span style="font-family: SFCC1095;  font-size:13.0px">
Figure </span>
<span style="font-family: SFRM1095;  font-size:14.0px">
3.4 – Comparatif débit/portée des diﬀérentes technologies sans ﬁl<br></span>
<span style="font-family: SFSX1200;  font-size:15.0px">
3.2.2 Autres critères<br></span>
<span style="font-family: SFRM1095;  font-size:14.0px">
Outre les considérations de portée et de consommation, les technologies sans-ﬁl et les protocoles<br>associés présentent d’autres caractéristiques importantes pour notre problématique. Nous avons donc<br>
<br>comparé les diﬀérents protocoles qui semblaient répondre le mieux aux besoins, nous avons souhaité<br>
<br>comparer leur diﬃculté d’implantation, leur sécurité, leur débit et leur topologie possible. La diﬃculté<br>
<br>d’implémentation est une notion très subjective, qu’il est diﬃcile d’évaluer et nous ne l’avons pas gar-<br>
<br>der comme critère. Les critères restant sont résumé dans le tableau 3.3.<br>
<br>Protocole<br>
<br>Wiﬁ<br>
<br>Bluetooth<br>
<br>802.15.4(ZigBee)<br>
<br>802.15.4(6LoWPAN)<br>
<br>LORA<br>
<br>Sécurité<br>
<br>Débit Topologie<br>
<br>Sécurisé(AES)<br>
<br>Selon Mode utilisé<br>
<br>54MB/s étoile, arbre, maillé<br>
<br>2MB/s étoile<br>
<br>Selon implémentation 200kB/s étoile, arbre, maillé<br>
<br>250kB/s étoile, arbre, maillé<br>
<br>30kB/s étoile<br>
<br>Sécurisé(AES)<br>
<br>AES128<br>
<br></span>
<span style="font-family: SFCC1095;  font-size:13.0px">
Table </span>
<span style="font-family: SFRM1095;  font-size:14.0px">
3.3 – Comparatif des diﬀérentes technologies sans-ﬁl<br>On constate que tous les protocoles oﬀrent une bonne sécurité si on prend la peine de l’implémenter,<br>
<br>les débits varies et le 6LowPAN présente un des plus bas débit à 250kB/s. La topologie varie selon<br>
<br>les protocoles, et la topologie en étoile étant adaptée à notre problématique dans laquelle une voiture<br>
<br>informe n lampadaire autonome de sa position, la topologie ne limite pas notre choix. En choisissant<br>
<br>le 6LowPAN, nous optons donc pour un protocole qui oﬀre un relativement bas débit, mais cela n’est<br>
<br>pas très grave car les volumes de données à transmettre sont extrêmement faible.<br>
<br></span>
<span style="font-family: SFSX1200;  font-size:15.0px">
3.2.3 Solution retenue<br></span>
<span style="font-family: SFRM1095;  font-size:14.0px">
Suite aux diﬀérents comparatifs, nous avons choisi d’implémenter la technologie 802.15.4 sur les<br>cartes SKY-mote avec le protocole 802.15.4 6LowPAN associé. Ce choix tiens d’abord d’un soucis<br>
<br>de correspondance matériel/technologie/protocole, mais aussi des caractéristiques individuelles des<br>
<br>éléments cités tels que présentés dans les paragraphes précédents. Cette technologie de liaisons est<br>
<br>associée à des projecteurs à LEDs qui assurent une forte luminosité avec une faible consommation<br>
<br>électrique, montés sur batterie, tel que cela est décrit par la ﬁgure 4.1.<br>
<br></span>
<span style="font-family: SFSX2074;  font-size:25.0px">
4 Mise en œuvre<br></span>
<span style="font-family: SFSX1440;  font-size:17.5px">
4.1 Architecture générale de Smart-City Lights<br></span>
<span style="font-family: SFRM1095;  font-size:14.0px">
L’architecture générale est conçue autour de SKY-mote autonomes capables de communiquer entre-<br>eux en utilisant le protocole 802.15.4 . C’est un réseau décentralisé, où chacun est capable de commu-<br>
<br>niquer avec tout le monde (dans une limite de portée physique) sans dépendre d’un service tiers. La<br>
<br>topologie déployé est un réseau en étoile à partir de chaque voiture, dans laquelle chaque mote émet<br>
<br>et reçoit des messages en broadcast contenant toutes les informations nécessaire sans qu’il y ai besoin<br>
<br>d’initialiser des connexions. Outre la simplicité d’implementation, cette solution oﬀre aussi une faible<br>
<br>consommation de bande passante car très peu de messages sont echangés.<br>
<br>Côté voiture, le SKY-mote embarqué dans la twizy connaît sa position grâce au GPS embarqué dans<br>
<br>la twizy. Ce GPS est relié à un micro ordinateur présent dans la twizy, qui communique les coordonnées<br>
<br>actuelles de la voiture au SKY-mote. Le SKY-mote communique alors cette position en </span>
<span style="font-family: SFTI1095;  font-size:13.5px">
broadcast </span>
<span style="font-family: SFRM1095;  font-size:14.0px">
et le<br>mode d’éclairage souhaité à toutes les SKY-mote à porté.<br>
<br>Côté lampes, les autres SKY-motes (ﬁxés aux lampadaires) connaissent leur propre position GPS<br>
<br>enregistrée en dur à l’installation car celle-ci est ﬁxe. Quand les motes reçoivent les coordonnées de<br>
<br>la twizy, un calcul de distance est eﬀectué avec la latitude et longitude récupérées et l’éclairage est<br>
<br>déclenché si nécessaire, c’est à dire si la distance entre la voiture et le lampadaire est assez faible. La<br>
<br>durée de l’éclairage est mise à jour à chaque réception de position donnant une distance suﬃsamment<br>
<br>courte (20mètres dans nos tests), et s’eﬀectue de manière alternative si le mode alerte est enclenché.<br>
<br>Il a été envisagé de réaliser une rediﬀusion du message de la twizy avec un seul bond aﬁn de per-<br>
<br>mettre aux SKY-motes hors de portée de la twizy de recevoir tout de même sa position, mais cela ne<br>
<br>s’est pas révéler nécessaire, la porté de la technologie 802.15.4 étant largement suﬃsante pour assurer<br>
<br>de bonne communication directe.<br>
<br>La solution permet une gestion de plusieurs voitures en simultané et la défaillance d’un SKY-mote<br>
<br>n’a pas de répercussion sur le reste de l’environnement, seul le lampadaire concerné cesse de fonction-<br>
<br>ner. De plus il n’y a pas d’interférence entre deux véhicules, chacun envoyant sa position a tous ceux<br>
<br>qui le reçoivent et si les deux véhicules sont proches, le lampadaire qui reçoit les deux décide juste de<br>
<br>s’allumer quand il y est déjà, sans que cela perturbe le fonctionnement globale du système.<br>
<br></span>
<span style="font-family: SFSX1440;  font-size:17.5px">
4.2 Architecture matérielle du contrôle-projecteur<br></span>
<span style="font-family: SFRM1095;  font-size:14.0px">
Le principe est d’utiliser un SKY-mote autonome, qui décide d’allumer ou d’éteindre son projecteur<br>selon ce qu’il reçoit sur son antenne 802.15.4. Il reçoit des messages contenant toutes les données né-<br>
<br>cessaires directement de la voiture. Il calcule la distance qui le sépare de la voiture et la compare à un<br>
<br>seuil ﬁxé d’avance. Si la distance est inférieur au seuil, le SKY-mote décide d’allumer son projecteur à<br>
<br>LED, et agit pour cela sur un relais électro-magnétique tel que présenté sur la ﬁgure 4.1<br>
<br>Des projecteurs LED seront mis en place sur chaque lampadaire sur le parking, couplés à des SKY-<br>
<br>mote selon le schéma de la ﬁgure 4.1 (le mote est représenté par son port d’extension :<br>
<br>La solution proposée n’a malheureusement pas pu être testée physiquement car les projecteurs n’ont<br>
<br>pas été reçus dans les temps. Nous avons donc réalisé une simulation Cooja permettant<br>
<br></span>
<span style="font-family: SFCC1095;  font-size:13.0px">
Figure </span>
<span style="font-family: SFRM1095;  font-size:14.0px">
4.1 – Schéma du couplage SKY-mote / projecteur<br>de faire la démonstration du code développé. Nous avons aussi essayer de réaliser une mise en oeuvre<br>
<br>d’usage des ports d’extension, pour prouver la faisabilité du couplage SKY-mote/projecteur LED, mais<br>
<br>cela n’a pas pu être réalisé avec ContikiOS. Des essais prometteurs mais non concluant ont<br>
<br>pu être réalisé avec TinyOS. En attendant la réalisation d’un code fonctionnel, le reste<br>
<br>du système à été développer en utilisant les LEDs intégrés aux SKY-Mote.<br>
<br>D’un point de vue hardware, lorsque la décision d’allumer le lampadaire est prise, le SKY-mote envoie<br>
<br>une impulsion électrique dans une pin de son port d’extension. Celui-ci est relié électriquement à un<br>
<br>relais électronique bistable contrôlant le circuit de puissance du projecteur à LED. Ce relais<br>
<br>permet de séparer l’électronique de contrôle, constitué du SKY-mote de l’électronique de puissance<br>
<br>qui alimente le projecteur à LED. Son fonctionnement bistable permet de ne consommer de l’énergie<br>
<br>pour la commande que lors du changement de commande. Le circuit de puissance est constitué d’une<br>
<br>batterie, dans notre cas un </span>
<span style="font-family: SFTI1095;  font-size:13.5px">
power-pack </span>
<span style="font-family: SFRM1095;  font-size:14.0px">
qui alimente le projecteur à LED, un interrupteur classique<br>permet à un utilisateur de couper manuellement le projecteur, pour d’éventuelles maintenances, tandis<br>
<br>que le relais électronique agit comme un interrupteur à commande numérique.<br>
<br></span>
<span style="font-family: SFSX1440;  font-size:17.5px">
4.3 Micro-code développé<br></span>
<span style="font-family: SFRM1095;  font-size:14.0px">
Pour réaliser l’architecture envisagée, nous avons écrit deux programmes en C pouvant s’exécuter<br>sur les SKY-mote, chacun de ces codes est ensuite adapté pour y inscrire soit pour les voitures, le trajet<br>
<br>du mote (en l’absence de connection à un GPS embarqué dans la twizy) soit pour les lampadaire, la<br>
<br>position GPS à laquelle le mote sera ﬁxé.<br>
<br></span>
<span style="font-family: SFSX1200;  font-size:15.0px">
4.3.1 SKY-mote twizy<br></span>
<span style="font-family: SFRM1095;  font-size:14.0px">
Ce programme a pour but de permettre au SKY-mote connecté à la twizy de pouvoir communiquer<br>les coordonnées GPS de celle-ci aux autres SKY-motes en utilisant le protocole 802.15.4 .<br>
<br>Les tests sur le Parking ne pouvant être réalisés faute de matériel, la liaison entre le module GPS de<br>
<br>la twizy et la SKY-mote n’a pas été implémentée. Cela pourra être réalisé via la connexion USB des<br>
<br>SKY-mote, qui peux être branché directement sur la carte DFRobot servant d’ordinateur de bord à la<br>
<br>twizy. Cette carte connaît la position GPS de la twizy grâce à un GPS Garmin 18x lvc.<br>
<br>Nous nous contentons ici d’enregistrer dans notre programme une coordonnée GPS à émettre, que l’on<br>
<br>peut faire varier dynamiquement pour les simulations. La version actuelle simule numériquement la<br>
<br>traversée du parking dans la longueur.<br>
<br>L’envoi se fait sous la forme d’une chaîne de caractère concaténant la latitude, la longitude et un<br>
<br>ﬂag de valeur 1 si le mode alerte est actif. Les 6 premiers caractères correspondent aux 6 premiers<br>
<br>décimaux de degré de la latitude, suivis des 6 premiers décimaux de degré de la longitude et enﬁn un<br>
<br>1 ou un 0 pour le ﬂag d’alerte.<br>
<br></span>
<span style="font-family: SFSX1200;  font-size:15.0px">
4.3.2 SKY-mote Lampadaire<br></span>
<span style="font-family: SFRM1095;  font-size:14.0px">
Ce programme est exécuté sur chaque SKY-mote de lampadaire et permet d’enclencher l’éclairage<br>de ceux-ci si la twizy est à portée. La latitude et la longitude de l’emplacement du lampadaire sont<br>
<br>enregistrées directement dans deux variables aﬁn de réaliser un calcul de distance par approximation<br>
<br>linéaire. Les SKY-motes fonctionnant en 16 bits empêchant l’utilisation des bibliothèques mathéma-<br>
<br>tiques usuelles, il a été nécessaire de coder une fonction racine carrée, ce qui a été réalisé via l’algorithme<br>
<br>d’approximation de Newton. Cela a de plus l’avantage de réduire la somme des calculs réalisés par la<br>
<br>carte, ce qui réduit sa consommation et accélère son fonctionnement.<br>
<br>La SKY-mote est capable de recevoir le </span>
<span style="font-family: SFTI1095;  font-size:13.5px">
broadcast</span>
<span style="font-family: SFRM1095;  font-size:14.0px">
 envoyé par le SKY-mote de la twizy sous<br>forme de chaîne de caractères. Nous la décodons pour récupérer la latitude et longitude de la twizy<br>
<br>ainsi que le ﬂag correspondant au mode d’aﬃchage. Le programme calcule la distance par rapport à<br>
<br>ses propres coordonnées et si la twizy est à moins de 20 mètres, l’éclairage de la LED est enclenché<br>
<br>pour 5 secondes. Si le mode alerte est activé via le ﬂag dédié, l’éclairage s’eﬀectuera de manière à<br>
<br>clignoter à une fréquence d’une demie-seconde. En mode classique, la durée d’éclairage est remise à 5<br>
<br>secondes à chaque nouvelle réception de position en dessous de 20 mètres. Il est également envisagé<br>
<br>que la SKY-mote rediﬀuse en </span>
<span style="font-family: SFTI1095;  font-size:13.5px">
broadcast </span>
<span style="font-family: SFRM1095;  font-size:14.0px">
les coordonnées de la twizy pour transmettre l’information aux<br>autres lampadaires hors de portée du message de la twizy. Ce renvoi en </span>
<span style="font-family: SFTI1095;  font-size:13.5px">
broadcast </span>
<span style="font-family: SFRM1095;  font-size:14.0px">
semble cependant<br>superﬂu au vu de la faible taille des installations (parking) et de la portée des antennes utilisées ( 125m).<br>
<br></span>
<span style="font-family: SFSX1440;  font-size:17.5px">
4.4 Tests<br></span>
<span style="font-family: SFRM1095;  font-size:14.0px">
Les tests ont été réalisés avec le simulateur Cooja permettant de visualiser les diﬀérentes<br>SKY-motes ainsi que leurs portées d’émission. L’environnement du parking a été reproduit en plaçant<br>
<br>les SKY-mote représentant les lampadaires dans la même conﬁguration que le parking de Télécom<br>
<br>Nancy.<br>
<br></span>
<span style="font-family: SFCC1095;  font-size:13.0px">
Figure </span>
<span style="font-family: SFRM1095;  font-size:14.0px">
4.2 – Schéma d’une simulation avec déplacement linéaire<br>Le déplacement de la twizy sur le parking a été simulé en faisant varier la position GPS émise par<br>
<br>la SKY-mote représentant la twizy. Le Mote représentant la twizy bougeant lui aussi de manière ap-<br>
<br>proximative grâce à l’extension Mobility de Cooja. Sur la ﬁgure 4.2, on constate que les<br>
<br>motes hors de portée  sont inactifs, ceux qui sont à portée, mais en dehors du cercle de 20 mètres<br>
<br>reçoivent mais restent éteint, tandis que les autres qui sont à portée et en dessous de 20 mètres sont<br>
<br>allumés.<br>
<br>D’autres tests ont été réalisé avec deux véhicules comme sur la ﬁgure 4.3. On y a constater les inter-<br>
<br>actions lorsque les deux véhicules sont à portée des mêmes lampadaires. On commence à y apercevoir<br>
<br>la limite des tests sur Cooja, la synchronisation entre des déplacements GPS et la position des voitures<br>
<br>dans la simulation est diﬃcile à mettre en place. Néanmoins on prouve que notre système peut gérer<br>
<br>plusieurs voitures en même temps.<br>
<br></span>
<span style="font-family: SFCC1095;  font-size:13.0px">
Figure </span>
<span style="font-family: SFRM1095;  font-size:14.0px">
4.3 – Schéma d’une simulation impliquant deux voitures<br>Nous avons réussi à réaliser 3 scénarios diﬀérents, celui d’une voiture avançant sur le parking, celui<br>
<br>d’une voiture avançant puis qui s’arrête pour déclencher le mode alerte, et enﬁn celui de deux voitures<br>
<br>circulant sur le parking. Les résultats sont satisfaisants, d’après ces simulations, il n’est pas nécessaire<br>
<br>de réaliser des retransmissions aux autres SKY-motes aux alentours pour augmenter la portée de<br>
<br>l’information. Nos simulations se déroulant dans l’environnement du Parking de Télécom Nancy, ceux-<br>
<br>ci nous invitent pour une prochaine étape à les réaliser en version grandeur nature directement sur<br>
<br>le parking pour vériﬁer le bon fonctionnement en condition réel, et être plus maniable quand aux<br>
<br>mouvements de la twizy pour des tests plus approfondis.<br>
<br></span>
<span style="font-family: SFSX1440;  font-size:17.5px">
4.5 Diﬃcultés rencontrées<br></span>
<span style="font-family: SFRM1095;  font-size:14.0px">
La prise de connaissance des technologies utilisées –SKY-mote, Contiki , Cooja et 802.15.4–<br>a nécessité la lecture de documentations longues, complexes et souvent incomplètes car axées sur des<br>
<br>outils ou des situations très spéciﬁques. La mise en place de circuit électriques utilisant les ports d’ex-<br>
<br>tension des SKY-motes étant peu répandue, il a été très compliqué de trouver des exemples concernant<br>
<br>leur utilisation.<br>
<br>La présence concurrentiel de contikiOS et TinyOS  à elle aussi perturbé nos recherches car<br>
<br>tous les exemples utilisés pour TinyOS sont rédigé en NesC, qui est un dialecte du C non compatible<br>
<br>avec Contiki. Il a parfois été nécessaire d’eﬀectuer un travail de traduction entre les languages pour<br>
<br>obtenir des résultats.<br>
<br>Nous avons aussi fait face à la limitation de puissance des SKY-motes en terme d’espace de sto-<br>
<br>ckage, mais surtout en terme de longueur des registres de calcul, puisque le fonctionnement 16 bits<br>
<br>des processeurs MSP430 des SKY-mote les empêche d’utiliser la majeure partie des bibliothèques C<br>
<br>standard. Nous avons dû adapter notre programme avec une implémentation spéciﬁque du calcul de<br>
<br>distance, la reprogrammation de la fonction racine carré en utilisant le principe de Newton ou encore<br>
<br>des adaptations au niveau du type de données utilisées, toujours dans le but de rester sur les cases de<br>
<br>16bits de l’architecture CPU utilisé.<br>
<br></span>
<span style="font-family: SFSX2074;  font-size:25.0px">
5 Conclusion<br></span>
<span style="font-family: SFRM1095;  font-size:14.0px">
Ce PIDR s’est inscrit dans la problématique de la ville intelligente, avec pour objectif de rendre<br>dynamique et interactif les éclairages publique, notamment par le biais d’une voiture connecté : la<br>
<br>twizy.<br>
<br>Ce Projet Interdisciplinaire ou de Découverte de la Recherche à été enrichissant sur le plan du déve-<br>
<br>loppement de logiciel proche des couches réseaux et proche du matériel. Il nous a permis de comprendre<br>
<br>l’envoi de message dans un réseau décentralisé de capteurs autonomes. Nous avons réussi à déployer sur<br>
<br>simulateur une série d’algorithme interagissant entre eux via la technologie sans ﬁl 802.15.4, et avons en<br>
<br>cela établis la preuve du concept utilisé. Nous avons constaté avec plaisir que nos algorithmes simples<br>
<br>donnaient de bon résultats pour suivre en éclairage une voiture avançant lentement sur un parking. La<br>
<br>non-réception du matériel nous a contraint à adapter notre méthode de travail, notamment en réalisant<br>
<br>plus de tests sur l’environnement Cooja et il a par conséquent été décevant de ne pas pouvoir le mettre<br>
<br>en place physiquement.<br>
<br>Nous n’avons pas réussi à atteindre tous les objectifs, mais le développement global est bien avancés,<br>
<br>avec de bonne simulations. Il reste principalement à ﬁnaliser l’interaction entre les Pins d’extensions<br>
<br>GPIO et les projecteurs, ce qui demande de réaliser des tests avec du matériel réel.<br>
<br>De manière général, plusieurs poursuites et améliorations du projet peuvent être envisagées :<br>
<br>— Prendre en compte la vitesse de la voiture pour optimiser l’éclairage, notamment en amont de la<br>
<br>trajectoire.<br>
<br>— Établir la connexion entre la twizy et la SKY-mote pour accéder aux données de bord de la twizy.<br>
<br>— Relier eﬀectivement les SKY-mote aux projecteurs (quand ils seront reçus) pour déclencher un<br>
<br>éclairage au lieu d’allumer une LED.<br>
<br>Ces trois points sont accompagnés d’une dernière tâche qui consistera à régler ﬁnement les temps<br>
<br>d’allumage, les fréquences de clignotement, les portées seuils pour l’allumage, ... pour optimiser la<br>
<br>consommation électrique ﬁnale de l’installation, et atteindre ainsi l’objectif d’économie d’énergie à<br>
<br>l’origine du projet.<br>
<br></span>
<span style="font-family: SFSX1440;  font-size:17.5px">
Glossaire<br></span>
<span style="font-family: SFSX1095;  font-size:13.5px">
Projet Interdisciplinaire ou de Découverte de la Recherche </span>
<span style="font-family: SFRM1095;  font-size:14.0px">
Projet obligatoire d’initiation à la re-<br>cherche active au sein d’une équipe ou d’un laboratoire visant à mettre en place une solution<br>
<br>pertinente à un problème précis.<br>
<br></span>
<span style="font-family: SFSX1095;  font-size:13.5px">
Smart City </span>
<span style="font-family: SFRM1095;  font-size:14.0px">
Une ville intelligente – de l’anglais «Smart City» – est une zone urbaine intégrant les<br>technologies de l’information et de la communication, et des dispositifs connectés au réseau dans<br>
<br>le but d’optimiser ses services urbains.<br>
<br></span>
<span style="font-family: SFSX1095;  font-size:13.5px">
Telos B SKY-Mote </span>
<span style="font-family: SFRM1095;  font-size:14.0px">
Carte programmable développée par l’université de Berkeley, elle permet no-<br>tamment la mise en place de réseau de capteurs autonomes relié en 802.15.4. Ces cartes parfois<br>
<br>abrégé Mote sont de plus en plus utilisé pour mettre en place des objets et structures connectées<br>
<br>dites intelligentes.<br>
<br></span>
<span style="font-family: SFSX1095;  font-size:13.5px">
Twizy </span>
<span style="font-family: SFRM1095;  font-size:14.0px">
La Renault Twizy est une petite voiture électrique orientée sur l’écomobilité. Celle de l’école<br>dispose d’équipements supplémentaires pour la rendre interactive avec son environnement.<br>
<br></span>
<span style="font-family: SFSX2074;  font-size:25.0px">
Bibliographie<br></span>
<span style="font-family: SFRM1095;  font-size:14.0px">
.<br></span></body></html>
