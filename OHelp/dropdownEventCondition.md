> **Dropdown event with condition**

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
