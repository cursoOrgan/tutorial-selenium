#TUTORIAL SELENIUM WEBDRIVER

En este documento se va a realizar un tutorial sobre Selenium Webdriver para un usuario inexperto que quiera aprender lo mas basico.

##INDICE

* **1. Introduccion**
* **2. Instalacion Selenium Webdriver**
* **3. Comandos**
* **3.1 Find Element**
* **3.2 Metodos utilizados sobre el driver**
* **3.3 Metodos utilizados sobre elementos de la web**
* **3.4 Asserts**
* **4. Recomendaciones y consejos**
* **5. TestNG**
* **6. JUnit4**

##INTRODUCCION

En las pruebas de software, la automatización de pruebas consiste en el uso de software especial para controlar la ejecución de pruebas y la comparación entre los resultados obtenidos y los resultados esperados. La automatización de pruebas permite incluir pruebas repetitivas y necesarias dentro de un proceso formal de pruebas ya existente o bien adicionar pruebas cuya ejecución manual resultaría difícil.

Algunas pruebas de software tales como las pruebas de regresión pueden ser laboriosas y consumir mucho tiempo para su ejecución si se realizan manualmente. Además, una aproximación manual puede no ser efectiva para encontrar ciertos tipos de defectos, mientras que las pruebas automatizadas ofrecen una alternativa que lo permite. Una vez que una prueba ha sido automatizada, ésta puede ejecutarse repetitiva y rápidamente en particular con los productos de software que tienen ciclos de mantenimiento largo, ya que incluso cambios relativamente menores en la vida de una aplicación pueden inducir fallos en funcionalidades que anteriormente operaban de manera correcta.

**Selenium** es un entorno de pruebas de software para aplicaciones basadas en la web. Selenium es un plugin de Firefox, el cual provee una herramienta de grabar/reproducir para crear pruebas sin usar un lenguaje de scripting para pruebas (Selenium IDE). Selenium tiene otro componente llamado Selenium WebDriver, que es el sucesor de Selenium Remote Control (Selenium RC).

**Selenium WebDriver** hace posible escribir pruebas específicas automatizadas para aplicaciones web, en cualquier lenguaje de programación, lo que permite una mejor integración de Selenium a entornos de prueba existentes. Los lenguajes de programación soportados son Java, Ruby, Python, Perl, PHP y C#.

El uso de Selenium puede ser un poco limitado en cuanto a páginas web dinámicas, es decir, que usen algún tipo de sincronización como puede ser Ajax. En cuanto a páginas estáticas, no se produce ninguna limitación en cuanto a acciones a realizar. Estas limitaciones técnicas pueden subsanarse con métodos de espera o pequeños trucos para esperar a que se sincronice algo “esperando” a que se oculte el símbolo de carga o similares.

##INSTALACION SELENIUM WEBDRIVER

Para la utilización de Selenium WebDriver es necesario un entorno de desarrollo como pueden ser NetBeans o Eclipse. En este caso vamos a utlizar NetBeans porque podemos descargar el paquete Java JDK y NetBeans juntos sin necesidad de instalar cosas por separado. A continuación se muestran los pasos para instalar y utilizar Selenium WebDriver:

