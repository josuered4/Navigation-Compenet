En este respositorio se mostrara como es la implementación 
de la libería de navigation-component, y su implementacion 
dentro de un proyecto Android que usa activities como xml.

<h2>Dependencias</h2>
Para el uso de esta liberia se requier de la instalacion de 
dos librerias:
<ul>
<li>navigation-fragment-ktx</li>
<li>navigation-ui-ktx</li>
</ul>

<h2>Implementacion</h2>

<h3>1er Paso</h3>
<li>Comenzaremos con la creación de 3 fragments y acada uno le
pondremos un color (definido en colors). </li>
<br>
<li>A continuación pasaremos con la creación de un grafo de navegación, 
que no es mas que un artefacto xml como los activities, en donde estaran 
regristados la mayoria de nuestros activities y fragments del proyectos, junto
a su relacion en tanto navegación, cabe mencionar que esto es mas visual de codigo</li>

    //crear dentro de res, un directorio navigation y 
    //dentro de este un navigation resource file

    res/navigation/main_graph.xml

<strong>Nota</strong><br>
<li>Agregar solo los componentes de nav, y seleccionar el principal. </li>
<li>Tambien desde acá podemos agregar los parametros a pasar por rutas.</li>

<h3>2do Paso "Contenedor Navegación"</h3>
En el caso de los Fragements, es importante definir un activity contenedor y no solo eso
sino tambien un elementos que muestre los fragments a los que podemos navegar. <br>
En este caso utilizaremos el "Main Activity" para mostrar los fragments, pero para esto necesitamos lo siguiente:
<li>Un FragmentContainerView: Es un elemento especial que nos permite cargar fragments, animaciones y navegacion</li>
<li>Un BottomNavigationView: Es otro elementos, por el cual mostraremos por botones las pantallas a acceder</li>

    <androidx.fragment.app.FragmentContainerView
            android:id="@+id/navHostFragment"
            android:name="androidx.navigation.fragment.NavHostFragment"
            app:navGraph="@navigation/main_graph"
            app:defaultNavHost="true"
            /> 

<em>El tamaño y ubicación puede quedar a ti disposición pero es importante, agregar
el id, la propiedad "name", asignarle el graph de nacegacion y el NavHost, para indicar que el activity
es el host.</em>


<h3>3re Paso "Rutas de Navegación"</h3>
Regresando a nuestro grafo, es importante enlazar los elementos en relacion con su navegacion,
esto lo podemos hacer con la UI de Android o agregando etiquetas "Action" en nuestro xml.

    <fragment android:id="@+id/secondFragment" 
              **Mas Propiedades**
        <action android:id="@+id/action_secondFragment_to_thirdFragment2" 
            app:destination="@id/thirdFragment"/>
    </fragment>

<em>Como podemos ver "action" tinene un id y un desination, que es la id del item a navegar 
<strong>Se recomienda hacer esto con la UI de Android</strong></em>