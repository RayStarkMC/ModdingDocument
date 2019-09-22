# public enum ForgeDirection
方向を表す列挙。


## 列挙子

### DOWN
下方向。y-

### UP
上方向。y+

### NORTH
北方向。z-

### SOUTH
南方向。z+

### WEST
西方向。x-

### EAST
東方向。x+

### UNKNOWN
getOrientation(int id)で対応する列挙子が無いときに利用される。


## フィールド

### public final int offsetX
x軸オフセット。

### public final int offsetY
y軸オフセット。

### public final int offsetZ
z軸オフセット。

### public final int flag
未使用？

### public static final ForgeDirection[] VALID_DIRECTIONS;
UNKNOWNを除いたForgeDirectionの配列。

### public static final int[] OPPOSITES
ordinal()を基準に反対の方向のインデックスを保持した配列。

### public static final int[][] ROTATION_MATRIX
軸方向を見たときのある方向を時計回りに90°回転した時の方向のordinal()を表す表現行列。
回転後の面はROTATION_MATRIX[axis][direction]となる。


## メソッド

### public static ForgeDirection getOrientation(int id)
idに対応した方向を返す。  
VALID_DIRECTIONS[id]を返すが、不適切なidが渡された場合はUNKNOWNを返す。  
[MovingObjectPosition]のsideHitを渡すと面に対応する方向を返す。

### public ForgeDirection getOpposite()
この方向の逆方向を返す。

### public ForgeDirection getRotation(ForgeDirection axis)
axis方向を見てこの方向を時計回りに90°回転した方向を返す。

[MovingObjectPosition]:/ForgeBin/net/minecraft/util/MovingObjectPosition.md
