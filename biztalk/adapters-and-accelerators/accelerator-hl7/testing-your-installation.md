---
title: "測試安裝 |Microsoft 文件"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- testing installation
- installing, testing installation
ms.assetid: db27a75c-db7f-46ff-b8ef-2624ff18dcc8
caps.latest.revision: "7"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 8a813634f2fe03d427ef5d0b14688ecca977f571
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/20/2017
---
# <a name="testing-your-installation"></a><span data-ttu-id="783f5-102">測試您的安裝</span><span class="sxs-lookup"><span data-stu-id="783f5-102">Testing Your Installation</span></span>
<span data-ttu-id="783f5-103">您可以設定您[!INCLUDE[HL7_CurrentVersion_FirstRef](../../includes/hl7-currentversion-firstref-md.md)]進行測試以手動方式執行端對端教學課程，或執行端對端教學課程程式的安裝。</span><span class="sxs-lookup"><span data-stu-id="783f5-103">You can set up your [!INCLUDE[HL7_CurrentVersion_FirstRef](../../includes/hl7-currentversion-firstref-md.md)] installation for testing either by manually running through the end-to-end tutorial or by executing the end-to-end tutorial program.</span></span> <span data-ttu-id="783f5-104">若要執行程式，請按一下**啟動教學課程**按鈕在安裝期間，或是執行 C:\Program Files\Microsoft BizTalk EndToEndTutorial.exe\<版本 > Accelerator for HL7\SDK\End 端對端教學課程（在執行安裝和組態） 之後的資料夾。</span><span class="sxs-lookup"><span data-stu-id="783f5-104">To exercise the program, either click the **Launch Tutorial** button during setup or execute EndToEndTutorial.exe in the C:\Program Files\Microsoft BizTalk \<version> Accelerator for HL7\SDK\End-to-End Tutorial folder (after running installation and configuration).</span></span> <span data-ttu-id="783f5-105">這些自動化的動作將會執行相同的設定步驟，您必須手動執行透過本教學課程執行。</span><span class="sxs-lookup"><span data-stu-id="783f5-105">Either of these automated actions will perform the same setup steps that you would manually perform by running through the tutorial.</span></span> <span data-ttu-id="783f5-106">端對端教學課程程式會執行下列動作：</span><span class="sxs-lookup"><span data-stu-id="783f5-106">The end-to-end tutorial program does the following:</span></span>  
  
-   <span data-ttu-id="783f5-107">部署 MSH 和通知結構描述</span><span class="sxs-lookup"><span data-stu-id="783f5-107">Deploys MSH and ACK schemas</span></span>  
  
-   <span data-ttu-id="783f5-108">部署版本 2.3.1 通用結構描述</span><span class="sxs-lookup"><span data-stu-id="783f5-108">Deploys Version 2.3.1 common schemas</span></span>  
  
-   <span data-ttu-id="783f5-109">部署 ADT 結構描述</span><span class="sxs-lookup"><span data-stu-id="783f5-109">Deploys ADT schemas</span></span>  
  
-   <span data-ttu-id="783f5-110">建立 Tutorial_1WayReceive 接收埠</span><span class="sxs-lookup"><span data-stu-id="783f5-110">Creates the Tutorial_1WayReceive receive port</span></span>  
  
-   <span data-ttu-id="783f5-111">建立 Tutorial_MLLPReceive 接收位置</span><span class="sxs-lookup"><span data-stu-id="783f5-111">Creates the Tutorial_MLLPReceive receive location</span></span>  
  
-   <span data-ttu-id="783f5-112">建立 Tutorial_BTAHL7PickUp 接收埠</span><span class="sxs-lookup"><span data-stu-id="783f5-112">Creates the Tutorial_BTAHL7PickUp receive port</span></span>  
  
