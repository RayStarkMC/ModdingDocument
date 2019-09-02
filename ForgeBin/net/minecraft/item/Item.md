# class Item
ゲーム内における[ItemStack]の振る舞いを表現するクラス。  
[ItemStack]が生成されるときに必ずItemクラスが参照され、[ItemStack]の各振る舞いはItemクラスのメソッドを参照する。Blockクラスに対してはこのクラスを継承したItemBlockクラスが対応している。

## フィールド
### static final RegistryNamespaced itemRegistry
Minecraft本体のアイテムレジストリ。  
基本的にForgeのGameRegistryを利用するため使用しない。

### protected static Random itemRand
Itemクラスに紐づけされたRondomインスタンス。  
アイテムに関係した乱数を生成するときに利用されている。

### protected int maxStackSize
このアイテムの最大スタック数。  
初期値は64。

### protected boolean bFull3D


[ItemStack]:/ForgeBin/net/minecraft/item/ItemStack.md
