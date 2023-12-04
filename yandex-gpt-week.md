# GPT Week (23-НОЯ - 01-ДЕК 2023)
https://shad.yandex.ru/gptweek  

## Интенсив GPT Week: 01 Введение в большие языковые модели  
Спикер: Миша Хрущёв, руководитель группы претрейна YandexGPT
- [Лекция](https://www.youtube.com/watch?v=c7VUzWKFECg)
- [Семинар](https://www.youtube.com/watch?v=xeNBAoYAZCY)
- [Ноутбук](https://disk.yandex.ru/d/QqYRiUd4jBEjkg)


## Интенсив GPT Week: 02 Про претрейн LLM  
Спикер: Миша Хрущёв, руководитель группы претрейна YandexGPT  
- [Лекция - часть 1](https://www.youtube.com/watch?v=xAQoZflquMw)
- [Лекция - часть 2](https://www.youtube.com/watch?v=xbVrjWaeCHc)  

Ссылки:  
- [Трансформеры и Attention](https://arxiv.org/abs/1706.03762)
- [GPT-3](https://arxiv.org/abs/2005.14165)
- [Поиск оптимального времени обучения для моделей](https://arxiv.org/abs/2203.15556)
- Llama: [https://arxiv.org/abs/2302.13971](https://arxiv.org/abs/2302.13971) и [https://arxiv.org/abs/2307.09288](https://arxiv.org/abs/2307.09288)
- [Adan](https://arxiv.org/abs/2208.06677)
- [FSDP](https://pytorch.org/tutorials/intermediate/FSDP_tutorial.html)
- DeepSpeed - фреймворк для распределенного обучения. Мы от него отошли, но там куча полезных статей: [https://www.deepspeed.ai/](https://www.deepspeed.ai/)
- [RoPE](https://www.arxiv-vanity.com/papers/2104.09864/)

## Интенсив GPT Week: 03 Подготовка данных для обучения претрейна и замер качества больших языковых моделей  
Спикер: Лёша Зотов, руководитель группы качества данных YandexGPT  
- [Лекция](https://www.youtube.com/watch?v=mu2JJEzK5ik)  
- [Семинар](https://www.youtube.com/watch?v=fiBXu0f92FE)  
- [Ноутбук](https://disk.yandex.ru/d/aYYPDNPDyemtUA)  

Ссылки:  
- [Training Compute-Optimal Large Language Models (Hoffman et al., 2022)](https://arxiv.org/abs/2203.15556)
- [Scaling Data-Constrained Language Models (Muennighoff et al., 2023)](https://arxiv.org/abs/2305.16264)
- [The RefinedWeb Dataset for Falcon LLM](https://arxiv.org/abs/2306.01116)
- [Nougat: Neural Optical Understanding for Academic Documents](https://arxiv.org/abs/2308.13418)
- [Scaling Language Models: Methods, Analysis & Insights from Training Gopher](https://arxiv.org/abs/2112.11446)
- [OpenWebMath: An Open Dataset of High-Quality Mathematical Web Text](https://arxiv.org/abs/2310.06786)
- [Объяснение Minhash + LSH алгоритма](https://cse.iitkgp.ac.in/~animeshm/algoml/lsh.pdf)
- [D4: Improving LLM Pretraining via Document De-Duplication and Diversification](https://arxiv.org/abs/2308.12284)
- [Textbooks Are All You Need](https://arxiv.org/abs/2306.11644)
- [In-Context Pretraining: Language Modeling Beyond Document Boundaries](https://arxiv.org/abs/2310.10638)
- [DoReMi: Optimizing Data Mixtures Speeds Up Language Model Pretraining](https://arxiv.org/abs/2305.10429) 


## Интенсив GPT Week : 04 Alignment
Спикер: Паша Темирчев, разработчик группы поиска смысла  
- [Лекция](https://www.youtube.com/watch?v=f5JFXvX7FLE)
- [Семинар](https://www.youtube.com/watch?v=dcN0BFa0OAI)

Ссыллки:
1) [A General Language Assistant as a Laboratory for Alignment](https://arxiv.org/abs/2112.00861)

Статья от Anthropic, в которой вводится терминология Harmless, Helpful, Honest агента, и в целом описан процесс обучения модели предпочтений.

2) [Reinforcement Learning Textbook, Ivanov S.](https://arxiv.org/abs/2201.09746)

Конспект лекций по обучению с подкреплением от Сергея Иванова на русском языке (рекомендуем).

3) [Proximal Policy Optimization](https://arxiv.org/abs/1707.06347)

РРО - алгоритм, который обычно используется в дообучении LMок на задачу Alignment. В лекции мы его проскочили вскользь, разобрав его базу - градиент по политике.

4) [Direct Preference Optimization](https://arxiv.org/pdf/2305.18290.pdf)  
Метод alignment'а, с которым мы познакомимся на семинаре


## Интенсив GPT Week : 05 Ускорение инференса LLM 
Рома Горб, разработчик группы претрейна YandexGPT  
- [Лекция](https://www.youtube.com/watch?v=AnAR1QcP-QQ)  
- [Семинар](https://www.youtube.com/watch?v=YlBjVVnAsWg)   
- [Ноутбук](https://disk.yandex.ru/d/1aC4Qu2X4NHfvg)   

Ссылки:  
- [Канал в телеге](https://t.me/gromka_public  )
- [Про GPU и ускорение pretrain-a](https://habr.com/en/companies/yandex/articles/672396/)  
- [Курс Practical RL в ШАД-е](https://github.com/yandexdataschool/Practical_RL)  
- [Статья MiniLLM](https://arxiv.org/abs/2002.10957)  
- [Статья LLM.int8()](https://arxiv.org/abs/2208.07339)  
- [Статья SmoothQuant](https://arxiv.org/abs/2211.10438)  
- [Статья GPT-Q (OPT-Q)](https://arxiv.org/abs/2210.17323)  
- [Сравнение фреймворков](https://sersavvov.com/blog/7-frameworks-for-serving-llms)  
- [Continuous Batching](https://www.anyscale.com/blog/continuous-batching-llm-inference)  
- [PEFT и API sharing](https://habr.com/en/companies/yandex/articles/588214/)  
- [Speculative Decoding](https://arxiv.org/abs/2302.01318)  
