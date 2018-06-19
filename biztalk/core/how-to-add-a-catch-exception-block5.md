---
title: 如何新增 Catch 例外狀況 Block5 |Microsoft 文件
ms.custom: ''
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- exceptions, adding Catch Exception block
- Catch Exception blocks, adding
ms.assetid: 4875060c-976c-40e7-830a-ffd1a47ba68a
caps.latest.revision: 8
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: f6c045677fb2d177377725a3f11e81a5c5c70f9e
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/20/2017
ms.locfileid: "22246502"
---
# <a name="how-to-add-a-catch-exception-block"></a><span data-ttu-id="eed9e-102">如何新增 Catch 例外狀況區塊</span><span class="sxs-lookup"><span data-stu-id="eed9e-102">How to Add a Catch Exception Block</span></span>
<span data-ttu-id="eed9e-103">若要加入**Catch 例外狀況**封鎖**範圍**圖形，**交易類型**屬性**範圍**圖形必須設定為**無**或**長時間執行的**。</span><span class="sxs-lookup"><span data-stu-id="eed9e-103">To add a **Catch Exception** block to a **Scope** shape, the **Transaction Type** property of the **Scope** shape must be set to **None** or **Long Running**.</span></span>  
  
### <a name="to-add-a-catch-exception-block"></a><span data-ttu-id="eed9e-104">新增 Catch 例外狀況區塊</span><span class="sxs-lookup"><span data-stu-id="eed9e-104">To add a catch exception block</span></span>  
  
1.  <span data-ttu-id="eed9e-105">以滑鼠右鍵按一下**範圍**圖形，，然後按一下**新例外狀況處理常式**。</span><span class="sxs-lookup"><span data-stu-id="eed9e-105">Right-click the **Scope** shape, and then click **New Exception Handler**.</span></span>  
  
     <span data-ttu-id="eed9e-106">A **Catch 例外狀況**區塊便會加入至協調流程緊接相關聯**範圍**圖形。</span><span class="sxs-lookup"><span data-stu-id="eed9e-106">A **Catch Exception** block is added to the orchestration immediately following the associated **Scope** shape.</span></span>  
  
2.  <span data-ttu-id="eed9e-107">在**屬性**視窗中，指定的屬性。</span><span class="sxs-lookup"><span data-stu-id="eed9e-107">In the **Properties** window, specify the properties.</span></span>  
  
     <span data-ttu-id="eed9e-108">最重要的屬性是**例外狀況物件類型**; 這是將要 catch 的訊息類型。</span><span class="sxs-lookup"><span data-stu-id="eed9e-108">The most important property is the **Exception Object Type**; this is the type of message it will catch.</span></span>  
  
    |<span data-ttu-id="eed9e-109">屬性</span><span class="sxs-lookup"><span data-stu-id="eed9e-109">Property</span></span>|<span data-ttu-id="eed9e-110">Description</span><span class="sxs-lookup"><span data-stu-id="eed9e-110">Description</span></span>|  
    |--------------|-----------------|  
    |<span data-ttu-id="eed9e-111">**例外狀況物件名稱**</span><span class="sxs-lookup"><span data-stu-id="eed9e-111">**Exception Object Name**</span></span>|<span data-ttu-id="eed9e-112">指定例外狀況處理常式所攔截的例外狀況物件名稱。</span><span class="sxs-lookup"><span data-stu-id="eed9e-112">Assigns a name to the exception object caught by the exception handler.</span></span>|  
    |<span data-ttu-id="eed9e-113">**例外狀況物件類型**</span><span class="sxs-lookup"><span data-stu-id="eed9e-113">**Exception Object Type**</span></span>|<span data-ttu-id="eed9e-114">決定此例外狀況處理常式將會攔截的物件類型 (衍生自 System.Exception)。</span><span class="sxs-lookup"><span data-stu-id="eed9e-114">Determines the object type (derived from System.Exception) that this exception handler will catch.</span></span>|  
  
3.  <span data-ttu-id="eed9e-115">在**屬性**視窗，請在**例外狀況物件類型**清單中，選取**一般例外狀況**。</span><span class="sxs-lookup"><span data-stu-id="eed9e-115">In the **Properties** window, in the **Exception Object Type** list, select **General Exception**.</span></span>  
  
4.  <span data-ttu-id="eed9e-116">內部**Catch 例外狀況**封鎖，新增圖形以建立處理的例外狀況的處理序。</span><span class="sxs-lookup"><span data-stu-id="eed9e-116">Inside the **Catch Exception** block, add shapes to create the process for handling the exception.</span></span>  
  
    1.  <span data-ttu-id="eed9e-117">以滑鼠右鍵按一下下面的**CatchException** ，指向 **插入圖形**，然後選取**建構訊息**。</span><span class="sxs-lookup"><span data-stu-id="eed9e-117">Right-click below the **CatchException** and point to **Insert Shape**, and then select **Construct Message**.</span></span>  
  
    2.  <span data-ttu-id="eed9e-118">[] 內按兩下**MessageAssignment**開啟文字編輯器，然後輸入 「 訊息指派。</span><span class="sxs-lookup"><span data-stu-id="eed9e-118">Double-click inside **MessageAssignment** to open the Text Editor and enter the Message assignment.</span></span>  
  
         <span data-ttu-id="eed9e-119">例如，輸入 `Message_3 = Test`。</span><span class="sxs-lookup"><span data-stu-id="eed9e-119">For example, type `Message_3 = Test`.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="eed9e-120">另請參閱</span><span class="sxs-lookup"><span data-stu-id="eed9e-120">See Also</span></span>  
 <span data-ttu-id="eed9e-121">[完成例外狀況訊息](../core/completing-the-exception-message1.md) </span><span class="sxs-lookup"><span data-stu-id="eed9e-121">[Completing the Exception Message](../core/completing-the-exception-message1.md) </span></span>  
 <span data-ttu-id="eed9e-122">[如何新增範圍圖形](../core/how-to-add-a-scope-shape5.md) </span><span class="sxs-lookup"><span data-stu-id="eed9e-122">[How to Add a Scope Shape](../core/how-to-add-a-scope-shape5.md) </span></span>  
 [<span data-ttu-id="eed9e-123">使用 BizTalk Server 例外狀況處理</span><span class="sxs-lookup"><span data-stu-id="eed9e-123">Using BizTalk Server Exception Handling</span></span>](../core/using-biztalk-server-exception-handling5.md)