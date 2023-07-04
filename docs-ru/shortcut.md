## Намерение развития

Настройте файл пользовательских переменных как нужно, внедрите файл shortcut.styl, и общая спецификация дизайна `class` будет сгенерирована на основе пользовательских переменных.

## Использование

```stylus
@import "your-variable-file.styl" // Файл пользовательских переменных
@import "~stylus-shortcut/src/shortcut.styl" // Упрощённое создание стиля
```

## Пользовательские переменные

Переменные по умолчанию инициализируются в файле `shortcut.styl` функцией стилей `?=`. Если вам нужно настроить переменные, просто обратитесь к файлу пользовательских переменных перед внесением этого файла, чтобы переопределить соответствующие переменные, и стиль будет сгенерирован в соответствии с вновь определенными переменными.

```stylus
// Шаблоны пользовательских переменных
/**
 * Стиль генерирует префикс, и по умолчанию префикс не добавляется
 * В случае совпадения и противоречия встроенные правила стиля могут иметь префикс
 */
yoz_prefix ?= '';
/**
 * Общие переменные цвета
 * default variable by color
 */
yoz_color ?= {
  primary: #1890ff,
  link: #1890ff,
  success: #52c41a,
  warning: #faad14,
  error: #f5222d,
  heading: rgba(black, 0.85),
  text: rgba(black, 0.65),
  sub_text: rgba(black, 0.45),
  disabled: #c5c8ce,
  border: #e8eaec
};
/**
 * Общие переменные линии
 * default variable by line
 */
yoz_line ?= {
  so1: 1px solid yoz_color.border,
  do1: 1px dotted yoz_color.border,
  da1: 1px dashed yoz_color.border
};
/**
 * Общие переменные скругления
 * default variable by border radius
 */
yoz_radius ?= {
  s: 4px,
  m: 8px,
  l: 20px,
  lr: 20px 0 0 0,
  c: 100%
};
/**
 * Общие переменные тени
 * default variable by shadow
 */
yoz_shadow ?= {
  s: 0 0 2px rgba(0, 0, 0, 0.6),
  m: 0 0 5px rgba(0, 0, 0, 0.6)
};
/**
 * Общие переменные шрифта
 * default variable by font-family
 */
yoz_font_family ?= {
  sans: unquote('-apple-system,BlinkMacSystemFont,Segoe UI,Roboto,Oxygen,Ubuntu,Cantarell,Fira Sans,Droid Sans,Helvetica Neue,sans-serif'),
  serif: unquote('serif')
};
/**
 * Общие переменные размера шрифта и межстрочного интервала
 * default variable by font-size and line-height
 */
yoz_font_size ?= {
  s: 12px 20px,
  m: 14px 22px,
  st: 16px 24px,
  t: 18px 28px,
  lt: 20px 30px
};
/**
 * Общие переменные интервала
 * default variable by spacing
 */
yoz_spacing ?= {
  '5': 5px,
  '10': 10px,
  '20': 20px,
  '30': 30px,
  'a': auto
};
/**
 * Общие переменные сетки
 * default variable by grid system
 */
// Количество пользовательских сеток
yoz_grid_col ?= 24;
// Расстояние между сетками
yoz_grid_gutter ?= {
  s: 10px,
  m: 20px
};
// Отзывчивые границы сетки
yoz_grid_query ?= {
  l: 'max-width: 1200px', // large - Большой экран
  m: 'max-width: 992px', // middle - Монитор. Выше 1000 - это в основном монитор для ПК, тогда используются такие сокращения, как большой, средний и маленький
  t: 'max-width: 768px', // tablets - Планшет
  p: 'max-width: 540px', // phone - Телефон
};
```

Скопируйте изменённый шаблон переменной и укажите его перед файлом shortcut.styl

```stylus
@import "your-variable-file.styl" // Файл пользовательских переменных
@import "~stylus-shortcut/src/shortcut.styl"
```

На него также можно ссылаться глобально в конфигурации `stylusOptions`, чтобы переменные можно было применять непосредственно к нескольким файлам стилей в проекте

> Элементы переменной могут быть установлены свободно по правилу, пользовательские переменные будут покрывать значения по умолчанию

## Часто используемые

