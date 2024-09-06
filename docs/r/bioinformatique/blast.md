### Fichiers fasta

`library(seqinr)`

* `read.fasta(file = fichier)` lire un fichier fasta ou fastaq.

## BLAST

`library(rBLAST)`

1. Générer la base pour le blast.
2. Faire un prédict pour blaster les séquences.


* `readDNAStringSet(fic_seq, format='fasta')` importer un fichier fasta.

### BLAST

0. `makeblastdb(fichier, dbtype = "nucl")` créer les fichiers pour créer une bdd blast (génére les fichiers pour.
seq_res <- readDNAStringSet(fic_seq, format='fasta')
1. `db <- blast(fic_ref)` déclarer la bdd blast.
2. `predict(db, seq_res)` blaster les séquences.
