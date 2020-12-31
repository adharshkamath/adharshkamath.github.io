---
title: Mathy Compiler Demo
description: 'Try out the Mathy Compiler with a web interface!'
date: 2020-12-07T06:43:38.000Z
tags: [OpenMP, Compiler, DSL]
---

<style type="text/css">
* {
  box-sizing: border-box;
}

.wrapper {
  max-width: 1200px;
}
.column {
  float: left;
  width: 45%;
  padding: 10px;
}

.row:after {
  content: "";
  display: table;
  clear: both;
}

@media screen and (max-width: 600px) {
  .column {
    float: left;
    width: 100%;
    padding: 10px;
    margin:0 auto;
    margin-block-end: 5%;
  }
}
</style>
Read more about the syntax and the expected output of the project [here](/projects/mathy-compiler).
<div>
Useful symbols:
<table style="margin-bottom:2%;margin-top:1%">
<tr> <td> &forall; </td>  <td>  &sum; </td>  <td>  &prod; </td>  <td>  |  </td> </tr>
</table>
</div>
<div class="row">
  <div class="column" style="float:left;text-align:center;">
    <form action="https://mathy-compiler.herokuapp.com/compile" id="codeForm" method="POST">
    <textarea name="code" form="searchForm" id="code" onkeyup="textAreaAdjust(this)" style="width:90%;height: 200px;margin:auto;" placeholder="Enter the code here..."></textarea>
    <br>
    <input type="submit" value="Compile" style="margin-inline-start:3%;margin-block-end: 1%">
    </form>
  </div>
  <div id="result" class="column" style="float:right">
    <b> <h3>OpenMP output will appear here!</h3> </b>
  </div>
</div>

### Some Examples:

(Paste these in the input box above and get the output)

<div class="row">
  <div class="column" style="float:left">
    <b> <h3>Calculating mean:</h3> </b>
	<div style="border:medium solid #333333;padding:1%">
	mean = &sum;(a[i]/100) | 0 <=i< 100
	</div>
  </div>
  <div class="column" style="float:right">
    <b> <h3>Matrix multiplication:</h3> </b>
	<div style="border:medium solid #333333;padding:1%">
	&forall;(i) | 0 <= i < 600 {<br>
    &emsp; &forall;(j) | 0 <= j <= 800 {<br>
        &emsp; &emsp; &emsp; c[i][j] = &sum;(a[i][k] * b[k][j]) | 0<= k <=200<br>
    	&emsp; &emsp; }<br>
	}<br>
	</div>
</div>

<script type="text/javascript">
$( "#codeForm" ).submit(function( event ) {
  event.preventDefault();
  $("#overlay").fadeIn(300);
  var url = document.getElementById("codeForm").getAttribute("action"),
    term = document.getElementById("code").value.trim();
    console.log(term);
  var posting = $.post( url, { code: term } );
  posting.done(function( data ) {
    $("#overlay").fadeOut(300);
    $( "#result" ).empty().append( "<b><h3>OpenMP Output:</h3>" + data + "<b>" );
  });
});
function textAreaAdjust(element) {
  element.style.height = "1px";
  element.style.height = (25+element.scrollHeight)+"px";
}
</script>

<br>
