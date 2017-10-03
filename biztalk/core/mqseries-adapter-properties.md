---
title: "MQSeries 配接器屬性 |Microsoft 文件"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- MQXQH_RemoteQName property [MQSeries adapters]
- MQMD_ReplyToQ property [MQSeries adapters]
- configuring [MQSeries adapters], properties
- MQXQH_MsgDesc_ReplyToQMgr property [MQSeries adapters]
- UserHttpHeaders property [MQSeries adapters]
- MQMD_CorrelId property [MQSeries adapters]
- MQXQH_MsgDesc_MsgId property [MQSeries adapters]
- MQXQH_MsgDesc_ReplyToQ property [MQSeries adapters]
- SubmissionHandle property [MQSeries adapters]
- BizTalk_CorrelationID property [MQSeries adapters]
- MQMD_ReplyToQMgr property [MQSeries adapters]
- EnableChunkedEncoding property [MQSeries adapters]
- MQSeries adapters, properties
- MQXQH_MsgDesc_CorrelId property [MQSeries adapters]
- MQXQH_RemoteQMgrName property [MQSeries adapters]
- MQMD_MsgId property [MQSeries adapters]
ms.assetid: c3cfbc8c-4c9b-431e-b0b6-4c065a69ce6b
caps.latest.revision: "11"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: fae8cc1ed67f077b6ae12945da10c58cf0f147da
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/20/2017
---
# <a name="mqseries-adapter-properties"></a><span data-ttu-id="e1b33-102">MQSeries 配接器屬性</span><span class="sxs-lookup"><span data-stu-id="e1b33-102">MQSeries Adapter Properties</span></span>
<span data-ttu-id="e1b33-103">若要從 BizTalk 協調流程存取 MQSeries 標頭屬性，您必須將 MQSeries.dll 組件的參考新增到您的專案。</span><span class="sxs-lookup"><span data-stu-id="e1b33-103">To access MQSeries header properties from a BizTalk orchestration, you must add a reference to the MQSeries.dll assembly to your project.</span></span> <span data-ttu-id="e1b33-104">這個組件位於您安裝 MQSeries 配接器的位置，例如 [!INCLUDE[btsBiztalkServerPath](../includes/btsbiztalkserverpath-md.md)]。</span><span class="sxs-lookup"><span data-stu-id="e1b33-104">This assembly is located where you installed the MQSeries adapter, for example, [!INCLUDE[btsBiztalkServerPath](../includes/btsbiztalkserverpath-md.md)].</span></span>  
  
 <span data-ttu-id="e1b33-105">您參考 MQSeries 屬性結構描述之後，其他內容屬性可用於各種 BizTalk Server 開發工具 (例如，**訊息指派**圖形在協調流程設計師 」 中的)。</span><span class="sxs-lookup"><span data-stu-id="e1b33-105">After you reference the MQSeries property schema, additional context properties are available to various BizTalk Server development tools (for example, the **Message Assignment** shape in Orchestration Designer).</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="e1b33-106">當您處理 MQSeries 標頭屬性時，請確定您遵照＜IBM WebSphere MQ＞文件中的指導方針。</span><span class="sxs-lookup"><span data-stu-id="e1b33-106">Make sure that you follow the guidelines in the IBM WebSphere MQ documentation when you work with MQSeries header properties.</span></span>  
  
 <span data-ttu-id="e1b33-107">配接器會自動升級部分 MQSeries 屬性。</span><span class="sxs-lookup"><span data-stu-id="e1b33-107">The adapter automatically promotes some MQSeries properties.</span></span> <span data-ttu-id="e1b33-108">您的應用程式和自訂元件必須避免降級這些屬性。</span><span class="sxs-lookup"><span data-stu-id="e1b33-108">Your applications and custom components must avoid demoting these properties.</span></span> <span data-ttu-id="e1b33-109">您可以使用自訂管線元件升級的其他屬性。</span><span class="sxs-lookup"><span data-stu-id="e1b33-109">You can promote additional properties by using custom pipeline components.</span></span> <span data-ttu-id="e1b33-110">自動升級的屬性如下：</span><span class="sxs-lookup"><span data-stu-id="e1b33-110">The automatically promoted properties are as follows:</span></span>  
  
