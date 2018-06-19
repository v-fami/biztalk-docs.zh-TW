---
title: 如何建構 Web 訊息部分，從基本.NET 類型 |Microsoft 文件
ms.custom: ''
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- creating, Web messages
- Web messages, Message Assignment shape [Orchestration Designer]
- Web messages, creating
- Message Assignment shape [Orchestration Designer], Web messages
- Web messages, parts
- Web messages, .NET types
ms.assetid: 1fe52412-d2bc-484c-8925-c7ff3ca7704b
caps.latest.revision: 9
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 991970d5b0d40da1ec00b54919d2742cfd48353c
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/20/2017
ms.locfileid: "22248022"
---
# <a name="how-to-construct-a-web-message-part-from-a-primitive-net-type"></a><span data-ttu-id="97e50-102">如何建構 Web 訊息部分，從基本.NET 類型</span><span class="sxs-lookup"><span data-stu-id="97e50-102">How to Construct a Web Message Part from a Primitive .NET Type</span></span>
<span data-ttu-id="97e50-103">從基本.NET 類型建立 Web 訊息部分使用**訊息指派**圖形。</span><span class="sxs-lookup"><span data-stu-id="97e50-103">You create a Web message part from a primitive .NET type by using a **Message Assignment** shape.</span></span> <span data-ttu-id="97e50-104">或者，您也可以使用 .NET Helper 類別來設定部分，以便從基本 .NET 類型建立 Web 訊息部分。</span><span class="sxs-lookup"><span data-stu-id="97e50-104">Alternatively, you can create a Web message part from a primitive .NET type by using a .NET helper class to set the parts.</span></span> <span data-ttu-id="97e50-105">如需有關使用.NET 類別建立訊息類型的詳細資訊，請參閱[使用者程式碼中的 建構訊息](../core/constructing-messages-in-user-code.md)。</span><span class="sxs-lookup"><span data-stu-id="97e50-105">For more information on creating message types by using a .NET class, see [Constructing Messages in User Code](../core/constructing-messages-in-user-code.md).</span></span>  
  
### <a name="to-construct-a-web-message-part-from-a-primitive-net-type"></a><span data-ttu-id="97e50-106">若要從基本 .NET 類型建構 Web 訊息部分</span><span class="sxs-lookup"><span data-stu-id="97e50-106">To construct a Web message part from a primitive .NET type</span></span>  
  
1.  <span data-ttu-id="97e50-107">開啟協調流程，開啟**工具箱**按一下**BizTalk 協調流程** 索引標籤。</span><span class="sxs-lookup"><span data-stu-id="97e50-107">With an orchestration open, open the **Toolbox** and click the **BizTalk Orchestrations** tab.</span></span>  
  
2.  <span data-ttu-id="97e50-108">拖曳**建構訊息**圖形至協調流程。</span><span class="sxs-lookup"><span data-stu-id="97e50-108">Drag a **Construct Message** shape to the orchestration.</span></span>  
  
3.  <span data-ttu-id="97e50-109">編輯**建構訊息**屬性，以包括您建立 Web 訊息類型的訊息執行個體。</span><span class="sxs-lookup"><span data-stu-id="97e50-109">Edit the **Message Constructed** property to include the message instance that you created for the Web message type.</span></span>  
  
4.  <span data-ttu-id="97e50-110">拖曳**訊息指派**圖形拖曳到**建構訊息**圖形。</span><span class="sxs-lookup"><span data-stu-id="97e50-110">Drag a **Message Assignment** shape onto the **Construct Message** shape.</span></span>  
  
5.  <span data-ttu-id="97e50-111">按兩下**訊息指派**圖形以開啟 BizTalk 運算式編輯器。</span><span class="sxs-lookup"><span data-stu-id="97e50-111">Double-click the **Message Assignment** shape to open the BizTalk Expression Editor.</span></span>  
  
6.  <span data-ttu-id="97e50-112">在 [BizTalk 運算式編輯器] 方塊中，將 Web 訊息類型的部分設定為需要的值。</span><span class="sxs-lookup"><span data-stu-id="97e50-112">Set the parts of the Web message type to their required values in the BizTalk Expression Editor box.</span></span>  
  
     <span data-ttu-id="97e50-113">例如，下列程式碼會將運算式設定為字串：</span><span class="sxs-lookup"><span data-stu-id="97e50-113">For example, the following code sets the expression to a string:</span></span>  
  
    ```  
    ItemAvailRequestInstance.Item_ID = "This is Item_ID.";  
    ```  
  
## <a name="see-also"></a><span data-ttu-id="97e50-114">另請參閱</span><span class="sxs-lookup"><span data-stu-id="97e50-114">See Also</span></span>  
 [<span data-ttu-id="97e50-115">建構 Web 訊息</span><span class="sxs-lookup"><span data-stu-id="97e50-115">Constructing Web Messages</span></span>](../core/constructing-web-messages.md)