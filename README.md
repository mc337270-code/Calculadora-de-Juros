<!DOCTYPE html>
<html lang="pt-br">
<head>
  <meta charset="UTF-8">
  <title>Calculadora de Juros Compostos</title>
  <style>
    body {
      background: #0a0a0a;
      color: #00ff88;
      font-family: Arial, sans-serif;
      display: flex;
      justify-content: center;
      align-items: center;
      height: 100vh;
    }

    .container {
      background: #111;
      padding: 25px;
      border-radius: 15px;
      box-shadow: 0 0 20px #00ff88;
      width: 300px;
      text-align: center;
    }

    h2 {
      margin-bottom: 20px;
    }

    input {
      width: 90%;
      padding: 10px;
      margin: 8px 0;
      border: none;
      border-radius: 8px;
      background: #000;
      color: #00ff88;
      outline: none;
      text-align: center;
    }

    button {
      background: #00ff88;
      color: #000;
      border: none;
      padding: 10px;
      margin: 5px;
      border-radius: 8px;
      cursor: pointer;
      font-weight: bold;
      width: 45%;
    }

    button:hover {
      background: #00cc66;
    }

    .resultado {
      margin-top: 15px;
      text-align: left;
    }
  </style>
</head>

<body>

<div class="container">
  <h2>💚 Calculadora de Juros</h2>

  <input type="number" id="valor" placeholder="Valor mensal (R$)">
  <input type="number" id="taxa" placeholder="Taxa (%)">
  <input type="number" id="meses" placeholder="Meses">

  <div>
    <button onclick="calcular()">Calcular</button>
    <button onclick="limpar()">Limpar</button>
  </div>

  <div class="resultado" id="resultado"></div>
</div>

<script>
function calcular() {
  let valor = parseFloat(document.getElementById("valor").value);
  let taxa = parseFloat(document.getElementById("taxa").value) / 100;
  let meses = parseInt(document.getElementById("meses").value);

  if (!valor || !taxa || !meses) {
    alert("Preencha todos os campos!");
    return;
  }

  let montante = 0;

  for (let i = 0; i < meses; i++) {
    montante = (montante + valor) * (1 + taxa);
  }

  let total = valor * meses;
  let juros = montante - total;

  document.getElementById("resultado").innerHTML =
    `<p>💰 Total investido: R$ ${total.toFixed(2)}</p>
     <p>📈 Juros ganhos: R$ ${juros.toFixed(2)}</p>
     <p>🏦 Montante final: R$ ${montante.toFixed(2)}</p>`;
}

function limpar() {
  document.getElementById("valor").value = "";
  document.getElementById("taxa").value = "";
  document.getElementById("meses").value = "";
  document.getElementById("resultado").innerHTML = "";
}
</script>

</body>
</html>
