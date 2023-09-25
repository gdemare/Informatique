Packages : 
```
from sklearn.decomposition import PCA
from matplotlib import pyplot as pl
import numpy as np
import pandas as pd
```

```
normalizeData = StandardScaler().fit_transform(data) #normaliser les données

pca = PCA(n_components=3)
projection = pca.fit_transform(tst)

acp = pd.DataFrame( projection )
varaince_exp = np.round( pca.explained_variance_ratio_/sum(pca.explained_variance_ratio_)*100, 0)
acp.columns  = [ 'axe' + str(i) + '(' + str(j) + ')'  for i, j in zip(acp.columns.values, varaince_exp)]

acp.index = data.index

sns.scatterplot( x = acp.iloc[:, 0], y = acp.iloc[:, 1])
```

## Description de la ACP

* `pca.explained_variance_ratio_` pourcentage de la variance représentée.
