---
title: 單一登入： 事件 10653 |Microsoft 文件
ms.custom: ''
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: a0d85aca-20d9-4d65-8834-b31eacf143c8
caps.latest.revision: 13
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 91ec21a7883c3c1d3e97519f9239050ea18035fd
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/20/2017
ms.locfileid: "22271798"
---
# <a name="single-sign-on-event-10653"></a><span data-ttu-id="1da11-102">單一登入： 事件 10653</span><span class="sxs-lookup"><span data-stu-id="1da11-102">Single Sign-On: Event 10653</span></span>
## <a name="details"></a><span data-ttu-id="1da11-103">詳細資料</span><span class="sxs-lookup"><span data-stu-id="1da11-103">Details</span></span>  
  
|||  
|-|-|  
|<span data-ttu-id="1da11-104">產品名稱</span><span class="sxs-lookup"><span data-stu-id="1da11-104">Product Name</span></span>|<span data-ttu-id="1da11-105">企業單一登入</span><span class="sxs-lookup"><span data-stu-id="1da11-105">Enterprise Single Sign-On</span></span>|  
|<span data-ttu-id="1da11-106">產品版本</span><span class="sxs-lookup"><span data-stu-id="1da11-106">Product Version</span></span>|[!INCLUDE[btsSSOVersion](../includes/btsssoversion-md.md)]|  
|<span data-ttu-id="1da11-107">事件識別碼</span><span class="sxs-lookup"><span data-stu-id="1da11-107">Event ID</span></span>|<span data-ttu-id="1da11-108">10653</span><span class="sxs-lookup"><span data-stu-id="1da11-108">10653</span></span>|  
|<span data-ttu-id="1da11-109">事件來源</span><span class="sxs-lookup"><span data-stu-id="1da11-109">Event Source</span></span>|<span data-ttu-id="1da11-110">ENTSSO</span><span class="sxs-lookup"><span data-stu-id="1da11-110">ENTSSO</span></span>|  
|<span data-ttu-id="1da11-111">元件</span><span class="sxs-lookup"><span data-stu-id="1da11-111">Component</span></span>|<span data-ttu-id="1da11-112">N\A</span><span class="sxs-lookup"><span data-stu-id="1da11-112">N\A</span></span>|  
|<span data-ttu-id="1da11-113">符號名稱</span><span class="sxs-lookup"><span data-stu-id="1da11-113">Symbolic Name</span></span>|<span data-ttu-id="1da11-114">SSO_ERROR_PS_ADAPTER_CALLBACK_ACCESS_DENIED</span><span class="sxs-lookup"><span data-stu-id="1da11-114">SSO_ERROR_PS_ADAPTER_CALLBACK_ACCESS_DENIED</span></span>|  
|<span data-ttu-id="1da11-115">訊息文字</span><span class="sxs-lookup"><span data-stu-id="1da11-115">Message Text</span></span>|<span data-ttu-id="1da11-116">密碼同步伺服器 （針對配接器） 存取 denied.%r</span><span class="sxs-lookup"><span data-stu-id="1da11-116">Password sync server (for adapters) access denied.%r</span></span>|  
  
## <a name="explanation"></a><span data-ttu-id="1da11-117">說明</span><span class="sxs-lookup"><span data-stu-id="1da11-117">Explanation</span></span>  
 <span data-ttu-id="1da11-118">這個錯誤事件表示用戶端嘗試連線到伺服器，但呼叫被拒絕。</span><span class="sxs-lookup"><span data-stu-id="1da11-118">This Error event indicates that a client attempted to contact the server but the call was refused.</span></span> <span data-ttu-id="1da11-119">原因可能是由數種不同原因，例如不正確的通訊協定或安全性權限不足。</span><span class="sxs-lookup"><span data-stu-id="1da11-119">This can be caused by a number of different reasons, such as incorrect protocol or insufficient security permissions.</span></span>  
  
## <a name="user-action"></a><span data-ttu-id="1da11-120">使用者動作</span><span class="sxs-lookup"><span data-stu-id="1da11-120">User Action</span></span>  
 <span data-ttu-id="1da11-121">若要解決這個錯誤，執行下列作業：</span><span class="sxs-lookup"><span data-stu-id="1da11-121">To resolve this error, do the following:</span></span>  
  
-   <span data-ttu-id="1da11-122">請注意，此訊息中的資訊和事件記錄檔中的任何相關資訊，請連絡 Microsoft 產品支援服務。</span><span class="sxs-lookup"><span data-stu-id="1da11-122">Note the information in this message, and any relevant information in the event log, and contact Microsoft Product Support Services.</span></span>  
  
 <span data-ttu-id="1da11-123">如需詳細資訊，請參閱中的下列資源[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]協助：</span><span class="sxs-lookup"><span data-stu-id="1da11-123">For more information, see the following resources in [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] Help:</span></span>  
  
-   [<span data-ttu-id="1da11-124">密碼同步處理</span><span class="sxs-lookup"><span data-stu-id="1da11-124">Password Synchronization</span></span>](../core/password-synchronization2.md)