---
title: 如何新增範圍 Shape4 |Microsoft 文件
ms.custom: ''
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- adding, Scope shapes
- Scope shape, adding
ms.assetid: 4ed56ada-a656-40b1-b34a-0c0803c01216
caps.latest.revision: 5
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: a81bb85412784616d185b64ee39f1e777d19fea3
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/20/2017
ms.locfileid: "22248326"
---
# <a name="how-to-add-a-scope-shape"></a><span data-ttu-id="f0205-102">如何新增範圍圖形</span><span class="sxs-lookup"><span data-stu-id="f0205-102">How to Add a Scope Shape</span></span>
<span data-ttu-id="f0205-103">請遵循下列步驟來新增**範圍**圖形。</span><span class="sxs-lookup"><span data-stu-id="f0205-103">Follow these steps to add a **Scope** shape.</span></span>  
  
### <a name="to-add-a-scope-shape"></a><span data-ttu-id="f0205-104">若要新增範圍圖形</span><span class="sxs-lookup"><span data-stu-id="f0205-104">To add a scope shape</span></span>  
  
1.  <span data-ttu-id="f0205-105">以滑鼠右鍵按一下下方的箭號**receivefromin**通訊埠，請指向**插入圖形**，然後按一下 **範圍**。</span><span class="sxs-lookup"><span data-stu-id="f0205-105">Right-click the arrow below the **ReceiveFromIn** port, point to **Insert Shape**, and then click **Scope**.</span></span>  
  
     <span data-ttu-id="f0205-106">在 [範圍] 圖形中，設定可能有錯誤的作業。</span><span class="sxs-lookup"><span data-stu-id="f0205-106">In the Scope shape, you set operations that might have a fault.</span></span>  
  
     <span data-ttu-id="f0205-107">例如，在 SQLExecute 協調流程中加入傳送作業、接收作業和傳送埠。</span><span class="sxs-lookup"><span data-stu-id="f0205-107">For example, add a send, a receive and a send port in an SQLExecute orchestration.</span></span> <span data-ttu-id="f0205-108">在這個範例中，您會傳送訊息至 SERVER。</span><span class="sxs-lookup"><span data-stu-id="f0205-108">In this example, you send a message to SERVER.</span></span> <span data-ttu-id="f0205-109">SERVER 會提供回應。</span><span class="sxs-lookup"><span data-stu-id="f0205-109">SERVER gives a response.</span></span> <span data-ttu-id="f0205-110">然後執行其餘的協調流程，並將資訊傳回給 OutFile 連接埠。</span><span class="sxs-lookup"><span data-stu-id="f0205-110">It runs the rest of the orchestration and returns information back to the OutFile port.</span></span>  
  
2.  <span data-ttu-id="f0205-111">在 「 範圍 」 圖形，設定**交易**至**無**。</span><span class="sxs-lookup"><span data-stu-id="f0205-111">In the Scope shape, set the **Transaction** to **None**.</span></span>  
  
3.  <span data-ttu-id="f0205-112">「 範圍 」 圖形內按一下滑鼠右鍵，然後選取**新例外狀況處理常式**。</span><span class="sxs-lookup"><span data-stu-id="f0205-112">Right-click inside the Scope shape and select **New Exception Handler**.</span></span>  
  
     <span data-ttu-id="f0205-113">這會建立**Catch 例外狀況**區塊。</span><span class="sxs-lookup"><span data-stu-id="f0205-113">This creates the **Catch Exception** block.</span></span> <span data-ttu-id="f0205-114">從後端發生的例外狀況，它會攔截到內部**Catch 例外狀況**區塊。</span><span class="sxs-lookup"><span data-stu-id="f0205-114">If an exception occurs from the back-end, it is caught inside the **Catch Exception** block.</span></span>  
  
4.  <span data-ttu-id="f0205-115">在**Catch 例外狀況**區塊中，您必須加入的邏輯。</span><span class="sxs-lookup"><span data-stu-id="f0205-115">In the **Catch Exception** block, you must add the logic.</span></span>  
    <span data-ttu-id="f0205-116">在必須設定的邏輯中，最重要的一個就是您預期會收到的錯誤訊息類型。</span><span class="sxs-lookup"><span data-stu-id="f0205-116">The most important logic that you must set is the type of error message that you expect to receive.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="f0205-117">另請參閱</span><span class="sxs-lookup"><span data-stu-id="f0205-117">See Also</span></span>  
 [<span data-ttu-id="f0205-118">使用 BizTalk Server 例外狀況處理</span><span class="sxs-lookup"><span data-stu-id="f0205-118">Using BizTalk Server Exception Handling</span></span>](../core/using-biztalk-server-exception-handling4.md)