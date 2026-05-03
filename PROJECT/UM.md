# 1. Introduction

## 1.1 Project Overview

This project extends the Eclipse BaSyx AAS Web UI by introducing additional functionalities for processing technical XML-based engineering data, such as KBL, VEC, and other structured industrial formats.

The main objective of these extensions is to simplify and standardize the integration of external engineering data into the Asset Administration Shell (AAS). The system enables users to upload complex model files, automatically validate their structure and content, extract relevant technical information, and visualize XML data in a clear and navigable format.

By automating these processes, the plugins reduce manual effort, improve data consistency, and support a more efficient and reliable engineering workflow within the BaSyx ecosystem.

## 1.2 Purpose of this Manual

This User Manual explains how to use the implemented functionalities step by step.

It is intended for:

- Users of the BaSyx Web UI  
- Developers and testers working with the extensions  
- Project partners and stakeholders evaluating the solution  

The manual focuses on practical usage rather than technical implementation details and provides a guided overview of all available features.



## 1.3 Included Functionalities

The project introduces the following extensions to the BaSyx Web UI:

- File Upload with automatic validation and plausibility checks  
- XML Viewer with hierarchical tree navigation and node inspection  
- Automatic AAS generation from KBL/VEC files via a guided wizard  

These features work together to provide a seamless workflow from raw engineering data to structured AAS representations.


# 2. System Requirements

To use the extended BaSyx Web UI, the following requirements must be met:

- Running instance of the **BaSyx AAS Web UI** and **AAS Server environment**    (More info on how to set up: https://github.com/eclipse-basyx/basyx-aas-web-ui/blob/main/README.md)
- Modern web browser (Google Chrome, Microsoft Edge, or Mozilla Firefox recommended)  

# 3. Functionalities

This section describes the main features of the system and how to use them in practice.


# 3.1 File Upload with Validation

## Description

Users can upload XML-based engineering files such as **KBL, VEC, or general XML files** into the BaSyx system via the Submodel editor.

After the upload is triggered, the system automatically performs a validation process that includes:

- Checking file structure integrity  
- Detecting file content type (MIME-Type detection)  
- Verifying compatibility with supported XML schemas  

This ensures that only valid and processable files are integrated into the Asset Administration Shell (AAS).

---

## Steps

### 1. Open Submodel Tree
Open the desired **Submodel Tree** inside the AAS Editor.

<img width="1195" height="986" alt="image" src="https://github.com/user-attachments/assets/acdf2938-a8a8-44b7-bc0d-e1121c6a57ea" />

---

### 2. Add Submodel Element
Navigate to **"Add Submodel Element"** in the context menu.

A new window will open.

---

### 3. Select File Type
Select **Type: File**.

<img width="856" height="178" alt="image" src="https://github.com/user-attachments/assets/7f76a230-908e-40d2-9b93-a8db02110752" />

---

### 4. Configure File Element
A new configuration window opens.

Enter the required information in the input fields and select **File** as the value type.

<img width="1792" height="1060" alt="image" src="https://github.com/user-attachments/assets/dd233408-16f2-41bd-886a-799fec5612a6" />

---

### 5. Upload File and Save
Upload your desired XML-based file and press **Save** to confirm the creation.

<img width="1601" height="1073" alt="image" src="https://github.com/user-attachments/assets/d2b84bb3-c490-4ae1-a350-dbed4c08d4aa" />

---

## Result

### Valid File
- The file is accepted successfully  
- It is added to the Submodel tree  
- It becomes available for further processing (e.g. XML Viewer, AAS generation)

---

### Invalid File
If the file does not pass validation, an error message is displayed explaining the reason for rejection.

Typical error cases include:

#### Missing XML Header
<img width="1061" height="717" alt="image" src="https://github.com/user-attachments/assets/e5ed1ab4-da4e-4e74-babe-ba9c1b570859" />

---

#### Invalid Elements / Structure Violation
<img width="1066" height="805" alt="image" src="https://github.com/user-attachments/assets/eabe46ed-c083-4790-89ee-eec382cfc572" />

---

#### Not Well-Formed XML File
<img width="1073" height="805" alt="image" src="https://github.com/user-attachments/assets/210ef405-5980-4ca8-a013-f1c9c05a33ed" />







# 3.2 XML Viewer

## Description

The XML Viewer provides a structured and interactive representation of uploaded XML-based files.

Instead of displaying raw XML text, the content is visualized as a **tree structure**, allowing users to:

- Navigate through hierarchical data  
- Expand and collapse XML nodes  
- Inspect attributes, values, and identifiers (IDs)  
- Quickly locate relevant sections of the file  

This improves readability and simplifies working with complex engineering data structures.

## How to Open the XML Viewer

1. Click on an already uploaded XML-based file (e.g. XML, KBL, VEC) in the BaSyx UI
2. Open the XML Viewer by clicking the **“Visualization”** button

📸 Screenshot:  
<img width="2009" height="908" alt="image" src="https://github.com/user-attachments/assets/29198bad-46bd-4b46-b720-70963513fd7f" />

## Layout Overview

After opening the viewer, the screen is divided into two parts:

### Left Side – Tree Structure
- Displays the XML document as a hierarchical tree
- Each node represents an XML element
- Elements can be expanded or collapsed
- Shows the structure of the file (parent-child relationships)

### Right Side – XML Content View
- Shows the full document structure in xml form
<img width="1651" height="1071" alt="image" src="https://github.com/user-attachments/assets/4dc19cf8-a76c-46c2-bfac-67b3f1ce5dfe" />


## Navigation & Interaction

- Clicking on a node in the tree view:
  - Navigates to the corresponding XML element
  - Highlights the selected element in the XML view
<img width="2000" height="1109" alt="image" src="https://github.com/user-attachments/assets/1817c2b2-c9cb-43be-b9e1-92762e8bfe57" />


- Users can expand and collapse nodes to explore the structure step by step by clicking on the arrow

<img width="1768" height="1139" alt="image" src="https://github.com/user-attachments/assets/8661d4c2-e60b-4f4c-8051-72cef7f59105" />





# 3.3 Generate AAS from File

## Description

This feature enables the automatic generation of an **Asset Administration Shell (AAS)** based on uploaded KBL or VEC files.

A guided wizard analyzes the uploaded file and extracts relevant engineering data. The user can select which elements should be included in the final AAS structure.

The system then creates:

- A structured AAS instance  
- Automatically generated submodels  
- Populated technical data fields  

## Steps

1. Open the **three-dot menu** of the uploaded file  
2. Select **Create AAS from File**  
3. Upload or confirm the selected KBL/VEC file  
4. Click **Generate Technical Data** to extract available information  
5. Review and select the desired data elements  
6. Click **Generate AAS** to finalize the process  

## Result

A new AAS is created containing at least the following submodels:

- **HandoverDocumentation** (original file attached)  
- **TechnicalData** (extracted structured information)

The generated AAS is automatically stored on the AAS server and becomes available for further use.




# 5. Copyright / License

This project was developed by **Team3 at DHBW** as part of the academic study program.

It is based on the **Eclipse BaSyx framework**, which is licensed under the **MIT License / Eclipse open-source project**.

All custom implementations, plugins, and extensions created within this project are the intellectual work of Team3.

**Optional note:**

All screenshots, UI designs, and plugin extensions © Team3 (DHBW).
