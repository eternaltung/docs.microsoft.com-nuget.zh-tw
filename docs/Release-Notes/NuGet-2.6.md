---
title: "NuGet 2.6 版本資訊 |Microsoft 文件"
author: karann-msft
ms.author: karann-msft
manager: ghogen
ms.date: 11/11/2016
ms.topic: article
ms.prod: nuget
ms.technology: 
ms.assetid: d99bbf29-2b9a-4dc5-a823-5eb4f9e30f7f
description: "包括已知的問題、 錯誤修正、 新增的功能，以及 Dcr NuGet 2.6 版本資訊。"
keywords: "NuGet 2.6 版本資訊，將 bug 修正、 已知問題、 已新增的功能，Dcr"
ms.reviewer:
- karann-msft
- unniravindranathan
ms.openlocfilehash: f93e34326aa9ab3d6bd5d1756126e6bfa24fd82e
ms.sourcegitcommit: d0ba99bfe019b779b75731bafdca8a37e35ef0d9
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/14/2017
---
# <a name="nuget-26-release-notes"></a><span data-ttu-id="e6da9-104">NuGet 2.6 版本資訊</span><span class="sxs-lookup"><span data-stu-id="e6da9-104">NuGet 2.6 Release Notes</span></span>

<span data-ttu-id="e6da9-105">[NuGet 2.5 版本資訊](../release-notes/nuget-2.5.md) | [NuGet 2.6.1 WebMatrix 版本資訊](../release-notes/nuget-2.6.1-for-webmatrix.md)</span><span class="sxs-lookup"><span data-stu-id="e6da9-105">[NuGet 2.5 Release Notes](../release-notes/nuget-2.5.md) | [NuGet 2.6.1 for WebMatrix Release Notes](../release-notes/nuget-2.6.1-for-webmatrix.md)</span></span>

<span data-ttu-id="e6da9-106">NuGet 2.6 已於 2013 年 6 月 26 日發行。</span><span class="sxs-lookup"><span data-stu-id="e6da9-106">NuGet 2.6 was released on June 26, 2013.</span></span>

## <a name="notable-features-in-the-release"></a><span data-ttu-id="e6da9-107">在版本中值得注意的功能</span><span class="sxs-lookup"><span data-stu-id="e6da9-107">Notable features in the release</span></span>

### <a name="support-for-visual-studio-2013"></a><span data-ttu-id="e6da9-108">Visual Studio 2013 的支援</span><span class="sxs-lookup"><span data-stu-id="e6da9-108">Support for Visual Studio 2013</span></span>

<span data-ttu-id="e6da9-109">NuGet 2.6 是第一次釋放所提供的 Visual Studio 2013 的支援。</span><span class="sxs-lookup"><span data-stu-id="e6da9-109">NuGet 2.6 is the first release that provides support for Visual Studio 2013.</span></span> <span data-ttu-id="e6da9-110">和 Visual Studio 2012，像是 NuGet 套件管理員擴充功能隨附於每個版本的 Visual Studio。</span><span class="sxs-lookup"><span data-stu-id="e6da9-110">And like Visual Studio 2012, the NuGet Package Manager extension is included in every edition of Visual Studio.</span></span>

<span data-ttu-id="e6da9-111">為了提供最佳的可能支援 Visual Studio 2013，同時仍然支援 Visual Studio 2010 和 Visual Studio 2012，並保持越小越好的延伸大小，我們會產生個別的擴充功能時的 Visual Studio 2013原始副檔名會繼續以 Visual Studio 2010 和 2012年為目標。</span><span class="sxs-lookup"><span data-stu-id="e6da9-111">In order to provide the best possible support for Visual Studio 2013 while still supporting both Visual Studio 2010 and Visual Studio 2012, and keeping the extension sizes as small as possible, we are producing a separate extension for Visual Studio 2013 while the original extension continues to target both Visual Studio 2010 and 2012.</span></span>

<span data-ttu-id="e6da9-112">從 NuGet 2.6 開始，我們將發佈兩個擴充功能，如下所示：</span><span class="sxs-lookup"><span data-stu-id="e6da9-112">Starting with NuGet 2.6, we will publish two extensions as below:</span></span>

