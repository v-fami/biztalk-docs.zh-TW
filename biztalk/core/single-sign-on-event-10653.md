---
title: 單一登入： 事件 10653 |Microsoft Docs
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
ms.openlocfilehash: a9f0edb3ce5fa7f8fb59c4b65914a9c8b6640adc
ms.sourcegitcommit: 266308ec5c6a9d8d80ff298ee6051b4843c5d626
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/27/2018
ms.locfileid: "36969455"
---
# <a name="single-sign-on-event-10653"></a><span data-ttu-id="47337-102">單一登入： 事件 10653</span><span class="sxs-lookup"><span data-stu-id="47337-102">Single Sign-On: Event 10653</span></span>
## <a name="details"></a><span data-ttu-id="47337-103">詳細資料</span><span class="sxs-lookup"><span data-stu-id="47337-103">Details</span></span>  

|                 |                                                            |
|-----------------|------------------------------------------------------------|
|  <span data-ttu-id="47337-104">產品名稱</span><span class="sxs-lookup"><span data-stu-id="47337-104">Product Name</span></span>   |                 <span data-ttu-id="47337-105">企業單一登入</span><span class="sxs-lookup"><span data-stu-id="47337-105">Enterprise Single Sign-On</span></span>                  |
| <span data-ttu-id="47337-106">產品版本</span><span class="sxs-lookup"><span data-stu-id="47337-106">Product Version</span></span> | [!INCLUDE[btsSSOVersion](../includes/btsssoversion-md.md)] |
|    <span data-ttu-id="47337-107">事件識別碼</span><span class="sxs-lookup"><span data-stu-id="47337-107">Event ID</span></span>     |                           <span data-ttu-id="47337-108">10653</span><span class="sxs-lookup"><span data-stu-id="47337-108">10653</span></span>                            |
|  <span data-ttu-id="47337-109">事件來源</span><span class="sxs-lookup"><span data-stu-id="47337-109">Event Source</span></span>   |                           <span data-ttu-id="47337-110">ENTSSO</span><span class="sxs-lookup"><span data-stu-id="47337-110">ENTSSO</span></span>                           |
|    <span data-ttu-id="47337-111">元件</span><span class="sxs-lookup"><span data-stu-id="47337-111">Component</span></span>    |                            <span data-ttu-id="47337-112">N\A</span><span class="sxs-lookup"><span data-stu-id="47337-112">N\A</span></span>                             |
|  <span data-ttu-id="47337-113">符號名稱</span><span class="sxs-lookup"><span data-stu-id="47337-113">Symbolic Name</span></span>  |        <span data-ttu-id="47337-114">SSO_ERROR_PS_ADAPTER_CALLBACK_ACCESS_DENIED</span><span class="sxs-lookup"><span data-stu-id="47337-114">SSO_ERROR_PS_ADAPTER_CALLBACK_ACCESS_DENIED</span></span>         |
|  <span data-ttu-id="47337-115">訊息文字</span><span class="sxs-lookup"><span data-stu-id="47337-115">Message Text</span></span>   |    <span data-ttu-id="47337-116">密碼同步處理伺服器 （針對配接器） 存取 denied.%r</span><span class="sxs-lookup"><span data-stu-id="47337-116">Password sync server (for adapters) access denied.%r</span></span>    |

## <a name="explanation"></a><span data-ttu-id="47337-117">說明</span><span class="sxs-lookup"><span data-stu-id="47337-117">Explanation</span></span>  
 <span data-ttu-id="47337-118">這個錯誤事件表示用戶端嘗試連線到伺服器，但拒絕呼叫。</span><span class="sxs-lookup"><span data-stu-id="47337-118">This Error event indicates that a client attempted to contact the server but the call was refused.</span></span> <span data-ttu-id="47337-119">原因可能是由數項不同的原因，例如不正確的通訊協定或安全性權限不足。</span><span class="sxs-lookup"><span data-stu-id="47337-119">This can be caused by a number of different reasons, such as incorrect protocol or insufficient security permissions.</span></span>  

## <a name="user-action"></a><span data-ttu-id="47337-120">使用者動作</span><span class="sxs-lookup"><span data-stu-id="47337-120">User Action</span></span>  
 <span data-ttu-id="47337-121">若要解決這個錯誤，執行下列作業：</span><span class="sxs-lookup"><span data-stu-id="47337-121">To resolve this error, do the following:</span></span>  

- <span data-ttu-id="47337-122">請注意，此訊息中的資訊和事件記錄檔中的任何相關資訊，請連絡 Microsoft 產品支援服務。</span><span class="sxs-lookup"><span data-stu-id="47337-122">Note the information in this message, and any relevant information in the event log, and contact Microsoft Product Support Services.</span></span>  

  <span data-ttu-id="47337-123">如需詳細資訊，請參閱中的下列資源[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]幫助：</span><span class="sxs-lookup"><span data-stu-id="47337-123">For more information, see the following resources in [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] Help:</span></span>  

- [<span data-ttu-id="47337-124">密碼同步</span><span class="sxs-lookup"><span data-stu-id="47337-124">Password Synchronization</span></span>](../core/password-synchronization2.md)
