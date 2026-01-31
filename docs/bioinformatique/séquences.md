 __trimming__ découper les séquences par exemple, pour retirer les parties non désirées comme les adaptateurs des séquenceurs et les séquences de mauvaise qualité. Paramètres : Longueur de la séquences, un seuil de qualité.
__assembleur__ assembler des séquences. Paramètres : kmers (nombre minimal de bases chevauchantes), longueur minimum des contigs. Utilisé pour le séquençage et la quantification.
__blast__ aligner des séquences sur un génome de référence. Paramètres : seuil  d'identité, couverture.

Logiciels de :

- trimming  : `trim-galore`, `trimmomatic`, `autoadapt` 
- assembleur : `megahit`
- bast : `blastn`
- manipuler les séquences (tri, index) : `samtools`
- recherche de polymorphisme `GATK`
- alignement de séquences de novo `Vsearch`. Il permet de dédupliquer les séquences, estimer l'abondance, et clustering.
- binning regrouper des séquences en fonction de caractéristiques comme les séquences appartenant à la même espèce.
- bowtie2 aligner des séquences sur une bdd.
- prodigal détecter les gènes dans un génome procaryote.
- 4-mer référence à des motifs de 4 nucléotides chevauchant (fenêtre glissante). L'analyse de fait par la comparaison des fréquence de quatre nucléotides de la distribution.
- `metabat`
- `micomplete` détecter les marqueurs de gènes des Bactéries et des Archées. Retourner le poids de la complétion, la contamination.

#### Formats de fichiers

- `sam` et `bam` = format binaire
## Preprocessing

### Trimmomatic

``` 
trimmomatic \
    SE \
    -phred33 \
    fichier.fastq.gz \
    fichier.trim.fastq.gz \ 
    ILLUMINACLIP:adaptors.fa:2:30:10 \
    TRAILING:30 \
    MINLEN:32
```

* `trimmomatic` Le nom de l’outil.
* `SE` si les fichiers sont Single-End (SE) ou Paired-End (PE).
* `-phred33` le décalage du score de qualité (-phred33 ou -phred64).
* `fichier.fastq.gz` Le fichier à nettoyer.
* `fichier.trim.fastq.gz` Le fichier de sortie.
* `ILLUMINACLIP:adaptors.fa:2:30:10` Les paramètres de l’algorithme pour retirer les adapteurs.
* `TRAILING:30` Les paramètres pour l’algorithme de nettoyage de la fin des séquences.
* `MINLEN:32` La taille minimale des séquences à conserver.

Présentation des algorithmes :

* LUMINACLIP: Utilisé pour supprimer les adaptateurs des séquences. Il faut spécifier :
    ome/etudiant11/data/fastq/ERR047167_R1.fastq 
    * le ficher FASTA contenant les séquences d'adaptateurs.
    * le nombre d'erreurs autorisées.
    * la position des séquences d'adaptateurs.

* LEADING: Supprime les bases de faible qualité à l'extrémité 5' (début) de chaque lecture.
* TRAILING: Supprime les bases de faible qualité à l'extrémité 3' (fin) de chaque lecture.
* SLIDINGWINDOW: Effectue un filtrage de qualité glissante sur la séquence. Si une fenêtre de certaines bases a une qualité moyenne en dessous du seuil spécifié, ces bases sont supprimées.
* MINLEN: Élimine les lectures qui deviennent trop courtes après le processus de nettoyage en fonction d'une longueur minimale spécifiée.


* `java -jar trimmomatic-0.39.jar` exécuter trimmomatic.
*`fastqc ficher.fastq` rapport sur les séquences. 

!!! note
    A adatpé en fonction des graphiques obtenues avec fastqc

## Assembleur

### Abyss

Abyss est un logiciel d'assemblage de novo développé pour traiter des données de séquençage à haut débit, en particulier celles provenant de technologies de séquençage Illumina.

#### Séquençage paired-end

```
abyss-pe k=25 n=10 l=25 in='/home/etudiant11/data/fastq/ERR047167_R1_trim.fastq /home/etudiant11/data/fastq/ERR047167_R2_trim.fastq' name=difficile
```

Paramètres :

* `k=25` taille de k-mer à utiliser.
* `l=25` pour permettre     
* `in='fichier_1.fastq.gz fichier_2.fastq.gz'` fichier d'entrée.
* `name=ecoli` nom du préfix pour les fichiers de sortie.
