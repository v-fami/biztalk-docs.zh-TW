---
title: "群組控制編號違反語法 |Microsoft 文件"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: e173c914-cb5c-4369-ac2f-8f9abee420cb
caps.latest.revision: "8"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 4c9364260d9c90b9935f894eb3a0ada882057ea5
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/20/2017
---
# <a name="group-control-number-violates-syntax"></a><span data-ttu-id="f96bf-102">群組控制編號違反語法</span><span class="sxs-lookup"><span data-stu-id="f96bf-102">Group control number violates syntax</span></span>
## <a name="details"></a><span data-ttu-id="f96bf-103">詳細資料</span><span class="sxs-lookup"><span data-stu-id="f96bf-103">Details</span></span>  
  
|||  
|-|-|  
|<span data-ttu-id="f96bf-104">產品名稱</span><span class="sxs-lookup"><span data-stu-id="f96bf-104">Product Name</span></span>|[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]|  
|<span data-ttu-id="f96bf-105">產品版本</span><span class="sxs-lookup"><span data-stu-id="f96bf-105">Product Version</span></span>|[!INCLUDE[btsEDIVersion](../includes/btsediversion-md.md)]|  
|<span data-ttu-id="f96bf-106">事件識別碼</span><span class="sxs-lookup"><span data-stu-id="f96bf-106">Event ID</span></span>|-|  
|<span data-ttu-id="f96bf-107">事件來源</span><span class="sxs-lookup"><span data-stu-id="f96bf-107">Event Source</span></span>|[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]<span data-ttu-id="f96bf-108">EDI</span><span class="sxs-lookup"><span data-stu-id="f96bf-108"> EDI</span></span>|  
|<span data-ttu-id="f96bf-109">元件</span><span class="sxs-lookup"><span data-stu-id="f96bf-109">Component</span></span>|<span data-ttu-id="f96bf-110">EDI 引擎</span><span class="sxs-lookup"><span data-stu-id="f96bf-110">EDI Engine</span></span>|  
|<span data-ttu-id="f96bf-111">符號名稱</span><span class="sxs-lookup"><span data-stu-id="f96bf-111">Symbolic Name</span></span>|<span data-ttu-id="f96bf-112">X12FaInvalidControlNumberDescription</span><span class="sxs-lookup"><span data-stu-id="f96bf-112">X12FaInvalidControlNumberDescription</span></span>|  
|<span data-ttu-id="f96bf-113">訊息文字</span><span class="sxs-lookup"><span data-stu-id="f96bf-113">Message Text</span></span>|<span data-ttu-id="f96bf-114">群組控制編號違反語法</span><span class="sxs-lookup"><span data-stu-id="f96bf-114">Group control number violates syntax</span></span>|  
  
## <a name="explanation"></a><span data-ttu-id="f96bf-115">說明</span><span class="sxs-lookup"><span data-stu-id="f96bf-115">Explanation</span></span>  
 <span data-ttu-id="f96bf-116">這個錯誤/警告/資訊事件表示接收管線無法處理內送 X12 交換的群組控制編號 GS06 和 GE02 欄位中的交換，因為不符合指定長度的資料類型服務結構描述。</span><span class="sxs-lookup"><span data-stu-id="f96bf-116">This Error/Warning/Information event indicates that the receive pipeline could not process the incoming X12 interchange because the group control number in the GS06 and GE02 fields of the interchange did not conform to the data type or length specified in the service schema.</span></span> <span data-ttu-id="f96bf-117">服務架構是 X12ServiceSchema BaseArtifacts.dll 中。</span><span class="sxs-lookup"><span data-stu-id="f96bf-117">The service schema is the X12ServiceSchema in BaseArtifacts.dll.</span></span>  
  
## <a name="user-action"></a><span data-ttu-id="f96bf-118">使用者動作</span><span class="sxs-lookup"><span data-stu-id="f96bf-118">User Action</span></span>  
 <span data-ttu-id="f96bf-119">若要解決這個錯誤，請確定符合的資料類型 (X12_N0) 和服務結構描述中指定的長度 （介於一到九位數） GS06 和 GE02 交換的欄位中包含的群組控制編號，並接著必須重新傳送交換。</span><span class="sxs-lookup"><span data-stu-id="f96bf-119">To resolve this error, make sure that the group control numbers contained in the GS06 and GE02 fields of the interchange conform to the data type (X12_N0) and length (between one and nine digits) specified in the service schema, and then have the interchange resent.</span></span>