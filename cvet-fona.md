# Цвет фона

Начнем с установки другого цвета фона для `Greeting`. Вы можете сделать это, обернув `Text`составной объект расширением `Surface`. `Surface`принимает цвет, поэтому используйте **`MaterialTheme.colors.primary`**.

Примечание. `Surface`И `MaterialTheme`являются концепциями, связанными с [Material Design](https://material.io/design/introduction) , системой дизайна, созданной Google, чтобы помочь вам создавать пользовательские интерфейсы и возможности.

```
@Composable
private fun MyApp() {
    Surface(color = MaterialTheme.colors.background) {
        Greeting("Android")
    }
}
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
import android.os.Bundle
import androidx.activity.ComponentActivity
import androidx.activity.compose.setContent
import androidx.compose.foundation.layout.padding
import androidx.compose.material.MaterialTheme
import androidx.compose.material.Surface
import androidx.compose.material.Text
import androidx.compose.runtime.Composable
import androidx.compose.ui.Modifier
import androidx.compose.ui.tooling.preview.Preview
import androidx.compose.ui.unit.dp
import com.codelab.basicstep1.ui.theme.BasicsCodelabTheme

class MainActivity : ComponentActivity() {
    override fun onCreate(savedInstanceState: Bundle?) {
        super.onCreate(savedInstanceState)
        setContent {
            BasicsCodelabTheme {
                MyApp()
            }
        }
    }
}

@Composable
private fun MyApp() {
    Surface(color = MaterialTheme.colors.background) {
        Greeting("Android")
    }
}

@Composable
private fun Greeting(name: String) {
    Surface(color = MaterialTheme.colors.primary) {
        Text(text = "Hello $name!", modifier = Modifier.padding(24.dp))
    }
}

@Preview(showBackground = true)
@Composable
private fun DefaultPreview() {
    BasicsCodelabTheme {
        MyApp()
    }
}
```

![52d5ed8919f277f0.png](https://developer.android.com/codelabs/jetpack-compose-basics/img/52d5ed8919f277f0.png)

Есть десятки модификаторов, которые можно использовать для выравнивания, анимации, компоновки, создания кликабельных или прокручиваемых, трансформации и т. Д. Полный список можно найти в [Списке модификаторов компоновки](https://developer.android.com/jetpack/compose/modifiers-list) . Некоторые из них вы будете использовать на следующих этапах.
