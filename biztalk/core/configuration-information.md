---
title: 組態資訊 |Microsoft 文件
ms.custom: ''
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- Call Rules shape [Orchestration Designer], planning
- Call Rules shape [Orchestration Designer], configuring
ms.assetid: aa4924c6-4270-473b-aa0a-6d8b18375a39
caps.latest.revision: 11
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: f9a35767815eaf7406a7baae5d9dccb833492287
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/20/2017
ms.locfileid: "22233462"
---
# <a name="configuration-information"></a><span data-ttu-id="954da-102">組態資訊</span><span class="sxs-lookup"><span data-stu-id="954da-102">Configuration Information</span></span>
<span data-ttu-id="954da-103">本主題描述如何設定**呼叫規則**圖形。</span><span class="sxs-lookup"><span data-stu-id="954da-103">This topic describes how to configure the **Call Rules** shape.</span></span>  
  
## <a name="orchestration-variables-and-fact-types"></a><span data-ttu-id="954da-104">協調流程變數和事實類型</span><span class="sxs-lookup"><span data-stu-id="954da-104">Orchestration variables and fact types</span></span>  
 <span data-ttu-id="954da-105">在協調流程其中**呼叫規則**圖形所在，您必須具有符合原則中所使用的類型的變數。</span><span class="sxs-lookup"><span data-stu-id="954da-105">In the orchestration where the **Call Rules** shape resides, you must have variables that match types used in the policy.</span></span> <span data-ttu-id="954da-106">若您的變數類型不正確，就無法提供正確的參數給原則。</span><span class="sxs-lookup"><span data-stu-id="954da-106">If you do not have the correct types of variables, you cannot supply the correct parameters to the policy.</span></span> <span data-ttu-id="954da-107">假設您有**呼叫規則**圖形在協調流程為 CallMyRules，且您使用 CallMyRules 來呼叫 MyPolicy。</span><span class="sxs-lookup"><span data-stu-id="954da-107">Suppose that you have a **Call Rules** shape in an orchestration, CallMyRules, and you use CallMyRules to call MyPolicy.</span></span> <span data-ttu-id="954da-108">若在 MyPolicy 中使用的 .NET 類別為 MyClass，則您必須在協調流程中建立 MyAssembly.MyClass 類型的變數。</span><span class="sxs-lookup"><span data-stu-id="954da-108">If a .NET class, MyClass, is used in MyPolicy, you must create a variable of a MyAssembly.MyClass type in the orchestration.</span></span> <span data-ttu-id="954da-109">同樣地，若 MyPolicy 擁有**DataConnection**繫結，您必須建立的變數**Microsoft.RuleEngine.DataConnection**協調流程中的型別。</span><span class="sxs-lookup"><span data-stu-id="954da-109">Similarly, if MyPolicy has **DataConnection** bindings, you must create a variable of a **Microsoft.RuleEngine.DataConnection** type in the orchestration.</span></span>  
  
 <span data-ttu-id="954da-110">除了在協調流程內建立變數，您還必須為這些範圍變數建立執行個體。</span><span class="sxs-lookup"><span data-stu-id="954da-110">In addition to creating the variables in the orchestration, you must also create instances for these variables.</span></span> <span data-ttu-id="954da-111">您可以藉由新增**運算式**圖形至協調流程。</span><span class="sxs-lookup"><span data-stu-id="954da-111">You can do this by adding an **Expression** shape to your orchestration.</span></span> <span data-ttu-id="954da-112">使用上述範例中，您必須產生 MyAssembly.MyClass 執行個體和**DataConnection**執行個體。</span><span class="sxs-lookup"><span data-stu-id="954da-112">Using the preceding example, you should instantiate a MyAssembly.MyClass instance and a **DataConnection** instance.</span></span> <span data-ttu-id="954da-113">具現化**DataConnection**執行個體，執行下列動作：</span><span class="sxs-lookup"><span data-stu-id="954da-113">To instantiate the **DataConnection** instance, you do the following:</span></span>  
  
-   <span data-ttu-id="954da-114">建立**SqlConnection**執行個體，並將它指派給 MySqlCon。</span><span class="sxs-lookup"><span data-stu-id="954da-114">Create a **SqlConnection** instance and assign it to MySqlCon.</span></span>  
  
-   <span data-ttu-id="954da-115">建立**DataConnection**執行個體，並將它指派給 dataConnection (變數**DataConnection**類型)，如下列程式碼片段所示：</span><span class="sxs-lookup"><span data-stu-id="954da-115">Create a **DataConnection** instance and assign it to dataConnection (variable of **DataConnection** type), as shown in the following code fragment:</span></span>  
  
    ```  
    dataConnection = new Microsoft.RuleEngine.DataConnection("NameOfSqlDatabaseHere", "NameOfYourTableHere", MySqlCon);  
    ```  
  
