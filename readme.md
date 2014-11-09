# GifLinks

Простая javascript библиотека для добавления полноэкранных gif как hover-эффектов. Это очень серьезно, [вот демо](http://tholman.com/giflinks)! Можно также поиграть с исходным кодом [вживую на CodePen](http://codepen.io/tholman/pen/gJBdi).

### Инструкции

GifLinks это самостоятельная библиотека (никаких jquery, и тому подобного) так что использование довольно прямолинейно. Вся стилизация элементов в руках пользователей, `GifLinks.js` только управляет созданием, стилизацией и управлением gif-попапом, предоставляя несколько css-классов для кастомной стилизации.

#### HTML

Есть не так много ограничений на то, какие 'html'-элементы можно использовать для GifLinks, единственно необходимым является атрибут `data-src`, который должен указывать на gif/image, который вы хотите показать на hover-е.

```html
<a href="awesome.html" data-src="./img/awesome.gif"> Ты только посмотри на это! </a>

<!-- Можно использовать любой элемент, серьезно -->

<span class="anything" data-src="./img/amazing.gif" /> Бабах! </span>
```

#### JS

Чтобы начать использовать GifLinks.js, просто передайте элемент в функцию ```Giflinks```, когда они отрендерятся. Это можно сделать с `document.querySelector`, выбирая элементы как вам нравится.

```html
<a href="awesome.html" data-src="./img/awesome.gif"> Посмотри сюда! </a>

<script>
window.onload = function() {
	// Добавим GifLink-и ко всем якорям на странице!
    var element = document.querySelector( 'a' );
	GifLinks( element );
}
</script>
```

Или несколько за один раз через имя класса.

```html
<a class="giflink-to-be" href="awesome.html" data-src="./img/awesome.gif"> Посмотри сюда! </a>
<a class="giflink-to-be" href="incredible.html" data-src="./img/incredible.gif"> Просто Изумительно! </a>

<script>
window.onload = function() {
	// Перевести все картинки в Giflink-и с классом 'giflink-to-be'.
    var elements = document.querySelectorAll( '.giflink-to-be' );
	GifLinks( elements );
}
</script>
```

Также можно передать флаг для прелоада картинки. В таком случае giflinks будут активны как только загрузка завершится!

```html
<a href="awesome.html" data-src="./img/awesome.gif"> Посмотри сюда! </a>

<script>
window.onload = function() {
	// Добавим GifLink-и ко всем а-тэгам на странице и попросим либу сделать пре-лоад!
    var element = document.querySelector( 'a' );
	GifLinks( element, { preload: true } );
}
</script>
```

#### CSS
Есть несколько мелких вещей, с которыми можно играть с css.

У всех активных giflink есть классы `ready` и `giflink`. А если в элементе есть активная ссылка, также добавятся `has-link` и `no-link`.

Также, если вы пользуетесь прелоадом, giflink-и получат класс `preloaded`, который можно использовать, чтобы показать, что ссылка доступна, например так:

```css
.giflink.preloaded {
	transition: color 300ms;
	color: #ff0000;
}
```

### Лицензия

The MIT License (MIT)

Copyright (C) 2014 ~ [Tim Holman](http://tholman.com) ~ timothy.w.holman@gmail.com
