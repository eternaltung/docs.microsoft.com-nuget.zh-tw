---
title: 服務的索引，NuGet API
description: 服務索引是 NuGet HTTP 應用程式開發介面的進入點，並列舉伺服器的功能。
author: joelverhagen
ms.author: jver
manager: skofman
ms.date: 10/26/2017
ms.topic: reference
ms.reviewer: kraigb
ms.openlocfilehash: 84e623e8480e4d17edad2ec3b2da6dcb6e53d21b
ms.sourcegitcommit: 3eab9c4dd41ea7ccd2c28bb5ab16f6fbbec13708
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/26/2018
ms.locfileid: "31822090"
---
# <a name="service-index"></a>服務索引

服務索引是 JSON 文件是 NuGet 套件來源的進入點，可讓用戶端實作探索套件來源的功能。 服務索引會使用兩個必要屬性的 JSON 物件： `version` （服務索引的結構描述版本） 和`resources`（端點或套件來源的功能）。

nuget.org 的服務索引位於`https://api.nuget.org/v3/index.json`。

## <a name="versioning"></a>版本控制

`version`值是 SemVer 2.0.0 可以剖析版本的字串表示服務索引的結構描述版本。 API 要求的版本字串的主要版本號碼`3`。 服務索引結構描述會進行非中斷變更，就會增加的版本字串的次要版本。

服務索引中的每個資源的版本也是獨立於服務索引結構描述版本。

目前的結構描述版本是`3.0.0`。 `3.0.0`版本功能上相當於舊版`3.0.0-beta.1`版本，但應該是慣用的穩定，已定義的結構描述更清楚地通訊。

## <a name="http-methods"></a>HTTP 方法

服務索引是使用 HTTP 方法存取`GET`和`HEAD`。

## <a name="resources"></a>資源

`resources`屬性包含此封裝來源所支援的資源陣列。

### <a name="resource"></a>資源

資源是中的物件`resources`陣列。 它代表套件來源已建立版本功能。 資源具有下列屬性：

名稱          | 類型   | 必要 | 注意
------------- | ------ | -------- | -----
@id           | 字串 | 是      | 資源 URL
@type         | 字串 | 是      | 字串常數，其代表資源類型
註解       | 字串 | 否       | 可讀取描述的資源

`@id`是 URL，必須是絕對路徑，也必須是具有 HTTP 或 HTTPS 的結構描述。

`@type`用來識別與資源進行互動時所要使用的特定通訊協定。 資源的類型是不透明的字串，但通常具有格式：

    {RESOURCE_NAME}/{RESOURCE_VERSION}

用戶端預期硬`@type`他們了解及套件來源的服務索引中查閱值。 確切`@type`現今使用的值會列舉中列出的個別資源的參考文件上[API 概觀](overview.md#resources-and-schema)。

本文件中，為了不同資源的相關文件將基本上是依據`{RESOURCE_NAME}`服務索引相當於群組案例中找到。 

沒有每個資源都有唯一的需求`@id`或`@type`。 這是由用戶端實作，以判斷哪個資源，而不用另一個。 一個可能的實作是相同或相容的資源`@type`可用以循環配置資源方式發生連線失敗或伺服器發生錯誤。

### <a name="sample-request"></a>範例要求

取得 https://api.nuget.org/v3/index.json

### <a name="sample-response"></a>範例回應

[!code-JSON [service-index.json](./_data/service-index.json)]
