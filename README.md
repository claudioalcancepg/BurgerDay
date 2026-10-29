<!DOCTYPE html>
<html lang="pt-BR">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>Day Burger - Pedidos</title>
    <style>
        :root {
            --primary-color: #e50914;
            --secondary-color: #ff3b30;
            --dark-color: #121212;
            --card-bg: #1e1e1e;
            --text-color: #ffffff;
            --text-muted: #b3b3b3;
            --accent: #ff9800;
        }

        * {
            margin: 0;
            padding: 0;
            box-sizing: border-box;
            font-family: 'Segoe UI', Tahoma, Geneva, Verdana, sans-serif;
        }

        body {
            background-color: var(--dark-color);
            color: var(--text-color);
            padding-bottom: 50px;
        }

        header {
            background: linear-gradient(135deg, #1a0505 0%, #2b0808 100%);
            border-bottom: 3px solid var(--primary-color);
            padding: 20px 15px;
            text-align: center;
        }

        header h1 {
            color: var(--primary-color);
            font-size: 2.2rem;
            text-transform: uppercase;
            letter-spacing: 2px;
            margin-bottom: 5px;
            text-shadow: 2px 2px 4px rgba(0,0,0,0.5);
        }

        header p {
            color: var(--text-muted);
            font-size: 0.95rem;
        }

        .container {
            max-width: 500px;
            margin: 20px auto;
            padding: 0 15px;
        }

        .card {
            background-color: var(--card-bg);
            border-radius: 12px;
            overflow: hidden;
            box-shadow: 0 8px 20px rgba(0,0,0,0.6);
            border: 1px solid #333;
            margin-bottom: 20px;
        }

        .product-image {
            width: 100%;
            height: auto;
            display: block;
            border-bottom: 2px solid var(--primary-color);
        }

        .product-details {
            padding: 20px;
        }

        .product-title {
            font-size: 1.4rem;
            margin-bottom: 8px;
            color: #fff;
        }

        .product-desc {
            color: var(--text-muted);
            font-size: 0.9rem;
            margin-bottom: 15px;
            line-height: 1.4;
        }

        .product-price {
            font-size: 1.6rem;
            color: var(--accent);
            font-weight: bold;
            margin-bottom: 20px;
        }

        .quantity-control {
            display: flex;
            align-items: center;
            justify-content: space-between;
            background: #2a2a2a;
            padding: 10px 15px;
            border-radius: 8px;
            margin-bottom: 20px;
        }

        .quantity-control label {
            font-weight: bold;
            font-size: 1rem;
        }

        .qty-btns {
            display: flex;
            align-items: center;
            gap: 15px;
        }

        .qty-btns button {
            background: var(--primary-color);
            color: white;
            border: none;
            width: 35px;
            height: 35px;
            border-radius: 50%;
            font-size: 1.2rem;
            cursor: pointer;
            transition: 0.2s;
            display: flex;
            align-items: center;
            justify-content: center;
        }

        .qty-btns button:active {
            transform: scale(0.9);
        }

        #qty-value {
            font-size: 1.2rem;
            font-weight: bold;
            min-width: 20px;
            text-align: center;
        }

        .section-title {
            font-size: 1.1rem;
            margin-bottom: 10px;
            color: var(--primary-color);
            border-left: 4px solid var(--primary-color);
            padding-left: 8px;
        }

        .form-group {
            margin-bottom: 15px;
        }

        .form-group label {
            display: block;
            margin-bottom: 5px;
            font-size: 0.9rem;
            color: var(--text-muted);
        }

        .form-group input, .form-group textarea, .form-group select {
            width: 100%;
            padding: 12px;
            border-radius: 8px;
            border: 1px solid #444;
            background-color: #2a2a2a;
            color: white;
            font-size: 1rem;
        }

        .form-group input:focus, .form-group textarea:focus, .form-group select:focus {
            border-color: var(--primary-color);
            outline: none;
        }

        .payment-options {
            display: grid;
            grid-template-columns: repeat(3, 1fr);
            gap: 10px;
            margin-bottom: 15px;
        }

        .payment-option {
            background-color: #2a2a2a;
            border: 2px solid #444;
            border-radius: 8px;
            padding: 12px 5px;
            text-align: center;
            cursor: pointer;
            font-size: 0.9rem;
            font-weight: bold;
            transition: 0.2s;
        }

        .payment-option.selected {
            border-color: var(--primary-color);
            background-color: rgba(229, 9, 20, 0.15);
            color: var(--primary-color);
        }

        #pix-box {
            display: none;
            background: #252525;
            border: 1px dashed var(--accent);
            padding: 15px;
            border-radius: 8px;
            margin-bottom: 15px;
            text-align: center;
        }

        #pix-box p {
            font-size: 0.85rem;
            color: var(--text-muted);
            margin-bottom: 8px;
        }

        .pix-key-display {
            background: #121212;
            padding: 10px;
            border-radius: 6px;
            font-family: monospace;
            font-size: 0.95rem;
            color: var(--accent);
            margin-bottom: 10px;
            word-break: break-all;
        }

        .btn-copy {
            background: var(--accent);
            color: #000;
            border: none;
            padding: 8px 15px;
            border-radius: 5px;
            font-weight: bold;
            cursor: pointer;
            font-size: 0.85rem;
        }

        .btn-copy:active {
            opacity: 0.8;
        }

        .summary-box {
            background: #252525;
            padding: 15px;
            border-radius: 8px;
            margin-bottom: 20px;
        }

        .summary-row {
            display: flex;
            justify-content: space-between;
            margin-bottom: 8px;
            font-size: 0.95rem;
        }

        .summary-row.total {
            font-size: 1.2rem;
            font-weight: bold;
            color: var(--accent);
            border-top: 1px solid #444;
            padding-top: 8px;
            margin-top: 8px;
        }

        .btn-whatsapp {
            width: 100%;
            background-color: #25d366;
            color: white;
            border: none;
            padding: 15px;
            border-radius: 8px;
            font-size: 1.1rem;
            font-weight: bold;
            cursor: pointer;
            display: flex;
            align-items: center;
            justify-content: center;
            gap: 10px;
            box-shadow: 0 4px 10px rgba(37, 211, 102, 0.3);
            transition: 0.2s;
        }

        .btn-whatsapp:hover {
            background-color: #20ba5a;
        }

        .pickup-badge {
            background: rgba(255, 152, 0, 0.15);
            color: var(--accent);
            border: 1px solid var(--accent);
            padding: 12px;
            border-radius: 8px;
            text-align: center;
            font-size: 0.9rem;
            font-weight: bold;
            margin-bottom: 20px;
            line-height: 1.4;
        }
    </style>
