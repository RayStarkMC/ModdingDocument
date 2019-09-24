# @SideOnly(Side.CLIENT) public interface IIconRegister
[Item]クラスでアイコンを登録する際に利用されるインターフェース。


## メソッド

### IIcon registerIcon(String iconString)
iconStringに対応する[IIcon]を構築する。  
iconStringの形式は<ドメイン名>:<テクスチャ名(小文字)>。テクスチャはresources/assets/<ドメイン名>/textures/(items|blocks)/<テクスチャ名>.pngとなるように配置する。ドメイン名はユニークであれば任意の文字列が使える。他のModとの競合を考慮し、modidを指定しておくと無難。

[Item]:/ForgeBin/net/minecraft/item/Item.md
[IIcon]:/ForgeBin/net/minecraft/util/IIcon.md
