---
title: 位元組屬性值無效。 |Microsoft 文件
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
ms.openlocfilehash: 5789ae17b5127b58de45e5c4764b4ef490c43f1f
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/20/2017
ms.locfileid: "22278710"
---
# <a name="the-byte-property-value-is-not-valid"></a><span data-ttu-id="a3494-102">位元組屬性值無效</span><span class="sxs-lookup"><span data-stu-id="a3494-102">The byte property value is not valid</span></span>
## <a name="details"></a><span data-ttu-id="a3494-103">詳細資料</span><span class="sxs-lookup"><span data-stu-id="a3494-103">Details</span></span>  
  
|||  
|-|-|  
|<span data-ttu-id="a3494-104">產品名稱</span><span class="sxs-lookup"><span data-stu-id="a3494-104">Product Name</span></span>|[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]|  
|<span data-ttu-id="a3494-105">產品版本</span><span class="sxs-lookup"><span data-stu-id="a3494-105">Product Version</span></span>|[!INCLUDE[btsEDIVersion](../includes/btsediversion-md.md)]|  
|<span data-ttu-id="a3494-106">事件識別碼</span><span class="sxs-lookup"><span data-stu-id="a3494-106">Event ID</span></span>|-|  
|<span data-ttu-id="a3494-107">事件來源</span><span class="sxs-lookup"><span data-stu-id="a3494-107">Event Source</span></span>|[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]<span data-ttu-id="a3494-108">EDI</span><span class="sxs-lookup"><span data-stu-id="a3494-108"> EDI</span></span>|  
|<span data-ttu-id="a3494-109">元件</span><span class="sxs-lookup"><span data-stu-id="a3494-109">Component</span></span>|<span data-ttu-id="a3494-110">批次處理引擎</span><span class="sxs-lookup"><span data-stu-id="a3494-110">Batching Engine</span></span>|  
|<span data-ttu-id="a3494-111">符號名稱</span><span class="sxs-lookup"><span data-stu-id="a3494-111">Symbolic Name</span></span>|<span data-ttu-id="a3494-112">InvalidBytePropertyValue</span><span class="sxs-lookup"><span data-stu-id="a3494-112">InvalidBytePropertyValue</span></span>|  
|<span data-ttu-id="a3494-113">訊息文字</span><span class="sxs-lookup"><span data-stu-id="a3494-113">Message Text</span></span>|<span data-ttu-id="a3494-114">位元組屬性值無效</span><span class="sxs-lookup"><span data-stu-id="a3494-114">The byte property value is not valid</span></span>|  
  
## <a name="explanation"></a><span data-ttu-id="a3494-115">說明</span><span class="sxs-lookup"><span data-stu-id="a3494-115">Explanation</span></span>  
 <span data-ttu-id="a3494-116">這個錯誤/警告/資訊事件表示批次篩選條件 對話方塊中的資料列中的屬性輸入的值無效，因為屬性需要一個位元組值，但輸入的值不是一個位元組。</span><span class="sxs-lookup"><span data-stu-id="a3494-116">This Error/Warning/Information event indicates that a value entered for a property in a row of the Batch Filter dialog box was invalid, because the property required a byte value, but the value entered was not a byte.</span></span>  
  
## <a name="user-action"></a><span data-ttu-id="a3494-117">使用者動作</span><span class="sxs-lookup"><span data-stu-id="a3494-117">User Action</span></span>  
 <span data-ttu-id="a3494-118">若要解決這個錯誤，開啟 [批次篩選條件] 對話方塊從內 [交換批次建立設定] 頁面的 [EDI 屬性] 對話方塊。</span><span class="sxs-lookup"><span data-stu-id="a3494-118">To resolve this error, open the Batch Filter dialog box from within the Interchange Batch Creation Settings page of the EDI Properties dialog box.</span></span> <span data-ttu-id="a3494-119">請確定輸入需要的位元組值的屬性值實際上是一個位元組。</span><span class="sxs-lookup"><span data-stu-id="a3494-119">Make sure that the value entered for a property that requires a byte value is in fact a byte.</span></span>