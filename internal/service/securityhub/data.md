
### 【〇】entities

| カラム名 | データ型 | 制約 | デフォルト値 | 説明 | Atlas送信対象 |
| --- | --- | --- | --- | --- | --- |
| id | uuid |  |  | 主キー | 〇 |
| status | character varying |  | 'published' | ステータス | 〇 |
| sort | integer | nullable |  | ソート順 | 〇 |
| user_created | uuid | nullable |  | 作成者 | 〇 |
| date_created | timestamp with time zone | nullable |  | 作成日時 | 〇 |
| user_updated | uuid | nullable |  | 更新者 | 〇 |
| date_updated | timestamp with time zone | nullable |  | 更新日時 | 〇 |
| entity_name | character varying | nullable | NULL | 企業名 | 〇 |
| address | character varying | nullable | NULL | 住所 | 〇 |
| phone_number | character varying | nullable | NULL | 電話番号 | 〇 |
| corporate_number | character varying | nullable | NULL | 法人番号 | 〇 |
| postal_code | character varying | nullable | NULL | 郵便番号 | 〇 |
| closing_month | integer | nullable |  | 決算月 | 〇 |
| mail_domains | json | nullable |  | メールドメイン | 〇 |

### 【〇】invitation_email_histories

| カラム名 | データ型 | 制約 | デフォルト値 | 説明 | Atlas送信対象 |
| --- | --- | --- | --- | --- | --- |
| id | uuid |  |  | 主キー | 〇 |
| date_created | timestamp with time zone | nullable |  | 作成日時 | 〇 |
| date_updated | timestamp with time zone | nullable |  | 更新日時 | 〇 |
| status | character varying | nullable | 'inviting' | ステータス | 〇 |
| email | character varying | nullable | NULL | メールアドレス |  |
| entity_id | character varying | nullable |  | 企業ID | 〇 |
| is_email_sent | boolean | nullable | false | メール送信フラグ | 〇 |
| user_created | uuid | nullable |  | 作成者 | 〇 |
| is_user_joined | boolean | nullable |  | ユーザー参加フラグ | 〇 |
| date_expired | timestamp with time zone | nullable |  | 有効期限 | 〇 |

### 【〇】invitations

| カラム名 | データ型 | 制約 | デフォルト値 | 説明 | Atlas送信対象 |
| --- | --- | --- | --- | --- | --- |
| id | uuid |  |  | 主キー | 〇 |
| status | character varying |  | 'published' | ステータス | 〇 |
| sort | integer | nullable |  | ソート順 | 〇 |
| user_created | uuid | nullable |  | 作成者 | 〇 |
| date_created | timestamp with time zone | nullable |  | 作成日時 | 〇 |
| user_updated | uuid | nullable |  | 更新者 | 〇 |
| date_updated | timestamp with time zone | nullable |  | 更新日時 | 〇 |
| entity_id | uuid | nullable |  | 企業ID | 〇 |
| invitation_code | character varying | nullable | NULL | 招待コード | 〇 |
| is_reusable | boolean | nullable | false | 再利用可能フラグ | 〇 |
| expires_at | timestamp without time zone | nullable |  | 有効期限 | 〇 |
| issued_by | uuid | nullable |  | 発行者 | 〇 |
| project_ids | json | nullable |  | プロジェクトID一覧 | 〇 |
| survey_ids | json | nullable |  | 調査ID一覧 | 〇 |
| invitation_status | character varying |  | 'unused' | 招待ステータス | 〇 |
| id_type | character varying | nullable | NULL | IDタイプ | 〇 |
| issuer_type | character varying | nullable | NULL | 発行者タイプ | 〇 |

### 【〇】projects

