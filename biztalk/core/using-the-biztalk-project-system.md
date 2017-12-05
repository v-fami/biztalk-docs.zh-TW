---
title: "使用 BizTalk 專案系統 |Microsoft 文件"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- BizTalk Editor, opening
- BizTalk Mapper, opening
- Orchestration Designer, opening
- Pipeline Designer, opening
ms.assetid: a28c715e-128c-463a-b421-9b3efe76a530
caps.latest.revision: "23"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: c5b8c3a83d75219b9e52fd2ab13124480d772832
ms.sourcegitcommit: 3fc338e52d5dbca2c3ea1685a2faafc7582fe23a
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/01/2017
---
# <a name="using-the-biztalk-project-system"></a><span data-ttu-id="eb179-102">使用 BizTalk 專案系統</span><span class="sxs-lookup"><span data-stu-id="eb179-102">Using the BizTalk Project System</span></span>
<span data-ttu-id="eb179-103">您可以使用 BizTalk 專案系統，在 Microsoft [!INCLUDE[btsVStudioNoVersion](../includes/btsvstudionoversion-md.md)] 環境下建立、組織和設定 BizTalk 方案。</span><span class="sxs-lookup"><span data-stu-id="eb179-103">You can use the BizTalk project system to create, organize, and configure BizTalk solutions in the Microsoft [!INCLUDE[btsVStudioNoVersion](../includes/btsvstudionoversion-md.md)] environment.</span></span> <span data-ttu-id="eb179-104">本節中的主題與程序描述如何透過使用 BizTalk 專案系統執行許多工作。</span><span class="sxs-lookup"><span data-stu-id="eb179-104">The topics and procedures in this section describe how to perform various tasks by using the BizTalk project system.</span></span>  
  
 <span data-ttu-id="eb179-105">BizTalk Server 專案系統會使用相同的專案管理原則和程序使用中的其他 Microsoft Build Engine (MSBuild) 專案[!INCLUDE[btsVStudioNoVersion](../includes/btsvstudionoversion-md.md)]。</span><span class="sxs-lookup"><span data-stu-id="eb179-105">The BizTalk Server project system uses the same project management principles and procedures that you use with other Microsoft Build Engine (MSBuild) projects in [!INCLUDE[btsVStudioNoVersion](../includes/btsvstudionoversion-md.md)].</span></span> <span data-ttu-id="eb179-106">本節詳細描述在建立可於 Microsoft [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] 上執行的應用程式時，可能會使用的通用程序。</span><span class="sxs-lookup"><span data-stu-id="eb179-106">This section details common procedures that you might use when creating an application that runs on Microsoft [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)].</span></span>  
  
 <span data-ttu-id="eb179-107">如需 MSBuild 的詳細資訊，請參閱中的 MSBuild 參考章節[!INCLUDE[btsVStudioNoVersion](../includes/btsvstudionoversion-md.md)]結合處[http://go.microsoft.com/fwlink/?LinkId=193567](http://go.microsoft.com/fwlink/?LinkId=193567)。</span><span class="sxs-lookup"><span data-stu-id="eb179-107">For more information about MSBuild, see the MSBuild reference section in the [!INCLUDE[btsVStudioNoVersion](../includes/btsvstudionoversion-md.md)] Combined Collection at [http://go.microsoft.com/fwlink/?LinkId=193567](http://go.microsoft.com/fwlink/?LinkId=193567).</span></span>  
  
 <span data-ttu-id="eb179-108">如需有關使用[!INCLUDE[btsVStudioNoVersion](../includes/btsvstudionoversion-md.md)]環境中，請參閱中的 「 管理方案、 專案和檔案 」[!INCLUDE[btsVStudioNoVersion](../includes/btsvstudionoversion-md.md)]結合處[http://msdn.microsoft.com/library/wbzbtw81.aspx](http://msdn.microsoft.com/library/wbzbtw81.aspx)。</span><span class="sxs-lookup"><span data-stu-id="eb179-108">For more information about using the [!INCLUDE[btsVStudioNoVersion](../includes/btsvstudionoversion-md.md)] environment, see "Managing Solutions, Projects, and Files" in the [!INCLUDE[btsVStudioNoVersion](../includes/btsvstudionoversion-md.md)] Combined Collection at [http://msdn.microsoft.com/library/wbzbtw81.aspx](http://msdn.microsoft.com/library/wbzbtw81.aspx).</span></span>  
  
 <span data-ttu-id="eb179-109">下圖顯示 BizTalk 專案系統設計環境，與**新專案**對話方塊開啟。</span><span class="sxs-lookup"><span data-stu-id="eb179-109">The following figure shows the BizTalk project system design environment with the **New Project** dialog box open.</span></span>  
  
 <span data-ttu-id="eb179-110">![專案系統](../core/media/bts-biztalk2009-projectsystems.gif "bts_BizTalk2009_ProjectSystems")</span><span class="sxs-lookup"><span data-stu-id="eb179-110">![Project Systems](../core/media/bts-biztalk2009-projectsystems.gif "bts_BizTalk2009_ProjectSystems")</span></span>  
<span data-ttu-id="eb179-111">描述專案系統設計環境</span><span class="sxs-lookup"><span data-stu-id="eb179-111">Depicts the Project System Design Environment</span></span>  
  
### <a name="to-open-biztalk-editor"></a><span data-ttu-id="eb179-112">開啟 BizTalk 編輯器</span><span class="sxs-lookup"><span data-stu-id="eb179-112">To open BizTalk Editor</span></span>  
  
1.  <span data-ttu-id="eb179-113">在 [方案總管] 中按一下結構描述。</span><span class="sxs-lookup"><span data-stu-id="eb179-113">In Solution Explorer, click a schema.</span></span>  
  
    > [!NOTE]
    >  <span data-ttu-id="eb179-114">若要開啟 BizTalk 編輯器，您必須先建立結構描述，或開啟先前建立的結構描述。</span><span class="sxs-lookup"><span data-stu-id="eb179-114">To open BizTalk Editor, you must first create a schema or open a previously created schema.</span></span> <span data-ttu-id="eb179-115">如需建立結構描述資訊，請參閱[如何建立 XML 訊息結構描述](../core/how-to-create-schemas-for-xml-messages.md)。</span><span class="sxs-lookup"><span data-stu-id="eb179-115">For information about creating a schema, see [How to Create Schemas for XML Messages](../core/how-to-create-schemas-for-xml-messages.md).</span></span> <span data-ttu-id="eb179-116">另請參閱[加入專案項目](../core/adding-project-items.md)。</span><span class="sxs-lookup"><span data-stu-id="eb179-116">Also see [Adding Project Items](../core/adding-project-items.md).</span></span>  
  
2.  <span data-ttu-id="eb179-117">在**檢視**功能表上，按一下 **開啟**。</span><span class="sxs-lookup"><span data-stu-id="eb179-117">On the **View** menu, click **Open**.</span></span>  
  
     <span data-ttu-id="eb179-118">-或者-</span><span class="sxs-lookup"><span data-stu-id="eb179-118">—Or—</span></span>  
  
     <span data-ttu-id="eb179-119">結構描述中，以滑鼠右鍵按一下，然後按一下 **開啟**。</span><span class="sxs-lookup"><span data-stu-id="eb179-119">Right-click the schema, and then click **Open**.</span></span>  
  
     <span data-ttu-id="eb179-120">-或者-</span><span class="sxs-lookup"><span data-stu-id="eb179-120">—Or—</span></span>  
  
     <span data-ttu-id="eb179-121">按兩下結構描述。</span><span class="sxs-lookup"><span data-stu-id="eb179-121">Double-click the schema.</span></span>  
  
     <span data-ttu-id="eb179-122">BizTalk 編輯器中就會開啟選取的結構描述。</span><span class="sxs-lookup"><span data-stu-id="eb179-122">The selected schema opens in BizTalk Editor.</span></span>  
  
    > [!NOTE]
    >  <span data-ttu-id="eb179-123">若要建立結構描述，您必須開啟一個專案。</span><span class="sxs-lookup"><span data-stu-id="eb179-123">To create a schema, you must have a project open.</span></span> <span data-ttu-id="eb179-124">如需如何建立專案的資訊，請參閱[如何建立 BizTalk 專案](../core/how-to-create-biztalk-projects.md)。</span><span class="sxs-lookup"><span data-stu-id="eb179-124">For information about how to create a project, see [How to Create BizTalk Projects](../core/how-to-create-biztalk-projects.md).</span></span> <span data-ttu-id="eb179-125">將項目加入至專案的相關資訊，請參閱[如何建立 XML 訊息結構描述](../core/how-to-create-schemas-for-xml-messages.md)。</span><span class="sxs-lookup"><span data-stu-id="eb179-125">For information about adding items to a project, see [How to Create Schemas for XML Messages](../core/how-to-create-schemas-for-xml-messages.md).</span></span> <span data-ttu-id="eb179-126">另請參閱[加入專案項目](../core/adding-project-items.md)。</span><span class="sxs-lookup"><span data-stu-id="eb179-126">Also see [Adding Project Items](../core/adding-project-items.md).</span></span>  
  
### <a name="to-open-biztalk-mapper"></a><span data-ttu-id="eb179-127">開啟 BizTalk 對應工具</span><span class="sxs-lookup"><span data-stu-id="eb179-127">To open BizTalk Mapper</span></span>  
  
1.  <span data-ttu-id="eb179-128">在 [方案總管] 中按一下對應。</span><span class="sxs-lookup"><span data-stu-id="eb179-128">In Solution Explorer, click a map.</span></span>  
  
    > [!NOTE]
    >  <span data-ttu-id="eb179-129">若要開啟 BizTalk 對應工具，您必須先建立對應，或開啟先前建立的對應。</span><span class="sxs-lookup"><span data-stu-id="eb179-129">To open BizTalk Mapper, you must first create a map or open a previously created map.</span></span> <span data-ttu-id="eb179-130">如需建立對應資訊，請參閱[如何建立新的對應](../core/how-to-create-new-maps.md)。</span><span class="sxs-lookup"><span data-stu-id="eb179-130">For information about creating a map, see [How to Create New Maps](../core/how-to-create-new-maps.md).</span></span> <span data-ttu-id="eb179-131">另請參閱[加入專案項目](../core/adding-project-items.md)。</span><span class="sxs-lookup"><span data-stu-id="eb179-131">Also see [Adding Project Items](../core/adding-project-items.md).</span></span>  
  
2.  <span data-ttu-id="eb179-132">在**檢視**功能表上，按一下 **開啟**。</span><span class="sxs-lookup"><span data-stu-id="eb179-132">On the **View** menu, click **Open**.</span></span>  
  
     <span data-ttu-id="eb179-133">-或者-</span><span class="sxs-lookup"><span data-stu-id="eb179-133">—Or—</span></span>  
  
     <span data-ttu-id="eb179-134">以滑鼠右鍵按一下地圖，然後按一下**開啟**。</span><span class="sxs-lookup"><span data-stu-id="eb179-134">Right-click the map, and then click **Open**.</span></span>  
  
     <span data-ttu-id="eb179-135">-或者-</span><span class="sxs-lookup"><span data-stu-id="eb179-135">—Or—</span></span>  
  
     <span data-ttu-id="eb179-136">按兩下對應。</span><span class="sxs-lookup"><span data-stu-id="eb179-136">Double-click a map.</span></span>  
  
     <span data-ttu-id="eb179-137">BizTalk 對應工具中就會開啟選取的對應。</span><span class="sxs-lookup"><span data-stu-id="eb179-137">The selected map opens in BizTalk Mapper.</span></span>  
  
    > [!NOTE]
    >  <span data-ttu-id="eb179-138">若要建立對應，您必須開啟一個專案。</span><span class="sxs-lookup"><span data-stu-id="eb179-138">To create a map, you must have a project open.</span></span> <span data-ttu-id="eb179-139">如需如何建立專案的資訊，請參閱[如何建立 BizTalk 專案](../core/how-to-create-biztalk-projects.md)。</span><span class="sxs-lookup"><span data-stu-id="eb179-139">For information about how to create a project, see [How to Create BizTalk Projects](../core/how-to-create-biztalk-projects.md).</span></span> <span data-ttu-id="eb179-140">將項目加入至專案的相關資訊，請參閱[加入專案項目](../core/adding-project-items.md)。</span><span class="sxs-lookup"><span data-stu-id="eb179-140">For information about adding items to a project, see [Adding Project Items](../core/adding-project-items.md).</span></span> <span data-ttu-id="eb179-141">另請參閱[如何建立新的對應](../core/how-to-create-new-maps.md)。</span><span class="sxs-lookup"><span data-stu-id="eb179-141">Also see [How to Create New Maps](../core/how-to-create-new-maps.md).</span></span>  
  
### <a name="to-open-orchestration-designer"></a><span data-ttu-id="eb179-142">開啟協調流程設計師</span><span class="sxs-lookup"><span data-stu-id="eb179-142">To open Orchestration Designer</span></span>  
  
1.  <span data-ttu-id="eb179-143">在 [方案總管] 中按一下協調流程 (.odx)。</span><span class="sxs-lookup"><span data-stu-id="eb179-143">In Solution Explorer, click an orchestration (.odx).</span></span>  
  
    > [!NOTE]
    >  <span data-ttu-id="eb179-144">若要開啟協調流程設計師 」，您必須先建立協調流程，或開啟先前建立的協調流程。</span><span class="sxs-lookup"><span data-stu-id="eb179-144">To open Orchestration Designer, you must first create an orchestration or open a previously created orchestration.</span></span> <span data-ttu-id="eb179-145">如需如何建立協調流程相關資訊，請參閱[使用協調流程設計師](../core/working-in-orchestration-designer.md)。</span><span class="sxs-lookup"><span data-stu-id="eb179-145">For information about how to create an orchestration, see [Working in Orchestration Designer](../core/working-in-orchestration-designer.md).</span></span>  
  
2.  <span data-ttu-id="eb179-146">在**檢視**功能表上，按一下 **開啟**。</span><span class="sxs-lookup"><span data-stu-id="eb179-146">On the **View** menu, click **Open**.</span></span>  
  
     <span data-ttu-id="eb179-147">-或者-</span><span class="sxs-lookup"><span data-stu-id="eb179-147">—Or—</span></span>  
  
     <span data-ttu-id="eb179-148">協調流程中，以滑鼠右鍵按一下，然後按一下 **開啟**。</span><span class="sxs-lookup"><span data-stu-id="eb179-148">Right-click the orchestration, and then click **Open**.</span></span>  
  
     <span data-ttu-id="eb179-149">-或者-</span><span class="sxs-lookup"><span data-stu-id="eb179-149">—Or—</span></span>  
  
     <span data-ttu-id="eb179-150">按兩下協調流程。</span><span class="sxs-lookup"><span data-stu-id="eb179-150">Double-click the orchestration.</span></span>  
  
     <span data-ttu-id="eb179-151">就會開啟「協調流程設計師」。</span><span class="sxs-lookup"><span data-stu-id="eb179-151">Orchestration Designer opens.</span></span>  
  
    > [!NOTE]
    >  <span data-ttu-id="eb179-152">若要建立協調流程，您必須開啟一個專案。</span><span class="sxs-lookup"><span data-stu-id="eb179-152">To create an orchestration, you must have a project open.</span></span> <span data-ttu-id="eb179-153">如需如何建立專案的資訊，請參閱[如何建立 BizTalk 專案](../core/how-to-create-biztalk-projects.md)。</span><span class="sxs-lookup"><span data-stu-id="eb179-153">For information about how to create a project, see [How to Create BizTalk Projects](../core/how-to-create-biztalk-projects.md).</span></span> <span data-ttu-id="eb179-154">將項目加入至專案的相關資訊，請參閱[加入專案項目](../core/adding-project-items.md)。</span><span class="sxs-lookup"><span data-stu-id="eb179-154">For information about adding items to a project, see [Adding Project Items](../core/adding-project-items.md).</span></span> <span data-ttu-id="eb179-155">另請參閱[使用協調流程設計師](../core/working-in-orchestration-designer.md)。</span><span class="sxs-lookup"><span data-stu-id="eb179-155">Also see [Working in Orchestration Designer](../core/working-in-orchestration-designer.md).</span></span>  
  
### <a name="to-open-pipeline-designer"></a><span data-ttu-id="eb179-156">開啟管線設計師</span><span class="sxs-lookup"><span data-stu-id="eb179-156">To open Pipeline Designer</span></span>  
  
1.  <span data-ttu-id="eb179-157">在 [方案總管] 中按一下管線。</span><span class="sxs-lookup"><span data-stu-id="eb179-157">In Solution Explorer, click a pipeline.</span></span>  
  
    > [!NOTE]
    >  <span data-ttu-id="eb179-158">若要開啟管線設計師，您必須先建立管線，或開啟先前建立的管線。</span><span class="sxs-lookup"><span data-stu-id="eb179-158">To open Pipeline Designer, you must first create a pipeline or open a previously created pipeline.</span></span> <span data-ttu-id="eb179-159">如需如何建立管線資訊，請參閱[如何建立新管線](../core/how-to-create-a-new-pipeline.md)。</span><span class="sxs-lookup"><span data-stu-id="eb179-159">For information about how to create a pipeline, see [How to Create a New Pipeline](../core/how-to-create-a-new-pipeline.md).</span></span>  
  
2.  <span data-ttu-id="eb179-160">在**檢視**功能表上，按一下 **開啟**。</span><span class="sxs-lookup"><span data-stu-id="eb179-160">On the **View** menu, click **Open**.</span></span>  
  
     <span data-ttu-id="eb179-161">-或者-</span><span class="sxs-lookup"><span data-stu-id="eb179-161">—Or—</span></span>  
  
     <span data-ttu-id="eb179-162">以滑鼠右鍵按一下管線，然後按一下**開啟**。</span><span class="sxs-lookup"><span data-stu-id="eb179-162">Right-click the pipeline, and then click **Open**.</span></span>  
  
     <span data-ttu-id="eb179-163">-或者-</span><span class="sxs-lookup"><span data-stu-id="eb179-163">—Or—</span></span>  
  
     <span data-ttu-id="eb179-164">按兩下管線。</span><span class="sxs-lookup"><span data-stu-id="eb179-164">Double-click the pipeline.</span></span>  
  
     <span data-ttu-id="eb179-165">就會開啟「管線設計師」。</span><span class="sxs-lookup"><span data-stu-id="eb179-165">Pipeline Designer opens.</span></span>  
  
    > [!NOTE]
    >  <span data-ttu-id="eb179-166">若要建立管線，您必須開啟一個專案。</span><span class="sxs-lookup"><span data-stu-id="eb179-166">To create a pipeline, you must have a project open.</span></span> <span data-ttu-id="eb179-167">如需如何建立專案的資訊，請參閱[如何建立 BizTalk 專案](../core/how-to-create-biztalk-projects.md)。</span><span class="sxs-lookup"><span data-stu-id="eb179-167">For information about how to create a project, see [How to Create BizTalk Projects](../core/how-to-create-biztalk-projects.md).</span></span> <span data-ttu-id="eb179-168">將項目加入至專案的相關資訊，請參閱[加入專案項目](../core/adding-project-items.md)。</span><span class="sxs-lookup"><span data-stu-id="eb179-168">For information about adding items to a project, see [Adding Project Items](../core/adding-project-items.md).</span></span> <span data-ttu-id="eb179-169">另請參閱[使用協調流程設計師](../core/working-in-orchestration-designer.md)。</span><span class="sxs-lookup"><span data-stu-id="eb179-169">Also see [Working in Orchestration Designer](../core/working-in-orchestration-designer.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="eb179-170">請參閱</span><span class="sxs-lookup"><span data-stu-id="eb179-170">See Also</span></span>  
 <span data-ttu-id="eb179-171">[建立協調流程使用協調流程設計師](../core/creating-orchestrations-using-orchestration-designer.md) </span><span class="sxs-lookup"><span data-stu-id="eb179-171">[Creating Orchestrations Using Orchestration Designer](../core/creating-orchestrations-using-orchestration-designer.md) </span></span>  
 <span data-ttu-id="eb179-172">[使用管線設計師](../core/using-pipeline-designer.md) </span><span class="sxs-lookup"><span data-stu-id="eb179-172">[Using Pipeline Designer](../core/using-pipeline-designer.md) </span></span>  
 <span data-ttu-id="eb179-173">[商務規則編輯器的視窗](../core/windows-of-the-business-rule-composer.md) </span><span class="sxs-lookup"><span data-stu-id="eb179-173">[Windows of the Business Rule Composer](../core/windows-of-the-business-rule-composer.md) </span></span>  
 <span data-ttu-id="eb179-174">[使用 BizTalk 編輯器](../core/using-biztalk-editor.md) </span><span class="sxs-lookup"><span data-stu-id="eb179-174">[Using BizTalk Editor](../core/using-biztalk-editor.md) </span></span>  
 <span data-ttu-id="eb179-175">[使用 BizTalk 對應工具](../core/using-biztalk-mapper.md) </span><span class="sxs-lookup"><span data-stu-id="eb179-175">[Using BizTalk Mapper](../core/using-biztalk-mapper.md) </span></span>  
 [<span data-ttu-id="eb179-176">開發人員工具</span><span class="sxs-lookup"><span data-stu-id="eb179-176">Developer Tools</span></span>](../core/developer-tools.md)