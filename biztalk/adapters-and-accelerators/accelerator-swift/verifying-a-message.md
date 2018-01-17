---
title: "確認訊息 |Microsoft 文件"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- messages, verifying
- verifying, messages
ms.assetid: df2b72bb-4dc1-4fdd-8f63-35fc73a12151
caps.latest.revision: "6"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 0f2fdc186e93bd182b3021a3ef8fc258cee59923
ms.sourcegitcommit: 3fd1c85d9dc2ce7b77da75a5c2087cc48cfcbe50
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 01/17/2018
---
# <a name="verifying-a-message"></a><span data-ttu-id="bf65e-102">確認訊息</span><span class="sxs-lookup"><span data-stu-id="bf65e-102">Verifying a Message</span></span>
<span data-ttu-id="bf65e-103">本章節描述如何確認已修復的訊息。</span><span class="sxs-lookup"><span data-stu-id="bf65e-103">This section describes how to verify a message that has been repaired.</span></span>  
  
### <a name="to-verify-a-message"></a><span data-ttu-id="bf65e-104">若要確認訊息</span><span class="sxs-lookup"><span data-stu-id="bf65e-104">To verify a message</span></span>  
  
1.  <span data-ttu-id="bf65e-105">在 Internet Explorer 中，開啟 MRSR http://localhost/sites/bassite 您的網站。</span><span class="sxs-lookup"><span data-stu-id="bf65e-105">In Internet Explorer, open your MRSR site at http://localhost/sites/bassite.</span></span>  
  
2.  <span data-ttu-id="bf65e-106">在 [首頁] 視窗中，按一下**文件**。</span><span class="sxs-lookup"><span data-stu-id="bf65e-106">In the Home window, click **Documents**.</span></span>  
  
3.  <span data-ttu-id="bf65e-107">在文件視窗中，在**文件庫**，按一下   **\<*部門名稱*\>_Verifier**。</span><span class="sxs-lookup"><span data-stu-id="bf65e-107">In the Documents window, under **Document Libraries**, click **\<*Department name*\>_Verifier**.</span></span>  
  
4.  <span data-ttu-id="bf65e-108">在確認視窗中，按一下 **收件匣**。</span><span class="sxs-lookup"><span data-stu-id="bf65e-108">In the Verify window, click **Inbox**.</span></span>  
  
5.  <span data-ttu-id="bf65e-109">在 確認收件匣 視窗中，指向 訊息的標題，請按一下訊息標題右邊的箭號，然後按一下**編輯在 Microsoft Office InfoPath**。</span><span class="sxs-lookup"><span data-stu-id="bf65e-109">In the Verify Inbox window, point to the title of the message, click the arrow to the right of the message title, and then click **Edit in Microsoft Office InfoPath**.</span></span>  
  
6.  <span data-ttu-id="bf65e-110">在**檔案下載**對話方塊中，按一下 **開啟**。</span><span class="sxs-lookup"><span data-stu-id="bf65e-110">In the **File Download** dialog box, click **Open**.</span></span>  
  
