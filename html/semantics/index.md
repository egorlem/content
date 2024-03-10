---
title: "Что такое семантика?"
description: "Как работает семантическая вёрстка и зачем она вообще нужна."
authors:
  - punkmachine
contributors:
  - skorobaeus
  - gvozdenkov
  - tatianafokina
related:
  - a11y/chto-takoe-a11y
  - a11y/a11y-html
  - html/seo-for-beginners
tags:
  - article
---

## Кратко

Семантическая вёрстка — особый подход к написанию HTML-разметки страниц. При этом подходе разработчик опирается не на содержание сайта, а на смысловое предназначение каждого блока и логическую структуру страницы.

## Семантические теги

В современном стандарте HTML есть большое количество семантических тегов под разные логические блоки веб-документа. Приведу список семантических тегов, разделяющих HTML-документ на секции:

- [`<article>`](/html/article/) — тег для создания самостоятельных блоков контента. Его содержимое может быть карточкой статьи в блоге, карточкой товара, рекламным баннером и любым другим самодостаточным логическим блоком.
- [`<aside>`](/html/aside/) — тег для дополнительного контента, используется для создания «сайдбара» или бокового меню на сайтах.
- [`<nav>`](/html/nav/) — контейнер для навигации со ссылками на другие страницы и разделы сайта.
- [`<section>`](/html/section/) — логический контейнер для объединия содержимого по смыслу. Его часто путают с `<article>`. `<section>` используют для отделения одной смысловой части от другой, а `<article>` — самодостаточный контейнер со своим содержимым.
- [`<main>`](/html/main/) — контейнер для основного содержимого страницы.
- [`<header>`](/html/header/) — тег для выделения вводного содержимого или навигации. Не привязан к конкретному месту страницы или внутрии её отдельной секции, но традиционно используется для создания основной навигации по сайту — «шапки». Также можно использовать для оборачивания оглавления раздела, заголовка статьи с вводной информацией о ней и т. д.
- [`<footer>`](/html/footer/) — тег с информацией о разделе. Например, это могут быть данные о том, когда была написана статья, её авторе и пр. Тоже не имеет жёсткой привязки к положению на странице или отдельной секции, к которой относится.

К примеру, здесь у `<article>` есть дата начала старта курса, которую можно поместить в «подвал» карточки:

```html
<article>
  <header>
    <h2>SEO для начинающих</h2>
    <span class="author">Иван Иванович</span>
  </header>

  <p>
    Благодаря этому курсу вы научитесь задавливать конкурентов
    с помощью ссылочной массы, а не качественного контента.
  </p>

  <footer>
    <time datetime="2023-02-13">
      13 февраля 2023
    </time>
  </footer>
</article>
```

Кроме семантических тегов, выделяющих целые разделы документа, есть ещё и контентные. Например:

- [`<h1>`-`<h6>`](/html/h1-h6/) — для определения заголовков на странице. `<h1>` используют для заголовка в документе, который является основным для всего документа или раздела. Остальные теги служат для подзаголовков, которая обозначает иерархию и структуру содержимого.
- [`<button>`](/html/button/) — для кнопок. Можно использовать для отправки форм, выполнения команд или вызова функций через JavaScript.
- [`<img>`](/html/img/) — для вставки изображений в документ.
- [`<table>`](/html/tables/) — для таблиц. Состоят из нескольких элементов для структурирования данных: `<tr>` для строк, `<th>` для заголовочных ячеек и `<td>` для стандартных ячеек.
- [`<ul>`](/html/ul/) — определяет неупорядоченный список, который обычно отображается с маркерами.
- [`<a>`](/html/a/) — для ссылок, с помощью которых пользователи переходят от одного документа к другому.
- [`<p>`](/html/p/) — для абзаца текста. Абзацы являются основными блоками текста в HTML и используются для разделения содержимого на управляемые и логически разграниченные секции. Они упрощают чтение и делают текст понятным.

