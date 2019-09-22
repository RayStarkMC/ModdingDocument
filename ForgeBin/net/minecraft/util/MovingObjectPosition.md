# public class MovingObjectPosition
視線上の[Entity]又は[Block]の位置を表すコンテナクラス。  
全てのフィールドが**可変**なため扱いには注意。[Entity]の位置を表す場合、**コンストラクタがhitVecを複製しない**ので注意。



## フィールド

### public MovingObjectPosition.MovingObjectType typeOfHit
視点の対象の種類。  
[MovingObjectType]参照。

### public int blockX
[Block]のx座標。

### public int blockY
[Block]のy座標。

### public int blockZ
[Block]のz座標。

### public int sideHit
視線あたっている[Block]のヒット面。  
[ForgeDirection].getOrientation(int id)に渡すことで面に対応する列挙を取得できる。  
0 DOWN  
1 UP  
2 NORTH  
3 SOUTH  
4 WEST  
5 EAST  
その他 UNKNOWN

### public Vec3 hitVec
[Entity]または[Block]に当たった視点を表す位置ベクトル。

### public Entity entityHit
視点が当たっている[Entity]。

### public int subHit
未使用。初期値1。

### public Object hitInfo;
未使用。初期値null。


## コンストラクタ

### public MovingObjectPosition(int x, int y, int z, int sideHit, Vec3 hitVec)
typeOfHitをBLOCKに設定したMovingObjectPositionを生成する。
hitVecは複製される。

### public MovingObjectPosition(int x, int y, int z, int sideHit, Vec3 hitVec, boolean isHitBlock)
typeOfHitをBLOCKまたはMISSに設定したMovingObjectPositionを生成する。
hitVecは複製される。

### public MovingObjectPosition(Entity entityHit)
typeOfHitをENTITYに設定したMovingObjectPositionを生成する。
hitVecはentityの座標の位置ベクトルが指定される。

### public MovingObjectPosition(Entity entityHit, Vec3 hitVec)
typeOfHitをENTITYに設定したMovingObjectPositionを生成する。
hitVecは**複製されない**。

### public String toString()
このMovingObjectPositionの文字列表現を取得する。


# public static enum MovingObjectType
視点の対象の種類を表す列挙。


## 列挙子

### MISS
視点の対象が無いことを表す列挙子。

### BLOCK
[Block]を表す列挙子。

### ENTITY
[Entity]を表す列挙子。

[Block]:/ForgeBin/net/minecraft/block/Block.md
[Entity]:/ForgeBin/net/minecraft/entity/Entity.md
[MovingObjectType]:/ForgeBin/net/minecraft/util/MovingObjectPosition.md#public-static-enum-movingobjecttype
[ForgeDirection]:/ForgeBin/net/minecraftforge/common/util/ForgeDirection.md
