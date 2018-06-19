---
redirect_url: /biztalk/core/creating-tibco-rendezvous-send-handlers/
redirect_document_id: true
ROBOTS: NOINDEX
ms.openlocfilehash: 44da7839f0bee96db332dada214bdbc503067f56
ms.sourcegitcommit: dd7c54feab783ae2f8fe75873363fe9ffc77cd66
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/07/2017
ms.locfileid: "24013157"
---
# <a name="how-to-create-send-ports-for-tibco-rendezvous"></a><span data-ttu-id="aa523-101">如何為 TIBCO Rendezvous 建立傳送埠</span><span class="sxs-lookup"><span data-stu-id="aa523-101">How to Create Send Ports for TIBCO Rendezvous</span></span>
<span data-ttu-id="aa523-102">遵循下列步驟，使用 [!INCLUDE[btsVStudioNoVersion](../includes/btsvstudionoversion-md.md)] 來建立傳送埠。</span><span class="sxs-lookup"><span data-stu-id="aa523-102">Follow these steps to create a send port using [!INCLUDE[btsVStudioNoVersion](../includes/btsvstudionoversion-md.md)].</span></span>  
  
### <a name="to-create-a-send-port"></a><span data-ttu-id="aa523-103">建立傳送埠</span><span class="sxs-lookup"><span data-stu-id="aa523-103">To create a send port</span></span>  
  
1.  <span data-ttu-id="aa523-104">在 BizTalk Server 管理主控台中，依序展開**BizTalk Server 管理**，依序展開**BizTalk 群組**，依序展開**應用程式**，然後展開 所需應用程式。</span><span class="sxs-lookup"><span data-stu-id="aa523-104">In the BizTalk Server Administration Console, expand **BizTalk Server Administration**, expand **BizTalk Group**, expand **Applications**, and then expand the desired application.</span></span>  
  
2.  <span data-ttu-id="aa523-105">以滑鼠右鍵按一下**傳送埠**，指向 **新增**，然後按一下 **靜態請求-回應傳送埠**。</span><span class="sxs-lookup"><span data-stu-id="aa523-105">Right-click **Send Ports**, point to **New**, and then click **Static Solicit-Response Send Port**.</span></span>  
  
3.  <span data-ttu-id="aa523-106">在**傳送埠屬性**對話方塊方塊中，執行下列動作：</span><span class="sxs-lookup"><span data-stu-id="aa523-106">In the **Send Port Properties** dialog box, do the following:</span></span>  
  
    1.  <span data-ttu-id="aa523-107">輸入傳送埠名稱，例如`SendToTIBCORV`。</span><span class="sxs-lookup"><span data-stu-id="aa523-107">Type a name for the send port, for example, `SendToTIBCORV`.</span></span>  
  
    2.  <span data-ttu-id="aa523-108">從**類型**下拉式清單中，選取**TIBCO Rendezvous**。</span><span class="sxs-lookup"><span data-stu-id="aa523-108">From the **Type** drop-down list, select **TIBCO Rendezvous**.</span></span>  
  
    3.  <span data-ttu-id="aa523-109">從**傳送處理常式**下拉式清單中，選取 URI。</span><span class="sxs-lookup"><span data-stu-id="aa523-109">From the **Send handler** drop-down list, select the URI.</span></span>  
  
    4.  <span data-ttu-id="aa523-110">從**傳送管線**下拉式清單中，選取**Microsoft.BizTalk.DefaultPipelines.XMLTransmit**。</span><span class="sxs-lookup"><span data-stu-id="aa523-110">From the **Send Pipeline** drop-down list, select **Microsoft.BizTalk.DefaultPipelines.XMLTransmit**.</span></span> <span data-ttu-id="aa523-111">從**接收管線**下拉式清單中，選取 **[microsoft.biztalk.defaultpiplelines.xmlreceive]**。</span><span class="sxs-lookup"><span data-stu-id="aa523-111">From the **Receive Pipeline** drop-down list, select **Microsoft.BizTalk.DefaultPiplelines.XMLReceive**.</span></span>  
  
    6.  <span data-ttu-id="aa523-112">按一下**設定**以設定傳送埠。</span><span class="sxs-lookup"><span data-stu-id="aa523-112">Click **Configure** to configure the send port.</span></span>  
  
4.  <span data-ttu-id="aa523-113">在**TIBCO Rendezvous 傳輸屬性**對話方塊方塊中，執行下列動作：</span><span class="sxs-lookup"><span data-stu-id="aa523-113">In the **TIBCO Rendezvous Transport Properties** dialog box, do the following:</span></span>  
  
    1.  <span data-ttu-id="aa523-114">輸入屬性。</span><span class="sxs-lookup"><span data-stu-id="aa523-114">Enter the properties.</span></span>  
  
         <span data-ttu-id="aa523-115">您不需要設定登入資訊。</span><span class="sxs-lookup"><span data-stu-id="aa523-115">You do not have to set the logon information.</span></span>  
  
    2.  <span data-ttu-id="aa523-116">在此清單中，選取您建立來代表 TIBCO Rendezvous 系統的 SSO 分支機構應用程式。</span><span class="sxs-lookup"><span data-stu-id="aa523-116">In the list, select the SSO affiliate application you created to represent the TIBCO Rendezvous system.</span></span>  
  
    3.  <span data-ttu-id="aa523-117">如**使用 SSO**，選取**是**。</span><span class="sxs-lookup"><span data-stu-id="aa523-117">For **Use SSO**, select **Yes**.</span></span>  
  
    4.  <span data-ttu-id="aa523-118">按一下 **[確定]**。</span><span class="sxs-lookup"><span data-stu-id="aa523-118">Click **OK**.</span></span>  
  
5.  <span data-ttu-id="aa523-119">按一下 **[確定]**。</span><span class="sxs-lookup"><span data-stu-id="aa523-119">Click **OK**.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="aa523-120">另請參閱</span><span class="sxs-lookup"><span data-stu-id="aa523-120">See Also</span></span>  
 [<span data-ttu-id="aa523-121">建立 TIBCO Rendezvous 傳送處理常式</span><span class="sxs-lookup"><span data-stu-id="aa523-121">Creating TIBCO Rendezvous Send Handlers</span></span>](../core/creating-tibco-rendezvous-send-handlers.md)