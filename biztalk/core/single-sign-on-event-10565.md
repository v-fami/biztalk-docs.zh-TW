---
title: 單一登入： 事件 10565 |Microsoft 文件
ms.custom: ''
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 6d279491-dc0d-44c4-a77e-a67498a3481d
caps.latest.revision: 8
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 9567421210689d8615cf88e7fbd6493ef5749d02
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/20/2017
ms.locfileid: "22271030"
---
# <a name="single-sign-on-event-10565"></a><span data-ttu-id="14037-102">單一登入： 事件 10565</span><span class="sxs-lookup"><span data-stu-id="14037-102">Single Sign-On: Event 10565</span></span>
## <a name="details"></a><span data-ttu-id="14037-103">詳細資料</span><span class="sxs-lookup"><span data-stu-id="14037-103">Details</span></span>  
  
|||  
|-|-|  
|<span data-ttu-id="14037-104">產品名稱</span><span class="sxs-lookup"><span data-stu-id="14037-104">Product Name</span></span>|<span data-ttu-id="14037-105">企業單一登入</span><span class="sxs-lookup"><span data-stu-id="14037-105">Enterprise Single Sign-On</span></span>|  
|<span data-ttu-id="14037-106">產品版本</span><span class="sxs-lookup"><span data-stu-id="14037-106">Product Version</span></span>|[!INCLUDE[btsSSOVersion](../includes/btsssoversion-md.md)]|  
|<span data-ttu-id="14037-107">事件識別碼</span><span class="sxs-lookup"><span data-stu-id="14037-107">Event ID</span></span>|<span data-ttu-id="14037-108">10565</span><span class="sxs-lookup"><span data-stu-id="14037-108">10565</span></span>|  
|<span data-ttu-id="14037-109">事件來源</span><span class="sxs-lookup"><span data-stu-id="14037-109">Event Source</span></span>|<span data-ttu-id="14037-110">ENTSSO</span><span class="sxs-lookup"><span data-stu-id="14037-110">ENTSSO</span></span>|  
|<span data-ttu-id="14037-111">元件</span><span class="sxs-lookup"><span data-stu-id="14037-111">Component</span></span>|<span data-ttu-id="14037-112">不適用</span><span class="sxs-lookup"><span data-stu-id="14037-112">N/A</span></span>|  
|<span data-ttu-id="14037-113">符號名稱</span><span class="sxs-lookup"><span data-stu-id="14037-113">Symbolic Name</span></span>|<span data-ttu-id="14037-114">SSO_ERROR_SECRET_VALIDATE_FAILED</span><span class="sxs-lookup"><span data-stu-id="14037-114">SSO_ERROR_SECRET_VALIDATE_FAILED</span></span>|  
|<span data-ttu-id="14037-115">訊息文字</span><span class="sxs-lookup"><span data-stu-id="14037-115">Message Text</span></span>|<span data-ttu-id="14037-116">無法從登錄載入密碼。</span><span class="sxs-lookup"><span data-stu-id="14037-116">The secret could not be loaded from the registry.</span></span> <span data-ttu-id="14037-117">SSO 服務的服務帳戶變更或密碼可能已損毀。</span><span class="sxs-lookup"><span data-stu-id="14037-117">The service account for the SSO service may have been changed or the secret may be corrupted.</span></span> <span data-ttu-id="14037-118">從備份 file.%r 還原密碼</span><span class="sxs-lookup"><span data-stu-id="14037-118">Restore the secret from a backup file.%r</span></span><br /><br /> <span data-ttu-id="14037-119">MSID: %1</span><span class="sxs-lookup"><span data-stu-id="14037-119">MSID: %1</span></span>|  
  
## <a name="explanation"></a><span data-ttu-id="14037-120">說明</span><span class="sxs-lookup"><span data-stu-id="14037-120">Explanation</span></span>  
 <span data-ttu-id="14037-121">有可能，系統中的系統管理員已變更為 SSO 服務帳戶，讓無法解密。</span><span class="sxs-lookup"><span data-stu-id="14037-121">It is likely that an administrator in the system has changed the SSO Service account, making decryption impossible.</span></span>  
  
## <a name="user-action"></a><span data-ttu-id="14037-122">使用者動作</span><span class="sxs-lookup"><span data-stu-id="14037-122">User Action</span></span>  
 <span data-ttu-id="14037-123">尋找變更 SSO 服務帳戶的人員，然後從備份檔案還原密碼。</span><span class="sxs-lookup"><span data-stu-id="14037-123">Find the person who changed the SSO Service account, and then restore the secret from a backup file.</span></span> <span data-ttu-id="14037-124">如需有關還原密碼的詳細資訊，請參閱[管理主要密碼](../core/managing-the-master-secret.md)。</span><span class="sxs-lookup"><span data-stu-id="14037-124">For more information on restoring the secret, see [Managing the Master Secret](../core/managing-the-master-secret.md).</span></span>