---
title: 測試您的安裝 |Microsoft Docs
ms.custom: ''
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- testing installation
- installing, testing installation
ms.assetid: db27a75c-db7f-46ff-b8ef-2624ff18dcc8
caps.latest.revision: 7
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 6d2d94ffce01bd299ad836b7f1fb7c82f66a8196
ms.sourcegitcommit: 266308ec5c6a9d8d80ff298ee6051b4843c5d626
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/27/2018
ms.locfileid: "36971903"
---
# <a name="testing-your-installation"></a><span data-ttu-id="12fcf-102">測試您的安裝</span><span class="sxs-lookup"><span data-stu-id="12fcf-102">Testing Your Installation</span></span>
<span data-ttu-id="12fcf-103">您可以設定您[!INCLUDE[HL7_CurrentVersion_FirstRef](../../includes/hl7-currentversion-firstref-md.md)]進行測試以手動方式執行端對端教學課程，或執行端對端教學課程程式的安裝。</span><span class="sxs-lookup"><span data-stu-id="12fcf-103">You can set up your [!INCLUDE[HL7_CurrentVersion_FirstRef](../../includes/hl7-currentversion-firstref-md.md)] installation for testing either by manually running through the end-to-end tutorial or by executing the end-to-end tutorial program.</span></span> <span data-ttu-id="12fcf-104">若要執行程式，請按一下**啟動的教學課程**按鈕在安裝期間，或在 C:\Program Files\Microsoft BizTalk 執行 EndToEndTutorial.exe\<版本\>Accelerator for HL7\SDK\端對端教學課程的資料夾 （在之後執行安裝和設定）。</span><span class="sxs-lookup"><span data-stu-id="12fcf-104">To exercise the program, either click the **Launch Tutorial** button during setup or execute EndToEndTutorial.exe in the C:\Program Files\Microsoft BizTalk \<version\> Accelerator for HL7\SDK\End-to-End Tutorial folder (after running installation and configuration).</span></span> <span data-ttu-id="12fcf-105">這些自動化動作會執行相同的安裝步驟，您會以手動方式執行來完成教學課程。</span><span class="sxs-lookup"><span data-stu-id="12fcf-105">Either of these automated actions will perform the same setup steps that you would manually perform by running through the tutorial.</span></span> <span data-ttu-id="12fcf-106">端對端教學課程程式會執行下列動作：</span><span class="sxs-lookup"><span data-stu-id="12fcf-106">The end-to-end tutorial program does the following:</span></span>  
  
- <span data-ttu-id="12fcf-107">部署 MSH 和通知結構描述</span><span class="sxs-lookup"><span data-stu-id="12fcf-107">Deploys MSH and ACK schemas</span></span>  
  
- <span data-ttu-id="12fcf-108">部署第 2.3.1 版通用結構描述</span><span class="sxs-lookup"><span data-stu-id="12fcf-108">Deploys Version 2.3.1 common schemas</span></span>  
  
- <span data-ttu-id="12fcf-109">部署 ADT 結構描述</span><span class="sxs-lookup"><span data-stu-id="12fcf-109">Deploys ADT schemas</span></span>  
  
- <span data-ttu-id="12fcf-110">建立 Tutorial_1WayReceive 接收埠</span><span class="sxs-lookup"><span data-stu-id="12fcf-110">Creates the Tutorial_1WayReceive receive port</span></span>  
  
- <span data-ttu-id="12fcf-111">建立 Tutorial_MLLPReceive 接收位置</span><span class="sxs-lookup"><span data-stu-id="12fcf-111">Creates the Tutorial_MLLPReceive receive location</span></span>  
  
- <span data-ttu-id="12fcf-112">建立 Tutorial_BTAHL7PickUp 接收埠</span><span class="sxs-lookup"><span data-stu-id="12fcf-112">Creates the Tutorial_BTAHL7PickUp receive port</span></span>  
  
