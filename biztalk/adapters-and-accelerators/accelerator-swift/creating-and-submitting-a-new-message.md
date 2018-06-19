---
title: 建立及提交新訊息 |Microsoft 文件
ms.custom: ''
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- creating, messages
- submitting, messages
- messages, submitting
- messages, creating
ms.assetid: 88b7a2d3-44a4-44e4-ba8c-527c10290925
caps.latest.revision: 8
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 42cd2a82fe0ecde75446e68f9f58e17f103e5efa
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/20/2017
ms.locfileid: "22209862"
---
# <a name="creating-and-submitting-a-new-message"></a><span data-ttu-id="bab1b-102">建立及提交新的訊息</span><span class="sxs-lookup"><span data-stu-id="bab1b-102">Creating and Submitting a New Message</span></span>
<span data-ttu-id="bab1b-103">本節說明如何提交新的訊息。</span><span class="sxs-lookup"><span data-stu-id="bab1b-103">This section describes how to submit a new message.</span></span> <span data-ttu-id="bab1b-104">做為已修復的訊息，新的訊息必須驗證並核准訊息建立者以外的人。</span><span class="sxs-lookup"><span data-stu-id="bab1b-104">As with a repaired message, a new message must be verified and approved by people other than the message creator.</span></span>  
  
 <span data-ttu-id="bab1b-105">若要提交新的訊息，您必須上傳到新的 SWIFT 訊息文件庫的您想要提交的訊息類型的訊息範本檔案。</span><span class="sxs-lookup"><span data-stu-id="bab1b-105">To submit a new message, you must upload into the New SWIFT Messages document library a message template file for the type of message that you want to submit.</span></span> <span data-ttu-id="bab1b-106">您可以手動上傳的單一訊息的範本，或您可以上傳使用 FormPublish 工具的所有訊息範本。</span><span class="sxs-lookup"><span data-stu-id="bab1b-106">You can upload a single message template manually, or you can upload all message templates using the FormPublish tool.</span></span>  
  
### <a name="to-upload-a-single-message-template-into-the-new-document-library"></a><span data-ttu-id="bab1b-107">若要將單一訊息範本上傳到新的文件庫</span><span class="sxs-lookup"><span data-stu-id="bab1b-107">To upload a single message template into the new document library</span></span>  
  
1.  <span data-ttu-id="bab1b-108">請參閱章節[表單產生器公用程式來產生 MT/MX InfoPath 表單](../../adapters-and-accelerators/accelerator-swift/form-generator-utility-to-generate-mt-mx-infopath-forms.md)如需相關指示。</span><span class="sxs-lookup"><span data-stu-id="bab1b-108">Refer to the section [Form Generator Utility to Generate MT/MX InfoPath Forms](../../adapters-and-accelerators/accelerator-swift/form-generator-utility-to-generate-mt-mx-infopath-forms.md) for instructions.</span></span>  
  
### <a name="to-create-and-submit-a-new-message"></a><span data-ttu-id="bab1b-109">若要建立並提交新的訊息</span><span class="sxs-lookup"><span data-stu-id="bab1b-109">To create and submit a new message</span></span>  
  
1.  <span data-ttu-id="bab1b-110">在 Internet Explorer 中，開啟 MRSR http://localhost/sites/bassite 您的網站。</span><span class="sxs-lookup"><span data-stu-id="bab1b-110">In Internet Explorer, open your MRSR site at http://localhost/sites/bassite.</span></span>  
  
2.  <span data-ttu-id="bab1b-111">按一下**文件**，然後按一下 **新 SWIFT 訊息**。</span><span class="sxs-lookup"><span data-stu-id="bab1b-111">Click **Documents**, and then click **New SWIFT Messages**.</span></span>  
  
3.  <span data-ttu-id="bab1b-112">在 [新 SWIFT 訊息] 頁面中，按兩下包含您想要建立的訊息類型分類的名稱。</span><span class="sxs-lookup"><span data-stu-id="bab1b-112">On the New SWIFT Messages page, double-click the name of the category containing the type of the message that you would like to create.</span></span>  
  
4.  <span data-ttu-id="bab1b-113">按一下您想要建立之訊息的表單範本。</span><span class="sxs-lookup"><span data-stu-id="bab1b-113">Click the form template for the message that you want to create.</span></span>  
  
5.  <span data-ttu-id="bab1b-114">在[!INCLUDE[btsInpathNoVersion](../../includes/btsinpathnoversion-md.md)]2007年 視窗中的，在訊息形成，類型 （以星號說明） 的所有必要的欄位和任何選用的欄位，您想要使用的訊息資料。</span><span class="sxs-lookup"><span data-stu-id="bab1b-114">In the [!INCLUDE[btsInpathNoVersion](../../includes/btsinpathnoversion-md.md)] 2007 window, in the message form, type message data for all required fields (as denoted by an asterisk) and any optional fields you want to use.</span></span>  
  
6.  <span data-ttu-id="bab1b-115">若要查閱 BIC、 目前的角色： 建立窗格，請按一下**BIC 查閱**。</span><span class="sxs-lookup"><span data-stu-id="bab1b-115">To look up a BIC, in the Current Role: Create pane, click **BIC Lookup**.</span></span>  
  
