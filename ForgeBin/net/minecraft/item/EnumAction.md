# public enum EnumAction
アイテムを手に持って右クリック時の[EntityPlayer]の動作を表す列挙。  
主に[EntityPlayer]によって利用され、右クリック時の処理(サウンド再生、モーション等)を決める。5種類の動作が定義されており、[Item].[getItemUseAction(ItemStack heldStack)]で取得する。アイテムの右クリック時の動作を変更したいときは同メソッドをOverrideして返す列挙子を変更する。  


## 列挙子

### none
動作しない事を表す列挙子。

### eat
食事動作を表す列挙子。

### drink
飲料動作を表す列挙子。

### block
防御動作を表す列挙子。

### bow
弓を引く動作を表す列挙子。


[entityPlayer]:/ForgeBin/net/minecraft/entity/player/EntityPlayer.md

[item]:/ForgeBin/net/minecraft/item/Item.md

[getItemUseAction(ItemStack heldStack)]:[Item]#public-enumaction-getitemuseactionitemstack-helditem
