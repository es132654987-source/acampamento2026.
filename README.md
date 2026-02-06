<!DOCTYPE html>
<html lang="pt">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>JA App | 2ª Região Santiago</title>
    <script src="https://cdn.tailwindcss.com"></script>
    <link href="https://fonts.googleapis.com/css2?family=Outfit:wght@300;400;600;800&display=swap" rel="stylesheet">
    <style>
        body { font-family: 'Outfit', sans-serif; background-color: #f1f5f9; }
        .glass { background: rgba(255, 255, 255, 0.95); backdrop-filter: blur(10px); }
        .gradient-header { background: linear-gradient(135deg, #0f172a 0%, #1e3a8a 100%); }
        .tab-active { color: #1e3a8a; border-bottom: 3px solid #eab308; font-weight: 800; }
        .no-scrollbar::-webkit-scrollbar { display: none; }
        .rule-card { border-left: 4px solid #ef4444; background: #fee2e2; padding: 10px; border-radius: 10px; margin-bottom: 8px; font-size: 12px; }
        .check-card { border-left: 4px solid #10b981; background: #d1fae5; padding: 10px; border-radius: 10px; margin-bottom: 8px; font-size: 12px; }
    </style>
</head>
<body class="pb-24">

    <header class="gradient-header text-white pt-10 pb-20 px-6 rounded-b-[45px] shadow-2xl relative text-center">
        <div class="bg-yellow-500 text-blue-900 text-[9px] font-black px-4 py-1 rounded-full uppercase inline-block mb-3 tracking-widest">Santiago - 2ª Região</div>
        <h1 class="text-2xl font-extrabold tracking-tighter leading-none uppercase italic">Acampamento JA 2026</h1>
        
        <div class="glass max-w-xs mx-auto mt-6 p-4 rounded-3xl shadow-xl flex justify-around text-blue-900 font-bold">
            <div id="days">00<br><span class="text-[8px] opacity-60 uppercase">Dias</span></div>
            <div id="hours">00<br><span class="text-[8px] opacity-60 uppercase">Hrs</span></div>
            <div id="mins">00<br><span class="text-[8px] opacity-60 uppercase">Min</span></div>
        </div>
    </header>

    <main class="max-w-md mx-auto -mt-12 px-4 space-y-6">

        <section class="grid grid-cols-2 gap-4">
            <a href="https://www.bibliaonline.com.br" target="_blank" class="glass p-4 rounded-[25px] shadow-lg text-center border-b-4 border-blue-600 active:scale-95 transition">
                <span class="text-2xl block mb-1">📖</span>
                <span class="text-[10px] font-bold text-blue-900 uppercase italic">Bíblia</span>
            </a>
            <a href="https://www.hinarioadventista.com.br/" target="_blank" class="glass p-4 rounded-[25px] shadow-lg text-center border-b-4 border-yellow-500 active:scale-95 transition">
                <span class="text-2xl block mb-1">🎶</span>
                <span class="text-[10px] font-bold text-blue-900 uppercase italic">Hinário</span>
            </a>
        </section>

        <section class="glass rounded-[35px] shadow-xl overflow-hidden bg-white">
            <div class="flex bg-gray-50/50 border-b overflow-x-auto no-scrollbar">
                <button onclick="showTab('info')" id="t-info" class="flex-1 py-4 text-[9px] font-black tab-active min-w-[80px]">GERAL</button>
                <button onclick="showTab('check')" id="t-check" class="flex-1 py-4 text-[9px] font-black text-gray-400 min-w-[80px]">MOCHILA</button>
                <button onclick="showTab('rules')" id="t-rules" class="flex-1 py-4 text-[9px] font-black text-gray-400 min-w-[80px]">REGRAS</button>
                <button onclick="showTab('staff')" id="t-staff" class="flex-1 py-4 text-[9px] font-black text-gray-400 min-w-[80px]">EQUIPA</button>
            </div>

            <div class="p-6 min-h-[300px]">
                <div id="tab-info" class="space-y-4">
                    <h4 class="text-blue-900 font-bold text-xs uppercase underline italic">Programa:</h4>
                    <p id="display-activities" class="text-xs text-gray-600 whitespace-pre-line"></p>
                    <h4 class="text-green-700 font-bold text-xs uppercase underline italic mt-4">Cardápio:</h4>
                    <p id="display-menu" class="text-xs text-gray-600 whitespace-pre-line"></p>
                </div>

                <div id="tab-check" class="hidden space-y-2">
                    <h4 class="text-emerald-700 font-bold text-xs uppercase mb-4 text-center tracking-widest">🎒 Itens Essenciais</h4>
                    <div id="display-items" class="space-y-1">
                        </div>
                </div>

                <div id="tab-rules" class="hidden space-y-2">
                    <h4 class="text-red-700 font-bold text-xs uppercase mb-4 text-center tracking-widest">🚫 Normas de Conduta</h4>
                    <div id="display-rules" class="space-y-1">
                        </div>
                </div>

                <div id="tab-staff" class="hidden space-y-3">
                    <h4 class="text-blue-900 font-bold text-xs uppercase mb-4 text-center tracking-widest">👥 Responsáveis</h4>
                    <div id="staff-list" class="space-y-2 text-[11px]"></div>
                </div>
            </div>
        </section>

        <button onclick="fazerInscricao()" class="w-full bg-blue-900 text-white py-5 rounded-[30px] shadow-2xl font-bold flex justify-center items-center gap-3 active:scale-95 transition">
            <span>Confirmar Minha Presença</span>
            <img src="https://cdn-icons-png.flaticon.com/512/733/733585.png" class="w-5 h-5 invert">
        </button>

        <div class="pt-6 text-center">
            <button onclick="document.getElementById('admin').classList.toggle('hidden')" class="text-[9px] font-bold text-gray-400 uppercase tracking-[4px]">⚙️ Gestão Administrativa</button>
        </div>

        <div id="admin" class="hidden glass p-6 rounded-[40px] border-2 border-blue-100 mt-4 space-y-4 shadow-2xl">
            <h2 class="text-center font-black text-blue-900 text-sm">EDITAR APP</h2>
            
            <input id="edit-phone" value="2385802977" class="w-full p-3 rounded-2xl bg-gray-100 text-xs font-bold border-none" placeholder="WhatsApp Direção">
            <textarea id="edit-activities" placeholder="Programa..." class="w-full p-3 rounded-2xl bg-gray-100 text-xs border-none" rows="2"></textarea>
            <textarea id="edit-menu" placeholder="Cardápio..." class="w-full p-3 rounded-2xl bg-gray-100 text-xs border-none" rows="2"></textarea>
            <textarea id="edit-items" placeholder="O que levar (um por linha)..." class="w-full p-3 rounded-2xl bg-gray-100 text-xs border-none" rows="3"></textarea>
            <textarea id="edit-rules" placeholder="Regras (uma por linha)..." class="w-full p-3 rounded-2xl bg-gray-100 text-xs border-none" rows="3"></textarea>
            
            <div class="border-t pt-4 space-y-2">
                <input id="staff-diretor" placeholder="Diretor" class="w-full p-2 rounded-xl bg-gray-100 text-[10px]">
                <input id="staff-cozinha" placeholder="Cozinha" class="w-full p-2 rounded-xl bg-gray-100 text-[10px]">
                <input id="staff-emerg" value="132" class="w-full p-2 rounded-xl bg-red-50 text-red-600 text-[10px] font-bold">
            </div>

            <button onclick="saveAll()" class="w-full bg-blue-600 text-white py-4 rounded-2xl font-bold shadow-lg uppercase active:bg-blue-700">Guardar Tudo</button>
        </div>
    </main>

    <script>
        function showTab(t) {
            ['info', 'check', 'rules', 'staff'].forEach(tab => {
                document.getElementById('tab-'+tab).classList.add('hidden');
                document.getElementById('t-'+tab).classList.remove('tab-active');
                document.getElementById('t-'+tab).classList.add('text-gray-400');
            });
            document.getElementById('tab-'+t).classList.remove('hidden');
            document.getElementById('t-'+t).classList.add('tab-active');
        }

        const targetDate = new Date("Feb 15, 2026 08:00:00").getTime();
        setInterval(() => {
            const gap = targetDate - new Date().getTime();
            if(gap > 0) {
                document.getElementById('days').innerHTML = Math.floor(gap / (1000 * 60 * 60 * 24)) + "<br><span class='text-[8px] opacity-60 uppercase'>Dias</span>";
                document.getElementById('hours').innerHTML = Math.floor((gap % (1000 * 60 * 60 * 24)) / (1000 * 60 * 60)) + "<br><span class='text-[8px] opacity-60 uppercase'>Hrs</span>";
                document.getElementById('mins').innerHTML = Math.floor((gap % (1000 * 60 * 60)) / (1000 * 60)) + "<br><span class='text-[8px] opacity-60 uppercase'>Min</span>";
            }
        }, 1000);

        function saveAll() {
            const data = {
                phone: document.getElementById('edit-phone').value,
                activities: document.getElementById('edit-activities').value,
                menu: document.getElementById('edit-menu').value,
                items: document.getElementById('edit-items').value,
                rules: document.getElementById('edit-rules').value,
                staff: {
                    diretor: document.getElementById('staff-diretor').value,
                    cozinha: document.getElementById('staff-cozinha').value,
                    emerg: document.getElementById('staff-emerg').value
                }
            };
            localStorage.setItem('JA_MASTER_V2', JSON.stringify(data));
            location.reload();
        }

        window.onload = function() {
            const saved = JSON.parse(localStorage.getItem('JA_MASTER_V2'));
            if(saved) {
                document.getElementById('display-activities').innerText = saved.activities || "Em breve";
                document.getElementById('display-menu').innerText = saved.menu || "Em breve";
                
                // Checklist
                const itemsDiv = document.getElementById('display-items');
                if(saved.items) saved.items.split('\n').forEach(i => { if(i.trim()) itemsDiv.innerHTML += `<div class="check-card">✅ ${i}</div>`; });
                
                // Regras
                const rulesDiv = document.getElementById('display-rules');
                if(saved.rules) saved.rules.split('\n').forEach(r => { if(r.trim()) rulesDiv.innerHTML += `<div class="rule-card">📢 ${r}</div>`; });

                // Staff
                document.getElementById('staff-list').innerHTML = `
                    <div class="p-3 bg-blue-50 rounded-xl mb-2"><strong>Direção:</strong> ${saved.staff.diretor}</div>
                    <div class="p-3 bg-blue-50 rounded-xl mb-2"><strong>Cozinha:</strong> ${saved.staff.cozinha}</div>
                    <div class="p-3 bg-red-100 text-red-700 rounded-xl font-bold text-center italic">EMERGÊNCIA: ${saved.staff.emerg}</div>
                `;

                // Admin Fill
                document.getElementById('edit-phone').value = saved.phone;
                document.getElementById('edit-activities').value = saved.activities;
                document.getElementById('edit-menu').value = saved.menu;
                document.getElementById('edit-items').value = saved.items;
                document.getElementById('edit-rules').value = saved.rules;
                document.getElementById('staff-diretor').value = saved.staff.diretor;
                document.getElementById('staff-cozinha').value = saved.staff.cozinha;
                document.getElementById('staff-emerg').value = saved.staff.emerg;
            } else {
                // Dados Iniciais Sugeridos
                document.getElementById('edit-items').value = "Bíblia e Lição\nFarda JA\nPrato, Caneca e Talheres\nMaterial de Higiene\nColchão e Cobertor";
                document.getElementById('edit-rules').value = "Respeitar os horários\nNão sair do recinto sem aviso\nUso de vestuário adequado\nTelemóveis apenas em horas livres";
            }
        };

        function fazerInscricao() {
            const fone = document.getElementById('edit-phone').value;
            window.open(`https://wa.me/${fone}?text=Olá! Quero me inscrever no Acampamento JA 2026 de Assomada!`);
        }
    </script>
</body>
</html>
