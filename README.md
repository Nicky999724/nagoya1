<!DOCTYPE html>
<html lang="zh-TW">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>名古屋 8 天 7 夜自由行手帳 & 美食指南</title>
    <!-- Tailwind CSS CDN -->
    <script src="https://cdn.tailwindcss.com"></script>
    <!-- FontAwesome Icons -->
    <link rel="stylesheet" href="https://cdnjs.cloudflare.com/ajax/libs/font-awesome/6.4.0/css/all.min.css">
    <!-- Google Fonts -->
    <link href="https://fonts.googleapis.com/css2?family=Noto+Sans+TC:wght@300;400;500;700&display=swap" rel="stylesheet">
    <style>
        body {
            font-family: 'Noto Sans TC', -apple-system, BlinkMacSystemFont, sans-serif;
            background-color: #f7f9fc;
        }
        .hide-scrollbar::-webkit-scrollbar {
            display: none;
        }
        .hide-scrollbar {
            -ms-overflow-style: none;
            scrollbar-width: none;
        }
        .glass-card {
            background: rgba(255, 255, 255, 0.95);
            backdrop-filter: blur(10px);
            border: 1px solid rgba(226, 232, 240, 0.8);
        }
    </style>
</head>
<body class="text-slate-800 pb-20">

    <!-- Header Navigation -->
    <header class="sticky top-0 z-40 bg-white/90 backdrop-blur-md border-b border-slate-200 shadow-sm">
        <div class="max-w-4xl mx-auto px-4 py-3 flex items-center justify-between">
            <div class="flex items-center space-x-2">
                <span class="w-8 h-8 rounded-full bg-red-500 text-white flex items-center justify-center font-bold text-lg shadow-sm">名</span>
                <div>
                    <h1 class="font-bold text-lg leading-tight text-slate-800">名古屋自由行手帳</h1>
                    <p class="text-xs text-slate-500">2026/11/21 (六) - 11/28 (六)</p>
                </div>
            </div>
            <div class="flex items-center space-x-2">
                <button onclick="resetData()" title="重置預設資料" class="p-2 text-slate-400 hover:text-red-500 transition-colors text-sm rounded-lg hover:bg-slate-100">
                    <i class="fa-solid font-bold fa-rotate-left"></i>
                </button>
                <button onclick="openAddModal()" class="bg-red-500 hover:bg-red-600 text-white px-3 py-1.5 rounded-full text-xs font-medium shadow-md shadow-red-200 flex items-center space-x-1 transition-all active:scale-95">
                    <i class="fa-solid fa-plus text-xs"></i>
                    <span>新增項目</span>
                </button>
            </div>
        </div>

        <!-- Tab Bar -->
        <div class="max-w-4xl mx-auto px-4 flex border-t border-slate-100">
            <button id="tab-itinerary" onclick="switchTab('itinerary')" class="flex-1 py-3 text-center font-medium text-sm border-b-2 border-red-500 text-red-600 flex items-center justify-center space-x-2 transition-all">
                <i class="fa-regular fa-calendar-check"></i>
                <span>每日行程</span>
            </button>
            <button id="tab-food" onclick="switchTab('food')" class="flex-1 py-3 text-center font-medium text-sm border-b-2 border-transparent text-slate-500 hover:text-slate-800 flex items-center justify-center space-x-2 transition-all">
                <i class="fa-solid fa-utensils"></i>
                <span>美食與咖啡廳</span>
            </button>
        </div>
    </header>

    <main class="max-w-4xl mx-auto px-4 pt-4">

        <!-- ================= ITINERARY VIEW ================= -->
        <section id="view-itinerary" class="block">
            <!-- Day Selector Horizontal Scroll -->
            <div class="flex space-x-2 overflow-x-auto pb-3 pt-1 hide-scrollbar">
                <button onclick="selectDay(1)" id="day-btn-1" class="day-btn px-4 py-2 rounded-2xl flex-shrink-0 text-left bg-red-500 text-white shadow-md transition-all">
                    <div class="text-[10px] opacity-80 uppercase tracking-wider">Day 1</div>
                    <div class="font-bold text-sm">11/21 (六)</div>
                </button>
                <button onclick="selectDay(2)" id="day-btn-2" class="day-btn px-4 py-2 rounded-2xl flex-shrink-0 text-left bg-white text-slate-600 border border-slate-200 hover:bg-slate-50 transition-all">
                    <div class="text-[10px] opacity-60 uppercase tracking-wider">Day 2</div>
                    <div class="font-bold text-sm">11/22 (日)</div>
                </button>
                <button onclick="selectDay(3)" id="day-btn-3" class="day-btn px-4 py-2 rounded-2xl flex-shrink-0 text-left bg-white text-slate-600 border border-slate-200 hover:bg-slate-50 transition-all">
                    <div class="text-[10px] opacity-60 uppercase tracking-wider">Day 3</div>
                    <div class="font-bold text-sm">11/23 (一)</div>
                </button>
                <button onclick="selectDay(4)" id="day-btn-4" class="day-btn px-4 py-2 rounded-2xl flex-shrink-0 text-left bg-white text-slate-600 border border-slate-200 hover:bg-slate-50 transition-all">
                    <div class="text-[10px] opacity-60 uppercase tracking-wider">Day 4</div>
                    <div class="font-bold text-sm">11/24 (二)</div>
                </button>
                <button onclick="selectDay(5)" id="day-btn-5" class="day-btn px-4 py-2 rounded-2xl flex-shrink-0 text-left bg-white text-slate-600 border border-slate-200 hover:bg-slate-50 transition-all">
                    <div class="text-[10px] opacity-60 uppercase tracking-wider">Day 5</div>
                    <div class="font-bold text-sm">11/25 (三)</div>
                </button>
                <button onclick="selectDay(6)" id="day-btn-6" class="day-btn px-4 py-2 rounded-2xl flex-shrink-0 text-left bg-white text-slate-600 border border-slate-200 hover:bg-slate-50 transition-all">
                    <div class="text-[10px] opacity-60 uppercase tracking-wider">Day 6</div>
                    <div class="font-bold text-sm">11/26 (四)</div>
                </button>
                <button onclick="selectDay(7)" id="day-btn-7" class="day-btn px-4 py-2 rounded-2xl flex-shrink-0 text-left bg-white text-slate-600 border border-slate-200 hover:bg-slate-50 transition-all">
                    <div class="text-[10px] opacity-60 uppercase tracking-wider">Day 7</div>
                    <div class="font-bold text-sm">11/27 (五)</div>
                </button>
                <button onclick="selectDay(8)" id="day-btn-8" class="day-btn px-4 py-2 rounded-2xl flex-shrink-0 text-left bg-white text-slate-600 border border-slate-200 hover:bg-slate-50 transition-all">
                    <div class="text-[10px] opacity-60 uppercase tracking-wider">Day 8</div>
                    <div class="font-bold text-sm">11/28 (六)</div>
                </button>
            </div>

            <!-- Hotel Banner Card -->
            <div id="hotel-info-card" class="bg-gradient-to-r from-amber-500 to-orange-500 text-white rounded-2xl p-4 my-3 shadow-md flex justify-between items-center">
                <div class="flex items-center space-x-3">
                    <div class="w-10 h-10 rounded-full bg-white/20 flex items-center justify-center text-lg">
                        <i class="fa-solid fa-hotel"></i>
                    </div>
                    <div>
                        <div class="text-xs text-amber-100 font-medium">當日住宿 HOTEL</div>
                        <div id="current-hotel-name" class="font-bold text-base">Apartment Hotel 11 Nagoya Sakae</div>
                    </div>
                </div>
                <a id="current-hotel-map" href="https://maps.google.com/?q=Apartment Hotel 11 Nagoya Sakae" target="_blank" class="bg-white/20 hover:bg-white/30 text-white px-3 py-1.5 rounded-full text-xs font-semibold backdrop-blur-sm transition-all flex items-center space-x-1">
                    <i class="fa-solid fa-map-location-dot"></i>
                    <span>地圖</span>
                </a>
            </div>

            <!-- Schedule Items Container -->
            <div id="itinerary-list" class="space-y-3 mt-4">
                <!-- Dynamically Inserted -->
            </div>
        </section>

        <!-- ================= FOOD & CAFES VIEW ================= -->
        <section id="view-food" class="hidden">
            <!-- Search & Filter Controls -->
            <div class="flex flex-col sm:flex-row gap-3 mb-4">
                <div class="relative flex-1">
                    <i class="fa-solid fa-magnifying-glass absolute left-3.5 top-3 text-slate-400 text-sm"></i>
                    <input type="text" id="food-search" oninput="filterFoodList()" placeholder="搜尋店名、地點或種類..." class="w-full pl-10 pr-4 py-2 rounded-xl border border-slate-200 text-sm focus:outline-none focus:ring-2 focus:ring-red-400 bg-white">
                </div>
                <div class="flex space-x-2">
                    <button onclick="setFoodCategory('ALL')" id="food-cat-ALL" class="food-cat-btn px-4 py-2 rounded-xl text-xs font-semibold bg-red-500 text-white shadow-sm">全部</button>
                    <button onclick="setFoodCategory('朝食')" id="food-cat-朝食" class="food-cat-btn px-4 py-2 rounded-xl text-xs font-semibold bg-white text-slate-600 border border-slate-200 hover:bg-slate-50">早午餐/咖啡</button>
                    <button onclick="setFoodCategory('FOOD')" id="food-cat-FOOD" class="food-cat-btn px-4 py-2 rounded-xl text-xs font-semibold bg-white text-slate-600 border border-slate-200 hover:bg-slate-50">精選正餐</button>
                </div>
            </div>

            <!-- Food Directory Grid -->
            <div id="food-grid" class="grid grid-cols-1 sm:grid-cols-2 gap-4">
                <!-- Dynamically Inserted -->
            </div>
        </section>

    </main>

    <!-- Floating Action Button for Adding New Item -->
    <button onclick="openAddModal()" class="fixed right-5 bottom-5 w-14 h-14 bg-red-500 hover:bg-red-600 text-white rounded-full shadow-lg flex items-center justify-center text-xl transition-all active:scale-95 z-30">
        <i class="fa-solid fa-plus"></i>
    </button>

    <!-- Add/Edit Modal -->
    <div id="item-modal" class="fixed inset-0 bg-slate-900/50 backdrop-blur-sm z-50 flex items-center justify-center p-4 hidden">
        <div class="bg-white rounded-2xl max-w-md w-full p-6 shadow-2xl relative max-h-[90vh] overflow-y-auto">
            <button onclick="closeModal()" class="absolute right-4 top-4 text-slate-400 hover:text-slate-600">
                <i class="fa-solid fa-xmark text-lg"></i>
            </button>
            
            <h3 id="modal-title" class="text-lg font-bold text-slate-800 mb-4">新增行程 / 美食店家</h3>

            <form id="item-form" onsubmit="handleFormSubmit(event)" class="space-y-4">
                <input type="hidden" id="edit-id">

                <div>
                    <label class="block text-xs font-semibold text-slate-600 mb-1">類型 Type</label>
                    <select id="item-type" onchange="toggleFormFields()" class="w-full px-3 py-2 rounded-lg border border-slate-200 text-sm focus:ring-2 focus:ring-red-400 focus:outline-none">
                        <option value="itinerary">每日行程 (Itinerary Event)</option>
                        <option value="food">美食餐廳 / 咖啡廳 (Food & Cafe)</option>
                    </select>
                </div>

                <!-- Itinerary Specific Fields -->
                <div id="field-day" class="block">
                    <label class="block text-xs font-semibold text-slate-600 mb-1">指定天數 Day</label>
                    <select id="item-day" class="w-full px-3 py-2 rounded-lg border border-slate-200 text-sm focus:ring-2 focus:ring-red-400 focus:outline-none">
                        <option value="1">Day 1 (11/21 六)</option>
                        <option value="2">Day 2 (11/22 日)</option>
                        <option value="3">Day 3 (11/23 一)</option>
                        <option value="4">Day 4 (11/24 二)</option>
                        <option value="5">Day 5 (11/25 三)</option>
                        <option value="6">Day 6 (11/26 四)</option>
                        <option value="7">Day 7 (11/27 五)</option>
                        <option value="8">Day 8 (11/28 六)</option>
                    </select>
                </div>

                <div id="field-time" class="block">
                    <label class="block text-xs font-semibold text-slate-600 mb-1">時間 (例: 14:30 或 18:00 - 20:00)</label>
                    <input type="text" id="item-time" placeholder="例如: 14:50" class="w-full px-3 py-2 rounded-lg border border-slate-200 text-sm focus:ring-2 focus:ring-red-400 focus:outline-none">
                </div>

                <!-- Food Specific Category -->
                <div id="field-category" class="hidden">
                    <label class="block text-xs font-semibold text-slate-600 mb-1">美食分類 Category</label>
                    <select id="item-category" class="w-full px-3 py-2 rounded-lg border border-slate-200 text-sm focus:ring-2 focus:ring-red-400 focus:outline-none">
                        <option value="朝食">朝食 / 早午餐 / 咖啡廳</option>
                        <option value="FOOD">FOOD / 精選主餐 / 燒肉壽司</option>
                    </select>
                </div>

                <div>
                    <label class="block text-xs font-semibold text-slate-600 mb-1">名稱 / 標題 Name</label>
                    <input type="text" id="item-title" required placeholder="例如: あつた蓬萊軒松坂屋店" class="w-full px-3 py-2 rounded-lg border border-slate-200 text-sm focus:ring-2 focus:ring-red-400 focus:outline-none">
                </div>

                <div>
                    <label class="block text-xs font-semibold text-slate-600 mb-1">Google 地圖連結 (Google Maps Link)</label>
                    <input type="url" id="item-map" placeholder="https://maps.app.goo.gl/..." class="w-full px-3 py-2 rounded-lg border border-slate-200 text-sm focus:ring-2 focus:ring-red-400 focus:outline-none">
                </div>

                <div>
                    <label class="block text-xs font-semibold text-slate-600 mb-1">備註 / 簡介 / 推薦菜單 Notes</label>
                    <textarea id="item-notes" rows="2" placeholder="填寫推薦菜色、注意事項等..." class="w-full px-3 py-2 rounded-lg border border-slate-200 text-sm focus:ring-2 focus:ring-red-400 focus:outline-none"></textarea>
                </div>

                <div class="pt-3 flex space-x-2">
                    <button type="button" onclick="closeModal()" class="w-1/2 py-2.5 rounded-xl border border-slate-200 text-slate-600 font-medium text-sm hover:bg-slate-50 transition-all">取消</button>
                    <button type="submit" class="w-1/2 py-2.5 rounded-xl bg-red-500 text-white font-medium text-sm hover:bg-red-600 shadow-md shadow-red-200 transition-all">儲存項目</button>
                </div>
            </form>
        </div>
    </div>

    <!-- Application Script Logic -->
    <script>
        // Initial Default Itinerary & Food Data extracted directly from user sheet
        const DEFAULT_HOTELS = {
            1: { name: "Apartment Hotel 11 Nagoya Sakae", map: "https://maps.google.com/?q=Apartment+Hotel+11+Nagoya+Sakae" },
            2: { name: "Apartment Hotel 11 Nagoya Sakae", map: "https://maps.google.com/?q=Apartment+Hotel+11+Nagoya+Sakae" },
            3: { name: "Apartment Hotel 11 Nagoya Sakae", map: "https://maps.google.com/?q=Apartment+Hotel+11+Nagoya+Sakae" },
            4: { name: "Vessel Hotel Campana Nagoya", map: "https://maps.google.com/?q=Vessel+Hotel+Campana+Nagoya" },
            5: { name: "Vessel Hotel Campana Nagoya", map: "https://maps.google.com/?q=Vessel+Hotel+Campana+Nagoya" },
            6: { name: "Vessel Hotel Campana Nagoya", map: "https://maps.google.com/?q=Vessel+Hotel+Campana+Nagoya" },
            7: { name: "Vessel Hotel Campana Nagoya", map: "https://maps.google.com/?q=Vessel+Hotel+Campana+Nagoya" },
            8: { name: "Vessel Hotel Campana Nagoya (寄放行李)", map: "https://maps.google.com/?q=Vessel+Hotel+Campana+Nagoya" }
        };

        const DEFAULT_ITINERARY = [
            // Day 1
            { id: 'it-1', day: 1, time: '14:50', title: '小港機場起飛 ✈️', note: '搭機前往名古屋中部國際機場', map: '' },
            { id: 'it-2', day: 1, time: '18:50', title: '抵達名古屋中部國際機場 (NGO)', note: '辦理入境手續、提取行李', map: '' },
            { id: 'it-3', day: 1, time: '19:30', title: 'μ-SKY 列車 → 名古屋車站', note: '轉乘名鐵地下鐵前往榮站住宿', map: '' },
            { id: 'it-4', day: 1, time: '21:00', title: 'patisserie an 甜點巡禮', note: '夜晚精緻法式甜點品嚐', map: 'https://maps.google.com/?q=patisserie+an+Nagoya' },
            // Day 2
            { id: 'it-5', day: 2, time: '11:00', title: 'PARCO 百貨購物逛街', note: '潮流服飾、動漫與設計雜貨', map: 'https://maps.google.com/?q=Nagoya+PARCO' },
            { id: 'it-6', day: 2, time: '14:30', title: 'Alpen Nagoya & SKYLE | スカイ Uniqlo', note: '旗艦大型戶外運動用品與平價服飾', map: 'https://maps.google.com/?q=Skyle+Nagoya' },
            { id: 'it-7', day: 2, time: '17:00', title: '壽物 (Kotobukimono)', note: '榮商圈周邊散策逛街', map: '' },
            { id: 'it-8', day: 2, time: '18:30', title: '名駅燒肉 伏見屋 飛驒牛 別館 🥩', note: '晚餐重點：極上頂級飛驒牛燒肉享用', map: 'https://maps.google.com/?q=名駅焼肉+伏見屋+飛騨牛+別館' },
            // Day 3
            { id: 'it-9', day: 3, time: '10:00', title: 'mont-bell | 中日大樓 (Chunichi Building)', note: '戶外裝備挑選與中日大樓新地標散步', map: 'https://maps.google.com/?q=中日ビル' },
            { id: 'it-10', day: 3, time: '12:00', title: 'HAERA 韓國服飾/選品店', note: '午間流行選品店逛街', map: '' },
            { id: 'it-11', day: 3, time: '14:30', title: 'LOFT 榮店購物', note: '文具、生活雜貨、美妝大買特買', map: 'https://maps.google.com/?q=Loft+Sakae' },
            { id: 'it-12', day: 3, time: '16:00', title: 'LACHIC 百貨散策', note: '美食與精緻設計品牌', map: 'https://maps.google.com/?q=LACHIC+Nagoya' },
            { id: 'it-13', day: 3, time: '18:00', title: 'あつた蓬萊軒 松坂屋店 🍱', note: '名古屋必吃百年鰻魚飯三吃 (Hitsumabushi)', map: 'https://maps.google.com/?q=あつた蓬莱軒+松坂屋店' },
            { id: 'it-14', day: 3, time: '20:30', title: '中部電力未來塔 (中部電力 MIRAI TOWER)', note: '久屋大通公園欣賞經典綠洲塔夜景', map: 'https://maps.google.com/?q=中部電力+MIRAI+TOWER' },
            // Day 4
            { id: 'it-15', day: 4, time: '09:30', title: '飯店退房 & 寄放行李至 Vessel Hotel', note: '移防名古屋車站附近住宿', map: 'https://maps.google.com/?q=Vessel+Hotel+Campana+Nagoya' },
            { id: 'it-16', day: 4, time: '10:30', title: '熱田神宮 參拜', note: '三大神宮之一，感受三神器「草薙劍」氣場與千年巨木', map: 'https://maps.google.com/?q=熱田神宮' },
            { id: 'it-17', day: 4, time: '13:00', title: '白鳥庭園 漫步', note: '池泉回遊式日本庭園，享受平靜日式景致', map: 'https://maps.google.com/?q=白鳥庭園' },
            { id: 'it-18', day: 4, time: '15:30', title: '大須商店街 & 大須觀音寺 巡禮', note: '傳統小吃、古著店與觀音寺參拜', map: 'https://maps.google.com/?q=大須観音' },
            // Day 5
            { id: 'it-19', day: 5, time: '09:00', title: '搭乘地下鐵東山線 (黃線)', note: '前往藤丘/愛知地球博記念公園方向', map: '' },
            { id: 'it-20', day: 5, time: '10:00', title: '東山動植物園 / 藤が丘 散策', note: '朝氣園區巡禮', map: 'https://maps.google.com/?q=東山動植物園' },
            { id: 'it-21', day: 5, time: '13:00', title: '吉卜力公園 (Ghibli Park) 🌳', note: '預約進入吉卜力大倉庫與童話主題園區', map: 'https://maps.google.com/?q=Ghibli+Park' },
            // Day 6
            { id: 'it-22', day: 6, time: '10:00', title: '犬山城 (國寶犬山城) & 城下町巡禮 🏯', note: '登上現存最古老木造天守閣，逛犬山城下町傳統美食', map: 'https://maps.google.com/?q=犬山城' },
            // Day 7
            { id: 'it-23', day: 7, time: '10:00', title: '常滑招財貓故鄉 (常滑燒散步道) / 市區採買', note: '走訪巨型招財貓「Tokonyan」與陶瓷小徑', map: 'https://maps.google.com/?q=Tokoname' },
            { id: 'it-24', day: 7, time: '14:00', title: '名城公園 & 名古屋城 散策', note: '欣賞金鯱標誌與本丸御殿', map: 'https://maps.google.com/?q=名古屋城' },
            { id: 'it-25', day: 7, time: '16:30', title: 'Yamaha Music 名古屋旗艦店', note: '音樂愛好者體驗館', map: 'https://maps.google.com/?q=Yamaha+Music+Nagoya' },
            // Day 8
            { id: 'it-26', day: 8, time: '11:00', title: '常滑陶藝散策 / 中部國際機場 Flight Park', note: '最後伴手禮採買', map: '' },
            { id: 'it-27', day: 8, time: '19:40', title: '名古屋中部國際機場 起飛 ✈️', note: '準備搭機返回臺灣', map: '' },
            { id: 'it-28', day: 8, time: '22:35', title: '抵達高雄小港機場 順利回家 🏠', note: '結束豐富的 8 天名古屋之旅！', map: '' }
        ];

        const DEFAULT_FOOD = [
            // 朝食 / 咖啡廳
            { id: 'fd-1', category: '朝食', title: 'コンパル 大須本店 (Konparu)', note: '經典名古屋喫茶店，必吃炸蝦三明治！', map: 'https://maps.app.goo.gl/4CCHKVeas...' },
            { id: 'fd-2', category: '朝食', title: 'イトウ珈琲喫茶室 (Ito Coffee)', note: '昭和復古風喫茶室，香醇手沖咖啡與厚片吐司', map: 'https://maps.app.goo.gl/FXj87M7r32...' },
            { id: 'fd-3', category: '朝食', title: 'Bon Voyage', note: '溫馨早午餐與質感咖啡小店', map: 'https://maps.app.goo.gl/Aj2KMPWJE...' },
            { id: 'fd-4', category: '朝食', title: '咖啡 River (喫茶 River)', note: '位於名駅周邊的風格喫茶店', map: 'https://maps.app.goo.gl/sSZVkBhgk...' },
            { id: 'fd-5', category: '朝食', title: 'KAKO 柳橋店', note: '名古屋第一家自家烘焙咖啡，絕品四色小倉紅豆吐司', map: 'https://maps.app.goo.gl/s5icWKbCo...' },
            { id: 'fd-6', category: '朝食', title: 'コンパル サンロード (Konparu Sun Road)', note: '名古屋車站地下街方便的朝食首選', map: 'https://maps.app.goo.gl/dJC1TB9wgr...' },
            { id: 'fd-7', category: '朝食', title: 'Bucyo Coffee', note: '超濃郁紅豆泥吐司與自家焙煎黑咖啡', map: 'https://maps.app.goo.gl/kbM5NjOLK...' },

            // FOOD (正餐)
            { id: 'fd-8', category: 'FOOD', title: '鮨乃悠家 新榮町 | Sushinoyouya', note: '精緻無菜單日本料理 / 高級壽司套餐', map: 'https://maps.app.goo.gl/kWbDZvo51...' },
            { id: 'fd-9', category: 'FOOD', title: '迴轉壽司 鐵座 おの寺', note: '高人氣職人迴轉壽司，新鮮海味現點現握', map: 'https://maps.app.goo.gl/wQv125PZv...' },
            { id: 'fd-10', category: 'FOOD', title: '狐狸庵 (Kitsune-an)', note: '道地烏龍麵與日式家常料理', map: 'https://maps.app.goo.gl/xN7juNP1...' },
            { id: 'fd-11', category: 'FOOD', title: '鰻屋 平山', note: '炭火慢烤香氣四溢的道地關東/關西風鰻魚飯', map: 'https://maps.app.goo.gl/7feU7H4Ti5...' },
            { id: 'fd-12', category: 'FOOD', title: '鰻登屋 らむらい', note: '在地人隱藏版外酥內嫩鰻魚料理', map: 'https://maps.app.goo.gl/Pgf7xR9MT...' },
            { id: 'fd-13', category: 'FOOD', title: '矢場味噌豬排 柳丁店 (Yabaton)', note: '名古屋必吃濃厚特製赤味噌炸豬排', map: 'https://maps.app.goo.gl/ddcjKVY9I...' }
        ];

        // Global State Manager
        let currentTab = 'itinerary';
        let currentSelectedDay = 1;
        let currentFoodFilter = 'ALL';

        let itineraryData = [];
        let foodData = [];

        // Initialize App Data
        function initData() {
            const savedItinerary = localStorage.getItem('nagoya_itinerary');
            const savedFood = localStorage.getItem('nagoya_food');

            if (savedItinerary) {
                itineraryData = JSON.parse(savedItinerary);
            } else {
                itineraryData = [...DEFAULT_ITINERARY];
                saveItinerary();
            }

            if (savedFood) {
                foodData = JSON.parse(savedFood);
            } else {
                foodData = [...DEFAULT_FOOD];
                saveFood();
            }
        }

        function saveItinerary() {
            localStorage.setItem('nagoya_itinerary', JSON.stringify(itineraryData));
        }

        function saveFood() {
            localStorage.setItem('nagoya_food', JSON.stringify(foodData));
        }

        function resetData() {
            if (confirm('確定要將所有行程與美食資料重置為預設行程嗎？')) {
                itineraryData = [...DEFAULT_ITINERARY];
                foodData = [...DEFAULT_FOOD];
                saveItinerary();
                saveFood();
                renderApp();
            }
        }

        // Navigation Switcher
        function switchTab(tab) {
            currentTab = tab;
            const itinBtn = document.getElementById('tab-itinerary');
            const foodBtn = document.getElementById('tab-food');

            const itinView = document.getElementById('view-itinerary');
            const foodView = document.getElementById('view-food');

            // Reset Tab styles
            itinBtn.className = "flex-1 py-3 text-center font-medium text-sm border-b-2 border-transparent text-slate-500 hover:text-slate-800 flex items-center justify-center space-x-2 transition-all";
            foodBtn.className = "flex-1 py-3 text-center font-medium text-sm border-b-2 border-transparent text-slate-500 hover:text-slate-800 flex items-center justify-center space-x-2 transition-all";

            itinView.classList.add('hidden');
            foodView.classList.add('hidden');

            if (tab === 'itinerary') {
                itinBtn.className = "flex-1 py-3 text-center font-medium text-sm border-b-2 border-red-500 text-red-600 flex items-center justify-center space-x-2 transition-all";
                itinView.classList.remove('hidden');
                renderItinerary();
            } else if (tab === 'food') {
                foodBtn.className = "flex-1 py-3 text-center font-medium text-sm border-b-2 border-red-500 text-red-600 flex items-center justify-center space-x-2 transition-all";
                foodView.classList.remove('hidden');
                renderFood();
            }
        }

        function openMapQuery(queryName) {
            window.open(`https://maps.google.com/?q=${encodeURIComponent(queryName)}`, '_blank');
        }

        function selectDay(day) {
            currentSelectedDay = day;
            document.querySelectorAll('.day-btn').forEach((btn, idx) => {
                if ((idx + 1) === day) {
                    btn.className = "day-btn px-4 py-2 rounded-2xl flex-shrink-0 text-left bg-red-500 text-white shadow-md transition-all";
                } else {
                    btn.className = "day-btn px-4 py-2 rounded-2xl flex-shrink-0 text-left bg-white text-slate-600 border border-slate-200 hover:bg-slate-50 transition-all";
                }
            });

            // Update Hotel Header
            const hotel = DEFAULT_HOTELS[day] || { name: '自選飯店', map: 'https://maps.google.com' };
            document.getElementById('current-hotel-name').innerText = hotel.name;
            document.getElementById('current-hotel-map').href = hotel.map;

            renderItinerary();
        }

        // Render Itinerary View
        function renderItinerary() {
            const listEl = document.getElementById('itinerary-list');
            const dayItems = itineraryData.filter(item => parseInt(item.day) === currentSelectedDay);

            if (dayItems.length === 0) {
                listEl.innerHTML = `
                    <div class="text-center py-12 bg-white rounded-2xl border border-dashed border-slate-300">
                        <i class="fa-regular fa-calendar-xmark text-4xl text-slate-300 mb-2"></i>
                        <p class="text-slate-500 text-sm">今日尚無安排行程，點選右下角 + 新增行程！</p>
                    </div>
                `;
                return;
            }

            listEl.innerHTML = dayItems.map((item) => `
                <div class="glass-card rounded-2xl p-4 shadow-sm hover:shadow-md transition-all relative flex flex-col sm:flex-row justify-between items-start sm:items-center group">
                    <div class="flex items-start space-x-3.5 w-full sm:w-auto">
                        <div class="bg-red-50 text-red-600 font-bold text-xs px-2.5 py-1.5 rounded-xl border border-red-100 flex-shrink-0 mt-0.5">
                            ${item.time || '全天'}
                        </div>
                        <div>
                            <h4 class="font-bold text-slate-800 text-base leading-snug">${escapeHtml(item.title)}</h4>
                            ${item.note ? `<p class="text-xs text-slate-500 mt-1">${escapeHtml(item.note)}</p>` : ''}
                        </div>
                    </div>
                    
                    <div class="flex items-center space-x-2 mt-3 sm:mt-0 w-full sm:w-auto justify-end border-t sm:border-t-0 pt-2 sm:pt-0 border-slate-100">
                        ${item.map ? `
                            <a href="${escapeHtml(item.map)}" target="_blank" class="bg-emerald-50 text-emerald-600 hover:bg-emerald-100 px-3 py-1.5 rounded-xl text-xs font-semibold flex items-center space-x-1 transition-all">
                                <i class="fa-solid fa-location-dot"></i>
                                <span>導航</span>
                            </a>
                        ` : `
                            <a href="https://maps.google.com/?q=${encodeURIComponent(item.title + ' 名古屋')}" target="_blank" class="bg-slate-100 hover:bg-slate-200 text-slate-600 px-3 py-1.5 rounded-xl text-xs font-medium flex items-center space-x-1 transition-all">
                                <i class="fa-solid fa-magnifying-glass-location"></i>
                                <span>搜尋</span>
                            </a>
                        `}
                        <button onclick="editItem('itinerary', '${item.id}')" class="text-slate-400 hover:text-slate-600 p-1.5 text-xs">
                            <i class="fa-solid fa-pen"></i>
                        </button>
                        <button onclick="deleteItem('itinerary', '${item.id}')" class="text-slate-400 hover:text-red-500 p-1.5 text-xs">
                            <i class="fa-solid fa-trash"></i>
                        </button>
                    </div>
                </div>
            `).join('');
        }

        // Render Food Directory View
        function renderFood() {
            const gridEl = document.getElementById('food-grid');
            const searchKeyword = document.getElementById('food-search').value.toLowerCase().trim();

            let filtered = foodData;
            if (currentFoodFilter !== 'ALL') {
                filtered = filtered.filter(f => f.category === currentFoodFilter);
            }
            if (searchKeyword) {
                filtered = filtered.filter(f => 
                    f.title.toLowerCase().includes(searchKeyword) || 
                    (f.note && f.note.toLowerCase().includes(searchKeyword))
                );
            }

            if (filtered.length === 0) {
                gridEl.innerHTML = `
                    <div class="col-span-full text-center py-12 bg-white rounded-2xl border border-dashed border-slate-300">
                        <i class="fa-solid fa-utensils text-4xl text-slate-300 mb-2"></i>
                        <p class="text-slate-500 text-sm">沒有找到符合條件的美食店家</p>
                    </div>
                `;
                return;
            }

            gridEl.innerHTML = filtered.map(item => `
                <div class="glass-card rounded-2xl p-4 shadow-sm hover:shadow-md transition-all flex flex-col justify-between border-l-4 ${item.category === '朝食' ? 'border-l-amber-400' : 'border-l-red-500'}">
                    <div>
                        <div class="flex justify-between items-start mb-1.5">
                            <span class="text-[10px] font-bold px-2 py-0.5 rounded-md ${item.category === '朝食' ? 'bg-amber-100 text-amber-700' : 'bg-red-100 text-red-700'}">
                                ${item.category === '朝食' ? '朝食 / 喫茶店' : 'FOOD / 美食'}
                            </span>
                            <div class="flex space-x-1">
                                <button onclick="editItem('food', '${item.id}')" class="text-slate-400 hover:text-slate-600 p-1 text-xs">
                                    <i class="fa-solid fa-pen"></i>
                                </button>
                                <button onclick="deleteItem('food', '${item.id}')" class="text-slate-400 hover:text-red-500 p-1 text-xs">
                                    <i class="fa-solid fa-trash"></i>
                                </button>
                            </div>
                        </div>
                        <h4 class="font-bold text-slate-800 text-base mb-1">${escapeHtml(item.title)}</h4>
                        ${item.note ? `<p class="text-xs text-slate-500 mb-3">${escapeHtml(item.note)}</p>` : ''}
                    </div>

                    <div class="pt-3 border-t border-slate-100 flex justify-end">
                        <a href="${item.map ? escapeHtml(item.map) : `https://maps.google.com/?q=${encodeURIComponent(item.title)}`}" target="_blank" class="w-full bg-slate-900 hover:bg-slate-800 text-white py-2 px-3 rounded-xl text-xs font-medium flex items-center justify-center space-x-2 transition-all shadow-sm">
                            <i class="fa-solid fa-map-location-dot text-red-400"></i>
                            <span>Google Maps 店家地圖</span>
                        </a>
                    </div>
                </div>
            `).join('');
        }

        function setFoodCategory(cat) {
            currentFoodFilter = cat;
            document.querySelectorAll('.food-cat-btn').forEach(btn => {
                btn.className = "food-cat-btn px-4 py-2 rounded-xl text-xs font-semibold bg-white text-slate-600 border border-slate-200 hover:bg-slate-50";
            });
            document.getElementById(`food-cat-${cat}`).className = "food-cat-btn px-4 py-2 rounded-xl text-xs font-semibold bg-red-500 text-white shadow-sm";
            renderFood();
        }

        function filterFoodList() {
            renderFood();
        }

        // Modal Form Handling (Add/Edit)
        function openAddModal() {
            document.getElementById('modal-title').innerText = "新增行程 / 美食";
            document.getElementById('item-form').reset();
            document.getElementById('edit-id').value = "";
            document.getElementById('item-type').value = currentTab === 'itinerary' ? 'itinerary' : 'food';
            document.getElementById('item-day').value = currentSelectedDay;
            toggleFormFields();
            document.getElementById('item-modal').classList.remove('hidden');
        }

        function closeModal() {
            document.getElementById('item-modal').classList.add('hidden');
        }

        function toggleFormFields() {
            const type = document.getElementById('item-type').value;
            if (type === 'itinerary') {
                document.getElementById('field-day').classList.remove('hidden');
                document.getElementById('field-time').classList.remove('hidden');
                document.getElementById('field-category').classList.add('hidden');
            } else {
                document.getElementById('field-day').classList.add('hidden');
                document.getElementById('field-time').classList.add('hidden');
                document.getElementById('field-category').classList.remove('hidden');
            }
        }

        function editItem(type, id) {
            document.getElementById('modal-title').innerText = "編輯內容";
            document.getElementById('edit-id').value = id;
            document.getElementById('item-type').value = type;
            toggleFormFields();

            if (type === 'itinerary') {
                const item = itineraryData.find(i => i.id === id);
                if (item) {
                    document.getElementById('item-day').value = item.day;
                    document.getElementById('item-time').value = item.time || '';
                    document.getElementById('item-title').value = item.title;
                    document.getElementById('item-map').value = item.map || '';
                    document.getElementById('item-notes').value = item.note || '';
                }
            } else {
                const item = foodData.find(f => f.id === id);
                if (item) {
                    document.getElementById('item-category').value = item.category || 'FOOD';
                    document.getElementById('item-title').value = item.title;
                    document.getElementById('item-map').value = item.map || '';
                    document.getElementById('item-notes').value = item.note || '';
                }
            }
            document.getElementById('item-modal').classList.remove('hidden');
        }

        function deleteItem(type, id) {
            if (confirm('確定要刪除此項目嗎？')) {
                if (type === 'itinerary') {
                    itineraryData = itineraryData.filter(i => i.id !== id);
                    saveItinerary();
                    renderItinerary();
                } else {
                    foodData = foodData.filter(f => f.id !== id);
                    saveFood();
                    renderFood();
                }
            }
        }

        function handleFormSubmit(e) {
            e.preventDefault();
            const editId = document.getElementById('edit-id').value;
            const type = document.getElementById('item-type').value;

            const title = document.getElementById('item-title').value.trim();
            const map = document.getElementById('item-map').value.trim();
            const note = document.getElementById('item-notes').value.trim();

            if (type === 'itinerary') {
                const day = parseInt(document.getElementById('item-day').value);
                const time = document.getElementById('item-time').value.trim();

                if (editId) {
                    // Update existing
                    const idx = itineraryData.findIndex(i => i.id === editId);
                    if (idx !== -1) {
                        itineraryData[idx] = { id: editId, day, time, title, note, map };
                    }
                } else {
                    // Create new
                    const newId = 'it-' + Date.now();
                    itineraryData.push({ id: newId, day, time, title, note, map });
                }
                saveItinerary();
                if (currentTab !== 'itinerary') switchTab('itinerary');
                selectDay(day);
            } else {
                const category = document.getElementById('item-category').value;

                if (editId) {
                    // Update existing
                    const idx = foodData.findIndex(f => f.id === editId);
                    if (idx !== -1) {
                        foodData[idx] = { id: editId, category, title, note, map };
                    }
                } else {
                    // Create new
                    const newId = 'fd-' + Date.now();
                    foodData.push({ id: newId, category, title, note, map });
                }
                saveFood();
                if (currentTab !== 'food') switchTab('food');
                renderFood();
            }

            closeModal();
        }

        function renderApp() {
            renderItinerary();
            renderFood();
        }

        function escapeHtml(str) {
            if (!str) return '';
            return str
                .replace(/&/g, "&amp;")
                .replace(/</g, "&lt;")
                .replace(/>/g, "&gt;")
                .replace(/"/g, "&quot;")
                .replace(/'/g, "&#039;");
        }

        // Window Init Load
        window.onload = function() {
            initData();
            selectDay(1);
        }
    </script>
</body>
</html># nagoya1
