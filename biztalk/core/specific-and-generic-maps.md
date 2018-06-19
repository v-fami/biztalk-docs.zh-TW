---
title: 特定和一般對應 |Microsoft 文件
ms.custom: ''
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- maps, specific
- maps, generic
ms.assetid: ee26dd13-affb-47c5-961a-f2377129de22
caps.latest.revision: 11
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: a6ad84e23c3981730ee4cf7655a42d87c46158e3
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/20/2017
ms.locfileid: "22276302"
---
# <a name="specific-and-generic-maps"></a><span data-ttu-id="a5a46-102">特定與一般對應</span><span class="sxs-lookup"><span data-stu-id="a5a46-102">Specific and Generic Maps</span></span>
<span data-ttu-id="a5a46-103">當您建立將資料轉換的對應時，您可以建立*特定*或*泛型*對應。</span><span class="sxs-lookup"><span data-stu-id="a5a46-103">When you create a map that transforms data, you can create either a *specific* or a *generic* map.</span></span>  
  
 <span data-ttu-id="a5a46-104">您可以使用特定對應，以符合特殊交易夥伴的需求。</span><span class="sxs-lookup"><span data-stu-id="a5a46-104">You use a specific map to meet the needs of a particular trading partner.</span></span> <span data-ttu-id="a5a46-105">當您有非常特殊的商務需求或與交易夥伴有特殊的商務協議時，請使用特定對應。</span><span class="sxs-lookup"><span data-stu-id="a5a46-105">Use a specific map when you have very specific business needs or business agreements with your trading partner.</span></span> <span data-ttu-id="a5a46-106">特定對應的優點在於它可自訂以符合特定交易夥伴的商務功能需求。</span><span class="sxs-lookup"><span data-stu-id="a5a46-106">The advantage of a specific map is that it is customized to meet the needs of the business functions you have with specific trading partners.</span></span> <span data-ttu-id="a5a46-107">特定對應的缺點在於它不能與多個交易夥伴搭配使用。</span><span class="sxs-lookup"><span data-stu-id="a5a46-107">The disadvantage of a specific map is that it cannot be used with multiple trading partners.</span></span> <span data-ttu-id="a5a46-108">若您將交易夥伴數目與那些交易夥伴交換的不同訊息類型數目相乘，則必須配置足夠的時間與資源來管理所有關聯的對應。</span><span class="sxs-lookup"><span data-stu-id="a5a46-108">If you multiply the number of trading partners by the number of different message types exchanged with those trading partners, you must allocate enough time and resources to manage all of the associated maps.</span></span>  
  
 <span data-ttu-id="a5a46-109">相反地，一般對應則設計為可搭配多個交易夥伴使用。</span><span class="sxs-lookup"><span data-stu-id="a5a46-109">Generic maps, on the other hand, are designed to be used with multiple trading partners.</span></span> <span data-ttu-id="a5a46-110">因此，您不需要開發與維護特殊商務文件的多個結構描述，而只需要為每個類型的商務文件建立一個結構描述，然後搭配所有交易夥伴使用。</span><span class="sxs-lookup"><span data-stu-id="a5a46-110">Therefore, instead of developing and maintaining multiple schemas for a particular business document, you create one schema for each type of business document, and then use them with all of your trading partners.</span></span> <span data-ttu-id="a5a46-111">雖然以一個對應搭配多個交易夥伴使用可節省時間與資源，但這些對應並非自訂，所以可能無法符合所有狀況的需求。</span><span class="sxs-lookup"><span data-stu-id="a5a46-111">While using one map with multiple trading partners saves time and resources, these maps are not customized and may not be meet the needs of all cases.</span></span>  
  
 <span data-ttu-id="a5a46-112">您可能要同時建立特定和一般對應，依照您的商務性質而定。</span><span class="sxs-lookup"><span data-stu-id="a5a46-112">It is likely that you will create both specific and generic maps, depending on the nature of your business.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="a5a46-113">另請參閱</span><span class="sxs-lookup"><span data-stu-id="a5a46-113">See Also</span></span>  
 <span data-ttu-id="a5a46-114">[對應](../core/maps.md) </span><span class="sxs-lookup"><span data-stu-id="a5a46-114">[Maps](../core/maps.md) </span></span>  
 [<span data-ttu-id="a5a46-115">使用 BizTalk 對應工具建立對應</span><span class="sxs-lookup"><span data-stu-id="a5a46-115">Creating Maps Using BizTalk Mapper</span></span>](../core/creating-maps-using-biztalk-mapper.md)