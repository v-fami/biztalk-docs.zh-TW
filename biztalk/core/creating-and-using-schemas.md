---
title: "建立和使用結構描述 |Microsoft 文件"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- generating schemas
- schemas
- creating schemas
- schemas, generating
ms.assetid: 3927b0b3-db3b-4494-b003-d930af734e58
caps.latest.revision: "9"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: f10275c5ed0b887907c7b26b7d1ce8ad5003b099
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/20/2017
---
# <a name="creating-and-using-schemas"></a><span data-ttu-id="9f2c9-102">建立和使用結構描述</span><span class="sxs-lookup"><span data-stu-id="9f2c9-102">Creating and Using Schemas</span></span>
<span data-ttu-id="9f2c9-103">Microsoft BizTalk Adapter for TIBCO Enterprise Message Service (EMS) 會使用您利用 XML 編輯器或 Visual Studio 的 BizTalk Server 編輯器 (僅限當您在協調流程中使用配接器時) 建立的結構描述。</span><span class="sxs-lookup"><span data-stu-id="9f2c9-103">Microsoft BizTalk Adapter for TIBCO Enterprise Message Service (EMS) uses schemas that you create using an XML editor or the BizTalk Server Editor in Visual Studio (only when you use the adapter in an orchestration).</span></span> <span data-ttu-id="9f2c9-104">結構描述說明您預期的資訊類型。</span><span class="sxs-lookup"><span data-stu-id="9f2c9-104">The schema describes the type of information that you expect.</span></span> <span data-ttu-id="9f2c9-105">本主題包含傳送與接收處理常式的資訊。</span><span class="sxs-lookup"><span data-stu-id="9f2c9-105">This topic contains information for both a send and a receive handler.</span></span>  
  
 <span data-ttu-id="9f2c9-106">您建立來與 BizTalk Adapter for TIBCO Enterprise Message Service 搭配使用的結構描述必須有目標命名空間。</span><span class="sxs-lookup"><span data-stu-id="9f2c9-106">The schemas you create for use with BizTalk Adapter for TIBCO Enterprise Message Service must have a target namespace.</span></span> <span data-ttu-id="9f2c9-107">BizTalk Server 需要目標命名空間，因為那是讓指定的訊息執行個體與指定的協調流程產生關聯的索引鍵。</span><span class="sxs-lookup"><span data-stu-id="9f2c9-107">BizTalk Server requires the target namespace because it is the key that associates a given message instance with a given orchestration.</span></span> <span data-ttu-id="9f2c9-108">換句話說，協調流程會訂閱擁有特定目標命名空間的任何訊息，而含有該目標命名空間的內送 XML 訊息會提供給訂閱該訊息的每個協調流程。</span><span class="sxs-lookup"><span data-stu-id="9f2c9-108">In other words, an orchestration subscribes to any message that has a specific target namespace, and an incoming XML message that has that target namespace is given to every orchestration that subscribed to the message.</span></span> <span data-ttu-id="9f2c9-109">如果 XML 文件結構描述沒有目標命名空間，BizTalk Server 會使用根項目的名稱做為索引鍵。</span><span class="sxs-lookup"><span data-stu-id="9f2c9-109">If an XML document schema does not have a target namespace, BizTalk Server uses the name of the root element as a key.</span></span>  
  
## <a name="generating-a-schema"></a><span data-ttu-id="9f2c9-110">產生結構描述</span><span class="sxs-lookup"><span data-stu-id="9f2c9-110">Generating a Schema</span></span>  
 <span data-ttu-id="9f2c9-111">下列程序說明如何產生結構描述，以及如何設定目標命名空間。</span><span class="sxs-lookup"><span data-stu-id="9f2c9-111">The following procedures show how to generate a schema and how to set the target namespace.</span></span>  
  
