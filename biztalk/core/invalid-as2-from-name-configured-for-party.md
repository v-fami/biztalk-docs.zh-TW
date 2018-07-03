---
title: 無效的 AS2-從設定合作對象的名稱 |Microsoft Docs
ms.custom: ''
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: cde739bd-f6f7-4e4a-8f02-9a99e9d82fc9
caps.latest.revision: 8
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 136e2e11d20560531bf0f34eb2c93429b6c50f33
ms.sourcegitcommit: 266308ec5c6a9d8d80ff298ee6051b4843c5d626
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/27/2018
ms.locfileid: "36999647"
---
# <a name="invalid-as2-from-name-configured-for-party"></a><span data-ttu-id="b99f3-102">無效的 AS2-從設定合作對象的名稱</span><span class="sxs-lookup"><span data-stu-id="b99f3-102">Invalid AS2-From name configured for Party</span></span>
## <a name="details"></a><span data-ttu-id="b99f3-103">詳細資料</span><span class="sxs-lookup"><span data-stu-id="b99f3-103">Details</span></span>  
  
|                 |                                                                                        |
|-----------------|----------------------------------------------------------------------------------------|
|  <span data-ttu-id="b99f3-104">產品名稱</span><span class="sxs-lookup"><span data-stu-id="b99f3-104">Product Name</span></span>   |   [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]   |
| <span data-ttu-id="b99f3-105">產品版本</span><span class="sxs-lookup"><span data-stu-id="b99f3-105">Product Version</span></span> |               [!INCLUDE[btsEDIVersion](../includes/btsediversion-md.md)]               |
|    <span data-ttu-id="b99f3-106">事件識別碼</span><span class="sxs-lookup"><span data-stu-id="b99f3-106">Event ID</span></span>     |                                           -                                            |
|  <span data-ttu-id="b99f3-107">事件來源</span><span class="sxs-lookup"><span data-stu-id="b99f3-107">Event Source</span></span>   | [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]<span data-ttu-id="b99f3-108"> EDI</span><span class="sxs-lookup"><span data-stu-id="b99f3-108"> EDI</span></span> |
|    <span data-ttu-id="b99f3-109">元件</span><span class="sxs-lookup"><span data-stu-id="b99f3-109">Component</span></span>    |                                       <span data-ttu-id="b99f3-110">AS2 引擎</span><span class="sxs-lookup"><span data-stu-id="b99f3-110">AS2 Engine</span></span>                                       |
|  <span data-ttu-id="b99f3-111">符號名稱</span><span class="sxs-lookup"><span data-stu-id="b99f3-111">Symbolic Name</span></span>  |                           <span data-ttu-id="b99f3-112">InvalidAS2FromNameConfiguredError</span><span class="sxs-lookup"><span data-stu-id="b99f3-112">InvalidAS2FromNameConfiguredError</span></span>                            |
|  <span data-ttu-id="b99f3-113">訊息文字</span><span class="sxs-lookup"><span data-stu-id="b99f3-113">Message Text</span></span>   |              <span data-ttu-id="b99f3-114">無效的 AS2-從設定合作對象的名稱：{0}值： {1}</span><span class="sxs-lookup"><span data-stu-id="b99f3-114">Invalid AS2-From name configured for Party: {0}   Value: {1}</span></span>              |
  
## <a name="explanation"></a><span data-ttu-id="b99f3-115">說明</span><span class="sxs-lookup"><span data-stu-id="b99f3-115">Explanation</span></span>  
 <span data-ttu-id="b99f3-116">這個錯誤/警告/資訊事件表示，AS2 編碼器或解碼器無法處理 AS2 訊息因為值的 AS2-From 標頭設定的已識別的合作對象不符合 AS2 RFC 4130 中的規格。</span><span class="sxs-lookup"><span data-stu-id="b99f3-116">This Error/Warning/Information event indicates that the AS2 encoder or decoder could not process the AS2 message because the value of the AS2-From header configured for the identified party did not conform to the specifications in AS2 RFC 4130.</span></span>  
  
## <a name="user-action"></a><span data-ttu-id="b99f3-117">使用者動作</span><span class="sxs-lookup"><span data-stu-id="b99f3-117">User Action</span></span>  
 <span data-ttu-id="b99f3-118">若要解決這個錯誤，請確定 AS2-From 標頭設定為合作對象符合 AS2 RFC 4130 第 6.2 部分中的規格，而且再有訊息重新傳送。</span><span class="sxs-lookup"><span data-stu-id="b99f3-118">To resolve this error, make sure that the AS2-From header configured for the party conforms to the specifications in section 6.2 of AS2 RFC 4130, and then have the message resent.</span></span>