| カラム名 | データ型 | 制約 | デフォルト値 | 説明 | Atlas送信対象 |
| --- | --- | --- | --- | --- | --- |
| id | uuid |  |  | 主キー | 〇 |
| status | character varying |  | 'published' | ステータス | 〇 |
| sort | integer | nullable |  | ソート順 | 〇 |
| user_created | uuid | nullable |  | 作成者 | 〇 |
| date_created | timestamp with time zone | nullable |  | 作成日時 | 〇 |
| user_updated | uuid | nullable |  | 更新者 | 〇 |
| date_updated | timestamp with time zone | nullable |  | 更新日時 | 〇 |
| project_name | character varying | nullable | NULL | プロジェクト名 | 〇 |
| overview | text | nullable |  | 概要 | 〇 |
| requester | character varying | nullable | '日本経済新聞社' | 依頼者 | 〇 |
| usage | text | nullable |  | 用途 | 〇 |
| faqs | json | nullable |  | FAQ | 〇 |
| needs_commercial_consent | boolean | nullable | false | 商用同意必要フラグ | 〇 |
| entity_users | json | nullable |  | 企業ユーザー | 〇 |

### 【〇】projects_entities (中間テーブル)

| カラム名 | データ型 | 制約 | デフォルト値 | 説明 | Atlas送信対象 |
| --- | --- | --- | --- | --- | --- |
| id | integer |  | nextval() | 主キー | 〇 |
| project_id | uuid | nullable |  | プロジェクトID | 〇 |
| entity_id | uuid | nullable |  | 企業ID | 〇 |

### 【〇】survey_answers

| カラム名 | データ型 | 制約 | デフォルト値 | 説明 | Atlas送信対象 |
| --- | --- | --- | --- | --- | --- |
| id | character varying |  | NULL | 主キー | 〇 |
| status | character varying |  | 'published' | ステータス | 〇 |
| sort | integer | nullable |  | ソート順 | 〇 |
| user_created | uuid | nullable |  | 作成者 | 〇 |
| date_created | timestamp with time zone | nullable |  | 作成日時 | 〇 |
| user_updated | uuid | nullable |  | 更新者 | 〇 |
| date_updated | timestamp with time zone | nullable |  | 更新日時 | 〇 |
| download_excel | uuid | nullable |  | ダウンロードExcel |  |
| upload_excel | uuid | nullable |  | アップロードExcel |  |
| survey_id | uuid | nullable |  | 調査ID | 〇 |
| answer_method | character varying | nullable | NULL | 回答方法 | 〇 |
| submitted_by | uuid | nullable |  | 提出者 | 〇 |
| submit_time | timestamp without time zone | nullable |  | 提出日時 | 〇 |
| department | character varying | nullable | NULL | 部署 | 〇 |
| position | character varying | nullable | NULL | 役職 | 〇 |
| contact_name | character varying | nullable | NULL | 連絡先名 |  |
| email | character varying | nullable | NULL | メールアドレス |  |
| phone_number | character varying | nullable | NULL | 電話番号 | 〇 |
| fax_number | character varying | nullable | NULL | FAX番号 | 〇 |
| can_commercial_use | boolean | nullable | false | 商用利用可能フラグ | 〇 |
| answer | json | nullable |  | 回答 |  |
| entity_id | uuid | nullable |  | 企業ID | 〇 |
| survey_status | character varying |  | 'undecided' | 調査ステータス | 〇 |
| initial_answer | json | nullable |  | 初期回答 |  |
| answer_owners | json | nullable |  | 回答所有者 | 〇 |
| page_answers | json | nullable |  | ページ回答 |  |
| question_metadata | json | nullable |  | 質問メタデータ |  |
| previous_survey_summary_id | uuid | nullable |  | 前回調査サマリーID | 〇 |

### 【〇】surveys

