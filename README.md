<!DOCTYPE html>
<html>
<head>
  <title>Monitoring IoT</title>
  <meta name="viewport" content="width=device-width, initial-scale=1">
  <style>
    body { font-family: Arial; text-align: center; }
    table { margin: auto; border-collapse: collapse; }
    td, th { border: 1px solid black; padding: 8px; }
    button { padding: 10px; margin: 5px; }
  </style>
</head>
<body>

<h2>📡 Monitoring ESP32</h2>

<button onclick="start()">START</button>
<button onclick="stop()">STOP</button>

<table id="tabel"></table>

<script>
let interval;

function ambilData() {
  fetch("https://script.google.com/macros/s/AKfycbxgIg20epuwEqKGnZrBq-WY1Sjj-YY9iO9OLZrzUl6QgnAAnBxqANninVAW25D1S1nq/exec")
  .then(res => res.json())
  .then(data => {
    let table = document.getElementById("tabel");
    table.innerHTML = "";

    data.forEach(row => {
      let tr = "<tr>";
      row.forEach(cell => {
        tr += "<td>" + cell + "</td>";
      });
      tr += "</tr>";
      table.innerHTML += tr;
    });
  });
}

function start() {
  interval = setInterval(ambilData, 3000);
}

function stop() {
  clearInterval(interval);
}
</script>

</body>
</html>
