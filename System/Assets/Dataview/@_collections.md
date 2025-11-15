---
summary: 🗃️ Contagem e lista de coleções
---
~~~dataviewjs
// Obter coleções
const colecoes = dv.pages('"System/Collections"').sort(p => p.file.ctime, 'desc').slice(0, 33);
const totalColecoes = colecoes.length;

// Calcular estatísticas
let colecoesComNotas = 0;
let totalNotas = 0;
let colecoesComOutlinks = 0;
let totalOutlinks = 0;

for (let p of colecoes) {
    const inlinksCount = p.file.inlinks ? p.file.inlinks.length : 0;
    const outlinksCount = p.file.outlinks ? p.file.outlinks.length : 0;
    
    if (inlinksCount > 0) {
        colecoesComNotas++;
        totalNotas += inlinksCount;
    }
    
    if (outlinksCount > 0) {
        colecoesComOutlinks++;
        totalOutlinks += outlinksCount;
    }
}

// Calcular métricas adicionais
const taxaColecoesComNotas = totalColecoes > 0 ? Math.round((colecoesComNotas / totalColecoes) * 100) : 0;
const mediaNotasPorColecao = colecoesComNotas > 0 ? Math.round(totalNotas / colecoesComNotas) : 0;

// -----------------------------
// 📊 CARTÕES DE RESUMO ESTILIZADOS
// -----------------------------
const summaryDiv = dv.el("div", "");
summaryDiv.style.cssText = `
    background: rgba(0, 0, 0, 0.7);
    border-radius: 8px;
    padding: 12px;
    margin-bottom: 15px;
    border-left: 4px solid #7e57c2;
`;

const statsHTML = `
<div style="display: grid; grid-template-columns: repeat(auto-fit, minmax(150px, 1fr)); gap: 8px; margin-bottom: 12px;">
    <div style="text-align: center; padding: 10px; background: rgba(255,255,255,0.15); border-radius: 6px; border: 1px solid rgba(255,255,255,0.2);">
        <div style="font-size: 0.8em; color: #e0e0e0; margin-bottom: 5px;">📂 Coleções</div>
        <div style="font-weight: bold; font-size: 1.1em; color: #ffffff;">${totalColecoes}</div>
    </div>
    <div style="text-align: center; padding: 10px; background: rgba(255,255,255,0.15); border-radius: 6px; border: 1px solid rgba(255,255,255,0.2);">
        <div style="font-size: 0.8em; color: #e0e0e0; margin-bottom: 5px;">📝 Com Notas</div>
        <div style="font-weight: bold; font-size: 1.1em; color: #4caf50;">${colecoesComNotas}</div>
    </div>
    <div style="text-align: center; padding: 10px; background: rgba(255,255,255,0.15); border-radius: 6px; border: 1px solid rgba(255,255,255,0.2);">
        <div style="font-size: 0.8em; color: #e0e0e0; margin-bottom: 5px;">📑 Total Notas</div>
        <div style="font-weight: bold; font-size: 1.1em; color: #ff9800;">${totalNotas}</div>
    </div>
    <div style="text-align: center; padding: 10px; background: rgba(255,255,255,0.15); border-radius: 6px; border: 1px solid rgba(255,255,255,0.2);">
        <div style="font-size: 0.8em; color: #e0e0e0; margin-bottom: 5px;">🔗 Com Links</div>
        <div style="font-weight: bold; font-size: 1.1em; color: #2196f3;">${colecoesComOutlinks}</div>
    </div>
</div>

<div style="display: flex; justify-content: space-around; align-items: center; flex-wrap: wrap; gap: 6px; background: rgba(255,255,255,0.1); padding: 8px; border-radius: 6px; border: 1px solid rgba(255,255,255,0.15);">
    <div style="text-align: center; min-width: 80px; padding: 6px; background: rgba(0,0,0,0.3); border-radius: 6px; border: 1px solid rgba(255,255,255,0.1);">
        <div style="font-size: 1.2em; margin-bottom: 3px;">📊</div>
        <div style="font-weight: bold; font-size: 0.9em; color: #ffffff; margin-bottom: 2px;">${taxaColecoesComNotas}%</div>
        <div style="font-size: 0.75em; color: #b0b0b0; font-weight: 500;">Taxa Notas</div>
    </div>
    <div style="text-align: center; min-width: 80px; padding: 6px; background: rgba(0,0,0,0.3); border-radius: 6px; border: 1px solid rgba(255,255,255,0.1);">
        <div style="font-size: 1.2em; margin-bottom: 3px;">📈</div>
        <div style="font-weight: bold; font-size: 0.9em; color: #ffffff; margin-bottom: 2px;">${mediaNotasPorColecao}</div>
        <div style="font-size: 0.75em; color: #b0b0b0; font-weight: 500;">Média/Col.</div>
    </div>
    <div style="text-align: center; min-width: 80px; padding: 6px; background: rgba(0,0,0,0.3); border-radius: 6px; border: 1px solid rgba(255,255,255,0.1);">
        <div style="font-size: 1.2em; margin-bottom: 3px;">🔗</div>
        <div style="font-weight: bold; font-size: 0.9em; color: #ffffff; margin-bottom: 2px;">${totalOutlinks}</div>
        <div style="font-size: 0.75em; color: #b0b0b0; font-weight: 500;">Total Links</div>
    </div>
    <div style="text-align: center; min-width: 80px; padding: 6px; background: rgba(0,0,0,0.3); border-radius: 6px; border: 1px solid rgba(255,255,255,0.1);">
        <div style="font-size: 1.2em; margin-bottom: 3px;">📚</div>
        <div style="font-weight: bold; font-size: 0.9em; color: #ffffff; margin-bottom: 2px;">${Math.round(totalNotas / Math.max(totalColecoes, 1))}</div>
        <div style="font-size: 0.75em; color: #b0b0b0; font-weight: 500;">Notas/Col.</div>
    </div>
</div>
`;

