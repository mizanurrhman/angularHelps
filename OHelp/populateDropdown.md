> **Populate a dropdownLis from Database**

> Html Code 
```html
<p-dropdown inputId="ddlReason" formControlName="ddlReason" (onChange)="reasonClick($event)"
[options]="reason" optionLabel="NAME" [filter]="true" [resetFilterOnHide]="true" [style]="{'width':'100%'}">
</p-dropdown>
```
* `reason: any[];` data stored this list come from DB and from this list dropdown will bind data to 
* `[options]="reason"` option propery
> **TypeScript**
```ts
this.t12201Service.getAllReason()
      .subscribe((success: any) => {
        this.reason = success;
        this.reason.splice(0, 0, { CODE: '', NAME: '' });
      });
```
> **Call service** `this.t12201Service.getAllReason()` from `service.ts`
```ts
 getAllReason() {
    return this.http.get('api/t12201/getAllReason').pipe(map(response => response));
  }
```
> **Service call Controller** 
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
> Get data from DAL called by controller 
```cs
public IEnumerable<dynamic> GetAllReason(string lang)
{
  var query = $@"SELECT T_DOTN_RSN_CODE CODE, T_LANG{lang}_NAME NAME  FROM T12006 ORDER BY 2 ";
  return QueryList<dynamic>(query);
}
```
> QueryList Method
```cs
protected IEnumerable<T> QueryList<T>(string query)
{
  IList<T> entities;
  using (var connection = Connection)
  entities = connection.Query<T>(query).ToList();
  return entities;
}
```
