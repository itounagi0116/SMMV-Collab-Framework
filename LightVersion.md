# SMMV-Collabフレームワーク ライト版

## 概要
人間と生成AIの効率的な協働を実現する軽量設計フレームワーク。
エンタープライズ開発のエッセンスを残しつつ、小〜中規模プロジェクトに適した簡素化されたアプローチを提供。

## 1. 簡略化コア原則

### 1.1 基本設計原則
- **単一責任**: 各クラスは明確に定義された単一の役割を持つ
- **拡張と保守**: 既存コード修正なしで機能追加できる設計
- **インターフェース**: 小さく焦点を絞ったインターフェース設計
- **依存関係**: 抽象に依存し、具体実装への直接依存を避ける

### 1.2 簡略化アーキテクチャ
- 3層アーキテクチャ（UI、ビジネスロジック、データ）
- 各層の責任範囲を明確に区分

## 2. AI協働最適化

- わかりやすい構造と命名規約
- AIプロンプトテンプレート
- レイヤー別コード生成ガイド

## 3. 軽量ディレクトリ構成

```
src/
├── ui/                 # UI層
│   ├── views/          # 画面・コンポーネント
│   └── controllers/    # コントローラー
│
├── core/               # ビジネスロジック層
│   ├── models/         # ドメインモデル
│   ├── services/       # サービス
│   └── interfaces/     # 抽象インターフェース
│
├── data/               # データ層
│   ├── repositories/   # データアクセス実装
│   └── external/       # 外部サービス連携
│
└── utils/              # 共通ユーティリティ
```

## 4. AI活用ガイド

### プロンプト例
```
「[core/services]に新しい[ServiceName]を作成し、以下の機能を実装してください:
- 目的: [サービスの目的]
- 依存: [依存するインターフェース]
- 処理内容: [主要機能]
- エラー処理: [考慮すべき例外]」
```

## 5. 簡略実装例

```python
# core/interfaces/user_repository.py
class UserRepository:
    def find_by_id(self, user_id):
        pass
    
    def save(self, user):
        pass

# core/models/user.py
class User:
    def __init__(self, user_id, name, email):
        self.id = user_id
        self.name = name
        self.email = email
        self.validate()
    
    def validate(self):
        # 基本検証ロジック

# core/services/user_service.py
class UserService:
    def __init__(self, user_repository):
        self.user_repository = user_repository
    
    def register_user(self, name, email):
        user = User(None, name, email)
        return self.user_repository.save(user)
```

## 6. 開発フロー

1. モデルとインターフェースの設計
2. サービス実装（AIプロンプト活用）
3. データ層でインターフェース実装
4. UI層での表示・操作実装
5. テストと改善

## 7. ベストプラクティス

- 一貫した命名規則の使用
- 明示的な依存関係の宣言
- 適切なエラー処理とログ記録
- テスト容易性を考慮した設計

このライト版は、フルフレームワークの思想を維持しながら、
より小規模なプロジェクトや迅速な開発に適した簡略化を施しています。
