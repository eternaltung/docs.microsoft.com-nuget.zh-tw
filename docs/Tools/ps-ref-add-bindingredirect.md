---
title: "NuGet 加入 BindingRedirect PowerShell 參考 |Microsoft 文件"
author: kraigb
ms.author: kraigb
manager: ghogen
ms.date: 12/07/2017
ms.topic: reference
ms.prod: nuget
ms.technology: 
ms.assetid: 90f4dcb0-6e5a-4948-8ea9-62e0d061d95a
description: "在 Visual Studio 中的 NuGet 封裝管理員主控台新增 BindingRedirect PowerShell 命令的參考。"
keywords: "NuGet 封裝管理員主控台中，NuGet Powershell 命令，新增 BindingRedirect NuGet Powershell 參考"
ms.reviewer:
- karann-msft
- unniravindranathan
ms.openlocfilehash: 7bf8cdb938195f4747932b38ef0d5bb6c34b9137
ms.sourcegitcommit: d0ba99bfe019b779b75731bafdca8a37e35ef0d9
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/14/2017
---
# <a name="add-bindingredirect-package-manager-console-in-visual-studio"></a><span data-ttu-id="2cd00-104">新增 BindingRedirect （在 Visual Studio 中的封裝管理員主控台）</span><span class="sxs-lookup"><span data-stu-id="2cd00-104">Add-BindingRedirect (Package Manager Console in Visual Studio)</span></span>

<span data-ttu-id="2cd00-105">*只能在[NuGet Package Manager Console](Package-Manager-Console.md) Windows 上的 Visual Studio 中。*</span><span class="sxs-lookup"><span data-stu-id="2cd00-105">*Available only within the [NuGet Package Manager Console](Package-Manager-Console.md) in Visual Studio on Windows.*</span></span>

<span data-ttu-id="2cd00-106">會檢查專案的輸出路徑內的所有組件，並在需要時，將繫結重新導向加入至應用程式或 web 組態檔。</span><span class="sxs-lookup"><span data-stu-id="2cd00-106">Examines all assemblies within the output path for a project and adds binding redirects to the application or web configuration file where necessary.</span></span> <span data-ttu-id="2cd00-107">安裝套件時，就會自動執行此命令。</span><span class="sxs-lookup"><span data-stu-id="2cd00-107">This command is run automatically when installing a package.</span></span>

<span data-ttu-id="2cd00-108">如需繫結重新導向和使用的原因的詳細資訊，請參閱[重新導向組件版本](https://docs.microsoft.com/dotnet/framework/configure-apps/redirect-assembly-versions).NET 文件中。</span><span class="sxs-lookup"><span data-stu-id="2cd00-108">For details on binding redirects and why they are used, see [Redirecting Assembly Versions](https://docs.microsoft.com/dotnet/framework/configure-apps/redirect-assembly-versions) in the .NET documentation.</span></span>

## <a name="syntax"></a><span data-ttu-id="2cd00-109">語法</span><span class="sxs-lookup"><span data-stu-id="2cd00-109">Syntax</span></span>

```ps
Add-BindingRedirect [-ProjectName] <string> [<CommonParameters>]
```

## <a name="parameters"></a><span data-ttu-id="2cd00-110">參數</span><span class="sxs-lookup"><span data-stu-id="2cd00-110">Parameters</span></span>

| <span data-ttu-id="2cd00-111">參數</span><span class="sxs-lookup"><span data-stu-id="2cd00-111">Parameter</span></span> | <span data-ttu-id="2cd00-112">說明</span><span class="sxs-lookup"><span data-stu-id="2cd00-112">Description</span></span> |
| --- | --- |
| <span data-ttu-id="2cd00-113">ProjectName</span><span class="sxs-lookup"><span data-stu-id="2cd00-113">ProjectName</span></span> | <span data-ttu-id="2cd00-114">（必要）要在其中加入繫結重新導向的專案。</span><span class="sxs-lookup"><span data-stu-id="2cd00-114">(Required) The project to which to add binding redirects.</span></span> <span data-ttu-id="2cd00-115">-ProjectName 參數是選擇性的。</span><span class="sxs-lookup"><span data-stu-id="2cd00-115">The -ProjectName switch itself is optional.</span></span> |

<span data-ttu-id="2cd00-116">這些參數接受管線輸入或萬用字元的字元。</span><span class="sxs-lookup"><span data-stu-id="2cd00-116">None of these parameters accept pipeline input or wildcard characters.</span></span>

## <a name="common-parameters"></a><span data-ttu-id="2cd00-117">一般參數</span><span class="sxs-lookup"><span data-stu-id="2cd00-117">Common Parameters</span></span>

<span data-ttu-id="2cd00-118">`Add-BindingRedirect`支援下列[一般 PowerShell 參數](http://go.microsoft.com/fwlink/?LinkID=113216)： 偵錯、 錯誤動作、 ErrorVariable、 OutBuffer、 OutVariable、 PipelineVariable、 Verbose、 WarningAction 和 WarningVariable。</span><span class="sxs-lookup"><span data-stu-id="2cd00-118">`Add-BindingRedirect` supports the following [common PowerShell parameters](http://go.microsoft.com/fwlink/?LinkID=113216): Debug, Error Action, ErrorVariable, OutBuffer, OutVariable, PipelineVariable, Verbose, WarningAction, and WarningVariable.</span></span>

## <a name="examples"></a><span data-ttu-id="2cd00-119">範例</span><span class="sxs-lookup"><span data-stu-id="2cd00-119">Examples</span></span>

```ps
Add-BindingRedirect MyProject

Add-BindingRedirect -ProjectName MyProject
```