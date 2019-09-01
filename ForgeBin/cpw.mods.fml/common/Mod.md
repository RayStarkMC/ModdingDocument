# @interface Mod
付与されたクラスがMod本体であることを表すアノテーション。

Mod本体となるクラスに付与し、必要なメタデータを記入し、初期化イベント用のハンドラを用意する。


## メタデータ

### String modid();
Mod同士を識別するためのID。ユニークなIDを指定する。  

### String name() default "";
ユーザーに周知するMod名

### String version() default "";
Modのバージョンを指定する。

## アノテーション

### @interface EventHandler
イベントハンドラ用のメソッドに付与するアノテーション。メソッドの引数で処理したいイベントを受け取るようにする。

### @interface Instance
ModIDから@Modが付与されたクラスのインスタンスを取得するためのアノテーション。
#### String value() default "";
インスタンスを取得するModのIDを指定する。
