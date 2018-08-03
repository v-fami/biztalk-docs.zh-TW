---
title: 步驟 2： 設定雙向 Wcf-webhttp 傳送埠 |Microsoft 文件
ms.custom: ''
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 0bcab296-7921-4df4-abcc-eea78cc827e8
caps.latest.revision: 5
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: f355275f9480cfa13f3a15bcc6522fbe7ec83b8c
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/20/2017
ms.locfileid: "22278886"
---
# <a name="step-2-configure-a-two-way-wcf-webhttp-send-port"></a><span data-ttu-id="e01e6-102">步驟 2： 設定雙向 Wcf-webhttp 傳送埠</span><span class="sxs-lookup"><span data-stu-id="e01e6-102">Step 2: Configure a Two-way WCF-WebHttp Send Port</span></span>
<span data-ttu-id="e01e6-103">在這個步驟您要設定雙向**Wcf-webhttp**傳送埠以叫用 REST 資源 URL，以擷取在美國空中電信業者的排程中的延遲。</span><span class="sxs-lookup"><span data-stu-id="e01e6-103">In this step you configure a two-way **WCF-WebHttp** send port to invoke the REST resource URL to retrieve delays in the US air carriers’ schedules.</span></span>  
  
### <a name="to-configure-wcf-webhttp-send-port"></a><span data-ttu-id="e01e6-104">若要設定 WCF-WebHttp 傳送埠</span><span class="sxs-lookup"><span data-stu-id="e01e6-104">To configure WCF-WebHttp send port</span></span>  
  
