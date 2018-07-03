---
title: Loopback 教學課程 |Microsoft Docs
ms.custom: ''
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- loopbacks, tutorial
- loopback tutorial, about the loopback tutorial
- loopback tutorial
- tutorials, loopback tutorial
ms.assetid: 0f69c1f1-4039-4949-8eed-127ceabbc3cc
caps.latest.revision: 5
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 97714d5f7e604acbb798739fc4eb545a07968980
ms.sourcegitcommit: 266308ec5c6a9d8d80ff298ee6051b4843c5d626
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/27/2018
ms.locfileid: "37010095"
---
# <a name="loopback-tutorial"></a><span data-ttu-id="2a5ec-102">Loopback 教學課程</span><span class="sxs-lookup"><span data-stu-id="2a5ec-102">Loopback Tutorial</span></span>
<span data-ttu-id="2a5ec-103">本教學課程包含詳細的步驟，說明如何使用 Microsoft®[!INCLUDE[BTARN_CurrentVersion_FirstRef](../../includes/btarn-currentversion-firstref-md.md)]來模擬在單一電腦上的主要和夥伴組織之間的程序實作。</span><span class="sxs-lookup"><span data-stu-id="2a5ec-103">This tutorial contains detailed steps that describe how you can use Microsoft® [!INCLUDE[BTARN_CurrentVersion_FirstRef](../../includes/btarn-currentversion-firstref-md.md)] to simulate a process implementation between the home and partner organization on a single computer.</span></span>  
  
 <span data-ttu-id="2a5ec-104">在真實的生產環境，您的交易夥伴組織實作會是在遠端電腦上。</span><span class="sxs-lookup"><span data-stu-id="2a5ec-104">In a real production environment, your partner organization implementation resides on a remote computer.</span></span> <span data-ttu-id="2a5ec-105">此教學課程使用回送公用程式建立鏡像交易夥伴協議，以在相同電腦上模擬交易夥伴。</span><span class="sxs-lookup"><span data-stu-id="2a5ec-105">This tutorial uses the Loopback utility to create a mirror trading agreement to simulate the trading partner on the same computer.</span></span> <span data-ttu-id="2a5ec-106">單一電腦的回送實例只適用於開發和測試。</span><span class="sxs-lookup"><span data-stu-id="2a5ec-106">Using a single computer loop-back scenario works for development and test purposes.</span></span> <span data-ttu-id="2a5ec-107">建議您，不要在實際執行環境中使用回送公用程式。</span><span class="sxs-lookup"><span data-stu-id="2a5ec-107">It is recommended that you do not to use the Loopback utility in a production environment.</span></span>  
  
 <span data-ttu-id="2a5ec-108">此回送實例不支援簽章訊息，因此也不支援不可否認性。</span><span class="sxs-lookup"><span data-stu-id="2a5ec-108">This loopback scenario does not support signing messages, and thus does not support non-repudiation.</span></span>  
  
 <span data-ttu-id="2a5ec-109">如果您設定憑證授權單位，並且已有用於測試的加密私密金鑰，此實例便會支援訊息加密。</span><span class="sxs-lookup"><span data-stu-id="2a5ec-109">This scenario supports encryption of messages if you have a certification authority configured, and you have a private key for encryption available for test purposes.</span></span>  
  
 <span data-ttu-id="2a5ec-110">在此教學課程中，您將建立主要組織、交易夥伴組織、交易協議、使用回送公用程式建立鏡像協議，並且執行範例程序以確認回送實例。</span><span class="sxs-lookup"><span data-stu-id="2a5ec-110">In this tutorial, you create a home organization, a partner organization, a trade agreement, use the Loopback utility to create a mirror agreement, and then run a sample process to verify the loop-back scenario.</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="2a5ec-111">本節內容</span><span class="sxs-lookup"><span data-stu-id="2a5ec-111">In This Section</span></span>  
  
-   [<span data-ttu-id="2a5ec-112">教學課程的事前準備</span><span class="sxs-lookup"><span data-stu-id="2a5ec-112">Preparing for the Tutorial</span></span>](../../adapters-and-accelerators/accelerator-rosettanet/preparing-for-the-tutorial.md)  
  
-   [<span data-ttu-id="2a5ec-113">步驟 1：建立主要組織</span><span class="sxs-lookup"><span data-stu-id="2a5ec-113">Step 1: Create the Home Organization</span></span>](../../adapters-and-accelerators/accelerator-rosettanet/step-1-create-the-home-organization.md)  
  
-   [<span data-ttu-id="2a5ec-114">步驟 2：建立交易夥伴組織</span><span class="sxs-lookup"><span data-stu-id="2a5ec-114">Step 2: Create the Partner Organization</span></span>](../../adapters-and-accelerators/accelerator-rosettanet/step-2-create-the-partner-organization.md)  
  
-   [<span data-ttu-id="2a5ec-115">步驟 3：編輯交易夥伴介面程序</span><span class="sxs-lookup"><span data-stu-id="2a5ec-115">Step 3: Edit the Partner Interface Process</span></span>](../../adapters-and-accelerators/accelerator-rosettanet/step-3-edit-the-partner-interface-process.md)  
  
-   [<span data-ttu-id="2a5ec-116">步驟 4：建立交易協議</span><span class="sxs-lookup"><span data-stu-id="2a5ec-116">Step 4: Create a Trade Agreement</span></span>](../../adapters-and-accelerators/accelerator-rosettanet/step-4-create-a-trade-agreement.md)  
  
-   [<span data-ttu-id="2a5ec-117">步驟 5：建立鏡像協議</span><span class="sxs-lookup"><span data-stu-id="2a5ec-117">Step 5: Create a Mirror Agreement</span></span>](../../adapters-and-accelerators/accelerator-rosettanet/step-5-create-a-mirror-agreement.md)  
  
-   [<span data-ttu-id="2a5ec-118">步驟 6：啟動協調流程</span><span class="sxs-lookup"><span data-stu-id="2a5ec-118">Step 6: Start Orchestrations</span></span>](../../adapters-and-accelerators/accelerator-rosettanet/step-6-start-orchestrations.md)  
  
-   [<span data-ttu-id="2a5ec-119">步驟 7：建立範例 LOB 訊息</span><span class="sxs-lookup"><span data-stu-id="2a5ec-119">Step 7: Create a Sample LOB Message</span></span>](../../adapters-and-accelerators/accelerator-rosettanet/step-7-create-a-sample-lob-message.md)  
  
-   [<span data-ttu-id="2a5ec-120">步驟 8：檢視 BTARN 資料庫中的訊息</span><span class="sxs-lookup"><span data-stu-id="2a5ec-120">Step 8: View Messages in the BTARN Databases</span></span>](../../adapters-and-accelerators/accelerator-rosettanet/step-8-view-messages-in-the-btarn-databases.md)