| カラム名 | データ型 | 制約 | デフォルト値 | 説明 | Atlas送信対象 |
| --- | --- | --- | --- | --- | --- |
| id | uuid |  |  | 主キー | 〇 |
| status | character varying |  | 'draft' | ステータス | 〇 |
| sort | integer | nullable |  | ソート順 | 〇 |
| user_created | uuid | nullable |  | 作成者 | 〇 |
| date_created | timestamp with time zone | nullable |  | 作成日時 | 〇 |
| user_updated | uuid | nullable |  | 更新者 | 〇 |
| date_updated | timestamp with time zone | nullable |  | 更新日時 | 〇 |
| project_id | uuid | nullable |  | プロジェクトID | 〇 |
| survey_name | character varying | nullable | NULL | 調査名 | 〇 |
| survey_no | character varying | nullable | NULL | 調査番号 | 〇 |
| survey_qa | json | nullable |  | 調査Q&A | 〇 |
| variable_definition | json | nullable |  | 変数定義 | 〇 |
| start_date | date | nullable |  | 開始日 | 〇 |
| end_date | date | nullable |  | 終了日 | 〇 |
| previous_answer | json | nullable |  | 前回回答 | 〇 |
| question_num | character varying | nullable | NULL | 質問番号 | 〇 |
| schedules | json | nullable |  | スケジュール | 〇 |
| consent_matters | json | nullable |  | 同意事項 | 〇 |
| request_mode_enabled | boolean | nullable | false | リクエストモード有効フラグ | 〇 |
| answer_methods | json | nullable | ["web","excel"] | 回答方法 | 〇 |
| participant_type | character varying | nullable | NULL | 参加者タイプ | 〇 |
| articles | json | nullable |  | 記事 | 〇 |
| lasttime_output_time | timestamp with time zone | nullable |  | 最終出力時間 | 〇 |
| post_survey_flag | boolean | nullable | false | アンケート後フラグ | 〇 |
| post_survey | character varying | nullable | NULL | アンケート後 | 〇 |

### 【〇】users

| カラム名 | データ型 | 制約 | デフォルト値 | 説明 | Atlas送信対象 |
| --- | --- | --- | --- | --- | --- |
| id | uuid |  |  | 主キー | 〇 |
| status | character varying |  | 'published' | ステータス | 〇 |
| sort | integer | nullable |  | ソート順 | 〇 |
| user_created | uuid | nullable |  | 作成者 | 〇 |
| date_created | timestamp with time zone | nullable |  | 作成日時 | 〇 |
| user_updated | uuid | nullable |  | 更新者 | 〇 |
| date_updated | timestamp with time zone | nullable |  | 更新日時 | 〇 |
| display_name | character varying | nullable | NULL | 表示名 |  |
| department | character varying | nullable | NULL | 部署 | 〇 |
| login_id | character varying | nullable | NULL | ログインID |  |
| id_type | character varying | nullable | NULL | IDタイプ | 〇 |
| service_consent | character varying | nullable | 'NULL' | サービス同意 | 〇 |
| survey_id | uuid | nullable |  | 調査ID | 〇 |
| used_invitation_code | character varying | nullable | NULL | 使用招待コード | 〇 |
| directus_user_id | uuid |  |  | DirectusユーザーID | 〇 |
| user_serial_id | character varying | nullable | NULL | ユーザーシリアルID |  |
| nikkei_member_no | character varying | nullable | NULL | 日経会員番号 |  |
| user_status | character varying | nullable | 'inactive' | ユーザーステータス | 〇 |

### 【〇】users_entities (中間テーブル)

| カラム名 | データ型 | 制約 | デフォルト値 | 説明 | Atlas送信対象 |
| --- | --- | --- | --- | --- | --- |
| id | integer |  | nextval() | 主キー | 〇 |
| user_id | uuid | nullable |  | ユーザーID | 〇 |
| entity_id | uuid | nullable |  | 企業ID | 〇 |

### 【✕】assigned_user_email_histories

| カラム名 | データ型 | 制約 | デフォルト値 | 説明 | Atlas送信対象 |
| --- | --- | --- | --- | --- | --- |
| id | uuid |  |  | 主キー |  |
| user_created | uuid | nullable |  | 作成者 |  |
| date_created | timestamp with time zone | nullable |  | 作成日時 |  |
| email | character varying | nullable |  | メールアドレス |  |
| entity_id | uuid | nullable |  | 企業ID |  |
| survey_id | uuid | nullable |  | 調査ID |  |
| is_email_sent | boolean | nullable | false | メール送信フラグ |  |

### 【✕】contacts

