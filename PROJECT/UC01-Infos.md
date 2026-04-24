# XML / KBL / VEC Validator

### Programmer: Martin Böhm

## Upload Handler

- checks XML-plausibility if file ends with .VEC, .KBL, .XML
- checks separate root elements for .KBL, .VEC
- checks IODD plausibilty, if .XML-file is IODD-file

### Source Code

- ./aas-web-ui/src/utils/XmlValidator.ts

### Class Diagram Xml Validator

```mermaid
%%{init: {'classDiagram': {'nodeSpacing': 100}}}%%
classDiagram

class XmlValidator {
    -file: File | null
    -errorMessage: string
    -resultMessage: string
    -allowedKblRoots: string[]
    -allowedVecRoots: string[]
    -ioddNamespace: string

    -validateWellFormedXML(f: File): Promise~ValidatorResult~
    -validateVecFile(f: File): Promise~boolean~
    -validateKBLFile(f: File): Promise~boolean~
    -validateXmlFile(f: File): Promise~boolean~

    -hasElement(doc: Document, tagName: string): boolean
    -getFirstElement(doc: Document, tagName: string): Element | null
    -hasDirectChildElement(parent: Element | null, tagName: string): boolean

    -isIoddDoc(doc: Document): boolean
    -validateIoddCore(doc: Document): boolean
    -hasDeviceNameOrVariantProductName(doc: Document): boolean
    -hasPrimaryLanguageInExternalTextCollection(doc: Document): boolean

    +uploadHandler(fileInput: any | null): Promise~string~
}
```

## Flowchart XmlValidator

```mermaid
flowchart TD
    A[uploadHandler] --> D{File Extension?}

    D -->|other| K[Upload other]

    D -->|.kbl| K1[validateWellFormedXML]
    K1 --> K2{errorMessage?}
    K2 -->|error| C1[No Upload KBL]
    K2 -->|empty| K3[validateKBLFile]
    K3 -->|error| C1
    K3 -->|ok| U1[Upload KBL]

    D -->|.vec| V1[validateWellFormedXML]
    V1 --> V2{errorMessage?}
    V2 -->|error| C2[No Upload VEC]
    V2 -->|empty| V3[validateVecFile]
    V3 -->|error| C2
    V3 -->|ok| U2[Upload VEC]

    D -->|.xml| X1[validateWellFormedXML]
    X1 --> X2{errorMessage?}
    X2 -->|error| C3[No Upload XML]
    X2 -->|empty| X3[validateXmlFile]
    X3 -->|error| C3
    X3 -->|ok| L{is IODD XML?}
    L -->|no| U3[Upload XML]
    L -->|yes| N[validateIoddCore]
    N -->|error| C3
    N -->|ok| U4[Upload XML with IODD]
```

## MimeType Expansion for KBL/VEC

MIME type settings were expanded to include media types with pending IANA registration requests (as of April 2026).

### Source Code:

- .\aas-web-ui\src\composables\AAS\SubmodelElements\File.ts
- .\aas-web-ui\src\components\EditorComponents\InputTypes\FileInput.vue
