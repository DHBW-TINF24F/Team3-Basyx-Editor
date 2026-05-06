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


Users can upload XML-based engineering files such as **KBL, VEC, or general XML files** into the BaSyx system via the Submodel editor.

After the upload is triggered, the system automatically performs a validation process that includes:

- Checking file structure integrity  
- Detecting file content type (MIME-Type detection)  
- Verifying compatibility with supported XML schemas  

This ensures that only valid and processable files are integrated into the Asset Administration Shell (AAS).



## Steps

### 1. Open Submodel Tree
Open the desired **Submodel Tree** inside the AAS Editor, to which you want to add the new file.Then Navigate to **"Add Submodel Element"** in the context menu.

<img width="1195" height="986" alt="image" src="https://github.com/user-attachments/assets/acdf2938-a8a8-44b7-bc0d-e1121c6a57ea" />

---

### 2. Select File Type
Select **Type: File**.

<img width="856" height="178" alt="image" src="https://github.com/user-attachments/assets/7f76a230-908e-40d2-9b93-a8db02110752" />

---

### 3. Configure File Element
A new configuration window opens.

Enter the required information in the input fields and select **File** as the value type.

<img width="1792" height="1060" alt="image" src="https://github.com/user-attachments/assets/dd233408-16f2-41bd-886a-799fec5612a6" />

---

### 4. Upload File and Save
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

This feature enables the automatic generation of an **Asset Administration Shell (AAS)** based on uploaded **KBL** or **VEC** files.

A guided wizard analyzes the selected file and extracts relevant engineering data. Users can review and customize the extracted information before generating the final AAS structure.

The system automatically creates:

- A structured AAS instance  
- Generated submodels  
- Pre-filled technical data fields based on the uploaded file  

---

## Steps

### 1. Switch to Editor Mode
Switch to the **Editor Mode** in the BaSyx UI.

<img width="2028" height="756" alt="image" src="https://github.com/user-attachments/assets/29f18f9f-de6e-40f6-9ea7-1bd0bb7a365d" />

---

### 2. Open AAS Generator
Click on the **three-dot menu (⋮)** and select  
**"Create AAS from KBL/VEC"**.

<img width="1776" height="797" alt="image" src="https://github.com/user-attachments/assets/029f3e67-f2ff-4c88-a4ca-57d31715eb09" />

---

### 3. Upload Files
A setup dialog will appear.

- Upload a **KBL or VEC file** in the upper section (required)  
- Optionally, upload a **product image** in the lower section via drag & drop or file selection  

<img width="789" height="1039" alt="image" src="https://github.com/user-attachments/assets/15163219-876a-4d40-8e97-edc53ceb3965" />

---

### 4. Configure AAS Metadata
After uploading the file, additional configuration fields become visible.

You can review and modify:
- **Short ID**
- **AAS Name**
- **Description**
- **Asset Kind**

You must generate or define:
- **Asset ID**
- **AAS ID**

These IDs can be:
- Generated automatically using the provided buttons (recommended)  
- Manually defined by the user  

<img width="994" height="1101" alt="image" src="https://github.com/user-attachments/assets/2fa958e7-8484-4b45-b801-022e0fbe5220" />

---

### 5. Review and Select Data Points
Scroll down to view the extracted data from the uploaded file.

- The data is displayed in a **tree structure**
- Each folder contains related data points
- By default, all data points are selected

You can:
- Expand folders to inspect content  
- Select or deselect specific data points using checkboxes  

<img width="1405" height="1035" alt="image" src="https://github.com/user-attachments/assets/05e6244d-aabf-4de2-867e-26aa78c086a7" />

---

### 6. Inspect Data Details (Optional)
You can open individual data points to inspect their detailed values before including them in the AAS.

<img width="1637" height="1014" alt="image" src="https://github.com/user-attachments/assets/b2f74691-3126-455f-873b-e46213a2ea98" />

---

### 7. Create the AAS
Finalize the process by clicking **"Create AAS"**.

<img width="982" height="1128" alt="image" src="https://github.com/user-attachments/assets/fd602642-1ea6-473f-807d-313ff2ab2667" />

---

### 8. Completion
The AAS is generated and uploaded to the system.

---

## Result

A new AAS is created containing at least the following submodels:

- **HandoverDocumentation**  
  Contains the original uploaded file, including metadata such as file name, format, and reference.

- **TechnicalData**  
  Contains the extracted and structured engineering data selected by the user.

<img width="794" height="898" alt="image" src="https://github.com/user-attachments/assets/59b4f653-5e95-49a3-a0e0-a0af44c8b211" />


# 5. Copyright / License

## License

This project is based on the Eclipse BaSyx AAS Web UI, which is licensed under the MIT License.

All additional functionalities, plugins, and extensions developed within this project are:

© 2026 Team3 – DHBW Stuttgart  
Licensed under the MIT License.


## Screenshots and Documentation

All screenshots, UI mockups, diagrams, and documentation created as part of this project are:

© 2026 Team3 – DHBW Stuttgart

These materials may be used for documentation, presentation, and academic purposes.

