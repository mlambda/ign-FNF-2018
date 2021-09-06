Données sous licence etatlab : https://www.etalab.gouv.fr/licence-ouverte-open-licence

Données obtenues auprès de l'IGN (https://www.ign.fr/) le 01/09/2021

dataset123_v1_512pix :

- 123 zones de 512m par 512m annotées avec une nomenclature (pniv3la) à 6 classes (1:NonForet, 2:SolMineral,3:LandeLigneuse, 4:FormationHerbacee, 5:Feuillus, 6:Coniferes)
- Le jeu de données donne 1968 vignettes de 512 pixel x 512 pixel (1 pixel = 25cm sur le terrain). Par facilité ont été saisies 123 zones de 16 vignettes voisines (exemple dalles_512m_11190_4_4_observation_thr.tif concerne la zone de 512m avec identifiant 11190) donc pour des questions d'indépendances spatiales il vaut mieux que toutes les vignettes d'une zone aillent dans le même ensemble train/validation/test.
- Deux formats d'annotations avec le numéro du label pour annotation (_annotation_pniv3la.tif) ou sous forme one-hot encoding (_annotation_nch_pniv3la.tif)
- Dans les observations il y a 5 canaux (infrarouge, rouge, vert, bleu, hauteur)
- dans nos expérimentations la classes NonForêt n'a pas été apprise 'class weight = 0) les modèles s'appliquant uniquemenr aux zones naturelles et forestières.


dataset_FNF_54-57 :

20 zones de 5km x 5km avec une nomenclature à 2 classes 0:Non Forêt et 1:Forêt
- Cette fois ci le modèle n'est pas spécifique au contexte Foret, on cherche justement à produire un masque Forêt à l'intérieur duquel on va appliquer le modèle issu du premier dataset.
- Attention la classe Forêt ce n'est pas "arbres" c'est une classe avec un certain de degré de généralisation dans la définition Forêt = "surfaces de végétation de plus de 5000 m2, d'une largeur minimum de 20m, avec un taux de couvert de végétation de 10%, dont l'utilisation du sol n'est pas agricole.  " (mais en segmentation sémantique on l'apprend vraiment bien dès que le receptive field est suffisant)
- Le jeu de données donne 1620 vignettes de 1048 pixel x 1048 pixel (1 pixel = 50cm sur le terrain).
- En observation il n'y a que 3 canaux (infrarouge, rouge, vert)
- Et en magasin je n'avais que les données annotées formatées en one-hot encoding. mais le deuxième canal du one-hot encong = le label (0 ou 1)
- En plus j'ai mis deux versions du dataset_FNF_54-57 : Annotations et images de 2009 et Annotations et images de 2018.


