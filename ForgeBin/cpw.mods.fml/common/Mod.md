# public @interface Mod
付与されたクラスがMod本体であることを表すアノテーション。

Mod本体となるクラスに付与し、必要なメタデータを記入する。


## メソッド

### String modid();
Mod同士を識別するためのID。ユニークなIDを指定する。  

### String version() default "";
Modのバージョンを指定する。
