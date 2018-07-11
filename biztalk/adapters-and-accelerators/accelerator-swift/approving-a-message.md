---
title: 核准訊息 |Microsoft Docs
ms.custom: ''
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- messages, approving
- approving messages
ms.assetid: e6abfef3-aab2-470e-a7a7-a6d091ffba53
caps.latest.revision: 5
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 0c565f40c6c455456101521414edf0c377411014
ms.sourcegitcommit: 266308ec5c6a9d8d80ff298ee6051b4843c5d626
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/27/2018
ms.locfileid: "36967103"
---
# <a name="approving-a-message"></a><span data-ttu-id="23d53-102">核准訊息</span><span class="sxs-lookup"><span data-stu-id="23d53-102">Approving a Message</span></span>
<span data-ttu-id="23d53-103">本章節描述如何核准訊息修復和驗證。</span><span class="sxs-lookup"><span data-stu-id="23d53-103">This section describes how to approve a message that has been repaired and verified.</span></span>  

### <a name="to-approve-a-message"></a><span data-ttu-id="23d53-104">核准訊息</span><span class="sxs-lookup"><span data-stu-id="23d53-104">To approve a message</span></span>  

1. <span data-ttu-id="23d53-105">在 Internet Explorer 中，開啟 MRSR 網站http://localhost/sites/bassite。</span><span class="sxs-lookup"><span data-stu-id="23d53-105">In Internet Explorer, open your MRSR site at http://localhost/sites/bassite.</span></span>  

2. <span data-ttu-id="23d53-106">在 [首頁] 視窗中，按一下**文件**。</span><span class="sxs-lookup"><span data-stu-id="23d53-106">In the Home window, click **Documents**.</span></span>  

3. <span data-ttu-id="23d53-107">在文件視窗中，在**文件庫**，按一下 **\<*部門名稱*\>_Approver**。</span><span class="sxs-lookup"><span data-stu-id="23d53-107">In the Documents window, under **Document Libraries**, click **\<*Department name*\>_Approver**.</span></span>  

4. <span data-ttu-id="23d53-108">在 [\<部門名稱\>_Approver] 視窗中，按一下**收件匣**。</span><span class="sxs-lookup"><span data-stu-id="23d53-108">In the \<Department name\>_Approver window, click **Inbox**.</span></span>  

5. <span data-ttu-id="23d53-109">在 收件匣 視窗中，指向 訊息的標題、 按一下訊息標題右邊的箭號，然後按一下**在 Microsoft Office InfoPath 中編輯**。</span><span class="sxs-lookup"><span data-stu-id="23d53-109">In the Inbox window, point to the title of the message, click the arrow to the right of the message title, and then click **Edit in Microsoft Office InfoPath**.</span></span>  

6. <span data-ttu-id="23d53-110">SWIFT 加速器窗格中的[!INCLUDE[btsOfficeNoVersion](../../includes/btsofficenoversion-md.md)] [!INCLUDE[btsInpathNoVersion](../../includes/btsinpathnoversion-md.md)] 2007年 視窗中，按一下**錯誤**。</span><span class="sxs-lookup"><span data-stu-id="23d53-110">In the SWIFT Accelerator pane of the [!INCLUDE[btsOfficeNoVersion](../../includes/btsofficenoversion-md.md)][!INCLUDE[btsInpathNoVersion](../../includes/btsinpathnoversion-md.md)] 2007 window, click **Errors**.</span></span> <span data-ttu-id="23d53-111">檢閱中顯示任何錯誤**剖析和 XML 驗證錯誤** 方塊中， **BRE 驗證錯誤** 方塊中，而**執行階段錯誤** 方塊中。</span><span class="sxs-lookup"><span data-stu-id="23d53-111">Review any errors shown in the **Parse and XML Validation Errors** box, the **BRE Validation Errors** box, and the **Runtime Errors** box.</span></span>  

7. <span data-ttu-id="23d53-112">在 [!INCLUDE[btsInpathNoVersion](../../includes/btsinpathnoversion-md.md)]形成、 捲動到錯誤的位置，然後確認 已更正錯誤。</span><span class="sxs-lookup"><span data-stu-id="23d53-112">In the [!INCLUDE[btsInpathNoVersion](../../includes/btsinpathnoversion-md.md)] form, scroll to the location of the error and verify that the error has been corrected.</span></span> <span data-ttu-id="23d53-113">您可以看到原始錯誤是依序按一下**錯誤**中目前的角色： 核准窗格中，並在其中一個 [錯誤] 窗格中檢視錯誤。</span><span class="sxs-lookup"><span data-stu-id="23d53-113">You can see what the original error was by clicking **Errors** in the Current Role: Approve pane, and viewing the error in one of the error panes.</span></span> <span data-ttu-id="23d53-114">您也可以比較出來並修復版本的訊息，依序按一下**訊息的詳細資料**中目前的角色： 核准窗格。</span><span class="sxs-lookup"><span data-stu-id="23d53-114">You can also compare the unrepaired and repaired versions of the message by clicking **Message Details** in the Current Role: Approve pane.</span></span>  

