---
stage: 04-script
platform: bilibili
status: draft
source_workflow: /04-script-draft
upstream_inputs:
  - 02-plan/README.md (status: draft)
  - 02-plan/tutorial.final.md (status: draft)
  - 03-plan-bilibili/README.md (status: draft)
  - shared/docs/remotion-spec.md
---

> ⚠️ **重做版（对齐三段主线）**：本脚本已按 `tutorial.final.md` 的「教人用 Vibe Coding」三段主线重写——开场 → 找技术路径 → 技术选型 → 技术落地 → 总结，并逐段对齐 `03-plan-bilibili/README.md` 的 12 个 scene_storyboard。旧的「两步/选路线·搭引擎」框架已弃用（流程即代码/角色编排归 EP05/EP06）。上游 `tutorial.final.md` 当前为 `draft`，本稿随其一同待人工复核后再置 `approved`。

# ep02 视频脚本：《用 Vibe Coding 搭一套能自动出片的视频渲染引擎》

**总时长预估**：约 5 分 18 秒（318s）
**口播字数预估**：约 1750 字
**主线**：站在"没有前后端基础、用大白话指挥 AI（Vibe Coding）"的视角，讲三步——① 找技术路径（让 AI 罗列现成路线）；② 技术选型（对约束选定 Remotion）；③ 技术落地（驱动 Remotion 按配置出片）。
**反噱头纪律**：不以"多少行代码/百倍效率/一键生成"为卖点；SSR `window` 坑定位为"选这条路要付的税"。

---

## 第一段：【@IntroScene】开场钩子（0:00–0:30，30s）

- **[画面]** 调用 `@IntroScene`。参数 `title`="用 Vibe Coding 搭一套能自动出片的视频渲染引擎"，`subtitle`="《Vibe Coding 造一条自动化视频生产线》EP02 · 视频渲染"，`roadmap`=["① 探索技术路径", "② 严谨技术选型", "③ 自动化落地"]，`background`="particles"。
  - **[子镜头时间线]**（黄金 5 秒留存，极速视觉切换）：
    - 0s [双画面切入]：左边修改 JSON 配置文件（修改标题与文本内容），右边终端自动运行 `npx remotion render`，进度条 1 秒锁死、新视频一秒出片
    - 4s [代码结构演示]：画面展开 IDE，展示 JSON 配置文件中数据字段与渲染出的视频画面的动态对应映射，体现“改配置即改片”的声明式优势
    - 15s [主视觉渐显]：粒子背景渐显，主标题弹性入场（spring_scale）
    - 20s [副标题与路线图]：副标题淡入，三步路线图（探索路径、严谨选型、自动化落地）依次浮现并锁定
- **[口播]** 改一版视频，我只改配置里这一行字，回车，一秒钟新片自动出来。能这么干，靠的是一个判断：AI 最擅长的就是文本和代码，那就把整条视频也变成代码和数据来驱动——改数据，就等于改片。这一期，就用这招解决视频自动渲染。整套引擎我一行没手写，全靠大白话指挥 AI，这就叫 Vibe Coding：我没前后端基础，只负责说要什么、判断对不对，写和填交给 AI。三步走——找技术路径、做技术选型、技术落地出片。记一句：你说人话，AI 干脏活，没基础也能抄。

---

## 第二段：【@ConceptScene】找技术路径·先让 AI 把路摆出来（共同内核）（0:30–0:45，15s）

- **[画面]** 调用 `@ConceptScene`。参数 `eyebrow`="找技术路径"，`title`="先让 AI 把'能把视频写成代码'的路都摆出来"，`items`=[{label:"INPUT", title:"用代码/数据描述画面"}, {label:"COMPILE", title:"程序编译成帧"}, {label:"OUTPUT", title:"合成视频"}]，`background`="gradient"。
  - **[子镜头时间线]**：0s eyebrow + 标题入场 → 3s 三步骤卡片 stagger 入场 → 7s 箭头依次连接 INPUT→COMPILE→OUTPUT → 11s 整体轻微脉冲强调"内核一样"。
- **[口播]** 第一步，找路。别自己埋头啃文档，把选择题直接甩给 AI：想把视频写成代码、自动出片，有哪些现成路子？它一摆出来，内核就清楚了——这些路子全是一回事：用代码描述画面、编译成一帧帧、再合成视频，区别只在用什么语言、什么引擎。

---

## 第三段：【@ConceptScene】找技术路径·六条技术路线（0:45–1:20，35s）

- **[画面]** 调用 `@ConceptScene`（卡片阵列，6 张）。参数 `title`="AI 摆出的六条路线"，`items`=[{title:"网页渲染 · Remotion", desc:"React 组件+CSS，无头浏览器逐帧截图"}, {title:"Motion Canvas/Revideo", desc:"写函数描述动画时序"}, {title:"Manim", desc:"Python 描述几何/公式"}, {title:"MoviePy", desc:"Python 操作像素+FFmpeg"}, {title:"PixiJS/Cocos", desc:"Canvas 上逐帧画"}, {title:"FFmpeg+脚本", desc:"命令行合成"}]。
  - **[子镜头时间线]**：0s 标题入场 → 3s 前三条卡片 stagger 入场 → 15s 后三条卡片 stagger 入场 → 28s 高亮 Remotion 卡 → 32s 底部浮出"同一内核：把画面编译成帧"。
- **[口播]** AI 一口气给我摆了六条路。第一条网页渲染，台柱子是 Remotion，拿 React 组件加 CSS 画画面，再用无头浏览器一帧帧截图，复杂排版最拿手。第二条 Motion Canvas，写函数描述动画时序，做代码演示很顺手。第三条 Manim，用 Python 描述几何和公式，数学可视化的神器。第四条 MoviePy，Python 直接抠像素加 FFmpeg，简单拼接够用。第五条 PixiJS 这类画布引擎，在 Canvas 上逐帧画，专治复杂粒子特效。第六条 FFmpeg 加脚本，命令行合成，批量转码、烧字幕特别猛。六个名字听着各不相同，扒到底都在干同一件事——把画面编译成帧。

