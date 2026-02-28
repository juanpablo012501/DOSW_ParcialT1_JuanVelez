# DOSW_ParcialT1_JuanVelez

## Preguntas

**1. Diagrama de contexto**

![Diagrama de context](/docs/uml/DiagContexto.jpg) 

**2. Patrones de diseño**

**A) Factory Method**  

* Tipo: creacional
* Este patron es aplicable a esta solución puesto que tenemos varios tipos de eventos,  
 a saber, talleres, conferencias y hackathones, así pues, el sistema puede pedirle a  
 la clase **Factory** (o **Creadora**) usando su método **createProduct** (en este caso: **createEvent**)  
 para crear el tipo de evento correcto. Algo a recalcar es que todos los tipos de evento  
 han de implementar la interfaz **Event** para que el método **createEvent** sea consistente
 en el tipo de retorno. Este patron nos permitirá a futuro extender con fácilidad los tipos  
 de eventos que haya, evitando acoplamiento.

**B) Observer**

* Tipo: comportamental
* Este patron puede ser muy bueno en para la plataforma puesto que quienes se hayan inscrito a un evento  
 se les debe notificar si el evento tiene algún cambio (cancelado, postergado, etc) estos cambios sólo  
 les interesa a quienes están inscritos al evento así podemos evitar gastar recursos enenviar notificaciones  
 a quienes no están suscritos (interesados en el evento) y además evitamos que los inscritos tengan que estar  
 pendientes del evento por otro medio.

**3. Requerimientos**  

+ **Funcionales**  
  1. Los ususarios (profesor, administradores) deben poder crear eventos ativos
     (este requerimiento aplica el patron creacional que seleccioné) 
  2. Los inscritos a un evento deben ser notificados sobre cambios en este
     (este requerimiento aplica el patron comportamental que seleccioné)
  3. Los usuarios deben poder inscribirse a un evento disponible
     (este requerimiento aplica el patron comportamental que seleccioné)

+ **No Funcianles**
   1. Todos los eventos tienen un estado confirmado o cancelado
   2. Los coreos deben terminar en **@mail.escuelaing.edu.co**

**4. Requerimientos más importantes**
1. Los ususarios (profesor, administradores) deben poder crear eventos activos.

![Diagrama casos de uso 1](/docs/uml/DCU1.jpg)
![Historia de usuario 1](/docs/uml/HU1.jpg)   
![Historia de usuario 2](/docs/uml/HU2.png)

2. Los usuarios deben poder inscribirse a un evento disponible.

![Diagrama casos de uso 1](/docs/uml/DCU2.jpg)  
![Diagrama casos de uso 1](/docs/uml/HU1.jpg)

**5. Especificación**  

1. Los ususarios (profesor, administradores) deben poder crear eventos activos.

| Campo       | Descripción                                                                                                                                                  |  
|-------------|--------------------------------------------------------------------------------------------------------------------------------------------------------------|
| ID          | RF-01                                                                                                                                                        |
| Nombre      | crear evento                                                                                                                                                 |
| Descripcion | el sistema debe permitir la creación de eventos y el tipo dado al personal autorizado                                                                        |
| Precondición | el usuario debe poder ingresar al sistema                                                                                                                    |
| Actor | profesores y administrativos                                                                                                                                 |
| Flujo | 1. el actor solicita la creación   <br/> 2. el sistema verifique que pueda  <br/> 3. el sistema solicita la información  <br/> 4. el sistema crea el evento |
| Diagrama casos de uso | ![Diagrama casos de uso 1](/docs/uml/DCU1.jpg)                                                                                                               |
| Poscondición | el evento debe ser creado y que este esté integrado al sistema                                                                                               |

2. Los usuarios deben poder inscribirse a un evento disponible.

| Campo       | Descripción                                                                                                                                                                                                                           |  
|-------------|---------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
| ID          | RF-02                                                                                                                                                                                                                                 |
| Nombre      | inscribirse a un evento                                                                                                                                                                                                               |
| Descripcion | el sistema debe encargarse de inscribir a quien lo solicite si es posible                                                                                                                                                             |
| Precondición | el usuario debe poder ingresar al sistema y el evento debe existir y no estar cancelado                                                                                                                                               |
| Actor | usuario (profesor, administrativo, estudiante)                                                                                                                                                                                        |
| Flujo | 1. el actor debe solicitar inscribirse a evento   <br/> 2. el sistema corrobora que el evento no este cancelado y haya cupo  <br/> 3. el sistema crea el observer para el usuario  <br/> 4. el sistema le da una respuesta al usuario |
| Diagrama casos de uso | ![Diagrama casos de uso 1](/docs/uml/DCU2.jpg)                                                                                                                                                                                        
| Poscondición | el usuario debe estar inscrito y poder recibir las notificaciones con respecto al evento                                                                                                                                              |

**6. Descomposición (Sprint)**  
* **Épica:** El usuario autorizado puede crear un evento
* **Historia de usuario:** Como usuario autorizado (profesor o administrativo) quiero crear  
 un evento para poder llevar a cabo mis roles como empleado.
* **Tarea1:** Crear la interfaz de eventos
* **Tarea2:** Crear la clase Factory.
* **Tarea3:** Crear las subclases de factory para cada tipo de evento.

**7. Diagrama de clases**
![Diagrama de clases](/docs/uml/DC.jpg)

+ Los principios solid que aplican son S ya que cada clase se encarga de su propia responsabiliadad y O porqué  
 la solución está diseñada para ser extendida, de tal manera que no se requiera hacer cambios a lo que ya se creo.