| カラム名 | データ型 | 制約 | デフォルト値 | 説明 | Atlas送信対象 |
| --- | --- | --- | --- | --- | --- |
| id | uuid |  |  | 主キー |  |
| status | character varying |  | 'published' | ステータス |  |
| sort | integer | nullable |  | ソート順 |  |
| user_created | uuid | nullable |  | 作成者 |  |
| date_created | timestamp with time zone | nullable |  | 作成日時 |  |
| user_updated | uuid | nullable |  | 更新者 |  |
| date_updated | timestamp with time zone | nullable |  | 更新日時 |  |
| usage | character varying | nullable | NULL | 用途 |  |
| contact_category | character varying | nullable | NULL | 連絡先カテゴリ |  |
| email | character varying | nullable | NULL | メールアドレス |  |
| phone_number | character varying | nullable | NULL | 電話番号 |  |
| fax_number | character varying | nullable | NULL | FAX番号 |  |
| hours_of_operation | text | nullable |  | 営業時間 |  |
| contact_name | text | nullable |  | 連絡先名 |  |
| postal_code | character varying | nullable | NULL | 郵便番号 |  |
| address | character varying | nullable | NULL | 住所 |  |
| send_flg | boolean | nullable | false | 送信フラグ |  |

### 【✕】entity_groups

| カラム名 | データ型 | 制約 | デフォルト値 | 説明 | Atlas送信対象 |
| --- | --- | --- | --- | --- | --- |
| id | uuid |  |  | 主キー |  |
| status | character varying |  | 'draft' | ステータス |  |
| sort | integer | nullable |  | ソート順 |  |
| user_created | uuid | nullable |  | 作成者 |  |
| date_created | timestamp with time zone | nullable |  | 作成日時 |  |
| user_updated | uuid | nullable |  | 更新者 |  |
| date_updated | timestamp with time zone | nullable |  | 更新日時 |  |
| group_no | character varying | nullable | NULL | グループ番号 |  |
| group_name | character varying | nullable | NULL | グループ名 |  |

### 【✕】esg_publishments

| カラム名 | データ型 | 制約 | デフォルト値 | 説明 | Atlas送信対象 |
| --- | --- | --- | --- | --- | --- |
| id | character varying |  | NULL | 主キー |  |
| status | character varying |  | 'draft' | ステータス |  |
| sort | integer | nullable |  | ソート順 |  |
| user_created | uuid | nullable |  | 作成者 |  |
| date_created | timestamp with time zone | nullable |  | 作成日時 |  |
| user_updated | uuid | nullable |  | 更新者 |  |
| date_updated | timestamp with time zone | nullable |  | 更新日時 |  |
| version_number | integer | nullable |  | バージョン番号 |  |
| year | integer | nullable |  | 年度 |  |
| criteria | character varying | nullable | NULL | 基準 |  |
| entity_id | uuid | nullable |  | 企業ID |  |
| survey_id | uuid | nullable |  | 調査ID |  |
| raw_answer | json | nullable |  | 生回答 |  |
| publishment_answer | json | nullable |  | 公開用回答 |  |
| check_result | character varying | nullable | NULL | チェック結果 |  |
| submitted_by | uuid | nullable |  | 提出者 |  |
| submit_time | timestamp without time zone | nullable |  | 提出日時 |  |

### 【✕】esg_survey_answer_operations (オペレーション用)

| カラム名 | データ型 | 制約 | デフォルト値 | 説明 | Atlas送信対象 |
| --- | --- | --- | --- | --- | --- |
| id | integer |  | nextval() | 主キー |  |
| status | character varying |  | 'draft' | ステータス |  |
| sort | integer | nullable |  | ソート順 |  |
| user_created | uuid | nullable |  | 作成者 |  |
| date_created | timestamp with time zone | nullable |  | 作成日時 |  |
| user_updated | uuid | nullable |  | 更新者 |  |
| date_updated | timestamp with time zone | nullable |  | 更新日時 |  |
| mode | character varying | nullable | NULL | モード |  |
| survey_id | uuid | nullable |  | 調査ID |  |
| processed_status | character varying | nullable | NULL | 処理ステータス |  |
| processed_message | json | nullable |  | 処理メッセージ |  |

### 【✕】faqs

