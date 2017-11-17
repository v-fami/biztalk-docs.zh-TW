---
title: "修復和重新提交訊息 |Microsoft 文件"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: ccd720b4-44a2-4c44-bf6e-8cf5e9ded1aa
caps.latest.revision: "3"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: e524ffca1b79032dce55f74e195032d14ec1bf9e
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/20/2017
---
# <a name="repairing-and-resubmitting-a-message"></a><span data-ttu-id="65d66-102">修復和重新提交訊息</span><span class="sxs-lookup"><span data-stu-id="65d66-102">Repairing and Resubmitting a Message</span></span>
<span data-ttu-id="65d66-103">若要修復並重新提交失敗的訊息，使用 ESB 管理入口網站的 [錯誤] 頁面。</span><span class="sxs-lookup"><span data-stu-id="65d66-103">To repair and resubmit a failed message, use the Faults page of the ESB Management Portal.</span></span>  
  
### <a name="to-repair-and-resubmit-a-message-for-processing"></a><span data-ttu-id="65d66-104">修復並重新提交訊息，以進行處理</span><span class="sxs-lookup"><span data-stu-id="65d66-104">To repair and resubmit a message for processing</span></span>  
  
1.  <span data-ttu-id="65d66-105">找出所需的錯誤訊息上[入口網站錯誤網頁](../esb-toolkit/portal-faults-page.md)ESB 管理入口網站頁面。</span><span class="sxs-lookup"><span data-stu-id="65d66-105">Locate the desired fault message on the [Portal Faults Page](../esb-toolkit/portal-faults-page.md) page of the ESB Management Portal.</span></span> <span data-ttu-id="65d66-106">使用 [錯誤] 頁面上的篩選功能來搜尋特定訊息。</span><span class="sxs-lookup"><span data-stu-id="65d66-106">Use the filtering capabilities on the Faults page to search for a specific message.</span></span> <span data-ttu-id="65d66-107">空白的任何控制項來擷取所有的訊息。</span><span class="sxs-lookup"><span data-stu-id="65d66-107">Leave any of the controls empty to retrieve all messages.</span></span> <span data-ttu-id="65d66-108">請注意，篩選非常大的錯誤資料庫上可能需要花費幾秒鐘的時間才會顯示適當的結果。</span><span class="sxs-lookup"><span data-stu-id="65d66-108">Note that filtering on a very large fault database may take several seconds to display the appropriate results.</span></span> <span data-ttu-id="65d66-109">圖 1 所示的錯誤頁面。</span><span class="sxs-lookup"><span data-stu-id="65d66-109">Figure 1 illustrates the Faults page.</span></span>  
  
     <span data-ttu-id="65d66-110">![FaultsPage](../esb-toolkit/media/faultspage.gif "FaultsPage")</span><span class="sxs-lookup"><span data-stu-id="65d66-110">![FaultsPage](../esb-toolkit/media/faultspage.gif "FaultsPage")</span></span>  
  
     <span data-ttu-id="65d66-111">**圖 1**</span><span class="sxs-lookup"><span data-stu-id="65d66-111">**Figure 1**</span></span>  
  
     <span data-ttu-id="65d66-112">**ESB 管理入口網站的 [錯誤] 頁面**</span><span class="sxs-lookup"><span data-stu-id="65d66-112">**The Faults page of the ESB Management Portal**</span></span>  
  
2.  <span data-ttu-id="65d66-113">按一下以開啟所需的錯誤訊息的資料列中的任何位置[入口網站錯誤訊息檢視器](../esb-toolkit/portal-fault-message-viewer.md)頁面[錯誤詳細資料檢視](../esb-toolkit/fault-details-view.md)。</span><span class="sxs-lookup"><span data-stu-id="65d66-113">Click anywhere in the row of the desired fault message to open the [Portal Fault Message Viewer](../esb-toolkit/portal-fault-message-viewer.md) page in [Fault Details View](../esb-toolkit/fault-details-view.md).</span></span>  
  
