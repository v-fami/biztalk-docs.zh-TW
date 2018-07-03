---
title: 單一登入： 事件 10746 |Microsoft Docs
ms.custom: ''
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 8189120b-923a-4c88-937e-f06565bcac56
caps.latest.revision: 13
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: b3f4fa77909ba53e16d3dffd31073ff93e233ed5
ms.sourcegitcommit: 266308ec5c6a9d8d80ff298ee6051b4843c5d626
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/27/2018
ms.locfileid: "36998863"
---
# <a name="single-sign-on-event-10746"></a><span data-ttu-id="2a6e6-102">單一登入： 事件 10746</span><span class="sxs-lookup"><span data-stu-id="2a6e6-102">Single Sign-On: Event 10746</span></span>
## <a name="details"></a><span data-ttu-id="2a6e6-103">詳細資料</span><span class="sxs-lookup"><span data-stu-id="2a6e6-103">Details</span></span>  

|                 |                                                                                                                                               |
|-----------------|-----------------------------------------------------------------------------------------------------------------------------------------------|
|  <span data-ttu-id="2a6e6-104">產品名稱</span><span class="sxs-lookup"><span data-stu-id="2a6e6-104">Product Name</span></span>   |                                                           <span data-ttu-id="2a6e6-105">企業單一登入</span><span class="sxs-lookup"><span data-stu-id="2a6e6-105">Enterprise Single Sign-On</span></span>                                                           |
| <span data-ttu-id="2a6e6-106">產品版本</span><span class="sxs-lookup"><span data-stu-id="2a6e6-106">Product Version</span></span> |                                          [!INCLUDE[btsSSOVersion](../includes/btsssoversion-md.md)]                                           |
|    <span data-ttu-id="2a6e6-107">事件識別碼</span><span class="sxs-lookup"><span data-stu-id="2a6e6-107">Event ID</span></span>     |                                                                     <span data-ttu-id="2a6e6-108">10746</span><span class="sxs-lookup"><span data-stu-id="2a6e6-108">10746</span></span>                                                                     |
|  <span data-ttu-id="2a6e6-109">事件來源</span><span class="sxs-lookup"><span data-stu-id="2a6e6-109">Event Source</span></span>   |                                                                    <span data-ttu-id="2a6e6-110">ENTSSO</span><span class="sxs-lookup"><span data-stu-id="2a6e6-110">ENTSSO</span></span>                                                                     |
|    <span data-ttu-id="2a6e6-111">元件</span><span class="sxs-lookup"><span data-stu-id="2a6e6-111">Component</span></span>    |                                                                      <span data-ttu-id="2a6e6-112">N\A</span><span class="sxs-lookup"><span data-stu-id="2a6e6-112">N\A</span></span>                                                                      |
|  <span data-ttu-id="2a6e6-113">符號名稱</span><span class="sxs-lookup"><span data-stu-id="2a6e6-113">Symbolic Name</span></span>  |                                                           <span data-ttu-id="2a6e6-114">SSO_WARN_PASSWORD_EXPIRED</span><span class="sxs-lookup"><span data-stu-id="2a6e6-114">SSO_WARN_PASSWORD_EXPIRED</span></span>                                                           |
|  <span data-ttu-id="2a6e6-115">訊息文字</span><span class="sxs-lookup"><span data-stu-id="2a6e6-115">Message Text</span></span>   | <span data-ttu-id="2a6e6-116">外部帳戶的密碼已 expired.%r</span><span class="sxs-lookup"><span data-stu-id="2a6e6-116">The password for the external account has expired.%r</span></span><br /><br /> <span data-ttu-id="2a6e6-117">追蹤識別碼: %1 %r</span><span class="sxs-lookup"><span data-stu-id="2a6e6-117">Tracking ID: %1%r</span></span><br /><br /> <span data-ttu-id="2a6e6-118">配接器: %2 %r</span><span class="sxs-lookup"><span data-stu-id="2a6e6-118">Adapter: %2%r</span></span><br /><br /> <span data-ttu-id="2a6e6-119">外部帳戶： %3</span><span class="sxs-lookup"><span data-stu-id="2a6e6-119">External Account: %3</span></span> |

## <a name="explanation"></a><span data-ttu-id="2a6e6-120">說明</span><span class="sxs-lookup"><span data-stu-id="2a6e6-120">Explanation</span></span>  
 <span data-ttu-id="2a6e6-121">這個警告事件表示外部帳戶的密碼已過期。</span><span class="sxs-lookup"><span data-stu-id="2a6e6-121">This Warning event indicates that the password for the external account has expired.</span></span>  

## <a name="user-action"></a><span data-ttu-id="2a6e6-122">使用者動作</span><span class="sxs-lookup"><span data-stu-id="2a6e6-122">User Action</span></span>  
 <span data-ttu-id="2a6e6-123">若要解決這個警告，請檢查系統和應用程式事件記錄檔相關聯的錯誤。</span><span class="sxs-lookup"><span data-stu-id="2a6e6-123">To resolve this warning, check the system and application event logs for associated errors.</span></span>    

## <a name="more-info"></a><span data-ttu-id="2a6e6-124">其他資訊</span><span class="sxs-lookup"><span data-stu-id="2a6e6-124">More info</span></span>
<span data-ttu-id="2a6e6-125">如需詳細資訊，請參閱下列資源：</span><span class="sxs-lookup"><span data-stu-id="2a6e6-125">For more information, see the following resources:</span></span>  

- <span data-ttu-id="2a6e6-126">**密碼同步配接器屬性： 選項** [!INCLUDE[ui-guidance-developers-reference](../includes/ui-guidance-developers-reference.md)]</span><span class="sxs-lookup"><span data-stu-id="2a6e6-126">**Password Sync Adapter Properties: Options** [!INCLUDE[ui-guidance-developers-reference](../includes/ui-guidance-developers-reference.md)]</span></span>  

- [<span data-ttu-id="2a6e6-127">密碼同步</span><span class="sxs-lookup"><span data-stu-id="2a6e6-127">Password Synchronization</span></span>](../core/password-synchronization2.md)
