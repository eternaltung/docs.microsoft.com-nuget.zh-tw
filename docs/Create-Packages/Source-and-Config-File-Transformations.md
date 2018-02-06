---
title: "NuGet 套件的原始程式檔和組態檔轉換 | Microsoft Docs"
author: kraigb
ms.author: kraigb
manager: ghogen
ms.date: 4/24/2017
ms.topic: article
ms.prod: nuget
ms.technology: 
ms.assetid: 20991d69-9e2e-4881-bbf2-96ae634e1872
description: "NuGet 套件可在安裝時轉換原始程式檔和組態檔 (XML) 的詳細資料。"
keywords: "NuGet 套件安裝、NuGet 套件轉換、修改組態檔、修改原始程式碼"
ms.reviewer:
- karann-msft
- unniravindranathan
- anangaur
ms.openlocfilehash: 89a55716ccbc9043cfce4c7f38ec8ab9a0e2f768
ms.sourcegitcommit: a40c1c1cc05a46410f317a72f695ad1d80f39fa2
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 01/05/2018
---
# <a name="transforming-source-code-and-configuration-files"></a><span data-ttu-id="59c13-104">轉換原始程式碼和組態檔</span><span class="sxs-lookup"><span data-stu-id="59c13-104">Transforming source code and configuration files</span></span>

<span data-ttu-id="59c13-105">針對使用 `packages.config` 或 `project.json` 的專案，NuGet 支援在套件安裝和解除安裝期間轉換原始程式碼和組態檔的能力。</span><span class="sxs-lookup"><span data-stu-id="59c13-105">For projects using `packages.config` or `project.json`, NuGet supports the ability to make transformations to source code and configuration files at package install and uninstall times.</span></span>

> [!Note]
> <span data-ttu-id="59c13-106">使用[專案檔中的套件參考](../Consume-Packages/Package-References-in-Project-Files.md)在專案中安裝套件時，不會套用原始程式檔和組態檔轉換。</span><span class="sxs-lookup"><span data-stu-id="59c13-106">Source and configuration file transformations are not applied when a package is installed in a project using [Package References in project files](../Consume-Packages/Package-References-in-Project-Files.md).</span></span> 

