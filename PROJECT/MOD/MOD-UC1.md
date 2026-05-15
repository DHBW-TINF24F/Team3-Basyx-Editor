# Module Documentation: File Import and Validation Subsystem

## 1. Overview

The `XmlValidator.ts` module provides validation logic for XML-based file uploads as described in [SAS 7.1](../TINF24F_3_SAS.md) and in the [BaSyx WebUI issue](https://github.com/eclipse-basyx/basyx-aas-web-ui/issues/1179).

It validates the following file formats in particular:

- KBL
- VEC
- generic XML
- IODD XML

The validation checks file extensions, XML well-formedness, XML headers, format-dependent root elements, and, for IODD files, additional mandatory core structures.

---

## 2. Purpose

The module is intended to validate uploaded XML-based files before further processing.

Its objective is to detect malformed or technically unsuitable files at an early stage and return a comprehensible error message to the calling components.

Core functions:

- Validation of uploaded files
- Routing based on file extension
- XML header validation
- XML well-formedness validation
- Validation of allowed root elements for KBL and VEC
- Detection of IODD documents
- Validation of mandatory IODD core elements
- Return of an error message for UI components

---

## 3. Responsibilities

The module is responsible for:

| Area | Description |
|---|---|
| Upload validation | Validation of a provided `File` object |
| Format routing | Selection of the appropriate validation logic based on the file extension |
| XML base validation | Validation of header, syntax, and parser errors |
| KBL validation | Validation of allowed root elements for `.kbl` files |
| VEC validation | Validation of allowed root elements for `.vec` files |
| XML/IODD validation | Acceptance of generic XML files and additional validation for IODD |
| IODD mandatory-element validation | Verification that mandatory IODD structures are present |
| Error messages | Provision of specific error messages for calling components |

### Mandatory IODD Elements

For detected IODD documents, the validator checks whether the following mandatory elements or structures are present:

| Element / Structure | Requirement |
|---|---|
| `DeviceIdentity` | Must be present |
| `DeviceFunction` | Must be present |
| `DeviceIdentity/DeviceName` or `DeviceVariant/ProductName` | At least one of these naming structures must be present |
| `ExternalTextCollection/PrimaryLanguage` | Must be present if `ExternalTextCollection` exists |

The module is not primarily responsible for:

| Non-responsibility | Reason |
|---|---|
| Complete technical KBL/VEC validation | It only checks basic structural and root-element rules |
| Processing or extraction of XML data | The module validates only; it does not transform data |
| File persistence | Storage is handled outside the validator |
| UI rendering of errors | Error texts are returned but not displayed by the module itself |
| Collection of all validation errors | Validation stops at the first detected error |

---

## 4. Public API

### `uploadHandler(fileInput: File | null): Promise<string>`

Central entry point for validating uploaded files.

#### Parameters

| Name | Type | Required | Description |
|---|---|---:|---|
| `fileInput` | `File \| null` | yes | File object to be validated |

#### Return Value

| Return value | Meaning |
|---|---|
| `""` | Validation successful or no validation required |
| `string` | Error message if validation failed |

#### Behavior

The method determines which specific validation function is used based on the file extension.

| File extension | Validation function |
|---|---|
| `.vec` | `validateVecFile()` |
| `.kbl` | `validateKBLFile()` |
| `.xml` | `validateXmlFile()` |
| other | no specific validation; returns an empty error string |

#### Example

```typescript
const validationError = await uploadHandler(file)

if (validationError !== '') {
  console.error('Validation failed:', validationError)
}
```

---

## 5. Core Validation Functions

### 5.1 `validateWellFormedXML(f: File): Promise<ValidatorResult>`

Base step for all XML-based validations.

#### Purpose

Checks whether a file can be read and parsed as XML.

#### Checks

| Check | Description |
|---|---|
| XML header | The file must contain an XML declaration with `<?xml` |
| XML syntax | The file is parsed with `DOMParser` |
| Parser errors | `parsererror` elements are detected |

#### Return Value

| Return value | Meaning |
|---|---|
| `{ ok: true, doc: Document }` | XML is well-formed |
| `{ ok: false, doc: null }` | XML is malformed or could not be parsed |

#### Possible Error Messages

| Error message | Cause |
|---|---|
| `XML header is missing.` | No XML declaration is present |
| `XML is not well-formed.` | Parser error detected |
| `Error while parsing the XML file.` | Exception during parsing |

---

### 5.2 `validateVecFile(f: File): Promise<boolean>`

Validates `.vec` files.

#### Checks

| Check | Description |
|---|---|
| File extension | The file must end with `.vec` |
| XML well-formedness | Checked via `validateWellFormedXML()` |
| Root element | The root element must match an allowed VEC root |

#### Allowed Root Elements

The check is case-insensitive.

| Root element |
|---|
| `VecContent` |
| `VecContentV2` |
| `VecContent_Base` |

#### Possible Error Messages

| Error message | Cause |
|---|---|
| `Only .vec files are allowed.` | The file has an invalid extension |
| `No root element found.` | No root element was found |
| `${localName} is not a valid root element for .vec files.` | The root element is not allowed for VEC |

---

### 5.3 `validateKBLFile(f: File): Promise<boolean>`

Validates `.kbl` files.

#### Checks

| Check | Description |
|---|---|
| File extension | The file must end with `.kbl` |
| XML well-formedness | Checked via `validateWellFormedXML()` |
| Root element | The root element must match an allowed KBL root |

#### Allowed Root Elements

The check is case-insensitive.

| Root element |
|---|
| `KBL_container` |
| `KBLContainer` |
| `KBL_Container` |
| `KBLContainer_Old` |

#### Possible Error Messages

| Error message | Cause |
|---|---|
| `Only .kbl files are allowed.` | The file has an invalid extension |
| `No root element found.` | No root element was found |
| `${localName} is not a valid root element for .kbl files.` | The root element is not allowed for KBL |

---

### 5.4 `validateXmlFile(f: File): Promise<boolean>`

Validates `.xml` files.

#### Flow

```txt
1. Check XML well-formedness.
2. Detect the IODD namespace.
3. If IODD is detected:
   3.1 Validate the IODD core structure.
4. If no IODD is detected:
   4.1 Accept the file as generic XML.
```

#### IODD Namespace

```txt
http://www.io-link.com/IODD/2010/10
```

---

### 5.5 `validateIoddCore(doc: Document): boolean`

Validates central structures of an IODD document.

#### Mandatory Structures

| Element / Structure | Description |
|---|---|
| `DeviceIdentity` | Container for device metadata |
| `DeviceFunction` | Functional specification |
| `DeviceIdentity/DeviceName` or `DeviceVariant/ProductName` | Device name or fallback product name |
| `ExternalTextCollection/PrimaryLanguage` | Mandatory if `ExternalTextCollection` exists |

#### Possible Error Messages

| Error message | Cause |
|---|---|
| `IODD element 'DeviceIdentity' is missing.` | `DeviceIdentity` is missing |
| `IODD element 'DeviceFunction' is missing.` | `DeviceFunction` is missing |
| `IODD element 'DeviceIdentity/DeviceName' is missing, and fallback 'DeviceVariant/ProductName' is also missing.` | No device name and no fallback product name are present |
| `IODD element 'ExternalTextCollection' exists, but 'PrimaryLanguage' is missing.` | `ExternalTextCollection` exists without `PrimaryLanguage` |

---

## 6. Helper Functions

### 6.1 XML Element Queries

| Function | Purpose |
|---|---|
| `hasElement(doc: Document, tagName: string): boolean` | Checks whether an element exists anywhere in the document |
| `getFirstElement(doc: Document, tagName: string): Element \| null` | Returns the first matching element |
| `hasDirectChildElement(parent: Element \| null, tagName: string): boolean` | Checks whether a direct child element exists |

---

### 6.2 IODD Detection

| Function | Purpose |
|---|---|
| `isIoddDoc(doc: Document): boolean` | Checks whether the document uses the IODD namespace |

---

### 6.3 IODD Detail Checks

| Function | Purpose |
|---|---|
| `hasDeviceNameOrVariantProductName(doc: Document): boolean` | Checks whether a device name or fallback product name is present |
| `hasPrimaryLanguageInExternalTextCollection(doc: Document): boolean` | Checks whether an existing `ExternalTextCollection` contains `PrimaryLanguage` |

---

## 7. Module State

The module uses module-level variables to manage the current validation state.

```typescript
let file: File | null = null
let errorMessage: string = ''
let resultMessage: string = ''
```

| Variable | Meaning |
|---|---|
| `file` | File currently being validated |
| `errorMessage` | Most recent error message |
| `resultMessage` | Most recent success message or diagnostic information |

Important:

- `uploadHandler()` returns `errorMessage`.
- `resultMessage` is only relevant internally or for diagnostics.
- Because of the module-level state, parallel validations should be handled with care.

---

## 8. Data and Control Flow

```txt
File | null
   ↓
uploadHandler()
   ↓
Check file extension
   ↓
Format-dependent validation function
   ├─ .vec → validateVecFile()
   ├─ .kbl → validateKBLFile()
   ├─ .xml → validateXmlFile()
   └─ other → no specific validation
   ↓
validateWellFormedXML()
   ↓
DOMParser
   ↓
Root-element or IODD-structure validation
   ↓
errorMessage
   ↓
Return to component
```

---

## 9. Use in Components

### 9.1 Use in `UploadAASKblVec.vue`

```typescript
const validationError = await uploadHandler(file)

if (validationError && validationError.trim() !== '') {
  // Show the error to the user
  return
}
```

### 9.2 Use in `FileForm.vue`

```typescript
const errormsg = await uploadHandler(fileElement.value)

if (errormsg !== '') {
  errors.value.set('fileInput', errormsg)
  return
}
```

---

## 10. Test Coverage

The tests are located in:

```txt
tests/utils/XMLValidator.test.ts
```

The tests cover the following areas:

| Area | Examples |
|---|---|
| KBL validation | missing header, invalid root element, well-formed KBL, malformed KBL |
| VEC validation | valid VEC, invalid VEC root, missing version tag |
| Namespace handling | VEC inside KBL, KBL inside VEC |
| Malformed XML | unclosed tags, invalid declarations |
| Cross-format errors | VEC content in `.kbl`, KBL content in `.vec` |

---

## 11. Technical Notes

### DOMParser

The module uses `DOMParser` to parse XML.

MIME type used by the parser:

```txt
text/xml
```

Important:

- `DOMParser` is browser-based.
- Parser errors are detected via `parsererror` elements.

---

### MIME Type Detection and Automatic shortID Population

Additional MIME types used for the supported KBL and VEC files are:

```txt
application/kbl+xml
application/vec+xml
```

These MIME types are defined in:

```txt
src\components\EditorComponents\InputTypes\FileInput.vue
```

at lines `121` and `122`.

MIME type detection is implemented in:

```txt
src\composables\AAS\SubmodelElements\File.ts
```

at lines `227` to `229`.

---

### Case-insensitive Root Matching

Root element names are normalized before comparison.

This allows spelling variants of the permitted root elements to be accepted.

---

### Namespace-aware Queries

Element queries are namespace-aware.

For this purpose, queries such as the following are used:

```typescript
getElementsByTagNameNS('*', name)
```

This makes it possible to validate XML documents that use namespaces.

---

### Early Exit

Validation stops at the first error.

The module does not attempt to collect all errors in a document.

---

### Automatic Population of ShortID

This module is also responsible for automatically populating the `shortID`Field based on the uploaded filename.

---

## 12. Maintenance Notes

When changes are made to the module, the following areas should be checked:

| Change | Affected areas |
|---|---|
| New supported file extension | `uploadHandler()` |
| New VEC root elements | `validateVecFile()` |
| New KBL root elements | `validateKBLFile()` |
| Changed IODD structure rules | `validateIoddCore()` and IODD helper functions |
| Adjustment of error messages | Calling components and tests |
| Change in parser logic | `validateWellFormedXML()` |
| Parallel validation | Module-level state `file`, `errorMessage`, `resultMessage` |

---

## 13. Known Risks

| Risk | Impact | Recommendation |
|---|---|---|
| Module-level state | Parallel validations could interfere with one another | Prefer local state or serialize calls |
| Early exit | The user only sees the first error | Implement error accumulation if required |
| DOMParser behavior | Browser-dependent parser details may occur | Run tests in the target environment |
| Unknown KBL/VEC root variants | Valid files could be rejected | Review the root allowlist regularly |
| Other file extensions are not validated | Potentially unchecked files may proceed | Document this behavior deliberately or make validation stricter |
| IODD validation only checks core structure | Technically incomplete IODD files may be accepted | Add full IODD schema validation if needed |

---

## 14. Outlook

In the future, the validation logic could be extended to support additional XML-based file formats as well as entirely different file types. This would make the module more flexible and allow it to cover a broader range of upload scenarios.
