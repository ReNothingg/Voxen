# Персональный TTS на своём голосе (Coqui TTS + Python 3.11.9)

Проект для создания синтеза речи (TTS) на собственном голосе с использованием библиотеки [Coqui TTS](https://github.com/coqui-ai/TTS). Работает на Windows, совместим с Python 3.11.9.

## 📁 Структура проекта

```
my_tts_project/
├── data/
│   ├── raw/               # Исходные записи (WAV)
│   ├── normalized/        # Нормализованные WAV-файлы
│   └── metadata.csv       # Таблица разметки: имя файла | текст
├── configs/
│   └── config.json        # Конфигурация модели
├── scripts/
│   ├── record_dataset.py  # Скрипт записи фраз с микрофона
│   ├── normalize_audio.py # Скрипт нормализации WAV
│   ├── train.py           # Запуск обучения
│   └── synthesize.py      # Синтез текста в речь
├── output/                # Выходные данные: модель, лог, синтез
│   └── model.pth
├── .gitignore
└── README.md
```

## ⚙️ Установка среды

```bash
python -m venv tts_env
tts_env\Scripts\activate
pip install --upgrade pip setuptools
pip install torch torchvision torchaudio
pip install coqui-tts soundfile librosa numpy scipy matplotlib
```

## 🎤 Запись и подготовка данных

1. Отредактируйте список фраз в `scripts/record_dataset.py`.
2. Запустите скрипт и прочитайте фразы:
   ```bash
   python scripts/record_dataset.py
   ```
3. Нормализуйте аудио:
   ```bash
   python scripts/normalize_audio.py
   ```
4. Создайте `metadata.csv`:
   ```
   0001.wav|Привет, как дела?|
   0002.wav|Сегодня хорошая погода.|
   ...
   ```

## 🧠 Обучение модели

Настройте `configs/config.json` под ваши данные. Затем запустите:

```bash
python scripts/train.py
```

Модель будет сохраняться в `output/`.

## 🗣️ Синтез речи

После завершения обучения:

```bash
python scripts/synthesize.py
```

Результат сохранится как `output/output.wav`.

## 🛠 Зависимости

- Python 3.11.9
- Coqui TTS
- PyTorch
- soundfile, librosa
- numpy, scipy, matplotlib (опционально)
