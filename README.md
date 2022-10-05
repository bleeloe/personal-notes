#  Javascript function collection for Web Development
My notes for coding... 

## JavaScript pass JSON through parameter's function 

```javascript
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
```html
// data from js
<script>
var data2 = {var1: "value 2", var2: 123};
var new_data = JSON.stringify(data2).replace(/'/g, '&#39').replace(/"/g, '&quot;');

var button = '<button onclick="panggil(&#39data&#39,' + new_data + ')"><i class="fa fa-eye"></i></button>';

</script>

// load in html 
<button onclick="panggil('' new data)">Button</button>

```



### SUM column on table 
sum html table easy with this function 
```javascript
function sumColumn(classSum,idTarget,callback){
    var row = document.getElementsByClassName(classSum), sum = 0;
    for(var i = 0; i < row.length; i++)
    {
        var val = row.item(i).value || 0;
        sum += parseFloat(val);
    }        
    if (isNaN(sum)||sum ==='') {
        sum = 0;
    }
    if(typeof callback == "function"){
        document.getElementById(idTarget).innerHTML = callback(sum) ;
    }else{
        document.getElementById(idTarget).innerHTML = sum ;
    }
    return sum;        
};
```



### Window PopUp on center 
```javascript
window.popup = function (url, title, width, height) {
    var left = (window.screen.width / 2) - ((width / 2) + 0 );
    var top = (window.screen.height / 2) - ((height / 2) + 50);
    var win = window.open(url,title,
    "status=no,height=" + height + ",width=" + width + ",resizable=yes,left="
    + left + ",top=" + top + ",screenX=" + left + ",screenY="
    + top + ",toolbar=no,menubar=no,scrollbars=no,location=no,directories=no");    
};
```



### Dynamic table 
copy everyting on row with easy
```javascript
function addRow(tableID,setEmpty,selector) {
    tableID = (typeof tableID !== 'undefined') ?  tableID : '';
    setEmpty = (typeof setEmpty !== 'undefined') ?  setEmpty : true;
    selector = (typeof selector !== 'undefined') ? selector : 'input,select';
    var table=document.getElementById(tableID).getElementsByTagName('tbody')[0];
    var rowCount=table.rows.length;    
    var row=table.insertRow(rowCount);
    var colCount=table.rows[0].cells.length;
    for (var i=0; i < colCount; i++) {
        var newcell=row.insertCell(i);
        newcell.innerHTML=table.rows[0].cells[i].innerHTML;  
        if (setEmpty) {
            getInput = newcell.querySelectorAll(selector);
            for (let loop = 0; loop < getInput.length; loop++) {
                const element = getInput[loop];
                element.value = 0;
            }
            // for (var x = 0; x < newcell.childNodes.length; x++) {
            //     switch (newcell.childNodes[x].type) {
            //     case "text":
            //         newcell.childNodes[x].value='';
            //         break;
            //     case "hidden":
            //         newcell.childNodes[x].value='';
            //         break;
            //     case "date":
            //         newcell.childNodes[x].value='';
            //         break;
            //     case "number":
            //         newcell.childNodes[x].value='';
            //         break;
            //     case "checkbox":
            //         newcell.childNodes[x].checked=false;
            //         break;
            //     case "select-one":
            //         newcell.childNodes[x].selectedIndex=x;
            //         break;
            //     }
            // }
        }
    }
    return row;
}
function deleteRow(tableID, rowMin) {
    tableID = (typeof tableID !== 'undefined')? tableID:'';
    rowMin = (typeof rowMin !== 'undefined') ? rowMin:1; 
    try {
        var table=document.getElementById(tableID).getElementsByTagName('tbody')[0];
        var rowCount=table.rows.length - 1;
        for (var i=rowCount; 0 < i; i--) {
            var row=table.rows[i];
            if (rowCount < rowMin) {
                console.log("Cannot delete all the rows.");
                break;
            }
            table.deleteRow(i);
            rowCount++;
            i++;            
            break;
        }
    } catch (e) {
        alert(e);
    }
}
```



### Paste Number Only 
```javascript
$('#app').on('keyup', '.clean_paste_number',function(){
	var r = $(this).val().replace(/[^\d.-]/g,'');
	$(this).val(r);
})
```




### Display Servertime Realtime
write server time to `<span id="servertime"><?php echo $servertime ?></span>` then put these JS 
```javascript
var currenttime = document.getElementById("servertime").innerHTML;
var montharray = new Array("Jan","Feb","Mar","Apr","Mei","Jun","Jul","Agus","Sep","Okt","Nov","Des");
var serverdate = new Date(currenttime);
function padlength(what){
    var output=(what.toString().length==1)? "0"+what : what;
    return output;
}
function displaytime(){
    serverdate.setSeconds(serverdate.getSeconds() + 1);
    var datestring = padlength(serverdate.getDate()) + " "+ montharray[serverdate.getMonth()]+" "+serverdate.getFullYear();
    var timestring=padlength(serverdate.getHours())+":"+padlength(serverdate.getMinutes())+":"+padlength(serverdate.getSeconds());
    document.getElementById("servertime").innerHTML=datestring+" "+timestring;
}
window.onload=function(){
    setInterval("displaytime()", 1000);
}
```

### Click Input selection focus 
select text when click the input 
```javascript
$("#app").on('click focus','input.click-focus',function () {      
   ($(this).val() == 0) ? $(this).val('') : ''; $(this).select();
});
$("#app").on('blur', 'input.click-focus', function () {
   ($(this).val() == 0) ? $(this).val(0) : '';   
});
```