-   <span data-ttu-id="e1b33-111">**BizTalk_CorrelationID**</span><span class="sxs-lookup"><span data-stu-id="e1b33-111">**BizTalk_CorrelationID**</span></span>  
  
-   <span data-ttu-id="e1b33-112">**MQMD_CorrelId**</span><span class="sxs-lookup"><span data-stu-id="e1b33-112">**MQMD_CorrelId**</span></span>  
  
-   <span data-ttu-id="e1b33-113">**MQMD_MsgId**</span><span class="sxs-lookup"><span data-stu-id="e1b33-113">**MQMD_MsgId**</span></span>  
  
-   <span data-ttu-id="e1b33-114">**MQMD_ReplyToQ**</span><span class="sxs-lookup"><span data-stu-id="e1b33-114">**MQMD_ReplyToQ**</span></span>  
  
-   <span data-ttu-id="e1b33-115">**MQMD_ReplyToQMgr**</span><span class="sxs-lookup"><span data-stu-id="e1b33-115">**MQMD_ReplyToQMgr**</span></span>  
  
-   <span data-ttu-id="e1b33-116">**MQXQH_RemoteQMgrName**</span><span class="sxs-lookup"><span data-stu-id="e1b33-116">**MQXQH_RemoteQMgrName**</span></span>  
  
-   <span data-ttu-id="e1b33-117">**MQXQH_RemoteQName**</span><span class="sxs-lookup"><span data-stu-id="e1b33-117">**MQXQH_RemoteQName**</span></span>  
  
-   <span data-ttu-id="e1b33-118">**MQXQH_MsgDesc_CorrelId**</span><span class="sxs-lookup"><span data-stu-id="e1b33-118">**MQXQH_MsgDesc_CorrelId**</span></span>  
  
-   <span data-ttu-id="e1b33-119">**MQXQH_MsgDesc_MsgId**</span><span class="sxs-lookup"><span data-stu-id="e1b33-119">**MQXQH_MsgDesc_MsgId**</span></span>  
  
-   <span data-ttu-id="e1b33-120">**MQXQH_MsgDesc_ReplyToQ**</span><span class="sxs-lookup"><span data-stu-id="e1b33-120">**MQXQH_MsgDesc_ReplyToQ**</span></span>  
  
-   <span data-ttu-id="e1b33-121">**MQXQH_MsgDesc_ReplyToQMgr**</span><span class="sxs-lookup"><span data-stu-id="e1b33-121">**MQXQH_MsgDesc_ReplyToQMgr**</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="e1b33-122">本節內容</span><span class="sxs-lookup"><span data-stu-id="e1b33-122">In This Section</span></span>  
  
-   [<span data-ttu-id="e1b33-123">屬性的資料類型轉換</span><span class="sxs-lookup"><span data-stu-id="e1b33-123">Data Type Conversion of Properties</span></span>](../core/data-type-conversion-of-properties.md)  
  
-   [<span data-ttu-id="e1b33-124">與 BizTalk Server 相關的屬性</span><span class="sxs-lookup"><span data-stu-id="e1b33-124">Properties Related to BizTalk Server</span></span>](../core/properties-related-to-biztalk-server.md)  
  
-   [<span data-ttu-id="e1b33-125">MQSeries 內容屬性</span><span class="sxs-lookup"><span data-stu-id="e1b33-125">MQSeries Context Properties</span></span>](../core/mqseries-context-properties.md)  
  
## <a name="see-also"></a><span data-ttu-id="e1b33-126">另請參閱</span><span class="sxs-lookup"><span data-stu-id="e1b33-126">See Also</span></span>  
 [<span data-ttu-id="e1b33-127">設定 MQSeries 配接器</span><span class="sxs-lookup"><span data-stu-id="e1b33-127">Configuring the MQSeries Adapter</span></span>](../core/configuring-the-mqseries-adapter.md)