---
title: "將配接器新增至 BizTalk Server |Microsoft 文件"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- adapters [JD Edwards OneWorld adapters], installing
- installing, JD Edwards OneWorld adapters
- JD Edwards OneWorld adapters, installing
ms.assetid: e2018856-1943-48e9-b43f-7d527880e4bd
caps.latest.revision: "12"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 63de8824112c9891c6d67eee424a84dd4968976c
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/20/2017
---
# <a name="adding-the-adapter-to-biztalk-server"></a><span data-ttu-id="50ffa-102">將配接器新增至 BizTalk Server</span><span class="sxs-lookup"><span data-stu-id="50ffa-102">Adding the Adapter to BizTalk Server</span></span>
<span data-ttu-id="50ffa-103">Microsoft BizTalk Adapter for JD Edwards OneWorld 包含 [接收處理常式] 和 [傳送處理常式] 資料夾。</span><span class="sxs-lookup"><span data-stu-id="50ffa-103">Microsoft BizTalk Adapter for JD Edwards OneWorld contains both the Receive Handler and Send Handler folders.</span></span> <span data-ttu-id="50ffa-104">[傳送處理常式] 資料夾包含 BizTalkServerApplication。</span><span class="sxs-lookup"><span data-stu-id="50ffa-104">The Send Handler folder contains BizTalkServerApplication.</span></span> <span data-ttu-id="50ffa-105">BizTalk Adapter for JD Edwards OneWorld 是可建立的；它會在與 BizTalk Server 相同的程序中執行，而且不會在外掛式主控件程序中執行。</span><span class="sxs-lookup"><span data-stu-id="50ffa-105">BizTalk Adapter for JD Edwards OneWorld is creatable; it runs in-process with BizTalk Server and does not run in an isolated host process.</span></span>  
  
 <span data-ttu-id="50ffa-106">請使用下列程序將此配接器新增至 BizTalk Server。</span><span class="sxs-lookup"><span data-stu-id="50ffa-106">Use the following procedure to add the adapter to BizTalk Server.</span></span>  
  
### <a name="to-add-biztalk-adapter-for-jd-edwards-oneworld"></a><span data-ttu-id="50ffa-107">若要新增 BizTalk Adapter for JD Edwards OneWorld</span><span class="sxs-lookup"><span data-stu-id="50ffa-107">To add BizTalk Adapter for JD Edwards OneWorld</span></span>  
  
1.  <span data-ttu-id="50ffa-108">上**啟動**功能表上，指向**Program Files**，指向  [!INCLUDE[btsBizTalkServer2006r3ui](../includes/btsbiztalkserver2006r3ui-md.md)]，然後按一下  **BizTalk Server 管理**啟動[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]管理主控台。</span><span class="sxs-lookup"><span data-stu-id="50ffa-108">On the **Start** menu, point to **Program Files**, point to [!INCLUDE[btsBizTalkServer2006r3ui](../includes/btsbiztalkserver2006r3ui-md.md)], and then click **BizTalk Server Administration** to start the [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] Administration Console.</span></span>  
  
2.  <span data-ttu-id="50ffa-109">展開**BizTalk Server 管理**，依序展開**BizTalk 群組**，然後展開**平台設定**。</span><span class="sxs-lookup"><span data-stu-id="50ffa-109">Expand **BizTalk Server Administration**, expand **BizTalk Group**, and then expand **Platform Settings**.</span></span>  
  
3.  <span data-ttu-id="50ffa-110">以滑鼠右鍵按一下**配接器**，指向 **新增**，然後按一下**配接器**。</span><span class="sxs-lookup"><span data-stu-id="50ffa-110">Right-click **Adapters**, point to **New**, and click **Adapter**.</span></span>  
  
4.  <span data-ttu-id="50ffa-111">在**配接器屬性**對話方塊中，輸入配接器的名稱。</span><span class="sxs-lookup"><span data-stu-id="50ffa-111">In the **Adapter Properties** dialog box, type a name for the adapter.</span></span> <span data-ttu-id="50ffa-112">例如，JDEdwards。</span><span class="sxs-lookup"><span data-stu-id="50ffa-112">For example, JDEdwards.</span></span>  
  
5.  <span data-ttu-id="50ffa-113">選取**[jdeoneworld]**從**配接器**清單，然後再按**確定**。</span><span class="sxs-lookup"><span data-stu-id="50ffa-113">Select **JDEOneWorld** from the **Adapter** list, and then click **OK**.</span></span>  
  
