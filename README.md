<div align="center">

<img src="assets/vector-logo.png" alt="Vector Agent-Ready" width="200"/>

# Vector Agent-Ready

[![Ecosystem: Vector](https://img.shields.io/badge/Ecosystem-Vector-blue.svg)](https://osmosy.github.io/)

**Методология подготовки контента для ИИ-агентов — 7 слоёв, применимых к сайтам, репозиториям и базам знаний**

[![Hermes Agent](https://img.shields.io/badge/Hermes-Agent-blue.svg)](https://github.com/NousResearch/hermes-agent)
[![Layers: 7](https://img.shields.io/badge/Layers-7-green.svg)](#семь-слоёв)
[![Based on: pimenov.ai](https://img.shields.io/badge/Based%20on-pimenov.ai-orange.svg)](https://pimenov.ai/knowledge/agent-ready-sajt-metodologiya-podgotovki-dlya-ii-agentov/)
[![License: MIT](https://img.shields.io/badge/License-MIT-yellow.svg)](LICENSE)

</div>

---

Методология превращает контент из витрины для людей в среду, понятную ИИ-агентам. Не через чат-виджет или кнопку «спросить ИИ», а через архитектуру контента, машиночитаемые слои и редакторский порядок.

## Семь слоёв

### 1. Предсказуемые URL
Агент может строить ссылки без парсинга меню.

- Стабильная иерархия без случайных ID
- URL из slug, не из ID базы данных
- URL не меняется после публикации
- Нет дублирующих путей к одному материалу

```
✅ /knowledge/agent-ready/
✅ /docs/staffing-v1.md
❌ /page/3f7a2b1c-e8c9-4015-82cf
```

### 2. Доступный текст
Агент читает контент без рендеринга JavaScript.

- Весь контент доступен в HTML/Markdown без JS
- Семантический HTML (заголовки, списки, таблицы)
- Изображения имеют alt-тексты
- RSS/Atom-фиды, search index в JSON
- Markdown-представления страниц

### 3. Явные связи
Агент понимает не только страницу, но и её место в системе.

- Внутренние ссылки между материалами
- Блоки «По теме» / «Связанные материалы»
- Теги (о чём) + graph tags (роль в системе)
- Relation-свойства: «Статья → Услуга», «Справочник → Статья»

### 4. Машиночитаемые слои
Агент получает метаинформацию о сайте в удобном формате.

| Файл | Назначение |
|------|-----------|
| `llms.txt` | Индекс сайта для LLM: структура, ключевые страницы |
| `agent-description.md` | Описание проекта для агента: что это, как устроено, как читать |
| `AGENTS.md` | Правила доступа: что можно, что нельзя, approval gates |
| `sitemap.xml` | Карта сайта (стандарт) |
| JSON-LD | Структурированные данные для поисковиков и агентов |

### 5. Контентный граф
Агент видит кластеры, пробелы, маршруты.

- SVG-карта графа связей между страницами
- Semantic snapshot (TF-IDF): какие темы покрыты, какие нет
- Graph Opportunities Console: что добавить
- В экосистеме Vector: `vector-work` — хаб-навык, связывающий все проекты

### 6. Правила доступа
Агент знает, где читать, где предлагать, где создавать.

- `AGENTS.md` — конституция проекта
- Публичный API vs read-only API
- Approval gates: что агент может делать без подтверждения
- Permissions: read → suggest → draft → publish

### 7. Редакторский контроль
Человек сохраняет финальное решение.

- Статусы: черновик → на проверке → опубликовано
- Checkpoint'ы перед публикацией
- Handoff-протоколы: агент → человек → агент
- Агент не публикует без проверки человеком

## Применение в экосистеме Vector

| Слой | Как реализовано в Vector |
|------|------------------------|
| 1. URL | `github.com/Osmosy/vector-*` — стабильные пути |
| 2. Текст | README.md — чистый Markdown, без JS |
| 3. Связи | Перекрёстные ссылки между всеми 8 репозиториями |
| 4. Машиночитаемые | SKILL.md (YAML), `agent-description.md` в каждом репо |
| 5. Граф | `vector-work` — хаб-навык экосистемы |
| 6. Доступ | GitHub public, AGENTS.md |
| 7. Контроль | Git-коммиты с ревью |

## Главное наблюдение

Всё, что делает контент понятным агенту, делает его понятнее и человеку. Agent-ready — это не отдельная оптимизация для машин. Это зрелая архитектура контента. Агенты просто быстро показывают, где в этой архитектуре дыры.

## Источник

Методология на базе статьи [pimenov.ai — Agent-ready сайт](https://pimenov.ai/knowledge/agent-ready-sajt-metodologiya-podgotovki-dlya-ii-agentov/).

## Деплой: GitHub Pages

Бесплатный хостинг статических сайтов из GitHub. Пуш в репозиторий → сайт в интернете за минуту.

**Применение в Vector:**
- `vector-work` → публичный сайт экосистемы (`osmosy.github.io`)
- `vector-marketing` → лендинги клиентов: агент генерит → пуш → сайт живёт
- Документация любого проекта → GitHub Pages = публичный доступ без хостинга

```bash
# Settings → Pages → Source: Deploy from branch → main → /docs
# Сайт будет доступен по адресу:
https://osmosy.github.io/vector-work/
```

См. руководство: [pimenov.ai — GitHub Pages](https://pimenov.ai/knowledge/github-pages-besplatnyj-hosting/)
