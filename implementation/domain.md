# Domain層の実装方法

Utilitiesディレクトリに、EntityやValueObjectの基底クラスが入っています。  
EntityやValueObjectはこれらを継承して作成します。
```
- app
    - Domain
        - Utilities <- ここ 
```

## Entityの実装

Entityを作成する場合は、AbstractEntityを継承してください。

###protected $identifierKeys
Entityの識別子となる属性の配列
```php
protected $identifierKeys = ['studentCode',];
```

###protected $attributes  
Entityに含まれる属性名の配列
```php
protected $attributes = ['studentCode', 'name'];
```

###protected $fillable
コンストラクタで同時代入可能な属性の配列
```php
protected $fillable = ['studentCode'];
```
###protected $repositories
依存注入するリポジトリを指定するための配列  
リポジトリのパスを文字列で指定します。
```php
protected $repositories = [StudentRepository::class];
```

### public function getIdentifier(): StudentIdentifier
識別子を取得するためのメソッド ※実装必須  
各Entityの識別子クラスを作成し、返却します。
```php
public function getIdentifier(): StudentIdentifier
{
    $data = $this->getIdentifierData(); //$identifierKeysで指定した属性を配列で取ってくるメソッド
    return new StudentIdentifier($data);
}
```
###public function equal(StudentIdentifier $id): bool
Entityを比較するメソッド、引数にはEntityの識別子クラスを指定します。
```
public function equal(StudentIdentifier $id): bool
{
    return parent::_equal($id); //それぞれの属性が同一か判定
}
```


## ValueObjectの実装