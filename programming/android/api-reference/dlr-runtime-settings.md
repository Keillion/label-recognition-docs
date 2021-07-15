---
layout: default-layout
title: Dynamsoft Label Recognizer Android Class - DLRRuntimeSettings
description: This page shows the DLRRuntimeSettings struct of Dynamsoft Label Recognizer for Android Language.
keywords: DLRRuntimeSettings, struct, android
needAutoGenerateSidebar: true
needGenerateH3Content: true
---


# class com.dynamsoft.dlr.DLRRuntimeSettings
Defines a struct to configure the text recognizer runtime settings. These settings control the text recognition process.
  
  

## Attributes
  
| Attribute | Type |
|---------- | ---- |
| [`maxThreadCount`](#maxthreadcount) | *int* |
| [`characterModelName`](#charactermodelname) | *String* |
| [`referenceRegion`](#referenceregion) | [`DLRReferenceRegion`](dlr-reference-region.md) |
| [`textArea`](#textarea) | [`Quadrilateral`](quadrilateral.md) |
| [`dictionaryPath`](#dictionarypath) | *String* |
| [`dictionaryCorrectionThreshold`](#dictionarycorrectionthreshold) | [`DLRDictionaryCorrectionThreshold`](dlr-dictionary-correction-threshold.md) |
| [`binarizationModes`](#binarizationmodes) | *int\[\]* |
| [`furtherModes`](#furthermodes) | [`DLRFurtherModes`](dlr-further-modes.md)|
| [`lineSpecification`](#linespecification) | [`DLRLineSpecification`](dlr-line-specification.md) |

### maxThreadCount
Sets the number of threads the algorithm will use to recognize label.
```java
int maxThreadCount
```
- **Value range**   
    [1, 4]
      
- **Default value**   
    4
    
- **Remarks**   
    To keep a balance between speed and quality, the library concurrently runs four different threads by default.

### characterModelName
The name of the CharacterModel.
```java
String characterModelName
```


### referenceRegion
Sets the reference region to search for text.
```java
DLRReferenceRegion referenceRegion
```

### textArea
Sets the text area relative to the reference region.
```java
com.dynamsoft.core.Quadrilateral textArea
```

### dictionaryPath
Sets the path of the dictionary file.
```java
String dictionaryPath
```

### dictionaryCorrectionThreshold
Sets the threshold of dictionary error correction.
```java
DLRDictionaryCorrectionThreshold dictionaryCorrectionThreshold
```


### binarizationModes
Sets the mode and priority for binarization.

```java
int[] binarizationModes
```

- **Value range**   
    Each array item can be any one of the [`EnumBinarizationMode`]({{ site.enumerations }}parameter-mode-enums.html#binarizationmode) Enumeration items.
      
- **Default value**   
    `[EnumBinarizationMode.BM_LOCAL_BLOCK, EnumBinarizationMode.BM_SKIP, EnumBinarizationMode.BM_SKIP, EnumBinarizationMode.BM_SKIP, EnumBinarizationMode.BM_SKIP, EnumBinarizationMode.BM_SKIP, EnumBinarizationMode.BM_SKIP, EnumBinarizationMode.BM_SKIP]`
    
- **Remarks**   
    The array index represents the priority of the item. The smaller index is, the higher priority is.


### furtherModes
Sets further modes.

```java
DLRFurtherModes furtherModes
```

- **See also**  
    [`DLRFurtherModes`](dlr-further-modes.md)


### lineSpecification
Sets line specification.

```java
DLRLineSpecification lineSpecification
```

- **See also**  
    [`DLRLineSpecification`](dlr-line-specification.md)