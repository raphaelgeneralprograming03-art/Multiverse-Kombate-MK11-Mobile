
<html lang="pt-BR">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>Multiverse Kombat 11 Mobile</title>
    <style>
        :root {
            --gold: #d4af37;
            --dark-bg: #0b0b0e;
            --panel-bg: #141419;
            --card-border: #2e2e38;
            --red-glow: #ef4444;
            --blue-glow: #3b82f6;
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
            padding: 15px;
        }

        header {
            width: 100%;
            max-width: 1000px;
            display: flex;
            justify-content: space-between;
            align-items: center;
            background: linear-gradient(90deg, #181820, #09090d);
            border: 2px solid var(--gold);
            padding: 10px 20px;
            border-radius: 6px;
            margin-bottom: 15px;
            box-shadow: 0 0 15px rgba(212, 175, 55, 0.2);
        }

        h1 {
            color: var(--gold);
            font-size: 1.4rem;
            text-transform: uppercase;
            letter-spacing: 2px;
        }

        .currencies {
            display: flex;
            gap: 15px;
            font-size: 0.9rem;
            font-weight: bold;
        }

        .curr-item {
            display: flex;
            align-items: center;
            gap: 5px;
            background: #22222b;
            padding: 5px 10px;
            border-radius: 4px;
            border: 1px solid #383846;
        }

        .app-container {
            width: 100%;
            max-width: 1000px;
            background: var(--panel-bg);
            border: 2px solid var(--card-border);
            border-radius: 8px;
            padding: 15px;
            display: flex;
            flex-direction: column;
            gap: 15px;
        }

        /* TELA DE SELEÇÃO DE EQUIPE E ADVERSÁRIO */
        .selection-screen {
            display: flex;
            flex-direction: column;
            gap: 15px;
        }

        .section-title {
            color: var(--gold);
            font-size: 1.1rem;
            text-transform: uppercase;
            border-bottom: 1px solid var(--gold);
            padding-bottom: 5px;
            display: flex;
            justify-content: space-between;
        }

        .team-slots-container {
            display: flex;
            justify-content: space-between;
            gap: 15px;
            flex-wrap: wrap;
        }

        .slot-group {
            flex: 1;
            min-width: 280px;
            background: #191922;
            padding: 10px;
            border-radius: 6px;
            border: 1px solid #2e2e3d;
        }

        .slots-row {
            display: flex;
            gap: 10px;
            margin-top: 10px;
        }

        .card-slot {
            flex: 1;
            height: 130px;
            background: #0d0d12;
            border: 2px dashed #4b4b5e;
            border-radius: 6px;
            display: flex;
            flex-direction: column;
            align-items: center;
            justify-content: center;
            cursor: pointer;
            transition: all 0.2s;
            position: relative;
            overflow: hidden;
            text-align: center;
            padding: 5px;
        }

        .card-slot.active {
            border: 2px solid var(--gold);
            background: #1e1e28;
            box-shadow: 0 0 10px rgba(212, 175, 55, 0.3);
        }

        .card-slot.enemy-slot {
            border-color: var(--red-glow);
        }

        .card-slot.enemy-slot.active {
            border: 2px solid var(--red-glow);
            box-shadow: 0 0 10px rgba(239, 68, 68, 0.4);
        }

        .slot-name {
            font-weight: bold;
            font-size: 0.85rem;
            color: #fff;
            margin-top: 5px;
        }

        .slot-universe {
            font-size: 0.7rem;
            color: #a1a1aa;
        }

        /* ROSTER DE PERSONAGENS */
        .roster-grid {
            display: grid;
            grid-template-columns: repeat(auto-fill, minmax(130px, 1fr));
            gap: 10px;
            max-height: 250px;
            overflow-y: auto;
            padding-right: 5px;
        }

        .char-card {
            background: #1e1e28;
            border: 2px solid #383846;
            border-radius: 6px;
            padding: 8px;
            display: flex;
            flex-direction: column;
            align-items: center;
            cursor: pointer;
            transition: 0.2s;
        }

        .char-card:hover {
            border-color: var(--gold);
            transform: translateY(-2px);
        }

        .char-card.selected {
            border-color: #22c55e;
            opacity: 0.6;
        }

        .char-avatar {
            width: 45px;
            height: 45px;
            border-radius: 50%;
            display: flex;
            align-items: center;
            justify-content: center;
            font-weight: bold;
            font-size: 1.2rem;
            color: #fff;
            margin-bottom: 5px;
            border: 2px solid #fff;
        }

        .char-info {
            text-align: center;
        }

        .char-title {
            font-size: 0.8rem;
            font-weight: bold;
            color: #fff;
        }

        .char-universe-badge {
            font-size: 0.65rem;
            color: var(--gold);
            text-transform: uppercase;
        }

        /* PAINEL DE DETALHES DE HABILIDADES */
        .skills-detail-panel {
            background: #181820;
            border: 1px solid #333342;
            border-radius: 6px;
            padding: 10px;
            display: flex;
            flex-direction: column;
            gap: 8px;
        }

        .skill-item {
            display: flex;
            align-items: center;
            gap: 10px;
            background: #20202c;
            padding: 8px;
            border-radius: 4px;
            border-left: 3px solid var(--gold);
        }

        .skill-icon {
            background: #333346;
            width: 30px;
            height: 30px;
            border-radius: 4px;
            display: flex;
            align-items: center;
            justify-content: center;
            font-weight: bold;
            color: var(--gold);
            font-size: 0.8rem;
        }

        .skill-text {
            display: flex;
            flex-direction: column;
        }

        .skill-name {
            font-size: 0.85rem;
            font-weight: bold;
            color: #fff;
        }

        .skill-desc {
            font-size: 0.75rem;
            color: #a1a1aa;
        }

        /* BOTÃO DE INICIAR COMBATE */
        .btn-fight {
            background: linear-gradient(135deg, #b91c1c, #7f1d1d);
            border: 2px solid #ef4444;
            color: #fff;
            padding: 12px;
            font-size: 1.1rem;
            font-weight: bold;
            text-transform: uppercase;
            letter-spacing: 2px;
            border-radius: 6px;
            cursor: pointer;
            box-shadow: 0 0 15px rgba(239, 68, 68, 0.4);
            transition: all 0.2s;
            text-align: center;
            margin-top: 5px;
        }

        .btn-fight:hover {
            background: linear-gradient(135deg, #dc2626, #991b1b);
            box-shadow: 0 0 25px rgba(239, 68, 68, 0.7);
        }

        /* CANVAS DA ARENA DE COMBATE */
        .arena-wrapper {
            display: none;
            flex-direction: column;
            align-items: center;
            gap: 10px;
        }

        canvas {
            background: radial-gradient(circle at center, #1f2937 0%, #030712 100%);
            border: 2px solid var(--gold);
            border-radius: 6px;
            box-shadow: 0 0 20px rgba(0,0,0,0.8);
        }

        .hud-arena {
            width: 100%;
            display: flex;
            justify-content: space-between;
            align-items: center;
            background: #111116;
            padding: 10px;
            border-radius: 6px;
            border: 1px solid #2e2e3d;
        }

        .hud-player-box {
            display: flex;
            flex-direction: column;
            width: 42%;
            gap: 4px;
        }

        .hp-bar-bg {
            width: 100%;
            height: 16px;
            background: #2a2a36;
            border-radius: 3px;
            overflow: hidden;
            border: 1px solid #444456;
        }

        .hp-bar-fill {
            height: 100%;
            width: 100%;
            transition: width 0.2s;
        }

        .p1-fill { background: #22c55e; }
        .p2-fill { background: #ef4444; }

        .power-bar-container {
            display: flex;
            gap: 4px;
        }

        .power-block {
            flex: 1;
            height: 8px;
            background: #2a2a36;
            border-radius: 2px;
        }

        .power-block.active {
            background: #3b82f6;
            box-shadow: 0 0 6px #3b82f6;
        }

        .controls-panel {
            width: 100%;
            display: flex;
            justify-content: space-between;
            gap: 10px;
            margin-top: 5px;
        }

        .tag-buttons {
            display: flex;
            gap: 8px;
        }

        .tag-btn {
            width: 55px;
            height: 55px;
            background: #20202c;
            border: 2px solid #444456;
            border-radius: 6px;
            color: #fff;
            font-size: 0.75rem;
            font-weight: bold;
            cursor: pointer;
            display: flex;
            align-items: center;
            justify-content: center;
            text-align: center;
        }

        .tag-btn.active {
            border-color: var(--gold);
            box-shadow: 0 0 8px var(--gold);
        }

        .action-btns {
            display: flex;
            gap: 8px;
        }

        .action-btn {
            background: #272736;
            border: 1px solid var(--gold);
            color: var(--gold);
            padding: 8px 14px;
            border-radius: 4px;
            font-weight: bold;
            cursor: pointer;
            text-transform: uppercase;
            font-size: 0.8rem;
        }

        .action-btn:hover:not(:disabled) {
            background: var(--gold);
            color: #000;
        }

        .action-btn:disabled {
            opacity: 0.4;
            border-color: #444;
            color: #777;
            cursor: not-allowed;
        }
    </style>
</head>
<body>

    <header>
        <h1>Multiverse Kombat 11</h1>
        <div class="currencies">
            <div class="curr-item">🪙 150,000</div>
            <div class="curr-item">💎 1,250</div>
        </div>
    </header>

    <div class="app-container">
        
        <!-- TELA 1: SELEÇÃO DE TIME E ADVERSÁRIO -->
        <div id="selectionScreen" class="selection-screen">
            
            <div class="section-title">
                <span>Monte Seu Time (3v3) & Escolha o Oponente</span>
                <span style="font-size: 0.8rem; color: #a1a1aa;">Módulo 1</span>
            </div>

            <div class="team-slots-container">
                <!-- SEU TIME -->
                <div class="slot-group">
                    <div style="font-size: 0.85rem; font-weight: bold; color: #22c55e; margin-bottom: 5px;">SUA EQUIPE (3 LUTADORES)</div>
                    <div class="slots-row">
                        <div class="card-slot active" id="slot-0" onclick="selectSlot(0)">
                            <div class="slot-name" id="slot-name-0">Vazio</div>
                            <div class="slot-universe" id="slot-univ-0">Slot 1</div>
                        </div>
                        <div class="card-slot" id="slot-1" onclick="selectSlot(1)">
                            <div class="slot-name" id="slot-name-1">Vazio</div>
                            <div class="slot-universe" id="slot-univ-1">Slot 2</div>
                        </div>
                        <div class="card-slot" id="slot-2" onclick="selectSlot(2)">
                            <div class="slot-name" id="slot-name-2">Vazio</div>
                            <div class="slot-universe" id="slot-univ-2">Slot 3</div>
                        </div>
                    </div>
                </div>

                <!-- ADVERSÁRIO -->
                <div class="slot-group" style="flex: 0.4;">
                    <div style="font-size: 0.85rem; font-weight: bold; color: var(--red-glow); margin-bottom: 5px;">ADVERSÁRIO (OPONENTE)</div>
                    <div class="slots-row">
                        <div class="card-slot enemy-slot" id="slot-enemy" onclick="selectSlot('enemy')">
                            <div class="slot-name" id="slot-name-enemy">Vazio</div>
                            <div class="slot-universe" id="slot-univ-enemy">Oponente</div>
                        </div>
                    </div>
                </div>
            </div>

            <div class="section-title">Elenco de Personagens Disponíveis</div>

            <!-- ROSTER DE PERSONAGENS PARA SELEÇÃO -->
            <div class="roster-grid" id="rosterGrid"></div>

            <!-- HABILIDADES DO PERSONAGEM SELECIONADO -->
            <div class="section-title">Habilidades do Personagem Em Foco</div>
            <div class="skills-detail-panel" id="skillsPanel">
                <div style="font-size: 0.8rem; color: #888;">Clique em qualquer personagem do elenco acima para ver suas 3 habilidades especiais de combate!</div>
            </div>

            <button class="btn-fight" onclick="startFight()">Iniciar Combate Mortal ⚔️</button>
        </div>

        <!-- TELA 2: ARENA DE COMBATE CANVA 2D -->
        <div id="arenaWrapper" class="arena-wrapper">
            
            <div class="hud-arena">
                <!-- P1 -->
                <div class="hud-player-box">
                    <div id="p1-hud-name" style="font-weight: bold; font-size: 0.85rem; color: var(--gold);">P1</div>
                    <div class="hp-bar-bg"><div id="p1-hp" class="hp-bar-fill p1-fill"></div></div>
                    <div class="power-bar-container" id="p1-power-box">
                        <div class="power-block"></div>
                        <div class="power-block"></div>
                        <div class="power-block"></div>
                    </div>
                </div>

                <div style="font-weight: bold; color: var(--gold); font-size: 1.1rem;">VS</div>

                <!-- P2 -->
                <div class="hud-player-box" style="align-items: flex-end;">
                    <div id="p2-hud-name" style="font-weight: bold; font-size: 0.85rem; color: var(--red-glow);">OPONENTE</div>
                    <div class="hp-bar-bg"><div id="p2-hp" class="hp-bar-fill p2-fill"></div></div>
                    <div class="power-bar-container" id="p2-power-box" style="width: 100%;">
                        <div class="power-block"></div>
                        <div class="power-block"></div>
                        <div class="power-block"></div>
                    </div>
                </div>
            </div>

            <canvas id="fightCanvas" width="960" height="420"></canvas>

            <!-- PAINEL DE CONTROLES NO COMBATE -->
            <div class="controls-panel">
                <div class="tag-buttons" id="tagButtons"></div>

                <div class="action-btns">
                    <button class="action-btn" onclick="executeAttack()">Ataque Básico</button>
                    <button class="action-btn" id="btn-sp1" onclick="executeSpecial(1)" disabled>Especial 1</button>
                    <button class="action-btn" id="btn-sp2" onclick="executeSpecial(2)" disabled>Especial 2</button>
                    <button class="action-btn" id="btn-sp3" onclick="executeSpecial(3)" disabled style="border-color: #ef4444; color: #ef4444;">Fatal Blow</button>
                    <button class="action-btn" onclick="exitArena()" style="border-color: #888; color: #aaa;">Sair</button>
                </div>
            </div>
        </div>

    </div>

    <script>
        // BANCO DE DADOS COMPLETO DOS PERSONAGENS E SUAS HABILIDADES
        const characters = [
            {
                id: 'spawn', name: 'Spawn', universe: 'Image Comics', color: '#00ff66',
                sp1: { name: 'Disparo de Necroplasma', desc: 'Dispara uma rajada concentrada de necroplasma verde de alto impacto.' },
                sp2: { name: 'Correntes K7-Leetha', desc: 'Ataca o oponente com correntes vivas e afiadas do traje simbiote.' },
                sp3: { name: 'Magia Ouroboros (Fatal)', desc: 'Invoca feitiçaria mística dimensional destruindo a alma do inimigo.' }
            },
            {
                id: 'scorpion', name: 'Scorpion', universe: 'Mortal Kombat', color: '#f59e0b',
                sp1: { name: 'Spear (Get Over Here!)', desc: 'Lança sua lança com corrente puxando o adversário para um golpe.' },
                sp2: { name: 'Teleport Punch', desc: 'Desaparece no fogo do Inferno e surge atrás do rival com um soco.' },
                sp3: { name: 'Toasty Hellfire (Fatal)', desc: 'Remove a máscara e incinera o oponente com o fogo infernal puro.' }
            },
            {
                id: 'subzero', name: 'Sub-Zero', universe: 'Mortal Kombat', color: '#38bdf8',
                sp1: { name: 'Gelo Congelante', desc: 'Dispara um projétil de gelo que paralisa temporariamente o inimigo.' },
                sp2: { name: 'Slide de Gelo', desc: 'Desliza rapidamente pelo chão derrubando o oponente com espinhos de gelo.' },
                sp3: { name: 'Fratura de Apagão (Fatal)', desc: 'Cria uma espada de gelo e empala o adversário com congelamento total.' }
            },
            {
                id: 'wolverine', name: 'Wolverine', universe: 'X-Men / Marvel', color: '#eab308',
                sp1: { name: 'Retalhar de Adamantium', desc: 'Sequência rápida de cortes ferozes com garras de metal indestrutível.' },
                sp2: { name: 'Fator de Cura Berserker', desc: 'Restaura vitalidade e aumenta a velocidade de ataque temporariamente.' },
                sp3: { name: 'Fúria Mutante (Fatal)', desc: 'Avança de forma selvagem desferindo dezenas de golpes letais.' }
            },
            {
                id: 'batman', name: 'Batman', universe: 'DC Comics', color: '#64748b',
                sp1: { name: 'Bat-Bumerangue Explosivo', desc: 'Lança projéteis táticos no peito do oponente que explodem ao impacto.' },
                sp2: { name: 'Bomba de Fumaça & Combo', desc: 'Desorienta o inimigo e desfere uma sequência de artes marciais.' },
                sp3: { name: 'Chamado do Batmóvel (Fatal)', desc: 'Atropela o oponente com o veículo blindado de Gotham.' }
            },
            {
                id: 'ironman', name: 'Homem de Ferro', universe: 'Marvel Comics', color: '#ef4444',
                sp1: { name: 'Repulsores Quânticos', desc: 'Dispara feixes de energia fotônica concentrada das palmas das mãos.' },
                sp2: { name: 'Micro-Mísseis Teleguiados', desc: 'Seta dezenas de mísseis perseguidores dos ombros da armadura.' },
                sp3: { name: 'Raio Unibeam no Peito (Fatal)', desc: 'Carrega o reator Arc no limite e dispara um feixe colossal.' }
            },
            {
                id: 'superman', name: 'Superman', universe: 'DC Comics', color: '#2563eb',
                sp1: { name: 'Visão de Calor', desc: 'Dispara feixes térmicos infravermelhos diretos dos olhos.' },
                sp2: { name: 'Sopro Congelante', desc: 'Sopra uma rajada congelante desacelerando o adversário.' },
                sp3: { name: 'Soco Orbital (Fatal)', desc: 'Leva o inimigo para o espaço sideral e o arremessa na Terra.' }
            },
            {
                id: 'phoenix', name: 'Jean Grey (Fênix)', universe: 'X-Men / Marvel', color: '#f97316',
                sp1: { name: 'Explosão Telecinética', desc: 'Ergue e arremessa o oponente usando a força da mente.' },
                sp2: { name: 'Onda Psíquica', desc: 'Emite uma barreira de energia psíquica que causa dano contínuo.' },
                sp3: { name: 'Chamas da Fênix (Fatal)', desc: 'Desperta a Entidade Fênix incinerando toda a arena de luta.' }
            }
        ];

        // ESTADO DA SELEÇÃO
        let myTeam = [null, null, null];
        let enemyChar = null;
        let activeSlot = 0; // 0, 1, 2 para P1 ou 'enemy'

        function initRoster() {
            const grid = document.getElementById('rosterGrid');
            grid.innerHTML = '';
            characters.forEach(char => {
                const card = document.createElement('div');
                card.className = 'char-card';
                card.onclick = () => onSelectCharacter(char);
                card.innerHTML = `
                    <div class="char-avatar" style="background: ${char.color}">${char.name[0]}</div>
                    <div class="char-info">
                        <div class="char-title">${char.name}</div>
                        <div class="char-universe-badge">${char.universe}</div>
                    </div>
                `;
                grid.appendChild(card);
            });

            // Selecionar os primeiros como padrão
            myTeam[0] = characters[0];
            myTeam[1] = characters[3];
            myTeam[2] = characters[5];
            enemyChar = characters[4];
            updateSlotsUI();
            showSkills(characters[0]);
        }

        function selectSlot(slot) {
            activeSlot = slot;
            document.querySelectorAll('.card-slot').forEach(s => s.classList.remove('active'));
            if (slot === 'enemy') {
                document.getElementById('slot-enemy').classList.add('active');
            } else {
                document.getElementById(`slot-${slot}`).classList.add('active');
            }
        }

        function onSelectCharacter(char) {
            if (activeSlot === 'enemy') {
                enemyChar = char;
            } else {
                myTeam[activeSlot] = char;
            }
            updateSlotsUI();
            showSkills(char);
        }

        function updateSlotsUI() {
            for (let i = 0; i < 3; i++) {
                const c = myTeam[i];
                document.getElementById(`slot-name-${i}`).innerText = c ? c.name : 'Vazio';
                document.getElementById(`slot-univ-${i}`).innerText = c ? c.universe : `Slot ${i+1}`;
            }
            document.getElementById('slot-name-enemy').innerText = enemyChar ? enemyChar.name : 'Vazio';
            document.getElementById('slot-univ-enemy').innerText = enemyChar ? enemyChar.universe : 'Oponente';
        }

        function showSkills(char) {
            const panel = document.getElementById('skillsPanel');
            panel.innerHTML = `
                <div style="font-weight: bold; color: ${char.color}; font-size: 0.95rem;">${char.name} (${char.universe})</div>
                <div class="skill-item">
                    <div class="skill-icon">SP1</div>
                    <div class="skill-text">
                        <div class="skill-name">${char.sp1.name}</div>
                        <div class="skill-desc">${char.sp1.desc}</div>
                    </div>
                </div>
                <div class="skill-item">
                    <div class="skill-icon">SP2</div>
                    <div class="skill-text">
                        <div class="skill-name">${char.sp2.name}</div>
                        <div class="skill-desc">${char.sp2.desc}</div>
                    </div>
                </div>
                <div class="skill-item">
                    <div class="skill-icon" style="color: #ef4444;">FB</div>
                    <div class="skill-text">
                        <div class="skill-name">${char.sp3.name}</div>
                        <div class="skill-desc">${char.sp3.desc}</div>
                    </div>
                </div>
            `;
        }

        // MOTOR DE COMBATE NO CANVAS 2D
        let activeFighterIdx = 0;
        let p1Data = null;
        let p2Data = null;
        let p1Power = 0;
        let fightInterval = null;

        function startFight() {
            if (!myTeam[0] || !enemyChar) {
                alert("Selecione pelo menos o primeiro lutador e o oponente!");
                return;
            }

            document.getElementById('selectionScreen').style.display = 'none';
            document.getElementById('arenaWrapper').style.display = 'flex';

            activeFighterIdx = 0;
            p1Data = { ...myTeam[activeFighterIdx], hp: 1000, maxHp: 1000, x: 250, y: 300 };
            p2Data = { ...enemyChar, hp: 1000, maxHp: 1000, x: 710, y: 300 };
            p1Power = 0;

            setupTagButtons();
            updateArenaHUD();
            startCanvasLoop();
        }

        function setupTagButtons() {
            const box = document.getElementById('tagButtons');
            box.innerHTML = '';
            myTeam.forEach((member, i) => {
                if (!member) return;
                const btn = document.createElement('div');
                btn.className = `tag-btn ${i === activeFighterIdx ? 'active' : ''}`;
                btn.innerText = member.name;
                btn.onclick = () => switchTag(i);
                box.appendChild(btn);
            });
        }

        function switchTag(idx) {
            if (!myTeam[idx] || idx === activeFighterIdx) return;
            activeFighterIdx = idx;
            p1Data.name = myTeam[idx].name;
            p1Data.color = myTeam[idx].color;
            setupTagButtons();
            updateArenaHUD();
        }

        function executeAttack() {
            p1Data.x += 20;
            let dmg = 40 + Math.floor(Math.random() * 20);
            p2Data.hp = Math.max(0, p2Data.hp - dmg);
            p1Power = Math.min(100, p1Power + 25);
            setTimeout(() => { p1Data.x = 250; }, 150);
            updateArenaHUD();
        }

        function executeSpecial(level) {
            let cost = level === 1 ? 33 : level === 2 ? 66 : 100;
            if (p1Power < cost) return;
            p1Power -= cost;
            let dmg = level === 1 ? 160 : level === 2 ? 320 : 550;
            p2Data.hp = Math.max(0, p2Data.hp - dmg);
            updateArenaHUD();
        }

        function updateArenaHUD() {
            document.getElementById('p1-hud-name').innerText = p1Data.name;
            document.getElementById('p2-hud-name').innerText = p2Data.name;

            document.getElementById('p1-hp').style.width = `${(p1Data.hp / p1Data.maxHp) * 100}%`;
            document.getElementById('p2-hp').style.width = `${(p2Data.hp / p2Data.maxHp) * 100}%`;

            const blocks = document.querySelectorAll('#p1-power-box .power-block');
            blocks[0].classList.toggle('active', p1Power >= 33);
            blocks[1].classList.toggle('active', p1Power >= 66);
            blocks[2].classList.toggle('active', p1Power >= 100);

            document.getElementById('btn-sp1').disabled = p1Power < 33;
            document.getElementById('btn-sp2').disabled = p1Power < 66;
            document.getElementById('btn-sp3').disabled = p1Power < 100;
        }

        function exitArena() {
            document.getElementById('arenaWrapper').style.display = 'none';
            document.getElementById('selectionScreen').style.display = 'flex';
        }

        function startCanvasLoop() {
            const canvas = document.getElementById('fightCanvas');
            const ctx = canvas.getContext('2d');

            function render() {
                ctx.clearRect(0, 0, canvas.width, canvas.height);

                // Chão do Cenário
                ctx.fillStyle = '#111827';
                ctx.fillRect(0, 320, canvas.width, 100);
                ctx.strokeStyle = '#d4af37';
                ctx.lineWidth = 2;
                ctx.beginPath();
                ctx.moveTo(0, 320); ctx.lineTo(canvas.width, 320);
                ctx.stroke();

                // Desenhar P1
                ctx.fillStyle = p1Data.color;
                ctx.beginPath();
                ctx.arc(p1Data.x, p1Data.y - 30, 30, 0, Math.PI * 2);
                ctx.fill();
                ctx.strokeStyle = '#fff';
                ctx.stroke();

                // Desenhar P2 (Oponente)
                ctx.fillStyle = p2Data.color;
                ctx.beginPath();
                ctx.arc(p2Data.x, p2Data.y - 30, 30, 0, Math.PI * 2);
                ctx.fill();
                ctx.strokeStyle = '#ef4444';
                ctx.stroke();

                requestAnimationFrame(render);
            }
            requestAnimationFrame(render);
        }

        // Inicializar aplicação ao carregar
        initRoster();
    </script>
</body>
</html>
