# 1. Introduction

## 1.1 Project Overview

This project extends the **BaSyx AAS Web UI** by adding new functionalities for processing technical XML-based engineering data such as **KBL**, **VEC**, and other structured industrial formats.

The main goal of these extensions is to simplify the integration of external engineering data into the **Asset Administration Shell (AAS)**. The system enables users to upload complex model files, automatically validate their structure and content, extract relevant technical information, and visualize XML data in a clear and navigable way.

By automating these steps, the plugin reduces manual effort, improves data consistency, and supports a more efficient engineering workflow within the BaSyx ecosystem.


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
- MIME-Type detection based on file content  
- XML Viewer with hierarchical tree navigation and node inspection  
- Automatic AAS generation from KBL/VEC files via a guided wizard  

These features work together to provide a seamless workflow from raw engineering data to structured AAS representations.


# 2. System Requirements

To use the extended BaSyx Web UI, the following requirements must be met:

- Running instance of the **BaSyx AAS Web UI**  
- Modern web browser (Google Chrome, Microsoft Edge, or Mozilla Firefox recommended)  
- Access to a configured **AAS Server environment**  
- Supported file formats:
  - `.xml`
  - `.kbl`
  - `.vec`



# 3. Functionalities

This section describes the main features of the system and how to use them in practice.


# 3.1 File Upload with Validation

## Description

Users can upload XML-based engineering files such as **KBL**, **VEC**, or general XML files into the BaSyx system.

After upload, the system automatically performs a validation process that includes:

- Checking file structure integrity  
- Detecting file content type (MIME-Type detection)  
- Verifying compatibility with supported schemas  

This ensures that only valid and processable files are integrated into the AAS environment.

## Steps

1. Open the **BaSyx AAS Editor**
2. Navigate to the upload section
3. Click on **Upload File**
4. Select a local `.xml`, `.kbl`, or `.vec` file
5. Wait for the validation process to complete

## Result

- **Valid file:** The file is accepted, linked to the AAS, and marked with a success indicator  
- **Invalid file:** An error message is displayed explaining why the file could not be processed  




# 3.2 XML Viewer

## Description

The XML Viewer provides a structured and interactive representation of uploaded XML-based files.

Instead of displaying raw XML text, the content is visualized as a **tree structure**, allowing users to:

- Navigate through hierarchical data  
- Expand and collapse XML nodes  
- Inspect attributes, values, and identifiers (IDs)  
- Quickly locate relevant sections of the file  

This improves readability and simplifies working with complex engineering data structures.

## Steps

1. Open an already uploaded file in the BaSyx UI  
2. The XML Viewer opens automatically or via selection  
3. Browse the tree structure on the left panel  
4. Click on nodes to view detailed information  

<img width="1386" height="1070" alt="Image" src="https://github.com/user-attachments/assets/90b2b62b-877e-4ab3-81e0-ba273b88fc57" />



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
