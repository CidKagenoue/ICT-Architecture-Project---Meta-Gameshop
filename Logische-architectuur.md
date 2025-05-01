# 02 - Logische Architectuur

## 🎯 Doel

Deze logische architectuur beschrijft de functionele onderdelen van het systeem. De indeling is gebaseerd op kwaliteitsattributen zoals schaalbaarheid, flexibiliteit en integratiemogelijkheden.

---

## 🧱 Componentenoverzicht

| Component              | Verantwoordelijkheid                                                                 |
|------------------------|----------------------------------------------------------------------------------------|
| **User Service**       | Gebruikersbeheer (aanmelden, registreren, voorkeuren, bibliotheek)                    |
| **Game Catalog**       | Verzamelt en beheert metadata over games                                              |
| **Shop Aggregator**    | Haalt prijzen en beschikbaarheid op bij externe winkels (Steam, Epic, etc.)          |
| **Recommendation Engine** | Genereert persoonlijke aanbevelingen op basis van gedrag en voorkeuren           |
| **Collection Manager** | Laat gebruikers hun eigen verzamelingen beheren                                       |
| **Search & Filter**    | Biedt geavanceerde zoek- en filterfunctionaliteit over de volledige catalogus         |
| **Review & Rating**    | Verwerkt gebruikersbeoordelingen en recensies                                         |
| **API Gateway**        | Verzorgt de toegang tot het systeem via een uniforme API                              |
| **Auth Service**       | Beheert authenticatie en autorisatie                                                  |
| **Admin Interface**    | Voor beheer van bronnen, moderatie van reviews, enz.                                  |

---

## 🔄 Logische Architectuur (Mermaid)

```mermaid
graph TD
    UI[User Interface] --> API[API Gateway]
    ADMIN[Admin Interface] --> API
    API --> AUTH[Auth Service]
    API --> USER[User Service]
    API --> GAME[Game Catalog]
    API --> RECO[Recommendation Engine]
    API --> COLL[Collection Manager]
    API --> SEARCH[Search & Filter]
    API --> REVIEW[Review & Rating]
    API --> SHOP[Shop Aggregator]

    USER --> AUTH
    RECO --> USER
    RECO --> GAME
    RECO --> REVIEW

    SEARCH --> GAME
    SEARCH --> REVIEW
    SEARCH --> SHOP

    COLL --> USER
    COLL --> GAME

    GAME --> SHOP
    REVIEW --> USER