## <a name="verifying-the-adapter"></a><span data-ttu-id="50ffa-114">確認配接器</span><span class="sxs-lookup"><span data-stu-id="50ffa-114">Verifying the Adapter</span></span>  
 <span data-ttu-id="50ffa-115">在[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]管理主控台中，您可以確認配接器會正確運作，藉由查看**邏輯系統**視窗。</span><span class="sxs-lookup"><span data-stu-id="50ffa-115">In the [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] Administration Console, you can verify that the adapter is functioning correctly by looking at the **Logical System** window.</span></span> <span data-ttu-id="50ffa-116">在初次安裝時，因為您尚未建立與伺服器系統的連線，也尚未建立任何邏輯系統，所以這個視窗會是空的。</span><span class="sxs-lookup"><span data-stu-id="50ffa-116">On initial installation, this window is empty because you have not yet established a connection to the server system, nor have you created any logical systems.</span></span>  
  
#### <a name="to-verify-that-the-adapter-is-running-correctly"></a><span data-ttu-id="50ffa-117">若要確認配接器已正確執行</span><span class="sxs-lookup"><span data-stu-id="50ffa-117">To verify that the adapter is running correctly</span></span>  
  
1.  <span data-ttu-id="50ffa-118">在[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]管理主控台中，展開**BizTalk 群組**，展開**平台設定**，依序展開**配接器**，然後選取**[Jdeoneworld]**。</span><span class="sxs-lookup"><span data-stu-id="50ffa-118">In the [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] Administration console, expand **BizTalk Group**, expand **Platform Settings**, expand **Adapters**, and then select **JDEOneWorld**.</span></span>  
  
2.  <span data-ttu-id="50ffa-119">在詳細資料窗格中，以滑鼠右鍵按一下**BizTalkServerApplication**，然後選取**屬性**。</span><span class="sxs-lookup"><span data-stu-id="50ffa-119">In the details pane, right-click **BizTalkServerApplication**, and select **Properties**.</span></span>  
  
3.  <span data-ttu-id="50ffa-120">按一下 **[屬性]** 索引標籤。</span><span class="sxs-lookup"><span data-stu-id="50ffa-120">Click the **Properties** tab.</span></span>  
  
4.  <span data-ttu-id="50ffa-121">設定 SQL 連線參數。</span><span class="sxs-lookup"><span data-stu-id="50ffa-121">Set the SQL Connection parameters.</span></span>  
  
    -   <span data-ttu-id="50ffa-122">**定義 SQL 資料庫參數-** SQL Server 名稱與資料庫就是您在安裝期間設定。</span><span class="sxs-lookup"><span data-stu-id="50ffa-122">**Define SQL Database Parameters -** The SQL Server Name and Database are those you set at installation.</span></span> <span data-ttu-id="50ffa-123">您可以在這個文字區域中重新定義此配接器的伺服器與資料庫。</span><span class="sxs-lookup"><span data-stu-id="50ffa-123">This is the text area that you can redefine the server and database for this adapter.</span></span>  
  
5.  <span data-ttu-id="50ffa-124">按一下**關閉**結束**邏輯系統**視窗。</span><span class="sxs-lookup"><span data-stu-id="50ffa-124">Click **Close** to exit the **Logical System** window.</span></span>  
  
     <span data-ttu-id="50ffa-125">下一個步驟是要使用 [!INCLUDE[btsVStudioNoVersion](../includes/btsvstudionoversion-md.md)] 來新增邏輯系統。</span><span class="sxs-lookup"><span data-stu-id="50ffa-125">Your next step is to add a logical system using [!INCLUDE[btsVStudioNoVersion](../includes/btsvstudionoversion-md.md)].</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="50ffa-126">另請參閱</span><span class="sxs-lookup"><span data-stu-id="50ffa-126">See Also</span></span>  
 <span data-ttu-id="50ffa-127">[規劃與架構](../core/planning-and-architecture17.md) </span><span class="sxs-lookup"><span data-stu-id="50ffa-127">[Planning and Architecture](../core/planning-and-architecture17.md) </span></span>  
 <span data-ttu-id="50ffa-128">[BizTalk Adapter for JD Edwards OneWorld 中的安全性](../core/security-in-biztalk-adapter-for-jd-edwards-oneworld.md) </span><span class="sxs-lookup"><span data-stu-id="50ffa-128">[Security in BizTalk Adapter for JD Edwards OneWorld](../core/security-in-biztalk-adapter-for-jd-edwards-oneworld.md) </span></span>  
 [<span data-ttu-id="50ffa-129">新增 BizTalk Adapter for JD Edwards OneWorld</span><span class="sxs-lookup"><span data-stu-id="50ffa-129">Adding BizTalk Adapter for JD Edwards OneWorld</span></span>](../core/adding-biztalk-adapter-for-jd-edwards-oneworld.md)