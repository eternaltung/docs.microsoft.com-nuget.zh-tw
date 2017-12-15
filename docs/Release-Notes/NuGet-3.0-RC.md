---
title: "NuGet 3.0 RC 版本資訊 |Microsoft 文件"
author: karann-msft
ms.author: karann-msft
manager: ghogen
ms.date: 11/11/2016
ms.topic: article
ms.prod: nuget
ms.technology: 
ms.assetid: cd0c102f-bc33-4aa2-a921-61fa21d42b28
description: "包括已知的問題、 錯誤修正、 新增的功能，以及 Dcr NuGet 3.0 RC 版本資訊。"
keywords: "NuGet 3.0 RC 版本資訊、 錯誤修正的已知問題，已新增的功能，Dcr"
ms.reviewer:
- karann-msft
- unniravindranathan
ms.openlocfilehash: 5d0eeae479617bc30901b599251628f72950cc67
ms.sourcegitcommit: d0ba99bfe019b779b75731bafdca8a37e35ef0d9
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/14/2017
---
# <a name="nuget-30-rc-release-notes"></a><span data-ttu-id="bb200-104">NuGet 3.0 RC 版本資訊</span><span class="sxs-lookup"><span data-stu-id="bb200-104">NuGet 3.0 RC Release Notes</span></span>

<span data-ttu-id="bb200-105">[NuGet 3.0 Beta 版本資訊](../release-notes/nuget-3.0-beta.md) | [NuGet 3.0 RC2 版本資訊](../release-notes/nuget-3.0-RC2.md)</span><span class="sxs-lookup"><span data-stu-id="bb200-105">[NuGet 3.0 Beta Release Notes](../release-notes/nuget-3.0-beta.md) | [NuGet 3.0 RC2 Release Notes](../release-notes/nuget-3.0-RC2.md)</span></span>

<span data-ttu-id="bb200-106">NuGet 3.0 RC 於 2015 年 4 月 29 日發行 Visual Studio 2015 RC 版本。</span><span class="sxs-lookup"><span data-stu-id="bb200-106">NuGet 3.0 RC was released on April 29, 2015 with the Visual Studio 2015 RC release.</span></span> <span data-ttu-id="bb200-107">此版本有一些重要的 bug 修正、 效能增強功能和更新以支援新的架構。</span><span class="sxs-lookup"><span data-stu-id="bb200-107">This release has a number of important bug fixes, performance improvements and updates to support the new frameworks.</span></span>  <span data-ttu-id="bb200-108">它只適用於 Visual Studio 2015。</span><span class="sxs-lookup"><span data-stu-id="bb200-108">It is only available for Visual Studio 2015.</span></span>

### <a name="continued-focus-on-performance"></a><span data-ttu-id="bb200-109">繼續對效能的焦點</span><span class="sxs-lookup"><span data-stu-id="bb200-109">Continued Focus on Performance</span></span>

<span data-ttu-id="bb200-110">穩定性和效能的 NuGet 查詢繼續我們會將焦點放在一個熱門主題。</span><span class="sxs-lookup"><span data-stu-id="bb200-110">Stability and performance of NuGet queries continue to be a hot topic that we are focusing on.</span></span>  <span data-ttu-id="bb200-111">在此版本中，您應該開始查看非常快速搜尋作業中的 NuGet UI 和網站。</span><span class="sxs-lookup"><span data-stu-id="bb200-111">With this release, you should start to see very quick search operations in the NuGet UI and website.</span></span>  <span data-ttu-id="bb200-112">我們正在監視的服務，並使用服務，以便我們可以繼續微調這些作業。</span><span class="sxs-lookup"><span data-stu-id="bb200-112">We're monitoring the service and how you use the service so that we can continue to tune these operations.</span></span>

## <a name="significant-issues-resolved"></a><span data-ttu-id="bb200-113">已解決的重要問題</span><span class="sxs-lookup"><span data-stu-id="bb200-113">Significant Issues Resolved</span></span>

<span data-ttu-id="bb200-114">穩定 NuGet 用戶端，以便我們可以解決的許多問題做為此版本的一部分。</span><span class="sxs-lookup"><span data-stu-id="bb200-114">In order to stabilize the NuGet clients, we resolved many issues as part of this release.</span></span>  <span data-ttu-id="bb200-115">以下是只有一些更重要的是已解決的問題的簡短清單：</span><span class="sxs-lookup"><span data-stu-id="bb200-115">Here is just a brief list of some of the more important issues resolved:</span></span>

