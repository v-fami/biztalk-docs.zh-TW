---
title: 修復訊息 |Microsoft 文件
ms.custom: ''
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- repairing messages
ms.assetid: 3a61b73b-5433-4249-b580-6194ccb4aebc
caps.latest.revision: ''
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 4489e463257f811fe2c71efea49880940751c66a
ms.sourcegitcommit: 8418b1a8f38b7f56979cd6e203f0b591e2f40fe1
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/28/2018
---
# <a name="repairing-a-message"></a><span data-ttu-id="420db-102">修復訊息</span><span class="sxs-lookup"><span data-stu-id="420db-102">Repairing a Message</span></span>
<span data-ttu-id="420db-103">本章節描述如何修復驗證失敗的訊息。</span><span class="sxs-lookup"><span data-stu-id="420db-103">This section describes how to repair a message that has failed validation.</span></span>  
  
### <a name="to-repair-a-message"></a><span data-ttu-id="420db-104">若要修復的訊息</span><span class="sxs-lookup"><span data-stu-id="420db-104">To repair a message</span></span>  
  
1.  <span data-ttu-id="420db-105">在 Internet Explorer 中，開啟 MRSR 網站，網址http://localhost/sites/bassite。</span><span class="sxs-lookup"><span data-stu-id="420db-105">In Internet Explorer, open your MRSR site at http://localhost/sites/bassite.</span></span>  
  
2.  <span data-ttu-id="420db-106">在 [首頁] 視窗中，按一下**文件**。</span><span class="sxs-lookup"><span data-stu-id="420db-106">In the Home window, click **Documents**.</span></span>  
  
3.  <span data-ttu-id="420db-107">在文件視窗中，在**文件庫**，按一下   **\<*部門名稱*\>**_**Repairer**.</span><span class="sxs-lookup"><span data-stu-id="420db-107">In the Documents window, under **Document Libraries**, click **\<*Department name*\>**_**Repairer**.</span></span>  
  
4.  <span data-ttu-id="420db-108">在\<*部門名稱*\>_Repair 視窗中，按一下 **收件匣**。</span><span class="sxs-lookup"><span data-stu-id="420db-108">In the \<*Department name*\>_Repair window, click **Inbox**.</span></span>  
  
5.  <span data-ttu-id="420db-109">在 收件匣 視窗中，指向 訊息的標題、 按一下訊息標題右邊的箭號，然後按一下**編輯在 Microsoft Office InfoPath**。</span><span class="sxs-lookup"><span data-stu-id="420db-109">In the Inbox window, point to the title of the message, click the arrow to the right of the message title, and then click **Edit in Microsoft Office InfoPath**.</span></span>  
  
6.  <span data-ttu-id="420db-110">SWIFT 加速器窗格[!INCLUDE[btsOfficeNoVersion](../../includes/btsofficenoversion-md.md)] [!INCLUDE[btsInpathNoVersion](../../includes/btsinpathnoversion-md.md)] 2007年 視窗中，確定**錯誤**已選取。</span><span class="sxs-lookup"><span data-stu-id="420db-110">In the SWIFT Accelerator pane of the [!INCLUDE[btsOfficeNoVersion](../../includes/btsofficenoversion-md.md)][!INCLUDE[btsInpathNoVersion](../../includes/btsinpathnoversion-md.md)] 2007 window, ensure that **Errors** is selected.</span></span> <span data-ttu-id="420db-111">檢閱中顯示任何錯誤**剖析和 XML 驗證錯誤**， **BRE 驗證錯誤**，和**執行階段錯誤**方塊。</span><span class="sxs-lookup"><span data-stu-id="420db-111">Review any errors shown in the **Parse and XML Validation Errors**, **BRE Validation Errors**, and **Runtime Errors** boxes.</span></span>  
  
