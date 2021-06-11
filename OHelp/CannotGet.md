#### Error `cannot Get /` !!

> Go Inside ClientApp folder run **`PowerShell`** enter command **`ng build`** 
> It'll show the specific Error
> if not able to run above `ng build` Take the script error then go link provided and see the solution, 
> todays case *`Set-ExecutionPolicy -ExecutionPolicy RemoteSigned -Scope CurrentUser`*  
> then run again **`ng build`**

When delete node_modules , global  
```
npm install --force 
ng build --prod
```
If not found angular cli 
```
npm install --save-dev @angular/cli@latest`
npm install -g  @angular/cli@latest 
ng serve
```
> Bootstrap
Error : Cannot find module '@schematics/angular/utility/parse-name'
```
npm cache clean
npm install @schematics/angular@12.0.4
```
* Worked `ng add @ng-bootstrap/ng-bootstrap`      

