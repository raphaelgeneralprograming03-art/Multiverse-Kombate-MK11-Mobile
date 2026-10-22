
<html lang="pt-BR">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>Multiverse Kombat 11 Mobile</title>
    <style>
        :root {
            --mk-gold: #d4af37;
            --mk-dark: #050508;
            --panel-bg: #0f0f14;
            --border-color: #272732;
            --red-glow: #ef4444;
            --blue-glow: #3b82f6;
            --purple-glow: #a855f7;
            --green-glow: #00ff66;
        }

        * {
            box-sizing: border-box;
            margin: 0;
            padding: 0;
            font-family: 'Segoe UI', Tahoma, Geneva, Verdana, sans-serif;
            user-select: none;
        }

        body {
            background-color: var(--mk-dark);
            color: #f3f4f6;
            display: flex;
            flex-direction: column;
            align-items: center;
            min-height: 100vh;
            padding: 10px;
        }

        /* HEADER & RECURSOS DO APLICATIVO */
        header {
            width: 100%;
            max-width: 1000px;
            display: flex;
            justify-content: space-between;
            align-items: center;
            background: linear-gradient(90deg, #16161f, #07070a);
            border: 2px solid var(--mk-gold);
            padding: 10px 20px;
            border-radius: 6px;
            margin-bottom: 12px;
            box-shadow: 0 0 15px rgba(212, 175, 55, 0.25);
        }

        h1 {
            color: var(--mk-gold);
            font-size: 1.3rem;
            text-transform: uppercase;
            letter-spacing: 2px;
            text-shadow: 0 0 10px rgba(212, 175, 55, 0.4);
        }

        .currencies {
            display: flex;
            gap: 12px;
            font-size: 0.85rem;
            font-weight: bold;
        }

        .curr-item {
            background: #1a1a24;
            padding: 5px 12px;
            border-radius: 4px;
            border: 1px solid #383848;
        }

        /* BARRA DE MENU ESTILO MK11 MOBILE */
        nav.menu-bar {
            width: 100%;
            max-width: 1000px;
            display: flex;
            gap: 8px;
            margin-bottom: 12px;
        }

        .nav-btn {
            flex: 1;
            background: #121218;
            border: 1px solid #383848;
            color: #a1a1aa;
            padding: 12px;
            font-weight: bold;
            font-size: 0.85rem;
            text-transform: uppercase;
            border-radius: 4px;
            cursor: pointer;
            transition: all 0.2s;
            text-align: center;
        }

        .nav-btn.active, .nav-btn:hover {
            background: linear-gradient(135deg, var(--mk-gold), #997a15);
            color: #000;
            border-color: var(--mk-gold);
            box-shadow: 0 0 12px rgba(212, 175, 55, 0.5);
        }

        .app-container {
            width: 100%;
            max-width: 1000px;
            background: var(--panel-bg);
            border: 2px solid var(--border-color);
            border-radius: 8px;
            padding: 15px;
            min-height: 520px;
        }

        .tab-content {
            display: none;
            flex-direction: column;
            gap: 15px;
        }

        .tab-content.active {
            display: flex;
        }

        .section-title {
            color: var(--mk-gold);
            font-size: 1.1rem;
            text-transform: uppercase;
            border-bottom: 1px solid var(--mk-gold);
            padding-bottom: 5px;
            display: flex;
            justify-content: space-between;
        }

        /* GRID DE CARTAS / COLEÇÃO */
        .cards-grid {
            display: grid;
            grid-template-columns: repeat(auto-fill, minmax(180px, 1fr));
            gap: 12px;
        }

        .card-item {
            background: linear-gradient(145deg, #181822, #0d0d12);
            border: 2px solid #383848;
            border-radius: 6px;
            padding: 10px;
            display: flex;
            flex-direction: column;
            align-items: center;
            position: relative;
            cursor: pointer;
            transition: transform 0.2s, border-color 0.2s;
        }

        .card-item:hover {
            transform: translateY(-3px);
            border-color: var(--mk-gold);
        }

        .card-item.gold { border-color: var(--mk-gold); }
        .card-item.diamond { border-color: var(--purple-glow); box-shadow: 0 0 10px rgba(168, 85, 247, 0.3); }

        .card-avatar {
            width: 60px;
            height: 60px;
            border-radius: 50%;
            display: flex;
            align-items: center;
            justify-content: center;
            font-size: 1.5rem;
            font-weight: bold;
            color: #fff;
            margin-bottom: 8px;
            border: 2px solid #fff;
        }

        .fusion-badge {
            position: absolute;
            top: 6px;
            right: 6px;
            background: var(--mk-gold);
            color: #000;
            font-weight: bold;
            font-size: 0.7rem;
            padding: 2px 6px;
            border-radius: 3px;
        }

        /* HUD DA ARENA DE COMBATE */
        .hud-arena {
            display: flex;
            justify-content: space-between;
            align-items: center;
            background: #09090d;
            padding: 10px 15px;
            border-radius: 6px;
            border: 1px solid #2e2e3d;
        }

        .fighter-hud {
            display: flex;
            flex-direction: column;
            width: 42%;
            gap: 4px;
        }

        .hp-bar-bg {
            width: 100%;
            height: 18px;
            background: #22222d;
            border: 1px solid #444458;
            border-radius: 3px;
            overflow: hidden;
        }

        .hp-bar-fill {
            height: 100%;
            width: 100%;
            transition: width 0.15s ease-out;
        }

        .p1-fill { background: linear-gradient(90deg, #16a34a, #22c55e); }
        .p2-fill { background: linear-gradient(90deg, #dc2626, #ef4444); }

        .power-meter {
            display: flex;
            gap: 4px;
            margin-top: 2px;
        }

        .power-block {
            flex: 1;
            height: 8px;
            background: #1e1e28;
            border: 1px solid #383846;
            border-radius: 2px;
        }

        .power-block.active {
            background: #3b82f6;
            box-shadow: 0 0 8px #3b82f6;
        }

        .canvas-container {
            position: relative;
            width: 100%;
            height: 380px;
            border-radius: 6px;
            overflow: hidden;
            border: 2px solid var(--mk-gold);
            box-shadow: 0 0 20px rgba(0,0,0,0.9);
        }

        canvas {
            display: block;
            width: 100%;
            height: 100%;
        }

        .controls-panel {
            display: flex;
            justify-content: space-between;
            align-items: center;
            background: #09090d;
            padding: 10px 15px;
            border-radius: 6px;
            border: 1px solid #2e2e3d;
            gap: 10px;
        }

        .action-btn {
            background: linear-gradient(135deg, #1a1a24, #0d0d12);
            border: 2px solid var(--mk-gold);
            color: var(--mk-gold);
            padding: 10px 16px;
            font-weight: bold;
            font-size: 0.85rem;
            border-radius: 4px;
            cursor: pointer;
            text-transform: uppercase;
            box-shadow: 0 4px 10px rgba(0,0,0,0.5);
            transition: all 0.15s;
        }

        .action-btn:hover:not(:disabled) {
            background: var(--mk-gold);
            color: #000;
        }

        .action-btn:disabled {
            opacity: 0.35;
            border-color: #383846;
            color: #71717a;
            cursor: not-allowed;
        }
    </style>
</head>
<body>

    <header>
        <h1>Multiverse Kombat 11</h1>
        <div class="currencies">
            <div class="curr-item">🪙 <span id="coins-display">250,000</span></div>
            <div class="curr-item">💎 <span id="souls-display">1,500</span></div>
        </div>
    </header>

    <!-- NAVEGAÇÃO DO APP (STYLE MK11 MOBILE) -->
    <nav class="menu-bar">
        <div class="nav-btn active" onclick="switchTab('home')">Home / Equipe</div>
        <div class="nav-btn" onclick="switchTab('collection')">Minha Coleção</div>
        <div class="nav-btn" onclick="switchTab('store')">Loja de Pacotes</div>
        <div class="nav-btn" onclick="switchTab('fight')">Arena de Combate</div>
    </nav>

    <div class="app-container">
        
        <!-- VISÃO GERAL: TAB HOME -->
        <div id="tab-home" class="tab-content active">
            <div class="section-title">
                <span>Visão Geral do Aplicativo & Equipe Ativa</span>
            </div>
            <p style="font-size: 0.85rem; color: #a1a1aa;">Selecione os membros do seu time 3v3 e entre na arena para enfrentar guerreiros de vários universos!</p>
            
            <div class="cards-grid" id="homeTeamGrid"></div>

            <button class="action-btn" style="margin-top: 15px; padding: 14px; font-size: 1rem;" onclick="switchTab('fight')">
                Entrar na Arena de Luta ⚔️
            </button>
        </div>

        <!-- VISÃO GERAL: TAB COLEÇÃO -->
        <div id="tab-collection" class="tab-content">
            <div class="section-title">Coleção Completa do Multiverso</div>
            <div class="cards-grid" id="fullCollectionGrid"></div>
        </div>

        <!-- VISÃO GERAL: TAB LOJA DE PACOTES -->
        <div id="tab-store" class="tab-content">
            <div class="section-title">Loja de Pacotes do Multiverso</div>
            <div style="display: flex; gap: 15px; flex-wrap: wrap;">
                <div style="flex: 1; background: #12121a; border: 2px solid var(--mk-gold); padding: 15px; border-radius: 6px; text-align: center;">
                    <h3 style="color: var(--mk-gold); margin-bottom: 8px;">Pacote Ouro do Multiverso</h3>
                    <p style="font-size: 0.8rem; color: #aaa; margin-bottom: 12px;">Garante 1 Carta de Lutador Ouro (MK, Marvel, DC, X-Men).</p>
                    <button class="action-btn" onclick="buyPack('gold')">Comprar (🪙 50,000)</button>
                </div>
                <div style="flex: 1; background: #12121a; border: 2px solid var(--purple-glow); padding: 15px; border-radius: 6px; text-align: center;">
                    <h3 style="color: var(--purple-glow); margin-bottom: 8px;">Pacote Diamante Supremo</h3>
                    <p style="font-size: 0.8rem; color: #aaa; margin-bottom: 12px;">Chance de obter Spawn, Divine Spawn e Entidades Cósmicas!</p>
                    <button class="action-btn" style="border-color: var(--purple-glow); color: var(--purple-glow);" onclick="buyPack('diamond')">Comprar (💎 400)</button>
                </div>
            </div>
        </div>

        <!-- VISÃO GERAL: ARENA DE COMBATE 2.5D -->
        <div id="tab-fight" class="tab-content">
            
            <div class="hud-arena">
                <div class="fighter-hud">
                    <div id="p1-name" style="font-weight: bold; color: var(--mk-gold);">Spawn</div>
                    <div class="hp-bar-bg"><div id="p1-hp" class="hp-bar-fill p1-fill"></div></div>
                    <div class="power-meter" id="p1-power-meter">
                        <div class="power-block"></div>
                        <div class="power-block"></div>
                        <div class="power-block"></div>
                    </div>
                </div>

                <div style="font-weight: bold; color: var(--mk-gold); font-size: 1.2rem;">VS</div>

                <div class="fighter-hud" style="align-items: flex-end;">
                    <div id="p2-name" style="font-weight: bold; color: var(--red-glow);">Batman</div>
                    <div class="hp-bar-bg"><div id="p2-hp" class="hp-bar-fill p2-fill"></div></div>
                    <div class="power-meter" id="p2-power-meter" style="width: 100%;">
                        <div class="power-block"></div>
                        <div class="power-block"></div>
                        <div class="power-block"></div>
                    </div>
                </div>
            </div>

            <div class="canvas-container">
                <canvas id="fightCanvas" width="960" height="380"></canvas>
            </div>

            <div class="controls-panel">
                <div style="display: flex; gap: 8px;" id="tagButtons"></div>

                <div style="display: flex; gap: 8px;">
                    <button class="action-btn" onclick="triggerAttack()">Ataque Básico</button>
                    <button class="action-btn" id="btn-sp1" onclick="triggerSpecial(1)" disabled style="border-color: #3b82f6; color: #60a5fa;">Especial 1</button>
                    <button class="action-btn" id="btn-sp2" onclick="triggerSpecial(2)" disabled style="border-color: #3b82f6; color: #60a5fa;">Especial 2</button>
                    <button class="action-btn" id="btn-fb" onclick="triggerSpecial(3)" disabled style="border-color: #ef4444; color: #f87171;">Fatal Blow</button>
                </div>
            </div>

        </div>

    </div>

    <script>
        let coins = 250000;
        let souls = 1500;

        const roster = [
            { id: 'spawn', name: 'Spawn', universe: 'Image Comics', tier: 'Diamante', color: '#00ff66', hp: 1200, maxHp: 1200, power: 0, fusion: 0 },
            { id: 'scorpion', name: 'Scorpion', universe: 'Mortal Kombat', tier: 'Ouro', color: '#f59e0b', hp: 950, maxHp: 950, power: 0, fusion: 0 },
            { id: 'subzero', name: 'Sub-Zero', universe: 'Mortal Kombat', tier: 'Ouro', color: '#38bdf8', hp: 900, maxHp: 900, power: 0, fusion: 0 },
            { id: 'wolverine', name: 'Wolverine', universe: 'X-Men / Marvel', tier: 'Ouro', color: '#eab308', hp: 1050, maxHp: 1050, power: 0, fusion: 0 },
            { id: 'batman', name: 'Batman', universe: 'DC Comics', tier: 'Ouro', color: '#64748b', hp: 1000, maxHp: 1000, power: 0, fusion: 0 }
        ];

        let activeIdx = 0;
        let player = roster[activeIdx];
        let enemy = { ...roster[4], hp: 1000, maxHp: 1000 };

        function switchTab(tabId) {
            document.querySelectorAll('.nav-btn').forEach(btn => btn.classList.remove('active'));
            document.querySelectorAll('.tab-content').forEach(tab => tab.classList.remove('active'));

            event.target.classList.add('active');
            document.getElementById(`tab-${tabId}`).classList.add('active');

            if (tabId === 'home') renderHomeGrid();
            if (tabId === 'collection') renderCollectionGrid();
        }

        function renderHomeGrid() {
            const grid = document.getElementById('homeTeamGrid');
            grid.innerHTML = '';
            roster.slice(0, 3).forEach((char, i) => {
                const card = document.createElement('div');
                card.className = `card-item ${char.tier === 'Diamante' ? 'diamond' : 'gold'}`;
                card.innerHTML = `
                    <div class="fusion-badge">F${char.fusion}</div>
                    <div class="card-avatar" style="background: ${char.color}">${char.name[0]}</div>
                    <div style="font-weight: bold; font-size: 0.85rem;">${char.name}</div>
                    <div style="font-size: 0.65rem; color: var(--mk-gold);">${char.universe}</div>
                `;
                grid.appendChild(card);
            });
        }

        function renderCollectionGrid() {
            const grid = document.getElementById('fullCollectionGrid');
            grid.innerHTML = '';
            roster.forEach(char => {
                const card = document.createElement('div');
                card.className = `card-item ${char.tier === 'Diamante' ? 'diamond' : 'gold'}`;
                card.innerHTML = `
                    <div class="fusion-badge">F${char.fusion}</div>
                    <div class="card-avatar" style="background: ${char.color}">${char.name[0]}</div>
                    <div style="font-weight: bold; font-size: 0.85rem;">${char.name}</div>
                    <div style="font-size: 0.65rem; color: var(--mk-gold);">${char.universe}</div>
                `;
                grid.appendChild(card);
            });
        }

        function buyPack(type) {
            if (type === 'gold' && coins >= 50000) {
                coins -= 50000;
            } else if (type === 'diamond' && souls >= 400) {
                souls -= 400;
            } else {
                alert("Recursos insuficientes!"); return;
            }
            document.getElementById('coins-display').innerText = coins.toLocaleString();
            document.getElementById('souls-display').innerText = souls.toLocaleString();
            alert("Pacote aberto! Carta adicionada à sua coleção!");
        }

        // MOTOR CANVAS DA ARENA DE COMBATE
        let p1X = 260, p2X = 700;
        let particles = [];

        function triggerAttack() {
            p1X += 60;
            setTimeout(() => {
                enemy.hp = Math.max(0, enemy.hp - 45);
                player.power = Math.min(100, player.power + 25);
                p1X -= 60;
                updateArenaHUD();
            }, 150);
        }

        function triggerSpecial(level) {
            let cost = level === 1 ? 33 : level === 2 ? 66 : 100;
            if (player.power < cost) return;
            player.power -= cost;
            let dmg = level === 1 ? 160 : level === 2 ? 320 : 550;
            enemy.hp = Math.max(0, enemy.hp - dmg);
            updateArenaHUD();
        }

        function updateArenaHUD() {
            document.getElementById('p1-name').innerText = player.name;
            document.getElementById('p2-name').innerText = enemy.name;
            document.getElementById('p1-hp').style.width = `${(player.hp / player.maxHp) * 100}%`;
            document.getElementById('p2-hp').style.width = `${(enemy.hp / enemy.maxHp) * 100}%`;

            const blocks = document.querySelectorAll('#p1-power-meter .power-block');
            blocks[0].classList.toggle('active', player.power >= 33);
            blocks[1].classList.toggle('active', player.power >= 66);
            blocks[2].classList.toggle('active', player.power >= 100);

            document.getElementById('btn-sp1').disabled = player.power < 33;
            document.getElementById('btn-sp2').disabled = player.power < 66;
            document.getElementById('btn-fb').disabled = player.power < 100;
        }

        function renderArena() {
            const canvas = document.getElementById('fightCanvas');
            const ctx = canvas.getContext('2d');
            ctx.clearRect(0, 0, canvas.width, canvas.height);

            // Cenário Fundo Gótico
            ctx.fillStyle = '#0a0a10';
            ctx.fillRect(0, 0, canvas.width, canvas.height);
            ctx.fillStyle = '#111118';
            ctx.fillRect(0, 280, canvas.width, 100);
            ctx.strokeStyle = '#d4af37';
            ctx.lineWidth = 2;
            ctx.strokeRect(0, 280, canvas.width, 100);

            // Jogador P1
            ctx.fillStyle = player.color;
            ctx.beginPath();
            ctx.arc(p1X, 240, 28, 0, Math.PI * 2);
            ctx.fill();
            ctx.strokeStyle = '#fff';
            ctx.stroke();

            // Jogador P2
            ctx.fillStyle = enemy.color;
            ctx.beginPath();
            ctx.arc(p2X, 240, 28, 0, Math.PI * 2);
            ctx.fill();
            ctx.strokeStyle = '#ef4444';
            ctx.stroke();

            requestAnimationFrame(renderArena);
        }

        renderHomeGrid();
        updateArenaHUD();
        requestAnimationFrame(renderArena);
    </script>
</body>
</html>
