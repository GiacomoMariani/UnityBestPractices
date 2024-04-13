# Game Title

## System Requirements

### Development System Requirements

| Requirement         | Description             |
|---------------------|-------------------------|
| Platforms           | [Platforms]             |
| Operating System    | [Operating System]      |
| Processor           | [Minimum Processor]     |
| Memory              | [Minimum RAM]           |
| Graphics            | [Minimum Graphics Card] |
| Storage             | [Minimum Storage Space] |
| Max Screen Size     | [Description]           |
| Older Devices       | [Description]           |
| Multiplayer Service | [Description]           |     

### Multiplayer Session Requirements

| Requirement                            | Description                                                  |
|----------------------------------------|--------------------------------------------------------------|
| Max Concurrent Users Per Session       | [Description]                                                |
| Session Length (typical)               | [Description]                                                |
| Session Max                            | [Description]                                                |
| Estimated Sessions Per Day Per Player  | [Description]                                                |
| Support External Spectatorship         | [Description]                                                |

### Server Requirements

| Requirement                                      | Description                                        |
|--------------------------------------------------|----------------------------------------------------|
| Multiplayer Topology                             | [Description]                                      |
| Start Region DataCenter                          | [Description]                                      |
| Server Update Approach                           | [Description]                                      |
| Fault Tolerance                                  | [Description]                                      |
| Server Platform                                  | [Description]                                      |
| Desired Bandwidth                                | [Description]                                      |
| Network Tick                                     | [Description]                                      |
| Max Single Package per Player Inbound            | [Description]                                      |
| Max Single Package per Player Outbound           | [Description]                                      |
| Maximum Latency (Per Game Mode IE Casual/Ranked) | [Description]                                      |

### Design Requirements

| Requirement                      | Description                                       |
|----------------------------------|---------------------------------------------------|
| Supported Controllers            | [Description of supported controllers]            |
| Input System                     | [Description of input system]                     |
| UI System                        | [Description of UI system]                        |
| Localization                     | [Description of localization requirements]        |
| Audio System                     | [Description of audio system requirements]        |
| Accessibility                    | [Description of accessibility requirements]       |
| Multiplayer Features             | [Description of multiplayer feature requirements] |
| Gamepad Support                  | [Description of gamepad support requirements]     |
| Modding Support                  | [Description of modding support requirements]     |
| Analytics and Telemetry          | [Description]                                     |
| Security and Anti-Cheat Measures | [Description]                                     |
| Social Features                  | [Description of social feature requirements]      |

### Backend Requirements

| Requirement                | Description                                              |
|----------------------------|----------------------------------------------------------|
| Matchmaking                | [Description of matchmaking requirements]                |
| Player Data                | [Description of player data requirements]                |
| Player Login System        | [Description of player login system requirements]        |
| Server Deployment Pipeline | [Description of server deployment pipeline requirements] |


### Art Requirements

| Requirement                 | Description                                                |
|-----------------------------|------------------------------------------------------------|
| Art Style                   | [Description of the desired art style]                     |
| Resolution and Aspect Ratio | [Description of the target resolution and aspect ratio]    |
| Cutscenes and Cinematics    | [Description of the cutscenes and cinematic requirements]  |

#### Geometry Budget - Characters

| Requirement       | Value Range                             |
|-------------------|-----------------------------------------|
| Vertex Count      | 5,000 to 25,000                         |
| Triangle Count    | 7,500 to 37,500                         |
| Memory Usage      | 50MB to 250MB                           |
| Draw Calls        | 1 to 5 per character model              |

#### Geometry Budget - Props

| Requirement       | Value Range                          |
|-------------------|--------------------------------------|
| Vertex Count      | 2,500 to 12,500                      |
| Triangle Count    | 3,750 to 18,750                      |
| Memory Usage      | 25MB to 125MB                        |
| Draw Calls        | 1 to 3 per prop model                |

#### Geometry Budget - Scenes

| Requirement       | Value Range                            |
|-------------------|----------------------------------------|
| Vertex Count      | Up to 1 million                        |
| Triangle Count    | Up to 2 million                        |
| Memory Usage      | 500MB to 2GB                           |
| Draw Calls        | Up to 50 per scene                     |
