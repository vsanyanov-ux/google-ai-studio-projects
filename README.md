# google-ai-studio-projects
Google AI Studio prompts, agents and experiments - versioned configurations

## Структура репозитория

```
google-ai-studio-projects/
├── prompts/          # Текстовые промпты и инструкции
│   ├── system/       # Системные промпты
│   ├── chat/         # Чат-промпты
│   └── freeform/     # Свободные промпты
├── agents/           # Конфигурации агентов
│   └── README.md     # Описание агентов
├── experiments/      # Экспериментальные настройки
│   └── README.md     # Описание экспериментов
├── configs/          # JSON конфигурации
│   └── model-settings.json
└── README.md         # Этот файл
```

## Типы проектов

### 1. Промпты (Prompts)
Текстовые файлы с промптами для разных задач.

**Формат файла:** `{название}-prompt.txt` или `.md`

**Что сохранять:**
- Системный промпт
- Примеры входных данных
- Настройки модели (temperature, top_p, top_k)
- Описание назначения

### 2. Агенты (Agents)
Конфигурации для автоматизированных агентов с function calling.

**Формат файла:** `{название}-agent.json`

**Что сохранять:**
- Системная инструкция
- Список функций и их описания
- Настройки модели
- Примеры использования

### 3. Эксперименты (Experiments)
Настройки для A/B тестирования и сравнения моделей.

## Как использовать

### Сохранение промпта из Google AI Studio

1. Открой свой промпт в AI Studio
2. Скопируй текст промпта
3. Создай файл в папке `prompts/` с расширением `.txt` или `.md`
4. Добавь метаданные в начале файла:
```markdown
---
Название: Генератор технических описаний
Модель: gemini-2.0-flash-exp
Temperature: 0.7
Top P: 0.95
Top K: 40
Дата создания: 2025-12-25
---

Текст промпта...
```

### Сохранение конфигурации агента

1. В AI Studio настрой агента с function calling
2. Экспортируй конфигурацию (если доступно) или вручную создай JSON:
```json
{
  "name": "assistant-name",
  "model": "gemini-2.0-flash-exp",
  "systemInstruction": "Ты помощник...",
  "tools": [
    {
      "functionDeclarations": [
        {
          "name": "get_weather",
          "description": "Получить погоду",
          "parameters": {...}
        }
      ]
    }
  ],
  "generationConfig": {
    "temperature": 0.9,
    "topP": 1,
    "topK": 40
  }
}
```
3. Сохрани в папке `agents/`

### Восстановление промпта

1. Открой нужный файл в репозитории
2. Скопируй содержимое
3. В AI Studio создай новый промпт
4. Вставь текст и настрой параметры из метаданных

## Версионирование

```bash
# Добавить новый промпт
git add prompts/новый-промпт.txt
git commit -m "Add: промпт для генерации кода"
git push

# Обновить существующий
git add prompts/существующий-промпт.txt
git commit -m "Update: улучшен промпт для анализа данных"
git push
```

## Важно

- **НЕ храни API-ключи** в конфигурациях
- Используй `.env` файлы локально (добавь в `.gitignore`)
- Документируй изменения в commit message
- Добавляй примеры использования для сложных промптов

## Полезные ссылки

- [Google AI Studio](https://aistudio.google.com/)
- [Gemini API Documentation](https://ai.google.dev/docs)
- [Best practices для промптов](https://ai.google.dev/docs/prompt_best_practices)
