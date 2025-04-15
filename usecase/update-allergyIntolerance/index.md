# Update an allergy or intolerance for a patient

## Wireframes

Wireframes are not prescriptive. See notes on [how to use wireframes](../index.md#understanding-wireframes)

### User goals

* add a new record of a side effect for a patient

### Interface goals

* minimise cogntive load
* minimise screen time 
* minimise need for a keyboard and mouse
* use data intelligently



### Process: Update alergy or intolerance 


```mermaid
flowchart TD
 

    TRIGGER(["side effects or reaction is determined"]) --> S2["The user views the allergy record"]
    S2 --> S3{"is there an <br>equivalent <br>entry?"}
    S3 -- Yes --> S4{"is it <br>accurate and <br>complete?"}
    S3 -- N0 ---> S3A[[edit record]]
    S3A --> SUCCESS(["process terminates"])
    S4 -- Yes --> SUCCESS(["process terminates"])
    S4 -- No --> S3A[[edit record]]


    style TRIGGER fill:#0085FC
    style SUCCESS fill:#ff9
```



### Sub-process: Edit Record

```mermaid
flowchart TB
    TRIGGER(["Edit record"]) --> S6["The user views the allergy record"] 
    S6["Updates <br><b>clinical status</b><br>[active | inactive | resolved]"]
    S7["Updates <br><b>verification status</b><br>[unconfirmed | confirmed | refuted | entered-in-error]"]
    S8["Updates <br><b>criticality</b><br>[low | high | unable-to-assess]"]
    S10["Adds <b>note</b>"]
    S11[["Adds reaction event"]]

    S6 --> S7
    S7 --> S8
    S8 --> S10
    S10 --> S11
	S11 --> SUCCESS(["process terminates"])


    style TRIGGER fill:#0085FC
    style SUCCESS fill:#ff9
```



### Sub-process:  Add Reaction Event

```mermaid
flowchart TB
    	TRIGGER(["Add rection Event"]) 
    	E1["Sets <br><b>event severity</b><br>[mild | moderate | severe]"]
        E2["Sets <b>event onset</b>"]
        E3["Finds or selects <br> <b>event symptoms</b>"]
        E4{"all symptoms <br>added?"}
        E5["Sets <b>event note<b></b></b>"]
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

