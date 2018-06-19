---
title: 如何設定整合閘道和 HTTP 輸出連接器 |Microsoft 文件
ms.custom: ''
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- Integration Gateway
- gateway nodes, creating
- HTTP Output Connector
ms.assetid: a02ee533-07a8-42fa-a72a-7e5359b18f40
caps.latest.revision: 6
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: acfa52be85a664432af95af0ca292e9cc394c6ca
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/20/2017
ms.locfileid: "22247918"
---
# <a name="how-to-configure-the-integration-gateway-and-http-output-connector"></a><span data-ttu-id="0b146-102">如何設定整合閘道和 HTTP 輸出連接器</span><span class="sxs-lookup"><span data-stu-id="0b146-102">How to Configure the Integration Gateway and HTTP Output Connector</span></span>
<span data-ttu-id="0b146-103">依照下列步驟設定「整合閘道」和「HTTP 輸出連接器」。</span><span class="sxs-lookup"><span data-stu-id="0b146-103">Follow these steps to configure the Integration Gateway and HTTP Output Connector.</span></span>  
  
### <a name="to-create-and-configure-a-new-gateway-node"></a><span data-ttu-id="0b146-104">若要建立和設定新的閘道節點</span><span class="sxs-lookup"><span data-stu-id="0b146-104">To create and configure a new gateway node</span></span>  
  
1.  <span data-ttu-id="0b146-105">在 Web 瀏覽器中開啟 PeopleSoft 應用程式。</span><span class="sxs-lookup"><span data-stu-id="0b146-105">In a Web browser, open the PeopleSoft application.</span></span>  
  
2.  <span data-ttu-id="0b146-106">找出**PeopleTools**，選取**Integration Broker**，然後選取**閘道**。</span><span class="sxs-lookup"><span data-stu-id="0b146-106">Locate **PeopleTools**, select **Integration Broker**, and then select **Gateways**.</span></span>  
  
3.  <span data-ttu-id="0b146-107">在**搜尋依據**欄位中，輸入`LOCAL`，然後按一下 **搜尋**。</span><span class="sxs-lookup"><span data-stu-id="0b146-107">In the **Search By** field, type `LOCAL`, and then click **Search**.</span></span>  
  
     ![](../core/media/psadapter-31-task-gatewaysearch.gif "PSAdapter_31_Task_GatewaySearch")  
  
4.  <span data-ttu-id="0b146-108">輸入`machine-name/PSIGW/PeopleSoftListeningConnector`到**Gateway URL**項目。</span><span class="sxs-lookup"><span data-stu-id="0b146-108">Enter `machine-name/PSIGW/PeopleSoftListeningConnector` into the **Gateway URL** entry.</span></span>  
  
     ![](../core/media/psadapter-32-task-gatewayurl.gif "PSAdapter_32_Task_GatewayURL")  
  
5.  <span data-ttu-id="0b146-109">按一下**重新整理**，然後按一下 **儲存**。</span><span class="sxs-lookup"><span data-stu-id="0b146-109">Click **Refresh**, and then click **Save**.</span></span>  
  
6.  <span data-ttu-id="0b146-110">按一下**屬性**連結**HTTPTARGET**若要檢視屬性/值組合，該識別碼。</span><span class="sxs-lookup"><span data-stu-id="0b146-110">Click the **Properties** link for **HTTPTARGET** to view the properties/value combination for that ID.</span></span>  
  
     <span data-ttu-id="0b146-111">您可以在此或在 [Node Definition] 設定 URL。</span><span class="sxs-lookup"><span data-stu-id="0b146-111">You can set the URL here, or at the Node Definition.</span></span> <span data-ttu-id="0b146-112">在本討論中，請在 Node 層級設定 URL。</span><span class="sxs-lookup"><span data-stu-id="0b146-112">For this discussion, set the URL at the Node level.</span></span>  
  
     ![](../core/media/psadapter-33-task-gatewaynodelevel.gif "PSAdapter_33_Task_GatewayNodeLevel")  
  
## <a name="see-also"></a><span data-ttu-id="0b146-113">另請參閱</span><span class="sxs-lookup"><span data-stu-id="0b146-113">See Also</span></span>  
 [<span data-ttu-id="0b146-114">建立 PeopleSoft HTTP 主控件和連接埠</span><span class="sxs-lookup"><span data-stu-id="0b146-114">Creating a PeopleSoft HTTP Host and Port</span></span>](../core/creating-a-peoplesoft-http-host-and-port.md)