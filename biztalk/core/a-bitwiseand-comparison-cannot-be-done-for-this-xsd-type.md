---
title: 無法對此 XSD 類型執行 BitwiseAnd 比較 |Microsoft Docs
ms.custom: ''
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 82bc2351-c002-458a-9d35-5fdcc91c6a0e
caps.latest.revision: 3
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: d057efc9f0fd9e1cd5625f191f811c53b2e1ad4f
ms.sourcegitcommit: 266308ec5c6a9d8d80ff298ee6051b4843c5d626
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/27/2018
ms.locfileid: "37019499"
---
# <a name="a-bitwiseand-comparison-cannot-be-done-for-this-xsd-type"></a><span data-ttu-id="9aae2-102">無法對此 XSD 類型執行 BitwiseAnd 比較</span><span class="sxs-lookup"><span data-stu-id="9aae2-102">A BitwiseAnd comparison cannot be done for this XSD type</span></span>
## <a name="details"></a><span data-ttu-id="9aae2-103">詳細資料</span><span class="sxs-lookup"><span data-stu-id="9aae2-103">Details</span></span>  
  
|                 |                                                                                        |
|-----------------|----------------------------------------------------------------------------------------|
|  <span data-ttu-id="9aae2-104">產品名稱</span><span class="sxs-lookup"><span data-stu-id="9aae2-104">Product Name</span></span>   |   [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]   |
| <span data-ttu-id="9aae2-105">產品版本</span><span class="sxs-lookup"><span data-stu-id="9aae2-105">Product Version</span></span> |               [!INCLUDE[btsEDIVersion](../includes/btsediversion-md.md)]               |
|    <span data-ttu-id="9aae2-106">事件識別碼</span><span class="sxs-lookup"><span data-stu-id="9aae2-106">Event ID</span></span>     |                                           -                                            |
|  <span data-ttu-id="9aae2-107">事件來源</span><span class="sxs-lookup"><span data-stu-id="9aae2-107">Event Source</span></span>   | [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]<span data-ttu-id="9aae2-108"> EDI</span><span class="sxs-lookup"><span data-stu-id="9aae2-108"> EDI</span></span> |
|    <span data-ttu-id="9aae2-109">元件</span><span class="sxs-lookup"><span data-stu-id="9aae2-109">Component</span></span>    |                                       <span data-ttu-id="9aae2-110">將 EDI 引擎</span><span class="sxs-lookup"><span data-stu-id="9aae2-110">EDI Engine</span></span>                                       |
|  <span data-ttu-id="9aae2-111">符號名稱</span><span class="sxs-lookup"><span data-stu-id="9aae2-111">Symbolic Name</span></span>  |                             <span data-ttu-id="9aae2-112">Err_InvalidBitwiseComparision</span><span class="sxs-lookup"><span data-stu-id="9aae2-112">Err_InvalidBitwiseComparision</span></span>                              |
|  <span data-ttu-id="9aae2-113">訊息文字</span><span class="sxs-lookup"><span data-stu-id="9aae2-113">Message Text</span></span>   |               <span data-ttu-id="9aae2-114">無法對此 XSD 類型執行 BitwiseAnd 比較。</span><span class="sxs-lookup"><span data-stu-id="9aae2-114">A BitwiseAnd comparison cannot be done for this XSD type.</span></span>                |
  
## <a name="explanation"></a><span data-ttu-id="9aae2-115">說明</span><span class="sxs-lookup"><span data-stu-id="9aae2-115">Explanation</span></span>  
 <span data-ttu-id="9aae2-116">這個錯誤/警告/資訊事件表示 BizTalk Server 無法嘗試決定要批次處理的訊息比較的內容屬性。</span><span class="sxs-lookup"><span data-stu-id="9aae2-116">This Error/Warning/Information event indicates BizTalk Server was unable to compare a context property while trying to decide to Batch a message.</span></span>  
  
## <a name="user-action"></a><span data-ttu-id="9aae2-117">使用者動作</span><span class="sxs-lookup"><span data-stu-id="9aae2-117">User Action</span></span>  
 <span data-ttu-id="9aae2-118">若要解決這個錯誤，請確定在作用中批次中提供的篩選條件未指定內容屬性其中具有 CSD 類型無法位元比較。</span><span class="sxs-lookup"><span data-stu-id="9aae2-118">To resolve this error, ensure that the filter provided in Active batches doesn’t specify a context property which has an CSD type that can’t be bitwise compared.</span></span>