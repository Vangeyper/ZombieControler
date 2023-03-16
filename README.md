
//////////////////////
// ZOMBIE CONTROLER //
//////////////////////


OBJETIVO:
  Este proyecto trata de juntar mis 2 aficiones: la programación y los juegos de mesa. Siempre he querido programar una IA que permitiese tomar decisiones, pero después de muchos años reconozco que es un trabajo muy complejo y que requiere mucha matemática detrás, y esa no es una de mis aficiones. Pero lo que si que me veo capaz es de crear una IAI (término que me acabo de inventar y significaría Inteligencia Artificial Mía o de mí). Esta IAI trataría de jugar al juego de la forma en que yo lo haría si estuviera jugando. 
  Evidentemente serán decisiones previstas, es decir no será una IA deductiva ni capaz de los logros que esperamos hoy en día de estos algoritmos, sino algo sencillo que me permita jugar en modo solitario a algunos de mis juegos favoritos contra mi propio automa. 
  Estoy aprendiendo nuevos lenguajes de programación, aunque llevo mas de 25 años trabajando profesionalmente de analista / programador, y jugando en solitario no llevo tanto, un par de años.
  La idea es que la IAI crezca de forma progresiva, en cada versión del aplicativo debería poder actuar ante un número más elevado de situaciones de la misma forma en que lo haría yo mismo. 
  No tengo claro como voy a plantear el aplicativo en cuanto a la secuencia y las opciones que ofrecerá al usuario. Lo iré modificando sobre la marcha. Seguramente habrán varios intentos antes de dar con el correcto.
  Tampoco me voy a centrar en los efectos gráficos, para eso siempre se está a tiempo. 
  Aunque no pretendo centrarlo en un solo juego, inicialmente será una aplicación para jugar al Zombicide Black Plague y Green Horde. Aunque es verdad que tendrá o soportará las nuevas reglas que he incluído en este juego de tablero. Estas nuevas reglas siempre vendrán marcadas por el escenario al que juguemos, no recuerdo alguna regla que hubiese modificado de forma global al juego, siempre las defino en el escenario. Lo que pasa es que si esa regla me gusta y es un éxito la sigo aplicando al resto de escenarios.

___________________

IDEAS VERSION 1.0.0
___________________  

  ------------------------------------------
  Componentes virtuales o no del aplicativo:
  ------------------------------------------
      Tablero de juego o terreno
        Tendrá que existir una forma de localización para poder tomar deciciones espaciales.
      Heroes
        Protagonistas con unas determinadas cualidades que llevamos personalmente y con los que intentamos ganar la partida.
      Enemigos - Zombies
        Enemigos muy diversos que deben moverse y actuar por IAI según las reglas del juego que estemos jugando (inicialmente Zombicide, pero la idea es abrirlo a otros similares simplemente modificando las reglas).
      Personas
        Son al igual que los héroes personas pero sin armamento ni capacidad de combate, representan el objetivo fácil de los zombies y la razón prioritaria por la que los héroes deben luchar: salvarlos y evitar que se transformen.


  --------------------
  Secuencia del juego:
  --------------------

    La secuencia del juego es diferente según el juego al que estemos jugando, pero si nos centramos en Zombicide tenemos que se dan:
       A - Fase de preparación

            1. Se escoge el escenario a jugar. Al hacerlo determinaremos:
                1.1. el Tablero de Juego: obstaculos y terreno a tener en cuenta 
                1.2. la cantidad de héroes y su posición inicial
                1.3. los objetivos de victoria y derrota
                1.4. las zonas de aparición
                1.5. las reglas especiales del escenario                
                1.6. tipos de enemigos a los que nos podremos enfrentar
                1.7. enemigos que aparecen inicialmente en el tablero ya desplegados
                1.8. ciudadanos (que no héroes) que aparecen en el juego ya desplegados
            2. El usuario determina los héroes que lleva, si no los limita el escenario podrá elegir entre los que tengamos.
            3. Para cada héroe el usuario selecciona el equipo inicial y su ubicación.

       B - Fase de héroes

            Cada héroe realiza sus acciones (el juego de tablero establece que se deben realizar secuencialmente, tanto por héroe como por jugador). La Aplicación permitirá jugar de forma secuencial como indica el juego de Tablero o de forma totalmente cooperativa, realizando las acciones en el orden deseado por el jugador con cada uno de sus héroes, incluso pudiendo un héroe realizar parte de sus acciones, dejar que prosiga otro héroe con parte de las suyas y después terminar el resto de acciones de todos los héroes.
            Las acciones que puede realizar cada héroe las definen las reglas del juego, el escenario, el nivel del héroe, sus habilidades y equipo.
            Las genéricas según el juego serían:
                 1. Moverse
                 2. Buscar equipo
                 3. Abrir una puerta (esta acción puede conllevar una aparición de zombies en la zona)
                 4. Reorganizar inventario
                 5. Intercambiar equipo
                 6. Combate cuerpo a cuerpo CaC
                 7. Combate a distancia CaD
                 8. Combate con mágia CcM
                 9. Ejecutar encantamiento
                10. Coger o Activar un objeto
                11. Hacer Ruido de forma deliverada
                12. No hacer ninguna acción
            
       C - Fase de Zombies (esta fase es la que inicialmente hará uso de la IAI)

            1. Activaciones: cada enemigo ejecuta su activación que consistirá en movimiento hacia objetivos humanos o del escenario y ataques siempre que puedan o lo indique el escenario.
            2. Apariciones de nuevos zombies: se añadirán al Tablero nuevos zombies según la aleatoriedad propia de las cartas del juego en las zonas de aparición. 

            NOTA: las apariciones según el juego están sujetas al número de miniaturas de que disponga el jugador, por lo que dentro de la aplicación podremos establecer ese número en la fase de preparación si así lo desea el jugador, de esta forma la aplicación tendrá en cuenta activaciones adicionales en los casos en que no tengamos miniaturas de ese tipo. 

       D - Control de final de partida o de Victoria

            1. Comprobar las reglas del escenario que indican si los héroes han ganado la partida o si por el contrario son los zombies los que la han ganado. Si el escenario no indica lo contrario se aplicarán las reglas básicas del juego:
                a> Los héroes pierden la partida si mueren todos.
                b> Los héroes pierden la partida si escapa un nigromante logra escapar habiendo 6 fichas de aparición en el Tablero.
                c> Los héroes ganan la partida si cumplen todos los objetivos del escenario.


  ----------------------------
  OBJETOS a Modelar en la App:
  ----------------------------
  
    HEROE
      Definición de nuestros héroes: rasgos como la vida, acciones, habilidades, ... 
    ZOMBIE
      Todo enemigo será catalogado dentro de la aplicación como un zombie, de momento no está abierto el que existan enemigos que no sean zombies, eso quedará para versiones posteriores.
    OBJETO DEL EQUIPO
      El equivalente a una carta de equipo.
    TABLERO  
    CIUDADANO
    TURNO
      No se si está definido como objeto o será realmente el desarrollo de la aplicación una vez iniciada la partida la que lo determina, pero en todo caso lo que quiero expresar es que de alguna manera se ha definir esa secuencia de acciones.
