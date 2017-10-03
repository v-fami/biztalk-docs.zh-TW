---
title: "如何新增錯誤個訊息 2 |Microsoft 文件"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- fault messages, adding
- messages, fault messages
ms.assetid: 8f1b40af-2c75-4167-8b62-a86b791907c9
caps.latest.revision: "7"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 6dee8a1fca0e30a96b6a714b5c717c0638bc8144
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/20/2017
---
# <a name="how-to-add-a-fault-message"></a><span data-ttu-id="3c304-102">如何新增錯誤訊息</span><span class="sxs-lookup"><span data-stu-id="3c304-102">How to Add a Fault Message</span></span>
<span data-ttu-id="3c304-103">當 您建立連接後端系統的連接埠時，會包含要求和回應 。</span><span class="sxs-lookup"><span data-stu-id="3c304-103">When you create a port to the back-end system, it contains a request and a response.</span></span> <span data-ttu-id="3c304-104">您必須新增訊息，以便將該訊息指派給錯誤。</span><span class="sxs-lookup"><span data-stu-id="3c304-104">You must add a message so that you can assign it to the fault.</span></span>  
  
### <a name="to-add-a-fault-message"></a><span data-ttu-id="3c304-105">若要新增錯誤訊息</span><span class="sxs-lookup"><span data-stu-id="3c304-105">To add a fault message</span></span>  
  
1.  <span data-ttu-id="3c304-106">在**協調流程檢視**視窗中，以滑鼠右鍵按一下**訊息**，然後選取**新訊息**。</span><span class="sxs-lookup"><span data-stu-id="3c304-106">In the **Orchestration View** window, right-click **Messages**, and select **New Message**.</span></span>  
  
     <span data-ttu-id="3c304-107">Message_3 隨即建立，您可將它專門指派給該錯誤。</span><span class="sxs-lookup"><span data-stu-id="3c304-107">This creates Message_3, which you can assign specifically to the fault.</span></span>  
  
2.  <span data-ttu-id="3c304-108">以滑鼠右鍵按一下 Message_3，然後選取**屬性**。</span><span class="sxs-lookup"><span data-stu-id="3c304-108">Right-click Message_3, and select **Properties**.</span></span>  
  
3.  <span data-ttu-id="3c304-109">在**屬性** 對話方塊中，將**訊息類型**。</span><span class="sxs-lookup"><span data-stu-id="3c304-109">In the **Properties** dialog box, set the **Message Type**.</span></span>  
  
     <span data-ttu-id="3c304-110">選取**.NET 類別**，然後選取  **systemstring**。</span><span class="sxs-lookup"><span data-stu-id="3c304-110">Select **.NET Classes** and then select **SystemString**.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="3c304-111">另請參閱</span><span class="sxs-lookup"><span data-stu-id="3c304-111">See Also</span></span>  
 [<span data-ttu-id="3c304-112">使用 BizTalk Server 例外狀況處理</span><span class="sxs-lookup"><span data-stu-id="3c304-112">Using BizTalk Server Exception Handling</span></span>](../core/using-biztalk-server-exception-handling3.md)