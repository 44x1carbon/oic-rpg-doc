# ディレクトリ構造

```
- app
    - Domain //ドメイン層のファイル
        - Common        //全ドメインで共有のドメインモデルなど
        - Dungeon       //Dungeonで利用するドメインモデルなど
        - Guild         //Guildで利用するドメインモデルなど
        - RaidBattle    //RaidBattleで利用するドメインモデルなど
        - Status        //Statusで利用するドメインモデルなど     
        - Utilities     //EntityやVOの基底クラス、その他Utilityなど
```

## Domain
このディレクトリは、ドメインモデルに関するファイルのディレクトリです。  
各子ディレクトリ(Utilitiesを除く)中には、それぞれのユビキタス言語のディレクトリが生成されます。  
このディレクトリの中には、EntityやValueObject,Factory,Repositoryのファイルを生成します。  
<small>※詳しくは[ドメインについて]()を参照してください。</small>

```
例）
- Domain
    - Common
        - Student //Student(学生)に関するドメインモデルを格納するディレクトリ
```