summaryDiv.innerHTML = statsHTML;

// -----------------------------
// 📋 TABELA ESTILIZADA
// -----------------------------
const tableData = [];

colecoes.forEach(p => {
    const notasCount = p.file.inlinks ? p.file.inlinks.length : 0;
    const outlinksCount = p.file.outlinks ? p.file.outlinks.length : 0;
    const dataCriacao = p.file.ctime ? p.file.ctime.toFormat("dd/MM/yyyy") : "-";
    const diasDesdeCriacao = p.file.ctime ? Math.floor((DateTime.now() - p.file.ctime) / (1000 * 60 * 60 * 24)) : "-";
    
    // Escolher ícone baseado no número de notas
    let icone = "📁";
    if (notasCount > 10) icone = "📚";
    else if (notasCount > 5) icone = "📖";
    else if (notasCount > 0) icone = "📘";
    
    // Cor baseada na idade da coleção
    let corIdade = "#b0b0b0";
    let bgColor = "rgba(255,255,255,0.05)";
    if (diasDesdeCriacao !== "-") {
        if (diasDesdeCriacao < 7) {
            corIdade = "#4caf50";
            bgColor = "rgba(76, 175, 80, 0.1)";
        } else if (diasDesdeCriacao < 30) {
            corIdade = "#ff9800";
            bgColor = "rgba(255, 152, 0, 0.1)";
        }
    }
    
    // Cor baseada no número de notas
    let corNotas = "#b0b0b0";
    if (notasCount > 10) corNotas = "#4caf50";
    else if (notasCount > 5) corNotas = "#ff9800";
    else if (notasCount > 0) corNotas = "#2196f3";

    tableData.push([
        // Coluna 1: Coleção com link correto
        p.file.link,
        // Coluna 2: Notas
        `<span style="color: ${corNotas}; font-weight: 600;">${notasCount}</span>`,
        // Coluna 3: Links
        `<span style="color: ${outlinksCount > 0 ? '#2196f3' : '#b0b0b0'}; font-weight: 500;">${outlinksCount}</span>`,
        // Coluna 4: Data de criação
        `<span style="color: #e0e0e0;">${dataCriacao}</span>`,
        // Coluna 5: Idade
        `<span style="color: ${corIdade}; background: ${bgColor}; padding: 2px 6px; border-radius: 12px; font-size: 0.8em; font-weight: 500;">${diasDesdeCriacao !== "-" ? diasDesdeCriacao + " dias" : "-"}</span>`
    ]);
});

