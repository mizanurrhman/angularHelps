> Example of Ternary Operator
```ts
const person = {name: 'Becky',gender: null}
```
* Value is present

`const name = person.name ?? 'Unknown person' ` OutPut: Becky
 
 * Value is not present 
 
`const gender = person.gender ?? 'Unknown gender'` OutPut: Unknown gender 

* Get conditional value  

`const name = person.name=='Becky' ? 'This is Becky' :'I am not Becky '` OutPut: `This is Becky`

   
