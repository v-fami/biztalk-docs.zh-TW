---
title: 迴圈路徑 |Microsoft 文件
ms.custom: ''
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- Looping functoids, paths
- maps, conditional looping
ms.assetid: 4612dc2d-2c39-427d-88ac-65f9e85873c7
caps.latest.revision: 7
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: e69e7d1c092ee5ca34b8c2ef3f309eff6c44b271
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/20/2017
ms.locfileid: "22262150"
---
# <a name="loop-paths"></a><span data-ttu-id="27bdf-102">迴圈路徑</span><span class="sxs-lookup"><span data-stu-id="27bdf-102">Loop Paths</span></span>
<span data-ttu-id="27bdf-103">如果其 Max Occurs 屬性大於 1，結構描述中的項目就會進入迴圈。</span><span class="sxs-lookup"><span data-stu-id="27bdf-103">An element in a schema is looping if its Max Occurs property is greater than 1.</span></span> <span data-ttu-id="27bdf-104">當您繪製來源結構描述的迴圈項目與目的結構描述的迴圈項目之間的連結時，就會發生迴圈路徑。</span><span class="sxs-lookup"><span data-stu-id="27bdf-104">A loop path occurs when you draw a link between a looping element in the source schema and a looping element in the destination schema.</span></span>  
  
## <a name="configuring-a-loop-path"></a><span data-ttu-id="27bdf-105">設定迴圈路徑</span><span class="sxs-lookup"><span data-stu-id="27bdf-105">Configuring a Loop Path</span></span>  
 <span data-ttu-id="27bdf-106">建立迴圈路徑時，BizTalk 對應工具會自動處理迴圈記錄。</span><span class="sxs-lookup"><span data-stu-id="27bdf-106">BizTalk Mapper automatically handles the looping records when you create a loop path.</span></span>  
  
 <span data-ttu-id="27bdf-107">將來源結構描述之迴圈記錄中的欄位連結到目的結構描述之迴圈記錄中的欄位，您就可以在對應中設定迴圈路徑。</span><span class="sxs-lookup"><span data-stu-id="27bdf-107">You can configure a loop path in a map by linking a field in a looping record in the source schema to a field that is in a looping record in the destination schema.</span></span> <span data-ttu-id="27bdf-108">下圖顯示僅將食物調查記錄複製到主要地址清單的對應。</span><span class="sxs-lookup"><span data-stu-id="27bdf-108">The figure below shows a map that copies only food survey records into a master address list.</span></span>  
  
 <span data-ttu-id="27bdf-109">![說明迴圈路徑用法的對應。](../core/media/correct-loop-path-map.gif "correct_loop_path_map")</span><span class="sxs-lookup"><span data-stu-id="27bdf-109">![Map illustrating the use of a loop path.](../core/media/correct-loop-path-map.gif "correct_loop_path_map")</span></span>  
<span data-ttu-id="27bdf-110">迴圈路徑對應</span><span class="sxs-lookup"><span data-stu-id="27bdf-110">Loop Path Map</span></span>  
  
## <a name="multiple-loop-paths"></a><span data-ttu-id="27bdf-111">多個迴圈路徑</span><span class="sxs-lookup"><span data-stu-id="27bdf-111">Multiple Loop Paths</span></span>  
 <span data-ttu-id="27bdf-112">將二或多個迴圈記錄包含的欄位連接到單一迴圈記錄包含的欄位時，會在對應中發生多個迴圈路徑。</span><span class="sxs-lookup"><span data-stu-id="27bdf-112">A multiple loop path occurs in a map when you link fields contained by two or more looping records to fields contained in a single looping record.</span></span> <span data-ttu-id="27bdf-113">下圖顯示將從兩個不同調查收集的地址組合到單一主要地址清單中的嘗試。</span><span class="sxs-lookup"><span data-stu-id="27bdf-113">The following figure shows an attempt to combine addresses collected from two different surveys into a single master address list.</span></span>  
  
 <span data-ttu-id="27bdf-114">![具有多個迴圈路徑對應](../core/media/multiple-loop-path-map.gif "multiple_loop_path_map")</span><span class="sxs-lookup"><span data-stu-id="27bdf-114">![Map with multiple loop paths](../core/media/multiple-loop-path-map.gif "multiple_loop_path_map")</span></span>  
