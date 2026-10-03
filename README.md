# EmberGen 界面中文词条库

[EmberGen](https://jangafx.com/) 1.2.6 界面文案的中英对照**词条数据**。

这个仓库只有数据，没有程序。

```
词条     4,118 条
表           9 个
```

## 目录

```
dict/zh_menu.json        菜单栏
dict/zh_startup.json     启动页
dict/zh_tooltip.json     控件的悬停提示
dict/zh_wrap.json        被折行的半句 —— 见下面「长句」一节
dict/zh_auto.json        主表。机翻打底，条目最多的一张
dict/zh_extra.json       主表的补充，机翻不合格的部分手工补译
dict/zh_gap.json         使用过程中陆续收集到的、其余各表里还没有的条目
dict/zh_fix.json         主表的修正表，最后应用、优先级最高
dict/zh_glossary.json    5 条术语锚点，不参与合并
```

## 合并顺序

**后面的覆盖前面的**：

```
zh_startup.json  →  zh_menu.json  →  zh_auto.json  →  zh_extra.json
   →  zh_tooltip.json  →  zh_wrap.json  →  zh_gap.json  →  zh_fix.json
```

所以：

- 要改某个词的译法，**改 `zh_fix.json`**，不要动 `zh_auto.json` —— 主表是机翻底表，改了容易被下一轮覆盖。
- `zh_gap.json` 是**追加**的，别整份覆盖重建，容易把已有条目冲掉。

## 数据格式

```json
{
  "_note": "本表的说明。以 _ 开头的键都是注释，不是词条。",
  "Lit": "受光",
  "Unlit": "不受光"
}
```

- **键** = 界面上的英文原文，**值** = 中文译文
- 以 `_` 开头的键是**给译者看的注释**，不参与翻译

## 翻译约定

- 标点一律用**半角**。
- 这几类一律**保留英文**：数据类型名（`Bool2` / `Float3` / `Uint8` / `Int32` …）、内部标识符（`Alloc` / `Blit` / `Futex` / `Wstring` …）、公司产品名。

### 长句

EmberGen 的界面是**先折行、再逐行取文本**的。所以一条很长的提示语，整句登记成一条键**永远不会被匹配到** —— 真正出现的是折行后的半行。

`zh_wrap.json` 收的就是这些半行。折行位置取决于控件宽度，**换分辨率或 DPI 后会失配**，届时要按新出现的半行补。

## 校对基准

按 EmberGen **1.2.6** 校对。

## 版权与用途

- EmberGen 是 **JangaFX** 的闭源商业软件。本仓库**不含它的任何文件**，译文所对应的界面原文版权归 JangaFX 所有。
- 词条译文由**星空汉化**编写，以 **CC BY-NC-SA 4.0** 发布（见 [LICENSE](LICENSE)）：署名、非商业、相同方式共享。
- 译文**完全免费**，禁止任何形式的售卖。如果你是付费买到的，说明你被骗了，请及时申请退款。
- EmberGen 版权归 JangaFX 所有，请支持正版。

## 反馈

B 站主页：<https://space.bilibili.com/177308205>

使用过程中遇到问题、发现漏译或译错，都欢迎来 B 站找我反馈。
