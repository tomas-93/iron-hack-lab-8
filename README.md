#Api Usuarios y Pedidos
```yml
openapi: 3.0.0
info:
  title: API de Usuarios y Pedidos
  description: API REST para gestionar usuarios y pedidos.
  version: 1.0.0

servers:
  - url: http://localhost:8080
    description: Servidor local

tags:
  - name: usuarios
    description: Operaciones relacionadas con usuarios
  - name: pedidos
    description: Operaciones relacionadas con pedidos

paths:
  /usuarios:
    get:
      tags:
        - usuarios
      summary: Obtener todos los usuarios
      responses:
        '200':
          description: Lista de usuarios
          content:
            application/json:
              schema:
                type: array
                items:
                  $ref: '#/components/schemas/Usuario'
        '500':
          description: Error interno del servidor
          content:
            application/json:
              schema:
                $ref: '#/components/schemas/Error'
    post:
      tags:
        - usuarios
      summary: Crear un nuevo usuario
      requestBody:
        required: true
        content:
          application/json:
            schema:
              $ref: '#/components/schemas/Usuario'
      responses:
        '201':
          description: Usuario creado exitosamente
          content:
            application/json:
              schema:
                $ref: '#/components/schemas/Usuario'
        '400':
          description: Solicitud incorrecta
          content:
            application/json:
              schema:
                $ref: '#/components/schemas/Error'
        '500':
          description: Error interno del servidor
          content:
            application/json:
              schema:
                $ref: '#/components/schemas/Error'

  /usuarios/{id}:
    get:
      tags:
        - usuarios
      summary: Obtener un usuario por ID
      parameters:
        - name: id
          in: path
          required: true
          schema:
            type: string
      responses:
        '200':
          description: Detalles del usuario
          content:
            application/json:
              schema:
                $ref: '#/components/schemas/Usuario'
        '404':
          description: Usuario no encontrado
          content:
            application/json:
              schema:
                $ref: '#/components/schemas/Error'
        '500':
          description: Error interno del servidor
          content:
            application/json:
              schema:
                $ref: '#/components/schemas/Error'

    put:
      tags:
        - usuarios
      summary: Actualizar un usuario por ID
      parameters:
        - name: id
          in: path
          required: true
          schema:
            type: string
      requestBody:
        required: true
        content:
          application/json:
            schema:
              $ref: '#/components/schemas/Usuario'
      responses:
        '200':
          description: Usuario actualizado exitosamente
          content:
            application/json:
              schema:
                $ref: '#/components/schemas/Usuario'
        '400':
          description: Solicitud incorrecta
          content:
            application/json:
              schema:
                $ref: '#/components/schemas/Error'
        '404':
          description: Usuario no encontrado
          content:
            application/json:
              schema:
                $ref: '#/components/schemas/Error'
        '500':
          description: Error interno del servidor
          content:
            application/json:
              schema:
                $ref: '#/components/schemas/Error'

    delete:
      tags:
        - usuarios
      summary: Eliminar un usuario por ID
      parameters:
        - name: id
          in: path
          required: true
          schema:
            type: string
      responses:
        '204':
          description: Usuario eliminado exitosamente
        '404':
          description: Usuario no encontrado
          content:
            application/json:
              schema:
                $ref: '#/components/schemas/Error'
        '500':
          description: Error interno del servidor
          content:
            application/json:
              schema:
                $ref: '#/components/schemas/Error'

  /pedidos:
    get:
      tags:
        - pedidos
      summary: Obtener todos los pedidos
      responses:
        '200':
          description: Lista de pedidos
          content:
            application/json:
              schema:
                type: array
                items:
                  $ref: '#/components/schemas/Pedido'
        '500':
          description: Error interno del servidor
          content:
            application/json:
              schema:
                $ref: '#/components/schemas/Error'
    post:
      tags:
        - pedidos
      summary: Crear un nuevo pedido
      requestBody:
        required: true
        content:
          application/json:
            schema:
              $ref: '#/components/schemas/Pedido'
      responses:
        '201':
          description: Pedido creado exitosamente
          content:
            application/json:
              schema:
                $ref: '#/components/schemas/Pedido'
        '400':
          description: Solicitud incorrecta
          content:
            application/json:
              schema:
                $ref: '#/components/schemas/Error'
        '500':
          description: Error interno del servidor
          content:
            application/json:
              schema:
                $ref: '#/components/schemas/Error'

  /pedidos/{id}:
    get:
      tags:
        - pedidos
      summary: Obtener un pedido por ID
      parameters:
        - name: id
          in: path
          required: true
          schema:
            type: string
      responses:
        '200':
          description: Detalles del pedido
          content:
            application/json:
              schema:
                $ref: '#/components/schemas/Pedido'
        '404':
          description: Pedido no encontrado
          content:
            application/json:
              schema:
                $ref: '#/components/schemas/Error'
        '500':
          description: Error interno del servidor
          content:
            application/json:
              schema:
                $ref: '#/components/schemas/Error'

    put:
      tags:
        - pedidos
      summary: Actualizar un pedido por ID
      parameters:
        - name: id
          in: path
          required: true
          schema:
            type: string
      requestBody:
        required: true
        content:
          application/json:
            schema:
              $ref: '#/components/schemas/Pedido'
      responses:
        '200':
          description: Pedido actualizado exitosamente
          content:
            application/json:
              schema:
                $ref: '#/components/schemas/Pedido'
        '400':
          description: Solicitud incorrecta
          content:
            application/json:
              schema:
                $ref: '#/components/schemas/Error'
        '404':
          description: Pedido no encontrado
          content:
            application/json:
              schema:
                $ref: '#/components/schemas/Error'
        '500':
          description: Error interno del servidor
          content:
            application/json:
              schema:
                $ref: '#/components/schemas/Error'

    delete:
      tags:
        - pedidos
      summary: Eliminar un pedido por ID
      parameters:
        - name: id
          in: path
          required: true
          schema:
            type: string
      responses:
        '204':
          description: Pedido eliminado exitosamente
        '404':
          description: Pedido no encontrado
          content:
            application/json:
              schema:
                $ref: '#/components/schemas/Error'
        '500':
          description: Error interno del servidor
          content:
            application/json:
              schema:
                $ref: '#/components/schemas/Error'

components:
  schemas:
    Usuario:
      type: object
      properties:
        id:
          type: string
          description: ID del usuario
        nombre:
          type: string
          description: Nombre del usuario
        apellidoPaterno:
          type: string
          description: Apellido paterno del usuario
        apellidoMaterno:
          type: string
          description: Apellido materno del usuario
        domicilio:
          type: string
          description: Domicilio del usuario
        fechaNacimiento:
          type: string
          format: date
          description: Fecha de nacimiento del usuario
      required:
        - nombre
        - apellidoPaterno
        - apellidoMaterno
        - domicilio
        - fechaNacimiento

    Pedido:
      type: object
      properties:
        id:
          type: string
          description: ID del pedido
        numeroPedido:
          type: string
          description: Número del pedido
        nombreProducto:
          type: string
          description: Nombre del producto
        fecha:
          type: string
          format: date
          description: Fecha del pedido
        monto:
          type: number
          format: float
          description: Monto del pedido
        puesto:
          type: string
          description: Puesto relacionado con el pedido
      required:
        - numeroPedido
        - nombreProducto
        - fecha
        - monto
        - puesto

    Error:
      type: object
      properties:
        message:
          type: string
          description: Mensaje de error


```
