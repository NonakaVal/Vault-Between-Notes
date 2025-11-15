---
up:
  - "[[+ ACE Pack]]"
---
Tanto **Areas** quanto **Projetos** fazem parte do **E (Efforts)** do sistema ACE - a dimensão da **ação** e **importância**.

---
![[How the Areas folder works]]

![[How the Projects folder works]]
### Campos importantes:

- **inicio** - data de início
- **entrega** - prazo final
- **status** - estado atual (In Progress, Finished, waiting, to start)

### Onde ficam:

`Projects & Areas/Projects/`

---

## 🔗 **Relacionamento entre Areas e Projetos**

### Hierarquia:

```
Area (Desenvolvimento Pessoal)
├── Projeto 1 (Curso de Python)
├── Projeto 2 (Ler 12 livros este ano)
└── Projeto 3 (Implementar sistema PKM)
```

### Fluxo:

1. **Areas** definem suas responsabilidades gerais
2. **Projetos** são iniciativas específicas dentro dessas áreas
3. Quando um projeto termina, a área continua existindo

```dataviewjs
// Mostra projetos com prazos e status
dv.pages('"Projects & Areas/Projects"')
  .where(p => p.type && p.type == "project")
```

---

## 💡 **Diferença Chave**

|Aspecto|Areas|Projetos|
|---|---|---|
|**Duração**|Contínua|Temporária|
|**Prazo**|Sem prazo|Com prazo definido|
|**Foco**|Manutenção|Conclusão|
|**Exemplo**|"Saúde"|"Perder 5kg em 3 meses"|
|**Metadata**|`type: area_family`|`type: project`|

---

## 🎨 **Uso Prático**

### Quando criar uma Area:

- ✅ É uma responsabilidade contínua
- ✅ Requer atenção regular
- ✅ Não tem "data de conclusão"

### Quando criar um Projeto:

- ✅ Tem objetivo claro e mensurável
- ✅ Tem prazo definido
- ✅ Pode ser marcado como "concluído"

---

## 🔄 **Templates Disponíveis**

### Area:

`System/Templates/Format/area.md`

- Cria estrutura básica da área
- Botão para criar notas da área
- Tags automáticas

### Projeto:

`System/Templates/Format/project.md`

- Campos de data início/entrega
- Selector de status
- Botão para criar notas do projeto
- Tags automáticas

### Notas vinculadas:

- `area note.md` - notas específicas de uma área
- `project note.md` - notas específicas de um projeto