7.  <span data-ttu-id="420db-112">在[!INCLUDE[btsInpathNoVersion](../../includes/btsinpathnoversion-md.md)]形成、 捲動至錯誤的位置以及修正錯誤。</span><span class="sxs-lookup"><span data-stu-id="420db-112">In the [!INCLUDE[btsInpathNoVersion](../../includes/btsinpathnoversion-md.md)] form, scroll to the location of the error, and correct the error.</span></span> <span data-ttu-id="420db-113">如果 XML 驗證錯誤，錯誤都將會以紅色反白顯示。</span><span class="sxs-lookup"><span data-stu-id="420db-113">If it is an XML validation error, the error will be highlighted in red.</span></span>  
  
    > [!NOTE]
    >  <span data-ttu-id="420db-114">BRE 驗證錯誤將不會反白顯示中以紅色[!INCLUDE[btsInpathNoVersion](../../includes/btsinpathnoversion-md.md)]表單。</span><span class="sxs-lookup"><span data-stu-id="420db-114">BRE validation errors will not be highlighted in red in the [!INCLUDE[btsInpathNoVersion](../../includes/btsinpathnoversion-md.md)] form.</span></span> <span data-ttu-id="420db-115">如需 BRE 驗證錯誤的詳細資訊，請參閱[SWIFT 錯誤碼](../../adapters-and-accelerators/accelerator-swift/swift-error-codes.md)。</span><span class="sxs-lookup"><span data-stu-id="420db-115">For more information about BRE validation errors, see [SWIFT Error Codes](../../adapters-and-accelerators/accelerator-swift/swift-error-codes.md).</span></span>  
  
    > [!NOTE]
    >  <span data-ttu-id="420db-116">如果錯誤是發生在伴隨著下拉式清單的欄位，您無法查看造成錯誤的原始值。</span><span class="sxs-lookup"><span data-stu-id="420db-116">If the error occurs in a field that is accompanied by a drop-down list, you will not be able to see the original value that caused the error.</span></span> <span data-ttu-id="420db-117">欄位會顯示 「 選取 」 而不是原始值。</span><span class="sxs-lookup"><span data-stu-id="420db-117">The field will display "Select" instead of the original value.</span></span> <span data-ttu-id="420db-118">從下拉式清單中選取適當的值。</span><span class="sxs-lookup"><span data-stu-id="420db-118">Select the appropriate value from the drop-down list.</span></span>  
  
