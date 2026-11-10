### Rapport d'analyse : Matrice des précipitations et de l'exposition aux inondations

**À :** Équipe de réduction des risques et autorités communales\
**De :** Analyste de données\
**Objet :** Matrice des précipitations et de l'exposition aux
inondations -- constats et recommandations

#### Partie 1 -- Analyse

À la suite d'une semaine de fortes précipitations ayant durement touché
six communes côtières du pays, allant de Gonaïves à Jacmel, il est
devenu indispensable d'optimiser l'allocation des ressources de secours
sur le terrain. L'objectif principal de ce rapport est d'identifier les
zones géographiques prioritaires nécessitant une inspection immédiate
des infrastructures de protection, telles que les digues, les ravines et
les abris d'urgence. Cette démarche implique directement l'équipe de
réduction des risques ainsi que les administrations municipales de
chaque commune concernée comme principales parties prenantes de la
sécurité civile.

Lors de l'analyse initiale des relevés météorologiques, un piège majeur
a été détecté sous la forme d'une valeur aberrante de -999.0 mm au jour
5 pour la station de Petit-Goâve. Cette valeur extrême représentait en
réalité un code sentinelle utilisé par la station pour signaler une
panne de capteur ou une absence temporaire de transmission. Si cette
valeur avait été intégrée naïvement dans nos calculs, Petit-Goâve aurait
présenté un cumul de pluie absurde et négatif de -696.0 mm, faussant
ainsi totalement l'évaluation des risques. Pour corriger cette anomalie
sans introduire de biais, nous avons neutralisé ce code en le déclarant
comme une valeur manquante. Afin d'estimer de manière réaliste la
pluviométrie totale sur 7 jours pour Petit-Goâve, le jour manquant a été
comblé en lui attribuant la moyenne des 6 autres jours valides observés
dans cette même commune.

Le tableau A ci-dessous présente la synthèse des observations de
pluviométrie collectées ainsi que le calcul de l'indice d'exposition
pour chaque commune.

##### Tableau A : Synthèse des précipitations, de l'exposition et niveau de priorité

  ----------------------------------------------------------------------------------------------------
  Commune           Jours     Cumul     Cumul     Maximum      Part      Indice         Vérification
                    valides   observé   estimé    journalier   ménages   d'exposition   prioritaire
                              (mm)      sur 7j    (mm)         exposés                  
                                        (mm)                   (%)                      
  ----------------- --------- --------- --------- ------------ --------- -------------- --------------
  **Cabaret**       7         335.0     335.0     110.0        41.0 %    137.4          **Oui**

  **Petit-Goâve**   6         303.0     353.5     124.0        38.0 %    134.3          **Oui**

  **Gonaïves**      7         293.0     293.0     96.0         35.0 %    102.6          Non

  **Léogâne**       7         218.0     218.0     75.0         30.0 %    65.4           Non

  **Saint-Marc**    7         263.0     263.0     88.0         22.0 %    57.9           Non

  **Jacmel**        7         250.0     250.0     81.0         18.0 %    45.0           Non
  ----------------------------------------------------------------------------------------------------

L'indice d'exposition calculé croise la sévérité du climat avec la
vulnérabilité sociale locale. Plus précisément, cet indice multiplie le
cumul de pluie estimé sur 7 jours par la part des ménages de la commune
résidant dans des zones historiquement inondables. Grâce à cette
méthodologie, nous pouvons classer objectivement les communes de la plus
exposée à la moins exposée : Cabaret arrive en tête (indice de 137.4),
suivie de très près par Petit-Goâve (134.3), puis Gonaïves (102.6),
Léogâne (65.4), Saint-Marc (57.9) et enfin Jacmel (45.0).

Pour déterminer quelles zones requièrent des inspections physiques
immédiates, nous avons établi une règle de vérification prioritaire
stricte. Une commune est classée comme hautement prioritaire si son
cumul de pluie observé dépasse le seuil critique de 300 mm sur
l'ensemble de la période, ou si elle a subi un événement de pluie
extrême supérieur à 100 mm en une seule journée. En appliquant ces
critères, Cabaret et Petit-Goâve sont les deux seules municipalités qui
se qualifient pour une intervention d'urgence. Cabaret dépasse en effet
simultanément les deux critères avec un cumul de 335.0 mm et un pic
journalier de 110.0 mm. Petit-Goâve déclenche également cette alerte
avec 303.0 mm accumulés et surtout le record de précipitation maximale
de notre échantillon s'élevant à 124.0 mm en 24 heures.

L'analyse temporelle met par ailleurs en évidence un phénomène
météorologique d'une intensité remarquable au cours du quatrième jour de
la semaine. Le tableau B met en relief la part représentée par cette
seule journée dans le bilan hydrologique global des différentes
localités.

##### Tableau B : Poids relatif des précipitations du Jour 4 par commune

  ------------------------------------------------------------------------
  Commune              Pluie cumulée Jour 4 (mm) Part du Jour 4 dans le
                                                 cumul (%)
  -------------------- ------------------------- -------------------------
  **Petit-Goâve**      124.0                     41 %

  **Léogâne**          75.0                      34 %

  **Saint-Marc**       88.0                      33 %

  **Cabaret**          110.0                     33 %

  **Gonaïves**         96.0                      33 %

  **Jacmel**           81.0                      32 %
  ------------------------------------------------------------------------

Ce quatrième jour a concentré à lui seul plus d'un tiers des
précipitations totales de toute la semaine pour l'ensemble des communes
de la région. À Petit-Goâve, cette concentration atteint un niveau
extrême où une seule journée de tempête a représenté 41 % de l'eau reçue
en sept jours.

Malgré la solidité globale de notre modèle, certaines limites techniques
doivent être gardées à l'esprit lors de la prise de décision. En
particulier, l'estimation linéaire du jour manquant à Petit-Goâve
suppose que la pluie y a été modérée ce jour-là, alors que la réalité
terrain aurait pu présenter une sécheresse ou au contraire une autre
tempête locale. De plus, il convient de souligner que toutes les données
analysées ici sont synthétiques et ont été générées à des fins
d'apprentissage.

#### Partie 2 -- Recommandations

1.  **Déploiement immédiat des inspecteurs de digues à Cabaret et
    Petit-Goâve :** En raison d'un cumul observé dépassant les seuils
    d'alerte (335.0 mm à Cabaret et 303.0 mm à Petit-Goâve), les équipes
    techniques de génie civil doivent être dépêchées en priorité dans
    ces deux communes sous 24 heures pour évaluer la résistance
    structurelle des digues fluviales.
2.  **Sécurisation des zones à fort taux d'exposition résidentielle :**
    À Cabaret, où 41.0 % des ménages habitent en zone inondable, et à
    Petit-Goâve (38.0 % d'exposition), il est crucial de valider la
    viabilité des abris temporaires d'urgence et de préparer des plans
    d'évacuation préventifs ciblés sur ces quartiers hautement
    vulnérables.
3.  **Modernisation et redondance du réseau de stations de mesure :**
    Suite à la perte de données enregistrée au jour 5 à Petit-Goâve
    (mesure absente compensée mathématiquement à 50.5 mm), il est
    recommandé d'équiper la station locale de capteurs redondants et
    d'une batterie de secours afin de garantir des séries de données
    d'urgence complètes sans devoir recourir à des estimations
    statistiques.
