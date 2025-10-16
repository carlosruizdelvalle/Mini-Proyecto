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
