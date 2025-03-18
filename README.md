//Rosilaine
<!DOCTYPE html>
<html lang="pt-BR">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>Busca de Usuário</title>
    <style>
        body { font-family: Arial, sans-serif; text-align: center; margin-top: 50px; }
        input, button { padding: 10px; margin: 5px; }
        #resultado { margin-top: 20px; font-weight: bold; }
    </style>
</head>
<body>
    <h2>Buscar Usuário por ID</h2>
    <input type="number" id="userId" placeholder="Digite o ID do usuário">
    <button onclick="buscarUsuario()">Buscar</button>
    <div id="resultado"></div>
    
    <script>
        async function buscarUsuario() {
            const userId = document.getElementById('userId').value;
            const resultado = document.getElementById('resultado');
            resultado.innerHTML = '';

            if (!userId) {
                resultado.innerHTML = 'Por favor, insira um ID válido.';
                return;
            }

            try {
                const response = await fetch(`https://jsonplaceholder.typicode.com/users/${userId}`);
                if (!response.ok) {
                    throw new Error('Usuário não encontrado');
                }
                const usuario = await response.json();
                resultado.innerHTML = `Nome: ${usuario.name} <br> Email: ${usuario.email} <br> Telefone: ${usuario.phone}`;
            } catch (error) {
                resultado.innerHTML = 'Usuário não encontrado';
            }
        }
    </script>
</body>
</html>

