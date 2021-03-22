> **Show Alert Message from Database**
>> Data From DB DAL

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
 > Cal controller from Service(FormService)
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
 this.messageService.add({ severity: 'info', summary: 'Info!', detail: this.messages.find
 (x => x.CODE == 'N0057').TEXT });
```
