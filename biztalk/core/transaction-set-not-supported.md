---
title: 不支援交易集 |Microsoft Docs
ms.custom: ''
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 5ffe8528-f34f-4189-8ee6-4ae1afb50c92
caps.latest.revision: 9
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: e767e81ba45ab711cc8c84b5f682ac0eba56b5a8
ms.sourcegitcommit: 266308ec5c6a9d8d80ff298ee6051b4843c5d626
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/27/2018
ms.locfileid: "37001129"
---
# <a name="transaction-set-not-supported"></a><span data-ttu-id="cfa3c-102">不支援交易集</span><span class="sxs-lookup"><span data-stu-id="cfa3c-102">Transaction Set Not Supported</span></span>
## <a name="details"></a><span data-ttu-id="cfa3c-103">詳細資料</span><span class="sxs-lookup"><span data-stu-id="cfa3c-103">Details</span></span>  
  
|                 |                                                                                        |
|-----------------|----------------------------------------------------------------------------------------|
|  <span data-ttu-id="cfa3c-104">產品名稱</span><span class="sxs-lookup"><span data-stu-id="cfa3c-104">Product Name</span></span>   |   [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]   |
| <span data-ttu-id="cfa3c-105">產品版本</span><span class="sxs-lookup"><span data-stu-id="cfa3c-105">Product Version</span></span> |               [!INCLUDE[btsEDIVersion](../includes/btsediversion-md.md)]               |
|    <span data-ttu-id="cfa3c-106">事件識別碼</span><span class="sxs-lookup"><span data-stu-id="cfa3c-106">Event ID</span></span>     |                                           -                                            |
|  <span data-ttu-id="cfa3c-107">事件來源</span><span class="sxs-lookup"><span data-stu-id="cfa3c-107">Event Source</span></span>   | [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]<span data-ttu-id="cfa3c-108"> EDI</span><span class="sxs-lookup"><span data-stu-id="cfa3c-108"> EDI</span></span> |
|    <span data-ttu-id="cfa3c-109">元件</span><span class="sxs-lookup"><span data-stu-id="cfa3c-109">Component</span></span>    |                                       <span data-ttu-id="cfa3c-110">將 EDI 引擎</span><span class="sxs-lookup"><span data-stu-id="cfa3c-110">EDI Engine</span></span>                                       |
|  <span data-ttu-id="cfa3c-111">符號名稱</span><span class="sxs-lookup"><span data-stu-id="cfa3c-111">Symbolic Name</span></span>  |                              <span data-ttu-id="cfa3c-112">X12TsNotSupportedDescription</span><span class="sxs-lookup"><span data-stu-id="cfa3c-112">X12TsNotSupportedDescription</span></span>                              |
|  <span data-ttu-id="cfa3c-113">訊息文字</span><span class="sxs-lookup"><span data-stu-id="cfa3c-113">Message Text</span></span>   |                             <span data-ttu-id="cfa3c-114">不支援交易集</span><span class="sxs-lookup"><span data-stu-id="cfa3c-114">Transaction Set Not Supported</span></span>                              |
  
## <a name="explanation"></a><span data-ttu-id="cfa3c-115">說明</span><span class="sxs-lookup"><span data-stu-id="cfa3c-115">Explanation</span></span>  
 <span data-ttu-id="cfa3c-116">這個錯誤/警告/資訊事件表示，接收管線無法處理內送交換因為該交易集的文件類型尚未部署文件結構描述。</span><span class="sxs-lookup"><span data-stu-id="cfa3c-116">This Error/Warning/Information event indicates that the receive pipeline could not process the incoming interchange because a document schema has not been deployed for the document type of that transaction set.</span></span>  
  
## <a name="user-action"></a><span data-ttu-id="cfa3c-117">使用者動作</span><span class="sxs-lookup"><span data-stu-id="cfa3c-117">User Action</span></span>  
 <span data-ttu-id="cfa3c-118">若要解決這個錯誤，請在[!INCLUDE[btsVStudioNoVersion](../includes/btsvstudionoversion-md.md)]部署文件類型的結構描述文件的交易集。</span><span class="sxs-lookup"><span data-stu-id="cfa3c-118">To resolve this error, in [!INCLUDE[btsVStudioNoVersion](../includes/btsvstudionoversion-md.md)] deploy a document schema for the document type of the transaction set.</span></span>