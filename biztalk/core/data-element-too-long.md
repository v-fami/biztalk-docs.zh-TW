---
title: 資料元素太長 |Microsoft 文件
ms.custom: ''
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: bf608cc1-d482-4e19-8f56-10d9e03feb79
caps.latest.revision: 8
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: fbfe63fccc442c35411bfae04c7f27629ce066ce
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/20/2017
ms.locfileid: "22238262"
---
# <a name="data-element-too-long"></a><span data-ttu-id="8818c-102">資料元素太長</span><span class="sxs-lookup"><span data-stu-id="8818c-102">Data element too long</span></span>
## <a name="details"></a><span data-ttu-id="8818c-103">詳細資料</span><span class="sxs-lookup"><span data-stu-id="8818c-103">Details</span></span>  
  
|||  
|-|-|  
|<span data-ttu-id="8818c-104">產品名稱</span><span class="sxs-lookup"><span data-stu-id="8818c-104">Product Name</span></span>|[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]|  
|<span data-ttu-id="8818c-105">產品版本</span><span class="sxs-lookup"><span data-stu-id="8818c-105">Product Version</span></span>|[!INCLUDE[btsEDIVersion](../includes/btsediversion-md.md)]|  
|<span data-ttu-id="8818c-106">事件識別碼</span><span class="sxs-lookup"><span data-stu-id="8818c-106">Event ID</span></span>|-|  
|<span data-ttu-id="8818c-107">事件來源</span><span class="sxs-lookup"><span data-stu-id="8818c-107">Event Source</span></span>|[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]<span data-ttu-id="8818c-108">EDI</span><span class="sxs-lookup"><span data-stu-id="8818c-108"> EDI</span></span>|  
|<span data-ttu-id="8818c-109">元件</span><span class="sxs-lookup"><span data-stu-id="8818c-109">Component</span></span>|<span data-ttu-id="8818c-110">EDI 引擎</span><span class="sxs-lookup"><span data-stu-id="8818c-110">EDI Engine</span></span>|  
|<span data-ttu-id="8818c-111">符號名稱</span><span class="sxs-lookup"><span data-stu-id="8818c-111">Symbolic Name</span></span>|-|  
|<span data-ttu-id="8818c-112">訊息文字</span><span class="sxs-lookup"><span data-stu-id="8818c-112">Message Text</span></span>|<span data-ttu-id="8818c-113">資料元素太長</span><span class="sxs-lookup"><span data-stu-id="8818c-113">Data element too long</span></span>|  
  
## <a name="explanation"></a><span data-ttu-id="8818c-114">說明</span><span class="sxs-lookup"><span data-stu-id="8818c-114">Explanation</span></span>  
 <span data-ttu-id="8818c-115">這個錯誤/警告/資訊事件表示 EDI 接收管線或 EDI 傳送管線無法處理內送交換，因為資料元素的結構描述所指定的最大長度超過。</span><span class="sxs-lookup"><span data-stu-id="8818c-115">This Error/Warning/Information event indicates that the EDI receive pipeline or the EDI Send pipeline could not process the incoming interchange because a data element was longer than the maximum length specified by the schema.</span></span>  
  
## <a name="user-action"></a><span data-ttu-id="8818c-116">使用者動作</span><span class="sxs-lookup"><span data-stu-id="8818c-116">User Action</span></span>  
 <span data-ttu-id="8818c-117">若要解決這個錯誤，請縮短不太長，因此它低於上限的交換中的資料元素。</span><span class="sxs-lookup"><span data-stu-id="8818c-117">To resolve this error, shorten the data element in the interchange that was too long so it is below the maximum limit.</span></span> <span data-ttu-id="8818c-118">若要判斷最大長度，\XSD_Schema 資料夾中開啟結構描述、 搜尋資料的項目識別碼，並識別 maxLength 值為何。</span><span class="sxs-lookup"><span data-stu-id="8818c-118">To determine the maximum length, open the schema in the \XSD_Schema folder, search on the data element ID, and identify what the maxLength value is.</span></span>