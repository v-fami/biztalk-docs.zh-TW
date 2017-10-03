---
title: "附錄 a： 元件介面方法 |Microsoft 文件"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- component interfaces, methods
- methods, component interfaces
- component interface methods
ms.assetid: c8377589-fbdf-4287-b822-53263a00381d
caps.latest.revision: "9"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 61cb5b87cb063f22c889291b8eff3b2be50d64a7
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/20/2017
---
# <a name="appendix-a-component-interface-methods"></a><span data-ttu-id="b8616-102">附錄 a： 元件介面方法</span><span class="sxs-lookup"><span data-stu-id="b8616-102">Appendix A: Component Interface Methods</span></span>
<span data-ttu-id="b8616-103">Microsoft BizTalk Adapter for PeopleSoft Enterprise 有針對元件介面提供標準方法。</span><span class="sxs-lookup"><span data-stu-id="b8616-103">Microsoft BizTalk Adapter for PeopleSoft Enterprise provides standard methods for component interfaces.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="b8616-104">前版方法中的 `interactiveMode` 參數有助於偵錯對後端的呼叫 (`Create/CreateEx`、`Update/UpdateEx` 和 `DeleteOnly`)。</span><span class="sxs-lookup"><span data-stu-id="b8616-104">The `interactiveMode` parameter, in the Ex-version of the methods, assists in debugging a call to the back-end (`Create/CreateEx`, `Update/UpdateEx`, and `DeleteOnly`).</span></span> <span data-ttu-id="b8616-105">對後端之 *Ex 呼叫中的每個項目都是分別進行呼叫，因此您會清楚知道哪個項目執行失敗。</span><span class="sxs-lookup"><span data-stu-id="b8616-105">Each item in the *Ex call to the back-end is called separately, so you know exactly which item failed.</span></span> <span data-ttu-id="b8616-106">沒有效能降低當您使用\*Ex 方法由於每個屬性的項目都會收到不同的呼叫。</span><span class="sxs-lookup"><span data-stu-id="b8616-106">There is a decrease in performance when you use an \*Ex method because each property's item receives a separate call.</span></span> <span data-ttu-id="b8616-107">您可以使用開發\*Ex 方法後再切換至主要方法 (例如， `Create`) 生產環境。</span><span class="sxs-lookup"><span data-stu-id="b8616-107">You can develop with \*Ex method and then switch to the main method (for example, `Create`) for production.</span></span> <span data-ttu-id="b8616-108">您也可以使用在實際執行偵錯參數，使用此方法之間切換， \*Ex 方法。</span><span class="sxs-lookup"><span data-stu-id="b8616-108">You can also use a debug switch at production to switch between using the method and the \*Ex method.</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="b8616-109">本節內容</span><span class="sxs-lookup"><span data-stu-id="b8616-109">In This Section</span></span>  
  
-   [<span data-ttu-id="b8616-110">CreateEx 方法</span><span class="sxs-lookup"><span data-stu-id="b8616-110">CreateEx Method</span></span>](../core/createex-method.md)  
  
-   [<span data-ttu-id="b8616-111">DeleteOnly 方法</span><span class="sxs-lookup"><span data-stu-id="b8616-111">DeleteOnly Method</span></span>](../core/deleteonly-method.md)  
  
-   [<span data-ttu-id="b8616-112">Find 方法</span><span class="sxs-lookup"><span data-stu-id="b8616-112">Find Method</span></span>](../core/find-method.md)  
  
-   [<span data-ttu-id="b8616-113">Get 方法</span><span class="sxs-lookup"><span data-stu-id="b8616-113">Get Method</span></span>](../core/get-method.md)  
  
-   [<span data-ttu-id="b8616-114">UpdateEx 方法</span><span class="sxs-lookup"><span data-stu-id="b8616-114">UpdateEx Method</span></span>](../core/updateex-method.md)  
  
-   [<span data-ttu-id="b8616-115">元件介面使用者定義方法</span><span class="sxs-lookup"><span data-stu-id="b8616-115">Component Interface User-Defined Methods</span></span>](../core/component-interface-user-defined-methods.md)  
  
-   [<span data-ttu-id="b8616-116">Effective Date 屬性</span><span class="sxs-lookup"><span data-stu-id="b8616-116">Effective Date Properties</span></span>](../core/effective-date-properties.md)