---
title: BizTalk FileAct 和互動配接器端對端教學課程 |Microsoft Docs
ms.custom: ''
ms.date: 2015-12-10
ms.prod: biztalk-server
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 73fbfb10-73e8-4365-a943-bcb9055f4f74
caps.latest.revision: 13
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: af083b0e38d372c18bca4496033983cd7f579347
ms.sourcegitcommit: 266308ec5c6a9d8d80ff298ee6051b4843c5d626
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/27/2018
ms.locfileid: "37014799"
---
# <a name="biztalk-fileact-and-interact-adapters-end-to-end-tutorial"></a><span data-ttu-id="dd019-102">BizTalk FileAct 和互動配接器端對端教學課程</span><span class="sxs-lookup"><span data-stu-id="dd019-102">BizTalk FileAct and InterAct Adapters End-to-End Tutorial</span></span>
<span data-ttu-id="dd019-103">The Microsoft®[!INCLUDE[swift_adapter](../../includes/swift-adapter-md.md)]端對端教學課程提供如何使用的特定資訊[!INCLUDE[swift_adapter](../../includes/swift-adapter-md.md)]和[!INCLUDE[btsBizTalkServerNoVersion](../../includes/btsbiztalkservernoversion-md.md)]來設定即時和儲存和轉送訊息交換案例。</span><span class="sxs-lookup"><span data-stu-id="dd019-103">The Microsoft® [!INCLUDE[swift_adapter](../../includes/swift-adapter-md.md)] End-to-End Tutorial provides specific information about how you can use [!INCLUDE[swift_adapter](../../includes/swift-adapter-md.md)] and [!INCLUDE[btsBizTalkServerNoVersion](../../includes/btsbiztalkservernoversion-md.md)] to set up real-time and store and forward message exchange scenarios.</span></span>  
  
 <span data-ttu-id="dd019-104">[!INCLUDE[swift_adapter](../../includes/swift-adapter-md.md)]端對端教學課程提供四個不同的案例，包括每一種解決方案的教學課程的形式的詳細的步驟。</span><span class="sxs-lookup"><span data-stu-id="dd019-104">The [!INCLUDE[swift_adapter](../../includes/swift-adapter-md.md)] End-To-End Tutorial provides four separate scenarios that include detailed steps in the form of tutorials for each type of solution.</span></span> <span data-ttu-id="dd019-105">這些教學課程之前，您應該了解 BizTalk Server 的基本概念並熟悉 SWIFT Alliance 閘道 (SAG) 文件。</span><span class="sxs-lookup"><span data-stu-id="dd019-105">Before you begin these tutorials, you should understand the fundamental concepts surrounding BizTalk Server, and be familiar with the SWIFT Alliance Gateway (SAG) documentation.</span></span>  
  
 <span data-ttu-id="dd019-106">A4SWIFT 端對端教學課程提供您詳細的步驟來設定即時與 FileAct 和 InterAct 配接器使用的儲存和轉寄案例 A4Swift。</span><span class="sxs-lookup"><span data-stu-id="dd019-106">The A4SWIFT end-to-end tutorial provides you with detailed steps to configure real-time and store-and-forward scenarios with both the FileAct and InterAct adapters for A4Swift.</span></span> <span data-ttu-id="dd019-107">針對每個案例中，您將會執行下列作業：</span><span class="sxs-lookup"><span data-stu-id="dd019-107">For each of the scenarios, you will do the following:</span></span>  
  
- <span data-ttu-id="dd019-108">設定 SWIFT 配接器</span><span class="sxs-lookup"><span data-stu-id="dd019-108">Configure the SWIFT adapter</span></span>  
  
- <span data-ttu-id="dd019-109">設定 SWIFTNet paramfile</span><span class="sxs-lookup"><span data-stu-id="dd019-109">Configure the SWIFTNet paramfile</span></span>  
  
- <span data-ttu-id="dd019-110">建立傳送埠和接收埠</span><span class="sxs-lookup"><span data-stu-id="dd019-110">Create send ports and receive ports</span></span>  
  
- <span data-ttu-id="dd019-111">測試案例</span><span class="sxs-lookup"><span data-stu-id="dd019-111">Test the scenario</span></span>  
  
  <span data-ttu-id="dd019-112">在本教學課程中，您將會進行兩個角色： 傳送者和接收者。</span><span class="sxs-lookup"><span data-stu-id="dd019-112">In this tutorial, you will play two roles: Sender and Receiver.</span></span> <span data-ttu-id="dd019-113">您將建立連接埠將訊息傳送和接收它們。</span><span class="sxs-lookup"><span data-stu-id="dd019-113">You will create ports that send messages and receive them.</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="dd019-114">本節內容</span><span class="sxs-lookup"><span data-stu-id="dd019-114">In This Section</span></span>  
  
-   [<span data-ttu-id="dd019-115">準備使用教學課程</span><span class="sxs-lookup"><span data-stu-id="dd019-115">Preparing to Use the Tutorial</span></span>](../../adapters-and-accelerators/fileact-interact/preparing-to-use-the-tutorial1.md)  
  
-   [<span data-ttu-id="dd019-116">InterAct 即時案例</span><span class="sxs-lookup"><span data-stu-id="dd019-116">InterAct Real-Time Scenario</span></span>](../../adapters-and-accelerators/fileact-interact/interact-real-time-scenario.md)  
  
-   [<span data-ttu-id="dd019-117">InterAct 儲存和轉寄 (推送) 案例</span><span class="sxs-lookup"><span data-stu-id="dd019-117">InterAct Store and Forward (Push) Scenario</span></span>](../../adapters-and-accelerators/fileact-interact/interact-store-and-forward-push-scenario.md)  
  
-   [<span data-ttu-id="dd019-118">FileAct 即時案例</span><span class="sxs-lookup"><span data-stu-id="dd019-118">FileAct Real-Time Scenario</span></span>](../../adapters-and-accelerators/fileact-interact/fileact-real-time-scenario.md)  
  
-   [<span data-ttu-id="dd019-119">FileAct 儲存和轉寄案例</span><span class="sxs-lookup"><span data-stu-id="dd019-119">FileAct Store and Forward Scenario</span></span>](../../adapters-and-accelerators/fileact-interact/fileact-store-and-forward-scenario.md)