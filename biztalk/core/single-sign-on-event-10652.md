---
title: 單一登入： 事件 10652 |Microsoft Docs
ms.custom: ''
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: ae7fe452-bcec-4722-8ec6-78d4fe462a0a
caps.latest.revision: 10
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: a2e27c678f2c031c642107cd770566f92d7ca708
ms.sourcegitcommit: 266308ec5c6a9d8d80ff298ee6051b4843c5d626
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/27/2018
ms.locfileid: "36985743"
---
# <a name="single-sign-on-event-10652"></a><span data-ttu-id="9c77a-102">單一登入： 事件 10652</span><span class="sxs-lookup"><span data-stu-id="9c77a-102">Single Sign-On: Event 10652</span></span>
## <a name="details"></a><span data-ttu-id="9c77a-103">詳細資料</span><span class="sxs-lookup"><span data-stu-id="9c77a-103">Details</span></span>  

|                 |                                                                           |
|-----------------|---------------------------------------------------------------------------|
|  <span data-ttu-id="9c77a-104">產品名稱</span><span class="sxs-lookup"><span data-stu-id="9c77a-104">Product Name</span></span>   |                         <span data-ttu-id="9c77a-105">企業單一登入</span><span class="sxs-lookup"><span data-stu-id="9c77a-105">Enterprise Single Sign-On</span></span>                         |
| <span data-ttu-id="9c77a-106">產品版本</span><span class="sxs-lookup"><span data-stu-id="9c77a-106">Product Version</span></span> |        [!INCLUDE[btsSSOVersion](../includes/btsssoversion-md.md)]         |
|    <span data-ttu-id="9c77a-107">事件識別碼</span><span class="sxs-lookup"><span data-stu-id="9c77a-107">Event ID</span></span>     |                                   <span data-ttu-id="9c77a-108">10652</span><span class="sxs-lookup"><span data-stu-id="9c77a-108">10652</span></span>                                   |
|  <span data-ttu-id="9c77a-109">事件來源</span><span class="sxs-lookup"><span data-stu-id="9c77a-109">Event Source</span></span>   |                                  <span data-ttu-id="9c77a-110">ENTSSO</span><span class="sxs-lookup"><span data-stu-id="9c77a-110">ENTSSO</span></span>                                   |
|    <span data-ttu-id="9c77a-111">元件</span><span class="sxs-lookup"><span data-stu-id="9c77a-111">Component</span></span>    |                                    <span data-ttu-id="9c77a-112">N\A</span><span class="sxs-lookup"><span data-stu-id="9c77a-112">N\A</span></span>                                    |
|  <span data-ttu-id="9c77a-113">符號名稱</span><span class="sxs-lookup"><span data-stu-id="9c77a-113">Symbolic Name</span></span>  |                   <span data-ttu-id="9c77a-114">SSO_ERROR_PASSWORD_SYNC_START_FAILED</span><span class="sxs-lookup"><span data-stu-id="9c77a-114">SSO_ERROR_PASSWORD_SYNC_START_FAILED</span></span>                    |
|  <span data-ttu-id="9c77a-115">訊息文字</span><span class="sxs-lookup"><span data-stu-id="9c77a-115">Message Text</span></span>   | <span data-ttu-id="9c77a-116">密碼同步處理服務無法 initialize.%r</span><span class="sxs-lookup"><span data-stu-id="9c77a-116">Password sync services failed to initialize.%r</span></span><br /><br /> <span data-ttu-id="9c77a-117">錯誤碼： %1</span><span class="sxs-lookup"><span data-stu-id="9c77a-117">Error Code: %1</span></span> |

## <a name="explanation"></a><span data-ttu-id="9c77a-118">說明</span><span class="sxs-lookup"><span data-stu-id="9c77a-118">Explanation</span></span>  
 <span data-ttu-id="9c77a-119">這個錯誤事件表示密碼同步處理服務無法啟動因為發生例外狀況。</span><span class="sxs-lookup"><span data-stu-id="9c77a-119">This Error event indicates that the Password Sync Service could not start due to an exception.</span></span>  

## <a name="user-action"></a><span data-ttu-id="9c77a-120">使用者動作</span><span class="sxs-lookup"><span data-stu-id="9c77a-120">User Action</span></span>  
 <span data-ttu-id="9c77a-121">若要解決這個錯誤，執行下列作業：</span><span class="sxs-lookup"><span data-stu-id="9c77a-121">To resolve this error, do the following:</span></span>  

- <span data-ttu-id="9c77a-122">請檢查 ENTSSO 或其他服務的相關錯誤的應用程式和系統事件記錄檔。</span><span class="sxs-lookup"><span data-stu-id="9c77a-122">Check both the Application and System event logs for related errors from ENTSSO or other services.</span></span>  

  <span data-ttu-id="9c77a-123">如需詳細資訊，請參閱中的下列資源[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]幫助：</span><span class="sxs-lookup"><span data-stu-id="9c77a-123">For more information, see the following resources in [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] Help:</span></span>  

- [<span data-ttu-id="9c77a-124">密碼同步</span><span class="sxs-lookup"><span data-stu-id="9c77a-124">Password Synchronization</span></span>](../core/password-synchronization2.md)
