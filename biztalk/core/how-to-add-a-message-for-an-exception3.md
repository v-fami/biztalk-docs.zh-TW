---
title: "如何新增 Exception3 訊息 |Microsoft 文件"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- exceptions, adding messages
- messages, exceptions
ms.assetid: 920f9b4d-e002-457c-ad44-f41bf2600e06
caps.latest.revision: "5"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 5ea1bb901437e77d63f42f6dd878bc7f23305a73
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/20/2017
---
# <a name="how-to-add-a-message-for-an-exception"></a><span data-ttu-id="09fad-102">如何新增例外狀況訊息</span><span class="sxs-lookup"><span data-stu-id="09fad-102">How to Add a Message for an Exception</span></span>
<span data-ttu-id="09fad-103">請依照下列步驟來新增含有訊息的錯誤。</span><span class="sxs-lookup"><span data-stu-id="09fad-103">Follow these steps to add a fault with a message.</span></span>  
  
### <a name="to-add-a-message-for-an-exception"></a><span data-ttu-id="09fad-104">若要新增例外狀況的訊息</span><span class="sxs-lookup"><span data-stu-id="09fad-104">To add a message for an exception</span></span>  
  
1.  <span data-ttu-id="09fad-105">在**協調流程檢視**視窗中，以滑鼠右鍵按一下**訊息**選取**新訊息**。</span><span class="sxs-lookup"><span data-stu-id="09fad-105">In the **Orchestration View** window, right-click **Messages** and select **New Message**.</span></span>  
  
     <span data-ttu-id="09fad-106">Message_3 隨即建立，您可將它專門指派給該錯誤。</span><span class="sxs-lookup"><span data-stu-id="09fad-106">This creates Message_3, which you can assign specifically to the fault.</span></span>  
  
2.  <span data-ttu-id="09fad-107">以滑鼠右鍵按一下**Message_3**選取**屬性**。</span><span class="sxs-lookup"><span data-stu-id="09fad-107">Right-click **Message_3** and select **Properties**.</span></span>  
  
3.  <span data-ttu-id="09fad-108">在**屬性** 對話方塊中，將**訊息類型**。</span><span class="sxs-lookup"><span data-stu-id="09fad-108">In the **Properties** dialog box, set the **Message Type**.</span></span>  
  
     <span data-ttu-id="09fad-109">選取**.NET 類別**，然後選取**[systemstring]**。</span><span class="sxs-lookup"><span data-stu-id="09fad-109">Select **.NET Classes**, and then select **SystemString**.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="09fad-110">另請參閱</span><span class="sxs-lookup"><span data-stu-id="09fad-110">See Also</span></span>  
 [<span data-ttu-id="09fad-111">使用 BizTalk Server 例外狀況處理</span><span class="sxs-lookup"><span data-stu-id="09fad-111">Using BizTalk Server Exception Handling</span></span>](../core/using-biztalk-server-exception-handling4.md)