---

## 第四段：【@TableScene + B 轨】技术选型·严谨权衡技术局限（1:20–2:15，55s）

- **[B 轨]** `@VideoSlot`：`[B 轨占位替换提醒：请用户补充 IDE 录屏 — 和 AI 对话深度分析每条技术路线的局限性与关键约束（clip_id=b-ide-route-pitfalls）]`，作为 A 轨判断层矩阵的过程性 cut-in。
- **[A 轨兜底]**（B 轨缺失时使用）调用 `@TableScene`。参数 `eyebrow`="对照技术约束做减法"，`title`="严谨分析技术路线局限性与关键约束"，`columns`=["技术路线","适用场景","局限条件","关键约束"]，`rows`=[["Remotion","前端栈、复杂网页排版、跨期模板复用","纯后台超长视频批处理","打包时读浏览器对象会崩；BUSL商业授权"],["Motion Canvas / Revideo","代码演示、精确时序动画设计","复杂企业级网页排版","技术生态规模较小，模板自攒成本高"],["Manim","数学、几何、算法可视化展示","常规 UI 排版、标准网页排版","学习曲线陡峭、排版弱、大场景渲染慢"],["MoviePy","纯 Python 简单拼贴、音轨自动闪避","复杂自适应布局、动态文字特效","排版繁琐、多层时重度消耗内存、难以缓存"],["PixiJS / Cocos","游戏类高性能粒子特效与交互动画","标准网页 UI 体系、自适应文字对齐","复杂多行文本排版与自适应计算繁琐"],["FFmpeg + 脚本","批量转码、底层音视频合并","高精度自定义动效、复杂页面排版","命令语法晦涩、调试与异常定位极度困难"]]，`highlight_row`=0，`highlight_column`=3。
  - **[子镜头时间线]**（口播 >15s，必填）：0s 表头淡入 → 5s 六行依次 stagger 入场（至 25s）→ 28s 高亮"关键约束"整列 → 38s B 轨 IDE 录屏切入 → 48s 高亮 Remotion 行 + 浮出"对照约束做减法"标记。
- **[口播]** 第二步，选型，最容易翻车。直接问 AI 哪个好没用，它会把每个都夸一遍；真正值钱的，是看清每条路在哪掉链子。所以我逼它：每条路适合干啥、有哪些会咬人的坑，全抖出来，整理成这张表。Remotion 适合前端栈和复杂自适应排版，但它 Node 打包、无头浏览器渲染，组件最外层直接读 window 会在打包阶段崩；而且走 BUSL 商业授权，规模化要付费。Motion Canvas 生态小，模板得自己攒；Manim 排版弱、渲染慢；MoviePy 写自适应排版繁琐、多层吃内存；PixiJS 光算文字对齐就费劲；FFmpeg 命令晦涩、出问题难定位。坑摊开，再对着自己的需求做减法。记一句：让 AI 把信息铺平，拍板你自己来。

---

## 第五段：【@ConceptScene】技术选型·回到约束，为什么选 Remotion（2:15–2:40，25s）

- **[画面]** 调用 `@ConceptScene`。参数 `eyebrow`="回到我自己的约束"，`title`="为什么是 Remotion"，`items`=[{label:"模板", title:"固定模板换数据就复用", desc:"改一处主题全系列生效", icon:"🏗️"}, {label:"AI", title:"让 AI 接手最稳", desc:"只填数据、套现成组件，最不容易出错", icon:"🤖"}, {label:"CLI", title:"一行命令就出片", desc:"npx remotion render 纯命令行", icon:"▶️"}, {label:"WEB", title:"网页生态现成可用", desc:"CSS/动效/图表库随手拿", icon:"🌐"}]，`background`="gradient"。
  - **[子镜头时间线]**：0s eyebrow+标题入场 → 3s 三条约束卡 stagger 入场 → 12s "Remotion 胜出"四点浮现 → 20s badge="决定性"强调"模板换数据复用"。
- **[口播]** 坑看清了，回到我自己的约束拍板。三条死要求摆给 AI：一期一个固定模板、换批数据就能批量出几十期；让 AI 改内容还不容易出错；好多期下来还得好维护。三条一对照，Remotion 明显赢——组件和数据分开，改一处主题整个系列跟着变；每期只让 AI 填数据、套现成组件，最不容易翻车；出片就一行命令；网页那套生态随手就能用。说白了：它最听 AI 的话，也最经得起反复折腾。

---

## 第六段：【@SplitLayout + @ComparisonCard】技术选型·Remotion vs 拼装 HTML 方案（2:40–3:05，25s）

- **[画面]** 调用 `@SplitLayout`（`direction`="horizontal"，`ratio`=0.5）：
  - 左 `@ComparisonCard`：`title`="✅ Remotion 框架"，`points`=["工程化复用：改一处组件，全系列样式同步","AI 维护友好：结构强约束，AI 只填配置数据","可长期维护：多期视频后依然拥有良好扩展性"]，`status`="success"。
  - 右 `@ComparisonCard`：`title`="❌ 拼装 HTML 方案"，`points`=["维护成本高：无工程化复用，每期需单独拼接","结构易跑偏：无强类型约束，AI 发挥空间过大","难以长期维护：超过十期视频后维护将成为灾难"]，`status`="error"。
  - 下方代价条：`text`="局限与代价：React 栈，采用 BUSL 商业授权（规模化商用要付费）"。
  - **[子镜头时间线]**：0s 分屏 center-out 展开 → 5s 左侧三条 stagger入场 → 13s 右侧三条 stagger 入场 → 20s 底部代价条浮出 → 23s 左侧微放大（胜出方 1.03x）。
