<!DOCTYPE html>
<html lang="pt-BR">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>🎮 TechBarcode • Jogos em Códigos de Barras | por DLOR</title>
    <style>
        * {
            margin: 0;
            padding: 0;
            box-sizing: border-box;
        }

        body {
            background: linear-gradient(145deg, #0b0f1c 0%, #1a1f2f 100%);
            font-family: 'Segoe UI', 'Roboto', system-ui, sans-serif;
            min-height: 100vh;
            display: flex;
            flex-direction: column;
            align-items: center;
            padding: 2rem 1rem;
            color: #eef2ff;
        }

        .creator-badge {
            display: inline-flex;
            align-items: center;
            gap: 0.5rem;
            background: linear-gradient(135deg, #1e2a4a, #2b1b4d);
            border: 1px solid #5f7eff;
            padding: 0.5rem 1.4rem;
            border-radius: 50px;
            margin-bottom: 1.5rem;
            font-size: 0.95rem;
            letter-spacing: 1.5px;
            text-transform: uppercase;
            font-weight: 600;
            box-shadow: 0 0 20px #5f7eff55, inset 0 0 10px #00000066;
        }

        .creator-badge .label {
            color: #8fa5ff;
            font-weight: 400;
            font-size: 0.8rem;
        }

        .creator-badge .name {
            background: linear-gradient(135deg, #a0e9ff, #c084fc);
            -webkit-background-clip: text;
            background-clip: text;
            color: transparent;
            font-weight: 800;
            font-size: 1.1rem;
            letter-spacing: 2px;
            text-shadow: 0 0 20px #c084fc88;
        }

        h1 {
            font-size: 2.8rem;
            font-weight: 700;
            letter-spacing: 2px;
            text-transform: uppercase;
            background: linear-gradient(135deg, #a0e9ff, #6b8cff, #c084fc);
            -webkit-background-clip: text;
            background-clip: text;
            color: transparent;
            text-shadow: 0 0 20px rgba(107, 140, 255, 0.5);
            margin-bottom: 0.5rem;
            text-align: center;
        }

        .subhead {
            font-size: 1.2rem;
            color: #9aa8c7;
            margin-bottom: 3rem;
            text-align: center;
            border-bottom: 1px solid #2e3a5c;
            padding-bottom: 1rem;
            max-width: 700px;
        }

        .subhead span {
            background: #1e263a;
            padding: 0.2rem 1rem;
            border-radius: 40px;
            font-weight: 500;
            color: #b7c9ff;
            box-shadow: inset 0 0 6px #00000055;
        }

        .grid {
            display: grid;
            grid-template-columns: repeat(auto-fit, minmax(300px, 1fr));
            gap: 2rem;
            max-width: 1400px;
            width: 100%;
            margin-bottom: 3rem;
        }

        .card {
            background: rgba(18, 25, 45, 0.8);
            backdrop-filter: blur(6px);
            border-radius: 32px;
            padding: 1.8rem 1.5rem 1.8rem;
            border: 1px solid #2d3b60;
            box-shadow: 0 20px 30px -10px #00000080, 0 0 0 1px #2f3d60 inset;
            transition: transform 0.2s ease, border-color 0.3s, box-shadow 0.3s;
            display: flex;
            flex-direction: column;
            align-items: center;
        }

        .card:hover {
            transform: translateY(-6px);
            border-color: #5f7eff;
            box-shadow: 0 24px 40px -10px #1a2bff55, 0 0 0 1px #4f6bff inset;
        }

        .barcode {
            display: flex;
            align-items: center;
            justify-content: center;
            gap: 4px;
            background: #0e121f;
            padding: 1rem 1rem;
            border-radius: 16px;
            border: 1px solid #263155;
            box-shadow: inset 0 4px 8px #00000066;
            margin-bottom: 1.2rem;
            width: 100%;
            min-height: 100px;
        }

        .bar {
            background: #e8edff;
            width: 4px;
            border-radius: 4px;
            box-shadow: 0 0 6px #7b9aff;
        }

        .bar:nth-child(odd) { height: 48px; }
        .bar:nth-child(even) { height: 36px; }
        .bar:nth-child(3n) { height: 56px; width: 6px; background: #b7c9ff; }
        .bar:nth-child(4n) { height: 42px; width: 3px; }
        .bar:nth-child(5n) { height: 60px; width: 7px; background: #ffffff; }

        .game-title {
            font-size: 1.8rem;
            font-weight: 700;
            letter-spacing: 1px;
            margin: 0.4rem 0 0.2rem;
            background: linear-gradient(to right, #d6e2ff, #a5b9ff);
            -webkit-background-clip: text;
            background-clip: text;
            color: transparent;
            text-align: center;
        }

        .game-desc {
            font-size: 0.95rem;
            color: #a6b3da;
            text-align: center;
            line-height: 1.5;
            padding: 0 0.5rem;
            margin-bottom: 1.4rem;
            flex-grow: 1;
        }

        .game-desc strong {
            color: #d0ddff;
            font-weight: 600;
        }

        .play-btn {
            background: linear-gradient(145deg, #2b3b6b, #1b2542);
            border: none;
            border-radius: 60px;
            padding: 0.8rem 2rem;
            font-size: 1.1rem;
            font-weight: 600;
            color: #ecf0ff;
            letter-spacing: 0.5px;
            cursor: pointer;
            box-shadow: 0 8px 0 #0b0f1a, 0 10px 20px #00000066;
            transition: all 0.07s ease;
            width: fit-content;
            border: 1px solid #4c62a0;
        }

        .play-btn:active {
            transform: translateY(6px);
            box-shadow: 0 2px 0 #0b0f1a, 0 8px 16px #00000088;
        }

        .play-btn:hover {
            background: linear-gradient(145deg, #3e5290, #253566);
            border-color: #7b95ff;
        }

        .badge {
            font-size: 0.75rem;
            background: #17233e;
            color: #92a9ff;
            padding: 0.25rem 0.9rem;
            border-radius: 20px;
            margin-top: 0.6rem;
            border: 1px solid #35487a;
            text-transform: uppercase;
            letter-spacing: 1px;
            font-weight: 500;
        }

        .game-modal {
            position: fixed;
            top: 0;
            left: 0;
            width: 100%;
            height: 100%;
            background: #05070ee6;
            backdrop-filter: blur(12px);
            display: flex;
            align-items: center;
            justify-content: center;
            z-index: 1000;
            visibility: hidden;
            opacity: 0;
            transition: opacity 0.2s, visibility 0.2s;
        }

        .game-modal.active {
            visibility: visible;
            opacity: 1;
        }

        .modal-content {
            background: #101624;
            max-width: 600px;
            width: 90%;
            border-radius: 48px;
            padding: 2rem 2rem 2.2rem;
            border: 1px solid #3e5590;
            box-shadow: 0 30px 60px #000000cc, 0 0 0 1px #25355c inset;
            text-align: center;
            position: relative;
        }

        .modal-title {
            font-size: 2.2rem;
            font-weight: 800;
            margin-bottom: 0.75rem;
            color: #b8cbff;
        }

        .modal-sub {
            color: #8091c0;
            margin-bottom: 1.5rem;
            font-size: 1rem;
        }

        .game-canvas {
            background: #0a0e18;
            border-radius: 28px;
            padding: 1.2rem;
            margin: 1rem 0 1.5rem;
            border: 1px solid #2f4172;
            min-height: 150px;
            display: flex;
            flex-direction: column;
            align-items: center;
            justify-content: center;
            font-size: 1.5rem;
            font-weight: 500;
            color: #adc0ff;
            box-shadow: inset 0 8px 18px #00000088;
        }

        .game-canvas p {
            font-size: 1.1rem;
            color: #90a5e0;
            margin: 0.4rem 0;
        }

        .close-btn {
            background: #27355a;
            border: 1px solid #4e66a0;
            padding: 0.8rem 2rem;
            border-radius: 40px;
            color: white;
            font-weight: 600;
            font-size: 1rem;
            cursor: pointer;
            transition: 0.1s;
            box-shadow: 0 6px 0 #0d1220;
        }

        .close-btn:active {
            transform: translateY(4px);
            box-shadow: 0 2px 0 #0d1220;
        }

        .close-btn:hover {
            background: #31447a;
        }

        .footer {
            color: #57648c;
            margin-top: 2rem;
            text-align: center;
            font-size: 0.9rem;
            border-top: 1px solid #1d2742;
            padding-top: 2rem;
            width: 100%;
            max-width: 900px;
            line-height: 1.8;
        }

        .footer .signature {
            display: block;
            margin-top: 0.6rem;
            font-size: 1rem;
            letter-spacing: 2px;
        }

        .footer .signature strong {
            background: linear-gradient(135deg, #a0e9ff, #c084fc);
            -webkit-background-clip: text;
            background-clip: text;
            color: transparent;
            font-weight: 800;
            font-size: 1.2rem;
            letter-spacing: 3px;
        }
    </style>
</head>
<body>

    <div class="creator-badge">
        <span class="label">criado por</span>
        <span class="name">DLOR</span>
    </div>

    <h1>⚡ TECH BARCODE</h1>
    <div class="subhead">
        <span>cada código de barras = um jogo único</span> &nbsp;👉 escaneie mentalmente e jogue
    </div>

    <div class="grid" id="gameGrid"></div>

    <div class="game-modal" id="gameModal">
        <div class="modal-content">
            <div class="modal-title" id="modalGameTitle">Jogo</div>
            <div class="modal-sub">🧬 executando código de barras...</div>
            <div class="game-canvas" id="modalGameCanvas"></div>
            <button class="close-btn" id="closeModalBtn">Fechar jogo</button>
        </div>
    </div>

    <div class="footer">
        ⚡ tecnologia • códigos de barras interativos • cada jogo é uma experiência única
        <span class="signature">criado por <strong>DLOR</strong></span>
    </div>

    <script>
        (function() {
            const games = [
                {
                    id: 1,
                    title: 'PONG BARRAS',
                    desc: '<strong>Visual:</strong> Barras brancas verticais que lembram raquetes. Bola quicando entre números.',
                    bars: [42, 56, 38, 60, 32, 48, 44, 62, 36, 52, 40, 58, 34, 46, 50, 30, 54, 42, 60, 38],
                    gameAction: () => `<p>🏓 PONTOS: 3 x 2</p><p>▮▮▮▮▮▮▮▮▮  BOLA  ●</p><p>▮▮▮▮▮▮▮▮▮  raquete esquerda</p><p>▮▮▮▮▮▮▮▮▮  raquete direita</p><p style="color:#8fa9ff;">Pong em barras — a bola acelera!</p>`
                },
                {
                    id: 2,
                    title: 'SNAKE BARCODE',
                    desc: '<strong>Visual:</strong> Barras irregulares simulam a cobrinha. Comida é um código vermelho.',
                    bars: [30, 58, 62, 44, 48, 36, 52, 60, 42, 56, 34, 50, 46, 40, 54, 38, 62, 44, 58, 32],
                    gameAction: () => `<p>🐍 COBRA: ████▓▓▓▒▒▒░░░</p><p>🍎 comida:  █▀▀▀▀▀█</p><p>▮▮▮▮▮▮▮▮▮▮▮▮▮▮▮</p><p>Pontos: 47  |  Recorde: 112</p>`
                },
                {
                    id: 3,
                    title: 'SPACE INVADERS',
                    desc: '<strong>Visual:</strong> Barras em diferentes alturas representam aliens e nave.',
                    bars: [50, 40, 60, 35, 55, 45, 65, 30, 52, 42, 58, 38, 48, 62, 33, 57, 43, 53, 47, 59],
                    gameAction: () => `<p>👾 ALIENS: █ █ █ █ █</p><p>🚀 NAVE:   █ █ █</p><p>▮▮▮▮▮▮▮▮▮▮▮▮▮▮▮▮</p><p>Inimigos restantes: 8  |  Score: 230</p>`
                },
                {
                    id: 4,
                    title: 'TETRIS CODE',
                    desc: '<strong>Visual:</strong> Barras coloridas empilhadas como blocos de tetris.',
                    bars: [44, 60, 38, 52, 46, 62, 34, 56, 42, 50, 48, 58, 36, 54, 40, 62, 44, 52, 38, 60],
                    gameAction: () => `<p>🟦🟦🟦  ██████  🟨🟨</p><p>🟦🟦  ██████  🟨🟨🟨</p><p>🟦  ██████  🟨</p><p>Linhas: 12  |  Nível: 7</p><p>Próxima peça: ████</p>`
                },
                {
                    id: 5,
                    title: 'BREAKOUT BARS',
                    desc: '<strong>Visual:</strong> Barras horizontais que representam tijolos e raquete.',
                    bars: [36, 48, 60, 32, 54, 42, 58, 38, 50, 44, 62, 34, 52, 46, 56, 40, 58, 38, 48, 60],
                    gameAction: () => `<p>🧱 TIJOLOS: ███ ███ ███ ███</p><p>▬▬▬▬▬▬▬▬▬▬▬▬▬▬▬▬</p><p>⚪ BOLA: ●</p><p>Vidas: 3  |  Tijolos: 12</p>`
                },
                {
                    id: 6,
                    title: 'FLAPPY BARRAS',
                    desc: '<strong>Visual:</strong> Barras que lembram canos verdes e o pássaro é um código.',
                    bars: [50, 60, 34, 46, 58, 38, 54, 44, 62, 36, 52, 48, 56, 40, 60, 32, 58, 42, 50, 46],
                    gameAction: () => `<p>🐤 PÁSSARO: █▀▀█</p><p>🟩 CANO: ████████</p><p>          ████████</p><p>          ████████</p><p>Pontos: 8  |  Recorde: 23</p>`
                }
            ];

            const gameGrid = document.getElementById('gameGrid');
            const modal = document.getElementById('gameModal');
            const modalTitle = document.getElementById('modalGameTitle');
            const modalCanvas = document.getElementById('modalGameCanvas');
            const closeModalBtn = document.getElementById('closeModalBtn');

            function renderBars(barsArray) {
                let barsHtml = '';
                barsArray.forEach((height, index) => {
                    let bgColor = '#e8edff';
                    let width = '4px';
                    if (index % 7 === 0) { bgColor = '#b7c9ff'; width = '5px'; }
                    if (index % 5 === 0) { bgColor = '#ffffff'; width = '6px'; }
                    if (index % 11 === 0) { bgColor = '#9bb0ff'; width = '7px'; }
                    const barHeight = Math.min(70, Math.max(24, height));
                    barsHtml += `<div class="bar" style="height: ${barHeight}px; width: ${width}; background: ${bgColor}; box-shadow: 0 0 8px ${bgColor}80;"></div>`;
                });
                return barsHtml;
            }

            games.forEach(game => {
                const card = document.createElement('div');
                card.className = 'card';
                card.dataset.gameId = game.id;

                const barcodeDiv = document.createElement('div');
                barcodeDiv.className = 'barcode';
                barcodeDiv.innerHTML = renderBars(game.bars);

                const title = document.createElement('div');
                title.className = 'game-title';
                title.textContent = game.title;

                const desc = document.createElement('div');
                desc.className = 'game-desc';
                desc.innerHTML = game.desc;

                const badge = document.createElement('div');
                badge.className = 'badge';
                badge.textContent = `código #${game.id.toString().padStart(3, '0')} • DLOR`;

                const btn = document.createElement('button');
                btn.className = 'play-btn';
                btn.textContent = '▶ JOGAR';
                btn.addEventListener('click', (e) => {
                    e.stopPropagation();
                    modalTitle.textContent = game.title;
                    modalCanvas.innerHTML = game.gameAction();
                    modal.classList.add('active');
                });

                card.appendChild(barcodeDiv);
                card.appendChild(title);
                card.appendChild(desc);
                card.appendChild(btn);
                card.appendChild(badge);

                gameGrid.appendChild(card);
            });

            closeModalBtn.addEventListener('click', () => {
                modal.classList.remove('active');
            });

            modal.addEventListener('click', (e) => {
                if (e.target === modal) {
                    modal.classList.remove('active');
                }
            });

            document.addEventListener('keydown', (e) => {
                if (e.key === 'Escape' && modal.classList.contains('active')) {
                    modal.classList.remove('active');
                }
            });

            setInterval(() => {
                document.querySelectorAll('.barcode .bar').forEach((bar) => {
                    if (Math.random() > 0.97) {
                        bar.style.transition = 'box-shadow 0.2s';
                        bar.style.boxShadow = '0 0 20px #7b9aff';
                        setTimeout(() => {
                            bar.style.boxShadow = '0 0 6px #7b9aff';
                        }, 150);
                    }
                });
            }, 300);

        })();
    </script>
</body>
</html>
