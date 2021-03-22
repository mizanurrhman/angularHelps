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
  ```ts

let oD = otherDate.split("/", 3); //'07-01-2021' dd-MM-yyyy
    let day = Number(oD[0]);
    let mon = Number(oD[1]) - 1;
    let yr =  Number(oD[2]);
    let othrDay = new Date(yr, mon, day);

    console.log(othrDay);
    // OR 
    var a = otherDate.split('/');
    var birthDate = new Date(Number(a[2]), Number(a[1]) - 1, Number(a[0]));

    console.log('anotherDate', birthDate);
```
OutPut `Thu Jan 07 2021 00:00:00 GMT+0800 (Singapore Standard Time)`

> format date `String.Format("{0:0.00}"`
