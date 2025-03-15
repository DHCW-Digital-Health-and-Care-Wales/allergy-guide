# Add an allergy or intolerance for a patient

> jump to : [Wireframes](#wireframes) | [diagrams](diagrams)
  
## Wireframes

Wireframes are not prescriptive. See notes on [how to use wireframes](url)

**Walk-through samples**
* [Add medicine allergy](#add-view-medicine-allergy)
  * [general medication example](general%20medication%20allergy%20-%20add.md)
  * [specific medication example](specific%20medication%20allergy%20-%20add.md)
* [Add other allergy](#add-view--other-allergy)
 
### User goals

* add a new record of a side effect for a patient

### Interface goals

* minimise cogntive load
* minimise screen time 
* minimise need for a keyboard and mouse
* use data intelligently





### Add view: medicine allergy

#### The user can:

1. see data from the patients medicines record when they select *medicine reaction*
   1. all SHOULD be backed by an entity using the DM+D coding system
2. find other medicines 
   1. the type ahead box finds matching values in SNOMED terminology, looking for concepts with an  'is a' relationship to 'UK product'
   2. If the concept behind the user selection has DM+D attributes, the DM+D coding system can be used alongside the SNOMED code
3. select from common symptoms
   1. all  SHOULD be backed by an entity using the SNOMED  coding system
4. find other symptoms 
   1. the type ahead box finds matching values in SNOMED terminology, looking for concepts with an  'is a' relationship to 'findings'
   2. the user can repeat this action for each additional symptom
5. enter partial dates for onset



![](assets/add-allergy-medicine.png)

### Add view:  other allergy



#### The user can:

1. see common substances know to cause food, boilogical or environmental allergic responses.
   1. all SHOULD be backed by an entity using the SNOMED coding system
2. find other substances
   1. the type ahead box finds matching values in SNOMED terminology, looking for concepts with an  'is a' relationship to 'substance'
   2. typing without a match results produces a text only coding
3. select from common symptoms
   1. all  SHOULD be backed by an entity using the SNOMED  coding system
4. find other symptoms 
   1. the type ahead box finds matching values in SNOMED terminology, looking for concepts with an  'is a' relationship to 'findings'
   2. the user can repeat this action for each additional symptom
5. enter partial dates for onset

![](assets/add-allergy-other.png)

## Diagrams

### Process: Add alergy or intolerance

```mermaid
flowchart TD
 

    TRIGGER(["side effects or reaction is determined"]) --> S2["The user views the allergy record"]
    S2 --> S3{"is there an <br>equivalent <br>entry?"}
    S3 -- Yes --> SUCCESS(["process terminates"])
    S3 -- No ---> S2A[[add record]]
    S2A--> SUCCESS(["process terminates"])
   


    style TRIGGER fill:#0085FC
    style SUCCESS fill:#ff9
```


### Sub-process: Add Record


```mermaid
flowchart TD
		TRIGGER(["add record"])
		S6["Sets <br><b>clinical status</b><br>[active | inactive | resolved]"]
        S5["Sets <br><b>category</b> <br>[food | medication | environment | biologic]"]
        S7["Sets <br><b>verification status</b><br>[unconfirmed | confirmed | refuted | entered-in-error]"]
        S8["Sets <br><b>criticality</b><br>[low | high | unable-to-assess]"]
        S9["User Finds or selects <br> <b>substance</b> <br>responsible for the risk"]
        S10["User Adds <b>note</b>"]
        S11[["Adds reaction Event"]]
        
	TRIGGER --> S5
	S5 --> S6
    S6 --> S7
    S7 --> S8
    S8 --> S9
    S9 --> S10
    S10 --> S11
    S11 --> SUCCESS(["process terminates"])
    
```

### Sub-process:  Add Reaction Event

```mermaid
flowchart TB
    	TRIGGER(["Add rection Event"]) 
    	E1["Sets <br><b>event severity</b><br>[mild | moderate | severe]"]
        E2["Sets <br><b>event onset</b>"]
        E3["Finds or selects <br> <b>event symptoms</b>"]
        E4{"all symptoms <br>added?"}
        E5["Sets <br><b>event note<b></b></b>"]
        E6{"substance<br> is different from <br>overall risk <br>substance?"}
        E7["Finds or selects <br> <b>event substance</b>"]
        
    TRIGGER --> E1    
    E1--> E2
    E2 --> E3
    E3 --> E4
    E4 -- Yes --> E5
    E4 -- No ---> E3
	E5 --> E6
	E6 -- Yes --> E7
    E6 -- No ---> SUCCESS
	E7 --> SUCCESS(["process terminates"])

    style TRIGGER fill:#0085FC
    style SUCCESS fill:#ff9
```

