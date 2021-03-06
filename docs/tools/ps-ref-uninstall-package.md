---
title: NuGet 解除安裝套件的 PowerShell 參考
description: 在 Visual Studio 中的 NuGet 封裝管理員主控台中的封裝解除安裝的 PowerShell 命令的參考。
author: karann-msft
ms.author: karann
manager: unnir
ms.date: 06/01/2017
ms.topic: reference
ms.openlocfilehash: 860a58c359c9b723564a70f83aee4eee5cebf16d
ms.sourcegitcommit: 2a6d200012cdb4cbf5ab1264f12fecf9ae12d769
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/06/2018
ms.locfileid: "34818863"
---
# <a name="uninstall-package-package-manager-console-in-visual-studio"></a>Uninstall-Package (Visual Studio 套件管理員主控台)

*本主題描述內的命令[NuGet Package Manager Console](package-manager-console.md) Windows 上的 Visual Studio 中。一般 PowerShell 解除安裝封裝的命令，請參閱[PowerShell PackageManagement 參考](/powershell/module/packagemanagement/?view=powershell-6)。*

移除封裝在專案中，選擇性地移除其相依性。 如果有其他套件相依於這個套件，此命令會失敗，除非 – 指定的 Force 選項。

## <a name="syntax"></a>語法

```ps
Uninstall-Package [-Id] <string> [-RemoveDependencies] [-ProjectName <string>] [-Force]
    [-Version <string>] [-WhatIf] [<CommonParameters>]
```

如果有其他套件相依於這個套件，此命令會失敗，除非 – 指定的 Force 選項。

## <a name="parameters"></a>參數

| 參數 | 描述 |
| --- | --- |
| ID | （必要）若要解除安裝封裝的識別碼。 -Id 參數是選擇性的。 |
| 版本 | 若要解除安裝，封裝版本預設為目前安裝的版本。 |
| RemoveDependencies | 解除安裝套件及其未使用相依性。 也就是說，如果任何相依性具有相依於它的另一個封裝，它會略過。 |
| ProjectName | 要從中解除安裝封裝，將預設為預設專案的專案。 |
| 強制 | 強制解除安裝，封裝，即使有其他套件相依於它。 |
| WhatIf | 顯示執行命令，而不需實際執行解除安裝時，會發生什麼情況。 |

這些參數接受管線輸入或萬用字元的字元。

## <a name="common-parameters"></a>一般參數

`Uninstall-Package` 支援下列[一般 PowerShell 參數](http://go.microsoft.com/fwlink/?LinkID=113216)： 偵錯、 錯誤動作、 ErrorVariable、 OutBuffer、 OutVariable、 PipelineVariable、 Verbose、 WarningAction 和 WarningVariable。

## <a name="examples"></a>範例

```ps
# Uninstalls the Elmah package from the default project
Uninstall-Package Elmah

# Uninstalls the Elmah package and all its unused dependencies
Uninstall-Package Elmah -RemoveDependencies 

# Uninstalls the Elmah package even if another package depends on it
Uninstall-Package Elmah -Force
```