7.  <span data-ttu-id="bf65e-111">中的目前角色： RekeyVerify 窗格[!INCLUDE[btsOfficeNoVersion](../../includes/btsofficenoversion-md.md)] [!INCLUDE[btsInpathNoVersion](../../includes/btsinpathnoversion-md.md)] 2007年] 視窗中，按一下 [**錯誤**。</span><span class="sxs-lookup"><span data-stu-id="bf65e-111">In the Current Roles: RekeyVerify pane of the [!INCLUDE[btsOfficeNoVersion](../../includes/btsofficenoversion-md.md)][!INCLUDE[btsInpathNoVersion](../../includes/btsinpathnoversion-md.md)] 2007 window, click **Errors**.</span></span> <span data-ttu-id="bf65e-112">檢閱中顯示任何錯誤**剖析和 XML 驗證錯誤**方塊和**BRE 驗證錯誤**方塊。</span><span class="sxs-lookup"><span data-stu-id="bf65e-112">Review any errors shown in the **Parse and XML Validation Errors** box and the **BRE Validation Errors** box.</span></span>  
  
8.  <span data-ttu-id="bf65e-113">在[!INCLUDE[btsInpathNoVersion](../../includes/btsinpathnoversion-md.md)]形成、 捲動到 錯誤的位置，確認已更正錯誤。</span><span class="sxs-lookup"><span data-stu-id="bf65e-113">In the [!INCLUDE[btsInpathNoVersion](../../includes/btsinpathnoversion-md.md)] form, scroll to the location of the error and verify that the error has been corrected.</span></span> <span data-ttu-id="bf65e-114">您可以看到原始錯誤是依序按一下**錯誤**目前的角色： RekeyVerify 窗格中，以及在其中一個錯誤窗格中檢視錯誤。</span><span class="sxs-lookup"><span data-stu-id="bf65e-114">You can see what the original error was by clicking **Errors** in the Current Role: RekeyVerify pane, and viewing the error in one of the error panes.</span></span> <span data-ttu-id="bf65e-115">您也可以比較出來和修復版本的訊息，依序按一下**訊息詳細資料**目前的角色： RekeyVerify 窗格。</span><span class="sxs-lookup"><span data-stu-id="bf65e-115">You can also compare the unrepaired and repaired versions of the message by clicking **Message Details** in the Current Role: RekeyVerify pane.</span></span>  
  
9. <span data-ttu-id="bf65e-116">若要確定會驗證訊息，**驗證**目前的角色： RekeyVerify] 窗格中，然後按一下 [**驗證訊息**。</span><span class="sxs-lookup"><span data-stu-id="bf65e-116">To ensure that the message will validate, click **Validation** in the Current Role: RekeyVerify pane, and then click **Validate Message**.</span></span>  
  
    > [!NOTE]
    >  <span data-ttu-id="bf65e-117">在目前的角色中的訊息驗證的 [結果] 窗格： RekeyVerify 窗格中會指出您需要重設金鑰的訊息中的所有欄位。</span><span class="sxs-lookup"><span data-stu-id="bf65e-117">The Results pane under Message Validation in the Current Role: RekeyVerify pane indicates all fields in the message that you need to rekey.</span></span> [!INCLUDE[btaA4SWIFT2.3abbrevnonumber](../../includes/btaa4swift2-3abbrevnonumber-md.md)]<span data-ttu-id="bf65e-118">將標示紅色星號 [訊息] 窗格中的這些欄位。</span><span class="sxs-lookup"><span data-stu-id="bf65e-118"> marks these fields in the Message pane with a red asterisk.</span></span>  
  
10. <span data-ttu-id="bf65e-119">重新鍵入資料，以紅色星號 （表示資料，必須 rekeyed 送出前） 標示為 [訊息] 窗格中的所有欄位至。</span><span class="sxs-lookup"><span data-stu-id="bf65e-119">Rekey data into all fields in the Message pane marked with a red asterisk (indicating that the data must be rekeyed before submission).</span></span>  
  
    > [!NOTE]
    >  <span data-ttu-id="bf65e-120">您也可以按一下來重設金鑰訊息欄位中顯示的資料，您需要**訊息詳細資料**目前的角色： RekeyVerify 窗格中，並捲動至欄位的原始訊息。</span><span class="sxs-lookup"><span data-stu-id="bf65e-120">You can display the data that you need to rekey into message fields by clicking **Message Details** in the Current Role: RekeyVerify pane, and scrolling through the original message to the field.</span></span> <span data-ttu-id="bf65e-121">這是，則為 true，除非發生驗證錯誤中的其中一個在原始訊息中，重設金鑰欄位必須在此情況下修復欄位，當您重設金鑰。</span><span class="sxs-lookup"><span data-stu-id="bf65e-121">This is true unless there was a validation error in one of the rekey fields in the original message, in which case you have to repair the field when you rekey it.</span></span>  
  
11. <span data-ttu-id="bf65e-122">按一下**驗證**中**目前角色： RekeyVerify**  窗格中，然後再按一下**驗證訊息**。</span><span class="sxs-lookup"><span data-stu-id="bf65e-122">Click **Validation** in the **Current Role: RekeyVerify** pane, and then click **Validate Message**.</span></span> <span data-ttu-id="bf65e-123">確認 [結果] 窗格會顯示訊息**訊息無效**。</span><span class="sxs-lookup"><span data-stu-id="bf65e-123">Verify that the Results pane displays the message **The message is valid**.</span></span>  
  
12. <span data-ttu-id="bf65e-124">按一下**送出**中[!INCLUDE[btsOfficeNoVersion](../../includes/btsofficenoversion-md.md)] [!INCLUDE[btsInpathNoVersion](../../includes/btsinpathnoversion-md.md)] 2007年視窗。</span><span class="sxs-lookup"><span data-stu-id="bf65e-124">Click **Submit** in the [!INCLUDE[btsOfficeNoVersion](../../includes/btsofficenoversion-md.md)][!INCLUDE[btsInpathNoVersion](../../includes/btsinpathnoversion-md.md)] 2007 window.</span></span>  
  
    > [!NOTE]
    >  <span data-ttu-id="bf65e-125">當您按一下**送出**，[!INCLUDE[btsInpathNoVersion](../../includes/btsinpathnoversion-md.md)]對訊息執行 XML 驗證。</span><span class="sxs-lookup"><span data-stu-id="bf65e-125">When you click **Submit**, [!INCLUDE[btsInpathNoVersion](../../includes/btsinpathnoversion-md.md)] performs XML validation on the message.</span></span> <span data-ttu-id="bf65e-126">如果驗證不成功，您必須修正驗證錯誤後再繼續。</span><span class="sxs-lookup"><span data-stu-id="bf65e-126">If the validation is not successful, you must fix the validation errors before proceeding.</span></span>  
  
13. <span data-ttu-id="bf65e-127">在 提交訊息 對話方塊中，按一下 **接受**提交變更接受已驗證的訊息。</span><span class="sxs-lookup"><span data-stu-id="bf65e-127">In the Submit Message dialog box, click **Accept** to submit the verified message with changes accepted.</span></span> <span data-ttu-id="bf65e-128">按一下**拒絕**來提交訊息被拒絕的變更。</span><span class="sxs-lookup"><span data-stu-id="bf65e-128">Click **Reject** to submit the message with changes rejected.</span></span> <span data-ttu-id="bf65e-129">按一下**取消**取消提交作業，並返回表單。</span><span class="sxs-lookup"><span data-stu-id="bf65e-129">Click **Cancel** to cancel the submission and return to the form.</span></span>  
  
    > [!NOTE]
    >  <span data-ttu-id="bf65e-130">如果您接受訊息的變更，[!INCLUDE[btsBizTalkServerNoVersion](../../includes/btsbiztalkservernoversion-md.md)]執行 BRE 驗證訊息。</span><span class="sxs-lookup"><span data-stu-id="bf65e-130">If you accept the message changes, [!INCLUDE[btsBizTalkServerNoVersion](../../includes/btsbiztalkservernoversion-md.md)] performs BRE validations on the message.</span></span>  
  
    > [!NOTE]
    >  <span data-ttu-id="bf65e-131">如果您拒絕訊息的修訂，[!INCLUDE[btsBizTalkServerNoVersion](../../includes/btsbiztalkservernoversion-md.md)]將訊息傳回至工作流程的第一個階段 （建立或修復），並重設修復工作流程。</span><span class="sxs-lookup"><span data-stu-id="bf65e-131">If you reject the message changes, [!INCLUDE[btsBizTalkServerNoVersion](../../includes/btsbiztalkservernoversion-md.md)] returns the message to the first stage of the workflow (create or repair) and resets the repair workflow.</span></span>  
  
14. <span data-ttu-id="bf65e-132">在選取的憑證來簽署格式的數位簽章精靈頁面上，選取您想要使用的表單 （憑證驗證器所建立），憑證及 **下一步**。</span><span class="sxs-lookup"><span data-stu-id="bf65e-132">On the Digital Signature Wizard page for selecting the certificate to sign the form, select the certificate that you want to use to sign the form (the certificate that you created for the verifier), and then click **Next**.</span></span>  
  
    > [!NOTE]
    >  <span data-ttu-id="bf65e-133">若要驗證數位簽章的有效性，請按一下**數位簽章**上**工具**功能表上，按一下您想要確認，然後再按一下數位簽章**檢視簽署表單**.</span><span class="sxs-lookup"><span data-stu-id="bf65e-133">To verify the validity of a digital signature, click **Digital Signatures** on the **Tools** menu, click the digital signature that you want to verify, and then click **View Signed Form**.</span></span> <span data-ttu-id="bf65e-134">如果您要新增此角色的另一個簽章，請執行這個動作[!INCLUDE[btaA4SWIFT2.3abbrevnonumber](../../includes/btaa4swift2-3abbrevnonumber-md.md)]管理主控台。</span><span class="sxs-lookup"><span data-stu-id="bf65e-134">If you need to add another signature for this role, do so in the [!INCLUDE[btaA4SWIFT2.3abbrevnonumber](../../includes/btaa4swift2-3abbrevnonumber-md.md)] Management Console.</span></span>  
  
15. <span data-ttu-id="bf65e-135">在輸入的註解的數位簽章精靈頁面上，按一下 **完成**。</span><span class="sxs-lookup"><span data-stu-id="bf65e-135">On the Digital Signature Wizard page for entering comments, click **Finish**.</span></span>  
  
16. <span data-ttu-id="bf65e-136">在驗證表單的 數位簽章精靈頁面上，確認您所簽署的訊息正確。</span><span class="sxs-lookup"><span data-stu-id="bf65e-136">On the Digital Signature Wizard page for verifying the form, verify that the message that you are signing is correct.</span></span> <span data-ttu-id="bf65e-137">按一下**檢視憑證**如果您想要確認您是否使用正確的簽章。</span><span class="sxs-lookup"><span data-stu-id="bf65e-137">Click **View Certificate** if you want to verify that you are using the correct signature.</span></span> <span data-ttu-id="bf65e-138">按一下**我已簽署前確認此內容**，然後按一下 **登**。</span><span class="sxs-lookup"><span data-stu-id="bf65e-138">Click **I have verified this content before signing**, and then click **Sign**.</span></span>  
  
17. <span data-ttu-id="bf65e-139">在 [確認數位簽章] 視窗中，按一下**關閉**。</span><span class="sxs-lookup"><span data-stu-id="bf65e-139">In the Verify Digital Signature window, click **Close**.</span></span>  
  
18. <span data-ttu-id="bf65e-140">在 [提交成功] 對話方塊中，按一下**確定**。</span><span class="sxs-lookup"><span data-stu-id="bf65e-140">In the Submission Success dialog box, click **OK**.</span></span>  
  
19. <span data-ttu-id="bf65e-141">關閉[!INCLUDE[btsInpathNoVersion](../../includes/btsinpathnoversion-md.md)]視窗。</span><span class="sxs-lookup"><span data-stu-id="bf65e-141">Close the [!INCLUDE[btsInpathNoVersion](../../includes/btsinpathnoversion-md.md)] window.</span></span>  
  
20. <span data-ttu-id="bf65e-142">在 MRSR 網站中，按一下 **文件，並列出**。</span><span class="sxs-lookup"><span data-stu-id="bf65e-142">In MRSR site, click **Documents and Lists**.</span></span> <span data-ttu-id="bf65e-143">如果您按下**接受**接受步驟 13 中的變更，請確認\<部門名稱\>_Approve 文件庫包含未修改過的訊息。</span><span class="sxs-lookup"><span data-stu-id="bf65e-143">If you clicked **Accept** to accept the changes in step 13, verify that the \<Department name\>_Approve document library contains the message that was just modified.</span></span> <span data-ttu-id="bf65e-144">如果您已經有開啟的文件與清單 視窗，按一下**重新整理**上**檢視**功能表。</span><span class="sxs-lookup"><span data-stu-id="bf65e-144">If you already had the Documents and Lists window open, click **Refresh** on the **View** menu.</span></span> <span data-ttu-id="bf65e-145">如果您按下**拒絕**拒絕步驟 13 中的變更，確認*\<電腦名稱\>*_Outbox 文件庫包含未修改過的訊息。</span><span class="sxs-lookup"><span data-stu-id="bf65e-145">If you clicked **Reject** to reject the changes in step 13, verify that the *\<computer name\>*_Outbox document library contains the message that was just modified.</span></span>