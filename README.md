# bakugan-api - _A little bakugan API_

Este proyecto es un microservicio desarrollado con Flask que se conecta a una base de datos MySQL. La API permite realizar algunas operaciones CRUD (Crear, Leer, Eliminar) en la tabla de `bakugan`. Los datos de conexión se gestionan mediante variables de entorno, cargadas desde un archivo `.env`.

## Requisitos

- Python 3.x
- MySQL
- [pip](https://pip.pypa.io/en/stable/installation/) para instalar las dependencias
- [Flask](https://flask.palletsprojects.com/)
- [python-dotenv](https://pypi.org/project/python-dotenv/) para manejar variables de entorno

## Configuración del proyecto

1. Clona este repositorio:
    ```bash
    git clone https://github.com/tu-usuario/bakugan-api.git
    cd bakugan-api
    ```

2. Crea un entorno virtual (opcional pero recomendado):
    ```bash
    python -m venv venv
    source venv/bin/activate  # En Linux/Mac
    venv\Scripts\activate  # En Windows
    ```

3. Instala las dependencias:
    ```bash
    pip install -r requirements.txt
    ```

4. Crea un archivo `.env` en la raíz del proyecto con la siguiente estructura, utilizando tus credenciales de MySQL:

    ```env
    USER_DB=tu_usuario_de_mysql
    KEY_DB=tu_password_de_mysql
    HOST_DB=localhost
    PORT_DB=3306
    NAME_DB=nombre_de_tu_base_de_datos
    ```

5. Crea la tabla `bakugan` en tu base de datos MySQL (puedes ajustar la estructura del archivo ```dump.sql``` según tus necesidades).

## Uso de la API

### Rutas disponibles

- **GET** `/`: Muestra un mensaje de bienvenida.
- **GET** `/get-all-bakugan`: Obtiene todos los Bakugan de la base de datos.
- **POST** `/insert-bakugan`: Inserta un nuevo Bakugan. Se deben enviar los datos en formato JSON en el cuerpo de la solicitud:
    ```json
    {
        "name": "Nombre del Bakugan",
        "type_primary": "Tipo primario",
        "type_secondary": "Tipo secundario"  # Opcional
    }
    ```
- **DELETE** `/delete-bakugan/<id>`: Elimina un Bakugan por su ID.

### Ejemplos

- **Insertar un Bakugan**:
    ```bash
    curl -X POST http://localhost:5000/insert-bakugan -H "Content-Type: application/json" -d '{"name": "Dragonoid", "type_primary": "Fire", "type_secondary": "Air"}'
    ```

- **Obtener todos los Bakugans**:
    ```bash
    curl http://localhost:5000/get-all-bakugan
    ```

- **Eliminar un Bakugan**:
    ```bash
    curl -X DELETE http://localhost:5000/delete-bakugan/1
    ```

## Ejecución del proyecto

1. Inicia la aplicación Flask:
    ```bash
    flask run
    ```
    o alternativo
    ```bash
    python -m flask run
    ```

3. Abre en el navegador [http://localhost:5000](http://localhost:5000) para verificar que el servidor esté funcionando correctamente.

## Contribuciones

¡Las contribuciones son bienvenidas! Si deseas colaborar, por favor abre un issue o envía un pull request.

## Licencia

Este proyecto está licenciado bajo la [MIT License](LICENSE).

Un saludo, wolfghost23 :D.

