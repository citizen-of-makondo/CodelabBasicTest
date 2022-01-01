# Цвет фона

Начнем с установки другого цвета фона для `Greeting`. Вы можете сделать это, обернув `Text`составной объект расширением `Surface`. `Surface`принимает цвет, поэтому используйте **`MaterialTheme.colors.primary`**.

Примечание. `Surface`И `MaterialTheme`являются концепциями, связанными с [Material Design](https://material.io/design/introduction) , системой дизайна, созданной Google, чтобы помочь вам создавать пользовательские интерфейсы и возможности.

```
@Composableprivate fun Greeting(name: String) {    Surface(color = MaterialTheme.colors.primary) {        Text (text = "Hello $name!")    }}
```

Компоненты, вложенные внутрь, `Surface`будут нарисованы поверх этого цвета фона.

Когда вы добавите этот код в проект, вы увидите кнопку « **Построить и обновить»** в правом верхнем углу Android Studio. Нажмите на него или создайте проект, чтобы увидеть новые изменения в предварительном просмотре.

![1886a2cbfefe7df3.png](https://developer.android.com/codelabs/jetpack-compose-basics/img/1886a2cbfefe7df3.png)

Вы можете увидеть новые изменения в превью:

![a6cd30458c8829a2.png](https://developer.android.com/codelabs/jetpack-compose-basics/img/a6cd30458c8829a2.png)

Возможно, вы упустили важную деталь: **текст теперь белый** . Когда мы это определили?

Вы не сделали! Компоненты материала, такие как `androidx.compose.material.Surface`, созданы, чтобы сделать ваш опыт лучше, заботясь об общих функциях, которые вы, вероятно, захотите в своем приложении, таких как выбор подходящего цвета для текста. Мы говорим, что Материал является _самоуверенным,_ потому что он предоставляет хорошие настройки по умолчанию и шаблоны, общие для большинства приложений. Компоненты материала в Compose построены поверх других базовых компонентов (in `androidx.compose.foundation`), которые также доступны из компонентов вашего приложения, если вам нужна большая гибкость.

В этом случае `Surface`понимается, что, когда фон установлен на `primary`цвет, любой текст поверх него должен использовать `onPrimary`цвет, который также определен в теме. Вы можете узнать больше об этом в разделе « **Тематика вашего приложения** ».

Примечание. Чтобы получить интерактивный список компонентов материалов в Compose, [посетите](https://play.google.com/store/apps/details?id=androidx.compose.material.catalog) приложение [Compose Material Catalog](https://play.google.com/store/apps/details?id=androidx.compose.material.catalog) .

### Модификаторы <a href="#modifiers" id="modifiers"></a>

Большинство элементов пользовательского интерфейса Compose, таких как `Surface`и, `Text`принимают необязательный `modifier`параметр. Модификаторы сообщают элементу пользовательского интерфейса, как размещать, отображать или вести себя в его родительском макете.

Например, `padding`модификатор применит некоторое пространство вокруг элемента, который он украшает. Вы можете создать модификатор заполнения с помощью `Modifier.padding()`.

Теперь добавьте отступ к вашему `Text`на экране:

```
import androidx.compose.foundation.layout.paddingimport androidx.compose.ui.Modifierimport androidx.compose.ui.unit.dp...@Composableprivate fun Greeting(name: String) {    Surface(color = MaterialTheme.colors.primary) {        Text(text = "Hello $name!", modifier = Modifier.padding(24.dp))    }}
```

Нажмите « **Построить и обновить»,** чтобы увидеть новые изменения.

![52d5ed8919f277f0.png](https://developer.android.com/codelabs/jetpack-compose-basics/img/52d5ed8919f277f0.png)

Есть десятки модификаторов, которые можно использовать для выравнивания, анимации, компоновки, создания кликабельных или прокручиваемых, трансформации и т. Д. Полный список можно найти в [Списке модификаторов компоновки](https://developer.android.com/jetpack/compose/modifiers-list) . Некоторые из них вы будете использовать на следующих этапах.
