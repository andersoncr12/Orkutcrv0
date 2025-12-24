<!DOCTYPE html>
<html lang="pt-BR">
<head>
<meta charset="UTF-8">
<title>Orkut Teste</title>
<meta name="viewport" content="width=device-width, initial-scale=1.0">
<style>
body { margin:0; font-family: Arial; background:#e6ecff; padding:20px; }
h1 { text-align:center; color:#6a5acd; }
#scraps { max-height:300px; overflow-y:auto; margin-bottom:10px; }
.scrap { background:#f1f1f1; margin:5px 0; padding:8px; border-radius:5px; }
input, button { width:100%; padding:10px; margin:5px 0; border-radius:5px; }
button { background:#6a5acd; color:white; border:none; }
</style>
</head>
<body>

<h1>💙 Orkut Teste</h1>

<div id="scraps"></div>
<input id="nome" placeholder="Seu nome">
<input id="msg" placeholder="Escreva um scrap">
<button onclick="enviar()">Enviar Scrap</button>

<script src="https://www.gstatic.com/firebasejs/9.23.0/firebase-app-compat.js"></script>
<script src="https://www.gstatic.com/firebasejs/9.23.0/firebase-firestore-compat.js"></script>

<script>
const firebaseConfig = {
  apiKey: "AIzaSyCUb2VNq9AETlzhE4w0eSwRPA4yBzrVC68",
  authDomain: "meu-50495.firebaseapp.com",
  projectId: "meu-50495",
  storageBucket: "meu-50495.firebasestorage.app",
  messagingSenderId: "941036013080",
  appId: "1:941036013080:web:61281776f379d87867a56d"
};

firebase.initializeApp(firebaseConfig);
const db = firebase.firestore();

function enviar(){
  const nomeVal = document.getElementById("nome").value || "Anonimo";
  const msgVal = document.getElementById("msg").value;
  if(msgVal.trim()=="") return;
  db.collection("scraps").add({
    nome: nomeVal,
    texto: msgVal,
    data: Date.now()
  });
  msg.value="";
}

db.collection("scraps").orderBy("data").onSnapshot(snap=>{
  scraps.innerHTML="";
  snap.forEach(doc=>{
    const data = doc.data();
    scraps.innerHTML += `<div class="scrap"><b>${data.nome}</b><br>${data.texto}</div>`;
  });
});
</script>

</body>
</html>
 # Orkutcrv0
