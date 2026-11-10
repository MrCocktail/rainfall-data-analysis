**DEVOIR #3**

**MODULE 2 -- SCÉNARIO 5**

Devoir d\'analyse -- Matrice des précipitations et de l\'exposition aux
inondations

*Logique de programmation, NumPy et simulation • Travail individuel*

  -----------------------------------------------------------------------
  **Informations**       
  ---------------------- ------------------------------------------------
  Nom et prénom          Bruno Jean David

  Date                   9 novembre 2026

  Module                 2

  Scénario               5 -- Matrice des précipitations et de
                         l\'exposition aux inondations \[CAS PRINCIPAL\]

  Date de remise         9 novembre 2026
  -----------------------------------------------------------------------

# 1. Contexte du devoir

Une semaine de fortes pluies a touché six communes côtières, de Gonaïves
à Jacmel. Des stations météorologiques ont enregistré la pluie tombée
chaque jour, et une enquête indique quelle part des ménages vit en zone
inondable. L\'équipe de réduction des risques ne peut pas envoyer
d\'inspecteurs partout en même temps : elle doit choisir où vérifier en
premier les digues, les ravines et les abris.

Vous êtes data scientist. En classe, vous avez construit le tableau
NumPy des pluies (6 communes × 7 jours) et remplacé la valeur sentinelle
-999 par NaN : ce code se trouve dans le notebook fourni. Dans ce
devoir, vous terminez le calcul : cumuls, maximum journalier, indice
d\'exposition et liste des communes à vérifier en priorité. Vous rédigez
ensuite un rapport pour l\'équipe de réduction des risques.

**Données :** S05_pluie_7jours.csv (données synthétiques, disponibles
sur Moodle). Unités : pluie en millimètres (mm) ; part des ménages en
zone inondable entre 0 et 1.

# 2. Méthodologie obligatoire

1.  Télécharger le notebook et le fichier CSV sur Moodle (partie 3).

2.  Ouvrir le notebook, aller au Scénario 5 et exécuter les cellules
    déjà faites en classe. Sans Colab, suivre la partie 4.

3.  Écrire vous-même le code qui complète l\'analyse (partie 6) et
    produit les tableaux (partie 5).

4.  Vérifier vos résultats avec vos deux contrôles assert.

5.  Rédiger le rapport destiné à l\'équipe de réduction des risques
    (partie 7).

6.  Redémarrer le noyau et exécuter toutes les cellules dans l\'ordre
    avant la remise.

# 3. Fichiers fournis sur Moodle

Deux fichiers sont fournis et disponibles sur la plateforme Moodle du
cours :

- **Le notebook du Module 2**
  (Module_02_Logique_de_Programmation_et_NumPy_FR.ipynb) : il contient
  le scénario 5 et le code déjà fait en classe (lecture des données,
  tableau NumPy des pluies 6 × 7, remplacement de la valeur sentinelle
  -999 par NaN, contrôle 1). Vous écrivez votre code à la suite, dans ce
  notebook.

- **Le fichier de données** S05_pluie_7jours.csv : une ligne par
  commune, une colonne par jour (j1 à j7, pluie en mm) et la colonne
  part_menages_zone_inondable (entre 0 et 1).

Téléchargez les deux fichiers depuis Moodle. Dans Colab, ouvrez le
notebook (**Fichier → Importer un notebook**), puis téléversez le
fichier CSV quand la cellule files.upload() le demande.

**Attention :** le code écrit en classe à la fin du scénario 5 contient
des erreurs. Vérifiez chaque résultat avant de continuer (par exemple,
un nombre de jours valides doit être un entier entre 0 et 7, et une
colonne doit être appelée par son nom exact).

# 4. Travailler sans Colab (VS Code ou PyCharm)

Si vous ne pouvez pas utiliser Google Colab, faites le devoir sur votre
ordinateur avec VS Code ou PyCharm.

**Option A -- garder le notebook (recommandé)**

1.  Dans Colab : **Fichier → Télécharger → Télécharger le fichier
    .ipynb**.

