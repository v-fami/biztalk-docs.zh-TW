---
redirect_url: /biztalk/core/adding-biztalk-adapter-for-jd-edwards-enterpriseone/
redirect_document_id: true
ROBOTS: NOINDEX
ms.openlocfilehash: fe877aa8c7b76a638df93a073eed0cf26f71a609
ms.sourcegitcommit: dd7c54feab783ae2f8fe75873363fe9ffc77cd66
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/07/2017
ms.locfileid: "24013277"
---
# <a name="how-to-create-send-ports-for-jd-edwards-enterpriseone"></a><span data-ttu-id="26f20-101">如何建立 JD Edwards EnterpriseOne 的傳送埠</span><span class="sxs-lookup"><span data-stu-id="26f20-101">How to Create Send Ports for JD Edwards EnterpriseOne</span></span>
<span data-ttu-id="26f20-102">使用 [!INCLUDE[btsVStudioNoVersion](../includes/btsvstudionoversion-md.md)] 建立傳送埠。</span><span class="sxs-lookup"><span data-stu-id="26f20-102">Using [!INCLUDE[btsVStudioNoVersion](../includes/btsvstudionoversion-md.md)], create a send port.</span></span>  
  
### <a name="to-create-a-send-port"></a><span data-ttu-id="26f20-103">建立傳送埠</span><span class="sxs-lookup"><span data-stu-id="26f20-103">To create a send port</span></span>  
  
1.  <span data-ttu-id="26f20-104">按一下**啟動**，指向 **所有程式**，指向  **Microsoft BizTalk Server**，然後按一下  **BizTalk Server 管理**。</span><span class="sxs-lookup"><span data-stu-id="26f20-104">Click **Start**, point to **All Programs**, point to **Microsoft BizTalk Server**, and then click **BizTalk Server Administration**.</span></span>  
  
2.  <span data-ttu-id="26f20-105">在 BizTalk Server 管理主控台中，展開  **BizTalk Server 管理**，依序展開**BizTalk 群組**，並展開**應用程式**，然後展開您要建立傳送埠的應用程式。</span><span class="sxs-lookup"><span data-stu-id="26f20-105">In the BizTalk Server Administration console, expand **BizTalk Server Administration**, expand **BizTalk Group**, and expand **Applications**, and then expand the application for which you want to create a send port.</span></span>  
  
3.  <span data-ttu-id="26f20-106">以滑鼠右鍵按一下**傳送埠**按一下**新增**，然後按一下 **靜態請求-回應連接埠**。</span><span class="sxs-lookup"><span data-stu-id="26f20-106">Right-click **Send Ports** and click **New**, and then click **Static Solicit-Response Port**.</span></span>  
  
4.  <span data-ttu-id="26f20-107">在**傳送埠屬性**對話方塊方塊中，執行下列動作：</span><span class="sxs-lookup"><span data-stu-id="26f20-107">In the **Send Port Properties** dialog box, do the following:</span></span>  
  
    -   <span data-ttu-id="26f20-108">在**名稱**方塊中，輸入傳送埠名稱 (例如， `SendToJDE`)。</span><span class="sxs-lookup"><span data-stu-id="26f20-108">In the **Name** box, type a send port name (for example, `SendToJDE`).</span></span>  
  
    -   <span data-ttu-id="26f20-109">從**類型**下拉式清單中，選取**JDEdwards**。</span><span class="sxs-lookup"><span data-stu-id="26f20-109">From the **Type** drop-down list, select **JDEdwards**.</span></span>  
  
    -   <span data-ttu-id="26f20-110">從**傳送處理常式**下拉式清單中，選取傳送處理常式位址。</span><span class="sxs-lookup"><span data-stu-id="26f20-110">From the **Send handler** drop-down list, select the send handler address.</span></span>  
  
5.  <span data-ttu-id="26f20-111">按一下 **[確定]**。</span><span class="sxs-lookup"><span data-stu-id="26f20-111">Click **OK**.</span></span>  
  
