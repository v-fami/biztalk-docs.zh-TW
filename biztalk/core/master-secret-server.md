---
title: 主要密碼伺服器 |Microsoft 文件
ms.custom: ''
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- Master Secret server, about Master Secret server
- Master Secret server, SSO
- SSO, encryption key
- Master Secret server, encryption key
- SSO, Master Secret server
ms.assetid: 93685a19-6c27-45db-bfc1-957574362687
caps.latest.revision: 8
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 6d02d5608546e86801bfc4a2281c42f902594e79
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/20/2017
ms.locfileid: "22262510"
---
# <a name="master-secret-server"></a><span data-ttu-id="878bb-102">主要密碼伺服器</span><span class="sxs-lookup"><span data-stu-id="878bb-102">Master Secret Server</span></span>
<span data-ttu-id="878bb-103">主要密碼伺服器是儲存主要密碼 (加密金鑰) 的企業單一登入 (SSO) 伺服器。</span><span class="sxs-lookup"><span data-stu-id="878bb-103">The master secret server is the Enterprise Single Sign-On (SSO) server that stores the master secret (encryption key).</span></span> <span data-ttu-id="878bb-104">主要密碼伺服器會於 SSO 系統管理員要求時產生主要密碼。</span><span class="sxs-lookup"><span data-stu-id="878bb-104">The master secret server generates the master secret when an SSO administrator requests it.</span></span> <span data-ttu-id="878bb-105">而且主要密碼伺服器會將加密的主要密碼儲存在登錄中。</span><span class="sxs-lookup"><span data-stu-id="878bb-105">The master secret server stores the encrypted master secret in the registry.</span></span> <span data-ttu-id="878bb-106">只有「單一登入」系統管理員可以存取主要密碼。</span><span class="sxs-lookup"><span data-stu-id="878bb-106">Only Single Sign-On administrators can access the master secret.</span></span>  
  
 <span data-ttu-id="878bb-107">其他的單一登入伺服器會每隔 30 秒查看主要密碼是否有變更。</span><span class="sxs-lookup"><span data-stu-id="878bb-107">The other Single Sign-On servers check every 30 seconds to see whether the master secret has changed.</span></span> <span data-ttu-id="878bb-108">若它已變更，伺服器就會以安全的方式讀取它，否則會繼續使用已快取於記憶體中的主要密碼。</span><span class="sxs-lookup"><span data-stu-id="878bb-108">If it has changed, they read it securely; otherwise, they continue to use the master secret they already have cached in memory.</span></span> <span data-ttu-id="878bb-109">SSO 服務會使用主要密碼，來加密和解密使用者認證。</span><span class="sxs-lookup"><span data-stu-id="878bb-109">The SSO service uses the master secret to encrypt and decrypt the user credentials.</span></span>  
  
 <span data-ttu-id="878bb-110">除非 SSO 系統管理員設定主要密碼伺服器並產生主要密碼，否則您將無法使用 SSO 系統。</span><span class="sxs-lookup"><span data-stu-id="878bb-110">You cannot use the SSO system until an SSO administrator configures the master secret server and generates the master secret.</span></span> <span data-ttu-id="878bb-111">主要密碼伺服器會在設定組態期間產生主要密碼。</span><span class="sxs-lookup"><span data-stu-id="878bb-111">The master secret server generates the master secret during configuration.</span></span> <span data-ttu-id="878bb-112">只有 SSO 系統管理員可以產生主要密碼。</span><span class="sxs-lookup"><span data-stu-id="878bb-112">Only SSO administrators can generate the master secret.</span></span> <span data-ttu-id="878bb-113">SSO 系統管理員必須設定主要密碼伺服器及 SSO 資料庫，應用程式才可以使用 SSO 服務。</span><span class="sxs-lookup"><span data-stu-id="878bb-113">An SSO administrator must configure the master secret server and the SSO database before an application can use the SSO service.</span></span>  
  
> [!IMPORTANT]
>  <span data-ttu-id="878bb-114">在您產生主要密碼之後，強烈建議您備份它，並將它儲存在安全的位置。</span><span class="sxs-lookup"><span data-stu-id="878bb-114">After you generate the master secret, it is strongly recommended that you back it up and store it in a secure location.</span></span>  
  
 <span data-ttu-id="878bb-115">當 SSO 系統管理員需要重新產生主要密碼時 (例如，若 SSO 系統管理員想要定期變更主要密碼)，主要密碼伺服器會同時儲存舊的與新的主要密碼。</span><span class="sxs-lookup"><span data-stu-id="878bb-115">When an SSO administrator needs to regenerate the master secret, for example, if the SSO administrator wants to change the master secret periodically, the master secret server stores both the old and new master secret.</span></span> <span data-ttu-id="878bb-116">主要密碼伺服器接著會查看所有的對應、使用舊的主要密碼將之解密，並使用新的主要密碼再次將它們加密。</span><span class="sxs-lookup"><span data-stu-id="878bb-116">The master secret server then goes through all the mappings, decrypts them using the old master secret, and encrypts them again using the new master secret.</span></span>  
  
 <span data-ttu-id="878bb-117">若主要密碼伺服器失敗，所有已經在執行的執行階段作業都將繼續執行，但是 SSO 伺服器將無法加密新認證。</span><span class="sxs-lookup"><span data-stu-id="878bb-117">If the master secret server fails, all runtime operations already running will continue to run, but SSO servers will not be able to encrypt new credentials.</span></span>  
  
> [!IMPORTANT]
>  <span data-ttu-id="878bb-118">SSO 系統中只能有一台主要密碼伺服器。</span><span class="sxs-lookup"><span data-stu-id="878bb-118">There can be only one master secret server in your SSO system.</span></span> <span data-ttu-id="878bb-119">因此，強烈建議您建立主要密碼伺服器叢集。</span><span class="sxs-lookup"><span data-stu-id="878bb-119">Therefore, it is strongly recommended you cluster the master secret server.</span></span> <span data-ttu-id="878bb-120">如需詳細資訊，請參閱[如何叢集化主要密碼伺服器](../core/how-to-cluster-the-master-secret-server1.md)。</span><span class="sxs-lookup"><span data-stu-id="878bb-120">For more information, see [How to Cluster the Master Secret Server](../core/how-to-cluster-the-master-secret-server1.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="878bb-121">另請參閱</span><span class="sxs-lookup"><span data-stu-id="878bb-121">See Also</span></span>  
 [<span data-ttu-id="878bb-122">使用 SSO</span><span class="sxs-lookup"><span data-stu-id="878bb-122">Using SSO</span></span>](../core/using-sso.md)