8.  <span data-ttu-id="420db-119">若要確定會驗證訊息，**驗證**目前的角色： 修復] 窗格中，，然後按一下 [**驗證訊息**。</span><span class="sxs-lookup"><span data-stu-id="420db-119">To ensure that the message will validate, click **Validation** in the Current Role: Repair pane, and then click **Validate Message**.</span></span> <span data-ttu-id="420db-120">確認 [結果] 窗格會顯示**訊息無效**。</span><span class="sxs-lookup"><span data-stu-id="420db-120">Verify that the Results pane displays **The message is valid**.</span></span>  
  
9. <span data-ttu-id="420db-121">在[!INCLUDE[btsOfficeNoVersion](../../includes/btsofficenoversion-md.md)] [!INCLUDE[btsInpathNoVersion](../../includes/btsinpathnoversion-md.md)] 2007年] 視窗中，按一下 [**送出**。</span><span class="sxs-lookup"><span data-stu-id="420db-121">In the [!INCLUDE[btsOfficeNoVersion](../../includes/btsofficenoversion-md.md)][!INCLUDE[btsInpathNoVersion](../../includes/btsinpathnoversion-md.md)] 2007 window, click **Submit**.</span></span>  
  
    > [!NOTE]
    >  <span data-ttu-id="420db-122">當您按一下**送出**，[!INCLUDE[btsInpathNoVersion](../../includes/btsinpathnoversion-md.md)]對訊息執行 XML 驗證。</span><span class="sxs-lookup"><span data-stu-id="420db-122">When you click **Submit**, [!INCLUDE[btsInpathNoVersion](../../includes/btsinpathnoversion-md.md)] performs XML validation on the message.</span></span> <span data-ttu-id="420db-123">如果驗證不成功，您必須修正驗證錯誤後再繼續。</span><span class="sxs-lookup"><span data-stu-id="420db-123">If the validation is not successful, you must fix the validation errors before proceeding.</span></span>  
  
10. <span data-ttu-id="420db-124">在提交訊息 對話方塊中，按一下**接受**要提交修復的訊息，以接受變更，請按一下**拒絕**拒絕變更，或按一下**取消**取消送出，並返回表單。</span><span class="sxs-lookup"><span data-stu-id="420db-124">In the Submit Message dialog box, click **Accept** to submit the repaired message with changes accepted, click **Reject** to reject the changes, or click **Cancel** to cancel the submission and return to the form.</span></span>  
  
    > [!NOTE]
    >  <span data-ttu-id="420db-125">如果您接受訊息的變更，[!INCLUDE[btsBizTalkServerNoVersion](../../includes/btsbiztalkservernoversion-md.md)]執行 BRE 驗證訊息。</span><span class="sxs-lookup"><span data-stu-id="420db-125">If you accept the message changes, [!INCLUDE[btsBizTalkServerNoVersion](../../includes/btsbiztalkservernoversion-md.md)] performs BRE validations on the message.</span></span>  
  
    > [!NOTE]
    >  <span data-ttu-id="420db-126">如果您在修復階段中，拒絕的訊息變更[!INCLUDE[btsBizTalkServerNoVersion](../../includes/btsbiztalkservernoversion-md.md)]會將訊息路由至 MessageBox，並張貼至事件檢視器會讀取錯誤 「 無法重設至工作流程中的第一個階段。 」。</span><span class="sxs-lookup"><span data-stu-id="420db-126">If you reject the message changes in the repair stage, [!INCLUDE[btsBizTalkServerNoVersion](../../includes/btsbiztalkservernoversion-md.md)] routes the message to the MessageBox, and posts to the Event Viewer an error that reads "Could not reset to the first stage in the workflow.".</span></span>  
  
11. <span data-ttu-id="420db-127">如果您按下**接受**或**拒絕**在步驟 10 中，在**數位簽章精靈**頁面上，選取您想要用來簽署格式的憑證 (憑證，您建立 repairer），然後按一下 **下一步**。</span><span class="sxs-lookup"><span data-stu-id="420db-127">If you clicked **Accept** or **Reject** in step 10, on the **Digital Signature Wizard** page, select the certificate that you want to use to sign the form (the certificate that you created for the repairer), and then click **Next**.</span></span>  
  
    > [!NOTE]
    >  <span data-ttu-id="420db-128">若要驗證數位簽章的有效性，請按一下**數位簽章**上**工具**功能表上，按一下您想要確認，然後再按一下數位簽章**檢視簽署表單**.</span><span class="sxs-lookup"><span data-stu-id="420db-128">To verify the validity of a digital signature, click **Digital Signatures** on the **Tools** menu, click the digital signature that you want to verify, and then click **View Signed Form**.</span></span>  
  
12. <span data-ttu-id="420db-129">在輸入註解的數位簽章精靈頁面上，按一下 **完成**。</span><span class="sxs-lookup"><span data-stu-id="420db-129">On the Digital Signature Wizard page for entering a comment, click **Finish**.</span></span>  
  
13. <span data-ttu-id="420db-130">在驗證表單的 數位簽章精靈頁面上，確認您所簽署的訊息和簽章正確。</span><span class="sxs-lookup"><span data-stu-id="420db-130">On the Digital Signature Wizard page for verifying the form, verify that the message that you are signing and your signature are correct.</span></span> <span data-ttu-id="420db-131">按一下**我已簽署前確認此內容**，然後按一下 **登**。</span><span class="sxs-lookup"><span data-stu-id="420db-131">Click **I have verified this content before signing**, and then click **Sign**.</span></span>  
  
14. <span data-ttu-id="420db-132">在 [確認數位簽章] 視窗中，按一下**關閉**。</span><span class="sxs-lookup"><span data-stu-id="420db-132">In the Verify Digital Signature window, click **Close**.</span></span>  
  
15. <span data-ttu-id="420db-133">在 [提交成功] 對話方塊中，按一下**確定**。</span><span class="sxs-lookup"><span data-stu-id="420db-133">In the Submission Success dialog box, click **OK**.</span></span>  
  
16. <span data-ttu-id="420db-134">關閉[!INCLUDE[btsInpathNoVersion](../../includes/btsinpathnoversion-md.md)]視窗。</span><span class="sxs-lookup"><span data-stu-id="420db-134">Close the [!INCLUDE[btsInpathNoVersion](../../includes/btsinpathnoversion-md.md)] window.</span></span>  
  
17. <span data-ttu-id="420db-135">在 MRSR 網站中，按一下 **文件**。</span><span class="sxs-lookup"><span data-stu-id="420db-135">In MRSR site, click **Documents**.</span></span> <span data-ttu-id="420db-136">如果您按下**接受**接受步驟 11 中的變更，請確認*\<部門名稱\>*_ReKeyVerify 文件庫包含您修復的訊息。</span><span class="sxs-lookup"><span data-stu-id="420db-136">If you clicked **Accept** to accept the changes in step 11, verify that the *\<Department name\>*_ReKeyVerify document library contains the message that you just repaired.</span></span> <span data-ttu-id="420db-137">如果您按下**拒絕**拒絕步驟 11 中的變更，請確認 A4SWIFT_Outbox 文件庫包含未修改過的訊息。</span><span class="sxs-lookup"><span data-stu-id="420db-137">If you clicked **Reject** to reject the changes in step 11, verify that the A4SWIFT_Outbox document library contains the message that was just modified.</span></span>