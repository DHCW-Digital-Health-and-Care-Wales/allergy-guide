## Allergy and Intolerance Implementation Guide

## Example 2: Add AllergyIntolerance:  confirmed allergic reaction to specific Penicillin



* ### Assumptions

  * all [common assumptions](..\index.md)



### Preconditions

* the HCW has safely identified the patient
* the patient decribes a chest infection they have currently and makes a statement to the HCW about side effects
  * the patient states they had a tight chest and a rash
* the HCW asks the patient to describe how side effects make them feel: 

  * They use words such as as mild, manageable, worrying, severe to help the patient describe the reactions
* the patient states the rash is annoying but their chest means they have to stop and sit every few minutes
* the patient has been prescribed Flucloxacillin 250mg capsules (A A H Pharmaceuticals Ltd) to treat a chest infection by their GP
* the patient has the medicines with them
* the HCW can observe the reactions
* the HCW decides this sounds like an allergic reaction rather than a simple intollerance
* the HCW decides this should be recorded on the patients record

### Actions

* the HCW checks the allergy record for the patient

* the HCW finds no record describing a Penicillin allergy

* the HCW adds a new record using a digital tool that allows them to:

  * choose the type as 'allergy'

  * choose the category for the allergy as 'medicine'

  * find or select 'Flucloxacillin 250mg capsules (A A H Pharmaceuticals Ltd)' 

  * state the allergy is confirmed (because the HCP is a witness)

  * add a note describing the discusion with the patient 

  * adds one reaction:

    * chooses mild and moderate
    * find or select 'wheal' and 'Airway constriction'
    * add a note describing each reaction- - relating to annoying and siting every few minutes
    * sets today as the onset date

  * state the criticality as moderate

  * indicates themselves as asserter of this information

    

### Outcome

* the HCP has automatically been allocated as the author
* the recorded date is automatically set
* the digital tool used SNOMED and DM+D to code sections of the record 
* the data is available for other systems to consume
* there is one recorded reaction

The data produced by the digital tool takes this general form

```json
{
  "resourceType": "AllergyIntolerance",
  "clinicalStatus": {
    "coding": [
      {
        "system": "http://terminology.hl7.org/CodeSystem/allergyintolerance-clinical",
        "code": "active",
        "display": "Active"
      }
    ]
  },
  "verificationStatus": {
    "coding": [
      {
        "system": "http://terminology.hl7.org/CodeSystem/allergyintolerance-verification",
        "code": "confirmed",
        "display": "Confirmed"
      }
    ]
  },
  "category": ["medication"],
  "criticality": "moderate",
  "code": {
    "coding": [
      {
            "system": "http://snomed.info/sct",
            "code": "120711000001100",
            "display": "Flucloxacillin 250mg capsules (A A H Pharmaceuticals Ltd) (product)"
          },
          {
            "system": "https://dmd.nhs.uk",
            "code": "120711000001100",
            "display": "Flucloxacillin 250mg capsules (A A H Pharmaceuticals Ltd)"
          }
    ]
  },
  "patient": {
    "reference": "{the patient}"
  },
  "recordedDate": "2025-04-17",
  "recorder": {
    "reference": "{the HCP}"
  },
  "asserter": {
    "reference": "{the HCP}"
  },
  "note":[{"text":"witnessed presented reaction symptoms- rash and tight chest"}],
  "reaction": [
    {
      
      "note": [{ "text": "skin reddening, laboured breathing" }],
      "manifestation": [
        {
          "coding": [
            {
              "system": "http://snomed.info/sct",
              "code": "44416002",
              "display": "Airway constriction (finding)"
            }
          ]
        },
        {
          "coding": [
            {
              "system": "http://snomed.info/sct",
              "code": "247472004",
              "display": "Wheal (finding)"
            }
          ]
        }
      ],
        "onSet":"2025-04-17",
        "exposureRoute": {
        "coding": [
          {
            "system": "http://snomed.info/sct",
            "code": "26643006",
            "display": "Oral route (qualifier value)"
          }
        ]
      }
    }
  ]
}
```

