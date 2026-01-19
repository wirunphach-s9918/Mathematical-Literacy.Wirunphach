<html lang="th" class="h-full">
 <head>
  <meta charset="UTF-8">
  <meta name="viewport" content="width=device-width, initial-scale=1.0">
  <title>คณิตศาสตร์การเงิน ป.5</title>
  <script src="https://cdn.tailwindcss.com"></script>
  <script src="/_sdk/element_sdk.js"></script>
  <link href="https://fonts.googleapis.com/css2?family=Kanit:wght@300;400;500;600;700&amp;display=swap" rel="stylesheet">
  <style>
    body {
      box-sizing: border-box;
      font-family: 'Kanit', sans-serif;
    }
    
    .coin {
      animation: bounce 0.5s ease-in-out;
    }
    
    @keyframes bounce {
      0%, 100% { transform: translateY(0); }
      50% { transform: translateY(-10px); }
    }
    
    @keyframes celebrate {
      0% { transform: scale(1); }
      50% { transform: scale(1.1); }
      100% { transform: scale(1); }
    }
    
    .celebrate {
      animation: celebrate 0.5s ease-in-out;
    }
    
    @keyframes fadeIn {
      from { opacity: 0; transform: translateY(20px); }
      to { opacity: 1; transform: translateY(0); }
    }
    
    .fade-in {
      animation: fadeIn 0.4s ease-out;
    }
    
    .product-card:hover {
      transform: translateY(-5px);
      box-shadow: 0 10px 25px rgba(0,0,0,0.1);
    }
    
    .product-card {
      transition: all 0.3s ease;
    }
  </style>
  <style>@view-transition { navigation: auto; }</style>
  <script src="/_sdk/data_sdk.js" type="text/javascript"></script>
 </head>
 <body class="h-full">
  <div id="app" class="h-full overflow-auto"><!-- Main Menu -->
   <div id="menu-screen" class="min-h-full p-4 md:p-8">
    <div class="max-w-4xl mx-auto"><!-- Header -->
     <div class="text-center mb-8 fade-in">
      <div class="text-6xl mb-4">
       💰
      </div>
      <h1 id="main-title" class="text-3xl md:text-4xl font-bold mb-2">คณิตศาสตร์การเงิน ป.5</h1>
      <p class="text-lg opacity-80">เรียนรู้เรื่องเงินอย่างสนุกสนาน!</p>
     </div><!-- Score Display -->
     <div class="flex justify-center gap-4 mb-8">
      <div class="px-6 py-3 rounded-2xl shadow-lg">
       <div class="text-sm opacity-70">
        คะแนนรวม
       </div>
       <div id="total-score" class="text-2xl font-bold">
        0
       </div>
      </div>
      <div class="px-6 py-3 rounded-2xl shadow-lg">
       <div class="text-sm opacity-70">
        ด่านที่ผ่าน
       </div>
       <div id="levels-passed" class="text-2xl font-bold">
        0/3
       </div>
      </div>
     </div><!-- Game Modes -->
     <div class="grid md:grid-cols-3 gap-6"><!-- Mode 1: Counting Money -->
      <div class="game-card rounded-3xl p-6 shadow-xl cursor-pointer product-card" onclick="startGame(1)">
       <div class="text-5xl mb-4 text-center">
        🪙
       </div>
       <h2 class="text-xl font-bold mb-2 text-center">นับเงิน</h2>
       <p class="text-sm opacity-80 text-center mb-4">ฝึกนับเหรียญและธนบัตร</p>
       <div class="text-center"><span class="inline-block px-4 py-2 rounded-full text-sm font-medium">เริ่มเล่น →</span>
       </div>
      </div><!-- Mode 2: Change Calculation -->
      <div class="game-card rounded-3xl p-6 shadow-xl cursor-pointer product-card" onclick="startGame(2)">
       <div class="text-5xl mb-4 text-center">
        🛒
       </div>
       <h2 class="text-xl font-bold mb-2 text-center">ทอนเงิน</h2>
       <p class="text-sm opacity-80 text-center mb-4">คำนวณเงินทอนจากการซื้อของ</p>
       <div class="text-center"><span class="inline-block px-4 py-2 rounded-full text-sm font-medium">เริ่มเล่น →</span>
       </div>
      </div><!-- Mode 3: Shopping -->
      <div class="game-card rounded-3xl p-6 shadow-xl cursor-pointer product-card" onclick="startGame(3)">
       <div class="text-5xl mb-4 text-center">
        🏪
       </div>
       <h2 class="text-xl font-bold mb-2 text-center">ซื้อของ</h2>
       <p class="text-sm opacity-80 text-center mb-4">เลือกซื้อสินค้าให้พอดีกับงบ</p>
       <div class="text-center"><span class="inline-block px-4 py-2 rounded-full text-sm font-medium">เริ่มเล่น →</span>
       </div>
      </div>
     </div><!-- Tips Section -->
     <div class="mt-8 p-6 rounded-2xl shadow-lg">
      <h3 class="font-bold mb-3 flex items-center gap-2"><span>💡</span> เคล็ดลับการนับเงิน</h3>
      <ul class="space-y-2 text-sm">
       <li>• เริ่มนับจากธนบัตร/เหรียญที่มีค่ามากที่สุดก่อน</li>
       <li>• จัดกลุ่มเหรียญเป็นกองๆ ละ 10 หรือ 100 บาท</li>
       <li>• ตรวจสอบผลลัพธ์โดยการนับซ้ำ</li>
      </ul>
     </div><!-- Creator Info -->
     <div class="mt-6 p-6 rounded-2xl shadow-lg text-center">
      <div class="text-3xl mb-3">
       👩‍💻
      </div>
      <h3 class="font-bold mb-2">ผู้สร้างเกม</h3>
      <p class="text-sm opacity-90">นางสาววิรัลพัชษ์ สว่างเดือน</p>
      <p class="text-sm opacity-80">ชั้นประถมศึกษาปีที่ 5/5 สาย MEP</p>
     </div>
    </div>
   </div><!-- Game Screen -->
   <div id="game-screen" class="min-h-full p-4 md:p-8 hidden">
    <div class="max-w-2xl mx-auto"><!-- Game Header -->
     <div class="flex justify-between items-center mb-6"><button onclick="backToMenu()" class="px-4 py-2 rounded-xl font-medium flex items-center gap-2 transition-all hover:scale-105"> ← กลับ </button>
      <div class="flex gap-3">
       <div class="px-4 py-2 rounded-xl"><span class="opacity-70">ข้อ:</span> <span id="current-question" class="font-bold">1</span>/5
       </div>
       <div class="px-4 py-2 rounded-xl"><span class="opacity-70">คะแนน:</span> <span id="game-score" class="font-bold">0</span>
       </div>
      </div>
     </div><!-- Question Area -->
     <div id="question-area" class="rounded-3xl p-6 md:p-8 shadow-xl mb-6">
      <h2 id="game-title" class="text-xl font-bold mb-4 text-center"></h2>
      <div id="question-content" class="text-center mb-6"></div>
      <div id="answer-area"></div>
     </div><!-- Feedback Area -->
     <div id="feedback" class="rounded-2xl p-4 text-center hidden">
      <div id="feedback-icon" class="text-4xl mb-2"></div>
      <div id="feedback-text" class="font-medium"></div>
     </div>
    </div>
   </div><!-- Result Screen -->
   <div id="result-screen" class="min-h-full p-4 md:p-8 hidden">
    <div class="max-w-md mx-auto text-center">
     <div id="result-emoji" class="text-8xl mb-6 celebrate"></div>
     <h2 id="result-title" class="text-3xl font-bold mb-4"></h2>
     <p id="result-score" class="text-xl mb-6"></p>
     <p id="encouragement" class="text-lg mb-8 opacity-80"></p>
     <div class="space-y-4"><button onclick="restartGame()" class="w-full py-4 rounded-2xl font-bold text-lg transition-all hover:scale-105"> 🔄 เล่นอีกครั้ง </button> <button onclick="backToMenu()" class="w-full py-4 rounded-2xl font-bold text-lg transition-all hover:scale-105"> 🏠 กลับหน้าหลัก </button>
     </div>
    </div>
   </div>
  </div>
  <script>
    // Default configuration
    const defaultConfig = {
      app_title: 'คณิตศาสตร์การเงิน ป.5',
      encouragement_text: 'เก่งมาก! ทำต่อไปนะ',
      background_color: '#FFF4F9',
      surface_color: '#FFFFFF',
      text_color: '#2D3748',
      primary_color: '#EC4899',
      secondary_color: '#A78BFA'
    };

    let config = { ...defaultConfig };

    // Game state
    let currentMode = 0;
    let currentQuestion = 0;
    let gameScore = 0;
    let totalScore = 0;
    let levelsPassed = [false, false, false];
    let questions = [];
    let correctAnswer = 0;

    // Thai currency
    const coins = [
      { value: 10, emoji: '🪙', name: 'เหรียญ 10 บาท' },
      { value: 5, emoji: '🪙', name: 'เหรียญ 5 บาท' },
      { value: 2, emoji: '🪙', name: 'เหรียญ 2 บาท' },
      { value: 1, emoji: '🪙', name: 'เหรียญ 1 บาท' }
    ];

    const bills = [
      { value: 1000, emoji: '💵', name: 'ธนบัตร 1,000 บาท' },
      { value: 500, emoji: '💵', name: 'ธนบัตร 500 บาท' },
      { value: 100, emoji: '💵', name: 'ธนบัตร 100 บาท' },
      { value: 50, emoji: '💵', name: 'ธนบัตร 50 บาท' },
      { value: 20, emoji: '💵', name: 'ธนบัตร 20 บาท' }
    ];

    const products = [
      { name: 'ดินสอ', emoji: '✏️', price: 15 },
      { name: 'ยางลบ', emoji: '🧽', price: 8 },
      { name: 'ไม้บรรทัด', emoji: '📏', price: 25 },
      { name: 'สมุด', emoji: '📓', price: 35 },
      { name: 'กระเป๋า', emoji: '🎒', price: 299 },
      { name: 'น้ำดื่ม', emoji: '💧', price: 10 },
      { name: 'ขนมปัง', emoji: '🍞', price: 20 },
      { name: 'นม', emoji: '🥛', price: 15 },
      { name: 'ไอศกรีม', emoji: '🍦', price: 25 },
      { name: 'ลูกอม', emoji: '🍬', price: 5 },
      { name: 'คุกกี้', emoji: '🍪', price: 30 },
      { name: 'น้ำผลไม้', emoji: '🧃', price: 18 }
    ];

    // Initialize SDK
    async function initApp() {
      if (window.elementSdk) {
        await window.elementSdk.init({
          defaultConfig,
          onConfigChange: async (newConfig) => {
            config = { ...defaultConfig, ...newConfig };
            applyStyles();
          },
          mapToCapabilities: (cfg) => ({
            recolorables: [
              {
                get: () => cfg.background_color || defaultConfig.background_color,
                set: (v) => { cfg.background_color = v; window.elementSdk.setConfig({ background_color: v }); }
              },
              {
                get: () => cfg.surface_color || defaultConfig.surface_color,
                set: (v) => { cfg.surface_color = v; window.elementSdk.setConfig({ surface_color: v }); }
              },
              {
                get: () => cfg.text_color || defaultConfig.text_color,
                set: (v) => { cfg.text_color = v; window.elementSdk.setConfig({ text_color: v }); }
              },
              {
                get: () => cfg.primary_color || defaultConfig.primary_color,
                set: (v) => { cfg.primary_color = v; window.elementSdk.setConfig({ primary_color: v }); }
              },
              {
                get: () => cfg.secondary_color || defaultConfig.secondary_color,
                set: (v) => { cfg.secondary_color = v; window.elementSdk.setConfig({ secondary_color: v }); }
              }
            ],
            borderables: [],
            fontEditable: undefined,
            fontSizeable: undefined
          }),
          mapToEditPanelValues: (cfg) => new Map([
            ['app_title', cfg.app_title || defaultConfig.app_title],
            ['encouragement_text', cfg.encouragement_text || defaultConfig.encouragement_text]
          ])
        });
        config = { ...defaultConfig, ...window.elementSdk.config };
      }
      applyStyles();
    }

    function applyStyles() {
      const bg = config.background_color || defaultConfig.background_color;
      const surface = config.surface_color || defaultConfig.surface_color;
      const text = config.text_color || defaultConfig.text_color;
      const primary = config.primary_color || defaultConfig.primary_color;
      const secondary = config.secondary_color || defaultConfig.secondary_color;

      document.body.style.backgroundColor = bg;
      document.body.style.color = text;

      document.getElementById('main-title').textContent = config.app_title || defaultConfig.app_title;

      // Score displays
      document.querySelectorAll('#menu-screen > div > .flex.justify-center > div').forEach(el => {
        el.style.backgroundColor = surface;
      });

      // Game cards
      document.querySelectorAll('.game-card').forEach(card => {
        card.style.backgroundColor = surface;
        const badge = card.querySelector('span');
        if (badge) {
          badge.style.backgroundColor = secondary;
          badge.style.color = text;
        }
      });

      // Tips section
      const tips = document.querySelector('#menu-screen .mt-8.p-6');
      if (tips) {
        tips.style.backgroundColor = surface;
      }
      
      // Creator info
      const creator = document.querySelector('#menu-screen .mt-6.p-6');
      if (creator) {
        creator.style.backgroundColor = surface;
      }

      // Game screen elements
      const questionArea = document.getElementById('question-area');
      if (questionArea) {
        questionArea.style.backgroundColor = surface;
      }

      // Back button
      const backBtn = document.querySelector('#game-screen button');
      if (backBtn) {
        backBtn.style.backgroundColor = secondary;
        backBtn.style.color = text;
      }

      // Score displays in game
      document.querySelectorAll('#game-screen .px-4.py-2.rounded-xl').forEach(el => {
        el.style.backgroundColor = surface;
      });

      // Result screen buttons
      document.querySelectorAll('#result-screen button').forEach((btn, i) => {
        if (i === 0) {
          btn.style.backgroundColor = primary;
          btn.style.color = '#FFFFFF';
        } else {
          btn.style.backgroundColor = secondary;
          btn.style.color = text;
        }
      });
    }

    function showScreen(screenId) {
      ['menu-screen', 'game-screen', 'result-screen'].forEach(id => {
        document.getElementById(id).classList.add('hidden');
      });
      document.getElementById(screenId).classList.remove('hidden');
    }

    function startGame(mode) {
      currentMode = mode;
      currentQuestion = 0;
      gameScore = 0;
      generateQuestions();
      showScreen('game-screen');
      showQuestion();
    }

    function generateQuestions() {
      questions = [];
      for (let i = 0; i < 5; i++) {
        switch (currentMode) {
          case 1:
            questions.push(generateCountingQuestion());
            break;
          case 2:
            questions.push(generateChangeQuestion());
            break;
          case 3:
            questions.push(generateShoppingQuestion());
            break;
        }
      }
    }

    function generateCountingQuestion() {
      const numCoins = {};
      let total = 0;
      
      // Random bills
      const billCount = Math.floor(Math.random() * 3);
      for (let i = 0; i < billCount; i++) {
        const bill = bills[Math.floor(Math.random() * 3) + 2]; // 20, 50, 100
        numCoins[bill.value] = (numCoins[bill.value] || 0) + 1;
        total += bill.value;
      }
      
      // Random coins
      const coinCount = Math.floor(Math.random() * 5) + 2;
      for (let i = 0; i < coinCount; i++) {
        const coin = coins[Math.floor(Math.random() * coins.length)];
        numCoins[coin.value] = (numCoins[coin.value] || 0) + 1;
        total += coin.value;
      }
      
      return { type: 'counting', money: numCoins, answer: total };
    }

    function generateChangeQuestion() {
      const product = products[Math.floor(Math.random() * products.length)];
      const payOptions = [20, 50, 100, 500, 1000].filter(v => v >= product.price);
      const paid = payOptions[Math.floor(Math.random() * payOptions.length)];
      const change = paid - product.price;
      
      return { type: 'change', product, paid, answer: change };
    }

    function generateShoppingQuestion() {
      const budget = [50, 100, 200][Math.floor(Math.random() * 3)];
      const availableProducts = products.filter(p => p.price <= budget);
      const shuffled = availableProducts.sort(() => Math.random() - 0.5).slice(0, 4);
      
      // Find valid combinations
      let validCombo = [];
      let comboTotal = 0;
      for (const p of shuffled) {
        if (comboTotal + p.price <= budget) {
          validCombo.push(p);
          comboTotal += p.price;
        }
      }
      
      return { type: 'shopping', budget, products: shuffled, validCombo, answer: comboTotal };
    }

    function showQuestion() {
      const q = questions[currentQuestion];
      document.getElementById('current-question').textContent = currentQuestion + 1;
      document.getElementById('game-score').textContent = gameScore;
      document.getElementById('feedback').classList.add('hidden');
      
      const surface = config.surface_color || defaultConfig.surface_color;
      const primary = config.primary_color || defaultConfig.primary_color;
      const secondary = config.secondary_color || defaultConfig.secondary_color;
      const text = config.text_color || defaultConfig.text_color;
      
      switch (q.type) {
        case 'counting':
          document.getElementById('game-title').textContent = '🪙 นับเงิน';
          let moneyDisplay = '<div class="flex flex-wrap justify-center gap-3 mb-6">';
          
          Object.entries(q.money).forEach(([value, count]) => {
            for (let i = 0; i < count; i++) {
              const isBill = parseInt(value) >= 20;
              moneyDisplay += `<div class="coin p-3 rounded-xl text-center" style="background-color: ${secondary}; animation-delay: ${i * 0.1}s">
                <div class="text-2xl">${isBill ? '💵' : '🪙'}</div>
                <div class="text-sm font-bold">${value} ฿</div>
              </div>`;
            }
          });
          
          moneyDisplay += '</div><p class="text-lg mb-4">รวมเงินทั้งหมดเท่าไร?</p>';
          document.getElementById('question-content').innerHTML = moneyDisplay;
          
          correctAnswer = q.answer;
          showNumberInput();
          break;
          
        case 'change':
          document.getElementById('game-title').textContent = '🛒 ทอนเงิน';
          document.getElementById('question-content').innerHTML = `
            <div class="text-6xl mb-4">${q.product.emoji}</div>
            <p class="text-xl mb-2">${q.product.name}</p>
            <p class="text-2xl font-bold mb-4" style="color: ${primary}">${q.product.price} บาท</p>
            <p class="text-lg">จ่ายด้วยเงิน <span class="font-bold">${q.paid}</span> บาท</p>
            <p class="text-lg mt-2">ได้เงินทอนเท่าไร?</p>
          `;
          
          correctAnswer = q.answer;
          showNumberInput();
          break;
          
        case 'shopping':
          document.getElementById('game-title').textContent = '🏪 ซื้อของ';
          let shoppingDisplay = `
            <p class="text-lg mb-2">งบประมาณ: <span class="font-bold text-2xl" style="color: ${primary}">${q.budget} บาท</span></p>
            <p class="text-sm mb-4 opacity-70">เลือกสินค้าที่ซื้อได้โดยไม่เกินงบ</p>
            <div class="grid grid-cols-2 gap-3 mb-4">
          `;
          
          q.products.forEach((p, i) => {
            shoppingDisplay += `
              <div id="product-${i}" class="product-option p-4 rounded-xl cursor-pointer transition-all" 
                   style="background-color: ${secondary}"
                   onclick="toggleProduct(${i}, ${p.price})">
                <div class="text-3xl mb-2">${p.emoji}</div>
                <div class="font-medium">${p.name}</div>
                <div class="font-bold">${p.price} ฿</div>
              </div>
            `;
          });
          
          shoppingDisplay += '</div>';
          shoppingDisplay += `<div class="text-lg">รวมเป็น: <span id="shopping-total" class="font-bold" style="color: ${primary}">0</span> บาท</div>`;
          
          document.getElementById('question-content').innerHTML = shoppingDisplay;
          
          correctAnswer = q.budget;
          document.getElementById('answer-area').innerHTML = `
            <button onclick="checkShoppingAnswer()" class="w-full py-4 rounded-xl font-bold text-lg text-white transition-all hover:scale-105" style="background-color: ${primary}">
              ✓ ตรวจคำตอบ
            </button>
          `;
          
          window.selectedProducts = [];
          window.shoppingBudget = q.budget;
          break;
      }
      
      applyStyles();
    }

    function showNumberInput() {
      const primary = config.primary_color || defaultConfig.primary_color;
      const secondary = config.secondary_color || defaultConfig.secondary_color;
      const text = config.text_color || defaultConfig.text_color;
      
      document.getElementById('answer-area').innerHTML = `
        <div class="flex justify-center gap-2 mb-4">
          <input type="number" id="answer-input" 
                 class="w-32 text-center text-2xl font-bold p-3 rounded-xl border-2 focus:outline-none"
                 style="border-color: ${primary}; color: ${text}"
                 placeholder="?"
                 onkeypress="if(event.key === 'Enter') checkAnswer()">
          <span class="text-2xl self-center">บาท</span>
        </div>
        <button onclick="checkAnswer()" class="w-full py-4 rounded-xl font-bold text-lg text-white transition-all hover:scale-105" style="background-color: ${primary}">
          ✓ ตรวจคำตอบ
        </button>
      `;
    }

    window.selectedProducts = [];
    window.shoppingBudget = 0;

    function toggleProduct(index, price) {
      const el = document.getElementById(`product-${index}`);
      const primary = config.primary_color || defaultConfig.primary_color;
      const secondary = config.secondary_color || defaultConfig.secondary_color;
      
      const idx = window.selectedProducts.indexOf(index);
      if (idx > -1) {
        window.selectedProducts.splice(idx, 1);
        el.style.backgroundColor = secondary;
        el.style.border = 'none';
      } else {
        window.selectedProducts.push(index);
        el.style.backgroundColor = primary + '30';
        el.style.border = `3px solid ${primary}`;
      }
      
      const q = questions[currentQuestion];
      const total = window.selectedProducts.reduce((sum, i) => sum + q.products[i].price, 0);
      document.getElementById('shopping-total').textContent = total;
    }

    function checkAnswer() {
      const input = document.getElementById('answer-input');
      const userAnswer = parseInt(input.value);
      
      if (isNaN(userAnswer)) {
        showFeedback(false, 'กรุณาใส่ตัวเลข');
        return;
      }
      
      const isCorrect = userAnswer === correctAnswer;
      if (isCorrect) {
        gameScore += 20;
      }
      
      showFeedback(isCorrect, isCorrect ? 
        `ถูกต้อง! คำตอบคือ ${correctAnswer} บาท` : 
        `ไม่ถูกต้อง คำตอบที่ถูกคือ ${correctAnswer} บาท`);
    }

    function checkShoppingAnswer() {
      const q = questions[currentQuestion];
      const total = window.selectedProducts.reduce((sum, i) => sum + q.products[i].price, 0);
      
      const isCorrect = total <= window.shoppingBudget && total > 0;
      if (isCorrect) {
        gameScore += 20;
      }
      
      showFeedback(isCorrect, isCorrect ? 
        `เยี่ยม! ซื้อของได้ ${total} บาท ไม่เกินงบ ${window.shoppingBudget} บาท` : 
        total === 0 ? 'กรุณาเลือกสินค้าอย่างน้อย 1 ชิ้น' : `เกินงบ! รวมเป็น ${total} บาท แต่มีงบแค่ ${window.shoppingBudget} บาท`);
    }

    function showFeedback(isCorrect, message) {
      const feedback = document.getElementById('feedback');
      const primary = config.primary_color || defaultConfig.primary_color;
      
      feedback.classList.remove('hidden');
      feedback.style.backgroundColor = isCorrect ? '#D1FAE5' : '#FEE2E2';
      feedback.style.color = isCorrect ? '#065F46' : '#991B1B';
      
      document.getElementById('feedback-icon').textContent = isCorrect ? '🎉' : '💪';
      document.getElementById('feedback-text').textContent = message;
      
      if (isCorrect || message.includes('ไม่ถูกต้อง') || message.includes('เกินงบ')) {
        setTimeout(() => {
          currentQuestion++;
          if (currentQuestion < 5) {
            showQuestion();
          } else {
            showResults();
          }
        }, 2000);
      }
    }

    function showResults() {
      const percentage = (gameScore / 100) * 100;
      let emoji, title;
      
      if (percentage >= 80) {
        emoji = '🏆';
        title = 'ยอดเยี่ยมมาก!';
        levelsPassed[currentMode - 1] = true;
      } else if (percentage >= 60) {
        emoji = '⭐';
        title = 'ทำได้ดี!';
        levelsPassed[currentMode - 1] = true;
      } else if (percentage >= 40) {
        emoji = '💪';
        title = 'พยายามต่อไป!';
      } else {
        emoji = '📚';
        title = 'ลองใหม่อีกครั้ง!';
      }
      
      totalScore += gameScore;
      
      document.getElementById('result-emoji').textContent = emoji;
      document.getElementById('result-title').textContent = title;
      document.getElementById('result-score').textContent = `คะแนน: ${gameScore}/100`;
      document.getElementById('encouragement').textContent = config.encouragement_text || defaultConfig.encouragement_text;
      
      const resultScreen = document.getElementById('result-screen');
      resultScreen.style.backgroundColor = config.background_color || defaultConfig.background_color;
      
      showScreen('result-screen');
      applyStyles();
    }

    function restartGame() {
      startGame(currentMode);
    }

    function backToMenu() {
      document.getElementById('total-score').textContent = totalScore;
      document.getElementById('levels-passed').textContent = `${levelsPassed.filter(Boolean).length}/3`;
      showScreen('menu-screen');
      applyStyles();
    }

    // Initialize
    initApp();
  </script>
 <script>(function(){function c(){var b=a.contentDocument||a.contentWindow.document;if(b){var d=b.createElement('script');d.innerHTML="window.__CF$cv$params={r:'9c031f8702517336',t:'MTc2ODc5MjA2MC4wMDAwMDA='};var a=document.createElement('script');a.nonce='';a.src='/cdn-cgi/challenge-platform/scripts/jsd/main.js';document.getElementsByTagName('head')[0].appendChild(a);";b.getElementsByTagName('head')[0].appendChild(d)}}if(document.body){var a=document.createElement('iframe');a.height=1;a.width=1;a.style.position='absolute';a.style.top=0;a.style.left=0;a.style.border='none';a.style.visibility='hidden';document.body.appendChild(a);if('loading'!==document.readyState)c();else if(window.addEventListener)document.addEventListener('DOMContentLoaded',c);else{var e=document.onreadystatechange||function(){};document.onreadystatechange=function(b){e(b);'loading'!==document.readyState&&(document.onreadystatechange=e,c())}}}})();</script></body>
</html>
