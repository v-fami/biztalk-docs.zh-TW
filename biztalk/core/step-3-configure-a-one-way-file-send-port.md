---
title: 步驟 3： 設定單向 FILE 傳送埠 |Microsoft Docs
ms.custom: ''
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: c52c6b6b-6f9c-48f2-8732-450fe3a15eae
caps.latest.revision: 4
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 67cc96dfccc7256681887290ef37261c4c7fecb9
ms.sourcegitcommit: 266308ec5c6a9d8d80ff298ee6051b4843c5d626
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/27/2018
ms.locfileid: "36987919"
---
# <a name="step-3-configure-a-one-way-file-send-port"></a><span data-ttu-id="923dc-102">步驟 3： 設定單向 FILE 傳送埠</span><span class="sxs-lookup"><span data-stu-id="923dc-102">Step 3: Configure a One-way FILE Send Port</span></span>
<span data-ttu-id="923dc-103">在此步驟中，您會設定單向 FILE 傳送埠取用 REST 介面從收到的回應訊息，並將它複製到檔案位置。</span><span class="sxs-lookup"><span data-stu-id="923dc-103">In this step you configure a one-way FILE send port that consumes the response message received from the REST interface and copies it to a file location.</span></span>  

### <a name="to-configure-a-file-send-port"></a><span data-ttu-id="923dc-104">若要設定 FILE 傳送埠</span><span class="sxs-lookup"><span data-stu-id="923dc-104">To configure a FILE send port</span></span>  

1. <span data-ttu-id="923dc-105">BizTalk Server 管理主控台，從下**BizTalk Application 1**節點，以滑鼠右鍵按一下**傳送連接埠**，指向**新增**，然後按一下 **靜態單向傳送埠**。</span><span class="sxs-lookup"><span data-stu-id="923dc-105">From BizTalk Server Administration Console, under the **BizTalk Application 1** node, right-click **Send Ports**, point to **New**, and then click **Static One-way Send Port**.</span></span>  

2. <span data-ttu-id="923dc-106">在 [一般] 索引標籤上，執行下列動作：</span><span class="sxs-lookup"><span data-stu-id="923dc-106">On the General tab, do the following:</span></span>  

   |<span data-ttu-id="923dc-107">使用</span><span class="sxs-lookup"><span data-stu-id="923dc-107">Use this</span></span>|<span data-ttu-id="923dc-108">以進行此動作</span><span class="sxs-lookup"><span data-stu-id="923dc-108">To do this</span></span>|  
   |--------------|----------------|  
   |<span data-ttu-id="923dc-109">**名稱**</span><span class="sxs-lookup"><span data-stu-id="923dc-109">**Name**</span></span>|<span data-ttu-id="923dc-110">型別**SendPortOutAzureMarketPlaceData**。</span><span class="sxs-lookup"><span data-stu-id="923dc-110">Type **SendPortOutAzureMarketPlaceData**.</span></span>|  
   |<span data-ttu-id="923dc-111">**型別**</span><span class="sxs-lookup"><span data-stu-id="923dc-111">**Type**</span></span>|<span data-ttu-id="923dc-112">選取 **檔案**。</span><span class="sxs-lookup"><span data-stu-id="923dc-112">Select **FILE**.</span></span>|  
   |<span data-ttu-id="923dc-113">**傳送處理常式**</span><span class="sxs-lookup"><span data-stu-id="923dc-113">**Send handler**</span></span>|<span data-ttu-id="923dc-114">選取 **[BizTalkServerApplication]**。</span><span class="sxs-lookup"><span data-stu-id="923dc-114">Select **BizTalkServerApplication**.</span></span>|  
   |<span data-ttu-id="923dc-115">**傳送管線**</span><span class="sxs-lookup"><span data-stu-id="923dc-115">**Send pipeline**</span></span>|<span data-ttu-id="923dc-116">選取  **PassThruTransmit**。</span><span class="sxs-lookup"><span data-stu-id="923dc-116">Select **PassThruTransmit**.</span></span>|  

    <span data-ttu-id="923dc-117">按一下 **設定**。</span><span class="sxs-lookup"><span data-stu-id="923dc-117">Click **Configure**.</span></span>  

