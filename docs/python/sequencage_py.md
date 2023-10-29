Importer les bibliothèques
```
from Bio import SeqIO
from Bio import pairwise2
```

## Déclaer des séquences 

* `SeqIO.parse('alignement.fasta', "fasta")` alignement du fichier fasta.
* `SeqIO.Seq("sequence")` déclarer une séquence.
* `SeqIO.write(align(ali), output, "fasta")` exporter l'alignement dans un fichier fasta.
* `sequence.complement()` renvoie la séquence complémentaire.
* `sequence.reverse_complement()` renvoie la séquence complémentaire inverse.
* `.translate()` passer d'une séquence nucléotide à la séquence d'acides aminés.

## Alignement des séquences

Bibliothèque `Pairwise` permet d'aligner des séquences deux à deux.

* `AlignIO.read(output_file, "fasta")` importer des fastas d'alignement.
* `pairwise2.align` aligner des séquences. Les éléments sont accessibles en classe (ex : `.id`). L'alignement utilise comme algo :
 * `.globalms(seq1, seq2, 2, -1, -5, -2)` algo globalms.
 * `.globalxx(seq1, seq2)` algo ?
* `AlignIO.write(alignment, "fichier.fasta", "fasta")` exporter l'alignement en fasta.

### Visualiser les séquences

Libary `pymsaviz`

* `mv = MsaViz( fichier, wrap_length=60, show_count=True)`
Paramètre :
* `show_consensus=True` créer un consensus.
* `mv.savefig("api_example01.png")` sauvegarder et afficher l'image dans un fichier.

Ajouter des fichiers :

* `mv.add_markers([30, (40, 50), 55], color="green", marker="+")` ajouter des repères.
* `mv.add_text_annotation((23, 39), "Libellé", text_color="red", range_color="red")` ajouter un région.

#### PubMed


