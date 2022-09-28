#  Personal Notes
My notes for coding... 

## JavaScript pass JSON through parameter's function 

```
// function to call 
function panggil(a,b){
  console.log(a);
  console.log(b);
}

// call function in js
panggil('data',{var1: "value 2", var2: 123});
``` 
To call function inside HTML need little hack using 
&#39  for single quote ' 
&quot; for double quote "

Suggest do not use &apos; because it will not work on html4 or old browser. 

Call function with JSON inside HTML 
```
// data from js
<script>
var data = {var1: "value 2", var2: 123};
</script>

// load in html 
<button onclick="panggil(' + index.row + ',' + JSON.stringify(data).replace(/'/g, '&#39').replace(/"/g, '&quot;')+')">Button</button>

```