Список всех тегов найдёте [в HTML Living Standard](https://html.spec.whatwg.org/multipage/).

## Почему важна семантика

Рассмотрим причины, зачем нужна семантическая вёрстка.

### Поддержка и читаемость кода

При использовании семантических тегов легче поддерживать исходный код проекта. Куда удобнее ориентироваться в коде, если он состоит из семантических тегов. Так любому члену команды будет понятна логика и структура интерфейса.

Семантические теги экономят время разработчиков и уменьшают количество строк кода в файлах. Например, в `<button>` и [`<input>`](/html/input) уже встроены обработчики событий, которые не нужно предусматривать разработчику. К примеру, чтобы воспроизвести нативное поведение кнопки, нужно слушать события `keydown` при нажатии на <kbd>Enter</kbd> и `keyup` для пробела и <kbd>Enter</kbd>.

### Доступность

Семантика — основа доступных интерфейсов. Зрячим пользователям часто легче ориентироваться по сайту, чем тем, кто его не видит. Люди со слепотой и слабовидящие используют [скринридеры](/a11y/screenreaders) и экранные лупы для чтения содержимого страницы. В этом случае семантическая HTML-разметка улучшает их пользовательский опыт и не создаёт барьеры, из-за которых люди с инвалидностью не могут пользоваться сайтом в принципе.

Дело в том, что в семантические теги уже встроены [роли](/a11y/aria-roles/), [состояния и свойства](/a11y/aria-attrs/). Роли помогают пользователям вспомогательных технологий понять, что это за элемент, и как им управлять. Состояния и свойства дают дополнительную информацию об элементах интерфейса. Например, скринридер расскажет про `<button>`, что это кнопка, а пользователи голосового управления кликнут по ней с помощью команды «кнопка, клик». У чекбоксов есть состояния `checked` и `unchecked`. Благодаря им не только визуально, но и на слух понятно, какой чекбокс выбран, а какой нет. Пример свойства — уровень заголовка. У тегов `<h1>`−`<h6>` есть свойство `level` по умолчанию. Скринридеры зачитывают уровень заголовка вместе с его ролью: заголовок первого уровня или заголовок четвёртого уровня.

Другая важная часть семантики — улучшение навигации для скринридеров. Теги вроде `<header>` и `<footer>` — ориентиры. Это значит, что пользователи могут быстро перемещаться по ним с помощью особых горячих клавиш. Дополнительно можно открыть список со всеми ориентирами со страницы, а также с заголовками, кнопками и ссылками. Кстати, перемещение по заголовкам в мире сринридерах — один из самых популярных [методов поиска информации по странице](https://webaim.org/projects/screenreadersurvey10/#finding).

Семантическая вёрстка также помогает избежать переписывания кода (рефакторинга) в будущем, если начнёте улучшать доступность сайта.

Напоследок, не придётся оптимизировать сайт под [режим принудительных цветов](/a11y/forced-colors/). Самая популярная разновидность — режим высокой контрастности в Windows. В нём цвета в системе и на сайтах ограничиваются до небольшой палитры. Eсли кнопка свёрстана на `<div>`, в таком режиме система не заменит ваш цвет на системный.

### Поисковая оптимизация

Семантика нужна и для поисковой оптимизации сайтов, которую коротко называют SEO. Уровень доступностм сайта сам по себе — один из факторов ранжирования в поисковых системах. Правильное использование семантических тегов приводит к более доступному интерфейсу для пользователей и при этом помогает обоходить другие в поисковой выдаче.

Семантическая вёрстка помогают и самим поисковым движкам. Они не понимают сам текст, его контекст и то, насколько он важен. Семантические теги дают поисковым системам нужный контекст, помогают понять содержимое сайта и проиндексировать его относительно других со схожей тематикой. При этом хорошие альтернативные описания `alt` к картинкам и закрытые субтитры к видео в `<track>` дают поисковым роботам ещё больше информации. Это поможет сайту попасть и в текстовую поисковую выдачу, и в выдачу при поиске по картинкам.

Структура сайта и соответствующие семантические теги не влияют на положение в выдаче, но повышают вероятность перехода на сайт. Например, в Google под название сайта попадают заголовки второго уровня, если используете тег `<h2>`. Пользователям легче понять структуру сайта и сделать выбор в его пользу, особенно когда на других сайтов вообще нет заголовков.

Навигация по сайту — важный фактор для продвижения сайта и простой способ повлиять на построение внутренних ссылок. Навигация `<nav>` со списком ссылок `<a>` в меню и футере поможет быстрее попасть в выдачу, чем ссылки в основной части страниц.

Пара полезных ссылок:

- [Intro To Why Accessibility is Important for Good SEO](https://www.deque.com/blog/intro-to-why-accessibility-is-important-for-good-seo/).
- [SEO and Accessibility Are Symbiotic](https://www.deque.com/blog/seo-and-accessibility-are-symbiotic/).
- [7 tactics that benefit both accessibility and SEO](https://www.deque.com/blog/7-tactics-that-benefit-both-accessibility-and-seo/).
- [Accessibility is the Future of Search](https://www.deque.com/blog/accessibility-is-the-future-of-search/).

## Как семантически разметить страницу

Разберём по шагам.

**Первый шаг**. Смотрим на крупные блоки всего сайта и выделяем их под теги для блоков. Например, `<header>`, `<footer>`, `<main>`, `<nav>` или `<aside>`. Обычно эти блоки повторяются на всех страницах.

Можете использовать правило большого пальца. Если тянет добавить к `<div>` классы вроде `header`, `sidebar`, `content`, `post` и `footer`, лучше использовать теги `<header>`, `<aside>`, `<main>`, `<article>` и `<footer>`.

![Две схемы разметки одной и той же страницы с семантическим HTML-кодом и без.](images/example-semantic-markup.png)
Сравнение несемантической и семантической структуры сайта.

**Второй шаг**. Смотрим на содержимое страницы. Исходя из него размечаем заголовки [`<h1>`-`<h6>`](/html/h1-h6/). Общепринято делать всего один заголовок первого уровня `<h1>` на странице. Также помните о правильном порядке заголовков.

Разберём на примере. На странице всего один заголовок первого уровня. Заголовки третьего уровня находятся в том же блоке, что и заголовок `<h2>`, являясь его подзаголовками. Третьей секцией снова идёт `<h2>` уже со своим содержимым.

```html
<main>
  <section>
    <h1></h1>
    <p></p>
  </section>

  <section>
    <h2></h2>
    <p></p>

    <h3></h3>
    <p></p>

    <h3></h3>
    <p></p>
  </section>

  <section>
    <h2></h2>
    <p></p>
  </section>
</main>
```

**Третий шаг**. Обращаем внимание на небольшие смысловые разделы страницы. Списки, таблицы, примеры кода, параграфы текста, цитаты и похожие элементы оборачиваются в свои теги.

**Четвёртый шаг**. Разбираемся с самыми мелкими элементами: кнопками, временем, изображениями, ссылками, видео и тому подобным.

## Примеры

### Вёрстка с `<div>` и `<span>`

Часть разработчиков может подумать, что использовать теги для кнопок, изображений, ссылок, видео, таблиц и списков излишне. До сих пор часто замечаю, что многие используют `<div>` даже для вёрстки этих базовых блоков.

Давайте на примере разберёмся, как можно сверстать двумя способами: с семантикой и без. Для начала без семантики:

<iframe title="Несемантическая вёрстка" src="demos/bad-markup/" height="1210"></iframe>

Не будем уделять внимание стилям, приведём только HTML-код из демо:

```html
<div class="container">
  <div class="header">
    <div class="nav">
      <a href="#" class="nav__item">Главная</a>
      <a href="#" class="nav__item">Блог</a>
      <a href="#" class="nav__item">Контакты</a>
    </div>
  </div>
  <div class="main">
    <span class="heading">Курсы компании «Гарцующий пони»</span>
    <div class="wrapper">
      <div class="card">
        <div class="card__header">
          <span class="card__heading">SEO для начинающих</span>
          <span class="card__author">Иван Иванович</span>
        </div>
        <div class="card__content">
          <img
            src="./images/seo-course.png"
            alt=""
            class="card__img"
            decoding="async"
          >
          <span class="card__description">
            Благодаря этому курсу вы научитесь задавливать конкурентов
            с помощью ссылочной массы, а не качественного контента.
          </span>
        </div>
        <div class="card__footer">
          <span>13 февраля 2023</span>
        </div>
      </div>

      <div class="card">
        <div class="card__header">
          <span class="card__heading">
            WordPress разработка
          </span>
          <span class="card__author">Ольга Ольгина</span>
        </div>
        <div class="card__content">
          <img
            src="./images/wordpress-course.png"
            alt=""
            class="card__img"
            decoding="async"
          >
          <span class="card__description">
            WordPress — топ за свои деньги. Изучите его, чтобы стать
            востребованным фрилансером.
          </span>
        </div>
        <div class="card__footer">
          <span>23 октября 2023</span>
        </div>
      </div>

      <div class="card">
        <div class="card__header">
          <span class="card__heading">JavaScript для чайников</span>
          <p class="card__author">М. Михайловских</p>
        </div>
        <div class="card__content">
          <img
            src="./images/javascript-course.png"
            alt=""
            class="card__img"
            decoding="async"
          >
          <span class="card__description">
            Курс подойдёт для любых чайников: электрических, газовых
            и даже для кастрюлек, временно подменяющих сломанный чайник.
          </span>
        </div>
        <div class="card__footer">
          <span>30 ноября 2023</span>
        </div>
      </div>
    </div>
  </div>
  <div class="footer">
    <span class="copyright">
      2023. Разработано компанией
      <a class="copyright__link" href="#">«Гарцующий пони»</a>
    </span>
  </div>
</div>
```

### Семантическая вёрстка

В предыдущем примере не использовались семантические элементы и всё свёрстано только на `<div>` и `<span>`. Теперь пример корректной семантической вёрстки:

<iframe title="Семантическая вёрстка" src="demos/good-markup/" height="1210"></iframe>

Посмотрим на исходный код корректной семантической вёрстки:

```html
<header class="header">
  <nav class="nav">
    <a href="#" class="nav__item">Главная</a>
    <a href="#" class="nav__item">Блог</a>
    <a href="#" class="nav__item">Контакты</a>
  </nav>
</header>
<main class="main">
  <h1 class="heading">Курсы компании «Гарцующий пони»</h1>
  <div class="wrapper">
    <article class="card">
      <header class="card__header">
        <h2 class="card__heading">SEO для начинающих</h2>
        <p class="card__author">Иван Иванович</p>
      </header>
      <div class="card__content">
        <img
          src="./images/seo-course.png"
          alt=""
          class="card__img"
          decoding="async"
        >
        <p class="card__description">
          Благодаря этому курсу вы научитесь задавливать конкурентов
          с помощью ссылочной массы, а не качественного контента.
        </p>
      </div>
      <footer class="card__footer">
        <time
          class="card__date"
          datetime="2023-02-13"
        >
          13 февраля 2023
        </time>
      </footer>
    </article>

    <article class="card">
      <header class="card__header">
        <h2 class="card__heading">WordPress разработка</h2>
        <p class="card__author">Ольга Ольгина</p>
      </header>
      <div class="card__content">
        <img
          src="./images/wordpress-course.png"
          alt=""
          class="card__img"
          decoding="async"
        >
        <p class="card__description">
          WordPress — топ за свои деньги. Изучите его,
          чтобы стать востребованным фрилансером.
        </p>
      </div>
      <footer class="card__footer">
        <time
          class="card__date"
          datetime="2023-10-23"
        >
          23 октября 2023
        </time>
      </footer>
    </article>

    <article class="card">
      <header class="card__header">
        <h2 class="card__heading">JavaScript для чайников</h2>
        <p class="card__author">М. Михайловских</p>
      </header>
      <div class="card__content">
        <img
          src="./images/javascript-course.png"
          alt=""
          class="card__img"
          decoding="async"
        >
        <p class="card__description">
          Курс подойдёт для любых чайников: электрических, газовых
          и даже для кастрюлек, временно подменяющих сломанный чайник.
        </p>
      </div>
      <footer class="card__footer">
        <time
          class="card__date"
          datetime="2023-11-30"
        >
          30 ноября 2023
        </time>
      </footer>
    </article>
  </div>
</main>
<footer class="footer">
  <p class="copyright">
    2023. Разработано компанией
    <a class="copyright__link"href="#">«Гарцующий пони»</a>
  </p>
</footer>
```

Теперь используем подходящие по семантическому смыслу теги вместо не имеющих его `<div>` и `<span>`. Шапка, подвал, ссылки, заголовки — всё это размечено так, как должно.