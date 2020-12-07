---
title: Mathy Compiler Demo
description: 'Try out the Mathy Compiler with a web interface! Detailed post coming up soon!'
date: 2020-12-07T06:43:38.000Z
tags: [OpenMP, Compiler, DSL]
---

<style>
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

<div class="row">
  <div class="column" style="background-color:#aaa;float:left;text-align:center;">
    <form action="http://127.0.0.1:5000/compile" id="codeForm" method="POST">
    <textarea name="code" form="searchForm" id="code" onkeyup="textAreaAdjust(this)" style="width:90%;height: 200px;margin:auto;" placeholder="Enter the code here..."></textarea>
    <br>
    <input type="submit" value="Compile" style="margin-inline-start:3%;margin-block-end: 1%">
    </form>
  </div>
  <div id="result" class="column" style="background-color:#bbb;float:right">
    <b> <h3>OpenMP Output:</h3> </b>
  </div>
</div>

<script>
$( "#codeForm" ).submit(function( event ) {
  event.preventDefault();
  var url = document.getElementById("codeForm").getAttribute("action"),
    term = document.getElementById("code").value.trim();
    console.log(term);
  var posting = $.post( url, { code: term } );
  posting.done(function( data ) {
    $( "#result" ).empty().append( "<b><h3>OpenMP Output:</h3>" + data + "<b>" );
  });
});
function textAreaAdjust(element) {
  element.style.height = "1px";
  element.style.height = (25+element.scrollHeight)+"px";
}
</script>
