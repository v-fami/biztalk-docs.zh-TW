---
title: 無法辨認的輸出訊息封送處理類型 |Microsoft Docs
ms.custom: ''
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: e675112b-12f3-47ff-95f7-ce1a05db120e
caps.latest.revision: 11
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: cda3e7bd3d20e39bb59c2c1fbe14dfc964fd541a
ms.sourcegitcommit: 266308ec5c6a9d8d80ff298ee6051b4843c5d626
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/27/2018
ms.locfileid: "37023428"
---
# <a name="unrecognized-outbound-message-marshalling-type"></a><span data-ttu-id="5dafd-102">無法辨認的輸出訊息封送處理類型</span><span class="sxs-lookup"><span data-stu-id="5dafd-102">Unrecognized outbound message marshalling type</span></span>
## <a name="details"></a><span data-ttu-id="5dafd-103">詳細資料</span><span class="sxs-lookup"><span data-stu-id="5dafd-103">Details</span></span>  
  
|                 |                                                                                        |
|-----------------|----------------------------------------------------------------------------------------|
|  <span data-ttu-id="5dafd-104">產品名稱</span><span class="sxs-lookup"><span data-stu-id="5dafd-104">Product Name</span></span>   |   [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]   |
| <span data-ttu-id="5dafd-105">產品版本</span><span class="sxs-lookup"><span data-stu-id="5dafd-105">Product Version</span></span> |               [!INCLUDE[btsWCFVersion](../includes/btswcfversion-md.md)]               |
|    <span data-ttu-id="5dafd-106">事件識別碼</span><span class="sxs-lookup"><span data-stu-id="5dafd-106">Event ID</span></span>     |                                           <span data-ttu-id="5dafd-107">0</span><span class="sxs-lookup"><span data-stu-id="5dafd-107">0</span></span>                                            |
|  <span data-ttu-id="5dafd-108">事件來源</span><span class="sxs-lookup"><span data-stu-id="5dafd-108">Event Source</span></span>   |                                           <span data-ttu-id="5dafd-109">0</span><span class="sxs-lookup"><span data-stu-id="5dafd-109">0</span></span>                                            |
|    <span data-ttu-id="5dafd-110">元件</span><span class="sxs-lookup"><span data-stu-id="5dafd-110">Component</span></span>    |                                           <span data-ttu-id="5dafd-111">0</span><span class="sxs-lookup"><span data-stu-id="5dafd-111">0</span></span>                                            |
|  <span data-ttu-id="5dafd-112">符號名稱</span><span class="sxs-lookup"><span data-stu-id="5dafd-112">Symbolic Name</span></span>  |                                           <span data-ttu-id="5dafd-113">0</span><span class="sxs-lookup"><span data-stu-id="5dafd-113">0</span></span>                                            |
|  <span data-ttu-id="5dafd-114">訊息文字</span><span class="sxs-lookup"><span data-stu-id="5dafd-114">Message Text</span></span>   | <span data-ttu-id="5dafd-115">無法辨認的輸出訊息封送類型;預期 UseBodyElement 或 UseTemplate</span><span class="sxs-lookup"><span data-stu-id="5dafd-115">Unrecognized outbound message marshalling type; expected UseBodyElement or UseTemplate</span></span> |
  
## <a name="explanation"></a><span data-ttu-id="5dafd-116">說明</span><span class="sxs-lookup"><span data-stu-id="5dafd-116">Explanation</span></span>  
 <span data-ttu-id="5dafd-117">WCF 中。OutboundBodyLocation 屬性設定為比 UseBodyElement 或 UseTemplate，自訂管線元件或協調流程中不同的值。</span><span class="sxs-lookup"><span data-stu-id="5dafd-117">The WCF.OutboundBodyLocation property is set to a value different than UseBodyElement or UseTemplate, in a custom pipeline component or orchestration.</span></span>  
  
## <a name="user-action"></a><span data-ttu-id="5dafd-118">使用者動作</span><span class="sxs-lookup"><span data-stu-id="5dafd-118">User Action</span></span>  
 <span data-ttu-id="5dafd-119">設定 WCF。OutboundBodyLocation 屬性設為有效的值。</span><span class="sxs-lookup"><span data-stu-id="5dafd-119">Set the WCF.OutboundBodyLocation property to a valid value.</span></span> <span data-ttu-id="5dafd-120">有效值為"UseBodyElement 」 或 「 UseTemplate"這是程式碼變更。</span><span class="sxs-lookup"><span data-stu-id="5dafd-120">Valid values are "UseBodyElement" or "UseTemplate" This is a code change.</span></span>   
<span data-ttu-id="5dafd-121">如需輸出訊息的詳細資訊，請參閱中的下列資源[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]幫助：</span><span class="sxs-lookup"><span data-stu-id="5dafd-121">For further information about outbound messaging, see the following resources in the [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] Help:</span></span>  
  
-   [<span data-ttu-id="5dafd-122">使用 WCF 配接器內容屬性設定動態傳送埠</span><span class="sxs-lookup"><span data-stu-id="5dafd-122">Configuring Dynamic Send Ports Using WCF Adapters Context Properties</span></span>](../core/configuring-dynamic-send-ports-using-wcf-adapters-context-properties.md)  
  
-   [<span data-ttu-id="5dafd-123">設定 WCF 配接器</span><span class="sxs-lookup"><span data-stu-id="5dafd-123">Configuring the WCF Adapters</span></span>](../core/configuring-the-wcf-adapters.md)