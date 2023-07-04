> Конфигурация stylus вводится глобально, что сокращает процесс стилизации, общие атрибуты стилей, такие как ширина, часто устанавливаются одновременно с высотой, цветом фона и цветом текста и т.д. Чтобы уменьшить объем кодирования и повысить эффективность работы. <p> Классифицируйте методы по применению: верстка (l-), текст (t-), стиль (s-), анимация (a-)</p>

## Как использовать

```stylus
@import "stylus-shortcut"
```

Как и в примере конфигурации vue-cli@3, настройте импорт для глобального внедрения в stylus-loader

```javascript
//vue.config.js
modules.export={
  ...
  css: {
    // Настройка модуля css
    loaderOptions: {
      // Передать параметры конфигурации загрузчику препроцессора
      stylus: {
        stylusOptions:{
          import: ["stylus-shortcut/src/mixin.styl"]
        }
      }
    }
  }
  ...
}
```

## Макет

- ### l-wh(width, height, round)

  > Установка ширины и высоты

  | Название | Формат значения | Доступность | По умолчанию |
  | :------- | :-------------- | :---------- | :----------- |
  | width    | unit            | Нет         |              |
  | height   | unit            | Да          | width        |
  | radius   | unit            | Да          | 0            |

  Пример:

  ```stylus
  .style {
    l-wh: 50px 30px 10px;
  }
  ```

  Результат:

  ```css
  .style {
    width: 50px;
    height: 30px;
    border-radius: 10px;
  }
  ```

- ### l-flex(direction, justify-content, align-items, wrap)

  > Быстрая установка основной оси flex-box, распределение основной оси, выравнивание вертикальной оси и сворачивание вышедшего за пределы; Значения атрибутов flex-direction, justify-content и align-items относительно длинные и их трудно запомнить, поэтому их можно легко применить, сократив.

  | Название        | Значение                                     | Доступность | По умолчанию |
  | :-------------- | :------------------------------------------- | :---------- | :----------- |
  | direction       | flex-direction - Соответствующее сокращение  | Нет         |              |
  | justify-content | justify-content - Соответствующее сокращение | Да          | fs           |
  | align-items     | align-items - Соответствующее сокращение     | Да          | s            |
  | wrap            | flex-wrap                                    | Да          | nowrap       |

  - **Сокращения flex-direction**

    > Идеи сокращения: h горизонтальное ； v вертикальное；r реверс

    | Сокращение | Значение       |
    | :--------- | :------------- |
    | h          | row            |
    | hr         | row-reverse    |
    | v          | column         |
    | vr         | column-reverse |

  - **Сокращения justify-content**

    > Идея сокращений: Начальная буква слова, а союз представляет собой сочетание первой буквы всех союзов

    | Сокращение | Значение      |
    | :--------- | :------------ |
    | fs         | flex-start    |
    | c          | center        |
    | fe         | flex-end      |
    | sa         | space-around  |
    | se         | space-evenly  |
    | sb         | space-between |

  - **Сокращения align-items**

    > Идея сокращений: Начальная буква слова, а союз представляет собой сочетание первой буквы всех союзов

    | Сокращение | Значение   |
    | :--------- | :--------- |
    | fs         | flex-start |
    | c          | center     |
    | fe         | flex-end   |
    | st         | stretch    |

  Пример:

  ```stylus
  .style {
    l-flex: h sb c wrap
  }
  ```

  Результат:

  ```css
  .style {
    flex-direction: row;
    justify-content: space-between;
    align-items: center;
    flex-wrap: wrap;
  }
  ```

- ### Интервал

  - #### l-mh(left, right)

    > Горизонтальный внешний интервал

    Ввод, пример ниже

  - #### l-ph(left, right)

    > Вертикальный внутренний интервал

    | Название | Формат значения | Доступность | По умолчанию |
    | :------- | :-------------- | :---------- | :----------- |
    | left     | unit            | Нет         |              |
    | right    | unit            | Да          | Ввод left    |

    Пример:

    ```stylus
    .style {
      l-mh: 50px 0;
      l-ph: 50px 0;
    }
    .style1 {
      l-mh: 50px;
      l-ph: 50px;
    }
    ```

    Результат:

    ```css
    .style {
      margin-left: 50px;
      margin-right: 0;

      padding-left: 50px;
      padding-right: 0;
    }
    .style1 {
      margin-left: 50px;
      margin-right: 50px;

      padding-left: 50px;
      padding-right: 0;
    }
    ```

  - #### l-mv(top, bottom)

    > Вертикальный внешний интервал

    Ввод, пример ниже

  - #### l-pv(top, bottom)

    > Вертикальный внутренний интервал

    | Название | Формат значения | Доступность | По умолчанию |
    | :------- | :-------------- | :---------- | :----------- |
    | top      | unit            | Нет         |              |
    | bottom   | unit            | Да          | Ввод top     |

    Пример:

    ```stylus
    .style {
      l-mv: 50px 0;
      l-pv: 50px 0;
    }
    .style1 {
      l-mv: 50px;
      l-pv: 50px;
    }
    ```

    Результат:

    ```css
    .style {
      margin-top: 50px;
      margin-bottom: 0;

      padding-top: 50px;
      padding-bottom: 0;
    }
    .style1 {
      margin-top: 50px;
      margin-bottom: 50px;

      padding-top: 50px;
      padding-bottom: 50px;
    }
    ```

