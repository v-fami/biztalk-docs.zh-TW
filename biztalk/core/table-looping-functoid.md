---
title: 表格迴圈運算質 |Microsoft 文件
ms.custom: ''
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- Table Looping functoids
- Table Looping functoids, about Table Looping functoids
ms.assetid: 6189a789-afe7-4e72-a778-2b0374db8f69
caps.latest.revision: 10
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 6c5e5f2967fb48bfe896c26246db1630266812f5
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/20/2017
ms.locfileid: "22278238"
---
# <a name="table-looping-functoid"></a>表格迴圈運算質
**表格迴圈**運算質可讓您建立用來建立輸出執行個體訊息的輸出值的資料表。 表格中的資料可包含連結和常數。 第一個輸入的參數**表格迴圈**運算質設定範圍，或多少次記錄迴圈。 第二個輸入參數**表格迴圈**運算質決定有多少資料行在資料表中，而其餘輸入不依特定順序定義資料表，可能的資料格的值。 如需有關使用這些屬性的詳細資訊，請參閱[Table-Driven 迴圈組態](../core/table-driven-looping-configuration.md)。 另請參閱[Table-Driven 迴圈範例](../core/table-driven-looping-example.md)。  
  
> [!NOTE]
>  **表格迴圈**運算質會重複它連接至迴圈記錄。 在每個重複項目中，它會在表格迴圈格線中為每一列迴圈一次，以產生多個輸出迴圈。  
  
## <a name="see-also"></a>另請參閱  
 [表格抽選程式運算質](../core/table-extractor-functoid.md)   
 [如何新增表格迴圈和表格擷取程式運算質至對應](../core/how-to-add-table-looping-and-table-extractor-functoids-to-a-map.md)   
 [進階運算質](../core/advanced-functoids.md)   
 [索引運算質](../core/index-functoid.md)   
 [反覆項目運算質](../core/iteration-functoid.md)   
 [迴圈運算質](../core/looping-functoid.md)   
 [記錄計數運算質](../core/record-count-functoid.md)