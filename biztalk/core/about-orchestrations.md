---
title: "關於協調流程 |Microsoft 文件"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- orchestrations
- Orchestration Designer
- orchestrations, about orchestrations
- Orchestration Designer, about Orchestration Designer
ms.assetid: c0d9a3fb-da87-42cc-9e9e-e2c37232e606
caps.latest.revision: "18"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 0bd3c1abeeb2c42c399a54aea4ba0128cc19bcd8
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/20/2017
---
# <a name="about-orchestrations"></a><span data-ttu-id="b4f6a-102">關於協調流程</span><span class="sxs-lookup"><span data-stu-id="b4f6a-102">About Orchestrations</span></span>
<span data-ttu-id="b4f6a-103">協調流程是一種靈活、功能強大的工具，用於代表以 XLANG/s 語言為基礎的可執行商務程序。</span><span class="sxs-lookup"><span data-stu-id="b4f6a-103">An orchestration is a flexible, powerful tool for representing an executable business process based on XLANG/s language.</span></span> <span data-ttu-id="b4f6a-104">XLANG/s 可視為具有某些 C# 運算式功能的訊息語言。</span><span class="sxs-lookup"><span data-stu-id="b4f6a-104">XLANG/s can be viewed as a messaging language with some of the expression capabilities of C#.</span></span> <span data-ttu-id="b4f6a-105">您可以在直覺式的視覺繪圖中，設計流程、解譯及產生資料、呼叫自訂程式碼，以及組織完整的流程，而在執行階段中，BizTalk 協調流程引擎則會執行 XLANG/s 檔案，也就是 BizTalk 協調流程設計師所產生的可執行商務流程。</span><span class="sxs-lookup"><span data-stu-id="b4f6a-105">You can design flow, interpret and generate data, call custom code, and organize the entire process in an intuitive visual drawing, and at run time, the BizTalk Orchestration Engine executes XLANG/s files which are the executable business processes that are produced by BizTalk Orchestration Designer.</span></span>  
  
 <span data-ttu-id="b4f6a-106">訊息、對訊息執行的傳送與接收動作、傳輸訊息時的連接埠，都是協調流程的基礎項目。</span><span class="sxs-lookup"><span data-stu-id="b4f6a-106">Messages, the send and receive actions that operate on them, and the ports through which they are transported are all fundamental elements of an orchestration.</span></span> <span data-ttu-id="b4f6a-107">訊息是協調流程和外界通訊及進行電子商務的媒介。</span><span class="sxs-lookup"><span data-stu-id="b4f6a-107">The message is the medium by which orchestrations communicate with the outside world and by which e-business is conducted.</span></span>  
  
 <span data-ttu-id="b4f6a-108">**接收**和**傳送**圖形封裝您需要為您的協調流程接收訊息，並從該處傳送訊息的功能。</span><span class="sxs-lookup"><span data-stu-id="b4f6a-108">**Receive** and **Send** shapes encapsulate the functionality you need to receive messages into your orchestration and send messages from it.</span></span> <span data-ttu-id="b4f6a-109">您應該熟悉「協調流程設計師」所提供用來代表您協調流程之邏輯流程的各種圖形。</span><span class="sxs-lookup"><span data-stu-id="b4f6a-109">You should become familiar with the various shapes that Orchestration Designer provides to represent the logical flow of your orchestration.</span></span>  
  
 <span data-ttu-id="b4f6a-110">還應該瞭解一些進階的協調流程概念，例如 Web 服務、相互關聯及長時間執行的交易。</span><span class="sxs-lookup"><span data-stu-id="b4f6a-110">You should understand advanced orchestration concepts such as Web services, correlation, and long-running transactions.</span></span> <span data-ttu-id="b4f6a-111">您可能不需使用全部的功能，但知道它們的作用是有幫助的。</span><span class="sxs-lookup"><span data-stu-id="b4f6a-111">You might not need to use all of these facilities, but it is helpful to know what they can do for you.</span></span>  
  
 <span data-ttu-id="b4f6a-112">Web 服務是一些程式，其介面符合為 Web 服務描述語言 (WSDL) 設定的標準。</span><span class="sxs-lookup"><span data-stu-id="b4f6a-112">Web services are programs with interfaces that adhere to the standards set forth in the Web Services Description Language (WSDL).</span></span> <span data-ttu-id="b4f6a-113">透過以標準方式定義訊息類型、連接埠、連接埠類型及作業，不同的系統能彼此有效地溝通。</span><span class="sxs-lookup"><span data-stu-id="b4f6a-113">By defining message types, ports, port types, and operations in a standard way, disparate systems can communicate effectively with each other.</span></span>  
  
 <span data-ttu-id="b4f6a-114">「相互關聯」是讓訊息與協調流程的特定執行中執行個體產生關聯的機制，可以在執行多個執行個體且有許多訊息來回傳遞時，讓您的商務程序取得適當的資訊。</span><span class="sxs-lookup"><span data-stu-id="b4f6a-114">Correlation is the mechanism by which messages are associated with particular running instances of an orchestration, so that your business process gets the appropriate information when many instances are running and many messages are being sent back and forth.</span></span>  
  
 <span data-ttu-id="b4f6a-115">交易可讓您在未預期的問題發生時，適當地維持協調流程的狀態。</span><span class="sxs-lookup"><span data-stu-id="b4f6a-115">Transactions enable you to maintain the state of an orchestration appropriately if any unexpected issues arise.</span></span> <span data-ttu-id="b4f6a-116">「協調流程設計師」提供處理例外狀況的各種方法，使您能夠透過可控管和預測的方式來處理錯誤。</span><span class="sxs-lookup"><span data-stu-id="b4f6a-116">Orchestration Designer provides various ways to handle exceptions, which enable you to deal with errors in a controlled and predictable manner.</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="b4f6a-117">本節內容</span><span class="sxs-lookup"><span data-stu-id="b4f6a-117">In This Section</span></span>  
  
-   [<span data-ttu-id="b4f6a-118">協調流程設計介面</span><span class="sxs-lookup"><span data-stu-id="b4f6a-118">The Orchestration Design Surface</span></span>](../core/the-orchestration-design-surface.md)  
  
-   [<span data-ttu-id="b4f6a-119">BizTalk 協調流程 索引標籤工具箱</span><span class="sxs-lookup"><span data-stu-id="b4f6a-119">BizTalk Orchestrations Tab, Toolbox</span></span>](../core/biztalk-orchestrations-tab-toolbox.md)  
  
-   [<span data-ttu-id="b4f6a-120">在協調流程開發中的步驟</span><span class="sxs-lookup"><span data-stu-id="b4f6a-120">Steps in Orchestration Development</span></span>](../core/steps-in-orchestration-development.md)  
  
-   [<span data-ttu-id="b4f6a-121">開發協調流程的安全性考量</span><span class="sxs-lookup"><span data-stu-id="b4f6a-121">Security Considerations for Developing Orchestrations</span></span>](../core/security-considerations-for-developing-orchestrations.md)  
  
-   [<span data-ttu-id="b4f6a-122">XLANG 的語言</span><span class="sxs-lookup"><span data-stu-id="b4f6a-122">XLANG-s Language</span></span>](../core/xlang-s-language.md)  
  
-   [<span data-ttu-id="b4f6a-123">關於 BizTalk 協調流程引擎</span><span class="sxs-lookup"><span data-stu-id="b4f6a-123">About the BizTalk Orchestration Engine</span></span>](../core/about-the-biztalk-orchestration-engine.md)