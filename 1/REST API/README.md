# :bulb: Modulo 1: REST API

## :book: Objetivo

- Entender que es una RestAPI.
- Diferenciar una RestAPI de una SOAP.
- Entender JSON.
- Entender Postman y cómo usarlo.


## :clipboard: Material

Consultar en la [presentación](https://docs.google.com/presentation/d/1ik1JkpY0564S_Taah9aETjbt0NGNIUTl/edit?usp=sharing&ouid=103375097265829776983&rtpof=true&sd=true).

# :books: Temas

## I. Rest API vs SOAP

### 1. SOAP

SOAP es un protocolo estándar que se creó originalmente para posibilitar la comunicación entre las aplicaciones que se diseñan con diferentes lenguajes y en distintas plataformas. Impone reglas integradas que aumentan la complejidad y la sobrecarga.

- Centrada en los servicios
- Estandarizado
- Requiere mayor ancho de banda
- Respuesta: XML
- Pruebas: Requiere software especializado
- Método:  POST

### 2. Rest API

REST es un conjunto de principios arquitectónicos que se ajusta a las necesidades de las aplicaciones móviles y los servicios web ligeros. Es un conjunto de pautas donde la implementación de las recomendaciones depende de los desarrolladores.

- Centrada en datos
- Flexible
- Liviano
- Respuesta: Diferentes tipos de respuesta
- Pruebas: En cualquier software que soporte HTTP
- Método: GET

### 3. Pautas Arquitectonicas REST

Se considera que una aplicación es RESTful si cumple con ciertas pautas arquitectónicas. Una aplicación de RESTful debe tener lo siguiente:

- Arquitectura cliente-servidor
- Comunicación cliente-servidor sin estado
- Datos que pueden almacenarse en caché
- Interfaz uniforme (más detalles a continuación)
- Restricción del sistema en capas

### 4. Una interfaz uniforme

es útil para:

- Identificar de recursos en las peticiones
- Manipular de recursos a través de representaciones
- Mandar mensajes auto-descriptivos
- Usar hipermedia como motor del estado de la aplicación



## II. Metodos HTTP

HTTP define un conjunto de métodos de petición para indicar la acción que se desea realizar para un recurso determinado.

#### 1. GET
El método GET solicita una representación de un recurso específico. Las peticiones que usan el método GET sólo deben recuperar datos.

#### 2.HEAD (en-US)
El método HEAD pide una respuesta idéntica a la de una petición GET, pero sin el cuerpo de la respuesta.

#### 3.POST
El método POST se utiliza para enviar una entidad a un recurso en específico, causando a menudo un cambio en el estado o efectos secundarios en el servidor.

#### 4.PUT
El modo PUT reemplaza todas las representaciones actuales del recurso de destino con la carga útil de la petición.

#### 5.DELETE (en-US)
El método DELETE borra un recurso en específico.

#### 6.CONNECT
El método CONNECT establece un túnel hacia el servidor identificado por el recurso.

#### 7.OPTIONS (en-US)
El método OPTIONS es utilizado para describir las opciones de comunicación para el recurso de destino.

#### 8.TRACE
El método TRACE realiza una prueba de bucle de retorno de mensaje a lo largo de la ruta al recurso de destino.

#### 9.PATCH
El método PATCH es utilizado para aplicar modificaciones parciales a un recurso.

| Metodo      | Proposito                                             | Respuesta                          |
| ----------- | ----------------------------------------------------- |----------------------------------- |
| **GET**     | Pedir información                                     | Informacion solicitada             |
| **HEAD**    | Pedir información pero solo retornar los HTTP Headers | Headers                            | 
| **POST**    | Enviar información                                    | *definida por necesidad tecnica*   |
| **PUT**     | Cargar un archivo                                     | *definida por necesidad tecnica*   |
| **DELETE**  | Elminar información                                   | *definida por necesidad tecnica*   |
| **CONNECT** | Establecer conección con algun servicio externo       | *definida por necesidad tecnica*   |
| **OPTIONS** | Listar los metodos HTTP soportados por la API         | lista de metodos y rutas de la API |
| **TRACE**   | Para propositos de debugeo                            | ECHO respuesta o *ping*            |
| **PATCH**   | Para editar informacion                               | *definida por necesidad tecnica*   |


## III. JSON

JSON (JavaScript Object Notation - Notación de Objetos de JavaScript) es un formato ligero de intercambio de datos. Está basado en un subconjunto del Lenguaje de Programación JavaScript. JSON es un formato de texto independiente del lenguaje pero utiliza convenciones que son ampliamente conocidas por los programadores lo cual hace que sea un lenguaje ideal para el intercambio de datos.

#### JSON example

```js
{
  "glossary": {
    "title": "example glossary",
    "GlossDiv": {
      "title": "S",
      "GlossList": {
        "GlossEntry": {
          "ID": "SGML",
          "SortAs": "SGML",
          "GlossTerm": "Standard Generalized Markup Language",
          "Acronym": "SGML",
          "Abbrev": "ISO 8879:1986",
          "GlossDef": {
            "para": "A meta-markup language, used to create markup languages such as DocBook.",
            "GlossSeeAlso": ["GML", "XML"]
          },
          "GlossSee": "markup"
        }
      }
    }
  }
}
```

#### XML example

```XML
<!DOCTYPE glossary PUBLIC "-//OASIS//DTD DocBook V3.1//EN">
 <glossary><title>example glossary</title>
  <GlossDiv><title>S</title>
   <GlossList>
    <GlossEntry ID="SGML" SortAs="SGML">
     <GlossTerm>Standard Generalized Markup Language</GlossTerm>
     <Acronym>SGML</Acronym>
     <Abbrev>ISO 8879:1986</Abbrev>
     <GlossDef>
      <para>A meta-markup language, used to create markup languages such as DocBook.</para>
      <GlossSeeAlso OtherTerm="GML">
      <GlossSeeAlso OtherTerm="XML">
     </GlossDef>
     <GlossSee OtherTerm="markup">
    </GlossEntry>
   </GlossList>
  </GlossDiv>
 </glossary>
```

## IV. POSTMAN

Postman es una plataforma de desarrollo de APIs enfocada en simplificar el ciclo de vida de las API y mejorar la colaboración con el equipo. Lo usamos habitualmente para probar nuestras API.

![Logo]()
<p align="center">
  <img src="https://res.cloudinary.com/postman/image/upload/t_team_logo/v1629869194/team/2893aede23f01bfcbd2319326bc96a6ed0524eba759745ed6d73405a3a8b67a8"/>
</p>

### 1. cURL

cURL es una herramienta de línea de comandos que nos permite ejecutar llamadas HTTP a recursos en línea o locales. Es sencillo de usar pero también implica ciertos desafíos, como la sencillez de lectura de las respuestas.

### 2. 



## :pencil2: Ejercicio





