---
title: "內容錯誤 |Microsoft 文件"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: d297db1a-352c-4e5a-b0aa-6edae8d74824
caps.latest.revision: "5"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: d4c03358ba08df939e7058a6d73603969dcddd8e
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/20/2017
---
# <a name="properties-errors"></a><span data-ttu-id="fed3a-102">內容錯誤</span><span class="sxs-lookup"><span data-stu-id="fed3a-102">Properties Errors</span></span>
<span data-ttu-id="fed3a-103">本節包含診斷及解決 WCF 屬性錯誤的詳細的資訊。</span><span class="sxs-lookup"><span data-stu-id="fed3a-103">This section contains detailed information for diagnosing and resolving WCF Properties errors.</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="fed3a-104">本節內容</span><span class="sxs-lookup"><span data-stu-id="fed3a-104">In This Section</span></span>  
  
-   [<span data-ttu-id="fed3a-105">錯誤載入屬性</span><span class="sxs-lookup"><span data-stu-id="fed3a-105">Error loading properties</span></span>](../core/error-loading-properties.md)  
  
-   [<span data-ttu-id="fed3a-106">儲存屬性時發生錯誤</span><span class="sxs-lookup"><span data-stu-id="fed3a-106">Error saving properties</span></span>](../core/error-saving-properties.md)  
  
-   [<span data-ttu-id="fed3a-107">無效的專案位置</span><span class="sxs-lookup"><span data-stu-id="fed3a-107">Invalid project location</span></span>](../core/invalid-project-location.md)  
  
-   [<span data-ttu-id="fed3a-108">訊息部分遺失元素</span><span class="sxs-lookup"><span data-stu-id="fed3a-108">Message part missing element</span></span>](../core/message-part-missing-element.md)  
  
-   [<span data-ttu-id="fed3a-109">不支援沒有部分訊息類型</span><span class="sxs-lookup"><span data-stu-id="fed3a-109">Message types without parts are not supported</span></span>](../core/message-types-without-parts-are-not-supported.md)  
  
-   [<span data-ttu-id="fed3a-110">OutboundCustomHeaders 沒有正確的格式</span><span class="sxs-lookup"><span data-stu-id="fed3a-110">OutboundCustomHeaders does not have correct format</span></span>](../core/outboundcustomheaders-does-not-have-correct-format.md)  
  
-   [<span data-ttu-id="fed3a-111">專案位置不是空白</span><span class="sxs-lookup"><span data-stu-id="fed3a-111">The project location is not empty</span></span>](../core/the-project-location-is-not-empty.md)  
  
-   [<span data-ttu-id="fed3a-112">無法從 XML 組態建立端點行為組態項目</span><span class="sxs-lookup"><span data-stu-id="fed3a-112">Unable to create endpoint behavior configuration element from XML configuration</span></span>](../core/unable-to-create-endpoint-behavior-configuration-element-from-xml-configuration.md)  
  
-   [<span data-ttu-id="fed3a-113">無法從 XML 組態建立服務行為組態項目</span><span class="sxs-lookup"><span data-stu-id="fed3a-113">Unable to create service behavior configuration element from XML configuration</span></span>](../core/unable-to-create-service-behavior-configuration-element-from-xml-configuration.md)  
  
-   [<span data-ttu-id="fed3a-114">無法匯出用戶端端點組態</span><span class="sxs-lookup"><span data-stu-id="fed3a-114">Unable to export client endpoint configuration</span></span>](../core/unable-to-export-client-endpoint-configuration.md)  
  
-   [<span data-ttu-id="fed3a-115">無法匯出服務端點組態</span><span class="sxs-lookup"><span data-stu-id="fed3a-115">Unable to export service endpoint configuration</span></span>](../core/unable-to-export-service-endpoint-configuration.md)  
  
-   [<span data-ttu-id="fed3a-116">找不到輸入內文路徑運算式的內容</span><span class="sxs-lookup"><span data-stu-id="fed3a-116">Unable to find content for inbound body path expression</span></span>](../core/unable-to-find-content-for-inbound-body-path-expression.md)  
  
-   [<span data-ttu-id="fed3a-117">找不到輸入內文路徑運算式相符項目</span><span class="sxs-lookup"><span data-stu-id="fed3a-117">Unable to find match for inbound body path expression</span></span>](../core/unable-to-find-match-for-inbound-body-path-expression.md)  
  
-   [<span data-ttu-id="fed3a-118">未預期的根項目</span><span class="sxs-lookup"><span data-stu-id="fed3a-118">Unexpected root element</span></span>](../core/unexpected-root-element.md)  
  
-   [<span data-ttu-id="fed3a-119">無法辨認封送處理類型的輸出訊息</span><span class="sxs-lookup"><span data-stu-id="fed3a-119">Unrecognized outbound message marshalling type</span></span>](../core/unrecognized-outbound-message-marshalling-type.md)  
  
-   [<span data-ttu-id="fed3a-120">不支援的安全性演算法套件</span><span class="sxs-lookup"><span data-stu-id="fed3a-120">Unsupported security algorithm suite</span></span>](../core/unsupported-security-algorithm-suite.md)  
  
-   [<span data-ttu-id="fed3a-121">不支援的交易通訊協定</span><span class="sxs-lookup"><span data-stu-id="fed3a-121">Unsupported transaction protocol</span></span>](../core/unsupported-transaction-protocol.md)  
  
-   [<span data-ttu-id="fed3a-122">WCF 用戶端必須允許模擬使用單一登入</span><span class="sxs-lookup"><span data-stu-id="fed3a-122">WCF client must allow impersonation to use Single Sign-On</span></span>](../core/wcf-client-must-allow-impersonation-to-use-single-sign-on.md)  
  
-   [<span data-ttu-id="fed3a-123">可能未安裝 Windows 元件</span><span class="sxs-lookup"><span data-stu-id="fed3a-123">Windows components may not be installed</span></span>](../core/windows-components-may-not-be-installed.md)