> [!NOTE]
>  <span data-ttu-id="954da-116">如果沒有相符的事實類型的變數，這些類型不會出現在參數**指定原則參數**清單方塊中的 **[CallRules 原則組態**] 對話方塊。</span><span class="sxs-lookup"><span data-stu-id="954da-116">If you do not have variables matching the fact types, these types will not appear as parameters in the **Specify policy parameters** list box in the **CallRules policy configuration** dialog box.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="954da-117">協調流程引擎會自動轉換做為參數，BRE 原則到您指定的訊息變數**TypedXmlDocument**物件，並將它們判斷提示至規則引擎執行原則之前的工作記憶體。</span><span class="sxs-lookup"><span data-stu-id="954da-117">The orchestration engine automatically converts the message variables you specify as parameters to a BRE policy into **TypedXmlDocument** objects, and asserts them into working memory of the rule engine prior to executing the policy.</span></span> <span data-ttu-id="954da-118">因此，您不需要像處理 .NET 和資料庫事實一樣，宣告 TypedXmlDocument 型別的變數。</span><span class="sxs-lookup"><span data-stu-id="954da-118">Therefore, you do not need to declare variables of type TypedXmlDocument as you did for .NET and database facts.</span></span>  
  
## <a name="message-type-and-document-type"></a><span data-ttu-id="954da-119">訊息類型和文件類型</span><span class="sxs-lookup"><span data-stu-id="954da-119">Message type and document type</span></span>  
 <span data-ttu-id="954da-120">您必須確定**DocumentType** （您所實作的商務規則編輯器 」 中） 您的商務規則中使用的 XML 節點的屬性等同於**MessageType**中定義這些 XML 節點協調流程，它必須符合**MessageType**訊息或訊息部分，將會傳遞至規則引擎中的**呼叫規則**圖形。</span><span class="sxs-lookup"><span data-stu-id="954da-120">You must ensure that the **DocumentType** property for XML nodes used in your business rule (that you implement in the Business Rule Composer) is the same as the **MessageType** for those XML nodes defined in the orchestration—it must match the **MessageType** of the message or message part that will be passed to the rule engine in the **Call Rules** shape.</span></span>  
  
 <span data-ttu-id="954da-121">例如，如果您在 BizTalk 專案中，定義訂單 (PO) XML 結構描述**MessageType**針對此結構描述定義**BTSProject.PO** (如果**BTSProject**是命名空間或使用預設命名空間的專案名稱）。</span><span class="sxs-lookup"><span data-stu-id="954da-121">For example, if you define a purchase order (PO) XML schema in a BizTalk project, the **MessageType** defined for this schema is **BTSProject.PO** (if **BTSProject** is the namespace or the project name using the default namespace).</span></span>  
  
 <span data-ttu-id="954da-122">如果是**PO\Amount**項目，才能卸除到規則定義，您必須變更其**DocumentType**屬性**BTSProject.PO**中 [屬性] 視窗.</span><span class="sxs-lookup"><span data-stu-id="954da-122">In the case of the **PO\Amount** element, before you drop it into a rule definition, you must change its **DocumentType**property to **BTSProject.PO** in the properties window.</span></span> <span data-ttu-id="954da-123">選取結構描述中的任何節點上時，您可以存取 屬性 視窗**XML 結構描述** 索引標籤 事實總管 中的。</span><span class="sxs-lookup"><span data-stu-id="954da-123">You can access the properties window when any node in the schema is selected on the **XML Schemas** tab in the Facts Explorer.</span></span> <span data-ttu-id="954da-124">此變更會套用至結構描述中的所有項目，但並不會隨著結構描述而儲存。</span><span class="sxs-lookup"><span data-stu-id="954da-124">This change is applied for all elements in the schema, but is not persisted with the schema.</span></span> <span data-ttu-id="954da-125">在啟動「商務規則編輯器」或重新載入結構描述後，必須將它重設。</span><span class="sxs-lookup"><span data-stu-id="954da-125">It must be reset when the Business Rule Composer is launched or the schema is reloaded.</span></span> <span data-ttu-id="954da-126">根據 XML 結構描述或直接從 XML 結構描述建置的規則，此動作對於詞彙定義而言是必要的。</span><span class="sxs-lookup"><span data-stu-id="954da-126">This is required for vocabulary definitions based either on XML schemas or on rules built directly from XML schemas.</span></span> <span data-ttu-id="954da-127">如果不這麼做，您仍然可以執行原則，但**呼叫規則**圖形將無法正常運作，並不會出現在訊息類型**指定原則參數**清單方塊中的 **[CallRules 原則組態**] 對話方塊。</span><span class="sxs-lookup"><span data-stu-id="954da-127">If you do not do this, you can still execute the policy, but the **Call Rules** shape will not work correctly, and message type will not appear in the **Specify policy parameters** list box in the **CallRules policy configuration** dialog box.</span></span>