---
title: BizTalk adapter for Siebel eBusiness 應用程式的概觀 |Microsoft 文件
ms.custom: ''
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- overview, adapter
- adapter, overview of
- adapter, overview
ms.assetid: 41ab7d42-7096-45ef-9763-a5ccf88eb652
caps.latest.revision: 5
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: efcc3a90f7025a5f396cd778676f5f3152bc7657
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/20/2017
ms.locfileid: "22222038"
---
# <a name="overview-of-biztalk-adapter-for-siebel-ebusiness-applications"></a><span data-ttu-id="70a97-102">BizTalk Adapter for Siebel eBusiness 應用程式中的概觀</span><span class="sxs-lookup"><span data-stu-id="70a97-102">Overview of BizTalk Adapter for Siebel eBusiness Applications</span></span>
<span data-ttu-id="70a97-103">[!INCLUDE[adaptersiebel](../../includes/adaptersiebel-md.md)]公開為 WCF 服務的 Siebel 系統。</span><span class="sxs-lookup"><span data-stu-id="70a97-103">The [!INCLUDE[adaptersiebel](../../includes/adaptersiebel-md.md)] exposes the Siebel system as a WCF service.</span></span> <span data-ttu-id="70a97-104">配接器用戶端可以交換 SOAP 訊息的配接器，以執行 Siebel 系統上的作業。</span><span class="sxs-lookup"><span data-stu-id="70a97-104">Adapter clients can perform operations on the Siebel system by exchanging SOAP messages with the adapter.</span></span> <span data-ttu-id="70a97-105">配接器會取用 WCF 訊息，並使適當地呼叫 Siebel 系統執行的作業。</span><span class="sxs-lookup"><span data-stu-id="70a97-105">The adapter consumes the WCF message and makes appropriate calls to the Siebel system to perform the operation.</span></span> <span data-ttu-id="70a97-106">配接器傳回來自 Siebel 系統的回應傳回給用戶端的 SOAP 訊息格式。</span><span class="sxs-lookup"><span data-stu-id="70a97-106">The adapter returns the response from the Siebel system back to the client in the form of SOAP messages.</span></span>  
  
 <span data-ttu-id="70a97-107">[!INCLUDE[adaptersiebel_short](../../includes/adaptersiebel-short-md.md)]介面描述中繼資料的 Siebel 成品 （商業元件、 商務服務） 結構的 SOAP 訊息的 WSDL 格式。</span><span class="sxs-lookup"><span data-stu-id="70a97-107">The [!INCLUDE[adaptersiebel_short](../../includes/adaptersiebel-short-md.md)] surfaces metadata of Siebel artifacts (business components, business services) that describes the structure of a SOAP message in the form of WSDL.</span></span> <span data-ttu-id="70a97-108">[!INCLUDE[adaptersiebel_short](../../includes/adaptersiebel-short-md.md)]使用[!INCLUDE[addadapterservreflong](../../includes/addadapterservreflong-md.md)]和[!INCLUDE[consumeadapterservlong](../../includes/consumeadapterservlong-md.md)]讓配接器用戶端擷取作業的中繼資料，並產生可使用的程式設計成品程式設計方案中。</span><span class="sxs-lookup"><span data-stu-id="70a97-108">The [!INCLUDE[adaptersiebel_short](../../includes/adaptersiebel-short-md.md)] uses the [!INCLUDE[addadapterservreflong](../../includes/addadapterservreflong-md.md)] and [!INCLUDE[consumeadapterservlong](../../includes/consumeadapterservlong-md.md)] to enable adapter clients to retrieve metadata for operations and generates programming artifacts that can be used in your programming solution.</span></span>  
  
 <span data-ttu-id="70a97-109">[!INCLUDE[adaptersiebel_short](../../includes/adaptersiebel-short-md.md)]使用 Siebel COM 資料控制項存取 Siebel 系統。</span><span class="sxs-lookup"><span data-stu-id="70a97-109">The [!INCLUDE[adaptersiebel_short](../../includes/adaptersiebel-short-md.md)] uses the Siebel COM Data Control to access the Siebel system.</span></span> <span data-ttu-id="70a97-110">Siebel COM 資料控制項來自配套 Siebel Web 用戶端。</span><span class="sxs-lookup"><span data-stu-id="70a97-110">The Siebel COM Data Control comes bundled with the Siebel Web client.</span></span> <span data-ttu-id="70a97-111">因此，確定您已安裝在同一部電腦上的 Siebel Web 用戶端[!INCLUDE[adaptersiebel_short](../../includes/adaptersiebel-short-md.md)]。</span><span class="sxs-lookup"><span data-stu-id="70a97-111">Hence, make sure you have the Siebel Web client installed on the same computer as the [!INCLUDE[adaptersiebel_short](../../includes/adaptersiebel-short-md.md)].</span></span> <span data-ttu-id="70a97-112">您可以使用[!INCLUDE[adaptersiebel_short](../../includes/adaptersiebel-short-md.md)]與 Siebel 系統通訊，以下列方式：</span><span class="sxs-lookup"><span data-stu-id="70a97-112">You can use the [!INCLUDE[adaptersiebel_short](../../includes/adaptersiebel-short-md.md)] to communicate with the Siebel system in the following ways:</span></span>  
  
