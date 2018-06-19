---
title: 匯入 Bindings2 |Microsoft 文件
ms.custom: ''
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- bindings, requirements
- importing, bindings
- bindings, importing
ms.assetid: 9e10bc04-aba8-430a-b8fd-de9399d54f88
caps.latest.revision: 13
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 2f2c92d5469f88494c77ad062d97c53768572a5b
ms.sourcegitcommit: 3fc338e52d5dbca2c3ea1685a2faafc7582fe23a
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/01/2017
ms.locfileid: "26006127"
---
# <a name="importing-bindings"></a><span data-ttu-id="f6737-102">匯入繫結</span><span class="sxs-lookup"><span data-stu-id="f6737-102">Importing Bindings</span></span>
<span data-ttu-id="f6737-103">本節中的主題描述如何將繫結匯入到 BizTalk 群組或應用程式中。</span><span class="sxs-lookup"><span data-stu-id="f6737-103">The topics in this section describe how to import bindings into a BizTalk group or application.</span></span>  
  
 <span data-ttu-id="f6737-104">當您匯入繫結時，請牢記下列要點：</span><span class="sxs-lookup"><span data-stu-id="f6737-104">When importing bindings, bear in mind the following important points:</span></span>  
  
-   <span data-ttu-id="f6737-105">**將覆寫現有的繫結。**</span><span class="sxs-lookup"><span data-stu-id="f6737-105">**Existing bindings will be overwritten.**</span></span> <span data-ttu-id="f6737-106">如果您要匯入的繫結與現有的繫結同名，將會覆寫現有的繫結。</span><span class="sxs-lookup"><span data-stu-id="f6737-106">If the bindings that you import have the same name as existing bindings, the existing bindings are overwritten.</span></span> <span data-ttu-id="f6737-107">此外，如果繫結檔案包含合作對象和別名，則已經存在於應用程式之同名的合作對象和別名的任何繫結也會被覆寫。</span><span class="sxs-lookup"><span data-stu-id="f6737-107">In addition, if the binding file contains parties and aliases, any bindings for parties and aliases of the same name that already exist in the application are overwritten.</span></span>  
  
-   <span data-ttu-id="f6737-108">**在群組中的所有繫結必須是唯一的。**</span><span class="sxs-lookup"><span data-stu-id="f6737-108">**All bindings in a group must be unique.**</span></span> <span data-ttu-id="f6737-109">如果已經存在於群組中的繫結與您要匯入的繫結同名，匯入作業將會失敗。</span><span class="sxs-lookup"><span data-stu-id="f6737-109">If a binding having the same name as one you are importing already exists in the group, the import operation will fail.</span></span>  
  
-   <span data-ttu-id="f6737-110">**您必須重新設定密碼。**</span><span class="sxs-lookup"><span data-stu-id="f6737-110">**You must reconfigure passwords.**</span></span> <span data-ttu-id="f6737-111">基於安全性理由，當您匯出繫結檔案時，BizTalk Server 會從該檔案移除繫結的密碼。</span><span class="sxs-lookup"><span data-stu-id="f6737-111">For security reasons, when you export a binding file, BizTalk Server removes the passwords for the bindings from the file.</span></span> <span data-ttu-id="f6737-112">匯入繫結後，您必須重新設定密碼，傳送埠和接受位置才能正常運作。</span><span class="sxs-lookup"><span data-stu-id="f6737-112">After importing the bindings, you must reconfigure passwords for send ports and receive locations before they will function.</span></span> <span data-ttu-id="f6737-113">您可以在 BizTalk Server 管理主控台的 [傳輸屬性] 對話方塊中，為傳送埠或接收位置設定密碼。</span><span class="sxs-lookup"><span data-stu-id="f6737-113">You configure passwords in the Transport Properties dialog box of the BizTalk Server Administration console for the send port or receive location.</span></span> <span data-ttu-id="f6737-114">如需指示，請參閱[如何建立傳送埠](../core/how-to-create-a-send-port2.md)。</span><span class="sxs-lookup"><span data-stu-id="f6737-114">For instructions, see [How to Create a Send Port](../core/how-to-create-a-send-port2.md).</span></span> <span data-ttu-id="f6737-115">另請參閱[如何建立接收位置](../core/how-to-create-a-receive-location.md)。</span><span class="sxs-lookup"><span data-stu-id="f6737-115">See also [How to Create a Receive Location](../core/how-to-create-a-receive-location.md).</span></span>  
  
