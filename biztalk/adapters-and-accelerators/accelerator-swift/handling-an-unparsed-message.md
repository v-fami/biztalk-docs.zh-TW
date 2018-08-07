---
title: 處理未剖析的訊息 |Microsoft Docs
ms.custom: ''
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- unparsed messages
- messages, unparsed messages
ms.assetid: c6a67ff3-3295-489f-9d5f-fb35b2bf8b19
caps.latest.revision: 4
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 8b24b7db4013e5e1f8fdb03c1278a19dc070d0e0
ms.sourcegitcommit: 266308ec5c6a9d8d80ff298ee6051b4843c5d626
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/27/2018
ms.locfileid: "36998663"
---
# <a name="handling-an-unparsed-message"></a><span data-ttu-id="ed9e2-102">處理未剖析的訊息</span><span class="sxs-lookup"><span data-stu-id="ed9e2-102">Handling an Unparsed Message</span></span>
<span data-ttu-id="ed9e2-103">本節說明如何處理未剖析的訊息。</span><span class="sxs-lookup"><span data-stu-id="ed9e2-103">This section describes how to handle an unparsed message.</span></span> <span data-ttu-id="ed9e2-104">不同於無法通過驗證的訊息，您無法修復的訊息，[!INCLUDE[btaA4SWIFT2.3abbrevnonumber](../../includes/btaa4swift2-3abbrevnonumber-md.md)]無法剖析。</span><span class="sxs-lookup"><span data-stu-id="ed9e2-104">Unlike messages that fail validation, you cannot repair a message that [!INCLUDE[btaA4SWIFT2.3abbrevnonumber](../../includes/btaa4swift2-3abbrevnonumber-md.md)] cannot parse.</span></span> <span data-ttu-id="ed9e2-105">Message Repair 和 New Submission 會顯示訊息和剖析錯誤的本質，並讓您列印訊息，或將它儲存到本機檔案。</span><span class="sxs-lookup"><span data-stu-id="ed9e2-105">Message Repair and New Submission displays the message and the nature of the parsing error, and enables you to print the message or save it to a local file.</span></span> <span data-ttu-id="ed9e2-106">然後，您可以警示將訊息傳送至特定的剖析失敗本質的實體。</span><span class="sxs-lookup"><span data-stu-id="ed9e2-106">You can then alert the entity that sent the message to the specific nature of the parsing failure.</span></span>  

### <a name="to-handle-an-unparsed-message"></a><span data-ttu-id="ed9e2-107">若要處理未剖析的訊息</span><span class="sxs-lookup"><span data-stu-id="ed9e2-107">To handle an unparsed message</span></span>  

1. <span data-ttu-id="ed9e2-108">在 Internet Explorer 中，開啟 MRSR 網站http://localhost/sites/bassite。</span><span class="sxs-lookup"><span data-stu-id="ed9e2-108">In Internet Explorer, open your MRSR site at http://localhost/sites/bassite.</span></span>  

2. <span data-ttu-id="ed9e2-109">在 [首頁] 視窗中，按一下**文件**。</span><span class="sxs-lookup"><span data-stu-id="ed9e2-109">In the Home window, click **Documents**.</span></span>  

3. <span data-ttu-id="ed9e2-110">在文件視窗中，在**文件庫**，按一下**Unparsed**。</span><span class="sxs-lookup"><span data-stu-id="ed9e2-110">In the Documents window, under **Document Libraries**, click **Unparsed**.</span></span>  

4. <span data-ttu-id="ed9e2-111">在未剖析的視窗中，按一下**收件匣**。</span><span class="sxs-lookup"><span data-stu-id="ed9e2-111">In the Unparsed window, click **Inbox**.</span></span>  

5. <span data-ttu-id="ed9e2-112">未剖析的收件匣 視窗中，在提供的訊息，未不剖析、 按一下訊息，右邊的箭號，然後按一下**在 Microsoft Office InfoPath 中編輯**。</span><span class="sxs-lookup"><span data-stu-id="ed9e2-112">In the Unparsed Inbox window, point to the message that did not parse, click the arrow to the right of the message, and then click **Edit in Microsoft Office InfoPath**.</span></span>  

6. <span data-ttu-id="ed9e2-113">在 [SWIFT 加速器] 窗格中，按一下**錯誤**。</span><span class="sxs-lookup"><span data-stu-id="ed9e2-113">In the SWIFT Accelerator pane, click **Errors**.</span></span>  

7. <span data-ttu-id="ed9e2-114">XML 驗證錯誤與剖析中 窗格中，會讀取剖析錯誤。</span><span class="sxs-lookup"><span data-stu-id="ed9e2-114">In the Parse and XML Validation Errors pane, read the parse error.</span></span>  

