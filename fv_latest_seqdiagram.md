@startuml
actor Shipper
actor Carrier
actor "Telematics Provider" as Telematics
participant "FreightVerify System" as FV
participant "Event Processor" as Processor
participant "PostgreSQL DB" as DB

== Shipment Created ==
Shipper -> FV: Create Shipment (shipment data)
FV -> DB: Insert shipment into Shipments Table
FV --> Shipper: Acknowledge Shipment Created

== Event Flow: Shipment Status Updates ==
loop Until Shipment Delivered
    Carrier -> FV: Send Shipment Status (Event Code: XB)
    FV -> Processor: Trigger Asset Assignment Processing (XB)
    Processor -> DB: Update Shipment Status (Assigned Asset)

    Carrier -> FV: Send Shipment Status (Event Code: X3)
    FV -> Processor: Trigger Pickup Arrival Processing (X3)
    Processor -> DB: Update Shipment Status (Pickup Arrival)

    Telematics -> FV: Provide Location Update (Event Code: LO)
    FV -> Processor: Process Location Update (LO)
    Processor -> DB: Update Shipment Location (Longitude, Latitude)

    Carrier -> FV: Send Shipment Status (Event Code: CP)
    FV -> Processor: Trigger Loading Completion Processing (CP)
    Processor -> DB: Update Shipment Status (Completed Loading)

    Carrier -> FV: Send Shipment Status (Event Code: X1)
    FV -> Processor: Trigger Drop Off Arrival Processing (X1)
    Processor -> DB: Update Shipment Status (Drop Off Arrival)

    note over Carrier: Status events continue for each update until shipment delivery.
end

== Shipment Delivered ==
Carrier -> FV: Send Shipment Status (Event Code: Delivered)
FV -> Processor: Trigger Final Delivery Processing (Delivered)
Processor -> DB: Mark Shipment as Delivered

FV --> Shipper: Notify Shipment Delivered
@enduml
