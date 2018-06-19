---
title: 用來加密訊息的憑證已被撤銷 |Microsoft 文件
ms.custom: ''
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 76c90690-002a-43bc-85f2-8aa5e7511ffa
caps.latest.revision: 9
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 4fbe34dcd2906d79a8d80ebdd00c3d9f293e6559
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/20/2017
ms.locfileid: "22279606"
---
# <a name="the-certificate-used-to-encrypt-a-message-has-been-revoked"></a><span data-ttu-id="1f7f0-102">用來加密訊息的憑證已被撤銷。</span><span class="sxs-lookup"><span data-stu-id="1f7f0-102">The certificate used to encrypt a message has been revoked</span></span>
## <a name="details"></a><span data-ttu-id="1f7f0-103">詳細資料</span><span class="sxs-lookup"><span data-stu-id="1f7f0-103">Details</span></span>  
  
|||  
|-|-|  
|<span data-ttu-id="1f7f0-104">產品名稱</span><span class="sxs-lookup"><span data-stu-id="1f7f0-104">Product Name</span></span>|[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]|  
|<span data-ttu-id="1f7f0-105">產品版本</span><span class="sxs-lookup"><span data-stu-id="1f7f0-105">Product Version</span></span>|[!INCLUDE[btsEDIVersion](../includes/btsediversion-md.md)]|  
|<span data-ttu-id="1f7f0-106">事件識別碼</span><span class="sxs-lookup"><span data-stu-id="1f7f0-106">Event ID</span></span>|-|  
|<span data-ttu-id="1f7f0-107">事件來源</span><span class="sxs-lookup"><span data-stu-id="1f7f0-107">Event Source</span></span>|[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]<span data-ttu-id="1f7f0-108">EDI</span><span class="sxs-lookup"><span data-stu-id="1f7f0-108"> EDI</span></span>|  
|<span data-ttu-id="1f7f0-109">元件</span><span class="sxs-lookup"><span data-stu-id="1f7f0-109">Component</span></span>|<span data-ttu-id="1f7f0-110">AS2 引擎</span><span class="sxs-lookup"><span data-stu-id="1f7f0-110">AS2 Engine</span></span>|  
|<span data-ttu-id="1f7f0-111">符號名稱</span><span class="sxs-lookup"><span data-stu-id="1f7f0-111">Symbolic Name</span></span>|<span data-ttu-id="1f7f0-112">EncryptionCertificateHasBeenRevokedError</span><span class="sxs-lookup"><span data-stu-id="1f7f0-112">EncryptionCertificateHasBeenRevokedError</span></span>|  
|<span data-ttu-id="1f7f0-113">訊息文字</span><span class="sxs-lookup"><span data-stu-id="1f7f0-113">Message Text</span></span>|<span data-ttu-id="1f7f0-114">用於加密訊息的憑證已遭到撤銷。</span><span class="sxs-lookup"><span data-stu-id="1f7f0-114">The certificate used to encrypt a message has been revoked.</span></span> <span data-ttu-id="1f7f0-115">憑證指紋: {0}</span><span class="sxs-lookup"><span data-stu-id="1f7f0-115">Certificate thumbprint: {0}</span></span>|  
  
## <a name="explanation"></a><span data-ttu-id="1f7f0-116">說明</span><span class="sxs-lookup"><span data-stu-id="1f7f0-116">Explanation</span></span>  
 <span data-ttu-id="1f7f0-117">這個錯誤/警告/資訊事件表示，傳送管線無法處理外寄訊息因為識別做為加密憑證的憑證已被撤銷。</span><span class="sxs-lookup"><span data-stu-id="1f7f0-117">This Error/Warning/Information event indicates that the send pipeline could not process the outgoing message because the certificate identified as the encryption certificate has been revoked.</span></span>  
  
## <a name="user-action"></a><span data-ttu-id="1f7f0-118">使用者動作</span><span class="sxs-lookup"><span data-stu-id="1f7f0-118">User Action</span></span>  
 <span data-ttu-id="1f7f0-119">若要解決這個錯誤，執行下列其中一項：</span><span class="sxs-lookup"><span data-stu-id="1f7f0-119">To resolve this error, do one of the following:</span></span>  
  
-   <span data-ttu-id="1f7f0-120">有訊息的接收者，建立新的憑證，並將公開金鑰傳送給您。</span><span class="sxs-lookup"><span data-stu-id="1f7f0-120">Have the receiver of the message create a new certificate and send the public key to you.</span></span> <span data-ttu-id="1f7f0-121">將憑證新增至本機電腦 \ 其他人憑證存放區，然後識別做為傳送埠屬性 對話方塊的 憑證 頁面中的加密憑證的憑證。</span><span class="sxs-lookup"><span data-stu-id="1f7f0-121">Add the certificate to the Local computer\Other People certificate store, and then identify the certificate as the encryption certificate in the Certificate page of the Send Port Properties dialog box.</span></span>  
  
-   <span data-ttu-id="1f7f0-122">停用的撤銷清單檢查藉由開啟 BizTalk Server 管理主控台，開啟 AS2 屬性 對話方塊的合作對象解析外寄訊息，按一下 一般 節點，然後清除 檢查憑證撤銷清單屬性。</span><span class="sxs-lookup"><span data-stu-id="1f7f0-122">Disable the revocation list check by opening the BizTalk Server Administration Console, opening the AS2 Properties dialog box for the party resolved for the outgoing message, clicking the General node, and then clearing the Check Certification Revocation List property.</span></span>