1. Descargamos e instalamos **Java** y el entorno de desarrollo **NetBeans**, que podemos descargar en la siguiente [web](http://www.oracle.com/technetwork/java/javase/downloads/jdk-netbeans-jsp-142931.html). Seleccionamos la versión correcta en nuestro caso.

2. Descargamos de la [página oficial](http://www.seleniumhq.org/download/) de Selenium Java Client.

3. Descargamos el paquete para Java y nos descargará una carpeta con múltiples archivos .jar, que serán las librerías que habrá que añadir en nuestro proyecto posteriormente para funcionar correctamente.

Podemos dejar todas las librerías en una misma carpeta para mayor comodidad y visualización.º

Abrimos el entorno de desarrollo NetBeans y vamos a “File” → “New Project” → “Categories: Java” → “Projects: Java Application” → “Next”.

4. Le damos un nombre al proyecto y donde lo vamos a guardar (para mayor comodidad crear una carpeta nueva donde vayamos a guardar todos los scripts para ser localizados fácilmente). Y finalmente damos a “Finish”.

5. Una vez que hemos creado el proyecto, pulsamos con el botón derecho encima de él y vamos a “Properties” → “Libraries” → “Add JAR/Folder” y añadimos todas las librerías que descargamos → “OK”.

6. Si lo hemos hecho correctamente deberían aparecer todas las librerías añadidas en la carpeta Libreries de nuestro proyecto.

Ya está todo listo para usar Selenium WebDriver. Simplemente abrimos nuestra clase principal y ahí escribimos todo el código que queramos.

##COMANDOS

El uso de Selenium WebDriver consiste en la interacción de la aplicación web que queramos testear con nuestro entorno de programación. Para dicho interacción lo que hacemos en el navegador es “inspeccionar” los elementos de la web. En Google Chrome se realiza de la siguiente manera:

1. Cuando estemos en la aplicación o página web hacemos botón derecho sobre el elemento que queramos inspeccionar.

2. Clicamos en “Inspeccionar elemento” y nos aparece abajo el código html de la web y el código en concreto del elemento que queremos inspeccionar.

###Find Element

Uno de los métodos más importantes que vamos a necesitar es “findElement”. Mediante este método, buscamos elementos de la web para poder interactuar con ellos, como puede ser un botón para clicar, un buscador donde introducir texto y buscar posteriormente, o cualquier elemento que tengamos en la vista de la aplicación. El método findElement requiere de un argumento de tipo “String” que podemos determinar por varias vías. En este manual trataremos varios tipos de argumentos que le podemos pasar a dicho método:

* Por la “id” de un elemento: si cuando inspeccionamos el código de un determinado elemento vemos que tiene una id asignada (no ocurre siempre) podemos “encontrar” el elemento de la siguiente manera:

*WebElement buscador = driver.findElement(By.id(“buscadorBtn”));*
*buscador.click();*

El ejemplo es sencillo, simplemente queremos darle a un botón que se llama “Buscador”, que nos lleva a una nueva vista de la aplicación. Por tanto, lo primero que hacemos es crear un elemento de la clase “WebElement”. Posteriormente le vamos a indicar que busque el elemento por la id que le hayan asignado. Una vez que hemos “encontrado” el elemento, al ser un botón, podemos hacer click sobre él para que nos lleve a la nueva vista.

* Por el nombre de la clase del elemento: en ocasiones en lugar de una id, el elemento puede estar asociado a una clase de elementos, lo cual se ve en el código como que tiene asociado un nombre en “class”. En ese caso podemos buscar el elemento por dicho nombre de la manera que sigue:

*WebElement buscador = driver.findElement(By.className(“buscadorBtn”));*

* Por el CSS Path (o ruta de CSS del elemento): el uso mediante este tipo de argumento es sencillo. Consiste en pasar como argumento la ruta de CSS del elemento. Esta ruta en aplicaciones complejas puede resultar muy complejo, por lo que los navegadores nos proporcionan dicho Path para que simplemente lo peguemos donde lo necesitemos. A continuación veremos cómo realizar dicha opción: 

Hay que tener en cuenta que se ha realizado sobre Google Chrome, en otros navegadores las acciones llevadas a cabo serán diferentes, pero las opciones deben estar presentes en todos los navegadores. 

Cuando tengamos localizado el elemento en concreto en nuestro código HTML, simplemente con clicar encima con el botón derecho nos aparecerán una serie de opciones. Clicando en “Copy CSS Path” ya tenemos nuestra ruta copiada y lista para pegar donde la necesitemos. Para utilizar dicha ruta en nuestro código Java, se realiza de la siguiente manera:

*WebElement buscador = driver.findElement(By.cssSelector(“cssPath”));*

* Por el XML Path (o ruta XML del elemento): igual que se puede hacer con la ruta CSS, podemos introducir como argumento la ruta XML del elemento. De manera similar en las opciones del elemento, seleccionamos la opción “Copy XPath”. Esta ruta la copiamos de manera similar en el método findElement como podemos ver a continuación:

*WebElement buscador = driver.findElement(By.xpath(“xpath”));*

Quizá, esta última opción es la más recomendable para incluir en nuestro método, ya que nos olvidamos de buscar nosotros la id o el nombre de la clase del elemento y además, es una ruta más reducida que la ruta CSS, por lo que se recomienda su uso por encima de cualquiera de los otros.

###Metodos utilizados sobre el driver

Cuando hemos creado el objeto de la clase WebDriver, podemos realizar sobre él varias acciones sencillas pero que serán muy necesarias en algunos casos.

* **get (String) :** este método nos lleva a una determinada página web que introducimos como String en el argumento. A continuación veremos un ejemplo que nos llevará a google.es:

*driver.get(“www.google.es”);*

* **close () :** este método cierra el navegador para finalizar el test:

*driver.close();*

Podemos realizar varias acciones sobre la ventana del navegador con el método **manage()**. Dentro de este método podemos ir ejecutando distintos métodos para realizar acciones. Dos acciones muy interesantes son redimensionar la vista del navegador o maximizarla. Esto se realiza mediante los dos siguientes comandos:

*//Maximizar la ventana*
*driver.manage().window().maximize();*

*//Redimensionar la ventana a la dimension que le indiquemos como argumento*
*driver.manage().window().setSize(DimensiontargetSize);*

También podemos realizar varias acciones sobre la navegación en la web, como puede ser refrescar la página o volver atrás. Esto se realiza mediante el método **navigate()**. Dentro de este método encontramos varios métodos que pueden ser de gran ayuda como pueden ser:

*//Refrescar la ventana*
*driver.navigate().refresh();*

*//Volver a la vista anterior*
*driver.navigate().back();*

###Metodos utilizados sobre elementos de la web

Una vez que tenemos un elemento de la clase WebElement creado podemos realizar acciones con él que Selenium irá ejecutando por sí mismo.

* **getText() :** Por ejemplo, si tenemos un elemento que es un texto determinado mostrado en cualquier lugar de la página web, podemos extraer el texto de modo que lo podemos convertir a una variable de tipo String. Esto lo podemos hacer con el método getText() de la siguiente manera:

*WebElement texto = driver.findElement(By.xpath(“xpath”));*
*String textoExtraido = texto.getText();*

Estas dos líneas de código las podemos ejecutar en una única línea de la siguiente manera:

*String textoExtraido = driver.findElement(By.xpath(“xpath”)).getText();*

* **sendKeys(String) :** cuando tenemos un cuadro de introducción de texto, podemos introducirle valores con éste método como podemos ver:

*WebElement usuario = driver.findElement(By.id(“#usuario”));*
*usuario.sendKeys(“usuarioCorrecto”);*

Con éste método, introducimos en el cuadro de texto el argumento del método sendKeys. También podemos hacer la simulación de pulsación de botones de nuestro teclado como pueden ser escape o enter. Estos botones no se introducen como tipo String. Ahora vemos un ejemplo de como simular la pulsación del botón Enter:

*WebElement usuario = driver.findElement(By.id(“#usuario”));*
*usuario.sendKeys(Keys.ENTER);*

**Para el uso de otras posibles teclas buscar en Internet cuando surja la necesidad.**

* **submit() :** si nos encontramos en la aplicación con un formulario de ingreso de datos, como puede ser un login con usuario y password típico, podemos usar el método submit() como podemos ver a continuación en un ejemplo de formulario con usuario y contraseña:

*WebElement usuario = driver.findElement(By.id(“#usuario”));*
*usuario.sendKeys(“usuarioCorrecto”);*
*WebElement password = driver.findElement(By.id(“#password”));*
*password.sendKeys(“passwordCorrecta”);*
*password.submit();*

En el último elemento del formulario, ejecutamos el método submit(). Esta acción es similar a pulsar el botón enter de nuestro teclado.

**OJO! El método submit() únicamente funcionará si nuestro cuadro de texto está dentro de un form en el código html.**

* **click() :** si tenemos un botón donde queremos pinchar en él, simplemente ejecutamos este método sobre el elemento. A continuación tenemos un ejemplo básico:

*WebElement boton = driver.findElement(By.id(“#btn”));*
*boton.click();*

* **clear() :** este método se utiliza para limpiar el texto que haya introducido en algún cuadro de introducción de texto. Ejemplo:

*WebElement buscadorPagina = driver.findElement(By.xpath("xpath"));*
*buscadorPagina.clear();*

* **getAttribute (String) :** este método se utiliza para obtener algún atributo del elemento como puede ser su nombre de clase o su id, por ejemplo. 

*WebElement buscadorPagina = driver.findElement(By.xpath("xpath"));*
*String className = buscadorPagina.getAttribute(“class”);*

* **getCssValue (String) :** si lo que queremos es obtener un valor de una propiedad css como puede ser el tamaño de letra, tipo de letra, tamaño de margen, etc, debemos utilizar éste método y no el anterior. Como argumento habrá que pasarle exactamente el nombre de la propiedad que queremos recuperar para su uso posterior. 

Si tenemos un elemento que sea una lista de elementos que podemos seleccionar, debemos utilizar el método **Select (String)**. Para utilizar dicho método debemos crear un objeto de la clase Select y pasarle como argumento la lista y posteriormente hacemos uso de varios métodos para seleccionar la opción que queramos pasándole como argumento de tipo String. Por ejemplo, si tenemos una lista ("nombre-lista") y queremos seleccionar uno de los elementos de la lista ("elemento-lista"), lo haremos del siguiente modo:

*new Select(driver.findElement(By.id("nombre-lista"))).selectByVisibleText(“elemento-lista”);*

* **Wait:**  Si tenemos problemas ya que al realizar una operación determinada, la aplicación debe realizar una pequeña carga, donde los datos de la siguiente vista no son cargados instantáneamente podemos utilizar métodos de espera (“wait”) hasta que cargue cierto elemento para seguir ejecutando el script.

Un método redactado para su uso sobre ciertos elementos, que necesitan una cierta espera hasta que la vista esté cargada para poder interactuar con dichos elementos es el siguiente:

*public static void tiempoEspera (String xpath) {*
	*WebDriverWait wait = new WebDriverWait (driver,25);*
	*WebElement element = wait.until(ExpectedConditions.elementToBeClickable(By.xpath(xpath)));*
*}*

25 sera el tiempo de espera hasta que aparezca el elemento. Si en ese tiempo determinado no aparece el elemento, el test dara error.

Las [condiciones esperadas](https://selenium.googlecode.com/git/docs/api/java/org/openqa/selenium/support/ui/ExpectedConditions.html)  podemos cambiarlas entre varias opciones. Para mas informacion buscar en Internet.

* **Contains (String) :** si queremos comprobar que una cadena de texto contenga otro texto, palabra o caracter se utiliza este método. Este método devuelve un valor booleano true o false, por lo que es necesario que lo utilicemos bajo una condición booleana (en un if, o en una variable booleana como se verá en el ejemplo siguiente). Es recomendable que ambas cadenas de string estén o en minúsculas (con el método toLowerCase()) o mayúsculas (con el método toUpperCase()) para que no haya errores debido a la sensibilidad. Entonces por ejemplo, si queremos comprobar si un String cadena1 contiene un String cadena2 lo haremos de la siguiente manera:

*String cadena1, cadena2;*
*boolean contenido = cadena1.toLowerCase().contains(cadena2.toLowerCase());*

###Asserts

La utilización de Selenium WebDriver se basa en la comprobación de que vamos obteniendo los resultados que vamos esperando. Para ello hay que ir realizando las comprobaciones que veamos necesarias, por lo que el uso de los **Asserts** es, quizás, una de las partes más importantes de Selenium. Assert es una biblioteca que se importa para el uso de varios métodos posteriormente. El uso de los Asserts es básico ya que se utilizan para la comprobación de un determinado caso. La diferencia entre utilizar asserts o a través del uso de if, es que si el if no es correcto no se ejecuta lo que vaya dentro de dicho if y sigue la ejecución correcta del test. En cambio, al usar assert, si el resultado no es correcto el test se para, indicándonos el error que se ha producido.

Hay varias formas de utilizar los asserts, que se irán explicando una a una.

* **assertEquals**

assertEquals es un método que se compone de dos argumentos, siempre del mismo tipo. Su uso se limita a comparar un valor con otro de modo que si son exactamente iguales, el resultado es correcto, por lo que se continúa con la ejecución. Esto se puede utilizar por ejemplo para comprobar que el título de la página es lo que esperamos o para comprobar si algún texto que debe aparecer en algún determinado lugar de la web, aparece tal y como nosotros queremos.

* **assertNotEquals**

El funcionamiento de este método es el contrario al anterior. Si la comparación no es exactamente igual, entonces el método devuelve un resultado correcto y se continúa con la ejecución del script.

* **assertNotNull**

assertNotNull se utiliza para comprobar si un determinado objeto de la web no es “null”. En caso de que queramos comprobar si algo se ha creado correctamente, podemos utilizar este método para comprobar que se ha creado bien, en caso de que el elemento sea “null” el assert dará error y se parará la ejecución.

* **assertNull**

El contrario que el anterior. Si el elemento es “null” entonces el assert tiene resultado correcto y se sigue ejecutando.

* **assertTrue**

Este método se utiliza con una condición booleana, de modo que si la condición que le imponemos al método es true, el assert será correcto y se ejecutará sin error. En caso de que la condición sea false, el assert dará error y se parará la ejecución.

* **assertFalse**

Este método hace lo contrario al anterior, de modo que el assert es correcto cuando la condición es false y da error cuando la condición es true.

##RECOMENDACIONES Y CONSEJOS

Ahora veremos algunas recomendaciones a llevar a cabo para el correcto uso de Selenium.

* Para la comprobación de que un dato ha aparecido correctamente tras hacer una búsqueda o tras aplicar unos filtros, si aparece una lista de elementos que queremos recorrer para comprobar si ha aparecido bien, deberemos utilizar un bucle que los recorra. Por ejemplo tenemos una aplicación que nos muestra una lista de elementos, que podemos filtrar según varios tipos de opciones. Cuando filtremos, queremos comprobar que los resultados obtenidos son correctos y están bien filtrados. Entonces deberemos realizar un bucle que recorra todos los elementos, cambiando el valor “i” del bucle en la sintaxis de modo que esa i permita que en cada iteración del bucle pase al siguiente elemento pero compruebe el mismo campo en todos ellos. 


* Si queremos comparar dos textos para ver si su valor es el mismo con algún assert, se recomienda que en el método cuando se implemente, ambos strings se pongan primero ambos a minúsculas o mayúsculas, ya que el programa es sensible a mayúsculas y minúsculas y cualquier diferencia de eso en un carácter hace que la comparación sea diferente aunque el texto sea el mismo.

* A veces necesitaremos pasar un campo numérico que queramos comparar que aparece en la web. Este dato aparecerá como tipo string cuando lo obtengamos con el método findElement. Posteriormente podemos convertirlo a entero con el método parseInt (String) de la clase Integer. Por ejemplo:

*String numeroString = “24”;*
*int numeroEntero = Integer.parseInt(numeroString);*

Tener en cuenta que a veces si introducimos algún texto y esperamos que ese texto no aparezca por cualquier motivo es un assert correcto, no sería incorrecto.

##TestNG

**TestNG es un framework para pruebas y testing** que trabaja con Java y está basado en JUnit (para Java) y NUnit (para .NET), pero introduciendo nuevas funcionalidades que los hacen más poderosos y fáciles de usar. TestNG está diseñado para cubrir todas las categorías de las pruebas: unitarias, funcionales, end-to-end, integración, etc.

Lo primero para trabajar con TestNG en NetBeans es descargar la [librería](http://testng.org/doc/download.html).

Una vez descargamos el archivo comprimido, lo descomprimimos y movemos la carpeta a la raíz donde nos interese a nosotros tenerla.

Para utilizar TestNG, tan sólo debemos añadir dicha librería en el proyecto que se haya creado para realizar nuestros tests. Una vez añadida, ya estamos listos para comenzar con las pruebas.

En NetBeans tenemos dos posibles ficheros para crear archivos TestNG:

* **TestNG Test Case** es la clase java donde diseñaremos nuestro test. Es como su propio nombre indica, un caso test.
* **TestNG Test Suite** es un archivo xml donde podemos gestionar la ejecución de múltiples Test Case en caso de tener más de un archivo.

###Test Case

Cuando creamos un archivo Test Case, se crea una estructura por defecto.

Las “etiquetas” que se ven encima de ciertos métodos que se generan por defecto, que van acompañadas con un carácter @, se conocen como **annotations (anotaciones)**. Existen muchos tipos de anotaciones en TestNG. Vamos a ver cada uno de los tipos a continuación:

* @BeforeSuite: el método con esa anotación se ejecutará antes que todos los test contenidos en el Test Suite.
* @AfterSuite: este método se ejecutará después de ejecutar los test contenidos en el Test Suite.
* @BeforeGroups: Este método se ejecutará antes del primer test que pertenezca a un determinado grupo de test invocados.
* @AfterGroups: este método se ejecutará después del último método que pertenezca a un grupo de test determinados.
* @BeforeClass: el método con dicha anotación se ejecutará antes del primer método de la clase invocada.
* @AfterClass: igual que el método anterior, pero en lugar de ejecutarse antes, éste método se ejecutará después de haber ejecutado todos los tests de esa clase.
* @BeforeMethod: este método será ejecutado antes de ejecutar cualquier método test.
* @AfterMethod: este método será ejecutado después de ejecutar cualquier método test.
* @Test: esta anotación se incluye en la cabecera de cada uno de los método que vamos a pasar como test. En un archivo Test Case puede haber tantos tests como veamos conveniente. Cualquier método de nuestra clase que queramos que sea comprobado como test, debe llevar esta etiqueta en la cabecera. En caso de no tenerla el resultado de ejecutarla no aparecerá como resultado de nuestros tests.

Una vez que tenemos definido una prueba, hay que ejecutarla. Para ejecutar un test se realizará de la siguiente manera:

Vamos a nuestro archivo Test Case en la lista de archivos del proyecto. Hacemos click con el botón derecho → “Test File”. Con esto, el test comenzará a ejecutarse automáticamente y al terminar nos aparecerá el resultado del test.

Si tenemos más de un test method para ejecutar se ejecutarán todos ellos uno a uno. Si alguno de ellos “falla”, la ejecución terminará y se devolverán los resultados oportunos de los test positivos, negativos y los que no se han podido ejecutar porque se ha detenido la prueba.

###Test Suite

Un **Test Suite** es una colección de Test Case. Está representado por un archivo XML que representa las características de ejecución. Es muy flexible a la hora de configurar los tests a ejecutar. Un test suite puede contener uno o más test y estará definido por la etiqueta <suite>. <suite> está formado a su vez de etiquetas **<test>**.

La etiqueta **<suite>** acepta los siguientes atributos:

* name: es el único atributo obligatorio.
* verbose
* parallel
* thread-count
* annotations
* time-out

Ejecutando el Test Suite el resultado será lo mismo que ejecutando uno a uno nuestros Test Case, pero ejecutará todos ellos uno tras uno.

###Grupos de test

TestNG tiene una funcionalidad muy útil que sus competidores (JUnit por ejemplo) no tienen. Dicha funcionalidad es la creación de **grupos de test**. No sólo se pueden definir grupos de test, sino que además, se pueden hacer grupos de grupos. Posteriormente a la hora de ejecutar, podemos ejecutar un grupo u otro, excluyendo a los que veamos necesarios por el momento. Hacer grupos de test provee de gran flexibilidad sobre la organización de nuestros tests y no requiere recompilar el código si queremos ejecutar dos conjuntos de tests diferentes.


Para definir un test como perteneciente a un grupo de test basta con incluir en la anotación @Test un atributo: (groups = { “nombreGrupo” }) ó (groups = {“nombreGrupo1”,”nombreGrupo2”}) en caso de querer definirlo en más de un grupo.

Posteriormente para definir qué grupo queremos ejecutar basta con definirlos en el Test Suite.

###Dependencia de test.

TestNG nos permite la ejecución de test “dependiendo” de ciertos resultados de test anteriores. Es decir, si Test2 depende de Test1, Test2 únicamente se ejecutará si Test1 ha sido exitoso. En caso contrario, Test2 no se ejecutará.

**Para mayor información sobre la herramienta TestNG en el siguiente enlace hay un tutorial muy bueno sobre todo lo relacionado con ello y numerosos ejemplos, además de otras funcionalidades que no se han explicado en este documento ya que no han sido necesarias aún, y que podemos encontrar también:**

[Enlace](http://www.tutorialspoint.com/testng/index.html) 

##JUnit4

Al igual que TestNG, JUnit es un framework de testing para Java. Este framework nos provee ciertas facilidades:

* Clases base con anotaciones (annotations) para escribir casos de test.
* Clase base para ejecutar los test, llamada TestRunner.
* Resultados de los tests ejecutados.

Lo primero que debemos realizar es la instalación de la librería JUnit en nuestro proyecto. Es posible que en todas las librerías que se descargaron para que funcione Selenium WebDriver ya se encuentren disponibles en ellas. Si no es así, en el siguiente [enlace](https://github.com/junit-team/junit/wiki/Download-and-Install) podemos encontrar las librerías necesarias para utilizar JUnit. 

Una vez tenemos las librerías descargadas, lo único que debemos hacer es crear nuestro proyecto y añadirlas.

Al igual que en TestNG, en JUnit, podemos crear igualmente dos tipos de archivos:

* JUnit Test es una clase java donde diseñaremos nuestros test individualmente. 
* Test Suite es una clase donde gestionamos, en caso de tener más de un JUnit Test, todos ellos.

###JUnit Test

Cuando creamos un archivo JUnit Test, se nos crea una estructura por defecto.

Al igual que en TestNG, **JUnit tiene anotaciones**, como puede verse encima de la definición de los métodos por defecto que se crean. Como ya se sabe, las anotaciones ayudan al framework JUnit a identificar rápidamente los métodos que tiene que ejecutar y cuándo los tiene que ejecutar.

A continuación vamos a ver las distintas anotaciones que tenemos disponibles en JUnit:

* **@Test:** identifica a un método como un “test method”.

* **@Before:** el método que vaya identificado con esta anotación, será ejecutado antes de cada test method. Se suele utilizar para preparar el ambiente de test, como inicializar la clase, leer datos de entrada, etc.

* **@After:** este método será ejecutado después de cada test method. Se suele utilizar para limpiar el ambiente de test, como puede ser eliminar datos temporales, reiniciar valores, etc.

* **@BeforeClass:** este método es ejecutado una única vez, antes del inicio de todos los test. El método que va definido con ésta anotación, deberá definirse como estático para poder trabajar en JUnit.

* **@AfterClass:** al contrario que el método anterior, este método es ejecutado una única vez al finalizar la ejecución de los tests. Igualmente, se debe definir como estático para que funcione correctamente.

* **@Ignore:** se ignora el test method. Es muy útil cuando por ejemplo se cambia algo de código de la aplicación y el test aún no se ha adaptado a los nuevos cambios.

Una vez hemos definido nuestro JUnit Test para ejecutarlo será de la misma manera que vimos en TestNG. Vamos a nuestro archivo y haciendo click con el botón derecho → Test File. Igualmente se ejecutarán los tests que hayamos anotado como @Test y nos devolverá el resultado. Del mismo modo, si alguno de nuestros test falla, la ejecución se detendrá, indicándonos el error, los tests que no se han ejecutado y los que se han ejecutado correctamente.

###Test Runner

Si tenemos varios tests por ejecutar, resulta demasiado tedioso tener que hacerlo uno por uno, por ello se utiliza una clase que se conoce como **Test Runner**, la cual ejecuta todos los tests que contenga, pudiendo ser un único test o múltiples.

Al crear un fichero Test Runner, se crea una estructura por defecto. Si observamos la primera línea del método main, la que contiene un objeto de la clase Result, podemos ver se hace mención a una clase llamada “FirefoxSuite”. Esta clase es una clase Test Suite (que se explicará más adelante) donde están contenidos otros múltiples tests.

También se podrán añadir los test uno por uno separados por comas.

Sin embargo, si tenemos múltiples test, lo más conveniente es realizar un Test Suite donde contenga todas esos múltiples tests y enlazar ese Test Suite en el Test Runner.

###Test Suite

Un **Test Suite** es un archivo donde se especifica un grupo de tests. Para crear un Test Suite son imprescindibles las anotaciones @RunWith y @Suite.SuiteClasses.

Lo único que hay que cambiar en una clase Test Suite son las dos anotaciones que se ven en la definición de la clase. La anotación @Suite.SuiteClasses({...}) es donde incluimos todos los JUnit Test que tengamos. 

**Toda la información sobre JUnit se puede obtener y ampliar de los siguientes enlaces:**

**[Enlace 1](http://www.vogella.com/tutorials/JUnit/article.html#unittesting)**

**[Enlace 2](http://www.toolsqa.com/java/junit-framework/junit-introduction/)**

**En estos enlaces podremos encontrar mayor información sobre JUnit y numerosos ejemplos.**


















