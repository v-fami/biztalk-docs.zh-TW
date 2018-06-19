---
title: 在 Siebel 商務服務的相關作業 |Microsoft 文件
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
ms.openlocfilehash: a1ffd133d76b1f8cae3f1732e48f817fe4fb26b8
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/20/2017
ms.locfileid: "22221942"
---
# <a name="operations-on-business-services-in-siebel"></a><span data-ttu-id="bd022-102">在 Siebel 商務服務的相關作業</span><span class="sxs-lookup"><span data-stu-id="bd022-102">Operations on Business Services in Siebel</span></span>
<span data-ttu-id="bd022-103">Siebel 商務服務是可以在 Siebel 中直接叫用的商務方法的集合。</span><span class="sxs-lookup"><span data-stu-id="bd022-103">A Siebel business service is a collection of business methods that can be directly invoked in Siebel.</span></span> <span data-ttu-id="bd022-104">商務元件和商務物件都已關聯到特定的資料和 Siebel 中的資料表，而商務服務叫用來執行特定工作的物件。</span><span class="sxs-lookup"><span data-stu-id="bd022-104">Whereas business components and business objects are associated to specific data and tables in Siebel, business services invoke the objects to perform specific tasks.</span></span>  
  
 <span data-ttu-id="bd022-105">[!INCLUDE[adaptersiebel_short](../../includes/adaptersiebel-short-md.md)]呈現的商務服務方法，作業名稱，並支援 IN、 OUT 和 INOUT 參數。</span><span class="sxs-lookup"><span data-stu-id="bd022-105">The [!INCLUDE[adaptersiebel_short](../../includes/adaptersiebel-short-md.md)] surfaces the business service methods as operation names and supports IN, OUT, and INOUT parameters.</span></span> <span data-ttu-id="bd022-106">例如，[!INCLUDE[adaptersiebel_short](../../includes/adaptersiebel-short-md.md)]介面**ATPRunCheck**做為作業的方法。</span><span class="sxs-lookup"><span data-stu-id="bd022-106">For example, the [!INCLUDE[adaptersiebel_short](../../includes/adaptersiebel-short-md.md)] surfaces the **ATPRunCheck** method as an operation.</span></span> <span data-ttu-id="bd022-107">這個方法屬於**ATP**商務服務。</span><span class="sxs-lookup"><span data-stu-id="bd022-107">This method belongs to the **ATP** business service.</span></span>  
  
 <span data-ttu-id="bd022-108">某些條件[!INCLUDE[adaptersiebel_short](../../includes/adaptersiebel-short-md.md)]會加諸使用 Siebel 商務服務時：</span><span class="sxs-lookup"><span data-stu-id="bd022-108">Certain conditions that the [!INCLUDE[adaptersiebel_short](../../includes/adaptersiebel-short-md.md)] imposes while using the Siebel business services:</span></span>  
  
-   <span data-ttu-id="bd022-109">Siebel 商務服務方法會接受並沒有指定的資料類型的引數，如果配接器會公開引數為文字。</span><span class="sxs-lookup"><span data-stu-id="bd022-109">If a Siebel business service method takes an argument that does not have the data type specified, the adapter exposes the argument as TEXT.</span></span>  
  
-   <span data-ttu-id="bd022-110">Siebel 商務服務方法引數可以是下列類型：</span><span class="sxs-lookup"><span data-stu-id="bd022-110">A Siebel business service method argument can be of the following types:</span></span>  
  
    -   <span data-ttu-id="bd022-111">字串 （公開為 xsd: string）</span><span class="sxs-lookup"><span data-stu-id="bd022-111">String (exposed as xsd:string)</span></span>  
  
    -   <span data-ttu-id="bd022-112">數字 (公開為 xsd： 十進位)</span><span class="sxs-lookup"><span data-stu-id="bd022-112">Number (exposed as xsd: decimal)</span></span>  
  
    -   <span data-ttu-id="bd022-113">日期 （公開為 xsd:DateTime、 使用模式 facet，指出時間部分必須設定為 00:00:00）</span><span class="sxs-lookup"><span data-stu-id="bd022-113">Date (exposed as xsd:DateTime, with pattern facet indicating that time part must be set to 00:00:00)</span></span>  
  
    -   <span data-ttu-id="bd022-114">階層 （公開為 xsd: string）</span><span class="sxs-lookup"><span data-stu-id="bd022-114">Hierarchy (exposed as xsd:string)</span></span>  
  
    -   <span data-ttu-id="bd022-115">整合物件 （公開為 xsd: string）</span><span class="sxs-lookup"><span data-stu-id="bd022-115">Integration Object (exposed as xsd:string)</span></span>  
  
     <span data-ttu-id="bd022-116">此外，商務服務方法會驗證引數傳遞的值是否符合對應型別。</span><span class="sxs-lookup"><span data-stu-id="bd022-116">Also, the business service method verifies whether the value passed for an argument complies with the corresponding type.</span></span> <span data-ttu-id="bd022-117">因此，如果商務服務方法會接受或傳回不符合對應的引數類型的值，配接器可能會擲回例外狀況。</span><span class="sxs-lookup"><span data-stu-id="bd022-117">So, if a business service method accepts or returns values that do not comply with the corresponding argument type, the adapter may throw an exception.</span></span> <span data-ttu-id="bd022-118">如果配接器無法順利叫用商務服務方法，結構描述驗證可能會失敗。</span><span class="sxs-lookup"><span data-stu-id="bd022-118">If the adapter does succeed in invoking the business service method, the schema validation may fail.</span></span>  
  
 <span data-ttu-id="bd022-119">如需詳細資訊：</span><span class="sxs-lookup"><span data-stu-id="bd022-119">For information about:</span></span>  
  
-   <span data-ttu-id="bd022-120">執行的作業上使用 BizTalk Server 的商務服務，請參閱[叫用商務服務方法使用 BizTalk Server 和 Siebel 配接器](../../adapters-and-accelerators/adapter-siebel/invoke-business-service-methods-using-biztalk-server-and-the-siebel-adapter.md)。</span><span class="sxs-lookup"><span data-stu-id="bd022-120">Performing operations on business services using BizTalk Server, see [Invoke Business Service Methods Using BizTalk Server and the Siebel adapter](../../adapters-and-accelerators/adapter-siebel/invoke-business-service-methods-using-biztalk-server-and-the-siebel-adapter.md).</span></span>  
  
-   <span data-ttu-id="bd022-121">訊息結構和商務服務上執行作業，請參閱的 SOAP 動作[商務服務作業的訊息結構描述](../../adapters-and-accelerators/adapter-siebel/message-schemas-for-business-service-operations.md))。</span><span class="sxs-lookup"><span data-stu-id="bd022-121">Message structures and SOAP actions to perform operations on business services, see [Message Schemas for Business Service Operations](../../adapters-and-accelerators/adapter-siebel/message-schemas-for-business-service-operations.md)).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="bd022-122">另請參閱</span><span class="sxs-lookup"><span data-stu-id="bd022-122">See Also</span></span>  
 [<span data-ttu-id="bd022-123">連接至 SAP 系統使用配接器</span><span class="sxs-lookup"><span data-stu-id="bd022-123">Connect to an SAP system using the adapter</span></span>](../../adapters-and-accelerators/adapter-sap/connect-to-an-sap-system-using-the-adapter.md)