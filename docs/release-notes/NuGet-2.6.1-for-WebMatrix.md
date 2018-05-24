---
title: NuGet 2.6.1 WebMatrix 版本資訊
description: Webmatrix 包括已知的問題、 錯誤修正、 新增的功能，以及 Dcr NuGet 2.6.1 的版本資訊。
author: karann-msft
ms.author: karann
manager: unnir
ms.date: 11/11/2016
ms.topic: conceptual
ms.openlocfilehash: 3d767788d348553cbb5cb82c6f70aac1894628c3
ms.sourcegitcommit: 3eab9c4dd41ea7ccd2c28bb5ab16f6fbbec13708
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/26/2018
---
# <a name="nuget-261-for-webmatrix-release-notes"></a><span data-ttu-id="47990-103">NuGet 2.6.1 WebMatrix 版本資訊</span><span class="sxs-lookup"><span data-stu-id="47990-103">NuGet 2.6.1 for WebMatrix Release Notes</span></span>

<span data-ttu-id="47990-104">[NuGet 2.6 版本資訊](../release-notes/nuget-2.6.md) | [NuGet 2.7 版本資訊](../release-notes/nuget-2.7.md)</span><span class="sxs-lookup"><span data-stu-id="47990-104">[NuGet 2.6 Release Notes](../release-notes/nuget-2.6.md) | [NuGet 2.7 Release Notes](../release-notes/nuget-2.7.md)</span></span>

