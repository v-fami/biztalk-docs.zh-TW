---
title: 控制結構描述標頭區段應該依照正確順序 |Microsoft Docs
ms.custom: ''
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 88f38e8f-243a-467f-84bd-a232ef148b4b
caps.latest.revision: 8
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 2c86b8d66526c0406faedeac0aedbbe0e1b270ad
ms.sourcegitcommit: 266308ec5c6a9d8d80ff298ee6051b4843c5d626
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/27/2018
ms.locfileid: "36967919"
---
# <a name="control-schema-should-have-header-segments-in-the-correct-order"></a><span data-ttu-id="007cd-102">控制結構描述標頭區段應該依照正確順序</span><span class="sxs-lookup"><span data-stu-id="007cd-102">Control schema should have header segments in the correct order</span></span>
## <a name="details"></a><span data-ttu-id="007cd-103">詳細資料</span><span class="sxs-lookup"><span data-stu-id="007cd-103">Details</span></span>  
  
|                 |                                                                                        |
|-----------------|----------------------------------------------------------------------------------------|
|  <span data-ttu-id="007cd-104">產品名稱</span><span class="sxs-lookup"><span data-stu-id="007cd-104">Product Name</span></span>   |   [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]   |
| <span data-ttu-id="007cd-105">產品版本</span><span class="sxs-lookup"><span data-stu-id="007cd-105">Product Version</span></span> |               [!INCLUDE[btsEDIVersion](../includes/btsediversion-md.md)]               |
|    <span data-ttu-id="007cd-106">事件識別碼</span><span class="sxs-lookup"><span data-stu-id="007cd-106">Event ID</span></span>     |                                           -                                            |
|  <span data-ttu-id="007cd-107">事件來源</span><span class="sxs-lookup"><span data-stu-id="007cd-107">Event Source</span></span>   | [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]<span data-ttu-id="007cd-108"> EDI</span><span class="sxs-lookup"><span data-stu-id="007cd-108"> EDI</span></span> |
|    <span data-ttu-id="007cd-109">元件</span><span class="sxs-lookup"><span data-stu-id="007cd-109">Component</span></span>    |                                       <span data-ttu-id="007cd-110">將 EDI 引擎</span><span class="sxs-lookup"><span data-stu-id="007cd-110">EDI Engine</span></span>                                       |
|  <span data-ttu-id="007cd-111">符號名稱</span><span class="sxs-lookup"><span data-stu-id="007cd-111">Symbolic Name</span></span>  |                                           -                                            |
|  <span data-ttu-id="007cd-112">訊息文字</span><span class="sxs-lookup"><span data-stu-id="007cd-112">Message Text</span></span>   |  <span data-ttu-id="007cd-113">控制結構描述的區段應該依照下列順序： ISA GS ST...SE GE IEA</span><span class="sxs-lookup"><span data-stu-id="007cd-113">Control schema should have segments in the following order: ISA GS ST .... SE GE IEA</span></span>  |
  
## <a name="explanation"></a><span data-ttu-id="007cd-114">說明</span><span class="sxs-lookup"><span data-stu-id="007cd-114">Explanation</span></span>  
 <span data-ttu-id="007cd-115">這個錯誤/警告/資訊事件表示 EDI 接收管線無法處理內送交換，因為標頭和結尾的交換、 群組和交易集不正確的順序，在交換中。</span><span class="sxs-lookup"><span data-stu-id="007cd-115">This Error/Warning/Information event indicates that the EDI receive pipeline could not process the incoming interchange because the headers and trailers for the interchange, groups, and transaction sets were not in the correct order in the interchange.</span></span>  
  
## <a name="user-action"></a><span data-ttu-id="007cd-116">使用者動作</span><span class="sxs-lookup"><span data-stu-id="007cd-116">User Action</span></span>  
 <span data-ttu-id="007cd-117">若要解決這個錯誤，請確定 ISA、 GS 和 ST 標頭和 SE、 GE 和 IEA 結尾，會在交換中，正確的順序，然後再重新傳送交換。</span><span class="sxs-lookup"><span data-stu-id="007cd-117">To resolve this error, ensure that the ISA, GS, and ST headers, and the SE, GE, and IEA trailers, are in the correct order in the interchange, and then resend the interchange.</span></span>