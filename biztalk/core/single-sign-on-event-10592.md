---
title: 單一登入： 事件 10592 |Microsoft Docs
ms.custom: ''
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: e044f9bd-c384-4f08-81f0-699e0c774c45
caps.latest.revision: 6
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: b9fdf7259de2217c2e6cd616f58b3b1118bf991c
ms.sourcegitcommit: 266308ec5c6a9d8d80ff298ee6051b4843c5d626
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/27/2018
ms.locfileid: "37017254"
---
# <a name="single-sign-on-event-10592"></a><span data-ttu-id="cec03-102">單一登入： 事件 10592</span><span class="sxs-lookup"><span data-stu-id="cec03-102">Single Sign-On: Event 10592</span></span>
## <a name="details"></a><span data-ttu-id="cec03-103">詳細資料</span><span class="sxs-lookup"><span data-stu-id="cec03-103">Details</span></span>  
  
|                 |                                                                                                                                                    |
|-----------------|----------------------------------------------------------------------------------------------------------------------------------------------------|
|  <span data-ttu-id="cec03-104">產品名稱</span><span class="sxs-lookup"><span data-stu-id="cec03-104">Product Name</span></span>   |                                                             <span data-ttu-id="cec03-105">企業單一登入</span><span class="sxs-lookup"><span data-stu-id="cec03-105">Enterprise Single Sign-On</span></span>                                                              |
| <span data-ttu-id="cec03-106">產品版本</span><span class="sxs-lookup"><span data-stu-id="cec03-106">Product Version</span></span> |                                             [!INCLUDE[btsSSOVersion](../includes/btsssoversion-md.md)]                                             |
|    <span data-ttu-id="cec03-107">事件識別碼</span><span class="sxs-lookup"><span data-stu-id="cec03-107">Event ID</span></span>     |                                                                       <span data-ttu-id="cec03-108">10592</span><span class="sxs-lookup"><span data-stu-id="cec03-108">10592</span></span>                                                                        |
|  <span data-ttu-id="cec03-109">事件來源</span><span class="sxs-lookup"><span data-stu-id="cec03-109">Event Source</span></span>   |                                                                       <span data-ttu-id="cec03-110">ENTSSO</span><span class="sxs-lookup"><span data-stu-id="cec03-110">ENTSSO</span></span>                                                                       |
|    <span data-ttu-id="cec03-111">元件</span><span class="sxs-lookup"><span data-stu-id="cec03-111">Component</span></span>    |                                                                        <span data-ttu-id="cec03-112">不適用</span><span class="sxs-lookup"><span data-stu-id="cec03-112">N/A</span></span>                                                                         |
|  <span data-ttu-id="cec03-113">符號名稱</span><span class="sxs-lookup"><span data-stu-id="cec03-113">Symbolic Name</span></span>  |                                                           <span data-ttu-id="cec03-114">SSO_WARN_TICKET_DECRYPT_FAILED</span><span class="sxs-lookup"><span data-stu-id="cec03-114">SSO_WARN_TICKET_DECRYPT_FAILED</span></span>                                                           |
|  <span data-ttu-id="cec03-115">訊息文字</span><span class="sxs-lookup"><span data-stu-id="cec03-115">Message Text</span></span>   | <span data-ttu-id="cec03-116">票證無法解密。</span><span class="sxs-lookup"><span data-stu-id="cec03-116">The ticket could not be decrypted.</span></span> <span data-ttu-id="cec03-117">票證無效或它可能會有 expired.%r</span><span class="sxs-lookup"><span data-stu-id="cec03-117">The ticket is not valid or it may have expired.%r</span></span><br /><br /> <span data-ttu-id="cec03-118">應用程式名稱: %1 %r</span><span class="sxs-lookup"><span data-stu-id="cec03-118">Application Name: %1%r</span></span><br /><br /> <span data-ttu-id="cec03-119">錯誤碼： %2</span><span class="sxs-lookup"><span data-stu-id="cec03-119">Error Code: %2</span></span> |
  
## <a name="explanation"></a><span data-ttu-id="cec03-120">說明</span><span class="sxs-lookup"><span data-stu-id="cec03-120">Explanation</span></span>  
 <span data-ttu-id="cec03-121">票證無效，或可能已過期。</span><span class="sxs-lookup"><span data-stu-id="cec03-121">The ticket is not valid or may have expired.</span></span>  
  
## <a name="user-action"></a><span data-ttu-id="cec03-122">使用者動作</span><span class="sxs-lookup"><span data-stu-id="cec03-122">User Action</span></span>  
 <span data-ttu-id="cec03-123">請確認您想要使用的票證有效，且尚未過期。</span><span class="sxs-lookup"><span data-stu-id="cec03-123">Confirm that the ticket you want to use is valid and has not expired.</span></span>