- <span data-ttu-id="12fcf-113">建立 Tutorial_FileReceiveLoc 接收位置</span><span class="sxs-lookup"><span data-stu-id="12fcf-113">Creates the Tutorial_FileReceiveLoc receive location</span></span>  
  
- <span data-ttu-id="12fcf-114">建立 Tutorial_sendAck_ADT 傳送埠</span><span class="sxs-lookup"><span data-stu-id="12fcf-114">Creates the Tutorial_sendAck_ADT send port</span></span>  
  
- <span data-ttu-id="12fcf-115">建立 Tutorial_sendMsg_RX 傳送埠</span><span class="sxs-lookup"><span data-stu-id="12fcf-115">Creates the Tutorial_sendMsg_RX send port</span></span>  
  
- <span data-ttu-id="12fcf-116">建立 Tutorial_BTAHL7Drop 傳送埠</span><span class="sxs-lookup"><span data-stu-id="12fcf-116">Creates the Tutorial_BTAHL7Drop send port</span></span>  
  
- <span data-ttu-id="12fcf-117">建立 Tutorial_MLLPSend 傳送埠</span><span class="sxs-lookup"><span data-stu-id="12fcf-117">Creates the Tutorial_MLLPSend send port</span></span>  
  
- <span data-ttu-id="12fcf-118">建立 Tutorial_ADTSystem 合作對象</span><span class="sxs-lookup"><span data-stu-id="12fcf-118">Creates the Tutorial_ADTSystem party</span></span>  
  
- <span data-ttu-id="12fcf-119">建立 Tutorial_RXSystem 合作對象</span><span class="sxs-lookup"><span data-stu-id="12fcf-119">Creates the Tutorial_RXSystem party</span></span>  
  
- <span data-ttu-id="12fcf-120">建立 Tutorial_HISystem 合作對象</span><span class="sxs-lookup"><span data-stu-id="12fcf-120">Creates the Tutorial_HISystem party</span></span>  
  
- <span data-ttu-id="12fcf-121">重新啟動 BizTalk 服務</span><span class="sxs-lookup"><span data-stu-id="12fcf-121">Restarts the BizTalk Service</span></span>  
  
  <span data-ttu-id="12fcf-122">如果您已執行的端對端教學課程的程式，您可以省略 for HL7 的預先定義的資料夾中的測試執行個體。</span><span class="sxs-lookup"><span data-stu-id="12fcf-122">If you have executed the end-to-end tutorial program, you can drop a test instance for HL7 in a pre-defined folder.</span></span> <span data-ttu-id="12fcf-123">與資料夾相關聯的接收管線會拾取訊息，並予以處理。</span><span class="sxs-lookup"><span data-stu-id="12fcf-123">The receive pipeline associated with the folder picks up the message and processes it.</span></span> <span data-ttu-id="12fcf-124">根據篩選器，傳送管線將傳送至目的地資料夾的文件。</span><span class="sxs-lookup"><span data-stu-id="12fcf-124">Based on filters, a send pipeline routes the document to the destination folder.</span></span> <span data-ttu-id="12fcf-125">這個簡單的 「 往返 」 練習 Microsoft 的基本建置組塊[!INCLUDE[btaBTAHL7NoNumber](../../includes/btabtahl7nonumber-md.md)]([!INCLUDE[btaBTAHL71.3abbrevnonumber](../../includes/btabtahl71-3abbrevnonumber-md.md)]) 引擎，並確認您的安裝。</span><span class="sxs-lookup"><span data-stu-id="12fcf-125">This simple "round-trip" exercises the basic building blocks of the Microsoft [!INCLUDE[btaBTAHL7NoNumber](../../includes/btabtahl7nonumber-md.md)] ([!INCLUDE[btaBTAHL71.3abbrevnonumber](../../includes/btabtahl71-3abbrevnonumber-md.md)]) engine and confirms your installation.</span></span>  
  