<span data-ttu-id="59c13-107">安裝套件時，**原始程式碼轉換**會將單向權杖取代套用至套件之 `content` 資料夾中的檔案，而權杖指的是 Visual Studio [套件屬性](/dotnet/api/vslangproj.projectproperties?redirectedfrom=MSDN&view=visualstudiosdk-2017#properties_)。</span><span class="sxs-lookup"><span data-stu-id="59c13-107">A **source code transformation** applies one-way token replacement to files in the package's `content` folder when the package is installed, where tokens refer to Visual Studio [project properties](/dotnet/api/vslangproj.projectproperties?redirectedfrom=MSDN&view=visualstudiosdk-2017#properties_).</span></span> <span data-ttu-id="59c13-108">這可讓您將檔案插入至專案的命名空間，或自訂一般會移入 ASP.NET 專案之 `global.asax` 中的程式碼。</span><span class="sxs-lookup"><span data-stu-id="59c13-108">This allows you to insert a file into the project's namespace, or to customize code that would typically go into `global.asax` in an ASP.NET project.</span></span>

<span data-ttu-id="59c13-109">**組態檔轉換**可讓您修改目標專案中的現有檔案 (例如 `web.config` 和 `app.config`)。</span><span class="sxs-lookup"><span data-stu-id="59c13-109">A **config file transformation** allows you to modify files that already exist in a target project, such as `web.config` and `app.config`.</span></span> <span data-ttu-id="59c13-110">例如，您的套件可能需要將項目新增至組態檔中的 `modules` 區段。</span><span class="sxs-lookup"><span data-stu-id="59c13-110">For example, your package might need to add an item to the `modules` section in the config file.</span></span> <span data-ttu-id="59c13-111">此轉換的完成是透過在專案中包含可描述要新增至組態檔之區段的特殊檔案。</span><span class="sxs-lookup"><span data-stu-id="59c13-111">This transformation is done by including special files in the package that describe the sections to add to the configuration files.</span></span> <span data-ttu-id="59c13-112">解除安裝套件時，接著會反轉這些相同的變更，讓這項作業成為雙向轉換。</span><span class="sxs-lookup"><span data-stu-id="59c13-112">When a package is uninstalled, those same changes are then reversed, making this a two-way transformation.</span></span>

## <a name="specifying-source-code-transformations"></a><span data-ttu-id="59c13-113">指定原始程式碼轉換</span><span class="sxs-lookup"><span data-stu-id="59c13-113">Specifying source code transformations</span></span>

1. <span data-ttu-id="59c13-114">您想要從套件插入至專案的檔案必須位在套件的 `content` 資料夾中。</span><span class="sxs-lookup"><span data-stu-id="59c13-114">Files that you want to insert from the package into the project must be located within the package's `content` folder.</span></span> <span data-ttu-id="59c13-115">例如，如果您想要將稱為 `ContosoData.cs` 的檔案安裝在目標專案的 `Models` 資料夾中，則它必須在套件的 `content\Models` 資料夾內部。</span><span class="sxs-lookup"><span data-stu-id="59c13-115">For example, if you want a file called `ContosoData.cs` to be installed in a `Models` folder of the target project, it must be inside the `content\Models` folder in the package.</span></span>

1. <span data-ttu-id="59c13-116">若要指示 NuGet 在安裝期間套用權杖取代，請將 `.pp` 附加至原始程式檔名稱。</span><span class="sxs-lookup"><span data-stu-id="59c13-116">To instruct NuGet to apply token replacement at install time, append `.pp` to the source code file name.</span></span> <span data-ttu-id="59c13-117">安裝之後，檔案的副檔名將不會是 `.pp`。</span><span class="sxs-lookup"><span data-stu-id="59c13-117">After installation, the file will not have the `.pp` extension.</span></span>

    <span data-ttu-id="59c13-118">例如，若要在 `ContosoData.cs` 中進行轉換，請將套件中的檔案命名為 `ContosoData.cs.pp`。</span><span class="sxs-lookup"><span data-stu-id="59c13-118">For example, to make transformations in `ContosoData.cs`, name the file in the package `ContosoData.cs.pp`.</span></span> <span data-ttu-id="59c13-119">它在安裝後會顯示為 `ContosoData.cs`。</span><span class="sxs-lookup"><span data-stu-id="59c13-119">After installation it will appear as `ContosoData.cs`.</span></span>

1. <span data-ttu-id="59c13-120">在原始程式檔中，使用表單 `$token$` 的不區分大小寫權杖指出 NuGet 應該取代為專案屬性的值：</span><span class="sxs-lookup"><span data-stu-id="59c13-120">In the source code file, use case-insensitive tokens of the form `$token$` to indicate values that NuGet should replace with project properties:</span></span>

    ```cs
    namespace $rootnamespace$.Models
    {
        public struct CategoryInfo
        {
            public string categoryid;
            public string description;
            public string htmlUrl;
            public string rssUrl;
            public string title;
        }
    }
    ```

    <span data-ttu-id="59c13-121">安裝時，NuGet 會將 `$rootnamespace$` 取代為 `Fabrikam`，並假設目標專案的根命名空間是 `Fabrikam`。</span><span class="sxs-lookup"><span data-stu-id="59c13-121">Upon installation, NuGet replaces `$rootnamespace$` with `Fabrikam` assuming the target project's whose root namespace is `Fabrikam`.</span></span>

<span data-ttu-id="59c13-122">`$rootnamespace$` 權杖是最常用的專案屬性，其他則列在 MSDN 的[專案屬性](/dotnet/api/vslangproj.projectproperties?redirectedfrom=MSDN&view=visualstudiosdk-2017#properties_)文件中。</span><span class="sxs-lookup"><span data-stu-id="59c13-122">The `$rootnamespace$` token is the most commonly used project property; all others are listed in the [Project Properties](/dotnet/api/vslangproj.projectproperties?redirectedfrom=MSDN&view=visualstudiosdk-2017#properties_) documentation on MSDN.</span></span> <span data-ttu-id="59c13-123">當然，請注意，某些屬性可能是專案類型所特有。</span><span class="sxs-lookup"><span data-stu-id="59c13-123">Be mindful, of course, that some properties might be specific to the project type.</span></span>

## <a name="specifying-config-file-transformations"></a><span data-ttu-id="59c13-124">指定組態檔轉換</span><span class="sxs-lookup"><span data-stu-id="59c13-124">Specifying config file transformations</span></span>

<span data-ttu-id="59c13-125">如下節所述，可以使用兩種方式進行組態檔轉換：</span><span class="sxs-lookup"><span data-stu-id="59c13-125">As described in the sections that follow, config file transformations can be done in two ways:</span></span>

- <span data-ttu-id="59c13-126">在套件的 `content` 資料夾中包含 `app.config.transform` 和 `web.config.transform` 檔案，其中 `.transform` 副檔名會告知 NuGet，這些檔案包含安裝套件時要與現有組態檔合併的 XML。</span><span class="sxs-lookup"><span data-stu-id="59c13-126">Include `app.config.transform` and `web.config.transform` files in your package's `content` folder, where the `.transform` extension tells NuGet that these files contain the XML to merge with existing config files when the package is installed.</span></span> <span data-ttu-id="59c13-127">解除安裝套件時，會移除這個相同的 XML。</span><span class="sxs-lookup"><span data-stu-id="59c13-127">When a package is uninstalled, that same XML is removed.</span></span>
- <span data-ttu-id="59c13-128">(NuGet 2.6 和更新版本) 使用 [XDT 語法](https://msdn.microsoft.com/library/dd465326.aspx)描述所需的變更，以在套件的 `content` 資料夾中包含 `app.config.install.xdt` 和 `web.config.install.xdt` 檔案。</span><span class="sxs-lookup"><span data-stu-id="59c13-128">(NuGet 2.6 and later) Include `app.config.install.xdt` and `web.config.install.xdt` files in your package's `content` folder, using [XDT syntax](https://msdn.microsoft.com/library/dd465326.aspx) to describe the desired changes.</span></span> <span data-ttu-id="59c13-129">使用此選項，您也可以包含 `.uninstall.xdt` 檔案，以在從專案移除套件時反轉變更。</span><span class="sxs-lookup"><span data-stu-id="59c13-129">With this option you can also include a `.uninstall.xdt` file to reverse changes when the package is removed from a project.</span></span>

> [!Note]
> <span data-ttu-id="59c13-130">轉換不會套用至 Visual Studio 中參考為連結的 `.config` 檔案。</span><span class="sxs-lookup"><span data-stu-id="59c13-130">Transformations are not applied to `.config` files referenced as a link in Visual Studio.</span></span>

<span data-ttu-id="59c13-131">使用 XDT 的優點是它提供語法以使用利用完整 XPath 支援進行項目和屬性比對來操作 XML DOM 結構，而不是僅合併兩個靜態檔案。</span><span class="sxs-lookup"><span data-stu-id="59c13-131">The advantage of using XDT is that instead of simply merging two static files, it provides a syntax for manipulating the structure of an XML DOM using element and attribute matching using full XPath support.</span></span> <span data-ttu-id="59c13-132">XDT 接著可以新增、更新或移除項目、將新項目放在特定位置，或取代/移除項目 (包含子節點)。</span><span class="sxs-lookup"><span data-stu-id="59c13-132">XDT can then add, update, or remove elements, place new elements at a specific location, or replace/remove elements (including child nodes).</span></span> <span data-ttu-id="59c13-133">這可讓您直接建立解除安裝轉換，以取消在套件安裝期間完成的所有轉換。</span><span class="sxs-lookup"><span data-stu-id="59c13-133">This makes it straightforward to create uninstall transforms that back out all transformations done during package installation.</span></span>

### <a name="xml-transforms"></a><span data-ttu-id="59c13-134">XML 轉換</span><span class="sxs-lookup"><span data-stu-id="59c13-134">XML transforms</span></span>

<span data-ttu-id="59c13-135">套件之 `content` 資料夾中的 `app.config.transform` 和 `web.config.transform` 只會包含要合併至專案之現有 `app.config` 和 `web.config` 檔案的項目。</span><span class="sxs-lookup"><span data-stu-id="59c13-135">The `app.config.transform` and `web.config.transform` in a package's `content` folder contain only those elements to merge into the project's existing `app.config` and `web.config` files.</span></span>

<span data-ttu-id="59c13-136">例如，假設專案一開始在 `web.config` 中包含下列內容：</span><span class="sxs-lookup"><span data-stu-id="59c13-136">As an example, suppose the project initially contains the following content in `web.config`:</span></span>

```xml
<configuration>
    <system.webServer>
        <modules>
            <add name="ContosoUtilities" type="Contoso.Utilities" />
        </modules>
    <system.webServer>
</configuration>
```

<span data-ttu-id="59c13-137">若要在套件安裝期間將 `MyNuModule` 項目新增至 `modules` 區段，請在套件的 `content` 資料夾中建立 `web.config.transform` 檔案，如下所示：</span><span class="sxs-lookup"><span data-stu-id="59c13-137">To add a `MyNuModule` element to the `modules` section during package install, create a `web.config.transform` file in the package's `content` folder that looks like this:</span></span>

```xml
<configuration>
    <system.webServer>
        <modules>
            <add name="MyNuModule" type="Sample.MyNuModule" />
        </modules>
    <system.webServer>
</configuration>
```

<span data-ttu-id="59c13-138">NuGet 安裝套件之後，`web.config` 會顯示如下：</span><span class="sxs-lookup"><span data-stu-id="59c13-138">After NuGet installs the package, `web.config` will appear as follows:</span></span>

```xml
<configuration>
    <system.webServer>
        <modules>
            <add name="ContosoUtilities" type="Contoso.Utilities" />
            <add name="MyNuModule" type="Sample.MyNuModule" />
        </modules>
    <system.webServer>
</configuration>
```

<span data-ttu-id="59c13-139">請注意，NuGet 不會取代 `modules` 區段，而只是新增項目和屬性，以在其中合併新項目。</span><span class="sxs-lookup"><span data-stu-id="59c13-139">Notice that NuGet didn't replace the `modules` section, it just merged the new entry into it by adding only new elements and attributes.</span></span> <span data-ttu-id="59c13-140">NuGet 不會變更任何現有項目或屬性。</span><span class="sxs-lookup"><span data-stu-id="59c13-140">NuGet will not change any existing elements or attributes.</span></span>

<span data-ttu-id="59c13-141">解除安裝套件時，NuGet 會重新檢查 `.transform` 檔案，並從適當的 `.config` 檔案中移除它所含的項目。</span><span class="sxs-lookup"><span data-stu-id="59c13-141">When the package is uninstalled, NuGet will examine the `.transform` files again and remove the elements it contains from the appropriate `.config` files.</span></span> <span data-ttu-id="59c13-142">請注意，此程序將不會影響 `.config` 檔案中您在套件安裝之後修改的任何列。</span><span class="sxs-lookup"><span data-stu-id="59c13-142">Note that this process will not affect any lines in the `.config` file that you modify after package installation.</span></span>

<span data-ttu-id="59c13-143">更廣泛的範例是 [ASP.NET 的錯誤記錄模組和處理常式 (ELMAH)](https://www.nuget.org/packages/elmah/) 套件會將許多項目新增至 `web.config`，然後在解除安裝套件時重新予以移除。</span><span class="sxs-lookup"><span data-stu-id="59c13-143">As a more extensive example, the [Error Logging Modules and Handlers for ASP.NET (ELMAH)](https://www.nuget.org/packages/elmah/) package adds many entries into `web.config`, which are again removed when a package is uninstalled.</span></span>

<span data-ttu-id="59c13-144">若要檢查其 `web.config.transform` 檔案，請從上面的連結下載 ELMAH 套件，並將套件延伸模組從 `.nupkg` 變更為 `.zip`，然後開啟該 ZIP 檔案中的 `content\web.config.transform`。</span><span class="sxs-lookup"><span data-stu-id="59c13-144">To examine its `web.config.transform` file, download the ELMAH package from the link above, change the package extension from `.nupkg` to `.zip`, and then open `content\web.config.transform` in that ZIP file.</span></span>

<span data-ttu-id="59c13-145">若要查看安裝和解除安裝套件的效果，請在 Visual Studio 中建立新的 ASP.NET 專案 (範本是在 [新增專案] 對話方塊的 [Visual C#] > [Web] 下方)，然後選取空白 ASP.NET 應用程式。</span><span class="sxs-lookup"><span data-stu-id="59c13-145">To see the effect of installing and uninstalling the package, create a new ASP.NET project in Visual Studio (the template is under **Visual C# > Web** in the New Project dialog), and select an empty ASP.NET application.</span></span> <span data-ttu-id="59c13-146">開啟 `web.config` 以查看其初始狀態。</span><span class="sxs-lookup"><span data-stu-id="59c13-146">Open `web.config` to see its initial state.</span></span> <span data-ttu-id="59c13-147">接著以滑鼠右鍵按一下專案，並選取 [管理 NuGet 套件]，再瀏覽 nuget.org 上的 ELMAH，然後安裝最新版本。</span><span class="sxs-lookup"><span data-stu-id="59c13-147">Then right-click the project, select **Manage NuGet Packages**, browse for ELMAH on nuget.org, and install the latest version.</span></span> <span data-ttu-id="59c13-148">請注意所有 `web.config` 變更。</span><span class="sxs-lookup"><span data-stu-id="59c13-148">Notice all the changes to `web.config`.</span></span> <span data-ttu-id="59c13-149">現在解除安裝套件，而您會看到 `web.config` 還原成其先前狀態。</span><span class="sxs-lookup"><span data-stu-id="59c13-149">Now uninstall the package and you'll see `web.config` revert to its prior state.</span></span>

### <a name="xdt-transforms"></a><span data-ttu-id="59c13-150">XDT 轉換</span><span class="sxs-lookup"><span data-stu-id="59c13-150">XDT transforms</span></span>

<span data-ttu-id="59c13-151">使用 NuGet 2.6 和更新版本，您可以使用 [XDT 語法](https://msdn.microsoft.com/library/dd465326.aspx)來修改組態檔。</span><span class="sxs-lookup"><span data-stu-id="59c13-151">With NuGet 2.6 and later, you can modify config files using [XDT syntax](https://msdn.microsoft.com/library/dd465326.aspx).</span></span> <span data-ttu-id="59c13-152">您也可以在 `$` 分隔符號 (不區分大小寫) 內包含屬性名稱，讓 NuGet 將權杖取代為[專案屬性](/dotnet/api/vslangproj.projectproperties?redirectedfrom=MSDN&view=visualstudiosdk-2017#properties_)。</span><span class="sxs-lookup"><span data-stu-id="59c13-152">You can also have NuGet replace tokens with [Project Properties](/dotnet/api/vslangproj.projectproperties?redirectedfrom=MSDN&view=visualstudiosdk-2017#properties_) by including the property name within `$` delimeters (case-insensitive).</span></span>

<span data-ttu-id="59c13-153">例如，下列 `app.config.install.xdt` 檔案會將 `appSettings` 項目從專案插入至包含 `FullPath`、`FileName` 和 `ActiveConfigurationSettings` 值的 `app.config`：</span><span class="sxs-lookup"><span data-stu-id="59c13-153">For example, the following `app.config.install.xdt` file will insert an `appSettings` element into `app.config` containing the `FullPath`, `FileName`, and `ActiveConfigurationSettings` values from the project:</span></span>

```xml
<?xml version="1.0"?>
<configuration xmlns:xdt="http://schemas.microsoft.com/XML-Document-Transform">
    <appSettings xdt:Transform="Insert">
        <add key="FullPath" value="$FullPath$" />
        <add key="FileName" value="$filename$" />
        <add key="ActiveConfigurationSettings " value="$ActiveConfigurationSettings$" />
    </appSettings>
</configuration>
```

<span data-ttu-id="59c13-154">另一個範例假設專案一開始在 `web.config` 中包含下列內容：</span><span class="sxs-lookup"><span data-stu-id="59c13-154">For another example, suppose the project initially contains the following content in `web.config`:</span></span>

```xml
<configuration>
    <system.webServer>
        <modules>
            <add name="ContosoUtilities" type="Contoso.Utilities" />
        </modules>
    <system.webServer>
</configuration>
```

<span data-ttu-id="59c13-155">若要在套件安裝期間將 `MyNuModule` 項目新增至 `modules` 區段，則套件的 `web.config.install.xdt` 將會包含下列項目：</span><span class="sxs-lookup"><span data-stu-id="59c13-155">To add a `MyNuModule` element to the `modules` section during package install, the package's `web.config.install.xdt` would contain the following:</span></span>

```xml
<?xml version="1.0"?>
<configuration xmlns:xdt="http://schemas.microsoft.com/XML-Document-Transform">
    <system.webServer>
        <modules>
            <add name="MyNuModule" type="Sample.MyNuModule" xdt:Transform="Insert" />
        </modules>
    </system.webServer>
</configuration>
```

<span data-ttu-id="59c13-156">安裝套件之後，`web.config` 會如下：</span><span class="sxs-lookup"><span data-stu-id="59c13-156">After installing the package, `web.config` will look like this:</span></span>

```xml
<configuration>
    <system.webServer>
        <modules>
            <add name="ContosoUtilities" type="Contoso.Utilities" />
            <add name="MyNuModule" type="Sample.MyNuModule" />
        </modules>
    <system.webServer>
</configuration>
```

<span data-ttu-id="59c13-157">若在套件解除安裝期間只要移除 `MyNuModule` 項目，則 `web.config.uninstall.xdt` 檔案應該包含下列項目：</span><span class="sxs-lookup"><span data-stu-id="59c13-157">To remove only the `MyNuModule` element during package uninstall, the `web.config.uninstall.xdt` file should contain the following:</span></span>

```xml
<?xml version="1.0"?>
<configuration xmlns:xdt="http://schemas.microsoft.com/XML-Document-Transform">
    <system.webServer>
        <modules>
            <add name="MyNuModule" xdt:Transform="Remove" xdt:Locator="Match(name)" />
        </modules>
    </system.webServer>
</configuration>
```