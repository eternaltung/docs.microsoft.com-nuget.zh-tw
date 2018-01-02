# [什麼是 NuGet？](What-is-NuGet.md)
# 快速入門
## [建立及發行套件](Quickstart/Create-and-Publish-a-Package.md)
## [使用套件](Quickstart/Use-a-Package.md)
# 輔助線
## [安裝 NuGet 用戶端工具](Guides/Install-NuGet.md)
## [建立 .NET Standard 套件 (Visual Studio 2017)](Guides/Create-NET-Standard-Packages-VS2017.md)
## [建立 .NET Standard 套件 (Visual Studio 2015)](Guides/Create-NET-Standard-Packages-VS2015.md)
## [建立 UWP 套件](Guides/Create-UWP-Packages.md)
## [建立 UWP 控制項作為 NuGet 套件](Guides/Create-UWP-Controls.md)
## [建立跨平台套件](Guides/Create-Cross-Platform-Packages.md)
## [查詢所有使用 API 的套件](Guides/api/query-for-all-published-packages.md)
# 建立套件
## [概觀和工作流程](Create-Packages/Overview-and-Workflow.md)
## [建立套件](Create-Packages/Creating-a-Package.md)
## [支援多個目標架構](Create-Packages/Supporting-Multiple-Target-Frameworks.md)
## [來源與組態檔轉換](Create-Packages/Source-and-Config-File-Transformations.md)
## [建立當地語系化的套件](Create-Packages/Creating-Localized-Packages.md)
## [發行前版本套件](Create-Packages/Prerelease-Packages.md)
## [原生套件](Create-Packages/Native-Packages.md)
## [符號套件](Create-Packages/Symbol-Packages.md)
## [套件](Create-Packages/Publish-a-package.md)
## [project.json 和 UWP](Create-Packages/project-json-and-UWP.md)
## [project.json 影響](Create-Packages/project-json-Impact.md)
# 取用套件
## [概觀和工作流程](Consume-Packages/Overview-and-Workflow.md)
## [尋找及選擇套件](Consume-Packages/Finding-and-Choosing-Packages.md)
## [套件還原](Consume-Packages/Package-Restore.md)
### [疑難排解](Consume-Packages/Package-restore-troubleshooting.md)
## [重新安裝和更新套件](Consume-Packages/Reinstalling-and-Updating-Packages.md)
## [套件和原始檔控制](Consume-Packages/Packages-and-Source-Control.md)
## [管理 NuGet 快取](Consume-Packages/Managing-the-NuGet-Cache.md)
## [設定 NuGet 行為](Consume-Packages/Configuring-NuGet-Behavior.md)
## [相依性解析](Consume-Packages/Dependency-Resolution.md)
## [專案檔中的套件參考](Consume-Packages/Package-References-in-Project-Files.md)
# 裝載套件
## [概觀](Hosting-Packages/Overview.md)
## [本機摘要](Hosting-Packages/Local-Feeds.md)
## [NuGet.Server](Hosting-Packages/NuGet-Server.md)
# 工具
## [nuget.exe CLI 參考](tools/nuget-exe-CLI-Reference.md)
### [add](Tools/cli-ref-add.md)
### [config](Tools/cli-ref-config.md) 
### [delete](Tools/cli-ref-delete.md) 
### [help 或 ?](Tools/cli-ref-help.md)
### [init](Tools/cli-ref-init.md) 
### [install](Tools/cli-ref-install.md)
### [list](Tools/cli-ref-list.md) 
### [locals](Tools/cli-ref-locals.md)
### [mirror](Tools/cli-ref-mirror.md)
### [pack](Tools/cli-ref-pack.md) 
### [push](Tools/cli-ref-push.md) 
### [restore](Tools/cli-ref-restore.md)
### [setapikey](Tools/cli-ref-setapikey.md)
### [sources](Tools/cli-ref-sources.md) 
### [spec](Tools/cli-ref-spec.md) 
### [update](Tools/cli-ref-update.md)
### [環境變數](Tools/cli-ref-environment-variables.md)
## [套件管理員 UI](Tools/Package-Manager-UI.md)
## [套件管理員主控台](Tools/Package-Manager-Console.md)
## [PowerShell 參考](Tools/PowerShell-Reference.md)
### [Add-BindingRedirect](Tools/ps-ref-add-bindingredirect.md)
### [Find-Package](Tools/ps-ref-find-package.md)
### [Get-Package](Tools/ps-ref-get-package.md)
### [Get-Project](Tools/ps-ref-get-project.md)
### [Install-Package](Tools/ps-ref-install-package.md)
### [Open-PackagePage](Tools/ps-ref-open-packagepage.md)
### [Sync-Package](Tools/ps-ref-sync-package.md)
### [Uninstall-Package](Tools/ps-ref-uninstall-package.md)
### [Update-Package](Tools/ps-ref-update-package.md)
## [dotnet 命令](Tools/dotnet-Commands.md)
# 參考資料
## [.nuspec](Schema/nuspec.md)
## [packages.config](Schema/packages-config.md)
## [project.json](Schema/project-json.md)
## [套件版本控制](reference/package-versioning.md)
## [Nuget.Config 檔案](Schema/nuget-config-file.md)
## [MSBuild 目標](Schema/msbuild-targets.md)
## [目標架構](Schema/Target-Frameworks.md)
## [分析器慣例](Schema/Analyzers-Conventions.md)
## [錯誤和警告](Reference/Errors-and-Warnings.md)
## [識別碼首碼保留項目](Reference/ID-Prefix-Reservation.md)
## [NuGet 用戶端 SDK](Reference/nuget-client-sdk.md)
## 擴充性
### [適用於 Visual Studio 2017 的 MyGet 認證提供者](Reference/extensibility/Nuget-Credential-Providers-for-Visual-Studio.md)
### [nuget.exe 認證提供者](Reference/extensibility/nuget-exe-Credential-Providers.md)
# API
## [概觀](API/overview.md)
## [服務索引](API/service-index.md)
## [推送與刪除](API/package-publish-resource.md)
## [搜尋](API/search-query-service-resource.md)
## [自動完成](API/search-autocomplete-service-resource.md)
## [套件中繼資料](API/registration-base-url-resource.md)
## [套件內容](API/package-base-address-resource.md)
## [檢舉不當使用 URL](API/report-abuse-resource.md)
## [目錄](API/catalog-resource.md)
## [nuget.org 通訊協定](API/nuget-protocols.md)
# Visual Studio 擴充性
## [Visual Studio 中的 NuGet API](Visual-Studio-Extensibility/NuGet-API-in-Visual-Studio.md)
## [專案系統支援](Visual-Studio-Extensibility/Project-System-Support.md)
## [Visual Studio 範本](Visual-Studio-Extensibility/Visual-Studio-Templates.md)
# 原則
## [NuGet 常見問題集](Policies/NuGet-FAQ.md)
## [監管](Policies/Governance.md)
## [生態系統](Policies/Ecosystem.md)
## [爭議解決方法](Policies/Dispute-Resolution.md)
## [刪除套件](Policies/Deleting-Packages.md)
# [GitHub 存放庫](https://github.com/NuGet)
# 版本資訊
## [已知問題](Release-Notes/Known-Issues.md)
## [NuGet 4.5 RTM](Release-Notes/NuGet-4.5-RTM.md)
## [NuGet 4.4 RTM](Release-Notes/NuGet-4.4-RTM.md)
## [NuGet 4.3 RTM](Release-Notes/NuGet-4.3-RTM.md)
## [NuGet 4.0 RTM](Release-Notes/NuGet-4.0-RTM.md)
## [NuGet 4.0 RC](Release-Notes/NuGet-4.0-RC.md)
## [NuGet 3.5 RTM](Release-Notes/NuGet-3.5-RTM.md)
## [NuGet 3.5 RC](Release-Notes/NuGet-3.5-RC.md)
## [NuGet 3.5 搶鮮版 2 (Beta 2)](Release-Notes/NuGet-3.5-Beta2.md)
## [NuGet 3.5 搶鮮版 (Beta)](Release-Notes/NuGet-3.5-Beta.md)
## [NuGet 3.4.4](Release-Notes/NuGet-3.4.4.md)
## [NuGet 3.4.3](Release-Notes/NuGet-3.4.3.md)
## [NuGet 3.4.2](Release-Notes/NuGet-3.4.2.md)
## [NuGet 3.4.1](Release-Notes/NuGet-3.4.1.md)
## [NuGet 3.4](Release-Notes/NuGet-3.4.md)
## [NuGet 3.4 RC](Release-Notes/NuGet-3.4-RC.md)
## [NuGet 3.3](Release-Notes/NuGet-3.3.md)
## [NuGet 3.2.1](Release-Notes/NuGet-3.2.1.md)
## [NuGet 3.2](Release-Notes/NuGet-3.2.md)
## [NuGet 3.2 RC](Release-Notes/NuGet-3.2-RC.md)
## [NuGet 3.1.1](Release-Notes/NuGet-3.1.1.md)
## [NuGet 3.1](Release-Notes/NuGet-3.1.md)
## [NuGet 3.0.0](Release-Notes/NuGet-3.0.0.md)
## [NuGet 3.0 RC2](Release-Notes/NuGet-3.0-RC2.md)
## [NuGet 3.0 RC](Release-Notes/NuGet-3.0-RC.md)
## [NuGet 3.0 搶鮮版 (Beta)](Release-Notes/NuGet-3.0-Beta.md)
## [NuGet 3.0 Preview](Release-Notes/NuGet-3.0-Preview.md)
## [NuGet 2.12](Release-Notes/NuGet-2.12.md)
## [NuGet 2.12 RC](Release-Notes/NuGet-2.12-RC.md)
## [NuGet 2.9 RC](Release-Notes/NuGet-2.9-RC.md)
## [NuGet 2.8.7](Release-Notes/NuGet-2.8.7.md)
## [NuGet 2.8.6](Release-Notes/NuGet-2.8.6.md)
## [NuGet 2.8.5](Release-Notes/NuGet-2.8.5.md)
## [NuGet 2.8.3](Release-Notes/NuGet-2.8.3.md)
## [NuGet 2.8.2](Release-Notes/NuGet-2.8.2.md)
## [NuGet 2.8.1](Release-Notes/NuGet-2.8.1.md)
## [NuGet 2.8](Release-Notes/NuGet-2.8.md)
## [NuGet 2.7.2](Release-Notes/NuGet-2.7.2.md)
## [NuGet 2.7.1](Release-Notes/NuGet-2.7.1.md)
## [NuGet 2.7](Release-Notes/NuGet-2.7.md)
## [NuGet 2.6.1-for-WebMatrix](Release-Notes/NuGet-2.6.1-for-WebMatrix.md)
## [NuGet 2.6](Release-Notes/NuGet-2.6.md)
## [NuGet 2.5](Release-Notes/NuGet-2.5.md)
## [NuGet 2.2.1](Release-Notes/NuGet-2.2.1.md)
## [NuGet 2.2](Release-Notes/NuGet-2.2.md)
## [NuGet 2.1](Release-Notes/NuGet-2.1.md)
## [NuGet 2.0](Release-Notes/NuGet-2.0.md)
## [NuGet 1.8](Release-Notes/NuGet-1.8.md)
## [NuGet 1.7](Release-Notes/NuGet-1.7.md)
## [NuGet 1.6](Release-Notes/NuGet-1.6.md)
## [NuGet 1.5](Release-Notes/NuGet-1.5.md)
## [NuGet 1.4](Release-Notes/NuGet-1.4.md)
## [NuGet 1.3](Release-Notes/NuGet-1.3.md)
## [NuGet 1.2](Release-Notes/NuGet-1.2.md)
## [NuGet 1.1](Release-Notes/NuGet-1.1.md)