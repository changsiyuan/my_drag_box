## my drag box

---

### 说明
- 实现了一个点击按钮后，弹出登录对话框，点击对话框以外的部分，隐藏对话框，且鼠标放在对话框上按下和移动能够拖动对话框的功能；

- 下图分别是：没有对话框、弹出对话框、移动对话框

![no_box](/image/no_box.png)

![box](/image/box.png)

![move_box](/image/move_box.png)

### 实现难点
- 如何实现点击按钮弹出对话框？
  - 刚开始对话框设置为`display:none;`
  - 点击按钮后，对话框被设置为`display:block;`
  - 将对话框的position属性设置为fixed，top/left/right/bottom属性均设置为0，背景色和透明度也相应设置，可保证对话框弹出后，非对话框的内容可见但不可点击；

- 如何实现点击非对话框的部分，使对话框隐藏？
  - 首先，必须精确的选中非对话框部分。由于jQuery的`:not`选择器用于反向选择元素，但本例中`#loginWapper`和`#innerWapper`所选中的对象是紧挨着的父子关系，并没有其他元素相间隔，所以用`#loginWapper:not(#innerWapper)`并不能实现我们的需求。正确的做法是获取事件的target属性，用`is`方法来判断；
  - 在检测到非对话框部分有点击事件发生时，对话框的display属性被设置为none；

- 如何实现拖放
  - 具体请见程序；