---
redirect_url: /biztalk/core/adding-biztalk-adapter-for-jd-edwards-oneworld/
redirect_document_id: true
ROBOTS: NOINDEX
ms.openlocfilehash: e075bfbfdb082887ea746ee81e24a5176d9ad98d
ms.sourcegitcommit: 266308ec5c6a9d8d80ff298ee6051b4843c5d626
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/27/2018
ms.locfileid: "36976599"
---
# <a name="adding-the-adapter-to-biztalk-server"></a><span data-ttu-id="7e525-101">新增配接器至 BizTalk Server</span><span class="sxs-lookup"><span data-stu-id="7e525-101">Adding the Adapter to BizTalk Server</span></span>
<span data-ttu-id="7e525-102">Microsoft BizTalk Adapter for JD Edwards OneWorld 包含 [接收處理常式] 和 [傳送處理常式] 資料夾。</span><span class="sxs-lookup"><span data-stu-id="7e525-102">Microsoft BizTalk Adapter for JD Edwards OneWorld contains both the Receive Handler and Send Handler folders.</span></span> <span data-ttu-id="7e525-103">[傳送處理常式] 資料夾包含 BizTalkServerApplication。</span><span class="sxs-lookup"><span data-stu-id="7e525-103">The Send Handler folder contains BizTalkServerApplication.</span></span> <span data-ttu-id="7e525-104">BizTalk Adapter for JD Edwards OneWorld 是可建立的；它會在與 BizTalk Server 相同的程序中執行，而且不會在外掛式主控件程序中執行。</span><span class="sxs-lookup"><span data-stu-id="7e525-104">BizTalk Adapter for JD Edwards OneWorld is creatable; it runs in-process with BizTalk Server and does not run in an isolated host process.</span></span>  
  
 <span data-ttu-id="7e525-105">請使用下列程序將此配接器新增至 BizTalk Server。</span><span class="sxs-lookup"><span data-stu-id="7e525-105">Use the following procedure to add the adapter to BizTalk Server.</span></span>  
  
### <a name="to-add-biztalk-adapter-for-jd-edwards-oneworld"></a><span data-ttu-id="7e525-106">若要新增 BizTalk Adapter for JD Edwards OneWorld</span><span class="sxs-lookup"><span data-stu-id="7e525-106">To add BizTalk Adapter for JD Edwards OneWorld</span></span>  
  
1. <span data-ttu-id="7e525-107">在上**開始**功能表上，指向**Program Files**，指向[!INCLUDE[btsBizTalkServer2006r3ui](../includes/btsbiztalkserver2006r3ui-md.md)]，然後按一下  **BizTalk Server 管理**啟動[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]管理主控台。</span><span class="sxs-lookup"><span data-stu-id="7e525-107">On the **Start** menu, point to **Program Files**, point to [!INCLUDE[btsBizTalkServer2006r3ui](../includes/btsbiztalkserver2006r3ui-md.md)], and then click **BizTalk Server Administration** to start the [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] Administration Console.</span></span>  
  
2. <span data-ttu-id="7e525-108">依序展開**BizTalk Server 管理**，展開**BizTalk 群組**，然後展開**平台設定**。</span><span class="sxs-lookup"><span data-stu-id="7e525-108">Expand **BizTalk Server Administration**, expand **BizTalk Group**, and then expand **Platform Settings**.</span></span>  
  
3. <span data-ttu-id="7e525-109">以滑鼠右鍵按一下**配接器**，指向**新增**，然後按一下**配接器**。</span><span class="sxs-lookup"><span data-stu-id="7e525-109">Right-click **Adapters**, point to **New**, and click **Adapter**.</span></span>  
  
4. <span data-ttu-id="7e525-110">在 [**配接器屬性**] 對話方塊中，輸入配接器的名稱。</span><span class="sxs-lookup"><span data-stu-id="7e525-110">In the **Adapter Properties** dialog box, type a name for the adapter.</span></span> <span data-ttu-id="7e525-111">例如，JDEdwards。</span><span class="sxs-lookup"><span data-stu-id="7e525-111">For example, JDEdwards.</span></span>  
  
5. <span data-ttu-id="7e525-112">選取  **jdeoneworld**從**配接器**清單，然後再按**確定**。</span><span class="sxs-lookup"><span data-stu-id="7e525-112">Select **JDEOneWorld** from the **Adapter** list, and then click **OK**.</span></span>  
  
