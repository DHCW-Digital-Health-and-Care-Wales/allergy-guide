## Allergy and Intolerance Implementation Guide

## Example 1: Add AllergyIntolerance: unconfirmed allergic reaction to general Penicillin



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

* the HCW find no record describing a Penecillin allergy

* the HCW adds a new record using a digital tool that allows them to:

  * choose the type as 'allergy'
  * choose the category for the allergy as 'medicine'
  * find or select 'Product containing Penicillin' as its the most common anitbiotic used to treat chest infections
  * state the allergy is unconfirmed (because no diagnostics have been presented as evidence)
  * set the approximate date or age this happened
  * add a note describing the discusion with the patient 
  * adds one reaction:
    * chooses moderate severity (as nothing discussed signals either mild nor severe)
    * find or select 'rash' and 'tight chest'
    * add a note describing each reaction- - relating to annoying and siting every few minutes
    * sets the approximate onset date
* state the inability to assess the criticality
  
  * indicate the patient asseted this information
  
    

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
        "code": "unconfirmed",
        "display": "Unconfirmed"
      }
    ]
  },
  "category": ["medication"],
  "criticality": "unable-to-assess",
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
  "recordedDate": "2025-03-01",
  "recorder": {
    "reference": "{the HCP}"
  },
  "asserter": {
    "reference": "{the patient}"
  },
  "note":[{"text":"patient decribed a historical reaction to antibiotics"}],
  "reaction": [
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



