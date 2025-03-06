# appsheet

Here is the ER diagram for my project:

```mermaid
erDiagram
    プロジェクト管理_ユーザー一覧_2024 {
        string 名前 PK
        string 権限
        boolean 削除フラグ
        datetime 作成日時
        string 作成者 FK
        datetime 最終更新日時
        string 最終更新者 FK
    }

    プロジェクト管理_タスク一覧_2024 {
        string タスクID PK
        string タスク名
        string ステータス
        text 詳細
        datetime 開始
        datetime 期限
        datetime 対応予定日
        string 担当者 FK
        decimal 工数
        string 作業ファイルリンク
        string 参考リンク
        boolean 削除フラグ
        datetime 作成日時
        string 作成者 FK
        datetime 最終更新日時
        string 最終更新者 FK
        string マイルストーン名 FK
        string プロジェクト名 FK
    }

    プロジェクト管理_マイルストーン一覧_2024 {
        string マイルストーンID PK
        string マイルストーン名
        string ステータス
        string プロジェクト名 FK
    }

    プロジェクト管理_プロジェクト一覧_2024 {
        string プロジェクトID PK
        string プロジェクト名
        string リーダー FK
    }

    プロジェクト管理_メモ一覧_2024 {
        string メモID PK
        text メモ内容
        string タスクID FK
        boolean 削除フラグ
        datetime 投稿日時
        string 投稿者 FK
        datetime 最終更新日時
        string 最終更新者 FK
    }

    プロジェクト管理_ユーザー一覧_2024 ||--o{ プロジェクト管理_タスク一覧_2024 : "担当者"
    プロジェクト管理_タスク一覧_2024 }o--|| プロジェクト管理_マイルストーン一覧_2024 : "関連"
    プロジェクト管理_マイルストーン一覧_2024 }o--|| プロジェクト管理_プロジェクト一覧_2024 : "関連"
    プロジェクト管理_タスク一覧_2024 ||--o{ プロジェクト管理_メモ一覧_2024 : "関連"
    プロジェクト管理_プロジェクト一覧_2024 ||--o{ プロジェクト管理_タスク一覧_2024 : "関連"
