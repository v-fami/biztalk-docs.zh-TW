---
title: 無效的授權值 |Microsoft 文件
ms.custom: ''
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 70d0dd75-b045-4b67-ba23-78551493f074
caps.latest.revision: 8
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: b4e83d35e379babeedca783fa8eb00774ccf05ea
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/20/2017
ms.locfileid: "22256990"
---
# <a name="invalid-authorization-value"></a><span data-ttu-id="c6190-102">無效的授權值</span><span class="sxs-lookup"><span data-stu-id="c6190-102">Invalid Authorization Value</span></span>
## <a name="details"></a><span data-ttu-id="c6190-103">詳細資料</span><span class="sxs-lookup"><span data-stu-id="c6190-103">Details</span></span>  
  
|||  
|-|-|  
|<span data-ttu-id="c6190-104">產品名稱</span><span class="sxs-lookup"><span data-stu-id="c6190-104">Product Name</span></span>|[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]|  
|<span data-ttu-id="c6190-105">產品版本</span><span class="sxs-lookup"><span data-stu-id="c6190-105">Product Version</span></span>|[!INCLUDE[btsEDIVersion](../includes/btsediversion-md.md)]|  
|<span data-ttu-id="c6190-106">事件識別碼</span><span class="sxs-lookup"><span data-stu-id="c6190-106">Event ID</span></span>|-|  
|<span data-ttu-id="c6190-107">事件來源</span><span class="sxs-lookup"><span data-stu-id="c6190-107">Event Source</span></span>|[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]<span data-ttu-id="c6190-108">EDI</span><span class="sxs-lookup"><span data-stu-id="c6190-108"> EDI</span></span>|  
|<span data-ttu-id="c6190-109">元件</span><span class="sxs-lookup"><span data-stu-id="c6190-109">Component</span></span>|<span data-ttu-id="c6190-110">EDI 引擎</span><span class="sxs-lookup"><span data-stu-id="c6190-110">EDI Engine</span></span>|  
|<span data-ttu-id="c6190-111">符號名稱</span><span class="sxs-lookup"><span data-stu-id="c6190-111">Symbolic Name</span></span>|<span data-ttu-id="c6190-112">X12Ta1InvalidAuthorizationValueDescription</span><span class="sxs-lookup"><span data-stu-id="c6190-112">X12Ta1InvalidAuthorizationValueDescription</span></span>|  
|<span data-ttu-id="c6190-113">訊息文字</span><span class="sxs-lookup"><span data-stu-id="c6190-113">Message Text</span></span>|<span data-ttu-id="c6190-114">無效的授權值</span><span class="sxs-lookup"><span data-stu-id="c6190-114">Invalid Authorization Value</span></span>|  
  
## <a name="explanation"></a><span data-ttu-id="c6190-115">說明</span><span class="sxs-lookup"><span data-stu-id="c6190-115">Explanation</span></span>  
 <span data-ttu-id="c6190-116">這個錯誤/警告/資訊事件表示接收管線無法處理內送交換，因為 ISA02 授權資訊的值不符合結構描述 （如果是 X12_AN)，所指定的資料類型，或是沒有結構描述 (10) 所需的數字的數目。</span><span class="sxs-lookup"><span data-stu-id="c6190-116">This Error/Warning/Information event indicates that the receive pipeline could not process the incoming interchange because the value of the Authorization Information in ISA02 did not conform to the data type specified by the schema (X12_AN), or did not have the number of digits required by the schema (10).</span></span> <span data-ttu-id="c6190-117">結構描述是 X12ServiceSchema BaseArtifacts.dll 中。</span><span class="sxs-lookup"><span data-stu-id="c6190-117">The schema is the X12ServiceSchema in BaseArtifacts.dll.</span></span>  
  
## <a name="user-action"></a><span data-ttu-id="c6190-118">使用者動作</span><span class="sxs-lookup"><span data-stu-id="c6190-118">User Action</span></span>  
 <span data-ttu-id="c6190-119">若要解決這個錯誤，請確定 ISA02 標頭中的值是否符合 X12： 資料類型和具有 10 個數字 （使用尾端空格），然後重新傳送交換。</span><span class="sxs-lookup"><span data-stu-id="c6190-119">To resolve this error, make sure that the value in the ISA02 header conforms to the X12:AN data type and has 10 digits (with trailing spaces), and then have the interchange resent.</span></span>