---
title: 不支援交易集 |Microsoft 文件
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
ms.openlocfilehash: 751b4bdff008a191a2367faea62fa92b6c15011b
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/20/2017
ms.locfileid: "22278638"
---
# <a name="transaction-set-not-supported"></a><span data-ttu-id="c413d-102">不支援交易集</span><span class="sxs-lookup"><span data-stu-id="c413d-102">Transaction Set Not Supported</span></span>
## <a name="details"></a><span data-ttu-id="c413d-103">詳細資料</span><span class="sxs-lookup"><span data-stu-id="c413d-103">Details</span></span>  
  
|||  
|-|-|  
|<span data-ttu-id="c413d-104">產品名稱</span><span class="sxs-lookup"><span data-stu-id="c413d-104">Product Name</span></span>|[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]|  
|<span data-ttu-id="c413d-105">產品版本</span><span class="sxs-lookup"><span data-stu-id="c413d-105">Product Version</span></span>|[!INCLUDE[btsEDIVersion](../includes/btsediversion-md.md)]|  
|<span data-ttu-id="c413d-106">事件識別碼</span><span class="sxs-lookup"><span data-stu-id="c413d-106">Event ID</span></span>|-|  
|<span data-ttu-id="c413d-107">事件來源</span><span class="sxs-lookup"><span data-stu-id="c413d-107">Event Source</span></span>|[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]<span data-ttu-id="c413d-108">EDI</span><span class="sxs-lookup"><span data-stu-id="c413d-108"> EDI</span></span>|  
|<span data-ttu-id="c413d-109">元件</span><span class="sxs-lookup"><span data-stu-id="c413d-109">Component</span></span>|<span data-ttu-id="c413d-110">EDI 引擎</span><span class="sxs-lookup"><span data-stu-id="c413d-110">EDI Engine</span></span>|  
|<span data-ttu-id="c413d-111">符號名稱</span><span class="sxs-lookup"><span data-stu-id="c413d-111">Symbolic Name</span></span>|<span data-ttu-id="c413d-112">X12TsNotSupportedDescription</span><span class="sxs-lookup"><span data-stu-id="c413d-112">X12TsNotSupportedDescription</span></span>|  
|<span data-ttu-id="c413d-113">訊息文字</span><span class="sxs-lookup"><span data-stu-id="c413d-113">Message Text</span></span>|<span data-ttu-id="c413d-114">不支援交易集</span><span class="sxs-lookup"><span data-stu-id="c413d-114">Transaction Set Not Supported</span></span>|  
  
## <a name="explanation"></a><span data-ttu-id="c413d-115">說明</span><span class="sxs-lookup"><span data-stu-id="c413d-115">Explanation</span></span>  
 <span data-ttu-id="c413d-116">這個錯誤/警告/資訊事件表示，接收管線無法處理內送交換因為文件結構描述尚未部署該交易集的文件類型。</span><span class="sxs-lookup"><span data-stu-id="c413d-116">This Error/Warning/Information event indicates that the receive pipeline could not process the incoming interchange because a document schema has not been deployed for the document type of that transaction set.</span></span>  
  
## <a name="user-action"></a><span data-ttu-id="c413d-117">使用者動作</span><span class="sxs-lookup"><span data-stu-id="c413d-117">User Action</span></span>  
 <span data-ttu-id="c413d-118">若要解決這個錯誤，請在[!INCLUDE[btsVStudioNoVersion](../includes/btsvstudionoversion-md.md)]部署交易集的文件類型的文件結構描述。</span><span class="sxs-lookup"><span data-stu-id="c413d-118">To resolve this error, in [!INCLUDE[btsVStudioNoVersion](../includes/btsvstudionoversion-md.md)] deploy a document schema for the document type of the transaction set.</span></span>