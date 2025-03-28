# Bushcraft skills

* [Knots](knots)
* [Fire lighting](firelighting)
* [Cooking](cooking)
* [Crafting](crafting)
* [Cordage](cordage)
* [Shelter building](shelterbuilding)
* [Camping](camping)
* [Foraging](foraging)
* [Navigation](navigation)
* [Butchery](butchery)
* [Tracking](tracking)
* [Trapping](trapping)
* [Hunting](hunting)

```mermaid
mindmap
  root((Bushcraft skills))
    Knots
    Fire lighting
        Methods
            Friction
            Percussion (sparks)
            Compression
            Solar
            Chemical
            Electrical
        Tools
            Ferrocerium
            Flint & steel
        Materials
            Tinder
                Char cloth
                Cotton wool
                Tinder fungus
                Magnesium or ferrocerium shavings
                Feather sticks
                Paper
            Extenders & accellerants
                Rubber
                Vaseline
                Fire lighters
            Fuel
                Wood
                Charcoal
                Coal
    Crafting
    Shelter
        Shelter building
        Camping
    Navigation
    Food
        Foraging
        Butchery
        Cooking
        Tracking
        Trapping
        Hunting
```

```mermaid
flowchart TB
    A("Foraging") --> B("Cooking")
    C("Fire lighting") --> B
    D("Crafting") --> G("Shelter building") & B
    F("Knots") --> G
    G --> E("Camping")
    H("Navigation") --> I("Tracking")
    I --> J("Trapping") & K("Hunting")
    J --> L("Butchery")
    K --> L
    L --> B

    style A stroke:#000000,fill:#00C853
    style C stroke:#000000,fill:#00C853
    style D stroke:#000000,fill:#00C853
    style H stroke:#000000,fill:#00C853
    style F stroke:#000000,fill:#00C853
    style L stroke:#000000,fill:#FFD600
    style B stroke:#000000,fill:#FFD600
    style G stroke:#000000,fill:#FFD600
    style E stroke:#000000,fill:#FF6D00
    style I stroke:#000000,fill:#FFD600
    style J stroke:#000000,fill:#FF6D00
    style K stroke:#000000,fill:#FF6D00
```
