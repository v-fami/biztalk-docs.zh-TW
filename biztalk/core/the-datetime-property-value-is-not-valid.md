---
title: 日期時間屬性值無效。 |Microsoft Docs
ms.custom: ''
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: a0dc527e-82d5-40dc-941e-f2e056163017
caps.latest.revision: 3
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 44cd97dc2cb185082ee2717d11ac7a09b9a0b66c
ms.sourcegitcommit: 266308ec5c6a9d8d80ff298ee6051b4843c5d626
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/27/2018
ms.locfileid: "36975407"
---
# <a name="the-datetime-property-value-is-not-valid"></a><span data-ttu-id="6bffa-102">日期時間屬性值無效</span><span class="sxs-lookup"><span data-stu-id="6bffa-102">The datetime property value is not valid</span></span>
## <a name="details"></a><span data-ttu-id="6bffa-103">詳細資料</span><span class="sxs-lookup"><span data-stu-id="6bffa-103">Details</span></span>  
  
|                 |                                                                                        |
|-----------------|----------------------------------------------------------------------------------------|
|  <span data-ttu-id="6bffa-104">產品名稱</span><span class="sxs-lookup"><span data-stu-id="6bffa-104">Product Name</span></span>   |   [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]   |
| <span data-ttu-id="6bffa-105">產品版本</span><span class="sxs-lookup"><span data-stu-id="6bffa-105">Product Version</span></span> |               [!INCLUDE[btsEDIVersion](../includes/btsediversion-md.md)]               |
|    <span data-ttu-id="6bffa-106">事件識別碼</span><span class="sxs-lookup"><span data-stu-id="6bffa-106">Event ID</span></span>     |                                           -                                            |
|  <span data-ttu-id="6bffa-107">事件來源</span><span class="sxs-lookup"><span data-stu-id="6bffa-107">Event Source</span></span>   | [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]<span data-ttu-id="6bffa-108"> EDI</span><span class="sxs-lookup"><span data-stu-id="6bffa-108"> EDI</span></span> |
|    <span data-ttu-id="6bffa-109">元件</span><span class="sxs-lookup"><span data-stu-id="6bffa-109">Component</span></span>    |                                       <span data-ttu-id="6bffa-110">將 EDI 引擎</span><span class="sxs-lookup"><span data-stu-id="6bffa-110">EDI Engine</span></span>                                       |
|  <span data-ttu-id="6bffa-111">符號名稱</span><span class="sxs-lookup"><span data-stu-id="6bffa-111">Symbolic Name</span></span>  |                                  <span data-ttu-id="6bffa-112">Err_InvalidDateTime</span><span class="sxs-lookup"><span data-stu-id="6bffa-112">Err_InvalidDateTime</span></span>                                   |
|  <span data-ttu-id="6bffa-113">訊息文字</span><span class="sxs-lookup"><span data-stu-id="6bffa-113">Message Text</span></span>   |                       <span data-ttu-id="6bffa-114">日期時間屬性值不是有效的。</span><span class="sxs-lookup"><span data-stu-id="6bffa-114">The datetime property value is not valid.</span></span>                        |
  
## <a name="explanation"></a><span data-ttu-id="6bffa-115">說明</span><span class="sxs-lookup"><span data-stu-id="6bffa-115">Explanation</span></span>  
 <span data-ttu-id="6bffa-116">這個錯誤/警告/資訊事件表示 BizTalk Server 無法嘗試決定是否要批次處理的訊息比較的內容屬性。</span><span class="sxs-lookup"><span data-stu-id="6bffa-116">This Error/Warning/Information event indicates BizTalk Server was unable to compare a context property while trying to decide whether to Batch a message.</span></span>  
  
## <a name="user-action"></a><span data-ttu-id="6bffa-117">使用者動作</span><span class="sxs-lookup"><span data-stu-id="6bffa-117">User Action</span></span>  
 <span data-ttu-id="6bffa-118">若要解決這個錯誤，確定作用中批次中提供的篩選條件不會指定日期的 XSD 類型的內容屬性的值是無效的日期。</span><span class="sxs-lookup"><span data-stu-id="6bffa-118">To resolve this error, ensure that the filter provided in Active batches doesn’t specify a context property which has an XSD type of date and the value is invalid date.</span></span>