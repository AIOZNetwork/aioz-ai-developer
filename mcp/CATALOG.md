# AIOZ AI Platform MCP Catalog

This catalog provides a comprehensive list of tools available on the AIOZ AI Platform MCP Server. The server includes both **Public Tools** (no authentication required) and **Authenticated Tools** (API Key required).

---

## Collection Module
Tools for creating and managing collections.
**Total: 8 tools (8 Authenticated)**

### Authenticated Tools
- `create_collection`: Create Collection.
- `get_list_collection`: Get List Collection.
- `get_collection_by_id`: Get Collection By Id.
- `update_collection`: Update Collection.
- `remove_item_from_collection`: Remove Item From Collection.
- `add_item_to_collection`: Add Item To Collection.
- `vote_collection`: Vote Collection.
- `get_collection_list_by_username`: Get Collection List By Username.

---

## Comment Module
Tools for comment operations.
**Total: 3 tools (3 Authenticated)**

### Authenticated Tools
- `update_comment`: Update comment.
- `get_comment_list`: Get comment list.
- `create_comment`: Create comment. Content max length is 10000 characters.

---

## Competition Module
Tools for competition lifecycle and leaderboard operations.
**Total: 10 tools (10 Authenticated)**

### Authenticated Tools
- `list_competitions`: List competitions. Get a list of competitions with filtering options.
- `get_competition_details_by_path`: Get competition details by path. Get details of a specific competition by path.
- `check_valid_repo_to_submit_data`: Check valid repo to submit data. Check valid repo to submit data for a competition.
- `submit_competition_data`: Submit competition data. Submit data for a competition.
- `estimate_cost_to_submit_data`: Estimate cost to submit data. Estimate cost to submit data for a competition.
- `get_submission_history`: Get submission history. Get submission history for a competition. sort is [created_at, score]. filter is [pending, completed, failed].
- `get_competition_details`: Get competition details. Get details of a specific competition by ID.
- `join_a_competition`: Join a competition. Join an existing competition by its ID.
- `get_competition_leaderboard`: Get competition leaderboard. Get leaderboard for a competition. Type allowed [public, private]. Sort allowed [accuracy, submissions].
- `get_leaderboard_by_competition_id_and_phase`: GetLeaderboardByCompetitionIdAndPhase. GetLeaderboardByCompetitionIdAndPhase. Sort allowed [accuracy, submissions].

---

## Core Module
Tools for core operations.
**Total: 3 tools (3 Authenticated)**

### Authenticated Tools
- `get_api_key_balance`: Get Api Key Balance.
- `get_api_key_info`: Get Api Key Info.
- `get_api_key_statistics`: Get Api Key Statistics.

---

## Dataset Module
Tools for dataset CRUD and discovery.
**Total: 9 tools (9 Authenticated)**

### Authenticated Tools
- `create_dataset`: Create dataset.
- `get_dataset_list`: Get dataset list. sort is one of trending, likes, downloads, created, created_oldest, modified.
- `get_dataset_list_by_user`: Get dataset list by user. sort is one of likes, downloads, created, modified.
- `get_matching_datasets_tags`: Get matching datasets tags. tag_type is one of tasks, sizes, licenses, languages, tags, all.
- `get_list_dataset_by_org_username`: Get List Dataset By Org Username. sort is one of name, size, created, modified.
- `get_dataset_by_id`: Get dataset by id.
- `update_dataset`: Update Dataset.
- `update_datasets_metadata`: Update dataset's metadata.
- `get_dataset_by_name`: Get dataset by name.

---

## Discussion Module
Tools for discussion threads and comments.
**Total: 7 tools (7 Authenticated)**

### Authenticated Tools
- `get_competition_discussion_list`: Get competition discussion list. sort is allow [trending, latest, active].
- `create_competition_discussion`: Create competition discussion. Content max length is 10000 characters.
- `get_dataset_discussion_list`: Get dataset discussion list. sort is allow [trending, latest, active].
- `create_dataset_discussion`: Create dataset discussion. Content max length is 10000 characters.
- `get_model_discussion_list`: Get model discussion list. sort is allow [trending, latest, active].
- `create_model_discussion`: Create model discussion. Content max length is 10000 characters.
- `update_discussion`: Update discussion.

---

## Model Module
Tools for public and private model lookup.
**Total: 14 tools (14 Authenticated)**

