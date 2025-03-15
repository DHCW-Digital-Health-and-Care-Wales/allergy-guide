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