| カラム名 | データ型 | 制約 | デフォルト値 | 説明 | Atlas送信対象 |
| --- | --- | --- | --- | --- | --- |
| id | uuid |  |  | 主キー |  |
| status | character varying |  | 'draft' | ステータス |  |
| sort | integer | nullable |  | ソート順 |  |
| user_created | uuid | nullable |  | 作成者 |  |
| date_created | timestamp with time zone | nullable |  | 作成日時 |  |
| user_updated | uuid | nullable |  | 更新者 |  |
| date_updated | timestamp with time zone | nullable |  | 更新日時 |  |
| title | character varying | nullable | NULL | タイトル |  |
| body | text | nullable |  | 本文 |  |
| categories | json | nullable |  | カテゴリ |  |

### 【✕】import_entities (オペレーション用)

| カラム名 | データ型 | 制約 | デフォルト値 | 説明 | Atlas送信対象 |
| --- | --- | --- | --- | --- | --- |
| id | uuid |  |  | 主キー |  |
| status | character varying |  | 'draft' | ステータス |  |
| sort | integer | nullable |  | ソート順 |  |
| user_created | uuid | nullable |  | 作成者 |  |
| date_created | timestamp with time zone | nullable |  | 作成日時 |  |
| user_updated | uuid | nullable |  | 更新者 |  |
| date_updated | timestamp with time zone | nullable |  | 更新日時 |  |
| project_id | uuid | nullable |  | プロジェクトID |  |
| link_specified_orgs | boolean | nullable | false | 指定組織連携フラグ |  |
| input_file | uuid | nullable |  | 入力ファイル |  |
| import_status | character varying | nullable | NULL | インポートステータス |  |
| processed_message | json | nullable |  | 処理メッセージ |  |
| mode | character varying | nullable | NULL | モード |  |
| export_file | uuid | nullable |  | エクスポートファイル |  |

### 【✕】inquiries

| カラム名 | データ型 | 制約 | デフォルト値 | 説明 | Atlas送信対象 |
| --- | --- | --- | --- | --- | --- |
| id | uuid |  |  | 主キー |  |
| status | character varying |  | 'published' | ステータス |  |
| sort | integer | nullable |  | ソート順 |  |
| user_created | uuid | nullable |  | 作成者 |  |
| date_created | timestamp with time zone | nullable |  | 作成日時 |  |
| user_updated | uuid | nullable |  | 更新者 |  |
| date_updated | timestamp with time zone | nullable |  | 更新日時 |  |
| title | character varying | nullable | NULL | タイトル |  |
| login_id | character varying | nullable | NULL | ログインID |  |
| name | character varying | nullable | NULL | 氏名 |  |
| department | character varying | nullable | NULL | 部署 |  |
| email | character varying | nullable | NULL | メールアドレス |  |
| body | text | nullable |  | 本文 |  |
| referrer_url | character varying | nullable | NULL | 参照元URL |  |
| inquiry_status | character varying | nullable | 'not_started' | 問い合わせステータス |  |
| inquiry_notes | json | nullable |  | 問い合わせメモ |  |

### 【✕】invitation_operations (オペレーション用)

| カラム名 | データ型 | 制約 | デフォルト値 | 説明 | Atlas送信対象 |
| --- | --- | --- | --- | --- | --- |
| id | uuid |  |  | 主キー |  |
| status | character varying |  | 'draft' | ステータス |  |
| sort | integer | nullable |  | ソート順 |  |
| user_created | uuid | nullable |  | 作成者 |  |
| date_created | timestamp with time zone | nullable |  | 作成日時 |  |
| user_updated | uuid | nullable |  | 更新者 |  |
| date_updated | timestamp with time zone | nullable |  | 更新日時 |  |
| project_id | uuid | nullable |  | プロジェクトID |  |
| expires_date | timestamp without time zone | nullable |  | 有効期限日 |  |
| export | boolean | nullable | false | エクスポートフラグ |  |
| export_file | uuid | nullable |  | エクスポートファイル |  |
| mode | character varying | nullable | NULL | モード |  |
| survey_id | uuid | nullable |  | 調査ID |  |
| tsvfile | uuid | nullable |  | TSVファイル |  |
| processed_status | character varying | nullable | NULL | 処理ステータス |  |
| processed_message | json | nullable |  | 処理メッセージ |  |
| closing_month | integer | nullable |  | 決算月 |  |

### 【✕】letter_addresses