3.  <span data-ttu-id="65d66-114">捲動到 錯誤詳細資料檢視的錯誤訊息中包含的訊息清單的底部。</span><span class="sxs-lookup"><span data-stu-id="65d66-114">Scroll to the bottom of the Fault Details view to the list of messages contained within the fault message.</span></span> <span data-ttu-id="65d66-115">圖 2 說明**訊息**錯誤檢視器 頁面的區段。</span><span class="sxs-lookup"><span data-stu-id="65d66-115">Figure 2 illustrates the **Messages** section of the Fault Viewer page.</span></span>  
  
     <span data-ttu-id="65d66-116">![訊息區段](../esb-toolkit/media/ch8-messagessection.gif "Ch8 MessagesSection")</span><span class="sxs-lookup"><span data-stu-id="65d66-116">![Messages Section](../esb-toolkit/media/ch8-messagessection.gif "Ch8-MessagesSection")</span></span>  
  
     <span data-ttu-id="65d66-117">**圖 2**</span><span class="sxs-lookup"><span data-stu-id="65d66-117">**Figure 2**</span></span>  
  
     <span data-ttu-id="65d66-118">**ESB 管理入口網站的 [錯誤檢視器] 頁面的 [訊息] 區段**</span><span class="sxs-lookup"><span data-stu-id="65d66-118">**The Messages section of the Fault Viewer page of the ESB Management Portal**</span></span>  
  
4.  <span data-ttu-id="65d66-119">按一下您想要重新提交訊息的訊息識別項。</span><span class="sxs-lookup"><span data-stu-id="65d66-119">Click the message identifier of the message you want to resubmit.</span></span> <span data-ttu-id="65d66-120">這會開啟中的訊息[訊息詳細資料檢視](../esb-toolkit/message-details-view.md)，其中顯示個別的訊息和訊息內容的詳細資料，如圖 3 所示。</span><span class="sxs-lookup"><span data-stu-id="65d66-120">This opens the message in [Message Details View](../esb-toolkit/message-details-view.md), which shows details of the individual message and the message content, as illustrated in Figure 3.</span></span>  
  
     <span data-ttu-id="65d66-121">![訊息檢視器](../esb-toolkit/media/ch8-messageviewer.gif "Ch8 MessageViewer")</span><span class="sxs-lookup"><span data-stu-id="65d66-121">![Message Viewer](../esb-toolkit/media/ch8-messageviewer.gif "Ch8-MessageViewer")</span></span>  
  
     <span data-ttu-id="65d66-122">**圖 3**</span><span class="sxs-lookup"><span data-stu-id="65d66-122">**Figure 3**</span></span>  
  
     <span data-ttu-id="65d66-123">**ESB 管理入口網站的 [訊息檢視器] 頁面**</span><span class="sxs-lookup"><span data-stu-id="65d66-123">**The Message Viewer page of the ESB Management Portal**</span></span>  
  
5.  <span data-ttu-id="65d66-124">按一下**編輯**包含訊息內容切換至編輯模式，，然後編輯 訊息內容所需的文字方塊底下的連結。</span><span class="sxs-lookup"><span data-stu-id="65d66-124">Click the **Edit** link under the text box that contains the message content to switch to edit mode, and then edit the message contents as required.</span></span> <span data-ttu-id="65d66-125">例如，您可能需要變更服務方法引動過程訊息中所包含的參數。</span><span class="sxs-lookup"><span data-stu-id="65d66-125">For example, you may need to change the parameters for service method invocations contained within the message.</span></span> <span data-ttu-id="65d66-126">請注意，您必須遵循 （例如 XML 或一般檔案格式） 的原生文件樣式以防止拒絕重新提交的訊息。</span><span class="sxs-lookup"><span data-stu-id="65d66-126">Note that you must adhere to the native document style (such as XML or flat file format) to prevent rejection of the message when resubmitted.</span></span> <span data-ttu-id="65d66-127">圖 4 說明**訊息詳細資料**訊息編輯器頁面區段。</span><span class="sxs-lookup"><span data-stu-id="65d66-127">Figure 4 illustrates the **Message Details** section of the Message Editor page.</span></span>  
  
     <span data-ttu-id="65d66-128">![訊息詳細資料](../esb-toolkit/media/ch8-messagedetails.gif "Ch8 MessageDetails")</span><span class="sxs-lookup"><span data-stu-id="65d66-128">![Message Details](../esb-toolkit/media/ch8-messagedetails.gif "Ch8-MessageDetails")</span></span>  
  
     <span data-ttu-id="65d66-129">**圖 4**</span><span class="sxs-lookup"><span data-stu-id="65d66-129">**Figure 4**</span></span>  
  
     <span data-ttu-id="65d66-130">**ESB 管理入口網站的 訊息檢視器 頁面的 訊息詳細資料區段**</span><span class="sxs-lookup"><span data-stu-id="65d66-130">**The Message Details section of the Message Viewer page of the ESB Management Portal**</span></span>  
  
