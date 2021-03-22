# Angular Project Helps
![Work With Dates](https://github.com/mizanurrhman/angularHelps/blob/main/OHelp/DateCalculation.md "Dates")

> Angualr CheatShit

![Angualr CheatShit](https://github.com/mizanurrhman/angularHelps/blob/main/ngCheatShit.png "OutPut")

![Angualr DataBinding](https://github.com/mizanurrhman/angularHelps/blob/main/ngDataBinding.jpg "Data Binding")

![Angualr Structural Directive](https://github.com/mizanurrhman/angularHelps/blob/main/ngStructuralDirective.png "Structural Directive")

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
`colorStatus: string = 'GREEN'`
```html
 <td rowspan="2">
<div [ngStyle]="{ 'background-color':colorStatus, 'display':  'inline-block', 'height':'50px' ,'width':'50px','border-radius': '50%','border':'solid lightgray 1px' }">
<span style="color:white; text-align: center; vertical-align: middle; line-height: 50px; font-size: 30px; display: block;">{{colorStatus.charAt(0)}}</span>
</div>
 <span> ngStyle condition</span>
<span [ngStyle]="{'color': (colorStatus.charAt(0) === 'W') ? 'Gray':'white', 'text-align': 'center', 'vertical-align': 'middle', 'line-height': '50px', 'font-size': '30px', 'display': 'block'}">{{colorStatus.charAt(0)}}</span>
```
![OutPut](https://github.com/mizanurrhman/angularHelps/blob/main/dr.JPG "OutPut")

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

#### Error `cannot Get /`
* Go Inside ClientApp folder run `PowerShell` enter command `ng build` if can not run this script error go link provided and see the solution, todays case `Set-ExecutionPolicy -ExecutionPolicy RemoteSigned -Scope CurrentUser` then run again `ng build`

#### Convert Specific Date format  

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


### Dropdown event with condition
```ts
this.userForm.get('ddlReason').setValue(this.reason.find(x => x.CODE == this.reasonCode));
switch (this.reasonCode) {
  case '01':
    this.donReqNoVisible = true;
    this.t12201Service.getDonReqNoList().subscribe((success: any) => {
      this.donReqNoList = success;
      this.userForm.get('ddlDonReqNo').setValue(this.donReqNoList.find(x => x.DON_REQNO == this.donorReqNo));
    });
    break;
  case '05':
  case '06':
    this.otherPatVisible = true;
    this.userForm.get('txtOtherPatNo').setValue(success["T_OTHER_PAT_NO"]);
    this.userForm.get('txtOtherPatName').setValue(success["T_OTHER_PAT_NAME"]);
    this.donReqNoVisible = false;
    break;
  default:
    this.otherPatVisible = false;
    this.userForm.get('txtOtherPatNo').setValue('');
    this.userForm.get('txtOtherPatName').setValue('');
    this.donReqNoVisible = false;
    this.userForm.get('ddlDonReqNo').setValue('');
}
```
## Show alert Message from Database
> Data From DB DAL

```cs
public IEnumerable<dynamic> GetAllMessage(string T_MSG_CODE, string Language)
        {
            var query = $"SELECT T_MSG_CODE CODE, T_LANG{Language}_MSG TEXT FROM T01004 WHERE T_MSG_CODE IN ({T_MSG_CODE})";
            return QueryList<dynamic>(query);
        }
```
> Cal DAL from controlar(FormController)

```cs
[HttpGet("/api/getAllMessage")]
        public IActionResult GetAllMessage(string msgCode)
        {
           var language = HttpContext.Session.Keys.Any() ? HttpContext.Session.GetString("USER_LANG") : "1";
            var formLabel = commonDal.GetAllMessage(msgCode, language);
            return Ok(formLabel);
        }
```
 >Cal controller from Service(FormService)
 ```ts
 getAllMessage(msgCode: string) {
    console.log(msgCode);
    return this.http.get('/api/getAllMessage', { params: { msgCode: msgCode } }).pipe(map(response => response));
  }
 ```
 > call service in component.ts during load page ` ngOnInit()`
 
 ```ts
 message :any[];
  this.formService.getAllMessage("'N0004','N0057','N0055','N0063','S0344','N0040','N0071','S0351'")
      .subscribe((success: any) => {
        this.messages = success;
      });
 ```
 > Now use it 
 
 ```ts
 this.messageService.add({ severity: 'info', summary: 'Info!', detail: this.messages.find(x => x.CODE == 'N0057').TEXT });
```





