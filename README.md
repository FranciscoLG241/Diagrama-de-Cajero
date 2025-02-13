# Diagrama de Cajero

## Trabajo a realizar

### Diagrama de Casos de Uso  

```plantuml
@startuml
actor Cliente
actor Banco

rectangle "Cajero Automático" {
    (Validar usuario) as R1
    (Sacar dinero) as R2
    (Verificar límite diario) as R3
    (Realizar transferencia) as R4
    (Ingresar dinero) as R5
    
    Cliente --> R1
    R1 --> Cliente : Acceso concedido
    Cliente --> R2
    R2 --> R3 : Validar límite diario
    Cliente --> R4
    Cliente --> R5

    R2 .> "Mostrar saldo insuficiente" : <<include>>
    R3 .> "Mostrar límite superado" : <<include>>
    
    R4 --> Banco
    R5 --> Banco
}
@enduml


Caso de Uso: Sacar Dinero
Flujo Normal
1.- El cliente se autentica en el sistema ingresando su tarjeta y PIN.
2.- El sistema valida la información y permite el acceso.
3.- El cliente selecciona la opción de "Sacar dinero".
4.- El sistema solicita al cliente ingresar el monto a retirar.
5.- El sistema verifica si el cliente tiene saldo suficiente.
6.- El sistema valida que la cantidad solicitada no supere el límite diario.
7.- Si las validaciones son exitosas, el cajero entrega el dinero y actualiza el saldo.
8.- Se muestra un mensaje confirmando la transacción y se pregunta si el cliente desea otra operación.


Flujo Alternativo
Saldo insuficiente: Si el cliente no tiene saldo suficiente, el sistema muestra un mensaje de error y solicita otra cantidad.
Límite diario excedido: Si la cantidad supera el límite permitido, el sistema muestra una advertencia y solicita otro monto.
Error de conexión: Si el sistema no puede completar la transacción, se muestra un mensaje de error y se cancela la operación.





