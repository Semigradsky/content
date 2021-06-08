---
title: "display"
tags:
  - doka
authors:
  - solarrust
contributors:
  - skorobaeus
summary:
  - блочная модель
  - block
  - inline-block
  - flex
  - grid
---

## Кратко

По умолчанию все элементы в HTML бывают блочными и строчными. Но в вёрстке часто случаются ситуации, что нам нужно изменить свойства элемента и сделать его не строчным, а блочным. И наоборот.

Тут на помощь приходит свойство `display` ✨

Помимо значений `block` (блочное отображение) и `inline` (строчное отображение) существует смешанное значение `inline-block`.

С развитием CSS кроме трёх перечисленных значений появились ещё `flex`, `grid` и редко используемые специфичные типа `table-cell`.

## Пример

Частая ситуация: на странице нужно отобразить иконки соцсетей со ссылками на аккаунты.

```html
<div class="wrapper">
  <ul class="social">
    <li class="social__item twitter">
      <a href="" class="social__link"></a>
    </li>
    <li class="social__item fb">
      <a href="" class="social__link"></a>
    </li>
    <li class="social__item youtube">
      <a href="" class="social__link"></a>
    </li>
  </ul>
</div>
```

Обрати внимание, что внутри ссылок ничего не написано. Нам не нужно выводить название соцсети, а нужно вывести иконку с логотипом. Что мы и сделаем при помощи фона.

```css
.social__item {
  display: inline-block; /* Выстраиваем пункты списка в ряд, а не друг под другом */
}

.social__link {
  display: block; /* Превращаем ссылки из строчных в блочные элементы */
  width: 30px; /* После этого можем задать высоту и ширину */
  height: 30px;
}

/* Ниже задаём иконки фоном для каждой отдельной ссылки */
.twitter {
  background: url(https://www.pinclipart.com/picdir/middle/20-203122_follow-us-twitter-logo-square-png-clipart.png)
    no-repeat center / contain;
}

.fb {
  background: url(https://cdn3.iconfinder.com/data/icons/social-network-30/512/social-02-512.png)
    no-repeat center / contain;
}

.youtube {
  background: url(http://www.vectorico.com/download/social_media/youtube-red-square.png)
    no-repeat center / contain;
}
```

По умолчанию ссылки являются строчными элементами. Это значит, что мы не можем задать им размеры (ширину и высоту), а также не можем задать фоновую картинку.

Пишем `display: block` и строка превращается в условный _кубик_, у которого могут быть и размеры и фон.

После этого смело меняем размер на нужный нам и фоном выводим иконки каждой из соц.сетей.

Помимо этого по ходу решения задачи мы задали свойство `display: inline-block` для пунктов списка с классом `.social__item`. За счёт этого элементы, которые по умолчанию являются блочными, приобретают внешние признаки строчных элементов. Вместо того, чтобы выстраиваться друг под другом, пункты списка теперь стоят рядом, в строку.

## Как это понять

Слово **display** переводится с английского просто и ожидаемо — показывать.

Значения свойства, которые встречаются в работе чаще всего:

- `none` — полностью скрывает элемент со страницы, не удаляя его при этом из HTML-разметки.
- `block` — элемент ведёт себя как блочный.
- `inline-block` — элемент ведёт себя снаружи как строчный, а внутри как блочный.
- `flex` — элемент становится флекс-контейнером, ведёт себя как блочный, а вложенные элементы становятся флекс-элементами. Подробнее [в гайде по flexbox](/css/flexbox-guide/).
- `grid` — элемент становится грид-контейнером. Снаружи грид-контейнер ведёт себя как блок. Дочерние элементы такого контейнера начинают подчиняться правилам грид-раскладки. Подробнее [в гайде по grid](/css/grid-guide/).

## Как пишется

Пишем имя свойства `display` и после двоеточия через пробел указываем одно из доступных значений при помощи ключевого слова.

Можно указать только одно значение.

Это свойство можно указать для совершенно любого HTML-элемента.

## Подсказки

💡 Свойство `display` нельзя анимировать 😔

💡 Значение по умолчанию отличается у каждого HTML-элемента. Если нет уверенности — загляни в Инструменты разработчика в браузере.