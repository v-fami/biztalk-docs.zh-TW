---
title: InfoPath 安全性 |Microsoft Docs
ms.custom: ''
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- security, InfoPath forms
- InfoPath forms, security
ms.assetid: 6ed7b5cc-9801-45a5-8fdb-e5d56dd36435
caps.latest.revision: 4
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: ef3b1eff57f225d90e7f491f0a8f48ef88f00463
ms.sourcegitcommit: 266308ec5c6a9d8d80ff298ee6051b4843c5d626
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/27/2018
ms.locfileid: "36983575"
---
# <a name="infopath-security"></a><span data-ttu-id="88f98-102">InfoPath 安全性</span><span class="sxs-lookup"><span data-stu-id="88f98-102">InfoPath Security</span></span>
<span data-ttu-id="88f98-103">Microsoft [!INCLUDE[btsOfficeNoVersion](../../includes/btsofficenoversion-md.md)] [!INCLUDE[btsInpathNoVersion](../../includes/btsinpathnoversion-md.md)] 2007年可讓您數位簽章使用數位憑證，將表單中使用 XML 簽章。</span><span class="sxs-lookup"><span data-stu-id="88f98-103">Microsoft [!INCLUDE[btsOfficeNoVersion](../../includes/btsofficenoversion-md.md)] [!INCLUDE[btsInpathNoVersion](../../includes/btsinpathnoversion-md.md)] 2007 uses XML Signatures to let you digitally sign a form using a digital certificate.</span></span> <span data-ttu-id="88f98-104">XML 簽章定義的標準 xml 數位簽章，您用來保護包含在 XML 文件中的資料。</span><span class="sxs-lookup"><span data-stu-id="88f98-104">XML Signatures defines a standard for XML-based digital signatures that you use to help secure the data contained in XML documents.</span></span> <span data-ttu-id="88f98-105">XML 簽章是由 World Wide Web Consortium (W3C) 所控制的標準。</span><span class="sxs-lookup"><span data-stu-id="88f98-105">XML Signatures is a standard governed by the World Wide Web Consortium (W3C).</span></span>  
  
 <span data-ttu-id="88f98-106">數位簽章是驗證的巨集或文件上電子、 加密型安全性戳記。</span><span class="sxs-lookup"><span data-stu-id="88f98-106">A digital signature is an electronic, encryption-based, secure stamp of authentication on a macro or document.</span></span> <span data-ttu-id="88f98-107">當數位簽章[!INCLUDE[btsInpathNoVersion](../../includes/btsinpathnoversion-md.md)]表單中，透過表單輸入的 XML 執行個體 「 加上 「 數位簽章 (簽章公用金鑰和帶正負號的資料摘要會寫入至 XML 中的專用節點)。</span><span class="sxs-lookup"><span data-stu-id="88f98-107">When digitally signing an [!INCLUDE[btsInpathNoVersion](../../includes/btsinpathnoversion-md.md)] form, the XML instance entered through the form is "stamped" with a digital signature (the signature public key and signed data digest is written to a dedicated node in the XML).</span></span> <span data-ttu-id="88f98-108">此簽章確認 XML 文件的簽名，並沒有改變。</span><span class="sxs-lookup"><span data-stu-id="88f98-108">This signature confirms that the XML document originated from the signer and has not been altered.</span></span> [!INCLUDE[btsInpathNoVersion](../../includes/btsinpathnoversion-md.md)]<span data-ttu-id="88f98-109"> 提供驗證、 為不可否定交易簽章、 部分簽署、 cosigning 和副署透過增強的數位簽章支援。</span><span class="sxs-lookup"><span data-stu-id="88f98-109"> provides verifiable, non-repudiable signing, partial signing, cosigning and countersigning through enhanced digital signature support.</span></span>  
  
 <span data-ttu-id="88f98-110">SWIFT [!INCLUDE[btsInpathNoVersion](../../includes/btsinpathnoversion-md.md)] A4SWIFT 所提供的 FormGenerator 公用程式產生的表單使用數位簽章的 countersigning 方法，讓彼此交互堆疊的 countersigners 的簽章。</span><span class="sxs-lookup"><span data-stu-id="88f98-110">The SWIFT [!INCLUDE[btsInpathNoVersion](../../includes/btsinpathnoversion-md.md)] forms generated with the FormGenerator utility provided by A4SWIFT use the countersigning method of digital signing to let signatures of countersigners to be stacked on top of each other.</span></span> <span data-ttu-id="88f98-111">此 countersigning 的簽章堆疊模型人力導向的程序建立或編輯 SWIFT 的訊息具有訊息由一或多個檢閱者和核准者檢閱並認可，最後將該訊息提交工作流程中的所有階段後才已。</span><span class="sxs-lookup"><span data-stu-id="88f98-111">This countersigning signature stack models the human-oriented process of creating or editing a SWIFT message, having the message reviewed and approved by one or more reviewers and approvers, and finally submitting that message only after all stages in a workflow have signed off.</span></span>  
  
 <span data-ttu-id="88f98-112">Repairers]、 [檢閱者] 或 [核准者登入的訊息，不論它們是否核准或拒絕它。</span><span class="sxs-lookup"><span data-stu-id="88f98-112">Repairers, reviewers, or approvers sign the message regardless of whether they approve or reject it.</span></span> <span data-ttu-id="88f98-113">簽章表示回應的真實性，並不一定表示 「 已接受 」 的決策。</span><span class="sxs-lookup"><span data-stu-id="88f98-113">The signature signifies authenticity of the response and does not necessarily signify an "accepted" decision.</span></span>  
  
 <span data-ttu-id="88f98-114">當[!INCLUDE[btsInpathNoVersion](../../includes/btsinpathnoversion-md.md)]送出表單，它會檢查訊息的有效性和簽章格式的使用者處於正確的角色。</span><span class="sxs-lookup"><span data-stu-id="88f98-114">When the [!INCLUDE[btsInpathNoVersion](../../includes/btsinpathnoversion-md.md)] form is submitted, it checks messages for validity and that the user signing the form is in the correct role.</span></span>  
  
 <span data-ttu-id="88f98-115">如果在任何階段 （除了修復） 工作流程中將會拒絕訊息，訊息會傳送回到修復階段。</span><span class="sxs-lookup"><span data-stu-id="88f98-115">If the message is rejected at any stage in a workflow (besides repair), the message is sent back to the repair stage.</span></span> <span data-ttu-id="88f98-116">如果在 repairer 或建立者階段，Message Repair 將會拒絕訊息和 New Submission 將訊息傳送回 Message Repair 和 New Submission 的協調流程執行個體具有將訊息標示為已拒絕的特定屬性。</span><span class="sxs-lookup"><span data-stu-id="88f98-116">If the message is rejected at the repairer or creator stage, Message Repair and New Submission sends the message back to the Message Repair and New Submission orchestration instance with specific properties marking the message as rejected.</span></span>  
  
 <span data-ttu-id="88f98-117">本章節描述如何在 Message Repair 和 New Submission 處理為角色定義的功能為基礎的數位簽章。</span><span class="sxs-lookup"><span data-stu-id="88f98-117">This section describes how Message Repair and New Submission handles the digital signatures based on the capabilities defined for a role.</span></span> <span data-ttu-id="88f98-118">工作流程中的角色與功能組合稱為 「 階段 」。</span><span class="sxs-lookup"><span data-stu-id="88f98-118">The role and capability combination is called a "stage" in the workflow.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="88f98-119">「 建立 」 角色是限制為單一的建立者跨所有部門。</span><span class="sxs-lookup"><span data-stu-id="88f98-119">The "create" role is limited to a single creator across all departments.</span></span>  
  
 <span data-ttu-id="88f98-120">此部分包含：</span><span class="sxs-lookup"><span data-stu-id="88f98-120">This section contains:</span></span>  
  
-   [<span data-ttu-id="88f98-121">建立和修復階段</span><span class="sxs-lookup"><span data-stu-id="88f98-121">Create and Repair Stages</span></span>](../../adapters-and-accelerators/accelerator-swift/creating-and-repairing-stages.md)  
  
-   [<span data-ttu-id="88f98-122">重設金鑰驗證階段</span><span class="sxs-lookup"><span data-stu-id="88f98-122">Rekey Verification Stage</span></span>](../../adapters-and-accelerators/accelerator-swift/rekey-verification-stage.md)  
  
-   [<span data-ttu-id="88f98-123">核准階段</span><span class="sxs-lookup"><span data-stu-id="88f98-123">Approval Stage</span></span>](../../adapters-and-accelerators/accelerator-swift/approval-stage.md)  
  
-   [<span data-ttu-id="88f98-124">散發數位憑證</span><span class="sxs-lookup"><span data-stu-id="88f98-124">Distributing Digital Certificates</span></span>](../../adapters-and-accelerators/accelerator-swift/distributing-digital-certificates.md)