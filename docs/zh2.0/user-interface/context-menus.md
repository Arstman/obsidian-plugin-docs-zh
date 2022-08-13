<!--
 * @Author: luhaifeng666 youzui@hotmail.com
 * @Date: 2022-08-09 17:26:34
 * @LastEditors: luhaifeng666
 * @LastEditTime: 2022-08-13 22:01:55
 * @Description: 
-->
# 快捷菜单

如果想要打开 context menu, 使用 [`Menu`](../reference/typescript/classes/Menu.md):

```ts
import { Menu, Notice, Plugin } from "obsidian";

export default class ExamplePlugin extends Plugin {
  async onload() {
    this.addRibbonIcon("dice", "Open menu", (event) => {
      // highlight-start
      const menu = new Menu(this.app);

      menu.addItem((item) =>
        item
          .setTitle("Copy")
          .setIcon("documents")
          .onClick(() => {
            new Notice("Copied");
          })
      );

      menu.addItem((item) =>
        item
          .setTitle("Paste")
          .setIcon("paste")
          .onClick(() => {
            new Notice("Pasted");
          })
      );

      menu.showAtMouseEvent(event);
      // highlight-end
    });
  }
}
```

[`showAtMouseEvent()`](../reference/typescript/classes/Menu.md#showatmouseevent) 方法打开鼠标点击的菜单。

:::tip
如果您需要控制菜单出现的位置，您可以使用 `menu.showAtPosition({ x: 20, y: 20 })` 去打开相对 Obsidian 窗口左上角相应位置的菜单。
:::

想知道还有哪些 icons 能够使用，可以查阅 [Icons](icons.md) 这篇文档。

您也可以通过订阅 `file-menu` 和 `editor-menu` workspace 事件的方式，向文件菜单或者编辑菜单中添加一个菜单项：

![Context menu positions](/images/img/context-menu-positions.png)

```ts
import { Notice, Plugin } from "obsidian";

export default class ExamplePlugin extends Plugin {
  async onload() {
    this.registerEvent(
      this.app.workspace.on("file-menu", (menu, file) => {
        menu.addItem((item) => {
          item
            .setTitle("Print file path 👈")
            .setIcon("document")
            .onClick(async () => {
              new Notice(file.path);
            });
        });
      })
    );

  this.registerEvent(
      this.app.workspace.on("editor-menu", (menu, editor, view) => {
        menu.addItem((item) => {
          item
            .setTitle("Print file path 👈")
            .setIcon("document")
            .onClick(async () => {
              new Notice(view.file.path);
            });
        });
      })
    );
  }
}
```

想要获取关于处理事件的更多信息，可以查阅 [Events](../events.md) 这篇文档。