### <a name="to-test-your-installation"></a><span data-ttu-id="12fcf-126">若要測試您的安裝</span><span class="sxs-lookup"><span data-stu-id="12fcf-126">To test your installation</span></span>  
  
1. <span data-ttu-id="12fcf-127">使用[!INCLUDE[btsWinNoVersion](../../includes/btswinnoversion-md.md)]總管 中，瀏覽至\<*磁碟機*\>: \Program Files\Microsoft BizTalk\<版本\>Accelerator for HL7\SDK\End 端對端教學課程的資料夾。</span><span class="sxs-lookup"><span data-stu-id="12fcf-127">Using [!INCLUDE[btsWinNoVersion](../../includes/btswinnoversion-md.md)] Explorer, browse to the \<*drive*\>:\Program Files\Microsoft BizTalk \<version\> Accelerator for HL7\SDK\End-to-End Tutorial folder.</span></span>  
  
2. <span data-ttu-id="12fcf-128">以滑鼠右鍵按一下**TutorialSampleInstance.txt**檔案，然後再按一下**複製**。</span><span class="sxs-lookup"><span data-stu-id="12fcf-128">Right-click the **TutorialSampleInstance.txt** file, and then click **Copy**.</span></span>  
  
3. <span data-ttu-id="12fcf-129">使用[!INCLUDE[btsWinNoVersion](../../includes/btswinnoversion-md.md)]總管 中，瀏覽至\<*磁碟機*\>: \Program Files\Microsoft BizTalk\<版本\>Accelerator for HL7\SDK\End 端對端 Tutorial\Tutorial_BTAHL7PickUp 資料夾中。</span><span class="sxs-lookup"><span data-stu-id="12fcf-129">Using [!INCLUDE[btsWinNoVersion](../../includes/btswinnoversion-md.md)] Explorer, browse to the \<*drive*\>:\Program Files\Microsoft BizTalk \<version\> Accelerator for HL7\SDK\End-to-End Tutorial\Tutorial_BTAHL7PickUp folder.</span></span>  
  
4. <span data-ttu-id="12fcf-130">以滑鼠右鍵按一下資料夾，然後按一下**貼上**。</span><span class="sxs-lookup"><span data-stu-id="12fcf-130">Right-click the folder, and then click **Paste**.</span></span>  
  
5. <span data-ttu-id="12fcf-131">使用[!INCLUDE[btsWinNoVersion](../../includes/btswinnoversion-md.md)]總管 中，瀏覽至\<*磁碟機*\>: \Program Files\Microsoft BizTalk\<版本\>Accelerator for HL7\SDK\End 端對端 Tutorial\Tutorial_BTAHL7Drop 資料夾中。</span><span class="sxs-lookup"><span data-stu-id="12fcf-131">Using [!INCLUDE[btsWinNoVersion](../../includes/btswinnoversion-md.md)] Explorer, browse to the \<*drive*\>:\Program Files\Microsoft BizTalk \<version\> Accelerator for HL7\SDK\End-to-End Tutorial\Tutorial_BTAHL7Drop folder.</span></span>  
  
    <span data-ttu-id="12fcf-132">您可以確認您的安裝是否成功，如果已處理的執行個體出現在**Tutorial_BTAHL7Drop**的資料夾\< *Guid*\>.txt。</span><span class="sxs-lookup"><span data-stu-id="12fcf-132">You can verify if your installation was successful if the processed instance appears in the **Tutorial_BTAHL7Drop** folder as \<*Guid*\>.txt.</span></span>  
  
   <span data-ttu-id="12fcf-133">請繼續進行下一個步驟中，[準備使用教學課程](../../adapters-and-accelerators/accelerator-hl7/preparing-to-use-the-tutorial2.md)。</span><span class="sxs-lookup"><span data-stu-id="12fcf-133">Proceed to the next step, [Preparing to Use the Tutorial](../../adapters-and-accelerators/accelerator-hl7/preparing-to-use-the-tutorial2.md).</span></span>