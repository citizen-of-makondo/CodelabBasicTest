# Повторное использование элементов



Чем больше компонентов вы добавляете в пользовательский интерфейс, тем больше уровней вложенности вы создаете. Это может повлиять на удобочитаемость, если функция становится действительно большой. Создавая небольшие повторно используемые компоненты, легко создать библиотеку элементов пользовательского интерфейса, используемых в вашем приложении. Каждый отвечает за одну небольшую часть экрана и может редактироваться независимо.

Создайте Composable с именем `MyApp`, содержащим приветствие.

```
@Composableprivate fun MyApp() {    Surface(color = MaterialTheme.colors.background) {        Greeting("Android")    }}
```

Это позволяет вам очистить `onCreate`обратный вызов и предварительный просмотр, поскольку теперь вы можете повторно использовать `MyApp`составной объект, избегая дублирования кода. Ваш `MainActivity.kt`файл должен выглядеть так:

```kotlin
import android.os.Bundleimport androidx.activity.ComponentActivityimport androidx.activity.compose.setContentimport androidx.compose.foundation.layout.paddingimport androidx.compose.material.MaterialThemeimport androidx.compose.material.Surfaceimport androidx.compose.material.Textimport androidx.compose.runtime.Composableimport androidx.compose.ui.Modifierimport androidx.compose.ui.tooling.preview.Previewimport androidx.compose.ui.unit.dpimport com.codelab.basicstep1.ui.theme.BasicsCodelabThemeclass MainActivity : ComponentActivity() {    override fun onCreate(savedInstanceState: Bundle?) {        super.onCreate(savedInstanceState)        setContent {            BasicsCodelabTheme {                MyApp()            }        }    }}@Composableprivate fun MyApp() {    Surface(color = MaterialTheme.colors.background) {        Greeting("Android")    }}@Composableprivate fun Greeting(name: String) {    Surface(color = MaterialTheme.colors.primary) {        Text(text = "Hello $name!", modifier = Modifier.padding(24.dp))    }}@Preview(showBackground = true)@Composableprivate fun DefaultPreview() {    BasicsCodelabTheme {        MyApp()    }}
```
