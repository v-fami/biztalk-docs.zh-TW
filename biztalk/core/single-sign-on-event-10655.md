---
title: 單一登入： 事件 10655 |Microsoft Docs
ms.custom: ''
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 1bb6a8dd-35e4-40a6-8900-450a9b6de249
caps.latest.revision: 10
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 75ce0442b02667ce9796d9418dae4b1700dd757d
ms.sourcegitcommit: 266308ec5c6a9d8d80ff298ee6051b4843c5d626
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/27/2018
ms.locfileid: "37013007"
---
# <a name="single-sign-on-event-10655"></a><span data-ttu-id="ee257-102">單一登入： 事件 10655</span><span class="sxs-lookup"><span data-stu-id="ee257-102">Single Sign-On: Event 10655</span></span>
## <a name="details"></a><span data-ttu-id="ee257-103">詳細資料</span><span class="sxs-lookup"><span data-stu-id="ee257-103">Details</span></span>  

|                 |                                                                              |
|-----------------|------------------------------------------------------------------------------|
|  <span data-ttu-id="ee257-104">產品名稱</span><span class="sxs-lookup"><span data-stu-id="ee257-104">Product Name</span></span>   |                          <span data-ttu-id="ee257-105">企業單一登入</span><span class="sxs-lookup"><span data-stu-id="ee257-105">Enterprise Single Sign-On</span></span>                           |
| <span data-ttu-id="ee257-106">產品版本</span><span class="sxs-lookup"><span data-stu-id="ee257-106">Product Version</span></span> |          [!INCLUDE[btsSSOVersion](../includes/btsssoversion-md.md)]          |
|    <span data-ttu-id="ee257-107">事件識別碼</span><span class="sxs-lookup"><span data-stu-id="ee257-107">Event ID</span></span>     |                                    <span data-ttu-id="ee257-108">10655</span><span class="sxs-lookup"><span data-stu-id="ee257-108">10655</span></span>                                     |
|  <span data-ttu-id="ee257-109">事件來源</span><span class="sxs-lookup"><span data-stu-id="ee257-109">Event Source</span></span>   |                                    <span data-ttu-id="ee257-110">ENTSSO</span><span class="sxs-lookup"><span data-stu-id="ee257-110">ENTSSO</span></span>                                    |
|    <span data-ttu-id="ee257-111">元件</span><span class="sxs-lookup"><span data-stu-id="ee257-111">Component</span></span>    |                                     <span data-ttu-id="ee257-112">N\A</span><span class="sxs-lookup"><span data-stu-id="ee257-112">N\A</span></span>                                      |
|  <span data-ttu-id="ee257-113">符號名稱</span><span class="sxs-lookup"><span data-stu-id="ee257-113">Symbolic Name</span></span>  |                   <span data-ttu-id="ee257-114">SSO_ERROR_PS_PING_CALLBACK_ACCESS_DENIED</span><span class="sxs-lookup"><span data-stu-id="ee257-114">SSO_ERROR_PS_PING_CALLBACK_ACCESS_DENIED</span></span>                   |
|  <span data-ttu-id="ee257-115">訊息文字</span><span class="sxs-lookup"><span data-stu-id="ee257-115">Message Text</span></span>   | <span data-ttu-id="ee257-116">密碼同步處理伺服器 （ping) 存取 denied.%r</span><span class="sxs-lookup"><span data-stu-id="ee257-116">Password sync server (for ping) access denied.%r</span></span><br /><br /> <span data-ttu-id="ee257-117">用戶端使用者： %1</span><span class="sxs-lookup"><span data-stu-id="ee257-117">Client User: %1</span></span> |

## <a name="explanation"></a><span data-ttu-id="ee257-118">說明</span><span class="sxs-lookup"><span data-stu-id="ee257-118">Explanation</span></span>  
 <span data-ttu-id="ee257-119">這個錯誤事件表示訊息傳送至 [名稱] 伺服器，但已封鎖的回覆。</span><span class="sxs-lookup"><span data-stu-id="ee257-119">This Error event indicates that a message was sent to the [name] server but the reply was blocked.</span></span> <span data-ttu-id="ee257-120">原因可能是由數項不同的原因，例如不正確的通訊協定或在伺服器上沒有足夠的安全性權限。</span><span class="sxs-lookup"><span data-stu-id="ee257-120">This can be caused by a number of different reasons, such as incorrect protocol or insufficient security permissions on the server.</span></span>  

## <a name="user-action"></a><span data-ttu-id="ee257-121">使用者動作</span><span class="sxs-lookup"><span data-stu-id="ee257-121">User Action</span></span>  
 <span data-ttu-id="ee257-122">若要解決這個錯誤，執行下列作業：</span><span class="sxs-lookup"><span data-stu-id="ee257-122">To resolve this error, do the following:</span></span>  

- <span data-ttu-id="ee257-123">請注意，此訊息中的資訊和事件記錄檔中的任何相關資訊，請連絡 Microsoft 產品支援服務。</span><span class="sxs-lookup"><span data-stu-id="ee257-123">Note the information in this message, and any relevant information in the event log, and contact Microsoft Product Support Services.</span></span>  

  <span data-ttu-id="ee257-124">如需詳細資訊，請參閱中的下列資源[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]幫助：</span><span class="sxs-lookup"><span data-stu-id="ee257-124">For more information, see the following resources in [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] Help:</span></span>  

- [<span data-ttu-id="ee257-125">密碼同步</span><span class="sxs-lookup"><span data-stu-id="ee257-125">Password Synchronization</span></span>](../core/password-synchronization2.md)
