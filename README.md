<!DOCTYPE html>
<html lang="pt-BR">
<head>
  <meta charset="UTF-8">
  <meta name="viewport" content="width=device-width, initial-scale=1.0">
  <meta name="theme-color" content="#f6f7fb">
  <title>Estudaê — Seu espaço de estudos</title>
  <style>
    :root {
      --bg: #f6f7fb;
      --surface: #ffffff;
      --text: #20243a;
      --muted: #737991;
      --primary: #6258e8;
      --primary-light: #eeedff;
      --border: #e8eaf2;
      --green: #2e9b71;
      --shadow: 0 12px 35px rgba(37, 42, 75, .07);
      font-family: Inter, ui-sans-serif, system-ui, -apple-system, BlinkMacSystemFont, "Segoe UI", sans-serif;
    }

    * { box-sizing: border-box; }

    body {
      margin: 0;
      color: var(--text);
      background: var(--bg);
    }

    button, input, select {
      font: inherit;
    }

    button { cursor: pointer; }

    .layout {
      min-height: 100vh;
      display: grid;
      grid-template-columns: 248px 1fr;
    }

    .sidebar {
      background: var(--surface);
      border-right: 1px solid var(--border);
      padding: 28px 18px;
      display: flex;
      flex-direction: column;
      gap: 30px;
    }

    .brand {
      display: flex;
      align-items: center;
      gap: 10px;
      padding: 0 10px;
      font-size: 21px;
      font-weight: 800;
      letter-spacing: -.7px;
    }

    .brand-icon {
      width: 36px;
      height: 36px;
      display: grid;
      place-items: center;
      border-radius: 12px;
      color: white;
      background: var(--primary);
    }

    .nav-label {
      padding: 0 12px;
      color: var(--muted);
      font-size: 11px;
      font-weight: 800;
      text-transform: uppercase;
      letter-spacing: 1px;
      margin-bottom: 8px;
    }

    .nav {
      display: grid;
      gap: 5px;
    }

    .nav a {
      display: flex;
      align-items: center;
      gap: 12px;
      padding: 11px 12px;
      border-radius: 11px;
      color: #60667e;
      text-decoration: none;
      font-size: 14px;
      font-weight: 600;
    }

    .nav a:hover, .nav a.active {
      background: var(--primary-light);
      color: var(--primary);
    }

    .sidebar-note {
      margin-top: auto;
      padding: 17px;
      border-radius: 16px;
      background: #f2f0ff;
      color: #514bb1;
      font-size: 13px;
      line-height: 1.5;
    }

    main {
      width: 100%;
      max-width: 1440px;
      margin: auto;
      padding: 28px 40px 60px;
    }

    .topbar {
      display: flex;
      justify-content: space-between;
      align-items: center;
      gap: 18px;
      margin-bottom: 30px;
    }

    .search {
      width: min(440px, 100%);
      position: relative;
    }

    .search input {
      width: 100%;
      padding: 13px 15px 13px 42px;
      border: 1px solid var(--border);
      border-radius: 12px;
      background: var(--surface);
      outline: none;
    }

    .search input:focus, input:focus, select:focus {
      border-color: var(--primary);
      box-shadow: 0 0 0 3px rgba(98, 88, 232, .12);
    }

    .search span {
      position: absolute;
      left: 14px;
      top: 11px;
      font-size: 18px;
    }

    .profile {
      display: flex;
      align-items: center;
      gap: 10px;
      font-size: 14px;
      font-weight: 700;
    }

    .avatar {
      display: grid;
      place-items: center;
      width: 38px;
      height: 38px;
      border-radius: 50%;
      background: #ffe4c7;
    }

    .hero {
      display: flex;
      justify-content: space-between;
      align-items: center;
      gap: 25px;
      padding: 34px;
      border-radius: 22px;
      color: #fff;
      background: linear-gradient(115deg, #6558e9, #8978f1);
      box-shadow: var(--shadow);
      overflow: hidden;
    }

    .hero h1 {
      margin: 0 0 10px;
      font-size: clamp(25px, 4vw, 36px);
      letter-spacing: -1px;
    }

    .hero p {
      max-width: 550px;
      margin: 0 0 22px;
      color: #eeecff;
      line-height: 1.6;
    }

    .hero-art {
      font-size: clamp(62px, 9vw, 105px);
      padding: 0 18px;
    }

    .button {
      display: inline-flex;
      align-items: center;
      justify-content: center;
      gap: 8px;
      padding: 11px 16px;
      border: 0;
      border-radius: 10px;
      color: white;
      background: var(--primary);
      font-weight: 700;
      text-decoration: none;
    }

    .hero .button {
      color: var(--primary);
      background: white;
    }

    .section {
      margin-top: 36px;
      scroll-margin-top: 20px;
    }

    .section-heading {
      display: flex;
      align-items: end;
      justify-content: space-between;
      gap: 15px;
      margin-bottom: 17px;
    }

    .section-heading h2 {
      margin: 0;
      font-size: 21px;
      letter-spacing: -.4px;
    }

    .section-heading p {
      margin: 5px 0 0;
      color: var(--muted);
      font-size: 13px;
    }

    .subject-grid {
      display: grid;
      grid-template-columns: repeat(4, minmax(0, 1fr));
      gap: 14px;
    }

    .subject-card, .panel, .stat-card {
      background: var(--surface);
      border: 1px solid var(--border);
      border-radius: 16px;
      box-shadow: 0 4px 15px rgba(37, 42, 75, .025);
    }

    .subject-card {
      padding: 18px;
      text-align: left;
      transition: transform .18s, box-shadow .18s;
    }

    .subject-card:hover {
      transform: translateY(-3px);
      box-shadow: var(--shadow);
    }

    .subject-emoji {
      display: grid;
      place-items: center;
      width: 43px;
      height: 43px;
      margin-bottom: 13px;
      border-radius: 13px;
      background: var(--tile, #eeedff);
      font-size: 22px;
    }

    .subject-card strong {
      display: block;
      margin-bottom: 5px;
      font-size: 14px;
    }

    .subject-card small { color: var(--muted); }

    .two-columns {
      display: grid;
      grid-template-columns: 1.1fr .9fr;
      gap: 18px;
    }

    .panel { padding: 22px; }

    .panel h3 {
      margin: 0 0 7px;
      font-size: 17px;
    }

    .panel > p {
      margin: 0 0 18px;
      color: var(--muted);
      font-size: 13px;
      line-height: 1.5;
    }

    .form-row {
      display: flex;
      gap: 10px;
      margin-bottom: 12px;
    }

    .field {
      display: grid;
      gap: 7px;
      flex: 1;
      margin-bottom: 12px;
    }

    .field label {
      font-size: 12px;
      color: #555b72;
      font-weight: 700;
    }

    input, select {
      width: 100%;
      min-width: 0;
      padding: 11px 12px;
      border: 1px solid var(--border);
      border-radius: 9px;
      color: var(--text);
      background: white;
      outline: none;
    }

    .result {
      display: none;
      margin-top: 15px;
      padding: 14px;
      border-radius: 11px;
      background: #f4f3ff;
      color: #34305f;
      line-height: 1.6;
      font-size: 14px;
      white-space: pre-line;
    }

    .result.show { display: block; }

    .quiz-options {
      display: grid;
      gap: 8px;
      margin: 14px 0;
    }

    .quiz-option {
      padding: 11px 12px;
      border: 1px solid var(--border);
      border-radius: 9px;
      text-align: left;
      color: var(--text);
      background: white;
    }

    .quiz-option:hover { border-color: var(--primary); }
    .quiz-option.correct { border-color: #69bd91; background: #effaf3; }
    .quiz-option.wrong { border-color: #e58b8b; background: #fff2f2; }

    .stats {
      display: grid;
      grid-template-columns: repeat(3, 1fr);
      gap: 14px;
    }

    .stat-card { padding: 18px; }
    .stat-card span { color: var(--muted); font-size: 12px; }
    .stat-card strong { display: block; margin-top: 8px; font-size: 24px; }

    .small-note {
      color: var(--muted);
      font-size: 11px;
      line-height: 1.5;
      margin-top: 12px;
    }

    footer {
      margin-top: 40px;
      padding-top: 20px;
      border-top: 1px solid var(--border);
      color: var(--muted);
      font-size: 12px;
      text-align: center;
    }

    @media (max-width: 1000px) {
      .subject-grid { grid-template-columns: repeat(3, 1fr); }
      .layout { grid-template-columns: 210px 1fr; }
      main { padding: 24px; }
    }

    @media (max-width: 720px) {
      .layout { display: block; }
      .sidebar {
        position: sticky;
        top: 0;
        z-index: 3;
        padding: 12px 14px;
        border-right: 0;
        border-bottom: 1px solid var(--border);
        gap: 10px;
      }
      .brand { padding: 0 4px; }
      .sidebar > div:nth-child(2), .sidebar-note { display: none; }
      .nav {
        display: flex;
        overflow-x: auto;
      }
      .nav a { flex: 0 0 auto; padding: 9px 10px; }
      .nav-label { display: none; }
      main { padding: 18px 14px 40px; }
      .topbar { margin-bottom: 18px; }
      .profile span:last-child { display: none; }
      .hero { padding: 24px; }
      .hero-art { padding: 0; }
      .subject-grid { grid-template-columns: repeat(2, 1fr); }
      .two-columns { grid-template-columns: 1fr; }
    }

    @media (max-width: 420px) {
      .hero-art { display: none; }
      .subject-grid { gap: 9px; }
      .subject-card { padding: 13px; }
      .form-row { flex-direction: column; gap: 0; }
      .stats { gap: 8px; }
      .stat-card { padding: 13px; }
      .stat-card strong { font-size: 20px; }
    }
  </style>
</head>
<body>
  <div class="layout">
    <aside class="sidebar">
      <div class="brand">
        <span class="brand-icon">✦</span>
        <span>Estudaê</span>
      </div>

      <div>
        <div class="nav-label">Menu</div>
        <nav class="nav" aria-label="Navegação principal">
          <a class="active" href="#inicio">🏠 Início</a>
          <a href="#materias">📚 Matérias</a>
          <a href="#estudo">📝 Resumos</a>
          <a href="#ferramentas">🧮 Calculadoras</a>
          <a href="#questionario">✅ Questionário</a>
        </nav>
      </div>

      <div class="sidebar-note">
        💡 <strong>Dica de estudo</strong><br>
        Faça pausas curtas entre os períodos de concentração para ajudar a manter o foco.
      </div>
    </aside>

    <main>
      <header class="topbar">
        <label class="search">
          <span>⌕</span>
          <input id="searchInput" type="search" placeholder="Pesquisar matéria ou assunto..." aria-label="Pesquisar">
        </label>
        <div class="profile">
          <span class="avatar">😊</span>
          <span>Olá, estudante!</span>
        </div>
      </header>

      <section class="hero" id="inicio">
        <div>
          <h1>Aprender fica mais leve por aqui ✨</h1>
          <p>Organize seus estudos, revise conteúdos e pratique para chegar mais confiante na próxima prova.</p>
          <a class="button" href="#materias">Explorar matérias <span>→</span></a>
        </div>
        <div class="hero-art" aria-hidden="true">📚</div>
      </section>

      <section class="section" id="materias">
        <div class="section-heading">
          <div>
            <h2>O que vamos estudar?</h2>
            <p>Escolha uma matéria para começar.</p>
          </div>
        </div>

        <div class="subject-grid" id="subjectGrid">
          <button class="subject-card" data-subject="Matemática" style="--tile:#eeedff">
            <span class="subject-emoji">➗</span><strong>Matemática</strong><small>Frações, equações e mais</small>
          </button>
          <button class="subject-card" data-subject="Inglês" style="--tile:#e5f4ff">
            <span class="subject-emoji">🔤</span><strong>Inglês</strong><small>Vocabulário e gramática</small>
          </button>
          <button class="subject-card" data-subject="Português" style="--tile:#fff0df">
            <span class="subject-emoji">📖</span><strong>Português</strong><small>Leitura e escrita</small>
          </button>
          <button class="subject-card" data-subject="História" style="--tile:#ffe9e8">
            <span class="subject-emoji">🏛️</span><strong>História</strong><small>Sociedades e acontecimentos</small>
          </button>
          <button class="subject-card" data-subject="Geografia" style="--tile:#e7f7ed">
            <span class="subject-emoji">🌍</span><strong>Geografia</strong><small>Lugares e paisagens</small>
          </button>
          <button class="subject-card" data-subject="Artes" style="--tile:#fff0f6">
            <span class="subject-emoji">🎨</span><strong>Artes</strong><small>Expressões e movimentos</small>
          </button>
          <button class="subject-card" data-subject="Ciências" style="--tile:#e5f8f6">
            <span class="subject-emoji">🔬</span><strong>Ciências</strong><small>Vida, natureza e matéria</small>
          </button>
          <button class="subject-card" data-subject="Física" style="--tile:#eaf0ff">
            <span class="subject-emoji">⚡</span><strong>Física</strong><small>Forças, energia e movimento</small>
          </button>
          <button class="subject-card" data-subject="Educação financeira" style="--tile:#fff5d9">
            <span class="subject-emoji">💰</span><strong>Educação financeira</strong><small>Orçamento, juros e escolhas</small>
          </button>
        </div>
      </section>

      <section class="section two-columns" id="estudo">
        <div class="panel">
          <h3>📝 Criar um resumo</h3>
          <p>Informe a matéria e o tema para montar um roteiro inicial de revisão.</p>
          <div class="field">
            <label for="summarySubject">Matéria</label>
            <select id="summarySubject">
              <option>Matemática</option><option>Inglês</option><option>Português</option>
              <option>História</option><option>Geografia</option><option>Artes</option>
              <option>Ciências</option><option>Física</option><option>Educação financeira</option>
            </select>
          </div>
          <div class="field">
            <label for="summaryTopic">Tema</label>
            <input id="summaryTopic" placeholder="Ex.: frações, sistema solar, verbos...">
          </div>
          <button class="button" id="summaryButton">Montar roteiro</button>
          <div class="result" id="summaryResult" aria-live="polite"></div>
          <div class="small-note">Este exemplo cria um roteiro de revisão. Para gerar conteúdo personalizado por inteligência artificial, é necessário conectar o site a um serviço de IA.</div>
        </div>

        <div class="panel" id="questionario">
          <h3>✅ Pergunta rápida</h3>
          <p>Teste seus conhecimentos com uma questão de exemplo.</p>
          <div id="quizQuestion"></div>
          <div class="quiz-options" id="quizOptions"></div>
          <div class="result" id="quizResult" aria-live="polite"></div>
          <button class="button" id="newQuestionButton">Nova pergunta</button>
        </div>
      </section>

      <section class="section" id="ferramentas">
        <div class="section-heading">
          <div>
            <h2>Calculadoras de estudo</h2>
            <p>Confira os cálculos e use os resultados como apoio à sua revisão.</p>
          </div>
        </div>

        <div class="two-columns">
          <div class="panel">
            <h3>➗ Calculadora de frações</h3>
            <p>Some, subtraia, multiplique ou divida frações.</p>
            <div class="form-row">
              <div class="field"><label for="num1">Numerador 1</label><input id="num1" type="number" value="1"></div>
              <div class="field"><label for="den1">Denominador 1</label><input id="den1" type="number" value="2"></div>
            </div>
            <div class="form-row">
              <div class="field">
                <label for="fractionOp">Operação</label>
                <select id="fractionOp">
                  <option value="+">Somar (+)</option><option value="-">Subtrair (−)</option>
                  <option value="*">Multiplicar (×)</option><option value="/">Dividir (÷)</option>
                </select>
              </div>
              <div class="field"><label for="num2">Numerador 2</label><input id="num2" type="number" value="1"></div>
              <div class="field"><label for="den2">Denominador 2</label><input id="den2" type="number" value="3"></div>
            </div>
            <button class="button" id="fractionButton">Calcular</button>
            <div class="result" id="fractionResult" aria-live="polite"></div>
          </div>

          <div class="panel">
            <h3>√ Raiz e equação</h3>
            <p>Calcule uma raiz quadrada ou resolva uma equação do tipo ax + b = c.</p>
            <div class="field">
              <label for="sqrtValue">Raiz quadrada de</label>
              <input id="sqrtValue" type="number" min="0" placeholder="Ex.: 81">
            </div>
            <button class="button" id="sqrtButton">Calcular raiz</button>
            <div class="result" id="sqrtResult" aria-live="polite"></div>
            <hr style="border:0;border-top:1px solid var(--border);margin:20px 0">
            <div class="form-row">
              <div class="field"><label for="coefA">a</label><input id="coefA" type="number" value="2"></div>
              <div class="field"><label for="coefB">b</label><input id="coefB" type="number" value="4"></div>
              <div class="field"><label for="coefC">c</label><input id="coefC" type="number" value="10"></div>
            </div>
            <button class="button" id="equationButton">Resolver ax + b = c</button>
            <div class="result" id="equationResult" aria-live="polite"></div>
          </div>

          <div class="panel">
            <h3>🔠 Simplificar polinômio</h3>
            <p>Exemplo aceito: <strong>2x^2 + 3x - x^2 + 4</strong>.</p>
            <div class="field">
              <label for="polynomialInput">Digite o polinômio</label>
              <input id="polynomialInput" placeholder="Ex.: 2x^2 + 3x - x^2 + 4">
            </div>
            <button class="button" id="polynomialButton">Simplificar</button>
            <div class="result" id="polynomialResult" aria-live="polite"></div>
          </div>

          <div class="panel">
            <h3>💰 Juros simples</h3>
            <p>Estimativa de juros simples: juros = capital × taxa × tempo.</p>
            <div class="form-row">
              <div class="field"><label for="capital">Valor inicial (R$)</label><input id="capital" type="number" min="0" placeholder="1000"></div>
              <div class="field"><label for="rate">Taxa ao mês (%)</label><input id="rate" type="number" min="0" step="any" placeholder="2"></div>
              <div class="field"><label for="months">Meses</label><input id="months" type="number" min="0" placeholder="6"></div>
            </div>
            <button class="button" id="interestButton">Calcular juros</button>
            <div class="result" id="interestResult" aria-live="polite"></div>
            <div class="small-note">Cálculo educativo simplificado; não considera taxas, impostos ou condições específicas de produtos financeiros.</div>
          </div>
        </div>
      </section>

      <section class="section">
        <div class="section-heading">
          <div>
            <h2>Seu progresso</h2>
            <p>Um passo de cada vez já é progresso.</p>
          </div>
        </div>
        <div class="stats">
          <div class="stat-card"><span>Matérias disponíveis</span><strong>9</strong></div>
          <div class="stat-card"><span>Questionários respondidos</span><strong id="quizCount">0</strong></div>
          <div class="stat-card"><span>Acertos</span><strong id="correctCount">0</strong></div>
        </div>
      </section>

      <footer>Estudaê • Ferramenta demonstrativa para apoiar seus estudos.</footer>
    </main>
  </div>

  <script>
    const $ = (id) => document.getElementById(id);

    function showResult(id, message) {
      const element = $(id);
      element.textContent = message;
      element.classList.add("show");
    }

    function gcd(a, b) {
      a = Math.abs(a);
      b = Math.abs(b);
      while (b) [a, b] = [b, a % b];
      return a || 1;
    }

    // Pesquisa filtra os cards de matérias.
    $("searchInput").addEventListener("input", (event) => {
      const query = event.target.value.toLocaleLowerCase("pt-BR");
      document.querySelectorAll(".subject-card").forEach((card) => {
        card.style.display = card.textContent.toLocaleLowerCase("pt-BR").includes(query) ? "" : "none";
      });
    });

    // Ao clicar em uma matéria, ela é selecionada no formulário de resumo.
    document.querySelectorAll(".subject-card").forEach((card) => {
      card.addEventListener("click", () => {
        $("summarySubject").value = card.dataset.subject;
        $("summaryTopic").focus();
        document.querySelector("#estudo").scrollIntoView({ behavior: "smooth" });
      });
    });

    $("summaryButton").addEventListener("click", () => {
      const subject = $("summarySubject").value;
      const topic = $("summaryTopic").value.trim();
      if (!topic) {
        showResult("summaryResult", "Digite um tema para montar seu roteiro.");
        return;
      }
      showResult("summaryResult",
        `Roteiro de revisão — ${subject}: ${topic}\n\n` +
        `1. Escreva o que você já sabe sobre o tema.\n` +
        `2. Anote os conceitos e palavras-chave que precisa revisar.\n` +
        `3. Procure um exemplo ou exercício relacionado ao assunto.\n` +
        `4. Explique o tema com suas próprias palavras.\n` +
        `5. Termine respondendo: qual parte ainda preciso estudar melhor?`);
    });

    // Questionário de demonstração.
    const questions = [
      { subject: "Matemática", question: "Qual fração representa a metade?", options: ["1/2", "1/3", "2/3"], answer: 0, explanation: "1/2 representa uma de duas partes iguais." },
      { subject: "Ciências", question: "Qual astro está no centro do nosso sistema planetário?", options: ["A Lua", "O Sol", "Marte"], answer: 1, explanation: "O Sol é a estrela no centro do Sistema Solar." },
      { subject: "Inglês", question: "O que significa a palavra inglesa “book”?", options: ["Caderno", "Livro", "Caneta"], answer: 1, explanation: "“Book” significa “livro” em português." },
      { subject: "Geografia", question: "Em qual continente fica o Brasil?", options: ["América do Sul", "Europa", "Ásia"], answer: 0, explanation: "O Brasil está localizado na América do Sul." },
      { subject: "Física", question: "Qual unidade é usada para medir força no Sistema Internacional?", options: ["Metro", "Newton", "Litro"], answer: 1, explanation: "A força é medida em newtons (N)." },
      { subject: "Português", question: "Qual destas palavras é um verbo?", options: ["Correr", "Azul", "Mesa"], answer: 0, explanation: "“Correr” expressa uma ação e é um verbo." },
      { subject: "História", question: "O que é uma fonte histórica?", options: ["Um vestígio usado para estudar o passado", "Uma previsão do tempo", "Um tipo de mapa"], answer: 0, explanation: "Fontes históricas são vestígios e registros que ajudam a estudar o passado." },
      { subject: "Artes", question: "Qual elemento visual pode indicar contorno e direção?", options: ["Linha", "Silêncio", "Temperatura"], answer: 0, explanation: "A linha é um elemento visual usado para criar contornos e direções." },
      { subject: "Educação financeira", question: "Qual atitude ajuda a organizar o orçamento?", options: ["Anotar receitas e despesas", "Ignorar os gastos", "Gastar todo o dinheiro assim que receber"], answer: 0, explanation: "Registrar receitas e despesas ajuda a acompanhar o orçamento." }
    ];

    let currentQuestion = 0;
    let answered = false;
    let quizCount = 0;
    let correctCount = 0;

    function renderQuestion() {
      answered = false;
      $("quizResult").classList.remove("show");
      const item = questions[currentQuestion];
      $("quizQuestion").innerHTML = `<strong>${item.subject}:</strong> ${item.question}`;
      const container = $("quizOptions");
      container.innerHTML = "";
      item.options.forEach((option, index) => {
        const button = document.createElement("button");
        button.className = "quiz-option";
        button.textContent = option;
        button.addEventListener("click", () => answerQuestion(index, button));
        container.appendChild(button);
      });
    }

    function answerQuestion(index, button) {
      if (answered) return;
      answered = true;
      quizCount++;
      const item = questions[currentQuestion];
      if (index === item.answer) {
        correctCount++;
        button.classList.add("correct");
        showResult("quizResult", `Correto! ${item.explanation}`);
      } else {
        button.classList.add("wrong");
        $("quizOptions").children[item.answer].classList.add("correct");
        showResult("quizResult", `Ainda não. ${item.explanation}`);
      }
      $("quizCount").textContent = quizCount;
      $("correctCount").textContent = correctCount;
    }

    $("newQuestionButton").addEventListener("click", () => {
      currentQuestion = (currentQuestion + 1) % questions.length;
      renderQuestion();
    });

    $("fractionButton").addEventListener("click", () => {
      const a = Number($("num1").value);
      const b = Number($("den1").value);
      const c = Number($("num2").value);
      const d = Number($("den2").value);
      const op = $("fractionOp").value;

      if (![a, b, c, d].every(Number.isFinite) || b === 0 || d === 0) {
        showResult("fractionResult", "Informe números válidos e denominadores diferentes de zero.");
        return;
      }

      let numerator;
      let denominator;
      if (op === "+") { numerator = a * d + c * b; denominator = b * d; }
      if (op === "-") { numerator = a * d - c * b; denominator = b * d; }
      if (op === "*") { numerator = a * c; denominator = b * d; }
      if (op === "/") {
        if (c === 0) { showResult("fractionResult", "Não é possível dividir por uma fração igual a zero."); return; }
        numerator = a * d; denominator = b * c;
      }

      if (denominator < 0) { numerator *= -1; denominator *= -1; }
      const divisor = gcd(numerator, denominator);
      const simpleN = numerator / divisor;
      const simpleD = denominator / divisor;
      const decimal = simpleN / simpleD;
      showResult("fractionResult", `Resultado: ${simpleN}/${simpleD} = ${decimal.toLocaleString("pt-BR", { maximumFractionDigits: 6 })}`);
    });

    $("sqrtButton").addEventListener("click", () => {
      const value = Number($("sqrtValue").value);
      if ($("sqrtValue").value === "" || !Number.isFinite(value) || value < 0) {
        showResult("sqrtResult", "Digite um número igual ou maior que zero.");
        return;
      }
      const result = Math.sqrt(value);
      showResult("sqrtResult", `√${value} = ${Number.isInteger(result) ? result : result.toLocaleString("pt-BR", { maximumFractionDigits: 6 })}`);
    });

    $("equationButton").addEventListener("click", () => {
      const a = Number($("coefA").value);
      const b = Number($("coefB").value);
      const c = Number($("coefC").value);
      if (![a, b, c].every(Number.isFinite)) {
        showResult("equationResult", "Preencha os três valores da equação.");
        return;
      }
      if (a === 0) {
        showResult("equationResult", b === c ? "A igualdade é verdadeira para qualquer valor de x." : "A equação não tem solução.");
        return;
      }
      const x = (c - b) / a;
      showResult("equationResult", `ax + b = c\n${a}x + (${b}) = ${c}\nx = (${c} − ${b}) ÷ ${a}\nx = ${x.toLocaleString("pt-BR", { maximumFractionDigits: 6 })}`);
    });

    $("polynomialButton").addEventListener("click", () => {
      const input = $("polynomialInput").value.replace(/\s+/g, "");
      if (!input) { showResult("polynomialResult", "Digite um polinômio."); return; }

      const terms = input.match(/[+-]?[^+-]+/g);
      const groups = new Map();
      let valid = true;

      for (const term of terms || []) {
        const match = term.match(/^([+-]?(?:\d*\.?\d+)?)?([a-zA-Z]?)(?:\^(\d+))?$/);
        if (!match) { valid = false; break; }

        let coefficientText = match[1];
        const variable = match[2] || "";
        const exponentText = match[3];
        if (exponentText && !variable) { valid = false; break; }

        if (coefficientText === "" || coefficientText === "+") coefficientText = "1";
        if (coefficientText === "-") coefficientText = "-1";
        const coefficient = Number(coefficientText);
        if (!Number.isFinite(coefficient)) { valid = false; break; }

        const exponent = variable ? (exponentText ? Number(exponentText) : 1) : 0;
        const key = variable ? `${variable}:${exponent}` : "";
        groups.set(key, (groups.get(key) || 0) + coefficient);
      }

      if (!valid) {
        showResult("polynomialResult", "Formato não reconhecido. Tente, por exemplo: 2x^2 + 3x - x^2 + 4.");
        return;
      }

      const entries = [...groups.entries()]
        .filter(([, coefficient]) => Math.abs(coefficient) > 1e-10)
        .sort((a, b) => {
          const expA = a[0] ? Number(a[0].split(":")[1]) : -1;
          const expB = b[0] ? Number(b[0].split(":")[1]) : -1;
          return expB - expA;
        });

      if (!entries.length) { showResult("polynomialResult", "Resultado: 0"); return; }

      const output = entries.map(([key, coefficient], index) => {
        const [variable, exponent] = key ? key.split(":") : ["", "0"];
        const abs = Math.abs(coefficient);
        const coeffText = variable && abs === 1 ? "" : String(abs);
        const variableText = variable ? variable + (Number(exponent) > 1 ? `^${exponent}` : "") : "";
        const sign = coefficient < 0 ? "−" : "+";
        const body = `${coeffText}${variableText}`;
        return index === 0 ? (coefficient < 0 ? `−${body}` : body) : ` ${sign} ${body}`;
      }).join("");

      showResult("polynomialResult", `Resultado: ${output}`);
    });

    $("interestButton").addEventListener("click", () => {
      const capital = Number($("capital").value);
      const rate = Number($("rate").value);
      const months = Number($("months").value);
      if ($("capital").value === "" || $("rate").value === "" || $("months").value === "" ||
          ![capital, rate, months].every(Number.isFinite) || capital < 0 || rate < 0 || months < 0) {
        showResult("interestResult", "Preencha os campos com valores iguais ou maiores que zero.");
        return;
      }
      const interest = capital * (rate / 100) * months;
      const total = capital + interest;
      const money = (value) => value.toLocaleString("pt-BR", { style: "currency", currency: "BRL" });
      showResult("interestResult", `Juros: ${money(interest)}\nTotal estimado: ${money(total)}`);
    });

    renderQuestion();
  </script>
</body>
</html>
