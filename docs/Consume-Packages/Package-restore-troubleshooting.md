---
title: "針對 Visual Studio 中的 NuGet 套件還原進行疑難排解 | Microsoft Docs"
author: kraigb
ms.author: kraigb
manager: ghogen
ms.date: 10/24/2017
ms.topic: article
ms.prod: nuget
ms.technology: 
description: "Visual Studio 中常見的 NuGet 還原錯誤描述，以及如何針對這些錯誤進行疑難排解。"
keywords: "NuGet 套件還原, 還原套件, 進行疑難排解, 疑難排解"
ms.reviewer:
- karann-msft
- unniravindranathan
ms.openlocfilehash: c0993e2585452e3c64da28d14bb1bbe1bea27768
ms.sourcegitcommit: 4651b16a3a08f6711669fc4577f5d63b600f8f58
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 02/01/2018
---
# <a name="troubleshooting-package-restore-errors-in-visual-studio"></a><span data-ttu-id="8f067-104">針對 Visual Studio 中的套件還原錯誤進行疑難排解</span><span class="sxs-lookup"><span data-stu-id="8f067-104">Troubleshooting package restore errors in Visual Studio</span></span>

> [!Note]
> <span data-ttu-id="8f067-105">此頁面會著重於在 Visual Studio 中還原套件時常見的錯誤及其解決步驟。</span><span class="sxs-lookup"><span data-stu-id="8f067-105">This page focuses on common errors when restoring packages in Visual Studio and steps to resolve them.</span></span> <span data-ttu-id="8f067-106">如欲了解如何還原套件，請參閱[套件還原](../consume-packages/package-restore.md#enabling-and-disabling-package-restore)。</span><span class="sxs-lookup"><span data-stu-id="8f067-106">For how-to restore packages, see [Package restore](../consume-packages/package-restore.md#enabling-and-disabling-package-restore).</span></span>

<span data-ttu-id="8f067-107">根據預設，在 Visual Studio 中建置專案會自動還原專案中參考的 NuGet 套件。</span><span class="sxs-lookup"><span data-stu-id="8f067-107">By default, building a project in Visual Studio automatically restores NuGet packages referenced in the project.</span></span> <span data-ttu-id="8f067-108">不過，如果 [工具] > [選項] > [NuGet 套件管理員] > [套件還原] 設定中已停用套件還原，且電腦上沒有必要的套件，建置就會失敗。</span><span class="sxs-lookup"><span data-stu-id="8f067-108">However, builds will fail if package restore is disabled in the **Tools > Options > NuGet Package Manager > Package Restore** settings and the necessary packages are not available on your computer.</span></span> <span data-ttu-id="8f067-109">在這些案例中您可能會看到下列錯誤：</span><span class="sxs-lookup"><span data-stu-id="8f067-109">In these cases you may see the following errors:</span></span>

```output
This project references NuGet package(s) that are missing on this computer.
Use NuGet Package Restore to download them. The missing file is {name}.
```

```output
One or more NuGet packages need to be restored but couldn't be because consent has
not been granted. To give consent, open the Visual Studio Options dialog, click on
the NuGet Package Manager node and check 'Allow NuGet to download missing packages
during build.' You can also give consent by setting the environment variable
'EnableNuGetPackageRestore' to 'true'. Missing packages: {name} 
```

<span data-ttu-id="8f067-110">若要啟用 [套件還原]，請開啟 [工具] > [選項] > [NuGet 套件管理員]，選取 [允許 NuGet 下載遺漏的套件] 和 [在 Visual Studio 建置期間自動檢查遺漏的套件] 選項：</span><span class="sxs-lookup"><span data-stu-id="8f067-110">To enable package restore, open **Tools > Options > NuGet Package Manager** and select the options for **Allow NuGet to download missing packages** and **Automatically check for missing packages during build in Visual Studio**:</span></span>

![在工具/選項中啟用 NuGet 套件還原](../consume-packages/media/restore-01-autorestoreoptions.png)