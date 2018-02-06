---
title: "什麼是 NuGet？它有哪些功能？ | Microsoft Docs"
author: kraigb
ms.author: kraigb
manager: ghogen
ms.date: 10/26/2017
ms.topic: hero-article
ms.prod: nuget
ms.technology: 
ms.assetid: c3faf278-4cbf-4733-96f6-9ee9f7203af9
description: "何謂 NuGet 和其功能的完整介紹"
keywords: "NuGet 套件管理員、使用、套件建立、套件裝載"
ms.reviewer:
- karann-msft
- unniravindranathan
ms.openlocfilehash: 2bc6a9e154df287fee6a7e00cc1349dfa2100643
ms.sourcegitcommit: a40c1c1cc05a46410f317a72f695ad1d80f39fa2
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 01/05/2018
---
# <a name="an-introduction-to-nuget"></a><span data-ttu-id="91474-105">NuGet 簡介</span><span class="sxs-lookup"><span data-stu-id="91474-105">An introduction to NuGet</span></span>

<span data-ttu-id="91474-106">任何新式開發平台的基本工具都是一種機制，而開發人員可以透過此機制建立、共用和使用實用的程式碼。</span><span class="sxs-lookup"><span data-stu-id="91474-106">An essential tool for any modern development platform is a mechanism through which developers can create, share, and consume useful  code.</span></span> <span data-ttu-id="91474-107">這類程式碼通常會打包成「套件」，其中包含已編譯程式碼 (如 DLL)，以及在取用這些套件之專案中所需的內容。</span><span class="sxs-lookup"><span data-stu-id="91474-107">Often such code is bundled into a "packages" that contain compiled code (as DLLs) along with other content needed in the projects that consume these packages.</span></span>

<span data-ttu-id="91474-108">針對 .NET，共用程式碼的機制是 **NuGet**，其定義如何建立、裝載和使用 .NET 的套件，並提供所有這些角色的工具。</span><span class="sxs-lookup"><span data-stu-id="91474-108">For .NET, the mechanism for sharing code is **NuGet**, which defines how packages for .NET are created, hosted, and consumed, and provides the tools for each of those roles.</span></span> 

<span data-ttu-id="91474-109">簡言之，NuGet 套件就是副檔名為 `.nupkg` 的單一 ZIP 檔案，內含已編譯程式碼 (DLL)、其他與該程式碼相關的檔案，以及包含套件版本號碼這類資訊的描述性資訊清單。</span><span class="sxs-lookup"><span data-stu-id="91474-109">Put simply, a NuGet package is a single ZIP file with the `.nupkg` extension that contains compiled code (DLLs), other files related to that code, and a descriptive manifest that includes information like the package's version number.</span></span> <span data-ttu-id="91474-110">程式庫開發人員建立套件檔案，並將其發行至主機。</span><span class="sxs-lookup"><span data-stu-id="91474-110">Library developers create package files and publish them to a host.</span></span> <span data-ttu-id="91474-111">套件取用者會收到這些套件，並將它們新增至其專案，然後在其專案程式碼中呼叫該程式庫功能。</span><span class="sxs-lookup"><span data-stu-id="91474-111">Package consumers receive those packages, add them to their projects, and then call that library's functionality in their project code.</span></span> <span data-ttu-id="91474-112">NuGet 本身接著會處理所有中間詳細資料。</span><span class="sxs-lookup"><span data-stu-id="91474-112">NuGet itself then handles all of the intermediate details.</span></span>

## <a name="the-flow-of-packages-between-creators-hosts-and-consumers"></a><span data-ttu-id="91474-113">建立者、主機和取用者之間的套件流程</span><span class="sxs-lookup"><span data-stu-id="91474-113">The flow of packages between creators, hosts, and consumers</span></span>

