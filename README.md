# 定时连接检查

通过 GitHub Actions 定时查询账号状态，按剩余时间执行轻量请求。

## 运行规则

- 每小时 11 分、41 分查询一次五小时额度的剩余重置时间。
- 剩余时间大于或等于 4 小时 55 分钟时发送请求；小于该时间时结束本轮。
- 手动运行直接发送请求。
- 请求正常完成且收到非空回复，即认定成功并结束。
- 查询和发送分别计数：失败后间隔 30 秒，最多重试 3 次，即每项最多尝试 4 次。
- 查询最终失败时结束本轮；发送最终失败时结束本轮。

## 配置与维护

在 Actions 页面查看运行日志；通过工作流菜单的 Disable workflow 暂停，Enable workflow 恢复。GitHub 定时调度可能延迟。

实现及依赖版本见 [warm.yml](.github/workflows/warm.yml)。

## 许可证

基于 viseshb/claude-codex-warmer 改写，使用 MIT 许可证，详见 [LICENSE](LICENSE)。
