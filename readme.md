# Sistema de Marcación FuturoTech

Sistema de escritorio para el registro de entrada y salida de empleados, desarrollado con JavaFX y MySQL.

## 📋 Descripción

Aplicación de escritorio que permite a los empleados registrar sus marcaciones de entrada y salida, con persistencia en base de datos MySQL y una interfaz gráfica intuitiva desarrollada en JavaFX.

## 🚀 Características

- ✅ Registro de marcaciones de entrada y salida
- ✅ Interfaz gráfica moderna con JavaFX
- ✅ Persistencia de datos con JPA/Hibernate
- ✅ Base de datos MySQL dockerizada
- ✅ Validación de datos en tiempo real
- ✅ Confirmación mediante diálogos
- ✅ Historial de marcaciones en tabla
- ✅ Conexión automática a base de datos
- ✅ Diseño responsive

## 🛠️ Tecnologías Utilizadas

- **Java 11+** - Lenguaje de programación
- **JavaFX 17** - Framework para interfaz gráfica
- **Maven** - Gestión de dependencias
- **MySQL 5.7** - Base de datos
- **Docker** - Containerización de MySQL
- **JPA/Hibernate** - ORM para persistencia
- **Git** - Control de versiones

## 📁 Estructura del Proyecto

```
marcacion/
├── src/
│   └── main/
│       ├── java/
│       │   └── com/marcacion/
│       │       ├── App.java
│       │       ├── controller/
│       │       │   └── MainController.java
│       │       ├── model/
│       │       │   └── Marcacion.java
│       │       ├── service/
│       │       │   └── MarcacionService.java
│       │       └── util/
│       │           └── JPAUtil.java
│       └── resources/
│           ├── fxml/
│           │   └── MainView.fxml
│           ├── css/
│           │   └── styles.css
│           ├── META-INF/
│               └── persistence.xml
├── docker/
│   ├── docker-compose.yml
│   └── init.sql
├── pom.xml
└── README.md
```

## 🔧 Requisitos Previos

### Software Necesario

1. **Java Development Kit (JDK) 11 o superior**
   - Descargar desde: https://openjdk.java.net/
   - Verificar instalación: `java -version`

2. **Apache Maven 3.6+**
   - Descargar desde: https://maven.apache.org/download.cgi
   - Verificar instalación: `mvn -version`

3. **Docker Desktop**
   - Descargar desde: https://www.docker.com/get-started
   - Verificar instalación: `docker --version`

4. **Git**
   - Descargar desde: https://git-scm.com/downloads
   - Verificar instalación: `git --version`

### Variables de Entorno

Asegúrate de tener configuradas las siguientes variables:

```bash
JAVA_HOME=/path/to/java
MAVEN_HOME=/path/to/maven
PATH=$PATH:$JAVA_HOME/bin:$MAVEN_HOME/bin
```

## 🚀 Instalación y Ejecución

### 1. Clonar el Repositorio

```bash
git clone https://github.com/AlenSaavedra/FuturoTech.git
cd marcacion
```

### 2. Configurar Base de Datos

#### Usando Docker Compose (Recomendado)

```bash
# Iniciar MySQL con Docker Compose
docker-compose up -d

# Verificar que esté corriendo
docker-compose ps
```


### 3. Compilar el Proyecto

```bash
# Limpiar y compilar
mvn clean compile

# Ejecutar tests (opcional)
mvn test

# Generar JAR ejecutable
mvn package
```

### 4. Ejecutar la Aplicación

#### Opción A: Con Maven

```bash
mvn javafx:run
```

#### Opción B: JAR ejecutable

```bash
java -jar target/marcacion-system-1.0.0.jar
```

## 📊 Base de Datos

### Configuración

- **Host:** localhost
- **Puerto:** 3306 - 3307
- **Base de datos:** marcacion_db
- **Usuario:** app_user
- **Contraseña:** app_password

### Esquema de Base de Datos

```sql
CREATE TABLE marcaciones (
    id BIGINT AUTO_INCREMENT PRIMARY KEY,
    nombre VARCHAR(100) NOT NULL,
    tipo_marcacion ENUM('Entrada', 'Salida') NOT NULL,
    fecha_hora DATETIME NOT NULL DEFAULT CURRENT_TIMESTAMP,
    created_at TIMESTAMP DEFAULT CURRENT_TIMESTAMP,
    updated_at TIMESTAMP DEFAULT CURRENT_TIMESTAMP ON UPDATE CURRENT_TIMESTAMP
);
```

### Comandos Útiles

```bash
# Conectarse a MySQL
docker exec -it futurotech_mysql mysql -u app_user -papp_password marcacion_db

# Ver logs de MySQL
docker logs futurotech_mysql

# Backup de la base de datos
docker exec futurotech_mysql mysqldump -u root -proot123 marcacion_db > backup.sql

# Restaurar backup
docker exec -i futurotech_mysql mysql -u root -proot123 marcacion_db < backup.sql
```

## 🎮 Uso de la Aplicación

### Interfaz Principal

1. **Campo Nombre:** Ingrese el nombre del empleado
2. **Tipo Marcación:** Seleccione "Entrada" o "Salida"
3. **Botón Registrar:** Guarda la marcación después de confirmación
4. **Tabla Historial:** Muestra todas las marcaciones registradas
5. **Botón Actualizar:** Refresca los datos de la tabla

### Flujo de Registro

1. Completar el formulario
2. Hacer clic en "Registrar"
3. Confirmar en el diálogo (SI/NO)
4. Si confirma, el registro se guarda automáticamente
5. La tabla se actualiza con el nuevo registro


## 📝 Licencia

Este proyecto está bajo la Licencia MIT - ver el archivo [LICENSE](LICENSE) para detalles.

## 👥 Autores

- **Luis Chango** - *Desarrollo inicial* - [@Lchango](https://github.com/Lchango)



## 📞 Soporte

Para soporte técnico:
- **Email:** lachango@est.teclemas.edu.ec

---

**© 2025 FuturoTech - Sistema de Marcación v1.0.0**
