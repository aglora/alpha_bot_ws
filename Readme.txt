Simulación en Gazebo de un robot móvil con ruedas enconfiguración diferencial desarrollado en ROS.

Basado en paquete existente: https://github.com/ros-mobile-robots/diffbot

Trabajo desarrollado en cuanto a localización, control de alto nivel y planificación de caminos con posibilidad de extensión a planificación de caminos/trayectorias.

LOCALIZACIÓN: Planteamos la localización del robot como resultado de la fusión sensorial de los sensores que lleva a bordo: IMU, Lidar y medidas de velocidad. En este trabajo, se presentan tres métodos de localización basados en la fusión mediante un EKF ...

CONTROLADOR ALTO NIVEL: Adaptación Pure-Pursuit Nos hemos basado en la técnica de control de alto nivel de persecución pura. A partir de ella hemos hecho una serie de adaptaciones particulares para nuestra configuración y hemos planteado algunas simplificaciones para su implementación...

PLANIFICACIÓN DE CAMINOS: se ha decidido usar el algoritmo de Dijkstra para calcular el camino de mínimo coste hasta el punto objetivo...

Toda la documentación relativa a resultados experimentales puede verse en la memoria de trabajo.

------------------------------------------------------------------------------------------------------------------------------

En este workspace de ROS, podemos encontrar en la carpeta /src/alpha_bot los distintos paquetes desarrollados:
*/alpha_bot_control: Aquí se encuentra nuestro controlador de alto nivel variante del pure-pursuit.
*/alpha_bot_description: Contiene el modelo del robot en xacro.
*/alpha_bot_localization: Permite elegir entre ground_truth, odometría con encoders, odometría láser, integración de todo ello por EKF.
*/alpha_bot_odometry: Contiene la propia odometría por giro en ruedas.
*/alpha_bot_planner: Contiene el planificador de Dijkstra, además de lanzar move_base para costmap.
*/alpha_bot_simulation: Se encarga de lanzar la simulación en Gazebo, la representación visual de datos en RVIZ, todos los paquetes necesarios para el funcionamiento íntegro del sistema, y rqt_steering para permitir variar parámetros del controlador de alto nivel.

Si se desea lanzar el programa, puede usarse el script ScriptEjecucion.sh con el comando:
./ScriptEjecucion.sh

Si se desea lanzar por uno mismo, puede usarse sim.launch, ya que este llamará a todo lo necesario. Para ello:
source devel/setup.sh
roslaunch alpha_bot_simulation sim.launch
