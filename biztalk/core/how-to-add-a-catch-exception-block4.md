---
title: 如何新增 Catch 例外狀況 Block4 |Microsoft 文件
ms.custom: ''
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- Catch Exception blocks, adding
- exception handling, Catch Exception blocks
ms.assetid: 632fa089-a1af-4126-b32b-68d4d8942387
caps.latest.revision: 12
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: b409f25fc32c609bb4c1a80c0582cdb1c363e965
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/20/2017
ms.locfileid: "22246822"
---
# <a name="how-to-add-a-catch-exception-block"></a><span data-ttu-id="a0700-102">如何新增 Catch 例外狀況區塊</span><span class="sxs-lookup"><span data-stu-id="a0700-102">How to Add a Catch Exception Block</span></span>
<span data-ttu-id="a0700-103">**Catch 例外狀況**區塊代表例外狀況處理常式。</span><span class="sxs-lookup"><span data-stu-id="a0700-103">The **Catch Exception** block represents an exception handler.</span></span> <span data-ttu-id="a0700-104">**攔截例外狀況**區塊會附加至結尾**範圍**協調流程設計師中的圖形。</span><span class="sxs-lookup"><span data-stu-id="a0700-104">**Catch Exception** blocks are attached to the end of a **Scope** shape in Orchestration Designer.</span></span> <span data-ttu-id="a0700-105">您可以附加多個**Catch 例外狀況**視需要會封鎖。</span><span class="sxs-lookup"><span data-stu-id="a0700-105">You can attach as many **Catch Exception** blocks as you need.</span></span>  
  
 <span data-ttu-id="a0700-106">您可以設定例外狀況處理常式，處理不同類型的例外狀況。</span><span class="sxs-lookup"><span data-stu-id="a0700-106">You can set up exception handlers to handle different kinds of exceptions.</span></span> <span data-ttu-id="a0700-107">對於每個例外狀況處理常式，您必須指定本身為例外狀況或衍生自系統類別之物件的例外狀況類型。</span><span class="sxs-lookup"><span data-stu-id="a0700-107">On each exception handler, you specify an exception type, which must be either an exception or an object derived from the class System.</span></span> <span data-ttu-id="a0700-108">若擲回的例外狀況符合例外狀況處理常式中指定的類型，便會呼叫該例外狀況處理常式。</span><span class="sxs-lookup"><span data-stu-id="a0700-108">If an exception is thrown that matches the specified type in an exception handler, that exception handler is called.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="a0700-109">若要加入**Catch 例外狀況**封鎖**範圍**圖形，交易類型屬性的**範圍**圖形必須設定為**無**或**長時間執行的**。</span><span class="sxs-lookup"><span data-stu-id="a0700-109">To add a **Catch Exception** block to a **Scope** shape, the Transaction Type property of the **Scope** shape must be set to **None** or **Long Running**.</span></span>  
  
