---
title: "NuGet 2.1 版本資訊 |Microsoft 文件"
author: karann-msft
ms.author: karann-msft
manager: ghogen
ms.date: 11/11/2016
ms.topic: article
ms.prod: nuget
ms.technology: 
ms.assetid: 6f972803-9e17-43f5-b77b-973c3accf695
description: "包括已知的問題、 錯誤修正、 新增的功能，以及 Dcr NuGet 2.1 版本資訊。"
keywords: "NuGet 2.1 版本資訊，將 bug 修正、 已知問題、 已新增的功能，Dcr"
ms.reviewer:
- karann-msft
- unniravindranathan
ms.openlocfilehash: c45cfb9f6a46a1efd9fe4531602191973da66290
ms.sourcegitcommit: d0ba99bfe019b779b75731bafdca8a37e35ef0d9
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/14/2017
---
# <a name="nuget-21-release-notes"></a><span data-ttu-id="6bdaa-104">NuGet 2.1 版本資訊</span><span class="sxs-lookup"><span data-stu-id="6bdaa-104">NuGet 2.1 Release Notes</span></span>

<span data-ttu-id="6bdaa-105">[NuGet 2.0 版本資訊](../release-notes/nuget-2.0.md) | [NuGet 2.2 版本資訊](../release-notes/nuget-2.2.md)</span><span class="sxs-lookup"><span data-stu-id="6bdaa-105">[NuGet 2.0 Release Notes](../release-notes/nuget-2.0.md) | [NuGet 2.2 Release Notes](../release-notes/nuget-2.2.md)</span></span>

<span data-ttu-id="6bdaa-106">NuGet 2.1 已於 2012 年 10 月 4 日發行。</span><span class="sxs-lookup"><span data-stu-id="6bdaa-106">NuGet 2.1 was released on October 4, 2012.</span></span>

## <a name="hierarchical-nugetconfig"></a><span data-ttu-id="6bdaa-107">階層式 Nuget.Config</span><span class="sxs-lookup"><span data-stu-id="6bdaa-107">Hierarchical Nuget.Config</span></span>
<span data-ttu-id="6bdaa-108">NuGet 2.1 可讓您更大的彈性來控制透過以遞迴方式向上尋找的資料夾結構的 NuGet 設定`NuGet.Config`檔案，然後建置組態從所有找到的檔案集。</span><span class="sxs-lookup"><span data-stu-id="6bdaa-108">NuGet 2.1 gives you greater flexibility in controlling NuGet settings by way of recursively walking up the folder structure looking for `NuGet.Config` files and then building the configuration from the set of all found files.</span></span>  <span data-ttu-id="6bdaa-109">例如，假設其中團隊具有 CI 組建的其他內部的相依性內部的封裝儲存機制。</span><span class="sxs-lookup"><span data-stu-id="6bdaa-109">As an example, consider the scenario where a team has an internal package repository for CI builds of other internal dependencies.</span></span> <span data-ttu-id="6bdaa-110">個別的專案的資料夾結構看起來可能如下所示：</span><span class="sxs-lookup"><span data-stu-id="6bdaa-110">The folder structure for an individual project might look like the following:</span></span>

    C:\
    C:\myteam\
    C:\myteam\solution1
    C:\myteam\solution1\project1

<span data-ttu-id="6bdaa-111">此外，如果方案已啟用封裝還原，也會存在下列資料夾：</span><span class="sxs-lookup"><span data-stu-id="6bdaa-111">Additionally, if package restore is enabled for the solution, the following folder will also exist:</span></span>

    C:\myteam\solution1\.nuget

<span data-ttu-id="6bdaa-112">為了有小組內部的封裝儲存機制適用於所有專案的小組，會在不讓它可供每個專案的電腦上，我們可以建立新的 Nuget.Config 檔案，並將它放在 c:\myteam 資料夾中。</span><span class="sxs-lookup"><span data-stu-id="6bdaa-112">In order to have the team’s internal package repository available for all projects that the team works on, while not making it available for every project on the machine, we can create a new Nuget.Config file and place it in the c:\myteam folder.</span></span> <span data-ttu-id="6bdaa-113">沒有任何方法指定為每個專案的 packages 資料夾。</span><span class="sxs-lookup"><span data-stu-id="6bdaa-113">There is no way to specificy a packages folder per project.</span></span>

