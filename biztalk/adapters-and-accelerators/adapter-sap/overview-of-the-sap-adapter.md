---
title: SAP 配接器的概觀 |Microsoft 文件
ms.custom: ''
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- adapters, overview
ms.assetid: 2d078b13-d41f-476f-bfb4-82be4d35a769
caps.latest.revision: 8
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 3031bdf1317d96f64f1ea247c6f8cbf83e1688c7
ms.sourcegitcommit: 5abd0ed3f9e4858ffaaec5481bfa8878595e95f7
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/28/2017
ms.locfileid: "25963028"
---
# <a name="overview-of-the-sap-adapter"></a><span data-ttu-id="25a25-102">SAP 配接器的概觀</span><span class="sxs-lookup"><span data-stu-id="25a25-102">Overview of the SAP adapter</span></span>
<span data-ttu-id="25a25-103">[!INCLUDE[adaptersap](../../includes/adaptersap-md.md)]公開為 WCF 服務的 SAP 系統。</span><span class="sxs-lookup"><span data-stu-id="25a25-103">The [!INCLUDE[adaptersap](../../includes/adaptersap-md.md)] exposes the SAP system as a WCF service.</span></span> <span data-ttu-id="25a25-104">配接器用戶端可以交換 SOAP 訊息的配接器，以執行 SAP 系統上的作業。</span><span class="sxs-lookup"><span data-stu-id="25a25-104">Adapter clients can perform operations on the SAP system by exchanging SOAP messages with the adapter.</span></span> <span data-ttu-id="25a25-105">配接器會取用 WCF 訊息，並使適當地呼叫 SAP 系統執行的作業。</span><span class="sxs-lookup"><span data-stu-id="25a25-105">The adapter consumes the WCF message and makes appropriate calls to the SAP system to perform the operation.</span></span> <span data-ttu-id="25a25-106">配接器傳回從 SAP 系統的回應傳回給用戶端的 SOAP 訊息格式。</span><span class="sxs-lookup"><span data-stu-id="25a25-106">The adapter returns the response from the SAP system back to the client in the form of SOAP messages.</span></span>  
  
 <span data-ttu-id="25a25-107">[!INCLUDE[adaptersap_short](../../includes/adaptersap-short-md.md)]表面的中繼資料的 SAP 成品 (RFC，BAPI IDOC) 描述結構的 SOAP 訊息的 WSDL 格式。</span><span class="sxs-lookup"><span data-stu-id="25a25-107">The [!INCLUDE[adaptersap_short](../../includes/adaptersap-short-md.md)] surfaces metadata of SAP artifacts (RFC, BAPI, IDOC) that describes the structure of a SOAP message in the form of WSDL.</span></span> <span data-ttu-id="25a25-108">[!INCLUDE[adaptersap_short](../../includes/adaptersap-short-md.md)]使用[!INCLUDE[addadapterservreflong](../../includes/addadapterservreflong-md.md)]， [!INCLUDE[addadapterwiz](../../includes/addadapterwiz-md.md)]，和[!INCLUDE[consumeadapterservlong](../../includes/consumeadapterservlong-md.md)]讓配接器用戶端擷取作業的中繼資料，並產生可使用的程式設計成品程式設計方案中。</span><span class="sxs-lookup"><span data-stu-id="25a25-108">The [!INCLUDE[adaptersap_short](../../includes/adaptersap-short-md.md)] uses [!INCLUDE[addadapterservreflong](../../includes/addadapterservreflong-md.md)], [!INCLUDE[addadapterwiz](../../includes/addadapterwiz-md.md)], and [!INCLUDE[consumeadapterservlong](../../includes/consumeadapterservlong-md.md)] to enable adapter clients to retrieve metadata for operations and generates programming artifacts that can be used in your programming solution.</span></span> <span data-ttu-id="25a25-109">如需有關[!INCLUDE[addadapterservreflong](../../includes/addadapterservreflong-md.md)]， [!INCLUDE[addadapterwiz](../../includes/addadapterwiz-md.md)]，和[!INCLUDE[consumeadapterservlong](../../includes/consumeadapterservlong-md.md)]，請參閱[連接到 Visual Studio 中的 SAP 系統](../../adapters-and-accelerators/adapter-sap/connect-to-the-sap-system-in-visual-studio.md)。</span><span class="sxs-lookup"><span data-stu-id="25a25-109">For more information about [!INCLUDE[addadapterservreflong](../../includes/addadapterservreflong-md.md)], [!INCLUDE[addadapterwiz](../../includes/addadapterwiz-md.md)], and [!INCLUDE[consumeadapterservlong](../../includes/consumeadapterservlong-md.md)], see [Connect to the SAP System in Visual Studio](../../adapters-and-accelerators/adapter-sap/connect-to-the-sap-system-in-visual-studio.md).</span></span>  
  
 <span data-ttu-id="25a25-110">[!INCLUDE[adaptersap_short](../../includes/adaptersap-short-md.md)]使用 Unicode RFC 程式庫，librfc32u.dll，與 SAP 系統，除了使用其他支援的 Dll 進行通訊。</span><span class="sxs-lookup"><span data-stu-id="25a25-110">The [!INCLUDE[adaptersap_short](../../includes/adaptersap-short-md.md)] uses the Unicode RFC library, librfc32u.dll, to communicate with the SAP system, in addition to using other supporting DLLs.</span></span> <span data-ttu-id="25a25-111">如需配接器需要的 SAP Dll 的完整清單，請參閱[!INCLUDE[adapterpacknoversion](../../includes/adapterpacknoversion-md.md)]安裝指南。</span><span class="sxs-lookup"><span data-stu-id="25a25-111">For a complete list of SAP DLLs that the adapter requires, see the [!INCLUDE[adapterpacknoversion](../../includes/adapterpacknoversion-md.md)] installation guide.</span></span> <span data-ttu-id="25a25-112">在一般安裝安裝指南 》\<安裝磁碟機：\>\Program Files\\[!INCLUDE[adapterpacknoversion](../../includes/adapterpacknoversion-md.md)]\Documents。</span><span class="sxs-lookup"><span data-stu-id="25a25-112">The installation guide is typically installed at \<installation drive:\>\Program Files\\[!INCLUDE[adapterpacknoversion](../../includes/adapterpacknoversion-md.md)]\Documents.</span></span> <span data-ttu-id="25a25-113">您可以使用[!INCLUDE[adaptersap_short](../../includes/adaptersap-short-md.md)]與 SAP 系統通訊，以下列方式：</span><span class="sxs-lookup"><span data-stu-id="25a25-113">You can use the [!INCLUDE[adaptersap_short](../../includes/adaptersap-short-md.md)] to communicate with the SAP system in the following ways:</span></span>  
  