</head>
<body>

    <header>
        <h1>Day Burger</h1>
        <p>Faça seu pedido e retire no balcão!</p>
        <p style="font-size: 0.85rem; color: #ff9800; margin-top: 5px; font-weight: bold;">⏰ Retiradas a partir das 19:30h</p>
        <p style="font-size: 0.8rem; color: var(--text-muted); margin-top: 3px;">Contato: (42) 98815-0451</p>
    </header>

    <div class="container">
        
        <!-- Cartão do Produto Único -->
        <div class="card">
            <img src="clássico burger + batata_be99ba.png" alt="Combo Dia de Hambúrguer" class="product-image">
            <div class="product-details">
                <h2 class="product-title">Dia de Hambúrguer</h2>
                <p class="product-desc">Clássico Burger + Batata + Coca Zero 200ml (Feito na brasa)</p>
                <div class="product-price">R$ 30,00</div>

                <div class="quantity-control">
                    <label>Quantidade:</label>
                    <div class="qty-btns">
                        <button onclick="mudarQtd(-1)">-</button>
                        <span id="qty-value">1</span>
                        <button onclick="mudarQtd(1)">+</button>
                    </div>
                </div>
            </div>
        </div>

        <div class="pickup-badge">
            📍 Modalidade Exclusiva: RETIRADA NO LOCAL<br>
            <small style="font-weight: normal; color: #fff;">⏰ As retiradas ocorrem <b>após as 19:30h</b></small>
        </div>

        <!-- Formulário do Cliente -->
        <div class="card" style="padding: 20px;">
            <h3 class="section-title">Seus Dados</h3>
            
            <div class="form-group">
                <label>Seu Nome *</label>
                <input type="text" id="nome" placeholder="Digite seu nome completo">
            </div>

            <div class="form-group">
                <label>Telefone / WhatsApp *</label>
                <input type="tel" id="telefone" placeholder="(42) 99999-9999">
            </div>

            <div class="form-group">
                <label>Horário de Retirada (a partir das 19:30h) *</label>
                <input type="time" id="horario" min="19:30" value="19:30">
            </div>

            <div class="form-group">
                <label>Observações do Pedido</label>
                <textarea id="obs" rows="2" placeholder="Ex: Sem cebola, pão bem selado..."></textarea>
            </div>

            <h3 class="section-title" style="margin-top: 20px;">Forma de Pagamento</h3>
            
            <div class="payment-options">
                <div class="payment-option selected" onclick="selecionarPagamento('Pix')">Pix</div>
                <div class="payment-option" onclick="selecionarPagamento('Cartão')">Cartão</div>
                <div class="payment-option" onclick="selecionarPagamento('Dinheiro')">Dinheiro</div>
            </div>

            <!-- Caixa Pix -->
            <div id="pix-box" style="display: block;">
                <p>Chave Pix (E-mail):</p>
                <div class="pix-key-display" id="pix-key-text">capg@alcancepontagrossa.com.br</div>
                <button class="btn-copy" onclick="copiarChavePix()">Copiar Chave Pix</button>
            </div>

            <!-- Resumo do Pedido -->
            <div class="summary-box">
                <div class="summary-row">
                    <span>Combos (<span id="summary-qtd">1</span>x):</span>
                    <span>R$ <span id="summary-subtotal">30,00</span></span>
                </div>
                <div class="summary-row total">
                    <span>Total a Pagar:</span>
                    <span>R$ <span id="summary-total">30,00</span></span>
                </div>
            </div>

            <!-- Botão Enviar WhatsApp -->
            <button class="btn-whatsapp" onclick="enviarPedido()">
                📲 Enviar Pedido via WhatsApp
            </button>
        </div>

    </div>

    <script>
        const PRECO_COMBO = 30.00;
        const SEU_NUMERO_WHATSAPP = "5542988150451";
        let quantidade = 1;
        let formaPagamentoSelecionada = "Pix";

        function mudarQtd(mudanca) {
            quantidade += mudanca;
            if (quantidade < 1) quantidade = 1;
            
            document.getElementById('qty-value').innerText = quantidade;
            document.getElementById('summary-qtd').innerText = quantidade;
            
            let total = quantidade * PRECO_COMBO;
            document.getElementById('summary-subtotal').innerText = total.toFixed(2).replace('.', ',');
            document.getElementById('summary-total').innerText = total.toFixed(2).replace('.', ',');
        }

        function selecionarPagamento(metodo) {
            formaPagamentoSelecionada = metodo;
            
            const opcoes = document.querySelectorAll('.payment-option');
            opcoes.forEach(op => {
                if(op.innerText.includes(metodo)) {
                    op.classList.add('selected');
                } else {
                    op.classList.remove('selected');
                }
            });

            const pixBox = document.getElementById('pix-box');
            if(metodo === 'Pix') {
                pixBox.style.display = 'block';
            } else {
                pixBox.style.display = 'none';
            }
        }

        function copiarChavePix() {
            const chave = "capg@alcancepontagrossa.com.br";
            navigator.clipboard.writeText(chave).then(() => {
                alert("Chave Pix copiada com sucesso!");
            }).catch(err => {
                console.error('Erro ao copiar chave pix: ', err);
            });
        }

        function enviarPedido() {
            const nome = document.getElementById('nome').value.trim();
            const telefone = document.getElementById('telefone').value.trim();
            const horario = document.getElementById('horario').value;
            const obs = document.getElementById('obs').value.trim();

            if (!nome) {
                alert("Por favor, preencha o seu nome!");
                document.getElementById('nome').focus();
                return;
            }

            if (!telefone) {
                alert("Por favor, preencha o seu telefone/WhatsApp!");
                document.getElementById('telefone').focus();
                return;
            }

            if (!horario) {
                alert("Por favor, selecione o horário de retirada!");
                document.getElementById('horario').focus();
                return;
            }

            if (horario < "19:30") {
                alert("As retiradas iniciam apenas a partir das 19:30h! Por favor, escolha um horário após as 19:30h.");
                document.getElementById('horario').focus();
                return;
            }

            let total = (quantidade * PRECO_COMBO).toFixed(2).replace('.', ',');

            let mensagem = `🍔 *NOVO PEDIDO - DAY BURGER* 🍔\n`;
            mensagem += `*(Retirada no Local)*\n\n`;
            mensagem += `👤 *Cliente:* ${nome}\n`;
            mensagem += `📞 *Telefone:* ${telefone}\n`;
            mensagem += `⏰ *Horário de Retirada:* ${horario}h\n\n`;
            mensagem += `🛒 *Qtd de Combos:* ${quantidade}x Combo Clássico Burger + Batata + Coca Zero 200ml\n`;
            mensagem += `💰 *Valor Total:* R$ ${total}\n`;
            mensagem += `💳 *Forma de Pagamento:* ${formaPagamentoSelecionada}\n`;
            
            if (formaPagamentoSelecionada === 'Pix') {
                mensagem += `*(Cliente irá enviar o comprovante do Pix)*\n`;
            }

            if (obs) {
                mensagem += `📝 *Observações:* ${obs}\n`;
            }

            mensagem += `\nAguardando confirmação do pedido!`;

            const url = `https://api.whatsapp.com/send?phone=${SEU_NUMERO_WHATSAPP}&text=${encodeURIComponent(mensagem)}`;
            window.open(url, '_blank');
        }
    </script>
</body>
</html>
