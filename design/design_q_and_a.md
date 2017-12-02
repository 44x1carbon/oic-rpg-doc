# Q & A

- [集約について](#集約について)

# 集約について
<hr>

## Q.集約の内部に別の集約の参照をどうやって持つのか?
A.直接参照を持つのではなく、GuildMemberIdのような間接的な参照をもたせます。
 
```
/* NG */
class RootEntity
{
  protected $otherRoot;
  
  public function __constractor(OtherRoot $otherRoot)
  {
    $this->otherRoot = $otherRoot;
  }
}
```

```
/* OK */
class RootEntity
{
  protected $otherRootId;
  
  public function __constractor(OtherRootId $otherRootId)
  {
    $this->otherRootId = $otherRootId;
  }
}
```

## Q.別の集約(ルートエンティティ)はどうやって取得するのか?
A.集約の中に対象エンティティのリポジトリを保持し、IDなどから取得します。

```
class RootEntity
{
  protected $otherRootId;
  protected $otherRootRepo;
  
  public function __constractor(OtherRootId $otherRootId)
  {
    $this->otherRootId = $otherRootId;
    $this->otherRootRepo = app(OtherRootRepositoryInterface::class);
  }
  
  public function toOtherRoot(): OtherRoot
  {
    return $this->otherRootRepo->findById($this->otherRootId);
  }
}
```