- **[口播]** 有人觉得直接让 AI 拿 HTML 拼更省事，比一比就清楚差在哪——注意，两条路都是 AI 写代码，差的是工程化。复用上，Remotion 组件和数据分开，改一处全系列同步；裸 HTML 没有复用，AI 每期都得从头拼，改着改着就乱。约束上，Remotion 用 TypeScript 把字段类型管死，AI 只能老实填空；裸 HTML 没有强类型兜底，AI 一撒欢结构就跑偏。维护上，到第十期，Remotion 还能轻松扩，裸 HTML 早成了一团乱麻。代价也如实说：得吃 React 这套栈，还得认 BUSL 授权、规模化付费。但前端本来就让 AI 写、我把方向，正好把 Vibe Coding 的长处吃满。一句话：宁可前期立规矩，别等后期擦屁股。

---

## 第七段：【@ConceptScene】技术落地①·一份配置，自动分发成画面（3:05–3:30，25s）

- **[画面]** 调用 `@ConceptScene`（流向图 + 组件清单）。参数 `eyebrow`="技术落地"，`title`="一份配置 → Explainer 按 type 分发 → 现成组件"，`items`=[{label:"comparison", title:"→ ComparisonCard 对比卡"}, {label:"terminal_scene", title:"→ 合成终端：逐行打字，不用真录屏"}, {label:"screenshot_scene", title:"→ 截图叠光标/点击/打字"}, {label:"charts", title:"→ 柱/线/饼图、KPI"}, {label:"ConceptScene/SplitLayout", title:"→ 概念图解/左右分屏"}]。
  - **[子镜头时间线]**：0s 流向图标题入场 → 4s "配置→Explainer→组件"箭头连通 → 12s type→组件清单 stagger 入场 → 20s 高亮 terminal_scene/screenshot_scene 旁标"不用真录屏"。
- **[口播]** 选型定了，第三步落地。落地也不用你手写，就是陪 AI 把配置和组件对上号。仓库里这台引擎叫 remotion-composer：你写一份配置，说清这段画面长啥样、上面叠什么，主程序 Explainer 就按配置里的 type 字段，自动拎出对应组件去渲。type 写 comparison 出对比卡，terminal_scene 是合成终端、命令逐行打出来、不用真录屏，screenshot_scene 把截图叠上光标点击，还有图表、概念图、分屏，全是现成通用件，照着填就能用。想更有辨识度，还能让 AI 在这之上扩一套自有品牌组件库——那是更大的话题，以后单开一期。记一句：引擎认 type，你喂对就行。

---

## 第八段：【@TerminalScene】技术落地①·配置即内容，让 AI 填字段（3:30–3:50，20s）

- **[画面]** 调用 `@TerminalScene`。参数 `title`="只写配置：一个 comparison"，`language`="jsonc"，`code`=`{\n  "type": "comparison",\n  "title": "手工时序 vs 声明式配置",\n  "leftLabel": "手工时序",  "leftValue": "手工调整图层位置，改一处全身受累",\n  "rightLabel": "声明式配置", "rightValue": "改一行配置，程序自动重新对位"\n}`。
  - **[子镜头时间线]**：0s 终端标题入场 → 3s config 逐行打字入场 → 12s 高亮 `"type": "comparison"` → 16s 右侧注释浮出"TS 给每个字段定死格式，填错即编译报错"。
- **[口播]** 这是用 Vibe Coding 做视频最省心的一招：从不让 AI 发明新组件，只让它照现成组件填配置。比方要一张对比卡，我就说一句——左边手工时序、右边声明式配置。它吐出来就是这段：type 填 comparison，标题、左右两栏的标签和内容填齐，收工。全程没碰一行代码，只动了动嘴。记一句：别让 AI 造轮子，让它把现成的轮子装上。

---

## 第九段：【@SplitLayout + B 轨】技术落地①·造组件 ❌ vs 填数据 ✅（3:50–4:15，25s）

- **[B 轨]** `@VideoSlot`：`[B 轨占位替换提醒：请用户补充 IDE 录屏 — 左：AI 从零手写 ComparisonScene.tsx（反面 ❌）；右：只写一份 data 喂给现成 @ComparisonCard（正面 ✅）（clip_id=b-ide-config-fill）]`。
- **[A 轨兜底]**（B 轨缺失时使用）调用 `@SplitLayout`：
  - 左 `@TerminalScene`：`title`="❌ 从零手写组件"，`language`="tsx"，`code`=`// 违反"数据与视图分离"，容易写出不可复用组件\nexport const ComparisonScene = () => {\n  // 手写布局/样式/动画，无视现成 @ComparisonCard\n  return <div className="custom">...</div>;\n};`。
  - 右 `@TerminalScene`：`title`="✅ 只填数据，复用现成组件"，`language`="ts"，`code`=`const comparison = {\n  left:  { title: '手工时序',   value: '手工调整图层位置' },\n  right: { title: '声明式配置', value: '改一行配置程序重对位' },\n};\n// <ComparisonCard {...comparison} /> — TS 字段类型兜底`。
  - **[子镜头时间线]**：0s 分屏入场 → 4s 左侧红标 ❌ 代码淡入 → 11s 右侧绿标 ✅ 数据淡入 → 16s 高亮右侧数据结构（或 B 轨录屏切入）→ 22s 正确方放大强调。
