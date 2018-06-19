---
title: SQL Server 和配接器的用戶端上設定 MSDTC |Microsoft 文件
ms.custom: ''
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 2c87f455-a8c4-4169-bf18-695926136df1
caps.latest.revision: 14
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: cf519044dc28d417d85682189dd4a52585310ac0
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/20/2017
ms.locfileid: "22222918"
---
# <a name="configure-msdtc-on-sql-server-and-adapter-client"></a><span data-ttu-id="4494f-102">SQL Server 和配接器的用戶端上設定 MSDTC</span><span class="sxs-lookup"><span data-stu-id="4494f-102">Configure MSDTC on SQL Server and adapter client</span></span>
<span data-ttu-id="4494f-103">使用 SQL Server 上執行的操作[!INCLUDE[adaptersqlshort](../../includes/adaptersqlshort-md.md)] (透過[!INCLUDE[btsBizTalkServerNoVersion](../../includes/btsbiztalkservernoversion-md.md)]，WCF 服務模型或 WCF 通道模型) 可以在交易範圍內執行。</span><span class="sxs-lookup"><span data-stu-id="4494f-103">The operations performed on SQL Server using the [!INCLUDE[adaptersqlshort](../../includes/adaptersqlshort-md.md)] (through [!INCLUDE[btsBizTalkServerNoVersion](../../includes/btsbiztalkservernoversion-md.md)], the WCF service model, or the WCF channel model) can be performed within a transaction scope.</span></span> <span data-ttu-id="4494f-104">如果用戶端程式有多個交易的資源做為在相同交易的一部分，在交易取得提高 MSDTC 交易。</span><span class="sxs-lookup"><span data-stu-id="4494f-104">If the client program has more than one transactional resource as part of the same transaction, the transaction gets elevated to an MSDTC transaction.</span></span> <span data-ttu-id="4494f-105">若要啟用的介面卡來執行 MSDTC 交易的範圍內的作業，您必須執行的電腦上設定 MSDTC 這兩個[!INCLUDE[adaptersqlshort](../../includes/adaptersqlshort-md.md)]和 SQL Server。</span><span class="sxs-lookup"><span data-stu-id="4494f-105">To enable the adapter to perform operations within the scope of an MSDTC transaction, you must configure MSDTC both on the computer running the [!INCLUDE[adaptersqlshort](../../includes/adaptersqlshort-md.md)] and SQL Server.</span></span> <span data-ttu-id="4494f-106">此外，您必須將 MSDTC 加入 Windows 防火牆的例外狀況清單。</span><span class="sxs-lookup"><span data-stu-id="4494f-106">Also, you must add MSDTC to the exceptions list of Windows Firewall.</span></span> <span data-ttu-id="4494f-107">本節提供如何在執行配接器用戶端和 SQL Server 的電腦上執行這些工作的相關資訊。</span><span class="sxs-lookup"><span data-stu-id="4494f-107">This section provides information about how to perform these tasks on computers running the adapter client and SQL Server.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="4494f-108">使用 SQL Server 上執行的作業[!INCLUDE[btsBizTalkServerNoVersion](../../includes/btsbiztalkservernoversion-md.md)]一律牽涉到兩個資源，配接器連接到 SQL Server 和 SQL Server 上的 BizTalk 訊息方塊。</span><span class="sxs-lookup"><span data-stu-id="4494f-108">Performing operations on SQL Server using [!INCLUDE[btsBizTalkServerNoVersion](../../includes/btsbiztalkservernoversion-md.md)] always involves two resources—the adapter connecting to SQL Server and the BizTalk Message Box residing on SQL Server.</span></span> <span data-ttu-id="4494f-109">因此，所有作業都執行使用[!INCLUDE[btsBizTalkServerNoVersion](../../includes/btsbiztalkservernoversion-md.md)]MSDTC 交易的範圍內都執行。</span><span class="sxs-lookup"><span data-stu-id="4494f-109">Hence, all operations performed using [!INCLUDE[btsBizTalkServerNoVersion](../../includes/btsbiztalkservernoversion-md.md)] are performed within the scope of an MSDTC transaction.</span></span> <span data-ttu-id="4494f-110">因此，為了使用[!INCLUDE[adaptersqlshort](../../includes/adaptersqlshort-md.md)]與[!INCLUDE[btsBizTalkServerNoVersion](../../includes/btsbiztalkservernoversion-md.md)]，您必須一律啟用 MSDTC。</span><span class="sxs-lookup"><span data-stu-id="4494f-110">So, to use the [!INCLUDE[adaptersqlshort](../../includes/adaptersqlshort-md.md)] with [!INCLUDE[btsBizTalkServerNoVersion](../../includes/btsbiztalkservernoversion-md.md)], you must always enable MSDTC.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="4494f-111">作業在配接器用戶端就無法寫入任何資料的 SQL Server 資料庫，選取的作業，例如，您可能不想執行的作業在交易內的額外負擔。</span><span class="sxs-lookup"><span data-stu-id="4494f-111">For operations where the adapter client does not write any data to the SQL Server database, such as a Select operation, you might not want the additional overhead of performing the operations inside a transaction.</span></span> <span data-ttu-id="4494f-112">在這種情況下，您可以設定[!INCLUDE[adaptersqlshort](../../includes/adaptersqlshort-md.md)]執行沒有交易式內容的作業，藉由設定**UseAmbientTransaction**內容繫結至**false**。</span><span class="sxs-lookup"><span data-stu-id="4494f-112">In such cases, you can configure the [!INCLUDE[adaptersqlshort](../../includes/adaptersqlshort-md.md)] to perform operations without a transactional context by setting the **UseAmbientTransaction** binding property to **false**.</span></span> <span data-ttu-id="4494f-113">如需繫結屬性的詳細資訊，請參閱[閱讀 BizTalk Adapter for SQL Server 配接器繫結屬性](../../adapters-and-accelerators/adapter-sql/read-about-the-biztalk-adapter-for-sql-server-adapter-binding-properties.md)。</span><span class="sxs-lookup"><span data-stu-id="4494f-113">For more information about the binding property, see [Read about the BizTalk Adapter for SQL Server adapter Binding Properties](../../adapters-and-accelerators/adapter-sql/read-about-the-biztalk-adapter-for-sql-server-adapter-binding-properties.md).</span></span> <span data-ttu-id="4494f-114">在這種情況下，您不需要也將 MSDTC 設定。</span><span class="sxs-lookup"><span data-stu-id="4494f-114">In such cases, you do not need to configure MSDTC as well.</span></span>  
  
