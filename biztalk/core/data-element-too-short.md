---
title: 資料元素太短 |Microsoft Docs
ms.custom: ''
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: a22c0551-3262-476c-a6c6-2fd214331244
caps.latest.revision: 8
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: db14770404a45ddbfd3aea6ed71e9b8b22417515
ms.sourcegitcommit: 266308ec5c6a9d8d80ff298ee6051b4843c5d626
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/27/2018
ms.locfileid: "37005295"
---
# <a name="data-element-too-short"></a><span data-ttu-id="bd88f-102">資料元素太短</span><span class="sxs-lookup"><span data-stu-id="bd88f-102">Data element too short</span></span>
## <a name="details"></a><span data-ttu-id="bd88f-103">詳細資料</span><span class="sxs-lookup"><span data-stu-id="bd88f-103">Details</span></span>  
  
|                 |                                                                                        |
|-----------------|----------------------------------------------------------------------------------------|
|  <span data-ttu-id="bd88f-104">產品名稱</span><span class="sxs-lookup"><span data-stu-id="bd88f-104">Product Name</span></span>   |   [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]   |
| <span data-ttu-id="bd88f-105">產品版本</span><span class="sxs-lookup"><span data-stu-id="bd88f-105">Product Version</span></span> |               [!INCLUDE[btsEDIVersion](../includes/btsediversion-md.md)]               |
|    <span data-ttu-id="bd88f-106">事件識別碼</span><span class="sxs-lookup"><span data-stu-id="bd88f-106">Event ID</span></span>     |                                           -                                            |
|  <span data-ttu-id="bd88f-107">事件來源</span><span class="sxs-lookup"><span data-stu-id="bd88f-107">Event Source</span></span>   | [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]<span data-ttu-id="bd88f-108"> EDI</span><span class="sxs-lookup"><span data-stu-id="bd88f-108"> EDI</span></span> |
|    <span data-ttu-id="bd88f-109">元件</span><span class="sxs-lookup"><span data-stu-id="bd88f-109">Component</span></span>    |                                       <span data-ttu-id="bd88f-110">將 EDI 引擎</span><span class="sxs-lookup"><span data-stu-id="bd88f-110">EDI Engine</span></span>                                       |
|  <span data-ttu-id="bd88f-111">符號名稱</span><span class="sxs-lookup"><span data-stu-id="bd88f-111">Symbolic Name</span></span>  |                                           -                                            |
|  <span data-ttu-id="bd88f-112">訊息文字</span><span class="sxs-lookup"><span data-stu-id="bd88f-112">Message Text</span></span>   |                                 <span data-ttu-id="bd88f-113">資料元素太短</span><span class="sxs-lookup"><span data-stu-id="bd88f-113">Data element too short</span></span>                                 |
  
## <a name="explanation"></a><span data-ttu-id="bd88f-114">說明</span><span class="sxs-lookup"><span data-stu-id="bd88f-114">Explanation</span></span>  
 <span data-ttu-id="bd88f-115">這個錯誤/警告/資訊事件表示 EDI 接收管線或 EDI 傳送管線無法處理內送交換，因為資料元素已短於結構描述指定的最小長度。</span><span class="sxs-lookup"><span data-stu-id="bd88f-115">This Error/Warning/Information event indicates that the EDI receive pipeline or the EDI Send pipeline could not process the incoming interchange because a data element was shorter than the minimum length specified by the schema.</span></span>  
  
## <a name="user-action"></a><span data-ttu-id="bd88f-116">使用者動作</span><span class="sxs-lookup"><span data-stu-id="bd88f-116">User Action</span></span>  
 <span data-ttu-id="bd88f-117">若要解決這個錯誤，延長已太短，所以大於最小長度的交換中的資料元素。</span><span class="sxs-lookup"><span data-stu-id="bd88f-117">To resolve this error, lengthen the data element in the interchange that was too short so it is greater than the minimum length.</span></span> <span data-ttu-id="bd88f-118">若要判斷最小長度，\XSD_Schema 資料夾中開啟結構描述、 搜尋資料的項目識別碼，並識別 minLength 的值為何。</span><span class="sxs-lookup"><span data-stu-id="bd88f-118">To determine the minimum length, open the schema in the \XSD_Schema folder, search on the data element ID, and identify what the minLength value is.</span></span>