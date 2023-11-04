# AnimationController
# Descripción
Este proyecto te guiará a través de la creación y configuración de un Animator Controller para un enemigo esqueleto en Unity. Aprenderás a gestionar animaciones de movimiento, ataques y transiciones entre ellas. También, se incluye la programación del comportamiento del enemigo y la detección de golpes en el jugador.

# Requisitos
Unity 2022.3.10 o posterior

# Configuración Inicial
Agrega tus activos al proyecto, incluyendo el "First Person Controller" y el modelo de enemigo esqueleto con sus animaciones.
![image](https://github.com/Ariel454/AnimationController/assets/121766763/c4be7b3b-9726-4150-a5ce-11319267f5dd)

Coloca el enemigo en el escenario y adjunta un script.
![image](https://github.com/Ariel454/AnimationController/assets/121766763/868f3f69-a1c7-4090-90c0-0a7b9551c0ac)

Crea un "Animator Controller" para el enemigo.
![image](https://github.com/Ariel454/AnimationController/assets/121766763/fe8402f6-f3cb-4405-8c97-687563853ada)

Agrega dos estados de animación: uno para caminar y otro para estar de pie. Asigna las animaciones correspondientes y crea transiciones entre estos estados.
![image](https://github.com/Ariel454/AnimationController/assets/121766763/8c0023a3-bde0-4aa3-81e8-397248d8966c)

Configura las transiciones desactivando "Has Exit Time" y estableciendo condiciones para las transiciones entre estar de pie y caminar.
![image](https://github.com/Ariel454/AnimationController/assets/121766763/9d4f0108-6d8b-45be-825f-782f958d0b2d)

Repite el proceso para la animación de correr, creando y enlazando estados.
![image](https://github.com/Ariel454/AnimationController/assets/121766763/b3f0d3bc-d96d-46a8-a364-2ba10c7e5054)

Configura los parámetros para los booleanos de cada enlace de transición para activar y desactivar las animaciones.
![image](https://github.com/Ariel454/AnimationController/assets/121766763/89460c3d-504f-4e00-8655-2be7afabba05)

Para las animaciones, asegúrate de configurar el "Loop Time" en "Walk" para que la animación no se detenga mientras el personaje se mueve.
![image](https://github.com/Ariel454/AnimationController/assets/121766763/4beb73bc-32bb-418e-89a8-190befbda34e)

En el panel de Animation, selecciona la animación "Attack" y agrega un evento "Final_Ani()" al último segundo de la animación.
![image](https://github.com/Ariel454/AnimationController/assets/121766763/ee094b8b-a850-4485-b9a2-898c4382da56)

# Programación del Comportamiento del Enemigo
Variables Públicas:
rutina: Un entero que controla la rutina actual del enemigo.
cronometro: Un valor de tiempo que mide el tiempo transcurrido.
ani: Una referencia al componente Animator del enemigo para controlar sus animaciones.
angulo: Una variable de tipo Quaternion que almacena un ángulo de rotación.
grado: Un valor de ángulo en grados.
target: Una referencia al GameObject del jugador.
atacando: Un booleano que indica si el enemigo está atacando.
Método Start:
Se ejecuta al inicio del juego.
Inicializa la referencia al componente Animator y encuentra al jugador por su nombre ("Player").
Método Update:
Se llama en cada frame del juego y gestiona el comportamiento del enemigo.
Método Comportamiento_Enemigo:
Controla el comportamiento del enemigo en función de la distancia entre el enemigo y el jugador.
Si la distancia es mayor que 5 unidades:
Desactiva la animación de correr ("run").
Incrementa el cronómetro.
Si el cronómetro supera 4 segundos, elige una rutina aleatoria.
Dependiendo de la rutina, el enemigo puede quedarse quieto o moverse en una dirección aleatoria.
Si la distancia al jugador es menor o igual a 5 unidades:
El enemigo mira hacia el jugador y se mueve hacia él.
Si la distancia es mayor que 1 unidad y no está atacando, el enemigo corre hacia el jugador.
Si la distancia es menor o igual a 1 unidad, el enemigo inicia una animación de ataque y establece "atacando" en verdadero.
![image](https://github.com/Ariel454/AnimationController/assets/121766763/ec602bd4-65ef-49d0-ba47-532bda50dca8)
![image](https://github.com/Ariel454/AnimationController/assets/121766763/e5507a8d-df2a-497f-8e4d-4cbcb243f9a3)

# Método Final_Ani:
Llamado cuando la animación de ataque ha finalizado.
Desactiva la animación de ataque y establece "atacando" en falso.
![image](https://github.com/Ariel454/AnimationController/assets/121766763/442d26c9-4aec-44fa-aca0-192d54952f8d)

# Detección de Golpes y Daño
Asigna un "Box Collider" a tu arma y configúralo como "Trigger".
![image](https://github.com/Ariel454/AnimationController/assets/121766763/29d65e0f-d47b-44a0-b60f-26d837889303)

Activa el "Box Collider" en las secciones de tiempo de la animación donde se efectúan los golpes.
![image](https://github.com/Ariel454/AnimationController/assets/121766763/d56b68c8-bf15-43eb-9888-24906059328d)

En el script del jugador, implementa un método para detectar colisiones con el "Box Collider" del arma del enemigo y aplicar daño.
![image](https://github.com/Ariel454/AnimationController/assets/121766763/91424128-d6cb-4e81-a29c-885d25d4629e)
