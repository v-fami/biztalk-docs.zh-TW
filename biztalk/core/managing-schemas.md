---
title: 管理結構描述 |Microsoft 文件
description: 使用在 BizTalk Server 中，包括顯示和隱藏屬性結構描述使用 BizTalk 管理 檢視的 XSD，啟用追蹤
ms.custom: ''
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: c5632e79-b182-41c9-9138-eb88b44e3172
caps.latest.revision: 11
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: f0d7fe3eee97cf81c668ffe90fd9c0897af23cc1
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/20/2017
ms.locfileid: "22262598"
---
# <a name="manage-schemas"></a><span data-ttu-id="53896-103">管理結構描述</span><span class="sxs-lookup"><span data-stu-id="53896-103">Manage Schemas</span></span>

## <a name="overiew"></a><span data-ttu-id="53896-104">概觀</span><span class="sxs-lookup"><span data-stu-id="53896-104">Overiew</span></span>
<span data-ttu-id="53896-105">本節提供使用 [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] 管理主控台管理結構描述的指示。</span><span class="sxs-lookup"><span data-stu-id="53896-105">This section provides instructions on using the [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] Administration console to manage schemas.</span></span> <span data-ttu-id="53896-106">結構描述可供管線及協調流程用來呈現所要處理的訊息。</span><span class="sxs-lookup"><span data-stu-id="53896-106">Schemas are used by pipelines and orchestrations to represent the message that will be processed.</span></span>  
  
 <span data-ttu-id="53896-107">結構描述是在 [!INCLUDE[btsVStudioNoVersion](../includes/btsvstudionoversion-md.md)] 中建立，並編譯成 BizTalk 組件。</span><span class="sxs-lookup"><span data-stu-id="53896-107">Schemas are created in [!INCLUDE[btsVStudioNoVersion](../includes/btsvstudionoversion-md.md)] and compiled into BizTalk assemblies.</span></span> <span data-ttu-id="53896-108">您不能將結構描述個別新增到應用程式中；結構描述會在下列情況中新增至應用程式：</span><span class="sxs-lookup"><span data-stu-id="53896-108">You cannot add a schema to an application individually; a schema is added to an application as follows:</span></span>  
  
-   <span data-ttu-id="53896-109">當您新增 BizTalk 組件包含應用程式，結構描述中所述[如何將 BizTalk 組件新增至應用程式](../core/how-to-add-a-biztalk-assembly-to-an-application.md)。</span><span class="sxs-lookup"><span data-stu-id="53896-109">When you add a BizTalk assembly containing a schema to the application, as described in [How to Add a BizTalk Assembly to an Application](../core/how-to-add-a-biztalk-assembly-to-an-application.md).</span></span>  
  
-   <span data-ttu-id="53896-110">當您匯入.msi 檔案包含結構描述，其中包含 BizTalk 組件中所述的應用程式[如何匯入 BizTalk 應用程式](../core/how-to-import-a-biztalk-application.md)。</span><span class="sxs-lookup"><span data-stu-id="53896-110">When you import an .msi file into an application that includes a BizTalk assembly containing a schema, as described in [How to Import a BizTalk Application](../core/how-to-import-a-biztalk-application.md).</span></span>  
  
-   <span data-ttu-id="53896-111">當開發人員應用程式組件部署到包含從結構描述[!INCLUDE[btsVStudioNoVersion](../includes/btsvstudionoversion-md.md)]中所述，[從到 BizTalk 應用程式的 Visual Studio 部署 BizTalk 組件](../core/deploying-biztalk-assemblies-from-visual-studio-into-a-biztalk-application.md)。</span><span class="sxs-lookup"><span data-stu-id="53896-111">When a developer deploys into an application an assembly containing a schema from [!INCLUDE[btsVStudioNoVersion](../includes/btsvstudionoversion-md.md)], as described in [Deploying BizTalk Assemblies from Visual Studio into a BizTalk Application](../core/deploying-biztalk-assemblies-from-visual-studio-into-a-biztalk-application.md).</span></span>  
  
 <span data-ttu-id="53896-112">如需結構描述的背景資訊，請參閱[結構描述](../core/schemas.md)。</span><span class="sxs-lookup"><span data-stu-id="53896-112">For background information about schemas, see [Schemas](../core/schemas.md).</span></span> <span data-ttu-id="53896-113">如需開發結構描述的詳細資訊，請參閱[建立結構描述使用 BizTalk 編輯器](../core/creating-schemas-using-biztalk-editor.md)。</span><span class="sxs-lookup"><span data-stu-id="53896-113">For information about developing schemas, see [Creating Schemas Using BizTalk Editor](../core/creating-schemas-using-biztalk-editor.md).</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="53896-114">您可以使用 Microsoft Windows Management Instrumentation (WMI) 物件模型，建立和執行會自動化系統管理工作的指令碼。</span><span class="sxs-lookup"><span data-stu-id="53896-114">You can use Microsoft Windows Management Instrumentation (WMI) Object Model to create and run scripts that automate administrative tasks.</span></span> <span data-ttu-id="53896-115">如需使用 WMI 的詳細資訊，請參閱**WMI 類別參考** [!INCLUDE[ui-guidance-developers-reference](../includes/ui-guidance-developers-reference.md)]。</span><span class="sxs-lookup"><span data-stu-id="53896-115">For information about using WMI, see the **WMI Class Reference** [!INCLUDE[ui-guidance-developers-reference](../includes/ui-guidance-developers-reference.md)].</span></span>
  
## <a name="next-steps"></a><span data-ttu-id="53896-116">後續的步驟</span><span class="sxs-lookup"><span data-stu-id="53896-116">Next steps</span></span> 
  
-   [<span data-ttu-id="53896-117">顯示和隱藏屬性結構描述</span><span class="sxs-lookup"><span data-stu-id="53896-117">Show and Hide Property Schemas</span></span>](../core/how-to-show-and-hide-property-schemas.md)  
  
-   [<span data-ttu-id="53896-118">檢視結構描述定義 (XSD) 結構描述</span><span class="sxs-lookup"><span data-stu-id="53896-118">View the Schema Definition (XSD) of a Schema</span></span>](../core/how-to-view-the-schema-definition-xsd-of-a-schema.md)  
  
-   [<span data-ttu-id="53896-119">設定追蹤之結構描述</span><span class="sxs-lookup"><span data-stu-id="53896-119">Configure Tracking for a Schema</span></span>](../core/how-to-configure-tracking-for-a-schema.md)  
  
-   [<span data-ttu-id="53896-120">從應用程式移除結構描述</span><span class="sxs-lookup"><span data-stu-id="53896-120">Remove a Schema from an Application</span></span>](../core/how-to-remove-a-schema-from-an-application.md)