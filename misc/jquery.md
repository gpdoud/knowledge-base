# jQuery

## AJAX methods

$.getJSON(url).done(..).fail(..);

$.ajax({
  method:"POST",
  url: "http://localhost:xxxxx/api/..",
  data: JSON.stringify(json),
  contentType: "application/json"
}).done(..).fail(..);

## Other HTML

$("#id").val(0);
let name = $("#name").val();
let bool = $("#bool").prop("checked", true);
