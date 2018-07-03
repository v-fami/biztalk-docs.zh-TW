---
title: 啟用 MS 分散式交易協調器，以允許異動 for Oracle E-business Suite |Microsoft Docs
ms.custom: ''
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 634538e5-7292-4b3f-85b0-c6db86d0dbd2
caps.latest.revision: 4
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 53037e9a7dc1ccc3c0ef21860696060ad1c046a8
ms.sourcegitcommit: 266308ec5c6a9d8d80ff298ee6051b4843c5d626
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/27/2018
ms.locfileid: "36984991"
---
# <a name="enable-ms-distributed-transaction-coordinator-to-allow-transactions-for-oracle-e-business-suite"></a><span data-ttu-id="bdaf3-102">啟用以允許異動 for Oracle E-business Suite 的 MS 分散式交易協調器</span><span class="sxs-lookup"><span data-stu-id="bdaf3-102">Enable MS distributed transaction coordinator to allow transactions for Oracle E-Business Suite</span></span>
<span data-ttu-id="bdaf3-103">設定 MSDTC，才能開始建立應用程式使用[!INCLUDE[adapteroraclebusinessshort](../../includes/adapteroraclebusinessshort-md.md)]。</span><span class="sxs-lookup"><span data-stu-id="bdaf3-103">Configure MSDTC before you start creating applications that use the [!INCLUDE[adapteroraclebusinessshort](../../includes/adapteroraclebusinessshort-md.md)].</span></span>  
  
<span data-ttu-id="bdaf3-104">使用 Oracle E-business Suite 作業[!INCLUDE[adapteroraclebusinessshort](../../includes/adapteroraclebusinessshort-md.md)] (透過[!INCLUDE[btsBizTalkServerNoVersion](../../includes/btsbiztalkservernoversion-md.md)]，WCF 服務模型或 WCF 通道模型) 可以在交易範圍內執行。</span><span class="sxs-lookup"><span data-stu-id="bdaf3-104">The operations performed on Oracle E-Business Suite using the [!INCLUDE[adapteroraclebusinessshort](../../includes/adapteroraclebusinessshort-md.md)] (through [!INCLUDE[btsBizTalkServerNoVersion](../../includes/btsbiztalkservernoversion-md.md)], the WCF service model, or the WCF channel model) can be performed within a transaction scope.</span></span> <span data-ttu-id="bdaf3-105">如果用戶端程式會有一個以上的交易式資源作為相同交易的一部分，取得更高為 MSDTC 交易的交易。</span><span class="sxs-lookup"><span data-stu-id="bdaf3-105">If the client program has more than one transactional resource as part of the same transaction, the transaction gets elevated to an MSDTC transaction.</span></span> <span data-ttu-id="bdaf3-106">若要啟用配接器來執行 MSDTC 交易的範圍內的作業，請執行的電腦上設定 MSDTC [!INCLUDE[adapteroraclebusinessshort](../../includes/adapteroraclebusinessshort-md.md)]，並在 Oracle E-business Suite。</span><span class="sxs-lookup"><span data-stu-id="bdaf3-106">To enable the adapter to perform operations within the scope of an MSDTC transaction, configure MSDTC on the computer running the [!INCLUDE[adapteroraclebusinessshort](../../includes/adapteroraclebusinessshort-md.md)], and on the Oracle E-Business Suite.</span></span> <span data-ttu-id="bdaf3-107">此外，將 MSDTC 例外狀況清單在防火牆中，這可能是內建的 Windows 防火牆。</span><span class="sxs-lookup"><span data-stu-id="bdaf3-107">Also, add MSDTC to the exceptions list in your firewall, which may be the built-in Windows Firewall.</span></span> 
  
> [!NOTE]
>  <span data-ttu-id="bdaf3-108">設定 MSDTC 的步驟因不同作業系統而異。</span><span class="sxs-lookup"><span data-stu-id="bdaf3-108">The steps to configure MSDTC vary for different operating systems.</span></span> <span data-ttu-id="bdaf3-109">本主題中列出的步驟適用於 Windows 用戶端和 Windows Server 作業系統。</span><span class="sxs-lookup"><span data-stu-id="bdaf3-109">The steps listed in this topic apply to Windows client and Windows Server operating systems.</span></span>  
  