- **[口播]** 为什么填数据最稳，看这组对照。左边反面——让 AI 给这一期从零手写新组件，既重复造轮子，又把换数据复用这个最大好处弄没了。右边才对——只产出一份数据，丢给现成组件去渲。关键在于 Remotion 用 TypeScript 把每个 type 的字段格式焊死，AI 填错、漏填，编译当场报红，它只能在画好的格子里填空。这就像考试发的是填空题，而不是让你交白卷自由发挥——这正是没基础也能让 AI 把活干住的原因。

---

## 第十段：【@TableScene】技术落地②·数字人选型（定位陪衬，让 AI 列形象与坑）（4:15–4:45，30s）

- **[画面]** 调用 `@TableScene`（数字人选型矩阵）。参数 `title`="数字人选型：定位陪衬，让 AI 列形象与坑"，`columns`=["形象方案", "适用场景", "局限与代价"]，三行=真人出镜 / 写实对口型 / 二次元(VRM)，`highlight_row`=2（高亮选定的 VRM 行）。
  - **[子镜头时间线]**：0s 表头淡入 → 5s 真人/写实/二次元三行依次 stagger 入场 → 18s 高亮 VRM 行"对约束选定" → 26s 浮出拍板理由脚注（不露脸/可编程复用/避恐怖谷）。
- **[口播]** 还要不要个出镜形象串场？这事也走选型那套——先定死位置：数字人只做陪衬，不是主角。再让 AI 把可选形象连坑一起摆出来：真人出镜最可信，但得露脸、没法编程复用；写实对口型容易掉进恐怖谷、可信度反而崩；二次元 3D 角色风格统一、可编程、渲一次到处用，还不踩恐怖谷。对着我的约束挑——不露脸、要批量复用、避恐怖谷，就选 3D 角色 VRMAvatar，定死陪衬、坚决不做对口型。记一句：形象也让 AI 列，你按约束拍板。

---

## 第十一段：【@ScreenshotScene】技术落地②·数字人落地取景（4:45–5:03，18s）

- **[画面]** 调用 `@ScreenshotScene`（VRMAvatar 取景预设示意 + 三处 callout）。参数 `title`="AI 落地：渲一次按场景取景，站得稳"，`callouts`=[{at:"取景", text:"整体渲一次，按场景裁角落/半身/全身"}, {at:"脚踩稳", text:"在大腿上把髋部摆动反向抵消，脚踩原地"}, {at:"边界", text:"坚决不做对口型数字人、不做 AI 假界面"}]。
  - **[子镜头时间线]**：0s 主持人截图淡入 → 5s callout"取景预设（角落/半身/全身）"浮出 → 11s callout"脚踩稳（髋部反向抵消）"浮出 → 16s callout"反对口型边界"浮出。
- **[口播]** 选定之后交给 AI 落地。整体渲一次，再按场景裁角落、半身、全身，不用每段重搭。之前待机只摆髋部，整条腿像钟摆一样甩；在大腿上把那点摆动反向抵消，脚就踩稳了。可信度始终靠真实录屏，不整 AI 假界面。

---

## 第十二段：【@OutroScene】结尾 CTA（5:03–5:18，15s）

- **[画面]** 调用 `@OutroScene`。参数 `headline`="整期三步：找技术路径 + 技术选型 + 技术落地"，`cta`="关注 · 下期 EP03 字幕匹配：Whisper 让字幕踩着话音跳"，`background`="gradient"。
  - **[子镜头时间线]**：0s 总结三步淡入 → 5s "没基础也能复制"落点强调 → 9s CTA 下期 EP03 打字机逐字显现 → 12s 关注脉冲（绿色）。
- **[口播]** 回头看就三步：找路，让 AI 把现成路线全摆出来；选型，让 AI 列坑、你对着约束拍板；落地，填配置、套现成组件、配个陪衬数字人，AI 自动出片。真正要练的从来不是写代码，而是把需求讲清楚、把坑看住、把活交给 AI——没基础也能照着抄。下期 EP03，用 Whisper 让字幕踩着话音、一个字一个字往外蹦。关注一下，别错过。

---

## 6. 自我检查清单

- ✅ B 站深度版完整产出（12 段，对齐 03 蓝图 12 个 scene_storyboard，约 1750 字、约 5 分 18 秒）
- ✅ **主线＝教人用 Vibe Coding**：开场结果先行 + 人设；每个技术段体现"人讲需求/看坑/定规则 + AI 写和填"；结尾落点"没基础也能复制"
- ✅ **去抽象腔**：全文未用"范式/换一套心智模型/帧即状态"等抽象标签，一律大白话
- ✅ **单期范围纪律**：流程即代码/角色（EP05/06）、字幕（EP03）、音频均未展开，仅结尾一句预告
- ✅ **必讲要点覆盖核对**：逐条对齐 `tutorial.final.md` 末尾清单，16/16 全覆盖（详见下方）
- ✅ 所有组件均为 `remotion-spec.md` 已有组件，无新组件工单（呼应"配置即内容、不造组件"）
- ✅ **A/B 轨兜底完整性**：S4/S9 含 B 轨 `@VideoSlot` 录屏指示 + A 轨 `@TableScene`/`@SplitLayout` 兜底
- ✅ 恶俗 AI 词汇检查：无"赋能、打造、革新、全方位、数字化浪潮"
- ✅ **防静止**：所有 >15s 段落均配 [子镜头时间线]，无静止画面超 15s

### 必讲要点覆盖核对

