---
title: "如何保護管線 |Microsoft 文件"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: ac3a717f-acf8-4f08-a6fb-6d1d48b5b80a
caps.latest.revision: "8"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 903e9faec81ce58aac243fb7a22bac6678a81a42
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/20/2017
---
# <a name="how-to-secure-pipelines"></a><span data-ttu-id="b6dc2-102">如何保護管線</span><span class="sxs-lookup"><span data-stu-id="b6dc2-102">How to Secure Pipelines</span></span>

## <a name="authentication-trusted"></a><span data-ttu-id="b6dc2-103">信任的驗證</span><span class="sxs-lookup"><span data-stu-id="b6dc2-103">Authentication trusted</span></span>
<span data-ttu-id="b6dc2-104">主機可以在管理主控台中標示**信任的驗證**。</span><span class="sxs-lookup"><span data-stu-id="b6dc2-104">Hosts can be marked in the administration console as **Authentication Trusted**.</span></span> <span data-ttu-id="b6dc2-105">將主控件標示為 [信任的驗證] 表示 Microsoft BizTalk Server 將會信任該主控件所傳送訊息內容的安全性相關屬性。</span><span class="sxs-lookup"><span data-stu-id="b6dc2-105">Denoting a host as Authentication Trusted means that the Microsoft BizTalk Server will trust the security-related properties sent on the message context of a message from that host.</span></span> <span data-ttu-id="b6dc2-106">在訊息內容 的安全性相關屬性**OriginatorPID**，對應於訊息內容屬性 BTS。SourcePartyID，而**OriginatorSID**，對應於訊息內容屬性**BTS。WindowsUser**。</span><span class="sxs-lookup"><span data-stu-id="b6dc2-106">The security-related properties on the message context are the **OriginatorPID**, which corresponds to the message context property BTS.SourcePartyID, and the **OriginatorSID**, which corresponds to the message context property **BTS.WindowsUser**.</span></span> <span data-ttu-id="b6dc2-107">如需詳細資訊，請參閱**訊息內容屬性** [!INCLUDE[ui-guidance-developers-reference](../includes/ui-guidance-developers-reference.md)]。</span><span class="sxs-lookup"><span data-stu-id="b6dc2-107">For more information, see **Message Context Properties** [!INCLUDE[ui-guidance-developers-reference](../includes/ui-guidance-developers-reference.md)].</span></span>  
  
 <span data-ttu-id="b6dc2-108">主控件標示為**驗證信任**允許指定的受信任的主機新增訊息至佇列本身以外的任何人為訊息的寄件者。</span><span class="sxs-lookup"><span data-stu-id="b6dc2-108">A host that is marked as **Authentication Trusted** is allowed to indicate that the trusted host is adding a message to the queue from someone other than itself as the sender of the message.</span></span> <span data-ttu-id="b6dc2-109">換句話說，主機未標示為**信任的驗證**不允許將訊息加入佇列，他自己以外的訊息寄件者。</span><span class="sxs-lookup"><span data-stu-id="b6dc2-109">In other words, hosts that are not marked as **Authentication Trusted** are not allowed to add a message to the queue from a message sender other than themselves.</span></span>  
  
> [!IMPORTANT]
>  <span data-ttu-id="b6dc2-110">MIME/SMIME 解碼器管線元件不會檢查解密憑證的到期日。</span><span class="sxs-lookup"><span data-stu-id="b6dc2-110">The MIME/SMIME Decoder pipeline component does not check the expiration date of decryption certificates.</span></span> <span data-ttu-id="b6dc2-111">然而，它會檢查簽章憑證的到期日。</span><span class="sxs-lookup"><span data-stu-id="b6dc2-111">However, it does check the expiration date of signing certificates.</span></span>  
  
 <span data-ttu-id="b6dc2-112">編碼和解碼訊息透過 SMTP 或 HTTP 的相關資訊，請參閱[MIME SMIME 編碼器管線元件](../core/mime-smime-encoder-pipeline-component.md)。</span><span class="sxs-lookup"><span data-stu-id="b6dc2-112">For information about encoding and decoding messages sent over SMTP or HTTP, see [MIME-SMIME Encoder Pipeline Component](../core/mime-smime-encoder-pipeline-component.md).</span></span> <span data-ttu-id="b6dc2-113">另請參閱[MIME SMIME 解碼器管線元件](../core/mime-smime-decoder-pipeline-component.md)。</span><span class="sxs-lookup"><span data-stu-id="b6dc2-113">Also see [MIME-SMIME Decoder Pipeline Component](../core/mime-smime-decoder-pipeline-component.md).</span></span>  
  
 <span data-ttu-id="b6dc2-114">如需處理協力廠商時的簽章驗證資訊，請參閱[合作對象解析管線元件](../core/party-resolution-pipeline-component.md)。</span><span class="sxs-lookup"><span data-stu-id="b6dc2-114">For information about signature verification when dealing with third parties, see [Party Resolution Pipeline Component](../core/party-resolution-pipeline-component.md).</span></span> <span data-ttu-id="b6dc2-115">另請參閱[如何建立協議](http://msdn.microsoft.com/library/f8608cf7-8ac5-4f02-805e-5a0bdf19ca8c)。</span><span class="sxs-lookup"><span data-stu-id="b6dc2-115">Also see [How to Create an Agreement](http://msdn.microsoft.com/library/f8608cf7-8ac5-4f02-805e-5a0bdf19ca8c).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="b6dc2-116">另請參閱</span><span class="sxs-lookup"><span data-stu-id="b6dc2-116">See Also</span></span>  
 <span data-ttu-id="b6dc2-117">[建立管線使用管線設計師](../core/creating-pipelines-using-pipeline-designer.md) </span><span class="sxs-lookup"><span data-stu-id="b6dc2-117">[Creating Pipelines Using Pipeline Designer](../core/creating-pipelines-using-pipeline-designer.md) </span></span>  
 [<span data-ttu-id="b6dc2-118">開發自訂管線元件</span><span class="sxs-lookup"><span data-stu-id="b6dc2-118">Developing Custom Pipeline Components</span></span>](../core/developing-custom-pipeline-components.md)