```xml
<configuration>
    <packageSources>
    <add key="Official project team source" value="http://teamserver/api/v2/" />
    </packageSources>
    <disabledPackageSources />
    <activePackageSource>
    <add key="Official project team source" value="http://teamserver/api/v2/" />
    </activePackageSource>
</configuration>
```

<span data-ttu-id="6bdaa-114">我們現在可以看到的來源已加入執行 'nuget.exe 來源' 命令，從任何資料夾下方 c:\myteam 如下所示：</span><span class="sxs-lookup"><span data-stu-id="6bdaa-114">We can now see that the source was added by running the ‘nuget.exe sources’ command from any folder beneath c:\myteam as shown below:</span></span>

![從父 nuget 組態的封裝來源](./media/releasenotes-21-cfg-hierarchy.png)

<span data-ttu-id="6bdaa-116">`NuGet.Config`搜尋檔案順序如下：</span><span class="sxs-lookup"><span data-stu-id="6bdaa-116">`NuGet.Config` files are searched for in the following order:</span></span>

1. `.nuget\Nuget.Config`
2. <span data-ttu-id="6bdaa-117">遞迴逐步來自專案資料夾根目錄</span><span class="sxs-lookup"><span data-stu-id="6bdaa-117">Recursive walk from project folder to root</span></span>
3. <span data-ttu-id="6bdaa-118">全域`Nuget.Config`(`%appdata%\NuGet\Nuget.Config`)</span><span class="sxs-lookup"><span data-stu-id="6bdaa-118">Global `Nuget.Config` (`%appdata%\NuGet\Nuget.Config`)</span></span>

<span data-ttu-id="6bdaa-119">組態設定是套用在非*反向順序*，亦即，取決於上述排序，全域 Nuget.Config 就會先套用，後面接著探索到的 Nuget.Config 檔案從根專案資料夾，再由`.nuget\Nuget.Config`。</span><span class="sxs-lookup"><span data-stu-id="6bdaa-119">The configurations are than applied in the *reverse order*, meaning that based on the above ordering, the global Nuget.Config would be applied first, followed by the discovered Nuget.Config files from root to project folder, followed by `.nuget\Nuget.Config`.</span></span>  <span data-ttu-id="6bdaa-120">這是非常重要，如果您使用`<clear/>`項目移除設定的一組項目。</span><span class="sxs-lookup"><span data-stu-id="6bdaa-120">This is particularly important if you’re using the `<clear/>` element to remove a set of items from config.</span></span>

## <a name="specify-packages-folder-location"></a><span data-ttu-id="6bdaa-121">指定 'packages' 資料夾位置</span><span class="sxs-lookup"><span data-stu-id="6bdaa-121">Specify ‘packages’ Folder Location</span></span>
<span data-ttu-id="6bdaa-122">在過去，NuGet 已找到方案根資料夾下的已知 'packages' 資料夾管理方案套件。</span><span class="sxs-lookup"><span data-stu-id="6bdaa-122">In the past, NuGet has managed a solution’s packages from a known ‘packages’ folder found beneath the solution root folder.</span></span>  <span data-ttu-id="6bdaa-123">有許多不同的方案具有已安裝的 NuGet 封裝的開發團隊，這會導致在許多不同的地方，在檔案系統上安裝相同的封裝。</span><span class="sxs-lookup"><span data-stu-id="6bdaa-123">For development teams that have many different solutions which have NuGet packages installed, this can result in the same package being installed in many different places on the file system.</span></span>

