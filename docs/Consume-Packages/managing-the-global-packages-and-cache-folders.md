---
title: 如何在 NuGet 中管理全域套件、快取、暫存資料夾 | Microsoft Docs
author: kraigb
ms.author: kraigb
manager: ghogen
ms.date: 03/19/2018
ms.topic: article
ms.prod: nuget
ms.technology: ''
description: 如何管理全域套件安裝資料夾、套件快取，以及安裝、還原和更新套件時存在電腦上的暫存資料夾。
keywords: NuGet 全域套件資料夾, NuGet 套件快取, 套件快取, 套件安裝資料夾, NuGet 快取, 管理快取, 本機 NuGet 快取, 全域 NuGet 快取, NuGet locals 命令, 清除快取
ms.reviewer:
- karann-msft
- unniravindranathan
ms.openlocfilehash: e9f4383a3f1700b96e3d6fe9ea4c0a7c24daa45a
ms.sourcegitcommit: beb229893559824e8abd6ab16707fd5fe1c6ac26
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/28/2018
---
# <a name="managing-the-global-packages-cache-and-temp-folders"></a><span data-ttu-id="125eb-104">管理全域套件、快取和暫存資料夾</span><span class="sxs-lookup"><span data-stu-id="125eb-104">Managing the global packages, cache, and temp folders</span></span>

<span data-ttu-id="125eb-105">當您安裝、更新或還原套件時，NuGet 會管理專案結構之外數個資料夾中的套件和套件資訊：</span><span class="sxs-lookup"><span data-stu-id="125eb-105">Whenever you install, update, or restore a package, NuGet manages packages and package information in several folders outside of your project structure:</span></span>

| <span data-ttu-id="125eb-106">名稱</span><span class="sxs-lookup"><span data-stu-id="125eb-106">Name</span></span> | <span data-ttu-id="125eb-107">描述和位置 (依使用者)</span><span class="sxs-lookup"><span data-stu-id="125eb-107">Description and Location (per user)</span></span>|
| --- | --- |
| <span data-ttu-id="125eb-108">global&#8209;packages</span><span class="sxs-lookup"><span data-stu-id="125eb-108">global&#8209;packages</span></span> | <span data-ttu-id="125eb-109">*global-packages* 資料夾是 NuGet 安裝下載套件的位置。</span><span class="sxs-lookup"><span data-stu-id="125eb-109">The *global-packages* folder is where NuGet installs any downloaded package.</span></span> <span data-ttu-id="125eb-110">每個套件已經完全展開至符合套件識別碼和版本號碼的子資料夾。</span><span class="sxs-lookup"><span data-stu-id="125eb-110">Each package is fully expanded into a subfolder that matches the package identifier and version number.</span></span> <span data-ttu-id="125eb-111">使用 PackageReference 格式的專案一律使用直接從這個資料夾取得的套件。</span><span class="sxs-lookup"><span data-stu-id="125eb-111">Projects using the PackageReference format always use packages directly from this folder.</span></span> <span data-ttu-id="125eb-112">當使用 `packages.config` 時，套件會安裝到 *global-packages* 資料夾，然後複製到專案的 `packages` 資料夾。</span><span class="sxs-lookup"><span data-stu-id="125eb-112">When using the `packages.config`, packages are installed to the *global-packages* folder, then copied into the project's `packages` folder.</span></span><br/><ul><li><span data-ttu-id="125eb-113">Windows：`%userprofile%\.nuget\packages`</span><span class="sxs-lookup"><span data-stu-id="125eb-113">Windows: `%userprofile%\.nuget\packages`</span></span></li><li><span data-ttu-id="125eb-114">Mac/Linux：`~/.nuget/packages`</span><span class="sxs-lookup"><span data-stu-id="125eb-114">Mac/Linux: `~/.nuget/packages`</span></span></li><li><span data-ttu-id="125eb-115">使用 NUGET_PACKAGES 環境變數、`globalPackagesFolder` 或 `repositoryPath` [組態設定](../reference/nuget-config-file.md#config-section) (當分別使用 PackageReference 和 `packages.config` 時)，或 `RestorePackagesPath` MSBuild 屬性 (僅限 MSBuild) 來覆寫。</span><span class="sxs-lookup"><span data-stu-id="125eb-115">Override using the NUGET_PACKAGES environment variable, the `globalPackagesFolder` or `repositoryPath` [configuration settings](../reference/nuget-config-file.md#config-section) (when using PackageReference and `packages.config`, respectively), or the `RestorePackagesPath` MSBuild property (MSBuild only).</span></span> <span data-ttu-id="125eb-116">環境變數的優先性高於組態設定。</span><span class="sxs-lookup"><span data-stu-id="125eb-116">The environment variable takes precedence over the configuration setting.</span></span></li></ul> |
| <span data-ttu-id="125eb-117">http&#8209;cache</span><span class="sxs-lookup"><span data-stu-id="125eb-117">http&#8209;cache</span></span> | <span data-ttu-id="125eb-118">Visual Studio 套件管理員 (NuGet 3.x+) 和 `dotnet` 工具會將下載的套件複本存放在此快取中 (另存為 `.dat` 檔案)，並組織到每個套件來源的子資料夾。</span><span class="sxs-lookup"><span data-stu-id="125eb-118">The Visual Studio Package Manager (NuGet 3.x+) and the `dotnet` tool store copies of downloaded packages in this cache (saved as `.dat` files), organized into subfolders for each package source.</span></span> <span data-ttu-id="125eb-119">套件不會展開，而且快取的到期時間為 30 分鐘。</span><span class="sxs-lookup"><span data-stu-id="125eb-119">Packages are not expanded, and the cache has an expiration time of 30 minutes.</span></span><br/><ul><li><span data-ttu-id="125eb-120">Windows：`%localappdata%\NuGet\v3-cache`</span><span class="sxs-lookup"><span data-stu-id="125eb-120">Windows: `%localappdata%\NuGet\v3-cache`</span></span></li><li><span data-ttu-id="125eb-121">Mac/Linux：`~/.local/share/NuGet/v3-cache`</span><span class="sxs-lookup"><span data-stu-id="125eb-121">Mac/Linux: `~/.local/share/NuGet/v3-cache`</span></span></li><li><span data-ttu-id="125eb-122">使用 NUGET_HTTP_CACHE_PATH 環境變數來覆寫。</span><span class="sxs-lookup"><span data-stu-id="125eb-122">Override using the NUGET_HTTP_CACHE_PATH environment variable.</span></span></li></ul> |
| <span data-ttu-id="125eb-123">temp</span><span class="sxs-lookup"><span data-stu-id="125eb-123">temp</span></span> | <span data-ttu-id="125eb-124">NuGet 在其各種作業期間存放暫存檔的資料夾。</span><span class="sxs-lookup"><span data-stu-id="125eb-124">A folder where NuGet stores temporary files during its various operations.</span></span><br/><li><span data-ttu-id="125eb-125">Windows：`%temp%\NuGetScratch`</span><span class="sxs-lookup"><span data-stu-id="125eb-125">Windows: `%temp%\NuGetScratch`</span></span></li><li><span data-ttu-id="125eb-126">Mac/Linux：`/tmp/NuGetScratch`</span><span class="sxs-lookup"><span data-stu-id="125eb-126">Mac/Linux: `/tmp/NuGetScratch`</span></span></li></ul> |

