# System Test Plan
## Team3-Basyx-Editor

## Version Control

|Version|Date|Author|Comment|
|-----|-----------|------------|---------------------|
|1.0|16.04.2026|Daniel Ziegler|Version 1.0|
|1.1|24.04.2026|Daniel Ziegler|Fromulating Test Cases, adding Testfiles|
|1.2|05.05.2026|Daniel Ziegler|Linking the testcases to the right Requirements|
|1.3|06.05.2026|Daniel Ziegler|Fixed table of contents, corrected the testfile linkage|

## Table of contents
1. [Introduction](#1-introduction)
2. [Scope](#2-scope)
3. [Test Strategy](#3-test-strategy)
4. [Test Environment](#4-test-environment)
    - 4.1 [Hardware Environment](#41-hardware-environment)
    - 4.2 [Software Environment](#42-software-environment)
    - 4.3 [Deployment Setup](#43-deployment-setup)
5. [Test Cases Overwiew](#5-test-cases-overview)
    - 5.1 [TC01	Proper XML-Validation	MOD01](#51-tc01-proper-xml-validation-mod01)
    - 5.2 [TC02	Handle Error Messages	MOD01](#52-tc02-handle-error-messages-mod01)
    - 5.3 [TC03	Display XML structure	MOD02](#53-tc03-display-xml-structure-mod02)
    - 5.4 [TC04	AAS-Creation-Wizard functions properly	MOD03](#54-tc04-aas-creation-wizard-functions-properly-mod03)
    - 5.5 [TC05	Extraction of the AAS Information MOD03](#55-tc05-extraction-of-the-aas-information-mod03)
6. [Test Data](#6-test-data)



## 1. Introduction
The purpose of this System Test Plan (STP) is to define the overall testing approach for the BaSyx Editor Extension.
It describes the test strategy, environment, test cases, and acceptance criteria required to verify that the system fulfills the requirements specified in the Software Architecture Specification (SAS).
## 2. Scope
This document covers testing of the changes planed in the BaSyx Editor Extension including:
* MOD01 – File Import and Validation Subsystem
* MOD02 – XML Viewer and Navigation Subsystem
* MOD03 – AAS Generation and Submodel Mapping Subsystem

This document does not cover:
* Unit testing of minor changes to existing code
* Internal BaSyx backend functionality
## 3. Test Strategy
The testing strategy for the BaSyx Editor Extension ensures reliable validation of all added system functionalities through a structured and requirement-driven approach. A key objective is to achieve wide test coverage.  Both positive and negative scenarios, including edge cases are considered to verify system robustness.

Testing is performed using a function isolation approach, where individual functionalities are tested independently. This improves defect detection and simplifies root cause analysis.

To validate requirements effectively, both file-based and code-based testing are applied. File-based testing uses input data (e.g., XML, KBL, VEC files) to verify the import, parsing, and visualization processes. Code-based testing uses Vitest, the existing testing environment the Basyx software uses, to ensure reliable, automated unit and integration test execution. 

This approach ensures a comprehensive, traceable, and efficient validation of the system.
## 4. Test Environment
### 4.1. Hardware Environment
* Client machine (modern browser-capable system)
### 4.2. Software Environment
* Browser: Chrome, Firefox, Edge
* Frontend: Vue.js application
* Backend services:
* BaSyx Registry
* BaSyx AAS Repository
* BaSyx Submodel Service
### 4.3. Deployment Setup
* Docker-based deployment setup

## 5. Test Cases Overview
All testcases include:
* TC01	Proper XML-Validation	MOD01
* TC02	Handle Error Messages	MOD01
* TC03	Display XML structure	MOD02
* TC04	AAS Creation Wizard functions properly	MOD03
* TC05	Extraction of AAS Information MOD03

As an initial situation for all tests, it is assumed that the environment is functional and accessible and the BaSyx Web UI is open. Additionally, the mode is set to the BaSyx Editor, and at least one AAS is already imported and open. The AAS contains at least one Submodel with an XML-type file element included.

### 5.1. TC01 Proper XML-Validation MOD01
<table style="width:100%; border-collapse:collapse; font-family:Arial, sans-serif;">
  <tr>
    <th colspan="3" style="border:1px solid black; padding:8px; text-align:center;">
      Test case
    </th>
  </tr>
  <tr>
    <td style="border:1px solid black; padding:8px;"><strong>ID:</strong></td>
    <td colspan="3" style="border:1px solid black; padding:8px; ">&lt;TC01&gt;</td>
  </tr>
  <tr>
    <td style="border:1px solid black; padding:8px;"><strong>Name:</strong></td>
    <td colspan="3" style="border:1px solid black; padding:8px;">Proper XML-Validation</td>
  </tr>
  <tr>
    <td style="border:1px solid black; padding:8px;"><strong>Req.-ID:</strong></td>
    <td colspan="3" style="border:1px solid black; padding:8px;">RR.02</td>
  </tr>
  <tr>
    <td style="border:1px solid black; padding:8px;"><strong>Description:</strong></td>
    <td colspan="3" style="border:1px solid black; padding:8px;">
      The test case verifies that the function correctly validates XML, KBL, and VEC files by checking their headers and returns an appropriate error if the header is missing, invalid, or malformed.
    </td>
  </tr>

  <tr>
    <th colspan="3" style="border:1px solid black; padding:8px; text-align:center;">
      Unit test
    </th>
  </tr>
  <tr>
    <th style="border:1px solid black; padding:8px; text-align:center;">Found in:</th>
    <td colspan="2" style="border:1px solid black; padding:8px; text-align:center;">/tests/utils/XMLValidator.test.ts</td>
  </tr>
</table>

### 5.2. TC02 Handle Error Messages MOD01

<table style="width:100%; border-collapse:collapse; font-family:Arial, sans-serif;">
  <tr>
    <th colspan="3" style="border:1px solid black; padding:8px; text-align:center;">
      Test case
    </th>
  </tr>
  <tr>
    <td style="border:1px solid black; padding:8px;"><strong>ID:</strong></td>
    <td colspan="3" style="border:1px solid black; padding:8px; ">&lt;TC02&gt;</td>
  </tr>
  <tr>
    <td style="border:1px solid black; padding:8px;"><strong>Name:</strong></td>
    <td colspan="3" style="border:1px solid black; padding:8px;">Handle Error Messages</td>
  </tr>
  <tr>
    <td style="border:1px solid black; padding:8px;"><strong>Req.-ID:</strong></td>
    <td colspan="3" style="border:1px solid black; padding:8px;">FR.01, FR.03</td>
  </tr>
  <tr>
    <td style="border:1px solid black; padding:8px;"><strong>Description:</strong></td>
    <td colspan="3" style="border:1px solid black; padding:8px;">
      The test case verifies that incorrect XML, KBL, and VEC files return consistent, accurate, and meaningful error messages.
    </td>
  </tr>

  <tr>
    <th colspan="3" style="border:1px solid black; padding:8px; text-align:center;">
      Test steps
    </th>
  </tr>
  <tr>
    <th style="border:1px solid black; padding:8px; ">Step</th>
    <th style="border:1px solid black; padding:8px; ">Action</th>
    <th style="border:1px solid black; padding:8px; ">Expected result</th>
  </tr>
  <tr>
    <td style="border:1px solid black; padding:8px;">1</td>
    <td style="border:1px solid black; padding:8px;">Click the "add Submodel Element" button within a Submodel</td>
    <td style="border:1px solid black; padding:8px;">A Dialog for the type of Element opens</td>
  </tr>
  <tr>
    <td style="border:1px solid black; padding:8px;">2</td>
    <td style="border:1px solid black; padding:8px;">
      Select file and click "next"
    </td>
    <td style="border:1px solid black; padding:8px;">
      A dialog for element details opens
    </td>
  </tr>
  <tr>
    <td style="border:1px solid black; padding:8px;">3</td>
    <td style="border:1px solid black; padding:8px;">
      Under "Value" click "file" and add a file in the file input.
    </td>
    <td style="border:1px solid black; padding:8px;">
      The file is added to the dialog, the ShortID is filled with the filename if empty. The MIME type is displayed correctly.
    </td>
  </tr>
  <tr>
    <td style="border:1px solid black; padding:8px;">4</td>
    <td style="border:1px solid black; padding:8px;">
      Click "save"
    </td>
    <td style="border:1px solid black; padding:8px;">
      If the file is invalid, the file input is marked in red and an error is shown. If valid, an element is created with the correct MIME type. 
    </td>
  </tr>
</table>

### 5.3. TC03 Display XML structure MOD02

<table style="width:100%; border-collapse:collapse; font-family:Arial, sans-serif;">
  <tr>
    <th colspan="3" style="border:1px solid black; padding:8px; text-align:center;">
      Test case
    </th>
  </tr>
  <tr>
    <td style="border:1px solid black; padding:8px;"><strong>ID:</strong></td>
    <td colspan="3" style="border:1px solid black; padding:8px; ">&lt;TC03&gt;</td>
  </tr>
  <tr>
    <td style="border:1px solid black; padding:8px;"><strong>Name:</strong></td>
    <td colspan="3" style="border:1px solid black; padding:8px;">Display XML structure</td>
  </tr>
  <tr>
    <td style="border:1px solid black; padding:8px;"><strong>Req.-ID:</strong></td>
    <td colspan="3" style="border:1px solid black; padding:8px;">FR.04</td>
  </tr>
  <tr>
    <td style="border:1px solid black; padding:8px;"><strong>Description:</strong></td>
    <td colspan="3" style="border:1px solid black; padding:8px;">
      The test case verifies that the XML structure is correctly represented as a table of contents and that selecting entries navigates to the corresponding XML sections accurately and consistently within the viewer.
    </td>
  </tr>

  <tr>
    <th colspan="3" style="border:1px solid black; padding:8px; text-align:center;">
      Test steps
    </th>
  </tr>
  <tr>
    <th style="border:1px solid black; padding:8px; ">Step</th>
    <th style="border:1px solid black; padding:8px; ">Action</th>
    <th style="border:1px solid black; padding:8px; ">Expected result</th>
  </tr>
  <tr>
    <td style="border:1px solid black; padding:8px;">1</td>
    <td style="border:1px solid black; padding:8px;">Choose a Submodel with a XML-type file element and open it.</td>
    <td style="border:1px solid black; padding:8px;">A list of elements in the Submodel is shown.</td>
  </tr>
  <tr>
    <td style="border:1px solid black; padding:8px;">2</td>
    <td style="border:1px solid black; padding:8px;">
      Click on the XML-type file.
    </td>
    <td style="border:1px solid black; padding:8px;">
      A detailed description of the Element opens on the right.
    </td>
  </tr>
  <tr>
    <td style="border:1px solid black; padding:8px;">3</td>
    <td style="border:1px solid black; padding:8px;">
      Click on "Visualization".
    </td>
    <td style="border:1px solid black; padding:8px;">
      The XML preview with a table of contents and the XML content opens.
    </td>
  </tr>
  <tr>
    <td style="border:1px solid black; padding:8px;">4</td>
    <td style="border:1px solid black; padding:8px;">
      Scroll the XML content.
    </td>
    <td style="border:1px solid black; padding:8px;">
      Only the XML content is scrolled.
    </td>
  </tr>
  <tr>
    <td style="border:1px solid black; padding:8px;">5</td>
    <td style="border:1px solid black; padding:8px;">
      Scroll the table of contents.
    </td>
    <td style="border:1px solid black; padding:8px;">
      Only the table of contents is scrolled.
    </td>
  </tr>
  <tr>
    <td style="border:1px solid black; padding:8px;">6</td>
    <td style="border:1px solid black; padding:8px;">
      In table of contents click on an entry.
    </td>
    <td style="border:1px solid black; padding:8px;">
      The XML content jumps to this entry and highlights the line.
    </td>
  </tr>
  <tr>
    <td style="border:1px solid black; padding:8px;">7</td>
    <td style="border:1px solid black; padding:8px;">
      In table of contents click on the triangle next to an entry.
    </td>
    <td style="border:1px solid black; padding:8px;">
      The inner XML structure is revealed and the XML Content does not jump to the entry.
    </td>
  </tr>
</table>

### 5.4. TC04 AAS-Creation-Wizard functions properly MOD03

<table style="width:100%; border-collapse:collapse; font-family:Arial, sans-serif;">
  <tr>
    <th colspan="3" style="border:1px solid black; padding:8px; text-align:center;">
      Test case
    </th>
  </tr>
  <tr>
    <td style="border:1px solid black; padding:8px;"><strong>ID:</strong></td>
    <td colspan="3" style="border:1px solid black; padding:8px; ">&lt;TC04&gt;</td>
  </tr>
  <tr>
    <td style="border:1px solid black; padding:8px;"><strong>Name:</strong></td>
    <td colspan="3" style="border:1px solid black; padding:8px;">AAS-Creation-Wizard functions properly</td>
  </tr>
  <tr>
    <td style="border:1px solid black; padding:8px;"><strong>Req.-ID:</strong></td>
    <td colspan="3" style="border:1px solid black; padding:8px;">FR.05</td>
  </tr>
  <tr>
    <td style="border:1px solid black; padding:8px;"><strong>Description:</strong></td>
    <td colspan="3" style="border:1px solid black; padding:8px;">
      The test case verifies that the creation wizard’s graphical interface correctly guides the user through the process, displaying appropriate inputs, navigation, and feedback when creating Asset Administration Shells from KBL or VEC files.
    </td>
  </tr>

  <tr>
    <th colspan="3" style="border:1px solid black; padding:8px; text-align:center;">
      Test steps
    </th>
  </tr>
  <tr>
    <th style="border:1px solid black; padding:8px; ">Step</th>
    <th style="border:1px solid black; padding:8px; ">Action</th>
    <th style="border:1px solid black; padding:8px; ">Expected result</th>
  </tr>
  <tr>
    <td style="border:1px solid black; padding:8px;">1</td>
    <td style="border:1px solid black; padding:8px;">On the slide for the Asset Administration Shells, click on the three dots and on "Create AAS form KBL/VEC"</td>
    <td style="border:1px solid black; padding:8px;">The wizard for the AAS creation opens</td>
  </tr>
  <tr>
    <td style="border:1px solid black; padding:8px;">2</td>
    <td style="border:1px solid black; padding:8px;">
      Cilck on the FileInput and choose a KBL or VEC file.
    </td>
    <td style="border:1px solid black; padding:8px;">
      Only eligable files can be choosen. The file is displayed.
    </td>
  </tr>
  <tr>
    <td style="border:1px solid black; padding:8px;">3</td>
    <td style="border:1px solid black; padding:8px;">
      Optionally choose a picture for the AAS in the second FileInput.
    </td>
    <td style="border:1px solid black; padding:8px;">
      Only eligable files can be choosen. The file is displayed.
    </td>
  </tr>
  <tr>
    <td style="border:1px solid black; padding:8px;">4</td>
    <td style="border:1px solid black; padding:8px;">
      Provide or generate AAS ID and Asset ID Fill. Optionally change general Information for the AAS that will be created
    </td>
    <td style="border:1px solid black; padding:8px;">
      The fields for the Information are easy to use and display the entered values. The "generate" button fills the corresponding textinput with a generated value.
    </td>
  </tr>
  <tr>
    <td style="border:1px solid black; padding:8px;">5</td>
    <td style="border:1px solid black; padding:8px;">
      Choose Information which should be used to fill the Submodels of the AAS. 
    </td>
    <td style="border:1px solid black; padding:8px;">
      Individual Information can be selected or deselected.
    </td>
  </tr>
  <tr>
    <td style="border:1px solid black; padding:8px;">6</td>
    <td style="border:1px solid black; padding:8px;">
      Click "Create"
    </td>
    <td style="border:1px solid black; padding:8px;">
      The AAS is created with the provided Information.
    </td>
  </tr>
</table>

### 5.5. TC05 Extraction of the AAS Information MOD03

<table style="width:100%; border-collapse:collapse; font-family:Arial, sans-serif;">
  <tr>
    <th colspan="3" style="border:1px solid black; padding:8px; text-align:center;">
      Test case
    </th>
  </tr>
  <tr>
    <td style="border:1px solid black; padding:8px;"><strong>ID:</strong></td>
    <td colspan="3" style="border:1px solid black; padding:8px; ">&lt;TC05&gt;</td>
  </tr>
  <tr>
    <td style="border:1px solid black; padding:8px;"><strong>Name:</strong></td>
    <td colspan="3" style="border:1px solid black; padding:8px;">Extraction of the AAS Information</td>
  </tr>
  <tr>
    <td style="border:1px solid black; padding:8px;"><strong>Req.-ID:</strong></td>
    <td colspan="3" style="border:1px solid black; padding:8px;">FR.06</td>
  </tr>
  <tr>
    <td style="border:1px solid black; padding:8px;"><strong>Description:</strong></td>
    <td colspan="3" style="border:1px solid black; padding:8px;">
The test case verifies that AAS information is correctly extracted from a given file, ensuring all relevant elements are accurately identified, parsed, and made available for further processing.</td>
  </tr>

  <tr>
    <th colspan="3" style="border:1px solid black; padding:8px; text-align:center;">
      Unit Tests
    </th>
  </tr>
  <tr>
  <th style="border:1px solid black; padding:8px; text-align:center;">
    Found in:
  </th>
  <td colspan="2" style="border:1px solid black; padding:8px; text-align:center;">
  /tests/utils/KblVecUtils/KblVecDataPointTreeUtils.test.ts<br>
  /tests/utils/KblVecUtils/KblVecRequiredFieldUtils.test.ts<br>
  /tests/utils/KblVecUtils/KblVecSubmodelGenerationUtils.test.ts
  </td>
  </tr>
</table>



### 6. Test Data
The test data consists of various files located in the '/Testfiles' folder. The test data includes data structures composed of shortened KBL and VEC files. Structural defects are included within otherwise valid structures.

<table>
  <tr>
    <th colspan="2" style="border:1px solid black; padding:8px; text-align:center;">
      Test data:
    </th>
  </tr>
  <tr>
    <th style="border:1px solid black; padding:8px; ">Dataset</th>
    <th style="border:1px solid black; padding:8px; ">Data</th>  </tr>
  <tr>
    <td style="border:1px solid black; padding:8px;">1</td>
    <td style="border:1px solid black; padding:8px;">kbl_noheader.kbl</td>
  </tr>
  <tr>
    <td style="border:1px solid black; padding:8px;">2</td>
    <td style="border:1px solid black; padding:8px;">kbl_vec_inside.kbl
    </td>
  </tr>
  <tr>
    <td style="border:1px solid black; padding:8px;">3</td>
    <td style="border:1px solid black; padding:8px;">
      kbl_normal.kbl
    </td>
  </tr>
  <tr>
    <td style="border:1px solid black; padding:8px;">4</td>
    <td style="border:1px solid black; padding:8px;">
      kbl_faultykbl.kbl
    </td>
  </tr>
  <tr>
    <td style="border:1px solid black; padding:8px;">5</td>
    <td style="border:1px solid black; padding:8px;">
      kbl_faultyxml.kbl
    </td>
  </tr>
  <tr>
    <td style="border:1px solid black; padding:8px;">6</td>
    <td style="border:1px solid black; padding:8px;">
      kbl_nokbl.kbl
    </td>
  </tr>
  <tr>
    <td style="border:1px solid black; padding:8px;">7</td>
    <td style="border:1px solid black; padding:8px;">
      kbl_xml.xml
    </td>
  </tr>
  <tr>
    <td style="border:1px solid black; padding:8px;">8</td>
    <td style="border:1px solid black; padding:8px;">
      kbl_vec.vec
    </td>
  </tr>
  <tr>
    <td style="border:1px solid black; padding:8px;">9</td>
    <td style="border:1px solid black; padding:8px;">
      vec_normal.vec
    </td>
  </tr>
  <tr>
    <td style="border:1px solid black; padding:8px;">10</td>
    <td style="border:1px solid black; padding:8px;">
      vec_kbl.kbl
    </td>
  </tr>
  <tr>
    <td style="border:1px solid black; padding:8px;">11</td>
    <td style="border:1px solid black; padding:8px;">
      vec_endkbl.kbl
    </td>
  </tr>
  <tr>
    <td style="border:1px solid black; padding:8px;">12</td>
    <td style="border:1px solid black; padding:8px;">
      vec_noversion.vec
    </td>
  </tr>
  <tr>
    <td style="border:1px solid black; padding:8px;">13</td>
    <td style="border:1px solid black; padding:8px;">
      vec_kbl_inside.vec
    </td>
  </tr>
  <tr>
    <td style="border:1px solid black; padding:8px;">14</td>
    <td style="border:1px solid black; padding:8px;">
      missing_close.vec
    </td>
  </tr>
</table>