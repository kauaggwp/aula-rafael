<!DOCTYPE html>
<html lang="pt-BR">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>Gerador de Senha Forte</title>
    <style>
        body {
            font-family: Arial, sans-serif;
            display: flex;
            justify-content: center;
            align-items: center;
            min-height: 100vh;
            margin: 0;
            background-color: #f5f5f5;
        }
        .container {
            background-color: #fff;
            padding: 20px;
            border-radius: 8px;
            box-shadow: 0 0 10px rgba(0, 0, 0, 0.1);
            text-align: center;
            width: 300px;
        }
        .container h1 {
            margin: 0 0 20px;
        }
        .options {
            text-align: left;
            margin-bottom: 20px;
        }
        .options label {
            display: block;
            margin-bottom: 10px;
        }
        .password-output {
            font-weight: bold;
            font-size: 1.2em;
            margin: 20px 0;
            color: #333;
        }
        button {
            background-color: #4CAF50;
            color: white;
            padding: 10px 20px;
            border: none;
            border-radius: 5px;
            cursor: pointer;
        }
        button:hover {
            background-color: #45a049;
        }
    </style>
</head>
<body>

<div class="container">
    <h1>Gerador de Senha Forte</h1>
    <div class="options">
        <label>
            Comprimento da senha:
            <input type="number" id="length" value="12" min="6" max="30">
        </label>
        <label>
            <input type="checkbox" id="uppercase" checked> Incluir Letras Maiúsculas
        </label>
        <label>
            <input type="checkbox" id="lowercase" checked> Incluir Letras Minúsculas
        </label>
        <label>
            <input type="checkbox" id="numbers" checked> Incluir Números
        </label>
        <label>
            <input type="checkbox" id="symbols" checked> Incluir Símbolos
        </label>
    </div>
    <button onclick="generatePassword()">Gerar Senha</button>
    <div class="password-output" id="passwordOutput">Clique para gerar uma senha</div>
</div>

<script>
    function generatePassword() {
        const length = document.getElementById('length').value;
        const includeUppercase = document.getElementById('uppercase').checked;
        const includeLowercase = document.getElementById('lowercase').checked;
        const includeNumbers = document.getElementById('numbers').checked;
        const includeSymbols = document.getElementById('symbols').checked;

        const uppercaseChars = "ABCDEFGHIJKLMNOPQRSTUVWXYZ";
        const lowercaseChars = "abcdefghijklmnopqrstuvwxyz";
        const numberChars = "0123456789";
        const symbolChars = "!@#$%^&*()_+[]{}|;:,.<>?";

        let availableChars = "";
        if (includeUppercase) availableChars += uppercaseChars;
        if (includeLowercase) availableChars += lowercaseChars;
        if (includeNumbers) availableChars += numberChars;
        if (includeSymbols) availableChars += symbolChars;

        if (availableChars === "") {
            document.getElementById('passwordOutput').textContent = "Selecione ao menos uma opção!";
            return;
        }

        let password = "";
        for (let i = 0; i < length; i++) {
            const randomIndex = Math.floor(Math.random() * availableChars.length);
            password += availableChars[randomIndex];
        }

        document.getElementById('passwordOutput').textContent = password;
    }
</script>

</body>
</html>
