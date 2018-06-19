---
title: 如何新增 Exception1 訊息 |Microsoft 文件
ms.custom: ''
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- exceptions, adding messages
- messages, exceptions
- faults, adding messages
ms.assetid: e087db39-e745-47d4-a888-0b82a9f855c8
caps.latest.revision: 7
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: b60bfdfb222761aadd54b6c32567dfa6821355ae
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/20/2017
ms.locfileid: "22246590"
---
# <a name="how-to-add-a-message-for-an-exception"></a><span data-ttu-id="7e7e6-102">如何新增例外狀況訊息</span><span class="sxs-lookup"><span data-stu-id="7e7e6-102">How to Add a Message for an Exception</span></span>
<span data-ttu-id="7e7e6-103">下列主題說明如何新增例外狀況的訊息。</span><span class="sxs-lookup"><span data-stu-id="7e7e6-103">The following topic describes how to add a message for an exception.</span></span>  
  
### <a name="to-add-a-message-for-an-exception"></a><span data-ttu-id="7e7e6-104">若要新增例外狀況的訊息</span><span class="sxs-lookup"><span data-stu-id="7e7e6-104">To add a message for an exception</span></span>  
  
1.  <span data-ttu-id="7e7e6-105">在**協調流程檢視**視窗中，以滑鼠右鍵按一下**訊息**選取**新訊息**。</span><span class="sxs-lookup"><span data-stu-id="7e7e6-105">In the **Orchestration View** window, right-click **Messages** and select **New Message**.</span></span>  
  
     <span data-ttu-id="7e7e6-106">Message_3 隨即建立，您可將它專門指派給該錯誤。</span><span class="sxs-lookup"><span data-stu-id="7e7e6-106">This creates Message_3, which you can assign specifically to the fault.</span></span>  
  
2.  <span data-ttu-id="7e7e6-107">以滑鼠右鍵按一下**Message_3**選取**屬性**。</span><span class="sxs-lookup"><span data-stu-id="7e7e6-107">Right-click **Message_3** and select **Properties**.</span></span>  
  
3.  <span data-ttu-id="7e7e6-108">在**屬性**視窗中，將**訊息類型**。</span><span class="sxs-lookup"><span data-stu-id="7e7e6-108">In the **Properties** window, set the **Message Type**.</span></span>  
  
     <span data-ttu-id="7e7e6-109">選取 **.Net 類別**，然後選取 **[systemstring]**。</span><span class="sxs-lookup"><span data-stu-id="7e7e6-109">Select **.Net Classes**, and then select **SystemString**.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="7e7e6-110">另請參閱</span><span class="sxs-lookup"><span data-stu-id="7e7e6-110">See Also</span></span>  
 [<span data-ttu-id="7e7e6-111">使用 BizTalk Server 例外狀況處理</span><span class="sxs-lookup"><span data-stu-id="7e7e6-111">Using BizTalk Server Exception Handling</span></span>](../core/using-biztalk-server-exception-handling5.md)