2.  Installer Python 3, puis dans un terminal : pip install pandas numpy
    jupyter.

3.  VS Code : installer les extensions **Python** et **Jupyter**, puis
    ouvrir le fichier .ipynb. PyCharm : ouvrir directement le fichier
    .ipynb.

4.  Placer S05_pluie_7jours.csv dans le même dossier que le notebook.

**Option B -- convertir le notebook en fichier .py**

1.  Dans Colab : **Fichier → Télécharger → Télécharger le fichier .py**.
    Ou, si Jupyter est installé : jupyter nbconvert \--to script
    nom_du_notebook.ipynb.

2.  Installer les bibliothèques : pip install pandas numpy.

3.  Placer S05_pluie_7jours.csv dans le même dossier que le fichier .py,
    puis exécuter : python nom_du_fichier.py (ou bouton ▶ Run).

**Modifications obligatoires hors de Colab :**

- Supprimer les lignes from google.colab import files et uploaded =
  files.upload(). La ligne pd.read_csv(\"S05_pluie_7jours.csv\")
  fonctionne telle quelle si le fichier est dans le même dossier.

- Dans un fichier .py (option B) : remplacer display(\...) par
  print(\...).

# 5. Tableaux à produire (10 points)

**Tableau A -- Table finale** resultat : une ligne par commune, triée de
l\'indice d\'exposition le plus élevé au plus faible.

  -------------------------------------------------------------------------------
  **Colonne**                **Contenu (unité)**
  -------------------------- ----------------------------------------------------
  commune                    Nom de la commune

  jours_valides              Nombre de jours avec une mesure valide (jours,
                             entier de 0 à 7)

  cumul_observe_mm           Pluie totale mesurée, en ignorant les valeurs
                             manquantes (mm)

  cumul_estime_7j_mm         Pluie estimée sur 7 jours, arrondie à 1 décimale
                             (mm)

  max_journalier_mm          Pluie maximale tombée en une seule journée (mm)

  indice_exposition          Cumul estimé sur 7 jours × part des ménages en zone
                             inondable, arrondi à 1 décimale

  verification_prioritaire   True si cumul estimé \> 300 mm OU maximum journalier
                             \> 100 mm, sinon False
  -------------------------------------------------------------------------------

*Recopiez votre table ci-dessous, ou insérez une capture d\'écran de sa
sortie.*

![](media/image1.png){width="6.5in" height="1.5263888888888888in"}

**Tableau B -- Part du jour 4 dans le cumul de chaque commune (%)**

  -----------------------------------------------------------------------
  **commune**                                 **part_jour_4 (%)**
  ----------------------------------- -----------------------------------
  Gonaïves                                            33%

  Saint-Marc                                          33%

  Cabaret                                             33%

  Léogâne                                             34%

  Petit-Goâve                                         41%

  Jacmel                                              32%
  -----------------------------------------------------------------------

# 6. Code qui complète l\'analyse (30 points)

**Consigne :** dans le notebook, à la suite du code fait en classe,
écrivez le code qui réalise les étapes suivantes. Chaque étape
correspond à un commentaire de votre code.

\# Nombre de jours avec une mesure valide, par commune

\# Cumul observé en ignorant les NaN

\# Cumul estimé sur 7 jours (hypothèse : jour manquant = moyenne des
autres)

\# Pluie maximale d\'une seule journée, par commune

\# Part des ménages vivant en zone inondable (entre 0 et 1)

\# Indice d\'exposition = pluie estimée (mm) × part des ménages exposés

\# Broadcasting : diviser chaque ligne (6 × 7) par son cumul en colonne
(6 × 1)

\# Part du 4e jour (indice 3) dans le cumul de chaque commune, en %

\# Contrôle 2 : recalcul à la main du cumul de Gonaïves

\# Assembler la table finale à partir des tableaux calculés (indice
arrondi)

\# Règle : vérification prioritaire si \> 300 mm OU \> 100 mm/j

\# Trier de l\'indice le plus élevé au plus faible et renuméroter