<span data-ttu-id="6bdaa-124">NuGet 2.1 提供更細微地控制透過 [packages] 資料夾的位置`repositoryPath`中的項目`NuGet.Config`檔案。</span><span class="sxs-lookup"><span data-stu-id="6bdaa-124">NuGet 2.1 provides more granular control over the location of the packages folder via the `repositoryPath` element in the `NuGet.Config` file.</span></span>  <span data-ttu-id="6bdaa-125">建立階層式 Nuget.Config 支援上述範例，假設我們想要擁有 C:\myteam\ 共用相同的封裝資料夾下的所有專案。</span><span class="sxs-lookup"><span data-stu-id="6bdaa-125">Building on the previous example of hierarchical Nuget.Config support, assume that we wish to have all projects under C:\myteam\ share the same packages folder.</span></span>  <span data-ttu-id="6bdaa-126">若要這麼做，只要加入下列項目以`c:\myteam\Nuget.Config`。</span><span class="sxs-lookup"><span data-stu-id="6bdaa-126">To accomplish this, simply add the following entry to `c:\myteam\Nuget.Config`.</span></span>

```xml
<configuration>
    <config>
    <add key="repositoryPath" value="C:\myteam\teampackages" />
    </config>
    ...
</configuration>
```

<span data-ttu-id="6bdaa-127">在此範例中，共用`Nuget.Config`檔案會指定無論深度 C:\myteam，下方會建立每個專案的封裝共用的資料夾。</span><span class="sxs-lookup"><span data-stu-id="6bdaa-127">In this example, the shared `Nuget.Config` file specifies a shared packages folder for every project that is created beneath C:\myteam, regardless of depth.</span></span> <span data-ttu-id="6bdaa-128">請注意，是否您有現有的封裝資料夾方案根目錄下，您必須將它刪除，NuGet 會將封裝放在新位置之前。</span><span class="sxs-lookup"><span data-stu-id="6bdaa-128">Note that if you have an existing packages folder underneath your solution root, you will need to delete it before NuGet will place packages in the new location.</span></span>

