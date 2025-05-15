<html lang="pt-BR">
<head>
    <meta charset="UTF-8">
    <title>Itini Completo</title>
    <style>
        * { box-sizing: border-box; margin: 0; padding: 0; font-family: 'Segoe UI', Tahoma, sans-serif; }
        body { background: #f5f5f5; }
        .hidden { display: none; }

        .container { max-width: 400px; margin: 100px auto; padding: 30px; background: white; border-radius: 12px; box-shadow: 0 4px 15px rgba(0,0,0,0.1); }
        h2 { text-align: center; margin-bottom: 20px; }
        input, button { width: 100%; padding: 10px; margin-top: 10px; border-radius: 8px; border: 1px solid #ccc; }
        button { background: #4a90e2; color: white; border: none; font-weight: bold; cursor: pointer; }
        button:hover { background: #357bd8; }
        .link { text-align: center; margin-top: 15px; }
        .link a { color: #4a90e2; text-decoration: none; }
        .link a:hover { text-decoration: underline; }

        .chat-box { height: 300px; overflow-y: auto; border: 1px solid #ccc; padding: 10px; border-radius: 8px; background: #fff; margin-bottom: 10px; }
        .message { margin-bottom: 10px; display: flex; align-items: center; }
        .message img { width: 32px; height: 32px; border-radius: 50%; margin-right: 10px; border: 1px solid #ccc; object-fit: cover; }

        .chatgpt-layout { display: flex; flex-direction: column; height: 100vh; }
        .chatgpt-header { background: #202123; color: white; padding: 15px; font-size: 20px; font-weight: bold; }
        .chatgpt-main { flex: 1; overflow-y: auto; padding: 20px; background: #343541; color: white; }
        .chatgpt-input { padding: 15px; background: #202123; display: flex; gap: 10px; }
        .chatgpt-input input { flex: 1; padding: 12px; border-radius: 8px; border: none; }
        .chatgpt-input button { width: 100px; border-radius: 8px; background: #4a90e2; color: white; }
    </style>
</head>
<body>

<div class="container" id="loginTela">
    <h2>Login</h2>
    <input type="email" id="loginEmail" placeholder="E-mail">
    <input type="password" id="loginSenha" placeholder="Senha">
    <button onclick="fazerLogin()">Entrar</button>
    <div class="link">
        <a href="#" onclick="mostrarCadastro()">Criar uma conta</a>
    </div>
</div>

<div class="container hidden" id="cadastroTela">
    <h2>Criar Conta</h2>
    <input type="text" id="nome" placeholder="Nome">
    <input type="email" id="email" placeholder="E-mail">
    <input type="password" id="senha" placeholder="Senha">
    <input type="password" id="confirmar" placeholder="Confirmar Senha">
    <button onclick="fazerCadastro()">Cadastrar</button>
</div>

<div class="container hidden" id="modoSimples">
    <h2>Modo Simples</h2>
    <div class="chat-box" id="chatSimples"></div>
    <input type="text" id="inputSimples" placeholder="Mensagem...">
    <button onclick="enviarMensagem('simples')">Enviar</button>
    <button onclick="tentarAdm()">Modo Adm</button>
</div>

<div class="container hidden" id="fotoPerfilTela">
    <h2>Foto de Perfil</h2>
    <input type="file" id="fotoInput" accept="image/*">
    <button onclick="salvarFoto()">Ir para Modo Plus</button>
</div>

<div class="container hidden" id="plusTela">
    <h2>Itini Plus</h2>
    <div class="chat-box" id="chatPlus"></div>
    <input type="text" id="inputPlus" placeholder="Mensagem...">
    <button onclick="enviarMensagem('plus')">Enviar</button>
    <button onclick="tentarHiperPlus()">Modo Hiper Plus</button>
</div>

<script>
    let fotoBase64 = '';
    const botAvatar = 'https://cdn-icons-png.flaticon.com/512/4712/4712107.png';
    let usuarioLogado = null; // Variável para rastrear o usuário logado

    function mostrarCadastro() {
        document.getElementById('loginTela').classList.add('hidden');
        document.getElementById('cadastroTela').classList.remove('hidden');
    }

    function fazerLogin() {
        const email = document.getElementById('loginEmail').value;
        const senha = document.getElementById('loginSenha').value;

        // Aqui você implementaria a lógica real de verificação de login
        // (comparando com dados armazenados, por exemplo).
        // Por enquanto, vamos simular um login bem-sucedido para qualquer entrada.
        if (email && senha) {
            usuarioLogado = { email: email }; // Simula o usuário logado
            document.getElementById('loginTela').classList.add('hidden');
            document.getElementById('modoSimples').classList.remove('hidden');
        } else {
            alert('Por favor, preencha todos os campos.');
        }
    }

    function fazerCadastro() {
        const senha = document.getElementById('senha').value;
        const confirmar = document.getElementById('confirmar').value;
        const nome = document.getElementById('nome').value;
        const email = document.getElementById('email').value;

        if (!nome || !email || !senha || !confirmar) {
            return alert('Por favor, preencha todos os campos para o cadastro.');
        }

        if (senha !== confirmar) {
            return alert('Senhas não coincidem!');
        }

        // Aqui você implementaria a lógica para salvar os dados do novo usuário
        // (em um banco de dados, por exemplo).
        alert(`Usuário ${nome} cadastrado com sucesso!`);

        document.getElementById('cadastroTela').classList.add('hidden');
        document.getElementById('modoSimples').classList.remove('hidden');
        usuarioLogado = { email: email, nome: nome }; // Simula o usuário logado após o cadastro
    }

    function tentarAdm() {
        const senha = prompt('Senha do Modo Adm:');
        if (senha === 'Victor top') {
            document.getElementById('modoSimples').classList.add('hidden');
            document.getElementById('fotoPerfilTela').classList.remove('hidden');
        } else {
            alert('Senha incorreta!');
        }
    }

    function salvarFoto() {
        const file = document.getElementById('fotoInput').files[0];
        if (!file) return alert('Escolha uma foto!');
        const reader = new FileReader();
        reader.onload = function (e) {
            fotoBase64 = e.target.result;
            document.getElementById('fotoPerfilTela').classList.add('hidden');
            document.getElementById('plusTela').classList.remove('hidden');
        };
        reader.readAsDataURL(file);
    }

    function enviarMensagem(modo) {
        const inputId = modo === 'plus' ? 'inputPlus' : 'inputSimples';
        const chatId = modo === 'plus' ? 'chatPlus' : 'chatSimples';
        const input = document.getElementById(inputId);
        const chat = document.getElementById(chatId);
        const msg = input.value.trim();
        if (!msg) return;

        let mensagemUsuario = `<div class="message"><strong>Você:</strong> ${msg}</div>`;
        if (modo === 'plus' && fotoBase64) {
            mensagemUsuario = `<div class="message"><img src="${fotoBase64}"><strong>Você:</strong> ${msg}</div>`;
        }

        chat.innerHTML += mensagemUsuario;
        chat.innerHTML += `<div class="message"><img src="${botAvatar}"><strong>Itini:</strong> ${msg}</div>`;

        input.value = '';
        chat.scrollTop = chat.scrollHeight;
    }

    function tentarHiperPlus() {
        const senha = prompt('Senha do Modo Hiper Plus:');
        if (senha === 'victortop2') {
            abrirHiperPlus();
        } else {
            alert('Senha incorreta!');
        }
    }

    function abrirHiperPlus() {
        document.body.innerHTML = `
            <div class="chatgpt-layout">
                <div class="chatgpt-header">Itini Hiper Plus</div>
                <div id="hiperChat" class="chatgpt-main"></div>
                <div class="chatgpt-input">
                    <input type="text" id="inputHiper" placeholder="Digite aqui...">
                    <button onclick="enviarMensagemHiper()">Enviar</button>
                </div>
            </div>
        `;
    }

    function enviarMensagemHiper() {
        const input = document.getElementById('inputHiper');
        const chat = document.getElementById('hiperChat');
        const msg = input.value.trim();
        if (!msg) return;

        let mensagemUsuario = `
            <div style="display: flex; align-items: center; margin-bottom: 10px;">
                <img src="${fotoBase64}" style="width:32px; height:32px; border-radius:50%; margin-right:10px;">
                <span><strong>Você:</strong> ${msg}</span>
            </div>
        `;
        if (!fotoBase64) {
            mensagemUsuario = `
                <div style="margin-bottom: 10px;">
                    <span><strong>Você:</strong> ${msg}</span>
                </div>
            `;
        }

        chat.innerHTML += mensagemUsuario;
        chat.innerHTML += `
            <div style="display: flex; align-items: center; margin-bottom: 10px;">
                <img src="${botAvatar}" style="width:32px; height:32px; border-radius:50%; margin-right:10px;">
                <span><strong>Itini:</strong> ${msg}</span>
            </div>
        `;
        input.value = '';
        chat.scrollTop = chat.scrollHeight;
    }
</script>

</body>
</html>