- ### Линия `line-{key}_{name}`

  ```stylus
    yoz_line = {
      name: [border-width] [border-style] [border-color],
    };
  ```

  > Генерируется в соответствии с элементами в переменной `yoz_line`, значения по умолчанию можно найти в [пользовательских переменных](#Пользовательские-переменные), а для генерации соответствующих боковых линий предусмотрено следующее соответствие

  | key  | Описание         |
  | :--- | ---------------- |
  | a    | Все стороны      |
  | h    | Левая и права    |
  | v    | Верхняя и нижняя |
  | l    | Левая            |
  | r    | Провая           |
  | t    | Верхняя          |
  | b    | Нижняя           |

  #### Пример

  ```html
  <div id="LineDemo" class="box line-a_so1"></div>
  ```

  <div class="flex-v">
    <div>Установить границы: <span class="text-c_primary text-s_l">.line-<span id="LineDemoValue">a_so1</span></span></div>
    <label><input data-id="LineDemo" data-class="box line-" name="line" value="a_so1" type="radio" /> Сплошная линия по всем сторонам [ line-so1 ] </label>
    <label><input data-id="LineDemo" data-class="box line-" name="line" value="v_do1" type="radio" /> Сплошная линия сверху и снизу [ line-do1_v ] </label>
    <label><input data-id="LineDemo" data-class="box line-" name="line" value="h_do1" type="radio" /> Сплошная линия слева и справа [ line-do1_h ] </label>
    <label><input data-id="LineDemo" data-class="box line-" name="line" value="l_da1" type="radio" /> Пунктирная линия слева [ line-da1_l ] </label>
    <label><input data-id="LineDemo" data-class="box line-" name="line" value="t_da1" type="radio" /> Пунктирная линия сверху [ line-da1_t ] </label>
    <label><input data-id="LineDemo" data-class="box line-" name="line" value="r_da1" type="radio" /> Пунктирная линия справа [ line-da1_r ] </label>
    <label><input data-id="LineDemo" data-class="box line-" name="line" value="b_da1" type="radio" /> Пунктирная линия снизу [ line-da1_b ] </label>
  </div>

- ### Интервал `spac-{key}_{name}`

  ```stylus
    yoz_spacing = {
      name: [spacing],
    };
  ```

  > Генерируется в соответствии с элементами в переменной `yoz_spacing`, значения по умолчанию можно найти в [пользовательских переменных](#Пользовательские-переменные), а для генерации соответствующих полей используется следующее соответствие

  | key  | Описание               |
  | :--- | ---------------------- |
  | mv   | margin сверху и снизу  |
  | mh   | margin слева и справа  |
  | ml   | margin слева           |
  | mr   | margin справа          |
  | mt   | margin сверху          |
  | mb   | margin снизу           |
  | pv   | padding сверху и снизу |
  | ph   | padding слева и справа |
  | pl   | padding слева          |
  | pr   | padding справа         |
  | pt   | padding сверху         |
  | pb   | padding снизу          |

  #### Пример

  ```html
  <div class="clearfix">
    <div class="line-a_so1 spac-mr_10 float-l"><div class="box bg-c_primary spac-m_10">margin</div></div>
    <div class="line-a_so1 spac-mr_10 float-l"><div class="box bg-c_primary spac-mv_10">margin сверху и снизу</div></div>
    <div class="line-a_so1 spac-mr_10 float-l"><div class="box bg-c_primary spac-mh_10">margin слева и справа</div></div>
    <div class="line-a_so1 spac-mr_10 float-l"><div class="box bg-c_primary spac-ml_10">margin слева</div></div>
    <div class="line-a_so1 spac-mr_10 float-l"><div class="box bg-c_primary spac-mr_10">margin справа</div></div>
    <div class="line-a_so1 spac-mr_10 float-l"><div class="box bg-c_primary spac-mt_10">margin сверху</div></div>
    <div class="line-a_so1 spac-mr_10 float-l"><div class="box bg-c_primary spac-mb_10">margin снизу</div></div>
  </div>
  <div class="flex-h flex-jc_sb spac-mt_10">
    <div class="box line-a_so1 spac-p_10">padding</div>
    <div class="box line-a_so1 spac-pv_10">padding сверху и снизу</div>
    <div class="box line-a_so1 spac-ph_10">padding слева и справа</div>
    <div class="box line-a_so1 spac-pl_10">padding слева</div>
    <div class="box line-a_so1 spac-pr_10">padding справа</div>
    <div class="box line-a_so1 spac-pt_10">padding сверху</div>
    <div class="box line-a_so1 spac-pb_10">padding снизу</div>
  </div>
  ```

- ### Закругление `radius-{name}`

  ```stylus
    yoz_radius = {
      name: [radiusValue],
    };
  ```

  > Генерируется в соответствии с элементами в переменной `yoz_radius`, значения по умолчанию можно найти в [пользовательских переменных](#Пользовательские-переменные)

  #### Пример

  ```html
  <div class="flex-h flex-jc_sa">
    <div class="box bg-c_border radius-s"></div>
    <div class="box bg-c_border radius-m"></div>
    <div class="box bg-c_border radius-l"></div>
    <div class="box bg-c_border radius-lr"></div>
    <div class="box bg-c_border radius-c"></div>
  </div>
  ```

- ### Тень `shadow-{name}`

  ```stylus
    yoz_shadow = {
      name: [shadowValue],
    };
  ```

  > Генерируется в соответствии с элементами в переменной `yoz_shadow`, значения по умолчанию можно найти в [пользовательских переменных](#Пользовательские-переменные)

  #### Пример

  ```html
  <div class="flex-h flex-jc_sa">
    <div class="box shadow-s"></div>
    <div class="box shadow-m"></div>
  </div>
  ```

- ### Стиль курсора `curs-{name}`

  #### Пример

  | Название стиля       | Эффект                                                                |
  | :------------------- | :-------------------------------------------------------------------- |
  | `curs-auto`          | <img class="curs-auto" src="/img/cursor-auto.svg"/>                   |
  | `curs-default`       | <img class="curs-default" src="/img/cursor-default.svg"/>             |
  | `curs-pointer`       | <img class="curs-pointer" src="/img/cursor-pointer.svg"/>             |
  | `curs-wait`          | <img class="curs-wait" src="/img/cursor-wait.svg"/>                   |
  | `curs-text`          | <img class="curs-text" src="/img/cursor-text.svg"/>                   |
  | `curs-move`          | <img class="curs-move" src="/img/cursor-move.svg"/>                   |
  | `curs-help`          | <img class="curs-help" src="/img/cursor-help.svg"/>                   |
  | `curs-not-allowed`   | <img class="curs-not-allowed" src="/img/cursor-not-allowed.svg"/>     |
  | `curs-none`          | <div class="curs-none" style="height:20px; width:20px;"></div>        |
  | `curs-context-menu`  | <img class="curs-context-menu" src="/img/cursor-context-menu.svg"/>   |
  | `curs-progress`      | <img class="curs-progress" src="/img/cursor-progress.svg"/>           |
  | `curs-cell`          | <img class="curs-cell" src="/img/cursor-cell.svg"/>                   |
  | `curs-crosshair`     | <img class="curs-crosshair" src="/img/cursor-crosshair.svg"/>         |
  | `curs-vertical-text` | <img class="curs-vertical-text" src="/img/cursor-vertical-text.svg"/> |
  | `curs-alias`         | <img class="curs-alias" src="/img/cursor-alias.svg"/>                 |
  | `curs-copy`          | <img class="curs-copy" src="/img/cursor-copy.svg"/>                   |
  | `curs-no-drop`       | <img class="curs-no-drop" src="/img/cursor-no-drop.svg"/>             |
  | `curs-grab`          | <img class="curs-grab" src="/img/cursor-grab.svg"/>                   |
  | `curs-grabbing`      | <img class="curs-grabbing" src="/img/cursor-grabbing.svg"/>           |
  | `curs-all-scroll`    | <img class="curs-all-scroll" src="/img/cursor-all-scroll.svg"/>       |
  | `curs-col-resize`    | <img class="curs-col-resize" src="/img/cursor-col-resize.svg"/>       |
  | `curs-row-resize`    | <img class="curs-row-resize" src="/img/cursor-row-resize.svg"/>       |
  | `curs-n-resize`      | <img class="curs-n-resize" src="/img/cursor-n-resize.svg"/>           |
  | `curs-e-resize`      | <img class="curs-e-resize" src="/img/cursor-e-resize.svg"/>           |
  | `curs-s-resize`      | <img class="curs-s-resize" src="/img/cursor-s-resize.svg"/>           |
  | `curs-w-resize`      | <img class="curs-w-resize" src="/img/cursor-w-resize.svg"/>           |
  | `curs-ne-resize`     | <img class="curs-ne-resize" src="/img/cursor-ne-resize.svg"/>         |
  | `curs-nw-resize`     | <img class="curs-nw-resize" src="/img/cursor-nw-resize.svg"/>         |
  | `curs-se-resize`     | <img class="curs-se-resize" src="/img/cursor-se-resize.svg"/>         |
  | `curs-sw-resize`     | <img class="curs-sw-resize" src="/img/cursor-sw-resize.svg"/>         |
  | `curs-ew-resize`     | <img class="curs-ew-resize" src="/img/cursor-ew-resize.svg"/>         |
  | `curs-ns-resize`     | <img class="curs-ns-resize" src="/img/cursor-ns-resize.svg"/>         |
  | `curs-nesw-resize`   | <img class="curs-nesw-resize" src="/img/cursor-nesw-resize.svg"/>     |
  | `curs-nwse-resize`   | <img class="curs-nwse-resize" src="/img/cursor-nwse-resize.svg"/>     |
  | `curs-zoom-in`       | <img class="curs-zoom-in" src="/img/cursor-zoom-in.svg"/>             |
  | `curs-zoom-out`      | <img class="curs-zoom-out" src="/img/cursor-zoom-out.svg"/>           |

- ### Float

  - `float-l` на лево
  - `float-r` на право
  - `clearfix` сброс

  #### Пример

  ```html
  <style>
    .float {
      width: 100px;
      height: 100px;
      background: #f2f2f2;
    }
  </style>
  <div class="float float-r spac-mb_10">float справа</div>
  <div class="clearfix">
    <div class="float float-l">float слева</div>
    <div class="float float-r">float справа</div>
  </div>
  ```

## Текст

- ### Шрифт `text-f_{name}`

  ```stylus
  yoz_font_family = {
    name: unquote([font_family]), // unquote — встроенная функция stylus для удаления кавычек
  };
  ```

  > Генерируется в соответствии с элементами в переменной `yoz_font_family`, значения по умолчанию можно найти в [пользовательских переменных](#Пользовательские-переменные)

  #### Пример

  ```html
  <div class="text-f_sans">Шрифт без засечек</div>
  <div class="text-f_serif">Шрифт с засечками</div>
  ```

- ### Цвет текста `text-c_{name}`

  ```stylus
  yoz_color = {
    name: [color]
  };
  ```

  > Генерируется в соответствии с элементами в переменной `yoz_color`, значения по умолчанию можно найти в [пользовательских переменных](#Пользовательские-переменные)

  #### Пример

  ```html
  <div class="text-c_primary">Цвет текста primary</div>
  <div class="text-c_success">Цвет текста success</div>
  <div class="text-c_warning">Цвет текста warning</div>
  <div class="text-c_sub_text h:text-c_success">Цвет текста sub_text</div>
  ```

- ### Размер шрифта и межстрочный интервал `text-s_{name}`

  ```stylus
  yoz_font_size = {
    name: [font-size] [line-height]
  };
  ```

  > Генерируется в соответствии с элементами в переменной `yoz_font_size`, значения по умолчанию можно найти в [пользовательских переменных](#Пользовательские-переменные)

  #### Пример

  ```html
  <div class="text-s_e h:text-s_lt">small - вспомогательный текст</div>
  <div class="text-s_c">middle - весь текст</div>
  <div class="text-s_st">small title - подзаголовок</div>
  <div class="text-s_t">title - заголовок</div>
  <div class="text-s_lt">large title - большой заголовок</div>
  ```

- ### Выравнивание текста `text-a_{key}`

  > Следующие соответствия предоставляются по умолчанию.

  | key  | Значение | Описание        |
  | :--- | -------- | --------------- |
  | l    | left     | Текст слева     |
  | c    | center   | Текст по центру |
  | r    | right    | Текст справа    |
  | j    | justify  | Текст по ширине |

  #### Пример

  ```html
  <div id="textAlignDemo">
    Не плюй в колодец, пригодится воды напиться.<br />
    Без труда не выловишь и рыбку из пруда.<br />
    Не беречь поросли, не видать и дерева.<br />
    Дважды в год лето не бывает.<br />
    Летом не припасешь, зимой не принесешь.<br />
    Не зима знобит, а весна.<br />
    Летом - пыль, зимою снег одолевает.<br />
    Придёт осень, за всё спросит.<br />
    В июне первую ягоду в рот кладут, а вторую домой несут.<br />
    Кто любит земле кланяться - без добычи не останется.<br />
    Не та земля дорога, где медведь живёт, а та, где курица скребёт.<br />
    Пчела хоть и жалит, да мёд даёт.<br />
  </div>
  ```

  <div class="flex-v">
    <div>Выберите выравнивание текста: <span class="text-c_primary text-s_l">.text-a_<span id="textAlignDemoValue">l</span></span></div>
    <label><input data-id="textAlignDemo" data-class="text-a_" name="align" value="l" type="radio" /> текст слева</label>
    <label><input data-id="textAlignDemo" data-class="text-a_" name="align" value="r" type="radio" /> текст справа</label>
    <label><input data-id="textAlignDemo" data-class="text-a_" name="align" value="c" type="radio" /> текст по центру</label>
    <label><input data-id="textAlignDemo" data-class="text-a_" name="align" value="j" type="radio" /> текст по ширине</label>
  </div>

- ### Обрезание текста `text-o_{key}`

  > Следующие соответствия предоставляются по умолчанию.

  | key  | Значение | Описание   |
  | :--- | -------- | ---------- |
  | e    | ellipsis | многоточие |
  | c    | clip     | обрезать   |

  > Соответствующий код

  ```stylus
  overflow: hidden;
  text-overflow: $key;
  white-space: nowrap;
  ```

  #### Пример

  ```html
  <div id="textOverflowDemo" class="text-o_e" style="height: 30px; width: 200px;">
    Не плюй в колодец, пригодится воды напиться. Без труда не выловишь и рыбку из пруда. Не беречь поросли, не видать и дерева. Дважды в год лето не бывает. Летом не припасешь, зимой не принесешь. Не зима знобит, а весна. Летом - пыль, зимою снег одолевает. Придёт осень, за всё спросит. В июне первую ягоду в рот кладут, а вторую домой несут. Кто любит земле кланяться - без добычи не останется. Не та земля дорога, где медведь живёт, а та, где курица скребёт. Пчела хоть и жалит, да мёд даёт.
  </div>
  ```

  <div class="flex-v">
    <div>Выберите способ обрезания: <span class="text-c_primary text-s_l">.text-o_<span id="textOverflowDemoValue">e</span></span></div>
    <label><input data-id="textOverflowDemo" data-class="text-o_" name="overflow" value="e" type="radio" /> ellipsis</label>
    <label><input data-id="textOverflowDemo" data-class="text-o_" name="overflow" value="c" type="radio" /> clip</label>
  </div>

- ### Ужим текста `text-clamp_{1~6}`

  > По умолчанию для строк с 1 по 6 используется опущенный стиль, с учётом совместимости.

  #### Пример

  ```html
  <div id="textClampDemo" class="text-clamp_1">
    Не плюй в колодец, пригодится воды напиться.<br />
    Без труда не выловишь и рыбку из пруда.<br />
    Не беречь поросли, не видать и дерева.<br />
    Дважды в год лето не бывает.<br />
    Летом не припасешь, зимой не принесешь.<br />
    Не зима знобит, а весна.<br />
    Летом - пыль, зимою снег одолевает.<br />
    Придёт осень, за всё спросит.<br />
    В июне первую ягоду в рот кладут, а вторую домой несут.<br />
    Кто любит земле кланяться - без добычи не останется.<br />
    Не та земля дорога, где медведь живёт, а та, где курица скребёт.<br />
    Пчела хоть и жалит, да мёд даёт.<br />
  </div>
  ```

  <div class="flex-v">
    <div>Выберите способ ужима: <span class="text-c_primary text-s_l">.text-clamp_<span id="textClampDemoValue">1</span></span></div>
    <label><input data-id="textClampDemo" data-class="text-clamp_" name="clamp" value="1" type="radio" /> Ужимание после 1 строки</label>
    <label><input data-id="textClampDemo" data-class="text-clamp_" name="clamp" value="2" type="radio" /> Ужимание после 2 строки</label>
    <label><input data-id="textClampDemo" data-class="text-clamp_" name="clamp" value="3" type="radio" /> Ужимание после 3 строки</label>
    <label><input data-id="textClampDemo" data-class="text-clamp_" name="clamp" value="4" type="radio" /> Ужимание после 4 строки</label>
    <label><input data-id="textClampDemo" data-class="text-clamp_" name="clamp" value="5" type="radio" /> Ужимание после 5 строки</label>
    <label><input data-id="textClampDemo" data-class="text-clamp_" name="clamp" value="6" type="radio" /> Ужимание после 6 строки</label>
  </div>

## Фон

- ### Цвет фона `bg-c_{name}`

  ```stylus
  yoz_color = {
    name: [color]
  };
  ```

  > Генерируется в соответствии с элементами в переменной `yoz_color`, значения по умолчанию можно найти в [пользовательских переменных](#Пользовательские-переменные)

  #### Пример

  ```html
  <div class="flex-h flex-jc_sa">
    <div class="box bg-c_primary"></div>
    <div class="box bg-c_success"></div>
    <div class="box bg-c_warning"></div>
    <div class="box bg-c_link"></div>
    <div class="box bg-c_disabled"></div>
  </div>
  ```

- ### Режим заполнения `bg-m_{key}`

  > Следующие соответствия предоставляются по умолчанию.

  | key     | Значение  | Описание                                                                                                                    |
  | :------ | --------- | --------------------------------------------------------------------------------------------------------------------------- |
  | cover   | cover     | Масштабируйте изображение по ширине так, чтобы короткие края изображения были видны полностью, а длинные края были обрезаны |
  | contain | contain   | Масштабируйте изображение по ширине так, чтобы длинная сторона изображения была видна полностью                             |
  | fill    | 100% 100% | Растяните изображение так, чтобы оно заполнило элемент                                                                      |
  | fill_w  | 100% auto | Ширина 100%, высота адаптивная                                                                                              |
  | fill_h  | auto 100% | Высота 100%, ширина адаптивная                                                                                              |

  #### Пример

  ```html
  <div style="background-image: url(./img/bg.png);" id="BgModeDemo" class="box bg-m_cover"></div>
  <div class="spac-mv_20">
    <div>
      Выберите режим заполнения фона: <span class="text-c_primary text-s_l">.bg-m_<span id="BgModeDemoValue">cover</span></span>
    </div>
    <label><input data-id="BgModeDemo" data-class="box bg-m_" name="bgMode" value="cover" type="radio" /> cover</label>
    <label><input data-id="BgModeDemo" data-class="box bg-m_" name="bgMode" value="contain" type="radio" /> contain</label>
    <label><input data-id="BgModeDemo" data-class="box bg-m_" name="bgMode" value="fill" type="radio" /> fill</label>
    <label><input data-id="BgModeDemo" data-class="box bg-m_" name="bgMode" value="fill_w" type="radio" /> fill_w</label>
    <label><input data-id="BgModeDemo" data-class="box bg-m_" name="bgMode" value="fill_h" type="radio" /> fill_h</label>
  </div>
  ```

- ### Режим мозайки `bg-r_{key}`

  > Следующие соответствия предоставляются по умолчанию.

  | key  | Значение  | Описание              |
  | :--- | --------- | --------------------- |
  | no   | no-repeat | Без дублирования      |
  | xy   | repeat    | Оси x и y дублируются |
  | x    | repeat-x  | Ось x дублируется     |
  | y    | repeat-y  | Ось y дублируется     |

  #### Пример

  ```html
  <div style="background-image: url(./img/repeat.jpg);" id="BgRepeatDemo" class="box bg-r_no"></div>
  <div class="spac-mv_20">
    <div>
      Выберите режим мозайки: <span class="text-c_primary text-s_l">.bg-r_<span id="BgRepeatDemoValue">no</span></span>
    </div>
    <label><input data-id="BgRepeatDemo" data-class="box bg-r_" name="bgRepeat" value="no" type="radio" /> no</label>
    <label><input data-id="BgRepeatDemo" data-class="box bg-r_" name="bgRepeat" value="xy" type="radio" /> xy</label>
    <label><input data-id="BgRepeatDemo" data-class="box bg-r_" name="bgRepeat" value="x" type="radio" /> x</label>
    <label><input data-id="BgRepeatDemo" data-class="box bg-r_" name="bgRepeat" value="y" type="radio" /> y</label>
  </div>
  ```

## Flex Box

- ### Установка оси `flex-{key}`

  | key  | Значение       | Описание                   |
  | :--- | -------------- | -------------------------- |
  | h    | row            | Горизонтальное направление |
  | hr   | row-reverse    | Горизонтальная инверсия    |
  | v    | column         | Вертикальное направление   |
  | vr   | column-reverse | Вертикальная инверсия      |

  #### Пример

  ```html
  <div id="FlexDirectionDemo" class="flex-h">
    <div class="box bg-c_border spac-m_10">1</div>
    <div class="box bg-c_border spac-m_10">2</div>
    <div class="box bg-c_border spac-m_10">3</div>
    <div class="box bg-c_border spac-m_10">4</div>
    <div class="box bg-c_border spac-m_10">5</div>
  </div>
  ```

  <div>
    <div>Выберите способ: <span class="text-c_primary text-s_l">.flex-<span id="FlexDirectionDemoValue">h</span></span></div>
    <label><input data-id="FlexDirectionDemo" data-class="flex-" name="flex-" value="h" type="radio" /> flex-h</label>
    <label><input data-id="FlexDirectionDemo" data-class="flex-" name="flex-" value="hr" type="radio" /> flex-hr</label>
    <label><input data-id="FlexDirectionDemo" data-class="flex-" name="flex-" value="v" type="radio" /> flex-v</label>
    <label><input data-id="FlexDirectionDemo" data-class="flex-" name="flex-" value="vr" type="radio" /> flex-vr</label>
  </div>

- ### Выравнивание и расположение `flex-jc_{key}`

  | key  | Значение      | Описание                                                                                                                               |
  | :--- | ------------- | -------------------------------------------------------------------------------------------------------------------------------------- |
  | fs   | flex-start    | Сортировать с начала строки                                                                                                            |
  | c    | center        | По центру                                                                                                                              |
  | fe   | flex-end      | Сортировать с конца строки                                                                                                             |
  | sa   | space-around  | Располагает каждый элемент равномерно, выделяя одинаковое пространство вокруг каждого элемента                                         |
  | sb   | space-between | Расположите каждый элемент равномерно, первый элемент размещается в начальной точке, а последний элемент размещается в конечной точке. |
  | se   | space-evenly  | Располагает каждый элемент равномерно с одинаковым интервалом между каждым элементом                                                   |

  #### Пример

  ```html
  <div id="FlexJustifyContentDemo" class="flex-h flex-jc_fs">
    <div class="box bg-c_border spac-m_10">1</div>
    <div class="box bg-c_border spac-m_10">2</div>
    <div class="box bg-c_border spac-m_10">3</div>
    <div class="box bg-c_border spac-m_10">4</div>
    <div class="box bg-c_border spac-m_10">5</div>
  </div>
  ```

  <div>
    <div>Выберите способ: <span class="text-c_primary text-s_l">.flex-jc_<span id="FlexJustifyContentDemoValue">h</span></span></div>
    <label><input data-id="FlexJustifyContentDemo" data-class="flex-h flex-jc_" name="flexJustifyContent" value="fs" type="radio" /> flex-jc_fs[flex-start]</label>
    <label><input data-id="FlexJustifyContentDemo" data-class="flex-h flex-jc_" name="flexJustifyContent" value="fe" type="radio" /> flex-jc_fe[flex-end]</label>
    <label><input data-id="FlexJustifyContentDemo" data-class="flex-h flex-jc_" name="flexJustifyContent" value="c" type="radio" /> flex-jc_c[center]</label>
    <label><input data-id="FlexJustifyContentDemo" data-class="flex-h flex-jc_" name="flexJustifyContent" value="sa" type="radio" /> flex-jc_sa[space-around]</label>
    <label><input data-id="FlexJustifyContentDemo" data-class="flex-h flex-jc_" name="flexJustifyContent" value="sb" type="radio" /> flex-jc_sb[space-between]</label>
    <label><input data-id="FlexJustifyContentDemo" data-class="flex-h flex-jc_" name="flexJustifyContent" value="se" type="radio" /> flex-jc_se[space-evenly]</label>
  </div>

  - ### Выравнивание и расположение вертикальной оси `flex-ac_{key}`

    > Свойство align-content не действует, если все flex-элементы состоят только из одной строки.

  | key  | Значение      | Описание                                                                                                                               |
  | :--- | ------------- | -------------------------------------------------------------------------------------------------------------------------------------- |
  | fs   | flex-start    | Сортировать с начала строки                                                                                                            |
  | c    | center        | По центру                                                                                                                              |
  | fe   | flex-end      | Сортировать с конца строки                                                                                                             |
  | sa   | space-around  | Располагает каждый элемент равномерно, выделяя одинаковое пространство вокруг каждого элемента                                         |
  | sb   | space-between | Расположите каждый элемент равномерно, первый элемент размещается в начальной точке, а последний элемент размещается в конечной точке. |
  | se   | space-evenly  | Располагает каждый элемент равномерно с одинаковым интервалом между каждым элементом                                                   |

  #### Пример

  ```html
  <div id="FlexAlignContentDemo" class="flex-h flex-w_w flex-ac_fs" style="background:rgba(0,0,0,0.2); height:500px; width:300px;">
    <div class="box bg-c_border spac-m_10">1</div>
    <div class="box bg-c_border spac-m_10">2</div>
    <div class="box bg-c_border spac-m_10">3</div>
    <div class="box bg-c_border spac-m_10">4</div>
    <div class="box bg-c_border spac-m_10">5</div>
  </div>
  ```

  <div class="flex-v">
    <div>Выравнивание и расположение вертикальной оси: <span class="text-c_primary text-s_l">.flex-ac_<span id="FlexAlignContentDemoValue">fs</span></span></div>
    <label><input data-id="FlexAlignContentDemo" data-class="flex-h flex-w_w flex-ac_" name="flexAlignContent" value="fs" type="radio" /> flex-ac_fs[flex-start]</label>
    <label><input data-id="FlexAlignContentDemo" data-class="flex-h flex-w_w flex-ac_" name="flexAlignContent" value="fe" type="radio" /> flex-ac_fe[flex-end]</label>
    <label><input data-id="FlexAlignContentDemo" data-class="flex-h flex-w_w flex-ac_" name="flexAlignContent" value="c" type="radio" /> flex-ac_c[center]</label>
    <label><input data-id="FlexAlignContentDemo" data-class="flex-h flex-w_w flex-ac_" name="flexAlignContent" value="sa" type="radio" /> flex-ac_sa[space-around]</label>
    <label><input data-id="FlexAlignContentDemo" data-class="flex-h flex-w_w flex-ac_" name="flexAlignContent" value="sb" type="radio" /> flex-ac_sb[space-between]</label>
    <label><input data-id="FlexAlignContentDemo" data-class="flex-h flex-w_w flex-ac_" name="flexAlignContent" value="se" type="radio" /> flex-ac_se[space-evenly]</label>
  </div>

- ### Выравнивание вертикальной оси `flex-ai_{key}`

  | key  | Значение   | Описание                                                                                       |
  | :--- | ---------- | ---------------------------------------------------------------------------------------------- |
  | fs   | flex-start | Сортировать с начала строки                                                                    |
  | c    | center     | По центру                                                                                      |
  | fe   | flex-end   | Сортировать с конца строки                                                                     |
  | st   | stretch    | Располагает каждый элемент равномерно, выделяя одинаковое пространство вокруг каждого элемента |

  #### Пример

  ```html
  <div id="FlexAliginItemsDemo" class="flex-h">
    <div style="min-height:100px; height:auto;" class="box bg-c_border spac-mr_10 spac-mb_10">1</div>
    <div style="min-height:120px; height:auto;" class="box bg-c_border spac-mr_10 spac-mb_10">2</div>
    <div style="min-height:150px; height:auto;" class="box bg-c_border spac-mr_10 spac-mb_10">3</div>
    <div style="min-height:160px; height:auto;" class="box bg-c_border spac-mr_10 spac-mb_10">4</div>
    <div style="min-height:100px; height:auto;" class="box bg-c_border spac-mr_10 spac-mb_10">5</div>
  </div>
  ```

  <div class="flex-v">
    <div>Выравнивание вертикальной оси: <span class="text-c_primary text-s_l">.flex-ai_<span id="FlexAliginItemsDemoValue">st</span></span></div>
    <label><input data-id="FlexAliginItemsDemo" data-class="flex-h flex-ai_" name="flexAlignItems" value="st" type="radio" /> flex-ai_st[stretch]</label>
    <label><input data-id="FlexAliginItemsDemo" data-class="flex-h flex-ai_" name="flexAlignItems" value="fs" type="radio" /> flex-ai_s[flex-start]</label>
    <label><input data-id="FlexAliginItemsDemo" data-class="flex-h flex-ai_" name="flexAlignItems" value="fe" type="radio" /> flex-ai_e[flex-end]</label>
    <label><input data-id="FlexAliginItemsDemo" data-class="flex-h flex-ai_" name="flexAlignItems" value="c" type="radio" /> flex-ai_c[center]</label>
  </div>

- ### Выравнивание вертикальной дочерней главной оси `flex-as_{key}`

  | key  | Значение   | Описание                                                                                       |
  | :--- | ---------- | ---------------------------------------------------------------------------------------------- |
  | fs   | flex-start | Сортровать с начала строки                                                                     |
  | c    | center     | По центру                                                                                      |
  | fe   | flex-end   | Сортировать с конца строки                                                                     |
  | st   | stretch    | Располагает каждый элемент равномерно, выделяя одинаковое пространство вокруг каждого элемента |

  #### Пример

  ```html
  <div class="flex-h flex-ai_s">
    <div id="FlexAliginSelfDemo" style="min-height:100px; height:auto;" class="box bg-c_primary spac-mr_10 spac-mb_10">1</div>
    <div style="min-height:120px; height:auto;" class="box bg-c_border spac-mr_10 spac-mb_10">2</div>
    <div style="min-height:150px; height:auto;" class="box bg-c_border spac-mr_10 spac-mb_10">3</div>
    <div style="min-height:160px; height:auto;" class="box bg-c_border spac-mr_10 spac-mb_10">4</div>
    <div style="min-height:100px; height:auto;" class="box bg-c_border spac-mr_10 spac-mb_10">5</div>
  </div>
  ```

  <div class="flex-v">
    <div>Выравнивание вертикальной дочерней главной оси: <span class="text-c_primary text-s_l">.flex-ai_<span id="FlexAliginSelfDemoValue">st</span></span></div>
    <label><input data-id="FlexAliginSelfDemo" data-class="box bg-c_primary spac-mr_10 spac-mb_10 flex-as_" name="flexAlignItems" value="st" type="radio" /> flex-as_st[stretch]</label>
    <label><input data-id="FlexAliginSelfDemo" data-class="box bg-c_primary spac-mr_10 spac-mb_10 flex-as_" name="flexAlignItems" value="fs" type="radio" /> flex-as_s[flex-start]</label>
    <label><input data-id="FlexAliginSelfDemo" data-class="box bg-c_primary spac-mr_10 spac-mb_10 flex-as_" name="flexAlignItems" value="fe" type="radio" /> flex-as_e[flex-end]</label>
    <label><input data-id="FlexAliginSelfDemo" data-class="box bg-c_primary spac-mr_10 spac-mb_10 flex-as_" name="flexAlignItems" value="c" type="radio" /> flex-as_c[center]</label>
  </div>

- ### Сворачивание `flex-w_{key}`

  | key   | Значение     | Описание               |
  | :---- | ------------ | ---------------------- |
  | n     | nowrap       | Без разрыва строки     |
  | w     | wrap         | Разрыв строки          |
  | w_rtl | wrap-reverse | Обратный разрыв строки |

  #### Пример

  ```html
  <div id="flexWrapDemo" class="bg-c_sub_text flex-h">
    <div class="box bg-c_border spac-m_10">1</div>
    <div class="box bg-c_border spac-m_10">2</div>
    <div class="box bg-c_border spac-m_10">3</div>
    <div class="box bg-c_border spac-m_10">4</div>
    <div class="box bg-c_border spac-m_10">5</div>
    <div class="box bg-c_border spac-m_10">6</div>
    <div class="box bg-c_border spac-m_10">7</div>
    <div class="box bg-c_border spac-m_10">8</div>
    <div class="box bg-c_border spac-m_10">9</div>
    <div class="box bg-c_border spac-m_10">10</div>
    <div class="box bg-c_border spac-m_10">11</div>
    <div class="box bg-c_border spac-m_10">12</div>
    <div class="box bg-c_border spac-m_10">13</div>
    <div class="box bg-c_border spac-m_10">14</div>
    <div class="box bg-c_border spac-m_10">15</div>
  </div>
  ```

  <div class="flex-v">
    <div>Выберите разрыв строки контейнера: <span class="text-c_primary text-s_l">.flex-w_<span id="flexWrapDemoValue">n</span></span></div>
    <label><input data-id="flexWrapDemo" data-class="bg-c_sub_text flex-h flex-w_" name="flexWrap" value="n" type="radio" /> flex-w_n[nowrap]</label>
    <label><input data-id="flexWrapDemo" data-class="bg-c_sub_text flex-h flex-w_" name="flexWrap" value="w" type="radio" /> flex-w_w[wrap]</label>
    <label><input data-id="flexWrapDemo" data-class="bg-c_sub_text flex-h flex-w_" name="flexWrap" value="w_rtl" type="radio" /> flex-w_w_rtl[wrap-reverse]</label>
  </div>

- ### Заполнение `flex-fill`

  #### Пример

  ```html
  <div class="flex-h">
    <div class="box bg-c_border spac-mr_10 flex-fill">Заполнение</div>
    <div class="box bg-c_border"></div>
  </div>
  ```

## Анимация при наведении

- ### Анимация наведения `tran-{key}`

  | key    | Значение                                            |
  | :----- | --------------------------------------------------- |
  | all    | all                                                 |
  | colors | background-color, border-color, color, fill, stroke |
  | shadow | box-shadow                                          |

  <!--   | opacity                                             | opacity   | -->
  <!--   | transform                                           | transform | -->

  ```stylus
  .tran-all{
    transition-property: all;
    transition-timing-function: ease-in-out;
    transition-duration: 150ms;
  }
  ```

  #### Пример

  ```html
  <div id="tranDemo" class="box bg-c_success h:bg-c_warning tran-colors"></div>
  ```

- ### Время перехода `tran-f_{key}`

  | key  | Значение   |
  | :--- | ---------- |
  | l    | linear     |
  | ei   | ease-in    |
  | eo   | ease-out   |
  | eio  | ease-in-ou |

  #### Пример

  ```html
  <div id="tranTimeFunctionDemo" class="flex-h flex-jc_sb">
    <div class="box bg-c_success h:bg-c_warning tran-colors tran-f_l tran-t_1000">linear</div>
    <div class="box bg-c_success h:bg-c_warning tran-colors tran-f_ei tran-t_1000">ease-in</div>
    <div class="box bg-c_success h:bg-c_warning tran-colors tran-f_eo tran-t_1000">ease-out</div>
    <div class="box bg-c_success h:bg-c_warning tran-colors tran-f_eio tran-t_1000">ease-in-out</div>
  </div>
  ```

- ### Длительность перехода `tran-t_{key}`

  | key  | Значение |
  | :--- | -------- |
  | 200  | 200ms    |
  | 300  | 300ms    |
  | 500  | 500ms    |
  | 700  | 700ms    |
  | 1000 | 1000ms   |
  | 2000 | 2000ms   |

  #### Пример

  ```html
  <div id="tranTimeDemo" class="flex-h flex-jc_sb">
    <div class="box bg-c_success h:bg-c_warning tran-colors tran-t_200">200ms</div>
    <div class="box bg-c_success h:bg-c_warning tran-colors tran-t_300">300ms</div>
    <div class="box bg-c_success h:bg-c_warning tran-colors tran-t_500">500ms</div>
    <div class="box bg-c_success h:bg-c_warning tran-colors tran-t_700">700ms</div>
    <div class="box bg-c_success h:bg-c_warning tran-colors tran-t_1000">1000ms</div>
    <div class="box bg-c_success h:bg-c_warning tran-colors tran-t_2000">2000ms</div>
  </div>
  ```

- ### Время задержки перехода `tran-d_{key}`

  | key  | Значение |
  | :--- | -------- |
  | 200  | 200ms    |
  | 300  | 300ms    |
  | 500  | 500ms    |
  | 700  | 700ms    |
  | 1000 | 1000ms   |
  | 2000 | 2000ms   |

  #### Пример

  ```html
  <div id="tranDelayDemo" class="flex-h flex-jc_sb">
    <div class="box bg-c_success h:bg-c_warning tran-colors tran-d_200">200ms</div>
    <div class="box bg-c_success h:bg-c_warning tran-colors tran-d_300">300ms</div>
    <div class="box bg-c_success h:bg-c_warning tran-colors tran-d_500">500ms</div>
    <div class="box bg-c_success h:bg-c_warning tran-colors tran-d_700">700ms</div>
    <div class="box bg-c_success h:bg-c_warning tran-colors tran-d_1000">1000ms</div>
    <div class="box bg-c_success h:bg-c_warning tran-colors tran-d_2000">2000ms</div>
  </div>
  ```

## Система сетки

- ### Реализация системы сетки `row[-flex]`

  > Система сетки через float или flexbox

  #### Пример

  ```html
  <div>float реализует grid <b class="text-c_primary">.row</b></div>
  <div class="row gutter-s">
    <div class="col-6 bg-c_border">.col-6</div>
    <div class="col-6 bg-c_border">.col-6</div>
    <div class="col-ml_6 col-6 col-g bg-c_border">.col-6.col-ml_6</div>
    <!-- <div class="col-ml_2 bg-c_border">Эластичное заполнение</div> -->
  </div>
  <div class="spac-mt_20">flex реализует grid <b class="text-c_primary">.row-flex</b></div>
  <div class="row-flex gutter-s">
    <div class="col-6 bg-c_border">.col-6</div>
    <div class="col-ml_6 col-6 col-g bg-c_border">.col-6.col-ml_6</div>
    <div class="col-6 bg-c_border">.col-6</div>
  </div>
  ```

- ### Расстояние внутри сетки `gutter-{name}`

  ```stylus
    yoz_grid_gutter = {
      name: [gutter],
    };
  ```

  > 根据变量`yoz_grid_gutter`中成员生成，默认值可查看 [自定义变量](#自定义变量)

  #### Пример

  ```html
  <div>[s] интервал, заданный переменной <b class="text-c_primary">.gutter-s</b></div>
  <div class="row gutter-s line-a_so1 spac-pv_10">
    <div class="col-6"><div class="line-a_so1">.col-6</div></div>
    <div class="col-6"><div class="line-a_so1">.col-6</div></div>
    <div class="col-6"><div class="line-a_so1">.col-6</div></div>
    <div class="col-6"><div class="line-a_so1">.col-6</div></div>
  </div>
  <div class="spac-mt_20">[m] интервал, заданный переменной <b class="text-c_primary">.gutter-m</b></div>
  <div class="row gutter-m line-a_so1 spac-pv_10">
    <div class="col-6"><div class="line-a_so1">.col-6</div></div>
    <div class="col-6"><div class="line-a_so1">.col-6</div></div>
    <div class="col-6"><div class="line-a_so1">.col-6</div></div>
    <div class="col-6"><div class="line-a_so1">.col-6</div></div>
  </div>
  ```

- ### Блок сетки `col-{0~num}`

  ```stylus
      yoz_grid_col = [num];//数字，默认24

  ```

  > 根据变量`yoz_grid_col`分割，默认值可查看 [自定义变量](#自定义变量)

  #### Пример

  ```html
  <div class="row line-a_so1 spac-p_10">
    <div class="col-0"><div class="line-a_so1">.col-0</div></div>
    <div class="col-2"><div class="line-a_so1">.col-2</div></div>
    <div class="col-4"><div class="line-a_so1">.col-4</div></div>
    <div class="col-6"><div class="line-a_so1">.col-6</div></div>
    <div class="col-12"><div class="line-a_so1">.col-12</div></div>
  </div>
  ```

- ### Смещение блока сетки `col-{ml|mr}_{0~num}`

  | key  | Описание        |
  | :--- | --------------- |
  | ml   | Смещение влево  |
  | mr   | Смещение вправо |

  #### Пример

  ```html
  <div class="row line-a_so1 spac-p_10">
    <div class="col-0"><div class="line-a_so1">.col-0</div></div>
    <div class="col-4"><div class="line-a_so1">.col-4</div></div>
    <div class="col-2"><div class="line-a_so1">.col-2</div></div>
    <div class="col-4"><div class="line-a_so1">.col-4</div></div>
    <div class="col-10 col-ml_4"><div class="line-a_so1">.col-10.col-ml_4</div></div>
    <div class="col-6 col-mr_6"><div class="line-a_so1">.col-12.col-mr_2</div></div>
    <div class="col-12"><div class="line-a_so1">.col-12</div></div>
  </div>
  ```

- ### Отзывчивый блок сетки

  - `col-{media}-{0~num}`
  - `col-{media}-[ml|mr]_{0~num}`

  ```stylus
    yoz_grid_query = { // Поскольку порядок генерации влияет на приоритет отзывчивых правил, они должны быть упорядочены по ширине экрана от наибольшего к наименьшему, с наименьшим значением, применяющим max-width
      media: 'min-width: [screenWidth]',
      media: 'max-width: [screenWidth]',
    };
  ```

  | key  | Значение          | Описание        |
  | :--- | ----------------- | --------------- |
  | l    | max-width: 1200px | Большой экран   |
  | m    | max-width: 992px  | Небольшой экран |
  | t    | max-width: 768px  | Планшет         |
  | p    | max-width: 540px  | Телефон         |

  > 根据变量`yoz_grid_query`分割，默认值可查看 [自定义变量](#自定义变量)

  #### Пример

  ```html
  <div class="row gutter-s">
    <div class="col-p-24 col-t-0 col-0"><div class="line-a_so1 text-clamp_1">.col-p-24.col-t-0.col-0</div></div>
    <div class="col-p-12 col-p-ml_12 col-t-24 col-2"><div class="line-a_so1 text-clamp_1">.col-p-12.col-p-ml_12.col-t-24.col-2</div></div>
    <div class="col-p-12 col-p-mr_12 col-t-24 col-4"><div class="line-a_so1 text-clamp_1">.col-p-12.col-p-mr_12.col-t-24.col-4</div></div>
    <div class="col-p-24 col-t-12 col-6"><div class="line-a_so1 text-clamp_1">.col-p-24.col-t-12.col-6</div></div>
    <div class="col-p-24 col-t-12 col-12"><div class="line-a_so1 text-clamp_1">.col-p-24.col-t-12.col-12</div></div>
  </div>
  ```

  <div class="row">
    <div id="GridMediaDemo" class="col-24">
      <iframe style="height: 200px" src="./media.html"></iframe>
    </div>
  </div>

  <div class="flex-v">
    <label><input data-id="GridMediaDemo" data-class="col-" name="gridMedia" value="24" type="radio" /> Компьютер</label>
    <label><input data-id="GridMediaDemo" data-class="col-" name="gridMedia" value="12" type="radio" /> Планшет</label>
    <label><input data-id="GridMediaDemo" data-class="col-" name="gridMedia" value="8" type="radio" /> Телефон</label>
  </div>