- ### Позиционирование

  - #### l-abs(left, top, dir)

    > Быстрая установка абсолютного позиционирования

    Ввод, пример ниже

  - #### l-fix(left, top, dir)

    > Быстрая установка фиксированного позиционирования

    Ввод, пример ниже

  - #### l-rel(left, top, dir)

    > Быстрая установка относительного позиционирования

    Обычно позиционирование осуществляется двумя значениями `x`,`y` для расположения элемента в представлении, поэтому добавление третьего значения `dir` дополняет `x` и `y` относительно четырех углов прямоугольника.

    | Название | Формат значения | Доступность | По умолчанию |
    | :------- | :-------------- | :---------- | :----------- |
    | x        | unit            | Да          | auto         |
    | y        | unit            | Да          | auto         |
    | dir      | lt\|rt\|lb\|rb  | Да          | lt           |

    Пример:

    ```stylus
    .style {
      l-abs: 50px 0 'rb';
    }
    .style1 {
      l-rel: 50px 0 'lb';
    }
    .style2 {
      l-fix: 50px 50px
    }
    ```

    Результат:

    ```css
    .style {
      position: absolute;
      right: 50px;
      bottom: 0;
    }
    .style1 {
      position: relative;
      left: 50px;
      bottom: 0;
    }
    .style2 {
      position: fixed;
      left: 50px;
      top: 50px;
    }
    ```

## Текст

- ### t-fl(size, lineHeight, color/align)

  > Быстрая установка следующих свойств: font-size, line-height, color или text-align

  | Название     | Формат значения  | Доступность | По умолчанию                                |
  | :----------- | :--------------- | :---------- | :------------------------------------------ |
  | size         | unit             | Нет         |                                             |
  | lineHeight   | unit             | Да          | Ввод size                                   |
  | color\|align | rgba\|text-align | Да          | color для color и text-align для text-align |

  Пример:

  ```stylus
  .style {
    t-fl: 50px;
  }
  .style1 {
    t-fl: 50px 60px #333;
  }
  ```

  Результат:

  ```css
  .style {
    font-size: 50px;
    line-height: 50px;
  }
  .style1 {
    font-size: 50px;
    line-height: 60px;
    color: #333;
  }
  ```

- ### t-clamp(lineNum)

  > Для совместимости установите значение lineNum равным 2.

  | Название | Формат значения | Доступность | По умолчанию |
  | :------- | :-------------- | :---------- | :----------- |
  | lineNum  | number          | Нет         |              |

  Пример:

  ```stylus
  .style {
    t-clamp: 1;
  }
  .style1 {
    t-clamp: 3;
  }
  ```

  Результат:

  ```css
  .style {
    text-overflow: ellipsis;
    overflow: hidden;
    white-space: nowrap;
  }
  .style1 {
    overflow: hidden;
    display: -webkit-box;
    -webkit-line-clamp: 3;
    -webkit-box-orient: vertical;
  }
  ```

## Фон

- ### s-bg(bg, size, position, repeat)
  > Быстрая настройка background

| Название | Формат значения                  | Доступность | По умолчанию |
| :------- | :------------------------------- | :---------- | :----------- |
| bg       | Эквивалентно background          | Нет         |              |
| size     | Эквивалентно background-size     | Да          | cover        |
| position | Эквивалентно background-position | Да          | center       |
| repeat   | Эквивалентно background-repaeat  | Да          | no-repeat    |

Пример:

```stylus
.style {
  s-bg: #f2f2f2;
}
.style1 {
  s-bcb: url('image_path');
}
```

Результат:

```css
.style {
  background: #f2f2f2;
  background-size: cover;
  background-position: center;
  background-repeat: no-repeat;
}
.style1 {
  background: url("image_path");
  background-size: cover;
  background-position: center;
  background-repeat: no-repeat;
}
```

## Анимация

- ### a-eff(name, duration, delay)

> Быстрая установка name, duration и delay для анимаций

| Название | Формат значения | Доступность | По умолчанию |
| :------- | :-------------- | :---------- | :----------- |
| name     | string          | Нет         |              |
| duration | time unit       | Нет         |              |
| delay    | time unit       | Да          | 0s           |

Пример ниже

- ### a-loop(count)

  > Быстрая настройка количества воспроизведений анимации и воспроизведение в обратном направлении после завершения.

  | Название  | Формат значения | Доступность | По умолчанию |
  | :-------- | :-------------- | :---------- | :----------- |
  | count     | string          | Да          | infinite     |
  | alternate | boolean         | Да          | false        |

  Пример:

  ```stylus
  .style {
    a-eff: fade 1s .5s;
    a-loop: 2 true;
  }
  ```

  Результат:

  ```css
  .style {
    animation-name: fade;
    animation-duration: 1s;
    animation-delay: 0.5s;

    animation-iteration-count: 2;
    animation-direction: alternate;
  }
  ```