\# Afficher la table finale

------------------------------------------------------------------------

**Utilisez obligatoirement :** l\'indice 3 pour le jour 4, .index() pour
retrouver Gonaïves dans communes, et .round() pour arrondir (tableau B :
0 décimale ; cumul estimé et indice d\'exposition : 1 décimale).

**Commentez chaque ligne de votre code.**

**Votre code (ou capture d\'écran des cellules et de leur sortie) :**

+-----------------------------------------------------------------------+
| \# Nombre de jours avec une mesure valide, par commune                |
|                                                                       |
| nb_jours_valides = (\~np.isnan(pluie)).sum(axis=1)                    |
|                                                                       |
| \# Cumul observé en ignorant les NaN                                  |
|                                                                       |
| cumul_obs = np.nansum(pluie, axis=1)                                  |
|                                                                       |
| \# Cumul estimé sur 7 jours (hypothèse : jour manquant = moyenne des  |
| autres)                                                               |
|                                                                       |
| cumul_est = (cumul_obs / nb_jours_valides) \* 7                       |
|                                                                       |
| \# Pluie maximale d\'une seule journée, par commune                   |
|                                                                       |
| max_jour = np.nanmax(pluie, axis=1)                                   |
|                                                                       |
| \# Part des ménages vivant en zone inondable (entre 0 et 1)           |
|                                                                       |
| part_menages_inondable =                                              |
| pluie_df\[\"part_menages_zone_inondable\"\].to_numpy()                |
|                                                                       |
| \# Indice d\'exposition = pluie estimée (mm) × part des ménages       |
| exposés                                                               |
|                                                                       |
| ind_exposition = cumul_est \* part_menages_inondable                  |
|                                                                       |
|                                                                       |
|                                                                       |
| \# Broadcasting : diviser chaque ligne (6 × 7) par son cumul en       |
| colonne (6 × 1)                                                       |
|                                                                       |
| part_par_jour_relative = pluie / cumul_obs\[:, np.newaxis\]           |
|                                                                       |
| \# Part du 4e jour (indice 3) dans le cumul de chaque commune, en %   |
|                                                                       |
| part_jour_4_pct = part_par_jour_relative\[:, 3\] \* 100               |
|                                                                       |
|                                                                       |
|                                                                       |
| \# Contrôle 2 : recalcul à la main du cumul de Gonaïves               |
|                                                                       |
| idx_gonaives = list(communes).index(\"Gonaïves\")                     |
|                                                                       |
| cumul_gonaives_main = np.nansum(pluie\[idx_gonaives\])                |
|                                                                       |
| assert np.isclose(cumul_gonaives_main, 293.0), f\"Erreur contrôle     |
| cumul : {cumul_gonaives_main} au lieu de 293.0\"                      |
|                                                                       |
|                                                                       |
|                                                                       |
| \# Assembler la table finale à partir des tableaux calculés (indice   |
| arrondi)                                                              |
|                                                                       |
| table_finale = pd.DataFrame({                                         |
|                                                                       |
|     \"commune\": communes,                                            |
|                                                                       |
|     \"jours_valides\": nb_jours_valides,                              |
|                                                                       |
|     \"cumul_observe_mm\": cumul_obs,                                  |
|                                                                       |
|     \"cumul_estime_7j_mm\": cumul_est.round(1),                       |
|                                                                       |
|     \"max_journalier_mm\": max_jour,                                  |
|                                                                       |
|     \"indice_exposition\": ind_exposition.round(1),                   |
|                                                                       |
|     \"part_jour_4_pct\": part_jour_4_pct.round(0).astype(int)         |
|                                                                       |
| })                                                                    |
|                                                                       |
| \# Règle : vérification prioritaire si \> 300 mm OU \> 100 mm/j       |
|                                                                       |
| table_finale\[\"verification_prioritaire\"\] =                        |
| (table_finale\[\"cumul_observe_mm\"\] \> 300) \|                      |
| (table_finale\[\"max_journalier_mm\"\] \> 100)                        |
|                                                                       |
| \# Trier de l\'indice le plus élevé au plus faible et renuméroter     |
|                                                                       |
| table_finale = table_finale.sort_values(by=\"indice_exposition\",     |
| ascending=False).reset_index(drop=True)                               |
|                                                                       |
| \# Afficher la table finale                                           |
|                                                                       |
| display(table_finale)                                                 |
|                                                                       |
| ![](media/image2.png){width="6.5in" height="1.288888888888889in"}     |
+-----------------------------------------------------------------------+

# 7. Rapport à l\'équipe de réduction des risques (60 points)

Rédigez un rapport d\'au moins **20 phrases**, accompagné des tableaux A
et B et suivi d\'une section **Recommandations**. Le rapport s\'adresse
à des personnes qui n\'ont pas besoin de connaître Python : expliquez ce
que les résultats signifient pour la décision, pas comment le programme
fonctionne.

**À :** Équipe de réduction des risques et autorités communales

**Objet :** Matrice des précipitations et de l\'exposition aux
inondations -- constats et recommandations

**Partie 1 -- Analyse (au moins 20 phrases). Le texte doit :**

- présenter le contexte, l\'objectif et les parties prenantes ;

- expliquer le piège des données (la valeur -999) et comment il a été
  traité ;

- intégrer les tableaux A et B, chacun avec un titre, et les commenter ;

- présenter des résultats chiffrés avec leur unité (mm, jours, %) ;

- expliquer ce que mesure l\'indice d\'exposition et classer les
  communes ;

- identifier les communes à vérifier en priorité et expliquer la règle
  utilisée (\> 300 mm ou \> 100 mm en un jour) ;

- commenter le poids du jour 4 dans la pluie de la semaine ;

- mentionner au moins une limite (par exemple l\'estimation du jour
  manquant) ;

- préciser que les données sont synthétiques.

**Partie 2 -- Recommandations.** Après l\'analyse, proposez au moins 3
recommandations concrètes et priorisées (où envoyer les inspecteurs en
premier, quoi vérifier, comment améliorer les données des stations...).
Chaque recommandation doit s\'appuyer sur un résultat chiffré du
rapport.

Les tableaux et les recommandations ne comptent pas dans les 20 phrases.

# 8. Éléments à remettre

- Les tableaux A et B.

- Le code commenté qui complète l\'analyse (recopié ou en capture
  d\'écran), avec sa sortie.

- Le rapport : au moins 20 phrases + tableaux A et B + recommandations.

- Le notebook fourni (ou le fichier .py), complété et exécuté du début à
  la fin.

# 9. Vérification avant remise

☐ Ma table finale contient les 7 colonnes demandées et est triée par
indice décroissant.

☐ Les nombres de jours valides sont des entiers entre 0 et 7.

☐ J\'ai utilisé l\'indice 3 pour le jour 4, .index() pour Gonaïves et
.round() pour arrondir.

☐ Mes deux contrôles assert passent, et chaque ligne de mon code est
commentée.

☐ Mon rapport contient au moins 20 phrases, les tableaux A et B, et au
moins 3 recommandations.

☐ Mon rapport présente des résultats chiffrés avec leurs unités.

☐ J\'ai exécuté tout le code dans l\'ordre avant la remise.

# 10. Barème

  -------------------------------------------------------------------------
  **Critère**      **Détail**                                   **Points**
  ---------------- ------------------------------------------- ------------
  Tableaux         Tableaux A et B complets, colonnes               10
                   correctes, valeurs exactes, tri correct     

  Code             Calculs NumPy corrects (nansum, nanmax,          30
                   broadcasting), indice 3, .index(),          
                   .round(), contrôle 2, chaque ligne          
                   commentée                                   

  Rapport          Au moins 20 phrases, tableaux titrés et          60
                   commentés, constats chiffrés, limite, au    
                   moins 3 recommandations fondées sur les     
                   résultats                                   

  **Total**                                                      **100**
  -------------------------------------------------------------------------