6.  <span data-ttu-id="65d66-131">編輯之後的訊息，請選取 [重新送出的位置之下訊息文字] 方塊的下拉式清單中。</span><span class="sxs-lookup"><span data-stu-id="65d66-131">After editing the message, select a resubmission location in the drop-down list under the message text box.</span></span> <span data-ttu-id="65d66-132">此清單會顯示動態擷取可用的端點的清單。</span><span class="sxs-lookup"><span data-stu-id="65d66-132">This list shows the dynamically retrieved list of available endpoints.</span></span> <span data-ttu-id="65d66-133">您必須選取設定為重新送出端點的端點。</span><span class="sxs-lookup"><span data-stu-id="65d66-133">You must select an endpoint configured as a resubmission endpoint.</span></span> <span data-ttu-id="65d66-134">重新提交適用的下列端點：</span><span class="sxs-lookup"><span data-stu-id="65d66-134">The following endpoints are suitable for resubmission:</span></span>  
  
    -   <span data-ttu-id="65d66-135">**WCF 上手**。</span><span class="sxs-lookup"><span data-stu-id="65d66-135">**WCF On-Ramp**.</span></span> <span data-ttu-id="65d66-136">此端點是 ESB 行程服務 WCF 上手，僅適用於 XML 檔案。</span><span class="sxs-lookup"><span data-stu-id="65d66-136">This endpoint is the ESB Itinerary Services WCF on-ramp and is available only for XML files.</span></span> <span data-ttu-id="65d66-137">入口網站的 Web.config 檔案中定義此上手的 URL。</span><span class="sxs-lookup"><span data-stu-id="65d66-137">The portal Web.config file defines the URL for this on-ramp.</span></span>  
  
    -   <span data-ttu-id="65d66-138">**SOAP 上手**。</span><span class="sxs-lookup"><span data-stu-id="65d66-138">**SOAP On-Ramp**.</span></span> <span data-ttu-id="65d66-139">此端點是 ESB 行程服務 ASMX 上手，僅適用於 XML 檔案。</span><span class="sxs-lookup"><span data-stu-id="65d66-139">This endpoint is the ESB Itinerary Services ASMX on-ramp and is available only for XML files.</span></span> <span data-ttu-id="65d66-140">入口網站的 Web.config 檔案中定義此上手的 URL。</span><span class="sxs-lookup"><span data-stu-id="65d66-140">The portal Web.config file defines the URL for this on-ramp.</span></span>  
  
    -   <span data-ttu-id="65d66-141">**任何接收位置使用 BizTalk HTTP 配接器**。</span><span class="sxs-lookup"><span data-stu-id="65d66-141">**Any receive location using the BizTalk HTTP adapter**.</span></span> <span data-ttu-id="65d66-142">此選項適用於 XML 檔案和一般檔案。</span><span class="sxs-lookup"><span data-stu-id="65d66-142">This option is available for XML files and flat files.</span></span>  
  
7.  <span data-ttu-id="65d66-143">按一下**重新提交**送出郵件的連結。</span><span class="sxs-lookup"><span data-stu-id="65d66-143">Click the **Resubmit** link to resubmit the message.</span></span> <span data-ttu-id="65d66-144">訊息，指出**重新送出狀態**在訊息內容文字方塊下方會出現。</span><span class="sxs-lookup"><span data-stu-id="65d66-144">A message indicating the **Resubmission Status** appears under the message content text box.</span></span>  
  
8.  <span data-ttu-id="65d66-145">如有需要，開啟[稽核記錄檔 頁面](../esb-toolkit/audit-log-page.md)從**Admin**索引標籤，確認訊息重新提交，如圖 5 所示。</span><span class="sxs-lookup"><span data-stu-id="65d66-145">If required, open the [Audit Log Page](../esb-toolkit/audit-log-page.md) from the **Admin** tab to confirm message resubmission, as illustrated in Figure 5.</span></span>  
  
     <span data-ttu-id="65d66-146">![AuditLog 頁面小型檢視](../esb-toolkit/media/ch8-auditlogpagesmallview.gif "Ch8 AuditLogPageSmallView")</span><span class="sxs-lookup"><span data-stu-id="65d66-146">![AuditLog Page Small View](../esb-toolkit/media/ch8-auditlogpagesmallview.gif "Ch8-AuditLogPageSmallView")</span></span>  
  
     <span data-ttu-id="65d66-147">**圖 5**</span><span class="sxs-lookup"><span data-stu-id="65d66-147">**Figure 5**</span></span>  
  
     <span data-ttu-id="65d66-148">**ESB 管理入口網站的 [稽核記錄] 頁面**</span><span class="sxs-lookup"><span data-stu-id="65d66-148">**The Audit Log page of the ESB Management Portal**</span></span>