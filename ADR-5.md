# ADR - **Выбор фреймворка для разработки клиента**

**Участники:**
- Мухин
- Мухорин
- Пряшников

**Дата:** 28 сент. 2024 г.

**Статус:** Решено

## Контекст

- Команда: 3 балбеса
  - все трое сдали ООП малову на 5
  - один балбес знает все языки программирования и иммет опыт работы со всеми архитектурами
- Бюджет: 3 хотдога в неделю 
- Ресурсы: доступен проектный сервер (уже оплачен на 10 лет), два старых ноутбука, один модный MacBook Pro M1 Max 14" 64G 1Tb
- Сроки: на реализацию MVP имеется 6 месяцев
- Целевая аудитория: компании, отказывающиеся от зарубежных решений по редактированию документов.
- [Серверное решение](ADR-1.md) с возможностью переезда в Serverless в будущем
- [Golang](ADR-2.md)
- Долгосрок поддержка
- [Модульная архитектура бекенда](ADR-3.md)
- Тонкий клиент на основе Web+PWA
- [JS](ADR-4.md)

Надо разработать систему онлайн документов с возможностью совместного доступа и редактирования - [Golang](ADR-2.md), реалтайм, расчётная нагрузка до 2000 RPM и 1000 keepalive sessions, приоритет на сокращении длины пакетов, так как канал [выбранного нами сервера](ADR-1.md) составляет всего 100Мбит (фактически 50-70Mbit при средней загрузке сети регионального оператора). 

Фото минимально доступного нашим клиентам оборудования ниже:


![Клиентское оборудование](Pasted20240928101811.png)

## Рассматриваемые варианты

- **React**
	- Модный
	- Популярный
	- Толстый
	- Активно поддерживается сообществом
	- Тормозит на больших приложениях из-за ShadowDOM
- **Vue**
	- Модный
	- Активно поддерживается сообществом
- **Svelte**+**SvelteKit**
	- Очень модный
	- Активно поддерживается сообществом
	- Минимальный memory footprint и размер бандла
	- Нет ShadowDOM и работает реактивность
	- Compile-time reactivity

## Решение

**Svelte**+**SvelteKit**

## Обоснование

Выбор **Svelte**+**SvelteKit** обусловлен следующими факторами:

1. **Модность:** Модный язык, на нём пишет много программистов. Активно поддерживается сообществом
2. **Компетенции и сроки:** Наша команда объединяет несколько компетентных  разработчиков на **JS**+**Svelte**+**SvelteKit**, что позволит параллелить работу в рамках модулей и уложиться в сроки.
3. **Одобрение архитектора:** Архитектор одобряет
4. **Разработка командой балбесов:** Фреймворк прост в освоении, модели реактивности и интеграции с браузерами - идеально для команды балбесов.
5. **Поддержка:** Легко поддерживать с устоявшимися, battle-tested решениями и опытом команды.

## Последствия

**Мало готовых решений:** на многое нет готовых решений для этого  фреймворка
  - **Решение:** пишем кастомные решения.
### Риски
1. **Популярность решения может упасть при низких объёмах легаси**

## Затронутые области

1. **Клиентский опыт:** клиентам важно время загрузки и Responsiveness приложения.

## История

----