* <span data-ttu-id="bb200-116">ASP.NET 5 命名 K framework 的一部分，framework moniker 已更新來處理 dnx 和 dnxcore[連結](https://github.com/NuGet/Home/issues/215)</span><span class="sxs-lookup"><span data-stu-id="bb200-116">As part of the rename of the K framework for ASP.NET 5, framework monikers have been updated to handle dnx and dnxcore [link](https://github.com/NuGet/Home/issues/215)</span></span>
* <span data-ttu-id="bb200-117">加入說明 」 文件從 Visual Studio UI 中的連結[連結](https://github.com/NuGet/Home/issues/232)</span><span class="sxs-lookup"><span data-stu-id="bb200-117">Added help documentation from links in the Visual Studio UI [link](https://github.com/NuGet/Home/issues/232)</span></span>
* <span data-ttu-id="bb200-118">中的複雜參照的進一步處理`.nuspec`逗點分隔的 framework 參考與[連結](https://github.com/NuGet/Home/issues/276)</span><span class="sxs-lookup"><span data-stu-id="bb200-118">Better handling of complex references in `.nuspec` with comma-delimited framework references [link](https://github.com/NuGet/Home/issues/276)</span></span>
* <span data-ttu-id="bb200-119">修正日文的文化特性的支援[連結](https://github.com/NuGet/Home/issues/253)</span><span class="sxs-lookup"><span data-stu-id="bb200-119">Fixed support for Japanese cultures [link](https://github.com/NuGet/Home/issues/253)</span></span>
* <span data-ttu-id="bb200-120">更新的用戶端，以允許 ASP.NET 5 專案以使用新的 v3 端點[連結](https://github.com/NuGet/Home/issues/219)</span><span class="sxs-lookup"><span data-stu-id="bb200-120">Updated client to allow ASP.NET 5 projects to use new v3 endpoints [link](https://github.com/NuGet/Home/issues/219)</span></span>
* <span data-ttu-id="bb200-121">已更新為更好的控制代碼封裝與原始檔控制 資料夾[連結](https://github.com/NuGet/Home/issues/56)</span><span class="sxs-lookup"><span data-stu-id="bb200-121">Updated to better handle packages folder with source control [link](https://github.com/NuGet/Home/issues/56)</span></span>
* <span data-ttu-id="bb200-122">固定的附屬項目封裝的支援[連結](https://github.com/NuGet/Home/issues/17)</span><span class="sxs-lookup"><span data-stu-id="bb200-122">Fixed support for satellite packages [link](https://github.com/NuGet/Home/issues/17)</span></span>
* <span data-ttu-id="bb200-123">已更正的架構特定的內容檔案支援[連結](https://github.com/NuGet/Home/issues/18)</span><span class="sxs-lookup"><span data-stu-id="bb200-123">Corrected support for framework-specific content files [link](https://github.com/NuGet/Home/issues/18)</span></span>

## <a name="github-presence-overhaul"></a><span data-ttu-id="bb200-124">GitHub 存在重</span><span class="sxs-lookup"><span data-stu-id="bb200-124">GitHub presence overhaul</span></span>

<span data-ttu-id="bb200-125">我們所做一些變更，以便我們[來源 GitHub 上的程式碼儲存機制](http://github.com/nuget/home)。</span><span class="sxs-lookup"><span data-stu-id="bb200-125">We've made some changes to our [source code repositories on GitHub](http://github.com/nuget/home).</span></span>  <span data-ttu-id="bb200-126">如果 Visual Studio 用戶端、 Powershell 命令，或命令列中有任何問題可執行檔可以記錄這些問題，並監視其進度上我們[首頁 GitHub 儲存機制的問題清單](http://github.com/nuget/home/issues)。</span><span class="sxs-lookup"><span data-stu-id="bb200-126">If you have any issues with the NuGet Visual Studio client, the Powershell commands, or the command-line executable you can log those issues and monitor their progress on our [GitHub Home repository issues list](http://github.com/nuget/home/issues).</span></span>  <span data-ttu-id="bb200-127">我們在圖庫中的問題追蹤我們[GitHub NuGetGallery 儲存機制](http://github.com/nuget/NuGetGallery/issues)。</span><span class="sxs-lookup"><span data-stu-id="bb200-127">We are tracking issues for the gallery in our [GitHub NuGetGallery repository](http://github.com/nuget/NuGetGallery/issues).</span></span>


## <a name="stay-tuned"></a><span data-ttu-id="bb200-128">敬請期待</span><span class="sxs-lookup"><span data-stu-id="bb200-128">Stay Tuned</span></span>

<span data-ttu-id="bb200-129">請持續監控[我們的部落格](http://blog.nuget.org)詳細進度及針對 NuGet 3.0 公告 ！</span><span class="sxs-lookup"><span data-stu-id="bb200-129">Please keep an eye on [our blog](http://blog.nuget.org) for more progress and announcements for NuGet 3.0!</span></span>