## <a name="verifying-the-adapter"></a><span data-ttu-id="7e525-113">確認配接器</span><span class="sxs-lookup"><span data-stu-id="7e525-113">Verifying the Adapter</span></span>  
 <span data-ttu-id="7e525-114">在 [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]管理主控台中，您可以確認配接器藉由查看正確運作**邏輯系統**視窗。</span><span class="sxs-lookup"><span data-stu-id="7e525-114">In the [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] Administration Console, you can verify that the adapter is functioning correctly by looking at the **Logical System** window.</span></span> <span data-ttu-id="7e525-115">在初次安裝時，因為您尚未建立與伺服器系統的連線，也尚未建立任何邏輯系統，所以這個視窗會是空的。</span><span class="sxs-lookup"><span data-stu-id="7e525-115">On initial installation, this window is empty because you have not yet established a connection to the server system, nor have you created any logical systems.</span></span>  
  
#### <a name="to-verify-that-the-adapter-is-running-correctly"></a><span data-ttu-id="7e525-116">若要確認配接器已正確執行</span><span class="sxs-lookup"><span data-stu-id="7e525-116">To verify that the adapter is running correctly</span></span>  
  
1. <span data-ttu-id="7e525-117">在[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]管理主控台中，展開**BizTalk 群組**，展開**平台設定**，依序展開**配接器**，然後選取  **[Jdeoneworld]**。</span><span class="sxs-lookup"><span data-stu-id="7e525-117">In the [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] Administration console, expand **BizTalk Group**, expand **Platform Settings**, expand **Adapters**, and then select **JDEOneWorld**.</span></span>  
  
2. <span data-ttu-id="7e525-118">在 [詳細資料] 窗格中，以滑鼠右鍵按一下**BizTalkServerApplication**，然後選取**屬性**。</span><span class="sxs-lookup"><span data-stu-id="7e525-118">In the details pane, right-click **BizTalkServerApplication**, and select **Properties**.</span></span>  
  
3. <span data-ttu-id="7e525-119">按一下 **[屬性]** 索引標籤。</span><span class="sxs-lookup"><span data-stu-id="7e525-119">Click the **Properties** tab.</span></span>  
  
4. <span data-ttu-id="7e525-120">設定 SQL 連線參數。</span><span class="sxs-lookup"><span data-stu-id="7e525-120">Set the SQL Connection parameters.</span></span>  
  
   -   <span data-ttu-id="7e525-121">**定義 SQL 資料庫參數-** 的 SQL Server 名稱和資料庫是您在安裝期間設定。</span><span class="sxs-lookup"><span data-stu-id="7e525-121">**Define SQL Database Parameters -** The SQL Server Name and Database are those you set at installation.</span></span> <span data-ttu-id="7e525-122">您可以在這個文字區域中重新定義此配接器的伺服器與資料庫。</span><span class="sxs-lookup"><span data-stu-id="7e525-122">This is the text area that you can redefine the server and database for this adapter.</span></span>  
  
5. <span data-ttu-id="7e525-123">按一下 **關閉**以結束**邏輯系統**視窗。</span><span class="sxs-lookup"><span data-stu-id="7e525-123">Click **Close** to exit the **Logical System** window.</span></span>  
  
    <span data-ttu-id="7e525-124">下一個步驟是要使用 [!INCLUDE[btsVStudioNoVersion](../includes/btsvstudionoversion-md.md)] 來新增邏輯系統。</span><span class="sxs-lookup"><span data-stu-id="7e525-124">Your next step is to add a logical system using [!INCLUDE[btsVStudioNoVersion](../includes/btsvstudionoversion-md.md)].</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="7e525-125">另請參閱</span><span class="sxs-lookup"><span data-stu-id="7e525-125">See Also</span></span>  
 <span data-ttu-id="7e525-126">[規劃與架構](../core/planning-and-architecture17.md) </span><span class="sxs-lookup"><span data-stu-id="7e525-126">[Planning and Architecture](../core/planning-and-architecture17.md) </span></span>  
 <span data-ttu-id="7e525-127">[BizTalk Adapter for JD Edwards OneWorld 中的安全性](../core/security-in-biztalk-adapter-for-jd-edwards-oneworld.md) </span><span class="sxs-lookup"><span data-stu-id="7e525-127">[Security in BizTalk Adapter for JD Edwards OneWorld](../core/security-in-biztalk-adapter-for-jd-edwards-oneworld.md) </span></span>  
 [<span data-ttu-id="7e525-128">新增 BizTalk Adapter for JD Edwards OneWorld</span><span class="sxs-lookup"><span data-stu-id="7e525-128">Adding BizTalk Adapter for JD Edwards OneWorld</span></span>](../core/adding-biztalk-adapter-for-jd-edwards-oneworld.md)