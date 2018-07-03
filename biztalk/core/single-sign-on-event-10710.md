---
title: 單一登入： 事件 10710 |Microsoft Docs
ms.custom: ''
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 469dc407-be7a-45a1-bcf5-2ba7060a19e2
caps.latest.revision: 10
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 888468da03c01f654bd550ce210b02c4a03ad40b
ms.sourcegitcommit: 266308ec5c6a9d8d80ff298ee6051b4843c5d626
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/27/2018
ms.locfileid: "36989919"
---
# <a name="single-sign-on-event-10710"></a><span data-ttu-id="a9448-102">單一登入： 事件 10710</span><span class="sxs-lookup"><span data-stu-id="a9448-102">Single Sign-On: Event 10710</span></span>
## <a name="details"></a><span data-ttu-id="a9448-103">詳細資料</span><span class="sxs-lookup"><span data-stu-id="a9448-103">Details</span></span>  

|                 |                                                                                                                                                                             |
|-----------------|-----------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
|  <span data-ttu-id="a9448-104">產品名稱</span><span class="sxs-lookup"><span data-stu-id="a9448-104">Product Name</span></span>   |                                                                          <span data-ttu-id="a9448-105">企業單一登入</span><span class="sxs-lookup"><span data-stu-id="a9448-105">Enterprise Single Sign-On</span></span>                                                                          |
| <span data-ttu-id="a9448-106">產品版本</span><span class="sxs-lookup"><span data-stu-id="a9448-106">Product Version</span></span> |                                                         [!INCLUDE[btsSSOVersion](../includes/btsssoversion-md.md)]                                                          |
|    <span data-ttu-id="a9448-107">事件識別碼</span><span class="sxs-lookup"><span data-stu-id="a9448-107">Event ID</span></span>     |                                                                                    <span data-ttu-id="a9448-108">10710</span><span class="sxs-lookup"><span data-stu-id="a9448-108">10710</span></span>                                                                                    |
|  <span data-ttu-id="a9448-109">事件來源</span><span class="sxs-lookup"><span data-stu-id="a9448-109">Event Source</span></span>   |                                                                                   <span data-ttu-id="a9448-110">ENTSSO</span><span class="sxs-lookup"><span data-stu-id="a9448-110">ENTSSO</span></span>                                                                                    |
|    <span data-ttu-id="a9448-111">元件</span><span class="sxs-lookup"><span data-stu-id="a9448-111">Component</span></span>    |                                                                                     <span data-ttu-id="a9448-112">N\A</span><span class="sxs-lookup"><span data-stu-id="a9448-112">N\A</span></span>                                                                                     |
|  <span data-ttu-id="a9448-113">符號名稱</span><span class="sxs-lookup"><span data-stu-id="a9448-113">Symbolic Name</span></span>  |                                                                        <span data-ttu-id="a9448-114">SSO_INFO_PS_WIN_CHANGE_DAMPED</span><span class="sxs-lookup"><span data-stu-id="a9448-114">SSO_INFO_PS_WIN_CHANGE_DAMPED</span></span>                                                                        |
|  <span data-ttu-id="a9448-115">訊息文字</span><span class="sxs-lookup"><span data-stu-id="a9448-115">Message Text</span></span>   | <span data-ttu-id="a9448-116">Windows 密碼變更已禁止 （偵測到重複的和 discarded).%r</span><span class="sxs-lookup"><span data-stu-id="a9448-116">A Windows password change was damped (detected as a duplicate and discarded).%r</span></span><br /><br /> <span data-ttu-id="a9448-117">追蹤識別碼: %1 %r</span><span class="sxs-lookup"><span data-stu-id="a9448-117">Tracking ID: %1%r</span></span><br /><br /> <span data-ttu-id="a9448-118">Windows 帳戶: %2 %r</span><span class="sxs-lookup"><span data-stu-id="a9448-118">Windows Account: %2%r</span></span><br /><br /> <span data-ttu-id="a9448-119">用戶端使用者： %3</span><span class="sxs-lookup"><span data-stu-id="a9448-119">Client User: %3</span></span> |

## <a name="explanation"></a><span data-ttu-id="a9448-120">說明</span><span class="sxs-lookup"><span data-stu-id="a9448-120">Explanation</span></span>  
 <span data-ttu-id="a9448-121">這個資訊事件表示已捨棄 Windows 密碼變更，因為它偵測到為重複。</span><span class="sxs-lookup"><span data-stu-id="a9448-121">This Information event indicates that a Windows password change was discarded because it was detected as a duplicate.</span></span>  

## <a name="user-action"></a><span data-ttu-id="a9448-122">使用者動作</span><span class="sxs-lookup"><span data-stu-id="a9448-122">User Action</span></span>  

- <span data-ttu-id="a9448-123">使用者不必採取任何動作。</span><span class="sxs-lookup"><span data-stu-id="a9448-123">No user action is necessary.</span></span>  

  <span data-ttu-id="a9448-124">如需詳細資訊，請參閱下列資源：</span><span class="sxs-lookup"><span data-stu-id="a9448-124">For more information, see the following resources:</span></span>  

- [<span data-ttu-id="a9448-125">密碼同步</span><span class="sxs-lookup"><span data-stu-id="a9448-125">Password Synchronization</span></span>](../core/password-synchronization2.md)
