---
title: 單一登入： 事件 11063 |Microsoft Docs
ms.custom: ''
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: c84f91de-221d-43c4-8d23-3d1b7fd29cf7
caps.latest.revision: 7
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 5a653b8c5cf27925c65d8922a5a561855fdb6a4c
ms.sourcegitcommit: 266308ec5c6a9d8d80ff298ee6051b4843c5d626
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/27/2018
ms.locfileid: "36975567"
---
# <a name="single-sign-on-event-11063"></a><span data-ttu-id="4e1c2-102">單一登入： 事件 11063</span><span class="sxs-lookup"><span data-stu-id="4e1c2-102">Single Sign-On: Event 11063</span></span>
## <a name="details"></a><span data-ttu-id="4e1c2-103">詳細資料</span><span class="sxs-lookup"><span data-stu-id="4e1c2-103">Details</span></span>  
  
|                 |                                                            |
|-----------------|------------------------------------------------------------|
|  <span data-ttu-id="4e1c2-104">產品名稱</span><span class="sxs-lookup"><span data-stu-id="4e1c2-104">Product Name</span></span>   |                 <span data-ttu-id="4e1c2-105">企業單一登入</span><span class="sxs-lookup"><span data-stu-id="4e1c2-105">Enterprise Single Sign-On</span></span>                  |
| <span data-ttu-id="4e1c2-106">產品版本</span><span class="sxs-lookup"><span data-stu-id="4e1c2-106">Product Version</span></span> | [!INCLUDE[btsSSOVersion](../includes/btsssoversion-md.md)] |
|    <span data-ttu-id="4e1c2-107">事件識別碼</span><span class="sxs-lookup"><span data-stu-id="4e1c2-107">Event ID</span></span>     |                           <span data-ttu-id="4e1c2-108">11063</span><span class="sxs-lookup"><span data-stu-id="4e1c2-108">11063</span></span>                            |
|  <span data-ttu-id="4e1c2-109">事件來源</span><span class="sxs-lookup"><span data-stu-id="4e1c2-109">Event Source</span></span>   |                           <span data-ttu-id="4e1c2-110">ENTSSO</span><span class="sxs-lookup"><span data-stu-id="4e1c2-110">ENTSSO</span></span>                           |
|    <span data-ttu-id="4e1c2-111">元件</span><span class="sxs-lookup"><span data-stu-id="4e1c2-111">Component</span></span>    |                            <span data-ttu-id="4e1c2-112">不適用</span><span class="sxs-lookup"><span data-stu-id="4e1c2-112">N/A</span></span>                             |
|  <span data-ttu-id="4e1c2-113">符號名稱</span><span class="sxs-lookup"><span data-stu-id="4e1c2-113">Symbolic Name</span></span>  |          <span data-ttu-id="4e1c2-114">SSO_ERROR_PS_MIIS_CALLBACK_ACCESS_DENIED</span><span class="sxs-lookup"><span data-stu-id="4e1c2-114">SSO_ERROR_PS_MIIS_CALLBACK_ACCESS_DENIED</span></span>          |
|  <span data-ttu-id="4e1c2-115">訊息文字</span><span class="sxs-lookup"><span data-stu-id="4e1c2-115">Message Text</span></span>   |      <span data-ttu-id="4e1c2-116">密碼同步伺服器 (針對 MIIS) 存取遭拒。%r</span><span class="sxs-lookup"><span data-stu-id="4e1c2-116">Password sync server (for MIIS) access denied.%r</span></span>      |
  
## <a name="explanation"></a><span data-ttu-id="4e1c2-117">說明</span><span class="sxs-lookup"><span data-stu-id="4e1c2-117">Explanation</span></span>  
 <span data-ttu-id="4e1c2-118">MIIS 回呼存取被拒。</span><span class="sxs-lookup"><span data-stu-id="4e1c2-118">MIIS Callback access has been denied.</span></span> <span data-ttu-id="4e1c2-119">此錯誤最可能的原因是要使用 MIIS 和 ENTSSO 系統之間的 Kerberos 驗證失敗。</span><span class="sxs-lookup"><span data-stu-id="4e1c2-119">The most likely cause of this error is failure to use the Kerberos authentication between the ENTSSO system and MIIS.</span></span>  
  
## <a name="user-action"></a><span data-ttu-id="4e1c2-120">使用者動作</span><span class="sxs-lookup"><span data-stu-id="4e1c2-120">User Action</span></span>  
 <span data-ttu-id="4e1c2-121">確認 ENTSSO 系統使用 Kerberos 驗證。</span><span class="sxs-lookup"><span data-stu-id="4e1c2-121">Confirm that your ENTSSO system is using Kerberos authentication.</span></span> <span data-ttu-id="4e1c2-122">如需詳細資訊，請參閱 < [SSO 安全性建議](../core/sso-security-recommendations.md)。</span><span class="sxs-lookup"><span data-stu-id="4e1c2-122">For more information, see [SSO Security Recommendations](../core/sso-security-recommendations.md).</span></span>