-   <span data-ttu-id="783f5-113">建立 Tutorial_FileReceiveLoc 接收位置</span><span class="sxs-lookup"><span data-stu-id="783f5-113">Creates the Tutorial_FileReceiveLoc receive location</span></span>  
  
-   <span data-ttu-id="783f5-114">建立 Tutorial_sendAck_ADT 傳送埠</span><span class="sxs-lookup"><span data-stu-id="783f5-114">Creates the Tutorial_sendAck_ADT send port</span></span>  
  
-   <span data-ttu-id="783f5-115">建立 Tutorial_sendMsg_RX 傳送埠</span><span class="sxs-lookup"><span data-stu-id="783f5-115">Creates the Tutorial_sendMsg_RX send port</span></span>  
  
-   <span data-ttu-id="783f5-116">建立 Tutorial_BTAHL7Drop 傳送埠</span><span class="sxs-lookup"><span data-stu-id="783f5-116">Creates the Tutorial_BTAHL7Drop send port</span></span>  
  
-   <span data-ttu-id="783f5-117">建立 Tutorial_MLLPSend 傳送埠</span><span class="sxs-lookup"><span data-stu-id="783f5-117">Creates the Tutorial_MLLPSend send port</span></span>  
  
-   <span data-ttu-id="783f5-118">建立 Tutorial_ADTSystem 合作對象</span><span class="sxs-lookup"><span data-stu-id="783f5-118">Creates the Tutorial_ADTSystem party</span></span>  
  
-   <span data-ttu-id="783f5-119">建立 Tutorial_RXSystem 合作對象</span><span class="sxs-lookup"><span data-stu-id="783f5-119">Creates the Tutorial_RXSystem party</span></span>  
  
-   <span data-ttu-id="783f5-120">建立 Tutorial_HISystem 合作對象</span><span class="sxs-lookup"><span data-stu-id="783f5-120">Creates the Tutorial_HISystem party</span></span>  
  
-   <span data-ttu-id="783f5-121">重新啟動 BizTalk 服務</span><span class="sxs-lookup"><span data-stu-id="783f5-121">Restarts the BizTalk Service</span></span>  
  
 <span data-ttu-id="783f5-122">如果您有執行端對端教學課程程式，您可以省略 for HL7 預先定義的資料夾中的測試執行個體。</span><span class="sxs-lookup"><span data-stu-id="783f5-122">If you have executed the end-to-end tutorial program, you can drop a test instance for HL7 in a pre-defined folder.</span></span> <span data-ttu-id="783f5-123">該資料夾相關聯的接收管線會拾取訊息，並予以處理。</span><span class="sxs-lookup"><span data-stu-id="783f5-123">The receive pipeline associated with the folder picks up the message and processes it.</span></span> <span data-ttu-id="783f5-124">根據篩選器，傳送管線將傳送至目的地資料夾的文件。</span><span class="sxs-lookup"><span data-stu-id="783f5-124">Based on filters, a send pipeline routes the document to the destination folder.</span></span> <span data-ttu-id="783f5-125">這個簡單的 「 往返 」 會執行基本建置組塊的[!INCLUDE[btsCoName](../../includes/btsconame-md.md)] [!INCLUDE[btaBTAHL7NoNumber](../../includes/btabtahl7nonumber-md.md)] ([!INCLUDE[btaBTAHL71.3abbrevnonumber](../../includes/btabtahl71-3abbrevnonumber-md.md)]) 引擎，並確認您的安裝。</span><span class="sxs-lookup"><span data-stu-id="783f5-125">This simple "round-trip" exercises the basic building blocks of the [!INCLUDE[btsCoName](../../includes/btsconame-md.md)][!INCLUDE[btaBTAHL7NoNumber](../../includes/btabtahl7nonumber-md.md)] ([!INCLUDE[btaBTAHL71.3abbrevnonumber](../../includes/btabtahl71-3abbrevnonumber-md.md)]) engine and confirms your installation.</span></span>  
  
