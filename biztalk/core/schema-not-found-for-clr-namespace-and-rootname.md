---
title: 找不到 CLR 命名空間和 rootName 的結構描述 |Microsoft Docs
ms.custom: ''
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: db283d81-1cb0-460d-ace4-49a91ceb4a02
caps.latest.revision: 8
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: a830d46a439ad85e5e9e3d54afaca688dac201ca
ms.sourcegitcommit: 266308ec5c6a9d8d80ff298ee6051b4843c5d626
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/27/2018
ms.locfileid: "36966343"
---
# <a name="schema-not-found-for-clr-namespace-and-rootname"></a><span data-ttu-id="217bf-102">找不到 CLR 命名空間和 rootName 的結構描述</span><span class="sxs-lookup"><span data-stu-id="217bf-102">Schema not found for CLR Namespace and rootName</span></span>
## <a name="details"></a><span data-ttu-id="217bf-103">詳細資料</span><span class="sxs-lookup"><span data-stu-id="217bf-103">Details</span></span>  
  
|                 |                                                                                        |
|-----------------|----------------------------------------------------------------------------------------|
|  <span data-ttu-id="217bf-104">產品名稱</span><span class="sxs-lookup"><span data-stu-id="217bf-104">Product Name</span></span>   |   [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]   |
| <span data-ttu-id="217bf-105">產品版本</span><span class="sxs-lookup"><span data-stu-id="217bf-105">Product Version</span></span> |               [!INCLUDE[btsEDIVersion](../includes/btsediversion-md.md)]               |
|    <span data-ttu-id="217bf-106">事件識別碼</span><span class="sxs-lookup"><span data-stu-id="217bf-106">Event ID</span></span>     |                                           -                                            |
|  <span data-ttu-id="217bf-107">事件來源</span><span class="sxs-lookup"><span data-stu-id="217bf-107">Event Source</span></span>   | [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]<span data-ttu-id="217bf-108"> EDI</span><span class="sxs-lookup"><span data-stu-id="217bf-108"> EDI</span></span> |
|    <span data-ttu-id="217bf-109">元件</span><span class="sxs-lookup"><span data-stu-id="217bf-109">Component</span></span>    |                                       <span data-ttu-id="217bf-110">將 EDI 引擎</span><span class="sxs-lookup"><span data-stu-id="217bf-110">EDI Engine</span></span>                                       |
|  <span data-ttu-id="217bf-111">符號名稱</span><span class="sxs-lookup"><span data-stu-id="217bf-111">Symbolic Name</span></span>  |                               <span data-ttu-id="217bf-112">SchemaNotFoundForCLRAndRN</span><span class="sxs-lookup"><span data-stu-id="217bf-112">SchemaNotFoundForCLRAndRN</span></span>                                |
|  <span data-ttu-id="217bf-113">訊息文字</span><span class="sxs-lookup"><span data-stu-id="217bf-113">Message Text</span></span>   |              <span data-ttu-id="217bf-114">找不到 CLR 命名空間的結構描述 ={0}和 rootName = {1}</span><span class="sxs-lookup"><span data-stu-id="217bf-114">Schema not found for CLR Namespace = {0} and rootName = {1}</span></span>               |
  
## <a name="explanation"></a><span data-ttu-id="217bf-115">說明</span><span class="sxs-lookup"><span data-stu-id="217bf-115">Explanation</span></span>  
 <span data-ttu-id="217bf-116">這個錯誤/警告/資訊事件表示接收管線找不到使用與交換關聯的根名稱和已解決之交換的合作對象相關聯的命名空間的文件結構描述。</span><span class="sxs-lookup"><span data-stu-id="217bf-116">This Error/Warning/Information event indicates that the receive pipeline could not find the document schema using the root name associated with the interchange and the namespace associated with the party that was resolved for the interchange.</span></span>  
  
## <a name="user-action"></a><span data-ttu-id="217bf-117">使用者動作</span><span class="sxs-lookup"><span data-stu-id="217bf-117">User Action</span></span>  
 <span data-ttu-id="217bf-118">若要解決此錯誤，確定從交換採用的根目錄名稱與根據已解析合作對象之屬性決定的命名空間都對應部署的結構描述。</span><span class="sxs-lookup"><span data-stu-id="217bf-118">To resolve this error, ensure that the root name taken from the interchange and the namespace determined from the properties of the resolved party correspond together to a deployed schema.</span></span> <span data-ttu-id="217bf-119">BizTalk 根據交換的文件類型和版本判斷根目錄名稱。</span><span class="sxs-lookup"><span data-stu-id="217bf-119">BizTalk determines the root name from the document type and version in the interchange.</span></span> <span data-ttu-id="217bf-120">BizTalk 根據 [預設目標命名空間] 欄位 (針對預設結構描述)，或交換處理屬性中的 [啟用自訂交易集定義] 方格 (針對自訂結構描述)，判斷結構描述。</span><span class="sxs-lookup"><span data-stu-id="217bf-120">BizTalk determines the schema from the Default Target Namespace field (for default schemas) or the "Enable custom transaction set definitions" grid (for custom schemas) in the Interchange Processing Properties.</span></span>