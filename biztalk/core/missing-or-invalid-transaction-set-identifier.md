---
title: 遺漏或無效的交易集識別項 |Microsoft Docs
ms.custom: ''
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 282c8128-7d23-44e2-bf44-e90e52cb5fb1
caps.latest.revision: 8
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 0f0444468b7f7ff52b38bcd8db01a6bded5ed0a9
ms.sourcegitcommit: 266308ec5c6a9d8d80ff298ee6051b4843c5d626
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/27/2018
ms.locfileid: "37009927"
---
# <a name="missing-or-invalid-transaction-set-identifier"></a><span data-ttu-id="317f1-102">遺漏或無效的交易集識別項</span><span class="sxs-lookup"><span data-stu-id="317f1-102">Missing or invalid Transaction set identifier</span></span>
## <a name="details"></a><span data-ttu-id="317f1-103">詳細資料</span><span class="sxs-lookup"><span data-stu-id="317f1-103">Details</span></span>  
  
|                 |                                                                                        |
|-----------------|----------------------------------------------------------------------------------------|
|  <span data-ttu-id="317f1-104">產品名稱</span><span class="sxs-lookup"><span data-stu-id="317f1-104">Product Name</span></span>   |   [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]   |
| <span data-ttu-id="317f1-105">產品版本</span><span class="sxs-lookup"><span data-stu-id="317f1-105">Product Version</span></span> |               [!INCLUDE[btsEDIVersion](../includes/btsediversion-md.md)]               |
|    <span data-ttu-id="317f1-106">事件識別碼</span><span class="sxs-lookup"><span data-stu-id="317f1-106">Event ID</span></span>     |                                           -                                            |
|  <span data-ttu-id="317f1-107">事件來源</span><span class="sxs-lookup"><span data-stu-id="317f1-107">Event Source</span></span>   | [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]<span data-ttu-id="317f1-108"> EDI</span><span class="sxs-lookup"><span data-stu-id="317f1-108"> EDI</span></span> |
|    <span data-ttu-id="317f1-109">元件</span><span class="sxs-lookup"><span data-stu-id="317f1-109">Component</span></span>    |                                       <span data-ttu-id="317f1-110">將 EDI 引擎</span><span class="sxs-lookup"><span data-stu-id="317f1-110">EDI Engine</span></span>                                       |
|  <span data-ttu-id="317f1-111">符號名稱</span><span class="sxs-lookup"><span data-stu-id="317f1-111">Symbolic Name</span></span>  |                     <span data-ttu-id="317f1-112">EfactTsMissingOrInvalidTsIdentiferDescription</span><span class="sxs-lookup"><span data-stu-id="317f1-112">EfactTsMissingOrInvalidTsIdentiferDescription</span></span>                      |
|  <span data-ttu-id="317f1-113">訊息文字</span><span class="sxs-lookup"><span data-stu-id="317f1-113">Message Text</span></span>   |                     <span data-ttu-id="317f1-114">遺漏或無效的交易集識別項</span><span class="sxs-lookup"><span data-stu-id="317f1-114">Missing or invalid Transaction set identifier</span></span>                      |
  
## <a name="explanation"></a><span data-ttu-id="317f1-115">說明</span><span class="sxs-lookup"><span data-stu-id="317f1-115">Explanation</span></span>  
 <span data-ttu-id="317f1-116">這個錯誤/警告/資訊事件表示，接收管線或傳送管線無法處理 EDIFACT 交換因為 （在 [UNH2.1] 欄位中） 的交易集識別碼的值遺漏或具有無效的值。</span><span class="sxs-lookup"><span data-stu-id="317f1-116">This Error/Warning/Information event indicates that the receive or send pipeline could not process the EDIFACT interchange because the value of the transaction set identifier (in the UNH2.1 field) was missing or had an invalid value.</span></span>  
  
## <a name="user-action"></a><span data-ttu-id="317f1-117">使用者動作</span><span class="sxs-lookup"><span data-stu-id="317f1-117">User Action</span></span>  
 <span data-ttu-id="317f1-118">若要解決這個錯誤，請確定交換具有 [UNH2.1] 欄位的值。</span><span class="sxs-lookup"><span data-stu-id="317f1-118">To resolve this error, make sure that the interchange has a value for the UNH2.1 field.</span></span> <span data-ttu-id="317f1-119">請確認 UNH2.1 的值是有效的單位數以六位數文件類型指示項。</span><span class="sxs-lookup"><span data-stu-id="317f1-119">Verify that the value of UNH2.1 is a valid one-digit to six-digit document-type designator.</span></span>