### Authenticated Tools
- `create_model`: Create Model.
- `get_model_list`: Get Model List. filter is one of author, community, official, permission, verified.
- `get_model_list_by_user`: Get Model List By User.
- `matching_models_tags`: MatchingModels Tags. tag_type is one of tasks, licenses, libraries, languages, all.
- `get_list_model_by_org_username`: Get List Model By Org Username. sort is one of name, created, modified.
- `get_model`: Get Model.
- `update_model`: Update Model.
- `get_api_key_model_info`: Get Api Key Model Info.
- `update_model_metadata`: Update Model Metadata.
- `check_model_is_serving`: Check Model Is Serving.
- `get_model_statistics`: Get Model Statistics.
- `get_cost_to_compute_task_by_model_api_key`: Get cost to compute task by model api key.
- `get_current_model_versioning_by_model_id_by_api_key`: Get Current Model Versioning By Model Id By ApiKey.
- `get_model_by_name`: Get Model By Name.

---

## Organization Module
Tools for organization management.
**Total: 12 tools (12 Authenticated)**

### Authenticated Tools
- `get_organizations`: Get organizations.
- `get_organization`: Get organization.
- `update_organizations_info`: Update organization's info.
- `get_organizations_members`: Get organization's members.
- `get_user_organization_permission`: Get user organization permission.
- `get_organzition_earnings_statistics_by_owner`: Get Organzition Earnings Statistics By Owner.
- `get_organzition_spending_cost_statistics_by_owner`: Get Organzition Spending Cost Statistics By Owner.
- `get_list_org_deposit_history_by_owner`: Get List Org Deposit History By Owner.
- `get_org_transaction_analytics_by_owner`: Get Org Transaction Analytics By Owner.
- `get_list_org_transaction_history_by_owner`: Get List Org Transaction History By Owner. type is one of all, earnings, buy, unlock, download, call api, compute task, use playground, storage, verify model.
- `get_list_org_recent_transaction_by_owner`: Get List Org Recent Transaction By Owner. type is one of all, credits, charges.
- `get_list_org_withdrawal_history_by_owner`: Get list org withdrawal history by owner.

---

## Public Module
Tools for public operations.
**Total: 5 tools (5 Public)**

### Public Tools
- `estimate_storage_cost`: Estimate storage cost.
- `get_list_metadata`: Get list metadata. Category: (dataset, model, competition) - Type:(language, license, size, tag, task, library, category, reward, status, tag).
- `get_aioz_token_price`: Get Aioz token price.
- `get_user_medals_by_medal_name`: Get user medals by medal name. Get user medals by medal name. Medal name is allowed [gold, silver, bronze, swag, kudos, knowledge].
- `get_user_medal_statistics_by_username`: Get user medal statistics by username. Get user medal statistics by username.

---

## Reaction Module
Tools for reaction operations.
**Total: 3 tools (3 Authenticated)**

### Authenticated Tools
- `like_dataset`: Like dataset.
- `react_item`: React item. React to item (discussion, comment, collection).
- `like_model`: Like model.

---

## Repository Module
Tools for repository data retrieval.
**Total: 1 tool (1 Authenticated)**

### Authenticated Tools
- `get_readme_file_content`: Get readme file content.

---

## Storage Module
Tools for storage and URL management.
**Total: 4 tools (4 Authenticated)**

### Authenticated Tools
- `create_presigned_url`: Create Presigned Url. folder is one of avatars, thumbnails, covers, samples, documents.
- `get_user_upload_statistics`: Get user upload statistics.
- `get_user_uploads_by_folder`: Get user uploads by folder.
- `delete_url`: Delete Url.

---

## Task Module
Tools for task distribution and history.
**Total: 8 tools (8 Authenticated)**

### Authenticated Tools
- `get_task_review_by_task_id`: Get Task Review By Task Id.
- `distribute_task_v2`: Distribute Task v2.
- `create_task_reviews`: Create Task Reviews.
- `get_platform_task_by_id`: Get Platform Task By Id.
- `distribute_task`: Distribute Task.
- `get_tasks_histories`: Get Tasks Histories.
- `cancel_task`: Cancel Task.
- `get_api_key_log_by_task_id`: Get Api Key Log By TaskId.

---

## User Module
Tools for user profile and dashboard operations.
**Total: 11 tools (11 Authenticated)**

### Authenticated Tools
- `get_users_info`: Get user's info.
- `get_users_organization_usernames`: Get user's organization usernames.
- `update_users_profile`: Update user's profile.
- `get_user_earnings_statistics`: Get User Earnings Statistics.
- `get_user_spending_cost_statistics`: Get User Spending Cost Statistics.
- `get_list_user_deposit_history`: Get List User Deposit History.
- `get_user_transaction_analytics`: Get User Transaction Analytics.
- `get_list_transaction_history_by_user`: Get List Transaction History By User. type is one of all, earnings, buy, unlock, download, call api, compute task, use playground, storage, verify model.
- `get_list_recent_transaction_by_user`: Get List Recent Transaction By User. type is one of all, credits, charges.
- `get_list_user_withdrawal_history`: Get List User Withdrawal History.
- `get_users_info_username`: Get user's info.

---

