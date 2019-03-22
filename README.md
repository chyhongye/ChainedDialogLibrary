# ChainedDialogLibrary
链式对话框库，支持自定义动画

## 使用方法

在对应的Module中添加依赖
```gradle
dependencies {
    ...
    implementation 'com.chy.chydialoglib:chydialoglib:1.1.1'
    ...
}
```
----------
### 所有对话框的通用方法

    注意：不管使用哪种对话框，要专用方法和通用方法混用的，都需要先使用专用方法，否则无法正常混用

|方法|作用|参数/用法|默认值|  
|:----|:------:|:-:|:-:|
|setShowOnBottom(boolean showBottom)|设置是否在屏幕底部显示对话框|true在屏幕底部显示，false反之|false|
|setDialogSize(int width, int height)|设置对话框的宽度和高度|均为int型的dp值|0|
|setBothSidesMargin(int margin)|设置对话框的左右边距|int型的dp值|0|
|setOutCancel(boolean outCancel)|设置是否点击对话框外部可以隐藏对话框|true点击外部隐藏对话框，false反之|true|
|show(FragmentManager manager)|显示对话框|FragmentManager|-|
|setDialogAnim(DialogAnim dialogAnim)|设置对话框进出场动画|ANIM_ALPHA,<br>ANIM_SCALE,<br>ANIM_ROTATE,<br>ANIM_LEFT_TO_LEFT,<br>ANIM_LEFT_TO_TOP,<br>ANIM_LEFT_TO_RIGHT,<br>ANIM_LEFT_TO_BOTTOM,<br>ANIM_RIGHT_TO_RIGHT,<br>ANIM_RIGHT_TO_BOTTOM,<br>ANIM_RIGHT_TO_LEFT,<br>ANIM_RIGHT_TO_TOP,<br> ANIM_TOP_TO_TOP,<br>ANIM_TOP_TO_RIGHT,<br>ANIM_TOP_TO_BOTTOM,<br>ANIM_TOP_TO_LEFT,<br>ANIM_BOTTOM_TO_BOTTOM,<br>ANIM_BOTTOM_TO_LEFT,<br>ANIM_BOTTOM_TO_TOP,<br>ANIM_BOTTOM_TO_RIGHT|ANIM_SCALE|
|setCustomizeAnim(@StyleRes int animStyle)|设置自定义动画的方法|R.style.xxx<br>xxx为你定义在styles文件中的“android:windowEnterAnimation”<br>和“android:windowExitAnimation”动画|R.style.anim_scale|
----------
## 提示对话框
### 预览图
<img src="/preview/prompt_dialog.gif" alt="提示对话框预览图" width="360" height="640">

### 方法使用
|方法|作用|参数/用法|默认值|  
|:----|:------:|:-:|:-:|
|setButtonText(String btnText)|设置按钮文字|字符串|-|
|setButtonTextColor(@ColorInt int btnTextColor)|设置按钮文字颜色|Color值|-|
|setButtonTextFontSize(float btnTextSize)|设置按钮文字大小|浮点值|15sp|
|setContentText(String contentText)|设置内容文字|字符串|-|
|setContentTextColor(@ColorInt int contentTextColor)|设置内容文字颜色|字符串|-|
|setContentTextFontSize(float contentTextSize)|设置内容文字大小|浮点值|-|
|setBackgroundColor(@ColorInt int backgroundColor)|设置对话框背景颜色|Color值|-|
|setBackground(Drawable backgroundDrawable)|设置对话框背景|Drawable值|-|
|setBackgroundRes(@DrawableRes int backgroundDrawableResource)|设置对话框背景图|Resource中的id值|-|
|setDividingColor(@ColorInt int dividingColor)|设置水平分割线的颜色|Color值|#6b6b6b|
|setDividingShow(boolean dividingShow)|设置是否显示水平分割线|true为显示，false反之|true|
|setOnDialogClickListener(OnDialogClickListener listener)|设置按钮的监听器|监听OnDialogClickListener<br>返回onDialogClick(View view, BaseDialog dialog)|-|

### 简单用法
```java
PromptDialog.newInstance()
    .setButtonText("好的")
    .setButtonTextColor(Color.BLUE)
    .setContentText("测试通知")
    .setOnDialogClickListener(new OnDialogClickListener() {
        @Override
        public void onDialogClick(View view, BaseDialog dialog) {
            dialog.dismiss();
            }
        })
    .show(getSupportFragmentManager());
```
----------
## 文本对话框
### 预览图
<img src="/preview/text_dialog.gif" alt="文本对话框预览图" width="360" height="640">

