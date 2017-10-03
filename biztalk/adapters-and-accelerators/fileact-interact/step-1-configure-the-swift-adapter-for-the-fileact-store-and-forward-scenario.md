---
title: "步驟 1： 設定為 FileAct 存放與轉寄實例 SWIFT 的配接器 |Microsoft 文件"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 18653322-b748-4954-93f7-9a7a39e406f8
caps.latest.revision: "10"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 3d2946bcd37e0e7641a2d3bf750f88cd3199fc74
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/20/2017
---
# <a name="step-1-configure-the-swift-adapter-for-the-fileact-store-and-forward-scenario"></a><span data-ttu-id="0af25-102">步驟 1： 設定為 FileAct 存放與轉寄實例 SWIFT 的配接器</span><span class="sxs-lookup"><span data-stu-id="0af25-102">Step 1: Configure the SWIFT Adapter for the FileAct Store and Forward Scenario</span></span>
<span data-ttu-id="0af25-103">完成[準備使用本教學課程](../../adapters-and-accelerators/fileact-interact/preparing-to-use-the-tutorial1.md)開始此步驟之前。</span><span class="sxs-lookup"><span data-stu-id="0af25-103">Complete [Preparing to Use the Tutorial](../../adapters-and-accelerators/fileact-interact/preparing-to-use-the-tutorial1.md) before you begin this step.</span></span>
  
## <a name="configure-the-swift-adapter"></a><span data-ttu-id="0af25-104">設定 SWIFT 配接器</span><span class="sxs-lookup"><span data-stu-id="0af25-104">Configure the SWIFT adapter</span></span>  
  
1.  <span data-ttu-id="0af25-105">啟動**BizTalk Server 管理**。</span><span class="sxs-lookup"><span data-stu-id="0af25-105">Start **BizTalk Server Administration**.</span></span>  
  
2.  <span data-ttu-id="0af25-106">在主控台樹狀目錄中，依序展開**BizTalk Server 管理**、 依序展開 BizTalk 群組、 展開**平台設定**，依序展開**配接器**，以滑鼠右鍵按一下**FILEACT**，指向 **新增**，然後按一下 **傳送處理常式**。</span><span class="sxs-lookup"><span data-stu-id="0af25-106">In the console tree, expand **BizTalk Server Administration**, expand the BizTalk group, expand **Platform Settings**, expand **Adapter**, right-click **FILEACT**, point to **New**, and then click **Send Handler**.</span></span>  
  
3.  <span data-ttu-id="0af25-107">在**FILEACT – 介面卡 HandlerProperties**對話方塊**一般**索引標籤上，從**主機名稱**下拉式清單中，選取**fileacthost**，然後按一下 **屬性**。</span><span class="sxs-lookup"><span data-stu-id="0af25-107">In the **FILEACT – Adapter HandlerProperties** dialog box, on the **General** tab, from the **Host name** drop-down list, select **fileacthost**, and then click **Properties**.</span></span>  
  
4.  <span data-ttu-id="0af25-108">在**FILEACT 傳輸屬性**對話方塊**屬性**索引標籤上，執行下列動作：</span><span class="sxs-lookup"><span data-stu-id="0af25-108">In the **FILEACT Transport Properties** dialog box, on the **Properties** tab, do the following:</span></span>  
  
    |<span data-ttu-id="0af25-109">**使用此選項**</span><span class="sxs-lookup"><span data-stu-id="0af25-109">**Use this**</span></span>|<span data-ttu-id="0af25-110">**若要這樣做**</span><span class="sxs-lookup"><span data-stu-id="0af25-110">**To do this**</span></span>|  
    |------------------|--------------------|  
    |<span data-ttu-id="0af25-111">**引數**</span><span class="sxs-lookup"><span data-stu-id="0af25-111">**Arguments**</span></span>|<span data-ttu-id="0af25-112">輸入下列引數:-SagMessagePartner \<Fileact 用戶端訊息的夥伴建立 SAG >**附註：**引數中的用戶端是 MessagePartner SAG 中進行設定。</span><span class="sxs-lookup"><span data-stu-id="0af25-112">Type the following argument: -SagMessagePartner \<Fileact Client Message Partner created in SAG> **Note:**  The client in the argument is the MessagePartner you configured in SAG.</span></span>|  
    |<span data-ttu-id="0af25-113">**密碼編譯模式**</span><span class="sxs-lookup"><span data-stu-id="0af25-113">**Crypto Mode**</span></span>|<span data-ttu-id="0af25-114">從下拉式清單選取**進階**。</span><span class="sxs-lookup"><span data-stu-id="0af25-114">From the drop-down list, select **Advanced**.</span></span>|  
    |<span data-ttu-id="0af25-115">**FACryptoMode**</span><span class="sxs-lookup"><span data-stu-id="0af25-115">**FACryptoMode**</span></span>|<span data-ttu-id="0af25-116">從下拉式清單選取**進階**。</span><span class="sxs-lookup"><span data-stu-id="0af25-116">From the drop-down list, select **Advanced**.</span></span>|  
    |<span data-ttu-id="0af25-117">**記錄訊息**</span><span class="sxs-lookup"><span data-stu-id="0af25-117">**LogMessages**</span></span>|<span data-ttu-id="0af25-118">從下拉式清單選取**TRUE**。</span><span class="sxs-lookup"><span data-stu-id="0af25-118">From the drop-down list, select **TRUE**.</span></span> <span data-ttu-id="0af25-119">這可讓要擷取，並在 BAM 入口網站中追蹤的訊息事件。</span><span class="sxs-lookup"><span data-stu-id="0af25-119">This enables the message events to be captured and tracked in the BAM portal.</span></span>|  
    |<span data-ttu-id="0af25-120">**啟用**</span><span class="sxs-lookup"><span data-stu-id="0af25-120">**Enable**</span></span>|<span data-ttu-id="0af25-121">False</span><span class="sxs-lookup"><span data-stu-id="0af25-121">False</span></span>|  
    |<span data-ttu-id="0af25-122">**事件端點**</span><span class="sxs-lookup"><span data-stu-id="0af25-122">**Event end-point**</span></span>|<span data-ttu-id="0af25-123">輸入適當的 SAG 端點。</span><span class="sxs-lookup"><span data-stu-id="0af25-123">Type the appropriate SAG end-point.</span></span>|  
    |<span data-ttu-id="0af25-124">**PhysicalFolderName**</span><span class="sxs-lookup"><span data-stu-id="0af25-124">**PhysicalFolderName**</span></span>|<span data-ttu-id="0af25-125">在伺服器上，輸入資料夾的名稱。</span><span class="sxs-lookup"><span data-stu-id="0af25-125">Type the name of the folder on the server.</span></span> <span data-ttu-id="0af25-126">例如，C:\Fileact\ServerLocation。</span><span class="sxs-lookup"><span data-stu-id="0af25-126">For example, C:\Fileact\ServerLocation.</span></span>|  
    |<span data-ttu-id="0af25-127">**PollingInterval**</span><span class="sxs-lookup"><span data-stu-id="0af25-127">**PollingInterval**</span></span>|<span data-ttu-id="0af25-128">輸入適當的間隔 （以秒為單位） 之後，配接器會檢查的檔案傳輸的狀態。</span><span class="sxs-lookup"><span data-stu-id="0af25-128">Type the appropriate interval (in seconds) after which the adapter checks for the status of file transfer.</span></span>|  
    |<span data-ttu-id="0af25-129">**密碼**</span><span class="sxs-lookup"><span data-stu-id="0af25-129">**Password**</span></span>|<span data-ttu-id="0af25-130">輸入您用來連接到 SAG 的密碼。</span><span class="sxs-lookup"><span data-stu-id="0af25-130">Type the password you use to connect to SAG.</span></span> <span data-ttu-id="0af25-131">如需詳細資訊，請參閱 SAG 說明。</span><span class="sxs-lookup"><span data-stu-id="0af25-131">See SAG Help for more information.</span></span>|  
    |<span data-ttu-id="0af25-132">**使用者名稱**</span><span class="sxs-lookup"><span data-stu-id="0af25-132">**User Name**</span></span>|<span data-ttu-id="0af25-133">輸入您用來連接到 SAG 的使用者名稱。</span><span class="sxs-lookup"><span data-stu-id="0af25-133">Type the user name you use to connect to SAG.</span></span>|  
  
