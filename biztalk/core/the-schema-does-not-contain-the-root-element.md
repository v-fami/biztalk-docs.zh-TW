---
title: 結構描述不包含根項目 |Microsoft Docs
ms.custom: ''
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: efc33f2b-9e14-4d2e-8c8a-32b7696f80ea
caps.latest.revision: 8
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: fc2191a5d9ea891efa285d8fc5006f243319fde5
ms.sourcegitcommit: 266308ec5c6a9d8d80ff298ee6051b4843c5d626
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/27/2018
ms.locfileid: "37008439"
---
# <a name="the-schema-does-not-contain-the-root-element"></a><span data-ttu-id="00e49-102">結構描述不包含根項目</span><span class="sxs-lookup"><span data-stu-id="00e49-102">The schema does not contain the root element</span></span>
## <a name="details"></a><span data-ttu-id="00e49-103">詳細資料</span><span class="sxs-lookup"><span data-stu-id="00e49-103">Details</span></span>  
  
|                 |                                                                                        |
|-----------------|----------------------------------------------------------------------------------------|
|  <span data-ttu-id="00e49-104">產品名稱</span><span class="sxs-lookup"><span data-stu-id="00e49-104">Product Name</span></span>   |   [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]   |
| <span data-ttu-id="00e49-105">產品版本</span><span class="sxs-lookup"><span data-stu-id="00e49-105">Product Version</span></span> |               [!INCLUDE[btsEDIVersion](../includes/btsediversion-md.md)]               |
|    <span data-ttu-id="00e49-106">事件識別碼</span><span class="sxs-lookup"><span data-stu-id="00e49-106">Event ID</span></span>     |                                           -                                            |
|  <span data-ttu-id="00e49-107">事件來源</span><span class="sxs-lookup"><span data-stu-id="00e49-107">Event Source</span></span>   | [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]<span data-ttu-id="00e49-108"> EDI</span><span class="sxs-lookup"><span data-stu-id="00e49-108"> EDI</span></span> |
|    <span data-ttu-id="00e49-109">元件</span><span class="sxs-lookup"><span data-stu-id="00e49-109">Component</span></span>    |                                       <span data-ttu-id="00e49-110">將 EDI 引擎</span><span class="sxs-lookup"><span data-stu-id="00e49-110">EDI Engine</span></span>                                       |
|  <span data-ttu-id="00e49-111">符號名稱</span><span class="sxs-lookup"><span data-stu-id="00e49-111">Symbolic Name</span></span>  |                             <span data-ttu-id="00e49-112">SchemaCode102ENullRootElement</span><span class="sxs-lookup"><span data-stu-id="00e49-112">SchemaCode102ENullRootElement</span></span>                              |
|  <span data-ttu-id="00e49-113">訊息文字</span><span class="sxs-lookup"><span data-stu-id="00e49-113">Message Text</span></span>   |                    <span data-ttu-id="00e49-114">結構描述不包含根項目 {0}</span><span class="sxs-lookup"><span data-stu-id="00e49-114">The schema does not contain the root element {0}</span></span>                    |
  
## <a name="explanation"></a><span data-ttu-id="00e49-115">說明</span><span class="sxs-lookup"><span data-stu-id="00e49-115">Explanation</span></span>  
 <span data-ttu-id="00e49-116">這個錯誤/警告/資訊事件表示接收管線無法處理內送訊息或傳送管線無法處理外寄訊息，因為用以驗證訊息的結構描述未包含根項目。</span><span class="sxs-lookup"><span data-stu-id="00e49-116">This Error/Warning/Information event indicates that the receive pipeline could not process the incoming message or the send pipeline could not process the outgoing message because the schema used to validate the message did not contain the root element.</span></span>  
  
## <a name="user-action"></a><span data-ttu-id="00e49-117">使用者動作</span><span class="sxs-lookup"><span data-stu-id="00e49-117">User Action</span></span>  
 <span data-ttu-id="00e49-118">若要解決此錯誤，解除部署文件結構描述，新增根元素至結構描述，然後重新部署結構描述。</span><span class="sxs-lookup"><span data-stu-id="00e49-118">To resolve this error, undeploy the document schema, add the root element to the schema, and then redeploy the schema.</span></span>