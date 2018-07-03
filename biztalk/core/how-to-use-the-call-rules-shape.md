---
title: 如何使用 呼叫規則圖形 |Microsoft Docs
ms.custom: ''
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- Call Rules shape [Orchestration Designer], how to
- Call Rules shape [Orchestration Designer], configuring
- Call Rules shape [Orchestration Designer], policies
- policies, Call Rules shape [Orchestration Designer]
ms.assetid: e4bc8a2c-de7e-4e3a-81b8-12bcebb17d27
caps.latest.revision: 13
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 6955acfee9052a3b46dcfb70c90ecc95fe216be3
ms.sourcegitcommit: 266308ec5c6a9d8d80ff298ee6051b4843c5d626
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/27/2018
ms.locfileid: "37003111"
---
# <a name="how-to-use-the-call-rules-shape"></a><span data-ttu-id="b0967-102">如何使用呼叫規則圖形</span><span class="sxs-lookup"><span data-stu-id="b0967-102">How to Use the Call Rules Shape</span></span>
<span data-ttu-id="b0967-103">在協調流程設計師中，您可以使用**呼叫規則**圖形以呼叫商務原則。</span><span class="sxs-lookup"><span data-stu-id="b0967-103">In Orchestration Designer, you can use the **Call Rules** shape to call a business policy.</span></span>  
  
### <a name="to-configure-the-call-rules-shape"></a><span data-ttu-id="b0967-104">設定呼叫規則圖形</span><span class="sxs-lookup"><span data-stu-id="b0967-104">To configure the Call Rules shape</span></span>  
  
1. <span data-ttu-id="b0967-105">從 工具箱 中，在**BizTalk 協調流程**索引標籤，拖曳**呼叫規則** 圖形至協調流程設計介面上的連接線上。</span><span class="sxs-lookup"><span data-stu-id="b0967-105">From the Toolbox, in the **BizTalk Orchestrations** tab, drag the **Call Rules** shape onto a connecting line on the Orchestration Design Surface.</span></span>  
  
    <span data-ttu-id="b0967-106">-或-</span><span class="sxs-lookup"><span data-stu-id="b0967-106">—Or—</span></span>  
  
    <span data-ttu-id="b0967-107">以滑鼠右鍵按一下的連接線或圖形預留位置，您要加入的形狀，指向**插入圖形**操作功能表，然後按一下**呼叫規則**。</span><span class="sxs-lookup"><span data-stu-id="b0967-107">Right-click the connecting line or the shape placeholder where you want to add the shape, point to **Insert Shape** on the context menu, and then click **Call Rules**.</span></span>  
  
   > [!NOTE]
   >  <span data-ttu-id="b0967-108">在 BizTalk Server 中，您不需要有不可部分完成的範圍，插入**呼叫規則**圖形。</span><span class="sxs-lookup"><span data-stu-id="b0967-108">In BizTalk Server, you do not need to have an atomic scope to insert a **Call Rules** shape.</span></span> <span data-ttu-id="b0967-109">您可以拖曳**呼叫規則**圖形至協調流程設計介面，從 [工具箱]。</span><span class="sxs-lookup"><span data-stu-id="b0967-109">You can drag a **Call Rules** shape into the Orchestration Design Surface from the Toolbox.</span></span> <span data-ttu-id="b0967-110">不過，在 BizTalk Server**呼叫規則**功能表項目已停用操作功能表中如果您嘗試插入**呼叫規則**圖形的協調流程，並沒有不可部分完成的範圍內。</span><span class="sxs-lookup"><span data-stu-id="b0967-110">However, in BizTalk Server, the **Call Rules** menu item is disabled in the context menu if you try to insert a **Call Rules** shape inside an orchestration that does not have an atomic scope.</span></span> <span data-ttu-id="b0967-111">這是 [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] 產品的限制。</span><span class="sxs-lookup"><span data-stu-id="b0967-111">This is a limitation with the [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] product.</span></span>  
  
2. <span data-ttu-id="b0967-112">在協調流程設計師中，選取**呼叫規則**圖形。</span><span class="sxs-lookup"><span data-stu-id="b0967-112">In Orchestration Designer, select the **Call Rules** shape.</span></span>  
  
3. <span data-ttu-id="b0967-113">按兩下圖形以顯示**CallRules 原則組態** 對話方塊。</span><span class="sxs-lookup"><span data-stu-id="b0967-113">Double-click the shape to display the **CallRules policy configuration** dialog box.</span></span>  
  
4. <span data-ttu-id="b0967-114">在 **選取您想要呼叫的商務原則**下拉式清單中，選取您需要的原則。</span><span class="sxs-lookup"><span data-stu-id="b0967-114">In the **Select the business policy you wish to call** drop-down list, select the policy you need.</span></span>  
  
   > [!NOTE]
   >  <span data-ttu-id="b0967-115">呼叫規則組態在決定原則要使用的類型時，將查詢最新儲存的原則版本。</span><span class="sxs-lookup"><span data-stu-id="b0967-115">Call Rules configuration will look at the latest saved version of a policy when determining the types used in the policy.</span></span> <span data-ttu-id="b0967-116">在執行階段，則將使用最新部署的原則版本。</span><span class="sxs-lookup"><span data-stu-id="b0967-116">At run time, the latest deployed version of the policy will be used.</span></span>  
  
5. <span data-ttu-id="b0967-117">在 **指定原則參數**清單方塊中，選取 從變數**參數名稱**屬性。</span><span class="sxs-lookup"><span data-stu-id="b0967-117">In the **Specify policy parameters** list box, select a variable from the **Parameter Name** property.</span></span>  
  
   > [!NOTE]
   >  <span data-ttu-id="b0967-118">**呼叫規則**圖形基本上會重新建構訊息，如同使用**建構**圖形，接著可能會導致遺失訊息內容屬性。</span><span class="sxs-lookup"><span data-stu-id="b0967-118">The **Call Rules** shape is essentially reconstructing the message, as if using a **Construct** shape, which in turn may cause context properties of the message to be lost.</span></span>  
  
   > [!NOTE]
   >  <span data-ttu-id="b0967-119">您可以指定訊息或.NET 變數做為 BRE 原則的參數。</span><span class="sxs-lookup"><span data-stu-id="b0967-119">You can specify a message or a .NET variable as a parameter to a BRE policy.</span></span> <span data-ttu-id="b0967-120">要傳遞**TypedXmlDocument**事實，指定對應的訊息在協調流程中做為參數宣告。</span><span class="sxs-lookup"><span data-stu-id="b0967-120">To pass a **TypedXmlDocument** fact, specify the corresponding message declared in the orchestration as a parameter.</span></span> <span data-ttu-id="b0967-121">若要傳遞.NET 事實，指定.NET 變數宣告在協調流程中做為參數。</span><span class="sxs-lookup"><span data-stu-id="b0967-121">To pass a .NET fact, specify a .NET variable declared in the orchestration as a parameter.</span></span> <span data-ttu-id="b0967-122">若要將資料庫事實，指定型別的.NET 變數**DataConnection**或是**TypedDataTable**做為原則的參數。</span><span class="sxs-lookup"><span data-stu-id="b0967-122">To pass a database fact, specify a .NET variable of type **DataConnection** or **TypedDataTable** as a parameter to the policy.</span></span>