5.  <span data-ttu-id="0af25-134">按一下**確定**關閉 FILEACT 傳輸屬性 對話方塊。</span><span class="sxs-lookup"><span data-stu-id="0af25-134">Click **OK** to close the FILEACT Transport Properties dialog box.</span></span>  
  
6.  <span data-ttu-id="0af25-135">按一下**確定**關閉 FILEACT – 配接器處理常式屬性 對話方塊。</span><span class="sxs-lookup"><span data-stu-id="0af25-135">Click **OK** to close the FILEACT – Adapter Handler Properties dialog box.</span></span>  
  
7.  <span data-ttu-id="0af25-136">在訊息方塊中，按一下**確定**，然後重新啟動 FileAct 主控件執行個體。</span><span class="sxs-lookup"><span data-stu-id="0af25-136">In the Message box, click **OK**, and then restart the FileAct host instance.</span></span>  
  
## <a name="complete-steps"></a><span data-ttu-id="0af25-137">完成步驟</span><span class="sxs-lookup"><span data-stu-id="0af25-137">Complete steps</span></span>
 <span data-ttu-id="0af25-138">[FileAct 存放與轉寄的案例](../../adapters-and-accelerators/fileact-interact/fileact-store-and-forward-scenario.md) </span><span class="sxs-lookup"><span data-stu-id="0af25-138">[FileAct Store and Forward Scenario](../../adapters-and-accelerators/fileact-interact/fileact-store-and-forward-scenario.md) </span></span>  
 <span data-ttu-id="0af25-139">[步驟 2： 加入為 FileAct 存放與轉寄實例 Paramfile SWIFTNet 組態](../../adapters-and-accelerators/fileact-interact/step-2-add-swiftnet-configuration-to-paramfile-for-fileact-store-and-forward.md) </span><span class="sxs-lookup"><span data-stu-id="0af25-139">[Step 2: Add SWIFTNet Configuration to the Paramfile for the FileAct Store and Forward Scenario](../../adapters-and-accelerators/fileact-interact/step-2-add-swiftnet-configuration-to-paramfile-for-fileact-store-and-forward.md) </span></span>  
 <span data-ttu-id="0af25-140">[步驟 3： 建立傳送埠和接收埠為 FileAct 存放與轉寄的實例](../../adapters-and-accelerators/fileact-interact/step-3-create-send-ports-and-receive-ports-for-the-fileact-store-and-forward.md) </span><span class="sxs-lookup"><span data-stu-id="0af25-140">[Step 3: Create Send Ports and Receive Ports for the FileAct Store and Forward Scenario](../../adapters-and-accelerators/fileact-interact/step-3-create-send-ports-and-receive-ports-for-the-fileact-store-and-forward.md) </span></span>  
 [<span data-ttu-id="0af25-141">步驟 4： 測試 FileAct 存放與轉寄的端對端案例</span><span class="sxs-lookup"><span data-stu-id="0af25-141">Step 4: Test FileAct Store and Forward End-to-End Scenario</span></span>](../../adapters-and-accelerators/fileact-interact/step-4-test-fileact-store-and-forward-end-to-end-scenario.md)