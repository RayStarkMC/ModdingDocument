# final class ItemStack
ゲーム内におけるアイテムやブロックの塊を表すクラス。  
保持している[Item]、ダメージ値、NBTタグの3つのを中心としたデータを持ち、それらの振る舞いやユーティリティメソッドを提供する。プレイヤーやTilerEntityのインベントリ、レシピ実効時の見本、エンティティ等、様々な場面で利用される。ダメージ値やスタック数を負数に設定すると0となる。スタック数が0以下になった場合破棄されるが、こちらはItemStackを直接扱うメソッド側によってなされる。  
ItemStackのメソッドの多くの動作は保持している[Item]クラスのメソッドの実装よって決定される。ItemStackがBlockの塊を表現する場合は[Item]クラスとしてItemBlockを継承したクラスを保持し、そのメソッドの動作の多くはBlockクラスのメソッドにより決定される。

## フィールド
### int stackSize
アイテムスタックに含まれるアイテムの個数。

### NBTTagCompound stackTagCompound
アイテムスタックの保持するNBT。  
getTagCompound()で取得可能。

## コンストラクタ
### ItemStack(Item item, int stackSize, int damage)
指定したアイテム、スタックサイズ、ダメージ値でアイテムスタックを生成する。

### ItemStack(Block block, int stackSize, int metadata)
指定したブロック、スタックサイズ、ダメージ値でアイテムスタックを生成する。

## メソッド
### ItemStack splitStack(int stackSize)
自身のスタックから、引数で指定した個数を分離して新たなスタックを生成する。  
生成されたスタックは自身と同じアイテム、NBT、メタデータを保持する。生成元のスタックはstackSizeだけ個数が減る。

### Item getItem()
スタックが保持するアイテムクラスを返す。

### IIcon getIconIndex()
スタックのアイコンインデックスを返す。

### boolean tryPlaceItemIntoWorld(EntityPlayer player, World world, int x, int y, int z, int side, float hitX, float hitY, float hitZ)
スタックの使用を試みる。  
getItem().onItemUse()を呼び出す。  
何か行った場合はtrueを返す。

### ItemStack useItemRightClick(World world, EntityPlayer entityPlayer)
このスタックが右クリックされたときに呼ばれる。  
[Item].onItemUseFirst()や[Item].onItemUse()で何も行われなかった場合に実行される。アイテムがブロックに対して何らかの動作を実行する場合、空中右クリックした場合のみ呼ばれる。  
使用後のアイテムスタックを返す。

### ItemStack onFoodEaten(World world, EntityPlayer entityPlayer)
このスタックが食べられるときに呼ばれる。     
アイテムクラスのonEaten()を呼び出す。  
使用後のアイテムスタックを返す。

### int getMaxStackSize()
自身のスタックの最大スタック数を返す。

### boolean isStackable()
自身のスタックがスタック可能であればtrue。

### boolean isItemStackDamageable()
スタックが耐久値を持つ場合true

### boolean getHasSubtypes()
1つのアイテムクラスで複数のアイテムを表現している場合true。  
ex. ItemDye

### boolean isItemDamaged()
耐久値を持つスタックがダメージを受けている場合true。

### int getItemDamage()
スタックのダメージ値を返す。

### void setItemDamage(int damage)
スタックのダメージ値を指定した値に設定する。

### int getMaxDamage()
スタックの最大耐久値を返す。

### boolean attemptDamageItem(int damage, Random random)
スタックに指定したダメージを試みる。  
このダメージはrandomと耐久エンチャントにより軽減される。  
このメソッドはdamageItem()によって呼ばれる。  
return: スタックのダメージ値が最大耐久度を超えた場合true

### void damageItem(int damage, EntityLivingBase entityLiving)
引数のエンティティによりこのスタックにダメージを与える。

### void hitEntity(EntityLivingBase target, EntityPlayer entityPlayer)
targetに対してentityPlayerにより、このスタックを使って攻撃する際に呼ばれる。  
実際に行っているのは耐久値の消費と統計データの収集のみ。

### void func_150999_a(World world, Block targetBlock, int x, int y, int z, EntityPlayer entityPlayer)
targetBlockをこのスタックにより破壊する際に呼ばれる。
getItem().onBlockDestroyed()を呼び出す。

