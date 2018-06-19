---
redirect_url: /biztalk/core/adding-biztalk-adapter-for-jd-edwards-oneworld/
redirect_document_id: true
ROBOTS: NOINDEX
ms.openlocfilehash: d65b87fbcbdaf89289406ae6850b70c605123451
ms.sourcegitcommit: dd7c54feab783ae2f8fe75873363fe9ffc77cd66
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/07/2017
ms.locfileid: "24015566"
---
# <a name="how-to-create-send-ports-for-jd-edwards-oneworld"></a><span data-ttu-id="aef4c-101">如何建立 JD Edwards OneWorld 的傳送埠</span><span class="sxs-lookup"><span data-stu-id="aef4c-101">How to Create Send Ports for JD Edwards OneWorld</span></span>
<span data-ttu-id="aef4c-102">使用下列程序來建立傳送埠。</span><span class="sxs-lookup"><span data-stu-id="aef4c-102">Use the following procedure to create a send port.</span></span>  
  
### <a name="to-create-a-send-port"></a><span data-ttu-id="aef4c-103">建立傳送埠</span><span class="sxs-lookup"><span data-stu-id="aef4c-103">To create a send port</span></span>  
  
1.  <span data-ttu-id="aef4c-104">在 BizTalk Server 管理主控台中，展開**BizTalk Server 管理**，依序展開**BizTalk 群組**，依序展開**應用程式**，然後瀏覽至必要的應用程式。</span><span class="sxs-lookup"><span data-stu-id="aef4c-104">In the BizTalk Server Administration Console, expand **BizTalk Server Administration**, expand **BizTalk Group**, expand **Applications**, and then navigate to the required application.</span></span>  
  
2.  <span data-ttu-id="aef4c-105">以滑鼠右鍵按一下**傳送埠**，指向 **新增**，然後按一下 **靜態請求-回應傳送埠**。</span><span class="sxs-lookup"><span data-stu-id="aef4c-105">Right-click **Send Ports**, point to **New**, and then click **Static Solicit-Response Send Port**.</span></span>  
  
    > [!NOTE]
    >  <span data-ttu-id="aef4c-106">您也可以使用**靜態單向連接埠**。</span><span class="sxs-lookup"><span data-stu-id="aef4c-106">You can also use **Static One-Way Port**.</span></span>  
  
3.  <span data-ttu-id="aef4c-107">在**傳送埠屬性**對話方塊中，於**名稱**欄位中，輸入傳送埠名稱 (例如，輸入**SendToJDE**。)</span><span class="sxs-lookup"><span data-stu-id="aef4c-107">In the **Send Port Properties** dialog box, in the **Name** field, type a send port name (for example, type **SendToJDE**.)</span></span>  
  
4.  <span data-ttu-id="aef4c-108">在**類型**下拉式清單中，選取 **[jdeoneworld]**。</span><span class="sxs-lookup"><span data-stu-id="aef4c-108">In the **Type** drop-down list, select **JDEOneWorld**.</span></span>  
  
5.  <span data-ttu-id="aef4c-109">在**URI**下拉式清單中，選取傳送處理常式。</span><span class="sxs-lookup"><span data-stu-id="aef4c-109">In the **URI** drop-down list, select the send handler.</span></span>  
  
6.  <span data-ttu-id="aef4c-110">按一下 **[確定]**。</span><span class="sxs-lookup"><span data-stu-id="aef4c-110">Click **OK**.</span></span>  
  
