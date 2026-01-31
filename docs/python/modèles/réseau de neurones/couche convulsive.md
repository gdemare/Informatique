## Créer des noyaux particuliers

## Initialiser les poids

`pretrained_base.trainable = False` garder les poids initialisés. Généralement, le choix des poids de départ ont déjà été optimisés.


## Définir les noyaux

( étape non obligatoire) Les noyaux sont sont les extracteurs de caractéristiques.

### Créer un noyau

```
import learntools.computer_vision.visiontools as visiontools
from learntools.computer_vision.visiontools import edge, bottom_sobel, emboss, sharpen
```

| fonction | détection |
|---|---|
| `edge` | bord |
| `bottom_sobel` | |
| `emboss` | | 
| `sharpen` | |

`tf.constant(matrice)` définir un noyau (généralement matrice carrée impaire).

```
# Reformater pour rendre le noyau applicable.
kernel = tf.reshape(kernel, [*kernel.shape, 1, 1])
kernel = tf.cast(kernel, dtype=tf.float32)
```