# Business Case — BaSyx Editor Plugin Extension



---

## Short Product Overview
The BaSyx Editor Plugin Extension project aims to enhance the existing BaSyx GUI by extending the Editor Plugin, Viewer Plugin, and the REST API backend. The extension will enable users to attach and process external model files within the Asset Administration Shell (AAS), validate and link files by MIME type/definition, extract technical data from KBL and VEC files into the AAS "General Technical Data" submodel, provide structured REST access to XML contents, and visualize internal data structures in the Viewer Plugin. The result is improved usability, data accessibility, and interoperability across the BaSyx ecosystem.

---

## Project Introduction

### Stakeholders
| Role | Organization / Detail |
|---|---|
| Customer Stake-Holder | Rentschler & Wojcik |
| Provider | Team 3 |

<p align="right"><em>Table 1. Stakeholders</em></p>

### Team / Roles
| Role                    | Name                               | Email                                                               |
| ----------------------- | ---------------------------------- | ------------------------------------------------------------------- |
| Project Director        | Martin Böhm                        | inf24132@lehre.dhbw-stuttgart.de                                    |
| Product Manager         | Florian Zahn                       | inf24254@lehre.dhbw-stuttgart.de                                    |
| Test Manager            | Daniel Ziegler                     | inf24202@lehre.dhbw-stuttgart.de                                    |
| System Architect        | Federico Dibenedetto / Felix Bandl | inf24072@lehre.dhbw-stuttgart.de / inf24227@lehre.dhbw-stuttgart.de |
| Technical Documentation | Leonardo Risatti / Morten Haase    | inf24074@lehre.dhbw-stuttgart.de / inf24033@lehre.dhbw-stuttgart.de |

<p align="right"><em>Table 2. Project team and roles</em></p>

Note: Every group member also functions as a software developer.

---
## Table of Contents
- [Short Product Overview](#short-product-overview)
- [Project Introduction](#project-introduction)
  - [Stakeholders](#stakeholders)
  - [Team / Roles](#team--roles)
- [Product Overview](#product-overview)
- [Why implementation is viable](#why-implementation-is-viable)
- [Cost Overview](#cost-overview)
  - [Fixed Costs](#fixed-costs)
  - [Variable Costs (Personnel)](#variable-costs-personnel)
  - [Costs per Work Phase](#costs-per-work-phase)
  - [Total Cost and Markup](#total-cost-and-markup)
- [Gantt Diagram](#gantt-diagram)
- [Notes and Observations](#notes-and-observations)
- [Contact / Acknowledgements](#contact--acknowledgements)

---

## Product Overview

Key features and goals:
- Allow attaching external model files to an AAS and process them.
- Validate and link files based on MIME types and definitions.
- Analyze KBL and VEC files to extract key technical data (product features, general specifications).
- Integrate extracted data into the AAS "General Technical Data" submodel.
- Extend REST API to provide structured access to XML file contents.
- Upgrade the Viewer Plugin to visualize internal data structures.
- Overall aims: improved usability, better data access, stronger interoperability, and higher customizability.

---

## Why implementation is viable

- Increased user-friendliness through improved editing, visualization, and integration workflows.
- Efficiency gains in integrating and maintaining technical data.
- Greater flexibility thanks to manual edit capabilities.
- Positive effect on client reputation and potential to attract new users.
- Expected strong reception from existing users who require these capabilities, including non-technical users.

---

## Cost Overview

### Fixed Costs
| Item                  |    Cost (€) |
| --------------------- | ----------: |
| Internet and Energy   |     1,000 € |
| Software Licences     |       700 € |
| Additional Hardware   |       200 € |
| Education             |       700 € |
| **Total Fixed Costs** | **2,600 €** |

<p align="right"><em>Table 3. Fixed costs breakdown</em></p>

### Variable Costs (Personnel)

Estimated personnel costs per 180 hours (as provided):

| Role                    | Name                 | Hourly Wage (€) | Cost for 180 h (€) |
| ----------------------- | -------------------- | --------------: | -----------------: |
| Project Director        | Martin Böhm          |              30 |           5,400.00 |
| Project Manager         | Florian Zahn         |           26,50 |           4,770.00 |
| Test Manager            | Daniel Ziegler       |              25 |           4,500.00 |
| System Architect        | Federico Dibenedetto |              25 |           4,500.00 |
| System Architect        | Felix Bandl          |              25 |           4,500.00 |
| Technical Documentation | Leonardo Risatti     |              25 |           4,500.00 |
| Technical Documentation | Morten Haase         |              25 |           4,500.00 |
| **Total (per 180 h)**   |                      |                 |         **32,670** |
|                         |                      |                 |                    |

<p align="right"><em>Table 4. Variable personnel costs (per 180 h)</em></p>


### Costs per Work Phase
| Phase     | Martin Böhm | Florian Zahn | Daniel Ziegler | Federico Dibenedetto | Felix Bandl | Leonardo Risatti | Morten Haase |      Cost (€) |
| --------- | ----------- | ------------ | -------------- | -------------------- | ----------- | ---------------- | ------------ | ------------: |
| Analyse   | 40h         | 40h          | 20h            | 20h                  | 20h         | 30h              | 30h          |      5,260.00 |
| Design    | 40h         | 40h          | 20h            | 40h                  | 40h         | 40h              | 40h          |      6,760.00 |
| Coding    | 40h         | 40h          | 50h            | 60h                  | 60h         | 50h              | 50h          |      9,010.00 |
| Testing   | 30h         | 40h          | 70h            | 40h                  | 40h         | 50h              | 50h          |      8,210.00 |
| End Phase | 30h         | 20h          | 20h            | 20h                  | 20h         | 10h              | 10h          |      3,430.00 |
| **Total** | 180h        | 180h         | 180h           | 180h                 | 180h        | 180h             | 180h         | **32,670.00** |



<p align="right"><em>Table 5. Costs per work phase 
</em></p>

### Total Cost and Markup

After careful consideration within the team we came to the conclusion that a markup of 20% of the total cost *(fix cost + total costs per work pahse)*, wich would be **7,054.00€** is a vialbe charge for our services, creating a **final price of ==42,324.00€==**

---

## Gantt Diagramm 
![[Pasted image 20251118160147.png]]

---


## Contact / Acknowledgements
Prepared for: Rentschler & Wojcik  
Prepared by: Team 3 (project roles and contacts listed above)