// Criar tabela estilizada
const table = document.createElement("table");
table.style.cssText = `
    width: 100%;
    border-collapse: collapse;
    background: rgba(0, 0, 0, 0.7);
    border-radius: 6px;
    overflow: hidden;
    margin-top: 10px;
`;

const headers = ["📂 Coleção", "📝 Notas", "🔗 Links", "📅 Criada em", "⏳ Idade"];
const thead = document.createElement("thead");
const trHead = document.createElement("tr");

headers.forEach(h => {
    const th = document.createElement("th");
    th.innerHTML = h;
    th.style.cssText = `
        text-align: left;
        padding: 10px 12px;
        border-bottom: 2px solid rgba(255,255,255,0.2);
        background: rgba(255,255,255,0.1);
        color: #ffffff;
        font-weight: 600;
        font-size: 0.9em;
    `;
    trHead.appendChild(th);
});
thead.appendChild(trHead);
table.appendChild(thead);

const tbody = document.createElement("tbody");

tableData.forEach((row, index) => {
    const tr = document.createElement("tr");
    tr.style.cssText = `border-bottom: 1px solid rgba(255,255,255,0.05);`;
    
    row.forEach((cell, cellIndex) => {
        const td = document.createElement("td");
        td.style.cssText = `
            padding: 8px 12px;
            border-bottom: 1px solid rgba(255,255,255,0.1);
            color: #e0e0e0;
            font-size: 0.85em;
            vertical-align: middle;
        `;
        
        if (cellIndex === 0) {
            // Primeira coluna: usar o link diretamente
            const colecao = colecoes[index];
            const icone = row[1].includes('📚') ? "📚" : 
                         row[1].includes('📖') ? "📖" : 
                         row[1].includes('📘') ? "📘" : "📁";
            
            const linkContainer = document.createElement("div");
            linkContainer.style.cssText = `
                display: flex;
                align-items: center;
                gap: 8px;
            `;
            
            const iconSpan = document.createElement("span");
            iconSpan.textContent = icone;
            iconSpan.style.fontSize = "1.1em";
            
            linkContainer.appendChild(iconSpan);
            linkContainer.appendChild(dv.el("span", colecao.file.link));
            
            td.appendChild(linkContainer);
        } else {
            // Outras colunas: usar HTML
            td.innerHTML = cell;
        }
        
        tr.appendChild(td);
    });
    
    tbody.appendChild(tr);
});

table.appendChild(tbody);

// -----------------------------
// 🎯 LEGENDA ESTILIZADA
// -----------------------------
const legenda = dv.el("div", "");
legenda.style.cssText = `
    margin-top: 15px;
    padding: 10px;
    background: rgba(0, 0, 0, 0.6);
    border-radius: 6px;
    border: 1px solid rgba(255,255,255,0.1);
    font-size: 0.8em;
    color: #b0b0b0;
`;

legenda.innerHTML = `
    <div style="font-weight: bold; color: #ffffff; margin-bottom: 8px; font-size: 0.9em;">🎯 Legenda:</div>
    <div style="display: grid; grid-template-columns: repeat(auto-fit, minmax(200px, 1fr)); gap: 8px;">
        <div style="display: flex; align-items: center; gap: 6px;">
            <span>📚</span>
            <span>Muitas notas (>10)</span>
        </div>
        <div style="display: flex; align-items: center; gap: 6px;">
            <span>📖</span>
            <span>Algumas notas (6-10)</span>
        </div>
        <div style="display: flex; align-items: center; gap: 6px;">
            <span>📘</span>
            <span>Poucas notas (1-5)</span>
        </div>
        <div style="display: flex; align-items: center; gap: 6px;">
            <span>📁</span>
            <span>Sem notas</span>
        </div>
        <div style="display: flex; align-items: center; gap: 6px;">
            <span style="color: #4caf50;">●</span>
            <span>Recente (< 7 dias)</span>
        </div>
        <div style="display: flex; align-items: center; gap: 6px;">
            <span style="color: #ff9800;">●</span>
            <span>Novo (< 30 dias)</span>
        </div>
    </div>
`;

// -----------------------------
// 🚀 RENDERIZAÇÃO
// -----------------------------
// Adicionar resumo primeiro
dv.container.appendChild(summaryDiv);

// Adicionar tabela
dv.container.appendChild(table);

// Adicionar legenda
dv.container.appendChild(legenda);
~~~