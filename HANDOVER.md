# 项目交接说明（给接手的 AI / 未来的我）

> 这是赵梓延的个人主页项目。任何改动前请先读完本文件，尤其是「口径纪律」一节。
> 本文件随仓库公开，请勿写入任何敏感信息（密码、token、私人联系方式）。

## 1. 项目是什么

- 用途：腾讯转正答辩 + 求职用的个人主页，中英双版本。
- 形态：单文件 `index.html`（内联 CSS/JS，无构建步骤）+ `assets/` 图片。
- 事实基准：**以本人简历为准**，不编造数据、不夸大。
- 文风：小红书式低调写实——只陈述事实与结果，不自夸、不用形容词堆砌。

## 2. 仓库与线上地址

| 版本 | 仓库 | 线上地址 |
|---|---|---|
| 中文 | https://github.com/chaojixiaozhao/portfolio | https://chaojixiaozhao.github.io/portfolio/ |
| 英文 | https://github.com/chaojixiaozhao/portfolio-en | https://chaojixiaozhao.github.io/portfolio-en/ |

- 两个仓库内容独立，改一个不等同改另一个，**中英需同步改动**。
- 地址必须带 `/portfolio/`（或 `/portfolio-en/`）后缀；裸 `chaojixiaozhao.github.io` 是 404。
- 推送后约 40–60 秒自动生效，链接永久不变。

## 3. 口径纪律（红线，违反即回滚）

1. **禁止出现「预计年消耗 60–80 万」**。单客户写"百万级"，合计写"200 万+"。
2. **禁止复活旧表述**「跑不动」——已全部替换为四步法叙事。
3. **禁止加注来源括号**（如"（来源：小红书）"）——全站已清理，不要再引入。
4. 商机口径固定为「独立拓展跟进有效商机 25+」，触达关键人「15+」。
5. 能力雷达分数已定稿：learn 95 / resi 94 / eng 93 / ai 70 / data 65 / tech 48；**改分数必须本人明确要求**。
6. 简历上没有的成绩不要新增；拿不准就问本人，不要猜。

## 4. 四步成单法（「我怎么做事」区块的结构，勿打乱）

01 看市场 READ THE MARKET → 02 验数据 VALIDATE WITH DATA → 03 做触达 REACH & CONNECT → 04 供价值 DELIVER VALUE & CLOSE。
主线案例是腾讯云 AIGC 影视客户（AI 电影赛道判断 → 行业报告验证 Token 消耗 → 北京 AIGC 电影节晚宴结识 + 独立登门 → 跨模型统一账单痛点成单）。

## 5. 改动流程

1. 改 `index.html`（英文版改 `portfolio-en/index.html`）。
2. 校验 JS：把每个 `<script>` 块内容丢进 `new Function()` 跑一遍，语法必须全通过。
3. `git add -A && git commit && git push`。
4. 若在本机：`gh auth setup-git` 后再 push（否则报 "could not read Username"）。
5. 轮询 `curl` 线上页面确认新内容已出现；**用户看到旧内容是浏览器缓存，让他 Cmd+Shift+R 强刷**，不要据此以为没生效。

## 6. 已知技术坑

- **scrollspy 会重写导航 class**：`links[i].className=...` 会清掉语言按钮的 `langbtn` 类，必须 `if(links[i].classList.contains("langbtn"))continue;`。
- **JS 单引号字符串内禁止英文撇号**：写 "I am" 不要写 "I'm"。
- **翻译整站时不要整文件重写**：按行号映射替换（提取含 CJK 的行 → 分批译文 → 按行号替换），否则易破坏 CSS/JS。
- **git push 不接受 GitHub 账号密码**（2021 起废弃），需 PAT（Contents: Read and write）或 `gh auth login`。
- 图片 `portrait-baked.png` 是带 alpha 的 PNG，由页面实时渐变透出蓝色，**不要把蓝色背景烤进图片**。
- 移动端断点：880px、640px；改布局后需确认无横向溢出。

## 7. 上线前自检清单

- [ ] 两个 `<script>` 均通过 `new Function` 校验
- [ ] 线上页面与关键图片资源均返回 200
- [ ] 无横向溢出（桌面 + 手机宽度）
- [ ] 中文版无英文残留、英文版 CJK 残留为 0
- [ ] 未触碰第 3 节任何红线
