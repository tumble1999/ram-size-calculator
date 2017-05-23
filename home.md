---
layout: default
permalink: /404.html
---
<form class="calc" action="javascript:null;">
Data: <input type="text" class="data" value="8">-bit<br>
Address: <input type="text" class="address" value="4">-bit<br>
Storage: <input type="text" class="storage" value=""><select class="unit">
<option value="0.125">bits</option>
  <option value="1">B</option>
  <option value="1,024">KB</option>
  <option value="1,048,576">MB</option>
  <option value="1,073,741,824">GB</option>
  <option value="1,099,511,627,776">TB</option>
  <option value="1,125,899,906,842,624">PB</option>
  <option value="1,152,921,504,606,846,976">EB</option>
  <option value="1,180,591,620,717,411,303,424">ZB</option>
  <option value="1,208,925,819,614,629,174,706,176">YB</option>
</select><br>
<input type="submit" class="calc-add" value="Calculate Address"><input type="submit" class="calc-data" value="Calculate Data"><input type="submit" class="calc-storage" value="Calculate Storage">
</form>
<script src="https://ajax.googleapis.com/ajax/libs/jquery/2.1.1/jquery.min.js"></script>
<script>
var address = $('.address')[0];
var data = $('.data')[0];
var storage = $('.storage')[0];
var unit = $('.unit')[0];
//storage=data*2^(address)
//log(storage/data)/log(2)=address
//data=storage/(2^(address))
//address=Math.log(storage/data)/Math.log(2)


$(".calc-add").click(function(event) {
var mult=8*parseFloat(unit.value);
address.value = (Math.log((mult*parseFloat(storage.value))/parseFloat(data.value)))/(Math.log(2))
});

$(".calc-data").click(function(event) {
var mult=8*parseFloat(unit.value);
data.value = parseFloat(storage.value)*mult*(2^(-parseFloat(address.value)));
});

$(".calc-storage").click(function(event) {
var mult=8*parseFloat(unit.value);
storage.value = (parseFloat(data.value)*2^(parseFloat(address.value)))/mult;
});
</script>