|<span data-ttu-id="a0700-110">新增和填入 Catch 例外狀況區塊</span><span class="sxs-lookup"><span data-stu-id="a0700-110">Adding and populating a Catch Exception block</span></span>|  
|---------------------------------------------------|  
|<span data-ttu-id="a0700-111">1.以滑鼠右鍵按一下**範圍**您想要新增的圖形**Catch 例外狀況**區塊，並按一下**新例外狀況處理常式**。</span><span class="sxs-lookup"><span data-stu-id="a0700-111">1.  Right-click the **Scope** shape that you want to add a **Catch Exception** block to, and click **New Exception Handler**.</span></span><br />     <span data-ttu-id="a0700-112">A **Catch 例外狀況**區塊便會加入至協調流程緊接相關聯**範圍**圖形。</span><span class="sxs-lookup"><span data-stu-id="a0700-112">A **Catch Exception** block is added to the orchestration immediately following the associated **Scope** shape.</span></span><br /><span data-ttu-id="a0700-113">2.在**屬性**視窗中，指定的屬性。</span><span class="sxs-lookup"><span data-stu-id="a0700-113">2.  In the **Properties** window, specify the properties.</span></span> <span data-ttu-id="a0700-114">最重要的是**例外狀況物件類型**; 這是將要 catch 的訊息類型。</span><span class="sxs-lookup"><span data-stu-id="a0700-114">The most important is the **Exception Object Type**; this is the type of message it will catch.</span></span><br />     <span data-ttu-id="a0700-115">**例外狀況物件名稱**</span><span class="sxs-lookup"><span data-stu-id="a0700-115">**Exception Object Name**</span></span><br />     <span data-ttu-id="a0700-116">-將名稱指定給例外狀況處理常式所攔截的例外狀況物件。</span><span class="sxs-lookup"><span data-stu-id="a0700-116">- Assigns a name to the exception object caught by the exception handler.</span></span><br />     <span data-ttu-id="a0700-117">**例外狀況物件類型**</span><span class="sxs-lookup"><span data-stu-id="a0700-117">**Exception Object Type**</span></span><br />     <span data-ttu-id="a0700-118">-判斷物件類型 （衍生自 System.Exception），將會攔截此例外狀況處理常式。</span><span class="sxs-lookup"><span data-stu-id="a0700-118">- Determines the object type (derived from System.Exception) that this exception handler will catch.</span></span><br /><span data-ttu-id="a0700-119">3.在**屬性**視窗中，開啟**例外狀況物件類型**清單。</span><span class="sxs-lookup"><span data-stu-id="a0700-119">3.  In the **Properties** window, open the **Exception Object Type** list.</span></span> <span data-ttu-id="a0700-120">此清單包含**一般例外狀況**。</span><span class="sxs-lookup"><span data-stu-id="a0700-120">This list contains the **General Exception**.</span></span><br /><span data-ttu-id="a0700-121">4.內部**Catch 例外狀況**封鎖，新增圖形以建立處理的例外狀況的處理序。</span><span class="sxs-lookup"><span data-stu-id="a0700-121">4.  Inside the **Catch Exception** block, add shapes to create the process for handling the exception.</span></span><br /><span data-ttu-id="a0700-122">5.以滑鼠右鍵按一下下面的**Catch 例外狀況**，指向**插入圖形**，然後選取**建構訊息**。</span><span class="sxs-lookup"><span data-stu-id="a0700-122">5.  Right-click below the **Catch Exception**, point to **Insert Shape**, and select **Construct Message**.</span></span><br /><span data-ttu-id="a0700-123">6.[] 內按兩下**MessageAssignment**啟動文字編輯器中，並輸入 「 訊息指派。</span><span class="sxs-lookup"><span data-stu-id="a0700-123">6.  Double-click inside **MessageAssignment** to activate the Text Editor, and enter the Message assignment.</span></span><br />     <span data-ttu-id="a0700-124">例如，輸入 Message_3 = Test。</span><span class="sxs-lookup"><span data-stu-id="a0700-124">For example, type in Message_3 = Test.</span></span><br />     ![](../core/media/siebeladapter-21-exceptionhandling-message3test.gif "SiebelAdapter_21_ExceptionHandling_Message3Test")|  
  
## <a name="see-also"></a><span data-ttu-id="a0700-125">另請參閱</span><span class="sxs-lookup"><span data-stu-id="a0700-125">See Also</span></span>  
 <span data-ttu-id="a0700-126">[完成例外狀況訊息](../core/completing-the-exception-message2.md) </span><span class="sxs-lookup"><span data-stu-id="a0700-126">[Completing the Exception Message](../core/completing-the-exception-message2.md) </span></span>  
 <span data-ttu-id="a0700-127">[如何新增範圍圖形](../core/how-to-add-a-scope-shape3.md) </span><span class="sxs-lookup"><span data-stu-id="a0700-127">[How to Add a Scope Shape](../core/how-to-add-a-scope-shape3.md) </span></span>  
 [<span data-ttu-id="a0700-128">使用 BizTalk Server 例外狀況處理</span><span class="sxs-lookup"><span data-stu-id="a0700-128">Using BizTalk Server Exception Handling</span></span>](../core/using-biztalk-server-exception-handling1.md)