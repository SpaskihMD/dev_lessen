# 🎬 Открытие видео через терминал в Ubuntu

## 📦 Установка видеоплееров

```bash
# VLC (рекомендуется, поддерживает большинство форматов)
sudo apt install vlc

# MPV (легковесный, удобный для терминала)
sudo apt install mpv

# FFplay (входит в ffmpeg, минималистичный)
sudo apt install ffmpeg
```

## 🚀 Команды для воспроизведения

### VLC (из терминала)
```bash
# Открыть видео
vlc video.mp4

# В полноэкранном режиме
vlc --fullscreen video.mp4

# Без графического интерфейса (только видео)
vlc -I dummy video.mp4 --play-and-exit

# Воспроизвести по URL
vlc "https://example.com/video.mp4"
```

### MPV (проще и быстрее)
```bash
# Обычное воспроизведение
mpv video.mp4

# Начать с определённой секунды (2:30)
mpv --start=2:30 video.mp4

# В полноэкранном режиме
mpv --fs video.mp4

# Зациклить видео
mpv --loop video.mp4

# Замедлить/ускорить (0.5x или 2.0x)
mpv --speed=0.5 video.mp4
```

### FFplay (самый простой)
```bash
# Базовое воспроизведение
ffplay video.mp4

# Автозакрытие после завершения
ffplay -autoexit video.mp4

# Без звука
ffplay -an video.mp4
```

## 📂 Работа с несколькими файлами

```bash
# Все видео в папке (mpv закроется после каждого)
mpv *.mp4

# Плейлист
mpv --playlist <(ls *.mp4)

# Случайный порядок
mpv --shuffle *.mp4
```

## 🔗 Воспроизведение из интернета

```bash
# Скачанное ранее видео
mpv ~/Videos/video.mp4

# Прямая ссылка
mpv "https://example.com/video.mp4"

# RuTube (если прямая ссылка на файл)
mpv "https://rutube.ru/video/..."

# YouTube через yt-dlp + mpv
mpv $(yt-dlp -g "https://youtube.com/watch?v=...")
```

## ⌨️ Горячие клавиши (в MPV)

| Клавиша | Действие |
|---------|----------|
| `Space` | Пауза/продолжить |
| `←` `→` | Назад/вперёд на 5 секунд |
| `↑` `↓` | Громкость +10/-10 |
| `f` | Полный экран |
| `q` | Выход |
| `9` `0` | Громкость +/- |
| `[` `]` | Скорость -/+ 10% |
| `Ctrl+C` | Принудительный выход |

## 🎯 Быстрый пример (самый простой способ)

```bash
# 1. Установить mpv
sudo apt install mpv

# 2. Открыть видео
mpv Save-Video.md  # ❌ так не работает (это текст)

# Правильно — видеофайл:
mpv video.mp4
mpv ~/Загрузки/my_video.webm
```

## 💡 Полезные комбинации

```bash
# Найти и открыть все видео в текущей папке
find . -type f \( -name "*.mp4" -o -name "*.webm" -o -name "*.avi" \) -exec mpv {} \;

# Открыть видео в фоне
mpv video.mp4 &

# Создать алиас для быстрого открытия
echo "alias play='mpv --fs'" >> ~/.bashrc
source ~/.bashrc
play video.mp4
```

## ⚠️ Важно

**Файл `Save-Video.md` — это текстовый документ (Markdown), а не видео!**

Чтобы открыть его для просмотра текста:
```bash
less Save-Video.md     # постраничный просмотр
cat Save-Video.md      # вывести весь текст
nano Save-Video.md     # редактирование
```

Если вы действительно хотите открыть видео — укажите путь к видеофайлу (`.mp4`, `.webm`, `.avi`, `.mkv` и т.д.).