1. <span data-ttu-id="e6da9-113">[NuGet 套件管理員](http://visualstudiogallery.msdn.microsoft.com/27077b70-9dad-4c64-adcf-c7cf6bc9970c/file/37502/30/NuGet.Tools.vsix)（適用於 Visual Studio 2010 和 2012年）</span><span class="sxs-lookup"><span data-stu-id="e6da9-113">[NuGet Package Manager](http://visualstudiogallery.msdn.microsoft.com/27077b70-9dad-4c64-adcf-c7cf6bc9970c/file/37502/30/NuGet.Tools.vsix) (applies to Visual Studio 2010 and 2012)</span></span>
2. [<span data-ttu-id="e6da9-114">Visual Studio 2013 的 NuGet 封裝管理員</span><span class="sxs-lookup"><span data-stu-id="e6da9-114">NuGet Package Manager for Visual Studio 2013</span></span>](http://visualstudiogallery.msdn.microsoft.com/4ec1526c-4a8c-4a84-b702-b21a8f5293ca)

<span data-ttu-id="e6da9-115">此分割中， [nuget.org](https://nuget.org)首頁的 「 安裝 NuGet 」 按鈕將立即帶您到[安裝 NuGet](../guides/install-nuget.md)頁面上，您可以在何處安裝不同的 NuGet 用戶端的相關資訊。</span><span class="sxs-lookup"><span data-stu-id="e6da9-115">With this split, the [nuget.org](https://nuget.org) home page's "Install NuGet" button will now take you to the [installing NuGet](../guides/install-nuget.md) page, where you can find more information about installing the different NuGet clients.</span></span>

<a name="xdt"></a>

### <a name="xdt-webconfig-transformation-support"></a><span data-ttu-id="e6da9-116">XDT Web.config 轉換的支援</span><span class="sxs-lookup"><span data-stu-id="e6da9-116">XDT Web.config transformation support</span></span>

<span data-ttu-id="e6da9-117">其中一個最高要求 NuGet 用戶端功能已支援使用 XDT 轉換引擎使用 Visual Studio 中的功能更強大的 XML 轉換[建置組態轉換](http://msdn.microsoft.com/library/dd465318(v=vs.100).aspx)。</span><span class="sxs-lookup"><span data-stu-id="e6da9-117">One of the most highly-requested features for the NuGet client has been to support more powerful XML transformations using the XDT transformation engine which is used in Visual Studio [build configuration transformations](http://msdn.microsoft.com/library/dd465318(v=vs.100).aspx).</span></span>
<span data-ttu-id="e6da9-118">在 2013 年 4 月中，我們所做的有關 XDT NuGet 支援兩個大公告。</span><span class="sxs-lookup"><span data-stu-id="e6da9-118">In April 2013, we made two big announcements regarding NuGet support for XDT.</span></span> <span data-ttu-id="e6da9-119">第一個已 XDT 程式庫本身已被本身[以 NuGet 套件形式發行](https://nuget.org/packages/Microsoft.Web.Xdt)和[開啟來源 CodePlex 上](http://xdt.codeplex.com/)。</span><span class="sxs-lookup"><span data-stu-id="e6da9-119">The first was that the XDT library itself was being itself [released as a NuGet package](https://nuget.org/packages/Microsoft.Web.Xdt) and [open sourced on CodePlex](http://xdt.codeplex.com/).</span></span> <span data-ttu-id="e6da9-120">此步驟中啟用 XDT 引擎，可供自由其他開放原始碼軟體，包括 NuGet 用戶端。</span><span class="sxs-lookup"><span data-stu-id="e6da9-120">This step enabled the XDT engine to be used freely by other open-source software, including the NuGet client.</span></span> <span data-ttu-id="e6da9-121">第二個宣告已計劃來支援 XDT 引擎使用 NuGet 用戶端中的轉換。</span><span class="sxs-lookup"><span data-stu-id="e6da9-121">The second announcement was the plan to support use of the XDT engine for transformations in the NuGet client.</span></span> <span data-ttu-id="e6da9-122">NuGet 2.6 包含這項整合。</span><span class="sxs-lookup"><span data-stu-id="e6da9-122">NuGet 2.6 includes this integration.</span></span>

#### <a name="how-it-works"></a><span data-ttu-id="e6da9-123">它的運作方式</span><span class="sxs-lookup"><span data-stu-id="e6da9-123">How it works</span></span>

<span data-ttu-id="e6da9-124">若要充分利用 NuGet 的 XDT 支援，機制尋找類似的[目前組態轉換功能](../create-packages/source-and-config-file-transformations.md)。</span><span class="sxs-lookup"><span data-stu-id="e6da9-124">To take advantage of NuGet’s XDT support, the mechanics look similar to those of the [current config transformation feature](../create-packages/source-and-config-file-transformations.md).</span></span>
<span data-ttu-id="e6da9-125">轉換檔案會新增至套件的內容資料夾。</span><span class="sxs-lookup"><span data-stu-id="e6da9-125">Transformation files are added to the package’s content folder.</span></span> <span data-ttu-id="e6da9-126">不過，設定轉換會使用單一檔案的安裝和解除安裝，而 XDT 轉換可讓更細微的控制這兩個這些處理程序使用下列檔案：</span><span class="sxs-lookup"><span data-stu-id="e6da9-126">However, while config transformations use a single file for both installation and uninstallation, XDT transformations enable fine-grained control over both of these processes using the following files:</span></span>

- <span data-ttu-id="e6da9-127">Web.config.install.xdt</span><span class="sxs-lookup"><span data-stu-id="e6da9-127">Web.config.install.xdt</span></span>
- <span data-ttu-id="e6da9-128">Web.config.uninstall.xdt</span><span class="sxs-lookup"><span data-stu-id="e6da9-128">Web.config.uninstall.xdt</span></span>

<span data-ttu-id="e6da9-129">此外，NuGet 會使用檔案後置字元來判斷哪些引擎來執行轉換，以便使用現有 web.config.transforms 封裝將會繼續運作。</span><span class="sxs-lookup"><span data-stu-id="e6da9-129">Additionally, NuGet uses the file suffix to determine which engine to run for transformations, so packages using the existing web.config.transforms will continue to work.</span></span> <span data-ttu-id="e6da9-130">XDT 可以也將轉換套用至任何 XML 檔案 (不只是 web.config)，因此您可以利用這其他應用程式專案中。</span><span class="sxs-lookup"><span data-stu-id="e6da9-130">XDT transformations can also be applied to any XML file (not just web.config), so you can leverage this for other applications in your project.</span></span>

#### <a name="what-you-can-do-with-xdt"></a><span data-ttu-id="e6da9-131">您可以使用達成 XDT</span><span class="sxs-lookup"><span data-stu-id="e6da9-131">What you can do with XDT</span></span>

<span data-ttu-id="e6da9-132">XDT 的最大優點的其中一個是其[簡單但強大的語法](http://msdn.microsoft.com/library/dd465326.aspx)管理結構的 XML dom。</span><span class="sxs-lookup"><span data-stu-id="e6da9-132">One of XDT’s greatest strengths is its [simple but powerful syntax](http://msdn.microsoft.com/library/dd465326.aspx) for manipulating the structure of an XML DOM.</span></span> <span data-ttu-id="e6da9-133">XDT 會提供用於比對中以各種方式，從簡單的屬性名稱比對的完整 XPath 支援的項目控制項而不是只覆疊拖曳至另一個結構的一個固定格式文件結構。</span><span class="sxs-lookup"><span data-stu-id="e6da9-133">Rather than simply overlaying one fixed document structure onto another structure, XDT provides controls for matching elements in a variety of ways, from simple attribute name matching to full XPath support.</span></span> <span data-ttu-id="e6da9-134">一旦找到相符的項目或項目集，XDT 提供一組豐富的函式操作項目，而不論其所指新增、 更新或移除屬性，將新的項目放在特定位置，或取代或移除整個元素和其子系。</span><span class="sxs-lookup"><span data-stu-id="e6da9-134">Once a matching element or set of elements is found, XDT provides a rich set of functions for manipulating the elements, whether that means adding, updating, or removing attributes, placing a new element at a specific location, or replacing or removing the entire element and its children.</span></span>

### <a name="machine-wide-configuration"></a><span data-ttu-id="e6da9-135">整部機器組態</span><span class="sxs-lookup"><span data-stu-id="e6da9-135">Machine-Wide Configuration</span></span>

<span data-ttu-id="e6da9-136">NuGet 的優點是它細分否則大型可執行檔或程式庫至一組可整合，以及最重要的是維護和版本建立個別的模組化元件。</span><span class="sxs-lookup"><span data-stu-id="e6da9-136">One of the great strengths of NuGet is that it breaks down an otherwise large executable or library into a set of modular components which can be integrated, and most importantly maintained and versioned independently.</span></span> <span data-ttu-id="e6da9-137">不過，它的一個副作用，會是產品或產品系列的傳統的做法可能會變得愈來愈分散。</span><span class="sxs-lookup"><span data-stu-id="e6da9-137">One side effect of this, however, is that the conventional idea of a product or product family becomes potentially more fragmented.</span></span>
<span data-ttu-id="e6da9-138">NuGet 的自訂封裝來源功能提供一個方式來組織封裝，不過，自訂封裝來源不是可自行探索。</span><span class="sxs-lookup"><span data-stu-id="e6da9-138">NuGet’s custom package source feature provides one way of organizing packages; however, custom package sources are not discoverable on their own.</span></span>

<span data-ttu-id="e6da9-139">NuGet 2.6 延伸設定 NuGet 搜尋路徑 %programdata%/nuget/config 下的資料夾階層的邏輯。產品安裝程式可以將此登錄其產品的自訂封裝來源 資料夾下的自訂 NuGet 組態檔案。</span><span class="sxs-lookup"><span data-stu-id="e6da9-139">NuGet 2.6 extends the logic for configuring NuGet by searching the folder hierarchy under the path %ProgramData%/NuGet/Config. Product installers can add custom NuGet configuration files under this folder to register a custom package source for their products.</span></span> <span data-ttu-id="e6da9-140">此外，資料夾結構支援語意的產品、 版本和 IDE 的甚至 SKU。</span><span class="sxs-lookup"><span data-stu-id="e6da9-140">Additionally, the folder structure supports semantics for product, version, and even SKU of the IDE.</span></span> <span data-ttu-id="e6da9-141">依下列順序使用的 「 上一次在 wins"優先順序策略會套用這些目錄中的設定。</span><span class="sxs-lookup"><span data-stu-id="e6da9-141">Settings from these directories are applied in the following order with a "last in wins" precedence strategy.</span></span>

1. <span data-ttu-id="e6da9-142">%ProgramData%\NuGet\Config\*.config</span><span class="sxs-lookup"><span data-stu-id="e6da9-142">%ProgramData%\NuGet\Config\*.config</span></span>
2. <span data-ttu-id="e6da9-143">%ProgramData%\NuGet\Config\{IDE}\*.config</span><span class="sxs-lookup"><span data-stu-id="e6da9-143">%ProgramData%\NuGet\Config\{IDE}\*.config</span></span>
3. <span data-ttu-id="e6da9-144">%ProgramData%\NuGet\Config\{IDE}\{版本}\*.config</span><span class="sxs-lookup"><span data-stu-id="e6da9-144">%ProgramData%\NuGet\Config\{IDE}\{Version}\*.config</span></span>
4. <span data-ttu-id="e6da9-145">%ProgramData%\NuGet\Config\{IDE}\{版本}\{SKU}\*.config</span><span class="sxs-lookup"><span data-stu-id="e6da9-145">%ProgramData%\NuGet\Config\{IDE}\{Version}\{SKU}\*.config</span></span>

<span data-ttu-id="e6da9-146">在此清單中，以便在 Visual Studio 中，它將會是"VisualStudio"，為特定 NuGet 執行中，在 IDE {IDE} 預留位置。</span><span class="sxs-lookup"><span data-stu-id="e6da9-146">In this list, the {IDE} placeholder is specific to the IDE in which NuGet is running, so in the case of Visual Studio, it will be "VisualStudio".</span></span> <span data-ttu-id="e6da9-147">{版本} 和 {SKU} 預留位置 （例如提供 IDE"11.0"和"WDExpress"、"VWDExpress 」 和 「 Pro"，分別)。</span><span class="sxs-lookup"><span data-stu-id="e6da9-147">The {Version} and {SKU} placeholders are provided by the IDE (e.g. "11.0" and "WDExpress", "VWDExpress" and "Pro", respectively).</span></span> <span data-ttu-id="e6da9-148">資料夾可以再包含許多不同的 *.config 檔案。</span><span class="sxs-lookup"><span data-stu-id="e6da9-148">The folder can then contain many different *.config files.</span></span>
<span data-ttu-id="e6da9-149">因此，ACME 元件公司可以其產品安裝程式的過程中，加入自訂的套件來源將會是檢視只能在 Visual Studio 2012 Professional 和 Ultimate 版本中建立下列檔案路徑：</span><span class="sxs-lookup"><span data-stu-id="e6da9-149">Therefore, the ACME component company can, as a part of their product installer, add a custom package source which will be visible only in the Professional and Ultimate versions of Visual Studio 2012 by creating the following file path:</span></span>

<span data-ttu-id="e6da9-150">%ProgramData%\NuGet\Config\VisualStudio\11.0\Pro\acme.config</span><span class="sxs-lookup"><span data-stu-id="e6da9-150">%ProgramData%\NuGet\Config\VisualStudio\11.0\Pro\acme.config</span></span>

<span data-ttu-id="e6da9-151">NuGet 組態對話方塊時的資料夾結構可讓您可以直接軟體安裝程式，將整個電腦的封裝來源新增至 NuGet 的設定類似的程式，也允許做為封裝來源註冊更新其中一個特定使用者 （例如註冊 %appdata%/nuget/nuget.config 中） 或整部機器。</span><span class="sxs-lookup"><span data-stu-id="e6da9-151">While the folder structure makes it straightforward for programs like software installers to add machine-wide package sources to NuGet's configuration, the NuGet configuration dialog has also been updated to allow for the registration of package sources as either user-specific (e.g. registered in %AppData%/NuGet/NuGet.Config) or machine-wide.</span></span>

<span data-ttu-id="e6da9-152">Visual Studio 2013 中，檔案會安裝在使用這項功能：</span><span class="sxs-lookup"><span data-stu-id="e6da9-152">This feature is utilized by Visual Studio 2013, where a file is installed at:</span></span>

<span data-ttu-id="e6da9-153">%ProgramData%\NuGet\Config\VisualStudio\12.0\Microsoft.VisualStudio.config</span><span class="sxs-lookup"><span data-stu-id="e6da9-153">%ProgramData%\NuGet\Config\VisualStudio\12.0\Microsoft.VisualStudio.config</span></span>

<span data-ttu-id="e6da9-154">在這個檔案中，新的封裝來源，稱為 「.NET Framework 套件 」 設定。</span><span class="sxs-lookup"><span data-stu-id="e6da9-154">Within this file, a new package source called ".NET Framework Packages" is configured.</span></span>

![NuGet 組態檔的電腦的各種設定](./media/NuGet-Config-File-Machine-Wide.png)

### <a name="contextualizing-search"></a><span data-ttu-id="e6da9-156">Contextualizing 搜尋</span><span class="sxs-lookup"><span data-stu-id="e6da9-156">Contextualizing Search</span></span>

<span data-ttu-id="e6da9-157">由在 NuGet gallery 的封裝數目仍指數的速度成長，改善搜尋會保持為曾經 NuGet 優先順序清單的頂端。</span><span class="sxs-lookup"><span data-stu-id="e6da9-157">As the number of packages served by the NuGet gallery continues to grow at an exponential pace, improving search remains ever at the top of the NuGet priority list.</span></span> <span data-ttu-id="e6da9-158">NuGet 的計劃功能之一是搜尋的專案的內容中搜尋，這表示 NuGet 將使用做為準則的版本與 SKU 的 Visual Studio 所使用，以及您要建置類型的相關資訊來判斷可能相關性結果。</span><span class="sxs-lookup"><span data-stu-id="e6da9-158">One of the planned features for NuGet is contextual search, meaning that NuGet will use information about the version and SKU of Visual Studio that you are using and the type of project that you are building as criteria for determining the relevance of potential search results.</span></span>

<span data-ttu-id="e6da9-159">從 NuGet 2.6 開始，已安裝封裝，每次安裝內容會記錄為安裝操作資料的一部分。</span><span class="sxs-lookup"><span data-stu-id="e6da9-159">Starting with NuGet 2.6, each time a package is installed, the context for the installation is recorded as part of the installation operation data.</span></span>  <span data-ttu-id="e6da9-160">搜尋也會傳送相同的內容資訊，可在 NuGet Gallery，提高內容安裝趨勢的搜尋結果。</span><span class="sxs-lookup"><span data-stu-id="e6da9-160">Searches also send the same context information, which will allow the NuGet Gallery to boost search results by contextual installation trends.</span></span>  <span data-ttu-id="e6da9-161">在 NuGet Gallery 的未來更新會啟用此內容相關的相關性提高。</span><span class="sxs-lookup"><span data-stu-id="e6da9-161">A future update to the NuGet Gallery will enable this context-sensitive relevance boosting.</span></span>

### <a name="tracking-direct-installs-vs-dependency-installs"></a><span data-ttu-id="e6da9-162">追蹤直接安裝 vs。相依性安裝</span><span class="sxs-lookup"><span data-stu-id="e6da9-162">Tracking Direct Installs vs. Dependency Installs</span></span>

<span data-ttu-id="e6da9-163">封裝的作者越來越多依賴在[封裝統計資料](http://blog.nuget.org/20130226/Introducing-Package-Statistics.html)在 NuGet Gallery 上提供。</span><span class="sxs-lookup"><span data-stu-id="e6da9-163">Package authors are relying more and more on the [Package Statistics](http://blog.nuget.org/20130226/Introducing-Package-Statistics.html) provided on the NuGet Gallery.</span></span>  <span data-ttu-id="e6da9-164">其中一個重要的遺漏資料點作者需要的是直接的封裝會安裝與相依性安裝之間的差異。</span><span class="sxs-lookup"><span data-stu-id="e6da9-164">One significant missing data point that authors have asked for is a differentiation between direct package installs and dependency installs.</span></span>  <span data-ttu-id="e6da9-165">到目前為止，NuGet 用戶端未傳送任何內容周圍是否開發人員直接安裝封裝，或如果在安裝滿足相依性的安裝作業。</span><span class="sxs-lookup"><span data-stu-id="e6da9-165">Until now, the NuGet client did not send any context around the installation operation for whether the developer directly installed the package or if it was installed to satisfy a dependency.</span></span>
<span data-ttu-id="e6da9-166">從 NuGet 2.6，現在會將資料傳送為安裝操作。</span><span class="sxs-lookup"><span data-stu-id="e6da9-166">Starting with NuGet 2.6, that data will now be sent for the installation operation.</span></span>  <span data-ttu-id="e6da9-167">封裝在 NuGet Gallery 上的統計資料會公開做為個別的安裝作業，該資料與 「-相依性"後置詞。</span><span class="sxs-lookup"><span data-stu-id="e6da9-167">Package Statistics on the NuGet Gallery will expose that data as separate install operations, with a "-Dependency" suffix.</span></span>

* <span data-ttu-id="e6da9-168">安裝</span><span class="sxs-lookup"><span data-stu-id="e6da9-168">Install</span></span>
* <span data-ttu-id="e6da9-169">安裝相依性</span><span class="sxs-lookup"><span data-stu-id="e6da9-169">Install-Dependency</span></span>
* <span data-ttu-id="e6da9-170">更新</span><span class="sxs-lookup"><span data-stu-id="e6da9-170">Update</span></span>
* <span data-ttu-id="e6da9-171">更新相依性</span><span class="sxs-lookup"><span data-stu-id="e6da9-171">Update-Dependency</span></span>
* <span data-ttu-id="e6da9-172">重新安裝</span><span class="sxs-lookup"><span data-stu-id="e6da9-172">Reinstall</span></span>
* <span data-ttu-id="e6da9-173">重新安裝相依性</span><span class="sxs-lookup"><span data-stu-id="e6da9-173">Reinstall-Dependency</span></span>

<span data-ttu-id="e6da9-174">除了不同的作業名稱，也會針對安裝記錄相依的套件識別碼。</span><span class="sxs-lookup"><span data-stu-id="e6da9-174">In addition to the different operation name, the dependent package id is also recorded for the installation.</span></span>  <span data-ttu-id="e6da9-175">在 NuGet Gallery 的未來更新將會公開在報表中，可讓封裝作者以充分了解如何開發人員要安裝其封裝資料。</span><span class="sxs-lookup"><span data-stu-id="e6da9-175">A future update to the NuGet Gallery will expose that data within reports, allowing package authors to fully understand how developers are installing their packages.</span></span>

## <a name="bug-fixes"></a><span data-ttu-id="e6da9-176">Bug 修正</span><span class="sxs-lookup"><span data-stu-id="e6da9-176">Bug Fixes</span></span>

<span data-ttu-id="e6da9-177">NuGet 2.6 也包含數個 bug 修正。</span><span class="sxs-lookup"><span data-stu-id="e6da9-177">NuGet 2.6 also includes several bug fixes.</span></span> <span data-ttu-id="e6da9-178">如需完整的工作清單項目固定在 NuGet 2.6，請檢視[此版本的 NuGet Issue Tracker](https://nuget.codeplex.com/workitem/list/advanced?keyword=&status=Closed&type=All&priority=All&release=NuGet%202.6&assignedTo=All&component=All&sortField=LastUpdatedDate&sortDirection=Descending&page=0&reasonClosed=All)。</span><span class="sxs-lookup"><span data-stu-id="e6da9-178">For a full list of work items fixed in NuGet 2.6, please view the [NuGet Issue Tracker for this release](https://nuget.codeplex.com/workitem/list/advanced?keyword=&status=Closed&type=All&priority=All&release=NuGet%202.6&assignedTo=All&component=All&sortField=LastUpdatedDate&sortDirection=Descending&page=0&reasonClosed=All).</span></span>