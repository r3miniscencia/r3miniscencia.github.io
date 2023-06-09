- Basado en [[GTD]] y en un [video de Youtube de OneStutteringMind](https://youtu.be/nieOiG8LGa0), pero ligeramente adaptado por mi.
- ## Flujo de trabajo
	- ### Fase de captura de información
		- Añadir directamente en la agenda las cosas que tenga en la cabeza y no quiera olvidar, con el tag ` #inbox`
		- ~~También se pueden añadir desde el móvil enviando un mensaje a Telegram y usando mi script para descargarlo~~
	- ### Fase de análisis (clarify)
		- Se revisan los elementos de la etiqueta `#inbox` y se mira en qué caso se está:
			- Requiere acción (yo, o alguien, debe hacer algo acerca de este tema, para que cierto proyecto avance)
			- No requiere acción (es material de lectura o aficiones)
	- ### Fase de Organización
	  Según la clasificación que se haya hecho en el análisis, llega el momento de usar las primitivas apropiadas que nos da logseq
		- **Requiere acción**
			- **La acción ha de ser en un día concreto**
			  collapsed:: true
			  Básicamente son eventos **de calendario**. 
			  Añadirle mediante ==/date== un enlace a la fecha en que debe hacerse (opcionalmente anotar en otro calendario externo como Google Calendar si es importante que no se olvide, como una cita médica, etc.)
			- **La acción decido retrasarla a otro día**
			  collapsed:: true
			  Añadir con ==SCHEDULED== la fecha en la que quiero que resurja mediante. Opcionalmente puede tener también un `DEADLINE`
			- **Hacer lo antes posible**
			  collapsed:: true
			  Crear una tarea ==TODO== y si es posible ponerle un ==DEADLINE==
			- **Delegar**
			  collapsed:: true
			   Marcarla como ==WAITING== (se le puede poner también deadline o scheduled)
		- **No requiere acción**
			- **Material de referencia**
			  collapsed:: true
			  Crear una página para él. Usar las etiquetas apropiadas, o properties, para que sea fácil encontrar de nuevo esta información. El uso de templates ayuda aquí
			- **Someday/Maybe**
			  Etiquetar como `#maybe`. Opcionalmente ponerle `#card` para que a través de las flashcards nos recuerde esos temas y no queden para siempre enterrados
			- **Recordatorio**
			  collapsed:: true
			  Etiquetar con la jerarquía `#para/` (ej: `#para/leer`) y opcionalmente ponerle `#card`
			- **Basura**
			  collapsed:: true
			  Si al procesar el elemento de `#inbox` decides que al final no era útil, simplemente bórralo. No almacenes basura.
- # Revisión y trabajo
  Todo lo almacenado con este método se revisa básicamente de dos formas
	- Lo que requiere acción. 
	  Mediante queries avanzadas en la página [[Planificador]]
		- **Hoy** La tarea para hacer hoy está clasificada "por urgencia" en cuatro grandes bloques
			- **Tareas ya vencidas**
			  Tienen deadline en el pasado y aún están en estado pendiente. Son por tanto cosas urgentes en las que habría que ponerse a trabajar cuanto antes
			- **Tareas que vencen hoy**
			  Tienen deadline para hoy
			- **Tareas de hoy**
			  Son tareas "de calendario" para hoy (provienen de bloques que han enlazado al día de hoy), o bien tareas scheduled para comenzar hoy.
			- **Continuar con...**
			  Son tareas que estaban scheduled para días atrás. Por tanto seguramente se ha comenzado a trabajar ya en ellas, pero aún no se han terminado. Pueden tener deadlines, pero éstos pueden estar aún en el futuro, por lo que no son tan urgentes (si el deadline fuese hoy aparecería también en "Tareas que vencen hoy")
		- **Mañana**
		  Son tareas que tienen una fecha de scheduled o deadline o enlace al diario de mañana.
		- **Resto de la semana**
		  Son tareas que tienen una fecha de scheduled o deadline o enlace al diario para una fecha posterior a mañana y anterior a 8 días en el futuro.
		- **Sin día**
		  Son cualquier tarea pendiente (estado to-do) para la que no se ha fijado deadline ni fecha de comienzo con scheduled. No debería haber muchas tareas aquí, lo mejor es revisarlas y ponerles alguna fecha.
		- **Esperando**
		  Son todas las tareas con estado "waiting"
	- Tras revisar el [[Planificador]], se elige una tarea sobre la que comenzar a trabajar y se cambia su estado a "doing".
		- Eso la hará desaparecer de su categoría y aparecer en cambio al principio del [[Planificador]] en la sección 🔨 Now (haciendo)
		- Cuando se deje de trabajar en esa tarea se pasa de nuevo al estado "to-do", o bien "done" si se ha terminado. Logseq muestra el tiempo total en que estuvo en el estado "doing".
	- Lo que no requiere acción
		- Se puede consultar la etiqueta #para para encontrar cosas pendientes de mirar
		- En la etiqueta #maybe hay cosas que alguna vez nos interesaron y dejamos "en la incubadora"