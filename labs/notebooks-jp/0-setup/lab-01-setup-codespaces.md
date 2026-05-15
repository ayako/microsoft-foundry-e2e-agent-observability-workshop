# Lab 01: 開発環境をセットアップする

## 1. GitHub Codespaces を起動

1. サンドボックスとして使うため、リポジトリを自分のプロフィールに [Fork](https://github.com/beachside-project/microsoft-foundry-e2e-agent-observability-workshop/fork?branch=jp-contents) します。
1. Fork したリポジトリで GitHub Codespace を起動します。
    - （ブラウザーで）リポジトリの青い Code ボタンをクリック
    - Codespaces タブを選択
    - Create Codespace をクリック
1. VS Code 環境を含む新しいブラウザータブが開きます。
    - IDE が完全に読み込まれるまで待ちます。
    - ターミナルがアクティブになることを確認します。
    - 完了まで数分かかる場合があります。
1. これで開発環境の準備は完了です。

## 2. Setup-Env スクリプトを実行

_マルチテナント環境の場合は、先に以下を実行してください。_

```bash
# 既定テナントを設定（ログインで使用）
az login --tenant <TENANT_ID>

# 既定サブスクリプションを設定
az account set --subscription <SUBSCRIPTION_NAME_OR_ID>

# 次で確認
az account show
```

_あわせて、VS Code の AI Toolkit Extention と Azure Extention が正しいテナントを使っていることも確認してください。_

1. Azure アイコンをクリックし、Accounts & Tenants タブでチェックが 1 つだけになっていることを確認します。
1. AITK アイコンをクリックし、My Resources で既定の Foundry プロジェクトが設定されていることを確認します。


1. VS Code のターミナルで次のコマンドを実行します。

    ```bash
    ./labs/notebooks/setup-env.sh
    ```
1. 画面のように Azure へのログインを求められます。ログインを完了し、スクリプトが終了するまで実行させます。
    ![Run Env Script](assets/26-run-env-script.png)

1. 成功メッセージが表示され、正しい変数が入った `.env` ファイルが `labs/notebooks` フォルダーに作成されているはずです。
    ![Dev Env Ready](assets/27-dev-env-ready.png)
1. これでローカル環境変数の設定は完了です。

## 3. 進め方を選ぶ

| オプション | 説明 |
|:---|:---|
| [README.sdk.md](./../1-prompt-agents/README.sdk.md) | Microsoft Foundry SDK を使う、従来のコードファースト手順。コードをステップごとに進めます。 |
| [README.skills.md](./../1-prompt-agents/README.skills.md)| "observe" Foundry Skills を使って _observe-optimize_ ループを回す、コーディングエージェント中心の早期プレビュールート。 |

どちらか一方を完了したら、このステップに戻ってもう一方も試してみてください。今後の開発ワークフローをコーディングエージェントとスキルがどう加速するかを早めに体感するため、まずは Foundry Skills のルートから始めることをおすすめします。