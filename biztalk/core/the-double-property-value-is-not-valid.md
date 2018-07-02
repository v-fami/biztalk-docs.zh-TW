---
title: 雙精度屬性值無效。 |Microsoft Docs
ms.custom: ''
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: d5e799d8-5fbb-4262-9d1f-4954ba0e0237
caps.latest.revision: 8
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 43c6a7ef649b9c7e7d04806f86c00bfc3cc6f59f
ms.sourcegitcommit: 266308ec5c6a9d8d80ff298ee6051b4843c5d626
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/27/2018
ms.locfileid: "36981319"
---
# <a name="the-double-property-value-is-not-valid"></a><span data-ttu-id="57c88-102">雙精度屬性值無效</span><span class="sxs-lookup"><span data-stu-id="57c88-102">The double property value is not valid</span></span>
## <a name="details"></a><span data-ttu-id="57c88-103">詳細資料</span><span class="sxs-lookup"><span data-stu-id="57c88-103">Details</span></span>  
  
|                 |                                                                                        |
|-----------------|----------------------------------------------------------------------------------------|
|  <span data-ttu-id="57c88-104">產品名稱</span><span class="sxs-lookup"><span data-stu-id="57c88-104">Product Name</span></span>   |   [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]   |
| <span data-ttu-id="57c88-105">產品版本</span><span class="sxs-lookup"><span data-stu-id="57c88-105">Product Version</span></span> |               [!INCLUDE[btsEDIVersion](../includes/btsediversion-md.md)]               |
|    <span data-ttu-id="57c88-106">事件識別碼</span><span class="sxs-lookup"><span data-stu-id="57c88-106">Event ID</span></span>     |                                           -                                            |
|  <span data-ttu-id="57c88-107">事件來源</span><span class="sxs-lookup"><span data-stu-id="57c88-107">Event Source</span></span>   | [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]<span data-ttu-id="57c88-108"> EDI</span><span class="sxs-lookup"><span data-stu-id="57c88-108"> EDI</span></span> |
|    <span data-ttu-id="57c88-109">元件</span><span class="sxs-lookup"><span data-stu-id="57c88-109">Component</span></span>    |                                    <span data-ttu-id="57c88-110">批次引擎</span><span class="sxs-lookup"><span data-stu-id="57c88-110">Batching Engine</span></span>                                     |
|  <span data-ttu-id="57c88-111">符號名稱</span><span class="sxs-lookup"><span data-stu-id="57c88-111">Symbolic Name</span></span>  |                               <span data-ttu-id="57c88-112">InvalidDoublePropertyValue</span><span class="sxs-lookup"><span data-stu-id="57c88-112">InvalidDoublePropertyValue</span></span>                               |
|  <span data-ttu-id="57c88-113">訊息文字</span><span class="sxs-lookup"><span data-stu-id="57c88-113">Message Text</span></span>   |                         <span data-ttu-id="57c88-114">雙精度屬性值無效</span><span class="sxs-lookup"><span data-stu-id="57c88-114">The double property value is not valid</span></span>                         |
  
## <a name="explanation"></a><span data-ttu-id="57c88-115">說明</span><span class="sxs-lookup"><span data-stu-id="57c88-115">Explanation</span></span>  
 <span data-ttu-id="57c88-116">這個錯誤/警告/資訊事件表示在 [批次篩選條件] 對話方塊的某列中針對屬性輸入的值無效，因為屬性需要雙精度值，但是輸入的值不是雙精度。</span><span class="sxs-lookup"><span data-stu-id="57c88-116">This Error/Warning/Information event indicates that a value entered for a property in a row of the Batch Filter dialog box was invalid, because the property required a double value, but the value entered was not a double.</span></span>  
  
## <a name="user-action"></a><span data-ttu-id="57c88-117">使用者動作</span><span class="sxs-lookup"><span data-stu-id="57c88-117">User Action</span></span>  
 <span data-ttu-id="57c88-118">若要解決這個錯誤，開啟 [批次篩選條件] 對話方塊中從 [交換批次建立設定] 頁面中的 [EDI 屬性] 對話方塊。</span><span class="sxs-lookup"><span data-stu-id="57c88-118">To resolve this error, open the Batch Filter dialog box from within the Interchange Batch Creation Settings page of the EDI Properties dialog box.</span></span> <span data-ttu-id="57c88-119">請確定需要雙精度浮點數屬性，為輸入的值實際上是雙精度浮點數。</span><span class="sxs-lookup"><span data-stu-id="57c88-119">Make sure that the value entered for a property that requires a double is in fact a double.</span></span>