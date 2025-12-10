# Alice
Bot Whartsap
<!doctype html>
<html>
<head>
  <meta charset="utf-8">
  <title>Alice-IA | Panel du Bot WhatsApp</title>
  <style>
    body {
      font-family: Arial, sans-serif;
      max-width: 800px;
      margin: 40px auto;
      padding: 20px;
      background: #f1f1f1;
    }
    h1 {
      text-align: center;
      color: #333;
    }
    .card {
      background: white;
      padding: 20px;
      border-radius: 12px;
      box-shadow: 0 0 10px rgba(0,0,0,0.1);
      margin-top: 30px;
    }
    input, textarea {
      width: 100%;
      padding: 12px;
      margin: 10px 0;
      border: 1px solid #ccc;
      border-radius: 8px;
    }
    button {
      background: #25D366;
      color: white;
      padding: 12px 20px;
      font-size: 16px;
      border: none;
      border-radius: 8px;
      cursor: pointer;
      width: 100%;
    }
    button:hover {
      background: #1c9e4d;
    }
    #log {
      background: #f9f9f9;
      padding: 15px;
      border-radius: 8px;
      margin-top: 20px;
      white-space: pre-wrap;
    }
  </style>
</head>
<body>

  <h1>🌟 Alice-IA : Panneau de Contrôle</h1>

  <div class="card">
    <h2>Envoyer un message via Alice (Bot WhatsApp)</h2>

    <label>Numéro WhatsApp du destinataire :</label>
    <input id="to" placeholder="Ex : 2250700000000">

    <label>Message :</label>
    <textarea id="message" rows="5">Bonjour ! Ceci est un message envoyé avec Alice 🤖</textarea>

    <button onclick="sendMessage()">Envoyer le message</button>

    <div id="log">En attente…</div>
  </div>

  <script>
    async function sendMessage() {
      const to = document.getElementById("to").value.trim();
      const message = document.getElementById("message").value.trim();
      const log = document.getElementById("log");

      if (!to || !message) {
        alert("Remplis tous les champs !");
        return;
      }

      log.innerText = "Envoi du message…";

      try {
        const response = await fetch("https://TON_BACKEND_URL/send", {
          method: "POST",
          headers: { "Content-Type": "application/x-www-form-urlencoded" },
          body: new URLSearchParams({ to, message })
        });

        const data = await response.json();
        log.innerText = JSON.stringify(data, null, 2);

      } catch (err) {
        log.innerText = "Erreur : " + err.message;
      }
    }
  </script>

</body>
</html>
