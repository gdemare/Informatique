## Algorithme Largest-Triangle-Three-Buckets (LTTB)

`import lttbc`

* `lttbc.downsample(x_data, data, nb_points)` lisser les données avec l'agorithme LTTBC.

## Fonction d'Allan

## Transformation de Fourrier

### Numpy

* `np.fft.fft(noisy_signal)` transformer les données avec Fourrier.
* `np.fft.fftfreq(signal, d=freq)` déterminer les fréquences élémentaires des signaux périodiques avec d d'acquisition des points.
### Spicy

* `scipy.fft.fft(signal)` transformer les données avec Fourrier.
* `scipy.fft.fftfreq(signal.size, d=tps)` déterminer les fréquences élémentaires des signaux périodiques en fonction du temps d'acquisition entre chaque point.
* `scipy.fft.ifft(fourrier)` transformation inverse de Fourrier.

## Traitement du signal

`scipy.signal`

* `find_peaks(data)` trouver les maximums. Pas mal de paramètres.
* `peak_prominences(data, peaks)` renvoie la valeur des pics.
* `butter()` créer un filtre haute et basse fréquence. 
* `sosfiltfilt(sos, data)` appliquer le filtre.
