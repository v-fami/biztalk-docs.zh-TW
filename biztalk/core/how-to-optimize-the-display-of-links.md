---
title: 如何最佳化連結顯示 |Microsoft 文件
ms.custom: ''
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 2a9e16ff-01d3-4b7d-91c4-59d17266ee6d
caps.latest.revision: 9
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 689ab4c67bfe8cabc8109c373e899d391fdd56a5
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/20/2017
ms.locfileid: "22254382"
---
# <a name="how-to-optimize-the-display-of-links"></a>如何最佳化連結的顯示
當結構描述很大時，對應中可能包括來源與目的結構描述間的大量連結。 對應介面中若有許多連結，您會發現難以追蹤您需要使用的連結或物件。 此外，您不容易追蹤來源結構描述、連結、運算質以及目的結構描述之間的端對端關係。 在 BizTalk 對應工具中，您可以更妥善地管理複雜和大型的結構描述，並讓對應中的連結顯示呈現最佳狀態。 此主題提供如何檢視連結的詳細資訊。  
  
 您可以將連結分類如下：  
  
-   部分在範圍中  
  
-   完全在範圍中  
  
-   完全不在範圍中  
  
## <a name="prerequisites"></a>必要條件  
 這些指示需要執行中的 BizTalk 對應工具。  
  
## <a name="to-view-the-links-partially-in-scope"></a>檢視部分在範圍中的連結  
 至少有一端可在格線介面上看見的連結就稱為「部分在範圍中」。  
  
 下圖顯示「部分在範圍中」的連結。 格線頁上會以虛線的形式顯示這些連結。  
  
 在格線介面上，按一下部分可見的連結，然後格線頁就會自動向上/向下移動，以讓該關係進入目前的檢視。  
  
 ![部分在範圍中的對應工具連結](../core/media/mapper-partiallyinscope.gif "Mapper_PartiallyInScope")  
  
## <a name="to-view-the-links-completely-in-scope"></a>檢視完全在範圍中的連結  
 兩端 (節點對節點、節點對運算質、運算質對運算質，或運算質對節點) 都可以在格線介面上看見的連結稱為「完全在範圍中」。  
  
 下圖顯示 "DataCollection1" 與 "ST01" 之間 (完全在範圍中) 的連結。  
  
 按一下該連結，就會選取從來源節點至目標節點的關係。  
  
 ![完全在範圍中的對應工具連結](../core/media/mapper-completelyinscope.gif "Mapper_CompletelyInScope")  
  
## <a name="to-view-the-links-completely-out-of-scope"></a>檢視完全不在範圍中的連結  
 在目前的對應檢視中，看不到其任一端結束點的連結，稱為「完全不在範圍中」。  
  
 下圖顯示「完全不在範圍中」的連結。  
  
 如果您不想顯示這些連結，在地圖上的介面 （因為不連結會顯示），您可以選擇將其關閉，依序按一下![顯示所有連結](../core/media/mapper-showhideoutscopelinks.gif "Mapper_ShowHideOutScopeLinks")在對應工具公用程式功能區。 這樣可以降低格線檢視上可看見的連結數量。  
  
 ![完全超出範圍的對應工具連結](../core/media/mapper-completelyoutscope.gif "Mapper_CompletelyOutScope")  
  
## <a name="see-also"></a>另請參閱  
 [使用 BizTalk 對應工具中的增強的功能](../core/using-enhanced-features-in-biztalk-mapper.md)