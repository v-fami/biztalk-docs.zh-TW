---
title: "啟用 MS 分散式交易協調器，以允許異動 for Oracle E-business Suite |Microsoft 文件"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 634538e5-7292-4b3f-85b0-c6db86d0dbd2
caps.latest.revision: "4"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 0597c050e1531d71a62af04fe6c825653076297c
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/20/2017
---
# <a name="enable-ms-distributed-transaction-coordinator-to-allow-transactions-for-oracle-e-business-suite"></a><span data-ttu-id="92475-102">啟用以允許 for Oracle E-business Suite 交易的 MS 分散式交易協調器</span><span class="sxs-lookup"><span data-stu-id="92475-102">Enable MS distributed transaction coordinator to allow transactions for Oracle E-Business Suite</span></span>
<span data-ttu-id="92475-103">在您開始建立使用的應用程式之前，設定 MSDTC [!INCLUDE[adapteroraclebusinessshort](../../includes/adapteroraclebusinessshort-md.md)]。</span><span class="sxs-lookup"><span data-stu-id="92475-103">Configure MSDTC before you start creating applications that use the [!INCLUDE[adapteroraclebusinessshort](../../includes/adapteroraclebusinessshort-md.md)].</span></span>  
  
<span data-ttu-id="92475-104">使用 Oracle E-business Suite 作業[!INCLUDE[adapteroraclebusinessshort](../../includes/adapteroraclebusinessshort-md.md)] (透過[!INCLUDE[btsBizTalkServerNoVersion](../../includes/btsbiztalkservernoversion-md.md)]，WCF 服務模型或 WCF 通道模型) 可以在交易範圍內執行。</span><span class="sxs-lookup"><span data-stu-id="92475-104">The operations performed on Oracle E-Business Suite using the [!INCLUDE[adapteroraclebusinessshort](../../includes/adapteroraclebusinessshort-md.md)] (through [!INCLUDE[btsBizTalkServerNoVersion](../../includes/btsbiztalkservernoversion-md.md)], the WCF service model, or the WCF channel model) can be performed within a transaction scope.</span></span> <span data-ttu-id="92475-105">如果用戶端程式有多個交易的資源做為在相同交易的一部分，在交易取得提高 MSDTC 交易。</span><span class="sxs-lookup"><span data-stu-id="92475-105">If the client program has more than one transactional resource as part of the same transaction, the transaction gets elevated to an MSDTC transaction.</span></span> <span data-ttu-id="92475-106">若要啟用的介面卡來執行 MSDTC 交易的範圍內的作業，請執行的電腦上設定 MSDTC [!INCLUDE[adapteroraclebusinessshort](../../includes/adapteroraclebusinessshort-md.md)]，和 Oracle E-business suite。</span><span class="sxs-lookup"><span data-stu-id="92475-106">To enable the adapter to perform operations within the scope of an MSDTC transaction, configure MSDTC on the computer running the [!INCLUDE[adapteroraclebusinessshort](../../includes/adapteroraclebusinessshort-md.md)], and on the Oracle E-Business Suite.</span></span> <span data-ttu-id="92475-107">此外，MSDTC 例外狀況清單中加入您的防火牆，它可能是內建的 Windows 防火牆。</span><span class="sxs-lookup"><span data-stu-id="92475-107">Also, add MSDTC to the exceptions list in your firewall, which may be the built-in Windows Firewall.</span></span> 
  
> [!NOTE]
>  <span data-ttu-id="92475-108">設定 MSDTC 步驟對於不同作業系統有所差異。</span><span class="sxs-lookup"><span data-stu-id="92475-108">The steps to configure MSDTC vary for different operating systems.</span></span> <span data-ttu-id="92475-109">本主題中列出的步驟適用於 Windows 用戶端和 Windows Server 作業系統。</span><span class="sxs-lookup"><span data-stu-id="92475-109">The steps listed in this topic apply to Windows client and Windows Server operating systems.</span></span>  
  
## <a name="configure-msdtc"></a><span data-ttu-id="92475-110">設定 MSDTC</span><span class="sxs-lookup"><span data-stu-id="92475-110">Configure MSDTC</span></span>  
  
1.  <span data-ttu-id="92475-111">開啟**元件服務**。</span><span class="sxs-lookup"><span data-stu-id="92475-111">Open **Component Services**.</span></span>  

    <span data-ttu-id="92475-112">或者，在**伺服器管理員**，選取**工具**，然後選取**元件服務**。</span><span class="sxs-lookup"><span data-stu-id="92475-112">Or, In **Server Manager**, select **Tools**, and then select **Component Services**.</span></span>  
  
2.  <span data-ttu-id="92475-113">展開**元件服務**，依序展開**電腦**，依序展開**我的電腦**，依序展開**分散式交易協調器**，以滑鼠右鍵按一下**本機 DTC**，然後選取**屬性**。</span><span class="sxs-lookup"><span data-stu-id="92475-113">Expand **Component Services**, expand **Computers**, expand **My Computer**, expand **Distributed Transaction Coordinator**, right-click **Local DTC**, and select **Properties**.</span></span>  
  
