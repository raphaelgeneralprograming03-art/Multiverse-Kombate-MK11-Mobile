
<html lang="pt-BR">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>Multiverse Kombat 11 Mobile - Módulo 1</title>
    <style>
        :root {
            --mk-gold: #d4af37;
            --mk-dark: #0a0a0c;
            --mk-red: #b91c1c;
            --mk-blue: #2563eb;
            --panel-bg: #121216;
        }

        * {
            box-sizing: border-box;
            margin: 0;
            padding: 0;
            font-family: 'Cinzel', 'Courier New', Courier, monospace;
            user-select: none;
        }

        body {
            background-color: var(--mk-dark);
            color: #f3f4f6;
            display: flex;
            flex-direction: column;
            align-items: center;
            justify-content: center;
            min-height: 100vh;
            overflow: hidden;
        }

        .game-container {
            width: 900px;
            background: #000;
            border: 4px solid var(--mk-gold);
            box-shadow: 0 0 30px rgba(212, 175, 55, 0.3);
            border-radius: 6px;
            display: flex;
            flex-direction: column;
        }

        /* HUD Superior Estilo MK11 Mobile */
        .hud-top {
            display: flex;
            justify-content: space-between;
            align-items: center;
            background: linear-gradient(to bottom, #18181b, #09090b);
            padding: 10px 20px;
            border-bottom: 2px solid var(--mk-gold);
            height: 70px;
        }

        .fighter-hud {
            display: flex;
            flex-direction: column;
            width: 40%;
            gap: 4px;
        }

        .fighter-hud.p2 {
            align-items: flex-end;
        }

        .hud-name {
            font-size: 0.9rem;
            font-weight: bold;
            color: var(--mk-gold);
            text-transform: uppercase;
            letter-spacing: 1px;
        }

        .health-bar-container {
            width: 100%;
            height: 18px;
            background: #27272a;
            border: 2px solid #3f3f46;
            border-radius: 3px;
            overflow: hidden;
            position: relative;
        }

        .health-bar-fill {
            height: 100%;
            width: 100%;
            transition: width 0.15s ease-out;
        }

        .p1-hp { background: linear-gradient(90deg, #16a34a, #22c55e); }
        .p2-hp { background: linear-gradient(90deg, #dc2626, #ef4444); }

        .power-bars {
            display: flex;
            gap: 4px;
            margin-top: 2px;
        }

        .power-segment {
            width: 30px;
            height: 8px;
            background: #1e1b4b;
            border: 1px solid #4338ca;
            border-radius: 2px;
        }

        .power-segment.active {
            background: #6366f1;
            box-shadow: 0 0 6px #818cf8;
        }

        .vs-badge {
            font-size: 1.2rem;
            font-weight: bold;
            color: var(--mk-gold);
            text-shadow: 0 0 10px var(--mk-gold);
        }

        /* Canvas Arena */
        .canvas-wrapper {
            position: relative;
            width: 100%;
            height: 400px;
        }

        canvas {
            display: block;
            background: radial-gradient(circle at center, #1f2937 0%, #030712 100%);
        }

        /* Painel de Ações Estilo MK11 Mobile (Inferior) */
        .combat-control-panel {
            display: flex;
            justify-content: space-between;
            align-items: center;
            background: #18181b;
            border-top: 2px solid var(--mk-gold);
            padding: 15px 20px;
            gap: 15px;
        }

        .team-tags {
            display: flex;
            gap: 8px;
        }

        .tag-card {
            width: 60px;
            height: 60px;
            background: #27272a;
            border: 2px solid #52525b;
            border-radius: 4px;
            cursor: pointer;
            display: flex;
            align-items: center;
            justify-content: center;
            font-size: 0.7rem;
            font-weight: bold;
            text-align: center;
            color: #d4d4d8;
            transition: 0.2s;
        }

        .tag-card.active {
            border-color: var(--mk-gold);
            box-shadow: 0 0 8px var(--mk-gold);
        }

        .tag-card:hover {
            border-color: #fff;
        }

        .action-buttons {
            display: flex;
            gap: 10px;
            flex-grow: 1;
            justify-content: center;
        }

        .mk-btn {
            background: linear-gradient(135deg, #27272a, #09090b);
            border: 2px solid var(--mk-gold);
            color: var(--mk-gold);
            padding: 10px 18px;
            font-weight: bold;
            font-size: 0.85rem;
            border-radius: 4px;
            cursor: pointer;
            text-transform: uppercase;
            box-shadow: 0 4px 6px rgba(0,0,0,0.4);
            transition: all 0.1s;
        }

        .mk-btn:hover:not(:disabled) {
            background: var(--mk-gold);
            color: #000;
            box-shadow: 0 0 12px var(--mk-gold);
        }

        .mk-btn:active:not(:disabled) {
            transform: scale(0.95);
        }

        .mk-btn:disabled {
            opacity: 0.4;
            border-color: #3f3f46;
            color: #71717a;
            cursor: not-allowed;
        }

        .special-btn {
            border-color: #6366f1;
            color: #818cf8;
        }
        .special-btn:hover:not(:disabled) {
            background: #6366f1;
            color: #fff;
            box-shadow: 0 0 12px #6366f1;
        }
    </style>
</head>
<body>

    <div class="game-container">
        <!-- HUD Superior -->
        <div class="hud-top">
            <!-- Jogador 1 -->
            <div class="fighter-hud">
                <div class="hud-name" id="p1-name">Spawn (Image Comics)</div>
                <div class="health-bar-container">
                    <div id="p1-hp-fill" class="health-bar-fill p1-hp"></div>
                </div>
                <div class="power-bars" id="p1-power">
                    <div class="power-segment"></div>
                    <div class="power-segment"></div>
                    <div class="power-segment"></div>
                </div>
            </div>

            <div class="vs-badge">VS</div>

            <!-- Jogador 2 (Oponente) -->
            <div class="fighter-hud p2">
                <div class="hud-name" id="p2-name">Batman (DC Comics)</div>
                <div class="health-bar-container">
                    <div id="p2-hp-fill" class="health-bar-fill p2-hp"></div>
                </div>
                <div class="power-bars" id="p2-power">
                    <div class="power-segment"></div>
                    <div class="power-segment"></div>
                    <div class="power-segment"></div>
                </div>
            </div>
        </div>

        <!-- Canvas da Luta -->
        <div class="canvas-wrapper">
            <canvas id="fightCanvas" width="900" height="400"></canvas>
        </div>

        <!-- Painel de Comandos Inferior (MK11 Mobile Style) -->
        <div class="combat-control-panel">
            <!-- Troca de Personagens (Time 3v3) -->
            <div class="team-tags" id="p1-team-slots">
                <div class="tag-card active" onclick="switchFighter(0)">Spawn</div>
                <div class="tag-card" onclick="switchFighter(1)">Wolverine</div>
                <div class="tag-card" onclick="switchFighter(2)">Iron Man</div>
            </div>

            <!-- Botões de Ataque e Especiais -->
            <div class="action-buttons">
                <button class="mk-btn" onclick="executeBasicAttack()">Ataque Básico</button>
                <button class="mk-btn special-btn" id="btn-sp1" onclick="executeSpecial(1)" disabled>Especial 1</button>
                <button class="mk-btn special-btn" id="btn-sp2" onclick="executeSpecial(2)" disabled>Especial 2</button>
                <button class="mk-btn special-btn" id="btn-fatal" onclick="executeSpecial(3)" disabled style="border-color: #dc2626; color: #ef4444;">Fatal Blow</button>
            </div>
        </div>
    </div>

    <script>
        const canvas = document.getElementById('fightCanvas');
        const ctx = canvas.getContext('2d');

        // Dados do Jogador e Time 3v3
        const rosterP1 = [
            { name: "Spawn", hp: 1000, maxHp: 1000, power: 0, color: '#00ff66', spec: 'Rajada Necroplásmica' },
            { name: "Wolverine", hp: 900, maxHp: 900, power: 0, color: '#f59e0b', spec: 'Fúria de Adamantium' },
            { name: "Iron Man", hp: 850, maxHp: 850, power: 0, color: '#ef4444', spec: 'Laser Unibeam' }
        ];

        let activeIdx = 0;
        let player = rosterP1[activeIdx];

        // Oponente atual
        let enemy = {
            name: "Batman",
            hp: 1000,
            maxHp: 1000,
            power: 0,
            color: '#3b82f6'
        };

        // Posições visuais na arena 2D
        let pPos = { x: 200, y: 280, vx: 0 };
        let ePos = { x: 700, y: 280, vx: 0 };
        let combatState = "IDLE"; // IDLE, ATTACK, HIT

        function switchFighter(idx) {
            if (rosterP1[idx].hp <= 0) return;
            activeIdx = idx;
            player = rosterP1[activeIdx];
            
            // Atualizar UI de seleção
            document.querySelectorAll('.tag-card').forEach((card, i) => {
                card.classList.toggle('active', i === idx);
            });
            document.getElementById('p1-name').innerText = player.name;
            updateHUD();
        }

        function executeBasicAttack() {
            if (combatState !== "IDLE") return;
            combatState = "ATTACK";
            pPos.vx = 8;

            setTimeout(() => {
                let damage = 45;
                enemy.hp = Math.max(0, enemy.hp - damage);
                player.power = Math.min(100, player.power + 25); // Acúmulo de poder estilo MK Mobile
                
                pPos.vx = -4;
                setTimeout(() => { pPos.vx = 0; combatState = "IDLE"; }, 150);
                updateHUD();
            }, 180);
        }

        function executeSpecial(level) {
            let cost = level === 1 ? 33 : level === 2 ? 66 : 100;
            if (player.power < cost || combatState !== "IDLE") return;

            player.power -= cost;
            combatState = "SPECIAL";
            
            let damage = level === 1 ? 150 : level === 2 ? 320 : 550;
            
            setTimeout(() => {
                enemy.hp = Math.max(0, enemy.hp - damage);
                combatState = "IDLE";
                updateHUD();
            }, 500);
        }

        // IA Simples do Oponente atacando de tempos em tempos
        setInterval(() => {
            if (Math.random() < 0.4 && enemy.hp > 0 && player.hp > 0) {
                let dmg = 30;
                player.hp = Math.max(0, player.hp - dmg);
                ePos.vx = -6;
                setTimeout(() => { ePos.vx = 0; }, 150);
                updateHUD();
            }
        }, 2500);

        function updateHUD() {
            // HP P1
            document.getElementById('p1-hp-fill').style.width = `${(player.hp / player.maxHp) * 100}%`;
            // HP P2
            document.getElementById('p2-hp-fill').style.width = `${(enemy.hp / enemy.maxHp) * 100}%`;

            // Barras de Poder P1 (3 segmentos)
            const powerSegs = document.querySelectorAll('#p1-power .power-segment');
            powerSegs[0].classList.toggle('active', player.power >= 33);
            powerSegs[1].classList.toggle('active', player.power >= 66);
            powerSegs[2].classList.toggle('active', player.power >= 100);

            // Habilitar botões especiais conforme energia acumulada
            document.getElementById('btn-sp1').disabled = player.power < 33;
            document.getElementById('btn-sp2').disabled = player.power < 66;
            document.getElementById('btn-fatal').disabled = player.power < 100;
        }

        // Loop de Renderização do Canvas 2D
        function gameLoop() {
            ctx.clearRect(0, 0, canvas.width, canvas.height);

            // Cenário Fundo (Estilo MK Arena)
            ctx.fillStyle = '#111827';
            ctx.fillRect(0, 280, canvas.width, 120);
            ctx.strokeStyle = '#d4af37';
            ctx.lineWidth = 2;
            ctx.beginPath();
            ctx.moveTo(0, 280); ctx.lineTo(canvas.width, 280);
            ctx.stroke();

            // Atualizar posições físicas simples
            pPos.x += pPos.vx;
            if (pPos.x < 50) pPos.x = 50;
            if (pPos.x > ePos.x - 50) pPos.x = ePos.x - 50;

            ePos.x += ePos.vx;
            if (ePos.x > canvas.width - 50) ePos.x = canvas.width - 50;

            // Desenhar Jogador 1
            ctx.fillStyle = player.color;
            ctx.beginPath();
            ctx.arc(pPos.x, pPos.y - 30, 25, 0, Math.PI * 2);
            ctx.fill();
            ctx.lineWidth = 3;
            ctx.strokeStyle = '#fff';
            ctx.stroke();

            // Desenhar Oponente (P2)
            ctx.fillStyle = enemy.color;
            ctx.beginPath();
            ctx.arc(ePos.x, ePos.y - 30, 25, 0, Math.PI * 2);
            ctx.fill();
            ctx.stroke();

            requestAnimationFrame(gameLoop);
        }

        updateHUD();
        requestAnimationFrame(gameLoop);
    </script>
</body>
</html>
