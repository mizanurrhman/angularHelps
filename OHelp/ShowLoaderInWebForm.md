## How to Show loading gif image in html form 


> Create style inside `head`
```html
<style type="text/css">
  #load {
      width: 100%;
      height: 100%;
      position: fixed;
      z-index: 9999;
      background: url("images/working.gif") no-repeat center center rgba(0,0,0,0.25);
      display:none;
  }
 </style>
```
> `showLoader()` function inside `head` 

```html 
 <script>
   function showLoader() {
            document.getElementById("load").style.display = 'block';
        }    
    </script>
```

> Place a `div` with id `load` inside `form` under `body` tag 

```html
 <div id="load">
 </div>
```
> Cal `ShowLoader()` function from button `onclick` event    

```html
 <button id="btnLogin" runat="server" onserverclick="btnLogin_ServerClick" onclick="showLoader();">
  <img src="<%= VirtualPathUtility.ToAbsolute("~/images/login.png") %>" />
   Login
 </button>
```

![Loding...](https://github.com/mizanurrhman/angularHelps/blob/main/Images/ShowLoadingHtm.JPG "OutPut")
