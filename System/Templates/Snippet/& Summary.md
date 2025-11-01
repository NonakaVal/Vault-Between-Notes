```dataviewjs
//-----------------------------------------------------
// ⚙️ CONFIGURAÇÃO DE INTERVALO

const CONFIG = {
    tag: "#calendar/daily",      // Tag usada para filtrar notas
    sectionHeader: "Logs",       // Cabeçalho da seção alvo
    rangeDays: <% tp.system.prompt("Summary rangeDays config")%>,               // Intervalo em dias (padrão: últimos 30)
    sortOrder: "desc"            // Opções: "asc" | "desc"
};
//-----------------------------------------------------
// 🗓️ INTERVALO DE DATAS
//-----------------------------------------------------
const endDate = moment('<% tp.date.now("YYYY-MM-DD") %>', 'YYYY-MM-DD');
const startDate = moment(endDate).subtract(CONFIG.rangeDays, 'days');


//-----------------------------------------------------
// 📚 CATEGORIAS DE LOGS
//-----------------------------------------------------
const categories = [
  { icon: "🧩", name: "Aprendizado" },
  { icon: "⭐", name: "Algo muito bom" },
  { icon: "😞", name: "Frustração / Erros" },
  { icon: "😤", name: "Estresse / Sobrecarga" },
  { icon: "🤔", name: "Reflexões / Emoções" },
  { icon: "✅", name: "Conquistas / Realizações" },
  { icon: "💡", name: "Insights / Ideias" },
  { icon: "⚠️", name: "Obstáculos" },
  { icon: "🪴", name: "Hábitos / Rotina" },
];

//-----------------------------------------------------
// 📥 COLETA DE DADOS
//-----------------------------------------------------
let totals = Object.fromEntries(categories.map(c => [c.icon, 0]));
let totalLogs = 0;

for (const page of dv.pages("#calendar/daily")) {
  const fileDate = moment(page.file.name, "YYYY-MM-DD");
  if (!fileDate.isBetween(startDate, endDate, null, "[]")) continue;

  const content = await dv.io.load(page.file.path);
  const lines = content.split("\n");
  let insideLogs = false;

  for (let line of lines) {
    line = line.trim();
    if (/^#{1,3}\s*logs/i.test(line)) { insideLogs = true; continue; }
    if (insideLogs && /^#{1,3}\s+\w+/.test(line)) break;
    if (!insideLogs || !line.startsWith("-")) continue;

    for (const cat of categories) {
      if (line.includes(cat.icon)) {
        totals[cat.icon]++;
        totalLogs++;
        break;
      }
    }
  }
}

//-----------------------------------------------------
// 🖌️ RENDERIZAÇÃO HORIZONTAL EM UMA LINHA
//-----------------------------------------------------
let html = `<h5>📊 Logs (${startDate.format("DD/MM")} → ${endDate.format("DD/MM")})</h5>
<div style="display:flex; gap:16px; align-items:center;">`;

for (const cat of categories) {
  html += `<div style="display:flex; flex-direction:column; align-items:center;">
    <span>${cat.icon}</span>
    <span>${totals[cat.icon]}</span>
  </div>`;
}

html += `</div>
<p>🧮 Total de logs: <strong>${totalLogs}</strong></p>`;

dv.paragraph(html);

```