| カラム名 | データ型 | 制約 | デフォルト値 | 説明 | Atlas送信対象 |
| --- | --- | --- | --- | --- | --- |
| id | character varying |  | NULL | 主キー |  |
| status | character varying |  | 'published' | ステータス |  |
| sort | integer | nullable |  | ソート順 |  |
| user_created | uuid | nullable |  | 作成者 |  |
| date_created | timestamp with time zone | nullable |  | 作成日時 |  |
| user_updated | uuid | nullable |  | 更新者 |  |
| date_updated | timestamp with time zone | nullable |  | 更新日時 |  |
| entity_name | character varying | nullable | NULL | 企業名 |  |
| department | character varying | nullable | NULL | 部署 |  |
| position | character varying | nullable | NULL | 役職 |  |
| contact_name | character varying | nullable | NULL | 連絡先名 |  |
| postal_code | character varying | nullable | NULL | 郵便番号 |  |
| address | character varying | nullable | NULL | 住所 |  |
| email | character varying | nullable | NULL | メールアドレス |  |
| phone_number | character varying | nullable | NULL | 電話番号 |  |
| fax_number | character varying | nullable | NULL | FAX番号 |  |
| contains_survey | boolean | nullable | true | 調査含有フラグ |  |
| project_id | uuid | nullable |  | プロジェクトID |  |
| entity_id | uuid | nullable |  | 企業ID |  |
| is_primary | boolean | nullable | false | 主要フラグ |  |

### 【✕】notifications

| カラム名 | データ型 | 制約 | デフォルト値 | 説明 | Atlas送信対象 |
| --- | --- | --- | --- | --- | --- |
| id | uuid |  |  | 主キー |  |
| status | character varying |  | 'draft' | ステータス |  |
| sort | integer | nullable |  | ソート順 |  |
| user_created | uuid | nullable |  | 作成者 |  |
| date_created | timestamp with time zone | nullable |  | 作成日時 |  |
| user_updated | uuid | nullable |  | 更新者 |  |
| date_updated | timestamp with time zone | nullable |  | 更新日時 |  |
| title | character varying | nullable | NULL | タイトル |  |
| body | text | nullable |  | 本文 |  |
| from | timestamp without time zone | nullable |  | 開始日時 |  |
| to | timestamp without time zone | nullable |  | 終了日時 |  |

### 【✕】previous_survey_operations (オペレーション用)

| カラム名 | データ型 | 制約 | デフォルト値 | 説明 | Atlas送信対象 |
| --- | --- | --- | --- | --- | --- |
| id | uuid |  |  | 主キー |  |
| status | character varying |  | 'draft' | ステータス |  |
| sort | integer | nullable |  | ソート順 |  |
| user_created | uuid | nullable |  | 作成者 |  |
| date_created | timestamp with time zone | nullable |  | 作成日時 |  |
| user_updated | uuid | nullable |  | 更新者 |  |
| date_updated | timestamp with time zone | nullable |  | 更新日時 |  |
| mode | character varying | nullable | NULL | モード |  |
| previous_survey_id | uuid | nullable |  | 前回調査ID |  |
| import_tsvfile | uuid | nullable |  | インポートTSVファイル |  |
| processed_status | character varying | nullable | NULL | 処理ステータス |  |
| processed_message | json | nullable |  | 処理メッセージ |  |

### 【✕】previous_survey_summaries

| カラム名 | データ型 | 制約 | デフォルト値 | 説明 | Atlas送信対象 |
| --- | --- | --- | --- | --- | --- |
| id | uuid |  |  | 主キー |  |
| status | character varying |  | 'draft' | ステータス |  |
| sort | integer | nullable |  | ソート順 |  |
| user_created | uuid | nullable |  | 作成者 |  |
| date_created | timestamp with time zone | nullable |  | 作成日時 |  |
| user_updated | uuid | nullable |  | 更新者 |  |
| date_updated | timestamp with time zone | nullable |  | 更新日時 |  |
| previous_survey_id | uuid | nullable |  | 前回調査ID |  |
| entity_group_id | uuid | nullable |  | 企業グループID |  |
| answer_count | integer | nullable |  | 回答数 |  |
| answer_request_count | integer | nullable |  | 回答依頼数 |  |
| aggregation_type | character varying | nullable | NULL | 集計タイプ |  |

