# View allergy records for a patient

> jump to : [Wireframes](#wireframes) | [diagrams](diagrams)
> 
## Wireframes

Wireframes are not prescriptive. See notes on [how to use wireframes](../index.md#understanding-wireframes)

**Walk-through samples**
* [no entries in the record](#list-view-no-entries)
* [negation in the record](#list-view-positive-negation-statement)
* [entries in the record](#list-view--record-with-two-entries)
* expanded views of entries in the record
  * [first item epanded](#list-view--record-with-entry-expanded-a)
  * [second item epanded](#list-view--record-with-entry-expanded-b)
 

### User goals

* see all records of allergies for a patient

### Interface goals

* minimise screen time 
* provide a safe overview- enough to eliminate accidental risk of harm
* show more information as needed
* minimise need for a keyboard and mouse



### List view: no entries

#### The user can:

1. clearly see there is no record of allergies
2. create a new entry (when permitted)

![](assets/empty.png)

### List view: positive negation statement

#### The user can:

1. see an entry stating there are no allergies
   1. see the status of it
   2. see when it was last updated
   3. see more details may be available
2. create a new entry (when permitted)

![list with positive negation entry](assets/empty-no-known-allergies.png)

### List view:  record with two entries

#### The user can:

1. see two entries
   1. see the substance of each
   2. see the status of each
   3. see how critical the entries are
   4. see when each was last updated
   5. see more details may be available
2. see the most recent entries are first by when they were last updated
3. create a new entry (when permitted)

![](assets/list.png)

### List view:  record with entry expanded A

#### The user can:

1. see two entries
2. see the first of the entries is showing more details and
   1. see the notes and when the notes were made
   2. see reaction events and for each:
      1. see symptoms
      2. see the substance that caused the symtoms  (if known)
      3. see when it was recorded and who recorded it
      4. see notes about symptoms
   3. seehow to make changes to it  (when permitted)
3. see the most recent entries first by when they were last updated
4. create a new entry (when permitted)

![](assets/list-expanded-1.png)

### List view:  record with entry expanded B

#### The user can:

1. see two entries
2. see the second of the entries is showing more details and
   1. see the notes and when the notes were made
   2. see reaction events and for each:
      1. see symptoms
      2. see the substance that caused the symtoms  (if known)
      3. see when it was recorded and who recorded it
      4. see notes about symptoms
   3. seehow to make changes to it  (when permitted)
3. see the most recent entries first by when they were last updated
4. create a new entry (when permitted)

![](assets/list-expanded-2.png)


```mermaid
flowchart TD


    TRIGGER(["patient safely identified"]) 
    S2["The system reads the record"]
    S3{"any record entries?"}
    S3A["show empty list message"]
    S4["order by last updated descending"]
    S5["take record entry"]
    S6{"high risk, <br>breathing or <br>anaphalaxis <br>symptoms?"}
    S6A{"no DM+D or <br>SNOMED code?"}
    %%S6A{"medicine category <br>without <br>preferred coding?"}
    S7["alert user"]
    S8["display entry"]
    S9{"entries remaining?"}
    
    SUCCESS(["process terminates"])
  
  TRIGGER --> S2
  S2 --> S3
  S3 -- Yes --> S4
  S3 -- No --> S3A
  S4 --> S5
  S5 --> S6
  S6 -- Yes --> S7
  S6 -- No --> S6A
  S6A -- Yes --> S7
  S6A -- No --> S8
  S7 --> S8
  S8 --> S9
  S9 -- Yes --> S5
  S9 -- No --> SUCCESS
    style TRIGGER fill:#0085FC
    style SUCCESS fill:#ff9
```