7.  <span data-ttu-id="bab1b-116">輸入的金融機構、 銀行代碼和國家/地區名稱，然後按一下**搜尋**。</span><span class="sxs-lookup"><span data-stu-id="bab1b-116">Type the name of the financial institution, the bank code, and the country/region, and then click **Search**.</span></span>  
  
8.  <span data-ttu-id="bab1b-117">從 [BIC 查閱] 窗格中，將複製到訊息形式的適當銀行代碼欄位的 BIC。</span><span class="sxs-lookup"><span data-stu-id="bab1b-117">From the BIC Lookup pane, copy the BIC into the appropriate bank code field in the message form.</span></span>  
  
9. <span data-ttu-id="bab1b-118">目前的角色： 建立窗格，請按一下**驗證**，然後按一下 **驗證訊息**。</span><span class="sxs-lookup"><span data-stu-id="bab1b-118">In the Current Role: Create pane, click **Validation**, and then click **Validate Message**.</span></span>  
  
10. <span data-ttu-id="bab1b-119">在 [結果] 窗格的目前角色： 建立窗格，請判斷您需要在訊息中修正的錯誤。</span><span class="sxs-lookup"><span data-stu-id="bab1b-119">In the Results pane of the Current Role: Create pane, determine the errors that you need to fix in the message.</span></span>  
  
    > [!NOTE]
    >  <span data-ttu-id="bab1b-120">如果您有固定的所有驗證錯誤訊息中，您只能提交新的訊息。</span><span class="sxs-lookup"><span data-stu-id="bab1b-120">You can only submit a new message if you have fixed all validation errors in the message.</span></span>  
  
11. <span data-ttu-id="bab1b-121">從標準工具列則位於視窗的頂端，按一下 **送出**。</span><span class="sxs-lookup"><span data-stu-id="bab1b-121">From the Standard toolbar at the top of the window, click **Submit**.</span></span>  
  
12. <span data-ttu-id="bab1b-122">在選取的憑證來簽署格式的數位簽章精靈頁面上，選取您想要使用的表單 （您為建立者建立的憑證） 的憑證。</span><span class="sxs-lookup"><span data-stu-id="bab1b-122">On the Digital Signature Wizard page for selecting the certificate to sign the form, select the certificate that you want to use to sign the form (the certificate that you created for the creator).</span></span> <span data-ttu-id="bab1b-123">按一下**檢視憑證**如果您想要確認您是否使用正確的簽章。</span><span class="sxs-lookup"><span data-stu-id="bab1b-123">Click **View Certificate** if you want to verify that you are using the correct signature.</span></span> <span data-ttu-id="bab1b-124">按一下 **[下一步]**。</span><span class="sxs-lookup"><span data-stu-id="bab1b-124">Click **Next**.</span></span>  
  
    > [!NOTE]
    >  <span data-ttu-id="bab1b-125">若要驗證數位簽章的有效性，請按一下**數位簽章**上**工具**功能表上，按一下您想要確認，然後再按一下數位簽章**檢視簽署表單**.</span><span class="sxs-lookup"><span data-stu-id="bab1b-125">To verify the validity of a digital signature, click **Digital Signatures** on the **Tools** menu, click the digital signature that you want to verify, and then click **View Signed Form**.</span></span>  
  
13. <span data-ttu-id="bab1b-126">在輸入的註解的數位簽章精靈頁面上，按一下 **完成**。</span><span class="sxs-lookup"><span data-stu-id="bab1b-126">On the Digital Signature Wizard page for entering comments, click **Finish**.</span></span>  
  
14. <span data-ttu-id="bab1b-127">在驗證表單的 數位簽章精靈頁面上，確認您所簽署的訊息正確。</span><span class="sxs-lookup"><span data-stu-id="bab1b-127">On the Digital Signature Wizard page for verifying the form, verify that the message that you are signing is correct.</span></span> <span data-ttu-id="bab1b-128">按一下**檢視憑證**如果您想要確認您是否使用正確的簽章。</span><span class="sxs-lookup"><span data-stu-id="bab1b-128">Click **View Certificate** if you want to verify that you are using the correct signature.</span></span> <span data-ttu-id="bab1b-129">按一下**我已簽署前確認此內容**，然後按一下 **登**。</span><span class="sxs-lookup"><span data-stu-id="bab1b-129">Click **I have verified this content before signing**, and then click **Sign**.</span></span>  
  
15. <span data-ttu-id="bab1b-130">在 [確認數位簽章] 視窗中，按一下**關閉**。</span><span class="sxs-lookup"><span data-stu-id="bab1b-130">In the Verify Digital Signature window, click **Close**.</span></span>  
  
16. <span data-ttu-id="bab1b-131">在 [提交成功] 對話方塊中，按一下**確定**。</span><span class="sxs-lookup"><span data-stu-id="bab1b-131">In the Submission Success dialog box, click **OK**.</span></span>  
  
17. <span data-ttu-id="bab1b-132">關閉[!INCLUDE[btsInpathNoVersion](../../includes/btsinpathnoversion-md.md)]視窗。</span><span class="sxs-lookup"><span data-stu-id="bab1b-132">Close the [!INCLUDE[btsInpathNoVersion](../../includes/btsinpathnoversion-md.md)] window.</span></span>