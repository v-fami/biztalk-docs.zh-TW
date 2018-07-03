---
title: 單一登入： 事件 10547 |Microsoft Docs
ms.custom: ''
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: be25cdc9-d6c1-488d-9ead-877a2454c3d1
caps.latest.revision: 13
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 1af15d6a6259142d243738ab83cabe3e0c63e9c6
ms.sourcegitcommit: 266308ec5c6a9d8d80ff298ee6051b4843c5d626
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/27/2018
ms.locfileid: "37010943"
---
# <a name="single-sign-on-event-10547"></a><span data-ttu-id="4fcfb-102">單一登入： 事件 10547</span><span class="sxs-lookup"><span data-stu-id="4fcfb-102">Single Sign-On: Event 10547</span></span>
## <a name="details"></a><span data-ttu-id="4fcfb-103">詳細資料</span><span class="sxs-lookup"><span data-stu-id="4fcfb-103">Details</span></span>  

|                 |                                                                           |
|-----------------|---------------------------------------------------------------------------|
|  <span data-ttu-id="4fcfb-104">產品名稱</span><span class="sxs-lookup"><span data-stu-id="4fcfb-104">Product Name</span></span>   |                         <span data-ttu-id="4fcfb-105">企業單一登入</span><span class="sxs-lookup"><span data-stu-id="4fcfb-105">Enterprise Single Sign-On</span></span>                         |
| <span data-ttu-id="4fcfb-106">產品版本</span><span class="sxs-lookup"><span data-stu-id="4fcfb-106">Product Version</span></span> |        [!INCLUDE[btsSSOVersion](../includes/btsssoversion-md.md)]         |
|    <span data-ttu-id="4fcfb-107">事件識別碼</span><span class="sxs-lookup"><span data-stu-id="4fcfb-107">Event ID</span></span>     |                                   <span data-ttu-id="4fcfb-108">10547</span><span class="sxs-lookup"><span data-stu-id="4fcfb-108">10547</span></span>                                   |
|  <span data-ttu-id="4fcfb-109">事件來源</span><span class="sxs-lookup"><span data-stu-id="4fcfb-109">Event Source</span></span>   |                                  <span data-ttu-id="4fcfb-110">ENTSSO</span><span class="sxs-lookup"><span data-stu-id="4fcfb-110">ENTSSO</span></span>                                   |
|    <span data-ttu-id="4fcfb-111">元件</span><span class="sxs-lookup"><span data-stu-id="4fcfb-111">Component</span></span>    |                                    <span data-ttu-id="4fcfb-112">CO</span><span class="sxs-lookup"><span data-stu-id="4fcfb-112">CO</span></span>                                     |
|  <span data-ttu-id="4fcfb-113">符號名稱</span><span class="sxs-lookup"><span data-stu-id="4fcfb-113">Symbolic Name</span></span>  |                          <span data-ttu-id="4fcfb-114">SSO_WARN_UPDATE_FAILED</span><span class="sxs-lookup"><span data-stu-id="4fcfb-114">SSO_WARN_UPDATE_FAILED</span></span>                           |
|  <span data-ttu-id="4fcfb-115">訊息文字</span><span class="sxs-lookup"><span data-stu-id="4fcfb-115">Message Text</span></span>   | <span data-ttu-id="4fcfb-116">無法重新加密期間，更新 SSO 資料庫中的認證</span><span class="sxs-lookup"><span data-stu-id="4fcfb-116">Failed to update the credentials in the SSO database during re-encryption</span></span> |

## <a name="explanation"></a><span data-ttu-id="4fcfb-117">說明</span><span class="sxs-lookup"><span data-stu-id="4fcfb-117">Explanation</span></span>  
 <span data-ttu-id="4fcfb-118">這個警告事件表示，仍無法使用新的加密結果更新的認證。</span><span class="sxs-lookup"><span data-stu-id="4fcfb-118">This Warning event indicates that it was not possible to update the credentials with the result of the new encryption.</span></span> <span data-ttu-id="4fcfb-119">變更主要密碼時，藉由產生新的祕密或還原舊的密碼，來解密使用舊的密碼加密的所有密碼和重新加密以新的密碼在 SSO 資料庫上執行重新加密。</span><span class="sxs-lookup"><span data-stu-id="4fcfb-119">When the master secret is changed, either by generating a new secret or by restoring an old secret, a re-encryption is performed on the SSO database to decrypt all the secrets encrypted with the old secret, and re-encrypt them with the new secret.</span></span> <span data-ttu-id="4fcfb-120">如果認證已刪除，正在重新加密的過程中所顯示的一樣，會發生此事件。</span><span class="sxs-lookup"><span data-stu-id="4fcfb-120">This event can occur if the credentials were deleted as they were in the process of being re-encrypted.</span></span>  

## <a name="user-action"></a><span data-ttu-id="4fcfb-121">使用者動作</span><span class="sxs-lookup"><span data-stu-id="4fcfb-121">User Action</span></span>  
 <span data-ttu-id="4fcfb-122">若要解決這個警告，執行下列作業：</span><span class="sxs-lookup"><span data-stu-id="4fcfb-122">To resolve this warning, do the following:</span></span>  

- <span data-ttu-id="4fcfb-123">等候另一個在短暫的延遲; 之後所發生的重新加密如果，不會自動發生，請重新啟動 SSO 服務，其會觸發新的重新加密，如果有必要。</span><span class="sxs-lookup"><span data-stu-id="4fcfb-123">Wait for another re-encryption to occur after a short delay; if that does not occur automatically, restart the SSO service which will trigger a new re-encryption if one is required.</span></span>  

  <span data-ttu-id="4fcfb-124">如需詳細資訊，請參閱中的下列資源[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]幫助：</span><span class="sxs-lookup"><span data-stu-id="4fcfb-124">For more information, see the following resources in [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] Help:</span></span>  

- [<span data-ttu-id="4fcfb-125">了解 SSO</span><span class="sxs-lookup"><span data-stu-id="4fcfb-125">Understanding SSO</span></span>](../core/understanding-sso.md)
