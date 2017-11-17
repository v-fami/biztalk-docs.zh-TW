---
title: "設定交易隔離等級和交易逾時與 Oracle E-business Suite |Microsoft 文件"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: db3d64ad-037d-486a-bdde-45c8199613f1
caps.latest.revision: "6"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 89e818d6ca3fdda05ee877f9e6ef4f04d7a66176
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/20/2017
---
# <a name="configure-transaction-isolation-level-and-transaction-timeout-with-oracle-e-business-suite"></a><span data-ttu-id="74173-102">使用 Oracle E-business Suite 設定交易隔離等級和交易逾時</span><span class="sxs-lookup"><span data-stu-id="74173-102">Configure transaction isolation level and transaction timeout with Oracle E-Business Suite</span></span>
<span data-ttu-id="74173-103">在執行輸入的作業 （輪詢和通知） 時使用[!INCLUDE[adapteroracleebusinesslong](../../includes/adapteroracleebusinesslong-md.md)]與[!INCLUDE[btsBizTalkServerNoVersion](../../includes/btsbiztalkservernoversion-md.md)]，您應該適當地設定交易隔離等級和交易逾時值。</span><span class="sxs-lookup"><span data-stu-id="74173-103">While performing inbound operations (Polling and Notification) using the [!INCLUDE[adapteroracleebusinesslong](../../includes/adapteroracleebusinesslong-md.md)] with [!INCLUDE[btsBizTalkServerNoVersion](../../includes/btsbiztalkservernoversion-md.md)], you should appropriately configure the transaction isolation level and the transaction timeout values.</span></span> <span data-ttu-id="74173-104">若要這樣做：</span><span class="sxs-lookup"><span data-stu-id="74173-104">To do this:</span></span>  
  
1.  <span data-ttu-id="74173-105">啟動[!INCLUDE[btsBizTalkServerNoVersion](../../includes/btsbiztalkservernoversion-md.md)]管理主控台。</span><span class="sxs-lookup"><span data-stu-id="74173-105">Start the [!INCLUDE[btsBizTalkServerNoVersion](../../includes/btsbiztalkservernoversion-md.md)] Administration console.</span></span>  
  
2.  <span data-ttu-id="74173-106">在主控台樹狀目錄中，依序展開**BizTalk 群組**，然後展開**應用程式**。</span><span class="sxs-lookup"><span data-stu-id="74173-106">In the console tree, expand the **BizTalk Group**, and then expand **Applications**.</span></span>  
  
3.  <span data-ttu-id="74173-107">展開產生的中繼資料使用之後，您已部署的 BizTalk 應用程式[!INCLUDE[adapteroraclebusinessshort](../../includes/adapteroraclebusinessshort-md.md)]。</span><span class="sxs-lookup"><span data-stu-id="74173-107">Expand the BizTalk application that you have deployed after generating the metadata using the [!INCLUDE[adapteroraclebusinessshort](../../includes/adapteroraclebusinessshort-md.md)].</span></span>  
  
4.  <span data-ttu-id="74173-108">以滑鼠右鍵按一下**接收埠**，指向 **新增**，然後按一下 **單向接收埠**。</span><span class="sxs-lookup"><span data-stu-id="74173-108">Right-click **Receive Ports**, point to **New**, and then click **One-way Receive Port**.</span></span>  
  
5.  <span data-ttu-id="74173-109">在**接收埠屬性**對話方塊**一般**索引標籤上，輸入接收埠的名稱。</span><span class="sxs-lookup"><span data-stu-id="74173-109">In the **Receive Port Properties** dialog box, on the **General** tab, type a name for the receive port.</span></span>  
  
6.  <span data-ttu-id="74173-110">在左窗格中**接收埠屬性**對話方塊中，按一下 **接收位置**，然後按一下 **新增**在右窗格來定義新接收位置。</span><span class="sxs-lookup"><span data-stu-id="74173-110">In the left pane of the **Receive Port Properties** dialog box, click **Receive Locations**, and then click **New** in the right pane to define a new receive location.</span></span>  
  
7.  <span data-ttu-id="74173-111">在**接收位置屬性**對話方塊中，按一下  **Wcf-custom**中**類型**清單。</span><span class="sxs-lookup"><span data-stu-id="74173-111">In the **Receive Location Properties** dialog box, click **WCF-Custom** in the **Type** list.</span></span>  
  
8.  <span data-ttu-id="74173-112">按一下**設定**相鄰**類型**清單。</span><span class="sxs-lookup"><span data-stu-id="74173-112">Click **Configure** adjacent to the **Type** list.</span></span>  
  
