# Publish application in IIS

 * First put Published folder to a drive location into server/pc
1. Go `IIS Manager`  
2. Expand `Sites` 
3. `Right click` on Default Website > Add Application 
4. Write the name of Application like `WebLabCommandControl` in Alias text box 
5. `DefaultAppPoll` it should be framework 4.0 , if that no need to change it 
6. `Physical Path` will be the path of publish folder 
7. After click Ok `WebLabCommandControl` will added to Default Website list in left side ,click on it
8. Double Click on Default Document and click Add then write Login.aspx and click ok
Now you can Browse 
Note :If you change the `default app pool` then go to `Application Pools` from left side then select specific application pool then click `Advanced Setting` then Enable 32-bit Application =True  