## <a name="support-for-portable-libraries"></a><span data-ttu-id="6bdaa-129">可攜式程式庫支援</span><span class="sxs-lookup"><span data-stu-id="6bdaa-129">Support for Portable Libraries</span></span>
<span data-ttu-id="6bdaa-130">[可攜式類別庫](http://msdn.microsoft.com/library/gg597391.aspx)是可讓您建置組件，可以不需要修改不同 Microsoft 平台上，從.net Framework Windows Phone 和 Xbox 甚至的 silverlight 版本的.NET 4 第一次引進的功能360 （雖然在此階段中，NuGet 不支援 Xbox 可攜式程式庫目標）。</span><span class="sxs-lookup"><span data-stu-id="6bdaa-130">[Portable libraries](http://msdn.microsoft.com/library/gg597391.aspx) is a feature first introduced with .NET 4 that enables you to build assemblies that can work without modification on different Microsoft platforms, from versions of the.NET Framework to Silverlight to Windows Phone and even Xbox 360 (though at this time, NuGet does not support the Xbox portable library target).</span></span>  <span data-ttu-id="6bdaa-131">藉由擴充[封裝慣例](../create-packages/supporting-multiple-target-frameworks.md)framework 版本和設定檔，NuGet 2.1 現在支援可攜式程式庫，讓您建立封裝以將複合架構和設定檔目標`lib`資料夾。</span><span class="sxs-lookup"><span data-stu-id="6bdaa-131">By extending the [package conventions](../create-packages/supporting-multiple-target-frameworks.md) for framework versions and profiles, NuGet 2.1 now supports portable libraries by enabling you to create packages that have compound framework and profile target `lib` folders.</span></span>

<span data-ttu-id="6bdaa-132">例如，請考慮下列的可攜式類別庫提供的目標平台。</span><span class="sxs-lookup"><span data-stu-id="6bdaa-132">As an example, consider the following portable class library’s available target platforms.</span></span>

![可攜式程式庫建立對話方塊](./media/releasenotes-21-plib.png)

<span data-ttu-id="6bdaa-134">在建置之程式庫之後和命令`nuget.exe pack MyPortableProject.csproj`執行時，新的可攜式程式庫封裝的資料夾結構看藉由檢查產生的 NuGet 套件的內容。</span><span class="sxs-lookup"><span data-stu-id="6bdaa-134">After the library is built and the command `nuget.exe pack MyPortableProject.csproj` is run, the new portable library package folder structure can be seen by examining the contents of the generated NuGet package.</span></span>

![可攜式程式庫封裝配置](./media/releasenotes-21-plib-layout.png)

<span data-ttu-id="6bdaa-136">如您所見，可攜式程式庫資料夾名稱慣例遵循模式 '可攜式 {架構 1} + {framework n}' 的 framework 識別項遵循現有[架構名稱和版本慣例](../schema/target-frameworks.md)。</span><span class="sxs-lookup"><span data-stu-id="6bdaa-136">As you can see, the portable library folder name convention follows the pattern ‘portable-{framework 1}+{framework n}’ where the framework identifiers follow the existing [framework name and version conventions](../schema/target-frameworks.md).</span></span> <span data-ttu-id="6bdaa-137">使用適用於 Windows Phone 的 framework 識別項中找到一個例外狀況的名稱和版本的慣例。</span><span class="sxs-lookup"><span data-stu-id="6bdaa-137">One exception to the name and version conventions is found in the framework identifier used for Windows Phone.</span></span>  <span data-ttu-id="6bdaa-138">這個 moniker，應該使用的架構名稱 'wp' （wp7、 wp71 或 wp8）。</span><span class="sxs-lookup"><span data-stu-id="6bdaa-138">This moniker should use the framework name ‘wp’ (wp7, wp71 or wp8).</span></span> <span data-ttu-id="6bdaa-139">使用 ' silverlight-wp7'，例如，將會導致錯誤。</span><span class="sxs-lookup"><span data-stu-id="6bdaa-139">Using ‘silverlight-wp7’, for example, will result in an error.</span></span>

<span data-ttu-id="6bdaa-140">安裝時所建立從這個資料夾結構的套件，NuGet 可現在其架構和設定檔將規則套用至所指定的資料夾名稱中的多個目標。</span><span class="sxs-lookup"><span data-stu-id="6bdaa-140">When installing the package that is created from this folder structure, NuGet can now apply its framework and profile rules to multiple targets, as specified in the folder name.</span></span>  <span data-ttu-id="6bdaa-141">後方 NuGet 的比對規則是 「 更特定的 「 目標將會優先 」 較不特定 」 的原則。</span><span class="sxs-lookup"><span data-stu-id="6bdaa-141">Behind NuGet’s matching rules is the principle that “more specific” targets will take precedence over “less specific” ones.</span></span>  <span data-ttu-id="6bdaa-142">這表示，以特定平台為目標的 moniker 會一律透過慣用可攜式電腦如果它們都相容的專案。</span><span class="sxs-lookup"><span data-stu-id="6bdaa-142">This means that monikers targeting a specific platform will always be preferred over portable ones if they are both compatible with a project.</span></span>  <span data-ttu-id="6bdaa-143">此外，如果多個可移植的目標相容的專案，NuGet 會偏好平台支援一組 「 最靠近 」 專案參考封裝所在的一個。</span><span class="sxs-lookup"><span data-stu-id="6bdaa-143">Additionally, if multiple portable targets are compatible with a project, NuGet will prefer the one where the set of platforms supported is “closest” to the project referencing the package.</span></span>

## <a name="targeting-windows-8-and-windows-phone-8-projects"></a><span data-ttu-id="6bdaa-144">目標的 Windows 8 和 Windows Phone 8 專案</span><span class="sxs-lookup"><span data-stu-id="6bdaa-144">Targeting Windows 8 and Windows Phone 8 Projects</span></span>
<span data-ttu-id="6bdaa-145">NuGet 2.1 除了新增目標可攜式程式庫專案的支援，Windows 8 市集和 Windows Phone 8 專案中，以及一些新的一般 moniker 的 Windows 市集和 Windows Phone 專案將會提供新的 framework moniker容易管理整個各自的平台的未來版本。</span><span class="sxs-lookup"><span data-stu-id="6bdaa-145">In addition to adding support for targeting portable library projects, NuGet 2.1 provides new framework monikers for both Windows 8 Store and Windows Phone 8 projects, as well as some new general monikers for Windows Store and Windows Phone projects that will be easier to manage across future versions of the respective platforms.</span></span>

<span data-ttu-id="6bdaa-146">對於 Windows 8 市集應用程式中，識別項，看起來像這樣：</span><span class="sxs-lookup"><span data-stu-id="6bdaa-146">For Windows 8 Store applications, the identifiers look as follows:</span></span>

|<span data-ttu-id="6bdaa-147">2.0 及更早版本的 NuGet</span><span class="sxs-lookup"><span data-stu-id="6bdaa-147">NuGet 2.0 and earlier</span></span>|<span data-ttu-id="6bdaa-148">NuGet 2.1</span><span class="sxs-lookup"><span data-stu-id="6bdaa-148">NuGet 2.1</span></span>|
|----------------|-----------|
|<span data-ttu-id="6bdaa-149">winRT45。NETCore45</span><span class="sxs-lookup"><span data-stu-id="6bdaa-149">winRT45, .NETCore45</span></span>|<span data-ttu-id="6bdaa-150">Windows，Windows8，win win8</span><span class="sxs-lookup"><span data-stu-id="6bdaa-150">Windows, Windows8, win, win8</span></span>|

<br/>
<span data-ttu-id="6bdaa-151">Windows Phone 專案的識別項，看起來像這樣：</span><span class="sxs-lookup"><span data-stu-id="6bdaa-151">For Windows Phone projects, the identifiers look as follows:</span></span>

|<span data-ttu-id="6bdaa-152">Phone OS</span><span class="sxs-lookup"><span data-stu-id="6bdaa-152">Phone OS</span></span>|<span data-ttu-id="6bdaa-153">2.0 及更早版本的 NuGet</span><span class="sxs-lookup"><span data-stu-id="6bdaa-153">NuGet 2.0 and earlier</span></span>|<span data-ttu-id="6bdaa-154">NuGet 2.1</span><span class="sxs-lookup"><span data-stu-id="6bdaa-154">NuGet 2.1</span></span>
|----------------|-----------|-----------|
|<span data-ttu-id="6bdaa-155">Windows Phone 7</span><span class="sxs-lookup"><span data-stu-id="6bdaa-155">Windows Phone 7</span></span>|<span data-ttu-id="6bdaa-156">silverlight3 wp</span><span class="sxs-lookup"><span data-stu-id="6bdaa-156">silverlight3-wp</span></span>|<span data-ttu-id="6bdaa-157">wp，wp7，WindowsPhone WindowsPhone7</span><span class="sxs-lookup"><span data-stu-id="6bdaa-157">wp, wp7, WindowsPhone, WindowsPhone7</span></span>|
|<span data-ttu-id="6bdaa-158">Windows Phone 7.5 (Mango)</span><span class="sxs-lookup"><span data-stu-id="6bdaa-158">Windows Phone 7.5 (Mango)</span></span>|<span data-ttu-id="6bdaa-159">silverilght4 wp71</span><span class="sxs-lookup"><span data-stu-id="6bdaa-159">silverilght4-wp71</span></span>|<span data-ttu-id="6bdaa-160">wp71 WindowsPhone71</span><span class="sxs-lookup"><span data-stu-id="6bdaa-160">wp71, WindowsPhone71</span></span>|
|<span data-ttu-id="6bdaa-161">Windows Phone 8</span><span class="sxs-lookup"><span data-stu-id="6bdaa-161">Windows Phone 8</span></span>|<span data-ttu-id="6bdaa-162">（不支援）</span><span class="sxs-lookup"><span data-stu-id="6bdaa-162">(not supported)</span></span>|<span data-ttu-id="6bdaa-163">wp8 WindowsPhone8</span><span class="sxs-lookup"><span data-stu-id="6bdaa-163">wp8, WindowsPhone8</span></span>|
<br/>
<span data-ttu-id="6bdaa-164">在所有上述變更，舊的架構名稱會繼續受到完整支援 NuGet 2.1。</span><span class="sxs-lookup"><span data-stu-id="6bdaa-164">In all of the above changes, the old framework names will continue to be fully supported by NuGet 2.1.</span></span>  <span data-ttu-id="6bdaa-165">起，新的名稱應該使用時，就能更穩定跨各平台的未來版本。</span><span class="sxs-lookup"><span data-stu-id="6bdaa-165">Moving forward, the new names should be used as they will be more stable across future versions of the respective platforms.</span></span> <span data-ttu-id="6bdaa-166">新的名稱會*不*是支援的 NuGet 2.1 之前的版本，不過，因此詳加規劃時，切換。</span><span class="sxs-lookup"><span data-stu-id="6bdaa-166">The new names will *not* be supported in versions of NuGet prior to 2.1, however, so plan accordingly for when to make the switch.</span></span>

## <a name="improved-search-in-package-manager-dialog"></a><span data-ttu-id="6bdaa-167">在封裝管理員 對話方塊中改進的搜尋</span><span class="sxs-lookup"><span data-stu-id="6bdaa-167">Improved Search in Package Manager Dialog</span></span>
<span data-ttu-id="6bdaa-168">過去的數個反覆項目，透過變更已經引進來大幅提升速度及相關性的封裝搜尋在 NuGet gallery。</span><span class="sxs-lookup"><span data-stu-id="6bdaa-168">Over the past several iterations, changes have been introduced to the NuGet gallery that greatly improved the speed and relevance of package searches.</span></span>  <span data-ttu-id="6bdaa-169">不過，這些增強功能只限於 nuget.org 的網站。</span><span class="sxs-lookup"><span data-stu-id="6bdaa-169">However, these improvements were limited to the nuget.org Web site.</span></span>  <span data-ttu-id="6bdaa-170">NuGet 2.1 改進的搜尋體驗可讓透過 [NuGet 封裝管理員] 對話方塊。</span><span class="sxs-lookup"><span data-stu-id="6bdaa-170">NuGet 2.1 makes the improved search experience available through the NuGet package manager dialog.</span></span>  <span data-ttu-id="6bdaa-171">例如，假設您想要尋找 Windows Azure 快取預覽封裝。</span><span class="sxs-lookup"><span data-stu-id="6bdaa-171">As an example, imagine that you wanted to find the Windows Azure Caching Preview package.</span></span>  <span data-ttu-id="6bdaa-172">合理的搜尋查詢，此套件可能是 「 Azure 快取 」。</span><span class="sxs-lookup"><span data-stu-id="6bdaa-172">A reasonable search query for this package may be “Azure Cache”.</span></span>  <span data-ttu-id="6bdaa-173">在舊版的 [封裝管理員] 對話方塊中，所需的封裝會不甚至會列在結果的第一頁。</span><span class="sxs-lookup"><span data-stu-id="6bdaa-173">In previous versions of the package manager dialog, the desired package would not even be listed on the first page of results.</span></span>  <span data-ttu-id="6bdaa-174">不過，在 NuGet 2.1 中，所需的套件現在會出現在搜尋結果的頂端。</span><span class="sxs-lookup"><span data-stu-id="6bdaa-174">However, in NuGet 2.1, the desired package now shows up at the top of the search results.</span></span>

![封裝管理員對話方塊搜尋](./media/releasenotes-21-vsdlg-search.png)

## <a name="force-package-update"></a><span data-ttu-id="6bdaa-176">強制執行封裝的更新</span><span class="sxs-lookup"><span data-stu-id="6bdaa-176">Force Package Update</span></span>
<span data-ttu-id="6bdaa-177">之前 NuGet 2.1，NuGet 會略過更新封裝時不高的版本號碼。</span><span class="sxs-lookup"><span data-stu-id="6bdaa-177">Prior to NuGet 2.1, NuGet would skip updating a package when there was a not a high version number.</span></span>  <span data-ttu-id="6bdaa-178">此導入了人事某些案例 – 特別在建置或 CI 案例，小組不想增加每個組建編號的封裝版本。</span><span class="sxs-lookup"><span data-stu-id="6bdaa-178">This introduced friction for certain scenarios – particularly in the case of build or CI scenarios where the team did not want to increment the package version number with each build.</span></span>  <span data-ttu-id="6bdaa-179">所要的行為就是強制更新而定。</span><span class="sxs-lookup"><span data-stu-id="6bdaa-179">The desired behavior was to force an update regardless.</span></span>  <span data-ttu-id="6bdaa-180">NuGet 2.1 可應付此 '重新安裝' 旗標。</span><span class="sxs-lookup"><span data-stu-id="6bdaa-180">NuGet 2.1 addresses this with the ‘reinstall’ flag.</span></span>  <span data-ttu-id="6bdaa-181">例如，舊版的 NuGet 會產生下列時嘗試更新沒有較新的封裝版本的套件：</span><span class="sxs-lookup"><span data-stu-id="6bdaa-181">For example, previous versions of NuGet would result in the following when attempting to update a package that did not have a more recent package version:</span></span>

    PM> Update-Package Moq
    No updates available for 'Moq' in project 'MySolution.MyConsole'.

<span data-ttu-id="6bdaa-182">重新安裝旗標，封裝將會更新而不論是否有為較新版本。</span><span class="sxs-lookup"><span data-stu-id="6bdaa-182">With the reinstall flag, the package will be updated regardless of whether there is a newer version.</span></span>

    PM> Update-Package Moq -Reinstall
    Successfully removed 'Moq 4.0.10827' from MySolution.MyConsole.
    Successfully uninstalled 'Moq 4.0.10827'.
    Successfully installed 'Moq 4.0.10827'.
    Successfully added 'Moq 4.0.10827' to MySolution.MyConsole.

<span data-ttu-id="6bdaa-183">重新安裝旗標可幫助證明另一種情況就是重新架構為目標。</span><span class="sxs-lookup"><span data-stu-id="6bdaa-183">Another scenario where the reinstall flag proves beneficial is that of framework re-targeting.</span></span> <span data-ttu-id="6bdaa-184">變更目標 framework 的專案 （例如，從.NET 4 為.NET 4.5)，當更新封裝的重新安裝可以更新所有 NuGet 封裝在專案中安裝正確的組件的參考。</span><span class="sxs-lookup"><span data-stu-id="6bdaa-184">When changing the target framework of a project (for example, from .NET 4 to .NET 4.5), Update-Package -Reinstall can update references to the correct assemblies for all NuGet packages installed in the project.</span></span>

