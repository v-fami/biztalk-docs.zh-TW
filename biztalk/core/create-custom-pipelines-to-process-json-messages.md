---
title: "建立自訂管線來處理 JSON 訊息 |Microsoft 文件"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: b04faad1-b14b-4146-82c7-88a38d2a46a5
caps.latest.revision: "3"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 86c85f1a45dceb812fc805a66701653642d0ccb6
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/20/2017
---
# <a name="create-custom-pipelines-to-process-json-messages"></a><span data-ttu-id="01108-102">建立自訂管線來處理 JSON 訊息</span><span class="sxs-lookup"><span data-stu-id="01108-102">Create custom pipelines to process JSON messages</span></span>
> [!NOTE]
>  <span data-ttu-id="01108-103">本教學課程僅適用於 [!INCLUDE[prague](../includes/prague-md.md)]。</span><span class="sxs-lookup"><span data-stu-id="01108-103">This tutorial applies to [!INCLUDE[prague](../includes/prague-md.md)] only.</span></span>  
  
 [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]<span data-ttu-id="01108-104">提供可以用來處理 JSON 訊息內的管線元件[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]應用程式。</span><span class="sxs-lookup"><span data-stu-id="01108-104"> provides pipeline components that can be used to process JSON messages within a [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] application.</span></span> <span data-ttu-id="01108-105">在此步驟中，使用這些管線元件來建立可以在設定時使用的自訂管線[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]應用程式。</span><span class="sxs-lookup"><span data-stu-id="01108-105">In this step, we use those pipeline components to create custom pipelines that can be used when configuring a [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] application.</span></span>  
  
## <a name="create-a-custom-receive-pipeline"></a><span data-ttu-id="01108-106">建立自訂接收管線</span><span class="sxs-lookup"><span data-stu-id="01108-106">Create a custom receive pipeline</span></span>  
  
1.  <span data-ttu-id="01108-107">在[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]應用程式中的，從 [方案總管] 中，以滑鼠右鍵按一下專案，並指向**新增** > **新項目** > **接收管線**.</span><span class="sxs-lookup"><span data-stu-id="01108-107">In the [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] application, from the Solution Explorer, right-click the project, and point to **Add** > **New Item** > **Receive Pipeline**.</span></span> <span data-ttu-id="01108-108">提供的管線名稱`JSONToXmlReceivePipeline.btp`，然後按一下 **新增**。</span><span class="sxs-lookup"><span data-stu-id="01108-108">Provide the pipeline name as `JSONToXmlReceivePipeline.btp`, and then click **Add**.</span></span>  
  
2.  <span data-ttu-id="01108-109">內**解碼**階段新增**JSON 解碼器**。</span><span class="sxs-lookup"><span data-stu-id="01108-109">Within the **Decode** stage add the new **JSON decoder**.</span></span> <span data-ttu-id="01108-110">中的其他階段和其他螢幕擷取畫面所示的管線元件，並儲存變更。</span><span class="sxs-lookup"><span data-stu-id="01108-110">In the other stages and other pipeline components as shown in the screenshot, and save changes.</span></span>  
  
     <span data-ttu-id="01108-111">![自訂接收管線](../core/media/btsjson-receivepipeline.png "BTSJSON_ReceivePipeline")</span><span class="sxs-lookup"><span data-stu-id="01108-111">![Custom receive pipeline](../core/media/btsjson-receivepipeline.png "BTSJSON_ReceivePipeline")</span></span>  
  
## <a name="create-a-custom-send-pipeline"></a><span data-ttu-id="01108-112">建立自訂傳送管線</span><span class="sxs-lookup"><span data-stu-id="01108-112">Create a custom send pipeline</span></span>  
  
1.  <span data-ttu-id="01108-113">在[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]應用程式中的，從 [方案總管] 中，以滑鼠右鍵按一下專案，並指向**新增** > **新項目** > **傳送管線**.</span><span class="sxs-lookup"><span data-stu-id="01108-113">In the [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] application, from the Solution Explorer, right-click the project, and point to **Add** > **New Item** > **Send Pipeline**.</span></span> <span data-ttu-id="01108-114">提供的管線名稱`XmlToJSONSendPipeline.btp`，然後按一下 **新增**。</span><span class="sxs-lookup"><span data-stu-id="01108-114">Provide the pipeline name as `XmlToJSONSendPipeline.btp`, and then click **Add**.</span></span>  
  
2.  <span data-ttu-id="01108-115">內**編碼**階段新增**JSON 編碼器**。</span><span class="sxs-lookup"><span data-stu-id="01108-115">Within the **Encode** stage add the new **JSON encoder**.</span></span> <span data-ttu-id="01108-116">中的其他階段和其他螢幕擷取畫面所示的管線元件，並儲存變更。</span><span class="sxs-lookup"><span data-stu-id="01108-116">In the other stages and other pipeline components as shown in the screenshot, and save changes.</span></span>  
  
     <span data-ttu-id="01108-117">![自訂傳送管線](../core/media/btsjson-sendpipeline.png "BTSJSON_SendPipeline")</span><span class="sxs-lookup"><span data-stu-id="01108-117">![Custom send pipeline](../core/media/btsjson-sendpipeline.png "BTSJSON_SendPipeline")</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="01108-118">另請參閱</span><span class="sxs-lookup"><span data-stu-id="01108-118">See Also</span></span>  
 [<span data-ttu-id="01108-119">使用 BizTalk Server 處理 JSON 訊息</span><span class="sxs-lookup"><span data-stu-id="01108-119">Processing JSON messages using BizTalk Server</span></span>](../core/processing-json-messages-using-biztalk-server.md)