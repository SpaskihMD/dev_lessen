# 📥 Скачивание видео с RuTube в Ubuntu (терминал)

## 📦 Установка инструментов

```bash
# Установка yt-dlp (основной инструмент)
sudo apt update
sudo apt install python3-pip ffmpeg
pip3 install --upgrade yt-dlp

# Альтернативная установка через apt
sudo apt install yt-dlp
```

## 🚀 Базовое использование

| Команда | Описание |
|---------|----------|
| `yt-dlp "URL"` | Скачать в лучшем качестве |
| `yt-dlp -o "имя.%(ext)s" "URL"` | Указать имя файла |
| `yt-dlp -o "~/Videos/%(title)s.%(ext)s" "URL"` | Сохранить в папку Videos |

## ⚙️ Полезные опции

| Опция | Назначение |
|-------|------------|
| `-f "best[height<=720]"` | Ограничить качество (720p) |
| `-x --audio-format mp3` | Скачать только аудио в MP3 |
| `--limit-rate 1M` | Ограничить скорость (1 МБ/с) |
| `--write-subs --sub-lang ru` | Скачать русские субтитры |
| `--user-agent "Mozilla/5.0..."` | Подменить User-Agent |

## 📁 Скачивание плейлистов

```bash
yt-dlp -o "%(playlist_title)s/%(playlist_index)s - %(title)s.%(ext)s" "URL_ПЛЕЙЛИСТА"
```

## 🔧 Решение проблем

| Проблема | Решение |
|----------|---------|
| Ошибка скачивания | `pip3 install --upgrade yt-dlp` |
| Кэш мешает | `yt-dlp --rm-cache-dir` |
| Требуется авторизация | `yt-dlp --cookies-from-browser firefox "URL"` |
| Geo-блокировка | Использовать `--user-agent` с реальным браузером |

## 🔄 Альтернативные инструменты

```bash
# Через npm
sudo apt install npm
npm install -g rutube-dl
rutube-dl "URL"
```

## 💡 Быстрая памятка

```bash
# Обычное скачивание
yt-dlp "https://rutube.ru/video/..."

# Только аудио
yt-dlp -x --audio-format mp3 "URL"

# Обновление
pip3 install --upgrade yt-dlp
```

> ⚠️ **Важно:** RuTube периодически меняет защиту. Всегда держите `yt-dlp` обновлённым.
