<!DOCTYPE html>
<html lang="pt">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>Minha Loja de Roupas Online</title>
    <style>
        /* CSS - Estilo Geral */
        body { font-family: 'Segoe UI', sans-serif; background-color: #f0f2f5; margin: 0; padding: 0; color: #333; }
        header { background-color: #000; color: white; padding: 40px 20px; text-align: center; }
        
        /* Catálogo */
        .container { max-width: 1100px; margin: 20px auto; padding: 20px; }
        .catalogo { 
            display: grid; 
            grid-template-columns: repeat(auto-fit, minmax(250px, 1fr)); 
            gap: 25px; 
        }

        .cartao-produto { 
            background: white; border-radius: 15px; padding: 20px; text-align: center;
            box-shadow: 0 4px 12px rgba(0,0,0,0.08); transition: 0.3s;
        }
        .cartao-produto:hover { transform: translateY(-8px); box-shadow: 0 8px 20px rgba(0,0,0,0.15); }
        
        .preco { color: #27ae60; font-size: 1.4rem; font-weight: bold; margin: 10px 0; }
        .categoria { color: #999; font-size: 0.8rem; text-transform: uppercase; letter-spacing: 1px; }
        
        /* Botões */
        button { 
            background-color: #000; color: white; border: none; padding: 12px 25px; 
            border-radius: 25px; cursor: pointer; font-weight: 600; width: 100%; transition: 0.3s;
        }
        button:hover { background-color: #444; }

        /* Formulário */
        .seccao-pedido { background: white; margin-top: 50px; padding: 40px; border-radius: 15px; box-shadow: 0 4px 15px rgba(0,0,0,0.1); }
        .campo { margin-bottom: 15px; text-align: left; }
        label { display: block; margin-bottom: 5px; font-weight: bold; }
        input, select { width: 100%; padding: 12px; border: 1px solid #ddd; border-radius: 8px; box-sizing: border-box; }

        /* WhatsApp Floating Button */
        .btn-whatsapp {
            position: fixed; bottom: 20px; right: 20px; background-color: #25d366;
            color: white; padding: 15px 25px; border-radius: 50px; text-decoration: none;
            font-weight: bold; box-shadow: 0 4px 10px rgba(0,0,0,0.3); z-index: 1000;
        }
    </style>
</head>
<body>

    <header>
        <h1>LOUJABDE ROUPAS</h1>
        <p>As melhores tendências para o seu estilo</p>
    </header>

    <div class="container">
        <h2 style="text-align: center;">Nosso Catálogo</h2>
        <div id="lista-produtos" class="catalogo"></div>

        <div id="pedido" class="seccao-pedido">
            <h2 style="text-align: center;">Finalizar Pedido</h2>
            <form action="https://formspree.io/f/TEU_EMAIL_AQUI" method="POST">
                <div class="campo">
                    <label>Nome Completo:</label>
                    <input type="text" name="nome" placeholder="Seu nome" required>
                </div>
                <div class="campo">
                    <label>Peça Desejada:</label>
                    <input type="text" id="produto-selecionado" name="produto" readonly style="background-color: #eee;">
                </div>
                <div class="campo">
                    <label>Tamanho:</label>
                    <select name="tamanho">
                        <option>S</option><option>M</option><option>L</option><option>XL</option>
                    </select>
                </div>
                <div class="campo">
                    <label>Seu E-mail para contacto:</label>
                    <input type="email" name="email" required>
                </div>
                <button type="submit" style="background-color: #e67e22;">Enviar Pedido por E-mail</button>
            </form>
        </div>
    </div>

    <a href="https://wa.me/TEU_NUMERO_AQUI" class="btn-whatsapp" target="_blank">Falar no WhatsApp</a>

    <script>
        // Dados dos produtos
        const produtos = [
            { nome: "Vestido Floral", preco: 29.90, categoria: "Feminino" },
            { nome: "T-Shirt Básica", preco: 15.00, categoria: "Unissexo" },
            { nome: "Calças Jeans", preco: 39.99, categoria: "Masculino" },
            { nome: "Casaco Inverno", preco: 55.00, categoria: "Inverno" }
        ];

        // Função para carregar os produtos no HTML
        function carregarProdutos() {
            const divCatalogo = document.getElementById('lista-produtos');
            produtos.forEach(p => {
                divCatalogo.innerHTML += `
                    <div class="cartao-produto">
                        <span class="categoria">${p.categoria}</span>
                        <h3>${p.nome}</h3>
                        <p class="preco">${p.preco.toFixed(2)}€</p>
                        <button onclick="escolherProduto('${p.nome}')">Encomendar</button>
                    </div>
                `;
            });
        }

        // Função para preencher o formulário automaticamente
        function escolherProduto(nome) {
            document.getElementById('produto-selecionado').value = nome;
            document.getElementById('pedido').scrollIntoView({ behavior: 'smooth' });
        }

        // Iniciar
        carregarProdutos();
    </script>
</body>
</html>
