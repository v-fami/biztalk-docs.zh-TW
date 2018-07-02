---
title: 位元組屬性值無效。 |Microsoft Docs
ms.custom: ''
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: e8599688-9f05-4983-8850-9ac1479ce9cc
caps.latest.revision: 8
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 1ef443c74c47883d04bcad2c1da5bb9423f7c01d
ms.sourcegitcommit: 266308ec5c6a9d8d80ff298ee6051b4843c5d626
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/27/2018
ms.locfileid: "36977849"
---
# <a name="the-byte-property-value-is-not-valid"></a><span data-ttu-id="78f05-102">位元組屬性值無效</span><span class="sxs-lookup"><span data-stu-id="78f05-102">The byte property value is not valid</span></span>
## <a name="details"></a><span data-ttu-id="78f05-103">詳細資料</span><span class="sxs-lookup"><span data-stu-id="78f05-103">Details</span></span>  
  
|                 |                                                                                        |
|-----------------|----------------------------------------------------------------------------------------|
|  <span data-ttu-id="78f05-104">產品名稱</span><span class="sxs-lookup"><span data-stu-id="78f05-104">Product Name</span></span>   |   [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]   |
| <span data-ttu-id="78f05-105">產品版本</span><span class="sxs-lookup"><span data-stu-id="78f05-105">Product Version</span></span> |               [!INCLUDE[btsEDIVersion](../includes/btsediversion-md.md)]               |
|    <span data-ttu-id="78f05-106">事件識別碼</span><span class="sxs-lookup"><span data-stu-id="78f05-106">Event ID</span></span>     |                                           -                                            |
|  <span data-ttu-id="78f05-107">事件來源</span><span class="sxs-lookup"><span data-stu-id="78f05-107">Event Source</span></span>   | [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]<span data-ttu-id="78f05-108"> EDI</span><span class="sxs-lookup"><span data-stu-id="78f05-108"> EDI</span></span> |
|    <span data-ttu-id="78f05-109">元件</span><span class="sxs-lookup"><span data-stu-id="78f05-109">Component</span></span>    |                                    <span data-ttu-id="78f05-110">批次引擎</span><span class="sxs-lookup"><span data-stu-id="78f05-110">Batching Engine</span></span>                                     |
|  <span data-ttu-id="78f05-111">符號名稱</span><span class="sxs-lookup"><span data-stu-id="78f05-111">Symbolic Name</span></span>  |                                <span data-ttu-id="78f05-112">InvalidBytePropertyValue</span><span class="sxs-lookup"><span data-stu-id="78f05-112">InvalidBytePropertyValue</span></span>                                |
|  <span data-ttu-id="78f05-113">訊息文字</span><span class="sxs-lookup"><span data-stu-id="78f05-113">Message Text</span></span>   |                          <span data-ttu-id="78f05-114">位元組屬性值無效</span><span class="sxs-lookup"><span data-stu-id="78f05-114">The byte property value is not valid</span></span>                          |
  
## <a name="explanation"></a><span data-ttu-id="78f05-115">說明</span><span class="sxs-lookup"><span data-stu-id="78f05-115">Explanation</span></span>  
 <span data-ttu-id="78f05-116">這個錯誤/警告/資訊事件表示，輸入 [批次篩選條件] 對話方塊中的資料列中的屬性值無效，因為屬性需要一個位元組值，但輸入的值不是一個位元組。</span><span class="sxs-lookup"><span data-stu-id="78f05-116">This Error/Warning/Information event indicates that a value entered for a property in a row of the Batch Filter dialog box was invalid, because the property required a byte value, but the value entered was not a byte.</span></span>  
  
## <a name="user-action"></a><span data-ttu-id="78f05-117">使用者動作</span><span class="sxs-lookup"><span data-stu-id="78f05-117">User Action</span></span>  
 <span data-ttu-id="78f05-118">若要解決這個錯誤，開啟 [批次篩選條件] 對話方塊中從 [交換批次建立設定] 頁面中的 [EDI 屬性] 對話方塊。</span><span class="sxs-lookup"><span data-stu-id="78f05-118">To resolve this error, open the Batch Filter dialog box from within the Interchange Batch Creation Settings page of the EDI Properties dialog box.</span></span> <span data-ttu-id="78f05-119">請確定輸入需要的位元組值的屬性的值實際上是一個位元組。</span><span class="sxs-lookup"><span data-stu-id="78f05-119">Make sure that the value entered for a property that requires a byte value is in fact a byte.</span></span>