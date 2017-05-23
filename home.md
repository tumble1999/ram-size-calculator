---
layout: default
permalink: /404.html
---
<form class="calc">
Address: <input type="number"class="address" value="8">-bit<br>
Data: <input type="number" class="data" value="4">-bit<br>
Storage: <input type="number"class="storage" value="">-bit<br>
<input type="submit" value="Submit">
</form>
<script src="https://ajax.googleapis.com/ajax/libs/jquery/2.1.1/jquery.min.js"></script>
<script>
$(".calc").submit(function(event) {
alert("hello");
});
</script>
