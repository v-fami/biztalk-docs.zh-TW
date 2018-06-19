---
title: 如何解析對應警告和錯誤 |Microsoft 文件
ms.custom: ''
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: e8a3e7f3-c96c-4d3d-9f7c-d2bfd9ace4fd
caps.latest.revision: 11
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 1a2983a53bb47aa66d1564772d0f8e033132e5a8
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/20/2017
ms.locfileid: "22254878"
---
# <a name="how-to-resolve-map-warnings-and-errors"></a>如何解析對應警告和錯誤
當您編譯對應時，可能會發現編譯程序所導致的警告與錯誤。  
  
## <a name="resolve-warnings-and-errors-when-building-a-map"></a>解析建置對應時的警告和錯誤  
  
1.  對於連結與運算質錯誤，在**錯誤清單**視窗中，按兩下任何描述。  
  
     就會反白顯示與該錯誤關聯的連結、運算質或結構描述。 解析問題。  
  
2.  檢閱**描述**區域**錯誤清單**視窗來判斷其他錯誤。  
  
3.  按一下**輸出**視窗索引標籤以檢視其他警告與錯誤訊息資訊。  
  
4.  在您解決所有問題之後，以滑鼠右鍵按一下方案總管 中的對應檔案名稱，然後按一下**測試對應**或**建置方案**、 為情況下可能要。  
  
    > [!NOTE]
    >  若發生警告，則問題可能存在幾個格線頁上。 例如，您有一筆記錄的格線頁 1 (名為**項目**) 來源結構描述樹狀結構中，連結到記錄 (名為**數目**) 目的結構描述樹狀結構中。 2 的格線頁中，您有一筆記錄 (名為**產品**) 在來源結構描述樹狀結構連結到相同**數目**記錄目的地結構描述樹狀結構。 在此案例中，會產生警告訊息通知您有多個輸入相同的記錄。 不過您檢視格線頁 1，如果您看到只有一個輸入**數目**記錄。 
  
## <a name="see-also"></a>另請參閱  
 [編譯和測試對應](../core/compiling-and-testing-maps.md)   
 [BizTalk 對應工具 」 錯誤](../core/biztalk-mapper-errors.md)   
 [地圖疑難排解](../core/troubleshooting-maps.md)