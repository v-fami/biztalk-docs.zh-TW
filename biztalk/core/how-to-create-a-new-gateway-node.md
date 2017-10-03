---
title: "如何建立新的 Gateway 節點 |Microsoft 文件"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords: gateway nodes, creating
ms.assetid: e7c5f9a7-a58e-4661-9cb5-2414e31a57a3
caps.latest.revision: "8"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: b371243d58389415349d5a88c05b7bf312e70ef9
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/20/2017
---
# <a name="how-to-create-a-new-gateway-node"></a><span data-ttu-id="5e403-102">如何建立新的 Gateway 節點</span><span class="sxs-lookup"><span data-stu-id="5e403-102">How to Create a New Gateway Node</span></span>
<span data-ttu-id="5e403-103">請遵循以下步驟，在 PeopleSoft Enterprise 中建立及設定新的 Gateway 節點。</span><span class="sxs-lookup"><span data-stu-id="5e403-103">Follow these steps to create and configure a new Gateway node in PeopleSoft Enterprise.</span></span>  
  
### <a name="to-create-and-configure-a-new-gateway-node"></a><span data-ttu-id="5e403-104">若要建立和設定新的閘道節點</span><span class="sxs-lookup"><span data-stu-id="5e403-104">To create and configure a new gateway node</span></span>  
  
1.  <span data-ttu-id="5e403-105">在 PeopleSoft 中，在左窗格中，按一下**節點定義**連結。</span><span class="sxs-lookup"><span data-stu-id="5e403-105">In PeopleSoft, on the left panel, click the **Node Definitions** link.</span></span>  
  
2.  <span data-ttu-id="5e403-106">按一下**新增值** 索引標籤。</span><span class="sxs-lookup"><span data-stu-id="5e403-106">Click the **Add a New Value** tab.</span></span>  
  
3.  <span data-ttu-id="5e403-107">在**節點名稱**欄位中，輸入`MSEXTERNAL`，然後按一下 **新增**。</span><span class="sxs-lookup"><span data-stu-id="5e403-107">In the **Node Name** field, enter `MSEXTERNAL`, and then click **Add**.</span></span>  
  
4.  <span data-ttu-id="5e403-108">按一下**節點**索引標籤，然後輸入下列資訊：</span><span class="sxs-lookup"><span data-stu-id="5e403-108">Click the **Node** tab, and enter the following information:</span></span>  
  
    1.  <span data-ttu-id="5e403-109">**描述：**輸入節點的描述。</span><span class="sxs-lookup"><span data-stu-id="5e403-109">**Description:** Enter a description for the node.</span></span>  
  
    2.  <span data-ttu-id="5e403-110">**節點型別：**選取**外部**。</span><span class="sxs-lookup"><span data-stu-id="5e403-110">**Node Type:** Select **External**.</span></span>  
  
    3.  <span data-ttu-id="5e403-111">**路由類型：**選取**隱含**。</span><span class="sxs-lookup"><span data-stu-id="5e403-111">**Routing Type:** Select **Implicit**.</span></span>  
  
     ![](../core/media/psadapter-34-task-gatewaynodeconnector.gif "PSAdapter_34_Task_GatewayNodeConnector")  
  
5.  <span data-ttu-id="5e403-112">按一下**連接器**索引標籤，然後輸入下列資訊：</span><span class="sxs-lookup"><span data-stu-id="5e403-112">Click the **Connectors** tab, and enter the following information:</span></span>  
  
    1.  <span data-ttu-id="5e403-113">**閘道識別碼：**輸入`LOCAL`。</span><span class="sxs-lookup"><span data-stu-id="5e403-113">**Gateway ID:** Enter `LOCAL`.</span></span>  
  
    2.  <span data-ttu-id="5e403-114">**連接器識別碼：**輸入`HTTPTARGET`。</span><span class="sxs-lookup"><span data-stu-id="5e403-114">**Connector ID:** Enter `HTTPTARGET`.</span></span>  
  
     ![](../core/media/psadapter-35-task-gatewayhttptarget.gif "PSAdapter_35_Task_GatewayHTTPTarget")  
  
6.  <span data-ttu-id="5e403-115">按一下**查閱**圖示。</span><span class="sxs-lookup"><span data-stu-id="5e403-115">Click the **Lookup** icon.</span></span>  
  
7.  <span data-ttu-id="5e403-116">在下**連接器識別碼**，按一下  **HTTPTARGET**連結。</span><span class="sxs-lookup"><span data-stu-id="5e403-116">Under **Connector ID**, click the **HTTPTARGET** link.</span></span>  
  
     ![](../core/media/psadapter-36-task-gatewayconnectorid.gif "PSAdapter_36_Task_GatewayConnectorID")  
  
8.  <span data-ttu-id="5e403-117">在**屬性**索引標籤上，輸入下列資訊：</span><span class="sxs-lookup"><span data-stu-id="5e403-117">On the **Properties** tab, enter the following information:</span></span>  
  
    1.  <span data-ttu-id="5e403-118">**標頭：**輸入`Y`。</span><span class="sxs-lookup"><span data-stu-id="5e403-118">**Header:** Enter `Y`.</span></span>  
  
    2.  <span data-ttu-id="5e403-119">**[Httpproperty]:**輸入`POST`。</span><span class="sxs-lookup"><span data-stu-id="5e403-119">**HTTPPROPERTY:** Enter `POST`.</span></span>  
  
    3.  <span data-ttu-id="5e403-120">**[Primaryurl]:**輸入 IP 位址和連接埠的目標電腦 （開發電腦）。</span><span class="sxs-lookup"><span data-stu-id="5e403-120">**PrimaryURL:** Enter the IP address and port of the target computer (the development computer).</span></span>  
  
    > [!NOTE]
    >  <span data-ttu-id="5e403-121">**接收埠**先前設定。</span><span class="sxs-lookup"><span data-stu-id="5e403-121">The **Receive Port** was previously set.</span></span>  
  
     ![](../core/media/psadapter-37-task-gatewaynodereceiveport.gif "PSAdapter_37_Task_GatewayNodeReceivePort")  
  
## <a name="see-also"></a><span data-ttu-id="5e403-122">另請參閱</span><span class="sxs-lookup"><span data-stu-id="5e403-122">See Also</span></span>  
 [<span data-ttu-id="5e403-123">建立 PeopleSoft HTTP 主控件和連接埠</span><span class="sxs-lookup"><span data-stu-id="5e403-123">Creating a PeopleSoft HTTP Host and Port</span></span>](../core/creating-a-peoplesoft-http-host-and-port.md)