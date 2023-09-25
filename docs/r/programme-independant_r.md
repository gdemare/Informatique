## Créer un programme R indépendant

1. Télécharger une version R portable.
2. Installer les library dans le dossier R portable : `.libPaths("R-Portable/App/R-Portable/library")` 
3. créer un fichier exécutable windows `run.bat`.

``` 
SET ROPTS=--no-save --no-environ --no-init-file --no-restore --no-Rconsole
R-Portable\App\R-Portable\bin\Rscript.exe %ROPTS% script.R
``` 
