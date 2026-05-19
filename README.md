# 🚀 Team 3 – BaSyx Editor Extension

---

# 👥 Project Team – Team 3 Software Engineering

| Name | Role | Github |
| ---- | ---- | ---- |
| Martin Boehm  | Project Director | [martin-tinf24f](https://github.com/martin-tinf24f) |
| Florian Zahn | Project Manager | [Florian-Zahn](https://github.com/Florian-Zahn) |
| Federico Dibenedetto | System Architect | [FedeZ7](https://github.com/FedeZ7) |
| Felix Bandl | System Architect | [fix730](https://github.com/fix730) |
| Daniel Ziegler | Testmanager | [forestpit](https://github.com/forestpit) |
| Leonardo Risatti | Technical Documentation | [Loitt2](https://github.com/Loitt2) |

---

# 🌱 The Root Project

This project extends the **Eclipse BaSyx** ecosystem, with a focus on improving the BaSyx user interface, editor workflow, viewer functionality, and related backend services.

BaSyx provides an open-source framework for working with **Asset Administration Shells (AAS)**, which are standardized digital representations of physical or logical assets in Industry 4.0 environments.

The project builds on the existing BaSyx UI and backend infrastructure to simplify the integration, inspection, and transformation of external engineering data.

---

# 🧩 Our Project – BaSyx Editor Extension

The Team 3 project focuses on extending the BaSyx environment so that engineering model files can be imported, validated, viewed, and transformed into structured AAS content.

The system is designed to support model files such as:

- KBL
- VEC
- XML
- JSON-based structured data where applicable

The project improves the workflow from external engineering files to AAS-based digital asset models by introducing:

- import validation and MIME type handling
- structured XML visualization
- guided AAS generation from KBL/VEC files
- targeted backend retrieval of specific structured file data
- clearer error handling and improved system integration

The corresponding Issues we opened on the [BaSyx-Github Issues page](https://github.com/eclipse-basyx/basyx-aas-web-ui/issues) are:
- [\[FEATURE\] Import AAS from .KBL and .VEC files #1201](https://github.com/eclipse-basyx/basyx-aas-web-ui/issues/1201)
- [\[FEATURE\] XML Tree View with Distinguishable Node Labels and Navigation #1200](https://github.com/eclipse-basyx/basyx-aas-web-ui/issues/1200)
- [\[FEATURE\] REST API for Selective Access to Content within External XML/JSON Files #1180](https://github.com/eclipse-basyx/basyx-aas-web-ui/issues/1180)
- [\[FEATURE\] File Validation for XML, KBL, VEC #1179](https://github.com/eclipse-basyx/basyx-aas-web-ui/issues/1179)

The Pullrequest submitting the changes according to those Feature-Issues can be found [here](https://github.com/eclipse-basyx/basyx-aas-web-ui/pull/1230).

---

# 🧠 Project Overview

The BaSyx Editor Extension enables users and external systems to work more efficiently with engineering data inside the Asset Administration Shell ecosystem.

An **Asset Administration Shell** is a standardized digital representation of an asset. It can contain submodels, technical data, documentation, and structured information that supports digital engineering and Industry 4.0 use cases.

This project concentrates on four core capabilities:

1. Importing external model files with validation and MIME type detection
2. Displaying XML data in a structured and navigable form
3. Generating AAS content from KBL/VEC files through a wizard-driven workflow
4. Providing REST-based access to specific structured data points without transferring entire source files

---

# 🎯 Project Goal

The goal of this project is to reduce manual effort when integrating external engineering data into BaSyx and to make complex structured files easier to understand and reuse.

The system improves:

- reliability during file import
- transparency of XML-based content
- automation of AAS generation
- data quality and consistency
- targeted retrieval of engineering information
- usability of the BaSyx editor and viewer workflow

---

# 🔄 Before vs. After

## Before

- External model files required more manual handling
- File format mismatches were harder to detect
- XML content was difficult to navigate
- AAS creation from engineering files required substantial manual effort
- Specific values inside linked structured files were not easily retrievable through a focused backend interface
- Error handling during these workflows was less explicit

## After

- Imported files are validated before further processing
- MIME types are determined and stored appropriately
- XML files can be viewed through a structured navigation concept
- KBL/VEC data can be transformed into AAS content through a guided generation process
- Specific file entries can be queried through a dedicated backend interface
- Error cases are handled more clearly in both UI and API workflows

---

# 🧭 Main Use Cases

The project is structured around four central use cases.

---

## 📥 UC01 – Import with Plausibility Check and MIME Type Detection

Users can import external model files into the BaSyx editor. During upload, the application checks whether the file content is readable and whether the provided file format is plausible.

### Core Workflow

- The user selects and uploads a file through the UI
- The system checks whether the file content can be interpreted
- A file element is created when the import is valid
- The MIME type is determined and applied
- Invalid files trigger an error response instead of entering the workflow

### Benefit

This improves data quality at the beginning of the process and prevents incorrectly classified files from being used in later processing steps.

---

## 🌳 UC02 – XML Viewer with Navigation and Display Functions

Users can inspect attached XML-based files through a dedicated viewer interface.

<img width="640" height="400" alt="image" src="https://github.com/user-attachments/assets/4dc19cf8-a76c-46c2-bfac-67b3f1ce5dfe" />

### Core Workflow

- The user opens a linked KBL, VEC, or XML file
- The viewer presents a table of contents for the document
- The user selects entries from the navigation structure
- The corresponding XML section is displayed with relevant node information

### Benefit

Complex XML documents become easier to understand, inspect, and navigate without manually searching through raw file contents.

---

## 🏗️ UC03 – AAS Generator from KBL/VEC

Users can create a new Asset Administration Shell from validated KBL or VEC source files.

### Core Workflow

- The user starts AAS generation from a linked model file
- The system analyzes the file and checks validity
- A wizard guides the user through selecting relevant content
- The selected information is transformed into AAS structures
- The generated AAS is stored on the AAS server
- Two dedicated submodels are created:
  - `HandoverDocumentation`
  - `TechnicalData`

### Example Resulting Structure

```text
AAS
 ├── Submodel: HandoverDocumentation
 │    └── Original source file
 └── Submodel: TechnicalData
      ├── Extracted technical properties
      ├── Structured data points
      └── Mapped engineering information
```

### Benefit

This lowers manual modeling effort and accelerates the transformation of engineering data into standardized AAS representations.

---

## 🔎 UC04 – Automated Extraction of Specific XML Entries from the AAS

External systems or backend services can request targeted information from structured files linked in the BaSyx context.

### Core Workflow

- An external client sends a backend request with a file reference and query point
- The system inspects the referenced XML or JSON structure
- The requested node, path, ID, or field is located
- Only the requested data point is returned
- Invalid or missing query targets produce an appropriate error response

### Benefit

The interface avoids transferring complete source documents when only a small subset of information is required, making integration more efficient and precise.

---

# 🧱 System Architecture

The solution extends the existing BaSyx architecture through frontend and backend additions.

## Frontend – BaSyx UI

- File Upload Component
- MIME Type Detection and Plausibility Check
- XML Viewer with Tree-Based Navigation
- AAS Generator Wizard
- Error Message Handling System

## Backend – AAS Server Extensions

- KBL/VEC Data Extraction Service
- XML Query REST API Endpoint
- Support for targeted structured-data inspection and retrieval

---

# 📊 Non-Functional Requirements

The project also addresses the non-functional requirements:

- **Usability:** intuitive integration into the existing BaSyx UI workflow
- **Performance:** responsive processing of standard-sized model files with visible user feedback
- **Maintainability:** alignment with BaSyx conventions, documentation, tests, and open-source contribution readiness
- **Documentation:** structured user guidance for new workflows and setup improvements
- **Compatibility:** continued interoperability with the target BaSyx UI and backend infrastructure
- **Error Handling:** robust responses for invalid files, failed generation, API issues, and invalid query paths
- **Demo Availability:** publicly accessible demonstration environment for stakeholder validation

---

# ✅ Project Outcome

The Team 3 BaSyx Editor Extension establishes a more automated and reliable workflow for integrating engineering model files into Asset Administration Shells.

The final solution provides:

- safer model-file imports
- clearer XML file inspection
- guided AAS generation from KBL/VEC
- improved usability and error handling
- stronger alignment between engineering source data and AAS-based digital models

**Implementation note:** UC04 – Automated extraction of specific XML entries from the AAS – was specified in the SRS but was **not implemented** in the final project scope.

# 🔎 Live Hosting

The WebUI can be accessed [here](https://swe.fede.rocks).
To have full functionality please use a local or remotely hosted backend and connect it through the WebUI settings under Infrastructure. It may be necessary to refresh the page after changing the Infrastructure settings.
The BaSyx backend can be downloaded [here](https://basyx.org/get-started/application).
