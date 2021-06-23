Ejercicio 5: Documentación

Entregable parte 1


  ## Criterios de exclusión de ejemplos
  1. Se eliminan los valores extremos que no sean relevantes para la predicción de valores de las propiedades.
  2. Se elimina la variable Bedroom2, ya que la variable Rooms es mucho mas informativa.
  3. Debido a que las variables BuildingArea y YearBuilt tienen muchos datos faltantes se decide retirarlas del df
  4. Address, Method, SeleerG, Date, Lattitude, Longitude, Regionname : se descartan porque considero que no aportan informacion relevante o aportan informacion duplicada que se puede inferir de otra variable.
  

  ## Criterios de inclusion
  1. A partir del DF AIRBNB incorporamos a nuestro DF original la columna price, a la cual le aplicamos el promedio. El merged se hizo a traves de la variable zipcode luego de unificar sus valores.


  ## Características seleccionadas
  ### Características categóricas
  1. Suburb: Barrio. 253 valores posibles
  2. CouncilArea: Area municipal. 29 valores posibles
  3. Type: tipo de propiedad. 3 valores posibles (casa, monoambiente, duplex)
  
  
   Todas las características categóricas fueron codificadas con un
  método OneHotEncoding utilizando un agrupamiento para obtener un 
  minimo de valores frecuentes que varia segun la variable.
  
  ### Características numéricas
  1. Rooms: Cantidad de habitaciones
  2. Distance: Distancia al centro de la ciudad.
  3. airbnb_mean_price: Se agrega el precio promedio diario de publicaciones de la plataforma AirBnB en el mismo código 
  postal. [Link al repositorio con datos externos].
  4. Price: Precio de la propiedad en dolares
  5. Postcode/Zipcode: codigo postal
  6. Car: Cantidad de cocheras.
  7.airbnb_count_price: Se agrega la cantidad de valores de precios iguales en el mismo codigopostal
     utilizando publicaciones de la plataforma AirBnB [Link al repositorio con datos externos].
  8. Landsize: tamaño del terreno 
  9. Property Count: cantidad de propiedades que existen en el suburbio.
  
  
  ### Transformaciones:
  1. Se Reemplazaron los datos 0 en la variable Bathroom por 1
  2. La variable CAR fue imputada reemplazando los datos nulos con 0  utilizando el metodo fillna
  3. Para las variables categóricas seleccionadas, se agrupo o combino las categorías poco frecuentes para asegurar que todos los grupos tengan un número mínimo de registros usando el metodo replace
  4. La columna `CouncilArea` fue imputada utilizando el método k vecinos mas cercanos, en funcion de la variable 'Suburb'
  5. Todas las características numéricas fueron escaladas.
  
 
  
  ### Datos aumentados
  
     
     
     
Entregable parte 2


## Criterios de exclusión de ejemplos
  1.

  ## Características seleccionadas
  ### Características categóricas
  1. Type: tipo de propiedad. 3 valores posibles (casa, monoambiente, duplex)
  3. CouncilArea: Area municipal. 33 valores posibles
  4. Suburb: Barrio. 314 valores posibles

  
  Todas las características categóricas fueron codificadas con un
  método OneHotEncoding utilizando un agrupamiento para obtener un 
  minimo de valores frecuentes que varia segun la variable.
  
  ### Características numéricas
  1. Rooms: Cantidad de habitaciones
  2. Distance: Distancia al centro de la ciudad.
  3. airbnb_mean_price: Se agrega el precio promedio diario de 
     publicaciones de la plataforma AirBnB en el mismo código 
     postal. [Link al repositorio con datos externos].
  4.Price: Precio de la propiedad en dolares
  5.Zipcode: codigo postal
  6.Car: Cantidad de cocheras.
  7.airbnb_count_price: Se agrega la cantidad de valores de precios iguales en el mismo codigopostal
     utilizando publicaciones de la plataforma AirBnB [Link al repositorio con datos externos].
  8. Bathroom: cantidad de baños
  9. Building Area : dimension de area construida
  10.Yearbuilt: Año construido.
  11.Property Count: cantidad de propiedades que existen en el suburbio.
  
  ### Transformaciones:
  1. Todas las características numéricas fueron escaladas.
  2. La columna `CouncilArea` fue imputada utilizando el método k vecinos mas cercanos, en funcion de la variable 'Suburb'
  3. Las columnas `YearBuilt` y 'BuildingArea' fueron imputadas utilizando el 
     algoritmo k vecinos mas cercanos pero con todas las variables del df.
  4. ...

  ### Datos aumentados
  1. Se agregan las 5 primeras columnas obtenidas a través del
     método de PCA, aplicado sobre el conjunto de datos
     totalmente procesado.