> [!Note]
> <span data-ttu-id="125eb-127">NuGet 3.5 和更早版本使用的是 *packages-cache*，而非位於 `%localappdata%\NuGet\Cache` 中的 *http-cache*。</span><span class="sxs-lookup"><span data-stu-id="125eb-127">NuGet 3.5 and earlier uses *packages-cache* instead of the *http-cache*, which is located in `%localappdata%\NuGet\Cache`.</span></span>

<span data-ttu-id="125eb-128">NuGet 通常可使用快取和 *global-packages* 資料夾，以避免下載已經存在於電腦上的套件，藉此改善安裝、更新及還原作業的效能。</span><span class="sxs-lookup"><span data-stu-id="125eb-128">By using the cache and *global-packages* folders, NuGet generally avoids downloading packages that already exist on the computer, improving the performance of install, update, and restore operations.</span></span> <span data-ttu-id="125eb-129">當使用 PackageReference 時，*global-packages* 資料夾也可避免將下載的套件保留在專案資料夾內 (以免可能會不小心新增到原始檔控制中)，並降低 NuGet 對電腦儲存體的整體影響。</span><span class="sxs-lookup"><span data-stu-id="125eb-129">When using PackageReference, the *global-packages* folder also avoids keeping downloaded packages inside project folders, where they might be inadvertently added to source control, and reduces NuGet's overall impact on computer storage.</span></span>

