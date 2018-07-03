---
title: 處理交易集因為未設定 DocType 後所發生的錯誤 |Microsoft Docs
ms.custom: ''
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: a323658c-77d8-4059-aa15-d88c08e5450d
caps.latest.revision: 8
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: df010d497f61a14644c46f8b7f5cdfa183340615
ms.sourcegitcommit: 266308ec5c6a9d8d80ff298ee6051b4843c5d626
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/27/2018
ms.locfileid: "37003375"
---
# <a name="error-encountered-after-processing-transaction-sets-because-doctype-was-not-set"></a><span data-ttu-id="1de01-102">處理交易集因為未設定 DocType 後發生錯誤</span><span class="sxs-lookup"><span data-stu-id="1de01-102">Error encountered after processing Transaction Set(s) because DocType was not set</span></span>
## <a name="details"></a><span data-ttu-id="1de01-103">詳細資料</span><span class="sxs-lookup"><span data-stu-id="1de01-103">Details</span></span>  
  
|                 |                                                                                        |
|-----------------|----------------------------------------------------------------------------------------|
|  <span data-ttu-id="1de01-104">產品名稱</span><span class="sxs-lookup"><span data-stu-id="1de01-104">Product Name</span></span>   |   [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]   |
| <span data-ttu-id="1de01-105">產品版本</span><span class="sxs-lookup"><span data-stu-id="1de01-105">Product Version</span></span> |               [!INCLUDE[btsEDIVersion](../includes/btsediversion-md.md)]               |
|    <span data-ttu-id="1de01-106">事件識別碼</span><span class="sxs-lookup"><span data-stu-id="1de01-106">Event ID</span></span>     |                                           -                                            |
|  <span data-ttu-id="1de01-107">事件來源</span><span class="sxs-lookup"><span data-stu-id="1de01-107">Event Source</span></span>   | [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]<span data-ttu-id="1de01-108"> EDI</span><span class="sxs-lookup"><span data-stu-id="1de01-108"> EDI</span></span> |
|    <span data-ttu-id="1de01-109">元件</span><span class="sxs-lookup"><span data-stu-id="1de01-109">Component</span></span>    |                                       <span data-ttu-id="1de01-110">將 EDI 引擎</span><span class="sxs-lookup"><span data-stu-id="1de01-110">EDI Engine</span></span>                                       |
|  <span data-ttu-id="1de01-111">符號名稱</span><span class="sxs-lookup"><span data-stu-id="1de01-111">Symbolic Name</span></span>  |                                     <span data-ttu-id="1de01-112">DocTypeNotSet</span><span class="sxs-lookup"><span data-stu-id="1de01-112">DocTypeNotSet</span></span>                                      |
|  <span data-ttu-id="1de01-113">訊息文字</span><span class="sxs-lookup"><span data-stu-id="1de01-113">Message Text</span></span>   |     <span data-ttu-id="1de01-114">在處理之後所發生的錯誤{0}交易集。</span><span class="sxs-lookup"><span data-stu-id="1de01-114">Error encountered after processing {0} Transaction Set(s).</span></span> <span data-ttu-id="1de01-115">未設定 DocType</span><span class="sxs-lookup"><span data-stu-id="1de01-115">DocType was not set</span></span>     |
  
## <a name="explanation"></a><span data-ttu-id="1de01-116">說明</span><span class="sxs-lookup"><span data-stu-id="1de01-116">Explanation</span></span>  
 <span data-ttu-id="1de01-117">這個錯誤/警告/資訊事件表示 EDI 接收管線無法處理內送交易集，因為 ST01 (x12 交換) 或 UNH2.1 （適用於 EDIFACT 交換） 未設定為交易集。</span><span class="sxs-lookup"><span data-stu-id="1de01-117">This Error/Warning/Information event indicates that the EDI receive pipeline could not process an incoming transaction set because ST01 (for an X12 interchange) or UNH2.1 (for an EDIFACT interchange) was not set for the transaction set.</span></span>  
  
## <a name="user-action"></a><span data-ttu-id="1de01-118">使用者動作</span><span class="sxs-lookup"><span data-stu-id="1de01-118">User Action</span></span>  
 <span data-ttu-id="1de01-119">若要解決這個錯誤，請確認的交易集發生錯誤的 ST01 或 UNH1 區段，會設定為有效的文件類型。</span><span class="sxs-lookup"><span data-stu-id="1de01-119">To resolve this error, verify that the ST01 or UNH1 segment for the transaction set in error is set to a valid document type.</span></span>