## <a name="configure-msdtc"></a><span data-ttu-id="4494f-115">設定 MSDTC</span><span class="sxs-lookup"><span data-stu-id="4494f-115">Configure MSDTC</span></span>  
  
1.  <span data-ttu-id="4494f-116">開啟**元件服務**。</span><span class="sxs-lookup"><span data-stu-id="4494f-116">Open **Component Services**.</span></span>  

    <span data-ttu-id="4494f-117">或者，在**伺服器管理員**，選取**工具**，然後選取**元件服務**。</span><span class="sxs-lookup"><span data-stu-id="4494f-117">Or, In **Server Manager**, select **Tools**, and then select **Component Services**.</span></span>  
  
2.  <span data-ttu-id="4494f-118">展開**元件服務**，依序展開**電腦**，依序展開**我的電腦**，依序展開**分散式交易協調器**，以滑鼠右鍵按一下**本機 DTC**，然後選取**屬性**。</span><span class="sxs-lookup"><span data-stu-id="4494f-118">Expand **Component Services**, expand **Computers**, expand **My Computer**, expand **Distributed Transaction Coordinator**, right-click **Local DTC**, and select **Properties**.</span></span>  
  
3.  <span data-ttu-id="4494f-119">選取 **[安全性]** 索引標籤。在此索引標籤上，選取下列各項：</span><span class="sxs-lookup"><span data-stu-id="4494f-119">Select the **Security** tab. In this tab, select all of the following:</span></span> 

  - <span data-ttu-id="4494f-120">**網路 DTC 存取**</span><span class="sxs-lookup"><span data-stu-id="4494f-120">**Network DTC Access**</span></span>
  - <span data-ttu-id="4494f-121">**允許遠端用戶端**</span><span class="sxs-lookup"><span data-stu-id="4494f-121">**Allow Remote Clients**</span></span> 
  - <span data-ttu-id="4494f-122">**允許輸入**</span><span class="sxs-lookup"><span data-stu-id="4494f-122">**Allow Inbound**</span></span> 
  - <span data-ttu-id="4494f-123">**允許輸出**</span><span class="sxs-lookup"><span data-stu-id="4494f-123">**Allow Outbound**</span></span> 
  - <span data-ttu-id="4494f-124">**沒有所需的 Authetnication**</span><span class="sxs-lookup"><span data-stu-id="4494f-124">**No Authetnication Required**</span></span>
  
4.  <span data-ttu-id="4494f-125">選取 [確定] 儲存您的變更。</span><span class="sxs-lookup"><span data-stu-id="4494f-125">Select **OK** to save your changes.</span></span>  
  
