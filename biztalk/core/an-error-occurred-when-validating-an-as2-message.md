---
title: 驗證 AS2 訊息時發生錯誤 |Microsoft 文件
ms.custom: ''
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 0cf97c63-2bff-4474-9cd8-f68634493dcc
caps.latest.revision: 10
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 73f1c9b7cf4e444e256aadc3ade717fcf30735bd
ms.sourcegitcommit: 36350889f318e1f7e0ac9506dc8df794d475bda6
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/20/2018
ms.locfileid: "22230214"
---
# <a name="an-error-occurred-when-validating-an-as2-message"></a><span data-ttu-id="418eb-102">驗證 AS2 訊息時發生錯誤</span><span class="sxs-lookup"><span data-stu-id="418eb-102">An error occurred when validating an AS2 message</span></span>
## <a name="details"></a><span data-ttu-id="418eb-103">詳細資料</span><span class="sxs-lookup"><span data-stu-id="418eb-103">Details</span></span>  
  
|||  
|-|-|  
|<span data-ttu-id="418eb-104">제품 이름</span><span class="sxs-lookup"><span data-stu-id="418eb-104">Product Name</span></span>|[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]|  
|<span data-ttu-id="418eb-105">제품 버전</span><span class="sxs-lookup"><span data-stu-id="418eb-105">Product Version</span></span>|[!INCLUDE[btsEDIVersion](../includes/btsediversion-md.md)]|  
|<span data-ttu-id="418eb-106">이벤트 ID</span><span class="sxs-lookup"><span data-stu-id="418eb-106">Event ID</span></span>|-|  
|<span data-ttu-id="418eb-107">이벤트 원본</span><span class="sxs-lookup"><span data-stu-id="418eb-107">Event Source</span></span>|[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]<span data-ttu-id="418eb-108"> EDI</span><span class="sxs-lookup"><span data-stu-id="418eb-108"> EDI</span></span>|  
|<span data-ttu-id="418eb-109">元件</span><span class="sxs-lookup"><span data-stu-id="418eb-109">Component</span></span>|<span data-ttu-id="418eb-110">AS2 引擎</span><span class="sxs-lookup"><span data-stu-id="418eb-110">AS2 Engine</span></span>|  
|<span data-ttu-id="418eb-111">符號名稱</span><span class="sxs-lookup"><span data-stu-id="418eb-111">Symbolic Name</span></span>|-|  
|<span data-ttu-id="418eb-112">訊息文字</span><span class="sxs-lookup"><span data-stu-id="418eb-112">Message Text</span></span>|<span data-ttu-id="418eb-113">驗證 AS2 訊息時發生錯誤。</span><span class="sxs-lookup"><span data-stu-id="418eb-113">An error occurred when validating an AS2 message.</span></span> <span data-ttu-id="418eb-114">請確定所用的憑證尚未逾時或遭到撤銷。</span><span class="sxs-lookup"><span data-stu-id="418eb-114">Make sure the certificates used have not timed out or been revoked.</span></span>|  
  
## <a name="explanation"></a><span data-ttu-id="418eb-115">說明</span><span class="sxs-lookup"><span data-stu-id="418eb-115">Explanation</span></span>  
 <span data-ttu-id="418eb-116">這個錯誤/警告/資訊事件表示，AS2 接收管線或 AS2 傳送管線無法驗證 AS2 訊息。</span><span class="sxs-lookup"><span data-stu-id="418eb-116">This Error/Warning/Information event indicates that the AS2 receive pipeline or the AS2 send pipeline could not validate the AS2 message.</span></span> <span data-ttu-id="418eb-117">當用於簽章驗證程序的憑證無效、未存放在適當的位置，或和用於簽署程序的憑證不符時，此錯誤便可能會發生。</span><span class="sxs-lookup"><span data-stu-id="418eb-117">This can occur if the certificate used in the signature verification process is not valid, is not stored in the appropriate location, or does not match the certificate used in the signing process.</span></span>  
  
## <a name="user-action"></a><span data-ttu-id="418eb-118">使用者動作</span><span class="sxs-lookup"><span data-stu-id="418eb-118">User Action</span></span>  
 <span data-ttu-id="418eb-119">若要解決這個錯誤，請執行下列一個或多個動作：</span><span class="sxs-lookup"><span data-stu-id="418eb-119">To resolve this error, do one or more of the following:</span></span>  
  
-   <span data-ttu-id="418eb-120">確認 AS2 訊息中的簽章包裝函式是有效的。</span><span class="sxs-lookup"><span data-stu-id="418eb-120">Verify that the signature wrapper in the AS2 message is valid.</span></span> <span data-ttu-id="418eb-121">如果是無效的，請判定編碼器無法正確簽署訊息的原因。</span><span class="sxs-lookup"><span data-stu-id="418eb-121">If not, determine why the message was signed improperly by the encoder.</span></span>  
  
-   <span data-ttu-id="418eb-122">確認用於簽署程序的私密金鑰和用於簽章驗證程序的公開金鑰是相符的。</span><span class="sxs-lookup"><span data-stu-id="418eb-122">Verify that the private key used in the signing process and the public key used in the signature verification process match.</span></span>  
  
-   <span data-ttu-id="418eb-123">確認用於簽署和簽章驗證之憑證的 [金鑰使用方式] 屬性已設為 [資料編密]。</span><span class="sxs-lookup"><span data-stu-id="418eb-123">Verify that the Key Usage property of the certificate used for signing and signature verification is set to "data encipherment".</span></span>  
  
-   <span data-ttu-id="418eb-124">請確認沒有中斷的鏈結的中繼憑證授權單位。</span><span class="sxs-lookup"><span data-stu-id="418eb-124">Verify that there is not a broken chain of intermediate certificate authorities.</span></span> <span data-ttu-id="418eb-125">如果沒有，請刪除舊的憑證，以及建立並使用新的憑證。</span><span class="sxs-lookup"><span data-stu-id="418eb-125">If there is, delete the old certificate, and create and use a new certificate.</span></span>  
  
-   <span data-ttu-id="418eb-126">請確認該憑證尚未逾時藉由檢查到期日的憑證存放區 （使用 MMC 憑證嵌入式管理單元）.</span><span class="sxs-lookup"><span data-stu-id="418eb-126">Verify that the certificate has not timed out by checking its expiration date in the Certificates store (using MMC with a certificates snap-in.).</span></span>  
  
-   <span data-ttu-id="418eb-127">確認憑證藉由檢查憑證撤銷清單中未被撤銷。</span><span class="sxs-lookup"><span data-stu-id="418eb-127">Verify that the certificate has not been revoked by checking the Certification Revocation List.</span></span> <span data-ttu-id="418eb-128">(您可以在 [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] 管理主控台中勾選 [一般 AS2] 屬性的 [檢查憑證撤銷清單] 屬性，讓 BizTalk Server 自動檢查此項目)。</span><span class="sxs-lookup"><span data-stu-id="418eb-128">(You can have BizTalk Server check this automatically by checking the Check Certification Revocation List property in the General AS2 properties in the [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] Administration Console.)</span></span>  
  
-   <span data-ttu-id="418eb-129">確認用於簽章驗證的憑證儲存在本機電腦/其他人存放區的每個 BizTalk 伺服器裝載 MIME/SMIME 解碼器管線的每個主控件執行個體服務帳戶。</span><span class="sxs-lookup"><span data-stu-id="418eb-129">Verify that the certificate used for signature verification is stored in the Local computer/Other People store of each BizTalk server that hosts a MIME/SMIME decoder pipeline as each host instance service account.</span></span>