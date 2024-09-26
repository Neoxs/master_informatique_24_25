## Contraintes sur le modèle des tortues (avec collections)

### 1. une tortue mâle ne peut avoir de dates de ponte

```ocl
context Tortue
inv: self.sexe = 'M' implies self.datesPonte->isEmpty()
```

### 2. une tortue habite l’un des lieux de la répartition géographique de son espèce

```ocl
context Tortue
inv: self.espece.repartitionGeographique.lieu->includes(self.lieu)
```

### 3. tout aliment utilisable pour l’élevage en captivité fait partie du régime alimentaire général

```ocl
context EspeceTorue
inv: self.biologie.regimeGeneral->inclduesAll(self.modeElevage.regimeCaptive)

```

#### 3.bis sans inludesAll

```ocl
context EspeceTortue
inv: self.modeElevage.regimeCaptivité->forAll(t: typeAliment | self.biologie.regimeGeneral->includes(t))
```

### 4. écrire la post-condition de l’opération nourriturePossible(t:TypeAliment):boolean de la classe espèceTortue ; t est un un type d’aliment possible s’il fait partie du régime alimentaire général de l’espèce

```ocl
context EspeceTortue::nourriturePossible(t: TypeAliment): Boolean
post: result = self.biologie.regimeGeneral->includes(t)
```
