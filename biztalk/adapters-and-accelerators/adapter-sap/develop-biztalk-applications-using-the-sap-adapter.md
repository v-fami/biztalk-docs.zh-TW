---
title: "開發 BizTalk 應用程式使用 SAP 配接器 |Microsoft 文件"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- BizTalk applications, developing
- developing, BizTalk applications
ms.assetid: 4aa10897-a08e-4fc3-9c1f-40485d204273
caps.latest.revision: "13"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 75e70a52f12227b1bde3a43f9330c6fe373ac5a3
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/20/2017
---
# <a name="develop-biztalk-applications-using-the-sap-adapter"></a><span data-ttu-id="c2662-102">開發 BizTalk 應用程式使用 SAP 配接器</span><span class="sxs-lookup"><span data-stu-id="c2662-102">Develop BizTalk applications using the SAP adapter</span></span>
<span data-ttu-id="c2662-103">建立 BizTalk 專案中的開發 BizTalk 應用程式牽涉到[!INCLUDE[btsVStudioNoVersion](../../includes/btsvstudionoversion-md.md)]和使用[!INCLUDE[consumeadapterservlong](../../includes/consumeadapterservlong-md.md)]或[!INCLUDE[addadapterwiz](../../includes/addadapterwiz-md.md)]產生 XML 結構描述。</span><span class="sxs-lookup"><span data-stu-id="c2662-103">Developing BizTalk applications involves creating a BizTalk project in [!INCLUDE[btsVStudioNoVersion](../../includes/btsvstudionoversion-md.md)] and using the [!INCLUDE[consumeadapterservlong](../../includes/consumeadapterservlong-md.md)] or [!INCLUDE[addadapterwiz](../../includes/addadapterwiz-md.md)] to generate XML schema.</span></span> <span data-ttu-id="c2662-104">一旦您已經產生結構描述，您可以使用以內容為基礎的路由 (CBR)，或建立 BizTalk 協調流程傳送和接收符合產生結構描述的訊息。</span><span class="sxs-lookup"><span data-stu-id="c2662-104">Once you have generated the schema, you can either use Content-Based Routing (CBR) or create BizTalk orchestrations to send and receive messages that conform to the generated schema.</span></span>  
  
 <span data-ttu-id="c2662-105">CBR 可用在案例中傳送到 SAP 系統的訊息不需要任何大量的處理。</span><span class="sxs-lookup"><span data-stu-id="c2662-105">CBR can be used in scenarios where the messages being sent to the SAP system do not require any intensive processing.</span></span> <span data-ttu-id="c2662-106">比方說，如果您知道接收埠會接收僅特定類型的訊息，您可以加入篩選條件要比對篩選條件運算式至傳送埠將訊息路由傳送埠。</span><span class="sxs-lookup"><span data-stu-id="c2662-106">For example, if you know that the receive port will be receiving messages only of a certain type, you can add a filter to the send port to route the messages matching the filter expression to the send port.</span></span>  
  
 <span data-ttu-id="c2662-107">在 BizTalk 協調流程，建立傳送和接收埠以傳送和接收訊息的[!INCLUDE[wcfadapter_short](../../includes/wcfadapter-short-md.md)]，這會將訊息傳送至[!INCLUDE[btsBizTalkServerNoVersion](../../includes/btsbiztalkservernoversion-md.md)]。</span><span class="sxs-lookup"><span data-stu-id="c2662-107">In BizTalk orchestrations, you create send and receive ports to send and receive messages to and from the [!INCLUDE[wcfadapter_short](../../includes/wcfadapter-short-md.md)], which in turn sends the messages to [!INCLUDE[btsBizTalkServerNoVersion](../../includes/btsbiztalkservernoversion-md.md)].</span></span> <span data-ttu-id="c2662-108">本節提供使用 BizTalk 協調流程對 SAP 系統使用執行作業的相關資訊[!INCLUDE[adaptersap_short](../../includes/adaptersap-short-md.md)]。</span><span class="sxs-lookup"><span data-stu-id="c2662-108">This section provides information about using BizTalk orchestrations to perform operations on the SAP system using the [!INCLUDE[adaptersap_short](../../includes/adaptersap-short-md.md)].</span></span> <span data-ttu-id="c2662-109">[!INCLUDE[adaptersap_short](../../includes/adaptersap-short-md.md)]接著會採用[!INCLUDE[wcfadapter_short](../../includes/wcfadapter-short-md.md)]配接器，以互動的 WCF 繫結。</span><span class="sxs-lookup"><span data-stu-id="c2662-109">The [!INCLUDE[adaptersap_short](../../includes/adaptersap-short-md.md)] in turn uses the [!INCLUDE[wcfadapter_short](../../includes/wcfadapter-short-md.md)] adapter that can interact with a WCF binding.</span></span>  
  
