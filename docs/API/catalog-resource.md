---
title: "類別目錄、 NuGet V3 API |Microsoft 文件"
author:
- joelverhagen
- kraigb
ms.author:
- joelverhagen
- kraigb
manager: skofman
ms.date: 10/30/2017
ms.topic: reference
ms.prod: nuget
ms.technology: 
ms.assetid: cfd338b5-6253-48c0-88ba-17c6b98fc935
description: "目錄是所有的封裝，建立以及在 nuget.org 刪除索引。"
keywords: "NuGet V3 API 類別目錄，nuget.org 的交易記錄，複寫 NuGet.org，clone NuGet.org，NuGet.org 的附加專用的記錄"
ms.reviewer:
- karann
- unniravindranathan
ms.openlocfilehash: 50e329680c5527d2a69d9c2b1421dc3aa609b478
ms.sourcegitcommit: d0ba99bfe019b779b75731bafdca8a37e35ef0d9
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/14/2017
---
# <a name="catalog"></a><span data-ttu-id="519f1-104">Catalog</span><span class="sxs-lookup"><span data-stu-id="519f1-104">Catalog</span></span>

<span data-ttu-id="519f1-105">**目錄**是記錄上的封裝來源，例如建立和刪除的所有封裝作業的資源。</span><span class="sxs-lookup"><span data-stu-id="519f1-105">The **catalog** is a resource that records all package operations on a package source, such as creations and deletions.</span></span> <span data-ttu-id="519f1-106">目錄資源有`Catalog`輸入[服務索引](service-index.md)。</span><span class="sxs-lookup"><span data-stu-id="519f1-106">The catalog resource has the `Catalog` type in the [service index](service-index.md).</span></span>

> [!Note]
> <span data-ttu-id="519f1-107">目錄不是由官方 NuGet 用戶端，因為並非所有的封裝來源實作的類別目錄。</span><span class="sxs-lookup"><span data-stu-id="519f1-107">Because the catalog is not used by the official NuGet client, not all package sources implement the catalog.</span></span>

