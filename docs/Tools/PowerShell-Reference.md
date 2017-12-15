---
title: "NuGet PowerShell 參考 |Microsoft 文件"
author: kraigb
ms.author: kraigb
manager: ghogen
ms.date: 10/2/2017
ms.topic: reference
ms.prod: nuget
ms.technology: 
ms.assetid: cd08b869-44c6-480e-90f7-494a6d08e6d0
description: "Visual Studio 中的 NuGet 封裝管理員主控台中可用的 PowerShell 命令的完整參考。"
keywords: "NuGet 封裝管理員主控台中，NuGet Powershell 命令，NuGet Powershell 參考"
ms.reviewer:
- karann-msft
- unniravindranathan
ms.openlocfilehash: c0da5c88447784fdd49d824bbd03b11f73c22ebc
ms.sourcegitcommit: d0ba99bfe019b779b75731bafdca8a37e35ef0d9
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/14/2017
---
# <a name="powershell-reference"></a><span data-ttu-id="67019-104">PowerShell 參考</span><span class="sxs-lookup"><span data-stu-id="67019-104">PowerShell reference</span></span>

<span data-ttu-id="67019-105">Package Manager Console 提供下面所列的過特定的命令與 NuGet 互動的 Windows 上的 Visual Studio 中的 PowerShell 介面。</span><span class="sxs-lookup"><span data-stu-id="67019-105">The Package Manager Console provides a PowerShell interface within Visual Studio on Windows to interact with NuGet through the specific commands listed below.</span></span> <span data-ttu-id="67019-106">（[] 主控台不是目前可用在 Visual Studio for mac。）使用主控台的指引，請參閱[Package Manager Console](../tools/package-manager-console.md)主題。</span><span class="sxs-lookup"><span data-stu-id="67019-106">(The console is not presently available in Visual Studio for Mac.) For a guide to using the console, see the [Package Manager Console](../tools/package-manager-console.md) topic.</span></span>

> [!Tip]
> <span data-ttu-id="67019-107">所有的 PowerShell 命令僅與封裝耗用量。</span><span class="sxs-lookup"><span data-stu-id="67019-107">All PowerShell commands relate only to package consumption.</span></span> <span data-ttu-id="67019-108">建立和發佈封裝以外，封裝也可以是其他封裝的消費者，與沒有 PowerShell 命令。</span><span class="sxs-lookup"><span data-stu-id="67019-108">No PowerShell commands relate to creating and publishing packages except to the extent that a package can also be a consumer of other packages.</span></span>

