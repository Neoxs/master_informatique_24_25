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

