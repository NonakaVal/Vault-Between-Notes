# :LiFileText: Resumo

Um **sistema integrado de gestão do conhecimento** baseado no Sistema [[+ ACE Pack|ACE]] e no [[+ ARC Framework|ARC Framework]] , projetado para organizar **ideias, tempo e ações** em um fluxo coeso.

## 📁 Estrutura da Vault

![img|490](https://imgur.com/TTkN4ay.png)


- `+/` *(Ponto de captura inicial de toda nota criada.)*
- :LiLibraryBig: `Atlas/` *(Notas de estudos e conceitos).* 
	- `Conceitos/` 
	- `Mapas/` 
- :LiCalendar: `Calendar & Review/`  *(Diário, Planejamento)*
	- `Daily Notes/` 
	- `Monthly Notes`
	- `TaskNotes`
	- `Weekly Notes`
- :LiFolderGit2: `Projects & Areas/` *(Projetos e Áreas)* 
	- :LiFolderSync: `Areas`
	- :LiFolderCheck: `Projects`
- :LiSettings: `System/` *(Notas de controle e Templates)*

## 📕 Conteúdos e Features

#### 🏡 Homepage 

<center>
  <img src="https://imgur.com/iBUkoLF.png" width="550">
</center>


#### [[+ Gestão de Conhecimento| 📚 Notas sobre Gestão de conhecimento.]]

<center>
  <img src="https://imgur.com/5yGqZLP.png" width="490">
</center>


#### `Ctrl + N (Criação de Notas)` - [QuickAdd](https://github.com/chhoumann/quickadd) plugin 

<center>
  <img src="https://imgur.com/f6ezubJ.png.png" width="250">
</center>


#### Editor ✏️ [Editing Toolbar](https://github.com/cumany/obsidian-editing-toolbar)


<center>
  <img src="https://imgur.com/Mck7quO.png" width="500">
</center>


#### ✒️ [[@-templates|Templates Prontos]] 

````tabs
tab: 📜 Format
```dataview
TABLE without id file.link as "Template"
FROM "System/Templates/Format"
SORT file.name asc
LIMIT 9
```


tab: & Snippets
```dataview
TABLE without id file.link as "Template"
FROM "System/Templates/Snippet"
SORT file.name asc
LIMIT 10
```
````



#### 🔍 Notas de buscar [Dataview](https://github.com/blacksmithgu/obsidian-dataview)

```dataview
TABLE without id file.link as Note, summary as "Query "
FROM "System/Assets/Dataview"
SORT file.name desc
```


## 🔌  Lista completa Plugins

| Plugin                                                                                         | Description                                                           |
| ---------------------------------------------------------------------------------------------- | --------------------------------------------------------------------- |
| [Advanced URI](https://github.com/Vinzent03/obsidian-advanced-uri)                             | Vault control via URLs                                                |
| [BRAT](https://github.com/TfTHacker/obsidian42-brat)                                           | Beta plugin management with auto-updates                              |
| [Calendar](https://github.com/liamcain/obsidian-calendar-plugin)                               | Daily note calendar                                                   |
| [Callout Manager](https://github.com/eth-p/obsidian-callout-manager)                           | Callouts without CSS                                                  |
| [Charts View](https://github.com/caronchen/obsidian-chartsview-plugin)                         | Interactive charts                                                    |
| [Commander](https://github.com/phibr0/obsidian-commander)                                      | Custom commands                                                       |
| [Custom Frames](https://github.com/gino-ple-bags/obsidian-custom-frames)                       | Embed web pages                                                       |
| Dashboard Navigator                                                                            | Replaced by [Homepage](https://github.com/mirnovov/obsidian-homepage) |
| [Datacore](https://github.com/blacksmithgu/obsidian-datacore)                                  | Modern data engine                                                    |
| [Dataview](https://github.com/blacksmithgu/obsidian-dataview)                                  | Query notes like a database                                           |
| [Editing Toolbar](https://github.com/cumany/obsidian-editing-toolbar)                          | Floating edit toolbar                                                 |
| [Excalidraw](https://github.com/zsviczian/obsidian-excalidraw-plugin)                          | Drawing & whiteboarding tool                                          |
| [Force note view mode](https://github.com/bwca/obsidian-force-view-mode-of-note)               | Force default view mode                                               |
| [Home tab](https://github.com/oliverschwendener/obsidian-home-tab)                             | Browser-like home tab                                                 |
| [Homepage](https://github.com/mirnovov/obsidian-homepage)                                      | Set startup note                                                      |
| [Hotkeys for specific files](https://github.com/Vinzent03/obsidian-hotkeys-for-specific-files) | Hotkeys to open specific notes                                        |
| [Iconic](https://github.com/aidenlx/obsidian-iconic)                                           | Custom icons for files                                                |
| [JS Engine](https://github.com/Fevol/obsidian-js-engine)                                       | Run JS code in plugins                                                |
| [List Callouts](https://github.com/mgmeyers/obsidian-list-callouts)                            | Turn lists into callouts                                              |
| [Meta Bind](https://github.com/mnaouass/obsidian-meta-bind-plugin)                             | Inputs linked to frontmatter                                          |
| [Outliner](https://github.com/vslinko/obsidian-outliner)                                       | Outliner style and shortcuts                                          |
| [Paste URL into selection](https://github.com/denolehov/obsidian-url-into-selection)           | Turns selected text into a link                                       |
| [Periodic Notes](https://github.com/liamcain/obsidian-periodic-notes)                          | Notes for week/month/year                                             |
| [Projects](https://github.com/marcusolsson/obsidian-projects)                                  | Table, kanban, and calendar for projects                              |
| [QuickAdd](https://github.com/chhoumann/quickadd)                                              | Fast content capture                                                  |
| [Recent Files](https://github.com/tgrosinger/recent-files-obsidian)                            | Recently opened files list                                            |
| [Status Bar Organizer](https://github.com/L7Cy/obsidian-customizable-statusbar)                | Customizable status bar                                               |
| [Style Settings](https://github.com/mgmeyers/obsidian-style-settings)                          | GUI for theme & plugin customization                                  |
| [Tabs](https://github.com/git-yustasse/obsidian-tabs)                                          | Tabbed file navigation                                                |
| [TasksNotes](https://github.com/callumalpass/tasknotes)                                        | Tasks with dates, priorities, and filters                             |

---

![[Créditos-Atribuições]]