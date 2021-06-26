Ejercicio 5: Documentación


  ## Criterios de exclusión de ejemplos
  1. Se eliminan los valores extremos que no sean relevantes para la predicción de valores de las propiedades, con el metodo IQR
  2. Se elimina la variable Bedroom2, ya que la variable Rooms es mucho mas informativa.
  3. Debido a que las variables BuildingArea y YearBuilt tienen muchos datos faltantes se decide retirarlas del df
  4. Address, Method, SeleerG, Date, Lattitude, Longitude, Regionname : se descartan porque considero que no aportan informacion relevante o aportan informacion duplicada que se puede inferir de otra variable.
  5. Quitamos price porque es el target, no se usa para el procesamiento.
  6. También sacamos zipcode y postcode debido a que fueron utilizados para la realización del merge y no lo utilizaremos para predecir el precio
  7. Antes de transformar la matriz esparsa a densa, se evalua la dimension final antes de la transformacion teniendo como limite 10 MB. 


  ## Características seleccionadas
  ### Características categóricas
  1. Suburb: Barrio. 253 valores posibles
  2. CouncilArea: Area municipal. 29 valores posibles
  3. Type: tipo de propiedad. 3 valores posibles (casa, monoambiente, duplex)
  
  Todas las características categóricas fueron codificadas con un método OneHotEncoding utilizando un agrupamiento para obtener un minimo de valores frecuentes que varia segun la variable.
  
  Luego de realizar imputacion de CouncilArea en funcion de los Suburbios, se decide eliminar la variable Suburb ya que CouncilArea contiene informacion mas global de la ubicacion
  
  ### Características numéricas
  1. Rooms: Cantidad de habitaciones
  2. Distance: Distancia al centro de la ciudad.
  3. airbnb_mean_price: Se agrega el precio promedio diario de publicaciones de la plataforma AirBnB en el mismo código postal. [Link al repositorio con datos externos].
  4. Price: Precio de la propiedad en dolares
  5. Postcode/Zipcode: codigo postal
  6. Car: Cantidad de cocheras.
  7. airbnb_count_price: Se agrega la cantidad de valores de precios iguales en el mismo codigopostal
     utilizando publicaciones de la plataforma AirBnB [Link al repositorio con datos externos].
  8. Landsize: tamaño del terreno 
  9. Property Count: cantidad de propiedades que existen en el suburbio.
  10. Building Area : dimension de area construida
  11. Yearbuilt: Año construido.
  
  Las variables Rooms, Car y Bathroom fueron codificadas utilizando OneHotEncoding al considerarlas variables numericas discretas.
  
  
  ### Transformaciones:
  1. Se Reemplazaron los datos 0 en la variable Bathroom por 1
  2. La variable CAR fue imputada reemplazando los datos nulos con 0  utilizando el metodo fillna
  3. Para las variables categóricas seleccionadas, se agrupo o combino las categorías poco frecuentes para asegurar que todos los grupos tengan un número mínimo de registros usando el metodo replace
  4. La columna `CouncilArea` fue imputada utilizando el método k vecinos mas cercanos, en funcion de la variable 'Suburb'
  5. Todas las características numéricas fueron escaladas.
  6. Se recuperaron las columnas `YearBuilt` y 'BuildingArea' y se incorporaron al df mediante el metodo left-join al df ya procesado. Las mismas fueron imputadas utilizando el algoritmo k vecinos mas cercanos pero con todas las variables del df.
  7. Las variables zipcode, airbnb_record_count y airbnb_price_day_mean fueron imputadas utilizando el metodo KNN imputer con n=5
  8. 
  
  
  
 ### Datos aumentados
  1. Se combino nuestro df original con el df AIRBNB para obtener mayor informacion para predecir el precio, a partir de los zipcode realizamos el merge.
  2. Se crea el diccionario para utilizar en el DictVectorizer la matriz anterior con los datos ya escalados.
  3. Se tiene como criterio representar el 90% de la varianza con los componentes principales, por ende se agregan las 22 primeras columnas obtenidas a través del método de PCA.
     
     
     

  

  