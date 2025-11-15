---
up: "[[+ Gestão de Conhecimento]]"
---
# Padrões e Boas Práticas para Gestão de Conhecimento Pessoal

## Introdução

Com o surgimento das **[[03 Propriedades|Propriedades]]** — uma forma adequada de gerenciar metadados — tornou-se essencial estabelecer padrões e boas práticas para diferentes tipos de notas. Embora alguns possam chamar isso de "ontologias", utilizaremos o termo **"padrões"** para manter a simplicidade.

> **Importante:** Estes padrões não são regras rígidas. São diretrizes curadas que combinam práticas validadas pelo uso intensivo e experimentos em andamento.

---

## Terminologia Essencial

### Coleções

**Coleções** são notas especiais que contêm buscas salvas (queries) automaticamente atualizadas — alguns as chamam de "dashboards dinâmicos" ou "buscas automágicas".

**Exemplos comuns de coleções:**

- Mapas de Conteúdo (MOCs)
- Livros, Filmes e Séries
- Conceitos, Pessoas e Entidades
- Declarações, Perguntas e Citações
- Reuniões e Projetos
- Esforços e Iniciativas

### Visualizações

**Visualizações** são notas com buscas salvas que abrangem múltiplos tipos de notas do seu cofre, diferentemente das coleções que focam em um tipo específico.

---

## Boas Práticas Fundamentais

### 1. Nomenclatura de Propriedades: O Padrão `collection`

Uma prática emergente e altamente recomendada é prefixar propriedades especializadas com o nome da coleção relacionada.

**Exemplos:**

- `bookGenre`, `bookCategory`, `bookAgent`
- `showGenre`, `showType`, `showGroup`
- `peopleGroup`, `peopleRole`, `peopleRelation`

**Vantagens desta abordagem:**

1. **Auto-complete limpo:** Ao digitar "show", você verá apenas sugestões relevantes como "showGenre" ou "showGroup", sem poluição de propriedades não relacionadas.
    
2. **Descoberta intuitiva:** Não é necessário memorizar todas as propriedades. Basta começar a digitar o nome da coleção para ver todas as opções disponíveis.
    
3. **Organização escalável:** À medida que seu sistema cresce, essa convenção mantém tudo organizado e fácil de navegar.
    

### 2. Singular vs Plural

- **Tags:** A recomendação LYT é manter tudo no singular para consistência.
- **Propriedades:** Ainda não há consenso estabelecido. Escolha um padrão e mantenha-o consistente em todo o seu sistema.

### 3. Princípio do Minimalismo

> **Menos é mais** — comece simples e expanda apenas quando houver uma necessidade real.

Nem toda coleção precisa de todos os tipos de classificação. Use templates para automatizar metadados e criar dashboards dinâmicos rapidamente, mas evite complexidade desnecessária.

---

## Sistema de Classificação Hierárquica

### Visão Geral dos Níveis

A hierarquia funciona do mais abstrato ao mais pessoal:

```
Type (mais abstrato/oficial)
  ↓
Category/Genre (classificações reconhecidas)
  ↓
Group (mais pessoal/customizado)
```

### Detalhamento dos Níveis

#### `Type` — Nível Mais Abstrato

Diferencia categorias no nível mais alto e fundamental.

**Exemplos:**

- `bookType`: "ficção", "não-ficção"
- `showType`: "filme", "série", "documentário", "peça"
- `noteType`: "permanente", "literatura", "projeto"

#### `Category` — Classificações Oficiais

Classificações amplamente reconhecidas e padronizadas, mas não necessariamente específicas de um domínio artístico.

**Exemplos:**

- `bookCategory`: "biografia", "ensaio", "romance"
- `projectCategory`: "profissional", "pessoal", "acadêmico"

#### `Genre` — Classificações nas Artes

Classificações consensuais específicas para obras artísticas e culturais.

**Exemplos:**

- `showGenre`: "Ação", "Aventura", "Drama", "Comédia"
- `bookGenre`: "Ficção Científica", "Fantasia", "Terror"
- **Nota:** O Senhor dos Anéis teria `showGenre`: "Ação, Aventura, Drama"

#### `Group` — Agrupamentos Pessoais

Agrupamentos customizados que você mesmo cria para organizar conteúdo de forma pessoal.

**Exemplos:**

- `showGroup`: "Sci-Fi Favoritos", "Adaptações Literárias", "Clássicos da Família"
- `bookGroup`: "Lidos em 2024", "Recomendações", "Releituras Pendentes"

**Vantagem:** Permite criar visualizações dinâmicas customizadas, como "todos os filmes Sci-Fi" ou "livros para ler nas férias".

### Resumo Mental

Uma forma simples de lembrar:

> "`type` no topo, `group` na base. Preciso de algo no meio? Então escolho `category` ou `genre` conforme faz mais sentido."

---

## Termos Alternativos

### `Kind` (Tipo/Espécie)

Muito similar a `type`, pode gerar confusão se usado junto. É mais útil para diferenciar **tipos de notas** no sistema:

- Livro
- Esforço/Projeto
- Ideia/Conceito
- Reunião
- Filme/Série
- Pessoa/Entidade

**Recomendação:** Use `kind` OU `type`, mas não ambos no mesmo contexto.

### `Class` (Classe)

Também próximo de `type`, raramente usado em propriedades do dia a dia. Pode ser útil em contextos mais técnicos ou avançados, especialmente em sistemas com hierarquias complexas.

---

## Implementação Prática

### Começando Simples

1. **Identifique suas coleções principais** (ex: Livros, Projetos, Reuniões)
2. **Defina apenas o essencial:**
    - Um `type` se houver divisões claras
    - Um `group` para agrupamentos pessoais
3. **Crie templates básicos** para automatizar propriedades
4. **Expanda gradualmente** conforme surgem necessidades reais

### Exemplo: Coleção de Livros

**Estrutura mínima:**

```yaml
bookType: ficção
bookGroup: favoritos-2024
```

**Estrutura expandida (quando necessário):**

```yaml
bookType: ficção
bookGenre: Ficção Científica
bookCategory: romance
bookGroup: favoritos-2024, releituras
bookAuthor: [[Isaac Asimov]]
bookYear: 1951
bookRating: 5
```

---

 Seguir para ➡️ [[07 Sugestões de Classificações]]