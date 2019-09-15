# public class MathHelper
数値計算のヘルパメソッドをまとめたユーティリティクラス。  
sin, cosの高速取得や、各塩山の


## メソッド

### public static final float sin(float radian)
radisnのsinを返す。  
sin値は予め計算されルックアップテーブルに格納されており、sin値を高速に取り出せる。  
return: sin(radian)

### public static final float cos(float radian)
radianのcosを返す。  
sinテーブルに格納された値を取り出すため、cos値を拘束に取り出せる。  
return cos(radian)

### public static final float sqrt_float(float x)
float型xの非負の平方根をfloat型で返す。  
return: xの非負の平方根

### public static final float sqrt_double(double x)
double型xの非負の平方根をfloat型で返す。  
return: xの非負の平方根

### public static int floor_float(float x)
float型xについて、[x]をint型で返す。
return: [x]

### @SideOnly(Side.CLIENT) public static int truncateDoubleToInt(double x)
xをInterger.MAX_VALUE-1024以下のint型にキャストして返す。
return: Integer.MAX_VALUE-1024以下のint型にキャストされたx

### public static int floor_double(double x)
double型xについて、[x]をint型で返す。
return: [x]

### public static long floor_double_long(double x)
double型xについて、[x]をlong型で返す。

### @SideOnly(Side.CLIENT) public static int func_154353_e(double x)
double型xについて、[x]の絶対値をint型で返す。

### public static float abs(float x)
float型xについて、|x|をfloat型で返す。  
return: |x|

### public static int abs_int(int x)
int型xについて、|x|をint型で返す。  
return: |x|

### public static int ceiling_float_int(float x)
float型xについて、xの小数点以下切り上げをint型で返す。  
return: xの小数点以下切り上げ

###public static int ceiling_double_int(double x)
double型xについて、xの小数点以下切り上げをint型で返す。  
return: xの小数点以下切り上げ

### public static int clamp_int(int value, int min, int max)
int型valueについて、valueをmin, maxでクランプして返す。  
min <= value <= maxとなるようにvalueをmin, maxの範囲内に収めて返す。  
return: valueのmin, maxによるクランプ

### public static float clamp_float(float value, float min, float max)
float型valueについて、valueをmin, maxでクランプして返す。  
return: valueのmin, maxによるクランプ

### public static double clamp_double(double value, double min, double max)
double型valueについて、valueをmin, maxでクランプして返す。  
return: valueのmin, maxによるクランプ

### public static double denormalizeClamp(double x, double y, double r)
x, yをrにより線形補完した値を返す。  
rが0以下の場合はx, rが1以上の場合はyを返す。  
return: r<=0ならばx, r>=1ならばy, そうでなければx, yのrによる線形補完

### public static double abs_max(double x, double y)
x, yの絶対値を比較し、大きい絶対値を返す。  
return max([x] [y])

### @SideOnly(Side.CLIENT) public static int bucketInt(int i, int bucketSize)
floor((double)i / bucketSize)を返す。
return: floor((double)i / bucketSize)

### @SideOnly(Side.CLIENT) public static boolean stringNullOrLengthZero(String text)
textがnull, 又は空ならtrueを返す。  
return: textがnull, 又は空ならtrue

### public static int getRandomIntegerInRange(Random random, int min, int max)
min以上max以下のランダムなint値を返す。  
min >= maxの場合はminを返す。  
return: min >= maxならばmin、そうでなければmin以上max以下のランダムなint値

### public static float randomFloatClamp(Random random, float min, float max)
min以上max未満のランダムなfloat値を返す。  
min >= maxの場合はminを返す。  
return min >= maxならばmin、そうでなければmin以上max未満のランダムなfloat値

### public static double getRandomDoubleInRange(Random random, double min, double max)
min以上max未満のランダムなdouble値を返す。  
min >= maxの場合はminを返す。  
return min >= maxならばmin、そうでなければmin以上max未満のランダムなdouble値

### public static double average(long[] values)
valuesの平均値をdouble型で返します。  
return: valuesの平均値

### public static float wrapAngleTo180_float(float angle)
float値のangleを同じ向きで(-180, 180]の値に変換する。  
return: angleと同じ向きで(-180, 180]の角度

### public static double wrapAngleTo180_double(double angle)
double値のangleを同じ向きで(-180, 180]の値に変換する。  
return: angleと同じ向きで(-180, 180]の角度

### public static int parseIntWithDefault(String value, int default)
文字列valueをint型として解析するが、失敗した場合はdefaultを返す。  
return: int型として解析されたvalue, 失敗したらdefault

### public static int parseIntWithDefaultAndMax(String value, int default, int min)
文字列valueをintとして解析するが、失敗した場合はdefaultを返す。ただし、返す値はmin以上。  
return: int型として解析されたvalue、失敗した場合はdefault、ただしはmin以上

### public static double parseDoubleWithDefault(String value, double default)
valueをdouble型として解析するが、失敗した場合はdefaultを返す。  
return: double型として解析されたvalue、失敗した場合はdefault

### public static double parseDoubleWithDefaultAndMax(String value, double default, double min)
valueをdouble型として解析するが、失敗した場合はdefaultを返す。ただし、返す値はmin以上。  
return: double型として解析されたvalue、失敗したらdefault、ただしmin以上

### @SideOnly(Side.CLIENT) public static int roundUpToPowerOfTwo(int n)
n以上で最小な2の冪乗を返す。ただしnが0又は負の時は0を返す。  
return: n以上で最小な2の冪乗、ただしnが0又は負の時は0

### @SideOnly(Side.CLIENT) public static int calculateLogBaseTwo(int antilogarithm)
2を底とするantilogarithmの対数以下で最大のint値を返す。  
return: 2を底とするantilogarithmの対数以下で最大のint値

### @SideOnly(Side.CLIENT) public static int func_154354_b(int value, int base)
不明。value以上でbaseの倍数になる最小のvalueを返す？  
baseが負の時の返す値は未定義？  
return:  value以上でbaseの倍数になる最小のvalueを返す？
