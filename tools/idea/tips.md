#	IDEA 使用技巧

###	行注释的自动缩进

```
# 菜单定位
Preference > Editor > Code Style > Java > Code Generation > Comment Code
```

###	由 Command + Enter 激活的菜单

根据光标所在位置代码的特点，编辑器提供针对性的上下文菜单，称为 [*Intentions*](https://www.jetbrains.com/help/idea/2016.3/intentions-2.html?utm_content=2016.3&utm_medium=help_link&utm_source=from_product&utm_campaign=IC)。有只是因为于传统的、由鼠标右键激活的上下文菜单，这种上下文菜单由 Command + Enter 组合键激活，其配置界面可以通过以下通道打开：
```
# 菜单定位
Preference > Editor > Intentions
```

###	Live Template 不符合预期？

有时候模板自动展开时，与预先定义的格式有出入，这通常是因为根据编辑器根据当前代码样式自动重排的结果。每个模板右侧有若干选项（options），如果不希望启用自动重排功能，将以下选项灭活即可：
```
◻︎ Reformat according to style
```
