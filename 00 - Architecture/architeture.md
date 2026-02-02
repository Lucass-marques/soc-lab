graph TD
    subgraph LAB_ENVIRONMENT [Ambiente Local / On-Premise]
        style LAB_ENVIRONMENT fill:#f9f9f9,stroke:#333,stroke-width:2px
        
        ATTACKER[Kali Linux<br/>(Attacker)] -->|Bruteforce SMB/RDP<br/>NXC| VICTIM
        
        VICTIM[Windows 10<br/>DESKTOP-S4K0DB3] 
        style VICTIM fill:#ffcccc,stroke:#333
        
        VICTIM -->|Logs EventID 4625<br/>Winlogbeat| SIEM
        
        subgraph SIEM_SERVER [Server: 192.168.222.139]
            style SIEM_SERVER fill:#e1f5fe,stroke:#333
            SIEM[Elastic Search + Kibana<br/>Detector de Ameaças]
        end
        
        SIEM -->|Webhook Alert| SOAR
        
        subgraph SOAR_SERVER [Server: 192.168.222.140]
            style SOAR_SERVER fill:#e8f5e9,stroke:#333
            SOAR[Shuffle<br/>Automação de Workflow]
            IRIS[DFIR-IRIS<br/>Gestão de Incidentes]
        end
    end
    
    subgraph CLOUD_SERVICES [Nuvem / APIs Externas]
        style CLOUD_SERVICES fill:#fff3e0,stroke:#333
        GROQ[Groq Cloud API<br/>Model: Llama 3.3]
        DISCORD[Discord<br/>Notificação]
    end

    %% Fluxo de Automação
    SOAR -->|Envia JSON do Alerta| GROQ
    GROQ -->|Retorna Análise Tática| SOAR
    SOAR -->|Cria Caso + Análise| IRIS
    SOAR -->|Notifica Analista| DISCORD

    %% Estilização das bordas
    linkStyle 0 stroke:#red,stroke-width:2px;
    linkStyle 4 stroke:#blue,stroke-width:2px;