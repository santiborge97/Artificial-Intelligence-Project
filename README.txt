ESTRUCTURA C�DIGO FUENTE:

1� Celda: Aqu� tenemos la importaci�n de los correspondientes paquetes para realizar el proyecto

2� Celda: Aqu� se encuentra la funci�n PRINCIPAL. En esta funci�n primero se hace la llamada a otra funci�n(CalcularFotogramasClave)
que nos devuelve una lista con los frames soluci�n y una lista con todos los frames. Luego sacamos a partir del INPUTPATH y
el par�metro T una lista con las im�genes. Con esto sacamos las im�genes soluci�n que luego son escritas en la carpeta
OUTPUTPATH y se crea un video (funci�n crea video) en la misma carpeta.

3� Celda: Aqu� tenemos la funci�n CalcularFotogramasClave, en la cual primero sacamos las im�genes de la ruta especificada(con el par�metro T
 y el INPUTPATH). Luego sacamos los histogramas pudiendo elegir qu� t�cnica usar para juntar la informaci�n de los 3 histogramas de cada imagen(hacer la media o concatenarlos)
mediante el par�metro 't�cnica'. Despu�s aplicamos la funci�n aplicaKMedias a esa lista de histogramas que nos devuelve la lista con los centroides de los K cl�steres. Por �ltimo
hacemos una llamada a la funci�n CalculaCentroidesClases, que a partir de estos centroides nos devuelve la lista con los frames soluci�n.

4� Celda: Aqu� tenemos las dos funciones para juntar la informaci�n de los 3 histogramas de cada imagen. La primera funci�n es media_histogramas la cual en una lista va acumulando
los valores de cada histograma posici�n por posici�n para luego dividir entre 3 y sacar la media.La segunda funci�n es concatena_histogramas que se encarga de a�adir los histogramas
a una lista por lo que tendriamos una lista de tama�o tres veces el de un histograma(3*H)

5� Celda: Aqu� tenemos la funci�n aplicaKMedias. En esta funci�n hacemos una llamada a la funci�n KMeans de sklearn, pas�ndole como parametro la lista de frames y K(n�mero de cl�steres)
y a partir del resultado sacamos y devolvemos una lista con los centroides.

6� Celda: Aqu� tenemos la funci�n CalculaCentroidesClases, en la cual a partir de la lista de centroides devolvemos la lista de con los frames m�s cercanos a cada centroide seg�n un tipo
de distancia(euclidea,hamming o manhattan)

7� Celda: Aqu� tenemos las funciones para calcular las distancias seg�n sea Euclidea, Hamming o Manhattan.

8� Celda: Aqu� tenemos la funci�n creaVideo la cual a partir de las imagenes crea un video en el OUTPUTPATH mediante la funci�n VideoWriter(escribimos cada imagen 3 veces para que dure m�s tiempo
en el video)

9� Celda: Aqu� tenemos la celda donde hacemos la llamada a la funci�n PRINCIPAL, para ejecutar y probar el funcionamiento del programa.




INTERFAZ:

Para usar la interfaz hay que hacer lo siguiente:
1�)Abrir el fichero en Jupyter y ejecutar todas las celdas.
2�)Crear dos carpetas una (OUTPUTPATH) que ser� donde guardaremos las imagenes y el video, y la otra (INPUTPATH) donde estaran los frames del video a resumir.
3�)Con alg�n programa externo (Ej:Free Video to JPG Converter) sacar de un video los frames que queramos y guardarlos en la carpeta(INPUTPATH)
2�)A�adir en el fichero una celda en la que crearemos una variable con la ruta del INPUTPATH, otra con la ruta del OUTPUTPATH y tres variables para controlar
el tiempo (tiempo_inicial, tiempo_final, tiempo_ejecucion) en una de ellas realizar la llamada a la funci�n PRINCIPAL con los valores recomendados, por �ltimo ejecutar dicha celda. Ejemplo:

inputpath="D:\Archivos\Archivos\Desktop\FramesVideo1\Video1"
outputpath="D:\Archivos\Archivos\Desktop\GuardaImagen"

tiempo_inicial = time()
tiempo_final=PRINCIPAL(inputpath, outputpath, 40, 20, 256, 'media', 'manhattan')
tiempo_ejecucion=tiempo_final-tiempo_inicial
print('El tiempo de ejecuci�n es:',tiempo_ejecucion)



EXPERIMENTOS:
Para realizar los experimentos lo �nico  que hay que hacer es variar los par�metros de la llamada del ejemplo anterior [PRINCIPAL(INPUTPATH, OUTPUTPATH, T, K, H, tecnica, distancia)], despu�s
de cada experimento es recomendable borrar las im�genes guardadas en la carpeta OUTPUTPATH. Mirando el ejemplo anterior podemos ver que la instrucci�n print podemos ver el tiempo de ejecuci�n de
cada experimento, esto nos servir� para ver que valores son los mejores para cada par�metro.



