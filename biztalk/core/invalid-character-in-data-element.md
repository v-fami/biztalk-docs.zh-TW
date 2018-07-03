---
title: 資料元素中的無效字元 |Microsoft Docs
ms.custom: ''
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: db7e2c72-f2cc-4157-aa26-062d2cc1210b
caps.latest.revision: 8
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: f2461a5542daaf701c90a76d26c31b72095d5aef
ms.sourcegitcommit: 266308ec5c6a9d8d80ff298ee6051b4843c5d626
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/27/2018
ms.locfileid: "37010023"
---
# <a name="invalid-character-in-data-element"></a><span data-ttu-id="14036-102">資料元素中無效的字元</span><span class="sxs-lookup"><span data-stu-id="14036-102">Invalid character in data element</span></span>
## <a name="details"></a><span data-ttu-id="14036-103">詳細資料</span><span class="sxs-lookup"><span data-stu-id="14036-103">Details</span></span>  
  
|                 |                                                                                        |
|-----------------|----------------------------------------------------------------------------------------|
|  <span data-ttu-id="14036-104">產品名稱</span><span class="sxs-lookup"><span data-stu-id="14036-104">Product Name</span></span>   |   [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]   |
| <span data-ttu-id="14036-105">產品版本</span><span class="sxs-lookup"><span data-stu-id="14036-105">Product Version</span></span> |               [!INCLUDE[btsEDIVersion](../includes/btsediversion-md.md)]               |
|    <span data-ttu-id="14036-106">事件識別碼</span><span class="sxs-lookup"><span data-stu-id="14036-106">Event ID</span></span>     |                                           -                                            |
|  <span data-ttu-id="14036-107">事件來源</span><span class="sxs-lookup"><span data-stu-id="14036-107">Event Source</span></span>   | [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]<span data-ttu-id="14036-108"> EDI</span><span class="sxs-lookup"><span data-stu-id="14036-108"> EDI</span></span> |
|    <span data-ttu-id="14036-109">元件</span><span class="sxs-lookup"><span data-stu-id="14036-109">Component</span></span>    |                                       <span data-ttu-id="14036-110">將 EDI 引擎</span><span class="sxs-lookup"><span data-stu-id="14036-110">EDI Engine</span></span>                                       |
|  <span data-ttu-id="14036-111">符號名稱</span><span class="sxs-lookup"><span data-stu-id="14036-111">Symbolic Name</span></span>  |                     <span data-ttu-id="14036-112">X12DeInvalidCharacterInDataElementDescription</span><span class="sxs-lookup"><span data-stu-id="14036-112">X12DeInvalidCharacterInDataElementDescription</span></span>                      |
|  <span data-ttu-id="14036-113">訊息文字</span><span class="sxs-lookup"><span data-stu-id="14036-113">Message Text</span></span>   |                           <span data-ttu-id="14036-114">資料元素中無效的字元</span><span class="sxs-lookup"><span data-stu-id="14036-114">Invalid character in data element</span></span>                            |
  
## <a name="explanation"></a><span data-ttu-id="14036-115">說明</span><span class="sxs-lookup"><span data-stu-id="14036-115">Explanation</span></span>  
 <span data-ttu-id="14036-116">這個錯誤/警告/資訊事件表示接收管線無法處理內送交換，因為資料元素的值與 EDI 結構描述中指定的值不相符。</span><span class="sxs-lookup"><span data-stu-id="14036-116">This Error/Warning/Information event indicates that the receive pipeline could not process the incoming interchange because the value of a data element did not conform to the value specified in the EDI schema.</span></span>  
  
## <a name="user-action"></a><span data-ttu-id="14036-117">使用者動作</span><span class="sxs-lookup"><span data-stu-id="14036-117">User Action</span></span>  
 <span data-ttu-id="14036-118">若要解決此錯誤，請確定資料元素中的值符合 EDI 結構描述，然後重新傳送交換。</span><span class="sxs-lookup"><span data-stu-id="14036-118">To resolve this error, make sure that the value in the data element conforms to the EDI schema, and then have the interchange resent.</span></span>