### <a name="to-test-your-installation"></a><span data-ttu-id="783f5-126">若要測試您的安裝</span><span class="sxs-lookup"><span data-stu-id="783f5-126">To test your installation</span></span>  
  
1.  <span data-ttu-id="783f5-127">使用[!INCLUDE[btsWinNoVersion](../../includes/btswinnoversion-md.md)]總管 中，瀏覽至\<*磁碟機*>: \Program Files\Microsoft BizTalk\<版本 > Accelerator for HL7\SDK\End 端對端教學課程的資料夾。</span><span class="sxs-lookup"><span data-stu-id="783f5-127">Using [!INCLUDE[btsWinNoVersion](../../includes/btswinnoversion-md.md)] Explorer, browse to the \<*drive*>:\Program Files\Microsoft BizTalk \<version> Accelerator for HL7\SDK\End-to-End Tutorial folder.</span></span>  
  
2.  <span data-ttu-id="783f5-128">以滑鼠右鍵按一下**TutorialSampleInstance.txt**檔案，然後再按一下**複製**。</span><span class="sxs-lookup"><span data-stu-id="783f5-128">Right-click the **TutorialSampleInstance.txt** file, and then click **Copy**.</span></span>  
  
3.  <span data-ttu-id="783f5-129">使用[!INCLUDE[btsWinNoVersion](../../includes/btswinnoversion-md.md)]總管 中，瀏覽至\<*磁碟機*>: \Program Files\Microsoft BizTalk\<版本 > Accelerator for HL7\SDK\End 端對端 Tutorial\Tutorial_BTAHL7PickUp 資料夾。</span><span class="sxs-lookup"><span data-stu-id="783f5-129">Using [!INCLUDE[btsWinNoVersion](../../includes/btswinnoversion-md.md)] Explorer, browse to the \<*drive*>:\Program Files\Microsoft BizTalk \<version> Accelerator for HL7\SDK\End-to-End Tutorial\Tutorial_BTAHL7PickUp folder.</span></span>  
  
4.  <span data-ttu-id="783f5-130">以滑鼠右鍵按一下資料夾，然後按一下**貼上**。</span><span class="sxs-lookup"><span data-stu-id="783f5-130">Right-click the folder, and then click **Paste**.</span></span>  
  
5.  <span data-ttu-id="783f5-131">使用[!INCLUDE[btsWinNoVersion](../../includes/btswinnoversion-md.md)]總管 中，瀏覽至\<*磁碟機*>: \Program Files\Microsoft BizTalk\<版本 > Accelerator for HL7\SDK\End 端對端 Tutorial\Tutorial_BTAHL7Drop 資料夾。</span><span class="sxs-lookup"><span data-stu-id="783f5-131">Using [!INCLUDE[btsWinNoVersion](../../includes/btswinnoversion-md.md)] Explorer, browse to the \<*drive*>:\Program Files\Microsoft BizTalk \<version> Accelerator for HL7\SDK\End-to-End Tutorial\Tutorial_BTAHL7Drop folder.</span></span>  
  
     <span data-ttu-id="783f5-132">您可以確認您的安裝是否成功，如果已處理的執行個體出現在**Tutorial_BTAHL7Drop**資料夾\< *Guid*>.txt。</span><span class="sxs-lookup"><span data-stu-id="783f5-132">You can verify if your installation was successful if the processed instance appears in the **Tutorial_BTAHL7Drop** folder as \<*Guid*>.txt.</span></span>  
  
 <span data-ttu-id="783f5-133">繼續進行下一個步驟中，[準備使用本教學課程](../../adapters-and-accelerators/accelerator-hl7/preparing-to-use-the-tutorial2.md)。</span><span class="sxs-lookup"><span data-stu-id="783f5-133">Proceed to the next step, [Preparing to Use the Tutorial](../../adapters-and-accelerators/accelerator-hl7/preparing-to-use-the-tutorial2.md).</span></span>