### 【✕】projects_contacts (中間テーブル)

| カラム名 | データ型 | 制約 | デフォルト値 | 説明 | Atlas送信対象 |
| --- | --- | --- | --- | --- | --- |
| id | integer |  | nextval() | 主キー |  |
| project_id | uuid | nullable |  | プロジェクトID |  |
| contact_id | uuid | nullable |  | 連絡先ID |  |

### 【✕】survey_answer_operations (オペレーション用)

| カラム名 | データ型 | 制約 | デフォルト値 | 説明 | Atlas送信対象 |
| --- | --- | --- | --- | --- | --- |
| id | uuid |  |  | 主キー |  |
| status | character varying |  | 'draft' | ステータス |  |
| sort | integer | nullable |  | ソート順 |  |
| user_created | uuid | nullable |  | 作成者 |  |
| date_created | timestamp with time zone | nullable |  | 作成日時 |  |
| user_updated | uuid | nullable |  | 更新者 |  |
| date_updated | timestamp with time zone | nullable |  | 更新日時 |  |
| mode | character varying |  | NULL | モード |  |
| survey_id | uuid | nullable |  | 調査ID |  |
| output_file | uuid | nullable |  | 出力ファイル |  |
| excel_zipfile | uuid | nullable |  | ExcelZIPファイル |  |
| setting_tsvfile | uuid | nullable |  | 設定TSVファイル |  |
| processed_status | character varying | nullable | NULL | 処理ステータス |  |
| processed_message | json | nullable |  | 処理メッセージ |  |
| closing_month | integer | nullable |  | 決算月 |  |
| download_excel_file | uuid | nullable |  | ダウンロードExcelファイル |  |
| initial_answer_tsvfile | uuid | nullable |  | 初期回答TSVファイル |  |
| download_type | character varying | nullable | NULL | ダウンロードタイプ |  |
| previous_survey_id | uuid | nullable |  | 前回調査ID |  |

### 【✕】survey_answers_files (中間テーブル)

| カラム名 | データ型 | 制約 | デフォルト値 | 説明 | Atlas送信対象 |
| --- | --- | --- | --- | --- | --- |
| id | integer |  | nextval() | 主キー |  |
| survey_answers_id | character varying | nullable | NULL | 調査回答ID |  |
| directus_files_id | uuid | nullable |  | DirectusファイルID |  |

### 【✕】surveys_contacts (中間テーブル)

| カラム名 | データ型 | 制約 | デフォルト値 | 説明 | Atlas送信対象 |
| --- | --- | --- | --- | --- | --- |
| id | integer |  | nextval() | 主キー |  |
| survey_id | uuid | nullable |  | 調査ID |  |
| contact_id | uuid | nullable |  | 連絡先ID |  |

### 【✕】user_activities

| カラム名 | データ型 | 制約 | デフォルト値 | 説明 | Atlas送信対象 |
| --- | --- | --- | --- | --- | --- |
| id | uuid |  |  | 主キー |  |
| status | character varying |  | 'draft' | ステータス |  |
| sort | integer | nullable |  | ソート順 |  |
| user_created | uuid | nullable |  | 作成者 |  |
| date_created | timestamp with time zone | nullable |  | 作成日時 |  |
| user_updated | uuid | nullable |  | 更新者 |  |
| date_updated | timestamp with time zone | nullable |  | 更新日時 |  |
| user_id | uuid | nullable |  | ユーザーID |  |
| entity_id | uuid | nullable |  | 企業ID |  |
| survey_id | uuid | nullable |  | 調査ID |  |
| activity_type | character varying | nullable | NULL | アクティビティタイプ |  |
| new_metadata | json | nullable |  | 新メタデータ |  |
| old_metadata | json | nullable |  | 旧メタデータ |  |
| page_id | character varying | nullable | NULL | ページID |  |
| question_id | character varying | nullable | NULL | 質問ID |  |
| page_text | character varying | nullable | NULL | ページテキスト |  |
| question_text | character varying | nullable | NULL | 質問テキスト |  |
| comment | text | nullable |  | コメント |  |
