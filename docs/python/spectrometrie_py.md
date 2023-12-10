## Protéomique

`alphapept` Il est conseillé de l'installer dans un environnement Conda.

### io - importer et exporter les fichiers

`io` est basé sur la library `alphapept.pyrawfilereader`.
  
* `load_thermo_raw(fichier.raw,  )`
* `raw_conversion()` convertir en hdf.

### fasta - les peptides 

* `read_fasta_file(fichier.fasta)` lire un fichier fasta. `list( )` possibilité de le convertir en liste pour plus de lisibilité. Stocker dans un dictinnaire.
* `get_frag_dict()`
* `generate_database()`
* `generate_spectra()` génère le spectre associé.
* `generate_fasta_list(chemin)` exporter en fichier fasta.
* `generate_peptides()`


* `add_to_pept_dict([dic1,dic2])` fusionner des dictionnaires.