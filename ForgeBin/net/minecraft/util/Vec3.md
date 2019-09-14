# public class Ven3
3次元ベクトルを表すクラス。  
各フィールドは公開されているため注意。


## フィールド
### public double xCoord
x成分

### public double yCoord
y成分

### public double zCoord
z成分


## コンストラクタ
### protected Vec3(double x, double y, double z)
引数に基づいて3次元ベクトルを生成する。  
protectedなコンストラクタなので、外部から生成するときはcreateVectorHelper()を使う。


## メソッド
### public static Vec3 createVectorHelper(double x, double y, double z)
引数に基づいて3次元ベクトルを生成するスタティックファクトリメソッド。
return: 新しい3次元ベクトル

### protected Vec3 setComponents(double x, double y, double z)
このベクトルの成分を引数の成分に設定する。  
return: このベクトル

### public Vec3 subtract(Vec3 another)
このベクトルとanotherの差分ベクトルを生成する。  
return: another - this

### public Vec3 normalize()
このベクトルを正規化したベクトルを生成する。  
絶対値が1.0E-4より小さい場合は0ベクトルを生成する。
return: このベクトルの正規化ベクトル

### public double dotProduct(Vec3 another)
このベクトルとanotherの内積を返す。  
return: this・another

### public Vec3 crossProduct(Vec3 another)
このベクトルとanotherの外積ベクトルを生成する。  
Minecraftの座標系は右手系なことに注意。  
return: this × another

### public Vec3 addVector(double x, double y, double z)
このベクトルに引数の成分を足したベクトルを生成する。  
return: thisと引数の成分の和ベクトル

### public double distanceTo(Vec3 another)
このベクトルとanotherのユークリッド長を返す。  
return: thisとanotherのユークリッド長

### public double squareDistanceTo(Vec3 another)
このベクトルとanotherの平方ユークリッド長を返す。  
return: thisとanotherの平方ユークリッド長

### public double squareDistanceTo(double x, double y, double z)
このベクトルと引数の成分の平方ユークリッド長を返す。  
return: thisと引数の成分の平方ユークリッド長

### public double lengthVector()
このベクトルの長さを返す。
return: thisの長さ

### public Vec3 getIntermediateWithXValue(Vec3 another, double intermediateX)
intermediateXに基づいて、このベクトルとanotherのX軸に関する中間ベクトルを生成する。  
intermediateXは以下の式を満たす必要があり、そうでない場合はnullを返す。
```(java)
Math.abs(this.xCoort) <= Math.abs(intermediateX) && Math.abs(intermediateX) <= Math.abs(another.xCoord)
```
また、```Math.pow(another.xCoord - this.xCoord, 2)```が極端に小さい(つまり中間値を生成できない場合)場合もnullを返す。  
適切なintermediateXが渡された場合、intermediateXを元にx成分の内分比を計算、各成分の差分に内分比を適応しthisに足した和ベクトルを生成する。  
return: intermediateXに基づく中間ベクトル、または生成できないならnull

### public Vec3 getIntermediateWithYValue(Vec3 another, double intermediateY)
intermediateYに基づいて、このベクトルとanotherのY軸に関する中間ベクトルを生成する。  
getIntermediateWithXValue(Vec3 another, double intermediateX)同様にY軸に関して中間値ベクトルを生成する。
return: intermediateYに基づく中間ベクトル、または生成できないならnull

### public Vec3 getIntermediateWithZValue(Vec3 another, double intermediateZ)
intermediateZに基づいて、このベクトルとanotherのZ軸に関する中間ベクトルを生成する。  
getIntermediateWithXValue(Vec3 another, double intermediateX)同様にZ軸に関して中間値ベクトルを生成する。  
return: intermediateZに基づく中間ベクトル、または生成できないならnull

### public String toString()
このベクトルの文字列表現を返す。  
return: このベクトルの文字列表現

### public void rotateAroundX(float radRotation)
このベクトルをX軸中心にradRotationだけ回転する。

### public void rotateAroundY(float radRotation)
このベクトルをY軸中心にradRotationだけ回転する。

### public void rotateAroundZ(float radRotation)
このベクトルをZ軸中心にradRotationだけ回転する。
