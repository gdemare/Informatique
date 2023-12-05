Importer les bibliothèques
```
from Bio import SeqIO
from Bio import pairwise2
```

## Déclaer des séquences 

* `SeqIO.parse('alignement.fasta', "fasta")` alignement du fichier fasta.
* `Bio.Seq.Seq("sequence")` déclarer une séquence.
* `SeqIO.write(align(ali), "fichier.fasta", "fasta")` exporter la séquence dans un fichier fasta.
* `enumerate(seq)` renvoie la position et la base.

Propriétés des séquences :

* `annotations["organism"]` accéder attribut d'une séquence accessible `sequence.ATTRIBUT`.
* `sequence.complement()` renvoie la séquence complémentaire.
* `sequence.reverse_complement()` renvoie la séquence complémentaire inverse.
* `sequence.transcribe()` transcrire de l'ADN en ARN.
* `sequence.translate()` passer d'une séquence nucléotide à la séquence d'acides aminés.

## Alignement des séquences

Bibliothèque `Pairwise` permet d'aligner des séquences deux à deux.

* `AlignIO.read(output_file, "fasta")` importer des fastas d'alignement.
* `AlignIO.write(alignment, "fichier.fasta", "fasta")` exporter l'alignement en fasta.
* `pairwise2.align` aligner des séquences. Les éléments sont accessibles en classe (ex : `.id`). L'alignement utilise comme algo :

    * `.globalms(seq1, seq2, 2, -1, -5, -2)` algo globalms.
    * `.globalxx(seq1, seq2)` algo ?

### BLAST

`from Bio.Blast import NCBIWWW`
`from Bio.Blast import NCBIXML`

* `NCBIWWW.qblast("blastp", "nr", query_sequence)` nr pour non-redondante
* `NCBIXML.parse(result_handle)` parcourir et analyser un fichier.

### Visualiser les séquences

Libary `pymsaviz`

* `mv = MsaViz( fichier, wrap_length=60, show_count=True)`
Paramètre :

	* `show_consensus=True` créer un consensus.

* `mv.savefig("api_example01.png")` sauvegarder et afficher l'image dans un fichier.

Ajouter des fichiers :

* `mv.add_markers([30, (40, 50), 55], color = "green", marker = "+")` ajouter des repères.
* `mv.add_text_annotation((23, 39), "Libellé", text_color = "red", range_color = "red")` ajouter un région.

#### PubMed


