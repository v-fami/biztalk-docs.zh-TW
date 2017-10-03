---
title: "用來解密訊息的憑證已被撤銷 |Microsoft 文件"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 01767cb2-b16e-4b4b-ac4d-cd79b6c8860a
caps.latest.revision: "9"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 7cd9404f13f737b4cb82317193344e006979d333
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/20/2017
---
# <a name="the-certificate-used-to-decrypt-a-message-has-been-revoked"></a><span data-ttu-id="ab5dc-102">用來解密訊息的憑證已被撤銷。</span><span class="sxs-lookup"><span data-stu-id="ab5dc-102">The certificate used to decrypt a message has been revoked</span></span>
## <a name="details"></a><span data-ttu-id="ab5dc-103">詳細資料</span><span class="sxs-lookup"><span data-stu-id="ab5dc-103">Details</span></span>  
  
|||  
|-|-|  
|<span data-ttu-id="ab5dc-104">產品名稱</span><span class="sxs-lookup"><span data-stu-id="ab5dc-104">Product Name</span></span>|[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]|  
|<span data-ttu-id="ab5dc-105">產品版本</span><span class="sxs-lookup"><span data-stu-id="ab5dc-105">Product Version</span></span>|[!INCLUDE[btsEDIVersion](../includes/btsediversion-md.md)]|  
|<span data-ttu-id="ab5dc-106">事件識別碼</span><span class="sxs-lookup"><span data-stu-id="ab5dc-106">Event ID</span></span>|-|  
|<span data-ttu-id="ab5dc-107">事件來源</span><span class="sxs-lookup"><span data-stu-id="ab5dc-107">Event Source</span></span>|[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]<span data-ttu-id="ab5dc-108">EDI</span><span class="sxs-lookup"><span data-stu-id="ab5dc-108"> EDI</span></span>|  
|<span data-ttu-id="ab5dc-109">元件</span><span class="sxs-lookup"><span data-stu-id="ab5dc-109">Component</span></span>|<span data-ttu-id="ab5dc-110">AS2 引擎</span><span class="sxs-lookup"><span data-stu-id="ab5dc-110">AS2 Engine</span></span>|  
|<span data-ttu-id="ab5dc-111">符號名稱</span><span class="sxs-lookup"><span data-stu-id="ab5dc-111">Symbolic Name</span></span>|<span data-ttu-id="ab5dc-112">DecryptionCertificateHasBeenRevokedError</span><span class="sxs-lookup"><span data-stu-id="ab5dc-112">DecryptionCertificateHasBeenRevokedError</span></span>|  
|<span data-ttu-id="ab5dc-113">訊息文字</span><span class="sxs-lookup"><span data-stu-id="ab5dc-113">Message Text</span></span>|<span data-ttu-id="ab5dc-114">用於解密訊息的憑證已遭到撤銷。</span><span class="sxs-lookup"><span data-stu-id="ab5dc-114">The certificate used to decrypt a message has been revoked.</span></span> <span data-ttu-id="ab5dc-115">憑證指紋: {0}</span><span class="sxs-lookup"><span data-stu-id="ab5dc-115">Certificate thumbprint: {0}</span></span>|  
  
## <a name="explanation"></a><span data-ttu-id="ab5dc-116">說明</span><span class="sxs-lookup"><span data-stu-id="ab5dc-116">Explanation</span></span>  
 <span data-ttu-id="ab5dc-117">這個錯誤/警告/資訊事件表示，接收管線無法處理內送訊息因為用來將訊息解密憑證已遭到撤銷。</span><span class="sxs-lookup"><span data-stu-id="ab5dc-117">This Error/Warning/Information event indicates that the receive pipeline could not process the incoming message because the certificate to be used to decrypt the message has been revoked.</span></span>  
  
## <a name="user-action"></a><span data-ttu-id="ab5dc-118">使用者動作</span><span class="sxs-lookup"><span data-stu-id="ab5dc-118">User Action</span></span>  
 <span data-ttu-id="ab5dc-119">若要解決這個錯誤，執行下列其中一項：</span><span class="sxs-lookup"><span data-stu-id="ab5dc-119">To resolve this error, do one of the following:</span></span>  
  
-   <span data-ttu-id="ab5dc-120">建立新的憑證來取代已撤銷的憑證。</span><span class="sxs-lookup"><span data-stu-id="ab5dc-120">Create a new certificate to replace the revoked certificate.</span></span> <span data-ttu-id="ab5dc-121">將憑證新增至目前的使用者/個人憑證存放區，然後將憑證的公開金鑰傳送給傳送 AS2 訊息。</span><span class="sxs-lookup"><span data-stu-id="ab5dc-121">Add the certificate to the Current User/Personal certificate store, and then send the public key of the certificate to the sending of the AS2 message.</span></span>  
  
-   <span data-ttu-id="ab5dc-122">停用的撤銷清單檢查藉由開啟 BizTalk Server 管理主控台，開啟 AS2 屬性 對話方塊的合作對象解析外寄訊息，按一下 一般 節點，然後清除 檢查憑證撤銷清單屬性。</span><span class="sxs-lookup"><span data-stu-id="ab5dc-122">Disable the revocation list check by opening the BizTalk Server Administration Console, opening the AS2 Properties dialog box for the party resolved for the outgoing message, clicking the General node, and then clearing the Check Certification Revocation List property.</span></span>