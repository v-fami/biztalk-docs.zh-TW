---
title: 布林屬性值無效。 |Microsoft Docs
ms.custom: ''
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 62b6c178-f8ea-451a-b2dc-9396c24c0f5b
caps.latest.revision: 8
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 3fd5b3713c5570b3580abbb71d51d8dabf422c24
ms.sourcegitcommit: 266308ec5c6a9d8d80ff298ee6051b4843c5d626
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/27/2018
ms.locfileid: "37001159"
---
# <a name="the-boolean-property-value-is-not-valid"></a><span data-ttu-id="2789a-102">布林屬性值無效</span><span class="sxs-lookup"><span data-stu-id="2789a-102">The boolean property value is not valid</span></span>
## <a name="details"></a><span data-ttu-id="2789a-103">詳細資料</span><span class="sxs-lookup"><span data-stu-id="2789a-103">Details</span></span>  
  
|                 |                                                                                        |
|-----------------|----------------------------------------------------------------------------------------|
|  <span data-ttu-id="2789a-104">產品名稱</span><span class="sxs-lookup"><span data-stu-id="2789a-104">Product Name</span></span>   |   [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]   |
| <span data-ttu-id="2789a-105">產品版本</span><span class="sxs-lookup"><span data-stu-id="2789a-105">Product Version</span></span> |               [!INCLUDE[btsEDIVersion](../includes/btsediversion-md.md)]               |
|    <span data-ttu-id="2789a-106">事件識別碼</span><span class="sxs-lookup"><span data-stu-id="2789a-106">Event ID</span></span>     |                                           -                                            |
|  <span data-ttu-id="2789a-107">事件來源</span><span class="sxs-lookup"><span data-stu-id="2789a-107">Event Source</span></span>   | [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]<span data-ttu-id="2789a-108"> EDI</span><span class="sxs-lookup"><span data-stu-id="2789a-108"> EDI</span></span> |
|    <span data-ttu-id="2789a-109">元件</span><span class="sxs-lookup"><span data-stu-id="2789a-109">Component</span></span>    |                                    <span data-ttu-id="2789a-110">批次引擎</span><span class="sxs-lookup"><span data-stu-id="2789a-110">Batching Engine</span></span>                                     |
|  <span data-ttu-id="2789a-111">符號名稱</span><span class="sxs-lookup"><span data-stu-id="2789a-111">Symbolic Name</span></span>  |                              <span data-ttu-id="2789a-112">InvalidBooleanPropertyValue</span><span class="sxs-lookup"><span data-stu-id="2789a-112">InvalidBooleanPropertyValue</span></span>                               |
|  <span data-ttu-id="2789a-113">訊息文字</span><span class="sxs-lookup"><span data-stu-id="2789a-113">Message Text</span></span>   |                        <span data-ttu-id="2789a-114">布林屬性值無效</span><span class="sxs-lookup"><span data-stu-id="2789a-114">The boolean property value is not valid</span></span>                         |
  
## <a name="explanation"></a><span data-ttu-id="2789a-115">說明</span><span class="sxs-lookup"><span data-stu-id="2789a-115">Explanation</span></span>  
 <span data-ttu-id="2789a-116">這個錯誤/警告/資訊事件表示，輸入 [批次篩選條件] 對話方塊中的資料列中的屬性值無效，因為屬性需要布林值，但輸入的值不是布林值。</span><span class="sxs-lookup"><span data-stu-id="2789a-116">This Error/Warning/Information event indicates that a value entered for a property in a row of the Batch Filter dialog box was invalid, because the property required a boolean value, but the value entered was not a boolean.</span></span>  
  
## <a name="user-action"></a><span data-ttu-id="2789a-117">使用者動作</span><span class="sxs-lookup"><span data-stu-id="2789a-117">User Action</span></span>  
 <span data-ttu-id="2789a-118">若要解決這個錯誤，開啟 [批次篩選條件] 對話方塊中從 [交換批次建立設定] 頁面中的 [EDI 屬性] 對話方塊。</span><span class="sxs-lookup"><span data-stu-id="2789a-118">To resolve this error, open the Batch Filter dialog box from within the Interchange Batch Creation Settings page of the EDI Properties dialog box.</span></span> <span data-ttu-id="2789a-119">請確定輸入需要布林值屬性的值實際上是布林值。</span><span class="sxs-lookup"><span data-stu-id="2789a-119">Make sure that the value entered for a property that requires a boolean value is in fact a boolean.</span></span>