#### <a name="to-generate-a-schema-using-biztalk-editor"></a><span data-ttu-id="9f2c9-112">使用 BizTalk 編輯器產生結構描述</span><span class="sxs-lookup"><span data-stu-id="9f2c9-112">To generate a schema using BizTalk Editor</span></span>  
  
1.  <span data-ttu-id="9f2c9-113">在 [BizTalk 編輯器] 中開啟專案。</span><span class="sxs-lookup"><span data-stu-id="9f2c9-113">In the BizTalk Editor, open your project.</span></span>  
  
2.  <span data-ttu-id="9f2c9-114">在 [方案總管] 右上方中，選取**新增**，然後選取**新增產生的項目**。</span><span class="sxs-lookup"><span data-stu-id="9f2c9-114">Under Solution Explorer in the upper-right, select **Add**, and then select **Add Generated Items**.</span></span>  
  
3.  <span data-ttu-id="9f2c9-115">在**範本**窗格中，選取**產生結構描述**，然後按一下 **新增**。</span><span class="sxs-lookup"><span data-stu-id="9f2c9-115">In the **Templates** pane, select **Generate Schemas**, and then click **Add**.</span></span>  
  
4.  <span data-ttu-id="9f2c9-116">在**產生結構描述**對話方塊中，於**文件類型**清單中，選取**格式正確的 XML**。</span><span class="sxs-lookup"><span data-stu-id="9f2c9-116">In the **Generate Schemas** dialog box, in the **Document type** list, select **Well-Formed XML**.</span></span>  
  
5.  <span data-ttu-id="9f2c9-117">按一下**瀏覽**找出您要產生結構描述，然後輸入的檔案**確定**。</span><span class="sxs-lookup"><span data-stu-id="9f2c9-117">Click **Browse** to locate the input file for which you want to generate a schema, and then click **OK**.</span></span>  
  
     <span data-ttu-id="9f2c9-118">接下來，您必須設定目標命名空間。</span><span class="sxs-lookup"><span data-stu-id="9f2c9-118">Next, you must set the target namespace.</span></span>  
  
#### <a name="to-set-the-target-namespace"></a><span data-ttu-id="9f2c9-119">設定目標命名空間</span><span class="sxs-lookup"><span data-stu-id="9f2c9-119">To set the target namespace</span></span>  
  
1.  <span data-ttu-id="9f2c9-120">在 [BizTalk 編輯器] 中，開啟結構描述檔案，以滑鼠右鍵按一下**\<結構描述 >**，然後選取**屬性**。</span><span class="sxs-lookup"><span data-stu-id="9f2c9-120">In BizTalk Editor, open your schema file, right-click **\<schema>**, and then select **Properties**.</span></span>  
  
2.  <span data-ttu-id="9f2c9-121">在**屬性** 窗格中，找出**命名空間**欄位並輸入名稱，例如`testNameSpace`。</span><span class="sxs-lookup"><span data-stu-id="9f2c9-121">In the **Properties** pane, locate the **Namespace** field and type a name, for example, `testNameSpace`.</span></span>  
  
 <span data-ttu-id="9f2c9-122">您之後可以使用訊息繼續您的協調流程。</span><span class="sxs-lookup"><span data-stu-id="9f2c9-122">You can then continue with your orchestration using messages.</span></span> <span data-ttu-id="9f2c9-123">在挑選訊息後，BizTalk Server 會尋找使用的結構描述具有所設定目標命名空間的協調流程，接著進行協調流程程序。</span><span class="sxs-lookup"><span data-stu-id="9f2c9-123">When a message is picked up, BizTalk Server finds an orchestration that uses a schema with a set target namespace, and the orchestration process is followed.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="9f2c9-124">另請參閱</span><span class="sxs-lookup"><span data-stu-id="9f2c9-124">See Also</span></span>  
 [<span data-ttu-id="9f2c9-125">開發應用程式</span><span class="sxs-lookup"><span data-stu-id="9f2c9-125">Developing Applications</span></span>](../core/developing-applications5.md)