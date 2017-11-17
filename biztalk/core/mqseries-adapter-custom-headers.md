---
title: "MQSeries 配接器自訂標頭 |Microsoft 文件"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords: MQSeries adapters, custom headers
ms.assetid: b0e18203-a33f-4d50-8483-396699cdff23
caps.latest.revision: "10"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 09a05b8c73cd7be84af01eb4465681816e429bc3
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/20/2017
---
# <a name="mqseries-adapter-custom-headers"></a><span data-ttu-id="db540-102">MQSeries 配接器自訂標頭</span><span class="sxs-lookup"><span data-stu-id="db540-102">MQSeries Adapter Custom Headers</span></span>
<span data-ttu-id="db540-103">因為在 MQSeries 訊息中使用的標頭結構，您必須管理任何您想要使用的自訂標頭。</span><span class="sxs-lookup"><span data-stu-id="db540-103">Because of the header structures used in MQSeries messages, you must manage any custom headers you want to use.</span></span> <span data-ttu-id="db540-104">自訂標頭必須是訊息內文的一部分，以避免干擾 MQSeries 標頭的處理。</span><span class="sxs-lookup"><span data-stu-id="db540-104">Custom headers must be part of the message body to avoid interfering with the processing of the MQSeries headers.</span></span> <span data-ttu-id="db540-105">請確定您會避免降級任何自動升級的屬性。</span><span class="sxs-lookup"><span data-stu-id="db540-105">Make sure that you avoid demoting any one of the automatically promoted properties.</span></span> <span data-ttu-id="db540-106">如需自動升級屬性的詳細資訊，請參閱[MQSeries 配接器屬性](../core/mqseries-adapter-properties.md)。</span><span class="sxs-lookup"><span data-stu-id="db540-106">For more information about automatically promoted properties, see [MQSeries Adapter Properties](../core/mqseries-adapter-properties.md).</span></span>  
  
 <span data-ttu-id="db540-107">接著，在訊息內文中自訂標頭的合併需要其他處理。</span><span class="sxs-lookup"><span data-stu-id="db540-107">In turn, the incorporation of custom headers in the message body requires additional processing.</span></span> <span data-ttu-id="db540-108">其中一個解決方案就是在應用程式的管線中處理自訂標頭。</span><span class="sxs-lookup"><span data-stu-id="db540-108">One solution is to handle the custom headers in the pipelines of the application.</span></span> <span data-ttu-id="db540-109">接收管線會擷取自訂標頭資訊，並將資訊升級為內容屬性。</span><span class="sxs-lookup"><span data-stu-id="db540-109">A receive pipeline extracts the custom header information and promotes the information as context properties.</span></span> <span data-ttu-id="db540-110">同樣地，傳送管線會取得對應到自訂標頭的內容屬性，並降級訊息內文中的屬性。</span><span class="sxs-lookup"><span data-stu-id="db540-110">Similarly, the send pipeline takes the context properties corresponding to the custom header and demotes the properties in the body of the message.</span></span>  
  
 <span data-ttu-id="db540-111">在管線元件中使用自訂標頭的範例，請參閱[MQSSendPipelineComponent （BizTalk Server 範例）](../core/mqssendpipelinecomponent-biztalk-server-sample.md)。</span><span class="sxs-lookup"><span data-stu-id="db540-111">For an example of using custom headers in a pipeline component, see [MQSSendPipelineComponent (BizTalk Server Sample)](../core/mqssendpipelinecomponent-biztalk-server-sample.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="db540-112">另請參閱</span><span class="sxs-lookup"><span data-stu-id="db540-112">See Also</span></span>  
 [<span data-ttu-id="db540-113">MQSeries 配接器屬性</span><span class="sxs-lookup"><span data-stu-id="db540-113">MQSeries Adapter Properties</span></span>](../core/mqseries-adapter-properties.md)