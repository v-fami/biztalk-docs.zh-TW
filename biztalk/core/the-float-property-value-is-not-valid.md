---
title: 浮點數屬性值無效。 |Microsoft Docs
ms.custom: ''
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 79327dc6-fc5e-4290-9663-16bb64970d4b
caps.latest.revision: 8
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: d7f0752a05b9e692a002c80332032337230decb9
ms.sourcegitcommit: 266308ec5c6a9d8d80ff298ee6051b4843c5d626
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/27/2018
ms.locfileid: "36975071"
---
# <a name="the-float-property-value-is-not-valid"></a><span data-ttu-id="958dc-102">浮點數屬性值無效</span><span class="sxs-lookup"><span data-stu-id="958dc-102">The float property value is not valid</span></span>
## <a name="details"></a><span data-ttu-id="958dc-103">詳細資料</span><span class="sxs-lookup"><span data-stu-id="958dc-103">Details</span></span>  
  
|                 |                                                                                        |
|-----------------|----------------------------------------------------------------------------------------|
|  <span data-ttu-id="958dc-104">產品名稱</span><span class="sxs-lookup"><span data-stu-id="958dc-104">Product Name</span></span>   |   [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]   |
| <span data-ttu-id="958dc-105">產品版本</span><span class="sxs-lookup"><span data-stu-id="958dc-105">Product Version</span></span> |               [!INCLUDE[btsEDIVersion](../includes/btsediversion-md.md)]               |
|    <span data-ttu-id="958dc-106">事件識別碼</span><span class="sxs-lookup"><span data-stu-id="958dc-106">Event ID</span></span>     |                                           -                                            |
|  <span data-ttu-id="958dc-107">事件來源</span><span class="sxs-lookup"><span data-stu-id="958dc-107">Event Source</span></span>   | [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]<span data-ttu-id="958dc-108"> EDI</span><span class="sxs-lookup"><span data-stu-id="958dc-108"> EDI</span></span> |
|    <span data-ttu-id="958dc-109">元件</span><span class="sxs-lookup"><span data-stu-id="958dc-109">Component</span></span>    |                                    <span data-ttu-id="958dc-110">批次引擎</span><span class="sxs-lookup"><span data-stu-id="958dc-110">Batching Engine</span></span>                                     |
|  <span data-ttu-id="958dc-111">符號名稱</span><span class="sxs-lookup"><span data-stu-id="958dc-111">Symbolic Name</span></span>  |                               <span data-ttu-id="958dc-112">InvalidFloatPropertyValue</span><span class="sxs-lookup"><span data-stu-id="958dc-112">InvalidFloatPropertyValue</span></span>                                |
|  <span data-ttu-id="958dc-113">訊息文字</span><span class="sxs-lookup"><span data-stu-id="958dc-113">Message Text</span></span>   |                         <span data-ttu-id="958dc-114">浮點數屬性值無效</span><span class="sxs-lookup"><span data-stu-id="958dc-114">The float property value is not valid</span></span>                          |
  
## <a name="explanation"></a><span data-ttu-id="958dc-115">說明</span><span class="sxs-lookup"><span data-stu-id="958dc-115">Explanation</span></span>  
 <span data-ttu-id="958dc-116">這個錯誤/警告/資訊事件表示，輸入 [批次篩選條件] 對話方塊中的資料列中的屬性值無效，因為屬性需要浮點值，但輸入的值不是浮點數。</span><span class="sxs-lookup"><span data-stu-id="958dc-116">This Error/Warning/Information event indicates that a value entered for a property in a row of the Batch Filter dialog box was invalid, because the property required a float value, but the value entered was not a float.</span></span>  
  
## <a name="user-action"></a><span data-ttu-id="958dc-117">使用者動作</span><span class="sxs-lookup"><span data-stu-id="958dc-117">User Action</span></span>  
 <span data-ttu-id="958dc-118">若要解決這個錯誤，開啟 [批次篩選條件] 對話方塊中從 [交換批次建立設定] 頁面中的 [EDI 屬性] 對話方塊。</span><span class="sxs-lookup"><span data-stu-id="958dc-118">To resolve this error, open the Batch Filter dialog box from within the Interchange Batch Creation Settings page of the EDI Properties dialog box.</span></span> <span data-ttu-id="958dc-119">請確定需要浮點數屬性，為輸入的值實際上是浮點數。</span><span class="sxs-lookup"><span data-stu-id="958dc-119">Make sure that the value entered for a property that requires a float is in fact a float.</span></span>