<span data-ttu-id="125eb-130">NuGet 需要擷取套件時，首先會尋找 *global-packages* 資料夾。</span><span class="sxs-lookup"><span data-stu-id="125eb-130">When asked to retrieve a package, NuGet first looks in the *global-packages* folder.</span></span> <span data-ttu-id="125eb-131">如果套件的正確版本不存在，NuGet 便會檢查所有非 HTTP 套件來源。</span><span class="sxs-lookup"><span data-stu-id="125eb-131">If the exact version of package is not there, then NuGet checks all non-HTTP package sources.</span></span> <span data-ttu-id="125eb-132">如果仍然找不到套件，除非您使用 `dotnet.exe` 命令指定 `--no-cache`或使用 `nuget.exe` 命令指定 `-NoCache`，否則 NuGet 會尋找 *http-cache* 中的套件。</span><span class="sxs-lookup"><span data-stu-id="125eb-132">If the package is still not found, NuGet looks for the package in the *http-cache* unless you specify `--no-cache` with `dotnet.exe` commands or `-NoCache` with `nuget.exe` commands.</span></span> <span data-ttu-id="125eb-133">如果套件不在快取中，或者未使用快取，則 NuGet 會透過 HTTP 擷取套件。</span><span class="sxs-lookup"><span data-stu-id="125eb-133">If the package is not in the cache, or the cache isn't used, NuGet then retrieves the package over HTTP .</span></span>

