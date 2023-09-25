
```
from sklearn import tree
import graphviz

clf = tree.DecisionTreeClassifier( max_depth=1)

clf = clf.fit(X, Y)
tree.plot_tree(clf)

dot_data = tree.export_graphviz(clf, out_file=None) 
graph = graphviz.Source(dot_data)
regle = tree.export_text(clf, feature_names= X.columns.tolist() )
print( regle )
print( 'Accuracy :', round(clf.score(X, Y)*100, 2) )
```

Attention les variables explicatives sont de type numérique.
