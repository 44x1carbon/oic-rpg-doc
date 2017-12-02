# ユースケース

```uml
@startuml
left to right direction

:OICの学生: as Student
:ギルドメンバー: as GuildMember
:パーティー管理者: as PartyManager
:評価システム: as RatingSystem

GuildMember -|> Student
PartyManager -|> GuildMember

rectangle OIC-RPG {
  (ギルドメンバー登録) as RegisterGuild
  (プロフィールを編集する) as EditProfile

  package パーティー管理 {
    (募集役割を追加する) as AddWantedRole
    (募集役割の枠を追加する) as AddWantedRoleFrame
    (参加申請を許可する) as AcceptRequest
    (参加申請を却下する) as RejectRequest
    (制作アイデアを編集する) as EditProductIdea
    (パーティーを作成する) as RegisterParty
  }

  (パーティーに参加申請をする) as SendJoinRequest
  (パーティーを検索する) as SearchParty
  (パーティーの詳細を確認する) as BrowsePartyDetail
  (ギルドメンバーを検索する) as SearchGuildMember
  package ステータス管理 {
    (ジョブを取得する) as GetJob
    (ギルドメンバーに経験値を付与する) as GiveExpToGuildMember
  }
}

Student --> RegisterGuild
GuildMember --> EditProfile
GuildMember --> RegisterParty
GuildMember --> GetJob
GuildMember --> BrowsePartyDetail
GuildMember --> SearchGuildMember
GuildMember --> SearchParty
GuildMember --> SendJoinRequest
PartyManager --> AddWantedRole
PartyManager --> AddWantedRoleFrame
PartyManager --> EditProductIdea
PartyManager --> SearchGuildMember
PartyManager --> AcceptRequest
PartyManager --> RejectRequest
RatingSystem -up-> GiveExpToGuildMember

@enduml
```
