> **HTML** *Primeng*

```html
<div id="main">
  <ngx-loading [show]="loading"></ngx-loading>
  <p-toast></p-toast>
  <common-header [formCode]="formCode" (versionLoaded)="setVersion($event)" (labelLoaded)="setLabel($event)" (permissionLoaded)="setPermission($event)"></common-header>
  <div id="pageLeftPanelBg">
    <div id="options">
      <button type="button" class="Button New"  title="New" (click)="onBtnNewClick()"></button>
      <button type="button" class="Button Save" [disabled]="!readonly" title="Save" (click)="onBtnSaveClick()"></button>
      <button type="button" class="Button Clear"  title="Clear" (click)="onBtnClearClick()"></button>
      <common-button></common-button>
    </div>
  </div>
  <div id="container">
    <p-scrollPanel styleClass="scroll">
      <div class="content" style="width:1000px;">
        <form [formGroup]="userForm">
          <table>
              <tr>
                <td>
                  <p-radioButton name="rdoPatType" value="1"  label="{{onLabelLoad('lblAutoLog')}}" id="rdoAutoLog" formControlName="rdoAutoLog" (click)="rdoAutoLogClick()"></p-radioButton>&nbsp;
                 <p-radioButton name="rdoPatType" value="2"  label="{{onLabelLoad('lblDirectPatient')}}" id="rdoDirectPatient"  formControlName="rdoDirectPatient" (click)="rdoDirectPatientClick()"></p-radioButton>&nbsp;
                 <p-radioButton name="rdoPatType" value="3" inputId="rdoPatType" label="{{onLabelLoad('lblNormal')}}" id="rdoNormal"  formControlName="rdoNormal" (click)="rdoNormalClick()"></p-radioButton>&nbsp;
                </td>
              </tr>
            </table>
           <table>
            <tr>
              <td class="td_label">
                <label id="lblPatNo" for="txtPatNo"></label>
              </td>
              <td>
                <input type="text" id="txtPatNo" formControlName="txtPatNo" pInputText style="width: 100px" (change)="onPatNoChange()" />
              </td>
              <td colspan="4">
                <input type="text" id="txtPatName" formControlName="txtPatName" pInputText style="width:98%" readonly="readonly" />

              </td>
              <td></td>
              <td class="td_label">
                <label id="lblYear" for="txtYear"></label>
                <input type="text" id="txtYear" formControlName="txtYear" pInputText style="width:40px;"  readonly="readonly"  /> &nbsp;
                <label id="lblMonth" for="txtYear"> </label>
                <input type="text" id="txtMonth" formControlName="txtMonth" pInputText style="width:40px;"  readonly="readonly" />
              </td>
              <td rowspan="2">
                <div [ngStyle]="{ 'background-color':colorStatus, 'display':  'inline-block', 'height':'50px' ,'width':'50px','border-radius': '50%','border':'solid lightgray 1px' }">
                  <span style="color:white; text-align: center; vertical-align: middle; line-height: 50px; font-size: 30px; display: block;">{{colorStatus.charAt(0)}}</span>
                </div>
              </td>
            </tr>
            <tr>
              <td class="td_label">
                <label id="lblNationalID" for="txtNationalID"></label>
              </td>
              <td>
                <input type="text" id="txtNationalID" formControlName="txtNationalID" pInputText style="width: 100px"  readonly="readonly" />
              </td>
              <td class="td_label">
                <label id="lblNationality" for="txtNtnltyDes"></label>
              </td>
              <td>
                <input type="text" id="txtNationality" formControlName="txtNationality" pInputText style="width: 100px"  readonly="readonly" />
              </td>
              <td class="td_label">
                <label id="lblGender" for="txtGender"></label>
              </td>
              <td>
                <input type="text" id="txtGender" formControlName="txtGender" pInputText style="width: 100px"  readonly="readonly" />
              </td>
              <td class="td_label">
                <label id="lblMaritalStatus" for="txtMaritalStatus"></label>
              </td>
              <td>
                <input type="text" id="txtMaritalStatus" formControlName="txtMaritalStatus" pInputText style="width: 125px"  readonly="readonly" />
              </td>
            </tr>

            <tr>
              <td class="td_label">
                <label id="lblLastEpiNo" for="txtLastEpiNo"></label>
              </td>
              <td>
                <input type="text" id="txtLastEpiNo" formControlName="txtLastEpiNo" pInputText style="width: 100px"  readonly="readonly" />
              </td>
              <td class="td_label" colspan="2">
                <label id="lblLastArraivalDate" for="txtLastArraivalDate"></label>
              </td>
              <td>
                <input type="text" id="txtLastArraivalDate" formControlName="txtLastArraivalDate" pInputText style="width: 100px;"  readonly="readonly" />
              </td>
             <td>
                <input type="text" id="txtLastArraivalTime" formControlName="txtLastArraivalTime" pInputText style="width: 100px;"  readonly="readonly" />
              </td>
              <td class="td_label">
                <label id="lblDifferedDate" for="txtDifferedDate"></label>
              </td>
              <td>
                <input type="text" id="txtDifferedDate" formControlName="txtDifferedDate" pInputText style="width: 125px;"  readonly="readonly" />
              </td>
              <td>
                <!--<label id="lblRejStatus" for="txtRejStatus"></label>-->
               <input type="text" id="txtRejStatus" formControlName="txtRejStatus" pInputText style="width: 50px;display:none;"  readonly="readonly" />
              </td>
            </tr>
          </table>
          <hr />
          <br />
          
          <table>
            <tr>
              <td class="td_label">
                <label id="lblArraivalDate"></label>
              </td>
              <td>
                <input type="text"  id="txtArraivalDateE" formControlName="txtArraivalDateE" pInputText style="width: 100px"  readonly="readonly" />

              </td>
              <td>
                <input type="text"  id="txtArraivalDateA" formControlName="txtArraivalDateA" pInputText style="width: 300px"  readonly="readonly" />
              </td>
            </tr>
            <tr>
              <td class="td_label">
                <label id="lblReason" for="ddlReason"></label>
              </td>

              <td colspan="2">
                <p-dropdown inputId="ddlReason" formControlName="ddlReason" (onChange)="reasonClick($event)" [options]="reason" optionLabel="NAME" [filter]="true" [resetFilterOnHide]="true" [style]="{'width':'100%'}"></p-dropdown>
              </td>
            </tr>
            <tr *ngIf="otherPatVisible">
              <td class="td_label">
                <label id="lblOtherPatNo" for="txtOtherPatNo">{{onLabelLoad('lblOtherPatNo')}}</label>
               
              </td>
              <td>
                <input type="text" id="txtOtherPatNo" formControlName="txtOtherPatNo" pInputText style="width: 100px" (change)="onOtherPatNoChange()" />
              </td>
              <td>
                <input  type="text" id="txtOtherPatName" formControlName="txtOtherPatName" pInputText style="width: 300px" />
              </td>
            </tr>

            <tr *ngIf="donReqNoVisible">
            
              <td class="td_label">
                <label id="lblPatDonorNo" for="ddlDonReqNo">{{onLabelLoad('lblPatDonorNo')}}</label>
              </td>

              <td colspan="2">
                <p-dropdown inputId="ddlDonReqNo" formControlName="ddlDonReqNo" (onChange)="donReqNoClick($event)" [options]="reason" optionLabel="PAT_NAME" [filter]="true" [resetFilterOnHide]="true" [style]="{'width':'100%'}"></p-dropdown>
              </td>
            </tr>
          </table>
          <br />

        </form>
      </div>
    </p-scrollPanel>
  </div>

  <div id="version">
    <span>{{ version }}</span>
  </div>

</div>

```
![OutPut](https://github.com/mizanurrhman/angularHelps/blob/main/Images/dr.JPG?raw=true)

> **Component Typescript**
```ts
import { Component, OnInit } from '@angular/core';
import { FormBuilder, FormGroup, Validators, FormControl } from '@angular/forms';
import { Router } from '@angular/router';
import { MessageService } from 'primeng/api';
import { ConfirmationService } from 'primeng/components/common/confirmationservice';
import { CommonService } from '../../../services/common.service';
import { LoginService } from '../../../services/login.service';
import { FormService } from '../../../services/form.service';
import * as $ from "jquery";
import { ButtonComponent } from '../../button/button.component';
import { T12201Service } from '../../../services/transaction/t12201.service';

@Component({
  selector: 't12201',
  templateUrl: 't12201.component.html',
  providers: [T12201Service]

})
export class T12201Component implements OnInit {
  formCode: string = 'T12201';
  lblSelect: string;
  loading: boolean = false;
  userForm: FormGroup;
  messages: any[];

  patType: string = '3';
  reason: any[];
  reasonCode: string;
  patInfo: any = [];
  colorStatus: string = 'WHITE';
  otherPatVisible: boolean = false;
  donReqNoVisible: boolean = false;

  sysDate: Date = new Date();
  arivalDateG: string = new Date().toLocaleDateString("en-GB", { year: 'numeric', month: '2-digit', day: '2-digit' });
  arivalDateH: string = new Date().toLocaleDateString("ar-SA", { year: 'numeric', month: '2-digit', day: '2-digit' });
  arraivalDate17: string;
  differedDate: any;
  donationDate: any;
  patNo: string;
  otherPatNo: string;
  donorReqNo: string;
  donorNID: string;

  donReqNoList: any[];
  episodeNo: number;
  deathDate: string;
  donationSeqNo: string;

  labelsNew: any = [];
  lblCode: string;
  lblDesEnglish: string;
  lblDesArabic: string;

  readonly: boolean = true;
  canSave: boolean;
  canUpdate: boolean;
  canDelete: boolean;
  canQuery: boolean;

  userLang: string;
  siteCode: string;
  version: string;

  constructor(private loginService: LoginService, private t12201Service: T12201Service, private formService: FormService, private router: Router, private formBuilder: FormBuilder, private confirmationService: ConfirmationService,
    private messageService: MessageService) {
    this.userForm = this.formBuilder.group({
      'rdoAutoLog': new FormControl(''),
      'rdoDirectPatient': new FormControl(''),
      'rdoNormal': new FormControl(''),
      'txtPatNo': new FormControl('', Validators.required),
      'txtPatName': new FormControl(),
      'txtYear': new FormControl(),
      'txtMonth': new FormControl(),
      'txtNationalID': new FormControl(),
      'txtNationality': new FormControl(),
      'txtGender': new FormControl(),
      'txtMaritalStatus': new FormControl(),
      'txtLastEpiNo': new FormControl(),
      'txtLastArraivalDate': new FormControl(),
      'txtLastArraivalTime': new FormControl(),
      'txtDifferedDate': new FormControl(),
      'txtRejStatus': new FormControl(),
      'txtArraivalDateE': new FormControl(),
      'txtArraivalDateA': new FormControl(),
      'ddlReason': new FormControl('', Validators.required),
      'txtOtherPatNo': new FormControl(),
      'ddlDonReqNo': new FormControl(),
      'txtOtherPatName': new FormControl()

    });
    loginService.checkIdle();
    this.userForm.get('rdoNormal').setValue(this.patType);

  }

  ngOnInit(): void {
    this.loading = true;
    this.userLang = localStorage.getItem('userLang') as string;
    this.siteCode = localStorage.getItem('siteCode') as string;

    this.formService.getAllMessage("'N0004','N0057','N0055','N0063','S0344','N0040','N0071','S0351'")
      .subscribe((success: any) => {
        this.messages = success;
      });

    this.t12201Service.getAllReason()
      .subscribe((success: any) => {
        this.reason = success;
        this.reason.splice(0, 0, { CODE: '', NAME: '' });
      });

    $('body').on('keydown', 'input', function (e) {
      var self = $(this), form = self.parents('form:eq(0)'), focusable, next;
      if (e.keyCode === 13) {
        focusable = form.find('input:enabled').filter(':visible');
        next = focusable.eq(focusable.index(this) + 1);
        if (next.length) {
          next.focus();
        }
        return false;
      }
      return true;
    });

    $('label').parent().not('[class]').addClass('td_label');
  }

  setVersion(val: string) {
    this.version = val;
  }

  setLabel(labels: any) {
    this.loading = false;
    this.labelsNew = labels;
    for (var i = 0; i < labels.length; i++) {
      try {
        switch (labels[i].T_LABEL_NAME) {
          case 'lblCode':
            this.lblCode = labels[i].T_LABEL_TEXT;
            break;
          case 'lblDesEnglish':
            this.lblDesEnglish = labels[i].T_LABEL_TEXT;
            break;
          case 'lblDesArabic':
            this.lblDesArabic = labels[i].T_LABEL_TEXT;
            break;
        }
        $('#' + labels[i].T_LABEL_NAME)[0].innerText = labels[i].T_LABEL_TEXT;
      } catch (e) {
        continue;
      }
    }
  }
  onLabelLoad(e: string) {
    try {
      return this.labelsNew.filter(a => a.T_LABEL_NAME == e)[0].T_LABEL_TEXT;
    } catch (e) {
      return '';
    }
  }
  setPermission(permissions: any) {
    if (permissions.canOpen) {
      this.canSave = permissions.canSave;
      this.canUpdate = permissions.canUpdate;
      this.canDelete = permissions.canDelete;
      this.canQuery = permissions.canQuery;
    }
    else {
      this.messageService.add({ severity: 'error', summary: 'No permission!', detail: 'You don\'t have permission to open the screen' });
      let button = new ButtonComponent(this.loginService, this.router);
      button.onBtnLogoutClick();
    }
  }
  private makeEmpty() {
    this.readonly = true;
    this.userForm.reset();
    $('#txtPatNo').focus();

  }
  onBtnNewClick() {
    this.makeEmpty();
  }
  onBtnClearClick() {
    this.makeEmpty();
  }
  onPatNoChange() {
    this.readonly = true;

    this.patNo = this.userForm.get('txtPatNo').value;
    if (this.patNo != null && this.patNo.length > 0) {
      this.userForm.get('txtPatNo').setValue(('00000000' + this.userForm.get('txtPatNo').value).slice(-8));
      this.patNo = this.userForm.get('txtPatNo').value;
    }
    this.loading = true;
    this.t12201Service.getPatInfo(this.patNo).subscribe((success: any) => {
      this.patInfo = success;
      if (success) {
        this.loading = false;

        this.patType = success["T_PAT_TYPE"];
        switch (this.patType) {
          case '1':
            this.userForm.get('rdoAutoLog').setValue(this.patType);
            break;
          case '2':
            this.userForm.get('rdoDirectPatient').setValue(this.patType);
            break;
          default:
            this.patType = '3';
            this.userForm.get('rdoNormal').setValue('3');
            break;
        }

        this.userForm.get('txtPatName').setValue(success["PAT_NAME"]);
        this.userForm.get('txtYear').setValue(success["YRS"]);
        this.userForm.get('txtMonth').setValue(success["MOS"]);
        this.userForm.get('txtNationalID').setValue(success["T_NTNLTY_ID"]);
        this.userForm.get('txtNationality').setValue(success["NATIONALITY"]);
        this.userForm.get('txtGender').setValue(success["GENDER"]);
        this.userForm.get('txtMaritalStatus').setValue(success["MRTL_STTS"]);
        this.userForm.get('txtLastEpiNo').setValue(success["LAST_EPISODE_NO"]);

        this.deathDate = success.T_DEATH_DATE != null ? new Date(Date.parse(success.T_DEATH_DATE)).toLocaleDateString("en-GB", { year: 'numeric', month: '2-digit', day: '2-digit' }) : '';
        if (this.deathDate) {
          this.messageService.add({ severity: 'error', summary: 'Error!', detail: this.messages.find(x => x.CODE == 'N0004').TEXT });
          this.readonly = false;
        }

        if (success.LAST_ARRIVAL_DATE != null)
          this.userForm.get('txtLastArraivalDate').setValue(new Date(Date.parse(success.LAST_ARRIVAL_DATE)).toLocaleDateString("en-GB", { year: 'numeric', month: '2-digit', day: '2-digit' }));

        this.userForm.get('txtLastArraivalTime').setValue(success.LAST_ARRIVAL_TIME);

        if (success.DIFFERED_DATE != null)
          this.userForm.get('txtDifferedDate').setValue(new Date(Date.parse(success.DIFFERED_DATE)).toLocaleDateString("en-GB", { year: 'numeric', month: '2-digit', day: '2-digit' }));

        this.userForm.get('txtArraivalDateE').setValue(this.arivalDateG);
        this.userForm.get('txtArraivalDateA').setValue(this.arivalDateH);

        this.donationDate = success.DONATION_DATE != null ? new Date(Date.parse(success.DONATION_DATE)).toLocaleDateString("en-GB", { year: 'numeric', month: '2-digit', day: '2-digit' }) : '';
        let unitNo = success["UNITNO"] == null ? '' : success["UNITNO"];
        let virologyresult = success["VIROLOGY_POSITIVE"];
        if (virologyresult > 0) {
          this.messageService.add({ severity: 'error', summary: 'Error!', detail: 'This Donor is rejected because of Virology Positive Result for unit:' + unitNo });
          this.readonly = false;
        }

        this.userForm.get('txtRejStatus').setValue(success["REJ_STATUS"]);
        this.colorStatus = success["COLOR_STATUS"];

        let apheresis = success.APHERESIS;
        let acceptStatus = success.ACCEPT_STATUS;
        let diffStatus = success.DIFF_STATUS;
        let rejectStatus = success.REJ_STATUS;
        this.differedDate = success.DIFFERED_DATE;
        this.donorNID = success.T_NTNLTY_ID;
        let epiNo = success.LAST_EPISODE_NO == null ? 1 : success.LAST_EPISODE_NO;
        this.episodeNo = epiNo + 1;
        this.reasonCode = success["T_DOTN_RSN_CODE"];
        this.donationSeqNo = success["T_DONATION_SEQ_NO"];
        this.otherPatNo = success["T_OTHER_PAT_NO"];
        this.donorReqNo = success["T_DON_REQNO"];

        if (success["YRS"] < 16) {
          this.messageService.add({ severity: 'error', summary: 'Error!', detail: this.messages.find(x => x.CODE == 'N0057').TEXT });
          this.readonly = false;
          this.colorStatus = "WHITE";
        }

        if (success.T_ARRIVAL_DATE != null) {
          this.arraivalDate17 = new Date(Date.parse(success.T_ARRIVAL_DATE)).toLocaleDateString("en-GB", { year: 'numeric', month: '2-digit', day: '2-digit' });
          let isSysDate = this.isSysDate(this.arraivalDate17);
          let donationStatus = success.DONATION_STATUS;

          switch (isSysDate && donationStatus) {
            case '0':
              this.messageService.add({ severity: 'error', summary: 'Error!', detail: 'This Donor Already Arrived,Go for Questionary;  Arrival Date:' + this.arraivalDate17 });
              this.readonly = false;
              break;
            case '1':
              this.messageService.add({ severity: 'error', summary: 'Error!', detail: 'This Donor Already Arrived and Questionary Completed,Go for Vital Sign;  Arrival Date:' + this.arraivalDate17 });
              this.readonly = false;
              break;
            case '2':
              this.messageService.add({ severity: 'error', summary: 'Error!', detail: 'This Donor Already Arrived and Vital Sign Completed,Go for Donation Process;  Arrival Date:' + this.arraivalDate17 });
              this.readonly = false;
              break;
            case '3':
              this.messageService.add({ severity: 'error', summary: 'Error!', detail: 'This Donor Already Arrived and Donation Completed;  Arrival Date:' + this.arraivalDate17 });
              this.readonly = false;
              break;
          }
        }

        if (apheresis == null) {
          if ((diffStatus === '2' && acceptStatus === '2') || rejectStatus === '2') {
            if (this.differedDate != null) {
              if (this.sysDate.getTime() < this.differedDate.getTime()) {
                this.messageService.add({ severity: 'error', summary: 'Error!', detail: '1.This Patient is not eligible, Next Donation Date:' + this.differedDate });
                this.readonly = false;
              }
            } else {
              let diffDay57 = this.onDateDifference(this.sysDate, new Date(success.DONATION_DATE))
              if (diffDay57 < 57) {
                let donDate = new Date(success.DONATION_DATE);
                let eligibleDate = this.onDatePastFuture(donDate, 57);
                this.messageService.add({ severity: 'error', summary: 'Error!', detail: '2.This Patient is not eligible, Next Donation Date:' + eligibleDate });
                this.readonly = false;
              }
            }
          } else if ((diffStatus === '1' && acceptStatus === '2') || rejectStatus === '1') {
            this.messageService.add({ severity: 'error', summary: 'Error!', detail: 'This Donor has Rejected Permanently' });
            this.readonly = false;
          }
          else if ((diffStatus == null && acceptStatus === '1') || rejectStatus == null) {
            let diffDay57 = this.onDateDifference(this.sysDate, new Date(this.donationDate))
            if (diffDay57 < 57) {
              let donDate = new Date(success.DONATION_DATE);
              let eligibleDate = this.onDatePastFuture(donDate, 57);
              this.messageService.add({ severity: 'error', summary: 'Error!', detail: '3.This Patient is not eligible, Next Donation Date:' + eligibleDate });
              this.readonly = false;
            }
          }
        } else {
          if (success.PLT != null && success.RBCS == null && success.PLASMA == null) {
            if (success.VA > 0) {
              this.messageService.add({ severity: 'error', summary: 'Error!', detail: 'Apheresis Donation plt.This Patient is not eligible, Last Donation Date:' + this.donationDate });
              this.readonly = false;
            } if (success.VB > 1) {
              this.messageService.add({ severity: 'error', summary: 'Error!', detail: 'Apheresis Donation plt.This Patient is not eligible, Last Donation Date:' + this.donationDate });
              this.readonly = false;
            }
          }
          else if (success.PLT != null && success.RBCS != null && success.PLASMA == null && success.VC > 0) {
            this.messageService.add({ severity: 'error', summary: 'Error!', detail: 'Apheresis Donation plt and RBC .This Patient is not eligible, Last Donation Date:' + this.donationDate });
            this.readonly = false;
          }
          else if (success.PLT != null && success.RBCS != null && success.PLASMA != null && success.VD > 0) {
            this.messageService.add({ severity: 'error', summary: 'Error!', detail: 'Apheresis Donation plt,plasma and RBC .This Patient is not eligible, Last Donation Date:' + this.donationDate });
            this.readonly = false;
          }
          else if (success.PLT != null && success.RBCS == null && success.PLASMA != null && success.VE > 0) {
            this.messageService.add({ severity: 'error', summary: 'Error!', detail: 'Apheresis Donation plt and plasma .This Patient is not eligible, Last Donation Date:' + this.donationDate });
            this.readonly = false;
          }
        }

      } else {
        this.loading = false;
        this.makeEmpty();
        this.messageService.add({ severity: 'info', summary: 'Info!', detail: this.messages.find(x => x.CODE == 'N0055').TEXT });
      }
    }, error => {
      this.loading = false;
      console.log(error);
    });
  }
  onBtnSaveClick() {

    // console.log('save button clicked ' + this.patNo);

    if (this.canSave) {
      if (this.userForm.valid) {
        if (this.patType && (this.reasonCode === '05' || this.reasonCode === '06') && !this.otherPatNo) {
          this.messageService.add({ severity: 'error', summary: 'Required', detail: 'Please Enter Other Pat No' });
          return;
        }
        this.loading = true;
        //arivalDateG, time , donationdate , status send from DAL 
        this.t12201Service.insertT12017(this.patNo, this.arivalDateG, 'arraivalTime', 'Donationdate', '0', this.donorNID, this.reasonCode, this.episodeNo.toString(),
          this.userForm.get('txtOtherPatNo').value, this.donorReqNo, this.userForm.get('txtOtherPatName').value, this.patType)
          .subscribe((success: any) => {
            this.loading = false;
            this.messageService.add({ severity: 'info', summary: 'Info!', detail: this.messages.find(x => x.CODE == 'N0040').TEXT });
            this.makeEmpty();
          },
            error => {
              this.loading = false;
              if (error.status == 400)
                this.messageService.add({ severity: 'info', summary: 'Info!', detail: this.messages.find(x => x.CODE == 'N0071').TEXT });
              else
                console.log(error);
            });
      } else {
        this.validateAllFormFields(this.userForm);
      }

    } else {
      this.messageService.add({ severity: 'error', summary: 'No permission!', detail: 'You don\'t have permission to save' });
    }
  }
  private validateAllFormFields(formGroup: FormGroup) {
    if (!formGroup.controls['txtPatNo'].valid) {
      formGroup.controls['txtPatNo'].markAsDirty();
      this.messageService.add({ severity: 'info', summary: 'Required!', detail: this.messages.find(x => x.CODE == 'S0351').TEXT });

    }
    if (!formGroup.controls['ddlReason'].valid) {
      formGroup.controls['ddlReason'].markAsDirty();

      this.messageService.add({ severity: 'info', summary: 'Required!', detail: this.messages.find(x => x.CODE == 'N0063').TEXT });
    }
  }
  rdoAutoLogClick() {
    this.patType = "1";
  };
  rdoDirectPatientClick() {
    this.patType = "2";
  };
  rdoNormalClick() {
    this.patType = "3";
  };


  reasonClick(event) {
    this.reasonCode = event.value.CODE;
    switch (this.reasonCode) {
      case '01':
        this.donReqNoVisible = true;
        this.otherPatVisible = false;
        this.t12201Service.getDonReqNoList()
          .subscribe((success: any) => {
            this.donReqNoList = success;
            this.donReqNoList.splice(0, 0, { DON_REQNO: '', PAT_NAME: '' });
          });
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
    this.userForm.get('txtOtherPatName').setValue('');
    this.userForm.get('txtOtherPatNo').setValue('');
    this.otherPatNo = '';
    this.donorReqNo = '';

  }
  onOtherPatNoChange() {
    this.otherPatNo = this.userForm.get('txtOtherPatNo').value;
    if (this.otherPatNo && this.otherPatNo.length > 0) {
      this.userForm.get('txtOtherPatNo').setValue(('00000000' + this.userForm.get('txtOtherPatNo').value).slice(-8));
      this.otherPatNo = this.userForm.get('txtOtherPatNo').value;
      this.loading = true;
      this.t12201Service.getOtherPatient(this.otherPatNo).subscribe((data) => {
        this.loading = false;

        if (data) {
          this.userForm.get('txtOtherPatName').setValue(data);
        }
        else {
          this.messageService.add({ severity: 'info', summary: 'Info!', detail: this.messages.find(x => x.CODE == 'N0055').TEXT });
          this.userForm.get('txtOtherPatName').setValue('');
          this.userForm.get('txtOtherPatNo').setValue('');
          this.otherPatNo = '';
        }
      });
    }
  }
  donReqNoClick(event) {
    this.donorReqNo = event.value.DON_REQNO;
  }

  onDateDifference(fromDate: Date, toDate: Date) {
    let diffInTime = fromDate.getTime() - toDate.getTime();
    let diffInDays = Math.round(diffInTime / (1000 * 3600 * 24));
    return diffInDays;
  }
  onDatePastFuture(startingDate: Date, rangeDay: any) {
    let date = startingDate;
    date.setDate(date.getDate() + rangeDay);
    let datePastFuture = date.getDate() + '/' + (date.getMonth() + 1) + '/' + date.getFullYear();
    return datePastFuture;
  }

  isSysDate(otherDate: string) {
    let o = otherDate.split('/');
    let oDate = new Date(Number(o[2]), Number(o[1]) - 1, Number(o[0]));

    let d = new Date();
    let currentDate = new Date((d.getMonth() + 1) + '/' + d.getDate() + '/' + d.getFullYear());

    if (oDate.getTime() === currentDate.getTime())
      return true;
    return false;
  }

}
```
> **Service Typescript**
```ts
import { Injectable } from '@angular/core';
import { HttpClient } from '@angular/common/http';
import { map } from 'rxjs/operators';


@Injectable()
export class T12201Service {
  constructor(private http: HttpClient) {
  }
  getAllReason() {
    return this.http.get('api/t12201/getAllReason').pipe(map(response => response));
  }
  getDonReqNoList() {
    return this.http.get('api/t12201/getDonReqNo').pipe(map(response => response));
  }
  
  getPatInfo(patNo: string) {
    return this.http.get('api/t12201/getPatInfo', {params: {patNo:patNo}}).pipe(map(response => response));
  }
 
  getOtherPatient(patNo: string) {
    return this.http.get('api/t12201/GetOtherPatient', { params: { patNo: patNo }, responseType: 'text' }).pipe(map(response => response));
  }

  insertT12017(patNo: string,donationDate:string, arraivalDate: string, arraivalTime: string,  bloodDonStatus: string, donorNid: string, reasonCode: string, episodeNo: string, otherPatNo: string, donorReqNo: string,otherPatName: string,patType:string) {
    let t12017 = {
      T_PAT_NO: patNo,
      T_DONATION_DATE: donationDate,
      T_ARRIVAL_DATE: arraivalDate,
      T_ARRIVAL_TIME: arraivalTime,     
      T_BLOOD_DONATION_STATUS: bloodDonStatus,
      T_DONOR_NTNLTY_ID: donorNid,
      T_DOTN_RSN_CODE: reasonCode,
      T_EPISODE_NO: episodeNo,
      T_OTHER_PAT_NO: otherPatNo,
      T_DON_REQNO: donorReqNo,
      T_OTHER_PAT_NAME: otherPatName,
      T_PAT_TYPE:patType
    };
    return this.http.post('api/t12201/insertT12017', t12017).pipe(map(response => response));
  } 
}

```
> **Controller CSharp**
```cs
using BloodBankDAL.Transaction;
using Microsoft.AspNetCore.Http;
using Microsoft.AspNetCore.Mvc;
using Microsoft.Extensions.Configuration;
using System;
using System.Collections.Generic;
using System.Linq;
using System.Threading.Tasks;
using System.Transactions;

namespace BloodBank.Controllers.Transaction
{
    public class T12201Controller : Controller
    {
        private readonly T12201DAL t12201DAL;
        public T12201Controller(IConfiguration configuration)
        {
            t12201DAL = new T12201DAL(configuration);
        }
        [HttpGet("/api/t12201/getAllReason")]
        public IActionResult GetAllReason()
        {
            var auth = t12201DAL.GetRolePermission("T12201", HttpContext.Session.GetString("ROLE_CODE"))?.T_QRY_ACC.ToString();
            if (auth is null || auth != "1") return Unauthorized();
            var data = t12201DAL.GetAllReason(HttpContext.Session.GetString("USER_LANG"));
            return Ok(data);
        }
        [HttpGet("/api/t12201/getDonReqNo")]
        public IActionResult GetDonReqNo()
        {
            var auth = t12201DAL.GetRolePermission("T12201", HttpContext.Session.GetString("ROLE_CODE"))?.T_QRY_ACC.ToString();
            if (auth is null || auth != "1") return Unauthorized();
            var data = t12201DAL.GetDonReqNo();
            return Ok(data);
        }

        [HttpGet("/api/t12201/getPatInfo")]
        public IActionResult GetPatInfo(string patNo)
        {
            var auth = t12201DAL.GetRolePermission("T12201", HttpContext.Session.GetString("ROLE_CODE"))?.T_QRY_ACC.ToString();
            if (auth is null || auth != "1") return Unauthorized();
            var data = t12201DAL.GetPatInfo(HttpContext.Session.GetString("USER_LANG"), patNo, HttpContext.Session.GetString("SITE_CODE"));
            return Ok(data);
        }

        [HttpGet("/api/t12201/GetDonorReqPatient")]
        public IActionResult GetDonorReqPatient(string donorReqNo)
        {
            var auth = t12201DAL.GetRolePermission("T12201", HttpContext.Session.GetString("ROLE_CODE"))?.T_QRY_ACC.ToString();
            if (auth is null || auth != "1") return Unauthorized();
            string data = t12201DAL.GetDonorReqPatient(HttpContext.Session.GetString("USER_LANG"), donorReqNo);
            return Ok(data);
        }

        [HttpGet("/api/t12201/GetOtherPatient")]
        public IActionResult GetOtherPatName(string patNo)
        {
            var auth = t12201DAL.GetRolePermission("T12201", HttpContext.Session.GetString("ROLE_CODE"))?.T_QRY_ACC.ToString();
            if (auth is null || auth != "1") return Unauthorized();
            string data = t12201DAL.GetOtherPatient(HttpContext.Session.GetString("USER_LANG"), patNo);
            return Ok(data);
        }

        [HttpPost("/api/t12201/insertT12017")]
        public IActionResult InsertT12017([FromBody] dynamic t12017)
        {
            var auth = t12201DAL.GetRolePermission("T12201", HttpContext.Session.GetString("ROLE_CODE"))?.T_INS_ACC.ToString();
            if (auth is null || auth != "1") return Unauthorized();
            var t12017Insert = false;
            using (var trans = new TransactionScope())
            {
                t12017Insert = t12201DAL.InsertT12017(
                    HttpContext.Session.GetString("EMP_CODE"),
                    t12017.T_PAT_NO.ToString(),
                    t12017.T_DONATION_DATE.ToString(),
                    t12017.T_ARRIVAL_DATE.ToString(),
                    t12017.T_ARRIVAL_TIME.ToString(),
                    t12017.T_BLOOD_DONATION_STATUS.ToString(),
                    t12017.T_DONOR_NTNLTY_ID.ToString(),
                    t12017.T_DOTN_RSN_CODE.ToString(),
                    t12017.T_EPISODE_NO.ToString(),
                    t12017.T_OTHER_PAT_NO.ToString(),
                    t12017.T_DON_REQNO.ToString(),
                    t12017.T_OTHER_PAT_NAME.ToString(),
                    t12017.T_PAT_TYPE.ToString(),
                    HttpContext.Session.GetString("SITE_CODE")
                    );
                if (t12017Insert)
                    trans.Complete();
                else
                    return BadRequest(new { msg = "Save failed" });
            }
            
           // var data =t12201DAL.GetPatInfo(HttpContext.Session.GetString("USER_LANG"), t12017.T_PAT_NO.ToString(), HttpContext.Session.GetString("SITE_CODE"));
            return Created("", "");
        }
    }
}

```
> **DAL CSharp**
```cs
using Microsoft.Extensions.Configuration;
using System;
using System.Collections.Generic;
using System.Linq;
using System.Text;
using System.Threading.Tasks;

namespace BloodBankDAL.Transaction
{
    public class T12201DAL : CommonDAL
    {
        public T12201DAL(IConfiguration configuration) : base(configuration)
        {
        }
        public IEnumerable<dynamic> GetAllReason(string lang)
        {
            var query = $@"SELECT T_DOTN_RSN_CODE CODE, T_LANG{lang}_NAME NAME  FROM T12006 ORDER BY 2 ";
            return QueryList<dynamic>(query);
        }
        public IEnumerable<dynamic> GetDonReqNo()
        {
            var query = $@"SELECT T_DON_REQNO DON_REQNO, T_PAT_NAME PAT_NAME FROM T12065 where T_DON_REQNO is not null ORDER BY 1 ";
            return QueryList<dynamic>(query);
        }
        public string GetOtherPatient(string lang, string patNo)
        {
            var query = $@"SELECT T_FIRST_LANG{lang}_NAME ||' '|| T_FATHER_LANG{lang}_NAME ||' '|| T_GFATHER_LANG{lang}_NAME ||' '|| T_MOTHER_LANG{lang}_NAME || ' ' || T_FAMILY_LANG{lang}_NAME T_OTHER_PAT_NAME FROM T03001 where T_PAT_NO='{patNo}'";
            return QueryString(query);
        }
        public string GetDonorReqPatient(string lang, string donorReqNo)
        {
            var query = $@"SELECT  T_PAT_NAME FROM T12065 where T_DON_REQNO='{donorReqNo}'";
            return QueryString(query);
        }
        public dynamic GetPatInfo(string lang, string patNo,string siteCode)
        {
            var query = $@"SELECT CASE WHEN T.QANS>=1 THEN 'WHITE' ELSE 
                        CASE
                          WHEN R>0 THEN 'RED'
                          WHEN R = 0 AND Y > 0 THEN 'YELLOW'
                          WHEN R = 0 AND Y = 0 AND B > 0 THEN 'BLUE' 
                          WHEN R = 0 AND Y = 0 AND B = 0 AND  G > 0 THEN 'GREEN' 
                          ELSE 'WHITE'
                        END  
                    END COLOR_STATUS,
            T.T_PAT_NO,T.T_NTNLTY_ID,T.PAT_NAME,T.YRS,T.MOS,T.T_SEX,T.GENDER, T.T_NTNLTY_CODE,T.NATIONALITY,T.MRTL_STTS,T.T_MRTL_STATUS,T.T_DEATH_DATE,
            T.DIFFERED_DATE,T.DIFF_STATUS,T.ACCEPT_STATUS ,T.DONATION_DATE ,T.T_PAT_TYPE,T.T_EPISODE_NO,T.T_DOTN_RSN_CODE,T.T_DONATION_SEQ_NO,T.T_OTHER_PAT_NO,
            T.T_OTHER_PAT_NAME,T.T_DON_REQNO,T.REJ_STATUS,T.APHERESIS ,T.PLSMA ,T.PLT ,T.RBCS,T.LAST_EPISODE_NO,T.LAST_ARRIVAL_DATE,T.LAST_ARRIVAL_TIME,
            T.T_ARRIVAL_DATE,T.DONATION_STATUS, T.QANS,T.R,T.B,T.Y, T.G ,T.VA,T.VB,T.VC,T.VD,T.VE,T.VIROLOGY_POSITIVE
            FROM (
            SELECT T03001.T_PAT_NO,T03001.T_NTNLTY_ID, T03001.T_FIRST_LANG2_NAME||' '|| T03001.T_FATHER_LANG2_NAME ||' '||T03001.T_GFATHER_LANG2_NAME ||' '|| T03001.T_FAMILY_LANG2_NAME PAT_NAME,
            TRUNC(MONTHS_BETWEEN(SYSDATE,T03001.T_BIRTH_DATE) / 12, 0) YRS,TRUNC(MOD(MONTHS_BETWEEN(SYSDATE, T03001.T_BIRTH_DATE), 12),0) MOS,T03001.T_GENDER T_SEX, 
            T02006.T_LANG2_NAME GENDER,T03001.T_NTNLTY_CODE,T02003.T_LANG2_NAME NATIONALITY,T02007.T_LANG2_NAME MRTL_STTS,T03001.T_MRTL_STATUS,T03004.T_DEATH_DATE, 
            T_DIFFERED_DATE DIFFERED_DATE,T_DIFFERED_STATUS DIFF_STATUS,T_ACCEPT_STATUS ACCEPT_STATUS ,T12017.T_DONATION_DATE DONATION_DATE,T12017.T_PAT_TYPE,T12017.T_EPISODE_NO,
            T12017.T_DOTN_RSN_CODE,T12017.T_DONATION_SEQ_NO,T12017.T_OTHER_PAT_NO,T12017.T_OTHER_PAT_NAME, T12017.T_DON_REQNO,T_REJ_STATUS REJ_STATUS,T_APHERESIS APHERESIS ,T_PLSMA PLSMA ,T_PLT PLT ,T_RBCS RBCS
            ,MAX(TO_NUMBER(T12017.T_EPISODE_NO)) LAST_EPISODE_NO, MAX(T12017.T_ARRIVAL_DATE) LAST_ARRIVAL_DATE,MAX(T12017.T_ARRIVAL_TIME) LAST_ARRIVAL_TIME,
            T12017.T_ARRIVAL_DATE,T12017.T_BLOOD_DONATION_STATUS DONATION_STATUS 
            ,(SELECT COUNT( NVL(T_QNO_ANS,1)) QANS FROM T12071 WHERE T_DONOR_PATNO='{patNo}' AND T_DONOR_EPISODE=(SELECT  MAX(TO_NUMBER(T_EPISODE_NO)) FROM T12017 WHERE T_PAT_NO='{patNo}'  AND T_SITE_CODE='{siteCode}') AND T_QNO_ANS IS  NULL) QANS
            ,(SELECT  COUNT(T_EXP_ANS) R FROM T12071 A,T12068 B WHERE A.T_QNO=B.T_QNO AND A.T_DONOR_PATNO ='{patNo}' AND A.T_DONOR_EPISODE=(SELECT  MAX(TO_NUMBER(T_EPISODE_NO)) FROM T12017 WHERE T_PAT_NO='{patNo}' AND T_SITE_CODE='{siteCode}') AND A.T_QNO_ANS IS NOT NULL AND A.T_QNO_ANS<>B.T_EXP_ANS AND  B.T_QNO IN (SELECT T_QNO FROM T12068 WHERE UPPER(T_QUS_YES_COLOR)  LIKE '%RED%'    OR UPPER(T_QUS_NO_COLOR) LIKE '%RED%'))R
            ,(SELECT  COUNT(T_EXP_ANS) B FROM T12071 A,T12068 B WHERE A.T_QNO=B.T_QNO AND A.T_DONOR_PATNO ='{patNo}' AND A.T_DONOR_EPISODE=(SELECT  MAX(TO_NUMBER(T_EPISODE_NO)) FROM T12017 WHERE T_PAT_NO='{patNo}' AND T_SITE_CODE='{siteCode}') AND A.T_QNO_ANS IS NOT NULL AND A.T_QNO_ANS<>B.T_EXP_ANS AND  B.T_QNO IN (SELECT T_QNO FROM T12068 WHERE UPPER(T_QUS_YES_COLOR)  LIKE '%BLUE%'   OR UPPER(T_QUS_NO_COLOR) LIKE '%BLUE%')) B
            ,(SELECT  COUNT(T_EXP_ANS) Y FROM T12071 A,T12068 B WHERE A.T_QNO=B.T_QNO AND A.T_DONOR_PATNO ='{patNo}' AND A.T_DONOR_EPISODE=(SELECT  MAX(TO_NUMBER(T_EPISODE_NO)) FROM T12017 WHERE T_PAT_NO='{patNo}' AND T_SITE_CODE='{siteCode}') AND A.T_QNO_ANS IS NOT NULL AND A.T_QNO_ANS<>B.T_EXP_ANS AND  B.T_QNO IN (SELECT T_QNO FROM T12068 WHERE UPPER(T_QUS_YES_COLOR)  LIKE '%YELLOW%' OR UPPER(T_QUS_NO_COLOR) LIKE '%YELLOW%')) Y
            ,(SELECT  COUNT(T_EXP_ANS) G FROM T12071 A,T12068 B WHERE A.T_QNO=B.T_QNO AND A.T_DONOR_PATNO ='{patNo}' AND A.T_DONOR_EPISODE=(SELECT  MAX(TO_NUMBER(T_EPISODE_NO)) FROM T12017 WHERE T_PAT_NO='{patNo}' AND T_SITE_CODE='{siteCode}') AND A.T_QNO_ANS IS NOT NULL AND A.T_QNO_ANS=B.T_EXP_ANS  AND  B.T_QNO IN (SELECT T_QNO FROM T12068 WHERE UPPER(T_QUS_YES_COLOR)  LIKE '%GREEN%'  OR UPPER(T_QUS_NO_COLOR) LIKE '%GREEN%'))G
            ,(SELECT COUNT(*) VA FROM T12022 WHERE T_PLT IS NOT NULL AND T_PAT_NO ='{patNo}' AND T_SITE_CODE='{siteCode}' AND T_EPISODE_NO=(SELECT NVL(MAX(TO_NUMBER(T_EPISODE_NO)),0) FROM T12017 WHERE T_PAT_NO='{patNo}' AND T_SITE_CODE='{siteCode}') AND T_DONATION_DATE>=TRUNC(SYSDATE)-2)VA
            ,(SELECT COUNT(*) VB FROM T12022 WHERE T_PLT IS NOT NULL AND T_PAT_NO ='{patNo}' AND T_SITE_CODE='{siteCode}' AND T_EPISODE_NO=(SELECT NVL(MAX(TO_NUMBER(T_EPISODE_NO)),0) FROM T12017 WHERE T_PAT_NO='{patNo}' AND T_SITE_CODE='{siteCode}') AND T_DONATION_DATE>=TRUNC(SYSDATE)-7)VB
            ,(SELECT COUNT(*) VC FROM T12022 WHERE T_PAT_NO ='{patNo}' AND T_SITE_CODE='{siteCode}' AND T_EPISODE_NO=(SELECT NVL(MAX(TO_NUMBER(T_EPISODE_NO)),0) FROM T12017  WHERE T_PAT_NO='{patNo}'  AND T_SITE_CODE='{siteCode}') AND T_DONATION_DATE>TRUNC(SYSDATE)-60)VC
            ,(SELECT COUNT(*) VD FROM T12022 WHERE T_PAT_NO ='{patNo}' AND T_SITE_CODE='{siteCode}' AND T_EPISODE_NO=(SELECT NVL(MAX(TO_NUMBER(T_EPISODE_NO)),0) FROM T12017  WHERE T_PAT_NO='{patNo}'  AND T_SITE_CODE='{siteCode}') AND T_DONATION_DATE>TRUNC(SYSDATE)-60)VD 
            ,(SELECT COUNT(*) VE FROM T12022 WHERE T_PAT_NO ='{patNo}' AND T_SITE_CODE='{siteCode}' AND T_EPISODE_NO=(SELECT NVL(MAX(TO_NUMBER(T_EPISODE_NO)),0) FROM T12017  WHERE T_PAT_NO='{patNo}'  AND T_SITE_CODE='{siteCode}') AND T_DONATION_DATE>TRUNC(SYSDATE)-30)VE
            ,(SELECT NVL(MAX(B.T_UNIT_NO),0) UNITNO FROM T12017 A,T12022 B,T12019 C WHERE A.T_PAT_NO=B.T_PAT_NO AND A.T_SITE_CODE='{siteCode}' AND A.T_SITE_CODE=B.T_SITE_CODE AND A.T_DONOR_NTNLTY_ID=T03001.T_NTNLTY_ID AND B.T_UNIT_NO=C.T_UNIT_NO AND  C.T_VIOROLOGY_RESULT ='2')VIROLOGY_POSITIVE
            FROM  T03001 INNER JOIN T02006 ON T03001.T_GENDER = T02006.T_SEX_CODE INNER JOIN T02007 ON T03001.T_MRTL_STATUS = T02007.T_MRTL_STATUS_CODE INNER JOIN T02003 ON T03001.T_NTNLTY_CODE = T02003.T_NTNLTY_CODE  
            LEFT OUTER JOIN T12017  ON T03001.T_PAT_NO = T12017.T_PAT_NO AND T12017.T_SITE_CODE='{siteCode}' LEFT OUTER JOIN T12022  ON T12017.T_PAT_NO = T12022.T_PAT_NO AND T12017.T_SITE_CODE=T12022.T_SITE_CODE AND T12017.T_EPISODE_NO = T12022.T_EPISODE_NO LEFT OUTER JOIN T03004  ON T03004.T_PAT_NO = T03001.T_PAT_NO 
            AND T12017.T_EPISODE_NO=(SELECT  MAX(TO_NUMBER(T_EPISODE_NO))FROM T12017 WHERE T_PAT_NO='{patNo}' AND T_SITE_CODE='{siteCode}')
            WHERE T03001.T_PAT_NO='{patNo}'            
            GROUP BY  T03001.T_PAT_NO, T03001.T_NTNLTY_ID, T03001.T_FIRST_LANG2_NAME||' '|| T03001.T_FATHER_LANG2_NAME ||' '||T03001.T_GFATHER_LANG2_NAME ||' '|| T03001.T_FAMILY_LANG2_NAME, T03001.T_BIRTH_DATE, T02006.T_LANG2_NAME, T03001.T_GENDER,  T03001.T_NTNLTY_CODE, T02003.T_LANG2_NAME, T02007.T_LANG2_NAME, T03001.T_MRTL_STATUS,
            T03004.T_DEATH_DATE,T_DIFFERED_DATE,T12017.T_ARRIVAL_DATE, T_DIFFERED_STATUS, T_ACCEPT_STATUS ,T12017.T_DONATION_DATE,T12017.T_PAT_TYPE,T12017.T_EPISODE_NO,T12017.T_DOTN_RSN_CODE,T12017.T_DONATION_SEQ_NO,T12017.T_OTHER_PAT_NO,T12017.T_OTHER_PAT_NAME,T12017.T_DON_REQNO ,T12017.T_BLOOD_DONATION_STATUS, T_REJ_STATUS, T_APHERESIS , T_PLSMA , T_PLT , T_RBCS
            )T  where T.T_EPISODE_NO is null or T.T_EPISODE_NO=(SELECT  MAX(TO_NUMBER(T_EPISODE_NO))FROM T12017 WHERE T_PAT_NO='{patNo}'  AND T_SITE_CODE='{siteCode}')";
            return QuerySingle<dynamic>(query);
        }

        public string GetDonationSeqNo()
        {
            var query = @"SELECT LPAD(DONATION_NO_SEQ.NEXTVAL,8,'0') T_DONATION_SEQ_NO FROM DUAL";
            return QueryString(query);
        }
        public bool InsertT12017(string T_ENTRY_USER, string T_PAT_NO, string T_DONATION_DATE, string T_ARRIVAL_DATE, string T_ARRIVAL_TIME, string   T_BLOOD_DONATION_STATUS, string T_DONOR_NTNLTY_ID, string T_DOTN_RSN_CODE, string T_EPISODE_NO, string T_OTHER_PAT_NO, string T_DON_REQNO, string T_OTHER_PAT_NAME, string T_PAT_TYPE, string T_SITE_CODE)
        {
            var donationSeqNo = GetDonationSeqNo();
        var command = $@"INSERT INTO T12017(T_ENTRY_USER,T_ENTRY_DATE,        T_PAT_NO,T_DONATION_SEQ_NO,T_DONATION_NO,T_DONATION_DATE,T_ARRIVAL_DATE,T_ARRIVAL_TIME,T_BLOOD_DONATION_STATUS,T_DONOR_NTNLTY_ID,T_DOTN_RSN_CODE,T_EPISODE_NO,T_OTHER_PAT_NO,T_DON_REQNO,T_OTHER_PAT_NAME,T_FORM_NAME,T_PAT_TYPE,T_SITE_CODE)
 VALUES('{T_ENTRY_USER}',TRUNC(SYSDATE),'{T_PAT_NO}','{donationSeqNo}','{donationSeqNo}',TRUNC(SYSDATE),TRUNC(SYSDATE),TO_CHAR(SYSDATE,'HH24MI'),'{T_BLOOD_DONATION_STATUS}','{T_DONOR_NTNLTY_ID}','{T_DOTN_RSN_CODE}','{T_EPISODE_NO}','{T_OTHER_PAT_NO}','{T_DON_REQNO}','{T_OTHER_PAT_NAME}','T12201','{T_PAT_TYPE}','{T_SITE_CODE}')";
return Command(command);
        }   
    }
}
```

> **DataBase DAL**
```cs
using Dapper;
using Microsoft.Extensions.Configuration;
using Oracle.ManagedDataAccess.Client;
using System;
using System.Collections.Generic;
using System.Data;
using System.Linq;

namespace BloodBankDAL
{
    public class DatabaseDAL
    {
        private readonly string connectionString;

        public DatabaseDAL(IConfiguration configuration)
        {
            connectionString = configuration.GetConnectionString("Default");
        }

        public IDbConnection Connection
        {
            get
            {
                return new OracleConnection(connectionString);
            }
        }

        protected T LoginQuery<T>(string query, object param)
        {
            T entity;

            using (var connection = Connection)
                entity = connection.Query<T>(query, param).SingleOrDefault();

            return entity;
        }

        protected IEnumerable<T> QueryList<T>(string query)
        {
            IList<T> entities;

            using (var connection = Connection)
                entities = connection.Query<T>(query).ToList();

            return entities;
        }

        protected T QuerySingle<T>(string query)
        {
            T entity;

            using (var connection = Connection)
                entity = connection.Query<T>(query).SingleOrDefault();

            return entity;
        }

        protected string QueryString(string query)
        {
            try
            {
                using var connection = Connection;
                return connection.QuerySingle<string>(query);
            }
            catch (InvalidOperationException)
            {
                return "";
            }
        }

        protected DataTable ReportQuery(string query)
        {
            using var connection = new OracleConnection(connectionString);
            var oracleCommand = new OracleCommand
            {
                Connection = connection,
                CommandText = query
            };
            var oracleDataAdapter = new OracleDataAdapter(oracleCommand);
            var dataTable = new DataTable();
            oracleDataAdapter.Fill(dataTable);
            return dataTable;
        }

        protected bool Command(string command)
        {
            return Connection.Execute(command) > 0;
        }

        protected bool Command(string command, object param)
        {
            return Connection.Execute(command, new { IMAGE = param }) > 0;
        }
    }
}

```

> **Header Component**
> *html Component*

```html
<link rel="stylesheet" [href]="sanitizer.bypassSecurityTrustResourceUrl(css)" />
<div id="topbarBg">
  <div id="datePanel">
    <img src="images/calender.png" alt="calender" />
    <span class="todayg">{{ todayG }}</span>
    &brvbar;
    <span class="todayh">{{ todayH }}</span>
    <span class="formInfo">{{ formInfo }}</span>
  </div>
</div>
<div id="topbarSeparator"></div>
<div id="headerBg">
  <div id="logo">
    <img src="images/ministrylogo.png" alt="logo" height="62" width="80" />
  </div>
  <div id="user">
    <img src="images/user.png" id="usericon" alt="user icon" />
  </div>
  <div id="userName">
    <span>{{ userName }}</span>
  </div>
  <div id="title">
    <span class="red">برنامج الخدمة الصحية بمقابل</span>
  </div>
</div>
<p-contextMenu *ngIf="userRole==='0001'" [global]="true" [model]="labelMenu"></p-contextMenu>
<p-dialog header="Change Label" [(visible)]="display" modal="modal" [width]="600">
  <p-table #dt [value]="data" paginator="true" [rows]="10" pageLinks="10">
    <ng-template pTemplate="header">
      <tr>
        <th>Arabic</th>
        <th>English</th>
      </tr>
    </ng-template>
    <ng-template pTemplate="body" let-rowData>
      <tr>
        <td pEditableColumn>
          <p-cellEditor>
            <ng-template pTemplate="input">
              <input type="text" [(ngModel)]="rowData.T_LANG1_TEXT">
            </ng-template>
            <ng-template pTemplate="output">
              {{rowData.T_LANG1_TEXT}}
            </ng-template>
          </p-cellEditor>
        </td>
        <td pEditableColumn>
          <p-cellEditor>
            <ng-template pTemplate="input">
              <input type="text" [(ngModel)]="rowData.T_LANG2_TEXT">
            </ng-template>
            <ng-template pTemplate="output">
              {{rowData.T_LANG2_TEXT}}
            </ng-template>
          </p-cellEditor>
        </td>
      </tr>
    </ng-template>
  </p-table>
  <p-footer>
    <button type="button" pButton icon="pi pi-check" (click)="onSaveClick()" label="Save"></button>
    <button type="button" pButton icon="pi pi-times" (click)="display=false" label="Cancel"></button>
  </p-footer>
</p-dialog>

```
> **Component TS**
```ts
import { Component, OnInit, Input, Output, EventEmitter } from '@angular/core';
import { DomSanitizer } from '@angular/platform-browser';
import { MenuItem } from 'primeng/api';
import { CommonService } from '../../services/common.service';
import { FormService } from '../../services/form.service';

@Component({
  selector: 'common-header',
  templateUrl: 'header.component.html',
  styles: ['::ng-deep .ui-menuitem-link { text-decoration: none }']
})
export class HeaderComponent implements OnInit {
  @Input() formCode: string;
  @Output() versionLoaded: EventEmitter<string> = new EventEmitter<string>();
  @Output() labelLoaded = new EventEmitter();
  @Output() permissionLoaded = new EventEmitter();
  
  data: any[];
  private labelMenu: MenuItem[];
  display = false;

  userName: string;
  userLang: string;
  userRole: string;

  css: string;

  todayG: string = new Date().toLocaleDateString("en-GB", { year: 'numeric', month: '2-digit', day: '2-digit' });
  todayH: string = new Date().toLocaleDateString("ar-SA", { year: 'numeric', month: '2-digit', day: '2-digit' });
  formInfo: string;
  version: string;

  constructor(public sanitizer: DomSanitizer, private commonService: CommonService, private formService: FormService) {
  }

  ngOnInit(): void {
    this.labelMenu = [{
      label: 'Change Label', command: (event) => {
        this.commonService.editFormLabel(this.formCode)
          .subscribe((success: any) => {
            this.data = success;
            this.display = true;
          },
            error => {
              console.log(error.error.msg);
            });
      }
    }];

    this.userName = localStorage.getItem('userName') as string;
    this.userLang = localStorage.getItem('userLang') as string;
    this.userRole = localStorage.getItem('userRole') as string;

    this.css = this.userLang == '1' ? 'css/pagearb.css' : 'css/pageeng.css';

    this.formService.getFormInfo(this.formCode)
      .subscribe((success: any) => {
        this.formInfo = this.formCode + ' - ' + (this.userLang == '1' ? success.T_LANG1_NAME : success.T_LANG2_NAME);
        this.versionLoaded.emit(success.T_VERSION_NO);
      },
        error => {
          console.log(error.error.msg);
        });

    this.formService.getFormLabel(this.formCode)
      .subscribe((success: any) => {
        this.labelLoaded.emit(success);
      },
        error => {
          console.log(error.error.msg);
        });

    this.formService.getFormPermission(this.formCode)
      .subscribe((success: any) => {
       this.permissionLoaded.emit(success);
      },
        error => {
          console.log(error.error.msg);
        });
  }

  onSaveClick() {
    this.commonService.updateFormLabel(this.data)
      .subscribe((success: any) => {
        this.labelLoaded.emit(success);
      },
        error => {
          console.log(error);
        });
    this.display = false;
  }
}

```
> **Common Service**
```ts
import { Injectable } from '@angular/core';
import { HttpClient } from '@angular/common/http';
import { map } from 'rxjs/operators'
import * as $ from "jquery";

@Injectable()
export class CommonService {
  constructor(private http: HttpClient) {
  }

  editFormLabel(formCode: string) {
    return this.http.get('api/common/editFormLabel', { params: { formCode: formCode } }).pipe(map(response => response));
  }
  updateFormLabel(t95200: any[]) {
    return this.http.post('api/common/updateFormLabel', t95200).pipe(map(response => response));
  }
  getAllZone() {
    return this.http.get('api/common/getAllZone').pipe(map(response => response));
  }
  getAllZoneByRole() {
    return this.http.get('api/common/getAllZoneByRole').pipe(map(response => response));
  }
  getAllSiteByZone(zone: string, byUser: string) {
    return this.http.get('api/common/getAllSiteByZone', { params: { zone: zone, byUser: byUser } }).pipe(map(response => response));
  }
  getMudiriaSiteByZone(zone: string) {
    return this.http.get('api/common/getMudiriaSiteByZone', { params: { zone: zone } }).pipe(map(response => response));
  }
  getNonMudiriaSiteByZone(zone: string) {
    return this.http.get('api/common/getNonMudiriaSiteByZone', { params: { zone: zone } }).pipe(map(response => response));
  }
  getAllBank() {
    return this.http.get('api/common/getAllBank').pipe(map(response => response));
  }
  getAllProfitType() {
    return this.http.get('api/common/getAllProfitType').pipe(map(response => response));
  }
  getAllExpense() {
    return this.http.get('api/common/getAllExpense').pipe(map(response => response));
  }
  getAllWorkStation() {
    return this.http.get('api/common/getAllWorkStation').pipe(map(response => response));
  }
  getAllRole() {
    return this.http.get('api/common/getAllRole').pipe(map(response => response));
  }
  convertToDateString(sDate: any) {
    var dataType = typeof sDate;
    if (dataType == "string" || sDate == null) {
      return sDate;
    }
    return (sDate.getDate() < 10 ? '0' + sDate.getDate() : sDate.getDate()) + '/' + ((sDate.getMonth() + 1) 
    < 10 ? '0' + (sDate.getMonth() + 1) : (sDate.getMonth() + 1)) + '/' + sDate.getFullYear();
  }
  convertToTimeString(sDate: any) {
    var dataType = typeof sDate;
    if (dataType == "string" || sDate == null) {
      return sDate;
    }
    var date = new Date(sDate), hours = ("0" + date.getHours()).slice(-2), minutes = ("0" + date.getMinutes()).slice(-2);
    return [hours, minutes].join(":");
  }
  convertToDateTimeString(sDate: any) {
    var dataType = typeof sDate;
    if (dataType == "string" || sDate == null) {
      return sDate;
    }
    var time = new Date(sDate), hours = ("0" + time.getHours()).slice(-2), minutes = ("0" + time.getMinutes()).slice(-2);
    var tm = [hours, minutes].join(":");
    var dt = (sDate.getDate() < 10 ? '0' + sDate.getDate() : sDate.getDate()) + '/' + ((sDate.getMonth() + 1) 
    < 10 ? '0' + (sDate.getMonth() + 1) : (sDate.getMonth() + 1)) + '/' + sDate.getFullYear();
    return dt + ' ' + tm;
  }
  convertDateToString(sDate: any) {
    if (sDate == null) {
      return sDate;
    }
    var d = new Date(sDate);
    sDate = [('0' + d.getDate()).slice(-2), ('0' + (d.getMonth() + 1)).slice(-2), d.getFullYear()].join('/');
    return sDate;
  }
  addMin(sDate: any, min: number) {
    var time = new Date(sDate);
    time.setTime(time.getTime() + min * 60 * 1000);
    return time;
  }
  getMin(sDate: any) {
    var time = new Date(sDate);
    return time.getHours() * 60 + time.getMinutes();
  }
}

```
> **FormService**

```ts
import { Injectable } from '@angular/core';
import { HttpClient } from '@angular/common/http';
import { map } from 'rxjs/operators'

@Injectable()
export class FormService {
  constructor(private http: HttpClient) {
  }

  getFormInfo(formCode: string) {
    return this.http.get('api/getFormInfo', { params: { formCode: formCode } }).pipe(map(response => response));
  }

  getFormLabel(formCode: string) {
    return this.http.get('api/getFormLabel', { params: { formCode: formCode } }).pipe(map(response => response));
  }

  getFormPermission(formCode: string) {
    return this.http.get('/api/getPermission', { params: { formCode: formCode } }).pipe(map(response => response));
  }
  getAllMessage(msgCode: string) {
   return this.http.get('/api/getAllMessage', { params: { msgCode: msgCode } }).pipe(map(response => response));
  }

}

```
> **Form Service **

```ts
import { Injectable } from '@angular/core';
import { HttpClient } from '@angular/common/http';
import { map } from 'rxjs/operators'

@Injectable()
export class FormService {
  constructor(private http: HttpClient) {
  }

  getFormInfo(formCode: string) {
    return this.http.get('api/getFormInfo', { params: { formCode: formCode } }).pipe(map(response => response));
  }

  getFormLabel(formCode: string) {
    return this.http.get('api/getFormLabel', { params: { formCode: formCode } }).pipe(map(response => response));
  }

  getFormPermission(formCode: string) {
    return this.http.get('/api/getPermission', { params: { formCode: formCode } }).pipe(map(response => response));
  }
  getAllMessage(msgCode: string) {
   return this.http.get('/api/getAllMessage', { params: { msgCode: msgCode } }).pipe(map(response => response));
  }
}

```
> **Common Controller**
```cs
using BloodBankDAL;
using Microsoft.AspNetCore.Http;
using Microsoft.AspNetCore.Mvc;
using Microsoft.Extensions.Configuration;
using System.Linq;
using System.Transactions;

namespace BloodBank.Controllers
{
    public class CommonController : Controller
    {
        private readonly CommonDAL commonDal;

        public CommonController(IConfiguration configuration)
        {
            commonDal = new CommonDAL(configuration);
        }

        [HttpGet("/api/common/editFormLabel")]
        public IActionResult EditFormLabel(string formCode)
        {
            if (!HttpContext.Session.Keys.Any()) return Unauthorized();
            var formLabel = commonDal.EditFormLabel(formCode);
            return Ok(formLabel);
        }

        [HttpPost("/api/common/updateFormLabel")]
        public IActionResult UpdateFormLabel([FromBody] dynamic t01200)
        {
            if (!HttpContext.Session.Keys.Any()) return Unauthorized();
            if (HttpContext.Session.GetString("ROLE_CODE") != "0001") return Unauthorized();
            var t01200Update = false;
            using (var trans = new TransactionScope())
            {
                foreach (var data in t01200)
                {
                    t01200Update = commonDal.UpdateFormLabel(data.T_FORM_CODE.ToString(), data.T_LABEL_NAME.ToString(),
                    data.T_LANG1_TEXT.ToString(), data.T_LANG2_TEXT.ToString());
                    if (!t01200Update)
                        break;
                }
                if (t01200Update)
                    trans.Complete();
                else
                    return BadRequest(new { msg = "فشلت عملية الحفظ" });
            }
            var formLabel = commonDal.GetFormLabel(t01200[0].T_FORM_CODE.ToString(), HttpContext.Session.GetString("USER_LANG"));
            return Created("", formLabel);
        }
    }
}
```

