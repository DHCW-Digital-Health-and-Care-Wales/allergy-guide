
# Use cases

### [View allergy records for a patient](view-record/index.md)
A user can view an allergy record for a clear overview of known risks to a patient

### [Add an allergy or intolerance for a patient](add-allergyIntolerance/index.md)
A user can add a known risk so that others can understand it

### [Update an allergy or intollerance for a patient](update-allergyIntolerance/index.md)
A user can make changes a known risk when new information is known

## Background: all use cases

The following are common to all use cases and examples

### Common assumptions

* an allergy record is available in FHIR R4

* the system can provide a 'find or select' action to determine a medicine, side effects, routes of exposure etc

* the system can provide DM+D and/or SNOMED coding based on find or select actions

* the system can read and write to the allergy record in FHIR R4

  

### Comon definitions & abbreviations

* the system: a digital tool with allergy risk management functionality
  
* the user: a person with accces to the system
  
* HCW: Health Care worker

* FHIR: Fast Healthcare Interoperability Resource. A healthcare data exchange framework from HL7 international for the modern web

* Alllergy: used generally to describe an allergy or an intolerance here, with further local qualification between the two where relevant



## Flow diagrams

We use flow diagrams to describe steps taken between the start and end of process. Some key elements are shown here and, where appropriate. how these relate to FHIR resources.

| element                    | description                                                  | FHIR property path                      |
| -------------------------- | ------------------------------------------------------------ | --------------------------------------- |
| **bold** terms             | describes a data element, normally a property of the FHIR allergyIntolerance resource, expanded for readability. | n/a                                     |
| [ a \| b \| c ]            | Allowed values for a FHIR resource property                  | n/a                                     |
| **add record**             | This sub process is responsible for populating a new FHIR allergyIntollerance resource | . (allergyIntollerance)                 |
| >  **category**            | A text property with restricted values. <br />FHIR allergyIntollerance resource can have several categories at the same time | .category[x]                            |
| >  **clinical status**     | A coded property                                             | .clinicalStatus                         |
| >  **verification status** | A coded property                                             | .verificationStatus                     |
| >  **criticality**         | A text property with restricted values.                      | .criticality                            |
| >  **substance**           | A coded property. SHOULD be DM+D or SNOMED coded, MUST have text equivalent when not coded | .code  -                                |
| >  **note**                | FHIR allergyIntollerance resource can have several notes. Each note can have formatted or plain text, an author and a date | .note[x]                                |
| > **add reaction event**     | This sub process is responsible for populating a reaction event within a FHIR allergyIntollerance resource. A resource can have several reaction events. | .reaction[x]                            |
| > > **event severity**      | A text property with restricted values                       | .reaction[x].severity                   |
| > > **event onset**         | a date or partial date (in UTC format)                       | .reaction[x].onSet                      |
| > > **event symptoms**      | A coded property. SHOULD be SNOMED coded, MUST have text equivalent when not coded. A reaction can have several manifestations. | .reaction[x].manifestation[y]           |
| > > **event substance**     | A coded property. SHOULD be DM+D or SNOMED coded, MUST have text equivalent when not coded. MUST ONLY be populated when the known product or substance in the event differs from the main | .reaction[x].manifestation[y].substance |
| > > **event note**          | Can have several notes. Each note can have formatted or plain text, an author and a date | .reaction[x].manifestation[y].note[z]   |

