---
title: 關於在 BizTalk 專案中包含的 BizTalk 命名空間參考 |Microsoft 文件
ms.custom: ''
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- System.Xml namespace
- Microsoft.BizTalk.GlobalPropertySchemas namespace
- namespaces, System.Xml namespace
- System namespace
- namespaces, System namespace
- namespaces, Microsoft.BizTalk.GlobalPropertySchemas namespace
- Microsoft.BizTalk.DefaultPipelines namespace
- projects, namespaces
- namespaces, warnings
- namespaces, Microsoft.BIzTalk.DefaultPipelines namespace
- namespaces
ms.assetid: cb642eac-7307-44f8-bbba-3ae364e11ea2
caps.latest.revision: 10
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 820e15eb3524713dfd7d3f86311ca262fde191d5
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/20/2017
ms.locfileid: "22225174"
---
# <a name="about-biztalk-namespace-references-included-in-biztalk-projects"></a><span data-ttu-id="3ed4f-102">關於在 BizTalk 專案中包含的 BizTalk 命名空間參考</span><span class="sxs-lookup"><span data-stu-id="3ed4f-102">About BizTalk Namespace References Included in BizTalk Projects</span></span>
<span data-ttu-id="3ed4f-103">當您新增新的 BizTalk 專案時，預設會包含下列命名空間：</span><span class="sxs-lookup"><span data-stu-id="3ed4f-103">When you add a new BizTalk project, the following namespaces are included by default:</span></span>  
  
-   <span data-ttu-id="3ed4f-104">**Microsoft.BizTalk.DefaultPipelines**</span><span class="sxs-lookup"><span data-stu-id="3ed4f-104">**Microsoft.BizTalk.DefaultPipelines**</span></span>  
  
-   <span data-ttu-id="3ed4f-105">**Microsoft.BizTalk.GlobalPropertySchemas**</span><span class="sxs-lookup"><span data-stu-id="3ed4f-105">**Microsoft.BizTalk.GlobalPropertySchemas**</span></span>  
  
-   <span data-ttu-id="3ed4f-106">**系統**</span><span class="sxs-lookup"><span data-stu-id="3ed4f-106">**System**</span></span>  
  
-   <span data-ttu-id="3ed4f-107">**System.Xml**</span><span class="sxs-lookup"><span data-stu-id="3ed4f-107">**System.Xml**</span></span>  
  
 <span data-ttu-id="3ed4f-108">您也可以將新的參考和 Web 參考新增到您的專案。</span><span class="sxs-lookup"><span data-stu-id="3ed4f-108">You can also add new references and Web references to your project.</span></span> <span data-ttu-id="3ed4f-109">如需有關加入參考使用**專案**功能表上，請參閱[使用 Visual Studio](../core/using-visual-studio.md)。</span><span class="sxs-lookup"><span data-stu-id="3ed4f-109">For more information about adding references using the **Project** menu, see [Using Visual Studio](../core/using-visual-studio.md).</span></span> <span data-ttu-id="3ed4f-110">如需新增 Web 參考資訊，請參閱[加入 Web 參考](../core/adding-web-references.md)。</span><span class="sxs-lookup"><span data-stu-id="3ed4f-110">For information about adding Web references, see [Adding Web References](../core/adding-web-references.md).</span></span>  
  
> [!CAUTION]
>  <span data-ttu-id="3ed4f-111">請勿移除預設參考。</span><span class="sxs-lookup"><span data-stu-id="3ed4f-111">Do not remove the default references.</span></span> <span data-ttu-id="3ed4f-112">如果您移除預設參考，您可能會在專案中參考 BizTalk 項目時遇到問題。</span><span class="sxs-lookup"><span data-stu-id="3ed4f-112">If you remove the default references, you might encounter problems when referencing BizTalk items in your project.</span></span> <span data-ttu-id="3ed4f-113">您可以在方案總管中還原預設參考。</span><span class="sxs-lookup"><span data-stu-id="3ed4f-113">You can restore default references in Solution Explorer.</span></span>  
  
> [!CAUTION]
>  <span data-ttu-id="3ed4f-114">如果您的 BizTalk 專案參考另一個組件，而該組件已經更新，那麼在您的 BizTalk 專案中不會自動選擇更新或變更。</span><span class="sxs-lookup"><span data-stu-id="3ed4f-114">If your BizTalk project references another assembly, and that assembly is updated, the updates or changes are not automatically picked up in your BizTalk project.</span></span> <span data-ttu-id="3ed4f-115">您應該移除方案總管中已過期的參考，然後再次新增參考 (重新參考組件)。</span><span class="sxs-lookup"><span data-stu-id="3ed4f-115">You should remove the outdated reference in Solution Explorer, and then add the reference back (re-reference the assembly).</span></span> <span data-ttu-id="3ed4f-116">或者，您可以關閉您的方案然後重新開啟。</span><span class="sxs-lookup"><span data-stu-id="3ed4f-116">Alternatively, you can close your solution and reopen it.</span></span> <span data-ttu-id="3ed4f-117">不論使用哪種方式，您的專案都可以使用參考組件的最新更新。</span><span class="sxs-lookup"><span data-stu-id="3ed4f-117">In either case, the latest updates to the referenced assembly are available to your project.</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="3ed4f-118">本節內容</span><span class="sxs-lookup"><span data-stu-id="3ed4f-118">In This Section</span></span>  
  
-   [<span data-ttu-id="3ed4f-119">Microsoft.BizTalk.DefaultPipelines 參考</span><span class="sxs-lookup"><span data-stu-id="3ed4f-119">Microsoft.BizTalk.DefaultPipelines Reference</span></span>](../core/microsoft-biztalk-defaultpipelines-reference.md)  
  
-   [<span data-ttu-id="3ed4f-120">Microsoft.BizTalk.GlobalPropertySchemas 參考</span><span class="sxs-lookup"><span data-stu-id="3ed4f-120">Microsoft.BizTalk.GlobalPropertySchemas Reference</span></span>](../core/microsoft-biztalk-globalpropertyschemas-reference.md)  
  
-   [<span data-ttu-id="3ed4f-121">System 參考</span><span class="sxs-lookup"><span data-stu-id="3ed4f-121">System Reference</span></span>](../core/system-reference.md)  
  
-   [<span data-ttu-id="3ed4f-122">System.Xml 參考</span><span class="sxs-lookup"><span data-stu-id="3ed4f-122">System.Xml Reference</span></span>](../core/system-xml-reference.md)