---
layout: default
permalink: /404.html
---
<form class="calc" action="javascript:null;">
Data: <input type="text" class="data" value="8">-bit<br>
Address: <input type="text" class="address" value="4">-bit<br>
Storage: <input type="text" class="storage" value=""><select class="unit">
  <optgroup label="Binary">
  <option value="2 0">bits</option>
  <option value="2 3">B</option>
  <option value="2 13">KiB </option>
  <option value="2 23">MiB</option>
  <option value="2 33">GiB</option>
  <option value="2 43">TiB</option>
  <option value="2 53">PiB</option>
  <option value="2 63">EiB</option>
  <option value="2 73">ZiB</option>
  <option value="2 83">YiB</option>
  </optgroup>
  <optgroup label="Decimal">
  <option value="1000 1">KB</option>
  <option value="1000 2">MB</option>
  <option value="1000 3">GB</option>
  <option value="1000 4">TB</option>
  <option value="1000 5">PB</option>
  <option value="1000 6">EB</option>
  <option value="1000 7">ZB</option>
  <option value="1000 8">YB</option>
  </optgroup>
  <optgroup label="Other">
  <option value="custom">Custom</option>
  </optgroup>
  </select><br>
  <span class="custom">Custom </span>Multiplyer: <input type="text" class="custom" value=""><br>
<input type="submit" class="calc-data" value="Calculate Data"><input type="submit" class="calc-add" value="Calculate Address"><input type="submit" class="calc-storage" value="Calculate Storage">
</form>
<script src="https://ajax.googleapis.com/ajax/libs/jquery/2.1.1/jquery.min.js"></script>
<script>
var simpleCustom = false;

$('span.custom').hide();
var address = $('.address')[0];
var data = $('.data')[0];
var storage = $('.storage')[0];
var unit = $('.unit')[0];
var custom = $('input.custom')[0];
if(simpleCustom){
custom.value = Math.pow(parseFloat(this.value.split(" ")[0]),parseFloat(this.value.split(" ")[1]));
}
else {
custom.value = unit.value;
}
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
var mult;
if(unit.value=="custom"){

if(simpleCustom){
mult = parseFloat(custom.value)
}
else{
mult = Math.pow(parseFloat(custom.value.split(" ")[0]),parseFloat(unit.value.split(" ")[1]));
}

return mult;
}
else{
mult = Math.pow(parseFloat(unit.value.split(" ")[0]),parseFloat(custom.value.split(" ")[1]));
return mult;
}
}
$('.unit').on('change', function() {
  if(this.value=="custom"){
  console.log("custom");
  $('span.custom').show();
  }
  else{
  if(simpleCustom){
  custom.value = Math.pow(parseFloat(this.value.split(" ")[0]),parseFloat(this.value.split(" ")[1]));
  }
  else{
  custom.value = this.value;
  }
  $('span.custom').hide();
  }
})

$('.custom').on('input', function() {
unit.value = "custom";
console.log("custom");
$('span.custom').show();
})
</script>
