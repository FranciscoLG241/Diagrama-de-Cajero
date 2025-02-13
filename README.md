# Diagrama de Cajero

## Trabajo a realizar

### Diagrama de Casos de Uso  
Crea el diagrama de uso haciendo uso de PlantUML, representando los actores y casos de uso que identifiques en los requisitos.  

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








