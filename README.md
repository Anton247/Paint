# Paint
------------
Автор - Я
Контактная информация - [ВК](http://vk.com/kondratov_anton "ВК")
Используемые технологии: HTML, CSS, JS
Посмотреть проект можно по ссылке - [https://anton247.github.io/Paint/](https://anton247.github.io/Paint/ "https://anton247.github.io/Paint/")

#Описание
------------
Сайт - Paint, созданный на занятиях в Кванториуме. Сайт создавался с мая по июнь
Возможности Paint-а:
- рисование
- выбор цвета кисти
- выбор толщины кисти
- выбор цвета фона
- полная очистка поля
- сохранение нарисованной картинки в виде jpeg файла
- смена цвета фона независимо от рисунка

![Окно с сайтом](адрес "Окно с сайтом")

Цвет кисти и цвет фона регулируются с помощью:
```html
<input type="color" id="color" value="#ffffff">
```
```html
<input type="color" id="background" value="#000000">
```

![Картинка с примером выбора цветов](Картинка с примером выбора цветов "Картинка с примером выбора цветов")

В блоке **Сейчас выбран инструмент** отображается текущий инструмент для рисования. Всего их два: кисточка и ластик

![Картинка для инструментов](Картинка для инструментов "Картинка для инструментов")

Ниже присутствует ползунок выбора толщины кисточки
```html
 <input type="range" id="size" min="5" max="100" step="1" value="50">
```
![Картинка с толщиной](Картинка с толщиной "Картинка с толщиной")

При нажатии на ссылку
```html
<a download="myImage.jpg" id="save_image">Сохранить картинку</a>
```

Вызывается функция в JavaScript
```javascript
//сохранение холстов в виде картинки
document.getElementById("save_image").onclick = function(){
    let cnv_save = document.getElementById("save_canvas");
    let ctx_save = cnv_save.getContext("2d");
    cnv_save.width = displayWidth;
    cnv_save.height = displayHeight;
    //переносим на холст сохранения холст заднего фона
    ctx_save.drawImage(cnv_bg, 0, 0, cnv.width, cnv.height);
    //переносим на холст сохранения холст рисования
    ctx_save.drawImage(cnv, 0, 0, cnv.width, cnv.height);
    let image = cnv_save.toDataURL("image/jpg");
    this.href = image;
}
```
которая объединяет холсты с фоном и рисунком в один холст, который сохраняется как jpeg файл

![Картинка с сохранением](Картинка с сохранением "Картинка с сохранением")