> [!Important]
> <span data-ttu-id="67019-109">此處所列的命令專屬於在 Visual Studio 中，在 Package Manager Console 而不同[封裝管理模組命令](https://msdn.microsoft.com/powershell/reference/6/packagemanagement/packagemanagement)可在一般的 PowerShell 環境中。</span><span class="sxs-lookup"><span data-stu-id="67019-109">The commands listed here are specific to the Package Manager Console in Visual Studio, and differ from the [Package Management module commands](https://msdn.microsoft.com/powershell/reference/6/packagemanagement/packagemanagement) that are available in a general PowerShell environment.</span></span> <span data-ttu-id="67019-110">具體來說，每個環境有不適用於其他的命令，並在其特定的引數中，可能也不同命令具有相同名稱。</span><span class="sxs-lookup"><span data-stu-id="67019-110">Specifically, each environment has commands that are not available in the other, and commands with the same name may also differ in their specific arguments.</span></span> <span data-ttu-id="67019-111">當使用 Visual Studio 中的封裝管理主控台，指令及引數有本文所述套用。</span><span class="sxs-lookup"><span data-stu-id="67019-111">When using the Package Management Console in Visual Studio, the commands and arguments documented in this present topic apply.</span></span>

| <span data-ttu-id="67019-112">常見命令</span><span class="sxs-lookup"><span data-stu-id="67019-112">Common Commands</span></span> | <span data-ttu-id="67019-113">說明</span><span class="sxs-lookup"><span data-stu-id="67019-113">Description</span></span> | <span data-ttu-id="67019-114">NuGet 版本</span><span class="sxs-lookup"><span data-stu-id="67019-114">NuGet Version</span></span> |
| --- | --- | --- |
| [<span data-ttu-id="67019-115">安裝套件</span><span class="sxs-lookup"><span data-stu-id="67019-115">Install-Package</span></span>](ps-ref-install-package.md) | <span data-ttu-id="67019-116">在專案中安裝封裝及其相依性。</span><span class="sxs-lookup"><span data-stu-id="67019-116">Installs a package and its dependencies into the project.</span></span> | <span data-ttu-id="67019-117">全部</span><span class="sxs-lookup"><span data-stu-id="67019-117">All</span></span> |
| [<span data-ttu-id="67019-118">更新套件</span><span class="sxs-lookup"><span data-stu-id="67019-118">Update-Package</span></span>](ps-ref-update-package.md) | <span data-ttu-id="67019-119">更新封裝和其相依性或在專案中的所有封裝。</span><span class="sxs-lookup"><span data-stu-id="67019-119">Updates a package and its dependencies, or all packages in a project.</span></span> | <span data-ttu-id="67019-120">全部</span><span class="sxs-lookup"><span data-stu-id="67019-120">All</span></span> |
| [<span data-ttu-id="67019-121">尋找套件</span><span class="sxs-lookup"><span data-stu-id="67019-121">Find-Package</span></span>](ps-ref-find-package.md) | <span data-ttu-id="67019-122">搜尋使用的封裝識別碼或關鍵字的封裝來源。</span><span class="sxs-lookup"><span data-stu-id="67019-122">Searches a package source using a package ID or keywords.</span></span> | <span data-ttu-id="67019-123">3.0+</span><span class="sxs-lookup"><span data-stu-id="67019-123">3.0+</span></span> |
| [<span data-ttu-id="67019-124">取得封裝</span><span class="sxs-lookup"><span data-stu-id="67019-124">Get-Package</span></span>](ps-ref-get-package.md) | <span data-ttu-id="67019-125">擷取安裝在本機儲存機制中，封裝的清單，或列出可用的封裝，從套件來源。</span><span class="sxs-lookup"><span data-stu-id="67019-125">Retrieves the list of packages installed in the local repository, or lists packages available from a package source.</span></span> | <span data-ttu-id="67019-126">全部</span><span class="sxs-lookup"><span data-stu-id="67019-126">All</span></span> |

| <span data-ttu-id="67019-127">第二個命令</span><span class="sxs-lookup"><span data-stu-id="67019-127">Secondary Commands</span></span> | <span data-ttu-id="67019-128">說明</span><span class="sxs-lookup"><span data-stu-id="67019-128">Description</span></span> | <span data-ttu-id="67019-129">NuGet 版本</span><span class="sxs-lookup"><span data-stu-id="67019-129">NuGet Version</span></span> |
| --- | --- | --- |
| [<span data-ttu-id="67019-130">新增 BindingRedirect</span><span class="sxs-lookup"><span data-stu-id="67019-130">Add-BindingRedirect</span></span>](ps-ref-add-bindingredirect.md) | <span data-ttu-id="67019-131">檢查專案的輸出路徑內的所有組件，並將繫結重新導向至`app.config`或`web.config`在需要時。</span><span class="sxs-lookup"><span data-stu-id="67019-131">Examines all assemblies within the output path for a project and adds binding redirects to the `app.config` or `web.config` where necessary.</span></span> | <span data-ttu-id="67019-132">全部</span><span class="sxs-lookup"><span data-stu-id="67019-132">All</span></span> |
| [<span data-ttu-id="67019-133">取得專案</span><span class="sxs-lookup"><span data-stu-id="67019-133">Get-Project</span></span>](ps-ref-get-project.md) | <span data-ttu-id="67019-134">顯示預設值或指定的專案相關資訊。</span><span class="sxs-lookup"><span data-stu-id="67019-134">Displays information about the default or specified project.</span></span> | <span data-ttu-id="67019-135">3.0+</span><span class="sxs-lookup"><span data-stu-id="67019-135">3.0+</span></span> |
| [<span data-ttu-id="67019-136">開啟 PackagePage</span><span class="sxs-lookup"><span data-stu-id="67019-136">Open-PackagePage</span></span>](ps-ref-open-packagepage.md) | <span data-ttu-id="67019-137">啟動預設瀏覽器中使用專案、 授權或指定之封裝的報表濫用 URL。</span><span class="sxs-lookup"><span data-stu-id="67019-137">Launches the default browser with the project, license, or report abuse URL for the specified package.</span></span> | <span data-ttu-id="67019-138">在 3.0 + 已被取代</span><span class="sxs-lookup"><span data-stu-id="67019-138">Deprecated in 3.0+</span></span> |
| [<span data-ttu-id="67019-139">暫存器 TabExpansion</span><span class="sxs-lookup"><span data-stu-id="67019-139">Register-TabExpansion</span></span>](ps-ref-register-tabexpansion.md) | <span data-ttu-id="67019-140">登錄參數的命令，可讓您建立的常用的參數值的自訂擴充功能的 tab 鍵擴充。</span><span class="sxs-lookup"><span data-stu-id="67019-140">Registers a tab expansion for the parameters of a command, allowing you to create customized expansions for commonly-used parameter values.</span></span> | <span data-ttu-id="67019-141">全部</span><span class="sxs-lookup"><span data-stu-id="67019-141">All</span></span> |
| [<span data-ttu-id="67019-142">同步處理封裝</span><span class="sxs-lookup"><span data-stu-id="67019-142">Sync-Package</span></span>](ps-ref-sync-package.md) | <span data-ttu-id="67019-143">取得已安裝的版本封裝從指定專案和同步到解決方案中專案的其餘部分的版本。</span><span class="sxs-lookup"><span data-stu-id="67019-143">Get the version of installed package from specified project and syncs the version to the rest of projects in the solution.</span></span> | <span data-ttu-id="67019-144">3.0+</span><span class="sxs-lookup"><span data-stu-id="67019-144">3.0+</span></span> |
| [<span data-ttu-id="67019-145">解除安裝封裝</span><span class="sxs-lookup"><span data-stu-id="67019-145">Uninstall-Package</span></span>](ps-ref-uninstall-package.md) | <span data-ttu-id="67019-146">移除封裝在專案中，選擇性地移除其相依性。</span><span class="sxs-lookup"><span data-stu-id="67019-146">Removes a package from a project, optionally removing its dependencies.</span></span> | <span data-ttu-id="67019-147">全部</span><span class="sxs-lookup"><span data-stu-id="67019-147">All</span></span> |

<span data-ttu-id="67019-148">如需這些命令主控台內的任何完整的詳細說明，只要有問題的命令名稱與執行下列命令：</span><span class="sxs-lookup"><span data-stu-id="67019-148">For complete, detailed help on any of these commands within the console, just run the following with the command name in question:</span></span>

```ps
Get-Help <command> -full
```

<span data-ttu-id="67019-149">所有套件管理器主控台命令都支援下列[一般 PowerShell 參數](http://go.microsoft.com/fwlink/?LinkID=113216):</span><span class="sxs-lookup"><span data-stu-id="67019-149">All Package Manager Console commands support the following [common PowerShell parameters](http://go.microsoft.com/fwlink/?LinkID=113216):</span></span>

- <span data-ttu-id="67019-150">偵錯</span><span class="sxs-lookup"><span data-stu-id="67019-150">Debug</span></span>
- <span data-ttu-id="67019-151">ErrorAction</span><span class="sxs-lookup"><span data-stu-id="67019-151">ErrorAction</span></span>
- <span data-ttu-id="67019-152">ErrorVariable</span><span class="sxs-lookup"><span data-stu-id="67019-152">ErrorVariable</span></span>
- <span data-ttu-id="67019-153">OutBuffer</span><span class="sxs-lookup"><span data-stu-id="67019-153">OutBuffer</span></span>
- <span data-ttu-id="67019-154">OutVariable</span><span class="sxs-lookup"><span data-stu-id="67019-154">OutVariable</span></span>
- <span data-ttu-id="67019-155">PipelineVariable</span><span class="sxs-lookup"><span data-stu-id="67019-155">PipelineVariable</span></span>
- <span data-ttu-id="67019-156">詳細資訊</span><span class="sxs-lookup"><span data-stu-id="67019-156">Verbose</span></span>
- <span data-ttu-id="67019-157">WarningAction</span><span class="sxs-lookup"><span data-stu-id="67019-157">WarningAction</span></span>
- <span data-ttu-id="67019-158">WarningVariable</span><span class="sxs-lookup"><span data-stu-id="67019-158">WarningVariable</span></span>

<span data-ttu-id="67019-159">如需詳細資訊，請參閱[about_CommonParameters](http://go.microsoft.com/fwlink/?LinkID=113216) PowerShell 文件中。</span><span class="sxs-lookup"><span data-stu-id="67019-159">For details, refer to [about_CommonParameters](http://go.microsoft.com/fwlink/?LinkID=113216) in the PowerShell documentation.</span></span>