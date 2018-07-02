---
title: 單一登入： 事件 10714 |Microsoft Docs
ms.custom: ''
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 59d8509f-cc3e-40fa-ba3d-3dcb0e73c67a
caps.latest.revision: 13
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 30523330ccaabddb94acf1ca1eba7d5c46c5fe0c
ms.sourcegitcommit: 266308ec5c6a9d8d80ff298ee6051b4843c5d626
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/27/2018
ms.locfileid: "36985295"
---
# <a name="single-sign-on-event-10714"></a><span data-ttu-id="fafa5-102">單一登入： 事件 10714</span><span class="sxs-lookup"><span data-stu-id="fafa5-102">Single Sign-On: Event 10714</span></span>
## <a name="details"></a><span data-ttu-id="fafa5-103">詳細資料</span><span class="sxs-lookup"><span data-stu-id="fafa5-103">Details</span></span>  

|                 |                                                                                                   |
|-----------------|---------------------------------------------------------------------------------------------------|
|  <span data-ttu-id="fafa5-104">產品名稱</span><span class="sxs-lookup"><span data-stu-id="fafa5-104">Product Name</span></span>   |                                     <span data-ttu-id="fafa5-105">企業單一登入</span><span class="sxs-lookup"><span data-stu-id="fafa5-105">Enterprise Single Sign-On</span></span>                                     |
| <span data-ttu-id="fafa5-106">產品版本</span><span class="sxs-lookup"><span data-stu-id="fafa5-106">Product Version</span></span> |                    [!INCLUDE[btsSSOVersion](../includes/btsssoversion-md.md)]                     |
|    <span data-ttu-id="fafa5-107">事件識別碼</span><span class="sxs-lookup"><span data-stu-id="fafa5-107">Event ID</span></span>     |                                               <span data-ttu-id="fafa5-108">10714</span><span class="sxs-lookup"><span data-stu-id="fafa5-108">10714</span></span>                                               |
|  <span data-ttu-id="fafa5-109">事件來源</span><span class="sxs-lookup"><span data-stu-id="fafa5-109">Event Source</span></span>   |                                              <span data-ttu-id="fafa5-110">ENTSSO</span><span class="sxs-lookup"><span data-stu-id="fafa5-110">ENTSSO</span></span>                                               |
|    <span data-ttu-id="fafa5-111">元件</span><span class="sxs-lookup"><span data-stu-id="fafa5-111">Component</span></span>    |                                                <span data-ttu-id="fafa5-112">N\A</span><span class="sxs-lookup"><span data-stu-id="fafa5-112">N\A</span></span>                                                |
|  <span data-ttu-id="fafa5-113">符號名稱</span><span class="sxs-lookup"><span data-stu-id="fafa5-113">Symbolic Name</span></span>  |                             <span data-ttu-id="fafa5-114">SSO_WARN_PS_NOTIFICATION_RETRIES_EXPIRED</span><span class="sxs-lookup"><span data-stu-id="fafa5-114">SSO_WARN_PS_NOTIFICATION_RETRIES_EXPIRED</span></span>                              |
|  <span data-ttu-id="fafa5-115">訊息文字</span><span class="sxs-lookup"><span data-stu-id="fafa5-115">Message Text</span></span>   | <span data-ttu-id="fafa5-116">重試已過期，捨棄通知。%r</span><span class="sxs-lookup"><span data-stu-id="fafa5-116">Retries expired, discarding notification.%r</span></span><br /><br /> <span data-ttu-id="fafa5-117">追蹤識別碼: %1 %r</span><span class="sxs-lookup"><span data-stu-id="fafa5-117">Tracking ID: %1%r</span></span><br /><br /> <span data-ttu-id="fafa5-118">配接器： %2</span><span class="sxs-lookup"><span data-stu-id="fafa5-118">Adapter: %2</span></span> |

## <a name="explanation"></a><span data-ttu-id="fafa5-119">說明</span><span class="sxs-lookup"><span data-stu-id="fafa5-119">Explanation</span></span>  
 <span data-ttu-id="fafa5-120">這個警告事件表示密碼同步通知重試已過期，已捨棄通知。</span><span class="sxs-lookup"><span data-stu-id="fafa5-120">This Warning event indicates that the Password Sync notification retries have expired, and the notification has been discarded.</span></span>  

 <span data-ttu-id="fafa5-121">密碼變更 (從 Windows 到外部系統) 傳送到密碼同步配接器時，密碼同步配接器會通知已成功處理密碼變更。</span><span class="sxs-lookup"><span data-stu-id="fafa5-121">When a password change (from Windows to an external system) is delivered to a password sync adapter, the password sync adapter acknowledges that it has successfully processed the password change.</span></span> <span data-ttu-id="fafa5-122">如果密碼變更未在指定的時間內發生，或者如果變更期間發生其他問題，則密碼變更會再次傳送到密碼同步配接器。</span><span class="sxs-lookup"><span data-stu-id="fafa5-122">If the password change does not occur within a specified amount of time, or if another problem occurs during the change, the password change is delivered to the password sync adapter again.</span></span> <span data-ttu-id="fafa5-123">這是有限的時間 （最大重試），則會捨棄密碼變更通知。</span><span class="sxs-lookup"><span data-stu-id="fafa5-123">This is done a limited number of times (max retries) and then the password change notification is discarded.</span></span>  

## <a name="user-action"></a><span data-ttu-id="fafa5-124">使用者動作</span><span class="sxs-lookup"><span data-stu-id="fafa5-124">User Action</span></span>  
 <span data-ttu-id="fafa5-125">若要解決這個警告，執行下列作業：</span><span class="sxs-lookup"><span data-stu-id="fafa5-125">To resolve this warning, do the following:</span></span>  

- <span data-ttu-id="fafa5-126">請檢查關聯事件的系統和應用程式事件記錄檔。</span><span class="sxs-lookup"><span data-stu-id="fafa5-126">Check System and Application event logs for associated events.</span></span>  

  <span data-ttu-id="fafa5-127">如需詳細資訊，請參閱下列資源：</span><span class="sxs-lookup"><span data-stu-id="fafa5-127">For more information, see the following resources:</span></span>  

- [<span data-ttu-id="fafa5-128">如何設定密碼同步處理</span><span class="sxs-lookup"><span data-stu-id="fafa5-128">How to Configure Password Synchronization</span></span>](../core/how-to-configure-password-synchronization.md)  

- [<span data-ttu-id="fafa5-129">密碼同步</span><span class="sxs-lookup"><span data-stu-id="fafa5-129">Password Synchronization</span></span>](../core/password-synchronization2.md)