-   <span data-ttu-id="f6737-116">**群組中必須存在該主機。**</span><span class="sxs-lookup"><span data-stu-id="f6737-116">**The host must exist in the group.**</span></span> <span data-ttu-id="f6737-117">對應到繫結中指定之主控件的主控件必須已經存在於要匯入繫結到其中的 BizTalk 群組內，而且主控件信任層級必須相符。</span><span class="sxs-lookup"><span data-stu-id="f6737-117">A host corresponding to the host specified in the bindings must already exist in the BizTalk group into which the bindings are imported and the host trust level must match.</span></span> <span data-ttu-id="f6737-118">否則，匯入作業將會失敗。</span><span class="sxs-lookup"><span data-stu-id="f6737-118">Otherwise, the import operation will fail.</span></span>  
  
-   <span data-ttu-id="f6737-119">**繫結匯入行為取決於繫結來源。**</span><span class="sxs-lookup"><span data-stu-id="f6737-119">**Binding import behavior depends on the source of the bindings.**</span></span> <span data-ttu-id="f6737-120">繫結原先可能是從組件、應用程式或群組匯出的。</span><span class="sxs-lookup"><span data-stu-id="f6737-120">The bindings may have been exported from an assembly, application, or group.</span></span> <span data-ttu-id="f6737-121">根據繫結是從何處匯出而定，匯入作業可能會有不同的效果，如下表所示。</span><span class="sxs-lookup"><span data-stu-id="f6737-121">Depending on from where the bindings were exported, the import operation may have different effects, as shown in the following table.</span></span>  
  
    |<span data-ttu-id="f6737-122">繫結的來源</span><span class="sxs-lookup"><span data-stu-id="f6737-122">Origin of the bindings</span></span>|<span data-ttu-id="f6737-123">匯入至應用程式</span><span class="sxs-lookup"><span data-stu-id="f6737-123">Importing into an application</span></span>|<span data-ttu-id="f6737-124">匯入至群組</span><span class="sxs-lookup"><span data-stu-id="f6737-124">Importing into a group</span></span>|  
    |----------------------------|-----------------------------------|----------------------------|  
    |<span data-ttu-id="f6737-125">從組件匯出繫結</span><span class="sxs-lookup"><span data-stu-id="f6737-125">Bindings exported from an assembly</span></span>|<span data-ttu-id="f6737-126">指定的應用程式中必須有包含組件，其名稱與匯出繫結檔案的來源組件相同。</span><span class="sxs-lookup"><span data-stu-id="f6737-126">The specified application in must contain an assembly having the same name as the assembly from which the binding file was exported.</span></span> <span data-ttu-id="f6737-127">否則，匯入作業會失敗。</span><span class="sxs-lookup"><span data-stu-id="f6737-127">Otherwise, the import operation fails.</span></span>|<span data-ttu-id="f6737-128">此群組必須包含一個組件和應用程式，其名稱與匯出繫結檔案的來源組件和應用程式相同。</span><span class="sxs-lookup"><span data-stu-id="f6737-128">The group must contain an assembly and an application having the same name as the assembly and application from which the binding file was exported.</span></span> <span data-ttu-id="f6737-129">否則，匯入作業會失敗。</span><span class="sxs-lookup"><span data-stu-id="f6737-129">Otherwise, the import fails.</span></span>|  
    |<span data-ttu-id="f6737-130">從應用程式匯出繫結</span><span class="sxs-lookup"><span data-stu-id="f6737-130">Bindings exported from an application</span></span>|<span data-ttu-id="f6737-131">匯出繫結檔案的來源應用程式必須與指定的應用程式同名。</span><span class="sxs-lookup"><span data-stu-id="f6737-131">The application from which the binding file was exported must have the same name as the specified application.</span></span> <span data-ttu-id="f6737-132">否則，匯入作業會失敗。</span><span class="sxs-lookup"><span data-stu-id="f6737-132">Otherwise, the import operation fails.</span></span>|<span data-ttu-id="f6737-133">匯出繫結檔案的來源應用程式，其名稱必須與即將匯入繫結的群組中的某個應用程式相同。</span><span class="sxs-lookup"><span data-stu-id="f6737-133">The application from which the binding file was exported must have the same name as an application in the group into which you are importing the bindings.</span></span> <span data-ttu-id="f6737-134">否則，匯入作業會失敗。</span><span class="sxs-lookup"><span data-stu-id="f6737-134">Otherwise, the import operation fails.</span></span>|  
    |<span data-ttu-id="f6737-135">從群組匯出繫結</span><span class="sxs-lookup"><span data-stu-id="f6737-135">Bindings exported from a group</span></span>|<span data-ttu-id="f6737-136">匯出繫結檔案的來源群組中必須有個應用程式，其名稱與指定的應用程式相同。</span><span class="sxs-lookup"><span data-stu-id="f6737-136">The group from which the binding file was exported must include an application that has the same name as the specified application.</span></span> <span data-ttu-id="f6737-137">否則，匯入作業會失敗。</span><span class="sxs-lookup"><span data-stu-id="f6737-137">Otherwise, the import operation fails.</span></span>|<span data-ttu-id="f6737-138">會針對對應的應用程式來匯入繫結。</span><span class="sxs-lookup"><span data-stu-id="f6737-138">Bindings are imported for corresponding applications.</span></span> <span data-ttu-id="f6737-139">也就是說，匯出繫結的來源群組中，特定應用程式的繫結將會匯入到目前群組中同名的應用程式內。</span><span class="sxs-lookup"><span data-stu-id="f6737-139">In other words, the bindings of an application in the group from which bindings were exported are imported into an application having the same name in the current group.</span></span>|  
  
