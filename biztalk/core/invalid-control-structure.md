---
title: 無效的控制結構 |Microsoft Docs
ms.custom: ''
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 3f9bb104-7ea1-429a-8540-49f4d598fd46
caps.latest.revision: 8
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 46efe02beac27a055f32e5434dc5b9ac8313da5e
ms.sourcegitcommit: 266308ec5c6a9d8d80ff298ee6051b4843c5d626
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/27/2018
ms.locfileid: "37000079"
---
# <a name="invalid-control-structure"></a><span data-ttu-id="9a13c-102">無效的控制結構</span><span class="sxs-lookup"><span data-stu-id="9a13c-102">Invalid Control Structure</span></span>
## <a name="details"></a><span data-ttu-id="9a13c-103">詳細資料</span><span class="sxs-lookup"><span data-stu-id="9a13c-103">Details</span></span>  
  
|                 |                                                                                        |
|-----------------|----------------------------------------------------------------------------------------|
|  <span data-ttu-id="9a13c-104">產品名稱</span><span class="sxs-lookup"><span data-stu-id="9a13c-104">Product Name</span></span>   |   [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]   |
| <span data-ttu-id="9a13c-105">產品版本</span><span class="sxs-lookup"><span data-stu-id="9a13c-105">Product Version</span></span> |               [!INCLUDE[btsEDIVersion](../includes/btsediversion-md.md)]               |
|    <span data-ttu-id="9a13c-106">事件識別碼</span><span class="sxs-lookup"><span data-stu-id="9a13c-106">Event ID</span></span>     |                                           -                                            |
|  <span data-ttu-id="9a13c-107">事件來源</span><span class="sxs-lookup"><span data-stu-id="9a13c-107">Event Source</span></span>   | [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]<span data-ttu-id="9a13c-108"> EDI</span><span class="sxs-lookup"><span data-stu-id="9a13c-108"> EDI</span></span> |
|    <span data-ttu-id="9a13c-109">元件</span><span class="sxs-lookup"><span data-stu-id="9a13c-109">Component</span></span>    |                                       <span data-ttu-id="9a13c-110">將 EDI 引擎</span><span class="sxs-lookup"><span data-stu-id="9a13c-110">EDI Engine</span></span>                                       |
|  <span data-ttu-id="9a13c-111">符號名稱</span><span class="sxs-lookup"><span data-stu-id="9a13c-111">Symbolic Name</span></span>  |                        <span data-ttu-id="9a13c-112">X12Ta1InvalidControlStructureDescription</span><span class="sxs-lookup"><span data-stu-id="9a13c-112">X12Ta1InvalidControlStructureDescription</span></span>                        |
|  <span data-ttu-id="9a13c-113">訊息文字</span><span class="sxs-lookup"><span data-stu-id="9a13c-113">Message Text</span></span>   |                               <span data-ttu-id="9a13c-114">無效的控制結構</span><span class="sxs-lookup"><span data-stu-id="9a13c-114">Invalid Control Structure</span></span>                                |
  
## <a name="explanation"></a><span data-ttu-id="9a13c-115">說明</span><span class="sxs-lookup"><span data-stu-id="9a13c-115">Explanation</span></span>  
 <span data-ttu-id="9a13c-116">這個錯誤/警告/資訊事件表示 BizTalk Server 無法驗證對 TA1Schema TA1 通知的結構。</span><span class="sxs-lookup"><span data-stu-id="9a13c-116">This Error/Warning/Information event indicates that BizTalk Server could not validate the structure of the TA1 acknowledgment against the TA1Schema.</span></span>  
  
## <a name="user-action"></a><span data-ttu-id="9a13c-117">使用者動作</span><span class="sxs-lookup"><span data-stu-id="9a13c-117">User Action</span></span>  
 <span data-ttu-id="9a13c-118">若要解決這個錯誤，判斷為何 TA1 通知不會不符合 TA1Schema，並解決問題。</span><span class="sxs-lookup"><span data-stu-id="9a13c-118">To resolve this error, determine why the TA1 acknowledgment does not conform to the TA1Schema, and resolve the issue.</span></span>