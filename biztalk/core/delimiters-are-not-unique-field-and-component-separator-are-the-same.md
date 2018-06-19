---
title: 分隔符號不是唯一的欄位與元件分隔符號相同 |Microsoft 文件
ms.custom: ''
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: cba15b30-b07d-4caa-8c43-6b4d8c4ca81c
caps.latest.revision: 9
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 5f803612a905f0be196afcfc0b43af23501ccdf0
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/20/2017
ms.locfileid: "22238550"
---
# <a name="delimiters-are-not-unique-field-and-component-separator-are-the-same"></a><span data-ttu-id="0c801-102">分隔符號不是唯一、 欄位和元件分隔符號相同</span><span class="sxs-lookup"><span data-stu-id="0c801-102">Delimiters are not unique, field and component separator are the same</span></span>
## <a name="details"></a><span data-ttu-id="0c801-103">詳細資料</span><span class="sxs-lookup"><span data-stu-id="0c801-103">Details</span></span>  
  
|||  
|-|-|  
|<span data-ttu-id="0c801-104">產品名稱</span><span class="sxs-lookup"><span data-stu-id="0c801-104">Product Name</span></span>|[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]|  
|<span data-ttu-id="0c801-105">產品版本</span><span class="sxs-lookup"><span data-stu-id="0c801-105">Product Version</span></span>|[!INCLUDE[btsEDIVersion](../includes/btsediversion-md.md)]|  
|<span data-ttu-id="0c801-106">事件識別碼</span><span class="sxs-lookup"><span data-stu-id="0c801-106">Event ID</span></span>|-|  
|<span data-ttu-id="0c801-107">事件來源</span><span class="sxs-lookup"><span data-stu-id="0c801-107">Event Source</span></span>|[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]<span data-ttu-id="0c801-108">EDI</span><span class="sxs-lookup"><span data-stu-id="0c801-108"> EDI</span></span>|  
|<span data-ttu-id="0c801-109">元件</span><span class="sxs-lookup"><span data-stu-id="0c801-109">Component</span></span>|<span data-ttu-id="0c801-110">EDI 引擎</span><span class="sxs-lookup"><span data-stu-id="0c801-110">EDI Engine</span></span>|  
|<span data-ttu-id="0c801-111">符號名稱</span><span class="sxs-lookup"><span data-stu-id="0c801-111">Symbolic Name</span></span>|-|  
|<span data-ttu-id="0c801-112">訊息文字</span><span class="sxs-lookup"><span data-stu-id="0c801-112">Message Text</span></span>|<span data-ttu-id="0c801-113">分隔符號不是唯一、 欄位和元件分隔符號相同</span><span class="sxs-lookup"><span data-stu-id="0c801-113">Delimiters are not unique, field and component separator are the same</span></span>|  
  
## <a name="explanation"></a><span data-ttu-id="0c801-114">說明</span><span class="sxs-lookup"><span data-stu-id="0c801-114">Explanation</span></span>  
 <span data-ttu-id="0c801-115">這個錯誤/警告/資訊事件表示，EDI 傳送管線無法處理外寄交換因為資料元素和元件分隔符號相同的值。</span><span class="sxs-lookup"><span data-stu-id="0c801-115">This Error/Warning/Information event indicates that the EDI send pipeline could not process an outgoing interchange because the data element and component separators were the same value.</span></span> <span data-ttu-id="0c801-116">在 X12 交換，資料元素分隔符號是 ISA 區段的第四個字元的位置中的字元和元件分隔符號是 ISA16 欄位中的字元。</span><span class="sxs-lookup"><span data-stu-id="0c801-116">In an X12 interchange, the data element separator is the character in the fourth character position of the ISA segment and the component separator is the character in the ISA16 field.</span></span> <span data-ttu-id="0c801-117">在 EDIFACT 交換中，資料元素分隔符號是 UNA2 欄位中的字元和元件分隔符號是 UNA1 欄位中的字元。</span><span class="sxs-lookup"><span data-stu-id="0c801-117">In an EDIFACT interchange, the data element separator is the character in the UNA2 field and the component separator is the character in the UNA1 field.</span></span> <span data-ttu-id="0c801-118">兩個具有相同值的分隔符號可能 （但會導致錯誤狀況） 中保留的批次的案例中，或交換是透過傳遞傳輸接收，然後挑選向上為 MessageBox 中 XML 檔案傳送埠。</span><span class="sxs-lookup"><span data-stu-id="0c801-118">Two separators with the same value can occur (but will cause an error condition) in a preserved batch scenario, or if an interchange is received via a passthrough transmit and then picked up by the send port as an XML file in the MessageBox.</span></span>  
  
## <a name="user-action"></a><span data-ttu-id="0c801-119">使用者動作</span><span class="sxs-lookup"><span data-stu-id="0c801-119">User Action</span></span>  
 <span data-ttu-id="0c801-120">若要解決這個錯誤，變更值的其中一個資料元素或元件分隔符號，然後再重新提交交換。</span><span class="sxs-lookup"><span data-stu-id="0c801-120">To resolve this error, change the value of either the data element or component separators, and then resubmit the interchange.</span></span>