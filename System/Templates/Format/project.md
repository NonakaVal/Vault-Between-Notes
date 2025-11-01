---
project: "[[<% tp.file.folder() %>]]"
tags:
type: project
created: '[[<% tp.date.now("YYYY-MM-DD") %>]]'
---

| Data Início                                              | Data Entrega                                              | Status                                                                                                         |
| -------------------------------------------------------- | --------------------------------------------------------- | -------------------------------------------------------------------------------------------------------------- |
| `INPUT[datePicker(showcase, defaultValue(null)):inicio]` | `INPUT[datePicker(showcase, defaultValue(null)):entrega]` | `INPUT[inlineSelect(option('In Progress'), option('Finished'), option('waiting'), option('to start')):status]` |

```meta-bind-button
label: Criar Nota de Projeto
icon: plus
hidden: false
class: ""
id: TEMPLATE-CRIAR-NOVA-NOTA-PROJETO
style: default
actions:
  - type: command
    command: quickadd:choice:e7c0cfff-583f-4da9-a201-79b4d5a12de4
```

---
## 🧾 Descrição do Projeto








---

___
## 🎯 Objetivo

1. 🟢 Resultado ideal do projeto  
	1. 
2. 🟠 Resultado aceitável  
	1. 

## ❓ Expectativas
1. 🟢 O que pode ajudar o projeto  
	1. 
2. 🟠 Obstáculos potenciais  
	1. 
3. 👶 Inexperiências / Suposições  
	1. 
4. 👨‍💻 Insights e aprendizados  
	1. 

## ✅ Tarefas  
- 

## 📦 Recursos  
- 

## 📂 Registros do Projeto  
- 




<%* tp.hooks.on_all_templates_executed(async () => { 
    const file = tp.file.find_tfile(tp.file.path(true)); 
    const task_tag_value = tp.file.folder().toLowerCase().split(" ").join("_");
    await app.fileManager.processFrontMatter(file, (frontmatter) => { 
        frontmatter["tags"] = `project/${task_tag_value}`; 
    }); 
}); -%>