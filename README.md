# trolagemseguran-a

<!DOCTYPE html>
<html lang="pt-BR">
<head>
<meta charset="UTF-8">
<title>Secure Terminal Access</title>
<style>
body {
  background: black;
  color: #00ff00;
  font-family: monospace;
  font-size: 18px;
  padding: 20px;
  overflow: hidden;
}

#terminal {
  white-space: pre-line;
}

.cursor {
  display: inline-block;
  width: 10px;
  background: #00ff00;
  animation: blink 1s infinite;
}

@keyframes blink {
  0%, 50%, 100% { opacity: 1; }
  25%, 75% { opacity: 0; }
}

#countdown {
  color: red;
  font-size: 22px;
  margin-top: 20px;
}

#final {
  display: none;
  font-size: 28px;
  color: yellow;
  margin-top: 40px;
}
</style>
</head>
<body>

<div id="terminal"></div><span class="cursor"></span>
<div id="countdown"></div>

<div id="final">
  seloco, to zuando, fica dboa<br><br>
  <br>
  
</div>

<audio id="typeSound" src="https://www.soundjay.com/mechanical/keyboard-1.mp3"></audio>

<script>
const terminal = document.getElementById("terminal");
const typeSound = document.getElementById("typeSound");
const countdownDiv = document.getElementById("countdown");

function fakeIP() {
  return `${rand(10,255)}.${rand(0,255)}.${rand(0,255)}.${rand(0,255)}`;
}

function rand(min, max) {
  return Math.floor(Math.random() * (max - min) + min);
}

function fakeLocation() {
  const cidades = ["São Paulo"];
  return cidades[rand(0, cidades.length)];
}

function fakeDevice() {
  const devices = ["Android", "iPhone",];
  return devices[rand(0, devices.length)];
}

const lines = [
  "Inicializando exploit remoto...",
  "Bypassando criptografia SSL...",
  "Estabelecendo túnel seguro...",
  "IP detectado: " + fakeIP(),
  "Localização aproximada: " + fakeLocation(),
  "Dispositivo identificado: " + fakeDevice(),
  "Acessando câmera frontal...",
  "Extraindo fotos da galeria...",
  "Copiando lista de contatos...",
  "Interceptando mensagens privadas...",
  "Instalando acesso persistente...",
  "",
  "ACESSO ROOT CONCEDIDO."
];

let i = 0;

function typeLine() {
  if (i < lines.length) {
    let text = lines[i];
    let j = 0;

    let interval = setInterval(() => {
      terminal.innerHTML += text[j];
      typeSound.currentTime = 0;
      typeSound.play();
      j++;

      if (j >= text.length) {
        clearInterval(interval);
        terminal.innerHTML += "\n";
        i++;
        setTimeout(typeLine, 500);
      }
    }, 25);
  } else {
    startCountdown();
  }
}

function startCountdown() {
  let time = 5;
  countdownDiv.innerHTML = "Enviando dados em: " + time;

  let timer = setInterval(() => {
    time--;
    countdownDiv.innerHTML = "Enviando dados em: " + time;

    if (time <= 0) {
      clearInterval(timer);
      reveal();
    }
  }, 1000);
}

function reveal() {
  document.querySelector(".cursor").style.display = "none";
  countdownDiv.innerHTML = "";
  document.getElementById("final").style.display = "block";
}

typeLine();
</script>

</body>
</html>
