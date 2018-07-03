---
title: 整數屬性值無效。 |Microsoft Docs
ms.custom: ''
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 31d4e9a7-4336-40f1-997a-9f79d86b26d2
caps.latest.revision: 3
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 0f376cb7742aed676d8f834f2fa7f813f6754854
ms.sourcegitcommit: 266308ec5c6a9d8d80ff298ee6051b4843c5d626
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/27/2018
ms.locfileid: "37024388"
---
# <a name="the-integer-property-value-is-not-valid"></a><span data-ttu-id="2e7c1-102">整數屬性值無效</span><span class="sxs-lookup"><span data-stu-id="2e7c1-102">The integer property value is not valid</span></span>
## <a name="details"></a><span data-ttu-id="2e7c1-103">詳細資料</span><span class="sxs-lookup"><span data-stu-id="2e7c1-103">Details</span></span>  
  
|                 |                                                                                        |
|-----------------|----------------------------------------------------------------------------------------|
|  <span data-ttu-id="2e7c1-104">產品名稱</span><span class="sxs-lookup"><span data-stu-id="2e7c1-104">Product Name</span></span>   |   [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]   |
| <span data-ttu-id="2e7c1-105">產品版本</span><span class="sxs-lookup"><span data-stu-id="2e7c1-105">Product Version</span></span> |               [!INCLUDE[btsEDIVersion](../includes/btsediversion-md.md)]               |
|    <span data-ttu-id="2e7c1-106">事件識別碼</span><span class="sxs-lookup"><span data-stu-id="2e7c1-106">Event ID</span></span>     |                                           -                                            |
|  <span data-ttu-id="2e7c1-107">事件來源</span><span class="sxs-lookup"><span data-stu-id="2e7c1-107">Event Source</span></span>   | [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]<span data-ttu-id="2e7c1-108"> EDI</span><span class="sxs-lookup"><span data-stu-id="2e7c1-108"> EDI</span></span> |
|    <span data-ttu-id="2e7c1-109">元件</span><span class="sxs-lookup"><span data-stu-id="2e7c1-109">Component</span></span>    |                                       <span data-ttu-id="2e7c1-110">將 EDI 引擎</span><span class="sxs-lookup"><span data-stu-id="2e7c1-110">EDI Engine</span></span>                                       |
|  <span data-ttu-id="2e7c1-111">符號名稱</span><span class="sxs-lookup"><span data-stu-id="2e7c1-111">Symbolic Name</span></span>  |                                   <span data-ttu-id="2e7c1-112">Err_InvalidInteger</span><span class="sxs-lookup"><span data-stu-id="2e7c1-112">Err_InvalidInteger</span></span>                                   |
|  <span data-ttu-id="2e7c1-113">訊息文字</span><span class="sxs-lookup"><span data-stu-id="2e7c1-113">Message Text</span></span>   |                        <span data-ttu-id="2e7c1-114">整數屬性值不是有效的。</span><span class="sxs-lookup"><span data-stu-id="2e7c1-114">The integer property value is not valid.</span></span>                        |
  
## <a name="explanation"></a><span data-ttu-id="2e7c1-115">說明</span><span class="sxs-lookup"><span data-stu-id="2e7c1-115">Explanation</span></span>  
 <span data-ttu-id="2e7c1-116">這個錯誤/警告/資訊事件表示 BizTalk Server 無法嘗試決定是否要批次處理的訊息比較的內容屬性。</span><span class="sxs-lookup"><span data-stu-id="2e7c1-116">This Error/Warning/Information event indicates BizTalk Server was unable to compare a context property while trying to decide whether to Batch a message.</span></span>  
  
## <a name="user-action"></a><span data-ttu-id="2e7c1-117">使用者動作</span><span class="sxs-lookup"><span data-stu-id="2e7c1-117">User Action</span></span>  
 <span data-ttu-id="2e7c1-118">若要解決這個錯誤，請確定在作用中批次中提供的篩選條件未指定內容屬性的 XSD 類型為整數值無效。</span><span class="sxs-lookup"><span data-stu-id="2e7c1-118">To resolve this error, ensure that the filter provided in Active batches doesn’t specify a context property which has an XSD type of integer with an invalid value.</span></span>