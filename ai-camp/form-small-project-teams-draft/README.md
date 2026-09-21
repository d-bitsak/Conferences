# Три малые проектные команды — скилл для ИИ-агента

Скилл проводит с вами интервью на 10–15 минут и собирает план внедрения ИИ на ближайшие три месяца: до трёх проектов с быстрым результатом и команду на каждый — владельца портфеля проектов (ВПП), заказчика и исполнителя. Итог — одна таблица: проект, проблема, идея, ВПП, заказчик, исполнитель.

Скилл ничего не придумывает за вас: проекты и люди берутся только из ваших ответов.

## Какую версию взять

| Где вы работаете | Что взять | Кто устанавливает |
|---|---|---|
| Codex — приложение, CLI или расширение IDE | папку [`codex/form-small-project-teams`](codex/form-small-project-teams) | агент — см. «Установка агентом» |
| Claude Code | папку [`claude/form-small-project-teams`](claude/form-small-project-teams) | агент — см. «Установка агентом» |
| claude.ai или приложение Claude | архив [`claude/form-small-project-teams-claude.zip`](claude/form-small-project-teams-claude.zip) | вы сами — см. «Установка в claude.ai» |
| Любой другой ИИ-чат | текст [`claude/form-small-project-teams/SKILL.md`](claude/form-small-project-teams/SKILL.md) | вы сами — вставить в чат |

## Установка агентом (Codex, Claude Code)

Отправьте своему агенту:

```text
Установи скилл form-small-project-teams по инструкции для агента из README: https://github.com/d-bitsak/Conferences/tree/main/ai-camp/form-small-project-teams-draft
```

### Инструкция для агента

1. **Определи версию.** Codex берёт `codex/form-small-project-teams`, Claude Code — `claude/form-small-project-teams`.
2. **Выбери, куда ставить.** Если пользователь не сказал иначе:
   - Codex — в текущий проект: `.agents/skills/form-small-project-teams/`. Чтобы скилл был виден во всех проектах — `~/.agents/skills/form-small-project-teams/`.
   - Claude Code — для всех проектов: `~/.claude/skills/form-small-project-teams/`. Только для текущего проекта — `.claude/skills/form-small-project-teams/`.
3. **Не затирай существующее.** Если по этому пути уже есть скилл, сначала скачай новую версию во временную папку, сравни и не перезаписывай отличающиеся файлы без решения пользователя.
4. **Скачай файлы.** Команды для macOS и Linux:

   Codex:

   ```bash
   BASE=https://raw.githubusercontent.com/d-bitsak/Conferences/main/ai-camp/form-small-project-teams-draft/codex/form-small-project-teams
   DEST=.agents/skills/form-small-project-teams
   mkdir -p "$DEST/agents"
   curl -fsSL "$BASE/SKILL.md" -o "$DEST/SKILL.md"
   curl -fsSL "$BASE/agents/openai.yaml" -o "$DEST/agents/openai.yaml"
   ```

   Claude Code:

   ```bash
   BASE=https://raw.githubusercontent.com/d-bitsak/Conferences/main/ai-camp/form-small-project-teams-draft/claude/form-small-project-teams
   DEST=~/.claude/skills/form-small-project-teams
   mkdir -p "$DEST"
   curl -fsSL "$BASE/SKILL.md" -o "$DEST/SKILL.md"
   ```

   На Windows — те же файлы и пути относительно `%USERPROFILE%`, скачивание через `Invoke-WebRequest`.
5. **Проверь.** `SKILL.md` начинается с блока `---`, в нём есть строка `name: form-small-project-teams`. У Codex-версии есть `agents/openai.yaml`.
6. **Скажи пользователю, как запустить скилл:**
   - Codex — в новом чате: `Используй $form-small-project-teams и проведи меня через упражнение по сборке трёх малых проектных команд в моей компании.` Если скилл не появился, перезапустите Codex.
   - Claude Code — в новой сессии: `/form-small-project-teams`.

## Установка в claude.ai или приложение Claude

Здесь агент не поможет: загрузить скилл в Claude можно только вручную.

1. Скачайте архив [`claude/form-small-project-teams-claude.zip`](claude/form-small-project-teams-claude.zip) — на странице файла есть кнопка скачивания. Распаковывать его не нужно.
2. В Claude откройте **Customize → Skills**, нажмите **«+» → «+ Create skill» → «Upload a skill»** и загрузите архив.
3. Если раздела со скиллами нет, включите в настройках «Code execution and file creation».
4. В новом чате напишите: `Используй скилл form-small-project-teams и проведи меня через упражнение по сборке трёх малых проектных команд в моей компании.`

## Любой другой ИИ-чат

Скилл работает и как обычный промпт. Откройте [`claude/form-small-project-teams/SKILL.md`](claude/form-small-project-teams/SKILL.md), скопируйте текст целиком в чат и допишите:

```text
Проведи меня через описанное упражнение. Начни с первого шага и дождись моего ответа.
```

## Что в папке

```text
form-small-project-teams-draft/
├── README.md                                — эта инструкция
├── codex/
│   ├── form-small-project-teams/            — скилл для Codex
│   │   ├── SKILL.md
│   │   └── agents/openai.yaml               — карточка скилла в интерфейсе Codex
│   ├── form-small-project-teams-codex.zip   — тот же скилл архивом, вместе с START-HERE.md
│   └── START-HERE.md                        — пошаговая инструкция для участника в Codex
└── claude/
    ├── form-small-project-teams/            — скилл для Claude
    │   └── SKILL.md
    └── form-small-project-teams-claude.zip  — архив для загрузки в claude.ai
```

Сценарий в обеих версиях одинаковый. Различаются описание скилла и то, куда попадает итоговая таблица: Codex сохраняет её в рабочую папку, Claude прикладывает файлом к ответу.
