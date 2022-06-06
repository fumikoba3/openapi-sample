# swaggerのAPIドキュメントメンテナンス方法

## APIの追加手順

- 1. スキーマファイルを追加する
  - リクエストパラメータやレスポンスの形式を定義するスキーマファイルをschemasディレクトリ内に新規作成します
- 2. pathsにAPI仕様を記載するyamlファイルを作成します
  - リクエストパラメタやレスポンスのschemasの定義に$refを使って1で作ったスキーマファイルに紐付けます
- 3. openapi.yamlのpathsに2で追加したyamlファイルを追加します
- 4. 統合するコマンド `swagger-cli bundle -o ./openapi/build/openapi.yaml -t yaml ./openapi/openapi.yaml` (npm run api-buildで実行可) を実行してbuild/openapi.yamlを更新

## prismで確認

- 上記で作ったbuild/openapi.yamlはvscodeなどのswagger viwerなどでも見れますが、dockerのprismでもHTMLとして参照できます。
- またmockとしても立ち上げているのでopenapi.yamlにexampleなど記載するとrepsonseの内容を変えてmockのレスポンスを変更することができます
