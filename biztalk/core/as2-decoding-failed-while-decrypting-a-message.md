---
title: 解密訊息時發生 AS2 解碼失敗 |Microsoft 文件
ms.custom: ''
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: ab6f7ecd-23cf-4f6f-8f63-acc6618dc544
caps.latest.revision: 10
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 72ef95ad35e1da933197bac11a9d80f98ddabd6a
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/20/2017
ms.locfileid: "22230462"
---
# <a name="as2-decoding-failed-while-decrypting-a-message"></a><span data-ttu-id="35034-102">解碼訊息時發生 AS2 解碼失敗</span><span class="sxs-lookup"><span data-stu-id="35034-102">AS2 decoding failed while decrypting a message</span></span>
## <a name="details"></a><span data-ttu-id="35034-103">詳細資料</span><span class="sxs-lookup"><span data-stu-id="35034-103">Details</span></span>  
  
|||  
|-|-|  
|<span data-ttu-id="35034-104">產品名稱</span><span class="sxs-lookup"><span data-stu-id="35034-104">Product Name</span></span>|[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]|  
|<span data-ttu-id="35034-105">產品版本</span><span class="sxs-lookup"><span data-stu-id="35034-105">Product Version</span></span>|[!INCLUDE[btsEDIVersion](../includes/btsediversion-md.md)]|  
|<span data-ttu-id="35034-106">事件識別碼</span><span class="sxs-lookup"><span data-stu-id="35034-106">Event ID</span></span>|-|  
|<span data-ttu-id="35034-107">事件來源</span><span class="sxs-lookup"><span data-stu-id="35034-107">Event Source</span></span>|[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]<span data-ttu-id="35034-108">EDI</span><span class="sxs-lookup"><span data-stu-id="35034-108"> EDI</span></span>|  
|<span data-ttu-id="35034-109">元件</span><span class="sxs-lookup"><span data-stu-id="35034-109">Component</span></span>|<span data-ttu-id="35034-110">AS2 引擎</span><span class="sxs-lookup"><span data-stu-id="35034-110">AS2 Engine</span></span>|  
|<span data-ttu-id="35034-111">符號名稱</span><span class="sxs-lookup"><span data-stu-id="35034-111">Symbolic Name</span></span>|-|  
|<span data-ttu-id="35034-112">訊息文字</span><span class="sxs-lookup"><span data-stu-id="35034-112">Message Text</span></span>|<span data-ttu-id="35034-113">解密訊息時發生 AS2 解碼失敗。</span><span class="sxs-lookup"><span data-stu-id="35034-113">AS2 decoding failed while decrypting a message.</span></span>|  
  
## <a name="explanation"></a><span data-ttu-id="35034-114">說明</span><span class="sxs-lookup"><span data-stu-id="35034-114">Explanation</span></span>  
 <span data-ttu-id="35034-115">這個錯誤/警告/資訊事件表示接收管線的 AS2 解碼器元件無法解密 AS2 訊息。</span><span class="sxs-lookup"><span data-stu-id="35034-115">This Error/Warning/Information event indicates that the AS2 Decoder component of the receive pipeline could not decrypt the AS2 message.</span></span> <span data-ttu-id="35034-116">如果解密程序中使用的憑證無效，不會儲存在適當的位置，或不符合加密程序中使用的憑證，也可能會發生。</span><span class="sxs-lookup"><span data-stu-id="35034-116">This can occur if the certificate used in the decryption process is not valid, is not stored in the appropriate location, or does not match the certificate used in the encryption process.</span></span>  
  
## <a name="user-action"></a><span data-ttu-id="35034-117">使用者動作</span><span class="sxs-lookup"><span data-stu-id="35034-117">User Action</span></span>  
 <span data-ttu-id="35034-118">若要解決這個錯誤，請執行下列一個或多個動作：</span><span class="sxs-lookup"><span data-stu-id="35034-118">To resolve this error, do one or more of the following:</span></span>  
  
-   <span data-ttu-id="35034-119">驗證 AS2 訊息中的加密包裝函式有效。</span><span class="sxs-lookup"><span data-stu-id="35034-119">Verify that the encryption wrapper in the AS2 message is valid.</span></span> <span data-ttu-id="35034-120">如果沒有，判斷為何訊息已編碼的編碼器的不正確。</span><span class="sxs-lookup"><span data-stu-id="35034-120">If not, determine why the message was encoded improperly by the encoder.</span></span>  
  
-   <span data-ttu-id="35034-121">確認加密程序中使用的公用金鑰和解密程序中使用的私用金鑰相符。</span><span class="sxs-lookup"><span data-stu-id="35034-121">Verify that the public key used in the encryption process and the private key used in the decryption process match.</span></span>  
  
-   <span data-ttu-id="35034-122">確認用來加密和解密的憑證的金鑰使用方法屬性設定為 「 資料編密。</span><span class="sxs-lookup"><span data-stu-id="35034-122">Verify that the Key Usage property of the certificate used for encryption and decryption is set to "data encipherment".</span></span>  
  
-   <span data-ttu-id="35034-123">請確認沒有中斷的鏈結的中繼憑證授權單位。</span><span class="sxs-lookup"><span data-stu-id="35034-123">Verify that there is not a broken chain of intermediate certificate authorities.</span></span> <span data-ttu-id="35034-124">如果沒有，請刪除舊的憑證，和建立並使用新的憑證。</span><span class="sxs-lookup"><span data-stu-id="35034-124">If there is, delete the old certificate, and create and use a new certificate.</span></span>  
  
-   <span data-ttu-id="35034-125">請確認該憑證尚未逾時藉由檢查到期日的憑證存放區 （使用 MMC 憑證嵌入式管理單元）.</span><span class="sxs-lookup"><span data-stu-id="35034-125">Verify that the certificate has not timed out by checking its expiration date in the Certificates store (using MMC with a certificates snap-in.).</span></span>  
  
-   <span data-ttu-id="35034-126">請確認該憑證尚未被撤銷檢查憑證撤銷清單。</span><span class="sxs-lookup"><span data-stu-id="35034-126">Verify that the certificate has not been revoked by checking the Certification Revocation List.</span></span> <span data-ttu-id="35034-127">(您可以在 [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] 管理主控台中勾選 [一般 AS2] 屬性的 [檢查憑證撤銷清單] 屬性，讓 BizTalk Server 自動檢查此項目)。</span><span class="sxs-lookup"><span data-stu-id="35034-127">(You can have BizTalk Server check this automatically by checking the Check Certification Revocation List property in the General AS2 properties in the [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] Administration Console.)</span></span>  
  
-   <span data-ttu-id="35034-128">確認用來解密憑證會儲存在目前使用者 \ 個人存放區的每一部 BizTalk 伺服器裝載 MIME/SMIME 解碼器管線的每個主控件執行個體服務帳戶。</span><span class="sxs-lookup"><span data-stu-id="35034-128">Verify that the certificate used for decryption is stored in the Current User\Personal store of each BizTalk server that hosts a MIME/SMIME decoder pipeline as each host instance service account.</span></span>