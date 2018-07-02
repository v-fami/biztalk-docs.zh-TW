---
title: 不是唯一分隔符號 |Microsoft Docs
ms.custom: ''
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 1c37cc55-8923-4124-9004-91ee5093df9c
caps.latest.revision: 9
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 0d724533fb89d3f4d43654aadaf43094adb80e06
ms.sourcegitcommit: 266308ec5c6a9d8d80ff298ee6051b4843c5d626
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/27/2018
ms.locfileid: "36966741"
---
# <a name="delimiters-are-not-unique"></a><span data-ttu-id="1d608-102">不是唯一分隔符號</span><span class="sxs-lookup"><span data-stu-id="1d608-102">Delimiters are not unique</span></span>
## <a name="details"></a><span data-ttu-id="1d608-103">詳細資料</span><span class="sxs-lookup"><span data-stu-id="1d608-103">Details</span></span>  
  
|                 |                                                                                        |
|-----------------|----------------------------------------------------------------------------------------|
|  <span data-ttu-id="1d608-104">產品名稱</span><span class="sxs-lookup"><span data-stu-id="1d608-104">Product Name</span></span>   |   [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]   |
| <span data-ttu-id="1d608-105">產品版本</span><span class="sxs-lookup"><span data-stu-id="1d608-105">Product Version</span></span> |               [!INCLUDE[btsEDIVersion](../includes/btsediversion-md.md)]               |
|    <span data-ttu-id="1d608-106">事件識別碼</span><span class="sxs-lookup"><span data-stu-id="1d608-106">Event ID</span></span>     |                                           -                                            |
|  <span data-ttu-id="1d608-107">事件來源</span><span class="sxs-lookup"><span data-stu-id="1d608-107">Event Source</span></span>   | [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]<span data-ttu-id="1d608-108"> EDI</span><span class="sxs-lookup"><span data-stu-id="1d608-108"> EDI</span></span> |
|    <span data-ttu-id="1d608-109">元件</span><span class="sxs-lookup"><span data-stu-id="1d608-109">Component</span></span>    |                                       <span data-ttu-id="1d608-110">將 EDI 引擎</span><span class="sxs-lookup"><span data-stu-id="1d608-110">EDI Engine</span></span>                                       |
|  <span data-ttu-id="1d608-111">符號名稱</span><span class="sxs-lookup"><span data-stu-id="1d608-111">Symbolic Name</span></span>  |                                           -                                            |
|  <span data-ttu-id="1d608-112">訊息文字</span><span class="sxs-lookup"><span data-stu-id="1d608-112">Message Text</span></span>   |                               <span data-ttu-id="1d608-113">不是唯一分隔符號</span><span class="sxs-lookup"><span data-stu-id="1d608-113">Delimiters are not unique</span></span>                                |
  
## <a name="explanation"></a><span data-ttu-id="1d608-114">說明</span><span class="sxs-lookup"><span data-stu-id="1d608-114">Explanation</span></span>  
 <span data-ttu-id="1d608-115">這個錯誤/警告/資訊事件表示，EDI 傳送管線無法處理外寄交換因為兩個或多個分隔符號在交換中，識別與用來區隔的交換、 facet 都相同。</span><span class="sxs-lookup"><span data-stu-id="1d608-115">This Error/Warning/Information event indicates that the EDI send pipeline could not process an outgoing interchange because two or more of the separators identified in the interchange, and used to separate facets of the interchange, were the same.</span></span> <span data-ttu-id="1d608-116">分隔符號都會列在 ISA 區段的 X12 交換和 EDIFACT 的 UNA 區段中交換。</span><span class="sxs-lookup"><span data-stu-id="1d608-116">The separators are identified in the ISA segment of an X12 interchange and in the UNA segment of an EDIFACT interchange.</span></span> <span data-ttu-id="1d608-117">具有相同值的兩個或多個分隔符號可能會發生在保留批次案例中，或如果交換是透過通過傳輸接收，然後挑選最多的傳送埠即 MessageBox 中的 XML 檔案。</span><span class="sxs-lookup"><span data-stu-id="1d608-117">Two or more separators with the same value can occur in a preserved batch scenario, or if an interchange is received via a passthrough transmit and then picked up by the send port as an XML file in the MessageBox.</span></span> <span data-ttu-id="1d608-118">這個錯誤狀況會導致失敗之交換的處理。</span><span class="sxs-lookup"><span data-stu-id="1d608-118">This error condition will cause processing of the interchange to fail.</span></span>  
  
## <a name="user-action"></a><span data-ttu-id="1d608-119">使用者動作</span><span class="sxs-lookup"><span data-stu-id="1d608-119">User Action</span></span>  
 <span data-ttu-id="1d608-120">若要解決這個錯誤，找出在交換中使用的分隔符號有相同的值，並變更其中一個分隔符號的值。</span><span class="sxs-lookup"><span data-stu-id="1d608-120">To resolve this error, identify which separators in the interchange have the same value, and change the value of one of the separators.</span></span>