---
title: 單一登入： 事件 10705 |Microsoft Docs
ms.custom: ''
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 81456bdd-dfd8-4483-aa76-5ec72350cc70
caps.latest.revision: 12
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: c74e4ebe0119698348668eb2ca6f78b5697cc5d0
ms.sourcegitcommit: 266308ec5c6a9d8d80ff298ee6051b4843c5d626
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/27/2018
ms.locfileid: "36976895"
---
# <a name="single-sign-on-event-10705"></a><span data-ttu-id="26aca-102">單一登入： 事件 10705</span><span class="sxs-lookup"><span data-stu-id="26aca-102">Single Sign-On: Event 10705</span></span>
## <a name="details"></a><span data-ttu-id="26aca-103">詳細資料</span><span class="sxs-lookup"><span data-stu-id="26aca-103">Details</span></span>  

|                 |                                                                                                            |
|-----------------|------------------------------------------------------------------------------------------------------------|
|  <span data-ttu-id="26aca-104">產品名稱</span><span class="sxs-lookup"><span data-stu-id="26aca-104">Product Name</span></span>   |                                         <span data-ttu-id="26aca-105">企業單一登入</span><span class="sxs-lookup"><span data-stu-id="26aca-105">Enterprise Single Sign-On</span></span>                                          |
| <span data-ttu-id="26aca-106">產品版本</span><span class="sxs-lookup"><span data-stu-id="26aca-106">Product Version</span></span> |                         [!INCLUDE[btsSSOVersion](../includes/btsssoversion-md.md)]                         |
|    <span data-ttu-id="26aca-107">事件識別碼</span><span class="sxs-lookup"><span data-stu-id="26aca-107">Event ID</span></span>     |                                                   <span data-ttu-id="26aca-108">10705</span><span class="sxs-lookup"><span data-stu-id="26aca-108">10705</span></span>                                                    |
|  <span data-ttu-id="26aca-109">事件來源</span><span class="sxs-lookup"><span data-stu-id="26aca-109">Event Source</span></span>   |                                                   <span data-ttu-id="26aca-110">ENTSSO</span><span class="sxs-lookup"><span data-stu-id="26aca-110">ENTSSO</span></span>                                                   |
|    <span data-ttu-id="26aca-111">元件</span><span class="sxs-lookup"><span data-stu-id="26aca-111">Component</span></span>    |                                                    <span data-ttu-id="26aca-112">N\A</span><span class="sxs-lookup"><span data-stu-id="26aca-112">N\A</span></span>                                                     |
|  <span data-ttu-id="26aca-113">符號名稱</span><span class="sxs-lookup"><span data-stu-id="26aca-113">Symbolic Name</span></span>  |                                          <span data-ttu-id="26aca-114">SSO_WARN_PS_NOT_ADAPTER</span><span class="sxs-lookup"><span data-stu-id="26aca-114">SSO_WARN_PS_NOT_ADAPTER</span></span>                                           |
|  <span data-ttu-id="26aca-115">訊息文字</span><span class="sxs-lookup"><span data-stu-id="26aca-115">Message Text</span></span>   | <span data-ttu-id="26aca-116">指定的配接器不是配接器應用程式。</span><span class="sxs-lookup"><span data-stu-id="26aca-116">The specified adapter is not an adapter application.</span></span> <span data-ttu-id="26aca-117">檢查應用程式 type.%r</span><span class="sxs-lookup"><span data-stu-id="26aca-117">Check the application type.%r</span></span><br /><br /> <span data-ttu-id="26aca-118">配接器： %1</span><span class="sxs-lookup"><span data-stu-id="26aca-118">Adapter: %1</span></span> |

## <a name="explanation"></a><span data-ttu-id="26aca-119">說明</span><span class="sxs-lookup"><span data-stu-id="26aca-119">Explanation</span></span>  
 <span data-ttu-id="26aca-120">這個警告事件表示指定的配接器不是配接器應用程式。</span><span class="sxs-lookup"><span data-stu-id="26aca-120">This Warning event indicates that the specified adapter is not an adapter application.</span></span>  

## <a name="user-action"></a><span data-ttu-id="26aca-121">使用者動作</span><span class="sxs-lookup"><span data-stu-id="26aca-121">User Action</span></span>  
 <span data-ttu-id="26aca-122">若要解決這個警告，執行下列作業：</span><span class="sxs-lookup"><span data-stu-id="26aca-122">To resolve this warning, do the following:</span></span>  

- <span data-ttu-id="26aca-123">使用 SSO 管理 MMC 嵌入式管理單元，以滑鼠右鍵按一下指定的配接器，然後按一下 屬性來判斷應用程式類型，或使用命令列工具 ssops-清單和 ssops-顯示畫面來判斷應用程式類型。</span><span class="sxs-lookup"><span data-stu-id="26aca-123">Use the SSO Admin MMC Snap-In, right click the specified adapter, and then click Properties to determine the application type or use the command line tool  ssops -list and ssops -display to determine the application type.</span></span>  

- <span data-ttu-id="26aca-124">您可以使用 SSO 管理 MMC 嵌入式管理單元或 ssops-addapp，設定配接器應用程式。</span><span class="sxs-lookup"><span data-stu-id="26aca-124">Use the SSO Admin MMC Snap-In or ssops -addapp to set the adapter application.</span></span>  

  <span data-ttu-id="26aca-125">如需詳細資訊，請參閱下列資源：</span><span class="sxs-lookup"><span data-stu-id="26aca-125">For more information, see the following resources:</span></span>  

- [<span data-ttu-id="26aca-126">如何管理密碼同步處理</span><span class="sxs-lookup"><span data-stu-id="26aca-126">How to Administer Password Synchronization</span></span>](../core/how-to-administer-password-synchronization.md)
