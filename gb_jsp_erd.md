erDiagram
    Users ||--o{ User_Stats : has
    Users ||--o{ User_Achievements : earns
    Users ||--o{ Reviews : writes
    Users ||--o{ Purchases : makes
    Users ||--o{ Posts : creates
    Users ||--o{ Comments : writes
    Users ||--o{ Marketplace : lists
    Users ||--o{ Library : owns
    Users ||--o{ Game_Stats : tracks

    Games ||--o{ Reviews : receives
    Games ||--o{ Purchases : included_in
    Games ||--o{ Marketplace : listed_in
    Games ||--o{ Library : contained_in
    Games ||--o{ Game_Stats : tracks

    Posts ||--o{ Comments : has

    Achievements ||--o{ User_Achievements : awarded_to

    Users {
        int user_id PK
        string username
        string password
        string email
        string profile_image
        enum role
        timestamp created_at
    }

    User_Stats {
        int stats_id PK
        int user_id FK
        int total_play_time
        int total_purchases
        int total_reviews
    }

    Achievements {
        int achievement_id PK
        string name
        string description
    }

    User_Achievements {
        int user_achievement_id PK
        int user_id FK
        int achievement_id FK
        timestamp earned_at
    }

    Games {
        int game_id PK
        string title
        string description
        decimal price
        string image_url
        timestamp created_at
    }

    Reviews {
        int review_id PK
        int user_id FK
        int game_id FK
        int rating
        string comment
        int likes
        int dislikes
        timestamp created_at
    }

    Purchases {
        int purchase_id PK
        int user_id FK
        int game_id FK
        timestamp purchased_at
    }

    Posts {
        int post_id PK
        int user_id FK
        enum category
        string title
        string content
        string attachment
        timestamp created_at
    }

    Comments {
        int comment_id PK
        int post_id FK
        int user_id FK
        string content
        timestamp created_at
    }

    Marketplace {
        int listing_id PK
        int user_id FK
        int game_id FK
        string item_description
        decimal price
        timestamp created_at
    }

    Library {
        int library_id PK
        int user_id FK
        int game_id FK
        int play_time
        timestamp last_played
    }

    Game_Stats {
        int stat_id PK
        int user_id FK
        int game_id FK
        int score
        int level
        string achievements
    }