| # | 要点（tutorial.final.md 清单） | 脚本对应段落 | 状态 |
|---|------|------------|------|
| 1 | 一句话点题：本期用 Vibe Coding 解决"视频自动渲染" | 第一段 | ✅ |
| 2 | 关键认知钩子：AI 最强处理文本/代码 → 渲染用文本/代码/数据驱动 | 第一段 | ✅ |
| 3 | 人设（只点一次）：没基础、全程 Vibe Coding（讲需求/AI 写/人判断） | 第一段 | ✅ |
| 4 | 三步路线图：找技术路径 → 技术选型 → 技术落地 | 第一段 | ✅ |
| 5 | 让 AI 罗列多条路线（Remotion/Motion Canvas/Manim/MoviePy/PixiJS/FFmpeg） | 第二、三段 | ✅ |
| 6 | 点明共同内核：代码/数据描述画面 → 编译成帧 → 合成视频（只列不评） | 第二、三段 | ✅ |
| 7 | 逼 AI 给"不适用+已知坑"，人盯坑做减法 | 第四段 | ✅ |
| 8 | 回到自己约束（模板批量/AI 接手/跨期维护）→ 为什么 Remotion | 第五段 | ✅ |
| 9 | Remotion vs 复制粘贴 HTML 对照 + 代价（React 栈/BUSL），不渲染门槛 | 第六段 | ✅ |
| 10 | 引擎按 type 分发：配置 → Explainer 分发到组件 | 第七段 | ✅ |
| 11 | 组件清单：comparison/terminal_scene/screenshot_scene/charts/ConceptScene·SplitLayout | 第七段 | ✅ |
| 12 | 自有风格组件库：可在现成组件上扩品牌化模板，后续单独一期（一句带过） | 第七段 | ✅ |
| 13 | 配置即内容：让 AI 填字段别造组件、TS 类型兜底 | 第八、九段 | ✅ |
| 14 | 数字人选型与落地：定位陪衬 → 让 AI 列真人/写实/二次元(VRM) 形象与坑 → 对约束选定 VRM 3D 角色、不做对口型 → AI 落地（取景预设/脚站稳） | 第十、十一段 | ✅ |
| 15 | 三步法回顾 + "没编程基础也能复制" | 第十二段 | ✅ |
| 16 | 关注引导 + 下期预告（EP03 字幕匹配：Whisper 驱动 CaptionOverlay） | 第十二段 | ✅ |

---

## 7. 结构化校验块 (JSON Schema Block)

