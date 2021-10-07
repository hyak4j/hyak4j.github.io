# Android View元件效果整理


<!--more-->

### 1.Selector資源檔狀態屬性
   屬性名稱  |       說明
--------------|-------|
android:state_pressed | true表示元件被按下時套用
android:state_focused |true表示元件正被操作時套用
android:state_hovered | SDK > 14可用，等同於android:state_focused
android:state_selected |true表示元件被選時套用
android:state_checkable | true表示元件項目能被勾選時套用
android:state_checked | true表示元件項目被勾選時套用
android:state_enabled | true表示元件可以使用時套用
android:state_activated | true表示元件在作用中時套用
android:state_window_focused | true表示當程式正在操作時套用

**使用範例1 
(Selector定義於XML)**

```XML
<?xml version="1.0" encoding="utf-8"?>
<selector xmlns:android="http://schemas.android.com/apk/res/android">
    <item android:state_pressed="true" android:drawable="@color/btn_bg_pressed" />
    <item android:drawable="@color/btn_bg_normal" />
</selector>
```

**使用範例2 
(將Selector設置於元件background)**

```XML
<?xml version="1.0" encoding="utf-8"?>
<TextView xmlns:android="http://schemas.android.com/apk/res/android"
    android:id="@+id/mTxt"
    android:layout_width="match_parent"
    android:layout_height="wrap_content"
    android:background="@drawable/selector" />
```

