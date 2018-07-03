---
title: 在 Siebel 商務服務的作業 |Microsoft Docs
ms.custom: ''
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- operations, on business services
- business services, operations on
ms.assetid: 29a1a88c-8c7b-46f1-8faf-49ddd32ba2f0
caps.latest.revision: 4
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: df24fa8ee0bd51ddf919e5f88a47ceae9d0743fa
ms.sourcegitcommit: 266308ec5c6a9d8d80ff298ee6051b4843c5d626
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/27/2018
ms.locfileid: "37001367"
---
# <a name="operations-on-business-services-in-siebel"></a><span data-ttu-id="223d8-102">在 Siebel 商務服務的相關作業</span><span class="sxs-lookup"><span data-stu-id="223d8-102">Operations on Business Services in Siebel</span></span>
<span data-ttu-id="223d8-103">Siebel 商務服務是可直接叫用在 Siebel 商務方法的集合。</span><span class="sxs-lookup"><span data-stu-id="223d8-103">A Siebel business service is a collection of business methods that can be directly invoked in Siebel.</span></span> <span data-ttu-id="223d8-104">商務元件和商務物件是特定資料和 Siebel 中的資料表相關聯，而商務服務叫用來執行特定工作的物件。</span><span class="sxs-lookup"><span data-stu-id="223d8-104">Whereas business components and business objects are associated to specific data and tables in Siebel, business services invoke the objects to perform specific tasks.</span></span>  
  
 <span data-ttu-id="223d8-105">[!INCLUDE[adaptersiebel_short](../../includes/adaptersiebel-short-md.md)]呈現商務服務方法，作業名稱，並支援 IN、 OUT 及 INOUT 參數。</span><span class="sxs-lookup"><span data-stu-id="223d8-105">The [!INCLUDE[adaptersiebel_short](../../includes/adaptersiebel-short-md.md)] surfaces the business service methods as operation names and supports IN, OUT, and INOUT parameters.</span></span> <span data-ttu-id="223d8-106">例如，[!INCLUDE[adaptersiebel_short](../../includes/adaptersiebel-short-md.md)]表面**ATPRunCheck**做為作業的方法。</span><span class="sxs-lookup"><span data-stu-id="223d8-106">For example, the [!INCLUDE[adaptersiebel_short](../../includes/adaptersiebel-short-md.md)] surfaces the **ATPRunCheck** method as an operation.</span></span> <span data-ttu-id="223d8-107">這個方法所屬**ATP**商務服務。</span><span class="sxs-lookup"><span data-stu-id="223d8-107">This method belongs to the **ATP** business service.</span></span>  
  
 <span data-ttu-id="223d8-108">某些條件[!INCLUDE[adaptersiebel_short](../../includes/adaptersiebel-short-md.md)]加諸使用 Siebel 商務服務時：</span><span class="sxs-lookup"><span data-stu-id="223d8-108">Certain conditions that the [!INCLUDE[adaptersiebel_short](../../includes/adaptersiebel-short-md.md)] imposes while using the Siebel business services:</span></span>  
  
- <span data-ttu-id="223d8-109">Siebel 商務服務方法會接受並沒有指定的資料類型的引數，如果配接器會公開為文字的引數。</span><span class="sxs-lookup"><span data-stu-id="223d8-109">If a Siebel business service method takes an argument that does not have the data type specified, the adapter exposes the argument as TEXT.</span></span>  
  
- <span data-ttu-id="223d8-110">Siebel 商務服務方法引數可以是下列類型：</span><span class="sxs-lookup"><span data-stu-id="223d8-110">A Siebel business service method argument can be of the following types:</span></span>  
  
  - <span data-ttu-id="223d8-111">字串 （公開為 xsd: string）</span><span class="sxs-lookup"><span data-stu-id="223d8-111">String (exposed as xsd:string)</span></span>  
  
  - <span data-ttu-id="223d8-112">數字 (公開為 xsd: decimal)</span><span class="sxs-lookup"><span data-stu-id="223d8-112">Number (exposed as xsd: decimal)</span></span>  
  
  - <span data-ttu-id="223d8-113">日期 （公開為 xsd:DateTime，使用模式 facet 表示之時間部分必須設定為 00:00:00）</span><span class="sxs-lookup"><span data-stu-id="223d8-113">Date (exposed as xsd:DateTime, with pattern facet indicating that time part must be set to 00:00:00)</span></span>  
  
  - <span data-ttu-id="223d8-114">階層 （公開為 xsd: string）</span><span class="sxs-lookup"><span data-stu-id="223d8-114">Hierarchy (exposed as xsd:string)</span></span>  
  
  - <span data-ttu-id="223d8-115">整合物件 （公開為 xsd: string）</span><span class="sxs-lookup"><span data-stu-id="223d8-115">Integration Object (exposed as xsd:string)</span></span>  
  
    <span data-ttu-id="223d8-116">此外，商務服務方法會驗證傳遞的引數的值是否符合對應的型別。</span><span class="sxs-lookup"><span data-stu-id="223d8-116">Also, the business service method verifies whether the value passed for an argument complies with the corresponding type.</span></span> <span data-ttu-id="223d8-117">因此，如果商務服務方法會接受或傳回不符合對應的引數類型的值，配接器可能會擲回例外狀況。</span><span class="sxs-lookup"><span data-stu-id="223d8-117">So, if a business service method accepts or returns values that do not comply with the corresponding argument type, the adapter may throw an exception.</span></span> <span data-ttu-id="223d8-118">如果配接器未成功叫用商務服務方法，結構描述驗證可能會失敗。</span><span class="sxs-lookup"><span data-stu-id="223d8-118">If the adapter does succeed in invoking the business service method, the schema validation may fail.</span></span>  
  
  <span data-ttu-id="223d8-119">如需詳細資訊：</span><span class="sxs-lookup"><span data-stu-id="223d8-119">For information about:</span></span>  
  
- <span data-ttu-id="223d8-120">執行使用 BizTalk Server 的商務服務的相關作業，請參閱[叫用商務服務方法使用 BizTalk Server 和 Siebel 配接器](../../adapters-and-accelerators/adapter-siebel/invoke-business-service-methods-using-biztalk-server-and-the-siebel-adapter.md)。</span><span class="sxs-lookup"><span data-stu-id="223d8-120">Performing operations on business services using BizTalk Server, see [Invoke Business Service Methods Using BizTalk Server and the Siebel adapter](../../adapters-and-accelerators/adapter-siebel/invoke-business-service-methods-using-biztalk-server-and-the-siebel-adapter.md).</span></span>  
  
- <span data-ttu-id="223d8-121">訊息結構和 SOAP 動作的商務服務執行作業，請參閱[商務服務作業的訊息結構描述](../../adapters-and-accelerators/adapter-siebel/message-schemas-for-business-service-operations.md))。</span><span class="sxs-lookup"><span data-stu-id="223d8-121">Message structures and SOAP actions to perform operations on business services, see [Message Schemas for Business Service Operations](../../adapters-and-accelerators/adapter-siebel/message-schemas-for-business-service-operations.md)).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="223d8-122">另請參閱</span><span class="sxs-lookup"><span data-stu-id="223d8-122">See Also</span></span>  
 [<span data-ttu-id="223d8-123">連接到 SAP 系統使用配接器</span><span class="sxs-lookup"><span data-stu-id="223d8-123">Connect to an SAP system using the adapter</span></span>](../../adapters-and-accelerators/adapter-sap/connect-to-an-sap-system-using-the-adapter.md)