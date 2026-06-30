# Аудит промпт-блоков «Другой Вселенной»

Пользовательский интерфейс русской версии полностью русский. Рабочие инструкции, которые напрямую отправляются модели, оставлены на английском.

## Макросы SillyTavern

В промптах и карточках используются только стандартные макросы SillyTavern:

```text
{{char}}
{{user}}
```

Самодельные псевдомакросы с реальными именами пользователя или персонажа в промпты не передаются.

## Генерация стартовой сцены

Функция: `buildUniverseArial()`.

Основные правила:

```text
Use {{char}} for the character.
Use {{user}} for the player.
Never output the player's real display name.
Do not write actions, thoughts, biography, decisions, or dialogue for {{user}}.
End with a playable hook that invites {{user}} to respond.
```

## Механика «Яйцекладка»

Объект: `encounterTypes.oviposition`.

Рабочий промпт объясняет модели, что яйцекладка означает производство и помещение яиц внутрь `{{user}}` как физиологический репродуктивный или ролевой механизм. При выборе этой механики `{{char}}` обязан быть физиологически способен на это. Если исходный персонаж человек или несовместимое существо, адаптация меняет `{{char}}` на подходящий нефурри, преимущественно гуманоидный фэнтезийный, инопланетный, демонический, рептильный, инсектойдный или иной совместимый вид либо вариант тела.

Эта способность должна быть отражена в виде, анатомии, особенностях тела, Privates, сексуальности и логике сценария.

## Адаптация анкеты

Функция: `buildAdaptCharacterArial()`.

Промпт требует строгий JSON:

```json
{
  "description": "the fully filled template above",
  "personality": "the filled Personality section only",
  "scenario": "the filled Scenario section plus essential World context",
  "mes_example": "the filled Speech Examples and Opinions section only"
}
```

Поле `description` заполняется по шаблону:

```text
World
Time Period: (e.g. Middle Age, Winter)
World Details: (e.g. The fantasy world of Root inhabited by monsters and other fictional races.)

Scenario
Overall idea for scenario:

Appearance details of character
Race:
Height:
Age:
Hair:
Eyes:
Body:
Face:
Features:
Privates:
Starting Outfit
Head:
Accessories:
Makeup:
Neck:
Top:
Bottom:
Legs:
Shoes:
Panties: (If necessary)

Origin
Brief backstory of the character:

Residence
Location of the character:

Connections
Connections of the character: (e.g. relatives, servants, etc, if necessary)

Goal (Optional)
Main goals of the character:

Secret (Optional)
Some secrets of the character:

Personality
Archetype: (e.g. Shy Bakadere with a brother complex; Modificator + archetype + addition)
Tags:
Likes:
Dislikes:
Deep-Rooted Fears:
Details:
When Safe:
When Alone:
When Cornered:
With user:
Sexual Orientation: (e.g. strictly state, that your character is straight, and gay relationships disgust them)
Kinks/Preferences:
Sexual Quirks and Habits:

Speech

Speech Examples and Opinions (Replace with relevant examples)
Greeting Example:
Pleas for:
Caught:
A memory about:
A thought about:
char Synonyms: Important: This section lists synonymous phrases to substitute the characters name or pronouns and avoid repetition.
```

## Размер анкеты

Выбор размера передаётся в промпт отдельным блоком `DETAIL LEVEL`:

- Краткая: примерно 800-1 200 токенов.
- Стандартная: примерно 1 500-2 500 токенов.
- Подробная: примерно 3 000-5 000 токенов.
- Максимальная: примерно 6 000-8 000 токенов.

## Свой промпт адаптации

Если поле своего промпта заполнено, стандартный промпт заменяется текстом пользователя, но расширение всё равно добавляет блоки с выбранным языком и размером анкеты. Поддерживаются подстановки:

```text
{{char}}
{{user}}
{{story}}
{{description}}
{{personality}}
{{scenario}}
{{mes_example}}
{{adapt_size}}
{{adapt_language}}
```

Чтобы расширение смогло применить результат, свой промпт должен требовать валидный JSON с ключами `description`, `personality`, `scenario`, `mes_example`.