<!-- MANDATORY: 符合 shared/schemas/04-script.schema.json；本块是下游 TTS/组装/字幕/分发的唯一真源，approve 后冻结 -->
```json
{
  "title": "用 Vibe Coding 搭一套能自动出片的视频渲染引擎",
  "platform": "bilibili",
  "estimated_duration_seconds": 318,
  "total_word_count": 1750,
  "anti_hype_forbidden": ["多少行代码", "百倍", "千倍", "一键生成"],
  "sections": [
    {
      "id": "1",
      "section_ref": "开场钩子",
      "track": "A",
      "scene_template": "@IntroScene",
      "voice": "改一版视频，我只改配置里这一行字，回车，一秒钟新片自动出来。能这么干，靠的是一个判断：AI 最擅长的就是文本和代码，那就把整条视频也变成代码和数据来驱动——改数据，就等于改片。这一期，就用这招解决视频自动渲染。整套引擎我一行没手写，全靠大白话指挥 AI，这就叫 Vibe Coding：我没前后端基础，只负责说要什么、判断对不对，写和填交给 AI。三步走——找技术路径、做技术选型、技术落地出片。记一句：你说人话，AI 干脏活，没基础也能抄。",
      "visual_instructions": "@IntroScene：左改 JSON 配置右终端 npx remotion render 1秒出片 → IDE 展开 JSON 字段与渲染画面动态映射，体现“改配置即改片”声明式优势 → 粒子背景渐显 + 主副标题与三步路线图依次浮现",
      "duration_hint_seconds": 30,
      "visual_beats": [
        {"at_seconds": 0, "action": "[双画面] 左改 JSON 配置一行字，右终端 npx remotion render 进度条 1秒锁死、即刻出片"},
        {"at_seconds": 4, "action": "[代码结构演示] IDE 展开 JSON 配置，数据字段与渲染画面动态对应映射，体现“改配置即改片”的声明式优势"},
        {"at_seconds": 15, "action": "[主视觉] 粒子背景渐显，主标题弹性入场 spring_scale"},
        {"at_seconds": 20, "action": "[路线图] 副标题淡入，三步路线卡片依次浮现并锁定"}
      ]
    },
    {
      "id": "2",
      "section_ref": "找技术路径·让 AI 摆出多条路线（内核）",
      "track": "A",
      "scene_template": "@ConceptScene",
      "voice": "第一步，找路。别自己埋头啃文档，把选择题直接甩给 AI：想把视频写成代码、自动出片，有哪些现成路子？它一摆出来，内核就清楚了——这些路子全是一回事：用代码描述画面、编译成一帧帧、再合成视频，区别只在用什么语言、什么引擎。",
      "visual_instructions": "@ConceptScene：INPUT 描述画面 → COMPILE 编译成帧 → OUTPUT 合成视频，箭头连接",
      "duration_hint_seconds": 15,
      "visual_beats": [
        {"at_seconds": 0, "action": "eyebrow + 标题入场"},
        {"at_seconds": 3, "action": "三步骤卡片 stagger 入场"},
        {"at_seconds": 7, "action": "箭头连接 INPUT→COMPILE→OUTPUT"},
        {"at_seconds": 11, "action": "脉冲强调'内核一样'"}
      ]
    },
    {
      "id": "3",
      "section_ref": "找技术路径·六条技术路线",
      "track": "A",
      "scene_template": "@ConceptScene",
      "voice": "AI 一口气给我摆了六条路。第一条网页渲染，台柱子是 Remotion，拿 React 组件加 CSS 画画面，再用无头浏览器一帧帧截图，复杂排版最拿手。第二条 Motion Canvas，写函数描述动画时序，做代码演示很顺手。第三条 Manim，用 Python 描述几何和公式，数学可视化的神器。第四条 MoviePy，Python 直接抠像素加 FFmpeg，简单拼接够用。第五条 PixiJS 这类画布引擎，在 Canvas 上逐帧画，专治复杂粒子特效。第六条 FFmpeg 加脚本，命令行合成，批量转码、烧字幕特别猛。六个名字听着各不相同，扒到底都在干同一件事——把画面编译成帧。",
      "visual_instructions": "@ConceptScene：六张路线卡片（Remotion/Motion Canvas/Manim/MoviePy/PixiJS/FFmpeg），各配描述方式+适合场景",
      "duration_hint_seconds": 35,
      "visual_beats": [
        {"at_seconds": 0, "action": "标题入场"},
        {"at_seconds": 3, "action": "前三条卡片 stagger 入场"},
        {"at_seconds": 15, "action": "后三条卡片 stagger 入场"},
        {"at_seconds": 28, "action": "高亮 Remotion 卡"},
        {"at_seconds": 32, "action": "浮出'同一内核：编译成帧'"}
      ]
    },
    {
      "id": "4",
      "section_ref": "技术选型·严谨权衡技术局限与边界",
      "track": "A+B",
      "scene_template": "@TableScene",
      "voice": "第二步，选型，最容易翻车。直接问 AI 哪个好没用，它会把每个都夸一遍；真正值钱的，是看清每条路在哪掉链子。所以我逼它：每条路适合干啥、有哪些会咬人的坑，全抖出来，整理成这张表。Remotion 适合前端栈和复杂自适应排版，但它 Node 打包、无头浏览器渲染，组件最外层直接读 window 会在打包阶段崩；而且走 BUSL 商业授权，规模化要付费。Motion Canvas 生态小，模板得自己攒；Manim 排版弱、渲染慢；MoviePy 写自适应排版繁琐、多层吃内存；PixiJS 光算文字对齐就费劲；FFmpeg 命令晦涩、出问题难定位。坑摊开，再对着自己的需求做减法。记一句：让 AI 把信息铺平，拍板你自己来。",
      "visual_instructions": "B 轨：和 AI 深度分析技术路线局限的 IDE 录屏（b-ide-route-pitfalls）；A 轨兜底：@TableScene 六方案矩阵（适用场景/局限条件/关键约束），highlight_row=0、highlight_column=3",
      "duration_hint_seconds": 55,
      "b_track_required": true,
      "b_track_notes": "IDE 录屏：和 AI 追问每条技术路线的局限条件与关键约束",
      "visual_beats": [
        {"at_seconds": 0, "action": "表头淡入"},
        {"at_seconds": 5, "action": "六行依次 stagger 入场（至 25s）"},
        {"at_seconds": 28, "action": "高亮'关键约束'整列"},
        {"at_seconds": 38, "action": "B 轨 IDE 录屏切入"},
        {"at_seconds": 48, "action": "高亮 Remotion 行 + '对照约束做减法'标记"}
      ]
    },
    {
      "id": "5",
      "section_ref": "技术选型·回到约束为什么选 Remotion",
      "track": "A",
      "scene_template": "@ConceptScene",
      "voice": "坑看清了，回到我自己的约束拍板。三条死要求摆给 AI：一期一个固定模板、换批数据就能批量出几十期；让 AI 改内容还不容易出错；好多期下来还得好维护。三条一对照，Remotion 明显赢——组件和数据分开，改一处主题整个系列跟着变；每期只让 AI 填数据、套现成组件，最不容易翻车；出片就一行命令；网页那套生态随手就能用。说白了：它最听 AI 的话，也最经得起反复折腾。",
      "visual_instructions": "@ConceptScene：约束三条 → Remotion 胜出四点（模板/AI/CLI/网页生态），badge 决定性=数据分离",
      "duration_hint_seconds": 25,
      "visual_beats": [
        {"at_seconds": 0, "action": "eyebrow + 标题入场"},
        {"at_seconds": 3, "action": "三条约束卡 stagger 入场"},
        {"at_seconds": 12, "action": "Remotion 胜出四点浮现"},
        {"at_seconds": 20, "action": "badge='决定性'强调'模板换数据复用'"}
      ]
    },
    {
      "id": "6",
      "section_ref": "技术选型·Remotion vs 拼装 HTML 方案",
      "track": "A",
      "scene_template": "@SplitLayout",
      "voice": "有人觉得直接让 AI 拿 HTML 拼更省事，比一比就清楚差在哪——注意，两条路都是 AI 写代码，差的是工程化。复用上，Remotion 组件和数据分开，改一处全系列同步；裸 HTML 没有复用，AI 每期都得从头拼，改着改着就乱。约束上，Remotion 用 TypeScript 把字段类型管死，AI 只能老实填空；裸 HTML 没有强类型兜底，AI 一撒欢结构就跑偏。维护上，到第十期，Remotion 还能轻松扩，裸 HTML 早成了一团乱麻。代价也如实说：得吃 React 这套栈，还得认 BUSL 授权、规模化付费。但前端本来就让 AI 写、我把方向，正好把 Vibe Coding 的长处吃满。一句话：宁可前期立规矩，别等后期擦屁股。",
      "visual_instructions": "@SplitLayout(@ComparisonCard 左✅Remotion / 右❌拼装 HTML，各三条) + 底部代价条（React/BUSL）",
      "duration_hint_seconds": 25,
      "visual_beats": [
        {"at_seconds": 0, "action": "分屏 center-out 展开"},
        {"at_seconds": 5, "action": "左侧三条 stagger 入场"},
        {"at_seconds": 13, "action": "右侧三条 stagger 入场"},
        {"at_seconds": 20, "action": "底部代价条浮出"},
        {"at_seconds": 23, "action": "左侧微放大 1.03x"}
      ]
    },
    {
      "id": "7",
      "section_ref": "技术落地①·配置分发",
      "track": "A",
      "scene_template": "@ConceptScene",
      "voice": "选型定了，第三步落地。落地也不用你手写，就是陪 AI 把配置和组件对上号。仓库里这台引擎叫 remotion-composer：你写一份配置，说清这段画面长啥样、上面叠什么，主程序 Explainer 就按配置里的 type 字段，自动拎出对应组件去渲。type 写 comparison 出对比卡，terminal_scene 是合成终端、命令逐行打出来、不用真录屏，screenshot_scene 把截图叠上光标点击，还有图表、概念图、分屏，全是现成通用件，照着填就能用。想更有辨识度，还能让 AI 在这之上扩一套自有品牌组件库——那是更大的话题，以后单开一期。记一句：引擎认 type，你喂对就行。",
      "visual_instructions": "@ConceptScene：流向图 配置 → Explainer 按 type 分发 → 组件；type→组件清单 stagger，标注 terminal/screenshot 不用真录屏",
      "duration_hint_seconds": 25,
      "visual_beats": [
        {"at_seconds": 0, "action": "流向图标题入场"},
        {"at_seconds": 4, "action": "配置→Explainer→组件 箭头连通"},
        {"at_seconds": 12, "action": "type→组件清单 stagger 入场"},
        {"at_seconds": 20, "action": "高亮 terminal_scene/screenshot_scene 标'不用真录屏'"}
      ]
    },
    {
      "id": "8",
      "section_ref": "技术落地①·配置即内容",
      "track": "A",
      "scene_template": "@TerminalScene",
      "voice": "这是用 Vibe Coding 做视频最省心的一招：从不让 AI 发明新组件，只让它照现成组件填配置。比方要一张对比卡，我就说一句——左边手工时序、右边声明式配置。它吐出来就是这段：type 填 comparison，标题、左右两栏的标签和内容填齐，收工。全程没碰一行代码，只动了动嘴。记一句：别让 AI 造轮子，让它把现成的轮子装上。",
      "visual_instructions": "@TerminalScene：逐行打字展示一段 comparison 配置 JSON，高亮 type 字段 + 注释 TS 字段值兜底",
      "duration_hint_seconds": 20,
      "visual_beats": [
        {"at_seconds": 0, "action": "终端标题入场"},
        {"at_seconds": 3, "action": "config 逐行打字入场"},
        {"at_seconds": 12, "action": "高亮 \"type\": \"comparison\""},
        {"at_seconds": 16, "action": "注释浮出'TS 字段定死格式，填错即编译报错'"}
      ]
    },
    {
      "id": "9",
      "section_ref": "技术落地①·造组件 vs 填数据",
      "track": "A+B",
      "scene_template": "@SplitLayout",
      "voice": "为什么填数据最稳，看这组对照。左边反面——让 AI 给这一期从零手写新组件，既重复造轮子，又把换数据复用这个最大好处弄没了。右边才对——只产出一份数据，丢给现成组件去渲。关键在于 Remotion 用 TypeScript 把每个 type 的字段格式焊死，AI 填错、漏填，编译当场报红，它只能在画好的格子里填空。这就像考试发的是填空题，而不是让你交白卷自由发挥——这正是没基础也能让 AI 把活干住的原因。",
      "visual_instructions": "B 轨：IDE 录屏 从零手写❌ vs 只填数据✅（b-ide-config-fill）；A 轨兜底：@SplitLayout 左 @TerminalScene 手写组件代码 / 右 @TerminalScene data 对象",
      "duration_hint_seconds": 25,
      "b_track_required": true,
      "b_track_notes": "IDE 录屏：AI 从零手写组件 vs 只写 data 喂现成 @ComparisonCard",
      "visual_beats": [
        {"at_seconds": 0, "action": "分屏入场"},
        {"at_seconds": 4, "action": "左侧红标 ❌ 手写组件代码淡入"},
        {"at_seconds": 11, "action": "右侧绿标 ✅ data 数据淡入"},
        {"at_seconds": 16, "action": "高亮右侧数据结构（或 B 轨录屏切入）"},
        {"at_seconds": 22, "action": "正确方放大强调"}
      ]
    },
    {
      "id": "10",
      "section_ref": "技术落地②·数字人选型",
      "track": "A",
      "scene_template": "@TableScene",
      "voice": "还要不要个出镜形象串场？这事也走选型那套——先定死位置：数字人只做陪衬，不是主角。再让 AI 把可选形象连坑一起摆出来：真人出镜最可信，但得露脸、没法编程复用；写实对口型容易掉进恐怖谷、可信度反而崩；二次元 3D 角色风格统一、可编程、渲一次到处用，还不踩恐怖谷。对着我的约束挑——不露脸、要批量复用、避恐怖谷，就选 3D 角色 VRMAvatar，定死陪衬、坚决不做对口型。记一句：形象也让 AI 列，你按约束拍板。",
      "visual_instructions": "@TableScene：数字人选型矩阵（形象方案/适用场景/局限与代价），三行=真人出镜/写实对口型/二次元(VRM)，highlight_row=2，脚注=对约束选定 VRMAvatar、定死陪衬不做对口型",
      "duration_hint_seconds": 30,
      "visual_beats": [
        {"at_seconds": 0, "action": "表头淡入"},
        {"at_seconds": 5, "action": "真人/写实/二次元三行依次 stagger 入场"},
        {"at_seconds": 18, "action": "高亮 VRM 行'对约束选定'"},
        {"at_seconds": 26, "action": "浮出拍板理由脚注（不露脸/可编程复用/避恐怖谷）"}
      ]
    },
    {
      "id": "11",
      "section_ref": "技术落地②·数字人落地取景",
      "track": "A",
      "scene_template": "@ScreenshotScene",
      "voice": "选定之后交给 AI 落地。整体渲一次，再按场景裁角落、半身、全身，不用每段重搭。之前待机只摆髋部，整条腿像钟摆一样甩；在大腿上把那点摆动反向抵消，脚就踩稳了。可信度始终靠真实录屏，不整 AI 假界面。",
      "visual_instructions": "@ScreenshotScene：VRMAvatar 取景预设 + 三处 callout（取景·角落/半身/全身 · 脚踩稳·髋部反向抵消 · 反对口型边界）",
      "duration_hint_seconds": 18,
      "visual_beats": [
        {"at_seconds": 0, "action": "主持人截图淡入"},
        {"at_seconds": 5, "action": "callout '取景预设（角落/半身/全身）' 浮出"},
        {"at_seconds": 11, "action": "callout '脚踩稳（髋部反向抵消）' 浮出"},
        {"at_seconds": 16, "action": "callout '反对口型边界' 浮出"}
      ]
    },
    {
      "id": "12",
      "section_ref": "结尾 CTA",
      "track": "A",
      "scene_template": "@OutroScene",
      "voice": "回头看就三步：找路，让 AI 把现成路线全摆出来；选型，让 AI 列坑、你对着约束拍板；落地，填配置、套现成组件、配个陪衬数字人，AI 自动出片。真正要练的从来不是写代码，而是把需求讲清楚、把坑看住、把活交给 AI——没基础也能照着抄。下期 EP03，用 Whisper 让字幕踩着话音、一个字一个字往外蹦。关注一下，别错过。",
      "visual_instructions": "@OutroScene：三步法总结 + '没基础也能复制' + CTA 下期 EP03 字幕匹配，打字机 + 脉冲",
      "duration_hint_seconds": 15,
      "visual_beats": [
        {"at_seconds": 0, "action": "总结三步淡入"},
        {"at_seconds": 5, "action": "'没基础也能复制' 落点强调"},
        {"at_seconds": 9, "action": "CTA 下期 EP03 打字机逐字"},
        {"at_seconds": 12, "action": "关注脉冲（绿色）"}
      ]
    }
  ],
  "judgment_layer_coverage": {
    "highlights_pitfall": true,
    "explains_boundary": true,
    "acceptance_standard": true,
    "ai_limitations_exposed": true
  },
  "b_track_assets_required": [
    {
      "clip_id": "b-ide-route-pitfalls",
      "description": "IDE 录屏：和 AI 对话追问每条技术路线的'不适用 + 已知坑'，人盯着坑做减法",
      "zoom_crop_directives": [
        {"timestamp_start": "0:00", "timestamp_end": "0:10", "zoom_level": 1.0, "description": "全貌：对话提问'每个方案什么情况不适用、有哪些坑'"},
        {"timestamp_start": "0:10", "timestamp_end": "0:20", "zoom_level": 1.3, "description": "聚焦：AI 回答里的'坑'列表"}
      ]
    },
    {
      "clip_id": "b-ide-config-fill",
      "description": "IDE 录屏：从零手写组件（反面 ❌）对照只写一份 data 喂现成 @ComparisonCard（正面 ✅）",
      "zoom_crop_directives": [
        {"timestamp_start": "0:00", "timestamp_end": "0:15", "zoom_level": 1.0, "description": "全貌：打开配置文件，准备填字段"},
        {"timestamp_start": "0:15", "timestamp_end": "0:25", "zoom_level": 1.4, "description": "聚焦：comparison 的 left/right 字段 + TS 报错提示"}
      ]
    }
  ],
  "coverage_checklist": {
    "total": 16,
    "covered": 16,
    "items": [
      {"id": 1, "point": "一句话点题：本期用 Vibe Coding 解决视频自动渲染", "section": "1"},
      {"id": 2, "point": "关键认知钩子：AI 最强处理文本/代码 → 渲染用文本/代码/数据驱动", "section": "1"},
      {"id": 3, "point": "人设（只点一次）：没基础、全程 Vibe Coding", "section": "1"},
      {"id": 4, "point": "三步路线图：找技术路径 → 技术选型 → 技术落地", "section": "1"},
      {"id": 5, "point": "让 AI 罗列多条路线（六条）", "section": "2,3"},
      {"id": 6, "point": "点明共同内核：描述画面 → 编译成帧 → 合成视频（只列不评）", "section": "2,3"},
      {"id": 7, "point": "逼 AI 给不适用+已知坑，人盯坑做减法", "section": "4"},
      {"id": 8, "point": "回到自己约束 → 为什么 Remotion", "section": "5"},
      {"id": 9, "point": "Remotion vs 复制粘贴 HTML + 代价（React/BUSL）", "section": "6"},
      {"id": 10, "point": "引擎按 type 分发：配置 → Explainer → 组件", "section": "7"},
      {"id": 11, "point": "组件清单", "section": "7"},
      {"id": 12, "point": "自有风格组件库：现成组件上扩品牌化模板，后续单独一期", "section": "7"},
      {"id": 13, "point": "配置即内容、填字段别造组件、类型兜底", "section": "8,9"},
      {"id": 14, "point": "数字人选型与落地：定位陪衬→AI 列真人/写实/二次元(VRM)+坑→对约束选定 VRM、不做对口型→AI 落地（取景/脚稳）", "section": "10,11"},
      {"id": 15, "point": "三步法回顾 + 没基础也能复制", "section": "12"},
      {"id": 16, "point": "关注 + 下期预告（EP03 字幕匹配）", "section": "12"}
    ]
  }
}
```
