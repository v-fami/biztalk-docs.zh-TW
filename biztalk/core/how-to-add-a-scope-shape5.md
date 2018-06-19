---
title: 如何新增範圍 Shape5 |Microsoft 文件
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
ms.assetid: 1e16eda1-c4bd-4428-a477-78c453aeb1aa
caps.latest.revision: 9
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: c7bbe3f5fbb267fee618ac7f0b91c35ad33e1758
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/20/2017
ms.locfileid: "22246734"
---
# <a name="how-to-add-a-scope-shape"></a><span data-ttu-id="a2866-102">如何新增範圍圖形</span><span class="sxs-lookup"><span data-stu-id="a2866-102">How to Add a Scope Shape</span></span>
<span data-ttu-id="a2866-103">請遵循下列步驟來新增**範圍**圖形。</span><span class="sxs-lookup"><span data-stu-id="a2866-103">Follow these steps to add a **Scope**shape.</span></span>  
  
### <a name="to-add-a-scope-shape"></a><span data-ttu-id="a2866-104">新增範圍圖形</span><span class="sxs-lookup"><span data-stu-id="a2866-104">To add a Scope shape</span></span>  
  
1.  <span data-ttu-id="a2866-105">以滑鼠右鍵按一下下方的箭號**receivefromin**通訊埠，請指向**插入圖形**，然後按一下 **範圍**。</span><span class="sxs-lookup"><span data-stu-id="a2866-105">Right-click the arrow below the **ReceiveFromIn** port, point to **Insert Shape**, and then click **Scope**.</span></span>  
  
     <span data-ttu-id="a2866-106">在**範圍**」 圖形，設定可能有錯誤的作業。</span><span class="sxs-lookup"><span data-stu-id="a2866-106">In the **Scope** shape, you set operations that might have a fault.</span></span>  
  
     <span data-ttu-id="a2866-107">例如，在 SQLExecute 協調流程中加入傳送作業、接收作業和傳送埠。</span><span class="sxs-lookup"><span data-stu-id="a2866-107">For example, add a send, a receive and a send port in an SQLExecute orchestration.</span></span> <span data-ttu-id="a2866-108">在這個範例中，您會傳送訊息至 SERVER。</span><span class="sxs-lookup"><span data-stu-id="a2866-108">In this example, you send a message to SERVER.</span></span> <span data-ttu-id="a2866-109">SERVER 會提供回應。</span><span class="sxs-lookup"><span data-stu-id="a2866-109">SERVER gives a response.</span></span> <span data-ttu-id="a2866-110">然後執行其餘的協調流程，並將資訊傳回給 OutFile 連接埠。</span><span class="sxs-lookup"><span data-stu-id="a2866-110">It runs the rest of the orchestration and returns information back to the OutFile port.</span></span>  
  
2.  <span data-ttu-id="a2866-111">在**範圍**圖形中，將**交易類型**至**無**。</span><span class="sxs-lookup"><span data-stu-id="a2866-111">In the **Scope** shape, set the **Transaction Type** to **None**.</span></span>  
  
3.  <span data-ttu-id="a2866-112">以滑鼠右鍵按一下**範圍**圖形，並選取**新例外狀況處理常式**。</span><span class="sxs-lookup"><span data-stu-id="a2866-112">Right-click inside the **Scope** shape and select **New Exception Handler**.</span></span>  
  
     <span data-ttu-id="a2866-113">這會建立`Catch Exception`區塊。</span><span class="sxs-lookup"><span data-stu-id="a2866-113">This creates the `Catch Exception`block.</span></span> <span data-ttu-id="a2866-114">從後端發生的例外狀況，它會攔截到內部`Catch Exception`區塊。</span><span class="sxs-lookup"><span data-stu-id="a2866-114">If an exception occurs from the back-end, it is caught inside the `Catch Exception`block.</span></span>  
  
4.  <span data-ttu-id="a2866-115">您必須在 `Catch Exception` 區塊中加入邏輯。</span><span class="sxs-lookup"><span data-stu-id="a2866-115">In the `Catch Exception` block, you must add the logic.</span></span>  
  
     <span data-ttu-id="a2866-116">在必須設定的邏輯中，最重要的一個就是您預期會收到的錯誤訊息類型。</span><span class="sxs-lookup"><span data-stu-id="a2866-116">The most important logic that you must set is the type of error message that you expect to receive.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="a2866-117">另請參閱</span><span class="sxs-lookup"><span data-stu-id="a2866-117">See Also</span></span>  
 [<span data-ttu-id="a2866-118">使用 BizTalk Server 例外狀況處理</span><span class="sxs-lookup"><span data-stu-id="a2866-118">Using BizTalk Server Exception Handling</span></span>](../core/using-biztalk-server-exception-handling5.md)