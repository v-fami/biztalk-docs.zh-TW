---
title: "如何設定建構訊息圖形 |Microsoft 文件"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- Construct Message shape [Orchestration Designer], configuring
- Construct Message shape [Orchestration Designer]
- configuring [Orchestration Designer], Construct Message shapes
- Construct Message shape [Orchestration Designer], about Construct Message shape
ms.assetid: 8d052b4e-0873-4102-9462-6604423d0524
caps.latest.revision: "4"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 07b73e7fe62463767894808d7e95f12cf963e4dc
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/20/2017
---
# <a name="how-to-configure-the-construct-message-shape"></a><span data-ttu-id="78188-102">如何設定建構訊息圖形</span><span class="sxs-lookup"><span data-stu-id="78188-102">How to Configure the Construct Message Shape</span></span>
![](../core/media/ebiz-orch-constructmsg.gif "ebiz_orch_constructmsg")  
<span data-ttu-id="78188-103">建構訊息圖形</span><span class="sxs-lookup"><span data-stu-id="78188-103">Construct Message shape</span></span>  
  
 <span data-ttu-id="78188-104">您可以指定要建構的訊息變數，並指派給訊息或其訊息部分。</span><span class="sxs-lookup"><span data-stu-id="78188-104">You specify the message variable that you want to construct, and make assignments to the message or its parts.</span></span> <span data-ttu-id="78188-105">對指定訊息的所有指派均必須在同一個 [建構訊息] 圖形內發生。</span><span class="sxs-lookup"><span data-stu-id="78188-105">All assignments to any given message must take place within the same Construct Message shape.</span></span>  
  
 <span data-ttu-id="78188-106">若要修改已建構訊息 (如已收到的訊息) 上的屬性，必須透過指派第一個執行個體上的屬性給第二個執行個體，並修改新訊息執行個體的屬性以建構一個新的訊息執行個體；這些建構和修改作業均在相同的 [建構訊息] 圖形中發生。</span><span class="sxs-lookup"><span data-stu-id="78188-106">If you want to modify a property on a message that has already been constructed—such as a message that has been received—you must construct a new message instance by assigning the first to the second and then modifying the property on the new message instance; both the construction and modification occur within the same Construct Message shape.</span></span>  
  
### <a name="to-configure-a-construct-message-shape"></a><span data-ttu-id="78188-107">設定建構訊息圖形</span><span class="sxs-lookup"><span data-stu-id="78188-107">To configure a Construct Message shape</span></span>  
  
1.  <span data-ttu-id="78188-108">在 [屬性] 視窗中，使用**建構的訊息**屬性來指定哪些訊息此圖形會建構。</span><span class="sxs-lookup"><span data-stu-id="78188-108">In the Properties window, use the **Messages Constructed** property to specify which messages this shape will construct.</span></span>  
  
2.  <span data-ttu-id="78188-109">加入和設定一或多個**轉換**或**訊息指派**內**建構訊息 」 圖形**。</span><span class="sxs-lookup"><span data-stu-id="78188-109">Add and configure one or more **Transform** or **Message Assignment** shapes inside the **Construct Message shape**.</span></span>