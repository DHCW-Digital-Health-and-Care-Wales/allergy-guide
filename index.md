## Allergy and Intolerance Implementation Guide

## Introduction

The FHIR® Allergies API has been developed by NHS Wales. The API aims to better support the delivery of care by opening up nationally stored information and data that patients want to share with healthcare professionals. 

Our vision aligns with our health and social care partners in the UK: to produce a library of nationally defined HL7® FHIR® resources and patterns that can be implemented to simplify integration and interoperability within the UK.

## Mission

NHS Wales are working to collaborate with patients, healthcare workers and other key stakeholders to develop a national allergy service which will be available to organisations providing direct care to the patient. The Allergy intollerance information will be visible thoughout the patient journey. It will collate and present information about the patient that should be known by the clinician or care team in order to provide more effective care. We want a better service experience for the patient, by giving them confidence that the care teams they deal with understand their condition with consistancy. We must imrove their sense of well being and a small but important way to do this is to remove the need to ask for the same infomration multiple times.

### Allergy Intollerance

Allergy and intolarance information can indicate the patient's reactions to substances and the severity and criticality of how the reactions are manifested. These reactions may be caused by foods, the environment, medicines or biologicial substances and indicate key clinical information. They are most often used in general decision support and safer prescribing of medicines. 

Key purposes include:

* ensuring the key information is shared consistently across health and care – wherever the patient is treated

* ensuring that the information is clearly visible in clinical systems

* Identifying a patient that may require localised adjustments to care in light of intolerances or allergies

* Identifying high risk patients with critical manifestations such as anaphalaxis


Authorised healthcare workers can:

* query to see a collated allergy record from primary and secondary care
* modify the collated allergy record to update or add a new allergy intolerance information

### No warnings, alerts or notes

Do not look here for general, specific or short term annotations about the patient's state. This space does not deal with alerts or warnings. Broad or temporal notations can be raised as patient flags via alerts and warnings. Focused notation should be localised and stored closer to a given context- maintaining relevance to specific audiences. 

* TODO example of patient flag as alert
* TODO example of medication note, other?

## Overview

Allergy and intolerance information should be moved between different software using HL7 FHIR R4

- [DataStandardsWales-AllergyIntolerance](https://simplifier.net/guide/fhir-standards-wales-implementation-guide/Home/FHIR-Assets/Profiles-and-Extensions/Profiles/DataStandardsWales-AllergyIntolerance?version=2.1.0)

### Clinical scenario: producing an Allergy List

In this scenario, a patient is admitted as an inpatient; allergies are made available from several sources in varying quality. The end user will need to refine this prior to prescribing. The allergies are presented, checked and the current allergies list is created.

The purpose of these examples is to illustrate FHIR usage based on a simple clinical scenario.

#### 1) Prior to admission

If degraded allergies are recorded then steps will need to be taken during admission to make the record safe prior to treatment or prescription. The degraded allergies will need to be coded correctly and updated. No list exists at this stage and the query specified it should be returned if present.

##### All Allergy information available- no current list exists

- Potato
- Aspirin, Ibuprofen (transfer degraded)
- Aspirin
- Wasps (transfer degraded)
- Morphine/oramorph (transfer degraded)

#### 2) After admission

The allergy information has been refined by the user by consulting with the patient and finding equivalent coded substances and findings or disorders. Each allergy resource is updated as these changes occur. No current list need exist at this stage.

##### All Allergy information refined- items corrected

- Potato
- Ibuprofen
- Aspirin
- Wasp
- Morphine

#### 3) On discharge or transfer

After the visit, the patient's medications and allergies form a part of the discharge or transfer message. To encapsulate the current view at the point of discharge a current allergy list is generated and added to, or referenced by, outbound messaging.

##### Current Allergy list generated

- Potato
- Ibuprofen
- Aspirin
- Wasp
- Morphine

### Clinical scenario: updating an Allergy List

In this scenario, a patient is admitted as an inpatient; allergies are made available from an existing allergy list. The end user needs to update the list to add a newly discovered allergy and to update any existing items to make the list conformal.

#### 1) On admission

The user has been presented with a list of no known allergies, meaning it is understood the user has no allergies.

#### 2) During admission

The patient informs the user that they recently had a reaction to strawberries. The user **must** soft delete the no known allergies entry, add the strawberry allergy and update the current list.

#### 3) On discharge or transfer

After the visit, the patient's medications and allergies form a part of the discharge or transfer message. To encapsulate the current view at the point of discharge the current allergy list is added to, or referenced by, outbound messaging.