# OIC-STATUS クラス図

```uml
@startuml{plantuml_class_sample.png}

class コース {
}

class 学生 {
    学籍番号
    自身のスキルLvを算出()
}
学生 "*" -- "1" コース: 所属

class スキル {
    スキル名
    スキルLv
    スキル経験値
}
学生 o-- スキル

class 役割 {
    役割名
}
学生 o-- 役割

class 役割をこなす条件 {
    スキル名
    必要なスキルLv
}
役割 o-- 役割をこなす条件

package 授業評価 <<Frame>> {
    class 受講科目 {
        科目名
    }
    受講科目 o-- 身につくスキル
    受講科目 -le- 授業
    受講科目 -o 学生

    class 授業 {

    }
    授業 "1" -- "1" 受講学生名簿
    授業 -- 担当教員


    class 身につくスキル {
        スキル名
    }

    class 受講学生名簿 {
    }
    受講学生名簿 o-- 受講学生名簿列

    class 受講学生 {
        学籍番号
    }
    授業 "1" o-- "*" 受講学生
    担当教員 --> 受講学生名簿列: 記述(授業評価)

    class 受講学生名簿列 {
        授業日時
        平均評価点()
    }

    受講学生名簿列 o-- 授業評価

    class 授業評価 {
        受講学生の学籍番号
        授業日時
        評価点
    }
}
@enduml
```

## 授業評価入力

```uml
@startuml{plantuml_class_sample.png}

object 教師 {
}

教師 --> 名簿列ファクトリ: 1. 授業, 日時
教師 -> 名簿列: 3. 評価入力

object  名簿列ファクトリ {
}
名簿列ファクトリ -up-> 名簿列: 2. 生成

class 名簿列 << ValueObject >> {
    評価: <学籍番号, 評価点>
    評価入力(学籍番号, 評価点)
    評価平均算出()
}
note top of 名簿列: 永続化はされていない

class 名簿 << Entity >> {
    名簿列登録(名簿列)
}
名簿 <-ri- 名簿列: 名簿列登録
note top of 名簿: 名簿列の永続化&全生徒の評価が入力されているか確認

class 評価漏れポリシー {
    評価漏れチェック(名簿列)
}
名簿 --> 評価漏れポリシー: 評価漏れチェック

class 名簿リポジトリ {
    名簿列追加(名簿列)
}
評価漏れポリシー -> 名簿リポジトリ: 名簿列追加
@enduml
```

## 職業習得

```uml
@startuml{plantuml_class_sample.png}

object クライアント {
}
クライアント --> ダーマ神殿サービス: 1. 習得できるか(学生, 職業)
object 学生 {
    職業を追加する(職業)
}

object ダーマ神殿サービス {
    習得できるか(学生, 職業): bool
    職業を習得する(学生, 職業)
}
ダーマ神殿サービス --> 学生: 2. 職業を追加する(職業)

@enduml
```