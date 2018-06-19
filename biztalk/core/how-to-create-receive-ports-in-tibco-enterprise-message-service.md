---
redirect_url: /biztalk/core/creating-tibco-enterprise-message-service-receive-handlers/
redirect_document_id: true
ROBOTS: NOINDEX
ms.openlocfilehash: e31246cf90f42206de6a22fcc32338fcb2936db3
ms.sourcegitcommit: dd7c54feab783ae2f8fe75873363fe9ffc77cd66
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/07/2017
ms.locfileid: "24014885"
---
# <a name="how-to-create-receive-ports-in-tibco-enterprise-message-service"></a><span data-ttu-id="caa0a-101">如何在 TIBCO Enterprise Message Service 中建立接收埠</span><span class="sxs-lookup"><span data-stu-id="caa0a-101">How to Create Receive Ports in TIBCO Enterprise Message Service</span></span>
<span data-ttu-id="caa0a-102">請遵循下列步驟來建立接收埠。</span><span class="sxs-lookup"><span data-stu-id="caa0a-102">Follow these steps to create a receive port.</span></span>  
  
### <a name="to-create-a-receive-port"></a><span data-ttu-id="caa0a-103">建立接收埠</span><span class="sxs-lookup"><span data-stu-id="caa0a-103">To create a receive port</span></span>  
  
1.  <span data-ttu-id="caa0a-104">在 BizTalk Server 管理主控台中，依序展開**BizTalk Server 管理**，依序展開**BizTalk 群組**，依序展開**應用程式**，然後展開 所需應用程式。</span><span class="sxs-lookup"><span data-stu-id="caa0a-104">In the BizTalk Server Administration Console, expand **BizTalk Server Administration**, expand **BizTalk Group**, expand **Applications**, and then expand the desired application.</span></span>  
  
2.  <span data-ttu-id="caa0a-105">以滑鼠右鍵按一下**接收埠**，指向 **新增**，然後按一下 **單向接收埠**。</span><span class="sxs-lookup"><span data-stu-id="caa0a-105">Right-click **Receive Ports**, point to **New**, and then click **One-way Receive Ports**.</span></span>  
  
3.  <span data-ttu-id="caa0a-106">在**接收埠屬性**視窗，請在**一般**頁面上，執行下列動作：</span><span class="sxs-lookup"><span data-stu-id="caa0a-106">In the **Receive Port Properties** window, on the **General** page, do the following:</span></span>  
  
    1.  <span data-ttu-id="caa0a-107">在**名稱**欄位中，輸入`ReceiveFromTIBCOEMS`。</span><span class="sxs-lookup"><span data-stu-id="caa0a-107">In the **Name** field, type `ReceiveFromTIBCOEMS`.</span></span>  
  
    2.  <span data-ttu-id="caa0a-108">在**驗證**群組方塊中，指定使用驗證時，如何處理的訊息。</span><span class="sxs-lookup"><span data-stu-id="caa0a-108">In the **Authentication** group box, specify how messages are handled when using authentication.</span></span>  
  
    3.  <span data-ttu-id="caa0a-109">選取**啟用的路由失敗訊息**核取方塊。</span><span class="sxs-lookup"><span data-stu-id="caa0a-109">Select the **Enable routing for failed messages** checkbox.</span></span>  
  
4.  <span data-ttu-id="caa0a-110">在**接收位置**頁面上，執行下列動作：</span><span class="sxs-lookup"><span data-stu-id="caa0a-110">On the **Receive Locations** page, do the following:</span></span>  
  
    1.  <span data-ttu-id="caa0a-111">按一下 **[新增]**。</span><span class="sxs-lookup"><span data-stu-id="caa0a-111">Click **New**.</span></span>  
  
    2.  <span data-ttu-id="caa0a-112">在**接收位置**視窗，請在**一般**頁面上，輸入**名稱**接收位置。</span><span class="sxs-lookup"><span data-stu-id="caa0a-112">In the **Receive Locations** window, on the **General** page, type the **Name** of the receive location.</span></span>  
  
    3.  <span data-ttu-id="caa0a-113">從**類型**下拉式清單中，選取傳輸類型，以及從**接收處理常式**下拉式清單中，選取傳輸位址。</span><span class="sxs-lookup"><span data-stu-id="caa0a-113">From the **Type** drop-down list, select the transport type, and from the **Receive handler** drop-down list, select the transport address.</span></span>  
  
    4.  <span data-ttu-id="caa0a-114">從**接收管線**下拉式清單中，選取接收管線。</span><span class="sxs-lookup"><span data-stu-id="caa0a-114">From the **Receive pipeline** drop-down list, select the receive pipeline.</span></span>  
  
    5.  <span data-ttu-id="caa0a-115">在**排程**頁面上，選取**開始日期**和**結束日期**限制接收文件。</span><span class="sxs-lookup"><span data-stu-id="caa0a-115">On the **Schedule** page, select the **Start date** and the **End date** to restrict receiving documents.</span></span>  
  
    6.  <span data-ttu-id="caa0a-116">選取**啟用服務窗口**核取方塊。</span><span class="sxs-lookup"><span data-stu-id="caa0a-116">Select the **Enable service window** checkbox.</span></span>  
  
    7.  <span data-ttu-id="caa0a-117">按一下 **[確定]**。</span><span class="sxs-lookup"><span data-stu-id="caa0a-117">Click **OK**.</span></span>  
  
5.  <span data-ttu-id="caa0a-118">在**輸入對應**頁面上，選取輸入的對應轉換文件上選取的連接埠。</span><span class="sxs-lookup"><span data-stu-id="caa0a-118">On the **Inbound Maps** page, select the inbound maps for transforming documents on the selected port.</span></span>  
  
6.  <span data-ttu-id="caa0a-119">在**追蹤**頁面上，選取所需的追蹤訊息內文和追蹤訊息屬性。</span><span class="sxs-lookup"><span data-stu-id="caa0a-119">On the **Tracking** page, select the desired tracking message bodies and tracking message properties.</span></span>  
  
7.  <span data-ttu-id="caa0a-120">按一下 **[確定]**。</span><span class="sxs-lookup"><span data-stu-id="caa0a-120">Click **OK**.</span></span>  
  
