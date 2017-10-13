
```uml
@startuml

object ギルドメンバー
object アイデア主
object 募集主
object アイデア
object パーティー
object 参加申請
object 募集役割
object 招待
object スキル
object ジョブ
object チャット
object 参加希望者
object リアクション
object ステータス
object 功績
object パーティー詳細
object パーティーメンバー
object 募集内容 {
    募集期間
}
object スキル経験値
object スキルレベル


アイデア -le-> アイデア主
アイデア o-> リアクション
パーティー詳細 -up-> アイデア
パーティー o-> 招待
パーティー o-do-> 参加申請
パーティー -up-> チャット
パーティー -up-> 募集主
募集内容 o-le-> 募集役割
パーティー詳細 -> 募集内容
パーティー --> パーティー詳細
パーティー o--> パーティーメンバー
チャット o-> ギルドメンバー
アイデア -up-> チャット
リアクション -> ギルドメンバー
参加申請  --> 参加希望者
招待 -> ギルドメンバー
ギルドメンバー -> ステータス
ステータス o--> スキル
ステータス o--> ジョブ
ステータス o--> 功績




@enduml
```


```uml
@startuml

object ギルドメンバー
object アイデア主
object 募集主
object アイデア {
    Entity
    テーマ
    内容
}
object パーティー {
    Entity
    募集主の参照
}
object 参加申請 {
    Entity
    from(ギルドメンバーの参照)
    to(パーティーの参照)
    募集役割の参照
}
object 募集役割
object パーティーへの招待 {
    from(パーティーの参照)
    to(ギルドメンバーの参照)
    募集役割の参照
}
object スキル
object ジョブ
object チャット
object 参加希望者
object リアクション
object ステータス
object 功績
object パーティー情報
object パーティーメンバー
object パーティーメンバー情報
object 募集内容 {
    制作期間
}



パーティー情報 -do-> アイデア

パーティー -do- 参加申請
パーティー -up-> チャット
募集主 -- パーティー
募集内容 o-le募集役割
パーティー情報 -do-> 募集内容
パーティー情報 o-do-> パーティーメンバー情報
パーティー情報 -do-> 募集主情報
パーティー --> パーティー情報
パーティー o--> パーティーメンバー
ギルドメンバー o-> パーティーへの招待





@enduml
```
参加希望者 --|> ギルドメンバー

