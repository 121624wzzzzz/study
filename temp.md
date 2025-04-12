以下是完善后的 **Git 分支命名规范表格**，补充了更多常见的分支类型和使用场景，并优化了格式：

---

### **Git 分支命名规范（语义化分支）**
| **类型**       | **格式**                     | **示例**                     | **适用场景**                                                                 |
|----------------|-----------------------------|-----------------------------|-----------------------------------------------------------------------------|
| **功能开发**   | `feat/<功能描述>`           | `feat/user-auth`            | 新功能开发（如登录模块、支付接口）                                           |
| **问题修复**   | `fix/<问题描述>`            | `fix/login-error`           | 修复 Bug（如接口报错、样式问题）                                             |
| **文档更新**   | `docs/<修改范围>`           | `docs/quick-start`          | 更新 README、API 文档、注释等                                                |
| **代码重构**   | `refactor/<模块名>`         | `refactor/payment-service`  | 代码重构（不改变功能逻辑）                                                   |
| **测试相关**   | `test/<测试目标>`           | `test/user-regression`      | 添加单元测试、E2E 测试                                                       |
| **样式调整**   | `style/<修改范围>`          | `style/dark-mode`           | CSS/UI 样式调整（不涉及功能逻辑）                                            |
| **依赖更新**   | `chore/<依赖名>`            | `chore/update-react`        | 升级依赖版本、修改构建配置（如 webpack、CI）                                  |
| **性能优化**   | `perf/<优化目标>`           | `perf/api-response`         | 性能优化（如缓存数据库查询优化）                                       |
| **实验性功能** | `experiment/<功能名>`       | `experiment/ai-chat`        | 临时性实验分支（可能不会合并到主分支）                                       |
| **发布准备**   | `release/<版本号>`          | `release/v1.2.0`            | 发布前的最终测试和准备（禁止直接开发代码）                                    |
| **紧急热修复** | `hotfix/<问题描述>`         | `hotfix/security-patch`     | 生产环境紧急修复（从 `main` 分支创建，修复后直接合并回 `main` 和 `develop`） |

---

### **补充说明**
1. ****：
   • 使用 **小写字母** 和 `-` 连接单词（如 `user-auth` 而非 `userAuth`）。
   • 避免使用特殊字符（如 `*`, `_`, `#`）。
   • 保持名称简洁但明确（`fix/button-color` 优于 `fix/ui`）。

2. **分支生命周期**：
   • 功能分支合并后应删除（`git branch -d feat/xxx`）。
   • 长期分支（如 `develop`、`release`）需团队协商维护。

3. **协作场景**：
   ```bash
   # 创建分支并推送到远程
   git checkout -b feat/user-profile
   git push -u origin feat/user-profile  # -u 建立追踪关系
   ```

4. **与提交信息联动**：
   • 分支名和提交信息（commit message）应保持一致：
     ```bash
     git commit -m "feat: add user profile page"
     # 对应分支名：feat/user-profile
     ```

---

### **为什么需要规范？**
• **清晰分类**：通过前缀快速识别分支用途。
• **自动化支持**：CI/CD 工具可根据分支名触发不同流程（如 `feat/` 分支跑单元测试，`release/` 分支部署到生产环境）。
• **历史追溯**：`git log --graph` 时可直观看到变更脉络。

如果需要进一步扩展（如企业内部分支策略），可以结合 GitFlow 或 Trunk-Based Development 模型。