# Pràctica Kaggle APC UAB 2022-23

### Nom: Alexandre Galvany Pardo

### NIU: 1566586

### DATASET: Bike Sharing London

### URL: [kaggle](https://www.kaggle.com/datasets/hmavrodiev/london-bike-sharing-dataset)

# Cas Kaggle

## Introducció al Dataset

En el nostre cas tenim un dataset format per 10 atributs i un total de 17.414 files amb dades relacionades amb el lloguer de bicicletes que cada vegada esta sent més popular a les grans ciutats per tal de reduir el tràfic i reduir els nivells de contaminació que produeixen el cotxes dins del context en el que ens trobem de l’escalfament global. En aquest cas en concret, les dades de lloguer de bicicletes són de la ciutat de Londres entre el 2015-2017.

Referent a la base de dades en si es poden extreure tot tipus de dades a part de les de la temperatura, l’estació del any o la humitat.
Aquestes són els atributs més interessants:

- **is_weekend**: Si el lloguer de les bicicletes es feia al cap de setmana o durant la setmana.
- **cnt**: Nombre total de lloguer de bicicletes.

L’atribut que estudiarem en profunditat serà el cnt. Aquest atribut ens ajudarà a predir respecte els altres com poden ser el temps, l’estació del any o la temperatura quina és la demanda de bicicletes que podem tenir per aquell dia amb aquells atributs en concret.

## Objectius del Dataset

Quan hem seleccionat aquest dataset ha estat per tal de poder fer prediccions que serveixin al ajuntament de Londres per regular la disponibilitat de les bicicletes segons del dia de la setmana o bé del temps.

També pot servir per saber en quins dies hi ha menys demanda i així poder fer accions de manteniment tant a les estacions de bicicletes com de les bicicletes en si.

## Anàlisi Preliminar del Dataset

La nostre base de dades consta d’un total de 9 atributs:

- **timestamp**: Data i hora de quan es va fer la mostra
- **cnt**: Nombre total de lloguers nous de les bicicletes.
- **t1**: Temperatura en graus Celsius
- **t2**: Sensació tèrmica de en graus Celsius.
- **hum**: Humitat en %.
- **wind_speed**: Velocitat del vent en km/h.
- **weather_code**: Codi del temps on cadascun dels números representen un estat del temps.
  - 1 = Clar; majoritàriament clar, però tenen alguns valors amb boira/Boira/Taques de boira/ Boira a les proximitats.
  - 2 = Núvols dispersos / Pocs núvols.
  - 3 = Núvols trencats.
     4 = Ennuvolat.
  - 7 = Pluja / Plugim / Pluja lleugera.
  - 10 = Pluja amb tempesta elèctrica.
  - 26 = Nevada.
  - 94 = Boira congelant.
- **is_holiday**: Booleà que indica si el dia és festa o no quan es fa el lloguer.
- **is_weekend**: Booleà que indica si el dia és cap de setmana o no quan es fa el lloguer.
- **season**: Estacions del any per codis.
  - 0 = Primavera.
  - 1 = Estiu.
  - 2 = Tardor.
  - 3 = Hivern.

## Experiments

Durant aquesta pràctica hem aplicat la regressió lineal de les dades on el nostre atrbut objectiu era el nombre de bicicletes llogades, 'cnt'.
Hem aplicat les regressions no per a tots els atributs del dataset sino per aquells que tenen una major correlació respecte el nostre atribut objectiu.
Un cop hem fet el mapa de calor de correlació hem trobat que els atributs amb una major correlació són:

- **wind_speed**
- **t1**
- **t2**

Al fer les regressions lineals hem calculat quin es MSE i el r2 Score de cadascún dels atributs anteriors respecte al 'cnt'.

- **wind_speed**
  - MSE: 1062532.17
  - R2_score: 0.15
- **t1**
  - MSE: 1042414.61
  - R2_score: 0.13
- **t2**
  - MSE: 936361.51
  - R2_score: 0.20

Com veiem cap dels atributs acaba de tenir una correlació alta amb el nostre atribut objectiu, tot i que és la més alta dins dels diferents atributs.

## Models

També he volgut aplicar diferents models per tal de veure si es pot fer una classificació dels nostres atributs i trobar quins son els hiperparàmetres.
Per fer això s'aplicaràn 4 models diferents:

- KNN
- SVM
- Regressió Logística
- Decision Tree

Un cop aplicats els models tenim els següents hiperparàmetres segons el model:

- KNN:
  - {'metric': 'minkowski', 'n_neighbors': 11, 'weights': 'uniform'}
- SVM:
  - {'kernel': 'rbf'}
- Regressió Logística:
  - {'C': 100}
- Decision Tree
  - {'criterion': 'gini', 'max_depth': 3, 'min_samples_leaf': 5}

Al aplicar aquests models hem vist que el score que ens dona en tots els casos es molt baix i per tant podem concluir que les dades no es poden adaptar a cap model del classificació.

## Conclusions Finals

Un cop hem aplicat els diferents models de classificació i les regressions podem concloure que tot i que els atributs amb més correlació respecte el nombre de lloguer de bicicletes són els de temperatura, sensació tèrmica i velocitat del vent no podem dir que afecten directament al nostre atribut objectiu.

## Idees per Treballar en un Futur

En un futur es podria treballar més a fons amb altres metodes com podria ser el descencs de gradient per acabar de veure quins serien els atributs que més estarien relacionats amb el lloguer de bicicletes de Londres.