-   <span data-ttu-id="25a25-114">開發 BizTalk 應用程式。</span><span class="sxs-lookup"><span data-stu-id="25a25-114">By developing BizTalk applications.</span></span> <span data-ttu-id="25a25-115">請參閱[開發 BizTalk Server 應用程式](../../core/developing-biztalk-server-applications.md)如需詳細資訊。</span><span class="sxs-lookup"><span data-stu-id="25a25-115">See [Developing BizTalk Server Applications](../../core/developing-biztalk-server-applications.md) for more information.</span></span>  
  
-   <span data-ttu-id="25a25-116">使用[!INCLUDE[firstref_btsWinCommFoundation](../../includes/firstref-btswincommfoundation-md.md)]服務模型。</span><span class="sxs-lookup"><span data-stu-id="25a25-116">By using the [!INCLUDE[firstref_btsWinCommFoundation](../../includes/firstref-btswincommfoundation-md.md)] service model.</span></span> <span data-ttu-id="25a25-117">請參閱[開發 SAP 應用程式使用 WCF 服務模型](../../adapters-and-accelerators/adapter-sap/develop-sap-applications-using-the-wcf-service-model.md)。</span><span class="sxs-lookup"><span data-stu-id="25a25-117">See [Develop SAP applications using the WCF Service Model](../../adapters-and-accelerators/adapter-sap/develop-sap-applications-using-the-wcf-service-model.md).</span></span>
  
-   <span data-ttu-id="25a25-118">使用 WCF 通道模型。</span><span class="sxs-lookup"><span data-stu-id="25a25-118">By using the WCF channel model.</span></span> <span data-ttu-id="25a25-119">請參閱[開發 SAP 應用程式使用 WCF 通道模型](../../adapters-and-accelerators/adapter-sap/develop-sap-applications-using-the-wcf-channel-model.md)。</span><span class="sxs-lookup"><span data-stu-id="25a25-119">See [Develop SAP applications using the WCF Channel Model](../../adapters-and-accelerators/adapter-sap/develop-sap-applications-using-the-wcf-channel-model.md).</span></span>
  
## <a name="in-this-section"></a><span data-ttu-id="25a25-120">本節內容</span><span class="sxs-lookup"><span data-stu-id="25a25-120">In This Section</span></span>  
  
-   [<span data-ttu-id="25a25-121">配接器如何連接到 SAP 系統？</span><span class="sxs-lookup"><span data-stu-id="25a25-121">How Does the Adapter Connect to an SAP System?</span></span>](https://msdn.microsoft.com/library/cc185540.aspx)  
  
-   [<span data-ttu-id="25a25-122">配接器介面的 SAP 中繼資料的運作方式</span><span class="sxs-lookup"><span data-stu-id="25a25-122">How Does the Adapter Surface SAP Metadata?</span></span>](https://msdn.microsoft.com/library/dd788039.aspx)  
  
-   [<span data-ttu-id="25a25-123">哪些作業可以是執行使用配接器？</span><span class="sxs-lookup"><span data-stu-id="25a25-123">What Operations Can be Performed Using the Adapter?</span></span>](https://msdn.microsoft.com/library/dd788159.aspx)  
  
-   [<span data-ttu-id="25a25-124">配接器所支援的其他功能</span><span class="sxs-lookup"><span data-stu-id="25a25-124">Other Features Supported by the Adapter</span></span>](https://msdn.microsoft.com/library/dd788022.aspx)  
  
## <a name="see-also"></a><span data-ttu-id="25a25-125">請參閱</span><span class="sxs-lookup"><span data-stu-id="25a25-125">See Also</span></span>  
 [<span data-ttu-id="25a25-126">了解 BizTalk Adapter for mySAP Business Suite</span><span class="sxs-lookup"><span data-stu-id="25a25-126">Understand BizTalk Adapter for mySAP Business Suite</span></span>](../../adapters-and-accelerators/adapter-sap/understand-biztalk-adapter-for-mysap-business-suite.md)