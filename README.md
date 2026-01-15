<!DOCTYPE html>
<html lang="pt-br">
<head>
<meta charset="UTF-8">
<meta name="viewport" content="width=device-width, initial-scale=1.0">
<title>Aviator Hacker</title>

<style>
body {
    margin: 0;
    background: black;
    color: #00ff00;
    font-family: Arial, sans-serif;
    text-align: center;
}

.container {
    padding: 30px;
}

#plane {
    font-size: 60px;
    color: red;
    margin-bottom: 10px;
}

#status {
    font-size: 28px;
    margin: 20px;
}

#crash {
    font-size: 48px;
    font-weight: bold;
    color: #00ff00;
}

button {
    padding: 15px 40px;
    font-size: 18px;
    background: #00aa00;
    color: black;
    border: none;
    border-radius: 10px;
    cursor: pointer;
}

button:disabled {
    background: #033;
}

.history {
    margin-top: 25px;
    background: #050505;
    padding: 15px;
    border-radius: 10px;
}

.history span {
    margin: 6px;
    display: inline-block;
    color: #00ff00;
}
</style>
</head>

<body>
<div class="container">

    <div id="plane">✈️</div>

    <div id="status">Pronto para iniciar</div>

    <div id="crash"></div>

    <button id="startBtn">Iniciar</button>

    <div class="history">
        <h3>Histórico</h3>
        <div id="historyList"></div>
    </div>

</div>

<script>
const startBtn = document.getElementById("startBtn");
const statusEl = document.getElementById("status");
const crashEl = document.getElementById("crash");
const historyList = document.getElementById("historyList");

let history = [];

function gerarCrash() {
    const r = Math.random();
    if (r < 0.6) return (1 + Math.random() * 2).toFixed(2);
    if (r < 0.9) return (3 + Math.random() * 7).toFixed(2);
    return (10 + Math.random() * 200).toFixed(2);
}

function iniciar() {
    startBtn.disabled = true;
    crashEl.innerText = "";
    
    statusEl.innerHTML = "🧑‍💻 Calculando sinal...";

    setTimeout(() => {
        const resultado = gerarCrash();

        crashEl.innerText = resultado + "x";
        statusEl.innerText = "Resultado do crash:";
        
        history.unshift(resultado + "x");
        if (history.length > 10) history.pop();
        atualizarHistorico();

        startBtn.disabled = false;
    }, 5000);
}

function atualizarHistorico() {
    historyList.innerHTML = "";
    history.forEach(v => {
        const span = document.createElement("span");
        span.innerText = v;
        historyList.appendChild(span);
    });
}

startBtn.addEventListener("click", iniciar);
</script>
</body>
</html>

