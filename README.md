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

Call function with JSON with HTML 
```
// data from js
<script>
var data2 = {var1: "value 2", var2: 123};
var new_data = JSON.stringify(data2).replace(/'/g, '&#39').replace(/"/g, '&quot;');

var button = '<button onclick="panggil(&#39data&#39,' + new_data + ')"><i class="fa fa-eye"></i></button>';

</script>

// load in html 
<button onclick="panggil('' new data)">Button</button>

```
