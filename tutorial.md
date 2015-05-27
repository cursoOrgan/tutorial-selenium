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
* **5. JUnit4**
* **6. TestNG**
* **7. JUnit4 vs TestNG**

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


















