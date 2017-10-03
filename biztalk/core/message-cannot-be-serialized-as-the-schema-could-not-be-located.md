---
title: "無法序列化訊息，因為找不到結構描述 |Microsoft 文件"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 37897c04-650d-4695-846d-b8ba61365647
caps.latest.revision: "8"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: b887d4a07d7a461278d3858289882a9ce441e9e2
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/20/2017
---
# <a name="message-cannot-be-serialized-as-the-schema-could-not-be-located"></a><span data-ttu-id="0d798-102">無法序列化訊息，因為找不到結構描述</span><span class="sxs-lookup"><span data-stu-id="0d798-102">Message cannot be serialized as the schema could not be located</span></span>
## <a name="details"></a><span data-ttu-id="0d798-103">詳細資料</span><span class="sxs-lookup"><span data-stu-id="0d798-103">Details</span></span>  
  
|||  
|-|-|  
|<span data-ttu-id="0d798-104">產品名稱</span><span class="sxs-lookup"><span data-stu-id="0d798-104">Product Name</span></span>|[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]|  
|<span data-ttu-id="0d798-105">產品版本</span><span class="sxs-lookup"><span data-stu-id="0d798-105">Product Version</span></span>|[!INCLUDE[btsEDIVersion](../includes/btsediversion-md.md)]|  
|<span data-ttu-id="0d798-106">事件識別碼</span><span class="sxs-lookup"><span data-stu-id="0d798-106">Event ID</span></span>|-|  
|<span data-ttu-id="0d798-107">事件來源</span><span class="sxs-lookup"><span data-stu-id="0d798-107">Event Source</span></span>|[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]<span data-ttu-id="0d798-108">EDI</span><span class="sxs-lookup"><span data-stu-id="0d798-108"> EDI</span></span>|  
|<span data-ttu-id="0d798-109">元件</span><span class="sxs-lookup"><span data-stu-id="0d798-109">Component</span></span>|<span data-ttu-id="0d798-110">EDI 引擎</span><span class="sxs-lookup"><span data-stu-id="0d798-110">EDI Engine</span></span>|  
|<span data-ttu-id="0d798-111">符號名稱</span><span class="sxs-lookup"><span data-stu-id="0d798-111">Symbolic Name</span></span>|<span data-ttu-id="0d798-112">MessageSerializationFailureDueToMissingSchema</span><span class="sxs-lookup"><span data-stu-id="0d798-112">MessageSerializationFailureDueToMissingSchema</span></span>|  
|<span data-ttu-id="0d798-113">訊息文字</span><span class="sxs-lookup"><span data-stu-id="0d798-113">Message Text</span></span>|<span data-ttu-id="0d798-114">無法序列化訊息，因為找不到結構描述 {0}。</span><span class="sxs-lookup"><span data-stu-id="0d798-114">Message can not be serialized as the schema {0} could not be located.</span></span> <span data-ttu-id="0d798-115">無法部署結構描述或部署多個複本。</span><span class="sxs-lookup"><span data-stu-id="0d798-115">Either the schema is not deployed or multiple copies are deployed.</span></span>|  
  
## <a name="explanation"></a><span data-ttu-id="0d798-116">說明</span><span class="sxs-lookup"><span data-stu-id="0d798-116">Explanation</span></span>  
 <span data-ttu-id="0d798-117">這個錯誤/警告/資訊事件表示，傳送管線無法序列化到外寄交換因為管線無法判斷它需要用來序列化交換的結構描述。</span><span class="sxs-lookup"><span data-stu-id="0d798-117">This Error/Warning/Information event indicates that the send pipeline could not serialize the outgoing interchange because the pipeline could not determine the schema that it needed to use to serialize the interchange.</span></span> <span data-ttu-id="0d798-118">結構描述可能未部署或部署的結構描述的多個複本。</span><span class="sxs-lookup"><span data-stu-id="0d798-118">The schema was either not deployed or multiple copies of the schema were deployed.</span></span>  
  
## <a name="user-action"></a><span data-ttu-id="0d798-119">使用者動作</span><span class="sxs-lookup"><span data-stu-id="0d798-119">User Action</span></span>  
 <span data-ttu-id="0d798-120">若要解決這個錯誤，執行下列其中一項：</span><span class="sxs-lookup"><span data-stu-id="0d798-120">To resolve this error, do one of the following:</span></span>  
  
1.  <span data-ttu-id="0d798-121">與交換關聯的結構描述尚未部署，如果開啟 Visual Studio、 結構描述加入 BizTalk 專案，然後建置並部署專案。</span><span class="sxs-lookup"><span data-stu-id="0d798-121">If the schema associated with the interchange has not been deployed, open Visual Studio, add the schema to a BizTalk project, and then build and deploy the project.</span></span>  
  
2.  <span data-ttu-id="0d798-122">如果已部署的結構描述的多個複本，開啟 Visual Studio，並解除部署，但其中一個結構描述與交換關聯的複本。</span><span class="sxs-lookup"><span data-stu-id="0d798-122">If more than one copy of the schema has been deployed, open Visual Studio, and undeploy all but one of the copies of the schema associated with the interchange.</span></span>