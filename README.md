# Tarea-2.-Convertir-un-monolitico-en-microservicios-201800992
## Justificación del rediseño 

**Se separo la logica de negocio en 4 microservicios, ya que el diagrama UML Case Online Shopping System se puede varios flujos del carrito de compra, que son cadidatos a ser microservicios.**

### Microservicios propuestos
- User microservice
- Orders Microservice
- Orders Details Microservice
- Payments Microservice
**Ya que como dice la teoria, cada microservicio debe de tener una unica responsabilidad, se tomaron los flujos de Case Online Shopping System y se puede apreciar que estos flujos tienen independencia, por lo tanto son cadidatos a ser microservicios.**

## Descripción de los servicios

- User microservice
    * Se encargara de la autenticacion, roles y ingreso de los usuarios.
- Orders Microservice
    * Se encargara de la publicacion de productos, inventario y stock de Case Online Shopping System.
- Orders Details Microservice
    * Se encargara de realizar del detalle de cada orden, trabajando con Orders microservice.
- Payments Microservice
    * Se encargara de todo el flujo de pagos (compras y ventas) de todo el sistema.

## Diagrama de arquitectura

 ![texto_alternativo](Arquitectura%20de%20microservicios.jpeg)


## Lecciones aprendidas y desafíos enfrentados
*   Convertir una arquitectura monolitica tiene su nivel de complegidad, dependiendo de los flujos de trabajo. Ya que un requisito indispensable para convertir un servicio a microservicio es que este debe de tener una sola responsabilidad/trabajo, el desafio es identificar esos flujos que convertirlos en Microservicios.

## Despliegue 

* Para el despliegue del sistema se realizo un API-Gateway el cual se encuentra al igual que cada microservicio en una docker networks. Cada microservicio se comunicara por medio de NATS, al api Gateway. El servicio de NATS se desplegara en la misma docket Networks para que toda la comunicacion sea interna y solo se exponga el puerto del API-Gateway al mundo exterior.

*   Comandos Utilizados
    - > docker build -t 
    - > docker-compose up

* dockerfile.prod
    * Se utilizaron para el API-Gateway, User-ms, product-ms, Orders-ms, detail-ms y payment-ms el mismo docker compose en ambiente de produccion contruyendo los dist de las diferentes partes.

* Framework Utilizado.
    * NestJs

* Transport 
    - Se utilzo como protocolo de mensageria NATS, por la forma practica y facil de utlizar. 
    - No se necesita construir un dockerfile para nats, ya que docker automaticamente llama a la imagen de NATS con su nombre. 