3.  <span data-ttu-id="92475-114">選取 **[安全性]** 索引標籤。在此索引標籤上，選取下列各項：</span><span class="sxs-lookup"><span data-stu-id="92475-114">Select the **Security** tab. In this tab, select all of the following:</span></span> 

  - <span data-ttu-id="92475-115">**網路 DTC 存取**</span><span class="sxs-lookup"><span data-stu-id="92475-115">**Network DTC Access**</span></span>
  - <span data-ttu-id="92475-116">**允許遠端用戶端**</span><span class="sxs-lookup"><span data-stu-id="92475-116">**Allow Remote Clients**</span></span> 
  - <span data-ttu-id="92475-117">**允許輸入**</span><span class="sxs-lookup"><span data-stu-id="92475-117">**Allow Inbound**</span></span> 
  - <span data-ttu-id="92475-118">**允許輸出**</span><span class="sxs-lookup"><span data-stu-id="92475-118">**Allow Outbound**</span></span> 
  - <span data-ttu-id="92475-119">**沒有所需的 Authetnication**</span><span class="sxs-lookup"><span data-stu-id="92475-119">**No Authetnication Required**</span></span>
  
4.  <span data-ttu-id="92475-120">選取 [確定] 儲存您的變更。</span><span class="sxs-lookup"><span data-stu-id="92475-120">Select **OK** to save your changes.</span></span>  
  
5.  <span data-ttu-id="92475-121">如果提示您重新啟動 MSDTC 服務，請選取**是**。</span><span class="sxs-lookup"><span data-stu-id="92475-121">If prompted to restarted the MSDTC service, select **Yes**.</span></span> <span data-ttu-id="92475-122">重新啟動 MSDTC 服務之後，關閉屬性和元件服務 MMC。</span><span class="sxs-lookup"><span data-stu-id="92475-122">After the MSDTC service is restarted, close the properties and the Component Services MMC.</span></span> 
  
## <a name="add-msdtc-to-windows-firewall-exceptions-list"></a><span data-ttu-id="92475-123">加入 Windows 防火牆例外清單中的 MSDTC</span><span class="sxs-lookup"><span data-stu-id="92475-123">Add MSDTC to Windows Firewall exceptions list</span></span>  

> [!TIP] 
>  <span data-ttu-id="92475-124">Microsoft 分散式 Tansaction 協調器 (MSDTC) 可能已經能在防火牆中。</span><span class="sxs-lookup"><span data-stu-id="92475-124">Microsoft Distributed Tansaction Coordinator (MSDTC) may already be allowed in your firewall.</span></span> <span data-ttu-id="92475-125">如果是的話，它被顯示為輸入的規則。</span><span class="sxs-lookup"><span data-stu-id="92475-125">If so, it is listed as an Inbound Rule.</span></span> <span data-ttu-id="92475-126">如果未列出，請使用本節以允許 MSDTC。</span><span class="sxs-lookup"><span data-stu-id="92475-126">If it's not listed, use this section to allow MSDTC.</span></span> 

1.  <span data-ttu-id="92475-127">開啟**Windows 防火牆**，然後選取**進階設定**左側。</span><span class="sxs-lookup"><span data-stu-id="92475-127">Open **Windows Firewall**, and select **Advanced Settings** on the left.</span></span>  

    <span data-ttu-id="92475-128">或者，在**伺服器管理員**，選取**工具**，然後選取**具有進階安全性的 Windows 防火牆**。</span><span class="sxs-lookup"><span data-stu-id="92475-128">Or, In **Server Manager**, select **Tools**, and then select **Windows Firewall with Advanced Security**.</span></span>  
  
2.  <span data-ttu-id="92475-129">以滑鼠右鍵按一下**輸入規則**，然後選取**新規則**。</span><span class="sxs-lookup"><span data-stu-id="92475-129">Right click **Inbound Rules**, and select **New Rule**.</span></span>  
  
3.  <span data-ttu-id="92475-130">在精靈中：</span><span class="sxs-lookup"><span data-stu-id="92475-130">In the wizard:</span></span> 

    1. <span data-ttu-id="92475-131">選取**程式**，然後選取**下一步**。</span><span class="sxs-lookup"><span data-stu-id="92475-131">Select **Program**, and select **Next**.</span></span> 
    2. <span data-ttu-id="92475-132">設定**程式路徑**至`%SystemRoot%\system32\msdtc.exe`，然後選取**下一步**。</span><span class="sxs-lookup"><span data-stu-id="92475-132">Set the **program path** to `%SystemRoot%\system32\msdtc.exe`, and select **Next**.</span></span>  
    3. <span data-ttu-id="92475-133">**允許連線**，然後選取**下一步**。</span><span class="sxs-lookup"><span data-stu-id="92475-133">**Allow the connection**, and select **Next**.</span></span>
    4. <span data-ttu-id="92475-134">選取**網域**，然後選取**下一步**。</span><span class="sxs-lookup"><span data-stu-id="92475-134">Select **Domain**, and select **Next**.</span></span>
    5. <span data-ttu-id="92475-135">輸入任何名稱，例如`MSDTC for Oracle EBS`，然後選取**完成**。</span><span class="sxs-lookup"><span data-stu-id="92475-135">Enter any name, such as `MSDTC for Oracle EBS`, and select **Finish**.</span></span>
  
5.  <span data-ttu-id="92475-136">完成精靈，並關閉 Windows 防火牆。</span><span class="sxs-lookup"><span data-stu-id="92475-136">Complete the wizard, and close Windows Firewall.</span></span> 
  
## <a name="next"></a><span data-ttu-id="92475-137">下一個</span><span class="sxs-lookup"><span data-stu-id="92475-137">Next</span></span> 
[<span data-ttu-id="92475-138">適用於 Oracle EBS 配接器範例</span><span class="sxs-lookup"><span data-stu-id="92475-138">Samples for the Oracle EBS adapter</span></span>](../../adapters-and-accelerators/adapter-oracle-ebs/samples-for-the-oracle-ebs-adapter.md)