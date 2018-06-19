---
redirect_url: /biztalk/core/creating-peoplesoft-send-handlers/
redirect_document_id: true
ROBOTS: NOINDEX
ms.openlocfilehash: ec518c16383d847bf13706a6469b038b447c1543
ms.sourcegitcommit: dd7c54feab783ae2f8fe75873363fe9ffc77cd66
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/07/2017
ms.locfileid: "24013653"
---
# <a name="how-to-create-send-ports-for-peoplesoft-enterprise"></a><span data-ttu-id="faeeb-101">如何建立 PeopleSoft Enterprise 的傳送埠</span><span class="sxs-lookup"><span data-stu-id="faeeb-101">How to Create Send Ports for PeopleSoft Enterprise</span></span>
<span data-ttu-id="faeeb-102">請依照下列步驟使用 BizTalk Server 管理主控台建立傳送埠。</span><span class="sxs-lookup"><span data-stu-id="faeeb-102">Follow these steps to create a send port using BizTalk Server Administration Console.</span></span>  
  
## <a name="creating-a-send-port"></a><span data-ttu-id="faeeb-103">建立傳送埠</span><span class="sxs-lookup"><span data-stu-id="faeeb-103">Creating a Send Port</span></span>  
  
#### <a name="to-create-a-send-port"></a><span data-ttu-id="faeeb-104">建立傳送埠</span><span class="sxs-lookup"><span data-stu-id="faeeb-104">To create a send port</span></span>  
  
1.  <span data-ttu-id="faeeb-105">在 BizTalk Server 管理主控台中，依序展開**BizTalk Server 管理**，依序展開**BizTalk 群組**，依序展開**應用程式**，然後展開 所需應用程式。</span><span class="sxs-lookup"><span data-stu-id="faeeb-105">In the BizTalk Server Administration Console, expand **BizTalk Server Administration**, expand **BizTalk Group**, expand **Applications**, and then expand the desired application.</span></span>  
  
2.  <span data-ttu-id="faeeb-106">以滑鼠右鍵按一下**傳送埠**，指向 **新增**，然後按一下 **靜態請求-回應傳送埠**。</span><span class="sxs-lookup"><span data-stu-id="faeeb-106">Right-click **Send Ports**, point to **New**, and then click **Static Solicit-Response Send Port**.</span></span>  
  
3.  <span data-ttu-id="faeeb-107">在**傳送埠屬性**對話方塊方塊中，執行下列動作：</span><span class="sxs-lookup"><span data-stu-id="faeeb-107">In the **Send Port Properties** dialog box, do the following:</span></span>  
  
    1.  <span data-ttu-id="faeeb-108">輸入傳送埠名稱，例如`SSOSendToPeopleSoft`。</span><span class="sxs-lookup"><span data-stu-id="faeeb-108">Type a name for the send port, for example, `SSOSendToPeopleSoft`.</span></span>  
  
    2.  <span data-ttu-id="faeeb-109">從**類型**下拉式清單中，選取**PeopleSoft**。</span><span class="sxs-lookup"><span data-stu-id="faeeb-109">From the **Type** drop-down list, select **PeopleSoft**.</span></span>  
  
    3.  <span data-ttu-id="faeeb-110">從**傳送處理常式**下拉式清單中，選取 URI。</span><span class="sxs-lookup"><span data-stu-id="faeeb-110">From the **Send handler** drop-down list, select the URI.</span></span>  
  
    4.  <span data-ttu-id="faeeb-111">從 傳送管線 下拉式清單中，選取  **Microsoft.BizTalk.DefaultPipelines.XMLTransmit**。</span><span class="sxs-lookup"><span data-stu-id="faeeb-111">From the Send Pipeline drop-down list, select **Microsoft.BizTalk.DefaultPipelines.XMLTransmit**.</span></span>  
  
    5.  <span data-ttu-id="faeeb-112">從**接收管線**下拉式清單中，選取 **[microsoft.biztalk.defaultpiplelines.xmlreceive]**。</span><span class="sxs-lookup"><span data-stu-id="faeeb-112">From the **Receive Pipeline** drop-down list, select **Microsoft.BizTalk.DefaultPiplelines.XMLReceive**.</span></span>  
  
    6.  <span data-ttu-id="faeeb-113">按一下**設定**以設定傳送埠。</span><span class="sxs-lookup"><span data-stu-id="faeeb-113">Click **Configure** to configure the send port.</span></span>  
  
4.  <span data-ttu-id="faeeb-114">在**PeopleSoft 傳輸屬性**對話方塊方塊中，執行下列動作：</span><span class="sxs-lookup"><span data-stu-id="faeeb-114">In the **PeopleSoft Transport Properties** dialog box, do the following:</span></span>  
  
    1.  <span data-ttu-id="faeeb-115">展開**配接器必要屬性**，並輸入**應用程式伺服器路徑**， **JAVA_HOME**，**使用者名**， **密碼**，以及 Jar 檔案，以連接至 Peoplesoft 系統。</span><span class="sxs-lookup"><span data-stu-id="faeeb-115">Expand **Adapter Required Properties**, and enter **Application Server Path**, **JAVA_HOME**, **user name**, **password**, and the Jar file for connecting into the Peoplesoft system.</span></span>  
  
         <span data-ttu-id="faeeb-116">您不需要設定登入資訊。</span><span class="sxs-lookup"><span data-stu-id="faeeb-116">You do not have to set the logon information.</span></span>  
  
    2.  <span data-ttu-id="faeeb-117">在此清單中，選取您建立用來代表 PeopleSoft 系統的 SSO 分支機構應用程式。</span><span class="sxs-lookup"><span data-stu-id="faeeb-117">In the list, select the SSO affiliate application you created to represent the PeopleSoft system.</span></span>  
  
    3.  <span data-ttu-id="faeeb-118">如**使用 SSO**，選取**是**。</span><span class="sxs-lookup"><span data-stu-id="faeeb-118">For **Use SSO**, select **Yes**.</span></span>  
  
    4.  <span data-ttu-id="faeeb-119">按一下 **[確定]**。</span><span class="sxs-lookup"><span data-stu-id="faeeb-119">Click **OK**.</span></span>  
  
5.  <span data-ttu-id="faeeb-120">按一下 **[確定]**。</span><span class="sxs-lookup"><span data-stu-id="faeeb-120">Click **OK**.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="faeeb-121">另請參閱</span><span class="sxs-lookup"><span data-stu-id="faeeb-121">See Also</span></span>  
 [<span data-ttu-id="faeeb-122">建立 PeopleSoft 傳送處理常式</span><span class="sxs-lookup"><span data-stu-id="faeeb-122">Creating PeopleSoft Send Handlers</span></span>](../core/creating-peoplesoft-send-handlers.md)