9. <span data-ttu-id="74173-113">在**Wcf-custom 傳輸屬性**對話方塊中，按一下 [**行為**] 索引標籤。</span><span class="sxs-lookup"><span data-stu-id="74173-113">In the **WCF-Custom Transport Properties** dialog box, click the **Behavior** tab.</span></span>  
  
10. <span data-ttu-id="74173-114">在**行為**清單中，以滑鼠右鍵按一下**ServiceBehavior**，然後按一下**將延伸加入**。</span><span class="sxs-lookup"><span data-stu-id="74173-114">In the **Behavior** list, right-click **ServiceBehavior**, and click **Add extension**.</span></span>  
  
11. <span data-ttu-id="74173-115">在**選取行為延伸模組**對話方塊中，選取**oracleEBSAdapterInboundTransactionBehavior**，然後按一下**確定**。</span><span class="sxs-lookup"><span data-stu-id="74173-115">In the **Select Behavior Extension** dialog box, select **oracleEBSAdapterInboundTransactionBehavior**, and click **OK**.</span></span>  
  
12. <span data-ttu-id="74173-116">在左窗格中**Wcf-custom 傳輸屬性**，選取**oracleEBSAdapterInboundTransactionBehavior**服務**ServiceBehavior**。</span><span class="sxs-lookup"><span data-stu-id="74173-116">In the left pane of the **WCF-Custom Transport Properties**, select the **oracleEBSAdapterInboundTransactionBehavior** service under **ServiceBehavior**.</span></span>  
  
13. <span data-ttu-id="74173-117">在右窗格中**Wcf-custom 傳輸屬性**，指定適當的值**transactionIsolationLevel**和**transactionTimeout**參數。</span><span class="sxs-lookup"><span data-stu-id="74173-117">In the right pane of the **WCF-Custom Transport Properties**, specify appropriate values for the **transactionIsolationLevel** and **transactionTimeout** parameters.</span></span> <span data-ttu-id="74173-118">您可以選取任何下列的交易隔離等級： **Serializable**， **RepeatableRead**， **ReadCommitted**， **ReadUncommitted**，**快照**， **Chaos**，和**未指定**。</span><span class="sxs-lookup"><span data-stu-id="74173-118">You can select any of the following transaction isolation levels: **Serializable**, **RepeatableRead**, **ReadCommitted**, **ReadUncommitted**, **Snapshot**, **Chaos**, and **Unspecified**.</span></span> <span data-ttu-id="74173-119">如需這些交易隔離等級的資訊，請參閱**成員**區段在[http://go.microsoft.com/fwlink/?LinkId=126983](http://go.microsoft.com/fwlink/?LinkId=126983)。</span><span class="sxs-lookup"><span data-stu-id="74173-119">For information about these transaction isolation levels, see the **Members** section at [http://go.microsoft.com/fwlink/?LinkId=126983](http://go.microsoft.com/fwlink/?LinkId=126983).</span></span>  
  
    > [!IMPORTANT]
    >  <span data-ttu-id="74173-120">Oracle E-business Suite 支援只有下列兩個交易隔離等級： ReadCommitted 和 Serializable。</span><span class="sxs-lookup"><span data-stu-id="74173-120">Oracle E-Business Suite supports only the following two transaction isolation levels: ReadCommitted and Serializable.</span></span>  
  
     <span data-ttu-id="74173-121">![設定交易隔離層級](../../adapters-and-accelerators/adapter-oracle-ebs/media/2bafbb9d-4daa-43c0-abcb-35220e6a3cb5.gif "2bafbb9d-4daa-43c0-abcb-35220e6a3cb5")</span><span class="sxs-lookup"><span data-stu-id="74173-121">![Setting Transaction Isolation Level](../../adapters-and-accelerators/adapter-oracle-ebs/media/2bafbb9d-4daa-43c0-abcb-35220e6a3cb5.gif "2bafbb9d-4daa-43c0-abcb-35220e6a3cb5")</span></span>  
  
14. <span data-ttu-id="74173-122">按一下**確定**中**Wcf-custom 傳輸屬性** 對話方塊。</span><span class="sxs-lookup"><span data-stu-id="74173-122">Click **OK** in the **WCF-Custom Transport Properties** dialog box.</span></span>  
  
15. <span data-ttu-id="74173-123">按一下**確定**中將變更儲存開啟的對話方塊。</span><span class="sxs-lookup"><span data-stu-id="74173-123">Click **OK** in the open dialog boxes to save the changes.</span></span>