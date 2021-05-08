# Оценка результатов A/B-теста: выпускной проект
## Описание проекта:

В данном проекте проводится анализ результатов A/B-тестирования изменений, связанных с внедрением улучшенной рекомендательной системы, а также изучается влияние этих изменений на платежную воронку. Кроме того, оценивается корректность проведения теста на предмет пересечения тестовой аудитории с конкурирующим тестом, совпадения теста и маркетинговых событий, а также исследуется наличие других проблем временных границ теста.

**Техническое задание:**

- *Группы:* А — контрольная, B — новая платёжная воронка;
- *Дата запуска:* 2020-12-07;
- *Дата остановки набора новых пользователей:* 2020-12-21;
- *Дата остановки:* 2021-01-04;
- *Аудитория:* 15% новых пользователей из региона EU;
- *Ожидаемое количество участников теста:* 6000;
- *Ожидаемый эффект:* за 14 дней с момента регистрации пользователи покажут улучшение каждой метрики не менее, чем на 10%.

## Главные выводы:

По результатам исследования, можем заключить, что тест был проведен с большим количеством нарушений, и его результаты не должны считаться валидными:

* В обеих группах присутствует определенное число выбросов, искажающих данные о распределении, кроме того, сами распределения далеки от нормальных.
* Группы были набраны неравномерно - контрольная группа A почти в три раза больше, чем группа B, и объема выборок недостаточно, чтобы зарегистрировать значимые изменения согласно поставленному тех.заданию.
* Время проведения тестирования было выбрано неудачно - оно совпадает с рождественским / новогодним сезоном праздников, что влияет на результаты теста.
* Эксперимент планировалось завершить 4 января 2021, однако данные по событиям не поступали после 30 декабря - не исключены технические ошибки логирования.
* Механизм разбиения пользователей на группы работает с ошибками - группы нельзя назвать разбитыми случайно: они не только кардинально различаются по размеру, но и различаются по составу устройств (больше стационарных устройств в контрольной группе и больше мобильных - в экспериментальной), а это вносит серьезные искажения в результаты.

При этом, отметим, что мы наблюдали снижение конверсии на всех шагах воронки в группе B, хотя единственным статистически значимым различием можно условно назвать лишь этап корзины. Этим результатам не следует доверять, но не исключено, что изменения в рекомендательной системе действительно могли негативно повлиять на пользовательский опыт - это предположение следует проверить с помощью организации нового теста, который учтет все замечания и исключит ошибки.

## Используемые библиотеки:
pandas, numpy, matplotlib, seaborn, plotly, scipy, statsmodels, math