# Customer Requirement Specification (CRS)
## Team3-Basyx-Editor

## Version Control

|Version|Date|Author|Comment|
|-----|-----------|------------|---------------------|
|1.0|12.10.2025|Felix Bandl|first version|
|1.1|13.10.2025|Felix Bandl|priority added|
|1.2|31.10.2025|Felix Bandl|CRS adjusted after consultation with Mr. Rentschler|
|1.3|Date|Name|Comment3|
|1.4|Date|Name|Comment4|

## Table of contents
1. [Scope](#1-scope)
2. [Introduction](#2-introduction)
3. [Use Cases](#3-use-cases)
    - 3.1 [UC01: Import with plausibility check and MimeType detection](#31-uc01-import-with-plausibility-check-and-mimetype-detection)
    - 3.2 [UC02: XML viewer with navigation and display functions](#32-uc02-xml-viewer-with-navigation-and-display-functions)
    - 3.3 [UC03: AAS generator from KBL/VEC](#33-uc03-aas-generator-from-kblvec)
    - 3.4 [UC04: Automated extraction of specific XML entries from the AAS](#34-uc04-automated-extraction-of-specific-xml-entries-from-the-aas)
4. [Customer Requirements](#4-customer-requirements)
    - 4.1 [Functional Requirements](#41-functional-requirements)
        - 4.1.1 [FR.01 MimeType Detection of Model Files](#411-fr01-mimetype-detection-of-model-files)
        - 4.1.2 [FR.02 Plausibility Check (Extension vs. Content)](#412-fr02-plausibility-check-extension-vs-content)
        - 4.1.3 [FR.03 Table of Contents in XML Visualization](#413-fr03-table-of-contents-in-xml-visualization)
        - 4.1.4 [FR.04 AAS Generator Wizard and Property Adoption](#414-fr04-aas-generator-wizard-and-property-adoption)
        - 4.1.5 [FR.05 REST API for Targeted Data Retrieval](#415-fr05-rest-api-for-targeted-data-retrieval)
        - 4.1.6 [FR.06 Error Handling](#416-fr06-error-handling)
    - 4.2 [Non-functional Requirements](#42-non-functional-requirements)
        - 4.2.1 [NFR.001 Usability](#421-nfr001-usability)
        - 4.2.2 [NFR.002 Performance](#422-nfr002-performance)
        - 4.2.3 [NFR.003 Maintainability and Contribution to the Open-Source Project](#423-nfr003-maintainability-and-contribution-to-the-open-source-project)
        - 4.2.4 [NFR.004 Documentation](#424-nfr004-documentation)
        - 4.2.5 [NFR.005 Compatibility](#425-nfr005-compatibility)
        - 4.2.6 [NFR.006 Availability (Demo)](#426-nfr006-availability-demo)
     


## 1. Scope

This document explains the customer's problem and defines the essential project requirements and guidelines. It serves as a foundation and a common reference for all project stakeholders. A further focus is on defining the software requirements from a user and customer perspective, so that the development team understands the product vision and can translate it into tangible functions.

## 2. Introduction

![overview image](images/CRS/Introduction.png)

The central goal of this project is the functional extension of the Eclipse BaSyx user interface, particularly the editor and viewer plugins and the corresponding REST API backend. The extension is aimed at users who need a seamless and automated integration of existing engineering data, such as that available in KBL or VEC files, into the Asset Administration Shell (AAS).

At its core, the application should enable users to integrate external model files directly into the AAS. Instead of transferring data manually, the solution creates an efficient workflow in which the files are not only plausibility-checked and correctly linked, but also analyzed in terms of content. Essential information, such as technical data from wire harnesses, is automatically extracted and transferred to standardized submodels. This significantly reduces manual effort and increases data consistency.

Furthermore, the REST API will be extended to allow direct access to data points within attached XML files. This internal data can then be visualized in a structured and user-friendly way in the viewer. The customer benefit thus lies in the creation of a more powerful and intelligent user interface that makes it possible not only to manage complex data from external sources, but also to use and understand it directly in the context of the AAS.

## 3. Use Cases

### 3.1 UC01 Import with plausibility check and MimeType detection

| | |
| :--- | :--- |
| **Use Case ID** | UC01 |
| **Description** | The user wants to import an external model file with a specific format (KBL, VEC) or a general data format into the application. The application performs a plausibility check to ensure that the file extension and the actual content structure of the file match. After successful verification, the correct MimeType is set and the file is made available for further processing. |
| **Precondition** | The model file (e.g. KBL/VEC/XML/AML) exists on the user's local system. |
| **Postcondition on Success**| The file has been successfully validated. The correct MimeType has been determined and stored. The file is now available for subsequent processing steps (e.g., AAS generation). |
| **Triggering Event** | The user selects the file using an import function and starts the upload process. |

### 3.2 UC02 XML viewer with navigation and display functions

| | |
| :--- | :--- |
| **Use Case ID** | UC02 |
| **Description** | The user wants to view the contents of an XML file (e.g., imported KBL/VEC or AML data). The application provides an XML viewer that displays a table of contents for the XML document to facilitate navigation. The user can navigate to the appropriate section of the document using the table of contents.|
| **Precondition** | A valid XML file has already been successfully imported. |
| **Postcondition on Success**| The XML content is displayed clearly. Users can navigate to the relevant section of the XML file using the table of contents and view the details (including IDs) of the individual nodes. |
| **Triggering Event** |The user opens the viewer of an asset.|

### 3.3 UC03 AAS generator from KBL/VEC

| | |
| :--- | :--- |
| **Use Case ID** | UC03 |
  | **Description** | The user wants to automatically generate an `Asset Administration Shell (AAS)` from prepared model files. The application provides a wizard that analyzes the KBL/VEC data and generates the AAS structure (submodels and submodel elements). All properties selected by the user in the wizard are transferred to the AAS. Generation is performed via the API of the AAS generator.  |
| **Precondition** | A valid model file (e.g., KBL file) is available. The connection to the AAS generator (REST API) is active. |
| **Postcondition on Success**| A new AAS has been successfully generated, in which all supported data selected by the user is mapped from the model file as submodel elements. The created AAS is stored on the VWS server. |
| **Triggering Event** | The user starts the AAS Generation Wizard and selects a model file. |


### 3.4 UC04 Automated extraction of specific XML entries from the AAS

| | |
| :--- | :--- |
| **Use Case ID** | UC04 |
  | **Description** | An external system or internal backend service wants to retrieve specific, individual XML entries from the AAS model previously generated by UC03. The application provides a backend interface (REST API) that enables targeted data queries by transmitting a specific query point (e.g., the ID of an element or a path in the XML/AAS model). The interface then returns only the desired information (e.g., the value of a specific property).  |
| **Precondition** | An AAS model was successfully generated by UC03 and is available on the AAS server. The requesting system knows the ID or path of the desired XML/AAS entry. |
| **Postcondition on Success**| The backend interface automatically and accurately returns the requested specific XML/AAS information to the requesting system. |
| **Triggering Event** | The external system/backend service sends an API request to the interface containing the desired query point (path/ID).|

## 4. Customer Requirements
The requirements are described with an ID and an overview to enable the development team to understand and implement them in the development process. 

### 4.1 Functional Requirements

The functional requirements are prioritized from 1 to 5 to indicate which requirements are most important to implement. 5 means very important and 1 means not so important.


#### 4.1.1 FR.01 MimeType Detection of Model Files

| Field | Content | 
| :--- | :--- | 
| **Requirement ID** | FR.01 | 
| **Overview** | The application must correctly identify all supported model file types (e.g., KBL, VEC, XML, AML) upon upload and automatically assign the corresponding IANA-compliant MimeType. | 
| **Acceptance Criterion** | Based on the file extension, the system recognizes the file type (e.g., KBL, VEC, XML, or AML). | 
| **Priority** | 5 | 

#### 4.1.2 FR.02 Plausibility Check (Extension vs. Content)

| Field | Content | 
| :--- | :--- | 
| **Requirement ID** | FR.02 | 
| **Overview** | Before further processing, the application must perform a plausibility check that verifies the file extension against the actual content (start line/structure) of the file for agreement. | 
| **Acceptance Criterion** | In case of a conflict between extension and content (e.g., an .xml file starting with PK), the upload is aborted, and an informative error message (see FR.06) is issued. | 
| **Priority** | 4 | 

#### 4.1.3 FR.03 Table of Contents in XML Visualization

| Field | Content | 
| :--- | :--- | 
| **Requirement ID** | FR.03 | 
| **Overview** | The Viewer plugin must display the data of an attached XML file in a structured table of contents to enable navigation through the document. | 
| **Acceptance Criterion** | When a user opens an AAS and clicks on the Viewer, a new view displays the table of contents and the XML file. | 
| **Priority** | 4 | 
| **UI** |  ![FR001 XML Viewer Sketch](images/CRS/XMLViewer.png)|


#### 4.1.4 FR.04 AAS Generator Wizard and Property Adoption

| Field | Content | 
| :--- | :--- | 
| **Requirement ID** | FR.04 | 
| **Overview** | The application must provide a Wizard that uses the data extracted from the KBL/VEC files for the automatic generation of the AAS model and the associated Submodel Elements. All properties selected by the user must be adopted. | 
| **Acceptance Criterion** | The Wizard guides the user through the generation process. Upon completion, the generated AAS model contains all selected KBL/VEC data as Submodel Elements. | 
| **Priority** | 4 | 

#### 4.1.5 FR.05 REST API for Targeted Data Retrieval

| Field | Content | 
| :--- | :--- | 
| **Requirement ID** | FR.05 | 
| **Overview** | The backend interface (REST API) must be extended to allow external systems to automatically retrieve specific XML/AAS entries from the generated AAS by submitting a query path (Path/ID). (Reference to UC04). | 
| **Acceptance Criterion** | A new API endpoint exists. Upon a correct request, the API returns only the values of the specified Properties/Elements, not the entire Submodel content. | 
| **Priority** | 2 | 

#### 4.1.6 FR.06 Error Handling

| Field | Content | 
| :--- | :--- | 
| **Requirement ID** | FR.06 | 
| **Overview** | The system must correctly handle errors (e.g., corrupt files, API failures, invalid query paths) and return clear, informative error messages (UI) or correct HTTP status codes (API). | 
| **Acceptance Criterion** | A message is displayed upon invalid file (UC01); no crash occurs upon generation error (UC03); a 404 Not Found or 400 Bad Request is returned upon invalid API path (UC04). | 
| **Priority** | 4 |




### 4.2 Non-functional Requirements

#### 4.2.1 NFR.001 Usability

| | |
| :--- | :--- |
| **Requirement ID** | NFR.001 |
| **Overview** | The new functionalities in the editor and viewer must be intuitive and well integrated into the existing workflow of the BaSyx UI. |
| **Acceptance Criterion** | A user who is familiar with the BaSyx UI can perform the main use cases (uploading a file, viewing XML content) without consulting the documentation. The workflow for each use case is clear and logical. |

#### 4.2.2 NFR.002 Performance

| | |
| :--- | :--- |
| **Requirement ID** | NFR.002 |
| **Overview** | The parsing of the files and the data extraction should be efficient to ensure a responsive user experience. |
| **Acceptance Criterion** | The server-side processing (parsing, extraction, populating the submodel) of a standard-sized model file must be completed in under 5 seconds. The UI provides feedback (e.g., a loading indicator) during this process. |

#### 4.2.3 NFR.003 Maintainability and Contribution to the Open-Source Project

| | |
| :--- | :--- |
| **Requirement ID** | NFR.003 |
| **Overview** | The developed code must comply with the coding standards of the Eclipse BaSyx project and be well documented to facilitate maintenance and future contributions from the open source community. |
| **Acceptance Criterion** | The code follows existing project conventions. All new public classes and methods are documented. The implementation is covered by unit tests. A pull request for the new features is created and submitted to the official BaSyx repositories. |

#### 4.2.4 NFR.004 Documentation

| | |
| :--- | :--- |
| **Requirement ID** | NFR.004 |
| **Overview** | Clear and structured user documentation for the new functionalities must be created. |
| **Acceptance Criterion** | An online user documentation is created. It explains the new functions with step-by-step instructions and screenshots. The tutorials for setting up the BaSyx infrastructure are evaluated and improved where gaps have been identified. |

#### 4.2.5 NFR.005 Compatibility

| | |
| :--- | :--- |
| **Requirement ID** | NFR.005 |
| **Overview** | The extensions must be fully compatible with the target version of the BaSyx UI and the backend infrastructure and must not negatively affect existing functionalities. |
| **Acceptance Criterion** | All existing, unchanged functionalities of the BaSyx UI continue to function as expected after the integration of the new features. The solution can be built and run within the standard BaSyx build chain. |

#### 4.2.6 NFR.006 Availability (Demo)
| | |
| :--- | :--- |
| **Requirement ID** | NFR.006 |
| **Overview** | The final functionalities must be hosted on a publicly accessible demo server and be executable. |
| **Acceptance Criterion** | The Use Cases (UC01-UC04) implemented in the project can be tested live by project stakeholders via a provided URL without requiring a VPN or special software installations.|
