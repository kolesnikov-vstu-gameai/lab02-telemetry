# Лабораторная работа № 2. Сбор и анализ игровой телеметрии

Дисциплина «Игровой искусственный интеллект» · Максимум **20 баллов** (+5 за задание со звёздочкой)

**Студент:** ФИО, группа · **Вариант стека:** … · **Видео:** <ссылка> · **Отчёт:** `docs/report.md` → PDF

## Стек

Unity/Python клиент · SQLite/PostgreSQL · pandas · Streamlit/Jupyter

## Что нужно сдать

- [ ] Клиентский логгер событий
- [ ] БД с 20+ сессиями
- [ ] Скрипт анализа: 4 расчёта (длина сессий, retention, heatmap смертей, конверсия)
- [ ] Дашборд с 3+ визуализациями
- [ ] Отчёт PDF 5–7 стр.: схема событий, ER-диаграмма, скриншоты

Полное задание, критерии оценки и типичные ошибки — в методических указаниях (ЛР № 2).

## Структура

```
client/python_logger.py        логгер событий (JSON Lines → файл или HTTP POST)
client/unity/TelemetryLogger.cs  то же для Unity
server/app.py                  FastAPI: POST /events → SQLite
analysis/analyze.py            4 расчёта + сохранение графиков в results/
dashboard/app.py               Streamlit-дашборд
docs/event_schema.md           схема событий (заполнить)
```

```bash
pip install -e ".[dev]"
uvicorn server.app:app --reload         # сервер
python client/python_logger.py --simulate 20   # 20 синтетических сессий
python analysis/analyze.py && streamlit run dashboard/app.py
```

## Как сдавать

1. Работайте в этом репозитории, коммитьте по шагам (`step-1`, `step-2` …) — история коммитов учитывается.
2. Отчёт пишите в `docs/report.md` (черновик по разделам, 5–7 стр.), затем перенесите в официальный шаблон отчёта, принятый на кафедре, и экспортируйте в PDF (`docs/report.pdf`).
3. Видео — на YouTube/Диск, ссылку в README и в отчёт. Файлы видео в git не кладём.
4. Готовую работу отметьте тегом `git tag v1.0 && git push --tags` и создайте Release.