> [!IMPORTANT]
>  <span data-ttu-id="c2662-110">若要使用[!INCLUDE[adaptersap_short](../../includes/adaptersap-short-md.md)]與 Microsoft [!INCLUDE[btsBizTalkServerNoVersion](../../includes/btsbiztalkservernoversion-md.md)]，您都必須設定**EnableBizTalkCompatibilityMode**內容繫結至**True**。</span><span class="sxs-lookup"><span data-stu-id="c2662-110">To use the [!INCLUDE[adaptersap_short](../../includes/adaptersap-short-md.md)] with Microsoft [!INCLUDE[btsBizTalkServerNoVersion](../../includes/btsbiztalkservernoversion-md.md)], you must always set the **EnableBizTalkCompatibilityMode** binding property to **True**.</span></span> <span data-ttu-id="c2662-111">如需如何設定繫結屬性的資訊，請參閱[設定 SAP 配接器的繫結屬性](../../adapters-and-accelerators/adapter-sap/configure-the-binding-properties-for-the-sap-adapter.md)。</span><span class="sxs-lookup"><span data-stu-id="c2662-111">For information about how to set binding properties, see [Configure the binding properties for the SAP adapter](../../adapters-and-accelerators/adapter-sap/configure-the-binding-properties-for-the-sap-adapter.md).</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="c2662-112">本節內容</span><span class="sxs-lookup"><span data-stu-id="c2662-112">In This Section</span></span>  
  
-   [<span data-ttu-id="c2662-113">若要建立的 SAP 應用程式的必要條件</span><span class="sxs-lookup"><span data-stu-id="c2662-113">Prerequisites to create SAP applications</span></span>](../../adapters-and-accelerators/adapter-sap/prerequisites-to-create-sap-applications.md)
  
-   [<span data-ttu-id="c2662-114">若要建立的 SAP 應用程式的建置組塊</span><span class="sxs-lookup"><span data-stu-id="c2662-114">Building blocks to create SAP applications</span></span>](../../adapters-and-accelerators/adapter-sap/building-blocks-to-create-sap-applications.md)
  
-   [<span data-ttu-id="c2662-115">叫用中使用 BizTalk Server 的 SAP Rfc</span><span class="sxs-lookup"><span data-stu-id="c2662-115">Invoke RFCs in SAP using BizTalk Server</span></span>](../../adapters-and-accelerators/adapter-sap/invoke-rfcs-in-sap-using-biztalk-server.md)  
  
-   [<span data-ttu-id="c2662-116">從 SAP 使用 BizTalk Server 接收輸入 RFC 呼叫</span><span class="sxs-lookup"><span data-stu-id="c2662-116">Receive Inbound RFC Calls from SAP using BizTalk Server</span></span>](../../adapters-and-accelerators/adapter-sap/receive-inbound-rfc-calls-from-sap-using-biztalk-server.md)  
  
-   [<span data-ttu-id="c2662-117">叫用中使用 BizTalk Server 的 SAP tRFCs</span><span class="sxs-lookup"><span data-stu-id="c2662-117">Invoke tRFCs in SAP using BizTalk Server</span></span>](../../adapters-and-accelerators/adapter-sap/invoke-trfcs-in-sap-using-biztalk-server.md)  
  
-   [<span data-ttu-id="c2662-118">從 SAP 使用 BizTalk Server 接收輸入的 tRFC 呼叫</span><span class="sxs-lookup"><span data-stu-id="c2662-118">Receive Inbound tRFC Calls from SAP using BizTalk Server</span></span>](../../adapters-and-accelerators/adapter-sap/receive-inbound-trfc-calls-from-sap-using-biztalk-server.md)  
  
-   [<span data-ttu-id="c2662-119">執行 SAP 使用 BizTalk Server 中的 BAPI 交易</span><span class="sxs-lookup"><span data-stu-id="c2662-119">Run BAPI Transactions in SAP using BizTalk Server</span></span>](../../adapters-and-accelerators/adapter-sap/run-bapi-transactions-in-sap-using-biztalk-server.md)  
  
-   [<span data-ttu-id="c2662-120">傳送 Idoc 至 SAP 使用 BizTalk Server</span><span class="sxs-lookup"><span data-stu-id="c2662-120">Send IDOCs to SAP using BizTalk Server</span></span>](../../adapters-and-accelerators/adapter-sap/send-idocs-to-sap-using-biztalk-server.md)  
  
-   [<span data-ttu-id="c2662-121">從 SAP 使用 BizTalk Server 接收 Idoc</span><span class="sxs-lookup"><span data-stu-id="c2662-121">Receive IDOCs from SAP using BizTalk Server</span></span>](../../adapters-and-accelerators/adapter-sap/receive-idocs-from-sap-using-biztalk-server.md)  
  
-   [<span data-ttu-id="c2662-122">從交易內容，使用 BizTalk Server 中的 SAP 接收 Idoc</span><span class="sxs-lookup"><span data-stu-id="c2662-122">Receive IDOCs from SAP in a Transactional Context using BizTalk Server</span></span>](../../adapters-and-accelerators/adapter-sap/receive-idocs-from-sap-in-a-transactional-context-using-biztalk-server.md)  
  
## <a name="see-also"></a><span data-ttu-id="c2662-123">另請參閱</span><span class="sxs-lookup"><span data-stu-id="c2662-123">See Also</span></span>  
[<span data-ttu-id="c2662-124">開發您的 SAP 應用程式</span><span class="sxs-lookup"><span data-stu-id="c2662-124">Develop your SAP applications</span></span>](../../adapters-and-accelerators/adapter-sap/develop-your-sap-applications.md)