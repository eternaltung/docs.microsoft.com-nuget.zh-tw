---
title: NuGet 2.2 版本資訊
description: 包括已知的問題、 錯誤修正、 新增的功能，以及 Dcr NuGet 2.2 版本資訊。
author: karann-msft
ms.author: karann
manager: unnir
ms.date: 11/11/2016
ms.topic: conceptual
ms.openlocfilehash: 21f212de53da5faf1ec0762f97a840968b615b19
ms.sourcegitcommit: 3eab9c4dd41ea7ccd2c28bb5ab16f6fbbec13708
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/26/2018
ms.locfileid: "31822626"
---
# <a name="nuget-22-release-notes"></a>NuGet 2.2 版本資訊

[NuGet 2.1 版本資訊](../release-notes/nuget-2.1.md) | [NuGet 2.2.1 版本資訊](../release-notes/nuget-2.2.1.md)

NuGet 2.2 已於 2012 年 12 月 12 日發行。

## <a name="visual-studio-quick-launch"></a>Visual Studio 快速啟動
其中一個 Visual Studio 2012 中已加入的新功能是[快速啟動對話方塊](/visualstudio/ide/reference/quick-launch-environment-options-dialog-box)。 NuGet 2.2 擴充這個對話方塊中，讓它可以在 快速啟動中輸入搜尋詞彙以初始化 封裝管理員 對話方塊。 搜尋符合 'jquery' 的 NuGet 封裝在結果中，輸入 'jquery' 在快速啟動中，現在包含，例如的選項。

![在 Visual Studio 快速啟動中的 NuGet](./media/quick-launch.png)

選取此選項將會啟動的標準 NuGet 封裝管理員搜尋體驗的詞彙 'jquery'。

![預先填入的 NuGet 封裝管理員 對話方塊](./media/pkg-mgr-search-from-quick-launch.png)

## <a name="specify-entire-folder-for-package-contents"></a>指定封裝內容的整個資料夾
NuGet 2.2 現在可讓您指定在整個資料夾`<file>`元素`.nuspec`檔案以包含所有該資料夾的內容。 例如，下列會使所有指令碼封裝的指令碼資料夾中要加入至 contents\scripts 資料夾，當封裝安裝到專案。

```xml
<file src="scripts\" target="content\scripts"/>
```

**更新 6/24/16： 安裝封裝時，會忽略空的資料夾 [內容] 資料夾中。**

## <a name="known-issues"></a>已知問題

### <a name="package-installation-fails-for-f-projects-when-using-the-package-manager-console"></a>使用封裝管理員主控台時，套件安裝失敗的 F # 專案
將 NuGet 封裝安裝到使用封裝管理員主控台的 F # 專案時，會擲回 InvalidOperationException。 目前正積極努力與 F # 小組解決問題，但在此同時，因應措施是將 NuGet 封裝安裝到 F # 專案中透過 NuGet 的封裝管理員 對話方塊，而不是主控台。 [詳細的資訊已 CodePlex 上提供](http://nuget.codeplex.com/workitem/2873)。


## <a name="bug-fixes"></a>Bug 修正
NuGet 2.2 包含括許多錯誤修正。 如需完整的工作清單項目中修正 NuGet 2.2，請檢視[此版本的 NuGet Issue Tracker](http://nuget.codeplex.com/workitem/list/advanced?keyword=&status=Closed&type=All&priority=All&release=NuGet%202.2&assignedTo=All&component=All&sortField=LastUpdatedDate&sortDirection=Descending&page=0)。
