---
title: 步驟 5： 升級結構描述屬性 |Microsoft 文件
ms.custom: ''
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- message enrichment tutorial, pomoted properties
- promoted properties
- schemas, promoted properties
ms.assetid: cb51cece-1b65-4ba2-b8e6-ce8b6694cdb6
caps.latest.revision: 5
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 91d68ece5bedf7ec46a6d5ede7efc6878fa972fc
ms.sourcegitcommit: 3fc338e52d5dbca2c3ea1685a2faafc7582fe23a
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/01/2017
ms.locfileid: "26004471"
---
# <a name="step-5-promote-schema-properties"></a><span data-ttu-id="30e61-102">步驟 5： 升級結構描述屬性</span><span class="sxs-lookup"><span data-stu-id="30e61-102">Step 5: Promote Schema Properties</span></span>
<span data-ttu-id="30e61-103">在此步驟中，您將升級結構描述屬性，讓[!INCLUDE[btsBizTalkServerNoVersion](../../includes/btsbiztalkservernoversion-md.md)]協調流程可以參考您在稍後步驟中建立那些屬性值。</span><span class="sxs-lookup"><span data-stu-id="30e61-103">In this step, you promote schema properties so that a [!INCLUDE[btsBizTalkServerNoVersion](../../includes/btsbiztalkservernoversion-md.md)] orchestration can reference those property values that you create in later steps.</span></span> <span data-ttu-id="30e61-104">升級是一套機制，您使用參考訊息執行個體中的特定值，並且讓它存取[!INCLUDE[btsBizTalkServerNoVersion](../../includes/btsbiztalkservernoversion-md.md)]元件，例如協調流程或以內容為基礎的路由達成目的。</span><span class="sxs-lookup"><span data-stu-id="30e61-104">Promotion is a mechanism that you use to reference a specific value within a message instance and make it accessible to [!INCLUDE[btsBizTalkServerNoVersion](../../includes/btsbiztalkservernoversion-md.md)] components such as orchestration or for content-based routing purposes.</span></span> <span data-ttu-id="30e61-105">此外，升級的屬性會顯示[!INCLUDE[btsCoName](../../includes/btsconame-md.md)]在 「 運算式編輯器的 IntelliSense [!INCLUDE[btsVStudioNoVersion](../../includes/btsvstudionoversion-md.md)]。</span><span class="sxs-lookup"><span data-stu-id="30e61-105">Additionally, a promoted property is visible by [!INCLUDE[btsCoName](../../includes/btsconame-md.md)] IntelliSense in the Expression Editor of [!INCLUDE[btsVStudioNoVersion](../../includes/btsvstudionoversion-md.md)].</span></span>  
  
> [!NOTE]
>  [!INCLUDE[btaBTAHL71.3abbrevnonumber](../../includes/btabtahl71-3abbrevnonumber-md.md)]<span data-ttu-id="30e61-106">稽核和記錄功能與 「 BizTalk 狀況與活動追蹤 (HAT) 工具可以追蹤只升級的結構描述屬性。</span><span class="sxs-lookup"><span data-stu-id="30e61-106"> auditing and logging functionality with the BizTalk Health and Activity Tracking (HAT) tool can track only promoted schema properties.</span></span>  
  
### <a name="to-promote-schema-properties"></a><span data-ttu-id="30e61-107">若要升級結構描述屬性</span><span class="sxs-lookup"><span data-stu-id="30e61-107">To promote schema properties</span></span>  
  
1.  <span data-ttu-id="30e61-108">在 方案總管下**BTAHL7 專案**，連按兩下**DoorBell.xsd**開啟結構描述的節點。</span><span class="sxs-lookup"><span data-stu-id="30e61-108">In Solution Explorer, under **BTAHL7 Project**, double-click the **DoorBell.xsd** node to open the schema.</span></span>  
  
2.  <span data-ttu-id="30e61-109">以滑鼠右鍵按一下**FirstName**欄位項目，指向**升階**，然後按一下 **快速升級**。</span><span class="sxs-lookup"><span data-stu-id="30e61-109">Right-click the **FirstName** field element, point to **Promote**, and then click **Quick Promotion**.</span></span>  
  
