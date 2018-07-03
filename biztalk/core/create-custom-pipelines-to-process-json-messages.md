---
title: 建立自訂管線來處理 JSON 訊息 |Microsoft Docs
ms.custom: ''
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: b04faad1-b14b-4146-82c7-88a38d2a46a5
caps.latest.revision: 3
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: e28f825b1f26f3c080a02fd9a2e2bf8960a816fd
ms.sourcegitcommit: 266308ec5c6a9d8d80ff298ee6051b4843c5d626
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/27/2018
ms.locfileid: "37005991"
---
# <a name="create-custom-pipelines-to-process-json-messages"></a><span data-ttu-id="4733a-102">建立自訂管線來處理 JSON 訊息</span><span class="sxs-lookup"><span data-stu-id="4733a-102">Create custom pipelines to process JSON messages</span></span>
> [!NOTE]
>  <span data-ttu-id="4733a-103">本教學課程僅適用於 BizTalk Server。</span><span class="sxs-lookup"><span data-stu-id="4733a-103">This tutorial applies to BizTalk Server only.</span></span>  
  
 [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]<span data-ttu-id="4733a-104"> 提供可用來處理 JSON 訊息內的管線元件[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]應用程式。</span><span class="sxs-lookup"><span data-stu-id="4733a-104"> provides pipeline components that can be used to process JSON messages within a [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] application.</span></span> <span data-ttu-id="4733a-105">在此步驟中，我們可以使用這些管線元件建立自訂的管線，可以在設定時使用[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]應用程式。</span><span class="sxs-lookup"><span data-stu-id="4733a-105">In this step, we use those pipeline components to create custom pipelines that can be used when configuring a [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] application.</span></span>  
  
## <a name="create-a-custom-receive-pipeline"></a><span data-ttu-id="4733a-106">建立自訂接收管線</span><span class="sxs-lookup"><span data-stu-id="4733a-106">Create a custom receive pipeline</span></span>  
  
1. <span data-ttu-id="4733a-107">在 [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]應用程式中的，從 [方案總管] 中，以滑鼠右鍵按一下專案，並指向**新增** > **新項目** > **接收管線**.</span><span class="sxs-lookup"><span data-stu-id="4733a-107">In the [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] application, from the Solution Explorer, right-click the project, and point to **Add** > **New Item** > **Receive Pipeline**.</span></span> <span data-ttu-id="4733a-108">提供的管線名稱`JSONToXmlReceivePipeline.btp`，然後按一下**新增**。</span><span class="sxs-lookup"><span data-stu-id="4733a-108">Provide the pipeline name as `JSONToXmlReceivePipeline.btp`, and then click **Add**.</span></span>  
  
2. <span data-ttu-id="4733a-109">內**解碼**階段新增**JSON 解碼器**。</span><span class="sxs-lookup"><span data-stu-id="4733a-109">Within the **Decode** stage add the new **JSON decoder**.</span></span> <span data-ttu-id="4733a-110">中的其他階段和其他螢幕擷取畫面所示的管線元件，並儲存變更。</span><span class="sxs-lookup"><span data-stu-id="4733a-110">In the other stages and other pipeline components as shown in the screenshot, and save changes.</span></span>  
  
    <span data-ttu-id="4733a-111">![自訂接收管線](../core/media/btsjson-receivepipeline.png "BTSJSON_ReceivePipeline")</span><span class="sxs-lookup"><span data-stu-id="4733a-111">![Custom receive pipeline](../core/media/btsjson-receivepipeline.png "BTSJSON_ReceivePipeline")</span></span>  
  
## <a name="create-a-custom-send-pipeline"></a><span data-ttu-id="4733a-112">建立自訂傳送管線</span><span class="sxs-lookup"><span data-stu-id="4733a-112">Create a custom send pipeline</span></span>  
  
1. <span data-ttu-id="4733a-113">在 [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]應用程式中的，從 [方案總管] 中，以滑鼠右鍵按一下專案，並指向**新增** > **新項目** > **傳送管線**.</span><span class="sxs-lookup"><span data-stu-id="4733a-113">In the [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] application, from the Solution Explorer, right-click the project, and point to **Add** > **New Item** > **Send Pipeline**.</span></span> <span data-ttu-id="4733a-114">提供的管線名稱`XmlToJSONSendPipeline.btp`，然後按一下**新增**。</span><span class="sxs-lookup"><span data-stu-id="4733a-114">Provide the pipeline name as `XmlToJSONSendPipeline.btp`, and then click **Add**.</span></span>  
  
2. <span data-ttu-id="4733a-115">內**編碼**階段新增**JSON 編碼器**。</span><span class="sxs-lookup"><span data-stu-id="4733a-115">Within the **Encode** stage add the new **JSON encoder**.</span></span> <span data-ttu-id="4733a-116">中的其他階段和其他螢幕擷取畫面所示的管線元件，並儲存變更。</span><span class="sxs-lookup"><span data-stu-id="4733a-116">In the other stages and other pipeline components as shown in the screenshot, and save changes.</span></span>  
  
    <span data-ttu-id="4733a-117">![自訂傳送管線](../core/media/btsjson-sendpipeline.png "BTSJSON_SendPipeline")</span><span class="sxs-lookup"><span data-stu-id="4733a-117">![Custom send pipeline](../core/media/btsjson-sendpipeline.png "BTSJSON_SendPipeline")</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="4733a-118">另請參閱</span><span class="sxs-lookup"><span data-stu-id="4733a-118">See Also</span></span>  
 [<span data-ttu-id="4733a-119">使用 BizTalk Server 處理 JSON 訊息</span><span class="sxs-lookup"><span data-stu-id="4733a-119">Processing JSON messages using BizTalk Server</span></span>](../core/processing-json-messages-using-biztalk-server.md)