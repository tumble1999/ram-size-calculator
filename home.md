---
layout: default
permalink: /404.html
---
<form class="calc" action="javascript:null;">
Data: <input type="text" class="data" value="8">-bit<br>
Address: <input type="text" class="address" value="4">-bit<br>
Storage: <input type="text" class="storage" value=""><select class="unit">
  <option value="0.125">bits</option>
  <option value="1 0">B</option>
  <option value="1024">KB</option>
  <option value="1048576">MB</option>
  <option value="1073741824">GB</option>
  <option value="1099511627776">TB</option>
  <option value="1125899906842624">PB</option>
  <option value="1152921504606846976">EB</option>
  <option value="1180591620717411303424">ZB</option>
  <option value="1208925819614629174706176">YB</option>
</select><br>
<input type="submit" class="calc-data" value="Calculate Data"><input type="submit" class="calc-add" value="Calculate Address"><input type="submit" class="calc-storage" value="Calculate Storage">
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
address.value = (Math.log((getMult()*parseFloat(storage.value))/parseFloat(data.value)))/(Math.log(2))
});

$(".calc-data").click(function(event) {
data.value = parseFloat(storage.value)*getMult()*( Math.pow(2,-parseFloat(address.value) ) );
});

$(".calc-storage").click(function(event) {
storage.value = (parseFloat(data.value)*Math.pow( 2,parseFloat(address.value))  )/getMult();
});

function getMult() {
return Math.pow(parseFloat(unit.value.split(" ")[0]) ,parseFloat(unit.value.split(" ")[1]));
}
</script>