## <a name="configure-msdtc"></a><span data-ttu-id="bdaf3-110">設定 MSDTC</span><span class="sxs-lookup"><span data-stu-id="bdaf3-110">Configure MSDTC</span></span>  
  
1. <span data-ttu-id="bdaf3-111">開啟**元件服務**。</span><span class="sxs-lookup"><span data-stu-id="bdaf3-111">Open **Component Services**.</span></span>  

   <span data-ttu-id="bdaf3-112">或者，在**伺服器管理員**，選取**工具**，然後選取**元件服務**。</span><span class="sxs-lookup"><span data-stu-id="bdaf3-112">Or, In **Server Manager**, select **Tools**, and then select **Component Services**.</span></span>  
  
2. <span data-ttu-id="bdaf3-113">依序展開**Microsoft.biztalk.deployment.deployercomponent**，展開**電腦**，展開**我的電腦**，展開**分散式交易協調器**，以滑鼠右鍵按一下**本機 DTC**，然後選取**屬性**。</span><span class="sxs-lookup"><span data-stu-id="bdaf3-113">Expand **Component Services**, expand **Computers**, expand **My Computer**, expand **Distributed Transaction Coordinator**, right-click **Local DTC**, and select **Properties**.</span></span>  
  
3. <span data-ttu-id="bdaf3-114">選取 **[安全性]** 索引標籤。在此索引標籤中，選取下列各項：</span><span class="sxs-lookup"><span data-stu-id="bdaf3-114">Select the **Security** tab. In this tab, select all of the following:</span></span> 

   - <span data-ttu-id="bdaf3-115">**網路 DTC 存取**</span><span class="sxs-lookup"><span data-stu-id="bdaf3-115">**Network DTC Access**</span></span>
   - <span data-ttu-id="bdaf3-116">**允許遠端用戶端**</span><span class="sxs-lookup"><span data-stu-id="bdaf3-116">**Allow Remote Clients**</span></span> 
   - <span data-ttu-id="bdaf3-117">**允許輸入**</span><span class="sxs-lookup"><span data-stu-id="bdaf3-117">**Allow Inbound**</span></span> 
   - <span data-ttu-id="bdaf3-118">**允許輸出**</span><span class="sxs-lookup"><span data-stu-id="bdaf3-118">**Allow Outbound**</span></span> 
   - <span data-ttu-id="bdaf3-119">**沒有所需的 Authetnication**</span><span class="sxs-lookup"><span data-stu-id="bdaf3-119">**No Authetnication Required**</span></span>
  
4. <span data-ttu-id="bdaf3-120">選取 [確定] 儲存您的變更。</span><span class="sxs-lookup"><span data-stu-id="bdaf3-120">Select **OK** to save your changes.</span></span>  
  
5. <span data-ttu-id="bdaf3-121">如果系統提示重新啟動 MSDTC 服務，請選取**是**。</span><span class="sxs-lookup"><span data-stu-id="bdaf3-121">If prompted to restarted the MSDTC service, select **Yes**.</span></span> <span data-ttu-id="bdaf3-122">重新啟動 MSDTC 服務之後，關閉 [屬性和元件服務] MMC。</span><span class="sxs-lookup"><span data-stu-id="bdaf3-122">After the MSDTC service is restarted, close the properties and the Component Services MMC.</span></span> 
  
## <a name="add-msdtc-to-windows-firewall-exceptions-list"></a><span data-ttu-id="bdaf3-123">加入 Windows 防火牆例外清單中的 MSDTC</span><span class="sxs-lookup"><span data-stu-id="bdaf3-123">Add MSDTC to Windows Firewall exceptions list</span></span>  

