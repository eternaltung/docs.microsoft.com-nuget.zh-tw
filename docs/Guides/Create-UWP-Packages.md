---
title: "建立通用 Windows 平台的 NuGet 套件 | Microsoft Docs"
author: kraigb
ms.author: kraigb
manager: ghogen
ms.date: 7/17/2017
ms.topic: get-started-article
ms.prod: nuget
ms.technology: 
ms.assetid: d98524b1-a674-4803-8ac5-3c6bce867f86
description: "有關如何使用適用於通用 Windows 平台之 Windows 執行階段元件來建立 NuGet 套件的端對端逐步解說。"
keywords: "建立套件, UWP 的套件, Windows 執行階段元件"
ms.reviewer:
- karann-msft
- unniravindranathan
ms.openlocfilehash: 0513ad063d01e573672b6c84a9e819b6df516f03
ms.sourcegitcommit: d0ba99bfe019b779b75731bafdca8a37e35ef0d9
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/14/2017
---
# <a name="create-uwp-packages"></a><span data-ttu-id="f496b-104">建立 UWP 套件</span><span class="sxs-lookup"><span data-stu-id="f496b-104">Create UWP packages</span></span>

<span data-ttu-id="f496b-105">[通用 Windows 平台 (UWP)](https://developer.microsoft.com/windows) 會為每個執行 Windows 10 的裝置提供通用應用程式平台。</span><span class="sxs-lookup"><span data-stu-id="f496b-105">The [Universal Windows Platform (UWP)](https://developer.microsoft.com/windows) provides a common app platform for every device that runs Windows 10.</span></span> <span data-ttu-id="f496b-106">在此模型內，UWP 應用程式可以呼叫所有裝置通用的 WinRT API，也可以呼叫應用程式執行所在裝置系列特有的 API (包含 Win32 和 .NET)。</span><span class="sxs-lookup"><span data-stu-id="f496b-106">Within this model, UWP apps can call both the WinRT APIs that are common to all devices, and also APIs (including Win32 and .NET) that are specific to the device family on which the app is running.</span></span>

<span data-ttu-id="f496b-107">在本逐步解說中，您將使用可在受控和原生專案中使用的原生 UWP 元件 (包含 XAML 控制項) 來建立 NuGet 套件。</span><span class="sxs-lookup"><span data-stu-id="f496b-107">In this walkthrough you'll create a NuGet package with a native UWP component (including a XAML control) that can be used in both Managed and Native projects.</span></span>

1. [<span data-ttu-id="f496b-108">必要條件</span><span class="sxs-lookup"><span data-stu-id="f496b-108">Pre-requisites</span></span>](#pre-requisites)
1. [<span data-ttu-id="f496b-109">建立 UWP Windows 執行階段元件</span><span class="sxs-lookup"><span data-stu-id="f496b-109">Create a UWP Windows Runtime Component</span></span>](#create-a-uwp-windows-runtime-component)
1. [<span data-ttu-id="f496b-110">建立和更新 .nuspec 檔案</span><span class="sxs-lookup"><span data-stu-id="f496b-110">Create and update the .nuspec file</span></span>](#create-and-update-the-nuspec-file)
1. [<span data-ttu-id="f496b-111">封裝元件</span><span class="sxs-lookup"><span data-stu-id="f496b-111">Package the component</span></span>](#package-the-component)
1. [<span data-ttu-id="f496b-112">相關主題</span><span class="sxs-lookup"><span data-stu-id="f496b-112">Related topics</span></span>](#related-topics)

## <a name="pre-requisites"></a><span data-ttu-id="f496b-113">必要條件</span><span class="sxs-lookup"><span data-stu-id="f496b-113">Pre-requisites</span></span>

1. <span data-ttu-id="f496b-114">Visual Studio 2017 或 Visual Studio 2015.</span><span class="sxs-lookup"><span data-stu-id="f496b-114">Visual Studio 2017 or Visual Studio 2015.</span></span> <span data-ttu-id="f496b-115">從 [visualstudio.com](https://www.visualstudio.com/) 免費安裝 Community Edition，也可以使用 Professional Edition 和 Enterprise Edition。</span><span class="sxs-lookup"><span data-stu-id="f496b-115">Install the Community edition for free from [visualstudio.com](https://www.visualstudio.com/); you can use the Professional and Enterprise editions as well.</span></span>
1. <span data-ttu-id="f496b-116">NuGet CLI。</span><span class="sxs-lookup"><span data-stu-id="f496b-116">NuGet CLI.</span></span> <span data-ttu-id="f496b-117">從 [nuget.org/downloads](https://nuget.org/downloads) 下載最新版的 nuget.exe，並將它儲存至您選擇的位置。</span><span class="sxs-lookup"><span data-stu-id="f496b-117">Download the latest version of nuget.exe from [nuget.org/downloads](https://nuget.org/downloads), saving it to a location of your choice.</span></span> <span data-ttu-id="f496b-118">如果尚未新增，則請將該位置新增至您的 PATH 環境變數。</span><span class="sxs-lookup"><span data-stu-id="f496b-118">Then add that location to your PATH environment variable if it isn't already.</span></span>

> [!Note]
> <span data-ttu-id="f496b-119">nuget.exe 本身是 CLI 工具，不是安裝程式，因此請務必從瀏覽器儲存下載的檔案，而不是執行它。</span><span class="sxs-lookup"><span data-stu-id="f496b-119">nuget.exe is the CLI tool itself, not an installer, so be sure to save the downloaded file from your browser instead of running it.</span></span>


## <a name="create-a-uwp-windows-runtime-component"></a><span data-ttu-id="f496b-120">建立 UWP Windows 執行階段元件</span><span class="sxs-lookup"><span data-stu-id="f496b-120">Create a UWP Windows Runtime Component</span></span>

1. <span data-ttu-id="f496b-121">在 Visual Studio 中，選擇 [檔案] > [新增] > [專案]，並展開 [Visual C++] > [Windows] > [通用] 節點，然後選取 [Windows 執行階段元件 (通用 Windows)] 範本，並將名稱變更為 ImageEnhancer，然後按一下 [確定]。</span><span class="sxs-lookup"><span data-stu-id="f496b-121">In Visual Studio, choose **File > New > Project**, expand the **Visual C++ > Windows > Universal** node, select the **Windows Runtime Component (Universal Windows)** template, change the name to ImageEnhancer, and click OK.</span></span> <span data-ttu-id="f496b-122">當系統出現提示時，請接受目標版本和最低版本的預設值。</span><span class="sxs-lookup"><span data-stu-id="f496b-122">Accept the default values for Target Version and Minimum Version when prompted.</span></span>

    ![建立新 UWP Windows 執行階段元件專案](media/UWP-NewProject.png)

1. <span data-ttu-id="f496b-124">以滑鼠右鍵按一下方案總管中的專案，選取 [新增] > [新增項目]、按一下 [Visual C++] > [XAML] 節點、選取 [樣板化控制項]、將名稱變更為 AwesomeImageControl.cpp，然後按一下 [新增]：</span><span class="sxs-lookup"><span data-stu-id="f496b-124">Right click the project in Solution Explorer, select **Add > New Item**, click the **Visual C++ > XAML** node, select **Templated Control**, change the name to AwesomeImageControl.cpp, and click **Add**:</span></span>

    ![將新的 XAML 樣板化控制項項目新增至專案](media/UWP-NewXAMLControl.png)

1. <span data-ttu-id="f496b-126">以滑鼠右鍵按一下方案總管，然後選取 [屬性]。</span><span class="sxs-lookup"><span data-stu-id="f496b-126">Right-click the project in Solution Explorer and select **Properties.**</span></span> <span data-ttu-id="f496b-127">在 [屬性] 頁面中，展開 [組態屬性] > [C/C++]，然後按一下 [輸出檔案]。</span><span class="sxs-lookup"><span data-stu-id="f496b-127">In the Properties page, expand **Configuration Properties > C/C++** and click **Output Files**.</span></span> <span data-ttu-id="f496b-128">在右窗格中，將 [產生 XML 文件檔] 的值變更為 [是]：</span><span class="sxs-lookup"><span data-stu-id="f496b-128">In the pane on the right, change the value for **Generate XML Documentation Files** to Yes:</span></span>

    ![將 [產生 XML 文件檔] 設定為 [是]](media/UWP-GenerateXMLDocFiles.png)

1. <span data-ttu-id="f496b-130">現在以滑鼠右鍵按一下「方案」，並選取 [批次建置]，然後核取對話方塊中的三個 [偵錯] 方塊，如下顯示。</span><span class="sxs-lookup"><span data-stu-id="f496b-130">Right click the *solution* now, select **Batch Build**, check the three Debug boxes in the dialog as shown below.</span></span> <span data-ttu-id="f496b-131">這確保當您執行建置時，會為 Windows 所支援的每個目標系統產生一組完整成品。</span><span class="sxs-lookup"><span data-stu-id="f496b-131">This makes sure that when you do a build, you'll generate a full set of artifacts for each of the target systems that Windows supports.</span></span>

    ![批次建置](media/UWP-BatchBuild.png)

1. <span data-ttu-id="f496b-133">在 [批次建置] 對話方塊中，按一下 [建置] 確認專案，並建立 NuGet 套件所需的輸出檔案。</span><span class="sxs-lookup"><span data-stu-id="f496b-133">In the Batch Build dialog, and click **Build** to verify the project and create the output files that you'll need for the NuGet package.</span></span>

> [!Note]
> <span data-ttu-id="f496b-134">在本逐步解說中，您將偵錯成品用於套件。</span><span class="sxs-lookup"><span data-stu-id="f496b-134">In this walkthrough you'll use the Debug artifacts for the package.</span></span> <span data-ttu-id="f496b-135">針對非偵錯套件，請改為檢查 [批次建置] 對話方塊中的 [發行] 選項，並參照所遵循步驟中產生的發行資料夾。</span><span class="sxs-lookup"><span data-stu-id="f496b-135">For non-debug package, check the Release options in the Batch Build dialog instead, and refer to the resulting Release folders in the steps that follow.</span></span>


## <a name="create-and-update-the-nuspec-file"></a><span data-ttu-id="f496b-136">建立和更新 .nuspec 檔案</span><span class="sxs-lookup"><span data-stu-id="f496b-136">Create and update the .nuspec file</span></span>

<span data-ttu-id="f496b-137">若要建立初始 `.nuspec` 檔案，請執行下列三個步驟。</span><span class="sxs-lookup"><span data-stu-id="f496b-137">To create the initial `.nuspec` file, do the three steps below.</span></span> <span data-ttu-id="f496b-138">下列各節接著會引導您完成其他必要更新。</span><span class="sxs-lookup"><span data-stu-id="f496b-138">The sections that follow then guide you through other necessary updates.</span></span>

1. <span data-ttu-id="f496b-139">開啟命令提示字元，並巡覽至包含 `ImageEnhancer.vcxproj` 的資料夾 (這是低於方案檔一階的子資料夾)。</span><span class="sxs-lookup"><span data-stu-id="f496b-139">Open a command prompt and navigate to the folder containing `ImageEnhancer.vcxproj` (this will be a subfolder below where the solution file is).</span></span>
1. <span data-ttu-id="f496b-140">執行 NuGet `spec` 命令來產生 `ImageEnhancer.nuspec` (檔案名稱取自 `.vcxproj` 檔案的名稱)：</span><span class="sxs-lookup"><span data-stu-id="f496b-140">Run the NuGet `spec` command to generate `ImageEnhancer.nuspec` (the name of the file is taken from the name of the `.vcxproj` file):</span></span>

    ```
    nuget spec
    ```

1. <span data-ttu-id="f496b-141">在編輯器中開啟 `ImageEnhancer.nuspec`，然後進行更新使其符合下列內容，並使用適當的值取代 YOUR_NAME。</span><span class="sxs-lookup"><span data-stu-id="f496b-141">Open `ImageEnhancer.nuspec` in an editor and update it to match the following, replacing YOUR_NAME with an appropriate value.</span></span> <span data-ttu-id="f496b-142">尤其是在整個 nuget.org 中，`<id>` 值必須為唯一 (請參閱[建立套件](../create-packages/creating-a-package.md#choosing-a-unique-package-identifier-and-setting-the-version-number)中所述的命名慣例。</span><span class="sxs-lookup"><span data-stu-id="f496b-142">The `<id>` value, specifically, must be unique across nuget.org (see the naming conventions described in [Creating a package](../create-packages/creating-a-package.md#choosing-a-unique-package-identifier-and-setting-the-version-number)).</span></span> <span data-ttu-id="f496b-143">另請注意，您也必須更新作者和描述標記，否則會在封裝步驟期間發生錯誤。</span><span class="sxs-lookup"><span data-stu-id="f496b-143">Also note that you must also update the author and description tags or you'll get an error during the packing step.</span></span>

    ```xml
    <?xml version="1.0"?>
    <package >
        <metadata>
        <id>ImageEnhancer.YOUR_NAME</id>
        <version>1.0.0</version>
        <title>ImageEnhancer</title>
        <authors>YOUR_NAME</authors>
        <owners>YOUR_NAME</owners>
        <requireLicenseAcceptance>false</requireLicenseAcceptance>
        <description>Awesome Image Enhancer</description>
        <releaseNotes>First release</releaseNotes>
        <copyright>Copyright 2016</copyright>
        <tags>image enhancer imageenhancer</tags>
        </metadata>
    </package>
    ```

> [!Note]
> <span data-ttu-id="f496b-144">針對公眾使用而建置的套件，請特別注意 `<tags>` 項目，因為這些標籤可協助其他人找到您的套件，並了解其用途。</span><span class="sxs-lookup"><span data-stu-id="f496b-144">For packages built for public consumption, pay special attention to the `<tags>` element, as these tags help others find your package and understand what it does.</span></span>



### <a name="adding-windows-metadata-to-the-package"></a><span data-ttu-id="f496b-145">將 Windows 中繼資料新增至套件</span><span class="sxs-lookup"><span data-stu-id="f496b-145">Adding Windows metadata to the package</span></span>

<span data-ttu-id="f496b-146">Windows 執行階段元件需要描述其所有公開可用類型的中繼資料，讓其他應用程式和程式庫可以使用元件。</span><span class="sxs-lookup"><span data-stu-id="f496b-146">A Windows Runtime Component requires metadata that describes all of its publicly available types, which makes it possible for other apps and libraries to consume the component.</span></span> <span data-ttu-id="f496b-147">此中繼資料包含在 .winmd 檔案中，而此檔案是在您編譯專案時建立，並且必須併入 NuGet 套件中。</span><span class="sxs-lookup"><span data-stu-id="f496b-147">This metadata is contained in a .winmd file, which is created when you compile the project and must be included in your NuGet package.</span></span> <span data-ttu-id="f496b-148">具有 IntelliSense 資料的 XML 檔案也會在相同的時間建置，同時應該予以包含。</span><span class="sxs-lookup"><span data-stu-id="f496b-148">An XML file with IntelliSense data is also built at the same time, and should be included as well.</span></span>

<span data-ttu-id="f496b-149">將下列 `<files>` 節點新增至 `.nuspec` 檔案：</span><span class="sxs-lookup"><span data-stu-id="f496b-149">Add the following `<files>` node to the `.nuspec` file:</span></span>

```xml
<package>
    <metadata>
        ...
    </metadata>

    <files>
        <!-- WinMd and IntelliSense files -->
        <file src="..\Debug\ImageEnhancer\ImageEnhancer.winmd" target="lib\uap10.0"/>
        <file src="..\Debug\ImageEnhancer\ImageEnhancer.xml" target="lib\uap10.0"/>
    </files>
</package>
```

### <a name="adding-xaml-content"></a><span data-ttu-id="f496b-150">新增 XAML 內容</span><span class="sxs-lookup"><span data-stu-id="f496b-150">Adding XAML content</span></span>

<span data-ttu-id="f496b-151">若要包含 XAML 控制項與您的元件，您需要新增包含控制項的預設範本 (如專案範本所產生)。</span><span class="sxs-lookup"><span data-stu-id="f496b-151">To include a XAML control with your component, you need to add the XAML file that has the default template for the control (as generated by the project template).</span></span> <span data-ttu-id="f496b-152">在 `<files>` 區段中也包含這項內容：</span><span class="sxs-lookup"><span data-stu-id="f496b-152">This also goes in the `<files>` section:</span></span>

```xml
<?xml version="1.0"?>
<package >
    <metadata>
        ...
    </metadata>
    <files>
        ...

        <!-- XAML controls -->
        <file src="Themes\Generic.xaml" target="lib\uap10.0\Themes"/>

    </files>
</package>
```

### <a name="adding-the-native-implementation-libraries"></a><span data-ttu-id="f496b-153">新增原生實作程式庫</span><span class="sxs-lookup"><span data-stu-id="f496b-153">Adding the native implementation libraries</span></span>

<span data-ttu-id="f496b-154">在您的元件內，ImageEnhancer 類型的核心邏輯是原生程式碼，包含在為每個目標執行階段 (ARM、x86 和 x64) 產生的各種 `ImageEnhancer.dll` 組件。</span><span class="sxs-lookup"><span data-stu-id="f496b-154">Within your component, the core logic of the ImageEnhancer type is in native code, which is contained in the various `ImageEnhancer.dll` assemblies that are generated for each target runtime (ARM, x86, and x64).</span></span> <span data-ttu-id="f496b-155">若要將這些併入套件中，請在 `<files>` 區段和其相關聯 .pri 資源檔中參考它們：</span><span class="sxs-lookup"><span data-stu-id="f496b-155">To include these in the package, reference them in the `<files>` section along with their associated .pri resource files:</span></span>

```xml
<?xml version="1.0"?>
<package >
    <metadata>
        ...
    </metadata>
    <files>
        ...

        <!-- DLLs and resources -->
        <file src="..\ARM\Debug\ImageEnhancer\ImageEnhancer.dll" target="runtimes\win10-arm\native"/>
        <file src="..\ARM\Debug\ImageEnhancer\ImageEnhancer.pri" target="runtimes\win10-arm\native"/>

        <file src="..\x64\Debug\ImageEnhancer\ImageEnhancer.dll" target="runtimes\win10-x64\native"/>
        <file src="..\x64\Debug\ImageEnhancer\ImageEnhancer.pri" target="runtimes\win10-x64\native"/>

        <file src="..\Debug\ImageEnhancer\ImageEnhancer.dll" target="runtimes\win10-x86\native"/>
        <file src="..\Debug\ImageEnhancer\ImageEnhancer.pri" target="runtimes\win10-x86\native"/>

    </files>
</package>
```

### <a name="adding-targets"></a><span data-ttu-id="f496b-156">新增 .targets</span><span class="sxs-lookup"><span data-stu-id="f496b-156">Adding .targets</span></span>

<span data-ttu-id="f496b-157">接下來，可能使用 NuGet 套件的 C++ 和 JavaScript 專案需要有 .targets 檔案，才能識別必要組件和 winmd 檔案 </span><span class="sxs-lookup"><span data-stu-id="f496b-157">Next, C++ and JavaScript projects that might consume your NuGet package need a .targets file to identify the necessary assembly and winmd files.</span></span> <span data-ttu-id="f496b-158">(C# 和 Visual Basic 專案會自動執行這項作業)。建立此檔案，方法是將下列文字複製至 `ImageEnhancer.targets`，並將它儲存至與 `.nuspec` 檔案相同的資料夾中：</span><span class="sxs-lookup"><span data-stu-id="f496b-158">(C# and Visual Basic projects do this automatically.) Create this file by copying the text below into `ImageEnhancer.targets` and save it in the same folder as the `.nuspec` file:</span></span>

```xml
<?xml version="1.0" encoding="utf-8"?>
<Project xmlns="http://schemas.microsoft.com/developer/msbuild/2003">
    <PropertyGroup>
        <ImageEnhancer-Platform Condition="'$(Platform)' == 'Win32'">x86</ImageEnhancer-Platform>
        <ImageEnhancer-Platform Condition="'$(Platform)' != 'Win32'">$(Platform)</ImageEnhancer-Platform>
    </PropertyGroup>
    <ItemGroup Condition="'$(TargetPlatformIdentifier)' == 'UAP'">
        <Reference Include="$(MSBuildThisFileDirectory)..\..\lib\uap10.0\ImageEnhancer.winmd">
            <Implementation>ImageEnhancer.dll</Implementation>
        </Reference>
    <ReferenceCopyLocalPaths Include="$(MSBuildThisFileDirectory)..\..\runtimes\win10-$(ImageEnhancer-Platform)\native\ImageEnhancer.dll" />
    </ItemGroup>
</Project>
```

<span data-ttu-id="f496b-159">然後在 `.nuspec` 檔案中參照 `ImageEnhancer.targets`：</span><span class="sxs-lookup"><span data-stu-id="f496b-159">Then refer to `ImageEnhancer.targets` in your `.nuspec` file:</span></span>

```xml
<?xml version="1.0"?>
<package >
    <metadata>
        ...
    </metadata>
    <files>
        ...

        <!-- .targets -->
        <file src="ImageEnhancer.targets" target="build\native"/>

    </files>
</package>
```

### <a name="final-nuspec"></a><span data-ttu-id="f496b-160">最終 .nuspec</span><span class="sxs-lookup"><span data-stu-id="f496b-160">Final .nuspec</span></span>

<span data-ttu-id="f496b-161">最終 `.nuspec` 檔案現在看起來應該如下所示，並且應該將 YOUR_NAME 取代為適當值：</span><span class="sxs-lookup"><span data-stu-id="f496b-161">Your final `.nuspec` file should now look like the following, where again YOUR_NAME should be replaced with an appropriate value:</span></span>

```xml
<?xml version="1.0"?>
<package >
    <metadata>
    <id>ImageEnhancer.YOUR_NAME</id>
    <version>1.0.0</version>
    <title>ImageEnhancer</title>
    <authors>YOUR_NAME</authors>
    <owners>YOUR_NAME</owners>
    <requireLicenseAcceptance>false</requireLicenseAcceptance>
    <description>Awesome Image Enhancer</description>
    <releaseNotes>First Release</releaseNotes>
    <copyright>Copyright 2016</copyright>
    <tags>image enhancer imageenhancer</tags>
    </metadata>
    <files>
    <!-- WinMd and IntelliSense -->
    <file src="..\Debug\ImageEnhancer\ImageEnhancer.winmd" target="lib\uap10.0"/>
    <file src="..\Debug\ImageEnhancer\ImageEnhancer.xml" target="lib\uap10.0"/>

    <!-- XAML controls -->
    <file src="Themes\Generic.xaml" target="lib\uap10.0\Themes"/>

    <!-- DLLs and resources -->
    <file src="..\ARM\Debug\ImageEnhancer\ImageEnhancer.dll" target="runtimes\win10-arm\native"/>
    <file src="..\ARM\Debug\ImageEnhancer\ImageEnhancer.pri" target="runtimes\win10-arm\native"/>
    <file src="..\x64\Debug\ImageEnhancer\ImageEnhancer.dll" target="runtimes\win10-x64\native"/>
    <file src="..\x64\Debug\ImageEnhancer\ImageEnhancer.pri" target="runtimes\win10-x64\native"/>
    <file src="..\Debug\ImageEnhancer\ImageEnhancer.dll" target="runtimes\win10-x86\native"/>
    <file src="..\Debug\ImageEnhancer\ImageEnhancer.pri" target="runtimes\win10-x86\native"/>

    <!-- .targets -->
    <file src="ImageEnhancer.targets" target="build\native"/>

    </files>
</package>
```


## <a name="package-the-component"></a><span data-ttu-id="f496b-162">封裝元件</span><span class="sxs-lookup"><span data-stu-id="f496b-162">Package the component</span></span>

<span data-ttu-id="f496b-163">只要已完成的 `.nuspec` 參考您需要包含在套件中的所有檔案，就可隨時執行 `pack` 命令：</span><span class="sxs-lookup"><span data-stu-id="f496b-163">With the completed `.nuspec` referencing all the files you need to include in the package, you're ready to run the `pack` command:</span></span>

```
nuget pack ImageEnhancer.nuspec
```

<span data-ttu-id="f496b-164">這會產生 `ImageEnhancer.YOUR_NAME.1.0.0.nupkg`。</span><span class="sxs-lookup"><span data-stu-id="f496b-164">This will generate `ImageEnhancer.YOUR_NAME.1.0.0.nupkg`.</span></span> <span data-ttu-id="f496b-165">在如 [NuGet 套件總管](https://github.com/NuGetPackageExplorer/NuGetPackageExplorer)的工具中開啟此檔案，並展開所有節點，您將會看到下列內容：</span><span class="sxs-lookup"><span data-stu-id="f496b-165">Opening this file in a tool like the [NuGet Package Explorer](https://github.com/NuGetPackageExplorer/NuGetPackageExplorer) and expanding all the nodes, you'll see the following contents:</span></span>

![顯示 ImageEnhancer 套件的 NuGet 套件總管](media/UWP-PackageExplorer.png)

> [!Tip]
> <span data-ttu-id="f496b-167">`.nupkg` 檔案只是一個使用不同副檔名的 ZIP 檔。</span><span class="sxs-lookup"><span data-stu-id="f496b-167">A `.nupkg` file is just a ZIP file with a different extension.</span></span> <span data-ttu-id="f496b-168">然後，您也可以將 `.nupkg` 變更為 `.zip` 來檢查套件內容，但是請記住要先還原副檔名，再將套件上傳至 nuget.org。</span><span class="sxs-lookup"><span data-stu-id="f496b-168">You can also examine package contents, then, by changing `.nupkg` to `.zip`, but remember to restore the extension before uploading a package to nuget.org.</span></span>

<span data-ttu-id="f496b-169">若要讓其他開發人員使用您的套件，請遵循[發行套件](../create-packages/publish-a-package.md)上的指示。</span><span class="sxs-lookup"><span data-stu-id="f496b-169">To make your package available to other developers,  follow the instructions on [Publish a package](../create-packages/publish-a-package.md).</span></span>

## <a name="related-topics"></a><span data-ttu-id="f496b-170">相關主題</span><span class="sxs-lookup"><span data-stu-id="f496b-170">Related topics</span></span>

- [<span data-ttu-id="f496b-171">.nuspec 參考</span><span class="sxs-lookup"><span data-stu-id="f496b-171">.nuspec Reference</span></span>](../schema/nuspec.md)
- [<span data-ttu-id="f496b-172">符號套件</span><span class="sxs-lookup"><span data-stu-id="f496b-172">Symbol packages</span></span>](../create-packages/symbol-packages.md)
- [<span data-ttu-id="f496b-173">套件版本控制</span><span class="sxs-lookup"><span data-stu-id="f496b-173">Package versioning</span></span>](../reference/package-versioning.md)
- [<span data-ttu-id="f496b-174">支援多個 .NET Framework 版本</span><span class="sxs-lookup"><span data-stu-id="f496b-174">Supporting Multiple .NET Framework Versions</span></span>](../create-packages/supporting-multiple-target-frameworks.md)
- [<span data-ttu-id="f496b-175">在套件中包含 MSBuild 屬性和目標</span><span class="sxs-lookup"><span data-stu-id="f496b-175">Include MSBuild props and targets in a package</span></span>](../create-packages/creating-a-package.md#including-msbuild-props-and-targets-in-a-package)
- [<span data-ttu-id="f496b-176">建立當地語系化的套件</span><span class="sxs-lookup"><span data-stu-id="f496b-176">Creating Localized Packages</span></span>](../create-packages/creating-localized-packages.md)