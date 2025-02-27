<!DOCTYPE html>
<html lang="pt">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>Roleta de Símbolos</title>
    <style>
        body {
            display: flex;
            justify-content: center;
            align-items: center;
            height: 100vh;
            background-color: #007BFF;
            margin: 0;
        }
        .container {
            text-align: center;
            padding: 40px;
            background: white;
            border-radius: 20px;
            box-shadow: 0 6px 15px rgba(0, 0, 0, 0.3);
            max-width: 90%;
        }
        .roleta {
            font-size: 70px;
            font-weight: bold;
            width: 140px;
            height: 140px;
            display: flex;
            justify-content: center;
            align-items: center;
            margin: 30px auto;
            border: 6px solid #000;
            border-radius: 50%;
            background-color: white;
            position: relative;
            overflow: hidden;
        }
        .simbolo {
            font-size: 70px;
            color: black;
        }
        button {
            padding: 15px 30px;
            font-size: 20px;
            border: none;
            border-radius: 8px;
            cursor: pointer;
            background-color: #28a745;
            color: white;
            width: 100%;
            max-width: 300px;
        }
        button:hover {
            background-color: #218838;
        }
    </style>
</head>
<body>
    <div class="container">
        <div class="roleta" id="roleta">?</div>
        <button onclick="sortearSimbolo()">Sortear</button>
    </div>

    <script>
        const simbolos = [
            { simbolo: "★", cor: "gold" },
            { simbolo: "❤", cor: "red" },
            { simbolo: "♦", cor: "blue" },
            { simbolo: "♣", cor: "green" },
            { simbolo: "♠", cor: "black" },
            { simbolo: "⚡", cor: "yellow" },
            { simbolo: "☀", cor: "orange" },
            { simbolo: "☁", cor: "gray" }
        ];

        function sortearSimbolo() {
            const roleta = document.getElementById("roleta");
            let index = 0;
            let interval = setInterval(() => {
                roleta.innerHTML = `<span class="simbolo" style="color: ${simbolos[index].cor}">${simbolos[index].simbolo}</span>`;
                index = (index + 1) % simbolos.length;
            }, 100);

            setTimeout(() => {
                clearInterval(interval);
                setTimeout(() => {
                    const escolhido = simbolos[Math.floor(Math.random() * simbolos.length)];
                    roleta.innerHTML = `<span class="simbolo" style="color: ${escolhido.cor}">${escolhido.simbolo}</span>`;
                }, 100);
            }, 2000);
        }
    </script>
</body>
</html>
