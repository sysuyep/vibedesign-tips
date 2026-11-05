# 仓库结构与新一期的加入流程

本文写给负责盯更新的 X Trends 机器人，也方便人工补录时对照。

## 目录结构

```
README.md          总目录，最新一期在最上面
tips.json          机器可读的总索引
ARCHITECTURE.md    本文
tips/
  NNN-英文短名/
    README.md      单期页面：基本信息、作者讲解、完整提示词、效果
    prompt.md      只放提示词原文
    media/
      poster.jpg   效果视频封面
      demo.mp4     效果视频（有视频时才有）
```

- `NNN` 是三位期号，比如 `012`。英文短名用小写字母和连字符，概括这一期讲什么，比如 `animation-easing-rhythm`。
- 文件里不放表情符号。标题里的星星等符号去掉。
- 时间一律写北京时间。

## tips.json 每一项的字段

| 字段 | 含义 |
| --- | --- |
| number | 期号，整数 |
| slug | 英文短名 |
| folder | 这一期的文件夹路径 |
| title | 中文标题，去掉表情符号 |
| date | 发布日期，北京时间，YYYY-MM-DD |
| published_at | 发布时间，带 +08:00 |
| source_url | 主帖链接 |
| post_id | 主帖 id |
| prompt_ids | 提示词所在的帖子 id。提示词在主帖里时就是主帖 id |
| prompt_location | `main_post`（主帖正文）或 `author_reply`（作者自己的回复） |
| prompt_chars | 提示词字符数，用来粗查是否被截断 |
| media | 媒体文件列表：封面、视频，各带原始链接 |

## 新一期怎么加进来

1. **发现新一期**
   - 每天查一次 @Kubai087（用户 id 703796597335822336）最近的原创帖，不含回复和转帖。
   - 正文含《999 个小技巧》且带三位期号（如「012」），并且期号比 tips.json 里最大的大，就是新一期。
   - 同一期如果作者删帖重发或有两个版本，用较晚、内容较完整的那条。

2. **取正文**
   - 用 get_posts_by_ids 取主帖，带上 note_tweet 字段。长文在 note_tweet.text 里，普通 text 会被截断。

3. **找提示词**
   - 先看主帖正文：如果「可以直接抄」后面就是英文提示词，提示词就在主帖里。
   - 否则用 search_posts_all 查 `conversation_id:<主帖 id> from:Kubai087`，找以 `Prompt` 开头的回复（可能分成 Prompt (1)、Prompt (2)）。
   - 每条回复都要用 note_tweet.text 取全文。分成几段的按顺序拼起来。
   - 作者发帖后一段时间才补提示词的情况也有，没找到就隔几小时再查一次。

4. **取效果**
   - 主帖的视频：下载约 720p、2Mbps 左右的 mp4 存为 `media/demo.mp4`，不要下 2160p 的原画。
   - 封面图存为 `media/poster.jpg`。是图片帖的，按顺序存为 `media/1.jpg`、`media/2.jpg`。

5. **写文件**
   - 新建 `tips/NNN-英文短名/`，写 README.md、prompt.md、media。
   - 单期 README.md 的顺序：标题、基本信息表、作者讲了什么、Prompt、效果。
   - 在 tips.json 末尾追加一项，在根目录 README.md 目录表的最上面加一行，并更新总期数。

6. **检查**
   - prompt.md 的字数和原帖一致，结尾是完整句子。
   - 视频能播放，大小在几 MB 以内。
   - 链接都能打开。

7. **提交与通知**
   - 提交信息写成 `add 012 标题`，推送到私有仓库 sysuyep/vibedesign-tips。
   - 给用户推一条消息：期号、标题、一句话讲什么、提示词开头几行、原帖链接、仓库里这一期的链接。

## 来源说明

内容版权归 @Kubai087 所有，仓库只作个人学习存档，保持私有，每一期都保留原帖链接。
