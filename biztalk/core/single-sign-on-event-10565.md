---
title: 單一登入： 事件 10565 |Microsoft Docs
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
ms.openlocfilehash: d31b639853b845169c3360ec6367aee120a266d1
ms.sourcegitcommit: 266308ec5c6a9d8d80ff298ee6051b4843c5d626
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/27/2018
ms.locfileid: "37007999"
---
# <a name="single-sign-on-event-10565"></a><span data-ttu-id="6ef1d-102">單一登入： 事件 10565</span><span class="sxs-lookup"><span data-stu-id="6ef1d-102">Single Sign-On: Event 10565</span></span>
## <a name="details"></a><span data-ttu-id="6ef1d-103">詳細資料</span><span class="sxs-lookup"><span data-stu-id="6ef1d-103">Details</span></span>  
  
|                 |                                                                                                                                                                                                               |
|-----------------|---------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
|  <span data-ttu-id="6ef1d-104">產品名稱</span><span class="sxs-lookup"><span data-stu-id="6ef1d-104">Product Name</span></span>   |                                                                                           <span data-ttu-id="6ef1d-105">企業單一登入</span><span class="sxs-lookup"><span data-stu-id="6ef1d-105">Enterprise Single Sign-On</span></span>                                                                                           |
| <span data-ttu-id="6ef1d-106">產品版本</span><span class="sxs-lookup"><span data-stu-id="6ef1d-106">Product Version</span></span> |                                                                          [!INCLUDE[btsSSOVersion](../includes/btsssoversion-md.md)]                                                                           |
|    <span data-ttu-id="6ef1d-107">事件識別碼</span><span class="sxs-lookup"><span data-stu-id="6ef1d-107">Event ID</span></span>     |                                                                                                     <span data-ttu-id="6ef1d-108">10565</span><span class="sxs-lookup"><span data-stu-id="6ef1d-108">10565</span></span>                                                                                                     |
|  <span data-ttu-id="6ef1d-109">事件來源</span><span class="sxs-lookup"><span data-stu-id="6ef1d-109">Event Source</span></span>   |                                                                                                    <span data-ttu-id="6ef1d-110">ENTSSO</span><span class="sxs-lookup"><span data-stu-id="6ef1d-110">ENTSSO</span></span>                                                                                                     |
|    <span data-ttu-id="6ef1d-111">元件</span><span class="sxs-lookup"><span data-stu-id="6ef1d-111">Component</span></span>    |                                                                                                      <span data-ttu-id="6ef1d-112">不適用</span><span class="sxs-lookup"><span data-stu-id="6ef1d-112">N/A</span></span>                                                                                                      |
|  <span data-ttu-id="6ef1d-113">符號名稱</span><span class="sxs-lookup"><span data-stu-id="6ef1d-113">Symbolic Name</span></span>  |                                                                                       <span data-ttu-id="6ef1d-114">SSO_ERROR_SECRET_VALIDATE_FAILED</span><span class="sxs-lookup"><span data-stu-id="6ef1d-114">SSO_ERROR_SECRET_VALIDATE_FAILED</span></span>                                                                                        |
|  <span data-ttu-id="6ef1d-115">訊息文字</span><span class="sxs-lookup"><span data-stu-id="6ef1d-115">Message Text</span></span>   | <span data-ttu-id="6ef1d-116">無法從登錄載入祕密。</span><span class="sxs-lookup"><span data-stu-id="6ef1d-116">The secret could not be loaded from the registry.</span></span> <span data-ttu-id="6ef1d-117">SSO 服務的服務帳戶可能已變更，或將密碼可能已損毀。</span><span class="sxs-lookup"><span data-stu-id="6ef1d-117">The service account for the SSO service may have been changed or the secret may be corrupted.</span></span> <span data-ttu-id="6ef1d-118">從備份 file.%r 還原祕密</span><span class="sxs-lookup"><span data-stu-id="6ef1d-118">Restore the secret from a backup file.%r</span></span><br /><br /> <span data-ttu-id="6ef1d-119">MSID: %1</span><span class="sxs-lookup"><span data-stu-id="6ef1d-119">MSID: %1</span></span> |
  
## <a name="explanation"></a><span data-ttu-id="6ef1d-120">說明</span><span class="sxs-lookup"><span data-stu-id="6ef1d-120">Explanation</span></span>  
 <span data-ttu-id="6ef1d-121">很可能到系統中的系統管理員已變更為 SSO 服務帳戶，使無法解密。</span><span class="sxs-lookup"><span data-stu-id="6ef1d-121">It is likely that an administrator in the system has changed the SSO Service account, making decryption impossible.</span></span>  
  
## <a name="user-action"></a><span data-ttu-id="6ef1d-122">使用者動作</span><span class="sxs-lookup"><span data-stu-id="6ef1d-122">User Action</span></span>  
 <span data-ttu-id="6ef1d-123">尋找變更 SSO 服務帳戶的人員，並接著從備份檔案還原祕密。</span><span class="sxs-lookup"><span data-stu-id="6ef1d-123">Find the person who changed the SSO Service account, and then restore the secret from a backup file.</span></span> <span data-ttu-id="6ef1d-124">如需有關還原密碼的詳細資訊，請參閱 <<c0> [ 管理主要密碼](../core/managing-the-master-secret.md)。</span><span class="sxs-lookup"><span data-stu-id="6ef1d-124">For more information on restoring the secret, see [Managing the Master Secret](../core/managing-the-master-secret.md).</span></span>