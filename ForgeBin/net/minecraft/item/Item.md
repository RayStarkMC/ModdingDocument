# pulic class Item
ゲーム内における[ItemStack]の振る舞いを表現するクラス。  
[ItemStack]が生成されるときに必ずItemクラスが参照され、[ItemStack]の各振る舞いはItemクラスのメソッドを参照する。Blockクラスに対してはこのクラスを継承したItemBlockクラスが対応している。


## フィールド
### public static final RegistryNamespaced itemRegistry
Minecraft本体のアイテムレジストリ。  
基本的にForgeのGameRegistryを利用するため使用しない。

### protected static Random itemRand
Itemクラスに紐づけされたRondomインスタンス。  
アイテムに関係した乱数を生成するときに利用されている。

### protected int maxStackSize
このアイテムの最大スタック数。  
初期値は64。

### protected boolean bFull3D
trueの場合、このアイテムを3Dで描画する(?)。詳細不明。  
ItemTool等ではtrueになっている。初期値false。

### protected boolean hasSubtypes
trueの場合、このアイテムクラスが複数のアイテムを表す。  
1つのアイテムクラスで複数のアイテムを表す場合、trueとしなければならない。  
ex. ItemDye

### @SideOnly(Side.CLIENT) protected IIcon itemIcon
アイテムのテクスチャ。  
ゲーム開始時にregisterIcon()によって初期化される。このアイテムのアイコンが1つの場合はこの変数が利用されるが、複数のアイコンを使う場合は独自にIIconを保持しなければならない。　　
ex. ItemDye

### protected String iconString
アイコンのリソース置き場を表す文字列を表す。  
iconStringは全て小文字で<domain>:<テクスチャ名>とする。<domain>はMod毎にユニークな名前にする必要があるが、慣例としてModIDを指定する場合が多い。テクスチャはassets/<domain>/textures/items/下に配置し、ファイル名を<テクスチャ名>.pngとする。
ex. iconString: "ateliermod:bandage"の時, assets/ateliermod/texture/items/bandage.png

### public final RegistryDelegate<Item> delegate
このアイテムへの参照を保持する。


## メソッド
### public static int getIdFromItem(Item item)
引数のアイテムのIDを返す。

### public static Item getItemById(int id)
引数のIDで登録されているアイテムを返す。

### public static Item getItemFromBlock(Block block)
引数のブロックに対応するアイテムを返す。

### public static void registerItems()
バニラアイテムをレジストリへ登録する。  
Minecraft、及びMinecraftServer起動時に呼び出される。呼び出し不要。

### public Item setMaxStackSize(int maxStackSize)
このアイテムの最大スタック数を設定する。

### @SideOnly(Side.CLIENT) public int getSpriteNumber()
非推奨。オーバーライド不要。

### @SideOnly(Side.CLIENT) public IIcon getIconFromDamage(int damage)
非推奨。代わりにpublic IIcon getIconIndex(ItemStack itemStack)を利用する。
ダメージ値に応じたアイコンを返す。

### @SideOnly(Side.CLIENT) public IIcon getIconIndex(ItemStack itemStack)
このスタックのアイコンを返す。  
このメソッドはrequiresMultipleRenderPasses()がfalseを返すときに呼ばれる。
この実装ではgetIconFromDamage()を呼び出すが、オーバーライドすることでNBTに応じたIIconを返すことが出来る。

### public boolean onItemUse(ItemStack itemStack, EntityPlayer entityPlayer, World world, int x, int y, int z, int side, float hitX, float hitY, float hitZ)
アイテムをブロックに対して右クリックした場合に呼ばれる。  
何かを行った場合trueを返すことで、その後の処理を行わない。

### public float func_150893_a(ItemStack currentStack, Block block)
利用されない。代わりにgetDigSpeed()を使う。
引数のブロックに対する採掘速度を返す。

### public ItemStack onItemRightClick(ItemStack currentStack, World world, EntityPlayer entityPlayer)
アイテムが右クリックされた場合に呼ばれる。  
onItemUseFirst()やonItemUse()で何らかの処理が行われている場合は呼び出されない。  
使用後のアイテムスタックを返す。

### public ItemStack onEaten(ItemStack currentStack, World world, EntityPlayer entityPlayer)
このアイテムが食べられるときに呼ばれる。  
引数のプレイヤーがこのアイテムを食べたときの処理を行う。  
ex. ItemFood
return: 使用後のアイテムスタック

### @Deprecated public int getItemStackLimit()
非推奨。代わりにgetItemStackLimit(ItemStack itemStack)を利用する。  
このアイテムのスタック上限を返す。

### public int getMetadata(int metadata)
引数のメタデータのアイテムスタックによりブロックが設置される際、そのブロックのメタデータを返す。

### public boolean getHasSubtypes()
このアイテムが複数種のアイテムを表すならtrue。

