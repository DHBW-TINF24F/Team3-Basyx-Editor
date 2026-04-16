# System Test Plan
## Team3-Basyx-Editor

## Version Control

|Version|Date|Author|Comment|
|-----|-----------|------------|---------------------|
|1.0|16.10.2026|Daniel Ziegler|Version 1.0|
|1.1|Date|Name|Comment1|
|1.2|Date|Name|Comment2|
|1.3|Date|Name|Comment3|
|1.4|Date|Name|Comment4|

## Table of contents
1. [Introduction](#1-scope)
2. [Scope](#2)
3. [Definitions and Acronymes](#)
3. [Test Strategy](#3)
4. [Test Environment](#4)
    - 4.1 [Hardware Environment](#)
    - 4.2 [Software Environment](#)
    - 4.3 [Deployment Setup](#)
5. [Test Cases](#5)
    - 5.1
    - 5.2
    - 5.3
    - 5.4 
    - 5.5
    - 5.6
6. [Test Data](#6)


##dynamische Tests, keine statischen Tests, -> unit tests

## 1 Introduction
The purpose of this System Test Plan (STP) is to define the overall testing approach for the BaSyx Editor Extension.
It describes the test strategy, environment, test cases, and acceptance criteria required to verify that the system fulfills the requirements specified in the Software Architecture Specification (SAS).
## 2 Scope
This document covers testing of the changes planed in the BaSyx Editor Extension including:<br>
-MOD01 – File Import and Validation Subsystem<br>
-MOD02 – XML Viewer and Navigation Subsystem<br>
-MOD03 – AAS Generation and Submodel Mapping Subsystem<br>
-MOD04 – Targeted Data Retrieval Subsystem<br>
This document does not cover:<br>
-Unit testing of slight changes to already existing code<br>
-Internal BaSyx backend functionality<br>
## 3 Test Strategy
The testing strategy for the BaSyx Editor Extension ensures reliable validation of all added system functionalities through a structured and requirement-driven approach. A key objective is to achieve wide test coverage.  Both positive and negative scenarios, including edge cases are considered to verify system robustness.

Testing is performed using a function isolation approach, where individual functionalities are tested independently. This improves defect detection and simplifies root cause analysis.

To validate requirements effectively, both file-based and code-based testing are applied. File-based testing uses input data (e.g., XML, KBL, VEC files) to verify the import, parsing, and visualization processes. Code-based testing uses Vitest, the existing testing environment the Basyx software uses, to ensure reliable, automated unit and integration test execution. 

This approach ensures a comprehensive, traceable, and efficient validation of the system.
## 4 Test Environment
--noch md formatten / vielleicht auch noch umschreiben--
### 4.1 Hardware Environment
Client machine (modern browser-capable system)
### 4.2 Software Environment
Browser: Chrome, Firefox, Edge
Frontend: Vue.js application
Backend services:
BaSyx Registry
BaSyx AAS Repository
BaSyx Submodel Service
### 4.3 Deployment Setup
Docker-based deployment setup

## 5 Test Cases Overview
--Für steps einen Standartausgang definieren (Basyx Editor offen und eine AAS geöffnet)--
--normalerweise den kasten, aber bei unit tests auf den code verweisen, statt ausführungteil--
Test ID	Description	Related Module	Requirement
TC01	Proper XML-Validation	MOD01	FR.01
TC02	Handle Error Messages	MOD01	FR.02
TC03	Display XML structure	MOD02	FR.05
TC04	Generate AAS from KBL	MOD03	FR.02
TC05	Query specific data via API	MOD04	FR.04
TC06	Handle missing resource error	MOD04	FR.06
### 5.1 TC01    Proper XML-Validation	MOD01	FR.01
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
    <td colspan="3" style="border:1px solid black; padding:8px;">6000</td>
  </tr>
  <tr>
    <td style="border:1px solid black; padding:8px;"><strong>Description:</strong></td>
    <td colspan="3" style="border:1px solid black; padding:8px;">
      The test case verifies that the function correctly validates XML, KBL, and VEC files by checking their headers and returns an appropriate error when the header is missing, invalid, or malformed.
    </td>
  </tr>

  <tr>
    <th colspan="3" style="border:1px solid black; padding:8px; text-align:center;">
      Unit test
    </th>
  </tr>
  <tr>
    <th style="border:1px solid black; padding:8px; text-align:center;">Found in:</th>
    <td colspan="2" style="border:1px solid black; padding:8px; text-align:center;">src/........</td>
  </tr>
</table>

### 5.2 TC02	Handle Error Messages	MOD01	FR.01

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
    <td colspan="3" style="border:1px solid black; padding:8px;">6000</td>
  </tr>
  <tr>
    <td style="border:1px solid black; padding:8px;"><strong>Description:</strong></td>
    <td colspan="3" style="border:1px solid black; padding:8px;">
      The test case verifies that incorrect XML, KBL, and VEC files return an error with consistent, accurate, and meaningful error responses.
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
    <td style="border:1px solid black; padding:8px;">Click the add Element button within a Submodel</td>
    <td style="border:1px solid black; padding:8px;">A Dialog for the type of Element opens</td>
  </tr>
  <tr>
    <td style="border:1px solid black; padding:8px;">2</td>
    <td style="border:1px solid black; padding:8px;">
      Select file and click next
    </td>
    <td style="border:1px solid black; padding:8px;">
      A Dialog for Element-Details opens
    </td>
  </tr>
  <tr>
    <td style="border:1px solid black; padding:8px;">3</td>
    <td style="border:1px solid black; padding:8px;">
      Under Value click file and add a file in the fileinput.
    </td>
    <td style="border:1px solid black; padding:8px;">
      The file is added into the Dialog, the ShortID is filled with the filename if empty
    </td>
  </tr>
  <tr>
    <td style="border:1px solid black; padding:8px;">3</td>
    <td style="border:1px solid black; padding:8px;">
      Click save
    </td>
    <td style="border:1px solid black; padding:8px;">
      If the file is faulty, the fileinput is marked in red and an error is shown
    </td>
  </tr>
</table>

### 5.3 TC03	Display XML structure	MOD02	FR.05

<table style="width:100%; border-collapse:collapse; font-family:Arial, sans-serif;">
  <tr>
    <th colspan="3" style="border:1px solid black; padding:8px; text-align:center;">
      Test case
    </th>
  </tr>
  <tr>
    <td style="border:1px solid black; padding:8px;"><strong>ID:</strong></td>
    <td colspan="3" style="border:1px solid black; padding:8px; ">&lt;8000&gt;</td>
  </tr>
  <tr>
    <td style="border:1px solid black; padding:8px;"><strong>Name:</strong></td>
    <td colspan="3" style="border:1px solid black; padding:8px;">7000</td>
  </tr>
  <tr>
    <td style="border:1px solid black; padding:8px;"><strong>Req.-ID:</strong></td>
    <td colspan="3" style="border:1px solid black; padding:8px;">6000</td>
  </tr>
  <tr>
    <td style="border:1px solid black; padding:8px;"><strong>Description:</strong></td>
    <td colspan="3" style="border:1px solid black; padding:8px;">
      5000
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
    <td style="border:1px solid black; padding:8px;">4000</td>
    <td style="border:1px solid black; padding:8px;">3000</td>
  </tr>
  <tr>
    <td style="border:1px solid black; padding:8px;">2</td>
    <td style="border:1px solid black; padding:8px;">
      2000
    </td>
    <td style="border:1px solid black; padding:8px;">
      1000
    </td>
  </tr>
</table>

### 5.4 TC04	AAS-Creation-Wizard functions properly	MOD03	FR.02

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
    <td colspan="3" style="border:1px solid black; padding:8px;">6000</td>
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
    <td style="border:1px solid black; padding:8px;">On the slide for the administration shells, click on the three dots and on "Create AAS form KBL/VEC"</td>
    <td style="border:1px solid black; padding:8px;">The wizard for the AAS-Creation opens</td>
  </tr>
  <tr>
    <td style="border:1px solid black; padding:8px;">2</td>
    <td style="border:1px solid black; padding:8px;">
      Cilck on the FileInput and choose a KBL or VEC file.
    </td>
    <td style="border:1px solid black; padding:8px;">
      Only eligable files can be choosen. The file is displayed --weiterführen mit genaueren details--
    </td>
  </tr>
  <tr>
    <td style="border:1px solid black; padding:8px;">4</td>
    <td style="border:1px solid black; padding:8px;">
      Optionally choose a picture for the AAS in the second FileInput
    </td>
    <td style="border:1px solid black; padding:8px;">
      Only eligable files can be choosen. The file is displayed
    </td>
  </tr>
  <tr>
    <td style="border:1px solid black; padding:8px;">4</td>
    <td style="border:1px solid black; padding:8px;">
      Optionally fill in some general Information on the AAS, that will be created
    </td>
    <td style="border:1px solid black; padding:8px;">
      The fields for the Information are easy to interact with and display the Information
    </td>
  </tr>
  <tr>
    <td style="border:1px solid black; padding:8px;">5</td>
    <td style="border:1px solid black; padding:8px;">
      Click "Create"
    </td>
    <td style="border:1px solid black; padding:8px;">
      The AAS is created with the given Information.
    </td>
  </tr>
</table>

### 5.5 TC05	Mapping of the AAS Structure	MOD04	FR.04

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
    <td colspan="3" style="border:1px solid black; padding:8px;">Mapping of the AAS Structure</td>
  </tr>
  <tr>
    <td style="border:1px solid black; padding:8px;"><strong>Req.-ID:</strong></td>
    <td colspan="3" style="border:1px solid black; padding:8px;">6000</td>
  </tr>
  <tr>
    <td style="border:1px solid black; padding:8px;"><strong>Description:</strong></td>
    <td colspan="3" style="border:1px solid black; padding:8px;">
The test case verifies that the AAS is correctly formed from KBL and VEC files, ensuring proper structure, data mapping, and successful output without errors.    </td>
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
  /src/...
  </td>
  </tr>
</table>

### 5.6 TC06	Handle missing resource error	MOD04	FR.06

<table style="width:100%; border-collapse:collapse; font-family:Arial, sans-serif;">
  <tr>
    <th colspan="3" style="border:1px solid black; padding:8px; text-align:center;">
      Test case
    </th>
  </tr>
  <tr>
    <td style="border:1px solid black; padding:8px;"><strong>ID:</strong></td>
    <td colspan="3" style="border:1px solid black; padding:8px; ">&lt;8000&gt;</td>
  </tr>
  <tr>
    <td style="border:1px solid black; padding:8px;"><strong>Name:</strong></td>
    <td colspan="3" style="border:1px solid black; padding:8px;">7000</td>
  </tr>
  <tr>
    <td style="border:1px solid black; padding:8px;"><strong>Req.-ID:</strong></td>
    <td colspan="3" style="border:1px solid black; padding:8px;">6000</td>
  </tr>
  <tr>
    <td style="border:1px solid black; padding:8px;"><strong>Description:</strong></td>
    <td colspan="3" style="border:1px solid black; padding:8px;">
      5000
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
    <td style="border:1px solid black; padding:8px;">4000</td>
    <td style="border:1px solid black; padding:8px;">3000</td>
  </tr>
  <tr>
    <td style="border:1px solid black; padding:8px;">2</td>
    <td style="border:1px solid black; padding:8px;">
      2000
    </td>
    <td style="border:1px solid black; padding:8px;">
      1000
    </td>
  </tr>
</table>


### 6 Test Data