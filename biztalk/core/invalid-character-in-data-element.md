---
title: "無效的字元資料元素中 |Microsoft 文件"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: db7e2c72-f2cc-4157-aa26-062d2cc1210b
caps.latest.revision: "8"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: cc805fbede667013b56088b3d2c29913157c2fe5
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/20/2017
---
# <a name="invalid-character-in-data-element"></a><span data-ttu-id="dbc62-102">資料元素中無效的字元</span><span class="sxs-lookup"><span data-stu-id="dbc62-102">Invalid character in data element</span></span>
## <a name="details"></a><span data-ttu-id="dbc62-103">詳細資料</span><span class="sxs-lookup"><span data-stu-id="dbc62-103">Details</span></span>  
  
|||  
|-|-|  
|<span data-ttu-id="dbc62-104">產品名稱</span><span class="sxs-lookup"><span data-stu-id="dbc62-104">Product Name</span></span>|[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]|  
|<span data-ttu-id="dbc62-105">產品版本</span><span class="sxs-lookup"><span data-stu-id="dbc62-105">Product Version</span></span>|[!INCLUDE[btsEDIVersion](../includes/btsediversion-md.md)]|  
|<span data-ttu-id="dbc62-106">事件識別碼</span><span class="sxs-lookup"><span data-stu-id="dbc62-106">Event ID</span></span>|-|  
|<span data-ttu-id="dbc62-107">事件來源</span><span class="sxs-lookup"><span data-stu-id="dbc62-107">Event Source</span></span>|[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]<span data-ttu-id="dbc62-108">EDI</span><span class="sxs-lookup"><span data-stu-id="dbc62-108"> EDI</span></span>|  
|<span data-ttu-id="dbc62-109">元件</span><span class="sxs-lookup"><span data-stu-id="dbc62-109">Component</span></span>|<span data-ttu-id="dbc62-110">EDI 引擎</span><span class="sxs-lookup"><span data-stu-id="dbc62-110">EDI Engine</span></span>|  
|<span data-ttu-id="dbc62-111">符號名稱</span><span class="sxs-lookup"><span data-stu-id="dbc62-111">Symbolic Name</span></span>|<span data-ttu-id="dbc62-112">X12DeInvalidCharacterInDataElementDescription</span><span class="sxs-lookup"><span data-stu-id="dbc62-112">X12DeInvalidCharacterInDataElementDescription</span></span>|  
|<span data-ttu-id="dbc62-113">訊息文字</span><span class="sxs-lookup"><span data-stu-id="dbc62-113">Message Text</span></span>|<span data-ttu-id="dbc62-114">資料元素中無效的字元</span><span class="sxs-lookup"><span data-stu-id="dbc62-114">Invalid character in data element</span></span>|  
  
## <a name="explanation"></a><span data-ttu-id="dbc62-115">說明</span><span class="sxs-lookup"><span data-stu-id="dbc62-115">Explanation</span></span>  
 <span data-ttu-id="dbc62-116">這個錯誤/警告/資訊事件表示接收管線無法處理內送交換，因為資料元素的值與 EDI 結構描述中指定的值不相符。</span><span class="sxs-lookup"><span data-stu-id="dbc62-116">This Error/Warning/Information event indicates that the receive pipeline could not process the incoming interchange because the value of a data element did not conform to the value specified in the EDI schema.</span></span>  
  
## <a name="user-action"></a><span data-ttu-id="dbc62-117">使用者動作</span><span class="sxs-lookup"><span data-stu-id="dbc62-117">User Action</span></span>  
 <span data-ttu-id="dbc62-118">若要解決此錯誤，請確定資料元素中的值符合 EDI 結構描述，然後重新傳送交換。</span><span class="sxs-lookup"><span data-stu-id="dbc62-118">To resolve this error, make sure that the value in the data element conforms to the EDI schema, and then have the interchange resent.</span></span>