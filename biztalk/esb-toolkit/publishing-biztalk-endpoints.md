---
title: 發佈 BizTalk 端點 |Microsoft 文件
ms.custom: ''
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: c8e8cc81-c6c7-4269-81e3-8725082a0c98
caps.latest.revision: 2
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: e33517f1261324ad01eb0d9cad0f51b74c280828
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/20/2017
ms.locfileid: "22294286"
---
# <a name="publishing-biztalk-endpoints"></a><span data-ttu-id="fd7e3-102">發佈 BizTalk 端點</span><span class="sxs-lookup"><span data-stu-id="fd7e3-102">Publishing BizTalk Endpoints</span></span>
<span data-ttu-id="fd7e3-103">您可以使用 ESB 管理入口網站建立和發行項目變成目前設定的通用描述、 探索與整合 (UDDI) 伺服器。</span><span class="sxs-lookup"><span data-stu-id="fd7e3-103">You can use the ESB Management Portal to create and publish entries into the currently configured Universal Description, Discovery, and Integration (UDDI) server.</span></span>  
  
### <a name="to-publish-a-microsoft-biztalk-server-endpoint-into-the-current-uddi-server"></a><span data-ttu-id="fd7e3-104">若要將 Microsoft BizTalk Server 端點發行至目前的 UDDI 伺服器</span><span class="sxs-lookup"><span data-stu-id="fd7e3-104">To publish a Microsoft BizTalk Server endpoint into the current UDDI server</span></span>  
  
1.  <span data-ttu-id="fd7e3-105">指向**登錄**入口網站的主功能表上的索引標籤，然後按一下 **新登錄項目**開啟[新登錄項目頁面](../esb-toolkit/new-registry-entry-page.md)。</span><span class="sxs-lookup"><span data-stu-id="fd7e3-105">Point to the **Registry** tab on the portal main menu, and then click **New Registry Entry** to open the [New Registry Entry Page](../esb-toolkit/new-registry-entry-page.md).</span></span>  
  
2.  <span data-ttu-id="fd7e3-106">使用頁面上的下拉式清單，做為篩選條件的端點類型、 狀態，以及應用程式端點所在的位置。</span><span class="sxs-lookup"><span data-stu-id="fd7e3-106">Use the drop-down lists on the page to filter on the endpoint type, the status, and the application where the endpoint resides.</span></span>  
  
3.  <span data-ttu-id="fd7e3-107">按一下您要建立的 UDDI 登錄要求發行的端點旁邊的箭頭圖示。</span><span class="sxs-lookup"><span data-stu-id="fd7e3-107">Click the arrow icon next to the endpoint you want to publish to create a UDDI registration request.</span></span>  
  
4.  <span data-ttu-id="fd7e3-108">如果系統管理員已啟用自動發行的端點，在入口網站會自動發佈的 UDDI 伺服器到新的項目。</span><span class="sxs-lookup"><span data-stu-id="fd7e3-108">If an administrator has enabled auto-publishing of endpoints, the portal automatically publishes the new entry into the UDDI server.</span></span>  
  
5.  <span data-ttu-id="fd7e3-109">如果系統管理員尚未啟用自動發行的端點，將要求保留在佇列中直到系統管理員核准或拒絕要求。</span><span class="sxs-lookup"><span data-stu-id="fd7e3-109">If an administrator has not enabled auto-publishing of endpoints, the requests remains in the queue until an administrator approves or declines the request.</span></span>