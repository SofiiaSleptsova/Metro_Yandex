# <a name="up" />Проект Яндекс Метро

Яндекс.Метро — сервис, который позволяет ориентироваться в метро с помощью мобильного устройства. В приложении есть схема метро, которая помогает построить маршрут и оценить время в пути; в приложении появляются актуальные уведомления о работе станций метро и изменениях графика работы. 

## Содержание
- [Задачи тестировщика](#задачи-тестировщика)
- [Требования по проекту](#требования-по-проекту)
- [Инструменты](#инструменты)
- [Проектирование тестовой документации](#проектирование-тестовой-документации)
- [Выполнение тестов](#выполнение-тестов)

## Задачи тестировщика

<details>
<summary> Задачи </summary> 

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
-количество пересадок (если есть);  
-временной интервал маршрута — время в пути, время отправления и прибытия;  
-кнопка «Закрыть»;  
-кнопка «Детали маршрута»;  
-поля «Откуда» (начальный пункт) и «Куда» (пункт назначения) (поля должны валидироваться).  

![iScreen Shoter - Safari - 231103172338](https://github.com/SofiiaSleptsova/Yandex_Metro/assets/147629405/abe5f1a7-4098-4e03-8dab-be5cb81da27d)

1.2. Сброс маршрута   
-pакрыть маршрут можно только тапом на крестик в карточке маршрута. При закрытии маршрута в поле ввода «Откуда» сохраняется начальная станция из последнего маршрута. Поле ввода «Куда» и маршрут на схеме сбрасывается, выделение станций пропадает (кроме начальной станции).  
-если текущее время превышает время окончания маршрута, то временной интервал маршрута обновляется.  

#### 2. Выбор станции  

2.1. Станцию можно выбрать несколькими способами:  
-тапом на схеме;  
-по иконке i из разных карточек маршрута. Если из поиска выбрать станцию тапом на i и закрыть карточку станции, должен происходить возврат на экран поиска;

![iScreen Shoter - Safari - 231103172437](https://github.com/SofiiaSleptsova/Yandex_Metro/assets/147629405/57a94262-530c-435d-b7c8-f42c33f21a24)

-найти в поиске и нажать на станцию.  

2.2. Если станция выбрана, всегда выполняются следующие действия:  
-точка станции на схеме уменьшается.  
На точке станции появляется пин цвета линии или специальный пин для закрытой станции.

![iScreen Shoter - Safari - 231103172511](https://github.com/SofiiaSleptsova/Yandex_Metro/assets/147629405/87c40cbb-ce3f-4457-a7ea-c1e302da30a9)

Выбранная станция сохраняется в истории: при нажатии на поле «Откуда» или «Куда» раскрывается список, содержащий станции, которые пользователь выбирал ранее. Список должен сохраниться и в новой версии приложения.  
Шрифт названия станции становится bold.  

#### 3. Детали маршрута  

3.1. Переход к карточке маршрута  
Детали маршрута открываются двумя способами:  
-по тапу на кнопку Деталей маршрута в карточке маршрута;  
-по свайпу списка маршрутов вверх (только для смартфонов в портретной ориентации).  

3.2. Отображение  
В карточке маршрута отображается:  
-временной интервал маршрута:   
-время в пути;  
-время отправления;  
-время прибытия;  
Отрезки пересадок между участками маршрута.  
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

## Процесс работы

### Проектирование тестовой документации

![Чек-лист_ мобильное приложение-2](https://github.com/SofiiaSleptsova/Yandex_Metro/assets/147629405/6427ddfa-2563-45d8-b0b4-e77416e4d3b1)

### Выполнение тестов

[Тестовая документация с кликабельными ссылками на баг-репорты](https://docs.google.com/spreadsheets/d/1y_dVZCaKWYKP17JVRHCYdO9HxVyHSlECJB6-uux_4oA/edit?usp=sharing)

<details>
 <summary> Баг-репорты </summary>

<details>
<summary>ID: 683-95 </summary>

### Если текущее время превышает временной интервал, построенного маршрута, то временной интервал НЕ обновляется автоматически [683-95](https://slepsovasonya.youtrack.cloud/issue/683-95)
 
**Предусловия:**  
1. Открыть приложение "Яндекс.Метро"  
2. Установить город Москва  

**Шаги воспроизведения:**   
1. Нажать на схеме станцию "Марьино"  
2. В карточке станции "Марьино" кликнуть по кнопке "Отсюда"  
3. Нажать на схеме станцию "Братиславская"  
4. В карточке станции "Братиславская" кликнуть по кнопке "Сюда"  

**Ожидаемый результат:**  
При изменении текущего времени и превышении времени окончания маршрута - в карточке маршрута интервал времени обновляется  
**Фактический результат:**     
При изменении текущего времени и превышении времени окончания маршрута - в карточке маршрута интервал времени НЕ обновился  
[видео](https://slepsovasonya.youtrack.cloud/api/files/8-32?sign=MTY5OTQwMTYwMDAwMHwxLTF8OC0zMnxVUXJubDF4STc4ZlZGNV9IY3pYeXNKVDRvVV9GdDlHc3U5%0D%0AZ3piQWgwN0FrDQo%0D%0A&updated=1693222490648)

**Приоритет:**   
Серьезная  

**Окружение:** 
macOS  | 12.6.6  
Android Studio Giraffe | 2022.3.1  
Galaxy  | 6S (разрешение экрана 1080 х 1920)  
Яндекс.Метро | 3.6.  
***
</details>

<details>
<summary>ID: 683-1 </summary>

### Нажатие иконки "крестик" в карточке станции, возвращает в основной интерфейс [683-1](https://slepsovasonya.youtrack.cloud/issue/683-1/Nazhatie-ikonki-krestik-v-kartochke-stancii-vozvrashaet-v-osnovnoj-interfejs)
 
**Предусловия:**  
1. Открыть приложение "Яндекс.Метро"  
2. Установить город Москва  

**Шаги воспроизведения:**   
1. Нажать на поле ввода "Откуда"    
2. Ввести название станции  
3. Нажать на иконку "i", в нераскрытой карточке станции  
4. Нажать на иконку "крестик"  

**Ожидаемый результат:**   
При закрытии карточки станции, который открыт иконкой "i" из панели поиска, иконкой "крестик", должен происходить возврат на панель поиска  
**Фактический результат:**     
При закрытии карточки станции иконкой "крестик", который открыт иконкой "i" из панели поиска, происходит возврат в основной интерфейс  

**Приоритет:**   
Обычная    

**Окружение:** 
macOS  | 12.6.6  
Android Studio Giraffe | 2022.3.1  
Galaxy  | 6S (разрешение экрана 1080 х 1920)  
Яндекс.Метро | 3.6.  
***
</details>

<details>
<summary>ID: 683-4 </summary>

### При выборе закрытой станции через панель поиска, не появляется специальный пин для закрытой станции [683-4](https://slepsovasonya.youtrack.cloud/issue/683-4/Pri-vybore-zakrytoj-stancii-cherez-panel-poiska-ne-poyavlyaetsya-specialnyj-pin-dlya-zakrytoj-stancii)
 
**Предусловия:**  
1. Открыть приложение "Яндекс.Метро"  
2. Установить город Москва  

**Шаги воспроизведения:**   
1. Нажать на поле ввода "Откуда"  
2. Ввести название закрытой станции "Говорова"  
3. Выбрать из поиска закрытую станцию "Говорова  

**Ожидаемый результат:**   
При выборе закрытой станции через панель поиска, на схеме, над выбранной станцией появляется специальный пин  
**Фактический результат:**     
При выборе закрытой станции через панель поиска, на схеме, над выбранной станцией появляется стандартный пин  

<img src="https://github.com/SofiiaSleptsova/Yandex_Metro/assets/147629405/431634db-56dc-4e40-a7d4-eb15271178a4" width="200" height="400">

**Приоритет:**    
Серьезная  

**Окружение:**  
macOS  | 12.6.6  
Android Studio Giraffe | 2022.3.1  
Galaxy  | 6S (разрешение экрана 1080 х 1920)  
Яндекс.Метро | 3.6.  
***
</details>

<details>
<summary>ID: 683-5 </summary>

### В панели поиска НЕ отображается история станций, ранее выбранных через панель поиска [683-5](https://slepsovasonya.youtrack.cloud/issue/683-5/V-paneli-poiska-NE-otobrazhaetsya-istoriya-stancij-ranee-vybrannyh-cherez-panel-poiska)  
 
**Предусловия:**  
1. Открыть приложение "Яндекс.Метро"  
2. Установить город Москва  

**Шаги воспроизведения:**   
1. Нажать на поле ввода "Откуда"  
2. Ввести название станции "Жулебино"  
3. Выбрать станцию из результатов поиска "Жулебино"  

**Ожидаемый результат:**   
Выбранная станция через панель поиска, отображается в виде истории при вторичном открытии панели поиска "Откуда" или "Куда"  
**Фактический результат:**     
Выбранная станция через панель поиска, НЕ отображается в виде истории при вторичном открытии панели поиска "Откуда" или "Куда"  

**Приоритет:**    
Серьезная       

**Окружение:** 
macOS  | 12.6.6  
Android Studio Giraffe | 2022.3.1  
Galaxy  | 6S (разрешение экрана 1080 х 1920)  
Яндекс.Метро | 3.6.  
***
</details>

<details>
<summary>ID: 683-6 </summary>

### В панели поиска НЕ отображается история, ранее выбранных на схеме станций и кликом по кнопке "Отсюда/Сюда" [683-6](https://slepsovasonya.youtrack.cloud/issue/683-6/V-paneli-poiska-NE-otobrazhaetsya-istoriya-ranee-vybrannyh-na-sheme-stancij-i-klikom-po-knopke-Otsyuda-Syuda)  
 
**Предусловия:**  
1. Открыть приложение "Яндекс.Метро"  
2. Установить город Москва  

**Шаги воспроизведения:**   
1. Нажать на точку станции "Планерная"  
2. Нажать на кпопку "Отсюда"  
3. Закрыть карточку станции иконкой "крестик"  
4. Открыть поле ввода "Откуда"  

**Ожидаемый результат:**   
Выбранная на схеме станция и кликом по кнопке "Отсюда/Сюда" в карточке станции, отображается в виде истории при открытии панелей поиска "Откуда" или "Куда"  
**Фактический результат:**     
Выбранная на схеме станция и кликом по кнопке "Отсюда/Сюда" в карточке станции, НЕ отображается в виде истории при открытии панелей поиска "Откуда" или "Куда"  

**Приоритет:**   
Серьезная       

**Окружение:** 
macOS  | 12.6.6  
Android Studio Giraffe | 2022.3.1  
Galaxy  | 6S (разрешение экрана 1080 х 1920)  
Яндекс.Метро | 3.6.  
***
</details>

<details>
<summary>ID: 683-96 </summary>

###  Панель с деталями маршрута открывается по тапу любой зоны карточки маршрута [683-96](https://slepsovasonya.youtrack.cloud/issue/683-96)  
 
**Предусловия:**  
1. Открыть приложение "Яндекс.Метро"  
2. Установить город Москва  

**Шаги воспроизведения:**   
1. Нажать на схеме станцию "Марьино"  
2. В карточке станции "Марьино" кликнуть по кнопке "Отсюда"  
3. Нажать на схеме станцию "Братиславская"  
4. В карточке станции "Братиславская" кликнуть по кнопке "Сюда"  
5. Нажать на пустую зону карточки маршрута  

**Ожидаемый результат:**   
Панель с деталями маршрута открывается по тапу кнопки "Детали маршрута"  

**Фактический результат:**     
Панель с деталями маршрута открывается по тапу любой зоны карточки маршрута  
[видео](https://slepsovasonya.youtrack.cloud/api/files/8-37?sign=MTY5OTQwMTYwMDAwMHwxLTF8OC0zN3w5T3NHUUpaVG40TzZMM3luXzZySkRBVzB2NDl2M1B2SVh2%0D%0AenlzUjJMNzJvDQo%0D%0A&updated=1693281928312)

**Приоритет:**   
Обычная           

**Окружение:** 
macOS  | 12.6.6  
Android Studio Giraffe | 2022.3.1  
Galaxy  | 6S (разрешение экрана 1080 х 1920)  
Яндекс.Метро | 3.6.  
***
</details>

<details>
<summary>ID: 683-99 </summary>

###  При смене ориентации с портретной на ландшафтную, панель с деталями маршрута закрывается [683-99](https://slepsovasonya.youtrack.cloud/issue/683-99/Pri-smene-orientacii-s-portretnoj-na-landshaftnuyu-panel-s-detalyami-marshruta-zakryvaetsya)  
 
**Предусловия:**  
1. Открыть приложение "Яндекс.Метро"  
2. Установить город Москва  

**Шаги воспроизведения:**   
1. Нажать на схеме станцию "Марьино"  
2. В карточке станции "Марьино" кликнуть по кнопке "Отсюда"  
3. Нажать на схеме станцию "Братиславская"  
4. В карточке станции "Братиславская" кликнуть по кнопке "Сюда"  
5. Нажать на кнопку "Детали маршрута"  
6. Сменить ориентацию экрана на ландшафтную  

**Ожидаемый результат:**   
При смене ориентации на ландшафтную, панель с деталями маршрута переходит в левую часть экрана  
**Фактический результат:**     
При смене ориентации на ландшафтную, панель с деталями маршрута закрывается  

**Приоритет:**    
Обычная           

**Окружение:** 
macOS  | 12.6.6  
Android Studio Giraffe | 2022.3.1  
Galaxy  | 6S (разрешение экрана 1080 х 1920)  
Яндекс.Метро | 3.6.  
***
</details>

<details>
<summary>ID: 683-2 </summary>

###  При отсутствии интернет-соединения НЕ появляется уведомление об ошибке [683-2](https://slepsovasonya.youtrack.cloud/issue/683-2/Pri-otsutstvii-internet-soedineniya-NE-poyavlyaetsya-uvedomlenie-ob-oshibke)  
 
**Предусловия:**  
1. Отключить интернет-соединение  

**Шаги воспроизведения:**   
2. Открыть приложение "Яндекс.Метро"  
3. Установить город Москва  

**Ожидаемый результат:**   
При отсутствии интернет-соединения появляется уведомление об ошибке  
**Фактический результат:**     
При отсутствии интернет-соединения НЕ появляется уведомление об ошибке  

**Приоритет:**    
Критическая             

**Окружение:** 
macOS  | 12.6.6  
Android Studio Giraffe | 2022.3.1  
Galaxy  | 6S (разрешение экрана 1080 х 1920)  
Яндекс.Метро | 3.6.  
***
</details>

<details>
<summary>ID: 683-3 </summary>

###  При отключении интернет-соединения НЕ появляется уведомление об ошибке [683-3](https://slepsovasonya.youtrack.cloud/issue/683-3/Pri-otklyuchenii-internet-soedineniya-NE-poyavlyaetsya-uvedomlenie-ob-oshibke)  
 
**Предусловия:**  
1. Открыть приложение "Яндекс.Метро"  
2. Установить город Москва  

**Шаги воспроизведения:**   
1. Отключить интернет-соединение  

**Ожидаемый результат:**   
При отключении интернет-соединения появляется уведомление об ошибке  
**Фактический результат:**     
При отключении интернет-соединения НЕ появляется уведомление об ошибке  

**Приоритет:**    
Критическая             

**Окружение:** 
macOS  | 12.6.6  
Android Studio Giraffe | 2022.3.1  
Galaxy  | 6S (разрешение экрана 1080 х 1920)  
Яндекс.Метро | 3.6.  
***
</details>

<details>
<summary>ID: 683-100 </summary>

###  Смена ориентации экрана, с портретного на ландшафтную уменьшает масштаб построенного маршрута [683-100](https://slepsovasonya.youtrack.cloud/issue/683-100/Smena-orientacii-ekrana-s-portretnogo-na-landshaftnuyu-umenshaet-masshtab-postroennogo-marshruta)  
 
**Предусловия:**  
1. Открыть приложение "Яндекс.Метро"  
2. Установить город Москва  

**Шаги воспроизведения:**   
1. Нажать на схеме станцию "Краскова"  
2. В карточке станции "Краскова" кликнуть по кнопке "Отсюда"  
3. Нажать на схеме станцию "Ипподром"  
4. В карточке станции "Ипподром" кликнуть по кнопке "Сюда"  
5. Сменить ориентацию экрана на ландшафтную  

**Ожидаемый результат:**   
При смене ориентации экрана, масштаб построенного маршрута не должен увеличиться или уменьшиться  
**Фактический результат:**     
При смене ориентации экрана, масштаб построенного маршрута уменьшается  

<img src="https://github.com/SofiiaSleptsova/Yandex_Metro/assets/147629405/027930d7-dbf7-48e5-9150-5da6a230eaaa" width="200" height="400">

<img src="https://github.com/SofiiaSleptsova/Yandex_Metro/assets/147629405/d08b1dac-f452-4314-b26f-5736a13a0c30" width="400" height="200">

**Приоритет:**    
Обычная                

**Окружение:** 
macOS  | 12.6.6  
Android Studio Giraffe | 2022.3.1  
Galaxy  | 6S (разрешение экрана 1080 х 1920)  
Яндекс.Метро | 3.6.  
***
</details>

<details>
<summary>ID: 683-7 </summary>

###  Нажатие лонгтапом на точку станции на схеме НЕ раскрывает карточку станции [683-7](https://slepsovasonya.youtrack.cloud/issue/683-7/Nazhatie-longtapom-na-tochku-stancii-na-sheme-NE-raskryvaet-kartochku-stancii)  
 
**Предусловия:**  
1. Открыть приложение "Яндекс.Метро"  
2. Установить город Москва  

**Шаги воспроизведения:**   
1. Нажать на точку станции "Зябликово" лонгтапом  

**Ожидаемый результат:**   
При нажатии на станции при помощи лонг-тапа открывается карточка станции с кнопками «Отсюда»/«Сюда»  
**Фактический результат:**     
При нажатии на станцию при помощи лонг-тапа открывается НЕРАСКРЫТАЯ карточка станции (где указано название станции и линия)  

<img src="https://github.com/SofiiaSleptsova/Yandex_Metro/assets/147629405/641ea1c3-53d1-4036-ac61-ad6ae68b030e" width="200" height="400">

**Приоритет:**    
Обычная                

**Окружение:** 
macOS  | 12.6.6  
Android Studio Giraffe | 2022.3.1  
Galaxy  | 6S (разрешение экрана 1080 х 1920)  
Яндекс.Метро | 3.6.  
***
</details>

<details>
<summary>ID: 683-97 </summary>

###  При лонгтапом по станции схема смещается от установленного расположения [683-97](https://slepsovasonya.youtrack.cloud/issue/683-97)  
 
**Предусловия:**  
1. Открыть приложение "Яндекс.Метро"  
2. Установить город Москва  

**Шаги воспроизведения:**   
1. Нажать на схеме станцию "Щербинка" лонгтапом  

**Ожидаемый результат:**   
При нажатии лонгтапом по станции схема не смещается  
**Фактический результат:**     
При нажатии лонгтапом по станции схема имеет смещение  
[видео](https://slepsovasonya.youtrack.cloud/api/files/8-33?sign=MTY5OTQwMTYwMDAwMHwxLTF8OC0zM3xuZTdzbmduc29USmJxcUtUMEE2djdCUDJfRXZWYXRUZlRi%0D%0AQ24tS3VOSXA0DQo%0D%0A&updated=1693223790306)

**Приоритет:**    
Обычная                

**Окружение:** 
macOS  | 12.6.6  
Android Studio Giraffe | 2022.3.1  
Galaxy  | 6S (разрешение экрана 1080 х 1920)  
Яндекс.Метро | 3.6.  
***
</details>

<details>
<summary>ID: 683-98 </summary>

###  При скролле лонгтапом по станциям схема смещается от установленного расположение [683-98](https://slepsovasonya.youtrack.cloud/issue/683-98)  
 
**Предусловия:**  
1. Открыть приложение "Яндекс.Метро"  
2. Установить город Москва  

**Шаги воспроизведения:**   
1. Нажать на схеме станцию "Люблино" лонгтапом  
2. Выбрать следующую станцию "Котельники" лонгтапом  
3. Выбрать следующую станцию "Жулебино" лонгтапом  

**Ожидаемый результат:**   
При скролле лонгтапом по станциям схема не смещается  
**Фактический результат:**     
При скролле лонгтапом по станциям схема имеет смещение  

[видео](https://slepsovasonya.youtrack.cloud/api/files/8-34?sign=MTY5OTQwMTYwMDAwMHwxLTF8OC0zNHx0R0dldFdvN0dJZEpQRWFJcGVTUURvS2MtSnBMVVhaMGs4%0D%0AMlBjalB3cFd3DQo%0D%0A&updated=1693224807886)

**Приоритет:**    
Обычная                

**Окружение:** 
macOS  | 12.6.6  
Android Studio Giraffe | 2022.3.1  
Galaxy  | 6S (разрешение экрана 1080 х 1920)  
Яндекс.Метро | 3.6.  
***
</details>

<details>
<summary>ID: 683-110 </summary>

###  Во время скролла лонгтапом по схеме, пин на станции и выделение станции НЕ пропадает, если отвести лонгтап на пустую зону [683-110](https://slepsovasonya.youtrack.cloud/issue/683-110)  
 
**Предусловия:**  
1. Открыть приложение "Яндекс.Метро"  
2. Установить город Москва  

**Шаги воспроизведения:**   
1. Нажать лонгтапом на точку станции "Сходня"  
2. Сместить при помощи лонгтапа на следующую станцию "Фирсановская"  
3. Сместить при помощи лонгтапа на следующую станцию "Зеленоград-Крюково"  
4. Сместить при помощи лонгтапа на пустую зону  

**Ожидаемый результат:**  
При скролле лонгтапом, пин на станции и выделение станции пропадает, если отвести лонгтап на пустую зону  
**Фактический результат:**     
При скролле лонгтапом, пин на станции и выделение станции НЕ пропадает, если отвести лонгтап на пустую зону  

[видео](https://slepsovasonya.youtrack.cloud/api/files/8-35?sign=MTY5OTQwMTYwMDAwMHwxLTF8OC0zNXxZWWdQbWJ4Z3NZZ0taVHlvUWtXN2FkSlpkT24wZXNXTHpM%0D%0AQnZuazhzWWl3DQo%0D%0A&updated=1693281439601)

**Приоритет:**    
Серьезная                 

**Окружение:** 
macOS  | 12.6.6  
Android Studio Giraffe | 2022.3.1  
Galaxy  | 6S (разрешение экрана 1080 х 1920)  
Яндекс.Метро | 3.6.  
***
</details>

<details>
<summary>ID: 683-111 </summary>

###  Во время скролла лонгтапом по схеме, карточка станции НЕ закрывается, если отвести лонгтап на пустую зону [683-111](https://slepsovasonya.youtrack.cloud/issue/683-111)  
 
**Предусловия:**  
1. Открыть приложение "Яндекс.Метро"  
2. Установить город Москва   

**Шаги воспроизведения:**   
1. Нажать лонгтапом на точку станции "Сходня"  
2. Сместить при помощи лонгтапа на следующую станцию "Фирсановская"  
3. Сместить при помощи лонгтапа на следующую станцию "Зеленоград-Крюково"  
4. Сместить при помощи лонгтапа на пустую зону  

**Ожидаемый результат:**   
При скролле лонгтапом, карточка станции закрывается, если отвести лонгтап на пустую зону  
**Фактический результат:**     
При скролле лонгтапом, карточка станции НЕ закрывается, если отвести лонгтап на пустую зону  

[видео](https://slepsovasonya.youtrack.cloud/api/files/8-36?sign=MTY5OTQwMTYwMDAwMHwxLTF8OC0zNnxZNG43eE96NEVqY204YV81dUhKSXJyajZyY0VuOW5FYW10%0D%0AZzU1YlZGdHVBDQo%0D%0A&updated=1693281525979)

**Приоритет:**    
Серьезная                 

**Окружение:** 
macOS  | 12.6.6  
Android Studio Giraffe | 2022.3.1  
Galaxy  | 6S (разрешение экрана 1080 х 1920)  
Яндекс.Метро | 3.6.  
***
</details>

<details>
<summary>ID: 683-8 </summary>

###  Прекращении лонгтапа в точке станции во время смещения по схеме, закрывает карточку станции [683-8](https://slepsovasonya.youtrack.cloud/issue/683-8/Prekrashenii-longtapa-v-tochke-stancii-vo-vremya-smesheniya-po-sheme-zakryvaet-kartochku-stancii)  
 
**Предусловия:**  
1. Открыть приложение "Яндекс.Метро"  
2. Установить город Москва  

**Шаги воспроизведения:**   
1. Нажать лонгтапом на точку станции "Планерная"  
2. Сместить при помощи лонгтапа на следующую станцию "Сходненская"  
3. Сместить при помощи лонгтапа на следующую станцию "Тушинская"  
4. Отпустить лонгтап на станции "Тушинская"  

**Ожидаемый результат:**   
При прекращении лонгтапа в точке станции во время смещения по схеме, оставляет открытой карточку станции  
**Фактический результат:**     
При прекращении лонгтапа в точке станции во время смещения по схеме, закрывает карточку станции  

**Приоритет:**    
Критическая                  

**Окружение:** 
macOS  | 12.6.6  
Android Studio Giraffe | 2022.3.1  
Galaxy  | 6S (разрешение экрана 1080 х 1920)  
Яндекс.Метро | 3.6.  
***
</details>

<details>
<summary>ID: 683-9 </summary>
  
### Прекращение лонгтапа в точке во время смещения возвращает точку выбранной станции в стандартный режим [683-9](https://slepsovasonya.youtrack.cloud/issue/683-9/Prekrashenie-longtapa-v-tochke-vo-vremya-smesheniya-vozvrashaet-tochku-vybrannoj-stancii-v-standartnyj-rezhim)

**Предусловия:**
1. Открыть приложение "Яндекс.Метро"  
2. Установить город Москва

**Шаги воспроизведения:**
1. Нажать лонгтапом на точку станции "Планерная"  
2. Сместить при помощи лонгтапа на следующую станцию "Сходненская"  
3. Сместить при помощи лонгтапа на следующую станцию "Тушинская"  
4. Отпустить лонгтап на станции "Тушинская"

**Ожидаемый результат:**  
При прекращении лонгтапа в точке станции во время смещения по схеме, оставляетя на точке пин, меньший размер точки станции и жирный шрифт  
**Фактический результат:**  
При прекращении лонгтапа в точке во время смещения по схеме, с точки пропадает пин, точка станции и шрифт возвращаются в стандартный режим

**Приоритет:**   
Серьезная             

**Окружение:**  
macOS  | 12.6.6  
Android Studio Giraffe | 2022.3.1  
Galaxy  | 6S (разрешение экрана 1080 х 1920)  
Яндекс.Метро | 3.6.  
***
</details>

</details>
