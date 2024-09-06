
* [PyOpenMS](https://pyopenms.readthedocs.io/en/latest/introduction.html) fonction pour la spectrométrie de masse.
* [DeepNovo v2](https://github.com/volpato30/DeepNovoV2) séquencage de novo de protéines.
* pour la protéomique :

  * [ms proteomics tools](http://msproteomicstools.roestlab.org)
  * [AlphaPept](https://mannlabs.github.io/alphapept/)

### AlphaPept

!!! note
  Il est conseillé d'installer ces packages dans des environnements pandas.
  
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
