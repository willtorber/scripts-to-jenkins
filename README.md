# Learning about Jenkins

Dummy scripts used to test `Jenkins` functionalities.


## Conectando a GitHub con Jenkins

Es posible conectar un repositorio de GitHub a Jenkins, de modo que cuando ocurra un evento en el repositorio (por ejemplo, un *push*) automaticamente se ejecute un *build* del source code. Para que esto sea posible se deben realizar algunas configuraciones en Jenkins y GitHub.

### Jenkins:
1. Verificar que el **GitHub plugin** esté instalado (en caso de no estarlo proceder a instalarlo).
2. Se crea el Job de acuerdo a la necesidad del proyecto.
3. En la sección _General_ se marca la opción "Github Project" y se ingresa la URL de acceso del repositorio.
4. En la sección _SCM (Source Code Management)_ se marca la opción "Git", y se ingresa la URL del repositorio que permite la clonación (el host de Jenkins debe tener instalado Git).
    + En el apartado "Branches to build" se especifica el branch que Jenkins identificará y monitoreará. 
    + En caso de presentarse este error: **(403) No valid crumb was included in the request Jenkins**, en este [post](https://stackoverflow.com/questions/44711696/jenkins-403-no-valid-crumb-was-included-in-the-request) de Stackoverflow se plantean soluciones.
3.	En la sección _Build Triggers_ se marca la opción "GitHub hook trigger for GITScm polling".
### GitHub:
1.	Ingresar al repositorio de GitHub.
2.	Ingresar en la sección Settings -> Webhooks.
    +	Webhooks permite que servicios externos sean notificados cuando ocurren ciertos eventos. Cuando ocurra un evento especifico (por ejemplo, un push), GitHub enviará una solicitud POST a cada una de las URL proporcionadas en la configuración. Obtenga más información en la [Guía de Webhooks](https://developer.github.com/webhooks/).
3.	Se añade un nuevo Webhook.
4.	Se añade la Payload URL (si la URL no finaliza en */github-webhook/*, GItHub lanzara un error.)
5.	Por ultimo, se selecciona la opción "Just the push event".
