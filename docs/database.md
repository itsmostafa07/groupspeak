```
erDiagram
    USERS ||--o{ USER_SESSIONS : has
    USERS ||--o{ CONVERSATION_PARTICIPANTS : participates
    USERS ||--o{ MESSAGES : sends
    
    CONVERSATIONS ||--o{ CONVERSATION_PARTICIPANTS : contains
    CONVERSATIONS ||--o{ MESSAGES : contains
    
    USERS {
        uuid user_id PK
        string username UK
        string email UK
        string password_hash
        string display_name
        string avatar_url
        boolean is_online
        timestamp last_seen
        timestamp created_at
    }
    
    USER_SESSIONS {
        uuid session_id PK
        uuid user_id FK
        string session_token UK
        string device_info
        timestamp created_at
        timestamp expires_at
        timestamp last_activity
    }
    
    CONVERSATIONS {
        uuid conversation_id PK
        string name
        boolean is_group
        timestamp created_at
    }
    
    CONVERSATION_PARTICIPANTS {
        uuid participant_id PK
        uuid conversation_id FK
        uuid user_id FK
        timestamp joined_at
    }
    
    MESSAGES {
        uuid message_id PK
        uuid conversation_id FK
        uuid sender_id FK
        text content
        timestamp created_at
    }
```