<span data-ttu-id="125eb-134">如需詳細資訊，請參閱[安裝套件時會發生什麼事](ways-to-install-a-package.md#what-happens-when-a-package-is-installed)。</span><span class="sxs-lookup"><span data-stu-id="125eb-134">For more information, see [What happens when a package is installed](ways-to-install-a-package.md#what-happens-when-a-package-is-installed).</span></span>

## <a name="viewing-folder-locations"></a><span data-ttu-id="125eb-135">檢視資料夾位置</span><span class="sxs-lookup"><span data-stu-id="125eb-135">Viewing folder locations</span></span>

<span data-ttu-id="125eb-136">您可以使用 [dotnet nuget locals 命令](/dotnet/core/tools/dotnet-nuget-locals) 來檢視資料夾位置：</span><span class="sxs-lookup"><span data-stu-id="125eb-136">You can view folder locations using the [dotnet nuget locals command](/dotnet/core/tools/dotnet-nuget-locals):</span></span>

```cli
dotnet nuget locals all --list
```

<span data-ttu-id="125eb-137">一般輸出 (Mac/Linux；"user1" 是目前使用者名稱)：</span><span class="sxs-lookup"><span data-stu-id="125eb-137">Typical output (Mac/Linux; "user1" is the current username):</span></span>

```output
info : http-cache: /home/user1/.local/share/NuGet/v3-cache
info : global-packages: /home/user1/.nuget/packages/
info : temp: /tmp/NuGetScratch
```

<span data-ttu-id="125eb-138">若要顯示單一資料夾的位置，請使用 `http-cache`、`global-packages` 或 `temp`，不要使用 `all`。</span><span class="sxs-lookup"><span data-stu-id="125eb-138">To display the location of a single folder, use `http-cache`, `global-packages`, or `temp` instead of `all`.</span></span> 

<span data-ttu-id="125eb-139">您也可以使用 [nuget locals 命令](../tools/cli-ref-locals.md)來檢視位置：</span><span class="sxs-lookup"><span data-stu-id="125eb-139">You also view locations using the [nuget locals command](../tools/cli-ref-locals.md):</span></span>

```cli
# Display locals for all folders: global-packages, cache, and temp
nuget locals all -list
```

<span data-ttu-id="125eb-140">一般輸出 (Windows；"user1" 是目前使用者名稱)：</span><span class="sxs-lookup"><span data-stu-id="125eb-140">Typical output (Windows; "user1" is the current username):</span></span>

```output
http-cache: C:\Users\user1\AppData\Local\NuGet\v3-cache
global-packages: C:\Users\user1\.nuget\packages\
temp: C:\Users\user1\AppData\Local\Temp\NuGetScratch
```

<span data-ttu-id="125eb-141">(`package-cache` 使用於 NuGet 2.x 中，並在 NuGet 3.5 及更早版本中出現)。</span><span class="sxs-lookup"><span data-stu-id="125eb-141">(`package-cache` is used in NuGet 2.x and appears with NuGet 3.5 and earlier.)</span></span>

## <a name="clearing-local-folders"></a><span data-ttu-id="125eb-142">清除本機資料夾</span><span class="sxs-lookup"><span data-stu-id="125eb-142">Clearing local folders</span></span>

<span data-ttu-id="125eb-143">如果遇到套件安裝問題，或想要確保安裝的是遠端資源庫的套件，請使用 `locals --clear` 選項 (dotnet.exe) 或 `locals -clear` (nuget.exe)，指定要清除的資料夾，或 `all` 以清除所有資料夾：</span><span class="sxs-lookup"><span data-stu-id="125eb-143">If you encounter package installation problems or otherwise want to ensure that you're installing packages from a remote gallery, use the `locals --clear` option (dotnet.exe) or `locals -clear` (nuget.exe), specifying the folder to clear, or `all` to clear all folders:</span></span>

```cli
# Clear the 3.x+ cache (use either command)
dotnet nuget locals http-cache --clear
nuget locals http-cache -clear

# Clear the 2.x cache (NuGet CLI 3.5 and earlier only)
nuget locals packages-cache -clear

# Clear the global packages folder (use either command)
dotnet nuget locals global-packages --clear
nuget locals global-packages -clear

# Clear the temporary cache (use either command)
dotnet nuget locals temp --clear
nuget locals temp -clear

# Clear all caches (use either command)
dotnet nuget locals all --clear
nuget locals all -clear
```

<span data-ttu-id="125eb-144">目前在 Visual Studio 中開啟且由專案使用的任何套件不會從 *global-packages* 資料夾清除。</span><span class="sxs-lookup"><span data-stu-id="125eb-144">Any packages used by projects that are currently open in Visual Studio are not cleared from the *global-packages* folder.</span></span>

<span data-ttu-id="125eb-145">在 Visual Studio 中，使用 [工具] > [NuGet 套件管理員] > [套件管理員設定] 功能表命令，然後選取 [清除所有 NuGet 快取]。</span><span class="sxs-lookup"><span data-stu-id="125eb-145">In Visual Studio, use the **Tools > NuGet Package Manager > Package Manager Settings** menu command, then select **Clear All NuGet Cache(s)**.</span></span> <span data-ttu-id="125eb-146">目前無法透過套件管理員主控台來管理快取。</span><span class="sxs-lookup"><span data-stu-id="125eb-146">Managing the cache isn't presently available through the Package Manager Console.</span></span>

![用來清除快取的 NuGet 選項命令](media/options-clear-caches.png)

## <a name="troubleshooting-errors"></a><span data-ttu-id="125eb-148">疑難排解錯誤</span><span class="sxs-lookup"><span data-stu-id="125eb-148">Troubleshooting errors</span></span>

<span data-ttu-id="125eb-149">使用 `nuget locals` 或 `dotnet nuget locals` 時，可能會發生下列錯誤：</span><span class="sxs-lookup"><span data-stu-id="125eb-149">The following errors can occur when using `nuget locals` or `dotnet nuget locals`:</span></span>

- <span data-ttu-id="125eb-150">錯誤：「處理序無法存取檔案 <package> 因為其他處理序正在使用它」，或者「清除本機資源失敗：無法刪除一或多個檔案」</span><span class="sxs-lookup"><span data-stu-id="125eb-150">*Error: The process cannot access the file <package> because it is being used by another process* or *Clearing local resources failed: Unable to delete one or more files*</span></span>

    <span data-ttu-id="125eb-151">其他處理序正在使用資料夾內的一或多個檔案；例如，Visual Studio 專案已開啟，其中參照 *global-packages* 資料夾中的套件。</span><span class="sxs-lookup"><span data-stu-id="125eb-151">One or more files in the folder are in use by another process; for example, a Visual Studio project is open that refers to packages in the *global-packages* folder.</span></span> <span data-ttu-id="125eb-152">關閉這些處理序，並再試一次。</span><span class="sxs-lookup"><span data-stu-id="125eb-152">Close those processes and try again.</span></span>

- <span data-ttu-id="125eb-153">錯誤：「存取路徑 <path> 遭到拒絕」或者「目錄不是空的」</span><span class="sxs-lookup"><span data-stu-id="125eb-153">*Error: Access to the path <path> is denied* or *The directory is not empty*</span></span>

    <span data-ttu-id="125eb-154">您沒有刪除此快取中檔案的權限。</span><span class="sxs-lookup"><span data-stu-id="125eb-154">You don't have permission to delete files in the cache.</span></span> <span data-ttu-id="125eb-155">如果可能，請變更資料夾權限，並再試一次。</span><span class="sxs-lookup"><span data-stu-id="125eb-155">Change the folder permissions, if possible, and try again.</span></span> <span data-ttu-id="125eb-156">否則，請洽詢系統管理員。</span><span class="sxs-lookup"><span data-stu-id="125eb-156">Otherwise, contact your system administrator.</span></span>

- <span data-ttu-id="125eb-157">錯誤：「指定的路徑、檔案名稱或兩者都太長。完整的檔名必須少於 260 個字元，並且目錄名稱必須少於 248 個字元。」</span><span class="sxs-lookup"><span data-stu-id="125eb-157">*Error: The specified path, file name, or both are too long. The fully qualified file name must be less than 260 characters, and the directory name must be less than 248 characters.*</span></span>

    <span data-ttu-id="125eb-158">請縮短資料夾名稱，並再試一次。</span><span class="sxs-lookup"><span data-stu-id="125eb-158">Shorten the folder names and try again.</span></span>