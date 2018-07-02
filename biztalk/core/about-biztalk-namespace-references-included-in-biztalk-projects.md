---
title: 關於在 BizTalk 專案中包含的 BizTalk 命名空間參考 |Microsoft Docs
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
ms.openlocfilehash: 608f3ebf9a80553749fe5de558c2db05e3c7673d
ms.sourcegitcommit: 266308ec5c6a9d8d80ff298ee6051b4843c5d626
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/27/2018
ms.locfileid: "37016366"
---
# <a name="about-biztalk-namespace-references-included-in-biztalk-projects"></a><span data-ttu-id="ac9fc-102">關於在 BizTalk 專案中包含的 BizTalk 命名空間參考</span><span class="sxs-lookup"><span data-stu-id="ac9fc-102">About BizTalk Namespace References Included in BizTalk Projects</span></span>
<span data-ttu-id="ac9fc-103">當您新增新的 BizTalk 專案時，預設會包含下列命名空間：</span><span class="sxs-lookup"><span data-stu-id="ac9fc-103">When you add a new BizTalk project, the following namespaces are included by default:</span></span>  
  
- <span data-ttu-id="ac9fc-104">**Microsoft.BizTalk.DefaultPipelines**</span><span class="sxs-lookup"><span data-stu-id="ac9fc-104">**Microsoft.BizTalk.DefaultPipelines**</span></span>  
  
- <span data-ttu-id="ac9fc-105">**Microsoft.BizTalk.GlobalPropertySchemas**</span><span class="sxs-lookup"><span data-stu-id="ac9fc-105">**Microsoft.BizTalk.GlobalPropertySchemas**</span></span>  
  
- <span data-ttu-id="ac9fc-106">**系統**</span><span class="sxs-lookup"><span data-stu-id="ac9fc-106">**System**</span></span>  
  
- <span data-ttu-id="ac9fc-107">**System.Xml**</span><span class="sxs-lookup"><span data-stu-id="ac9fc-107">**System.Xml**</span></span>  
  
  <span data-ttu-id="ac9fc-108">您也可以將新的參考和 Web 參考新增到您的專案。</span><span class="sxs-lookup"><span data-stu-id="ac9fc-108">You can also add new references and Web references to your project.</span></span> <span data-ttu-id="ac9fc-109">如需新增參考使用**專案**功能表上，請參閱[使用 Visual Studio](../core/using-visual-studio.md)。</span><span class="sxs-lookup"><span data-stu-id="ac9fc-109">For more information about adding references using the **Project** menu, see [Using Visual Studio](../core/using-visual-studio.md).</span></span> <span data-ttu-id="ac9fc-110">如需新增 Web 參考的資訊，請參閱[加入 Web 參考](../core/adding-web-references.md)。</span><span class="sxs-lookup"><span data-stu-id="ac9fc-110">For information about adding Web references, see [Adding Web References](../core/adding-web-references.md).</span></span>  
  
> [!CAUTION]
>  <span data-ttu-id="ac9fc-111">請勿移除預設參考。</span><span class="sxs-lookup"><span data-stu-id="ac9fc-111">Do not remove the default references.</span></span> <span data-ttu-id="ac9fc-112">如果您移除預設參考，您可能會在專案中參考 BizTalk 項目時遇到問題。</span><span class="sxs-lookup"><span data-stu-id="ac9fc-112">If you remove the default references, you might encounter problems when referencing BizTalk items in your project.</span></span> <span data-ttu-id="ac9fc-113">您可以在方案總管中還原預設參考。</span><span class="sxs-lookup"><span data-stu-id="ac9fc-113">You can restore default references in Solution Explorer.</span></span>  
  
> [!CAUTION]
>  <span data-ttu-id="ac9fc-114">如果您的 BizTalk 專案參考另一個組件，而該組件已經更新，那麼在您的 BizTalk 專案中不會自動選擇更新或變更。</span><span class="sxs-lookup"><span data-stu-id="ac9fc-114">If your BizTalk project references another assembly, and that assembly is updated, the updates or changes are not automatically picked up in your BizTalk project.</span></span> <span data-ttu-id="ac9fc-115">您應該移除方案總管中已過期的參考，然後再次新增參考 (重新參考組件)。</span><span class="sxs-lookup"><span data-stu-id="ac9fc-115">You should remove the outdated reference in Solution Explorer, and then add the reference back (re-reference the assembly).</span></span> <span data-ttu-id="ac9fc-116">或者，您可以關閉您的方案然後重新開啟。</span><span class="sxs-lookup"><span data-stu-id="ac9fc-116">Alternatively, you can close your solution and reopen it.</span></span> <span data-ttu-id="ac9fc-117">不論使用哪種方式，您的專案都可以使用參考組件的最新更新。</span><span class="sxs-lookup"><span data-stu-id="ac9fc-117">In either case, the latest updates to the referenced assembly are available to your project.</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="ac9fc-118">本節內容</span><span class="sxs-lookup"><span data-stu-id="ac9fc-118">In This Section</span></span>  
  
-   [<span data-ttu-id="ac9fc-119">Microsoft.BizTalk.DefaultPipelines 參考</span><span class="sxs-lookup"><span data-stu-id="ac9fc-119">Microsoft.BizTalk.DefaultPipelines Reference</span></span>](../core/microsoft-biztalk-defaultpipelines-reference.md)  
  
-   [<span data-ttu-id="ac9fc-120">Microsoft.BizTalk.GlobalPropertySchemas 參考</span><span class="sxs-lookup"><span data-stu-id="ac9fc-120">Microsoft.BizTalk.GlobalPropertySchemas Reference</span></span>](../core/microsoft-biztalk-globalpropertyschemas-reference.md)  
  
-   [<span data-ttu-id="ac9fc-121">System 參考</span><span class="sxs-lookup"><span data-stu-id="ac9fc-121">System Reference</span></span>](../core/system-reference.md)  
  
-   [<span data-ttu-id="ac9fc-122">System.Xml 參考</span><span class="sxs-lookup"><span data-stu-id="ac9fc-122">System.Xml Reference</span></span>](../core/system-xml-reference.md)