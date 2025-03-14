## Allergy and Intolerance Implementation Guide

## Example 1: Update AllergyIntolerance:  confirm allergic reaction to general Penicillin



### Assumptions

* all [common assumptions](..\index.md)

### Preconditions

* the HCW has safely identified the patient

* the patient decribes a historic chest infection that they were given antibiotics capsules to treat and makes a statement to the HCW about side effects

  * the patient states they had a tight chest and a rash

* the HCW asks the patient to describe how side effects make them feel: 

  * They use words such as as mild, manageable, worrying, severe to help the patient describe the reactions

* the patient states the rash is annoying but their chest means they have to stop and sit every few minutes

* the patient doesnt know the specifc product

* the patient doesn't have the medicines with them

* the HCW wasn't present to observe the reactions

  * the HCW asks when this happened- was is recent?

* the HCW decides they cant currently assess how critical these reactions are

* the HCW decides this sounds like an allergic reaction rather than a simple intollerance

* the HCW decides this should be recorded on the patients record

  

### Actions

* the HCW checks the allergy record for the patient

* the HCW find an existing record describing a Penicillin allergy 

* the existing record signals that the allergy has not been verified (read unconfirmed)

* the HCW decides the allergy needs confirmation

* the HCW performs a skin prick test for Penicillin and observes the patient

* the HCW observes the test - it confirms the patients previous statements about the reaction

  * state its a confirmed allergy (because diagnostics have been presented as evidence)

  * add a note describing the interaction with the patient and the skin prick test

  * adds one reaction:

    * finds or selects the product used in the skin prick test
    * find or select 'wheal' and 'Airway constriction'
    * add a note describing the reaction - relating to test reaction times
    * sets the expose route as Intradermal
  * sets the onset date
  
* state the criticality as moderate
  
* indicates themselves as asserter of this information
  
    

### Outcome

* the HCP has automatically been allocated as the author
* the recorded date is unchanged
* the digital tool used SNOMED and DM+D to code sections of the record 
* the data is available for other systems to consume
* there are now two recorded reactions- one from the patient and one from the test

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
        "code": "890458001",
        "display": "Product containing penicillin (product)"
      }
    ]
  },
  "patient": {
    "reference": "{the patient}"
  },
  "recordedDate": "2025-04-01",
  "recorder": {
    "reference": "{the HCP}"
  },
  "asserter": {
    "reference": "{the HCP}"
  },
  "note":[{"text":"patient decribed a historical reaction to antibiotics"},{"text":"reaction confirmed with skin prick test- airway constricted, skin reddening around the test area"}],
  "reaction": [
    {
      "substance": {
        "coding": [
          {
            "system": "http://snomed.info/sct",
            "code": "42949111000001109",
            "display": "Generic Penicillium notatum 25micrograms/ml solution for skin prick test (product)"
          },
          {
            "system": "https://dmd.nhs.uk",
            "code": "42949111000001109",
            "display": "Generic Penicillium notatum 25micrograms/ml solution for skin prick test"
          }
        ]
      },
      "note": [{ "text": "symptoms onset under 5 minutes" }],
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
        "onSet":"2025-04-01",
        "exposureRoute": {
        "coding": [
          {
            "system": "http://snomed.info/sct",
            "code": "372464004",
            "display": "Intradermal route (qualifier value)"
          }
        ]
      }
    },
    {
      "note": [{ "text": "patient states rash annoying but mild, tight chest- they need to stop and sit every few minutes" }],
      "manifestation": [
        {
          "coding": [
            {
              "system": "http://snomed.info/sct",
              "code": "162415008",
              "display": "C/O: a rash (finding)"
            }
          ]
        },
        {
          "coding": [
            {
              "system": "http://snomed.info/sct",
              "code": "23924001",
              "display": "Tight chest (finding)"
            }
          ]
        }
      ],
      "onSet":"2024",
      "severity": "moderate"
    }
  ]
}

```



## Medicine 3: Health care worker (HCW) records a allergic reaction to specific Penicillin



### Preconditions

* the HCW has safely identified the patient

* the patient has been prescribed Flucloxacillin 250mg capsules (A A H Pharmaceuticals Ltd) to treat a chest infection by their GP

* the patient has the medicines with them

* the patient decribes a chest infection they have and makes a statement to the HCW about side effects

* the HCW can observe the reactions

* the patient states they had a tight chest and a rash

* the HCW asks to describe how bad the rash and tightness was: 

  * They use words such as as mild, manageable, worrying, severe to help the patient describe the reactions
  * the patient states the rash is annoying but their chest means they have to stop and sit every few minutes

  the HCW decides this sounds like an allergic reaction rather than a simple intollerance

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
* the digital tool used SNOMED to code sections of the record 
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

