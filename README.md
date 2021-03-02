# Angular Project Helps

 ### Example of Ternary Operator
```
const person = {name: 'Becky',gender: null}
```
 Value is present
`const name = person.name ?? 'Unknown person' ` OutPut: Becky
 Value is not present 
`const gender = person.gender ?? 'Unknown gender'` OutPut: Unknown gender 
   
  ### Formating Date field
  ```ts
  this.userForm.get('inputValue').setValue(new Date(Date.parse(datafield)).toLocaleDateString("en-GB", { year: 'numeric', month: '2-digit', day: '2-digit' }));
```
### Difference Between Two dates in Date 
  ```ts 
  let donDate = new Date(success.DONATION_DATE);       
 let diffInTime = this.sysDate.getTime() - donDate.getTime();
 let diffInDays = diffInTime / (1000 * 3600 * 24); 
 console.log(Math.round(diffInDays));
 ```
 
  
