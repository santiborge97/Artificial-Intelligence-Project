ESTRUCTURA CÓDIGO FUENTE:

1ª Celda: Aquí tenemos la importación de los correspondientes paquetes para realizar el proyecto

2ª Celda: Aquí se encuentra la función PRINCIPAL. En esta función primero se hace la llamada a otra función(CalcularFotogramasClave)
que nos devuelve una lista con los frames solución y una lista con todos los frames. Luego sacamos a partir del INPUTPATH y
el parámetro T una lista con las imágenes. Con esto sacamos las imágenes solución que luego son escritas en la carpeta
OUTPUTPATH y se crea un video (función crea video) en la misma carpeta.

3ª Celda: Aquí tenemos la función CalcularFotogramasClave, en la cual primero sacamos las imágenes de la ruta especificada(con el parámetro T
 y el INPUTPATH). Luego sacamos los histogramas pudiendo elegir qué técnica usar para juntar la información de los 3 histogramas de cada imagen(hacer la media o concatenarlos)
mediante el parámetro 'técnica'. Después aplicamos la función aplicaKMedias a esa lista de histogramas que nos devuelve la lista con los centroides de los K clústeres. Por último
hacemos una llamada a la función CalculaCentroidesClases, que a partir de estos centroides nos devuelve la lista con los frames solución.

4º Celda: Aquí tenemos las dos funciones para juntar la información de los 3 histogramas de cada imagen. La primera función es media_histogramas la cual en una lista va acumulando
los valores de cada histograma posición por posición para luego dividir entre 3 y sacar la media.La segunda función es concatena_histogramas que se encarga de añadir los histogramas
a una lista por lo que tendriamos una lista de tamaño tres veces el de un histograma(3*H)

5ª Celda: Aquí tenemos la función aplicaKMedias. En esta función hacemos una llamada a la función KMeans de sklearn, pasándole como parametro la lista de frames y K(número de clústeres)
y a partir del resultado sacamos y devolvemos una lista con los centroides.

6ª Celda: Aquí tenemos la función CalculaCentroidesClases, en la cual a partir de la lista de centroides devolvemos la lista de con los frames más cercanos a cada centroide según un tipo
de distancia(euclidea,hamming o manhattan)

7ª Celda: Aquí tenemos las funciones para calcular las distancias según sea Euclidea, Hamming o Manhattan.

8ª Celda: Aquí tenemos la función creaVideo la cual a partir de las imagenes crea un video en el OUTPUTPATH mediante la función VideoWriter(escribimos cada imagen 3 veces para que dure más tiempo
en el video)

9ª Celda: Aquí tenemos la celda donde hacemos la llamada a la función PRINCIPAL, para ejecutar y probar el funcionamiento del programa.




INTERFAZ:

Para usar la interfaz hay que hacer lo siguiente:
1º)Abrir el fichero en Jupyter y ejecutar todas las celdas.
2º)Crear dos carpetas una (OUTPUTPATH) que será donde guardaremos las imagenes y el video, y la otra (INPUTPATH) donde estaran los frames del video a resumir.
3º)Con algún programa externo (Ej:Free Video to JPG Converter) sacar de un video los frames que queramos y guardarlos en la carpeta(INPUTPATH)
2º)Añadir en el fichero una celda en la que crearemos una variable con la ruta del INPUTPATH, otra con la ruta del OUTPUTPATH y tres variables para controlar
el tiempo (tiempo_inicial, tiempo_final, tiempo_ejecucion) en una de ellas realizar la llamada a la función PRINCIPAL con los valores recomendados, por último ejecutar dicha celda. Ejemplo:

inputpath="D:\Archivos\Archivos\Desktop\FramesVideo1\Video1"
outputpath="D:\Archivos\Archivos\Desktop\GuardaImagen"

tiempo_inicial = time()
tiempo_final=PRINCIPAL(inputpath, outputpath, 40, 20, 256, 'media', 'manhattan')
tiempo_ejecucion=tiempo_final-tiempo_inicial
print('El tiempo de ejecución es:',tiempo_ejecucion)



EXPERIMENTOS:
Para realizar los experimentos lo único  que hay que hacer es variar los parámetros de la llamada del ejemplo anterior [PRINCIPAL(INPUTPATH, OUTPUTPATH, T, K, H, tecnica, distancia)], después
de cada experimento es recomendable borrar las imágenes guardadas en la carpeta OUTPUTPATH. Mirando el ejemplo anterior podemos ver que la instrucción print podemos ver el tiempo de ejecución de
cada experimento, esto nos servirá para ver que valores son los mejores para cada parámetro.



