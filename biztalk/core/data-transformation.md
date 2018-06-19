---
title: 資料轉換 |Microsoft 文件
ms.custom: ''
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- maps, data translation
- data translation, about data translation
- data transformation, about data transformation
- maps, data transformation
- data transformation, maps
- data translation, maps
ms.assetid: a6aa5e9a-8d9c-478d-8f69-f9b16ed1a18c
caps.latest.revision: 10
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 0ee1cd9b7e825f210032f7caaaa292496cfa44c0
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/20/2017
ms.locfileid: "22238646"
---
# <a name="data-transformation"></a>資料轉換
對應資料會依賴資料轉換。  
  
 資料轉換為目的結構描述中建立記錄和欄位的來源結構描述 （通常是不同的） 的記錄與欄位之間的對應關係的程序。 對應訂單和發票上的送貨地址和帳單地址資訊，即是資料轉換的例子。 這是最基本的對應類型。 資料轉換也可應用於下列作業：  
  
-   計算迴圈記錄中資料的平均值，然後將結果傳送至目的結構描述的單一欄位。  
  
-   將字元資料轉換為它的 ASCII 格式。  
  
-   在一或多項紀錄中新增或刪減資料，然後將結果放到目的結構描述中的單一欄位。  
  
 如果您要將資料從某種格式轉譯成另一種格式，您要使用管線。 這對於解決企業應用程式整合的問題相當有幫助，採用的作法是將特定類型的訊息轉譯為現有系統所要求的其他格式，但是這無法使用對應來完成。  
  
## <a name="see-also"></a>另請參閱  
 [對應](../core/maps.md)   
 [使用 BizTalk 對應工具建立對應](../core/creating-maps-using-biztalk-mapper.md)