-   <span data-ttu-id="f6737-140">**配接器的 Name 屬性可能不正確。**</span><span class="sxs-lookup"><span data-stu-id="f6737-140">**The Name attribute for an adapter may be incorrect.**</span></span> <span data-ttu-id="f6737-141">若此繫結檔案包含某配接器的設定，請確認繫結檔案中 TransportType 項目的 Name 屬性，與 BizTalk Server 管理主控台中配接器的設定相同 (在 [平台設定] > [配接器] 之下)。</span><span class="sxs-lookup"><span data-stu-id="f6737-141">If the binding file includes settings for an adapter, verify that the Name attribute of the TransportType element in the binding file is the same as that configured for the adapter in the BizTalk Server Administration console (under Platform Settings > Adapters).</span></span>  
  
     <span data-ttu-id="f6737-142">特別是，您應該確認這是大小寫，匯入來自繫結時[!INCLUDE[btsBizTalkServer2006](../includes/btsbiztalkserver2006-md.md)]至 BizTalk Server。</span><span class="sxs-lookup"><span data-stu-id="f6737-142">In particular, you should verify that this is the case when importing bindings from [!INCLUDE[btsBizTalkServer2006](../includes/btsbiztalkserver2006-md.md)] to BizTalk Server.</span></span> <span data-ttu-id="f6737-143">下面是這種狀況會造成問題的一些傳輸：</span><span class="sxs-lookup"><span data-stu-id="f6737-143">Some transports for which this may be an issue are as follows:</span></span>  
  
    -   <span data-ttu-id="f6737-144">MQS</span><span class="sxs-lookup"><span data-stu-id="f6737-144">MQS</span></span>  
  
    -   <span data-ttu-id="f6737-145">MSMQ</span><span class="sxs-lookup"><span data-stu-id="f6737-145">MSMQ</span></span>  
  
    -   <span data-ttu-id="f6737-146">POP3</span><span class="sxs-lookup"><span data-stu-id="f6737-146">POP3</span></span>  
  
    -   <span data-ttu-id="f6737-147">Windows SharePoint Services</span><span class="sxs-lookup"><span data-stu-id="f6737-147">Windows SharePoint Services</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="f6737-148">本節內容</span><span class="sxs-lookup"><span data-stu-id="f6737-148">In This Section</span></span>  
  
-   [<span data-ttu-id="f6737-149">如何將繫結匯入到 BizTalk 群組</span><span class="sxs-lookup"><span data-stu-id="f6737-149">How to Import Bindings into a BizTalk Group</span></span>](../core/how-to-import-bindings-into-a-biztalk-group.md)  
  
-   [<span data-ttu-id="f6737-150">如何將繫結匯入到 BizTalk 應用程式</span><span class="sxs-lookup"><span data-stu-id="f6737-150">How to Import Bindings into a BizTalk Application</span></span>](../core/how-to-import-bindings-into-a-biztalk-application.md)  
  
-   [<span data-ttu-id="f6737-151">如何匯入 EDI AS2 方案的繫結</span><span class="sxs-lookup"><span data-stu-id="f6737-151">How to Import Bindings for an EDI-AS2 Solution</span></span>](../core/how-to-import-bindings-for-an-edi-as2-solution.md)