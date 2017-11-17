---
redirect_url: /biztalk/core/creating-peoplesoft-send-handlers/
redirect_document_id: True
ROBOTS: NOINDEX
ms.openlocfilehash: e5f68232aa0cb59835523df0afac01f3d1949489
ms.sourcegitcommit: dd7c54feab783ae2f8fe75873363fe9ffc77cd66
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/07/2017
---
# <a name="how-to-set-pipelines-for-peoplesoft-enterprise"></a><span data-ttu-id="0865c-101">如何設定 PeopleSoft Enterprise 的管線</span><span class="sxs-lookup"><span data-stu-id="0865c-101">How to Set Pipelines for PeopleSoft Enterprise</span></span>
<span data-ttu-id="0865c-102">Microsoft BizTalk Adapter for PeopleSoft Enterprise 需要您選取適當的管線。</span><span class="sxs-lookup"><span data-stu-id="0865c-102">Microsoft BizTalk Adapter for PeopleSoft Enterprise requires that you select an appropriate pipeline.</span></span>  
  
## <a name="setting-pipelines"></a><span data-ttu-id="0865c-103">設定管線</span><span class="sxs-lookup"><span data-stu-id="0865c-103">Setting Pipelines</span></span>  
  
#### <a name="to-set-pipelines"></a><span data-ttu-id="0865c-104">設定管線</span><span class="sxs-lookup"><span data-stu-id="0865c-104">To set pipelines</span></span>  
  
1.  <span data-ttu-id="0865c-105">在 BizTalk Server 管理主控台中，依序展開**BizTalk Server 管理**，依序展開**BizTalk 群組**，依序展開**應用程式**，然後展開 [所需應用程式。</span><span class="sxs-lookup"><span data-stu-id="0865c-105">In the BizTalk Server Administration Console, expand **BizTalk Server Administration**, expand **BizTalk Group**, expand **Applications**, and then expand the desired application.</span></span>  
  
2.  <span data-ttu-id="0865c-106">以滑鼠右鍵按一下**傳送埠**，指向 [**新增**，然後按一下 [**靜態請求-回應傳送埠**。</span><span class="sxs-lookup"><span data-stu-id="0865c-106">Right-click **Send Ports**, point to **New**, and then click **Static Solicit-Response Send Port**.</span></span>  
  
3.  <span data-ttu-id="0865c-107">在**傳送埠屬性**對話方塊方塊中，執行下列動作：</span><span class="sxs-lookup"><span data-stu-id="0865c-107">In the **Send Port Properties** dialog box, do the following:</span></span>  
  
    1.  <span data-ttu-id="0865c-108">輸入傳送埠名稱，例如`SSOSendToPeopleSoft`。</span><span class="sxs-lookup"><span data-stu-id="0865c-108">Type a name for the send port, for example, `SSOSendToPeopleSoft`.</span></span>  
  
    2.  <span data-ttu-id="0865c-109">從**類型**下拉式清單中，選取**PeopleSoft**。</span><span class="sxs-lookup"><span data-stu-id="0865c-109">From the **Type** drop-down list, select **PeopleSoft**.</span></span>  
  
    3.  <span data-ttu-id="0865c-110">從**傳送處理常式**下拉式清單中，選取 URI。</span><span class="sxs-lookup"><span data-stu-id="0865c-110">From the **Send handler** drop-down list, select the URI.</span></span>  
  
    4.  <span data-ttu-id="0865c-111">從 [傳送管線] 下拉式清單中，選取 [ **Microsoft.BizTalk.DefaultPipelines.XMLTransmit**。</span><span class="sxs-lookup"><span data-stu-id="0865c-111">From the Send Pipeline drop-down list, select **Microsoft.BizTalk.DefaultPipelines.XMLTransmit**.</span></span>  
  
    5.  <span data-ttu-id="0865c-112">從**接收管線**下拉式清單中，選取**[microsoft.biztalk.defaultpiplelines.xmlreceive]**。</span><span class="sxs-lookup"><span data-stu-id="0865c-112">From the **Receive Pipeline** drop-down list, select **Microsoft.BizTalk.DefaultPiplelines.XMLReceive**.</span></span>  
  
4.  <span data-ttu-id="0865c-113">按一下 **[確定]**。</span><span class="sxs-lookup"><span data-stu-id="0865c-113">Click **OK**.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="0865c-114">另請參閱</span><span class="sxs-lookup"><span data-stu-id="0865c-114">See Also</span></span>  
 [<span data-ttu-id="0865c-115">建立 PeopleSoft 傳送處理常式</span><span class="sxs-lookup"><span data-stu-id="0865c-115">Creating PeopleSoft Send Handlers</span></span>](../core/creating-peoplesoft-send-handlers.md)