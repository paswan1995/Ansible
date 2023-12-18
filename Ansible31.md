## YAML

* It is a Data Description Format.
* It is widely used to store 
       *  Data
       *  Confugrations
* Data can be categorized into 2 types  

       * Simple/Scalar: 
          * Text `name: Ansible`
          * Number `version: 2.13`
          * Boolean `Opensource: yes`    
          
* Complex 
       * list/array (Plural) 
         "'yaml
         colors:</li>
         <li>red<li>
         <li>blue<li>
         <li>green
         "'
       * Object/map/directory
        `yaml`
        `address`
        `flatno: 407`
        `building: ramnivas`
        `city: Hyderabad`

* JSON/YAML use KEY-VALUE (Name Value) pairs.
* YAML Basic key value syntax is `key: value`
* Sample YAML ( QUALITY THOUGHT)
```
---
name: QualityThought
contact:
  email:
    - support@qualitythought.in
    - qualitythought.in@gmail.com
  phone:
    - 888888888
    - 999999999
  address:
    - flat: 407 
      building: mythrivanam
      city: hyderabad
    - flat: 307
      building: nilgiri
      city: Hydrebad
  
```


* In YAML `true or yes and false or no is a same thing`.
*Before `-` you have to give `2 space` and After `-` you have to give `1 space` .