8. <span data-ttu-id="23d53-115">若要確保會驗證訊息，請按一下**驗證**目前的角色： 核准 窗格中，然後按一下**驗證訊息**。</span><span class="sxs-lookup"><span data-stu-id="23d53-115">To ensure that the message will validate, click **Validation** in the Current Role: Approve pane, and then click **Validate Message**.</span></span> <span data-ttu-id="23d53-116">確認 [結果] 窗格會顯示訊息**訊息是有效**。</span><span class="sxs-lookup"><span data-stu-id="23d53-116">Verify that the Results pane displays the message **The message is valid**.</span></span>  

9. <span data-ttu-id="23d53-117">如果您已對文件中的變更核准[!INCLUDE[btsOfficeNoVersion](../../includes/btsofficenoversion-md.md)] [!INCLUDE[btsInpathNoVersion](../../includes/btsinpathnoversion-md.md)] 2007年 視窗中，按一下**送出**。</span><span class="sxs-lookup"><span data-stu-id="23d53-117">If you approve of the changes that have been made to the document, in the [!INCLUDE[btsOfficeNoVersion](../../includes/btsofficenoversion-md.md)][!INCLUDE[btsInpathNoVersion](../../includes/btsinpathnoversion-md.md)] 2007 window, click **Submit**.</span></span>  

   > [!NOTE]
   >  <span data-ttu-id="23d53-118">當您按一下 **提交**，[!INCLUDE[btsInpathNoVersion](../../includes/btsinpathnoversion-md.md)]對訊息執行 XML 驗證。</span><span class="sxs-lookup"><span data-stu-id="23d53-118">When you click **Submit**, [!INCLUDE[btsInpathNoVersion](../../includes/btsinpathnoversion-md.md)] performs XML validation on the message.</span></span> <span data-ttu-id="23d53-119">如果驗證不成功，您必須修正驗證錯誤，再繼續進行。</span><span class="sxs-lookup"><span data-stu-id="23d53-119">If the validation is not successful, you must fix the validation errors before proceeding.</span></span>  

10. <span data-ttu-id="23d53-120">在 [提交訊息] 對話方塊中，按一下**接受**提交核准的訊息，以接受變更。</span><span class="sxs-lookup"><span data-stu-id="23d53-120">In the Submit Message dialog box, click **Accept** to submit the approved message with changes accepted.</span></span> <span data-ttu-id="23d53-121">按一下 **拒絕**來提交訊息被拒絕的變更。</span><span class="sxs-lookup"><span data-stu-id="23d53-121">Click **Reject** to submit the message with changes rejected.</span></span> <span data-ttu-id="23d53-122">按一下 **取消**取消提交作業，並傳回至表單。</span><span class="sxs-lookup"><span data-stu-id="23d53-122">Click **Cancel** to cancel the submission and return to the form.</span></span>  

    > [!NOTE]
    >  <span data-ttu-id="23d53-123">如果您接受訊息會變更，[!INCLUDE[btsBizTalkServerNoVersion](../../includes/btsbiztalkservernoversion-md.md)]執行 BRE 驗證訊息上。</span><span class="sxs-lookup"><span data-stu-id="23d53-123">If you accept the message changes, [!INCLUDE[btsBizTalkServerNoVersion](../../includes/btsbiztalkservernoversion-md.md)] performs BRE validations on the message.</span></span>  
    > 
    > [!NOTE]
    >  <span data-ttu-id="23d53-124">如果您拒絕訊息會變更，[!INCLUDE[btsBizTalkServerNoVersion](../../includes/btsbiztalkservernoversion-md.md)]將訊息傳回至工作流程的第一個階段 （建立或修復） 並重設修復工作流程。</span><span class="sxs-lookup"><span data-stu-id="23d53-124">If you reject the message changes, [!INCLUDE[btsBizTalkServerNoVersion](../../includes/btsbiztalkservernoversion-md.md)] returns the message to the first stage of the workflow (create or repair) and resets the repair workflow.</span></span>  

