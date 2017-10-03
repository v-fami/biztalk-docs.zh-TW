---
title: "如何新增範圍 Shape3 |Microsoft 文件"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords: Scope shapes, adding
ms.assetid: 8068ce97-4409-4c88-89e8-6505b56cefc5
caps.latest.revision: "8"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 8231dfed1ea84ba5c11e0352f789b92cc38d0f83
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/20/2017
---
# <a name="how-to-add-a-scope-shape"></a><span data-ttu-id="c9028-102">如何新增範圍圖形</span><span class="sxs-lookup"><span data-stu-id="c9028-102">How to Add a Scope Shape</span></span>
<span data-ttu-id="c9028-103">使用下列程序來新增「範圍」圖形。</span><span class="sxs-lookup"><span data-stu-id="c9028-103">Use the following procedure to add a Scope shape.</span></span>  
  
### <a name="to-add-a-scope-shape"></a><span data-ttu-id="c9028-104">若要新增範圍圖形</span><span class="sxs-lookup"><span data-stu-id="c9028-104">To add a Scope Shape</span></span>  
  
1.  <span data-ttu-id="c9028-105">以滑鼠右鍵按一下下方的箭號**接收**通訊埠，請指向**插入圖形**，然後選取**範圍**。</span><span class="sxs-lookup"><span data-stu-id="c9028-105">Right-click the arrow below the **Receive** port, point to **Insert Shape**, and then select **Scope**.</span></span>  
  
     ![](../core/media/siebeladapter-18-exceptionhandling-insertscope.gif "SiebelAdapter_18_ExceptionHandling_InsertScope")  
  
     <span data-ttu-id="c9028-106">在**範圍**」 圖形，設定可能有錯誤的作業。</span><span class="sxs-lookup"><span data-stu-id="c9028-106">In the **Scope** shape, you set operations that might have a fault.</span></span>  
  
     <span data-ttu-id="c9028-107">例如，在 SQLExecute 協調流程中加入傳送作業、接收作業和傳送埠。</span><span class="sxs-lookup"><span data-stu-id="c9028-107">For example, add a send, a receive, and a send port in an SQLExecute orchestration.</span></span> <span data-ttu-id="c9028-108">在這個範例中，您會傳送訊息至 SERVER。</span><span class="sxs-lookup"><span data-stu-id="c9028-108">In this example, you send a message to SERVER.</span></span> <span data-ttu-id="c9028-109">SERVER 會提供回應。</span><span class="sxs-lookup"><span data-stu-id="c9028-109">SERVER gives a response.</span></span> <span data-ttu-id="c9028-110">然後執行其餘的協調流程，並將資訊傳回給 outFile 連接埠。</span><span class="sxs-lookup"><span data-stu-id="c9028-110">It runs the rest of the orchestration and returns information back to the outFile port.</span></span>  
  
2.  <span data-ttu-id="c9028-111">在**範圍**圖形中，將**交易**至**無**。</span><span class="sxs-lookup"><span data-stu-id="c9028-111">In the **Scope** shape, set the **Transaction** to **None**.</span></span>  
  
3.  <span data-ttu-id="c9028-112">以滑鼠右鍵按一下**範圍**圖形，然後選取**新例外狀況處理常式**。</span><span class="sxs-lookup"><span data-stu-id="c9028-112">Right-click inside the **Scope** shape, and select **New Exception Handler**.</span></span>  
  
     ![](../core/media/siebeladapter-19-exceptionhandling-newexception.gif "SiebelAdapter_19_ExceptionHandling_NewException")  
  
     <span data-ttu-id="c9028-113">這會建立**Catch 例外狀況**區塊。</span><span class="sxs-lookup"><span data-stu-id="c9028-113">This creates the **Catch Exception** block.</span></span> <span data-ttu-id="c9028-114">從後端系統發生的例外狀況，它會攔截到內部**Catch 例外狀況**區塊。</span><span class="sxs-lookup"><span data-stu-id="c9028-114">If an exception occurs from the back-end system, it is caught inside the **Catch Exception** block.</span></span>  
  
4.  <span data-ttu-id="c9028-115">在**Catch 例外狀況**區塊中，您必須加入的邏輯。</span><span class="sxs-lookup"><span data-stu-id="c9028-115">In the **Catch Exception** block, you must add the logic.</span></span>  
  
     <span data-ttu-id="c9028-116">在必須設定的邏輯中，最重要的一個就是您預期會收到的錯誤訊息類型。</span><span class="sxs-lookup"><span data-stu-id="c9028-116">The most important logic that you must set is the type of error message that you expect to receive.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="c9028-117">另請參閱</span><span class="sxs-lookup"><span data-stu-id="c9028-117">See Also</span></span>  
 [<span data-ttu-id="c9028-118">使用 BizTalk Server 例外狀況處理</span><span class="sxs-lookup"><span data-stu-id="c9028-118">Using BizTalk Server Exception Handling</span></span>](../core/using-biztalk-server-exception-handling1.md)