<span data-ttu-id="91474-114">NuGet 的角色是主機，因此本身會在 [nuget.org](https://www.nuget.org) 維護超過 60,000 個唯一公開可用套件的中央存放庫。每天都會有數百萬位 .NET 開發人員採用這些套件。</span><span class="sxs-lookup"><span data-stu-id="91474-114">In its role as host, NuGet itself maintains the central repository of over 60,000 unique, publicly-available packages at [nuget.org](https://www.nuget.org). These packages are employed by millions of .NET developers every day.</span></span> <span data-ttu-id="91474-115">NuGet 也可讓您在雲端、私人網路甚至只在本機檔案系統中私下裝載套件。</span><span class="sxs-lookup"><span data-stu-id="91474-115">NuGet also enables you to host packages privately in the cloud, on a private network, or even on just your local file system.</span></span> <span data-ttu-id="91474-116">如此一來，只有特定組織或客戶群組內的開發人員才能使用這些套件。</span><span class="sxs-lookup"><span data-stu-id="91474-116">By doing so, those packages are available to only those developers within a particular organization or customer group.</span></span> <span data-ttu-id="91474-117">[裝載您自己的 NuGet 摘要](Hosting-Packages/Overview.md)會說明這些選項。</span><span class="sxs-lookup"><span data-stu-id="91474-117">The options are explained on [Hosting your own NuGet feeds](Hosting-Packages/Overview.md).</span></span>

<span data-ttu-id="91474-118">不管其本質為何，主機都是作為套件「建立者」與套件「取用者」之間的連線點。</span><span class="sxs-lookup"><span data-stu-id="91474-118">Whatever its nature, a host serves as a point of connection between package *creators* and package *consumers*.</span></span> <span data-ttu-id="91474-119">建立者會建置有用的 NuGet 套件，並將其發行至主機。</span><span class="sxs-lookup"><span data-stu-id="91474-119">Creators build useful NuGet packages and publish them to a host.</span></span> <span data-ttu-id="91474-120">取用者接著會搜尋可存取主機上的實用和相容套件，並下載這些套件且將其包含在專案中。</span><span class="sxs-lookup"><span data-stu-id="91474-120">Consumers then search for useful and compatible packages on accessible hosts, downloading and including those packages in their projects.</span></span> <span data-ttu-id="91474-121">一旦安裝於專案，套件的 API 就可供專案程式碼的其餘部分使用。</span><span class="sxs-lookup"><span data-stu-id="91474-121">Once installed in a project, the packages' APIs are available to the rest of the project code.</span></span>

![套件建立者、套件主機與套件取用者之間的關聯性](media/nuget-roles.png)

<span data-ttu-id="91474-123">在此情況下，「相容」套件表示它包含針對與取用中專案目標架構相容的至少一個目標 .NET Framework 所建置的組件。</span><span class="sxs-lookup"><span data-stu-id="91474-123">A "compatible" package in this case means that it contains assemblies built for at least one target .NET framework that's compatible with the consuming project's target framework.</span></span> <span data-ttu-id="91474-124">若要可讓套件廣泛相容，其建立者會編譯各種目標架構的不同組件，並將它們全部併入相同的套件中。</span><span class="sxs-lookup"><span data-stu-id="91474-124">To make a package widely compatible, its creator compiles separate assemblies for various target frameworks and includes all of them in the same package.</span></span> <span data-ttu-id="91474-125">取用者安裝該套件時，NuGet 只會擷取專案所需的組件。</span><span class="sxs-lookup"><span data-stu-id="91474-125">When a consumer installs that package, NuGet extracts only those assemblies that are needed by the project.</span></span> <span data-ttu-id="91474-126">在該專案所產生的最終應用程式和 (或) 組件中，這可將套件的用量降到最低。</span><span class="sxs-lookup"><span data-stu-id="91474-126">This minimizes the package's footprint in the final application and/or assemblies produced by that project.</span></span>

## <a name="nuget-tools"></a><span data-ttu-id="91474-127">NuGet 工具</span><span class="sxs-lookup"><span data-stu-id="91474-127">NuGet tools</span></span>

<span data-ttu-id="91474-128">除了裝載支援之外，NuGet 也提供建立者和取用者所使用的各種工具：</span><span class="sxs-lookup"><span data-stu-id="91474-128">In addition to hosting support, NuGet also provides a variety of tools used by both creators and consumers:</span></span>

| <span data-ttu-id="91474-129">工具</span><span class="sxs-lookup"><span data-stu-id="91474-129">Tool</span></span> | <span data-ttu-id="91474-130">平台</span><span class="sxs-lookup"><span data-stu-id="91474-130">Platforms</span></span> | <span data-ttu-id="91474-131">適用的案例</span><span class="sxs-lookup"><span data-stu-id="91474-131">Applicable Scenarios</span></span> | <span data-ttu-id="91474-132">描述</span><span class="sxs-lookup"><span data-stu-id="91474-132">Description</span></span> |
| --- | --- | --- | --- |
| [<span data-ttu-id="91474-133">nuget.exe CLI</span><span class="sxs-lookup"><span data-stu-id="91474-133">nuget.exe CLI</span></span>](Tools/nuget-exe-CLI-Reference.md) | <span data-ttu-id="91474-134">全部</span><span class="sxs-lookup"><span data-stu-id="91474-134">All</span></span> | <span data-ttu-id="91474-135">建立、使用</span><span class="sxs-lookup"><span data-stu-id="91474-135">Creation, Consumption</span></span> | <span data-ttu-id="91474-136">提供所有 NuGet 功能，而且有些命令專門套用至套件建立者、有些命令只套用至取用者，其他命令則套用至兩者。</span><span class="sxs-lookup"><span data-stu-id="91474-136">Provides all NuGet capabilities, with some commands applying specifically to package creators, some applying only to consumers, and others applying to both.</span></span> <span data-ttu-id="91474-137">例如，套件建立者使用 `nuget pack` 命令以從各種組件和相關檔案建立套件、套件取用者使用 `nuget install` 以將套件納入專案，而每個人都使用 `nuget config` 來設定 NuGet 組態變數。</span><span class="sxs-lookup"><span data-stu-id="91474-137">For example, package creators use the `nuget pack` command to create a package from various assemblies and related files, package consumers use `nuget install` to include packages in a project, and everyone uses `nuget config` to set NuGet configuration variables.</span></span>  |
| [<span data-ttu-id="91474-138">套件管理員 UI</span><span class="sxs-lookup"><span data-stu-id="91474-138">Package Manager UI</span></span>](Tools/Package-Manager-UI.md) | <span data-ttu-id="91474-139">Windows 上的 Visual Studio</span><span class="sxs-lookup"><span data-stu-id="91474-139">Visual Studio on Windows</span></span> | <span data-ttu-id="91474-140">使用</span><span class="sxs-lookup"><span data-stu-id="91474-140">Consumption</span></span> | <span data-ttu-id="91474-141">提供易用 UI，以在 .NET 專案中安裝和管理套件。</span><span class="sxs-lookup"><span data-stu-id="91474-141">Provides an easy-to-use UI for installing and managing packages in .NET projects.</span></span> | 
| [<span data-ttu-id="91474-142">管理 NuGet UI</span><span class="sxs-lookup"><span data-stu-id="91474-142">Manage NuGet UI</span></span>](/visualstudio/mac/nuget-walkthrough) | <span data-ttu-id="91474-143">Visual Studio for Mac</span><span class="sxs-lookup"><span data-stu-id="91474-143">Visual Studio for Mac</span></span> | <span data-ttu-id="91474-144">使用</span><span class="sxs-lookup"><span data-stu-id="91474-144">Consumption</span></span> | <span data-ttu-id="91474-145">提供易用 UI，以在 .NET 專案中安裝和管理套件。</span><span class="sxs-lookup"><span data-stu-id="91474-145">Provide an easy-to-use UI for installing and managing packages in .NET projects.</span></span> |
| [<span data-ttu-id="91474-146">套件管理員主控台</span><span class="sxs-lookup"><span data-stu-id="91474-146">Package Manager Console</span></span>](Tools/Package-Manager-Console.md) | <span data-ttu-id="91474-147">Windows 上的 Visual Studio</span><span class="sxs-lookup"><span data-stu-id="91474-147">Visual Studio on Windows</span></span> | <span data-ttu-id="91474-148">使用</span><span class="sxs-lookup"><span data-stu-id="91474-148">Consumption</span></span> | <span data-ttu-id="91474-149">提供 [PowerShell 命令](Tools/Powershell-Reference.md)，以在 .NET 專案中安裝和管理套件。</span><span class="sxs-lookup"><span data-stu-id="91474-149">Provides [PowerShell commands](Tools/Powershell-Reference.md) for installing and managing packages in .NET projects.</span></span> | 
| [<span data-ttu-id="91474-150">dotnet CLI</span><span class="sxs-lookup"><span data-stu-id="91474-150">dotnet CLI</span></span>](Tools/dotnet-Commands.md) | <span data-ttu-id="91474-151">全部</span><span class="sxs-lookup"><span data-stu-id="91474-151">All</span></span> | <span data-ttu-id="91474-152">建立、使用</span><span class="sxs-lookup"><span data-stu-id="91474-152">Creation, Consumption</span></span> | <span data-ttu-id="91474-153">在 .NET Core 工具鏈內，直接提供特定 NuGet CLI 功能。</span><span class="sxs-lookup"><span data-stu-id="91474-153">Provides certain NuGet CLI capabilities directly within the .NET Core toolchain.</span></span> |
| [<span data-ttu-id="91474-154"> MSBuild</span><span class="sxs-lookup"><span data-stu-id="91474-154">MSBuild</span></span>](Schema/msbuild-targets.md) | <span data-ttu-id="91474-155">Windows</span><span class="sxs-lookup"><span data-stu-id="91474-155">Windows</span></span> | <span data-ttu-id="91474-156">建立、使用</span><span class="sxs-lookup"><span data-stu-id="91474-156">Creation, Consumption</span></span> | <span data-ttu-id="91474-157">可以建立套件，以及還原透過 MSBuild 工具鏈直接用於專案的套件。</span><span class="sxs-lookup"><span data-stu-id="91474-157">Provides the ability to create packages and restore packages used in a project directly through the MSBuild toolchain.</span></span> |

<span data-ttu-id="91474-158">如您所見，用來處理 NuGet 的工具大部分取決於建立 (和發行) 套件還是使用套件，以及您所工作的平台。</span><span class="sxs-lookup"><span data-stu-id="91474-158">As you can see, the tools with which you work with NuGet depend greatly on whether you're creating (and publishing) packages or consuming them, and the platform you're working on.</span></span> <span data-ttu-id="91474-159">在[套件建立工作流程](Create-Packages/Overview-and-Workflow.md)和[套件使用工作流程](Consume-Packages/Overview-and-Workflow.md)主題，以及這些章節中的其他主題，可以找到更具體的詳細資料。</span><span class="sxs-lookup"><span data-stu-id="91474-159">More specific details can be found in the [Package creation workflow](Create-Packages/Overview-and-Workflow.md) and [Package consumption workflow](Consume-Packages/Overview-and-Workflow.md) topics, along with other topics in those sections.</span></span> 

<span data-ttu-id="91474-160">套件建立者通常也是取用者，因為他們是以其他 NuGet 套件的現有功能為建置基礎。</span><span class="sxs-lookup"><span data-stu-id="91474-160">Package creators are typically also consumers, as they build on top of functionality that exists in other NuGet packages.</span></span> <span data-ttu-id="91474-161">當然，這些套件可能接著會與其他項目相依。</span><span class="sxs-lookup"><span data-stu-id="91474-161">And those packages, of course, may in turn depend on still others.</span></span>

## <a name="managing-dependencies"></a><span data-ttu-id="91474-162">管理相依性</span><span class="sxs-lookup"><span data-stu-id="91474-162">Managing dependencies</span></span>

<span data-ttu-id="91474-163">以其他人的工作為基礎輕鬆進行建置的能力，是讓套件管理系統功能強大的其中一項。</span><span class="sxs-lookup"><span data-stu-id="91474-163">The ability to easily build on the work of others is one of the things that makes a package management system so powerful.</span></span> <span data-ttu-id="91474-164">因此，大部分 NuGet 功能都會代表您的專案來管理相依性樹狀結構或「圖形」。</span><span class="sxs-lookup"><span data-stu-id="91474-164">Accordingly, much of what NuGet does is managing that dependency tree or "graph" on behalf of your project.</span></span> <span data-ttu-id="91474-165">簡言之，您只需要讓自己關注在專案中直接使用的套件。</span><span class="sxs-lookup"><span data-stu-id="91474-165">Simply said, you need only concern yourself with those packages that you're directly using in a project.</span></span> <span data-ttu-id="91474-166">如果所有這些套件本身都使用其他套件 (其可使用套件)，則 NuGet 會負責所有這些下層相依性。</span><span class="sxs-lookup"><span data-stu-id="91474-166">If any of those packages themselves consume other packages (which can consume packages), NuGet takes care of all those down-level dependencies.</span></span>

<span data-ttu-id="91474-167">下圖顯示與五個套件相依的專案，而這五個套件接著與許多其他套件相依。</span><span class="sxs-lookup"><span data-stu-id="91474-167">The following image shows a project that depends on five packages, which in turn depend on a number of others.</span></span>  

![.NET 專案的範例 NuGet 相依性圖形](media/dependency-graph.png)

<span data-ttu-id="91474-169">請注意，在相依性圖形中，有些套件會出現多次。</span><span class="sxs-lookup"><span data-stu-id="91474-169">Notice that some packages appear multiple times in the dependency graph.</span></span> <span data-ttu-id="91474-170">例如，套件 B 有三個不同的取用者，而每個取用者也可能為該套件 (未顯示) 指定不同的版本。</span><span class="sxs-lookup"><span data-stu-id="91474-170">For example, there are three different consumers of package B, and each consumer might also specify a different version for that package (not shown).</span></span> <span data-ttu-id="91474-171">因為這經常發生，所以 NuGet 幸運地會執行所有困難的工作，以確切判斷哪個版本的套件 B 符合其所有取用者。</span><span class="sxs-lookup"><span data-stu-id="91474-171">Because this is a common occurrence, NuGet fortunately does all the hard work to determine exactly which version of package B satisfies all its consumers.</span></span> <span data-ttu-id="91474-172">不管相依性圖形的深度為何，NuGet 接著都會對所有其他套件執行相同作業。</span><span class="sxs-lookup"><span data-stu-id="91474-172">NuGet then does the same for all other packages, no matter how deep the dependency graph becomes.</span></span>

<span data-ttu-id="91474-173">如需 NuGet 如何執行這項服務的詳細資料，請參閱[相依性解析](Consume-Packages/Dependency-Resolution.md)。</span><span class="sxs-lookup"><span data-stu-id="91474-173">For more details on how NuGet performs this service, see [Dependency resolution](Consume-Packages/Dependency-Resolution.md).</span></span>

## <a name="tracking-references-and-restoring-packages"></a><span data-ttu-id="91474-174">追蹤參考和還原套件</span><span class="sxs-lookup"><span data-stu-id="91474-174">Tracking references and restoring packages</span></span>

<span data-ttu-id="91474-175">因為專案可以輕鬆地在開發人員電腦、原始檔控制存放庫、組建伺服器等等之間移動，所以極適合保留來自直接繫結至專案之 NuGet 套件的二進位組件。</span><span class="sxs-lookup"><span data-stu-id="91474-175">Because projects can easily move between developer computers, source control repositories, build servers, and so forth, it's highly impractical to keep binary assemblies from NuGet packages directly bound to a project.</span></span> <span data-ttu-id="91474-176">這不僅會讓專案的每個複本不必要的膨脹 (因而浪費原始檔控制存放庫中的空間)，也會很難將套件二進位檔更新為較新版本，因為這需要跨專案的所有複本來完成。</span><span class="sxs-lookup"><span data-stu-id="91474-176">Not only would this make each copy of the project unnecessarily bloated (and thereby waste space in source control repositories), it would also make it very difficult to update package binaries to newer versions as this would have to be done across all copies of the project.</span></span> 

<span data-ttu-id="91474-177">相反地，NuGet 只會維護專案所相依之套件的參考清單 (包含最上層和下層相依性)，並提供方法，以在要求時還原所有參考的套件，如[套件還原](Consume-Packages/Package-Restore.md)中所述。</span><span class="sxs-lookup"><span data-stu-id="91474-177">Instead, NuGet simply maintains a reference list of the packages upon which a project depends (including both top-level and down-level dependencies), and provides the means to restore all referenced packages upon request as described on [Package restore](Consume-Packages/Package-Restore.md).</span></span> <span data-ttu-id="91474-178">也就是說，只要您將套件從某個主機安裝至專案，NuGet 就會在此參考清單中記錄套件識別碼和版本號碼 </span><span class="sxs-lookup"><span data-stu-id="91474-178">That is, whenever you install a package from some host into a project, NuGet records the package identifier and version number in this reference list.</span></span> <span data-ttu-id="91474-179">(當然，解除安裝套件會將它從清單中移除)。</span><span class="sxs-lookup"><span data-stu-id="91474-179">(Uninstalling a package, of course, removes it from the list.)</span></span> 

![在套件安裝時會建立 NuGet 參考清單，並且可以用來在其他位置還原套件](media/nuget-restore.png)

<span data-ttu-id="91474-181">只有參考清單時，NuGet 稍後隨時可以從公用和 (或) 私用主機重新安裝 (即還原) 所有這些套件 </span><span class="sxs-lookup"><span data-stu-id="91474-181">With only the reference list, NuGet can then reinstall&mdash;that is, restore&mdash;all of those packages from public and/or private hosts at any later time.</span></span> <span data-ttu-id="91474-182">(因此，nuget.org 不允許永久刪除已發行的套件，但可以將它們隱藏；請參閱[刪除套件](Policies/deleting-packages.md))。將專案認可到原始檔控制或以某種其他方式進行共用時，只需要包含參考清單，而且不需要包含任何套件二進位檔 (請參閱[套件和原始檔控制](Consume-Packages/Packages-and-Source-Control.md))。</span><span class="sxs-lookup"><span data-stu-id="91474-182">(For this reason, nuget.org does not allow permanent deletion of published packages, although they can be hidden; see [Deleting packages](Policies/deleting-packages.md).) When committing a project to source control, or sharing it in some other way, you need only include the reference list and need not include any package binaries (see [Packages and source control](Consume-Packages/Packages-and-Source-Control.md).)</span></span>

<span data-ttu-id="91474-183">接收專案的電腦 (例如，在自動部署系統期間取得專案複本的組建伺服器) 只會要求 NuGet 在必要時還原相依性。</span><span class="sxs-lookup"><span data-stu-id="91474-183">The computer that receives a project, such as a build server obtaining a copy of the project as part of an automated deployment system, simply asks NuGet to restore dependencies whenever they're needed.</span></span> <span data-ttu-id="91474-184">針對這個確切的用途，Visual Studio Team Services 這類組建系統會提供「NuGet 還原」步驟。</span><span class="sxs-lookup"><span data-stu-id="91474-184">Build systems like Visual Studio Team Services provide "NuGet restore" steps for this exact purpose.</span></span> <span data-ttu-id="91474-185">同樣地，如果開發人員取得專案的複本 (複製存放庫時)，然後在 Visual Studio 中開啟專案並執行建置，則 Visual Studio 會自動還原必要的 NuGet 套件。</span><span class="sxs-lookup"><span data-stu-id="91474-185">Similarly, when developers obtain a copy of a project (as when cloning a repository) then open the project in Visual Studio and run a build, Visual Studio automatically restores the necessary NuGet packages.</span></span> <span data-ttu-id="91474-186">開發人員也可以隨時在套件管理員主控台中使用 `nuget restore` CLI 命令或 `Install-Package` Cmdlet，告知 NuGet 還原套件。</span><span class="sxs-lookup"><span data-stu-id="91474-186">Developers can also tell NuGet to restore packages at any time using the `nuget restore` CLI command or the `Install-Package` cmdlet in the Package Manager Console.</span></span>

<span data-ttu-id="91474-187">清楚的是，開發人員所關注的 NuGet 主要角色將會代表您的專案維護該參考清單，並提供方式，以有效率地還原 (和更新) 這些參考的套件。</span><span class="sxs-lookup"><span data-stu-id="91474-187">Clearly, then, NuGet's primary role where developers are concerned is maintaining that reference list on behalf of your project and providing the means to efficiently restore (and update) those referenced packages.</span></span>

<span data-ttu-id="91474-188">其確切運作方式已歷經不同版本的 NuGet，因而導致數個*套件管理格式*，它們稱為：</span><span class="sxs-lookup"><span data-stu-id="91474-188">How this exactly happens has evolved over the different versions of NuGet, resulting in several *package management formats*, as they're called:</span></span>

- <span data-ttu-id="91474-189">[`packages.config`](Schema/packages-config.md)：*(NuGet 1.0+)* 一個 XML 檔案，維護專案中所有相依性的一般清單，內含其他已安裝套件的相依性。</span><span class="sxs-lookup"><span data-stu-id="91474-189">[`packages.config`](Schema/packages-config.md): *(NuGet 1.0+)* An XML file that maintains a flat list of all dependencies in the project, including the dependencies of other installed packages.</span></span> 
- <span data-ttu-id="91474-190">[`project.json`](Schema/project-json.md)：*(NuGet 3.0+)* 一個 JSON 檔案，維護相關檔案 `project.lock.json` 中專案與整體套件圖形的相依性清單。</span><span class="sxs-lookup"><span data-stu-id="91474-190">[`project.json`](Schema/project-json.md): *(NuGet 3.0+)* A JSON file that maintains a list of the project's dependencies with an overall package graph in an associated file, `project.lock.json`.</span></span> <span data-ttu-id="91474-191">此結構提供的效能優於[相依性解析](Consume-Packages/Dependency-Resolution.md) (包含可轉移還原) 中所述的 `packages.config`，但其本身一般已取代為下面的 PackageReference。</span><span class="sxs-lookup"><span data-stu-id="91474-191">This structure provides improved performance over `packages.config` as described on [Dependency Resolution](Consume-Packages/Dependency-Resolution.md), including transitive restore, but has itself been generally superseded by PackageReference below.</span></span>
- <span data-ttu-id="91474-192">[專案檔中的套件參考](Consume-Packages/Package-References-in-Project-Files.md) (也稱為 "PackageReference") | *(NuGet 4.0+)* 直接維護專案檔內的專案最上層相依性清單，因此不需要個別檔案。</span><span class="sxs-lookup"><span data-stu-id="91474-192">[Package references in project files](Consume-Packages/Package-References-in-Project-Files.md) (also known as "PackageReference") | *(NuGet 4.0+)* Maintains a list of a project's top-level dependencies directly within the project file, so no separate file is needed.</span></span> <span data-ttu-id="91474-193">動態產生相關聯的檔案 `project.assets.json` (例如 `project.lock.json`) 來管理整體相依性圖形。</span><span class="sxs-lookup"><span data-stu-id="91474-193">An associated file, `project.assets.json`, is dynamically generated like `project.lock.json` to manage the overall dependency graph.</span></span>

<span data-ttu-id="91474-194">任何指定專案中所使用的專案管理格式都取決於專案類型，以及可用的 NuGet 和 Visual Studio 版本。</span><span class="sxs-lookup"><span data-stu-id="91474-194">Which package management format is employed in any given project depends on the project type, and the available version of NuGet and Visual Studio.</span></span> <span data-ttu-id="91474-195">若要檢查正在使用的格式，只需要在安裝第一個套件之後，於專案根目錄中尋找 `packages.config` 或 `project.json`。</span><span class="sxs-lookup"><span data-stu-id="91474-195">To check what format is being used, simply look for `packages.config` or `project.json` in the project root after installing your first package.</span></span> <span data-ttu-id="91474-196">如果您看不到其中一個檔案，請直接查看 &lt;PackageReference&gt; 項目的專案檔。</span><span class="sxs-lookup"><span data-stu-id="91474-196">If you don't see either file, look in the project file directly for a &lt;PackageReference&gt;element.</span></span>

<span data-ttu-id="91474-197">例如，在 Visual Studio 2017 中，大部分專案類型都會使用 `packages.config`，但使用 PackageReference 的 UWP C# 和 .NET Core 專案。</span><span class="sxs-lookup"><span data-stu-id="91474-197">In Visual Studio 2017, for example, most project types use `packages.config` except for UWP C# and .NET Core projects which use PackageReference.</span></span> 

## <a name="what-else-does-nuget-do"></a><span data-ttu-id="91474-198">NuGet 還有其他功能嗎？</span><span class="sxs-lookup"><span data-stu-id="91474-198">What else does NuGet do?</span></span>

<span data-ttu-id="91474-199">總而言之，NuGet 提供 (以其裝載角色) nuget.org 中央存放庫，並支援私用裝載。</span><span class="sxs-lookup"><span data-stu-id="91474-199">To summarize what we've covered so far, NuGet provides (in its hosting role) the central nuget.org repository and supports private hosting.</span></span> <span data-ttu-id="91474-200">NuGet 提供開發人員建立、發行和使用套件所需的工具。</span><span class="sxs-lookup"><span data-stu-id="91474-200">NuGet provides the tools developers need for creating, publishing, and consuming packages.</span></span> <span data-ttu-id="91474-201">最重要的是，NuGet 會維護專案中所用套件的參考清單，而且可以用來從該清單中還原和更新這些套件。</span><span class="sxs-lookup"><span data-stu-id="91474-201">And most importantly, NuGet maintains a reference list of packages used in a project and the ability to restore and update those packages from that list.</span></span>

<span data-ttu-id="91474-202">為了讓這些程序有效率地運作，NuGet 會在幕後進行一些最佳化。</span><span class="sxs-lookup"><span data-stu-id="91474-202">To make these processes work efficiently, NuGet does some behind-the-scenes optimizations.</span></span> <span data-ttu-id="91474-203">最值得注意的是，NuGet 管理整個電腦和專案特定套件快取，以建立安裝和重新安裝的捷徑。</span><span class="sxs-lookup"><span data-stu-id="91474-203">Most notably, NuGet manages both computer-wide and project-specific package caches to shortcut installation and reinstallation.</span></span> <span data-ttu-id="91474-204">如果關注整個電腦的快取，則任何您在專案中下載並安裝的套件都會儲存在快取中，這樣在另一個專案中安裝相同的套件時就不需要再次進行下載。</span><span class="sxs-lookup"><span data-stu-id="91474-204">Where the computer-wide cache is concerned, any package that you download and install in a project is stored in the cache, such that installing the same package in another project doesn't have to download it again.</span></span> <span data-ttu-id="91474-205">當您經常還原大量套件時 (例如在組建伺服器上)，這十分有幫助。</span><span class="sxs-lookup"><span data-stu-id="91474-205">This is clearly very helpful when you're frequently restoring a larger number of packages, as on a build server.</span></span> <span data-ttu-id="91474-206">如需機制和其使用方式的詳細資料，請參閱[管理 NuGet 快取](Consume-Packages/Managing-the-Nuget-Cache.md)。</span><span class="sxs-lookup"><span data-stu-id="91474-206">For more details on the mechanism and how to work with it, see [Managing the NuGet cache](Consume-Packages/Managing-the-Nuget-Cache.md).</span></span>

<span data-ttu-id="91474-207">在個別專案內，NuGet 會執行許多工作，來管理整體相依性圖形 </span><span class="sxs-lookup"><span data-stu-id="91474-207">Within an individual project, NuGet does a lot of work to manage the overall dependency graph.</span></span> <span data-ttu-id="91474-208">(使用 `project.json` 或 &lt;PackageReference&gt; 時，NuGet 會將該資訊分別保留在稱為 `project.lock.json` 和 `project.assets.json` 的次要檔案中)。這同樣地包含解析相同套件之不同版本的多個參考。</span><span class="sxs-lookup"><span data-stu-id="91474-208">(When using `project.json` or &lt;PackageReference&gt;, NuGet keeps that information in a secondary file called `project.lock.json` and `project.assets.json`, respectively.) This again includes resolving multiple references to different versions of the same package.</span></span>

<span data-ttu-id="91474-209">也就是說，專案經常需要採用與一或多個本身具有相同相依性之套件的相依性。</span><span class="sxs-lookup"><span data-stu-id="91474-209">That is, it's quite common that a project takes a dependency on one or more packages that themselves have the same dependencies.</span></span> <span data-ttu-id="91474-210">例如，許多其他套件都會使用 nuget.org 上的一些最實用公用程式套件。</span><span class="sxs-lookup"><span data-stu-id="91474-210">For example, some of the most useful utility packages on nuget.org are employed by many other packages.</span></span> <span data-ttu-id="91474-211">在整個相依性圖形中，您可以輕鬆地擁有相同套件之不同版本的十個不同參考。</span><span class="sxs-lookup"><span data-stu-id="91474-211">In the entire dependency graph, ten, you could easily have ten different references to different versions of the same package.</span></span> <span data-ttu-id="91474-212">不過，您不會想要將該套件的多個版本帶入應用程式本身，因此 NuGet 找出每個人都可以使用的單一版本 </span><span class="sxs-lookup"><span data-stu-id="91474-212">However, you don't want to bring multiple versions of that package into the application itself, so NuGet sorts out which single version that everyone can use.</span></span> <span data-ttu-id="91474-213">(如需本主題的詳細資訊，請參閱[相依性解析](Consume-Packages/Dependency-Resolution.md))。</span><span class="sxs-lookup"><span data-stu-id="91474-213">(See [Dependency Resolution](Consume-Packages/Dependency-Resolution.md) for more on this topic.)</span></span>

<span data-ttu-id="91474-214">此外，NuGet 會維護所有與套件建構方式相關的規格 (包含[當地語系化](Create-Packages/Creating-Localized-Packages.md)和[偵錯符號](Create-Packages/Symbol-Packages.md)) 和其參考方式 (包含[版本範圍](reference/package-versioning.md#version-ranges-and-wildcards)和[發行前版本](create-packages/Prerelease-Packages.md))。NuGet 也針對認證提供者 (適用於存取私用主機) 以及撰寫 Visual Studio 延伸模組和專案範本的開發人員提供 API。</span><span class="sxs-lookup"><span data-stu-id="91474-214">Beyond that, NuGet maintains all the specifications related to how packages are structured (including [localization](Create-Packages/Creating-Localized-Packages.md) and [debug symbols](Create-Packages/Symbol-Packages.md)) and how they are referenced (including [version ranges](reference/package-versioning.md#version-ranges-and-wildcards) and [pre-release versions](create-packages/Prerelease-Packages.md).) NuGet also provides APIs for credential providers (for accessing private hosts) and for developers who write Visual Studio extensions and project templates.</span></span>

<span data-ttu-id="91474-215">請花一點時間瀏覽本文件的目錄，而您會在那裏看到所有呈現的功能，以及回溯到 NuGet 開始的版本資訊。</span><span class="sxs-lookup"><span data-stu-id="91474-215">Take a moment to browse the table of contents for this documentation, and you'll see all of these capabilities represented there, along with release notes dating back to NuGet's beginnings.</span></span>

## <a name="comments-contributions-and-issues"></a><span data-ttu-id="91474-216">意見、參與和問題</span><span class="sxs-lookup"><span data-stu-id="91474-216">Comments, contributions, and issues</span></span>

<span data-ttu-id="91474-217">最後，我們十分歡迎對本文件的意見和參與&mdash;只要選取任何頁面上的 [意見] 和 [編輯] 命令，或瀏覽 GitHub 上的[文件存放庫](https://github.com/NuGet/docs.microsoft.com-nuget/)和[文件問題清單](https://github.com/NuGet/docs.microsoft.com-nuget/issues)。</span><span class="sxs-lookup"><span data-stu-id="91474-217">Finally, we very much welcome comments and contributions to this documentation&mdash;just select the **Comments** and **Edit** commands on any page, or visit the [docs repository](https://github.com/NuGet/docs.microsoft.com-nuget/) and [docs issue list](https://github.com/NuGet/docs.microsoft.com-nuget/issues) on GitHub.</span></span>

<span data-ttu-id="91474-218">我們也歡迎透過[各種 GitHub 存放庫](https://github.com/NuGet/Home)來參與 NuGet 本身；在 [https://github.com/NuGet/home/issues](https://github.com/NuGet/home/issues) 上可以找到 NuGet 問題。</span><span class="sxs-lookup"><span data-stu-id="91474-218">We also welcome contributions to NuGet itself through its [various GitHub repositories](https://github.com/NuGet/Home); NuGet issues can be found on [https://github.com/NuGet/home/issues](https://github.com/NuGet/home/issues).</span></span>

<span data-ttu-id="91474-219">享受 NuGet 體驗！</span><span class="sxs-lookup"><span data-stu-id="91474-219">Enjoy your NuGet experience!</span></span>