# Proyecto Biblioteca Spring Boot

Proyecto desarrollado en **Spring Boot** que permite gestionar libros y autores, usando **PostgreSQL** como base de datos y consumiendo la API pública de **Gutendex** para obtener información de libros.

---

## 📝 Descripción

Esta aplicación es un backend para gestionar libros y autores de una biblioteca. Sus funcionalidades principales incluyen:  

- Registrar libros y autores automáticamente desde la API de **Gutendex**.  
- Listar libros y autores registrados en la base de datos.  
- Filtrar autores vivos en un determinado año.  
- Filtrar libros por idioma.  
- Transformar datos obtenidos de la API a objetos DTO (`LibroDTO`, `AutorDTO`).  
- Manejo de respuestas personalizadas mediante objetos `DatosRespuesta`.  
- Configuración de **CORS** para permitir solicitudes desde aplicaciones frontend.  
- Consola interactiva para ejecutar acciones sin necesidad de frontend.

---

## 🛠 Tecnologías utilizadas

- Java 21
- Spring Boot  
- Spring Data JPA  
- PostgreSQL  
- Maven  
- API pública: [Gutendex](https://gutendex.com/)  

---

## 📂 Estructura del proyecto
Biblioteca backend

src

main

java

└── com.aluracursos.biblioteca

├── config


│ └── CorsConfiguration.java

├── controller

│ └── LibroController.java

├── dto

│ ├── AutorDTO.java
│ └── LibroDTO.java
├── model
│ ├── Autor.java
│ ├── DatosAutor.java
│ ├── DatosLibro.java
│ ├── DatosRespuesta.java
│ └── Libro.java
├── principal
│ └── Principal.java
├── repository
│ ├── AutorRepository.java
│ └── LibroRepository.java
└── service
├── ConsumoAPI.java
├── ConvierteDatos.java
├── IConvierteDatos.java
└── LibroService.java
BibliotecaApplicationConsola.java
resources
└── application.properties

## ⚙️ Configuración

Clonar el repositorio y configurar la base de datos:

```bash
git clone https://github.com/alowincr/biblioteca-spring-boot-.git
cd biblioteca-spring-boot-
Configurar la base de datos PostgreSQL en src/main/resources/application.properties:

spring.datasource.url=jdbc:postgresql://localhost:5432/biblioteca
spring.datasource.username=TU_USUARIO
spring.datasource.password=TU_CONTRASEÑA
spring.jpa.hibernate.ddl-auto=update
spring.jpa.show-sql=true
spring.jpa.properties.hibernate.format_sql=true
server.port=8080

🚀 Ejecución
Para ejecutar el proyecto:

mvn clean install
mvn spring-boot:run
O ejecuta BibliotecaApplicationConsola.java desde IntelliJ.

🎛 Uso de la aplicación en consola
La clase Principal permite interactuar con la aplicación desde la consola. Opciones: 1 - Buscar libro por título, 2 - Listar libros registrados, 3 - Listar autores registrados, 4 - Listar autores vivos en un determinado año, 5 - Listar libros por idioma, 0 - Salir.

Ejemplo: buscar "Pride and Prejudice". La aplicación hace una petición a la API de Gutendex, obtiene los datos y registra el libro junto con sus autores en la base de datos:

Libro registrado desde Gutendex:
Libro{id=1, titulo='Pride and Prejudice', autores=[Jane Austen], idiomas=[en], ...}
Listar libros registrados muestra todos los libros que ya están guardados en la base de datos. Listar autores registrados lista todos los autores que tienen libros en la base de datos, sin duplicados. Listar autores vivos en un año filtra autores según su año de nacimiento y fallecimiento. Listar libros por idioma filtra libros según el idioma (en, es, fr, etc.).

🌐 Consumo de API externa
La clase ConsumoAPI realiza la llamada HTTP a la API de Gutendex. La clase ConvierteDatos convierte la respuesta JSON en objetos de modelo (Libro, Autor). Se evita duplicación de autores usando findByNombreIgnoreCase antes de guardarlos.

📌 Endpoints REST (si se desea usar API con frontend)
Método	Ruta	Descripción
GET	/libros	Listar todos los libros
GET	/libros/{id}	Obtener un libro por ID
POST	/libros	Crear un libro
PUT	/libros/{id}	Actualizar un libro
DELETE	/libros/{id}	Eliminar un libro
Nota: Los DTOs (LibroDTO, AutorDTO) se usan para enviar y recibir información de manera controlada y segura.

✅ Autor
Alonso - GitHub

