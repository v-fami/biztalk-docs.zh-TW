---
title: 無效的時間 |Microsoft Docs
ms.custom: ''
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 6942eb77-3ef1-460c-ac4f-8f1339c25d1b
caps.latest.revision: 8
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 555934e0be188011a69efb3966e5316bc716c254
ms.sourcegitcommit: 266308ec5c6a9d8d80ff298ee6051b4843c5d626
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/27/2018
ms.locfileid: "37023820"
---
# <a name="invalid-time"></a><span data-ttu-id="06b3a-102">無效的時間</span><span class="sxs-lookup"><span data-stu-id="06b3a-102">Invalid Time</span></span>
## <a name="details"></a><span data-ttu-id="06b3a-103">詳細資料</span><span class="sxs-lookup"><span data-stu-id="06b3a-103">Details</span></span>  
  
|                 |                                                                                        |
|-----------------|----------------------------------------------------------------------------------------|
|  <span data-ttu-id="06b3a-104">產品名稱</span><span class="sxs-lookup"><span data-stu-id="06b3a-104">Product Name</span></span>   |   [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]   |
| <span data-ttu-id="06b3a-105">產品版本</span><span class="sxs-lookup"><span data-stu-id="06b3a-105">Product Version</span></span> |               [!INCLUDE[btsEDIVersion](../includes/btsediversion-md.md)]               |
|    <span data-ttu-id="06b3a-106">事件識別碼</span><span class="sxs-lookup"><span data-stu-id="06b3a-106">Event ID</span></span>     |                                           -                                            |
|  <span data-ttu-id="06b3a-107">事件來源</span><span class="sxs-lookup"><span data-stu-id="06b3a-107">Event Source</span></span>   | [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]<span data-ttu-id="06b3a-108"> EDI</span><span class="sxs-lookup"><span data-stu-id="06b3a-108"> EDI</span></span> |
|    <span data-ttu-id="06b3a-109">元件</span><span class="sxs-lookup"><span data-stu-id="06b3a-109">Component</span></span>    |                                       <span data-ttu-id="06b3a-110">將 EDI 引擎</span><span class="sxs-lookup"><span data-stu-id="06b3a-110">EDI Engine</span></span>                                       |
|  <span data-ttu-id="06b3a-111">符號名稱</span><span class="sxs-lookup"><span data-stu-id="06b3a-111">Symbolic Name</span></span>  |                              <span data-ttu-id="06b3a-112">X12Ta1InvalidTimeDescription</span><span class="sxs-lookup"><span data-stu-id="06b3a-112">X12Ta1InvalidTimeDescription</span></span>                              |
|  <span data-ttu-id="06b3a-113">訊息文字</span><span class="sxs-lookup"><span data-stu-id="06b3a-113">Message Text</span></span>   |                                      <span data-ttu-id="06b3a-114">無效的時間</span><span class="sxs-lookup"><span data-stu-id="06b3a-114">Invalid Time</span></span>                                      |
  
## <a name="explanation"></a><span data-ttu-id="06b3a-115">說明</span><span class="sxs-lookup"><span data-stu-id="06b3a-115">Explanation</span></span>  
 <span data-ttu-id="06b3a-116">這個錯誤/警告/資訊事件表示，接收管線無法處理內送交換因為 EDI 結構描述或 GS05 欄位標頭在 X12 中的時間值所指定的資料類型不符合資料元素中的時間值服務結構描述不符合交換 (BaseArtifacts.dll 中的 X12ServiceSchema)。</span><span class="sxs-lookup"><span data-stu-id="06b3a-116">This Error/Warning/Information event indicates that the receive pipeline could not process the incoming interchange because a time value in a data element did not conform to the data type specified by the EDI schema or the time value in the GS05 field header in an X12 interchange did not conform to the service schema (X12ServiceSchema in BaseArtifacts.dll).</span></span> <span data-ttu-id="06b3a-117">對於 X12，服務結構描述會定義一次在 GS05 欄位截至 X12_TM 資料類型和長度為四到八個字元之間。</span><span class="sxs-lookup"><span data-stu-id="06b3a-117">For X12, the service schema defines a time in the GS05 field as of the X12_TM data type and between four and eight characters in length.</span></span>  
  
## <a name="user-action"></a><span data-ttu-id="06b3a-118">使用者動作</span><span class="sxs-lookup"><span data-stu-id="06b3a-118">User Action</span></span>  
 <span data-ttu-id="06b3a-119">若要解決這個錯誤，請確定時間，資料元素中的值符合 EDI 結構描述或 X12 服務結構描述符合交換的 GS05 標頭中的時間值所指定的資料類型，並再重新傳送交換。</span><span class="sxs-lookup"><span data-stu-id="06b3a-119">To resolve this error, make sure that a time value in a data element conforms to the data type specified by the EDI schema or a time value in the GS05 header of an X12 interchange conforms to the service schema, and then have the interchange resent.</span></span>