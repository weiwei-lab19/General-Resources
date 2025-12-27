# Demo: Hardware-in-the-Loop (HiL) with Speedgoat
This demo shows how to test a PLC control system in a HiL setup with a Speedgoat target machine. Video for this demo can be found [here](https://www.youtube.com/watch?v=Rb3Aefnu0NY)

```mermaid
graph TB
    subgraph DevEnv["Development Environment"]
        PC["Development Computer<br/>(MATLAB/Simulink)"]
        SRT["Simulink Real-Time"]
        PC --> SRT
    end
    
    subgraph SpeedgoatSys["Speedgoat Real-Time System"]
        SG["Speedgoat Target Machine<br/>(Real-Time Processor)"]
        IO["I/O Module Card(s)<br/>(Analog/Digital I/O)"]
        SG --> IO
    end
    
    subgraph PLCSys["PLC System"]
        PLC["PLC Controller<br/>(Control Hardware)"]
        PLCIO["PLC I/O Modules<br/>(Input/Output Cards)"]
        PLC --> PLCIO
    end
    
    subgraph Plant["Simulated Plant"]
        Model["Plant Model<br/>(Running on Speedgoat)"]
    end
    
    %% Ethernet connections
    PC ---|"Ethernet<br/>(Model Download &<br/>Monitoring)"| SG
    
    %% Real-time execution
    SRT -.->|"Compiles & Deploys"| Model
    Model -.->|"Executes in Real-Time"| SG
    
    %% Signal connections between Speedgoat and PLC
    IO <-->|"Analog Signals<br/>(Sensor Outputs)"| PLCIO
    IO <-->|"Digital Signals<br/>(Actuator Commands)"| PLCIO
    IO -.->|"Optional: Fieldbus<br/>(EtherCAT, CAN, etc.)"| PLCIO
    
    %% Closed loop
    Model -->|"Simulated Process<br/>Variables"| IO
    PLCIO -->|"Control Signals"| PLC
    PLC -->|"Control Commands"| PLCIO
    
    %% Styling
    classDef devStyle fill:#e1f5ff,stroke:#0288d1,stroke-width:2px
    classDef sgStyle fill:#fff3e0,stroke:#f57c00,stroke-width:2px
    classDef plcStyle fill:#f3e5f5,stroke:#7b1fa2,stroke-width:2px
    classDef simStyle fill:#e8f5e9,stroke:#388e3c,stroke-width:2px
    
    class PC,SRT devStyle
    class SG,IO sgStyle
    class PLC,PLCIO plcStyle
    class Model simStyle
```