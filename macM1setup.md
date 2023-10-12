# Mac M1 Silicon Setup

1) Устанавливаем homebrew https://brew.sh
`/bin/bash -c "$(curl -fsSL https://raw.githubusercontent.com/Homebrew/install/HEAD/install.sh)"`

2) Ставим xcode.
Заходим в магазин проложений apple - ищем по ключевому слову и устанавливаем

3) Ставим cmake через brew
`brew install cmake`

4) Ставим miniconda для управления пакетами и версиями python
```sh
wget https://github.com/conda-forge/miniforge/releases/latest/download/Miniforge3-MacOSX-arm64.sh
bash Miniforge3-MacOSX-arm64.sh
```

5) Даем установку конде принимать пакеты, поставленные pip-ом принимать, как родные - установленные кондой.
Это нужно для того, чтобы конда не переустанавливала пакеты, которые были установлены с pip-ом.
Дело в том, что для некоторых пакетов конда ставит их не оптимизированными для маковского проца.
Например, numpy поставленный через конду будет в 4 раза медленнее на некоторых задачах.
`conda config --set pip_interop_enabled true`

5) Ставим numpy через pip 
`pip install --no-binary :all: --no-use-pep517 numpy`
Если эта команда не проходит, то тогда просто
`pip install numpy`

6) Проверяем работы на тестовом скрипте:
```python
import time
import numpy as np
np.random.seed(42)
a = np.random.uniform(size=(300, 300))
runtimes = 10

timecosts = []
for _ in range(runtimes):
    s_time = time.time()
    for i in range(100):
        a += 1
        np.linalg.svd(a)
    timecosts.append(time.time() - s_time)
    print(f'{timecosts[-1]:.5f}s')

print(f'mean of {runtimes} runs: {np.mean(timecosts):.5f}s')
```

запускаем через python <имя скрипта>, должно получиться не более 3 секунд на итерацию.
Для сравнения - на интеле отрабатывает за 1 секунду, но это супер-оптимизированная библиотечка от интел для вычислений.
Не очень актуально уже, но источник для всего этого - https://gist.github.com/MarkDana/a9481b8134cf38a556cf23e1e815dafb
https://developer.apple.com/forums/thread/695963


7) Справка по работе с мини-кондой - точно пригодится:
https://docs.conda.io/projects/conda/en/4.6.0/_downloads/52a95608c49671267e40c689e0bc00ca/conda-cheatsheet.pdf

8) Очень удобно работать с sshfs для монтирования локально данных по ssh - для этого надо поставить 2 пакета по ссылке из статьи ниже.
https://www.petergirnus.com/blog/how-to-use-sshfs-on-macos

Далее надо погасить мак и долго держать кнопку питания, чтобы войти в меню загрузки. 
В меню выбрать через утилиты настройки безопасности и разрешить запуск приложений/расширений от сторонних разработчиков. 
После этого станет возможным работы с macFUSE.
Монтировать диски можно вот такой командой:
`sshfs username@remote:<удаленный путь> <локальный путь - куда монтировать> -o volname=VOLUME_NAME`






