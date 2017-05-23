---
layout: default
permalink: /404.html
---
<form class="calc" action="javascript:alert( 'success!' );">
Address: <input type="number" class="address" value="8">-bit<br>
Data: <input type="number" class="data" value="4">-bit<br>
Storage: <input type="number" class="storage" value=""><select class="unit">
  <option value="1">B</option>
  <option value="">KB</option>
  <option value="">MB</option>
  <option value="">GB</option>
  <option value="">TB</option>
  <option value="">PB</option>
  <option value="">EB</option>
  <option value="">ZB</option>
  <option value="">YB</option>
</select><br>
<input type="submit" value="Submit">
</form>
<script src="https://ajax.googleapis.com/ajax/libs/jquery/2.1.1/jquery.min.js"></script>
<script>
var address = $('.address')[0];
var data = $('.data')[0];
var storage = $('.storage')[0];
var unit = $('.unit')[0];
var mult = 8000;
$(".calc").submit(function(event) {
//storage=data*2^(address)
//log(storage/data)/log(2)=address
//data=storage/(2^(address))
//address=Math.log(storage/data)/Math.log(2)
if(address.value == ""){
address.value = Math.log((storage.value*mult)/data.value)/Math.log(2)
}
if(data.value == ""){
data.value = (storage.value*mult)/(2^(address.value))
}
if(storage.value == ""){
storage.value = (data.value*2^(address.value))/mult;
}
});
</script>
