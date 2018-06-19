---
title: 條件式迴圈 |Microsoft 文件
ms.custom: ''
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- Looping functoids, conditional
- Equal functoids
- maps, conditional looping
ms.assetid: eb16efb8-b12c-47d6-afc9-579fc85ea59c
caps.latest.revision: 6
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: c5452f6b8768442b95ac6bddde0e84ba07f68c85
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/20/2017
ms.locfileid: "22231974"
---
# <a name="conditional-looping"></a>條件式迴圈
您可以將條件加入至**迴圈**運算質所連結的輸出**迴圈**運算質和**邏輯**運算質到相同目的記錄。 只有在邏輯條件相符時，才會建立目的記錄。  
  
## <a name="conditional-looping-map"></a>條件式迴圈對應  
 ![說明條件式迴圈運算質的對應。] (../core/media/loopingconditionalfunctoid.gif "loopingconditionalfunctoid")  
  
 在上圖中，第一個**等於**運算質會**名稱**欄位底下 **[foodsurvey]** 至"Wendy wheeler"做比較。 第二個**等於**運算質會**名稱**欄位底下 **[flowersurvey]** 至"Kelly focht"做比較。 因此，對應會建立目的地**位址**記錄只會針對兩個名稱。 使用中的範例資料**迴圈**運算質範例中，輸出執行個體訊息會顯示如下。  
  
```  
<ns0:MasterAddresses xmlns:ns0="http://ConditionalLoop.MasterAddresses">  
    <Address Name="Wendy Wheeler" Street="7890 Broadway" City="Columbus" State="OH" PostalCode="46290">  
    <Address Name="Kelly Focht" Street="456 1st Ave" City="Miami" State="FL" PostalCode="81406">  
</ns0:MasterAddresses>  
```  
  
## <a name="see-also"></a>另請參閱  
 [如何新增迴圈運算質至對應](../core/how-to-add-looping-functoids-to-a-map.md)   
 [進階運算質](../core/advanced-functoids.md)   
 [索引運算質](../core/index-functoid.md)   
 [反覆項目運算質](../core/iteration-functoid.md)   
 [迴圈運算質](../core/looping-functoid.md)   
 [記錄計數運算質](../core/record-count-functoid.md)