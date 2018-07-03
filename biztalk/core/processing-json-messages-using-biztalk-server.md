---
title: 處理 JSON 訊息使用 BizTalk Server |Microsoft Docs
ms.custom: ''
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: c6db1421-9478-477c-8645-09eefba06246
caps.latest.revision: 6
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: db57847964c7e3da452675945b7d4557ae7cbc85
ms.sourcegitcommit: 266308ec5c6a9d8d80ff298ee6051b4843c5d626
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/27/2018
ms.locfileid: "36986343"
---
# <a name="processing-json-messages-using-biztalk-server"></a><span data-ttu-id="b3bbc-102">使用 BizTalk Server 處理 JSON 訊息</span><span class="sxs-lookup"><span data-stu-id="b3bbc-102">Processing JSON messages using BizTalk Server</span></span>
> [!NOTE]
>  <span data-ttu-id="b3bbc-103">本教學課程僅適用於 BizTalk Server。</span><span class="sxs-lookup"><span data-stu-id="b3bbc-103">This tutorial applies to BizTalk Server only.</span></span>  
  
 <span data-ttu-id="b3bbc-104">本教學課程示範如何處理使用 JSON 訊息[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]。</span><span class="sxs-lookup"><span data-stu-id="b3bbc-104">This tutorial demonstrates how to process JSON messages using [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)].</span></span> <span data-ttu-id="b3bbc-105">本教學課程會使用現在可以搭配 BizTalk Server 使用的自訂管線元件。</span><span class="sxs-lookup"><span data-stu-id="b3bbc-105">The tutorial uses custom pipeline components, now available with BizTalk Server.</span></span> <span data-ttu-id="b3bbc-106">這些管線元件會將 JSON 訊息轉換成 XML (接收到訊息時[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]協調流程，並將訊息從 XML 轉換為 JSON，同時送出訊息。</span><span class="sxs-lookup"><span data-stu-id="b3bbc-106">These pipeline components convert the JSON message to XML (while receiving the message into [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] orchestration, and converts the message from XML to JSON while sending the message out.</span></span>  
  
## <a name="what-does-this-tutorial-do"></a><span data-ttu-id="b3bbc-107">此教學課程，請執行有哪些功能？</span><span class="sxs-lookup"><span data-stu-id="b3bbc-107">What does this tutorial do?</span></span>  
 <span data-ttu-id="b3bbc-108">為了示範 JSON 處理，我們建立[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]會執行下列命令，以指定的順序：</span><span class="sxs-lookup"><span data-stu-id="b3bbc-108">To demonstrate JSON processing, we create a [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] that does the following, in the given order:</span></span>  
  
1. <span data-ttu-id="b3bbc-109">接收 JSON 訂單，並在接收管線中，使用 JSON 解碼器元件來轉換 XML 訊息的 JSON 訊息。</span><span class="sxs-lookup"><span data-stu-id="b3bbc-109">Receives a JSON purchase order and in the receive pipeline, uses a JSON decoder component to transform the JSON message to XML message.</span></span>  
  
2. <span data-ttu-id="b3bbc-110">XML 訂單轉換為使用對應的 XML 發票。</span><span class="sxs-lookup"><span data-stu-id="b3bbc-110">Transforms the XML purchase order into an XML invoice using a map.</span></span>  
  
3. <span data-ttu-id="b3bbc-111">在傳送管線中，將 XML 轉換的 JSON 編碼器發票到 JSON 使用發票，並傳送出去。</span><span class="sxs-lookup"><span data-stu-id="b3bbc-111">In the send pipeline, uses a JSON encoder to transform the XML invoice into a JSON invoice and sends it out.</span></span>  
  
   <span data-ttu-id="b3bbc-112">![處理 JSON 訊息，BizTalk Server 中的](../core/media/btsjson-flow.png "BTSJSON_Flow")</span><span class="sxs-lookup"><span data-stu-id="b3bbc-112">![Processing JSON messages in BizTalk Server](../core/media/btsjson-flow.png "BTSJSON_Flow")</span></span>  
  
## <a name="how-to-use-this-tutorial"></a><span data-ttu-id="b3bbc-113">如何使用本教學課程？</span><span class="sxs-lookup"><span data-stu-id="b3bbc-113">How to use this tutorial?</span></span>  
 <span data-ttu-id="b3bbc-114">本教學課程中建置範例 (**BTSJSO**)，您可以從下載[MSDN Code Gallery](http://go.microsoft.com/fwlink/?LinkId=403197)。</span><span class="sxs-lookup"><span data-stu-id="b3bbc-114">This tutorial is built around a sample (**BTSJSON**) that can be downloaded from the [MSDN Code Gallery](http://go.microsoft.com/fwlink/?LinkId=403197).</span></span> <span data-ttu-id="b3bbc-115">您可以使用範例，並進行此教學課程，以了解如何建置範例。</span><span class="sxs-lookup"><span data-stu-id="b3bbc-115">You could use the sample and go through this tutorial to understand how the sample was built.</span></span> <span data-ttu-id="b3bbc-116">或者，您可以使用本教學課程來建立您自己的解決方案由下而上。</span><span class="sxs-lookup"><span data-stu-id="b3bbc-116">Or, you could use this tutorial to create your own solution ground-up.</span></span> <span data-ttu-id="b3bbc-117">本教學課程的目標傾向第二種方法，讓您了解如何建置此解決方案。</span><span class="sxs-lookup"><span data-stu-id="b3bbc-117">This tutorial is targeted towards the second approach so that you understand how this solution was built.</span></span> <span data-ttu-id="b3bbc-118">此外，盡量，本教學課程與範例一致，並使用相同名稱的成品 （例如，結構描述、 轉換） 範例中使用。</span><span class="sxs-lookup"><span data-stu-id="b3bbc-118">Also, as much as possible, the tutorial is consistent with the sample and uses the same names for artifacts (for example, schemas, transforms) as used in the sample.</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="b3bbc-119">本節內容</span><span class="sxs-lookup"><span data-stu-id="b3bbc-119">In This Section</span></span>  
  
-   [<span data-ttu-id="b3bbc-120">產生 JSON 訊息的 XSD 結構描述</span><span class="sxs-lookup"><span data-stu-id="b3bbc-120">Generate an XSD schema for JSON message</span></span>](../core/generate-an-xsd-schema-for-json-message.md)  
  
-   [<span data-ttu-id="b3bbc-121">建立自訂管線來處理 JSON 訊息</span><span class="sxs-lookup"><span data-stu-id="b3bbc-121">Create custom pipelines to process JSON messages</span></span>](../core/create-custom-pipelines-to-process-json-messages.md)  
  
-   [<span data-ttu-id="b3bbc-122">建立 BizTalk Server 協調流程</span><span class="sxs-lookup"><span data-stu-id="b3bbc-122">Create a BizTalk Server orchestration</span></span>](../core/create-a-biztalk-server-orchestration.md)  
  
-   [<span data-ttu-id="b3bbc-123">部署和測試應用程式</span><span class="sxs-lookup"><span data-stu-id="b3bbc-123">Deploy and test the application</span></span>](../core/deploy-and-test-the-application.md)  
  
## <a name="see-also"></a><span data-ttu-id="b3bbc-124">另請參閱</span><span class="sxs-lookup"><span data-stu-id="b3bbc-124">See Also</span></span>  
 [<span data-ttu-id="b3bbc-125">BizTalk Server 教學課程</span><span class="sxs-lookup"><span data-stu-id="b3bbc-125">BizTalk Server Tutorials</span></span>](../core/biztalk-server-tutorials.md)