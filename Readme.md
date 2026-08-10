# [Addiction.fm](http://addiction.fm/) 2.0

[Русский](#русский)

<img width="1918" height="885" alt="image" src="https://github.com/user-attachments/assets/bdf23332-a122-4b1a-aca1-0bf1150165c8" />

**Mobile version:**

<img width="280" height="600" alt="image" src="https://github.com/user-attachments/assets/1dbd40fd-f5db-41bf-8215-38d193d0a10d" /><img width="280" height="600" alt="image" src="https://github.com/user-attachments/assets/b9c78e26-c095-43c0-8128-979a68d58972" />

**Generative radio. One button - sound built for your mental state.**

Addiction.fm is a browser-based generative audio app with no playlists, no accounts, and no ads. Pick a state - get a unique sound that never repeats.

---

## 🔥 What's new in 2.0

The biggest update since launch: the mobile interface was rebuilt from scratch, the drum bank grew five and a half times, and you can now run the radio without ever opening the tab.

### System-wide media controls

The radio is no longer trapped inside a browser tab. It shows up wherever a normal music player does, with its own artwork:

- **Android** - a card in the notification shade and on the lock screen: play/pause, track skipping, and a dedicated "another break" button.
- **Windows** - the Chrome and Edge media panel (the one behind the address-bar icon, which also feeds the system media controls), plus hardware media keys on keyboards and headsets.
- **iOS/macOS** - lock screen and Control Center.
- With a **sleep timer** armed, the system card draws a real countdown, so you can see what's left without unlocking the phone.

This turned out to be the fiddliest part of the release: the operating system has no idea Web Audio exists, so the card is carried by a separate inaudible `<audio>` element. Chrome and Edge only promote tracks longer than 5 seconds into the system controls, and a track of pure zeroes gets written off as "no audio at all" - so the carrier runs for 30 seconds and holds a square wave one least-significant bit tall: quieter than the noise floor of any signal chain, yet unmistakably real audio to the OS.

### 268 real breaks instead of 49

The drum bank went from 49 to **268 live loops** - real breaks, not synthesis. The large packs live in separate files and are only fetched once DRIVE is playing, so the page still opens instantly.

### Every visit sounds new

Track `#1` used to sound the same forever. Now the **bank is reshuffled on every visit**: the same track number today and tomorrow lands on completely different drums. Within a single session the numbering stays deterministic, so going back to `‹‹ #N ››` still returns the same track.

### The 🎲 "another break" button

Love the harmony, hate the drums? The 🎲 button in the player (or the `X` key, or the extra button in the system card) swaps the break **on the fly**, without restarting the track or breaking the mood.

### Redesigned mobile player

The phone player was rebuilt: a sticky panel at the bottom edge, a CSS-grid layout instead of wrapping rows, thumb-sized tap targets, and dedicated breakpoints for narrow screens. Sliders, timer, and track controls no longer fall apart at 360 pixels wide.

### Small things you can see and hear

- **mp3 codec delay compensation** - decoders leave up to 25 ms of silence at the head of a file, which made the slicing land just barely late. The real start of the loop is now detected from the signal, so hits sit exactly on the grid.
- **The break name** appears in the player caption and on the second line of the system card.
- **Custom icon** - the app artwork doubles as the tab favicon, the home-screen icon, and the system player cover.
- **Bank counter** in the About dialog shows how many breaks are loaded.
- **FOCUS was rewritten** around pure synthesis - the `genres.js` file from 1.1 is gone.

---

## Why this exists

Most music services require you to choose. Choosing is a distraction.
Addiction.fm removes the choice entirely: one button, one state, one stream of sound. Runs in the browser, no install required, no login needed.

---

## States

| State | Genre | For |
|-------|-------|-----|
| 🔴 **DRIVE** | Amen-break · Jungle · ~180 BPM | Energy, task focus, movement |
| 🔵 **FOCUS** | Deep ambient | Sub-bass and dark pads only - no drums |
| 🟢 **CALM** | Slow drone + rain | Relaxation, sleep, recovery |

---

## How it works

Sound is **generated in real time** via the Web Audio API - this is not streaming, not a playlist. Every press creates a unique combination:

- **DRIVE** - a break from a 268-loop bank sliced into 16th notes with DJ jumps, stutters and rolls, soft piano on top
- **FOCUS** - sub-bass synthesized in the chosen key, dark pads through a delay chain
- **CALM** - drone from detuned oscillators, filtered noise, slow bells

---

## Why Addiction.fm

- **Runs everywhere** - Chrome, Firefox, Safari, Android, iOS, Windows. Open and play.
- **Controlled from the OS** - Android shade, Windows media controls, lock screen, media keys
- **Works offline** - download the files and run locally from any folder
- **No accounts** - no tracking, no ads, no recommendation algorithms
- **Always different** - the generative engine creates a new version on every press
- **268 breaks** - the bank is reshuffled on every visit
- **Deterministic tracks** - the `‹‹ #N ››` counter locks a specific track by seed number within a session
- **WAV recording** - the ⏺ rec button captures the track in real time and downloads it as `.wav`
- **Propeller** - spins during playback, gradually coasts to a stop on pause

---

## Files

| File | What's inside | Required |
|------|---------------|----------|
| `addiction-fm.html` | the whole app: engine, interface, artwork | yes |
| `breaks.js` | base bank, 49 breaks | yes |
| `breaks2.js` | main pack, 219 breaks | optional, but far more fun |
| `breaks3.js` | pack top-up | optional |

Without `breaks2.js` and `breaks3.js` the radio runs on the base bank; without `breaks.js` it falls back to synthesized drums.

---

## Shortcuts

| Key | Action |
|-----|--------|
| `Space` | pause |
| `1` `2` `3` | state |
| `V` / `B` | previous / next track |
| `X` | another break |

---

Requirements: **modern browser** (Chrome 90+, Firefox 88+, Safari 15+). Nothing else.

---

## Tech stack

- **Web Audio API** - synthesis, slicing, mixing, real-time recording
- **Media Session API** - system media controls, artwork, sleep-timer countdown
- **OfflineAudioContext** - full track and stem rendering without artifacts
- **ScriptProcessorNode** - PCM capture for WAV export
- **Pure HTML/JS** - zero dependencies, zero frameworks, single file

---

## Author

Made by **Sewerbox** / [sewerdev](https://github.com/sewerdev)

Telegram: [@VestronVulture](https://t.me/VestronVulture)

*Addiction.fm is not a playlist. It's a state of mind.*

---

# Русский

# [Addiction.fm](http://addiction.fm/) 2.0

**[English Page](https://github.com/sewerdev/Addiction.fm)**

<img width="1918" height="889" alt="image" src="https://github.com/user-attachments/assets/34c4e750-e09f-4de1-b251-ba7719a08c4a" />

**Мобильная версия:**

<img width="280" height="600" alt="image" src="https://github.com/user-attachments/assets/0306540a-fcf1-4425-86bc-0522a70fc889" /><img width="280" height="600" alt="image" src="https://github.com/user-attachments/assets/255de5c5-1ffb-4a90-a7cd-198badc76b3a" />

**Генеративное радио. Одна кнопка - и звук создаётся под твоё состояние.**

[Addiction.fm](http://addiction.fm/) - это браузерное генеративное аудио-приложение без плейлистов, аккаунтов и рекламы. Выбери состояние - получи уникальный звук, который никогда не повторится.

---

## 🔥 Что нового в 2.0

Самое крупное обновление с момента запуска: переписан мобильный интерфейс, банк ударных вырос в пять с половиной раз, а управлять радио теперь можно, не открывая вкладку.

### Системный пункт управления

Радио больше не заперто во вкладке браузера. Оно появляется там же, где обычный музыкальный плеер, со своей обложкой:

- **Android** - карточка в шторке уведомлений и на экране блокировки: play/pause, переключение треков, отдельная кнопка «другой брейк».
- **Windows** - панель мультимедиа Chrome и Edge (та, что открывается по иконке в адресной строке и попадает в системный пункт управления), плюс аппаратные медиаклавиши на клавиатуре и наушниках.
- **iOS/macOS** - экран блокировки и Пункт управления.
- Если заведён **таймер сна**, в системной карточке рисуется реальный обратный отсчёт - видно, сколько осталось, не разблокируя телефон.

Технически это оказалось самой муторной частью: Web Audio для операционной системы не существует, поэтому карточку «несёт» отдельный неслышимый элемент `<audio>`. Chrome и Edge берут в системные контролы только дорожку длиннее 5 секунд, а на дорожке из чистых нулей система решает, что звука нет вообще - поэтому носитель длится 30 секунд и содержит меандр амплитудой в один младший бит: тише, чем шум любого тракта, но для системы это настоящий звук.

### 268 настоящих брейков вместо 49

Банк ударных вырос с 49 до **268 живых петель** - реальные брейки, а не синтез. Большие паки лежат отдельными файлами и подтягиваются только когда включён РАЗГОН, так что страница по-прежнему открывается мгновенно.

### Каждый заход - новый звук

Раньше трек `#1` всегда звучал одинаково. Теперь **порядок банка перетасовывается заново при каждом заходе на сайт**: тот же номер трека сегодня и завтра - совершенно разные ударные. Внутри одного сеанса номера остаются детерминированными, так что вернуться на `‹‹ #N ››` и услышать то же самое по-прежнему можно.

### Кнопка 🎲 «другой брейк»

Гармония нравится, а ударные - нет? Кнопка 🎲 в плеере (или клавиша `X`, или отдельная кнопка в системной карточке) меняет брейк **на лету**, не перезапуская трек и не сбивая настроение.

### Редизайн мобильного плеера

Плеер на телефоне собран заново: липкая панель у нижней кромки экрана, раскладка на CSS-сетке вместо переносов, крупные зоны нажатия под большой палец, отдельные брейкпойнты для узких экранов. Ползунки, таймер и переключение треков больше не разъезжаются на 360 пикселях ширины.

### Мелочи, которые слышно и видно

- **Компенсация задержки mp3-кодека** - декодер оставляет в начале файла до 25 мс тишины, из-за чего нарезка едва заметно запаздывала. Теперь реальное начало петли ищется по сигналу, и доли попадают ровно в сетку.
- **Имя брейка** видно в подписи плеера и во второй строке системной карточки.
- **Своя иконка** - обложка приложения работает как фавикон вкладки, иконка на домашнем экране и обложка в системном плеере.
- **Счётчик банка** в окне «О приложении» показывает, сколько брейков подгружено.
- **ФОКУС переписан** на чистый синтез - файл `genres.js` из версии 1.1 больше не нужен.

---

## Зачем это существует

Большинство музыкальных сервисов требуют выбора. Выбор - это отвлечение.
[Addiction.fm](http://addiction.fm/) убирает выбор полностью: одна кнопка, одно состояние, один поток звука. Работает в браузере, не требует установки, не просит логин.

---

## Состояния

| Состояние | Жанр | Для чего |
|-----------|------|----------|
| 🔴 **РАЗГОН** | Amen-break · Jungle · ~180 BPM | Энергия, фокус на задаче, движение |
| 🔵 **ФОКУС** | Глубокий эмбиент | Только суббасс и тёмные пэды - никаких ударных |
| 🟢 **ПОКОЙ** | Медленный дрон + дождь | Расслабление, сон, восстановление |

---

## Как это работает

Звук **генерируется в реальном времени** через Web Audio API - это не стриминг и не плейлист. Каждое нажатие создаёт уникальную комбинацию:

- **РАЗГОН** - брейк из банка на 268 петель нарезается по 16-м долям с DJ-прыжками, статтерами и роллами, мягкое пианино поверх
- **ФОКУС** - суббасс синтезируется в заданной тональности, тёмные пэды через delay-цепочку
- **ПОКОЙ** - дрон из расстроенных осцилляторов, фильтрованный шум, медленные колокольчики

---

## Преимущества

- **Работает везде** - Chrome, Firefox, Safari, Android, iOS, Windows. Открыть и играть.
- **Управление из системы** - шторка Android, пункт управления Windows, экран блокировки, медиаклавиши
- **Без интернета** - скачай файлы и запусти локально из любой папки
- **Нет аккаунтов** - нет трекинга, нет рекламы, нет алгоритмов рекомендаций
- **Каждый раз разный** - генеративный движок создаёт новую версию при каждом нажатии
- **268 брейков** - банк перетасовывается при каждом заходе
- **Детерминированные треки** - счётчик `‹‹ #N ››` фиксирует конкретный трек по seed-номеру внутри сеанса
- **Запись в WAV** - кнопка ⏺ rec захватывает трек в реальном времени и скачивает как `.wav`
- **Пропеллер** - крутится при воспроизведении, плавно тормозит при паузе

---

## Файлы

| Файл | Что внутри | Обязателен |
|------|------------|------------|
| `addiction-fm.html` | приложение целиком: движок, интерфейс, обложка | да |
| `breaks.js` | базовый банк, 49 брейков | да |
| `breaks2.js` | основной пак, 219 брейков | нет, но с ним интереснее |
| `breaks3.js` | добор пака | нет |

Без `breaks2.js` и `breaks3.js` радио работает на базовом банке, без `breaks.js` - на синтезированных ударных.

---

## Горячие клавиши

| Клавиша | Действие |
|---------|----------|
| `Space` | пауза |
| `1` `2` `3` | состояние |
| `V` / `B` | трек назад / вперёд |
| `X` | другой брейк |

---

Требования: **современный браузер** (Chrome 90+, Firefox 88+, Safari 15+). Больше ничего.

---

## Технологии

- **Web Audio API** - синтез, нарезка, микширование, запись в реальном времени
- **Media Session API** - системный пункт управления, обложка, обратный отсчёт таймера
- **OfflineAudioContext** - рендер полных треков и стемов без артефактов
- **ScriptProcessorNode** - захват PCM для экспорта в WAV
- **Чистый HTML/JS** - ноль зависимостей, ноль фреймворков, один файл

---

## Автор

Сделано **Sewerbox** / [sewerdev](https://github.com/sewerdev)

Telegram: [@VestronVulture](https://t.me/VestronVulture)

---

*[Addiction.fm](http://addiction.fm/) - это не плейлист. Это состояние.*