### 方法使用
|方法|作用|参数/用法|默认值|  
|:----|:------:|:-:|:-:|
|setDialogType(DIALOG_TYPE dialog_type)|设置对话框类型| NONE,<br>ERROR,<br>INFORMATION,<br>RIGHT,<br>WARNING|NONE|
|setCustomIcon(@DrawableRes int customIcon)|设置自定义的icon|Resource中的id值|-|
|setTitleText(String titleText)|设置对话框的标题文字|字符串|-|
|setTitleTextColor(@ColorInt int titleTextColor)|设置对话框标题文字的颜色|Color值|-|
|setTitleTextSize(float titleTextSize)|设置对话框标题文字大小|浮点值|-|
|setContentText(String contentText)|设置对话框内容文字|字符串|-|
|setContentTextColor(@ColorInt int contentTextColor)|设置对话框内容文字的颜色|Color值|-|
|setContentTextSize(float contentTextSize)|设置对话框内容文字大小|浮点值|-|
|setContentTextGravity(int contentGravity)|设置对话框内容文字的对齐方式|Gravity值|Gravity.CENTER|
|setBackgroundColor(@ColorInt int backgroundColor) |设置对话框背景颜色|Color值|-|
|setBackground(Drawable backgroundDrawable)|设置对话框背景|Drawable值|-|
|setBackgroundRes(@DrawableRes int backgroundDrawableResource)|设置对话框背景图|Resource中的id值|-|
|setCancelButtonText(String cancelText)|设置取消按钮文字|字符串|取消|
|setCancelButtonTextColor(@ColorInt int cancelButtonTextColor)|设置取消按钮文字颜色|Color值|Color.RED|
|setCancelButtonTextSize(float cancelButtonTextSize)|设置取消按钮文字大小|浮点值|15sp|
|setCancelButtonShow(boolean cancelButtonShow)|设置是否显示取消按钮|true为显示，false反之|true|
|setConfirmButtonText(String confirmButtonText)|设置确认按钮文字|字符串|好的|
|setConfirmButtonTextColor(@ColorInt int confirmButtonTextColor)|设置确认按钮文字颜色|Color值|Color.BLUE|
|setConfirmButtonTextSize(float confirmButtonTextSize)|设置确认按钮文字大小|浮点值|15sp|
|setConfirmButtonShow(boolean confirmShow)|设置是否显示确认按钮|true为显示，false反之|true|
|setHDividingShow(boolean hDividingShow)|设置是否显示水平分割线|true为显示，false反之|true|
|setHDividingColor(@ColorInt int hDividingColor)|设置水平分割线颜色|Color值|#6b6b6b|
|setVDividingShow(boolean vDividingShow)|设置是否显示垂直分割线|true为显示，false反之|true|
|setVDividingColor(@ColorInt int vDividingColor)|设置垂直分割线颜色|Color值|#6b6b6b|
|setOnCancelClickListener(OnDialogClickListener cancelClickListener)|设置取消按钮的点击事件|监听OnDialogClickListener<br>返回onDialogClick(View view, BaseDialog dialog)|-|
|setOnConfirmClickListener(OnDialogClickListener confirmClickListener)|设置确认按钮的点击事件|监听OnDialogClickListener<br>返回onDialogClick(View view, BaseDialog dialog)|-|

### 简单用法
```java
 TextDialog.newInstance()
    .setDialogType(TextDialog.DIALOG_TYPE.INFORMATION)
    .setTitleText("通知信息")
    .setContentText("Bootstrap 是一套用于 HTML、CSS 和 JS 开发的开源工具集。利用我们提供的 Sass 变量和大量 mixin、响应式栅格系统、可扩展的预制组件、基于 jQuery 的强大的插件系统，能够快速为你的想法开发出原型或者构建整个 app 。")
    .setContentTextGravity(Gravity.LEFT)
    .setOnCancelClickListener(new OnDialogClickListener() {
        @Override
        public void onDialogClick(View view, BaseDialog dialog) {
            toast("点击了取消按钮");
            dialog.dismiss();
        }
    })
    .setOnConfirmClickListener(new OnDialogClickListener() {
        @Override
        public void onDialogClick(View view, BaseDialog dialog) {
            toast("点击了确定按钮");
            dialog.dismiss();
        }
    })
    .show(getSupportFragmentManager());
```
----------
## 条目对话框
### 预览图
<img src="/preview/item_dialog.gif" alt="条目对话框预览图" width="360" height="640">

### 方法使用

### 简单用法
----------
## 网格对话框
### 预览图
<img src="/preview/grid_dialog.gif" alt="网格对话框预览图" width="360" height="640">

### 方法使用

### 简单用法
----------
## 加载对话框
### 预览图
<img src="/preview/loading_dialog.gif" alt="加载对话框预览图" width="360" height="640">

### 方法使用

### 简单用法