### public Item setHasSubtypes(boolean hasSubtypes)
このアイテムが複数種のアイテムを表すか設定する。　　
このアイテム自身を返す。

### public int getMaxDamage()
非推奨。代わりにgetMaxDamage(ItemStack itemStack)を使う。  
このアイテムの最大ダメージ値を返す。

### public Item setMaxDamage(int maxDamage)
非推奨。代わりにgetMaxDamage(ItemStack itemStack)をオーバーライドして最大ダメージ値を設定する。  
このアイテムの最大ダメージ値を設定する。  
このアイテム自身を返す。

### public boolean isDamageable()
このアイテムが耐久値を持つならtrue。  
初期の実装ではsetMaxDamageで設定された値を参照するため、バニラの耐久設定を利用しないのであればgetMaxDamage(ItemStack itemStack)の実装に合わせてオーバーライドする。

### public boolean hitEntity(ItemStack itemStack, EntityLivingBase target, EntityLivingBase player)
targetに対して攻撃したときに呼び出される。  
このアイテムでtargetに攻撃した際の処理を行う。  
return: このアイテムでtargetに対し攻撃した場合に耐久値が減るならtrue。

### public boolean func_150897_b(Block block)
このアイテムが引数のブロックの適正ツールか調べる。  
特定のブロックに対して適正ツールを設定したいときに使う。ForgeのToolClassAPIのsetHarvestLevel()により適正ツール属性を付与することもできる。  
return: このアイテムが引数のブロックの適正ツールならtrue

### public boolean itemInteractionForEntity(ItemStack itemStack, EntityPlayer entityPlayer, EntityLivingBase target)
このアイテムを持ってtargetを右クリックした際に呼ばれる。  
targetに対して何らかの干渉をする処理を行う。  
ex. ItemDye, ItemShares
return: 何らかの動作を行った場合true

### public Item setFull3D()
bFull3Dをtrueに設定する。　　
return: このアイテム

### @SideOnly(Side.CLIENT) public boolean isFull3D()
このアイテムが手に持たれている時に3D描画するならtrue。

### @SideOnly(Side.CLIENT) public boolean shouldRotateAroundWhenRendering()
このアイテムを180°反転して描画するならtrue。

### public Item setUnlocalizedName(String unlocalizedName)
このアイテムの未翻訳名を設定する。  
return: このアイテム

### public String getUnlocalizedNameInefficiently(ItemStack itemStack)
item.unlocalizedNameの翻訳を返す。  
通常アイテムの翻訳はitem.unlocalizedName.nameに対して設定するため、このメソッドはunlocalizedNameを返す。

### public String getUnlocalizedName()
非推奨。代わりにpublic String getUnlocalizedName(ItemStack itemStack)を利用する。  
return: このアイテムの未翻訳名  

### public String getUnlocalizedName(ItemStack itemStack)
このアイテムの未翻訳名を返す。　　
メタデータやNBTの違いにより異なる未翻訳名を返すことが出来る。
return: このアイテムの未翻訳名

### public Item setContainerItem(Item containerItem)
非推奨。代わりにpublic ItemStack getContainerItem(ItemStack itemStack)をOverrideする。  
このアイテムの容器を設定する。  
ex. バケツ  
return: このアイテム

### public boolean doesContainerItemLeaveCraftingGrid(ItemStack itemStack)
trueの場合、このアイテムがクラフトで消費されたとき、容器がクラフトグリッドを離れる。

### public boolean getShareTag()
true、又はこのアイテムがダメージ値を持つ場合、NBT情報がクライアントとサーバーで同期される。  
このアイテムの[ItemStack]をPacketBufferに書き込み際に呼ばれ、trueならばNBTデータを書き込むようになる。

### public Item getContainerItem()
非推奨。代わりにpublic ItemStack getContainerItem(ItemStack itemStack)を利用する。  
return: このアイテムの容器

### public boolean hasContainerItem()
非推奨。代わりにpublic boolean hasContainerItem(ItemStack stack)を使う。
return: このアイテムが容器を持つならばtrue

### @SideOnly(Side.CLIENT) public int getColorFromItemStack(ItemStack stack, int renderPath)
このアイテムの指定されたrenderPathにおけるRGB値を返す。  
ex. 革防具各種
return: このアイテムのRGB値

### public void onUpdate(ItemStack itemStack, World world, Entity owner, int numSlot, boolean isHeld)
ownerのインベントリにこのアイテムがある場合、クライアント側でtick毎に呼ばれる。  
サーバーに影響を与える処理を行う場合は処理を行った後、その結果をサーバーと同期する必要がある。

### public void onCreated(ItemStack createdStack, World world, EntityPlayer creater)
このアイテムが作成されたときに呼ばれる。  
このメソッドはサーバー、クライアント両側で呼ばれる。

### public boolean isMap()
このアイテムがItemMapBaseのサブクラスであればtrueを返す。