<span data-ttu-id="47990-105">NuGet 小組發行於 2014 年 3 月 26 日更新的 NuGet 套件管理員擴充 WebMatrix。</span><span class="sxs-lookup"><span data-stu-id="47990-105">The NuGet team released an updated NuGet Package Manager extension for WebMatrix on March 26, 2014.</span></span>  <span data-ttu-id="47990-106">可以從安裝此更新[WebMatrix 擴充程式庫](https://blogs.iis.net/webmatrix/retiring-the-webmatrix-extensions-gallery)使用下列步驟：</span><span class="sxs-lookup"><span data-stu-id="47990-106">This update can be installed from the [WebMatrix Extension Gallery](https://blogs.iis.net/webmatrix/retiring-the-webmatrix-extensions-gallery) using the following steps:</span></span>

1. <span data-ttu-id="47990-107">開啟 WebMatrix 3</span><span class="sxs-lookup"><span data-stu-id="47990-107">Open WebMatrix 3</span></span>
1. <span data-ttu-id="47990-108">按一下 [首頁] 功能區中的擴充功能圖示</span><span class="sxs-lookup"><span data-stu-id="47990-108">Click the Extensions icon in the Home ribbon</span></span>
1. <span data-ttu-id="47990-109">選取 [更新] 索引標籤</span><span class="sxs-lookup"><span data-stu-id="47990-109">Select the Updates tab</span></span>
1. <span data-ttu-id="47990-110">按一下以更新 2.6.1 NuGet 封裝管理員</span><span class="sxs-lookup"><span data-stu-id="47990-110">Click to update NuGet Package Manager to 2.6.1</span></span>
1. <span data-ttu-id="47990-111">關閉並重新啟動 WebMatrix 3</span><span class="sxs-lookup"><span data-stu-id="47990-111">Close and restart WebMatrix 3</span></span>

## <a name="notable-changes"></a><span data-ttu-id="47990-112">值得注意的變更</span><span class="sxs-lookup"><span data-stu-id="47990-112">Notable Changes</span></span>

<span data-ttu-id="47990-113">最大問題使用者此擴充功能更新解決兩個具有面臨取用 NuGet 封裝在 WebMatrix 內。</span><span class="sxs-lookup"><span data-stu-id="47990-113">This extension update addresses two of the biggest issues users have faced consuming NuGet packages within WebMatrix.</span></span>  <span data-ttu-id="47990-114">第一個是 NuGet 結構描述版本錯誤，且第二個前置零位元組 dll 的 bug`bin`資料夾。</span><span class="sxs-lookup"><span data-stu-id="47990-114">The first was a NuGet schema version error and the second was a bug leading to zero-byte DLLs in the `bin` folder.</span></span>

### <a name="nuget-schema-version-error"></a><span data-ttu-id="47990-115">NuGet 的結構描述版本錯誤</span><span class="sxs-lookup"><span data-stu-id="47990-115">NuGet Schema Version Error</span></span>

<span data-ttu-id="47990-116">自 WebMatrix 3 發行以來，已引進新的功能到新的結構描述版本所需的 NuGet 套件的 NuGet。</span><span class="sxs-lookup"><span data-stu-id="47990-116">Since WebMatrix 3 was released, new features have been introduced into NuGet that require a new schema version for the NuGet packages.</span></span>  <span data-ttu-id="47990-117">管理網站中的 NuGet 封裝時，這些新的封裝可能會導致您在 WebMatrix 中看到的錯誤。</span><span class="sxs-lookup"><span data-stu-id="47990-117">When trying to manage your NuGet packages in your web site, these new packages can lead to errors that you see in WebMatrix.</span></span>

![發生錯誤。](./media/NuGet-2.8/webmatrix-schema-version.png)

<span data-ttu-id="47990-121">這個最新版本提供的最新的 NuGet 套件，防止發生這個錯誤與相容性。</span><span class="sxs-lookup"><span data-stu-id="47990-121">This latest release provides compatibility with the newest NuGet packages, preventing this error from occurring.</span></span> <span data-ttu-id="47990-122">現在可以在 WebMatrix 安裝包括 Microsoft.AspNet.WebPages 套件的新版本。</span><span class="sxs-lookup"><span data-stu-id="47990-122">New versions of packages including Microsoft.AspNet.WebPages can now be installed in WebMatrix.</span></span>  <span data-ttu-id="47990-123">這些封裝的某些已使用 NuGet 功能，例如[XDT config 轉換](../release-notes/nuget-2.6.md#xdt)，這不支援在 WebMatrix 到目前為止。</span><span class="sxs-lookup"><span data-stu-id="47990-123">Some of these packages were using NuGet features such as [XDT config transforms](../release-notes/nuget-2.6.md#xdt), which wasn't supported in WebMatrix until now.</span></span>

### <a name="zero-byte-dlls-in-bin-folder"></a><span data-ttu-id="47990-124">Bin 資料夾中的零位元組 Dll</span><span class="sxs-lookup"><span data-stu-id="47990-124">Zero-Byte DLLs in bin Folder</span></span>

<span data-ttu-id="47990-125">某些使用者回報，之後安裝 NuGet 套件中包含 Dll 複製到 bin，WebMatrix Dll 顯示`bin`0 個位元組的檔案與資料夾。</span><span class="sxs-lookup"><span data-stu-id="47990-125">Some users have reported that after installing NuGet packages in WebMatrix that include DLLs that get copied to bin, that the DLLs show up in the `bin` folder as 0-byte files.</span></span>  <span data-ttu-id="47990-126">這會中斷應用程式在執行階段。</span><span class="sxs-lookup"><span data-stu-id="47990-126">This breaks the application at runtime.</span></span>

<span data-ttu-id="47990-127">[此問題](https://nuget.codeplex.com/workitem/4060)現在已修正。</span><span class="sxs-lookup"><span data-stu-id="47990-127">[This issue](https://nuget.codeplex.com/workitem/4060) has now been fixed.</span></span>

## <a name="other-recent-improvements"></a><span data-ttu-id="47990-128">其他最新的增強功能</span><span class="sxs-lookup"><span data-stu-id="47990-128">Other Recent Improvements</span></span>

<span data-ttu-id="47990-129">NuGet 封裝管理員 2.8 已發行適用於 Visual Studio，我們也會發行 NuGet 套件管理員 2.5.0 for WebMatrix。</span><span class="sxs-lookup"><span data-stu-id="47990-129">When NuGet Package Manager 2.8 was released for Visual Studio, we also released NuGet Package Manager 2.5.0 for WebMatrix.</span></span>  <span data-ttu-id="47990-130">雖然這在提到[NuGet 2.8 版本資訊](../release-notes/nuget-2.8.md#webmatrix-nuget-client-updates)，我們沒有提到特定的新功能導入了該更新。</span><span class="sxs-lookup"><span data-stu-id="47990-130">While this was mentioned in the [NuGet 2.8 Release Notes](../release-notes/nuget-2.8.md#webmatrix-nuget-client-updates), we didn't mention the specific new features that update introduced.</span></span>

### <a name="update-all"></a><span data-ttu-id="47990-131">更新所有</span><span class="sxs-lookup"><span data-stu-id="47990-131">Update All</span></span>

<span data-ttu-id="47990-132">您現在可以更新的所有網站的封裝，以一個步驟 ！</span><span class="sxs-lookup"><span data-stu-id="47990-132">You can now update all of your web site's packages in one step!</span></span>  <span data-ttu-id="47990-133">當您在 WebMatrix 中開啟 NuGet 延伸模組時，您會看到所有的封裝清單上的組件庫，安裝，以及具有可用的更新。</span><span class="sxs-lookup"><span data-stu-id="47990-133">When you open the NuGet extension in WebMatrix, you see the list of all packages on the gallery, those installed, and the ones with updates available.</span></span>  <span data-ttu-id="47990-134">之前，必須個別更新每個套件，但現在是有用的 [更新全部] 按鈕，就會出現在 [更新] 索引標籤。</span><span class="sxs-lookup"><span data-stu-id="47990-134">Previously, every package would have to be updated individually but now there is a useful "Update All" button that shows up on the Updates tab.</span></span>

![按一下 全部更新使用可用的更新來更新所有的封裝](./media/NuGet-2.8/webmatrix-update-all.png)

### <a name="overwrite-existing-files"></a><span data-ttu-id="47990-136">覆寫現有檔案</span><span class="sxs-lookup"><span data-stu-id="47990-136">Overwrite Existing Files</span></span>

<span data-ttu-id="47990-137">安裝封裝，其中包含存在於您的網站的檔案時，NuGet 就是一律只以無訊息方式略過這些檔案 （保留現有的檔案）。</span><span class="sxs-lookup"><span data-stu-id="47990-137">When installing packages that contain files that already exist in your web site, NuGet has always just silently ignored those files (leaving your existing files alone).</span></span>  <span data-ttu-id="47990-138">這可能會導致印象封裝已安裝，或當實際上它未正確更新。</span><span class="sxs-lookup"><span data-stu-id="47990-138">This could lead to the impression that a package was installed or updated correctly when in fact it wasn't.</span></span>  <span data-ttu-id="47990-139">NuGet 現在會提示輸入覆寫檔案。</span><span class="sxs-lookup"><span data-stu-id="47990-139">NuGet will now prompt for files to be overwritten.</span></span>

![解決檔案衝突](./media/NuGet-2.8/webmatrix-overwrite-file.png)