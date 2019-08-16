# public abstract class CreativeTabs
クリエイティブタブを表す抽象クラス。  
継承したクラスを宣言する事で新たなクリエイティブタブを追加する。

## コンストラクタ
### public CreativeTabs(String label)
クリエイティブタブのインスタンスを生成すると共に参照を保持する。  
labelで指定した文字列がタブの名前になる。  

## インスタンスメソッド
### @SideOnly(Side.Client) public abstract Item getTabIconItem()
タブアイコンに用いるアイテムを返す。  
表示したいアイテムを返すようにOverrideする。

###