11. <span data-ttu-id="23d53-125">在選取的憑證來簽署表單數位簽章精靈頁面上，選取您想要用來簽署表單 （您建立的核准者的憑證） 的憑證。</span><span class="sxs-lookup"><span data-stu-id="23d53-125">On the Digital Signature Wizard page for selecting the certificate to sign the form, select the certificate that you want to use to sign the form (the certificate that you created for the approver).</span></span> <span data-ttu-id="23d53-126">按一下 **檢視憑證**如果您想要確認您使用的正確的簽章。</span><span class="sxs-lookup"><span data-stu-id="23d53-126">Click **View Certificate** if you want to verify that you are using the correct signature.</span></span> <span data-ttu-id="23d53-127">按 [下一步] 。</span><span class="sxs-lookup"><span data-stu-id="23d53-127">Click **Next**.</span></span>  

    > [!NOTE]
    >  <span data-ttu-id="23d53-128">若要驗證數位簽章的有效性，請按一下**數位簽章**上**工具**功能表上，按一下您想要確認，然後再按一下數位簽章**檢視簽署表單**.</span><span class="sxs-lookup"><span data-stu-id="23d53-128">To verify the validity of a digital signature, click **Digital Signatures** on the **Tools** menu, click the digital signature that you want to verify, and then click **View Signed Form**.</span></span> <span data-ttu-id="23d53-129">您也可以查看哪些角色已的表單先前 （表單可以只由簽署每個工作流程一次的人） 依序按一下**數位簽章**上**工具**功能表。</span><span class="sxs-lookup"><span data-stu-id="23d53-129">You can also see which roles have signed the form previously (a form can only be signed by a person once per workflow) by clicking **Digital Signatures** on the **Tools** menu.</span></span> <span data-ttu-id="23d53-130">如果您需要新增這個角色的另一個簽章，請在[!INCLUDE[btaA4SWIFT2.3abbrevnonumber](../../includes/btaa4swift2-3abbrevnonumber-md.md)]管理主控台。</span><span class="sxs-lookup"><span data-stu-id="23d53-130">If you need to add another signature for this role, do so in the [!INCLUDE[btaA4SWIFT2.3abbrevnonumber](../../includes/btaa4swift2-3abbrevnonumber-md.md)] Management Console.</span></span>  

12. <span data-ttu-id="23d53-131">在輸入註解 [數位簽章精靈] 頁面上，按一下**完成**。</span><span class="sxs-lookup"><span data-stu-id="23d53-131">On the Digital Signature Wizard page for entering comments, click **Finish**.</span></span>  

13. <span data-ttu-id="23d53-132">在驗證表單的數位簽章精靈頁面，確認您所簽署的訊息正確無誤。</span><span class="sxs-lookup"><span data-stu-id="23d53-132">On the Digital Signature Wizard page for verifying the form, verify that the message that you are signing is correct.</span></span> <span data-ttu-id="23d53-133">按一下 **檢視憑證**如果您想要確認您使用的正確的簽章。</span><span class="sxs-lookup"><span data-stu-id="23d53-133">Click **View Certificate** if you want to verify that you are using the correct signature.</span></span> <span data-ttu-id="23d53-134">按一下 **我已登入之前確認此內容**，然後按一下**登**。</span><span class="sxs-lookup"><span data-stu-id="23d53-134">Click **I have verified this content before signing**, and then click **Sign**.</span></span>  

14. <span data-ttu-id="23d53-135">在 [確認數位簽章] 視窗中，按一下**關閉**。</span><span class="sxs-lookup"><span data-stu-id="23d53-135">In the Verify Digital Signature window, click **Close**.</span></span>  

15. <span data-ttu-id="23d53-136">在 [提交成功] 對話方塊中，按一下**確定**。</span><span class="sxs-lookup"><span data-stu-id="23d53-136">In the Submission Success dialog box, click **OK**.</span></span>  

16. <span data-ttu-id="23d53-137">關閉[!INCLUDE[btsInpathNoVersion](../../includes/btsinpathnoversion-md.md)]視窗。</span><span class="sxs-lookup"><span data-stu-id="23d53-137">Close the [!INCLUDE[btsInpathNoVersion](../../includes/btsinpathnoversion-md.md)] window.</span></span>  

17. <span data-ttu-id="23d53-138">在 [[!INCLUDE[btsWinNoVersion](../../includes/btswinnoversion-md.md)]總管] 中，開啟的資料夾，您將設定為接收已傳送的訊息。</span><span class="sxs-lookup"><span data-stu-id="23d53-138">In [!INCLUDE[btsWinNoVersion](../../includes/btswinnoversion-md.md)] Explorer, open the folder that you set up to receive sent messages.</span></span> <span data-ttu-id="23d53-139">請確認該資料夾包含已核准的訊息。</span><span class="sxs-lookup"><span data-stu-id="23d53-139">Verify that the folder contains the approved message.</span></span> <span data-ttu-id="23d53-140">若要確認已修復的訊息文字編輯器中開啟的郵件。</span><span class="sxs-lookup"><span data-stu-id="23d53-140">Open the message in a text editor to verify that the message has been repaired.</span></span>
