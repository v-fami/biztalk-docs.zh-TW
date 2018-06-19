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
# <a name="loop-paths"></a>迴圈路徑
如果其 Max Occurs 屬性大於 1，結構描述中的項目就會進入迴圈。 當您繪製來源結構描述的迴圈項目與目的結構描述的迴圈項目之間的連結時，就會發生迴圈路徑。  
  
## <a name="configuring-a-loop-path"></a>設定迴圈路徑  
 建立迴圈路徑時，BizTalk 對應工具會自動處理迴圈記錄。  
  
 將來源結構描述之迴圈記錄中的欄位連結到目的結構描述之迴圈記錄中的欄位，您就可以在對應中設定迴圈路徑。 下圖顯示僅將食物調查記錄複製到主要地址清單的對應。  
  
 ![說明迴圈路徑用法的對應。] (../core/media/correct-loop-path-map.gif "correct_loop_path_map")  
迴圈路徑對應  
  
## <a name="multiple-loop-paths"></a>多個迴圈路徑  
 將二或多個迴圈記錄包含的欄位連接到單一迴圈記錄包含的欄位時，會在對應中發生多個迴圈路徑。 下圖顯示將從兩個不同調查收集的地址組合到單一主要地址清單中的嘗試。  
  
 ![具有多個迴圈路徑對應](../core/media/multiple-loop-path-map.gif "multiple_loop_path_map")  
具有多個迴圈路徑的對應 (不正確)  
  
 此對應不會產生預期的結果。 當對應工具在編譯期間遇到多個迴圈路徑時，它會產生警告，並依預設選取第一個迴圈路徑。 若要將兩個不同的地址結合成單一主要地址清單中，使用**迴圈**運算質，如以下對應所示。  
  
 ![迴圈運算質用法的對應。] (../core/media/loopingfunctoid.gif "loopingfunctoid")  
迴圈運算值對應 (正確)  
  
 **迴圈**應該使用運算質，而不是在下列案例中的多個迴圈路徑：  
  
1.  當對應工具未在多個迴圈路徑的案例中產生所需的輸出時。  
  
2.  將輸入執行個體訊息中的多個重複結構組合成輸出執行個體訊息中的單一重複結構。  
  
3.  藉由將單一記錄對應至多個記錄，將一般結構描述轉換成階層式結構描述。 這是將一般結構描述轉換成 Microsoft Commerce Server 目錄的通用作業。  
  
## <a name="see-also"></a>另請參閱  
 [如何新增迴圈運算質至對應](../core/how-to-add-looping-functoids-to-a-map.md)   
 [迴圈運算質](../core/looping-functoid.md)