### boolean interactWithEntity(EntityPlayer entityPlayer, EntityLivingBase targetEntity)
このスタックにより対象のエンティティに干渉する。  
このメソッドはgetItem().interactWithEntity()を呼ぶ。

### ItemStack copy()
このスタックを複製する。  
複製されたスタックは同じアイテム、ダメージ値、NBTを持つ。

### static boolean areItemStackTagsEqual(ItemStack one, ItemStack theOther)
2つのスタックのNBTタグが等しいか調べる。

### static boolean areItemStacksEqual(ItemStack one, ItemStack theOther)
2つのスタックが完全に等しいか調べる。

### boolean isItemEqual(ItemStack other)
対象のスタックと同じアイテムを保持しているか調べる。

### String getUnlocalizedName()
アイテムのunlocalizedNameを取得する。

### static ItemStack copyItemStack(ItemStack targetStack)
対象のスタックを複製する。

### String toString()
このスタックの文字列表現を返す。

### void updateAnimation(World world, Entity entityPlayer, int slot, boolean isHeld)
スタックがプレイヤーインベントリに入っている間1tickに1度呼ばれる。

### void onCrafting(World world, EntityPlayer entityPlayer, int size)
アイテムがクラフトされた際に呼ばれる。  
統計データを加算し、getItem().onCreated()を呼ぶ。

### int getMaxItemUseDuration()
このスタックを使用するのにかかる時間を返す。

### EnumAction getItemUseAction()
アイテムを使用したときの動作を返す。

### void onPlayerStoppedUsing(World world, EntityPlayer entityPlayer, int itemInUseCount)
アイテムの使用を中止した際に呼ばれる。

### boolean hasTagCompound()
スタックがNBTタグを持っている場合true。

### NBTTagCompound getTagCompound()
スタックのNBTタグを取得する。

### NBTTagList getEnchantmentTagList()
スタックのエンチャントのタグリストを返す。

### void setTagCompound(NBTTagCompound tagCompound)
このスタックにタグをセットする。

### String getDisplayName()
このスタックの表示名を取得する。  
このスタックが表示名が金床等によって変えられている場合、そちらの名前を返す。そうでない場合、[Item]の名前を返す。このメソッドはlangファイルにItem名に対応する翻訳が記述されている場合、その名前を返す。

### ItemStack setStackDisplayName(String displayName)
このスタックの表示名を変更する。

### void func_135074_t()
このスタックの表示名が変更されている場合、元に戻す。

### boolean hasDisplayName()
このスタックが表示名を変更されている場合、true。

###  @SideOnly(Side.CLIENT) List getTooltip(EntityPlayer player, boolean isDebugMode)
ツールチップに表示する文字列が格納されたリストを返す。  
このメソッドでgetItem().addInformation()を呼び出す。

### @SideOnly(Side.CLIENT) boolean hasEffect(int pass)
描画時に呼ばれる。  
このアイテムがエンチャントを持っている場合true。

### EnumRarity getRarity()
このスタックのレアリティを返す。  
レアリティはツールチップの表示名等に利用される。

### boolean isItemEnchantable()
このスタックがエンチャント可能であればtrueを返す。

### void addEnchantment(Enchantment enchantment, int level)
このスタックに指定したレベルのエンチャントを付与する。

### boolean isItemEnchanted()
このスタックがエンチャントされている場合true。

### void setTagInfo(String key, NBTBase tag)
このスタックに指定したタグを付与する。

### boolean canEditBlocks()
このスタックによりブロックを編集できるならtrue。

### boolean isOnItemFrame()
このスタックがフレームに飾られている場合true。

### void setItemFrame(EntityItemFrame entityFrame)
このスタックを指定したフレームに飾る。  
entityFrameがnullの場合はフレームに飾られている状態を解除する。

### EntityItemFrame getItemFrame()
このスタックが飾られているフレームを返す。

### int getRepairCost()
このスタックの修繕コストを返す。

### void setRepairCost(int cost)
このスタックの修繕コストを設定する。

### Multimap getAttributeModifiers()
このスタックのAttributeModifierを取得する。

### IChatComponent func_151000_E()
このアイテムを表示するチャットコンポーネントを取得する。  
ホバーイベントがSHOW_ITEMに設定されており、マウスホバーでアイテムのツールチップが表示される

[Item]:/ForgeBin/net/minecraft/item/Item.md
