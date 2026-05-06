# System Test Plan
## Team3-Basyx-Editor

## Version Control

|Version|Date|Author|Comment|
|-----|-----------|------------|---------------------|
|1.0|05.05.2026|Daniel Ziegler|Version 1.0|
|1.1|06.05.2026|Daniel Ziegler|fix table of contents|
|1.2|06.05.2026|Daniel Ziegler|Added test results|

## Table of contents
1. [Introduction](#1-introduction)
2. [Scope](#2-scope)
3. [Results of Test Cases](#3-results-of-test-cases)
    - 3.1 [TC01	Proper XML-Validation	MOD01](#31-tc01-proper-xml-validation-mod01)
    - 3.2 [TC02	Handle Error Messages	MOD01](#32-tc02-handle-error-messages-mod01)
    - 3.3 [TC03	Display XML structure	MOD02](#33-tc03-display-xml-structure-mod02)
    - 3.4 [TC04	AAS-Creation-Wizard functions properly	MOD03](#34-tc04-aas-creation-wizard-functions-properly-mod03)
    - 3.5 [TC05	Extraction of Information for AAS-Generation MOD03](#35-tc05-extraction-of-information-for-aas-generation-mod03)


## 1. Introduction
This System Test Report (STR) documents the results of the system testing activities conducted for the BaSyx Editor Extension. The testing process was performed in accordance with the defined System Test Plan (STP) and aimed to verify that the implemented functionality meets the requirements specified in the Software Architecture Specification (SAS).

## 2. Scope
The scope of this report includes the evaluation of the following subsystems:

* MOD01 – File Import and Validation Subsystem
* MOD02 – XML Viewer and Navigation Subsystem
* MOD03 – AAS Generation and Submodel Mapping Subsystem

As defined in the STP, this report does not include results related to unit testing of minor code changes or internal BaSyx backend functionality.

## 3 Results of Test Cases

### 3.1. TC01 Proper XML-Validation MOD01
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


<table style=" border-collapse:collapse; font-family:Arial, sans-serif;">
  <tr>
    <td style="border:1px solid black; padding:8px;"><strong>Tester:</strong></td>
    <td colspan="2" style="border:1px solid black; padding:8px; ">Daniel Ziegler</td>
  </tr>
    <tr>
    <td style="border:1px solid black; padding:8px;"><strong>Date:</strong></td>
    <td colspan="2" style="border:1px solid black; padding:8px; ">06.05.2026</td>
  </tr>
    <tr>
    <td style="border:1px solid black; padding:8px;"><strong>Test result:</strong></td>
    <td colspan="2" style="border:1px solid black; padding:8px; ">PASSED</td>
  </tr>
</table>

### 3.2. TC02 Handle Error Messages MOD01

<table style="width:100%; border-collapse:collapse; font-family:Arial, sans-serif;">
  <tr>
    <th colspan="4" style="border:1px solid black; padding:8px; text-align:center;">
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
    <th colspan="4" style="border:1px solid black; padding:8px; text-align:center;">
      Test steps
    </th>
  </tr>
  <tr>
    <th style="border:1px solid black; padding:8px; ">Step</th>
    <th style="border:1px solid black; padding:8px; ">Action</th>
    <th style="border:1px solid black; padding:8px; ">Expected result</th>
    <th style="border:1px solid black; padding:8px; ">Actual result</th>
  </tr>
  <tr>
    <td style="border:1px solid black; padding:8px;">1</td>
    <td style="border:1px solid black; padding:8px;">Click the "add Submodel Element (+)" button within a Submodel</td>
    <td style="border:1px solid black; padding:8px;">A Dialog for the type of Element opens</td>
    <td style="border:1px solid black; padding:8px;">A dialog for selecting the element type appears</td>
  </tr>
  <tr>
    <td style="border:1px solid black; padding:8px;">2</td>
    <td style="border:1px solid black; padding:8px;">
      Select "file" and click "next"
    </td>
    <td style="border:1px solid black; padding:8px;">
      A dialog for element details opens
    </td>
    <td style="border:1px solid black; padding:8px;">A dialog for element details appears.</td>
  </tr>
  <tr>
    <td style="border:1px solid black; padding:8px;">3</td>
    <td style="border:1px solid black; padding:8px;">
      Under "Value" click "file" and add a file in the file input.
    </td>
    <td style="border:1px solid black; padding:8px;">
      The file is added to the dialog, the ShortID is filled with the filename if empty. The MIME type is displayed correctly.
    </td>
    <td style="border:1px solid black; padding:8px;">The selected file is added to the dialog, the ShortID is automatically populated and the MIME type is displayed correctly.</td>
  </tr>
  <tr>
    <td style="border:1px solid black; padding:8px;">4</td>
    <td style="border:1px solid black; padding:8px;">
      Optionally change other values including the ShortID
    </td>
    <td style="border:1px solid black; padding:8px;">
      The changes are displayed
    </td>
    <td style="border:1px solid black; padding:8px;">The Changes are displayed</td>
  </tr>
  <tr>
    <td style="border:1px solid black; padding:8px;">4</td>
    <td style="border:1px solid black; padding:8px;">
      Click "save"
    </td>
    <td style="border:1px solid black; padding:8px;">
      If the file is invalid, the file input is marked in red and an error is shown. If valid, an element is created with the correct MIME type. 
    </td>
    <td style="border:1px solid black; padding:8px;">For invalid files they are marked in red and an error is shown. For valid files an element with the correct MIME type is created.</td>
  </tr>
</table>

<table style=" border-collapse:collapse; font-family:Arial, sans-serif;">
  <tr>
    <th style="border:1px solid black; padding:8px;">Dataset:</th>
    <th  style="border:1px solid black; padding:8px; ">Expected Result:</th>
    <th  style="border:1px solid black; padding:8px; ">Actual Result:</th>
  </tr>
  <tr>
    <td style="border:1px solid black; padding:4px;">1</td>
    <td  style="border:1px solid black; padding:4px; ">No error</td>
    <td  style="border:1px solid black; padding:4px; ">No error</td>
  </tr>
  <tr>
    <td style="border:1px solid black; padding:4px;">2</td>
    <td  style="border:1px solid black; padding:4px; ">No Error</td>
    <td  style="border:1px solid black; padding:4px; ">No Error</td>
  </tr>
  <tr>
    <td style="border:1px solid black; padding:4px;">3</td>
    <td  style="border:1px solid black; padding:4px; ">No Error</td>
    <td  style="border:1px solid black; padding:4px; ">No Error</td>
  </tr>
  <tr>
    <td style="border:1px solid black; padding:4px;">4</td>
    <td  style="border:1px solid black; padding:4px; ">No error</td>
    <td  style="border:1px solid black; padding:4px; ">No error</td>
  </tr>
  <tr>
    <td style="border:1px solid black; padding:4px;">5</td>
    <td  style="border:1px solid black; padding:4px; ">Error: XML is not well-formed.</td>
    <td  style="border:1px solid black; padding:4px; ">Error: XML is not well-formed.</td>
  </tr>
  <tr>
    <td style="border:1px solid black; padding:4px;">6</td>
    <td  style="border:1px solid black; padding:4px; ">Error: XML is not well-formed.</td>
    <td  style="border:1px solid black; padding:4px; ">Error: XML is not well-formed.</td>
  </tr>
  <tr>
    <td style="border:1px solid black; padding:4px;">7</td>
    <td  style="border:1px solid black; padding:4px; ">Error: XML header is missing.</td>
    <td  style="border:1px solid black; padding:4px; ">Error: XML header is missing.</td>
  </tr>
  <tr>
    <td style="border:1px solid black; padding:4px;">8</td>
    <td  style="border:1px solid black; padding:4px; ">Error: XML is not well-formed.</td>
    <td  style="border:1px solid black; padding:4px; ">Error: XML is not well-formed.</td>
  </tr>
  <tr>
    <td style="border:1px solid black; padding:4px;">9</td>
    <td  style="border:1px solid black; padding:4px; ">Error: KBL_container is not a valid root element for .vec files.</td>
    <td  style="border:1px solid black; padding:4px; ">Error: KBL_container is not a valid root element for .vec files.</td>
  </tr>
  <tr>
    <td style="border:1px solid black; padding:4px;">10</td>
    <td  style="border:1px solid black; padding:4px; ">No Error</td>
    <td  style="border:1px solid black; padding:4px; ">No Error</td>
  </tr>
  <tr>
    <td style="border:1px solid black; padding:4px;">11</td>
    <td  style="border:1px solid black; padding:4px; ">No Error</td>
    <td  style="border:1px solid black; padding:4px; ">No Error</td>
  </tr>
  <tr>
    <td style="border:1px solid black; padding:4px;">12</td>
    <td  style="border:1px solid black; padding:4px; ">Error: XML is not well-formed.</td>
    <td  style="border:1px solid black; padding:4px; ">Error: XML is not well-formed.</td>
  </tr>
  <tr>
    <td style="border:1px solid black; padding:4px;">13</td>
    <td  style="border:1px solid black; padding:4px; ">Error: XML is not well-formed.</td>
    <td  style="border:1px solid black; padding:4px; ">Error: XML is not well-formed.</td>
  </tr>
  <tr>
    <td style="border:1px solid black; padding:4px;">14</td>
    <td  style="border:1px solid black; padding:4px; ">Error: VecContent is not a valid root element for .kbl files.</td>
    <td  style="border:1px solid black; padding:4px; ">Error: VecContent is not a valid root element for .kbl files.</td>
  </tr>
  <tr>
    <td style="border:1px solid black; padding:4px;">15</td>
    <td  style="border:1px solid black; padding:4px; ">No Error</td>
    <td  style="border:1px solid black; padding:4px; ">No Error</td>
  </tr>
  <tr>
    <td style="border:1px solid black; padding:4px;">16</td>
    <td  style="border:1px solid black; padding:4px; ">No Error</td>
    <td  style="border:1px solid black; padding:4px; ">No Error</td>
  </tr>
  <tr>
    <td colspan="3" style="border:1px solid black; padding:8px; "></td>
  </tr>
  <tr>
    <td style="border:1px solid black; padding:8px;"><strong>Tester:</strong></td>
    <td colspan="2" style="border:1px solid black; padding:8px; ">Daniel Ziegler</td>
  </tr>
  
  <tr>
    <td style="border:1px solid black; padding:8px;"><strong>Date:</strong></td>
    <td colspan="2" style="border:1px solid black; padding:8px; ">06.05.2026</td>
  </tr>
  <tr>
    <td style="border:1px solid black; padding:8px;"><strong>Test result:</strong></td>
    <td colspan="2" style="border:1px solid black; padding:8px; ">PASSED</td>
  </tr>
</table>

### 3.3. TC03 Display XML structure MOD02

<table style="width:100%; border-collapse:collapse; font-family:Arial, sans-serif;">
  <tr>
    <th colspan="4" style="border:1px solid black; padding:8px; text-align:center;">
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
    <th colspan="4" style="border:1px solid black; padding:8px; text-align:center;">
      Test steps
    </th>
  </tr>
  <tr>
    <th style="border:1px solid black; padding:8px; ">Step</th>
    <th style="border:1px solid black; padding:8px; ">Action</th>
    <th style="border:1px solid black; padding:8px; ">Expected result</th>
    <th style="border:1px solid black; padding:8px; ">Actual result</th>
  </tr>
  <tr>
    <td style="border:1px solid black; padding:8px;">1</td>
    <td style="border:1px solid black; padding:8px;">Choose a Submodel with a XML-type file element and open it.</td>
    <td style="border:1px solid black; padding:8px;">A list of elements in the Submodel is shown.</td>
    <td style="border:1px solid black; padding:8px;">A list of elements in the Submodel is displayed.</td>
  </tr>
  <tr>
    <td style="border:1px solid black; padding:8px;">2</td>
    <td style="border:1px solid black; padding:8px;">
      Click on the XML-type file.
    </td>
    <td style="border:1px solid black; padding:8px;">
      A detailed description of the Element opens on the right.
    </td>
    <td style="border:1px solid black; padding:8px;">A detailed description of the Element appears on the right.</td>
  </tr>
  <tr>
    <td style="border:1px solid black; padding:8px;">3</td>
    <td style="border:1px solid black; padding:8px;">
      Click on "Visualization".
    </td>
    <td style="border:1px solid black; padding:8px;">
      The XML preview with a table of contents and the XML content opens.
    </td>
    <td style="border:1px solid black; padding:8px;">The XML preview with a table of contents and the XML content is displayed.</td>
  </tr>
  <tr>
    <td style="border:1px solid black; padding:8px;">4</td>
    <td style="border:1px solid black; padding:8px;">
      Scroll the XML content.
    </td>
    <td style="border:1px solid black; padding:8px;">
      Only the XML content is scrolled.
    </td>
    <td style="border:1px solid black; padding:8px;">Only the XML content scrolls.</td>
  </tr>
  <tr>
    <td style="border:1px solid black; padding:8px;">5</td>
    <td style="border:1px solid black; padding:8px;">
      Scroll the table of contents.
    </td>
    <td style="border:1px solid black; padding:8px;">
      Only the table of contents is scrolled.
    </td>
    <td style="border:1px solid black; padding:8px;">Only the table of contents scrolls.</td>
  </tr>
  <tr>
    <td style="border:1px solid black; padding:8px;">6</td>
    <td style="border:1px solid black; padding:8px;">
      In table of contents click on an entry.
    </td>
    <td style="border:1px solid black; padding:8px;">
      The XML content jumps to this entry and highlights the line.
    </td>
    <td style="border:1px solid black; padding:8px;">The XML content jumps to the selected entry and highlights the line.</td>
  </tr>
  <tr>
    <td style="border:1px solid black; padding:8px;">7</td>
    <td style="border:1px solid black; padding:8px;">
      In table of contents click on the triangle next to an entry.
    </td>
    <td style="border:1px solid black; padding:8px;">
      The inner XML structure is revealed and the XML Content does not jump to the entry.
    </td>
    <td style="border:1px solid black; padding:8px;">The inner XML structure is revealed and the XML Content does not jump to the entry.</td>
  </tr>
</table>

<table style=" border-collapse:collapse; font-family:Arial, sans-serif;">
  <tr>
    <th style="border:1px solid black; padding:8px;">Dataset:</th>
    <th style="border:1px solid black; padding:8px; ">Expected Result:</th>
    <th style="border:1px solid black; padding:8px; ">Actual Result:</th>
  </tr>
  <tr>
    <td style="border:1px solid black; padding:4px;">1</td>
    <td style="border:1px solid black; padding:4px; ">The Visualisation works</td>
    <td style="border:1px solid black; padding:4px; ">The Visualisation works</td>
  </tr>
  <tr>
    <td style="border:1px solid black; padding:4px;">2</td>
    <td style="border:1px solid black; padding:4px; ">The Visualisation works</td>
    <td style="border:1px solid black; padding:4px; ">The Visualisation works</td>
  </tr>
  <tr>
    <td style="border:1px solid black; padding:4px;">3</td>
    <td style="border:1px solid black; padding:4px; ">The Visualisation works</td>
    <td style="border:1px solid black; padding:4px; ">The Visualisation works</td>
  </tr>
  <tr>
    <td style="border:1px solid black; padding:4px;">4</td>
    <td style="border:1px solid black; padding:4px; ">The Visualisation works</td>
    <td style="border:1px solid black; padding:4px; ">The Visualisation works</td>
  </tr>
  <tr>
    <td colspan="3" style="border:1px solid black; padding:8px; "></td>
  </tr>
  <tr>
    <td style="border:1px solid black; padding:8px;"><strong>Tester:</strong></td>
    <td colspan="2" style="border:1px solid black; padding:8px; ">Daniel Ziegler</td>
  </tr>
    <tr>
    <td style="border:1px solid black; padding:8px;"><strong>Date:</strong></td>
    <td colspan="2" style="border:1px solid black; padding:8px; ">06.05.2026</td>
  </tr>
    <tr>
    <td style="border:1px solid black; padding:8px;"><strong>Test result:</strong></td>
    <td colspan="2" style="border:1px solid black; padding:8px; ">PASSED</td>
  </tr>
</table>

### 3.4. TC04 AAS-Creation-Wizard functions properly MOD03

<table style="width:100%; border-collapse:collapse; font-family:Arial, sans-serif;">
  <tr>
    <th colspan="4" style="border:1px solid black; padding:8px; text-align:center;">
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
    <th colspan="4" style="border:1px solid black; padding:8px; text-align:center;">
      Test steps
    </th>
  </tr>
  <tr>
    <th style="border:1px solid black; padding:8px; ">Step</th>
    <th style="border:1px solid black; padding:8px; ">Action</th>
    <th style="border:1px solid black; padding:8px; ">Expected result</th>
    <th style="border:1px solid black; padding:8px; ">Actual result</th>
  </tr>
  <tr>
    <td style="border:1px solid black; padding:8px;">1</td>
    <td style="border:1px solid black; padding:8px;">On the slide for the Asset Administration Shells, click on the three dots and on "Create AAS form KBL/VEC"</td>
    <td style="border:1px solid black; padding:8px;">The wizard for the AAS creation opens</td>
    <td style="border:1px solid black; padding:8px;">The wizard for the AAS creation appears</td>
  </tr>
  <tr>
    <td style="border:1px solid black; padding:8px;">2</td>
    <td style="border:1px solid black; padding:8px;">
      Cilck on the FileInput and choose a KBL or VEC file.
    </td>
    <td style="border:1px solid black; padding:8px;">
      Only eligable files can be choosen. The file is displayed.
    </td>
    <td style="border:1px solid black; padding:8px;">The file is displayed.</td>
  </tr>
  <tr>
    <td style="border:1px solid black; padding:8px;">3</td>
    <td style="border:1px solid black; padding:8px;">
      Optionally choose a picture for the AAS in the second FileInput.
    </td>
    <td style="border:1px solid black; padding:8px;">
      Only eligable files can be choosen. The file is displayed.
    </td>
    <td style="border:1px solid black; padding:8px;">The file is displayed.</td>
  </tr>
  <tr>
    <td style="border:1px solid black; padding:8px;">4</td>
    <td style="border:1px solid black; padding:8px;">
      Provide or generate AAS ID and Asset ID and Type. Optionally change general Information for the AAS that will be created
    </td>
    <td style="border:1px solid black; padding:8px;">
      The fields for the Information are easy to use and display the entered values. The "generate" button fills the corresponding textinput with a generated value.
    </td>
    <td style="border:1px solid black; padding:8px;">When pressing "generate" the corresponding textinput fills.</td>
  </tr>
  <tr>
    <td style="border:1px solid black; padding:8px;">5</td>
    <td style="border:1px solid black; padding:8px;">
      Choose Information which should be used to fill the Submodels of the AAS. 
    </td>
    <td style="border:1px solid black; padding:8px;">
      Individual Information can be selected or deselected.
    </td>
    <td style="border:1px solid black; padding:8px;">Individual Information can be selected or deselected.</td>
  </tr>
  <tr>
    <td style="border:1px solid black; padding:8px;">6</td>
    <td style="border:1px solid black; padding:8px;">
      Click "Create"
    </td>
    <td style="border:1px solid black; padding:8px;">
      The AAS is created with the provided Information.
    </td>
    <td style="border:1px solid black; padding:8px;">The AAS is created using the provided information.</td>
  </tr>
</table>

<table style=" border-collapse:collapse; font-family:Arial, sans-serif;">
  <tr>
    <th style="border:1px solid black; padding:8px;">Dataset:</th>
    <th style="border:1px solid black; padding:8px; ">Expected Result:</th>
    <th style="border:1px solid black; padding:8px; ">Actual Result:</th>
  </tr>
  <tr>
    <td style="border:1px solid black; padding:4px;">1</td>
    <td style="border:1px solid black; padding:4px; ">The corresponding AAS is created</td>
    <td style="border:1px solid black; padding:4px; ">The corresponding AAS is created</td>
  </tr>
  <tr>
    <td style="border:1px solid black; padding:4px;">3</td>
    <td style="border:1px solid black; padding:4px; ">The corresponding AAS is created</td>
    <td style="border:1px solid black; padding:4px; ">The corresponding AAS is created</td>
  </tr>
  <tr>
    <td colspan="3" style="border:1px solid black; padding:8px; "></td>
  </tr>
  <tr>
    <td style="border:1px solid black; padding:8px;"><strong>Tester:</strong></td>
    <td colspan="2" style="border:1px solid black; padding:8px; ">Daniel Ziegler</td>
  </tr>
    <tr>
    <td style="border:1px solid black; padding:8px;"><strong>Date:</strong></td>
    <td colspan="2" style="border:1px solid black; padding:8px; ">06.05.2026</td>
  </tr>
    <tr>
    <td style="border:1px solid black; padding:8px;"><strong>Test result:</strong></td>
    <td colspan="2" style="border:1px solid black; padding:8px; ">PASSED</td>
  </tr>
</table>

### 3.5. TC05 Extraction of Information for AAS-Generation MOD03

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

<table style=" border-collapse:collapse; font-family:Arial, sans-serif;">
  <tr>
    <td style="border:1px solid black; padding:8px;"><strong>Tester:</strong></td>
    <td colspan="2" style="border:1px solid black; padding:8px; ">Daniel Ziegler</td>
  </tr>
    <tr>
    <td style="border:1px solid black; padding:8px;"><strong>Date:</strong></td>
    <td colspan="2" style="border:1px solid black; padding:8px; ">03.05.2026</td>
  </tr>
    <tr>
    <td style="border:1px solid black; padding:8px;"><strong>Test result:</strong></td>
    <td colspan="2" style="border:1px solid black; padding:8px; ">
    ERROR WITH: prefers File-Name over XML<br>
    ERROR WITH: interprets &lt;aas&gt;-tags correctly<br>
    ERROR WITH: reads description data point to only description
    </td>
  </tr>
</table>

<table style=" border-collapse:collapse; font-family:Arial, sans-serif;">
  <tr>
    <td style="border:1px solid black; padding:8px;"><strong>Tester:</strong></td>
    <td colspan="2" style="border:1px solid black; padding:8px; ">Daniel Ziegler</td>
  </tr>
    <tr>
    <td style="border:1px solid black; padding:8px;"><strong>Date:</strong></td>
    <td colspan="2" style="border:1px solid black; padding:8px; ">06.05.2026</td>
  </tr>
    <tr>
    <td style="border:1px solid black; padding:8px;"><strong>Test result:</strong></td>
    <td colspan="2" style="border:1px solid black; padding:8px; ">PASSED</td>
  </tr>
</table>
</table>