-   <span data-ttu-id="70a97-113">開發 BizTalk 應用程式。</span><span class="sxs-lookup"><span data-stu-id="70a97-113">By developing BizTalk applications.</span></span> <span data-ttu-id="70a97-114">請參閱[開發 BizTalk Server 應用程式](../../core/developing-biztalk-server-applications.md)。</span><span class="sxs-lookup"><span data-stu-id="70a97-114">See [Developing BizTalk Server Applications](../../core/developing-biztalk-server-applications.md).</span></span>
  
-   <span data-ttu-id="70a97-115">使用 WCF 服務模型。</span><span class="sxs-lookup"><span data-stu-id="70a97-115">By using the WCF service model.</span></span> <span data-ttu-id="70a97-116">請參閱[開發 Siebel 應用程式使用 WCF 服務模型](../../adapters-and-accelerators/adapter-siebel/develop-siebel-applications-using-the-wcf-service-model.md)。</span><span class="sxs-lookup"><span data-stu-id="70a97-116">See [Develop Siebel Applications by Using the WCF Service Model](../../adapters-and-accelerators/adapter-siebel/develop-siebel-applications-using-the-wcf-service-model.md).</span></span>  
  
-   <span data-ttu-id="70a97-117">使用 WCF 通道模型。</span><span class="sxs-lookup"><span data-stu-id="70a97-117">By using the WCF channel model.</span></span> <span data-ttu-id="70a97-118">請參閱開發的 Oracle 資料庫應用程式使用 WCF 通道模型[輸入連結描述](../../adapters-and-accelerators/adapter-oracle-database/develop-oracle-database-applications-using-the-wcf-channel-model.md)。</span><span class="sxs-lookup"><span data-stu-id="70a97-118">See Develop Oracle Database Applications by Using the WCF Channel Model[enter link description here](../../adapters-and-accelerators/adapter-oracle-database/develop-oracle-database-applications-using-the-wcf-channel-model.md).</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="70a97-119">本節內容</span><span class="sxs-lookup"><span data-stu-id="70a97-119">In This Section</span></span>  
  
-   <span data-ttu-id="70a97-120">[配接器如何連接至 Siebel 系統？](https://msdn.microsoft.com/library/cc185212(v=bts.10).aspx)</span><span class="sxs-lookup"><span data-stu-id="70a97-120">[How Does the Adapter Connect to a Siebel System?](https://msdn.microsoft.com/library/cc185212(v=bts.10).aspx)</span></span>  
  
-   <span data-ttu-id="70a97-121">[配接器介面 Siebel 中繼資料的運作方式](https://msdn.microsoft.com/library/cc185267(v=bts.10).aspx)</span><span class="sxs-lookup"><span data-stu-id="70a97-121">[How Does the Adapter Surface Siebel Metadata?](https://msdn.microsoft.com/library/cc185267(v=bts.10).aspx)</span></span>  
  
-   <span data-ttu-id="70a97-122">[哪些作業可以是執行使用配接器？](https://msdn.microsoft.com/library/cc185219(v=bts.10).aspx)</span><span class="sxs-lookup"><span data-stu-id="70a97-122">[What Operations Can be Performed Using the Adapter?](https://msdn.microsoft.com/library/cc185219(v=bts.10).aspx)</span></span>  
  
-   <span data-ttu-id="70a97-123">[配接器所支援的其他功能](https://msdn.microsoft.com/library/cc185252(v=bts.10).aspx)</span><span class="sxs-lookup"><span data-stu-id="70a97-123">[Other Features Supported by the Adapter](https://msdn.microsoft.com/library/cc185252(v=bts.10).aspx)</span></span> 
  
## <a name="see-also"></a><span data-ttu-id="70a97-124">另請參閱</span><span class="sxs-lookup"><span data-stu-id="70a97-124">See Also</span></span>  
 [<span data-ttu-id="70a97-125">瞭解 BizTalk Adapter for Siebel eBusiness 應用程式</span><span class="sxs-lookup"><span data-stu-id="70a97-125">Understand BizTalk Adapter for Siebel eBusiness Applications</span></span>](../../adapters-and-accelerators/adapter-siebel/understand-biztalk-adapter-for-siebel-ebusiness-applications.md)