### public EnumAction getItemUseAction(ItemStack heldStack)
このアイテムが使用されたときのアクションを返す。  
戻り値のアクションによって右クリック時の動作が変わる。

### public int getMaxItemUseDuration(ItemStack itemStack)
このアイテムを使用するのにかかるtick数を返す。

### public void onPlayerStoppedUsing(ItemStack itemStack, World world, EntityPlayer user, int itemInUseCount)
プレイヤーが右クリックによるアイテムの使用をやめたときに呼ばれる。

### public Item setPotionEffect(String potionEffect)
このアイテムがポーションの材料として利用されたときの効果を設定する。  
エフェクトはPotonHelperを使って設定する。  
return: このアイテム

### public String getPotionEffect(ItemStack itemStack)
このアイテムがのポーションの材料として利用されたときの効果を返す。

### public boolean isPotionIngredient(ItemStack itemStack)
このアイテムがポーションの材料であればtrueを返す。  
getPotionEffectがnullでなければtrueを返す。

### @SideOnly(Side.CLIENT) public void addInformation(ItemStack itemStack, EntityPlayer owner, List tooltipList, boolean isDebugMode)
ツールチップに表示する文字列を設定する。  
ownerがツールチップを表示する際に呼び出される。実装側ではtooltipListに1行ごとに表示する文字列を書き込む。

### public String getItemStackDisplayName(ItemStack itemStack)
このアイテムの表示名を返す。

### @SideOnly(Side.CLIENT) @Deprecated public boolean hasEffect(ItemStack itemStack)
非推奨。代わりにpublic boolean hasEffect(ItemStack itemStack, int pass)を使う。
このアイテムがポーションエフェクトを持っているならtrueを返す。

### public EnumRarity getRarity(ItemStack itemStack)
このアイテムのレアリティを返す。  
レアリティはアイテムを表示するときにのアイテム名の色等に利用される。

### public boolean isItemTool(ItemStack itemStack)
このアイテムがツールであればtrueを返す。  
このアイテムがエンチャントを施すことが出来る場合、trueを返す必要がある。  
デフォルトの実装ではスタックサイズが1かつ耐久値を持つ場合にtrueを返す。

### protected MovingObjectPosition getMovingObjectPositionFromPlayer(World world, EntityPlayer player, boolean includingStaticLiquid)
playerの視点上のブロック座標を保持した[MovingObjectPosition]を返すヘルパメソッド。  
この実装ではデフォルトのリーチである5m以内のブロックを捜査する。範囲内にブロックが存在しなかった場合、nullを返す。  
return: 視点のMovingObjectPosition、無ければnull

### public int getItemEnchantability()
非推奨。代わりにgetItemEnchantability(ItemStack stack)をOverrideする。  
このアイテムのエンチャント適正を返す。  
この数値が高いほど祭壇で良質なエンチャントが付与される。
0以下の値を返す場合、エンチャント不能になる。
return: エンチャント適正

### public boolean requiresMultipleRenderPasses()
アイテムを複数レイヤーに渡って描画を必要とする場合にtureを返す。  
このメソッドがfalseを返す場合、複数レイヤーによる描画関連のメソッドは無視される。  
return: IIconを複数レイヤーに渡って描画する場合true

### @SideOnly(Side.CLIENT) public IIcon getIconFromDamageForRenderPass(int damage, int pass)
ダメージ値とレンダーパスから対応するIIConを返す。  
デフォルトで[getIcon(ItemStack stack, int renderPass, EntityPlayer player, ItemStack usingItem, int useRemaining)]から呼ばれる。  
return: レイヤーpassでのIIcon

### @SideOnly(Side.CLIENT) public void getSubItems(Item itemStack, CreativeTabs tab, List subItemList)
このアイテムがクリエイティブタブに表示されるときに呼ばれる。  
Overrideし、subItemListに表示するアイテムを追加する。

### public Item setCreativeTab(CreativeTabs tabToDisplayOn)
このアイテムを表示するクリエイティブタブを指定する。  
同じアイテムを複数のクリエイティブタブに表示したい場合は[getCreativeTabs()]をOverrideする。  
return: このアイテム

### public IIcon getIcon(ItemStack stack, int renderPass, EntityPlayer player, ItemStack usingItem, int useRemaining)

### public CreativeTabs[] getCreativeTabs()

[ItemStack]:/ForgeBin/net/minecraft/item/ItemStack.md
[MovingObjectPosition]:/ForgeBin/net/minecraft/util/MovingObjectPosition.md


[getIcon(ItemStack stack, int renderPass, EntityPlayer player, ItemStack usingItem, int useRemaining)]:/ForgeBin/net/minecraft/item/Item.md#public-iicon-geticonitemstack-stack-int-renderpass-entityplayer-player-itemstack-usingitem-int-useremaining
[getCreativeTabs()]:/ForgeBin/net/minecraft/item/Item.md##public-creativetabs-getcreativetabs
