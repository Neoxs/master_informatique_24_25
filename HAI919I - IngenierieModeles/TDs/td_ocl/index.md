## Contraintes sur le modèle des tortues (avec collections)

### 1.une tortue mâle ne peut avoir de dates de ponte

```ocl
context Tortue
inv: self.sexe = 'M' implies self.datesPonte->isEmpty()
```
