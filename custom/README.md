# 自定义播放列表（Custom Playlists）

由贾维斯于 2026-10-20 实测生成：对 iptv-org 官方语言播放列表中的全部频道逐条
发起真实请求探测（HTTP 状态 + 内容验证），再对存活频道用 ffprobe 做真实解码验证。

## 文件

| 文件 | 内容 |
|---|---|
| `chinese.m3u` | 中文频道（已验证频道在前，未验证频道带 `(unverified)` 后缀） |
| `english.m3u` | 英语频道（同上） |

## 使用方法（IPTVnator）

1. 打开 IPTVnator → 添加播放列表（Playlists）→ 使用远程 URL（Remote URL）
2. 粘贴地址：
   - 中文：`https://raw.githubusercontent.com/summitdoudou/iptv/master/custom/chinese.m3u`
   - 英语：`https://raw.githubusercontent.com/summitdoudou/iptv/master/custom/english.m3u`
3. 频道名/台标/分组自动加载（列表含 `tvg-id` 与 `tvg-logo`）
4. 可选：加一个 XMLTV 的 EPG 源，IPTVnator 按 `tvg-id` 自动匹配节目单

其他支持 M3U 的播放器（VLC 等）也直接打开上面的 URL 即可。

## 说明与注意

- 带 `(unverified)` 的频道：HTTP 可达但 ffprobe 未解出视频，VLC 通常仍可播放，
  个别可能打不开，切换频道即可。
- 部分频道带 `[Geo-blocked]` 或 `[Not 24/7]` 标记：受地域限制或非 24 小时播出。
- 央视等频道的入口 URL 会 302 跳转到带时效 token 的地址，播放器会自动跟随
  跳转，属正常现象。
- 免费公共源稳定性有限，若某天失效可重新跑探测更新本目录。
