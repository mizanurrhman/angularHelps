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
#### Difference Between Two dates in Days 
 ```ts
onDateDifference(fromDate: Date, toDate: Date) {
    let diffInTime = fromDate.getTime() - toDate.getTime();
    let diffInDays = Math.round(diffInTime / (1000 * 3600 * 24));  
    return diffInDays; 
  }
```
 Call the function 
 > `onDateDifference(new Date('02/03/2021'), new Date('23/02/2021'))` Out Put : `7`
 
#### Date Past and Future from specific date

```ts
onDatePastFuture(startingDate: Date, rangeDay: any) {
    let date = startingDate;
    date.setDate(date.getDate() + rangeDay);
    let datePastFuture = date.getDate() + '/' + (date.getMonth() + 1) + '/' + date.getFullYear();
    return datePastFuture;
  }
  ```
  Call the function for 57 days past and future from 23/02/2021
  > `onDatePastFuture(new Date('23/2/2021'),57);`   OutPut: 21/4/2021 
  > `onDatePastFuture(new Date(23/2/2021),(-57));` OutPut: 28/12/2020
  
  