8. <span data-ttu-id="ed9e2-115">在剖析的訊息 窗格中，檢閱該訊息。</span><span class="sxs-lookup"><span data-stu-id="ed9e2-115">In the Unparsed Message pane, review the message.</span></span>  

   > [!NOTE]
   >  <span data-ttu-id="ed9e2-116">如果您想要在列印訊息時，剖析的訊息 窗格中，於**檔案**功能表上，按一下**列印**。</span><span class="sxs-lookup"><span data-stu-id="ed9e2-116">If you want to print the message, in the Unparsed Message pane, on the **File** menu, click **Print**.</span></span>  
   > 
   > [!NOTE]
   >  <span data-ttu-id="ed9e2-117">如果您想要將訊息儲存到本機檔案，在剖析的訊息 窗格中，於**檔案**功能表上，按一下**另存新檔**。</span><span class="sxs-lookup"><span data-stu-id="ed9e2-117">If you want to save the message to a local file, in the Unparsed Message pane, on the **File** menu, click **Save As**.</span></span> <span data-ttu-id="ed9e2-118">在**另存新檔**對話方塊中，於**將儲存在**下拉式清單中，移至您想要儲存的檔案中，然後再按一下資料夾**確定**。</span><span class="sxs-lookup"><span data-stu-id="ed9e2-118">In the **Save As** dialog box, in the **Save in** drop-down list, move to the folder that you want to save the file in, and then click **OK**.</span></span> [!INCLUDE[btaA4SWIFT2.3abbrevnonumber](../../includes/btaa4swift2-3abbrevnonumber-md.md)]<span data-ttu-id="ed9e2-119"> 將訊息儲存在 XML 格式。</span><span class="sxs-lookup"><span data-stu-id="ed9e2-119"> saves the message in XML format.</span></span>  

9. <span data-ttu-id="ed9e2-120">在剖析的訊息 窗格中，進行必要的變更，，然後按一下**送出**。</span><span class="sxs-lookup"><span data-stu-id="ed9e2-120">In the Unparsed Message pane, make the necessary changes, and then click **Submit**.</span></span>  

    > [!NOTE]
    >  <span data-ttu-id="ed9e2-121">您無法驗證您修復未剖析的訊息。</span><span class="sxs-lookup"><span data-stu-id="ed9e2-121">You cannot validate an unparsed message that you have repaired.</span></span>  

10. <span data-ttu-id="ed9e2-122">在 提交訊息 對話方塊中，按一下**接受**提交已修復的訊息，以接受變更，按一下**拒絕**拒絕變更，或按一下 **取消**取消送出，並返回表單。</span><span class="sxs-lookup"><span data-stu-id="ed9e2-122">In the Submit Message dialog box, click **Accept** to submit the repaired message with changes accepted, click **Reject** to reject the changes, or click **Cancel** to cancel the submission and return to the form.</span></span>  

11. <span data-ttu-id="ed9e2-123">如果您按下**Accept**或是**拒絕**在步驟 11 中，在數位簽章精靈頁面上，選取您想要用來簽署表單 （您為 repairer 建立憑證，） 的憑證，然後按一下 [**下一步]**。</span><span class="sxs-lookup"><span data-stu-id="ed9e2-123">If you clicked **Accept** or **Reject** in step 11, on the Digital Signature Wizard page, select the certificate that you want to use to sign the form (the certificate that you created for the repairer), and then click **Next**.</span></span>  

    > [!NOTE]
    >  <span data-ttu-id="ed9e2-124">若要驗證數位簽章的有效性，請按一下**數位簽章**上**工具**功能表上，按一下您想要確認，然後再按一下數位簽章**檢視簽署表單**.</span><span class="sxs-lookup"><span data-stu-id="ed9e2-124">To verify the validity of a digital signature, click **Digital Signatures** on the **Tools** menu, click the digital signature that you want to verify, and then click **View Signed Form**.</span></span>  

    > [!NOTE]
    >  <span data-ttu-id="ed9e2-125">任何執行的任何角色的使用者可以送出他們修復未剖析的訊息。</span><span class="sxs-lookup"><span data-stu-id="ed9e2-125">Any user performing any role can submit an unparsed message that they have repaired.</span></span>  

12. <span data-ttu-id="ed9e2-126">在輸入註解 [數位簽章精靈] 頁面上，按一下**完成**。</span><span class="sxs-lookup"><span data-stu-id="ed9e2-126">On the Digital Signature Wizard page for entering comments, click **Finish**.</span></span>  

13. <span data-ttu-id="ed9e2-127">在驗證表單的數位簽章精靈頁面，確認您所簽署的訊息正確無誤。</span><span class="sxs-lookup"><span data-stu-id="ed9e2-127">On the Digital Signature Wizard page for verifying the form, verify that the message that you are signing is correct.</span></span> <span data-ttu-id="ed9e2-128">按一下 **檢視憑證**如果您想要確認您使用的正確的簽章。</span><span class="sxs-lookup"><span data-stu-id="ed9e2-128">Click **View Certificate** if you want to verify that you are using the correct signature.</span></span> <span data-ttu-id="ed9e2-129">按一下 **我已登入之前確認此內容**，然後按一下**登**。</span><span class="sxs-lookup"><span data-stu-id="ed9e2-129">Click **I have verified this content before signing**, and then click **Sign**.</span></span>  

14. <span data-ttu-id="ed9e2-130">在 [確認數位簽章] 視窗中，按一下**關閉**。</span><span class="sxs-lookup"><span data-stu-id="ed9e2-130">In the Verify Digital Signature window, click **Close**.</span></span>  

15. <span data-ttu-id="ed9e2-131">在 [提交成功] 對話方塊中，按一下**確定**。</span><span class="sxs-lookup"><span data-stu-id="ed9e2-131">In the Submission Success dialog box, click **OK**.</span></span>  

16. <span data-ttu-id="ed9e2-132">關閉[!INCLUDE[btsInpathNoVersion](../../includes/btsinpathnoversion-md.md)]視窗。</span><span class="sxs-lookup"><span data-stu-id="ed9e2-132">Close the [!INCLUDE[btsInpathNoVersion](../../includes/btsinpathnoversion-md.md)] window.</span></span>
