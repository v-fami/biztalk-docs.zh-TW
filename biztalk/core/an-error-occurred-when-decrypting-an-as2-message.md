---
title: 解密 AS2 訊息時，發生錯誤 |Microsoft 文件
ms.custom: ''
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 0bfb1d2a-c79d-4541-8a6d-bab0986f456b
caps.latest.revision: 12
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 183933ae48468569cdd89f1d051f4bf961c71e05
ms.sourcegitcommit: 36350889f318e1f7e0ac9506dc8df794d475bda6
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/20/2018
ms.locfileid: "22230182"
---
# <a name="an-error-occurred-when-decrypting-an-as2-message"></a><span data-ttu-id="2538b-102">解密 AS2 訊息時發生錯誤</span><span class="sxs-lookup"><span data-stu-id="2538b-102">An error occurred when decrypting an AS2 message</span></span>
## <a name="details"></a><span data-ttu-id="2538b-103">詳細資料</span><span class="sxs-lookup"><span data-stu-id="2538b-103">Details</span></span>  
  
|||  
|-|-|  
|<span data-ttu-id="2538b-104">제품 이름</span><span class="sxs-lookup"><span data-stu-id="2538b-104">Product Name</span></span>|[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]|  
|<span data-ttu-id="2538b-105">제품 버전</span><span class="sxs-lookup"><span data-stu-id="2538b-105">Product Version</span></span>|[!INCLUDE[btsEDIVersion](../includes/btsediversion-md.md)]|  
|<span data-ttu-id="2538b-106">이벤트 ID</span><span class="sxs-lookup"><span data-stu-id="2538b-106">Event ID</span></span>|-|  
|<span data-ttu-id="2538b-107">이벤트 원본</span><span class="sxs-lookup"><span data-stu-id="2538b-107">Event Source</span></span>|[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]<span data-ttu-id="2538b-108"> EDI</span><span class="sxs-lookup"><span data-stu-id="2538b-108"> EDI</span></span>|  
|<span data-ttu-id="2538b-109">元件</span><span class="sxs-lookup"><span data-stu-id="2538b-109">Component</span></span>|<span data-ttu-id="2538b-110">AS2 引擎</span><span class="sxs-lookup"><span data-stu-id="2538b-110">AS2 Engine</span></span>|  
|<span data-ttu-id="2538b-111">符號名稱</span><span class="sxs-lookup"><span data-stu-id="2538b-111">Symbolic Name</span></span>|-|  
|<span data-ttu-id="2538b-112">訊息文字</span><span class="sxs-lookup"><span data-stu-id="2538b-112">Message Text</span></span>|<span data-ttu-id="2538b-113">解密 AS2 訊息時發生錯誤。</span><span class="sxs-lookup"><span data-stu-id="2538b-113">An error occurred when decrypting an AS2 message.</span></span>|  
  
## <a name="explanation"></a><span data-ttu-id="2538b-114">說明</span><span class="sxs-lookup"><span data-stu-id="2538b-114">Explanation</span></span>  
 <span data-ttu-id="2538b-115">這個錯誤/警告/資訊事件表示接收管線的 AS2 解碼器元件無法解密 AS2 訊息。</span><span class="sxs-lookup"><span data-stu-id="2538b-115">This Error/Warning/Information event indicates that the AS2 Decoder component of the receive pipeline could not decrypt the AS2 message.</span></span> <span data-ttu-id="2538b-116">如果解密程序中使用的憑證無效，不會儲存在適當的位置，或不符合加密程序中使用的憑證，也可能會發生。</span><span class="sxs-lookup"><span data-stu-id="2538b-116">This can occur if the certificate used in the decryption process is not valid, is not stored in the appropriate location, or does not match the certificate used in the encryption process.</span></span>  
  
## <a name="user-action"></a><span data-ttu-id="2538b-117">使用者動作</span><span class="sxs-lookup"><span data-stu-id="2538b-117">User Action</span></span>  
 <span data-ttu-id="2538b-118">若要解決這個錯誤，請執行下列一個或多個動作：</span><span class="sxs-lookup"><span data-stu-id="2538b-118">To resolve this error, do one or more of the following:</span></span>  
  
-   <span data-ttu-id="2538b-119">確認 AS2 訊息中的加密包裝函式有效。</span><span class="sxs-lookup"><span data-stu-id="2538b-119">Verify that the encryption wrapper in the AS2 message is valid.</span></span> <span data-ttu-id="2538b-120">如果沒有，判斷為什麼訊息編碼不正確編碼器。</span><span class="sxs-lookup"><span data-stu-id="2538b-120">If not, determine why the message was encoded improperly by the encoder.</span></span>  
  
-   <span data-ttu-id="2538b-121">確認加密程序中使用的公開金鑰和私密金鑰解密程序中使用相符。</span><span class="sxs-lookup"><span data-stu-id="2538b-121">Verify that the public key used in the encryption process and the private key used in the decryption process match.</span></span>  
  
-   <span data-ttu-id="2538b-122">確認用來加密和解密憑證的金鑰使用方法屬性設為 「 資料加密 」。</span><span class="sxs-lookup"><span data-stu-id="2538b-122">Verify that the Key Usage property of the certificate used for encryption and decryption is set to "data encipherment".</span></span>  
  
-   <span data-ttu-id="2538b-123">請確認沒有中斷的鏈結的中繼憑證授權單位。</span><span class="sxs-lookup"><span data-stu-id="2538b-123">Verify that there is not a broken chain of intermediate certificate authorities.</span></span> <span data-ttu-id="2538b-124">如果沒有，請刪除舊的憑證，以及建立並使用新的憑證。</span><span class="sxs-lookup"><span data-stu-id="2538b-124">If there is, delete the old certificate, and create and use a new certificate.</span></span>  
  
-   <span data-ttu-id="2538b-125">請確認該憑證尚未逾時藉由檢查到期日的憑證存放區 （使用 MMC 憑證嵌入式管理單元）.</span><span class="sxs-lookup"><span data-stu-id="2538b-125">Verify that the certificate has not timed out by checking its expiration date in the Certificates store (using MMC with a certificates snap-in.).</span></span>  
  
-   <span data-ttu-id="2538b-126">確認憑證藉由檢查憑證撤銷清單中未被撤銷。</span><span class="sxs-lookup"><span data-stu-id="2538b-126">Verify that the certificate has not been revoked by checking the Certification Revocation List.</span></span> <span data-ttu-id="2538b-127">(您可以藉由檢查憑證撤銷清單中的屬性中的一般 AS2 屬性自動檢查此 BizTalk Server[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]管理主控台。)</span><span class="sxs-lookup"><span data-stu-id="2538b-127">(You can have BizTalk Server check this automatically by checking the Check Certification Revocation List property in the General AS2 properties in the [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] Administration console.)</span></span>  
  
-   <span data-ttu-id="2538b-128">確認用來解密憑證會儲存在目前使用者 \ 個人存放區的每個 BizTalk 伺服器裝載 MIME/SMIME 解碼器管線的每個主控件執行個體服務帳戶。</span><span class="sxs-lookup"><span data-stu-id="2538b-128">Verify that the certificate used for decryption is stored in the Current User\Personal store of each BizTalk server that hosts a MIME/SMIME decoder pipeline as each host instance service account.</span></span>