## <a name="edit-package-sources-within-visual-studio"></a><span data-ttu-id="6bdaa-185">編輯 Visual Studio 中的封裝來源</span><span class="sxs-lookup"><span data-stu-id="6bdaa-185">Edit Package Sources Within Visual Studio</span></span>
<span data-ttu-id="6bdaa-186">在舊版的 NuGet 中，更新從套件來源中刪除並重新加入 [封裝來源所需的 Visual Studio 選項] 對話方塊。</span><span class="sxs-lookup"><span data-stu-id="6bdaa-186">In previous versions of NuGet, updating a package source from within the Visual Studio options dialog required deleting and re-adding the package source.</span></span>  <span data-ttu-id="6bdaa-187">NuGet 2.1 支援更新為第一級函式的組態使用者介面，以改善此工作流程。</span><span class="sxs-lookup"><span data-stu-id="6bdaa-187">NuGet 2.1 improves this workflow by supporting update as a first class function of the configuration user interface.</span></span>

![封裝管理員的組態對話方塊](./media/releasenotes-21-edit-pkg-source.png)

## <a name="bug-fixes"></a><span data-ttu-id="6bdaa-189">Bug 修正</span><span class="sxs-lookup"><span data-stu-id="6bdaa-189">Bug Fixes</span></span>
<span data-ttu-id="6bdaa-190">NuGet 2.1 包含括許多錯誤修正。</span><span class="sxs-lookup"><span data-stu-id="6bdaa-190">NuGet 2.1 includes many bug fixes.</span></span> <span data-ttu-id="6bdaa-191">如需完整的工作清單項目固定在 NuGet 2.0 中，請檢視[此版本的 NuGet Issue Tracker](http://nuget.codeplex.com/workitem/list/advanced?keyword=&status=Fixed&type=All&priority=All&release=NuGet%202.1&assignedTo=All&component=All&sortField=LastUpdatedDate&sortDirection=Descending&page=0)。</span><span class="sxs-lookup"><span data-stu-id="6bdaa-191">For a full list of work items fixed in NuGet 2.0, please view the [NuGet Issue Tracker for this release](http://nuget.codeplex.com/workitem/list/advanced?keyword=&status=Fixed&type=All&priority=All&release=NuGet%202.1&assignedTo=All&component=All&sortField=LastUpdatedDate&sortDirection=Descending&page=0).</span></span>