---
redirect_url: /biztalk/core/creating-tibco-enterprise-message-service-send-handlers/
redirect_document_id: true
ROBOTS: NOINDEX
ms.openlocfilehash: 6b15d9d03ef967bcf7189ef756da8fc63a0eb3f6
ms.sourcegitcommit: dd7c54feab783ae2f8fe75873363fe9ffc77cd66
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/07/2017
ms.locfileid: "24013677"
---
# <a name="how-to-create-send-ports-for-tibco-enterprise-message-service"></a><span data-ttu-id="972bd-101">如何建立 TIBCO Enterprise Message Service 的傳送埠</span><span class="sxs-lookup"><span data-stu-id="972bd-101">How to Create Send Ports for TIBCO Enterprise Message Service</span></span>
<span data-ttu-id="972bd-102">依照下列步驟建立傳送埠。</span><span class="sxs-lookup"><span data-stu-id="972bd-102">Follow these steps to create a send port.</span></span>  
  
## <a name="creating-a-send-port"></a><span data-ttu-id="972bd-103">建立傳送埠</span><span class="sxs-lookup"><span data-stu-id="972bd-103">Creating a Send Port</span></span>  
  
#### <a name="to-create-a-send-port"></a><span data-ttu-id="972bd-104">建立傳送埠</span><span class="sxs-lookup"><span data-stu-id="972bd-104">To create a send port</span></span>  
  
1.  <span data-ttu-id="972bd-105">在 BizTalk Server 管理主控台中，依序展開**BizTalk Server 管理**，依序展開**BizTalk 群組**，依序展開**應用程式**，然後展開 所需應用程式。</span><span class="sxs-lookup"><span data-stu-id="972bd-105">In the BizTalk Server Administration Console, expand **BizTalk Server Administration**, expand **BizTalk Group**, expand **Applications**, and then expand the desired application.</span></span>  
  
2.  <span data-ttu-id="972bd-106">以滑鼠右鍵按一下**傳送埠**，指向 **新增**，然後按一下 **靜態請求-回應傳送埠**。</span><span class="sxs-lookup"><span data-stu-id="972bd-106">Right-click **Send Ports**, point to **New**, and then click **Static Solicit-Response Send Port**.</span></span>  
  
3.  <span data-ttu-id="972bd-107">在**傳送埠屬性**對話方塊方塊中，執行下列動作：</span><span class="sxs-lookup"><span data-stu-id="972bd-107">In the **Send Port Properties** dialog box, do the following:</span></span>  
  
    1.  <span data-ttu-id="972bd-108">輸入傳送埠名稱，例如`SendToTIBCOEMS`。</span><span class="sxs-lookup"><span data-stu-id="972bd-108">Type a name for the send port, for example, `SendToTIBCOEMS`.</span></span>  
  
    2.  <span data-ttu-id="972bd-109">從**類型**下拉式清單中，選取**TIBCO EMS**。</span><span class="sxs-lookup"><span data-stu-id="972bd-109">From the **Type** drop-down list, select **TIBCO EMS**.</span></span>  
  
    3.  <span data-ttu-id="972bd-110">從**傳送處理常式**下拉式清單中，選取 URI。</span><span class="sxs-lookup"><span data-stu-id="972bd-110">From the **Send handler** drop-down list, select the URI.</span></span>  
  
    4.  <span data-ttu-id="972bd-111">從 傳送管線 下拉式清單中，選取  **Microsoft.BizTalk.DefaultPipelines.XMLTransmit**。</span><span class="sxs-lookup"><span data-stu-id="972bd-111">From the Send Pipeline drop-down list, select **Microsoft.BizTalk.DefaultPipelines.XMLTransmit**.</span></span>  
  
    5.  <span data-ttu-id="972bd-112">從**接收管線**下拉式清單中，選取 **[microsoft.biztalk.defaultpiplelines.xmlreceive]**。</span><span class="sxs-lookup"><span data-stu-id="972bd-112">From the **Receive Pipeline** drop-down list, select **Microsoft.BizTalk.DefaultPiplelines.XMLReceive**.</span></span>  
  
    6.  <span data-ttu-id="972bd-113">按一下**設定**以設定傳送埠。</span><span class="sxs-lookup"><span data-stu-id="972bd-113">Click **Configure** to configure the send port.</span></span>  
  
4.  <span data-ttu-id="972bd-114">在**TIBCO EMS 傳輸屬性**對話方塊方塊中，執行下列動作：</span><span class="sxs-lookup"><span data-stu-id="972bd-114">In the **TIBCO EMS Transport Properties** dialog box, do the following:</span></span>  
  
    1.  <span data-ttu-id="972bd-115">輸入**訊息處理**，**伺服器連線定義**，**交易支援**， **Username**，而**密碼**。</span><span class="sxs-lookup"><span data-stu-id="972bd-115">Enter **Message Handling**, **Server Connection Definition**, **Transaction Support**, **Username**, and the **password**.</span></span>  
  
         <span data-ttu-id="972bd-116">您不需要設定登入資訊。</span><span class="sxs-lookup"><span data-stu-id="972bd-116">You do not have to set the logon information.</span></span>  
  
    2.  <span data-ttu-id="972bd-117">在此清單中，選取您建立用來代表 TIBCO EMS 系統的分支機構應用程式。</span><span class="sxs-lookup"><span data-stu-id="972bd-117">In the list, select the affiliate application you created to represent the TIBCO EMS system.</span></span>  
  
    3.  <span data-ttu-id="972bd-118">如**使用 SSO**，選取**是**。</span><span class="sxs-lookup"><span data-stu-id="972bd-118">For **Use SSO**, select **Yes**.</span></span>  
  
    4.  <span data-ttu-id="972bd-119">按一下 **[確定]**。</span><span class="sxs-lookup"><span data-stu-id="972bd-119">Click **OK**.</span></span>  
  
5.  <span data-ttu-id="972bd-120">按一下 **[確定]**。</span><span class="sxs-lookup"><span data-stu-id="972bd-120">Click **OK**.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="972bd-121">另請參閱</span><span class="sxs-lookup"><span data-stu-id="972bd-121">See Also</span></span>  
  [<span data-ttu-id="972bd-122">建立 TIBCO Enterprise Message Service 傳送處理常式</span><span class="sxs-lookup"><span data-stu-id="972bd-122">Creating  TIBCO Enterprise Message Service Send Handlers</span></span>](../core/creating-tibco-enterprise-message-service-send-handlers.md)