La API de RecyclerView
A diferencia del ListView, GridView, etc… el RecyclerView se dedica únicamente a lo que su nombre indica, reciclar, reutilizar recursos y evitar el uso reiterado del costoso findViewById, no se preocupa del aspecto visual, para ello está el LayoutManager, 
Una clase una tarea, esa es la filosofía que sigue la API del RecyclerView, un paquete de clases  internas cada una con una responsabilidad:
Adapter
ViewHolder
LayoutManager
ItemDecoration
ItemAnimator
Adapter
Esta clase se encarga de crear las Views necesarias para cada elemento del RecyclerView, además, está muy unida al ViewHolder, teniendo que ser indicado en la declaración de la clase, muchos pensaréis que esto no es nuevo, que Google ya aconsejara este patrón tiempo atrás, esta vez fuerza a utilizarlo, teniendo que ser indicado en la implementación del Adapter, un paso adelante, sin duda.

ViewHolder
Como venía diciendo, el patrón ViewHolder no es nada nuevo, de hecho Google, lo lleva recomendando desde hace tiempo, se puede pensar en el como un cache de las vistas, pudiendo reutilizarlas en vez de crearlas nuevamente.

LayoutManager
El LayoutManager se encarga del layout de todas las vistas dentro del RecyclerView, concretando con el LinearLayoutManager, permite entre otros acceder a elementos mostrados en la pantalla como el primer elemento, último, o por ejemplo, el último completamente visible, esto de forma horizontal o vertical, en el ejemplo se ha utilizado la disposición en vertical.

ItemDecorator
Otro eslabón importante, son los llamados ItemDecorator, estos permiten modificar los elementos del RecycleView, este además, ofrece además ofrece un elemento llamado insets (márgenes) que pueden aplicarse a las vistas sin necesidad de modificar los parámetros del layout.

ItemAnimator
La clase ItemAnimator como su nombre indica, anima el RecyclerView cuando se añade y se elimina un elemento, el RecyclerView utiliza un ItemAnimator por defecto.
El RecyclerView ha de saber cuando se inserta un elemento o se elimina, con elementos como ListViews, GridViews, etc… esto se conseguía llamando al método notifyDataSetChanged(), a nivel de performance, es bastante costoso, ya que redibuja todos los items en el layout, lo propio con el RecyclerView es usar el método notifyItemInserted() para añadir, y notifyItemRemoved() para eliminar, actualizando solo la parte apropiada.
