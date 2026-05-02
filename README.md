# 🎬 Java Movies — Sistema de Gestión de Usuarios

Aplicación web desarrollada en Java con arquitectura MVC, que permite el registro, autenticación y administración de usuarios mediante una API REST conectada a una base de datos MySQL.

---

## 🛠️ Tecnologías utilizadas

- **Java** (Servlets - javax.servlet)
- **MySQL** — base de datos relacional
- **JDBC** con `PreparedStatement` — conexión segura a la base de datos
- **Jackson** (`ObjectMapper`) — serialización y deserialización JSON
- **Patrón DAO** — separación de lógica de negocio y acceso a datos
- **HTML/CSS** — interfaz de usuario

---

## ⚙️ Funcionalidades

- ✅ Registro de nuevos usuarios
- ✅ Login con validación de credenciales
- ✅ Listado de todos los usuarios (GET)
- ✅ Búsqueda de usuario por ID (GET)
- ✅ Modificación de datos de usuario (PUT)
- ✅ Eliminación de usuario (DELETE)
- ✅ Redirección a panel de administración post-login

---

## 🗂️ Estructura del proyecto

```
src/main/java/
├── conexion/
│   └── ConexionDB.java        # Conexión a MySQL via JDBC
├── controller/
│   ├── LoginServlet.java      # Autenticación de usuarios
│   ├── RegistroServlet.java   # Registro de nuevos usuarios
│   └── GestionUsuariosServlet.java  # API REST CRUD
├── dao/
│   ├── UserDao.java           # Validación de login
│   └── UsuarioDAO.java        # Operaciones CRUD en BD
└── modelo/
    └── Usuario.java           # Entidad Usuario
```

---

## 🗄️ Base de datos

El proyecto utiliza dos tablas en MySQL:

**`login`** — credenciales de acceso al sistema  
**`registroUsuarios`** — datos completos de los usuarios registrados

Campos de `registroUsuarios`: `id`, `nombre`, `apellido`, `email`, `password`, `fechaNacimiento`, `pais`

---

## 🚀 Cómo ejecutar el proyecto

### Requisitos previos
- Java JDK 8 o superior
- MySQL Server
- Apache Tomcat (o servidor de servlets compatible)
- Driver MySQL Connector/J

### Pasos

1. Clonar el repositorio
```bash
git clone https://github.com/MiguelNefle1/java-movies.git
```

2. Crear la base de datos en MySQL
```sql
CREATE DATABASE usuariosAdministrador;
```

3. Crear las tablas necesarias
```sql
CREATE TABLE login (
    id INT AUTO_INCREMENT PRIMARY KEY,
    email VARCHAR(100) NOT NULL,
    contrasena VARCHAR(100) NOT NULL
);

CREATE TABLE registroUsuarios (
    id INT AUTO_INCREMENT PRIMARY KEY,
    nombre VARCHAR(50),
    apellido VARCHAR(50),
    email VARCHAR(100),
    password VARCHAR(100),
    fechaNacimiento DATE,
    pais VARCHAR(50)
);
```

4. Configurar la conexión en `ConexionDB.java` si es necesario (usuario y contraseña de MySQL)

5. Desplegar en Tomcat y acceder desde el navegador

---

## 📡 Endpoints disponibles

| Método | URL | Descripción |
|--------|-----|-------------|
| POST | `/LoginServlet` | Autenticación de usuario |
| POST | `/registro` | Registro de nuevo usuario |
| GET | `/GestionUsuariosServlet` | Listar todos los usuarios |
| GET | `/GestionUsuariosServlet?id={id}` | Obtener usuario por ID |
| PUT | `/GestionUsuariosServlet` | Modificar usuario (JSON en body) |
| DELETE | `/GestionUsuariosServlet?id={id}` | Eliminar usuario |

---

## 📌 Mejoras pendientes

- [ ] Encriptación de contraseñas (BCrypt)
- [ ] Manejo de sesiones con `HttpSession`
- [ ] Validaciones de entrada en el servidor
- [ ] Migración a Spring Boot

---

## 👨‍💻 Autor

**Miguel Ángel Nefle**  
Instructor | Desarrollador Java  
[GitHub](https://github.com/MiguelNefle1) · [LinkedIn](https://www.linkedin.com/in/miguel-%C3%A1ngel-nefle/) · miguelnefle@gmail.com
