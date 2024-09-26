# TD - Object Constraint Language (OCL) appliqué sur le méta-modèle OCL

## 2. Quelques requêtes sur le Feature Diagram

```ocl
context Classifier
    def staticFeatures(): Set(Feature)
        feature->select(isStatic)
        feature->select(f: Feature | f.isStatic)
        feature->select(f | f.isStatic)
```

```ocl
def abstractBehavioralFeatures(): Set(BehavioralFeature)
    self.feature->select(f:Feature | f.oclIsTypeOf(BehavioralFeature) and f->oclAsType(BehavioralFeature).isAbstract)->oclAsType(Set(BegavioralFeatrue))
```

```ocl
Context Classifier
    inv abstractBehavioralFeatures()->ForAll(abf: BehavioralFeature | obf.method->isEmpty())
```

```ocl
Context BehavioralFeature
    inv isAbstract implies method->isEmpty()
```

### 4.

```ocl
Context Classifier
    def bagStructuralFeatures(): Set(StructuralFeature)
        feature->select(f: Feature | f.oclIsTypeOf(StructuralFeature) and not f.oclAsType(StructuralFeature).isOrdred and not f.oclAsType(StructuralFeature).isUnique)
```

### 5.

```ocl
Context Classifier
    def sortedBehavioralFeature(): OrdredSet(BehavioralFeature)
        feature->select(f: Feature | f.oclIsTypeOf(BehavioralFeature)
        ->sortedBy(oclAsType(BehavioralFeature).ownedParameter->size())
        -> asType(orderedSet(BehavioralFeature)))
```

Ou

```ocl
Context Classifier
    def sortedBehavioralFeature(): OrdredSet(BehavioralFeature)
        feature->select(f: Feature | f.oclIsTypeOf(BehavioralFeature)
        ->sortedBy(oclAsType(BehavioralFeature).ownedParameter->size())
        -> asType(orderedSet(BehavioralFeature)))
```

## 3. Quelques requêtes sur le Classifier Diagram

### 1.

```ocl
Context Classifier
    def parents(): Set(Classifier)
        self.generalization->collect(general)->asSet()
        self.generalization.general->asSet()
```

### 2.

```ocl
Context Classifier
    def allParants(): Set(Classifier)
        parents()->union(parents()->collect(allParents())->flatten())->asSet()
```

### 3.

```ocl
Context Classifier
    def allParants(): Set(Classifier)
        parents()->union(parents()->collect(allParents())->flatten())->asSet()
```

### 4.

```ocl
context Classifier
def: allParentsIncludingSelf(): Set(Classifier) =
    self.allParents()->including(self)

inv noCircularGeneralization:
    not self.allParentsIncludingSelf()->includes(self)
```
