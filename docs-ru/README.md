# Stylus-Shortcut

Упростите написание стилей! Спецификации дизайна быстро генерируют общие вспомогательные `class`; объединяют и сокращают часто сочетаемые атрибуты.

<!-- Функция stylus mixin позволяет сократить объём кода, который вам приходится писать, объединяя общие комбинации стилей в простое предложение и генерируя общие правила стиля из общих переменных темы через цикл stylus для быстрого доступа. -->

<!-- ## Намерение развития -->

<!-- Первоначальная цель написания этого проекта заключалась в разработке платформы SaaS. Я использовал ElementUI для разработки и использовал некоторые стили и цветовые переменные с помощью пользовательских тем. Часто бывает необходимо назвать некоторые элементы, а затем просто добавить к ним простой стиль, например, атрибут интервала или цвет текста. Переключение между файлами стилей и файлами DOM, а также присвоение имен мелким неважным элементам — это слишком много и раздражает; возможно, именно поэтому Bootstrap стала библиотекой, которую все любят.

Поэтому я просто создал обычные интервалы, шрифты, цвета, границы, флекс и тени по спецификации дизайна с помощью stylus, что было очень удобно; оказалось, что при частом переключении файлов легко забыть, что нужно сделать.
После этого, при написании стилей для некоторых сложных конструкций, часто после написания width, следующим предложением может быть height, и т.д. и т.п., написано много строк, но часто они сопровождаются правилами, позиционирование будет писать left, top, ширина и высота может также установить закругленный угол и т.д. После написания фронтенда в течение нескольких лет я давно устал от длинных правил стиля.
Поэтому я использовал функцию mixin в stylus, чтобы объединить обычные правила написания CSS в одно предложение - небольшая функция, которая может иметь большое значение.
При написании документации я также часто спрашиваю себя, не является ли проект настолько маленьким, что его нужно превратить в библиотеку? Я нашел ответ, маленький и простой - это первоначальный замысел этого проекта, он решает мелкие раздражители, которые часто упускаются из виду при разработке, организация правил для повышения эффективности письма также является самым важным ядром этого небольшого проекта
Если у вас такое же раздражение, как и у меня, попробуйте эту библиотеку~ -->

## Характеристики

- Новый способ объединить сокращения и уменьшить нагрузку при написании стиля
- Уменьшить повторяющееся написание стилей
- Быстро преобразовывать спецификации дизайна в библиотеку стилей
- Следовать соглашению об именовании BEM
- Маленький и простой

## Спецификация проекта

Настройте файл пользовательских переменных как нужно, внедрите файл shortcut.styl, и общая спецификация дизайна `class` будет сгенерирована на основе пользовательских переменных.

```stylus
@import "your-variable-file.styl" // Файл с пользовательскими переменными
@import "~stylus-shortcut/src/shortcut.styl" // Упроощённое создание стиля
```

- ### Спецификация цвета

  ```styl
  yoz_color ?= {
  	primary: #1890ff,
  	success: #52c41a,
  	warning: #faad14,
  	error: #f5222d,
  	heading: rgba(black, 0.85),
  	text: rgba(black, 0.65),
  	sub_text: rgba(black, 0.45),
  	disabled: #c5c8ce,
  	border: #e8eaec
  };
  ```
<div class="row gutter-s">
	<div class="col-4">
		<div class="color-box bg-c_primary"></div>
	</div>
	<div class="col-4">
		<div class="color-box bg-c_success"></div>
	</div>
	<div class="col-4">
		<div class="color-box bg-c_warning"></div>
	</div>
	<div class="col-4">
		<div class="color-box bg-c_error"></div>
	</div>
</div>
<div class="row gutter-s spac-mt_20">
	<div class="col-4">
		<div class="color-box bg-c_heading"></div>
	</div>
	<div class="col-4">
		<div class="color-box bg-c_text"></div>
	</div>
	<div class="col-4">
		<div class="color-box bg-c_sub_text"></div>
	</div>
	<div class="col-4">
		<div class="color-box bg-c_disabled"></div>
	</div>
	<div class="col-4">
		<div class="color-box bg-c_border"></div>
	</div>
</div>

- ### Текст

	```styl
	yoz_font_family ?= {
		sans: unquote('-apple-system,BlinkMacSystemFont,Segoe UI,Roboto,Oxygen,Ubuntu,Cantarell,Fira Sans,Droid Sans,Helvetica Neue,sans-serif'),
		serif: unquote('serif')
	};
	yoz_font_size ?= {
		s: 12px 20px,
		m: 14px 22px,
		b: 16px 24px,
		l: 18px 28px
	};
	```
	- #### Шрифт 
		<div class="text-f_sans">Шрифт без засечек</div>
		<div class="text-f_serif">Шрифт с засечками</div>

	- #### Размер
		<div class="text-s_e">small - Вспомогательный текст</div>
		<div class="text-s_c">middle - Полный текст</div>
		<div class="text-s_st">small title - Подзаголовок</div>
		<div class="text-s_t">title - Заголовок</div>
		<div class="text-s_lt">large title - Большой заголовок</div>

- ### Закругление
	```styl
	yoz_radius ?= {
		s: 4px,
		m: 8px,
		l: 20px,
		lr: 20px 0 0 0,
		c: 100%
	};
	```
<div class="row gutter-s">
	<div class="col-4">
		<div class="color-box bg-c_border radius-s"></div>
	</div>
	<div class="col-4">
		<div class="color-box bg-c_border radius-m"></div>
	</div>
	<div class="col-4">
		<div class="color-box bg-c_border radius-l"></div>
	</div>
	<div class="col-4">
		<div class="color-box bg-c_border radius-lr"></div>
	</div>
	<div class="col-4">
		<div class="color-box bg-c_border radius-c"></div>
	</div>
</div>

- ### Тень
	```styl
	yoz_shadow ?= {
		s: 0 0 2px rgba(0, 0, 0, 0.6),
		m: 0 0 5px rgba(0, 0, 0, 0.6)
	};
	```
<div class="row gutter-s">
	<div class="col-4">
		<div class="color-box bg-c_border shadow-s"></div>
	</div>
	<div class="col-4">
		<div class="color-box bg-c_border shadow-m"></div>
	</div>
</div>