3. <span data-ttu-id="923dc-118">從 [檔案傳輸屬性] 中，執行下列動作：</span><span class="sxs-lookup"><span data-stu-id="923dc-118">From File Transport Properties, do the following:</span></span>  


   |      <span data-ttu-id="923dc-119">使用</span><span class="sxs-lookup"><span data-stu-id="923dc-119">Use this</span></span>      |                                                              <span data-ttu-id="923dc-120">以進行此動作</span><span class="sxs-lookup"><span data-stu-id="923dc-120">To do this</span></span>                                                               |
   |--------------------|---------------------------------------------------------------------------------------------------------------------------------------|
   | <span data-ttu-id="923dc-121">**接收資料夾**</span><span class="sxs-lookup"><span data-stu-id="923dc-121">**Receive folder**</span></span> | <span data-ttu-id="923dc-122">輸入的位置，[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]複製回應訊息。</span><span class="sxs-lookup"><span data-stu-id="923dc-122">Type a location where [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] copies the response message.</span></span> |
   |   <span data-ttu-id="923dc-123">**檔案名稱**</span><span class="sxs-lookup"><span data-stu-id="923dc-123">**File name**</span></span>    |                                                       <span data-ttu-id="923dc-124">保留 `%MessageID%.xml`</span><span class="sxs-lookup"><span data-stu-id="923dc-124">Retain `%MessageID%.xml`</span></span>                                                        |


4. <span data-ttu-id="923dc-125">在 **篩選條件**索引標籤上，指定要取用所有的訊息寫入篩選器[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]Messagebox 資料庫中建立的接收埠[步驟 2： 設定雙向 Wcf-webhttp 傳送埠](../core/step-2-configure-a-two-way-wcf-webhttp-send-port.md).</span><span class="sxs-lookup"><span data-stu-id="923dc-125">On the **Filters** tab, specify the filter to consume all messages that are written to the [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] Message Box database by the receive port you created in [Step 2: Configure a Two-way WCF-WebHttp Send Port](../core/step-2-configure-a-two-way-wcf-webhttp-send-port.md).</span></span>  


   |              |                                       |
   |--------------|---------------------------------------|
   | <span data-ttu-id="923dc-126">**屬性**</span><span class="sxs-lookup"><span data-stu-id="923dc-126">**Property**</span></span> |         <span data-ttu-id="923dc-127">若要設定**BTS。SPName**</span><span class="sxs-lookup"><span data-stu-id="923dc-127">Set to **BTS.SPName**</span></span>         |
   | <span data-ttu-id="923dc-128">**[運算子]**</span><span class="sxs-lookup"><span data-stu-id="923dc-128">**Operator**</span></span> |             <span data-ttu-id="923dc-129">若要設定 **==**</span><span class="sxs-lookup"><span data-stu-id="923dc-129">Set to **==**</span></span>             |
   |  <span data-ttu-id="923dc-130">**ReplTest1**</span><span class="sxs-lookup"><span data-stu-id="923dc-130">**Value**</span></span>   | <span data-ttu-id="923dc-131">若要設定 `SendPortRESTAzureMarketPlace`</span><span class="sxs-lookup"><span data-stu-id="923dc-131">Set to `SendPortRESTAzureMarketPlace`</span></span> |


5. <span data-ttu-id="923dc-132">按一下 [確定] 。</span><span class="sxs-lookup"><span data-stu-id="923dc-132">Click **OK**.</span></span>  

## <a name="see-also"></a><span data-ttu-id="923dc-133">另請參閱</span><span class="sxs-lookup"><span data-stu-id="923dc-133">See Also</span></span>  
 [<span data-ttu-id="923dc-134">教學課程 5： 叫用 REST 介面，使用 BizTalk Server</span><span class="sxs-lookup"><span data-stu-id="923dc-134">Tutorial 5: Invoking a REST Interface Using BizTalk Server</span></span>](../core/tutorial-5-invoking-a-rest-interface-using-biztalk-server.md)