5.  <span data-ttu-id="4494f-126">如果提示您重新啟動 MSDTC 服務，請選取**是**。</span><span class="sxs-lookup"><span data-stu-id="4494f-126">If prompted to restarted the MSDTC service, select **Yes**.</span></span> <span data-ttu-id="4494f-127">重新啟動 MSDTC 服務之後，關閉屬性和元件服務 MMC。</span><span class="sxs-lookup"><span data-stu-id="4494f-127">After the MSDTC service is restarted, close the properties and the Component Services MMC.</span></span> 
  
## <a name="add-msdtc-to-windows-firewall-exceptions-list"></a><span data-ttu-id="4494f-128">加入 Windows 防火牆例外清單中的 MSDTC</span><span class="sxs-lookup"><span data-stu-id="4494f-128">Add MSDTC to Windows Firewall exceptions list</span></span>  

> [!TIP] 
>  <span data-ttu-id="4494f-129">Microsoft 分散式 Tansaction 協調器 (MSDTC) 可能已經能在防火牆中。</span><span class="sxs-lookup"><span data-stu-id="4494f-129">Microsoft Distributed Tansaction Coordinator (MSDTC) may already be allowed in your firewall.</span></span> <span data-ttu-id="4494f-130">如果是的話，它被顯示為輸入的規則。</span><span class="sxs-lookup"><span data-stu-id="4494f-130">If so, it is listed as an Inbound Rule.</span></span> <span data-ttu-id="4494f-131">如果未列出，請使用本節以允許 MSDTC。</span><span class="sxs-lookup"><span data-stu-id="4494f-131">If it's not listed, use this section to allow MSDTC.</span></span> 

1.  <span data-ttu-id="4494f-132">開啟**Windows 防火牆**，然後選取**進階設定**左側。</span><span class="sxs-lookup"><span data-stu-id="4494f-132">Open **Windows Firewall**, and select **Advanced Settings** on the left.</span></span>  

    <span data-ttu-id="4494f-133">或者，在**伺服器管理員**，選取**工具**，然後選取**具有進階安全性的 Windows 防火牆**。</span><span class="sxs-lookup"><span data-stu-id="4494f-133">Or, In **Server Manager**, select **Tools**, and then select **Windows Firewall with Advanced Security**.</span></span>  
  
2.  <span data-ttu-id="4494f-134">以滑鼠右鍵按一下**輸入規則**，然後選取**新規則**。</span><span class="sxs-lookup"><span data-stu-id="4494f-134">Right click **Inbound Rules**, and select **New Rule**.</span></span>  
  
3.  <span data-ttu-id="4494f-135">在精靈中：</span><span class="sxs-lookup"><span data-stu-id="4494f-135">In the wizard:</span></span> 

    1. <span data-ttu-id="4494f-136">選取**程式**，然後選取**下一步**。</span><span class="sxs-lookup"><span data-stu-id="4494f-136">Select **Program**, and select **Next**.</span></span> 
    2. <span data-ttu-id="4494f-137">設定**程式路徑**至`%SystemRoot%\system32\msdtc.exe`，然後選取**下一步**。</span><span class="sxs-lookup"><span data-stu-id="4494f-137">Set the **program path** to `%SystemRoot%\system32\msdtc.exe`, and select **Next**.</span></span>  
    3. <span data-ttu-id="4494f-138">**允許連線**，然後選取**下一步**。</span><span class="sxs-lookup"><span data-stu-id="4494f-138">**Allow the connection**, and select **Next**.</span></span>
    4. <span data-ttu-id="4494f-139">選取**網域**，然後選取**下一步**。</span><span class="sxs-lookup"><span data-stu-id="4494f-139">Select **Domain**, and select **Next**.</span></span>
    5. <span data-ttu-id="4494f-140">輸入任何名稱，例如`MSDTC for Oracle EBS`，然後選取**完成**。</span><span class="sxs-lookup"><span data-stu-id="4494f-140">Enter any name, such as `MSDTC for Oracle EBS`, and select **Finish**.</span></span>
  
5.  <span data-ttu-id="4494f-141">完成精靈，並關閉 Windows 防火牆。</span><span class="sxs-lookup"><span data-stu-id="4494f-141">Complete the wizard, and close Windows Firewall.</span></span> 
  
## <a name="see-also"></a><span data-ttu-id="4494f-142">另請參閱</span><span class="sxs-lookup"><span data-stu-id="4494f-142">See Also</span></span>  
[<span data-ttu-id="4494f-143">開發 SQL 應用程式</span><span class="sxs-lookup"><span data-stu-id="4494f-143">Develop your SQL applications</span></span>](../../adapters-and-accelerators/adapter-sql/develop-your-sql-applications.md)