1.  <span data-ttu-id="e01e6-105">從 BizTalk Server 管理主控台，在**BizTalk Application 1** ] 節點，以滑鼠右鍵按一下**傳送埠**，指向**新增**，然後按一下 [**靜態請求-回應傳送埠**。</span><span class="sxs-lookup"><span data-stu-id="e01e6-105">From BizTalk Server Administration Console, under the **BizTalk Application 1** node, right-click **Send Ports**, point to **New**, and then click **Static Solicit-Response Send Port**.</span></span>  
  
2.  <span data-ttu-id="e01e6-106">在 [一般] 索引標籤上，執行下列動作：</span><span class="sxs-lookup"><span data-stu-id="e01e6-106">On the **General** tab, do the following:</span></span>  
  
    |<span data-ttu-id="e01e6-107">使用</span><span class="sxs-lookup"><span data-stu-id="e01e6-107">Use this</span></span>|<span data-ttu-id="e01e6-108">動作</span><span class="sxs-lookup"><span data-stu-id="e01e6-108">To do this</span></span>|  
    |--------------|----------------|  
    |<span data-ttu-id="e01e6-109">**名稱**</span><span class="sxs-lookup"><span data-stu-id="e01e6-109">**Name**</span></span>|<span data-ttu-id="e01e6-110">型別**SendPortRESTAzureMarketPlace**。</span><span class="sxs-lookup"><span data-stu-id="e01e6-110">Type **SendPortRESTAzureMarketPlace**.</span></span>|  
    |<span data-ttu-id="e01e6-111">**型別**</span><span class="sxs-lookup"><span data-stu-id="e01e6-111">**Type**</span></span>|<span data-ttu-id="e01e6-112">選取**Wcf-webhttp**。</span><span class="sxs-lookup"><span data-stu-id="e01e6-112">Select **WCF-WebHttp**.</span></span>|  
    |<span data-ttu-id="e01e6-113">**傳送處理常式**</span><span class="sxs-lookup"><span data-stu-id="e01e6-113">**Send handler**</span></span>|<span data-ttu-id="e01e6-114">選取 **[BizTalkServerApplication]**。</span><span class="sxs-lookup"><span data-stu-id="e01e6-114">Select **BizTalkServerApplication**.</span></span>|  
    |<span data-ttu-id="e01e6-115">**傳送管線**</span><span class="sxs-lookup"><span data-stu-id="e01e6-115">**Send pipeline**</span></span>|<span data-ttu-id="e01e6-116">選取**PassThruTransmit**。</span><span class="sxs-lookup"><span data-stu-id="e01e6-116">Select **PassThruTransmit**.</span></span>|  
    |<span data-ttu-id="e01e6-117">**接收管線**</span><span class="sxs-lookup"><span data-stu-id="e01e6-117">**Receive pipeline**</span></span>|<span data-ttu-id="e01e6-118">選取**PassThruReceive**。</span><span class="sxs-lookup"><span data-stu-id="e01e6-118">Select **PassThruReceive**.</span></span>|  
  
     <span data-ttu-id="e01e6-119">按一下**設定**。</span><span class="sxs-lookup"><span data-stu-id="e01e6-119">Click **Configure**.</span></span>  
  
3.  <span data-ttu-id="e01e6-120">從**Wcf-webhttp 傳輸屬性**對話方塊方塊中，執行下列動作：</span><span class="sxs-lookup"><span data-stu-id="e01e6-120">From the **WCF-WebHttp Transport Properties** dialog box, do the following:</span></span>  
  
    1.  <span data-ttu-id="e01e6-121">在**一般**索引標籤上，針對**位址 (URI)**，輸入`https://api.datamarket.azure.com/oakleaf/US_Air_Carrier_Flight_Delays_Incr/`。</span><span class="sxs-lookup"><span data-stu-id="e01e6-121">On the **General** tab, for **Address (URI)**, enter `https://api.datamarket.azure.com/oakleaf/US_Air_Carrier_Flight_Delays_Incr/`.</span></span>  
  
    2.  <span data-ttu-id="e01e6-122">在 [一般] 索引標籤上的**HTTP 方法和 URL 對應**，輸入下列命令：</span><span class="sxs-lookup"><span data-stu-id="e01e6-122">On the General tab, for **HTTP Method and URL Mapping**, enter the following:</span></span>  
  
        ```  
        <BtsHttpUrlMapping>  
        <Operation Method="GET" Url="/On_Time_Performance" />  
        </BtsHttpUrlMapping>  
  
        ```  
  
         <span data-ttu-id="e01e6-123">在這裡，**取得**為 HTTP 動詞命令和**On_Time_Performance**附加至基底 URI 來建構唯一資源 URL，以擷取航班延誤。</span><span class="sxs-lookup"><span data-stu-id="e01e6-123">Here, **GET** is the HTTP verb and **On_Time_Performance** is appended to the base URI to construct a unique resource URL to retrieve flight delays.</span></span>  
         
         > [!TIP] 
         > <span data-ttu-id="e01e6-124">在 [URL] 欄位中，任何特殊的 XML 字元必須"逸出"。</span><span class="sxs-lookup"><span data-stu-id="e01e6-124">Within the URL field, any special XML characters must be "escaped".</span></span> <span data-ttu-id="e01e6-125">這可確保，處理，並且保留連接埠的特殊 XML 字元。</span><span class="sxs-lookup"><span data-stu-id="e01e6-125">This ensures that the special XML characters are processed, and preserved by the port.</span></span> <span data-ttu-id="e01e6-126">例如，`&`必須逸出特殊字元為`&amp;`。</span><span class="sxs-lookup"><span data-stu-id="e01e6-126">For example, the `&` special character must be escaped as `&amp;`.</span></span> 
           >
           ><span data-ttu-id="e01e6-127">從：`Url=”/Customer?{ID}& group=Location”`</span><span class="sxs-lookup"><span data-stu-id="e01e6-127">From: `Url=”/Customer?{ID}& group=Location”`</span></span>
           >
           >
           ><span data-ttu-id="e01e6-128">若要：`Url=”/Customer?{ID}&amp;group=Location”`</span><span class="sxs-lookup"><span data-stu-id="e01e6-128">To: `Url=”/Customer?{ID}&amp;group=Location”`</span></span>
  
    3.  <span data-ttu-id="e01e6-129">在**繫結**索引標籤上，針對**接收訊息大小上限**欄位中，選取夠大的值。</span><span class="sxs-lookup"><span data-stu-id="e01e6-129">On the **Bindings** tab, for the **Maximum Received Message Size** field, select a sufficiently large value.</span></span> <span data-ttu-id="e01e6-130">這是因為含有航班狀態的回應訊息通常相當大，有可能超過指定的預設訊息大小。</span><span class="sxs-lookup"><span data-stu-id="e01e6-130">That’s because typically the response message containing the flight status is considerably large and might exceed the default message size specified.</span></span>  
  
    4.  <span data-ttu-id="e01e6-131">在**安全性**索引標籤上，執行下列動作：</span><span class="sxs-lookup"><span data-stu-id="e01e6-131">On the **Security** tab, do the following:</span></span>  
  
        1.  <span data-ttu-id="e01e6-132">如**安全性模式**，選取**傳輸**。</span><span class="sxs-lookup"><span data-stu-id="e01e6-132">For the **Security mode**, select **Transport**.</span></span>  
  
        2.  <span data-ttu-id="e01e6-133">如**傳輸用戶端認證類型**，選取**基本**。</span><span class="sxs-lookup"><span data-stu-id="e01e6-133">For **Transport client credential type**, select **Basic**.</span></span>  
  
        3.  <span data-ttu-id="e01e6-134">在下**使用者名稱認證**方塊中，按一下**編輯**。</span><span class="sxs-lookup"><span data-stu-id="e01e6-134">Under the **User name credentials** box, click **Edit**.</span></span> <span data-ttu-id="e01e6-135">在**用戶端認證**對話方塊中，選取**執行不會使用單一登入**，並輸入使用者名稱和密碼從您擷取**我的帳戶**索引標籤上，當您有了登入[Windows Azure Marketplace](http://go.microsoft.com/fwlink/p/?LinkId=257913)。</span><span class="sxs-lookup"><span data-stu-id="e01e6-135">In the **Client Credentials** dialog box, select **Do no use Single-Sign On**, and enter the username and password that you retrieved from the **My Account** tab after you have logged into [Windows Azure Marketplace](http://go.microsoft.com/fwlink/p/?LinkId=257913).</span></span> <span data-ttu-id="e01e6-136">認證會列出針對**客戶 ID** （使用者名稱） 和**主要帳戶金鑰**（密碼） 標籤。</span><span class="sxs-lookup"><span data-stu-id="e01e6-136">The credentials are listed against the **Customer ID** (user name) and **Primary Account Key** (password) labels.</span></span>  
  
        4.  <span data-ttu-id="e01e6-137">按一下 **[確定]**。</span><span class="sxs-lookup"><span data-stu-id="e01e6-137">Click **OK**.</span></span>  
  
    5.  <span data-ttu-id="e01e6-138">在**訊息**索引標籤上，針對**隱藏動詞命令的主體**，指定您要刪除從要求訊息的訊息內容的動詞。</span><span class="sxs-lookup"><span data-stu-id="e01e6-138">On the **Messages** tab, for **Suppress Body for Verbs**, specify the verb for which you want to strip the message payload from the request message.</span></span> <span data-ttu-id="e01e6-139">此教學課程中，指定為`GET`。</span><span class="sxs-lookup"><span data-stu-id="e01e6-139">For this tutorial, specify this as `GET`.</span></span> <span data-ttu-id="e01e6-140">原因如下： GET 方法呼叫美國空中載波飛行延遲 REST 端點上的不需要的訊息內容。REST 資源 URL 就足以擷取資訊。</span><span class="sxs-lookup"><span data-stu-id="e01e6-140">Here’s why: A GET method call on the US Air Carrier flight delays REST endpoint does not require a message payload; the REST resource URL is sufficient to retrieve the information.</span></span> <span data-ttu-id="e01e6-141">不過，要觸發程序**Wcf-webhttp**讓其餘呼叫的傳送埠，您卸除具有某些訊息內文將虛擬訊息。</span><span class="sxs-lookup"><span data-stu-id="e01e6-141">However, to trigger the **WCF-WebHttp** send port that makes the REST call, you drop a dummy message that has some message body.</span></span> <span data-ttu-id="e01e6-142">傳送埠必須 REST 端點傳送該虛擬訊息，因為稍早所述，端點未預期的訊息內容。</span><span class="sxs-lookup"><span data-stu-id="e01e6-142">The send port must not send that dummy message to the REST endpoint because, as explained earlier, the endpoint does not expect a message payload.</span></span> <span data-ttu-id="e01e6-143">因此，再叫用 REST 端點，配接器去除訊息內容，從空的訊息只會針對您在中指定的動詞命令**隱藏動詞命令的主體**文字方塊。</span><span class="sxs-lookup"><span data-stu-id="e01e6-143">So, before invoking the REST endpoint, the adapter strips the message payload from the dummy message only for the verbs that you specify in the **Suppress Body for Verbs** text box.</span></span>  
  
    6.  <span data-ttu-id="e01e6-144">按一下**確定**直到您會回到 [傳送埠屬性] 對話方塊。</span><span class="sxs-lookup"><span data-stu-id="e01e6-144">Click **OK** until you are back on the Send Port Properties dialog box.</span></span> <span data-ttu-id="e01e6-145">從左窗格中，按一下 **篩選**，並指定要取用接收透過接收所有訊息的篩選條件連接埠中建立您[步驟 1： 設定 FILE 接收位置](../core/step-1-configure-a-file-receive-location.md)。</span><span class="sxs-lookup"><span data-stu-id="e01e6-145">From the left pane, click **Filters**, and specify the filter to consume all messages that are received through the receive port you created in [Step 1: Configure a FILE Receive Location](../core/step-1-configure-a-file-receive-location.md).</span></span>  
  
        |||  
        |-|-|  
        |<span data-ttu-id="e01e6-146">**屬性**</span><span class="sxs-lookup"><span data-stu-id="e01e6-146">**Property**</span></span>|<span data-ttu-id="e01e6-147">設定為**BTS。ReceivePortName**</span><span class="sxs-lookup"><span data-stu-id="e01e6-147">Set to **BTS.ReceivePortName**</span></span>|  
        |<span data-ttu-id="e01e6-148">**運算子**</span><span class="sxs-lookup"><span data-stu-id="e01e6-148">**Operator**</span></span>|<span data-ttu-id="e01e6-149">設定為**==**</span><span class="sxs-lookup"><span data-stu-id="e01e6-149">Set to **==**</span></span>|  
        |<span data-ttu-id="e01e6-150">**值**</span><span class="sxs-lookup"><span data-stu-id="e01e6-150">**Value**</span></span>|<span data-ttu-id="e01e6-151">設定為`ReceivePortRestAzureMarketPlace`</span><span class="sxs-lookup"><span data-stu-id="e01e6-151">Set to `ReceivePortRestAzureMarketPlace`</span></span>|  
  
    7.  <span data-ttu-id="e01e6-152">按一下 **[確定]**。</span><span class="sxs-lookup"><span data-stu-id="e01e6-152">Click **OK**.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="e01e6-153">另請參閱</span><span class="sxs-lookup"><span data-stu-id="e01e6-153">See Also</span></span>  
 [<span data-ttu-id="e01e6-154">教學課程 5： 叫用 REST 介面使用 BizTalk Server</span><span class="sxs-lookup"><span data-stu-id="e01e6-154">Tutorial 5: Invoking a REST Interface Using BizTalk Server</span></span>](../core/tutorial-5-invoking-a-rest-interface-using-biztalk-server.md)