> [!Note]
> <span data-ttu-id="519f1-108">目前，nuget.org 目錄不是可在中國使用。</span><span class="sxs-lookup"><span data-stu-id="519f1-108">Currently, the nuget.org catalog is not available in China.</span></span> <span data-ttu-id="519f1-109">如需詳細資訊，請參閱[NuGet/NuGetGallery #4949](https://github.com/NuGet/NuGetGallery/issues/4949)。</span><span class="sxs-lookup"><span data-stu-id="519f1-109">For more details, see [NuGet/NuGetGallery#4949](https://github.com/NuGet/NuGetGallery/issues/4949).</span></span>

## <a name="versioning"></a><span data-ttu-id="519f1-110">版本控制</span><span class="sxs-lookup"><span data-stu-id="519f1-110">Versioning</span></span>

<span data-ttu-id="519f1-111">下列`@type`會使用值：</span><span class="sxs-lookup"><span data-stu-id="519f1-111">The following `@type` value is used:</span></span>

<span data-ttu-id="519f1-112">@type 值</span><span class="sxs-lookup"><span data-stu-id="519f1-112">@type value</span></span>   | <span data-ttu-id="519f1-113">注意</span><span class="sxs-lookup"><span data-stu-id="519f1-113">Notes</span></span>
------------- | -----
<span data-ttu-id="519f1-114">Catalog/3.0.0</span><span class="sxs-lookup"><span data-stu-id="519f1-114">Catalog/3.0.0</span></span> | <span data-ttu-id="519f1-115">初版</span><span class="sxs-lookup"><span data-stu-id="519f1-115">The initial release</span></span>

## <a name="base-url"></a><span data-ttu-id="519f1-116">基礎 URL</span><span class="sxs-lookup"><span data-stu-id="519f1-116">Base URL</span></span>

<span data-ttu-id="519f1-117">下列應用程式開發介面的進入點 URL 是值`@id`上述資源相關聯的屬性`@type`值。</span><span class="sxs-lookup"><span data-stu-id="519f1-117">The entry point URL for the following APIs is the value of the `@id` property associated with the aforementioned resource `@type` values.</span></span> <span data-ttu-id="519f1-118">本主題會使用預留位置 URL `{@id}`。</span><span class="sxs-lookup"><span data-stu-id="519f1-118">This topic uses the placeholder URL `{@id}`.</span></span>

## <a name="http-methods"></a><span data-ttu-id="519f1-119">HTTP 方法</span><span class="sxs-lookup"><span data-stu-id="519f1-119">HTTP methods</span></span>

<span data-ttu-id="519f1-120">只有 HTTP 方法位於類別目錄資源支援的所有 Url`GET`和`HEAD`。</span><span class="sxs-lookup"><span data-stu-id="519f1-120">All URLs found in the catalog resource support only the HTTP methods `GET` and `HEAD`.</span></span>

## <a name="catalog-index"></a><span data-ttu-id="519f1-121">類別目錄索引</span><span class="sxs-lookup"><span data-stu-id="519f1-121">Catalog index</span></span>

<span data-ttu-id="519f1-122">類別目錄索引是文件中有一份類別目錄項目，排序 cronologically 的已知位置。</span><span class="sxs-lookup"><span data-stu-id="519f1-122">The catalog index is a document in a well-known location that has a list of catalog items, ordered cronologically.</span></span> <span data-ttu-id="519f1-123">它是目錄資源的進入點。</span><span class="sxs-lookup"><span data-stu-id="519f1-123">It is the entry point of the catalog resource.</span></span>

<span data-ttu-id="519f1-124">索引被組成類別目錄網頁。</span><span class="sxs-lookup"><span data-stu-id="519f1-124">The index is comprised of catalog pages.</span></span> <span data-ttu-id="519f1-125">每個類別目錄 頁面包含類別目錄項目。</span><span class="sxs-lookup"><span data-stu-id="519f1-125">Each catalog page contains catalog items.</span></span> <span data-ttu-id="519f1-126">每個類別目錄項目代表有關時間點的單一封裝的事件。</span><span class="sxs-lookup"><span data-stu-id="519f1-126">Each catalog item represents an event concerning a single package at a point in time.</span></span> <span data-ttu-id="519f1-127">類別目錄項目可以代表已建立、 未列出，relisted，或刪除從套件來源的封裝。</span><span class="sxs-lookup"><span data-stu-id="519f1-127">A catalog item can represent a package that was created, unlisted, relisted, or deleted from the package source.</span></span> <span data-ttu-id="519f1-128">藉由處理類別目錄中的項目依時間先後順序，用戶端可以建置 V3 套件來源上存在每個套件的最新檢視。</span><span class="sxs-lookup"><span data-stu-id="519f1-128">By processing the catalog items in chronological order, the client can build an up-to-date view of every package that exists on the V3 package source.</span></span>

<span data-ttu-id="519f1-129">簡單地說，類別目錄的 blob 會有下列的階層式結構：</span><span class="sxs-lookup"><span data-stu-id="519f1-129">In short, catalog blobs have the following hierarchical structure:</span></span>

- <span data-ttu-id="519f1-130">**索引**： 類別目錄的進入點。</span><span class="sxs-lookup"><span data-stu-id="519f1-130">**Index**: the entry point for the catalog.</span></span>
- <span data-ttu-id="519f1-131">**頁面**： 類別目錄項目的群組。</span><span class="sxs-lookup"><span data-stu-id="519f1-131">**Page**: a grouping of catalog items.</span></span>
- <span data-ttu-id="519f1-132">**分葉**： 文件表示為類別目錄項目，也就是在單一封裝狀態的快照。</span><span class="sxs-lookup"><span data-stu-id="519f1-132">**Leaf**: a document representing a catalog item, which is a snapshot of a single package's state.</span></span>

<span data-ttu-id="519f1-133">每個類別目錄物件具有名`commitTimeStamp`代表項目加入至目錄時。</span><span class="sxs-lookup"><span data-stu-id="519f1-133">Each catalog object has a property called the `commitTimeStamp` representing when the item was added to the catalog.</span></span> <span data-ttu-id="519f1-134">類別目錄項目加入至類別目錄中的頁面稱為認可的批次。</span><span class="sxs-lookup"><span data-stu-id="519f1-134">Catalog items are added to a catalog page in batches called commits.</span></span> <span data-ttu-id="519f1-135">在相同的認可的所有類別目錄項目具有相同的認可時間戳記 (`commitTimeStamp`) 和認可 ID (`commitId`)。</span><span class="sxs-lookup"><span data-stu-id="519f1-135">All catalog items in the same commit have the same commit timestamp (`commitTimeStamp`) and commit ID (`commitId`).</span></span> <span data-ttu-id="519f1-136">放在相同的認可中的類別目錄項目代表相同的點同時間發生的套件來源的事件。</span><span class="sxs-lookup"><span data-stu-id="519f1-136">Catalog items placed in the same commit represent events that happened around the same point in time on the package source.</span></span> <span data-ttu-id="519f1-137">目錄認可內沒有順序。</span><span class="sxs-lookup"><span data-stu-id="519f1-137">There is no ordering within a catalog commit.</span></span>

<span data-ttu-id="519f1-138">因為每個套件識別碼和版本是唯一的會永遠不會有一個以上的類別目錄項目認可中。</span><span class="sxs-lookup"><span data-stu-id="519f1-138">Because each package ID and version is unique, there will never be more than one catalog item in a commit.</span></span> <span data-ttu-id="519f1-139">這可確保，在單一封裝的類別目錄項目可以永遠會明確地排序認可時間戳記。</span><span class="sxs-lookup"><span data-stu-id="519f1-139">This ensures that catalog items for a single package can always be unambiguously ordered with respect to commit timestamp.</span></span>

<span data-ttu-id="519f1-140">沒有絕對不會以每個類別目錄的多個認可`commitTimeStamp`。</span><span class="sxs-lookup"><span data-stu-id="519f1-140">There is never be more than one commit to the catalog per `commitTimeStamp`.</span></span> <span data-ttu-id="519f1-141">換句話說，`commitId`是多餘的`commitTimeStamp`。</span><span class="sxs-lookup"><span data-stu-id="519f1-141">In other words, the `commitId` is redundant with the `commitTimeStamp`.</span></span>

<span data-ttu-id="519f1-142">相對於[套件中繼資料資源](registration-base-url-resource.md)、 索引的會按封裝識別碼、 類別目錄位於索引 （queryable） 只依時間。</span><span class="sxs-lookup"><span data-stu-id="519f1-142">In contrast to the [package metadata resource](registration-base-url-resource.md), which is indexed by package ID, the catalog is indexed (and queryable) only by time.</span></span>

<span data-ttu-id="519f1-143">類別目錄項目會固定加入到開始的單純遞增、 依時間先後順序中的類別目錄中。</span><span class="sxs-lookup"><span data-stu-id="519f1-143">Catalog items are always added to the catalog in a monotonically increasing, chronological order.</span></span> <span data-ttu-id="519f1-144">這表示，如果 X 次加入目錄認可，則沒有目錄認可會不斷加入時間小於或等於 X。</span><span class="sxs-lookup"><span data-stu-id="519f1-144">This means that if a catalog commit is added at time X then no catalog commit will ever be added with a time less than or equal to X.</span></span>

<span data-ttu-id="519f1-145">下列要求會擷取類別目錄索引。</span><span class="sxs-lookup"><span data-stu-id="519f1-145">The following request fetches the catalog index.</span></span>

```
GET {@id}
```

<span data-ttu-id="519f1-146">類別目錄索引是 JSON 文件，其中包含的物件具有下列屬性：</span><span class="sxs-lookup"><span data-stu-id="519f1-146">The catalog index is a JSON document that contains an object with the following properties:</span></span>

<span data-ttu-id="519f1-147">名稱</span><span class="sxs-lookup"><span data-stu-id="519f1-147">Name</span></span>            | <span data-ttu-id="519f1-148">類型</span><span class="sxs-lookup"><span data-stu-id="519f1-148">Type</span></span>             | <span data-ttu-id="519f1-149">必要</span><span class="sxs-lookup"><span data-stu-id="519f1-149">Required</span></span> | <span data-ttu-id="519f1-150">注意</span><span class="sxs-lookup"><span data-stu-id="519f1-150">Notes</span></span>
--------------- | ---------------- | -------- | -----
<span data-ttu-id="519f1-151">commitId</span><span class="sxs-lookup"><span data-stu-id="519f1-151">commitId</span></span>        | <span data-ttu-id="519f1-152">字串</span><span class="sxs-lookup"><span data-stu-id="519f1-152">string</span></span>           | <span data-ttu-id="519f1-153">是</span><span class="sxs-lookup"><span data-stu-id="519f1-153">yes</span></span>      | <span data-ttu-id="519f1-154">最新的認可與相關聯的唯一識別碼</span><span class="sxs-lookup"><span data-stu-id="519f1-154">A unique ID associated with the most recent commit</span></span>
<span data-ttu-id="519f1-155">commitTimeStamp</span><span class="sxs-lookup"><span data-stu-id="519f1-155">commitTimeStamp</span></span> | <span data-ttu-id="519f1-156">字串</span><span class="sxs-lookup"><span data-stu-id="519f1-156">string</span></span>           | <span data-ttu-id="519f1-157">是</span><span class="sxs-lookup"><span data-stu-id="519f1-157">yes</span></span>      | <span data-ttu-id="519f1-158">最新的認可時間戳記</span><span class="sxs-lookup"><span data-stu-id="519f1-158">A timestamp of the most recent commit</span></span>
<span data-ttu-id="519f1-159">count</span><span class="sxs-lookup"><span data-stu-id="519f1-159">count</span></span>           | <span data-ttu-id="519f1-160">整數</span><span class="sxs-lookup"><span data-stu-id="519f1-160">integer</span></span>          | <span data-ttu-id="519f1-161">是</span><span class="sxs-lookup"><span data-stu-id="519f1-161">yes</span></span>      | <span data-ttu-id="519f1-162">在索引中的頁面數目</span><span class="sxs-lookup"><span data-stu-id="519f1-162">The number of pages in the index</span></span>
<span data-ttu-id="519f1-163">項目</span><span class="sxs-lookup"><span data-stu-id="519f1-163">items</span></span>           | <span data-ttu-id="519f1-164">物件的陣列</span><span class="sxs-lookup"><span data-stu-id="519f1-164">array of objects</span></span> | <span data-ttu-id="519f1-165">是</span><span class="sxs-lookup"><span data-stu-id="519f1-165">yes</span></span>      | <span data-ttu-id="519f1-166">物件的陣列，每個物件，表示頁面</span><span class="sxs-lookup"><span data-stu-id="519f1-166">A array of objects, each object representing a page</span></span>

<span data-ttu-id="519f1-167">在每個項目`items`陣列是具有最少每一頁相關詳細資料的物件。</span><span class="sxs-lookup"><span data-stu-id="519f1-167">Each element in the `items` array is an object with some minimal details about each page.</span></span> <span data-ttu-id="519f1-168">這些頁面的物件不包含類別目錄保留 （項目）。</span><span class="sxs-lookup"><span data-stu-id="519f1-168">These page objects do not contain the catalog leaves (items).</span></span> <span data-ttu-id="519f1-169">未定義此陣列中項目的順序。</span><span class="sxs-lookup"><span data-stu-id="519f1-169">The order of the elements in this array is not defined.</span></span> <span data-ttu-id="519f1-170">網頁可以依照使用記憶體中的用戶端來排序其`commitTimeStamp`屬性。</span><span class="sxs-lookup"><span data-stu-id="519f1-170">Pages can be ordered by the client in memory using their `commitTimeStamp` property.</span></span>

<span data-ttu-id="519f1-171">引入新的頁面，`count`會遞增，而新的物件會出現在`items`陣列。</span><span class="sxs-lookup"><span data-stu-id="519f1-171">As new pages are introduced, the `count` will be incremented and new objects will appear in the `items` array.</span></span>

<span data-ttu-id="519f1-172">當項目加入至類別目錄，索引的`commitId`會變更和`commitTimeStamp`會增加。</span><span class="sxs-lookup"><span data-stu-id="519f1-172">As items are added to the catalog, the index's `commitId` will change and the `commitTimeStamp` will increase.</span></span> <span data-ttu-id="519f1-173">這兩個屬性會透過所有頁面基本上摘要`commitId`和`commitTimeStamp`值`items`陣列。</span><span class="sxs-lookup"><span data-stu-id="519f1-173">These two properties are essentially a summary over all page `commitId` and `commitTimeStamp` values in the `items` array.</span></span>

### <a name="catalog-page-object-in-the-index"></a><span data-ttu-id="519f1-174">目錄索引中的頁面物件</span><span class="sxs-lookup"><span data-stu-id="519f1-174">Catalog page object in the index</span></span>

<span data-ttu-id="519f1-175">類別目錄 頁面找到的物件類別目錄索引中`items`屬性具有下列屬性：</span><span class="sxs-lookup"><span data-stu-id="519f1-175">The catalog page objects found in the catalog index's `items` property have the following properties:</span></span>

<span data-ttu-id="519f1-176">名稱</span><span class="sxs-lookup"><span data-stu-id="519f1-176">Name</span></span>            | <span data-ttu-id="519f1-177">類型</span><span class="sxs-lookup"><span data-stu-id="519f1-177">Type</span></span>    | <span data-ttu-id="519f1-178">必要</span><span class="sxs-lookup"><span data-stu-id="519f1-178">Required</span></span> | <span data-ttu-id="519f1-179">注意</span><span class="sxs-lookup"><span data-stu-id="519f1-179">Notes</span></span>
--------------- | ------- | -------- | -----
@id             | <span data-ttu-id="519f1-180">字串</span><span class="sxs-lookup"><span data-stu-id="519f1-180">string</span></span>  | <span data-ttu-id="519f1-181">是</span><span class="sxs-lookup"><span data-stu-id="519f1-181">yes</span></span>      | <span data-ttu-id="519f1-182">要擷取類別目錄 頁面的 URL</span><span class="sxs-lookup"><span data-stu-id="519f1-182">The URL to fetch catalog page</span></span>
<span data-ttu-id="519f1-183">commitId</span><span class="sxs-lookup"><span data-stu-id="519f1-183">commitId</span></span>        | <span data-ttu-id="519f1-184">字串</span><span class="sxs-lookup"><span data-stu-id="519f1-184">string</span></span>  | <span data-ttu-id="519f1-185">是</span><span class="sxs-lookup"><span data-stu-id="519f1-185">yes</span></span>      | <span data-ttu-id="519f1-186">此頁面中的最新認可與相關聯的唯一識別碼</span><span class="sxs-lookup"><span data-stu-id="519f1-186">A unique ID associated with the most recent commit in this page</span></span>
<span data-ttu-id="519f1-187">commitTimeStamp</span><span class="sxs-lookup"><span data-stu-id="519f1-187">commitTimeStamp</span></span> | <span data-ttu-id="519f1-188">字串</span><span class="sxs-lookup"><span data-stu-id="519f1-188">string</span></span>  | <span data-ttu-id="519f1-189">是</span><span class="sxs-lookup"><span data-stu-id="519f1-189">yes</span></span>      | <span data-ttu-id="519f1-190">在這個頁面中的最新的認可時間戳記</span><span class="sxs-lookup"><span data-stu-id="519f1-190">A timestamp of the most recent commit in this page</span></span>
<span data-ttu-id="519f1-191">count</span><span class="sxs-lookup"><span data-stu-id="519f1-191">count</span></span>           | <span data-ttu-id="519f1-192">整數</span><span class="sxs-lookup"><span data-stu-id="519f1-192">integer</span></span> | <span data-ttu-id="519f1-193">是</span><span class="sxs-lookup"><span data-stu-id="519f1-193">yes</span></span>      | <span data-ttu-id="519f1-194">在 [類別目錄] 頁面中的項目數</span><span class="sxs-lookup"><span data-stu-id="519f1-194">The number of items in the catalog page</span></span>

<span data-ttu-id="519f1-195">相對於[套件中繼資料資源](registration-base-url-resource.md)這在某些情況下內嵌離開插入索引內，類別目錄保留永遠不會內嵌於索引一律必須使用的頁面讀取`@id`URL。</span><span class="sxs-lookup"><span data-stu-id="519f1-195">In contrast to the [package metadata resource](registration-base-url-resource.md) which in some cases inlines leaves into the index, catalog leaves are never inlined into the index and must always be fetched by using the page's `@id` URL.</span></span>

### <a name="sample-request"></a><span data-ttu-id="519f1-196">範例要求</span><span class="sxs-lookup"><span data-stu-id="519f1-196">Sample request</span></span>

```
GET https://api.nuget.org/v3/catalog0/index.json
```

### <a name="sample-response"></a><span data-ttu-id="519f1-197">範例回應</span><span class="sxs-lookup"><span data-stu-id="519f1-197">Sample response</span></span>

[!code-JSON [catalog-index.json](./_data/catalog-index.json)]

## <a name="catalog-page"></a><span data-ttu-id="519f1-198">類別目錄 頁面</span><span class="sxs-lookup"><span data-stu-id="519f1-198">Catalog page</span></span>

<span data-ttu-id="519f1-199">類別目錄 頁面是類別目錄項目的集合。</span><span class="sxs-lookup"><span data-stu-id="519f1-199">The catalog page is a collection of catalog items.</span></span> <span data-ttu-id="519f1-200">這是提取使用其中一種文件`@id`目錄索引中找到的值。</span><span class="sxs-lookup"><span data-stu-id="519f1-200">It is a document fetched using one of the `@id` values found in the catalog index.</span></span> <span data-ttu-id="519f1-201">類別目錄 頁面的 URL 不是有可預測性，應該使用類別目錄索引探索。</span><span class="sxs-lookup"><span data-stu-id="519f1-201">The URL to a catalog page is not intended to be predictable and should be discovered using only the catalog index.</span></span>

<span data-ttu-id="519f1-202">新的類別目錄項目會加入至最高的認可時間戳記只能與類別目錄索引中頁面或新的頁面。</span><span class="sxs-lookup"><span data-stu-id="519f1-202">New catalog items are added to the page in the catalog index only with the highest commit timestamp or to a new page.</span></span> <span data-ttu-id="519f1-203">一旦有較高的認可時間戳記的頁面加入至目錄時，較舊的分頁會永遠不會加入或變更。</span><span class="sxs-lookup"><span data-stu-id="519f1-203">Once a page with a higher commit timestamp is added to the catalog, older pages are never added to or changed.</span></span>

<span data-ttu-id="519f1-204">類別目錄頁文件是具有下列屬性的 JSON 物件：</span><span class="sxs-lookup"><span data-stu-id="519f1-204">The catalog page document is a JSON object with the following properties:</span></span>

<span data-ttu-id="519f1-205">名稱</span><span class="sxs-lookup"><span data-stu-id="519f1-205">Name</span></span>            | <span data-ttu-id="519f1-206">類型</span><span class="sxs-lookup"><span data-stu-id="519f1-206">Type</span></span>             | <span data-ttu-id="519f1-207">必要</span><span class="sxs-lookup"><span data-stu-id="519f1-207">Required</span></span> | <span data-ttu-id="519f1-208">注意</span><span class="sxs-lookup"><span data-stu-id="519f1-208">Notes</span></span>
--------------- | ---------------- | -------- | -----
<span data-ttu-id="519f1-209">commitId</span><span class="sxs-lookup"><span data-stu-id="519f1-209">commitId</span></span>        | <span data-ttu-id="519f1-210">字串</span><span class="sxs-lookup"><span data-stu-id="519f1-210">string</span></span>           | <span data-ttu-id="519f1-211">是</span><span class="sxs-lookup"><span data-stu-id="519f1-211">yes</span></span>      | <span data-ttu-id="519f1-212">此頁面中的最新認可與相關聯的唯一識別碼</span><span class="sxs-lookup"><span data-stu-id="519f1-212">A unique ID associated with the most recent commit in this page</span></span>
<span data-ttu-id="519f1-213">commitTimeStamp</span><span class="sxs-lookup"><span data-stu-id="519f1-213">commitTimeStamp</span></span> | <span data-ttu-id="519f1-214">字串</span><span class="sxs-lookup"><span data-stu-id="519f1-214">string</span></span>           | <span data-ttu-id="519f1-215">是</span><span class="sxs-lookup"><span data-stu-id="519f1-215">yes</span></span>      | <span data-ttu-id="519f1-216">在這個頁面中的最新的認可時間戳記</span><span class="sxs-lookup"><span data-stu-id="519f1-216">A timestamp of the most recent commit in this page</span></span>
<span data-ttu-id="519f1-217">count</span><span class="sxs-lookup"><span data-stu-id="519f1-217">count</span></span>           | <span data-ttu-id="519f1-218">整數</span><span class="sxs-lookup"><span data-stu-id="519f1-218">integer</span></span>          | <span data-ttu-id="519f1-219">是</span><span class="sxs-lookup"><span data-stu-id="519f1-219">yes</span></span>      | <span data-ttu-id="519f1-220">在頁面中的項目數</span><span class="sxs-lookup"><span data-stu-id="519f1-220">The number of items in the page</span></span>
<span data-ttu-id="519f1-221">項目</span><span class="sxs-lookup"><span data-stu-id="519f1-221">items</span></span>           | <span data-ttu-id="519f1-222">物件的陣列</span><span class="sxs-lookup"><span data-stu-id="519f1-222">array of objects</span></span> | <span data-ttu-id="519f1-223">是</span><span class="sxs-lookup"><span data-stu-id="519f1-223">yes</span></span>      | <span data-ttu-id="519f1-224">在這個頁面中的類別目錄項目</span><span class="sxs-lookup"><span data-stu-id="519f1-224">The catalog items in this page</span></span>
<span data-ttu-id="519f1-225">父代</span><span class="sxs-lookup"><span data-stu-id="519f1-225">parent</span></span>          | <span data-ttu-id="519f1-226">字串</span><span class="sxs-lookup"><span data-stu-id="519f1-226">string</span></span>           | <span data-ttu-id="519f1-227">是</span><span class="sxs-lookup"><span data-stu-id="519f1-227">yes</span></span>      | <span data-ttu-id="519f1-228">類別目錄索引 URL</span><span class="sxs-lookup"><span data-stu-id="519f1-228">A URL to the catalog index</span></span>

<span data-ttu-id="519f1-229">在每個項目`items`陣列是具有類別目錄項目某些最少詳細資料的物件。</span><span class="sxs-lookup"><span data-stu-id="519f1-229">Each element in the `items` array is an object with some minimal details about the catalog item.</span></span> <span data-ttu-id="519f1-230">這些項目物件不包含所有類別目錄項目的資料。</span><span class="sxs-lookup"><span data-stu-id="519f1-230">These item objects do not contain all of the catalog item's data.</span></span> <span data-ttu-id="519f1-231">頁面的項目順序`items`陣列未定義。</span><span class="sxs-lookup"><span data-stu-id="519f1-231">The order of the items in the page's `items` array is not defined.</span></span> <span data-ttu-id="519f1-232">項目可以依照使用記憶體中的用戶端來排序其`commitTimeStamp`屬性。</span><span class="sxs-lookup"><span data-stu-id="519f1-232">Items can be ordered by the client in memory using their `commitTimeStamp` property.</span></span>

<span data-ttu-id="519f1-233">在網頁中的類別目錄項目數目是由伺服器實作所定義。</span><span class="sxs-lookup"><span data-stu-id="519f1-233">The number of catalog items in a page is defined by server implementation.</span></span> <span data-ttu-id="519f1-234">Nuget.org，最多 550 項目中有每個頁面上，雖然實際數目的時間可能較小的點在下一步的認可批次大小某些網頁 dependong。</span><span class="sxs-lookup"><span data-stu-id="519f1-234">For nuget.org, there are at most 550 items in each page, although the actual number may be smaller for some pages dependong on the size of the next commit batch at the point in time.</span></span>

<span data-ttu-id="519f1-235">引入新的項目，`count`是遞增的和新的類別目錄項目物件會出現在`items`陣列。</span><span class="sxs-lookup"><span data-stu-id="519f1-235">As new items are introduced, the `count` is incremented and new catalog item objects appear in the `items` array.</span></span>

<span data-ttu-id="519f1-236">當項目加入至頁面上，`commitId`變更和`commitTimeStamp`會增加。</span><span class="sxs-lookup"><span data-stu-id="519f1-236">As items are added to the page, the `commitId` changes and the `commitTimeStamp` increases.</span></span> <span data-ttu-id="519f1-237">這兩個屬性會透過所有基本上摘要`commitId`和`commitTimeStamp`值`items`陣列。</span><span class="sxs-lookup"><span data-stu-id="519f1-237">These two properties are essentially a summary over all `commitId` and `commitTimeStamp` values in the `items` array.</span></span>

### <a name="catalog-item-object-in-a-page"></a><span data-ttu-id="519f1-238">目錄項目在網頁中的物件</span><span class="sxs-lookup"><span data-stu-id="519f1-238">Catalog item object in a page</span></span>

<span data-ttu-id="519f1-239">類別目錄 頁面中找到的類別目錄項目物件`items`屬性具有下列屬性：</span><span class="sxs-lookup"><span data-stu-id="519f1-239">The catalog item objects found in the catalog page's `items` property have the following properties:</span></span>

<span data-ttu-id="519f1-240">名稱</span><span class="sxs-lookup"><span data-stu-id="519f1-240">Name</span></span>            | <span data-ttu-id="519f1-241">類型</span><span class="sxs-lookup"><span data-stu-id="519f1-241">Type</span></span>    | <span data-ttu-id="519f1-242">必要</span><span class="sxs-lookup"><span data-stu-id="519f1-242">Required</span></span> | <span data-ttu-id="519f1-243">注意</span><span class="sxs-lookup"><span data-stu-id="519f1-243">Notes</span></span>
--------------- | ------- | -------- | -----
@id             | <span data-ttu-id="519f1-244">字串</span><span class="sxs-lookup"><span data-stu-id="519f1-244">string</span></span>  | <span data-ttu-id="519f1-245">是</span><span class="sxs-lookup"><span data-stu-id="519f1-245">yes</span></span>      | <span data-ttu-id="519f1-246">擷取目錄項目之 URL</span><span class="sxs-lookup"><span data-stu-id="519f1-246">The URL to fetch the catalog item</span></span>
@type           | <span data-ttu-id="519f1-247">字串</span><span class="sxs-lookup"><span data-stu-id="519f1-247">string</span></span>  | <span data-ttu-id="519f1-248">是</span><span class="sxs-lookup"><span data-stu-id="519f1-248">yes</span></span>      | <span data-ttu-id="519f1-249">類別目錄項目類型</span><span class="sxs-lookup"><span data-stu-id="519f1-249">The type of the catalog item</span></span>
<span data-ttu-id="519f1-250">commitId</span><span class="sxs-lookup"><span data-stu-id="519f1-250">commitId</span></span>        | <span data-ttu-id="519f1-251">字串</span><span class="sxs-lookup"><span data-stu-id="519f1-251">string</span></span>  | <span data-ttu-id="519f1-252">是</span><span class="sxs-lookup"><span data-stu-id="519f1-252">yes</span></span>      | <span data-ttu-id="519f1-253">此類別目錄項目相關聯的認可 ID</span><span class="sxs-lookup"><span data-stu-id="519f1-253">The commit ID associated with this catalog item</span></span>
<span data-ttu-id="519f1-254">commitTimeStamp</span><span class="sxs-lookup"><span data-stu-id="519f1-254">commitTimeStamp</span></span> | <span data-ttu-id="519f1-255">字串</span><span class="sxs-lookup"><span data-stu-id="519f1-255">string</span></span>  | <span data-ttu-id="519f1-256">是</span><span class="sxs-lookup"><span data-stu-id="519f1-256">yes</span></span>      | <span data-ttu-id="519f1-257">此類別目錄項目的認可時間戳記</span><span class="sxs-lookup"><span data-stu-id="519f1-257">The commit timestamp of this catalog item</span></span>
<span data-ttu-id="519f1-258">nuget:id</span><span class="sxs-lookup"><span data-stu-id="519f1-258">nuget:id</span></span>        | <span data-ttu-id="519f1-259">字串</span><span class="sxs-lookup"><span data-stu-id="519f1-259">string</span></span>  | <span data-ttu-id="519f1-260">是</span><span class="sxs-lookup"><span data-stu-id="519f1-260">yes</span></span>      | <span data-ttu-id="519f1-261">這個分葉與封裝識別碼</span><span class="sxs-lookup"><span data-stu-id="519f1-261">The package ID that this leaf is related to</span></span>
<span data-ttu-id="519f1-262">nuget:version</span><span class="sxs-lookup"><span data-stu-id="519f1-262">nuget:version</span></span>   | <span data-ttu-id="519f1-263">字串</span><span class="sxs-lookup"><span data-stu-id="519f1-263">string</span></span>  | <span data-ttu-id="519f1-264">是</span><span class="sxs-lookup"><span data-stu-id="519f1-264">yes</span></span>      | <span data-ttu-id="519f1-265">與這個分葉封裝版本</span><span class="sxs-lookup"><span data-stu-id="519f1-265">The package version that this leaf is related to</span></span>

<span data-ttu-id="519f1-266">`@type`值將會是下列兩個值之一：</span><span class="sxs-lookup"><span data-stu-id="519f1-266">The `@type` value will be one of the following two values:</span></span>

1. <span data-ttu-id="519f1-267">`nuget:PackageDetails`： 這會對應至`PackageDetails`目錄分葉文件中的類型。</span><span class="sxs-lookup"><span data-stu-id="519f1-267">`nuget:PackageDetails`: this corresponds to `PackageDetails` type in the catalog leaf document.</span></span>
1. <span data-ttu-id="519f1-268">`nuget:PackageDelete`： 這會對應至`PackageDelete`目錄分葉文件中的類型。</span><span class="sxs-lookup"><span data-stu-id="519f1-268">`nuget:PackageDelete`: this corresponds to the `PackageDelete` type in the catalog leaf document.</span></span>

<span data-ttu-id="519f1-269">如需詳細資訊表示每個型別，請參閱[對應項目類型](#item-types)下方。</span><span class="sxs-lookup"><span data-stu-id="519f1-269">For more details about what each type means, see the [corresponding items type](#item-types) below.</span></span>

### <a name="sample-request"></a><span data-ttu-id="519f1-270">範例要求</span><span class="sxs-lookup"><span data-stu-id="519f1-270">Sample request</span></span>

```
GET https://api.nuget.org/v3/catalog0/page2926.json
```

### <a name="sample-response"></a><span data-ttu-id="519f1-271">範例回應</span><span class="sxs-lookup"><span data-stu-id="519f1-271">Sample response</span></span>

[!code-JSON [catalog-page.json](./_data/catalog-page.json)]

## <a name="catalog-leaf"></a><span data-ttu-id="519f1-272">類別目錄的分葉</span><span class="sxs-lookup"><span data-stu-id="519f1-272">Catalog leaf</span></span>

<span data-ttu-id="519f1-273">類別目錄的分葉包含特定的封裝識別碼和版本，在某個時間點的相關中繼資料的時間。</span><span class="sxs-lookup"><span data-stu-id="519f1-273">The catalog leaf contains metadata about a specific package ID and version at some point in time.</span></span> <span data-ttu-id="519f1-274">它是使用文件`@id`類別目錄 頁面中找到的值。</span><span class="sxs-lookup"><span data-stu-id="519f1-274">It is a document fetched using the `@id` value found in a catalog page.</span></span> <span data-ttu-id="519f1-275">類別目錄的分葉的 URL 不是要 predictedable，應該使用類別目錄頁探索。</span><span class="sxs-lookup"><span data-stu-id="519f1-275">The URL to a catalog leaf is not intended to be predictedable and should be discovered using only a catalog page.</span></span>

<span data-ttu-id="519f1-276">目錄的分葉文件是具有下列屬性的 JSON 物件：</span><span class="sxs-lookup"><span data-stu-id="519f1-276">The catalog leaf document is a JSON object with the following properties:</span></span>

<span data-ttu-id="519f1-277">名稱</span><span class="sxs-lookup"><span data-stu-id="519f1-277">Name</span></span>                    | <span data-ttu-id="519f1-278">類型</span><span class="sxs-lookup"><span data-stu-id="519f1-278">Type</span></span>                       | <span data-ttu-id="519f1-279">必要</span><span class="sxs-lookup"><span data-stu-id="519f1-279">Required</span></span> | <span data-ttu-id="519f1-280">注意</span><span class="sxs-lookup"><span data-stu-id="519f1-280">Notes</span></span>
----------------------- | -------------------------- | -------- | -----
@type                   | <span data-ttu-id="519f1-281">字串或字串陣列</span><span class="sxs-lookup"><span data-stu-id="519f1-281">string or array of strings</span></span> | <span data-ttu-id="519f1-282">是</span><span class="sxs-lookup"><span data-stu-id="519f1-282">yes</span></span>      | <span data-ttu-id="519f1-283">目錄項目的型別</span><span class="sxs-lookup"><span data-stu-id="519f1-283">The type(s) of the catalog item</span></span>
<span data-ttu-id="519f1-284">commitId 目錄：</span><span class="sxs-lookup"><span data-stu-id="519f1-284">catalog:commitId</span></span>        | <span data-ttu-id="519f1-285">字串</span><span class="sxs-lookup"><span data-stu-id="519f1-285">string</span></span>                     | <span data-ttu-id="519f1-286">是</span><span class="sxs-lookup"><span data-stu-id="519f1-286">yes</span></span>      | <span data-ttu-id="519f1-287">與這個類別目錄項目相關聯的認可 ID</span><span class="sxs-lookup"><span data-stu-id="519f1-287">A commit ID associated with this catalog item</span></span>
<span data-ttu-id="519f1-288">commitTimeStamp 目錄：</span><span class="sxs-lookup"><span data-stu-id="519f1-288">catalog:commitTimeStamp</span></span> | <span data-ttu-id="519f1-289">字串</span><span class="sxs-lookup"><span data-stu-id="519f1-289">string</span></span>                     | <span data-ttu-id="519f1-290">是</span><span class="sxs-lookup"><span data-stu-id="519f1-290">yes</span></span>      | <span data-ttu-id="519f1-291">此類別目錄項目的認可時間戳記</span><span class="sxs-lookup"><span data-stu-id="519f1-291">The commit timestamp of this catalog item</span></span>
<span data-ttu-id="519f1-292">id</span><span class="sxs-lookup"><span data-stu-id="519f1-292">id</span></span>                      | <span data-ttu-id="519f1-293">字串</span><span class="sxs-lookup"><span data-stu-id="519f1-293">string</span></span>                     | <span data-ttu-id="519f1-294">是</span><span class="sxs-lookup"><span data-stu-id="519f1-294">yes</span></span>      | <span data-ttu-id="519f1-295">封裝識別碼的類別目錄項目</span><span class="sxs-lookup"><span data-stu-id="519f1-295">The package ID of the catalog item</span></span>
<span data-ttu-id="519f1-296">發行</span><span class="sxs-lookup"><span data-stu-id="519f1-296">published</span></span>               | <span data-ttu-id="519f1-297">字串</span><span class="sxs-lookup"><span data-stu-id="519f1-297">string</span></span>                     | <span data-ttu-id="519f1-298">是</span><span class="sxs-lookup"><span data-stu-id="519f1-298">yes</span></span>      | <span data-ttu-id="519f1-299">封裝的類別目錄項目發行的日期</span><span class="sxs-lookup"><span data-stu-id="519f1-299">The published date of the package catalog item</span></span>
<span data-ttu-id="519f1-300">version</span><span class="sxs-lookup"><span data-stu-id="519f1-300">version</span></span>                 | <span data-ttu-id="519f1-301">字串</span><span class="sxs-lookup"><span data-stu-id="519f1-301">string</span></span>                     | <span data-ttu-id="519f1-302">是</span><span class="sxs-lookup"><span data-stu-id="519f1-302">yes</span></span>      | <span data-ttu-id="519f1-303">封裝版本的類別目錄項目</span><span class="sxs-lookup"><span data-stu-id="519f1-303">The package version of the catalog item</span></span>

### <a name="item-types"></a><span data-ttu-id="519f1-304">項目類型</span><span class="sxs-lookup"><span data-stu-id="519f1-304">Item types</span></span>

<span data-ttu-id="519f1-305">`@type`屬性是字串陣列。</span><span class="sxs-lookup"><span data-stu-id="519f1-305">The `@type` property is a string or array of strings.</span></span> <span data-ttu-id="519f1-306">為了方便起見，如果`@type`值是字串，它應該會被視為一個大小的任何陣列。</span><span class="sxs-lookup"><span data-stu-id="519f1-306">For convenience, if the `@type` value is a string, it should be treated as any array of size one.</span></span> <span data-ttu-id="519f1-307">並非所有可能值`@type`記載。</span><span class="sxs-lookup"><span data-stu-id="519f1-307">Not all possible values for `@type` are documented.</span></span> <span data-ttu-id="519f1-308">不過，每個類別目錄項目有正好一個的兩個下列字串類型值：</span><span class="sxs-lookup"><span data-stu-id="519f1-308">However, each catalog item has exactly one of the two following string type values:</span></span>

1. <span data-ttu-id="519f1-309">`PackageDetails`： 表示封裝中繼資料的快照集</span><span class="sxs-lookup"><span data-stu-id="519f1-309">`PackageDetails`: represents a snapshot of package metadata</span></span>
1. <span data-ttu-id="519f1-310">`PackageDelete`： 表示已刪除的封裝</span><span class="sxs-lookup"><span data-stu-id="519f1-310">`PackageDelete`: represents a package that was deleted</span></span>

### <a name="package-details-catalog-items"></a><span data-ttu-id="519f1-311">封裝詳細資料類別目錄項目</span><span class="sxs-lookup"><span data-stu-id="519f1-311">Package details catalog items</span></span>

<span data-ttu-id="519f1-312">類別目錄項目型別`PackageDetails`包含 （識別碼和版本組合） 的特定套件的套件中繼資料的快照。</span><span class="sxs-lookup"><span data-stu-id="519f1-312">Catalog items with the type `PackageDetails` contain a snapshot of package metadata for a specific package (ID and version combination).</span></span> <span data-ttu-id="519f1-313">當封裝來源遇到下列任何案例，則會產生套件詳細資料的類別目錄項目：</span><span class="sxs-lookup"><span data-stu-id="519f1-313">A package details catalog item is produced when a package source encounters any of the following scenarios:</span></span>

1. <span data-ttu-id="519f1-314">封裝是**推入**。</span><span class="sxs-lookup"><span data-stu-id="519f1-314">A package is **pushed**.</span></span>
1. <span data-ttu-id="519f1-315">封裝是**列出**。</span><span class="sxs-lookup"><span data-stu-id="519f1-315">A package is **listed**.</span></span>
1. <span data-ttu-id="519f1-316">封裝是**未列出**。</span><span class="sxs-lookup"><span data-stu-id="519f1-316">A package is **unlisted**.</span></span>
1. <span data-ttu-id="519f1-317">封裝是**reflowed**。</span><span class="sxs-lookup"><span data-stu-id="519f1-317">A package is **reflowed**.</span></span>

<span data-ttu-id="519f1-318">封裝重新排列為基本上會產生假封裝本身發送不變更現有封裝的系統管理動作。</span><span class="sxs-lookup"><span data-stu-id="519f1-318">A package reflow is an administrative gesture that essentially generates a fake push of an existing package with no changes to the package itself.</span></span> <span data-ttu-id="519f1-319">重新排列 nuget.org，會使用其中一種適用的類別目錄的背景工作在修正 bug 之後。</span><span class="sxs-lookup"><span data-stu-id="519f1-319">On nuget.org, a reflow is used after fixing a bug in one of the background jobs which consume the catalog.</span></span>

<span data-ttu-id="519f1-320">用戶端使用的類別目錄項目不應嘗試判斷哪一種案例所產生的類別目錄項目。</span><span class="sxs-lookup"><span data-stu-id="519f1-320">Clients consuming the catalog items should not attempt to determine which of these scenarios produced the catalog item.</span></span> <span data-ttu-id="519f1-321">相反地，用戶端應該只需更新的任何維護的檢視或索引與類別目錄項目中包含的中繼資料。</span><span class="sxs-lookup"><span data-stu-id="519f1-321">Instead, the client should simply update any maintained view or index with the metadata contained in the catalog item.</span></span> <span data-ttu-id="519f1-322">此外，重複或多餘的類別目錄項目應該可正常地處理 （不斷地）。</span><span class="sxs-lookup"><span data-stu-id="519f1-322">Furthermore, duplicate or redundant catalog items should be handled gracefully (idempotently).</span></span>

<span data-ttu-id="519f1-323">封裝詳細資料的類別目錄項目具有下列屬性除了[包含在所有的類別目錄保留](#catalog-leaf)。</span><span class="sxs-lookup"><span data-stu-id="519f1-323">Package details catalog items have the following properties in addition to those [included on all catalog leaves](#catalog-leaf).</span></span>

<span data-ttu-id="519f1-324">名稱</span><span class="sxs-lookup"><span data-stu-id="519f1-324">Name</span></span>                    | <span data-ttu-id="519f1-325">類型</span><span class="sxs-lookup"><span data-stu-id="519f1-325">Type</span></span>                       | <span data-ttu-id="519f1-326">必要</span><span class="sxs-lookup"><span data-stu-id="519f1-326">Required</span></span> | <span data-ttu-id="519f1-327">注意</span><span class="sxs-lookup"><span data-stu-id="519f1-327">Notes</span></span>
----------------------- | -------------------------- | -------- | -----
<span data-ttu-id="519f1-328">authors</span><span class="sxs-lookup"><span data-stu-id="519f1-328">authors</span></span>                 | <span data-ttu-id="519f1-329">字串</span><span class="sxs-lookup"><span data-stu-id="519f1-329">string</span></span>                     | <span data-ttu-id="519f1-330">no</span><span class="sxs-lookup"><span data-stu-id="519f1-330">no</span></span>       |
<span data-ttu-id="519f1-331">created</span><span class="sxs-lookup"><span data-stu-id="519f1-331">created</span></span>                 | <span data-ttu-id="519f1-332">字串</span><span class="sxs-lookup"><span data-stu-id="519f1-332">string</span></span>                     | <span data-ttu-id="519f1-333">是</span><span class="sxs-lookup"><span data-stu-id="519f1-333">yes</span></span>      | <span data-ttu-id="519f1-334">第一次建立封裝時的時間戳記</span><span class="sxs-lookup"><span data-stu-id="519f1-334">A timestamp of when the package was first created</span></span>
<span data-ttu-id="519f1-335">dependencyGroups</span><span class="sxs-lookup"><span data-stu-id="519f1-335">dependencyGroups</span></span>        | <span data-ttu-id="519f1-336">物件的陣列</span><span class="sxs-lookup"><span data-stu-id="519f1-336">array of objects</span></span>           | <span data-ttu-id="519f1-337">no</span><span class="sxs-lookup"><span data-stu-id="519f1-337">no</span></span>       | <span data-ttu-id="519f1-338">相同格式化為[套件中繼資料資源](registration-base-url-resource.md#package-dependency-group)</span><span class="sxs-lookup"><span data-stu-id="519f1-338">Same format as the [package metadata resource](registration-base-url-resource.md#package-dependency-group)</span></span>
<span data-ttu-id="519f1-339">描述</span><span class="sxs-lookup"><span data-stu-id="519f1-339">description</span></span>             | <span data-ttu-id="519f1-340">字串</span><span class="sxs-lookup"><span data-stu-id="519f1-340">string</span></span>                     | <span data-ttu-id="519f1-341">no</span><span class="sxs-lookup"><span data-stu-id="519f1-341">no</span></span>       |
<span data-ttu-id="519f1-342">iconUrl</span><span class="sxs-lookup"><span data-stu-id="519f1-342">iconUrl</span></span>                 | <span data-ttu-id="519f1-343">字串</span><span class="sxs-lookup"><span data-stu-id="519f1-343">string</span></span>                     | <span data-ttu-id="519f1-344">no</span><span class="sxs-lookup"><span data-stu-id="519f1-344">no</span></span>       |
<span data-ttu-id="519f1-345">isPrerelease</span><span class="sxs-lookup"><span data-stu-id="519f1-345">isPrerelease</span></span>            | <span data-ttu-id="519f1-346">boolean</span><span class="sxs-lookup"><span data-stu-id="519f1-346">boolean</span></span>                    | <span data-ttu-id="519f1-347">是</span><span class="sxs-lookup"><span data-stu-id="519f1-347">yes</span></span>      | <span data-ttu-id="519f1-348">封裝版本是否在發行前版本</span><span class="sxs-lookup"><span data-stu-id="519f1-348">Whether or not the package version is prerelease</span></span>
<span data-ttu-id="519f1-349">語言</span><span class="sxs-lookup"><span data-stu-id="519f1-349">language</span></span>                | <span data-ttu-id="519f1-350">字串</span><span class="sxs-lookup"><span data-stu-id="519f1-350">string</span></span>                     | <span data-ttu-id="519f1-351">no</span><span class="sxs-lookup"><span data-stu-id="519f1-351">no</span></span>       |
<span data-ttu-id="519f1-352">licenseUrl</span><span class="sxs-lookup"><span data-stu-id="519f1-352">licenseUrl</span></span>              | <span data-ttu-id="519f1-353">字串</span><span class="sxs-lookup"><span data-stu-id="519f1-353">string</span></span>                     | <span data-ttu-id="519f1-354">no</span><span class="sxs-lookup"><span data-stu-id="519f1-354">no</span></span>       |
<span data-ttu-id="519f1-355">列出的</span><span class="sxs-lookup"><span data-stu-id="519f1-355">listed</span></span>                  | <span data-ttu-id="519f1-356">boolean</span><span class="sxs-lookup"><span data-stu-id="519f1-356">boolean</span></span>                    | <span data-ttu-id="519f1-357">no</span><span class="sxs-lookup"><span data-stu-id="519f1-357">no</span></span>       | <span data-ttu-id="519f1-358">與封裝是否列出</span><span class="sxs-lookup"><span data-stu-id="519f1-358">Whether or not the package is listed</span></span>
<span data-ttu-id="519f1-359">MinClientVersion</span><span class="sxs-lookup"><span data-stu-id="519f1-359">minClientVersion</span></span>        | <span data-ttu-id="519f1-360">字串</span><span class="sxs-lookup"><span data-stu-id="519f1-360">string</span></span>                     | <span data-ttu-id="519f1-361">no</span><span class="sxs-lookup"><span data-stu-id="519f1-361">no</span></span>       |
<span data-ttu-id="519f1-362">packageHash</span><span class="sxs-lookup"><span data-stu-id="519f1-362">packageHash</span></span>             | <span data-ttu-id="519f1-363">字串</span><span class="sxs-lookup"><span data-stu-id="519f1-363">string</span></span>                     | <span data-ttu-id="519f1-364">是</span><span class="sxs-lookup"><span data-stu-id="519f1-364">yes</span></span>      | <span data-ttu-id="519f1-365">封裝中，使用編碼的雜湊[標準 base 64](https://tools.ietf.org/html/rfc4648#section-4)</span><span class="sxs-lookup"><span data-stu-id="519f1-365">The hash of the package, encoding using [standard base 64](https://tools.ietf.org/html/rfc4648#section-4)</span></span>
<span data-ttu-id="519f1-366">packageHashAlgorithm</span><span class="sxs-lookup"><span data-stu-id="519f1-366">packageHashAlgorithm</span></span>    | <span data-ttu-id="519f1-367">字串</span><span class="sxs-lookup"><span data-stu-id="519f1-367">string</span></span>                     | <span data-ttu-id="519f1-368">是</span><span class="sxs-lookup"><span data-stu-id="519f1-368">yes</span></span>      |
<span data-ttu-id="519f1-369">packageSize</span><span class="sxs-lookup"><span data-stu-id="519f1-369">packageSize</span></span>             | <span data-ttu-id="519f1-370">整數</span><span class="sxs-lookup"><span data-stu-id="519f1-370">integer</span></span>                    | <span data-ttu-id="519f1-371">是</span><span class="sxs-lookup"><span data-stu-id="519f1-371">yes</span></span>      | <span data-ttu-id="519f1-372">封裝.nupkg，以位元組為單位的大小</span><span class="sxs-lookup"><span data-stu-id="519f1-372">The size of the package .nupkg in bytes</span></span>
<span data-ttu-id="519f1-373">projectUrl</span><span class="sxs-lookup"><span data-stu-id="519f1-373">projectUrl</span></span>              | <span data-ttu-id="519f1-374">字串</span><span class="sxs-lookup"><span data-stu-id="519f1-374">string</span></span>                     | <span data-ttu-id="519f1-375">no</span><span class="sxs-lookup"><span data-stu-id="519f1-375">no</span></span>       |
<span data-ttu-id="519f1-376">releaseNotes</span><span class="sxs-lookup"><span data-stu-id="519f1-376">releaseNotes</span></span>            | <span data-ttu-id="519f1-377">字串</span><span class="sxs-lookup"><span data-stu-id="519f1-377">string</span></span>                     | <span data-ttu-id="519f1-378">no</span><span class="sxs-lookup"><span data-stu-id="519f1-378">no</span></span>       |
<span data-ttu-id="519f1-379">requireLicenseAgreement</span><span class="sxs-lookup"><span data-stu-id="519f1-379">requireLicenseAgreement</span></span> | <span data-ttu-id="519f1-380">boolean</span><span class="sxs-lookup"><span data-stu-id="519f1-380">boolean</span></span>                    | <span data-ttu-id="519f1-381">no</span><span class="sxs-lookup"><span data-stu-id="519f1-381">no</span></span>       | <span data-ttu-id="519f1-382">假設`false`如果排除</span><span class="sxs-lookup"><span data-stu-id="519f1-382">Assume `false` if excluded</span></span>
<span data-ttu-id="519f1-383">摘要</span><span class="sxs-lookup"><span data-stu-id="519f1-383">summary</span></span>                 | <span data-ttu-id="519f1-384">字串</span><span class="sxs-lookup"><span data-stu-id="519f1-384">string</span></span>                     | <span data-ttu-id="519f1-385">no</span><span class="sxs-lookup"><span data-stu-id="519f1-385">no</span></span>       |
<span data-ttu-id="519f1-386">標記</span><span class="sxs-lookup"><span data-stu-id="519f1-386">tags</span></span>                    | <span data-ttu-id="519f1-387">字串陣列</span><span class="sxs-lookup"><span data-stu-id="519f1-387">array of strings</span></span>           | <span data-ttu-id="519f1-388">no</span><span class="sxs-lookup"><span data-stu-id="519f1-388">no</span></span>       |
<span data-ttu-id="519f1-389">標題</span><span class="sxs-lookup"><span data-stu-id="519f1-389">title</span></span>                   | <span data-ttu-id="519f1-390">字串</span><span class="sxs-lookup"><span data-stu-id="519f1-390">string</span></span>                     | <span data-ttu-id="519f1-391">no</span><span class="sxs-lookup"><span data-stu-id="519f1-391">no</span></span>       |
<span data-ttu-id="519f1-392">verbatimVersion</span><span class="sxs-lookup"><span data-stu-id="519f1-392">verbatimVersion</span></span>         | <span data-ttu-id="519f1-393">字串</span><span class="sxs-lookup"><span data-stu-id="519f1-393">string</span></span>                     | <span data-ttu-id="519f1-394">no</span><span class="sxs-lookup"><span data-stu-id="519f1-394">no</span></span>       | <span data-ttu-id="519f1-395">版本字串，因為它原先位於.nuspec</span><span class="sxs-lookup"><span data-stu-id="519f1-395">The version string as it is originally found in the .nuspec</span></span>

<span data-ttu-id="519f1-396">封裝`version`屬性是完整的正規化版本字串。</span><span class="sxs-lookup"><span data-stu-id="519f1-396">The package `version` property is the full, normalized version string.</span></span> <span data-ttu-id="519f1-397">這表示，SemVer 2.0.0 的組建資料可能會包含此處。</span><span class="sxs-lookup"><span data-stu-id="519f1-397">This means that SemVer 2.0.0 build data can be included here.</span></span>

<span data-ttu-id="519f1-398">`created`封裝來源，而這通常是短時間類別目錄項目的認可時間戳記之前先收到封裝時，時間戳記。</span><span class="sxs-lookup"><span data-stu-id="519f1-398">The `created` timestamp is when the package was first received by the package source, which is typically a short time before the catalog item's commit timestamp.</span></span>

<span data-ttu-id="519f1-399">`packageHashAlgorithm`是由伺服器實作 represeting 定義字串的雜湊演算法，用來產生`packageHash`。</span><span class="sxs-lookup"><span data-stu-id="519f1-399">The `packageHashAlgorithm` is a string defined by the server implementation represeting the hashing algorithm used to produce the `packageHash`.</span></span> <span data-ttu-id="519f1-400">一律使用 nuget.org`packageHashAlgorithm`值`SHA512`。</span><span class="sxs-lookup"><span data-stu-id="519f1-400">nuget.org always used the `packageHashAlgorithm` value of `SHA512`.</span></span>

<span data-ttu-id="519f1-401">`published`時間戳記是上次列出封裝時的時間。</span><span class="sxs-lookup"><span data-stu-id="519f1-401">The `published` timestamp is the time when the package was last listed.</span></span>

> [!Note]
> <span data-ttu-id="519f1-402">在 nuget.org，`published`值設為 1900 當套件很未列出的年份。</span><span class="sxs-lookup"><span data-stu-id="519f1-402">On nuget.org, the `published` value is set to year 1900 when the package is unlisted.</span></span>

#### <a name="sample-request"></a><span data-ttu-id="519f1-403">範例要求</span><span class="sxs-lookup"><span data-stu-id="519f1-403">Sample request</span></span>

```
GET https://api.nuget.org/v3/catalog0/data/2015.02.01.11.18.40/windowsazure.storage.1.0.0.json
```

#### <a name="sample-response"></a><span data-ttu-id="519f1-404">範例回應</span><span class="sxs-lookup"><span data-stu-id="519f1-404">Sample response</span></span>

[!code-JSON [catalog-package-details.json](./_data/catalog-package-details.json)]

### <a name="package-delete-catalog-items"></a><span data-ttu-id="519f1-405">封裝刪除類別目錄項目</span><span class="sxs-lookup"><span data-stu-id="519f1-405">Package delete catalog items</span></span>

<span data-ttu-id="519f1-406">類別目錄項目型別`PackageDelete`包含資訊指出類別目錄用戶端封裝已從套件來源中刪除，而且已無法再使用 （例如還原） 的任何封裝作業的最少。</span><span class="sxs-lookup"><span data-stu-id="519f1-406">Catalog items with the type `PackageDelete` contain a minimal set of information indicating to catalog clients that a package has been deleted from the package source and is no longer available for any package operation (such as restore).</span></span>

> [!Note]
> <span data-ttu-id="519f1-407">它可能會被刪除的封裝，稍後重新發佈使用相同的封裝識別碼和版本。</span><span class="sxs-lookup"><span data-stu-id="519f1-407">It is possible for a package to be deleted and later republished using the same package ID and version.</span></span> <span data-ttu-id="519f1-408">上 nuget.org，這是非常少見的情況，因為它會破壞套件識別碼和版本，表示為特定的封裝內容的官方用戶端的假設。</span><span class="sxs-lookup"><span data-stu-id="519f1-408">On nuget.org, this is a very rare case as it breaks the official client's assumption that a package ID and version imply a specific package content.</span></span> <span data-ttu-id="519f1-409">如需 nuget.org 要刪除封裝的相關詳細資訊，請參閱[我們原則](../policies/deleting-packages.md)。</span><span class="sxs-lookup"><span data-stu-id="519f1-409">For more information about package deletion on nuget.org, see [our policy](../policies/deleting-packages.md).</span></span>

<span data-ttu-id="519f1-410">封裝刪除類別目錄項目沒有任何額外的屬性，除了[包含在所有的類別目錄保留](#catalog-leaf)。</span><span class="sxs-lookup"><span data-stu-id="519f1-410">Package delete catalog items have no additional properties in addition to those [included on all catalog leaves](#catalog-leaf).</span></span>

<span data-ttu-id="519f1-411">`version`屬性是封裝.nuspec 中找到的原始版本字串。</span><span class="sxs-lookup"><span data-stu-id="519f1-411">The `version` property is the original version string found in the package .nuspec.</span></span>

<span data-ttu-id="519f1-412">`published`屬性是封裝刪除時，通常是做為短時間類別目錄項目的認可時間戳記之前的時間。</span><span class="sxs-lookup"><span data-stu-id="519f1-412">The `published` property is the time when package was deleted, which is typically as short time before the catalog item's commit timestamp.</span></span>

#### <a name="sample-request"></a><span data-ttu-id="519f1-413">範例要求</span><span class="sxs-lookup"><span data-stu-id="519f1-413">Sample request</span></span>

```
GET https://api.nuget.org/v3/catalog0/data/2017.11.02.00.40.00/netstandard1.4_lib.1.0.0-test.json
```

#### <a name="sample-response"></a><span data-ttu-id="519f1-414">範例回應</span><span class="sxs-lookup"><span data-stu-id="519f1-414">Sample response</span></span>

[!code-JSON [catalog-package-delete.json](./_data/catalog-package-delete.json)]

## <a name="cursor"></a><span data-ttu-id="519f1-415">Cursor</span><span class="sxs-lookup"><span data-stu-id="519f1-415">Cursor</span></span>

### <a name="overview"></a><span data-ttu-id="519f1-416">概觀</span><span class="sxs-lookup"><span data-stu-id="519f1-416">Overview</span></span>

<span data-ttu-id="519f1-417">本章節描述一種用戶端概念，雖然不一定是託管的通訊協定，但應該是任何實用的類別目錄用戶端實作的一部分。</span><span class="sxs-lookup"><span data-stu-id="519f1-417">This section describes a client concept that, although is not necessarily mandated by the protocol, should be part of any practical catalog client implementation.</span></span>

<span data-ttu-id="519f1-418">因為此目錄是以時間編製索引的僅附加的資料結構，應儲存在用戶端**游標**代表最多哪個時間點的用戶端已在本機處理類別目錄項目。</span><span class="sxs-lookup"><span data-stu-id="519f1-418">Because the catalog is an append-only data structure indexed by time, the client should store a **cursor** locally, representing up to what point in time the client has processed catalog items.</span></span> <span data-ttu-id="519f1-419">請注意，永遠不會使用用戶端的電腦時鐘會產生此資料指標的值。</span><span class="sxs-lookup"><span data-stu-id="519f1-419">Note that this cursor value should never be generated using the client's machine clock.</span></span> <span data-ttu-id="519f1-420">相反地，值應該來自於目錄物件的`commitTimestamp`值。</span><span class="sxs-lookup"><span data-stu-id="519f1-420">Instead, the value should come from a catalog object's `commitTimestamp` value.</span></span>

<span data-ttu-id="519f1-421">每次用戶端想要處理新的套件來源上的事件，它需要查詢類別目錄的所有類別目錄項目，認可時間戳記大於其預存的資料指標。</span><span class="sxs-lookup"><span data-stu-id="519f1-421">Every time the client wants to process new events on the package source, it need only query the catalog for all catalog items with a commit timestamp greater than its stored cursor.</span></span> <span data-ttu-id="519f1-422">用戶端已順利處理所有新的類別目錄項目之後，它會記錄只會處理做為其新的資料指標值的類別目錄項目的最新的認可時間戳記。</span><span class="sxs-lookup"><span data-stu-id="519f1-422">After the client successfully processes all new catalog items, it records the latest commit timestamp of catalog items just processed as its new cursor value.</span></span>

<span data-ttu-id="519f1-423">使用這個方法，用戶端可以確定永遠不會遺漏任何發生的封裝來源的封裝事件。</span><span class="sxs-lookup"><span data-stu-id="519f1-423">Using this approach, the client can be sure to never miss any package events that occurred on the package source.</span></span>
<span data-ttu-id="519f1-424">此外，用戶端永遠不會有重新處理資料指標的記錄的認可時間戳記之前的舊事件。</span><span class="sxs-lookup"><span data-stu-id="519f1-424">Additionally, the client never has to reprocess old events prior to the cursor's recorded commit timestamp.</span></span>

<span data-ttu-id="519f1-425">資料指標的強大概念用於許多 nuget.org 背景工作，用來保持 V3 API 本身。</span><span class="sxs-lookup"><span data-stu-id="519f1-425">This powerful concept of cursors is used for many of nuget.org background jobs and is used to keep the V3 API itself up-to-date.</span></span> 

### <a name="initial-value"></a><span data-ttu-id="519f1-426">Initial value</span><span class="sxs-lookup"><span data-stu-id="519f1-426">Initial value</span></span>

<span data-ttu-id="519f1-427">當目錄用戶端第一次正在啟動 （並因此會有任何資料指標的值） 時，它應該使用的預設資料指標的值。網路的`System.DateTimeOffset.MinValue`或這類類似可顯示的最小時間戳記的概念。</span><span class="sxs-lookup"><span data-stu-id="519f1-427">When the catalog client is starting for the very first time (and therefore has no cursor value), it should use a default cursor value of .NET's `System.DateTimeOffset.MinValue` or some such analogous notion of minimum representable timestamp.</span></span>

### <a name="iterating-over-catalog-items"></a><span data-ttu-id="519f1-428">逐一查看目錄項目</span><span class="sxs-lookup"><span data-stu-id="519f1-428">Iterating over catalog items</span></span>

<span data-ttu-id="519f1-429">若要查詢的下一個要處理的類別目錄項目集，用戶端應該：</span><span class="sxs-lookup"><span data-stu-id="519f1-429">To query for the next set of catalog items to process, the client should:</span></span>

1. <span data-ttu-id="519f1-430">從本機存放區擷取記錄的資料指標的值。</span><span class="sxs-lookup"><span data-stu-id="519f1-430">Fetch the recorded cursor value from a local store.</span></span>
1. <span data-ttu-id="519f1-431">下載及還原序列化的類別目錄的索引。</span><span class="sxs-lookup"><span data-stu-id="519f1-431">Download and deserialize the catalog index.</span></span>
1. <span data-ttu-id="519f1-432">尋找所有目錄頁面認可時間戳記*大於*資料指標。</span><span class="sxs-lookup"><span data-stu-id="519f1-432">Find all catalog pages with a commit timestamp *greater than* the cursor.</span></span>
1. <span data-ttu-id="519f1-433">宣告空白處理的類別目錄項目的清單。</span><span class="sxs-lookup"><span data-stu-id="519f1-433">Declare an empty list of catalog items to process.</span></span>
1. <span data-ttu-id="519f1-434">針對每個類別目錄 頁面中比對步驟 3:</span><span class="sxs-lookup"><span data-stu-id="519f1-434">For each catalog page matched in step 3:</span></span>
   1. <span data-ttu-id="519f1-435">下載及還原序列化的類別目錄 頁面。</span><span class="sxs-lookup"><span data-stu-id="519f1-435">Download and deserialized the catalog page.</span></span>
   1. <span data-ttu-id="519f1-436">尋找所有類別目錄項目，認可時間戳記*大於*資料指標。</span><span class="sxs-lookup"><span data-stu-id="519f1-436">Find all catalog items with a commit timestamp *greater than* the cursor.</span></span>
   1. <span data-ttu-id="519f1-437">將所有相符的類別目錄項目加入至在步驟 4 中宣告的清單。</span><span class="sxs-lookup"><span data-stu-id="519f1-437">Add all matching catalog items to the list declared in step 4.</span></span>
1. <span data-ttu-id="519f1-438">認可時間戳記排序類別目錄項目清單。</span><span class="sxs-lookup"><span data-stu-id="519f1-438">Sort the catalog item list by commit timestamp.</span></span>
1. <span data-ttu-id="519f1-439">依序處理每個類別目錄項目：</span><span class="sxs-lookup"><span data-stu-id="519f1-439">Process each catalog item in sequence:</span></span>
   1. <span data-ttu-id="519f1-440">下載及還原序列化的類別目錄項目。</span><span class="sxs-lookup"><span data-stu-id="519f1-440">Download and deserialize the catalog item.</span></span>
   1. <span data-ttu-id="519f1-441">適當地回應類別目錄項目的型別。</span><span class="sxs-lookup"><span data-stu-id="519f1-441">React appropriately to the catalog item's type.</span></span>
   1. <span data-ttu-id="519f1-442">處理類別目錄項目文件，以用戶端特定的方式。</span><span class="sxs-lookup"><span data-stu-id="519f1-442">Process the catalog item document in a client-specific fashion.</span></span>
1. <span data-ttu-id="519f1-443">記錄最後一個類別目錄項目認可時間戳記做為新的資料指標值。</span><span class="sxs-lookup"><span data-stu-id="519f1-443">Record the last catalog item's commit timestamp as the new cursor value.</span></span>

<span data-ttu-id="519f1-444">利用這個基本的演算法，用戶端實作可以建置的套件來源的完整檢視所有可用的封裝。</span><span class="sxs-lookup"><span data-stu-id="519f1-444">With this basic algorithm, the client implementation can build up a complete view of all packages available on the package source.</span></span> <span data-ttu-id="519f1-445">用戶端只需要在執行定期為永遠在 封裝來源的最近變更了解此演算法。</span><span class="sxs-lookup"><span data-stu-id="519f1-445">The client need only execute this algorithm periodically to always be aware of the latest changes to the package source.</span></span>

> [!Note]
> <span data-ttu-id="519f1-446">這是此演算法的 nuget.org 用以保存[套件中繼資料](registration-base-url-resource.md)，[封裝內容](package-base-address-resource.md)，[搜尋](search-query-service-resource.md)和[自動完成](search-autocomplete-service-resource.md)資源的最新狀態。</span><span class="sxs-lookup"><span data-stu-id="519f1-446">This is the algorithm that nuget.org uses to keep the [Package Metadata](registration-base-url-resource.md), [Package Content](package-base-address-resource.md), [Search](search-query-service-resource.md) and [Autocomplete](search-autocomplete-service-resource.md) resources up to date.</span></span>

### <a name="dependent-cursors"></a><span data-ttu-id="519f1-447">相依的資料指標</span><span class="sxs-lookup"><span data-stu-id="519f1-447">Dependent cursors</span></span>

<span data-ttu-id="519f1-448">假設有兩個類別目錄用戶端具有 inherant 的相依性，其中一個用戶端的輸出取決於另一個用戶端的輸出。</span><span class="sxs-lookup"><span data-stu-id="519f1-448">Suppose there are two catalog clients that have an inherant dependency where one client's output depends on another client's output.</span></span> 

#### <a name="example"></a><span data-ttu-id="519f1-449">範例</span><span class="sxs-lookup"><span data-stu-id="519f1-449">Example</span></span>

<span data-ttu-id="519f1-450">例如，在 nuget.org 新發行的封裝不應該出現在搜尋資源之前它會出現在封裝的中繼資料資源。</span><span class="sxs-lookup"><span data-stu-id="519f1-450">For example, on nuget.org a newly published package should not appear in the search resource before it appears in the package metadata resource.</span></span> <span data-ttu-id="519f1-451">這是因為官方 NuGet 用戶端所執行的 「 還原 」 作業會使用套件中繼資料資源。</span><span class="sxs-lookup"><span data-stu-id="519f1-451">This is because the "restore" operation performed by the official NuGet client uses the package metadata resource.</span></span> <span data-ttu-id="519f1-452">如果客戶發現封裝使用的搜尋服務，它們應該能夠順利還原該套件，套件中繼資料資源。</span><span class="sxs-lookup"><span data-stu-id="519f1-452">If a customer discovers a package using the search service, they should be able to successfully restore that package using the package metadata resource.</span></span> <span data-ttu-id="519f1-453">換句話說，搜尋資源套件中繼資料資源而定。</span><span class="sxs-lookup"><span data-stu-id="519f1-453">In other words, the search resource depends on the package metadata resource.</span></span> <span data-ttu-id="519f1-454">每個資源都有更新該資源的類別目錄用戶端背景工作。</span><span class="sxs-lookup"><span data-stu-id="519f1-454">Each resource has a catalog client background job updating that resource.</span></span> <span data-ttu-id="519f1-455">每個用戶端有它自己的資料指標。</span><span class="sxs-lookup"><span data-stu-id="519f1-455">Each client has its own cursor.</span></span>

<span data-ttu-id="519f1-456">因為這兩個資源會建置類別目錄更新搜尋資源的類別目錄用戶端資料指標從*必須不超過*封裝中繼資料類別目錄用戶端資料指標。</span><span class="sxs-lookup"><span data-stu-id="519f1-456">Since both resources are built off of the catalog, the cursor of the catalog client that updates the search resource *must not go beyond* the cursor of the package metadata catalog client.</span></span>

#### <a name="algorithm"></a><span data-ttu-id="519f1-457">演算法</span><span class="sxs-lookup"><span data-stu-id="519f1-457">Algorithm</span></span>

<span data-ttu-id="519f1-458">若要實作這項限制，簡單修改上述是演算法：</span><span class="sxs-lookup"><span data-stu-id="519f1-458">To implement this restriction, simple modify the algorithm above to be:</span></span>

1. <span data-ttu-id="519f1-459">從本機存放區擷取記錄的資料指標的值。</span><span class="sxs-lookup"><span data-stu-id="519f1-459">Fetch the recorded cursor value from a local store.</span></span>
1. <span data-ttu-id="519f1-460">下載及還原序列化的類別目錄的索引。</span><span class="sxs-lookup"><span data-stu-id="519f1-460">Download and deserialize the catalog index.</span></span>
1. <span data-ttu-id="519f1-461">尋找所有目錄頁面認可時間戳記*大於*游標**小於或等於其相依性資料指標。**</span><span class="sxs-lookup"><span data-stu-id="519f1-461">Find all catalog pages with a commit timestamp *greater than* the cursor **less than or equal to the dependency's cursor.**</span></span>
1. <span data-ttu-id="519f1-462">宣告空白處理的類別目錄項目的清單。</span><span class="sxs-lookup"><span data-stu-id="519f1-462">Declare an empty list of catalog items to process.</span></span>
1. <span data-ttu-id="519f1-463">針對每個類別目錄 頁面中比對步驟 3:</span><span class="sxs-lookup"><span data-stu-id="519f1-463">For each catalog page matched in step 3:</span></span>
   1. <span data-ttu-id="519f1-464">下載及還原序列化的類別目錄 頁面。</span><span class="sxs-lookup"><span data-stu-id="519f1-464">Download and deserialized the catalog page.</span></span>
   1. <span data-ttu-id="519f1-465">尋找所有類別目錄項目，認可時間戳記*大於*游標**小於或等於其相依性資料指標。**</span><span class="sxs-lookup"><span data-stu-id="519f1-465">Find all catalog items with a commit timestamp *greater than* the cursor **less than or equal to the dependency's cursor.**</span></span>
   1. <span data-ttu-id="519f1-466">將所有相符的類別目錄項目加入至在步驟 4 中宣告的清單。</span><span class="sxs-lookup"><span data-stu-id="519f1-466">Add all matching catalog items to the list declared in step 4.</span></span>
1. <span data-ttu-id="519f1-467">認可時間戳記排序類別目錄項目清單。</span><span class="sxs-lookup"><span data-stu-id="519f1-467">Sort the catalog item list by commit timestamp.</span></span>
1. <span data-ttu-id="519f1-468">依序處理每個類別目錄項目：</span><span class="sxs-lookup"><span data-stu-id="519f1-468">Process each catalog item in sequence:</span></span>
   1. <span data-ttu-id="519f1-469">下載及還原序列化的類別目錄項目。</span><span class="sxs-lookup"><span data-stu-id="519f1-469">Download and deserialize the catalog item.</span></span>
   1. <span data-ttu-id="519f1-470">適當地回應類別目錄項目的型別。</span><span class="sxs-lookup"><span data-stu-id="519f1-470">React appropriately to the catalog item's type.</span></span>
   1. <span data-ttu-id="519f1-471">處理類別目錄項目文件，以用戶端特定的方式。</span><span class="sxs-lookup"><span data-stu-id="519f1-471">Process the catalog item document in a client-specific fashion.</span></span>
1. <span data-ttu-id="519f1-472">記錄最後一個類別目錄項目認可時間戳記做為新的資料指標值。</span><span class="sxs-lookup"><span data-stu-id="519f1-472">Record the last catalog item's commit timestamp as the new cursor value.</span></span>

<span data-ttu-id="519f1-473">使用這個修改過的演算法，您可以建立一個系統相依的類別目錄用戶端的所有產生自己的特定索引、 成品等等。</span><span class="sxs-lookup"><span data-stu-id="519f1-473">Using this modified algorithm, you can build a system of dependent catalog clients all producing their own specific indexes, artifacts, etc.</span></span>