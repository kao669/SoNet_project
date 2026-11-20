erDiagram
    users ||--o{ posts : "작성한다 (1:N)"
    categories ||--o{ posts : "포함한다 (1:N)"
    posts ||--o{ post_images : "첨부한다 (1:N)"
    posts ||--o{ likes : "받는다 (1:N)"
    users ||--o{ likes : "누른다 (1:N)"
    posts ||--o{ comments : "가진다 (1:N)"
    users ||--o{ comments : "남긴다 (1:N)"

    users {
        BIGINT user_id PK "회원번호"
        VARCHAR(100) email UK "이메일(로그인ID)"
        VARCHAR(255) password "비밀번호"
        VARCHAR(30) nickname UK "닉네임"
        VARCHAR(500) profile_img_url "프로필이미지경로"
        VARCHAR(20) role "권한(ROLE_USER)"
        DATETIME created_at "가입일시"
    }

    categories {
        BIGINT category_id PK "채널번호"
        VARCHAR(50) name UK "채널명"
        VARCHAR(200) description "채널설명"
        INT display_order "정렬순서"
    }

    posts {
        BIGINT post_id PK "게시글번호"
        BIGINT user_id FK "작성자번호"
        BIGINT category_id FK "채널번호"
        VARCHAR(1000) content "본문내용"
        VARCHAR(255) hashtags "해시태그"
        DATETIME created_at "작성일시"
        DATETIME updated_at "수정일시"
    }

    post_images {
        BIGINT image_id PK "이미지번호"
        BIGINT post_id FK "게시글번호"
        VARCHAR(500) image_url "이미지경로"
        VARCHAR(255) original_name "원본파일명"
        INT sort_order "정렬순서"
    }

    likes {
        BIGINT like_id PK "좋아요번호"
        BIGINT user_id FK,UK "회원번호"
        BIGINT post_id FK,UK "게시글번호"
        DATETIME created_at "생성일시"
    }

    comments {
        BIGINT comment_id PK "댓글번호"
        BIGINT post_id FK "게시글번호"
        BIGINT user_id FK "작성자번호"
        VARCHAR(500) content "댓글내용"
        DATETIME created_at "작성일시"
    }
