# Mini-Proyecto
# Python + GCP + BQ


#Iniciaremos sesion en Cloud SSH


gcloud auth list

gcloud config list project

#Habilitamos las siguientes API y permisos

gcloud services enable  cloudfunctions.googleapis.com 
gcloud services enable  run.googleapis.com 
gcloud services enable  bigquery.googleapis.com


gcloud projects add-iam-policy-binding PROJECT_ID  --member=user:USER_EMAIL --role=roles/bigquery.jobUser

gcloud projects add-iam-policy-binding PROJECT_ID  --member=user:USER_EMAIL --role=roles/run.admin

gcloud projects add-iam-policy-binding PROJECT_ID  --member=user:USER_EMAIL --role=eventarc.googleapis.com

#Creamos un bucket sencillo donde se almacenara los ficheros.

gcloud storage buckets create gs://NAME_BUCKET/ --location=REGION


#Creamos el Servicio Cloud Run para automatizar la parte de Storage to BigQuery.


<img width="1075" height="605" alt="Image" src="https://github.com/user-attachments/assets/c87f2c98-200c-41f8-aad8-183e499ff009" />


#Debemos de añadir la clausula de Eventrac para la conexion con Storarge en la seccion de Triggers.

<img width="823" height="625" alt="Image" src="https://github.com/user-attachments/assets/a5ae0191-2a72-4189-a355-99990d4d510c" />

#Tras ello, nos dirigimos a BigQuery para la creacion del Dataset.

<img width="549" height="208" alt="Image" src="https://github.com/user-attachments/assets/0f4a330f-d411-441d-9ba3-0d8d6c65c772" />


#Crearemos y asignaremos un nombre para el Dataset con la region de nuestro proyecto.

<img width="540" height="788" alt="Image" src="https://github.com/user-attachments/assets/612cd43f-8bd2-4ff5-bbc8-2b4d3981b50c" />




# Mini-Proyecto
# Airflow


#En esta seccion, debemos de activar la API de Composer, del cual al buscarlo procederemos a su creacion con la version mas moderna posible.

<img width="1034" height="475" alt="Image" src="https://github.com/user-attachments/assets/1104cf9f-9135-4948-ab60-d9062e7a74d3" />
#En este caso, añadiremos los parametros obligatorios con el nombre del servicio, el tag para su identificacion, el Service Account que hara referencia y el tamaño, en este caso elegimos la Small para el ejemplo del test.

<img width="697" height="769" alt="Image" src="https://github.com/user-attachments/assets/ccbd3be6-a2e5-4d12-92ad-b450ff9f1afa" />

#Tras ello y esperar aprox. 20 minutos, tendriamos listo el Composer 

<img width="1708" height="248" alt="Image" src="https://github.com/user-attachments/assets/55d6f6ff-4d6c-4d39-983e-137798767b00" />


<img width="1894" height="383" alt="Image" src="https://github.com/user-attachments/assets/f3b72e85-f998-4157-9b11-3c93f46976cc" />

#A la hora de subir un DAG al Airflow, es necesario crear el script PY del DAG a subir en su propia cuenta de Storage de Airflow. Dicha cuenta se crea al crear el servicio Composer.
#Partemos de una plantilla previamente descargada y preparada, cambiando los valores indicados en el fichero adjunto.


#Si tenemos el fichero preparado, tendremos que subir dicho fichero al Bucket del almacenamiento de Airlfow que esta en su "cuentadealmacenamiento"\dags

<img width="1574" height="466" alt="Image" src="https://github.com/user-attachments/assets/afc0874a-bea8-4493-bcbc-4efbe7ca0af6" />

#Debemos de esperar 2 minutos aprox para ver los resultados de forma automatica en el sistema de Airflow.

<img width="1886" height="257" alt="Image" src="https://github.com/user-attachments/assets/f8453030-3909-41fa-ad73-8d123e5daf3a" />

Veremos las rutas del DAG iniciadas y terminadas. Observaremos mas detalles que nos ofrece el DAG para su seguimiento

<img width="1349" height="688" alt="Image" src="https://github.com/user-attachments/assets/c8c2996f-17b5-41a6-b37b-2ff3759da570" />

<img width="1112" height="395" alt="Image" src="https://github.com/user-attachments/assets/544b2074-c97e-465c-a849-ddfb066e294e" />