3.  <span data-ttu-id="30e61-110">按一下**確定**將屬性結構描述加入至專案。</span><span class="sxs-lookup"><span data-stu-id="30e61-110">Click **OK** to add the property schema to the project.</span></span>  
  
    > [!NOTE]
    >  [!INCLUDE[btsVStudioNoVersion](../../includes/btsvstudionoversion-md.md)]<span data-ttu-id="30e61-111">加入圖示的橙色圓形**FirstName**項目，表示已升級項目。</span><span class="sxs-lookup"><span data-stu-id="30e61-111"> adds an orange circle to the icon for the **FirstName** element, indicating that the element has been promoted.</span></span>  
  
4.  <span data-ttu-id="30e61-112">重複這些步驟將升級下列欄位項目：</span><span class="sxs-lookup"><span data-stu-id="30e61-112">Repeat these steps to promote the following field elements:</span></span>  
  
    -   <span data-ttu-id="30e61-113">**MiddleName**</span><span class="sxs-lookup"><span data-stu-id="30e61-113">**MiddleName**</span></span>  
  
    -   <span data-ttu-id="30e61-114">**LastName**</span><span class="sxs-lookup"><span data-stu-id="30e61-114">**LastName**</span></span>  
  
    -   <span data-ttu-id="30e61-115">**SSN**</span><span class="sxs-lookup"><span data-stu-id="30e61-115">**SSN**</span></span>  
  
    > [!IMPORTANT]
    >  <span data-ttu-id="30e61-116">請務必注意例如身分證號碼 (SSN) 會導致該升級一位病患識別碼 (PID)[!INCLUDE[btaBTAHL71.3abbrevnonumber](../../includes/btabtahl71-3abbrevnonumber-md.md)]追蹤整個系統的每個輸入訊息屬性。</span><span class="sxs-lookup"><span data-stu-id="30e61-116">It is important to note that promoting a patient ID (PID) such as a social security number (SSN) causes [!INCLUDE[btaBTAHL71.3abbrevnonumber](../../includes/btabtahl71-3abbrevnonumber-md.md)] to track that property for every inbound message through the system.</span></span> <span data-ttu-id="30e61-117">造成這種情況的副作用是，訊息追蹤資料庫會保留一份病患 s s n s。</span><span class="sxs-lookup"><span data-stu-id="30e61-117">The side effect of this situation is that the message-tracking database keeps a copy of patient SSNs.</span></span> <span data-ttu-id="30e61-118">這樣可以建立重大的安全性問題。</span><span class="sxs-lookup"><span data-stu-id="30e61-118">This can create a significant security issue.</span></span> <span data-ttu-id="30e61-119">您必須保護這個資料存放區，與必須特別小心，或完全避免 PID 資料的升級。</span><span class="sxs-lookup"><span data-stu-id="30e61-119">You must either protect this data store with extreme care or avoid the promotion of PID data completely.</span></span>  
  
     <span data-ttu-id="30e61-120">如需追蹤您已升級的結構描述項目為基礎的文件的詳細資訊，請參閱 < BizTalk Server 說明的健全狀況與活動追蹤的詳細資訊。</span><span class="sxs-lookup"><span data-stu-id="30e61-120">For more information about tracking documents based on the schema elements that you promoted, see BizTalk Server Help for information on Health and Activity Tracking.</span></span>  
  
 <span data-ttu-id="30e61-121">若要繼續[步驟 6： 驗證結構描述](../../adapters-and-accelerators/accelerator-hl7/step-6-validate-the-schemas.md)。</span><span class="sxs-lookup"><span data-stu-id="30e61-121">Proceed to [Step 6: Validate the Schemas](../../adapters-and-accelerators/accelerator-hl7/step-6-validate-the-schemas.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="30e61-122">請參閱</span><span class="sxs-lookup"><span data-stu-id="30e61-122">See Also</span></span>  
 [<span data-ttu-id="30e61-123">訊息擴充教學課程</span><span class="sxs-lookup"><span data-stu-id="30e61-123">Message Enrichment Tutorial</span></span>](../../adapters-and-accelerators/accelerator-hl7/message-enrichment-tutorial.md)