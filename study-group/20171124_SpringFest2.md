# Srping Security 5
- 本日はRC1

- WEbFllux対応
- OAuth2.0対応

## WebFlux対応
- リアクティブプログラミングをサポートする仕組み
- non-blockingに対応
- Servlet APIに依存しない
- Reactive Typeがある

- 前はServlet Filterに依存
  - Http Sessionとかが使えないよ
- AuthenticationWebFilter
  - Spring5が提供するインターフェース
  - reactiveのためのもの
  - AuthenticationProvidorが省略されている
- アーキテクチャは大きく変わっていない
 - クラスの役割が変わっている
- 従来のServlet対応版がなくなったわけではない。Spring MVCと連携は可能

### Configuration
- @EnableWEbFluxSecurity
- WebTestClient(5から)
- WebFluxのエンドポイントをテストできる
- MovkMvc(ローカルテスト用)
- @WithMockUserが使えるようになった
  - @WithMockUser(role="USER")でUSER
- csrf対策をサポートしている

### Reactive Method Security
- @EnableReactiveMethodSecurity
- @PreAuthrize("hasRole("")")

### そのた
- Loginページがリッチになった

## OAuth2.0

###
- OAuth2.0が散らばってたので新しいプロジェクトになった

### 提供されたもの
- Clientが導入された
- OpenID Connect
  - OpenID Providerが認証する
  - AccessTokenを返す
- 一般的にOAuth2.0 認証でなく認可なので認証の場合、影響が出る場合がある

### カスタマイズポイント
- ログインページ
  - oauth2login().loginPage("/login") <- ログイン用のリクエストパスを設定することで置き換えができる
- ImMemoryの実装となっている。
  - ClientRegistrationRepository
    - Client情報がこていならInMemory実装になっている

   - OAuth2AuthorizedClientService

### その他の改善
- PasswordEncoderの削除
  - CryptoのPasswordEncoderを使えばいい
- DelegatingPasswordEncoder
  - パスワードのハッシュ化のアルゴリズムごとに適切なPasswordEncoderに処理を移譲する