> [!TIP] 
>  <span data-ttu-id="bdaf3-124">Microsoft 分散式 Tansaction 協調器 (MSDTC) 可能已允許在防火牆中。</span><span class="sxs-lookup"><span data-stu-id="bdaf3-124">Microsoft Distributed Tansaction Coordinator (MSDTC) may already be allowed in your firewall.</span></span> <span data-ttu-id="bdaf3-125">如果是的話，它會列為輸入規則。</span><span class="sxs-lookup"><span data-stu-id="bdaf3-125">If so, it is listed as an Inbound Rule.</span></span> <span data-ttu-id="bdaf3-126">如果未列出，請使用本節以允許 MSDTC。</span><span class="sxs-lookup"><span data-stu-id="bdaf3-126">If it's not listed, use this section to allow MSDTC.</span></span> 

1.  <span data-ttu-id="bdaf3-127">開啟**Windows 防火牆**，然後選取**進階設定**左側。</span><span class="sxs-lookup"><span data-stu-id="bdaf3-127">Open **Windows Firewall**, and select **Advanced Settings** on the left.</span></span>  

    <span data-ttu-id="bdaf3-128">或者，在**伺服器管理員**，選取**工具**，然後選取**具有進階安全性的 Windows 防火牆**。</span><span class="sxs-lookup"><span data-stu-id="bdaf3-128">Or, In **Server Manager**, select **Tools**, and then select **Windows Firewall with Advanced Security**.</span></span>  
  
2.  <span data-ttu-id="bdaf3-129">以滑鼠右鍵按一下**輸入規則**，然後選取**新規則**。</span><span class="sxs-lookup"><span data-stu-id="bdaf3-129">Right click **Inbound Rules**, and select **New Rule**.</span></span>  
  
3.  <span data-ttu-id="bdaf3-130">在精靈中：</span><span class="sxs-lookup"><span data-stu-id="bdaf3-130">In the wizard:</span></span> 

    1. <span data-ttu-id="bdaf3-131">選取 [**計劃**，然後選取**下一步]**。</span><span class="sxs-lookup"><span data-stu-id="bdaf3-131">Select **Program**, and select **Next**.</span></span> 
    2. <span data-ttu-id="bdaf3-132">設定**程式路徑**要`%SystemRoot%\system32\msdtc.exe`，然後選取**下一步**。</span><span class="sxs-lookup"><span data-stu-id="bdaf3-132">Set the **program path** to `%SystemRoot%\system32\msdtc.exe`, and select **Next**.</span></span>  
    3. <span data-ttu-id="bdaf3-133">**允許連線**，然後選取**下一步**。</span><span class="sxs-lookup"><span data-stu-id="bdaf3-133">**Allow the connection**, and select **Next**.</span></span>
    4. <span data-ttu-id="bdaf3-134">選取 [**網域**，然後選取**下一步]**。</span><span class="sxs-lookup"><span data-stu-id="bdaf3-134">Select **Domain**, and select **Next**.</span></span>
    5. <span data-ttu-id="bdaf3-135">輸入任何名稱，例如`MSDTC for Oracle EBS`，然後選取**完成**。</span><span class="sxs-lookup"><span data-stu-id="bdaf3-135">Enter any name, such as `MSDTC for Oracle EBS`, and select **Finish**.</span></span>
  
5.  <span data-ttu-id="bdaf3-136">完成精靈，並關閉 Windows 防火牆。</span><span class="sxs-lookup"><span data-stu-id="bdaf3-136">Complete the wizard, and close Windows Firewall.</span></span> 
  
## <a name="next"></a><span data-ttu-id="bdaf3-137">下一個</span><span class="sxs-lookup"><span data-stu-id="bdaf3-137">Next</span></span> 
[<span data-ttu-id="bdaf3-138">適用於 Oracle EBS 配接器範例</span><span class="sxs-lookup"><span data-stu-id="bdaf3-138">Samples for the Oracle EBS adapter</span></span>](../../adapters-and-accelerators/adapter-oracle-ebs/samples-for-the-oracle-ebs-adapter.md)