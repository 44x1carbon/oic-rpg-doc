# 概要図

## OIC-GUILD

```uml
@startuml
scale 1.5

object 募集内容 {
    企画
    目標
    政策期間
    募集主の情報
}
object 募集役割 {
    役割名
    ジョブ
    スキル
    募集人数
}
package パーティーメンバー {
    object 参加希望者
    object 募集主
}
object パーティー {
    募集状態
}

参加希望者 -do-> 募集内容: 見る
参加希望者 --> パーティー: 参加
募集主 --> パーティー: パーティーメンバーの募集開始
パーティー --> 募集内容: 詳細
募集内容 -> 募集役割

@enduml
```

## OIC-STATUS

```uml
@startuml
scale 2

object ギルドメンバー {
}
object スキル {
    スキルLv
    スキル経験値
}
object ジョブ {
    習得条件
}

ギルドメンバー --> スキル: 所有
ギルドメンバー --> ジョブ: 取得

@enduml
```