<span data-ttu-id="27bdf-115">具有多個迴圈路徑的對應 (不正確)</span><span class="sxs-lookup"><span data-stu-id="27bdf-115">Map With Multiple Loop Paths (Incorrect)</span></span>  
  
 <span data-ttu-id="27bdf-116">此對應不會產生預期的結果。</span><span class="sxs-lookup"><span data-stu-id="27bdf-116">This map will not produce the expected results.</span></span> <span data-ttu-id="27bdf-117">當對應工具在編譯期間遇到多個迴圈路徑時，它會產生警告，並依預設選取第一個迴圈路徑。</span><span class="sxs-lookup"><span data-stu-id="27bdf-117">When the Mapper encounters multiple loop paths during compilation, it produces a warning and selects the first loop path by default.</span></span> <span data-ttu-id="27bdf-118">若要將兩個不同的地址結合成單一主要地址清單中，使用**迴圈**運算質，如以下對應所示。</span><span class="sxs-lookup"><span data-stu-id="27bdf-118">In order to combine the two different addresses into a single master address list, use a **Looping** functoid as shown in the map below.</span></span>  
  
 <span data-ttu-id="27bdf-119">![迴圈運算質用法的對應。](../core/media/loopingfunctoid.gif "loopingfunctoid")</span><span class="sxs-lookup"><span data-stu-id="27bdf-119">![Map illustrating the use of the looping functoid.](../core/media/loopingfunctoid.gif "loopingfunctoid")</span></span>  
<span data-ttu-id="27bdf-120">迴圈運算值對應 (正確)</span><span class="sxs-lookup"><span data-stu-id="27bdf-120">Looping Functoid Map (Correct)</span></span>  
  
 <span data-ttu-id="27bdf-121">**迴圈**應該使用運算質，而不是在下列案例中的多個迴圈路徑：</span><span class="sxs-lookup"><span data-stu-id="27bdf-121">The **Looping** functoid should be used instead of multiple loop paths in the following scenarios:</span></span>  
  
1.  <span data-ttu-id="27bdf-122">當對應工具未在多個迴圈路徑的案例中產生所需的輸出時。</span><span class="sxs-lookup"><span data-stu-id="27bdf-122">When the Mapper does not produce the desired output in a multiple loop paths scenario.</span></span>  
  
2.  <span data-ttu-id="27bdf-123">將輸入執行個體訊息中的多個重複結構組合成輸出執行個體訊息中的單一重複結構。</span><span class="sxs-lookup"><span data-stu-id="27bdf-123">To combine multiple repeating structures in an input instance message into a single repeating structure in the output instance message.</span></span>  
  
3.  <span data-ttu-id="27bdf-124">藉由將單一記錄對應至多個記錄，將一般結構描述轉換成階層式結構描述。</span><span class="sxs-lookup"><span data-stu-id="27bdf-124">To convert a flat schema to a hierarchical schema by mapping a single record to multiple records.</span></span> <span data-ttu-id="27bdf-125">這是將一般結構描述轉換成 Microsoft Commerce Server 目錄的通用作業。</span><span class="sxs-lookup"><span data-stu-id="27bdf-125">This is a common operation in converting flat schemas to Microsoft Commerce Server catalogs.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="27bdf-126">另請參閱</span><span class="sxs-lookup"><span data-stu-id="27bdf-126">See Also</span></span>  
 <span data-ttu-id="27bdf-127">[如何新增迴圈運算質至對應](../core/how-to-add-looping-functoids-to-a-map.md) </span><span class="sxs-lookup"><span data-stu-id="27bdf-127">[How to Add Looping Functoids to a Map](../core/how-to-add-looping-functoids-to-a-map.md) </span></span>  
 [<span data-ttu-id="27bdf-128">迴圈運算質</span><span class="sxs-lookup"><span data-stu-id="27bdf-128">Looping Functoid</span></span>](../core/looping-functoid.md)