# <a name="up" />Проект Яндекс Метро

Яндекс.Метро — сервис, который позволяет ориентироваться в метро с помощью мобильного устройства. В приложении есть схема метро, которая помогает построить маршрут и оценить время в пути; в приложении появляются актуальные уведомления о работе станций метро и изменениях графика работы. 

## Содержание
- [Задачи тестировщика](#задачи-тестировщика)
- [Требования по проекту](#требования-по-проекту)
- [Инструменты](#инструменты)
- [Планирование тестирования](#планирование-тестирования)
- [Тестовая документация](#тестовая-документация)

## Задачи тестировщика

<details>
<summary> Задачи </summary> 

#### Задачи 

1. Проанализировать требования к мобильному приложению Яндекс.Метро
2. Спроектировать чек-лист для тестирования мобильного приложения на часть требований (для новых фич)
3. Протестировать мобильное приложение в эмуляторе с помощью Android Studio завести баг-репорты 

***

</details>

## Требования по проекту

<details>
<summary>Требования к мобильному приложению Метро </summary>

#### 1. Список маршрутов  

1.1. В карточке маршрута отображается:  
 -информация маршрута — логотипы метро и номера линий метро, также сохраняется последовательность пересадок (если есть);  
 количество пересадок (если есть);  
-временной интервал маршрута — время в пути, время отправления и прибытия;  
кнопка «Закрыть»;  
кнопка «Детали маршрута»;  
поля «Откуда» (начальный пункт) и «Куда» (пункт назначения) (поля должны валидироваться).  

![iScreen Shoter - Safari - 231103172338](https://github.com/SofiiaSleptsova/Yandex_Metro/assets/147629405/abe5f1a7-4098-4e03-8dab-be5cb81da27d)

1.2. Сброс маршрута   
Закрыть маршрут можно только тапом на крестик в карточке маршрута. При закрытии маршрута в поле ввода «Откуда»   сохраняется начальная станция из последнего маршрута. Поле ввода «Куда» и маршрут на схеме сбрасывается, выделение   станций пропадает (кроме начальной станции).  
Если текущее время превышает время окончания маршрута, то временной интервал маршрута обновляется.  

#### 2. Выбор станции  

2.1. Станцию можно выбрать несколькими способами:  
тапом на схеме;  
по иконке i из разных карточек маршрута. Если из поиска выбрать станцию тапом на i и закрыть карточку станции, должен происходить возврат на экран поиска;

![iScreen Shoter - Safari - 231103172437](https://github.com/SofiiaSleptsova/Yandex_Metro/assets/147629405/57a94262-530c-435d-b7c8-f42c33f21a24)

найти в поиске и нажать на станцию.  
2.2. Если станция выбрана, всегда выполняются следующие действия:  
Точка станции на схеме уменьшается.  
На точке станции появляется пин цвета линии или специальный пин для закрытой станции.

![iScreen Shoter - Safari - 231103172511](https://github.com/SofiiaSleptsova/Yandex_Metro/assets/147629405/87c40cbb-ce3f-4457-a7ea-c1e302da30a9)

Выбранная станция сохраняется в истории: при нажатии на поле «Откуда» или «Куда» раскрывается список, содержащий станции, которые пользователь выбирал ранее. Список должен сохраниться и в новой версии приложения.  
Шрифт названия станции становится bold.  

#### 3. Детали маршрута  

3.1. Переход к карточке маршрута  
Детали маршрута открываются двумя способами:  
по тапу на кнопку Деталей маршрута в карточке маршрута;  
по свайпу списка маршрутов вверх (только для смартфонов в портретной ориентации).  
3.2. Отображение  
В карточке маршрута отображается:  
Временной интервал маршрута:   
время в пути;  
время отправления;  
время прибытия;  
отрезки пересадок между участками маршрута.  
Кнопка «Закрыть»  
Участки маршрута, разделённые сообщениями о пересадке  
Сообщение об удобных вагонах для посадки  
Картинка с указанием удобных вагонов  
Станции прибытия и отправления  
Пересадочные станции  
Промежуточные станции (если на участке больше одной промежуточной станции, отображаются свёрнутым списком)  
Рядом с каждой станцией, кроме промежуточных, отображается кнопка i для перехода в карточку станции  
Станция, расположенная в начале каждого участка, содержит название, номер линии и иконку сервиса  
Для каждой станции может отображаться событие  
При смене ориентации с портретной на ландшафтную детали маршрута отображаются в левой части экрана  
3.3. Закрытие карточки маршрута  
Закрыть карточку маршрута можно также двумя способами:  
по тапу на кнопку «Закрыть»;  
свайпом вниз.  
При закрытии деталей остаётся открытым список маршрутов, положение списка сохраняется, построенный маршрут не   сбрасывается.  

#### 4. Уведомление об ошибке:  

При отсутствии интернет-соединения появляется уведомление об ошибке.  

#### 5. Логика для альбомной ориентации  

Карточки маршрута и станции и поля поиска отображаются в левой части экрана.  
Карточки маршрута и станции открываются на всю высоту экрана.  
Карточки станции закрываются при взаимодействии со схемой.  
Маршруты отображаются в списке в левой части экрана.  
Баннер на маршруте отображается сверху списка маршрута, если доступно достаточно места.  
При смене ориентации экрана масштаб построенного маршрута не должен увеличиться или уменьшиться.  
Список маршрутов не сворачивается при тапе на ячейку маршрута. Выбранный маршрут выделяется.  
При построении маршрута маршрут вписывается в свободную область справа.  
При тапе на станцию на схеме (с и без маршрута) происходит минимальный подскролл схемы, чтобы вместить пин.  
При выборе станции по иконке i происходит минимальный подскролл схемы, чтобы вместить пин.  
Карточки маршрута, станции и настроек сохраняют своё положение при переходе из портретной ориентации в ландшафтную (и обратно): свёрнутые остаются свёрнутыми, открытые — открытыми, среднее положение переходит в среднее.  
Карточка Настроек открывается по центру экрана на некоторых девайсах (iPad и некоторые iPhone).  

#### 6. Лонг-тап по станции  

При нажатии на станцию при помощи лонг-тапа открывается карточка станции с кнопками «Отсюда»/«Сюда».  

![iScreen Shoter - Safari - 231103172655](https://github.com/SofiiaSleptsova/Yandex_Metro/assets/147629405/683e4426-6518-471d-981e-ee77ff31c34f)

Схема не должна смещаться вверх/вниз/влево/вправо при лонгтапе по станции.

#### 7. Скролл схемы при помощи лонг-тапа

Чтобы воспроизвести скролл схемы при помощи лонгтапа — сделай лонгтап по станции и, удерживая палец, переводи фокус на другие станции.  
При скролле лонгтапом можно выбрать нужную станцию, при этом схема остаётся неподвижной.  
При попадании на область клика точки станции или её названия, на точку ставится пин, точка станции уменьшается, название станции выделяется жирным шрифтом, появляется карточка станции.  
Пин на станции и выделение станции пропадает, когда она не попадает в зону клика.  
При дальнейшем движении шапка карточки станции остаётся неподвижной, и в ней меняются названия станций и сервисов. При этом карточка станции сохраняет минимальное состояние.
Если движение заканчивается на пустой области, карточка станции закрывается.  

***

</details>

## Инструменты
<p align="left"> 
  <a href="https://docs.google.com/" target="_blank" rel="noreferrer"><img src="https://w7.pngwing.com/pngs/240/1015/png-transparent-g-suite-google-docs-google-angle-rectangle-logo.png" width="36" height="36" alt="Google Sheets" /></a>
  <a href="https://www.jetbrains.com/youtrack/" target="_blank" rel="noreferrer"><img src="https://upload.wikimedia.org/wikipedia/commons/9/95/YouTrack_Icon.png" width="36" height="36" alt="Youtrack" /></a>
  <a href="https://developer.android.com/studio" target="_blank" rel="noreferrer"><img src="https://upload.wikimedia.org/wikipedia/commons/thumb/c/c1/Android_Studio_icon_%282023%29.svg/800px-Android_Studio_icon_%282023%29.svg.png" width="36" height="36" alt="Android_Studio" /></a>
</p> 
