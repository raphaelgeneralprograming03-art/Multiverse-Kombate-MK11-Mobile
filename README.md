
<html lang="pt-BR">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>Multiverse Kombat 11 Mobile - Módulo de Combate Visual</title>
    <style>
        :root {
            --gold: #d4af37;
            --dark-bg: #070709;
            --panel-bg: #121217;
            --border-color: #2b2b36;
            --red-glow: #ef4444;
            --blue-glow: #3b82f6;
            --purple-glow: #a855f7;
        }

        * {
            box-sizing: border-box;
            margin: 0;
            padding: 0;
            font-family: 'Segoe UI', Tahoma, Geneva, Verdana, sans-serif;
            user-select: none;
        }

        body {
            background-color: var(--dark-bg);
            color: #f3f4f6;
            display: flex;
            flex-direction: column;
            align-items: center;
            justify-content: flex-start;
            min-height: 100vh;
            padding: 10px;
        }

        header {
            width: 100%;
            max-width: 980px;
            display: flex;
            justify-content: space-between;
            align-items: center;
            background: linear-gradient(90deg, #16161f, #09090d);
            border: 2px solid var(--gold);
            padding: 10px 20px;
            border-radius: 6px;
            margin-bottom: 10px;
            box-shadow: 0 0 15px rgba(212, 175, 55, 0.2);
        }

        h1 {
            color: var(--gold);
            font-size: 1.3rem;
            text-transform: uppercase;
            letter-spacing: 2px;
            text-shadow: 0 0 8px rgba(212, 175, 55, 0.4);
        }

        .currencies {
            display: flex;
            gap: 12px;
            font-size: 0.85rem;
            font-weight: bold;
        }

        .curr-item {
            background: #1f1f28;
            padding: 5px 12px;
            border-radius: 4px;
            border: 1px solid #383846;
        }

        .game-wrapper {
            width: 100%;
            max-width: 980px;
            background: var(--panel-bg);
            border: 2px solid var(--border-color);
            border-radius: 8px;
            padding: 12px;
            display: flex;
            flex-direction: column;
            gap: 10px;
        }

        /* HUD SUPERIOR MK11 MOBILE */
        .hud-arena {
            width: 100%;
            display: flex;
            justify-content: space-between;
            align-items: center;
            background: #0f0f14;
            padding: 10px 15px;
            border-radius: 6px;
            border: 1px solid #2e2e3d;
        }

        .hud-fighter {
            display: flex;
            flex-direction: column;
            width: 42%;
            gap: 4px;
        }

        .hud-name {
            font-weight: bold;
            font-size: 0.9rem;
            color: var(--gold);
            text-transform: uppercase;
            letter-spacing: 1px;
        }

        .hp-bar-bg {
            width: 100%;
            height: 18px;
            background: #22222d;
            border: 1px solid #444458;
            border-radius: 3px;
            overflow: hidden;
            position: relative;
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

        .vs-badge {
            font-weight: bold;
            color: var(--gold);
            font-size: 1.2rem;
            text-shadow: 0 0 10px var(--gold);
        }

        /* CONTAINER DO CANVAS */
        .canvas-container {
            position: relative;
            width: 100%;
            height: 440px;
            border-radius: 6px;
            overflow: hidden;
            border: 2px solid var(--gold);
            box-shadow: 0 0 20px rgba(0,0,0,0.9);
        }

        canvas {
            display: block;
            width: 100%;
            height: 100%;
        }

        /* PAINEL DE CONTROLE DE ATAQUE estilo MK MOBILE */
        .controls-panel {
            display: flex;
            justify-content: space-between;
            align-items: center;
            background: #0f0f14;
            padding: 10px 15px;
            border-radius: 6px;
            border: 1px solid #2e2e3d;
            gap: 10px;
        }

        .team-tags {
            display: flex;
            gap: 8px;
        }

        .tag-card {
            width: 65px;
            height: 60px;
            background: #1a1a24;
            border: 2px solid #3e3e50;
            border-radius: 4px;
            cursor: pointer;
            display: flex;
            flex-direction: column;
            align-items: center;
            justify-content: center;
            font-size: 0.7rem;
            font-weight: bold;
            color: #d4d4d8;
            transition: all 0.2s;
        }

        .tag-card.active {
            border-color: var(--gold);
            box-shadow: 0 0 10px var(--gold);
            background: #252533;
        }

        .action-btns {
            display: flex;
            gap: 8px;
        }

        .action-btn {
            background: linear-gradient(135deg, #1a1a24, #0d0d12);
            border: 2px solid var(--gold);
            color: var(--gold);
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
            background: var(--gold);
            color: #000;
            box-shadow: 0 0 12px var(--gold);
        }

        .action-btn:disabled {
            opacity: 0.35;
            border-color: #383846;
            color: #71717a;
            cursor: not-allowed;
        }

        .special-sp {
            border-color: #3b82f6;
            color: #60a5fa;
        }
        .special-sp:hover:not(:disabled) {
            background: #3b82f6;
            color: #fff;
            box-shadow: 0 0 12px #3b82f6;
        }

        .special-fb {
            border-color: #ef4444;
            color: #f87171;
        }
        .special-fb:hover:not(:disabled) {
            background: #ef4444;
            color: #fff;
            box-shadow: 0 0 12px #ef4444;
        }
    </style>
</head>
<body>

    <header>
        <h1>Multiverse Kombat 11</h1>
        <div class="currencies">
            <div class="curr-item">🪙 350,000</div>
            <div class="curr-item">💎 2,100</div>
        </div>
    </header>

    <div class="game-wrapper">
        
        <!-- HUD DA ARENA -->
        <div class="hud-arena">
            <div class="hud-fighter">
                <div class="hud-name" id="p1-name">Spawn (Image)</div>
                <div class="hp-bar-bg"><div id="p1-hp-fill" class="hp-bar-fill p1-fill"></div></div>
                <div class="power-meter" id="p1-power-meter">
                    <div class="power-block"></div>
                    <div class="power-block"></div>
                    <div class="power-block"></div>
                </div>
            </div>

            <div class="vs-badge">VS</div>

            <div class="hud-fighter" style="align-items: flex-end;">
                <div class="hud-name" id="p2-name" style="color: var(--red-glow);">Batman (DC)</div>
                <div class="hp-bar-bg"><div id="p2-hp-fill" class="hp-bar-fill p2-fill"></div></div>
                <div class="power-meter" id="p2-power-meter" style="width: 100%;">
                    <div class="power-block"></div>
                    <div class="power-block"></div>
                    <div class="power-block"></div>
                </div>
            </div>
        </div>

        <!-- CANVAS DA ARENA DE COMBATE -->
        <div class="canvas-container">
            <canvas id="arenaCanvas" width="960" height="440"></canvas>
        </div>

        <!-- CONTROLES ESTILO MK MOBILE -->
        <div class="controls-panel">
            <div class="team-tags" id="teamTags">
                <div class="tag-card active" onclick="switchFighter(0)">Spawn</div>
                <div class="tag-card" onclick="switchFighter(1)">Wolverine</div>
                <div class="tag-card" onclick="switchFighter(2)">Scorpion</div>
            </div>

            <div class="action-btns">
                <button class="action-btn" onclick="triggerAttack()">Ataque Básico</button>
                <button class="action-btn special-sp" id="btn-sp1" onclick="triggerSpecial(1)" disabled>Especial 1</button>
                <button class="action-btn special-sp" id="btn-sp2" onclick="triggerSpecial(2)" disabled>Especial 2</button>
                <button class="action-btn special-fb" id="btn-fb" onclick="triggerSpecial(3)" disabled>Fatal Blow</button>
            </div>
        </div>

    </div>

    <script>
        const canvas = document.getElementById('arenaCanvas');
        const ctx = canvas.getContext('2d');

        // BANCO DE DADOS VISUAL DOS LUTADORES
        const teamP1 = [
            { name: "Spawn", id: 'spawn', hp: 1100, maxHp: 1100, suitColor: '#18181b', skinColor: '#27272a', capeColor: '#18181b', eyesColor: '#00ff66', power: 0, hasCape: true },
            { name: "Wolverine", id: 'wolverine', hp: 1000, maxHp: 1000, suitColor: '#eab308', skinColor: '#fca5a5', capeColor: null, eyesColor: '#ffffff', power: 0, hasCape: false },
            { name: "Scorpion", id: 'scorpion', hp: 950, maxHp: 950, suitColor: '#f59e0b', skinColor: '#27272a', capeColor: null, eyesColor: '#ffffff', power: 0, hasCape: false }
        ];

        let activeIndex = 0;
        let player = teamP1[activeIndex];

        let enemy = {
            name: "Batman", id: 'batman', hp: 1050, maxHp: 1050, suitColor: '#334155', skinColor: '#fca5a5', capeColor: '#0f172a', eyesColor: '#38bdf8', power: 0, hasCape: true
        };

        // Posições e Estados na Arena
        let pPos = { x: 260, y: 320, state: 'IDLE', animTimer: 0 };
        let ePos = { x: 700, y: 320, state: 'IDLE', animTimer: 0 };
        let effectParticles = [];

        function switchFighter(idx) {
            if (teamP1[idx].hp <= 0) return;
            activeIndex = idx;
            player = teamP1[activeIndex];

            document.querySelectorAll('.tag-card').forEach((card, i) => {
                card.classList.toggle('active', i === idx);
            });

            document.getElementById('p1-name').innerText = player.name;
            updateHUD();
        }

        function triggerAttack() {
            if (pPos.state !== 'IDLE') return;
            pPos.state = 'ATTACK';
            pPos.x += 80; // Avança para o soco

            setTimeout(() => {
                let damage = 40 + Math.floor(Math.random() * 15);
                enemy.hp = Math.max(0, enemy.hp - damage);
                player.power = Math.min(100, player.power + 25);

                // Partículas de impacto
                createHitFx(ePos.x - 20, ePos.y - 60, '#ef4444');

                pPos.x -= 80;
                pPos.state = 'IDLE';
                updateHUD();
            }, 180);
        }

        function triggerSpecial(level) {
            let cost = level === 1 ? 33 : level === 2 ? 66 : 100;
            if (player.power < cost || pPos.state !== 'IDLE') return;

            player.power -= cost;
            pPos.state = 'SPECIAL';

            let damage = level === 1 ? 180 : level === 2 ? 350 : 600;

            createHitFx(ePos.x, ePos.y - 70, level === 3 ? '#ef4444' : '#00ff66', 40);

            setTimeout(() => {
                enemy.hp = Math.max(0, enemy.hp - damage);
                pPos.state = 'IDLE';
                updateHUD();
            }, 400);
        }

        function createHitFx(x, y, color, count = 15) {
            for (let i = 0; i < count; i++) {
                effectParticles.push({
                    x, y,
                    vx: (Math.random() - 0.5) * 8,
                    vy: (Math.random() - 0.5) * 8,
                    life: 25,
                    color
                });
            }
        }

        function updateHUD() {
            document.getElementById('p1-hp-fill').style.width = `${(player.hp / player.maxHp) * 100}%`;
            document.getElementById('p2-hp-fill').style.width = `${(enemy.hp / enemy.maxHp) * 100}%`;

            const blocks = document.querySelectorAll('#p1-power-meter .power-block');
            blocks[0].classList.toggle('active', player.power >= 33);
            blocks[1].classList.toggle('active', player.power >= 66);
            blocks[2].classList.toggle('active', player.power >= 100);

            document.getElementById('btn-sp1').disabled = player.power < 33;
            document.getElementById('btn-sp2').disabled = player.power < 66;
            document.getElementById('btn-fb').disabled = player.power < 100;
        }

        // DESENHISTA VETORIAL DOS PERSONAGENS (CORPO HUMANOIDE COMPLETO)
        function drawFighter(ctx, x, y, charData, facingRight = true) {
            ctx.save();
            ctx.translate(x, y);
            if (!facingRight) ctx.scale(-1, 1);

            let time = Date.now() * 0.005;
            let breathe = Math.sin(time) * 2; // Animação de respiração da postura de luta

            // Sombra
            ctx.fillStyle = 'rgba(0,0,0,0.5)';
            ctx.beginPath();
            ctx.ellipse(0, 0, 30, 8, 0, 0, Math.PI * 2);
            ctx.fill();

            // Capa (Spawn ou Batman)
            if (charData.hasCape) {
                ctx.fillStyle = charData.capeColor;
                ctx.beginPath();
                ctx.moveTo(-15, -90 + breathe);
                ctx.quadraticCurveTo(-45 - Math.sin(time) * 5, -50, -35, 0);
                ctx.lineTo(-5, 0);
                ctx.quadraticCurveTo(-15, -40, -5, -90 + breathe);
                ctx.fill();
            }

            // Pernas
            ctx.strokeStyle = '#181820';
            ctx.lineWidth = 10;
            // Perna esquerda
            ctx.beginPath();
            ctx.moveTo(-10, -45); ctx.lineTo(-18, -20); ctx.lineTo(-22, 0);
            ctx.stroke();
            // Perna direita
            ctx.beginPath();
            ctx.moveTo(10, -45); ctx.lineTo(15, -20); ctx.lineTo(18, 0);
            ctx.stroke();

            // Tronco / Armadura
            ctx.fillStyle = charData.suitColor;
            ctx.beginPath();
            ctx.roundRect(-16, -90 + breathe, 32, 48, 6);
            ctx.fill();
            ctx.lineWidth = 2;
            ctx.strokeStyle = '#000';
            ctx.stroke();

            // Cabeça
            ctx.fillStyle = charData.skinColor;
            ctx.beginPath();
            ctx.arc(0, -104 + breathe, 14, 0, Math.PI * 2);
            ctx.fill();
            ctx.stroke();

            // Olhos Brilhantes
            ctx.fillStyle = charData.eyesColor;
            ctx.fillRect(3, -107 + breathe, 5, 3);

            // Braço Direiro (Postura de Luta)
            ctx.strokeStyle = charData.suitColor;
            ctx.lineWidth = 8;
            ctx.beginPath();
            ctx.moveTo(12, -80 + breathe);
            ctx.lineTo(24, -65 + breathe);
            ctx.lineTo(20, -80 + breathe); // Punho erguido
            ctx.stroke();

            ctx.restore();
        }

        // RENDERIZAÇÃO DO CENÁRIO GÓTICO DE MK11
        function renderScene() {
            ctx.clearRect(0, 0, canvas.width, canvas.height);

            // Fundo Gradiente Sombrio
            let bgGrad = ctx.createLinearGradient(0, 0, 0, canvas.height);
            bgGrad.addColorStop(0, '#050508');
            bgGrad.addColorStop(0.7, '#14141f');
            bgGrad.addColorStop(1, '#050508');
            ctx.fillStyle = bgGrad;
            ctx.fillRect(0, 0, canvas.width, canvas.height);

            // Colunas da Arena de Kombat
            ctx.fillStyle = '#1c1c26';
            for (let i = 80; i < canvas.width; i += 220) {
                ctx.fillRect(i, 40, 35, 280);
                // Detalhes da coluna
                ctx.strokeStyle = '#2d2d3d';
                ctx.strokeRect(i, 40, 35, 280);
            }

            // Tochas de Fogo Animadas nas Colunas
            let fireTime = Date.now() * 0.01;
            for (let i = 80; i < canvas.width; i += 220) {
                let fireH = 15 + Math.sin(fireTime + i) * 5;
                ctx.fillStyle = '#f97316';
                ctx.beginPath();
                ctx.arc(i + 17, 70, fireH / 2, 0, Math.PI * 2);
                ctx.fill();
            }

            // Piso de Pedra da Arena
            ctx.fillStyle = '#111118';
            ctx.fillRect(0, 320, canvas.width, 120);
            ctx.strokeStyle = varGold = '#d4af37';
            ctx.lineWidth = 3;
            ctx.beginPath();
            ctx.moveTo(0, 320); ctx.lineTo(canvas.width, 320);
            ctx.stroke();

            // Desenhar Partículas de Golpe
            for (let i = effectParticles.length - 1; i >= 0; i--) {
                let p = effectParticles[i];
                p.x += p.vx;
                p.y += p.vy;
                p.life--;
                ctx.fillStyle = p.color;
                ctx.beginPath();
                ctx.arc(p.x, p.y, 4, 0, Math.PI * 2);
                ctx.fill();
                if (p.life <= 0) effectParticles.splice(i, 1);
            }

            // Desenhar os 2 Lutadores
            drawFighter(ctx, pPos.x, pPos.y, player, true);
            drawFighter(ctx, ePos.x, ePos.y, enemy, false);

            requestAnimationFrame(renderScene);
        }

        updateHUD();
        requestAnimationFrame(renderScene);
    </script>
</body>
</html>
