---
title: "單一登入： 事件 10654 |Microsoft 文件"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 49372d5a-8136-4bdd-8004-b5736ddbe058
caps.latest.revision: "10"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 06d7de49ec1606c7c0a33f802af11af4e8ad2848
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/20/2017
---
# <a name="single-sign-on-event-10654"></a><span data-ttu-id="97564-102">單一登入： 事件 10654</span><span class="sxs-lookup"><span data-stu-id="97564-102">Single Sign-On: Event 10654</span></span>
## <a name="details"></a><span data-ttu-id="97564-103">詳細資料</span><span class="sxs-lookup"><span data-stu-id="97564-103">Details</span></span>  
  
|||  
|-|-|  
|<span data-ttu-id="97564-104">產品名稱</span><span class="sxs-lookup"><span data-stu-id="97564-104">Product Name</span></span>|<span data-ttu-id="97564-105">企業單一登入</span><span class="sxs-lookup"><span data-stu-id="97564-105">Enterprise Single Sign-On</span></span>|  
|<span data-ttu-id="97564-106">產品版本</span><span class="sxs-lookup"><span data-stu-id="97564-106">Product Version</span></span>|[!INCLUDE[btsSSOVersion](../includes/btsssoversion-md.md)]|  
|<span data-ttu-id="97564-107">事件識別碼</span><span class="sxs-lookup"><span data-stu-id="97564-107">Event ID</span></span>|<span data-ttu-id="97564-108">10654</span><span class="sxs-lookup"><span data-stu-id="97564-108">10654</span></span>|  
|<span data-ttu-id="97564-109">事件來源</span><span class="sxs-lookup"><span data-stu-id="97564-109">Event Source</span></span>|<span data-ttu-id="97564-110">ENTSSO</span><span class="sxs-lookup"><span data-stu-id="97564-110">ENTSSO</span></span>|  
|<span data-ttu-id="97564-111">元件</span><span class="sxs-lookup"><span data-stu-id="97564-111">Component</span></span>|<span data-ttu-id="97564-112">N\A</span><span class="sxs-lookup"><span data-stu-id="97564-112">N\A</span></span>|  
|<span data-ttu-id="97564-113">符號名稱</span><span class="sxs-lookup"><span data-stu-id="97564-113">Symbolic Name</span></span>|<span data-ttu-id="97564-114">SSO_ERROR_PS_WINDOWS_CALLBACK_ACCESS_DENIED</span><span class="sxs-lookup"><span data-stu-id="97564-114">SSO_ERROR_PS_WINDOWS_CALLBACK_ACCESS_DENIED</span></span>|  
|<span data-ttu-id="97564-115">訊息文字</span><span class="sxs-lookup"><span data-stu-id="97564-115">Message Text</span></span>|<span data-ttu-id="97564-116">密碼同步伺服器 (針對 Windows) 存取遭拒。%r</span><span class="sxs-lookup"><span data-stu-id="97564-116">Password sync server (for Windows) access denied.%r</span></span>|  
  
## <a name="explanation"></a><span data-ttu-id="97564-117">說明</span><span class="sxs-lookup"><span data-stu-id="97564-117">Explanation</span></span>  
 <span data-ttu-id="97564-118">這個錯誤事件表示訊息已傳送至 [name] 伺服器，但回覆遭到封鎖。</span><span class="sxs-lookup"><span data-stu-id="97564-118">This Error event indicates that a message was sent to the [name] server but the reply was blocked.</span></span> <span data-ttu-id="97564-119">原因可能是由數種不同原因，例如不正確的通訊協定或安全性權限不足的伺服器上。</span><span class="sxs-lookup"><span data-stu-id="97564-119">This can be caused by a number of different reasons, such as incorrect protocol or insufficient security permissions on the server.</span></span>  
  
## <a name="user-action"></a><span data-ttu-id="97564-120">使用者動作</span><span class="sxs-lookup"><span data-stu-id="97564-120">User Action</span></span>  
 <span data-ttu-id="97564-121">若要解決這個錯誤，執行下列作業：</span><span class="sxs-lookup"><span data-stu-id="97564-121">To resolve this error, do the following:</span></span>  
  
-   <span data-ttu-id="97564-122">請注意，此訊息中的資訊和事件記錄檔中的任何相關資訊，請連絡 Microsoft 產品支援服務。</span><span class="sxs-lookup"><span data-stu-id="97564-122">Note the information in this message, and any relevant information in the event log, and contact Microsoft Product Support Services.</span></span>  
  
 <span data-ttu-id="97564-123">如需詳細資訊，請參閱中的下列資源[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]協助：</span><span class="sxs-lookup"><span data-stu-id="97564-123">For more information, see the following resources in [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] Help:</span></span>  
  
-   [<span data-ttu-id="97564-124">密碼同步處理</span><span class="sxs-lookup"><span data-stu-id="97564-124">Password Synchronization</span></span>](../core/password-synchronization2.md)