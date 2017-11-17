---
title: "如何新增範圍 Shape1 |Microsoft 文件"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- Scope shapes, adding
- Scope shapes, Catch Exception blocks
- Catch Exception blocks, Scope shapes
- adding, Scope shapes
ms.assetid: dfe039d1-4c4a-4e21-ae03-7ca534aafec3
caps.latest.revision: "8"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 094f744f7d4d6d1c405ea50d222beb8c0a67920e
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/20/2017
---
# <a name="how-to-add-a-scope-shape"></a><span data-ttu-id="51cea-102">如何新增範圍圖形</span><span class="sxs-lookup"><span data-stu-id="51cea-102">How to Add a Scope Shape</span></span>
<span data-ttu-id="51cea-103">若要新增範圍圖形，請遵循下列步驟。</span><span class="sxs-lookup"><span data-stu-id="51cea-103">Follow these steps to add a Scope shape.</span></span>  
  
### <a name="to-add-a-scope-shape"></a><span data-ttu-id="51cea-104">若要新增範圍圖形</span><span class="sxs-lookup"><span data-stu-id="51cea-104">To add a Scope Shape</span></span>  
  
1.  <span data-ttu-id="51cea-105">以滑鼠右鍵按一下下方的箭號**receivefromin**通訊埠，請指向**插入圖形**，然後按一下 **範圍**。</span><span class="sxs-lookup"><span data-stu-id="51cea-105">Right-click the arrow below the **ReceiveFromIn** port, point to **Insert Shape**, and then click **Scope**.</span></span>  
  
     ![](../core/media/siebeladapter-18-exceptionhandling-insertscope.gif "SiebelAdapter_18_ExceptionHandling_InsertScope")  
  
     <span data-ttu-id="51cea-106">在 [範圍] 圖形中，設定可能有錯誤的作業。</span><span class="sxs-lookup"><span data-stu-id="51cea-106">In the Scope shape, you set operations that might have a fault.</span></span>  
  
     <span data-ttu-id="51cea-107">例如，在 SQLExecute 協調流程中加入傳送作業、接收作業和傳送埠。</span><span class="sxs-lookup"><span data-stu-id="51cea-107">For example, add a send, a receive, and a send port in an SQLExecute orchestration.</span></span> <span data-ttu-id="51cea-108">我們會在這個範例中，傳送訊息給 DB2。</span><span class="sxs-lookup"><span data-stu-id="51cea-108">In this example, we are sending a message to DB2.</span></span> <span data-ttu-id="51cea-109">DB2 會提供回應。</span><span class="sxs-lookup"><span data-stu-id="51cea-109">DB2 gives a response.</span></span> <span data-ttu-id="51cea-110">然後執行其餘的協調流程，並將資訊傳回給 OutFile 連接埠。</span><span class="sxs-lookup"><span data-stu-id="51cea-110">It runs the rest of the orchestration and returns information back to the OutFile port.</span></span>  
  
2.  <span data-ttu-id="51cea-111">在 「 範圍 」 圖形，設定**交易**至**無**。</span><span class="sxs-lookup"><span data-stu-id="51cea-111">In the Scope shape, set the **Transaction** to **None**.</span></span>  
  
3.  <span data-ttu-id="51cea-112">以滑鼠右鍵按一下 [範圍] 圖形，然後選取**新例外狀況處理常式**。</span><span class="sxs-lookup"><span data-stu-id="51cea-112">Right-click inside the Scope shape, and select **New Exception Handler**.</span></span>  
  
     ![](../core/media/siebeladapter-19-exceptionhandling-newexception.gif "SiebelAdapter_19_ExceptionHandling_NewException")  
  
     <span data-ttu-id="51cea-113">這時會建立 Catch 例外狀況區塊。</span><span class="sxs-lookup"><span data-stu-id="51cea-113">This creates the Catch Exception block.</span></span> <span data-ttu-id="51cea-114">這時從後端訂單系統發生的例外狀況，將會在此「Catch 例外狀況」區塊中遭到攔截。</span><span class="sxs-lookup"><span data-stu-id="51cea-114">If an exception occurs from the back-end, it is caught inside the Catch Exception block.</span></span>  
  
4.  <span data-ttu-id="51cea-115">您必須在 Catch 例外狀況區塊中加入邏輯。</span><span class="sxs-lookup"><span data-stu-id="51cea-115">In the Catch Exception block, you must add the logic.</span></span>  
  
     <span data-ttu-id="51cea-116">在必須設定的邏輯中，最重要的一個就是您預期的錯誤訊息類型。</span><span class="sxs-lookup"><span data-stu-id="51cea-116">The most important logic you must set is the type of error message you are expecting.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="51cea-117">另請參閱</span><span class="sxs-lookup"><span data-stu-id="51cea-117">See Also</span></span>  
 [<span data-ttu-id="51cea-118">使用 BizTalk Server 例外狀況處理</span><span class="sxs-lookup"><span data-stu-id="51cea-118">Using BizTalk Server Exception Handling</span></span>](../core/using-biztalk-server-exception-handling2.md)