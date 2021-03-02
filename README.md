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
  
  
#### condition in html control 
```html
<tr *ngIf="donReqNoVisible">
              <td class="td_label">
                  <label id="lblPatDonorNo" for="txtDonorNo">Donor No</label>
             </td>
              <td>
                <input type="text" id="txtDonorReqNo" formControlName="txtDonorReqNo" pInputText style=" width: 100px;" (change)="onDonorReqNoChange()" />
              </td>
              <td>
                <input type="text" id="txtDonorReqPatName" formControlName="txtDonorReqPatName" pInputText style="width: 200px;" />
              </td>
            </tr>
```
```ts
 otherPatVisible: boolean = false;
 donReqNoVisible: boolean = false;
 
reasonClick(event) {
    let reasonCode = event.value.CODE;
    switch (reasonCode) {
      case '01':
        this.donReqNoVisible = true;
        this.otherPatVisible = false;
        break;
      case '05':
      case '06':
        this.otherPatVisible = true;
        this.donReqNoVisible = false;
        break;
      default:
        this.otherPatVisible = false;
        this.donReqNoVisible = false;
        break;
    }
```
call from a control `(onChange)="reasonClick($event)"`


#### make a div circle with backgound fill color
```html
 <td rowspan="2">
              <div [ngStyle]="{ 'background-color' :  colorStatus, 'display':  'inline-block', 'height':'50px' ,'width':'50px','border-radius': '50%','border':'solid lightgray 1px' }">
              </div>
 </td>
```
value colorStatus come from .ts file `colorStatus: string = 'GREEN';`

#### Populate a dropdownLis from Database
html Code 
```html
<p-dropdown inputId="ddlReason" formControlName="ddlReason" (onChange)="reasonClick($event)" [options]="reason" optionLabel="NAME" [filter]="true" [resetFilterOnHide]="true" [style]="{'width':'100%'}"></p-dropdown>
```
` reason: any[];` data stored this list come from DB and from this list dropdown will bind data to `[options]="reason"` option propery
TypeScript
```ts
this.t12201Service.getAllReason()
      .subscribe((success: any) => {
        this.reason = success;
        this.reason.splice(0, 0, { CODE: '', NAME: '' });
      });
```
call service `this.t12201Service.getAllReason()` from `service.ts`
```ts
 getAllReason() {
    return this.http.get('api/t12201/getAllReason').pipe(map(response => response));
  }
```
service call controller 
```cs
[HttpGet("/api/t12201/getAllReason")]
        public IActionResult GetAllReason()
        {
            var auth = t12201DAL.GetRolePermission("T12201", HttpContext.Session.GetString("ROLE_CODE"))?.T_QRY_ACC.ToString();
            if (auth is null || auth != "1") return Unauthorized();
            var data = t12201DAL.GetAllReason(HttpContext.Session.GetString("USER_LANG"));
            return Ok(data);
        }
```
get data from DAL called by controller 
```cs
public IEnumerable<dynamic> GetAllReason(string lang)
        {
            var query = $@"SELECT T_DOTN_RSN_CODE CODE, T_LANG{lang}_NAME NAME  FROM T12006 ORDER BY 2 ";
            return QueryList<dynamic>(query);
        }
```
QueryList Method
```cs
  protected IEnumerable<T> QueryList<T>(string query)
        {
            IList<T> entities;

            using (var connection = Connection)
                entities = connection.Query<T>(query).ToList();

            return entities;
        }
```



