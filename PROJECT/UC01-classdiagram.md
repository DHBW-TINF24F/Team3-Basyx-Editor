# XML / KBL / VEC Validator
###     ./aas-web-ui/src/utils/XmlValidator.ts

## Class Diagram Xml Validator

```mermaid
%%{init: {'classDiagram': {'nodeSpacing': 100}}}%%
classDiagram

class XmlValidator {
    -file: File | null
    -errorMessage: string
    -resultMessage: string
    -allowedKblRoots: string[]
    -allowedVecRoots: string[]

    -validateWellFormedXML(f: File): Promise~ValidatorResult~
    -validateVecFile(f: File): Promise~boolean~
    -validateKBLFile(f: File): Promise~boolean~
    +uploadHandler(fileInput: any | null): Promise~string~
}
```

## Flowchart XmlValidator
```mermaid
flowchart TD
    A[uploadHandler] --> B{File?}
    B -->|no| C[errorMessage='Keine Datei'<br/>return errorMessage]
    B -->|yes| D{File Extension?}
    D -->|.vec| E[validateVecFile]
    D -->|.kbl| F[validateKBLFile]
    D -->|.xml| G[validateWellFormedXML]
    D -->|other| K
    E --> G
    F --> G
    G --> I{errorMessage ?}
    I -->|message| J[return errorMessage <br>=> no Upload]
    I -->|empty| K[return ' ' => Upload]
```
