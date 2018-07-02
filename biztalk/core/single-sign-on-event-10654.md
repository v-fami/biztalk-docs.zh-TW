---
title: 單一登入： 事件 10654 |Microsoft Docs
ms.custom: ''
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 49372d5a-8136-4bdd-8004-b5736ddbe058
caps.latest.revision: 10
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 6ca59040b340d033ab6c355c0440378f09d87000
ms.sourcegitcommit: 266308ec5c6a9d8d80ff298ee6051b4843c5d626
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/27/2018
ms.locfileid: "36974479"
---
# <a name="single-sign-on-event-10654"></a><span data-ttu-id="b9a7f-102">單一登入： 事件 10654</span><span class="sxs-lookup"><span data-stu-id="b9a7f-102">Single Sign-On: Event 10654</span></span>
## <a name="details"></a><span data-ttu-id="b9a7f-103">詳細資料</span><span class="sxs-lookup"><span data-stu-id="b9a7f-103">Details</span></span>  

|                 |                                                            |
|-----------------|------------------------------------------------------------|
|  <span data-ttu-id="b9a7f-104">產品名稱</span><span class="sxs-lookup"><span data-stu-id="b9a7f-104">Product Name</span></span>   |                 <span data-ttu-id="b9a7f-105">企業單一登入</span><span class="sxs-lookup"><span data-stu-id="b9a7f-105">Enterprise Single Sign-On</span></span>                  |
| <span data-ttu-id="b9a7f-106">產品版本</span><span class="sxs-lookup"><span data-stu-id="b9a7f-106">Product Version</span></span> | [!INCLUDE[btsSSOVersion](../includes/btsssoversion-md.md)] |
|    <span data-ttu-id="b9a7f-107">事件識別碼</span><span class="sxs-lookup"><span data-stu-id="b9a7f-107">Event ID</span></span>     |                           <span data-ttu-id="b9a7f-108">10654</span><span class="sxs-lookup"><span data-stu-id="b9a7f-108">10654</span></span>                            |
|  <span data-ttu-id="b9a7f-109">事件來源</span><span class="sxs-lookup"><span data-stu-id="b9a7f-109">Event Source</span></span>   |                           <span data-ttu-id="b9a7f-110">ENTSSO</span><span class="sxs-lookup"><span data-stu-id="b9a7f-110">ENTSSO</span></span>                           |
|    <span data-ttu-id="b9a7f-111">元件</span><span class="sxs-lookup"><span data-stu-id="b9a7f-111">Component</span></span>    |                            <span data-ttu-id="b9a7f-112">N\A</span><span class="sxs-lookup"><span data-stu-id="b9a7f-112">N\A</span></span>                             |
|  <span data-ttu-id="b9a7f-113">符號名稱</span><span class="sxs-lookup"><span data-stu-id="b9a7f-113">Symbolic Name</span></span>  |        <span data-ttu-id="b9a7f-114">SSO_ERROR_PS_WINDOWS_CALLBACK_ACCESS_DENIED</span><span class="sxs-lookup"><span data-stu-id="b9a7f-114">SSO_ERROR_PS_WINDOWS_CALLBACK_ACCESS_DENIED</span></span>         |
|  <span data-ttu-id="b9a7f-115">訊息文字</span><span class="sxs-lookup"><span data-stu-id="b9a7f-115">Message Text</span></span>   |    <span data-ttu-id="b9a7f-116">密碼同步伺服器 (針對 Windows) 存取遭拒。%r</span><span class="sxs-lookup"><span data-stu-id="b9a7f-116">Password sync server (for Windows) access denied.%r</span></span>     |

## <a name="explanation"></a><span data-ttu-id="b9a7f-117">說明</span><span class="sxs-lookup"><span data-stu-id="b9a7f-117">Explanation</span></span>  
 <span data-ttu-id="b9a7f-118">這個錯誤事件表示訊息傳送至 [名稱] 伺服器，但已封鎖的回覆。</span><span class="sxs-lookup"><span data-stu-id="b9a7f-118">This Error event indicates that a message was sent to the [name] server but the reply was blocked.</span></span> <span data-ttu-id="b9a7f-119">原因可能是由數項不同的原因，例如不正確的通訊協定或在伺服器上沒有足夠的安全性權限。</span><span class="sxs-lookup"><span data-stu-id="b9a7f-119">This can be caused by a number of different reasons, such as incorrect protocol or insufficient security permissions on the server.</span></span>  

## <a name="user-action"></a><span data-ttu-id="b9a7f-120">使用者動作</span><span class="sxs-lookup"><span data-stu-id="b9a7f-120">User Action</span></span>  
 <span data-ttu-id="b9a7f-121">若要解決這個錯誤，執行下列作業：</span><span class="sxs-lookup"><span data-stu-id="b9a7f-121">To resolve this error, do the following:</span></span>  

- <span data-ttu-id="b9a7f-122">請注意，此訊息中的資訊和事件記錄檔中的任何相關資訊，請連絡 Microsoft 產品支援服務。</span><span class="sxs-lookup"><span data-stu-id="b9a7f-122">Note the information in this message, and any relevant information in the event log, and contact Microsoft Product Support Services.</span></span>  

  <span data-ttu-id="b9a7f-123">如需詳細資訊，請參閱中的下列資源[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]幫助：</span><span class="sxs-lookup"><span data-stu-id="b9a7f-123">For more information, see the following resources in [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] Help:</span></span>  

- [<span data-ttu-id="b9a7f-124">密碼同步</span><span class="sxs-lookup"><span data-stu-id="b9a7f-124">Password Synchronization</span></span>](../core/password-synchronization2.md)
