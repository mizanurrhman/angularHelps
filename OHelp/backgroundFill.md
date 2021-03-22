> **`*ngIF` , `*ngStyle`** Condition & Fill a div with Text and background color**
>> **HideNShow Control & Dropdown Click Event **
 
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
 ```
 > **Dropdown Change Event**  `(onChange)="reasonClick($event)"`
 
 ```ts
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

> **Fill a Div with Text & color**

`colorStatus: string = 'GREEN'`

```html
 <td rowspan="2">
<div [ngStyle]="{ 'background-color':colorStatus, 'display':  'inline-block', 'height':'50px' ,'width':'50px','border-radius': '50%','border':'solid lightgray 1px' }">
<span style="color:white; text-align: center; vertical-align: middle; line-height: 50px; font-size: 30px; display: block;">{{colorStatus.charAt(0)}}</span>
</div>
 <span> ngStyle condition</span>
<span [ngStyle]="{'color': (colorStatus.charAt(0) === 'W') ? 'Gray':'white', 'text-align': 'center', 'vertical-align': 'middle', 'line-height': '50px', 'font-size': '30px', 'display': 'block'}">{{colorStatus.charAt(0)}}</span>
```
![OutPut](https://github.com/mizanurrhman/angularHelps/blob/main/Images/dr.JPG "Text With Background Color")

