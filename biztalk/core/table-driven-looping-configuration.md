---
title: "表格驅動迴圈組態 |Microsoft 文件"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- Table Looping functoids
- Table Extractor functoids, configuring
- Table Extractor functoids
- Table Extractor functoids, adding to grid
- Table Looping functoids, about Table Looping functoids
- Table Looping functoids, configuring
- Table Extractor functoids, about Table Extractor functoids
- Table Looping functoids, adding to map
ms.assetid: ecc24d9b-ebc0-4559-9746-58e3b00c02ab
caps.latest.revision: "8"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 2563c7f26d2beb0eba33173507989cc85aaabda1
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/20/2017
---
# <a name="table-driven-looping-configuration"></a>表格驅動迴圈組態
依照下列步驟設定對應中的表格驅動迴圈：  
  
-   **新增表格迴圈運算質至對應。** 您只需要一個**表格迴圈**運算質，每個表格驅動迴圈的執行個體。 例如，如果您使用表格驅動迴圈來衍生 BillTo 和 ShipTo 資訊，您只需要一個**表格迴圈**對應中的運算質。 不過，如果您使用表格驅動迴圈來衍生 BillTo 和 ShipTo 資訊以及 StoreName 和 StoreAddress 資訊，您可能需要兩個**表格迴圈**對應中的運算質。  
  
-   **顯示的格線頁中加入一個詳細的表格抽選程式運算質。** 加入做為許多**表格抽選程式**做為您的運算質需要每個**表格迴圈**運算質。 數目**表格抽選程式**運算質的目的結構描述中的欄位數目而定。 例如，如果您只需要**AddressCode**在您來源結構描述和公司名稱、 地址、 縣 （市）、 狀態、 郵遞區號和 AttentionName 目的地結構描述中的，您需要新增 6 個**表格抽選程式**若要顯示的格線頁的運算質。  
  
-   **以適當輸入設定表格迴圈運算質。** 首先，連結**表格迴圈**運算質到輸入執行個體記錄或項目。 並將它連結到輸出執行個體訊息中的結構。 接下來，使用設定輸入**設定\<運算質 > 運算質** 對話方塊。 如需如何設定這個屬性的詳細資訊，請參閱[編輯運算質屬性和輸入參數](../core/editing-functoid-properties-and-input-parameters.md)。 您輸入的輸入清單必須是完整且完整，因為這是您用來設定資料**資料表運算質方格**屬性。 這些輸入必須定義如下：  
  
    -   **第一個輸入。** 第一個輸入參數連接到輸入執行個體訊息記錄或欄位。 **表格迴圈**運算質都重複一次的記錄或欄位的每個執行個體。  
  
        > [!NOTE]
        >  這是必要的輸入。  
  
    -   **第二個輸入。** 第二個輸入參數定義迴圈格線中的資料行數目。 此格線最多可包含 228 個資料行。  
  
        > [!NOTE]
        >  這是必要的輸入。  
  
    -   **其餘輸入。** 其餘的輸入**表格迴圈**運算質所組成的所有可能的值，可能會出現在清單**資料表運算質方格**。  
  
        > [!NOTE]
        >  標籤連結非常有用。 標籤、 連結會出現在**資料表運算質方格**為完整指定路徑。  
  
         如需如何設定輸入的逐步指示**表格迴圈**運算質，請參閱[如何新增表格迴圈和表格擷取程式運算質至對應](../core/how-to-add-table-looping-and-table-extractor-functoids-to-a-map.md)。 請特別參閱步驟 3 到 8。  
  
-   **設定表格迴圈運算質的運算質在資料表方格屬性。** 使用**資料表運算質方格**屬性可開啟**設定表格迴圈運算質**對話方塊中，您可以在其中設定迴圈格線中的資料格。  
  
     如需有關如何設定迴圈格線的逐步指示，請參閱[如何新增表格迴圈和表格擷取程式運算質至對應](../core/how-to-add-table-looping-and-table-extractor-functoids-to-a-map.md)。 請特別參閱步驟 9 和 10。  
  
-   **設定表格抽選程式運算質。** 使用**輸入參數**屬性可設定**表格抽選程式**運算質的輸入，如下所示：  
  
    -   **第一個輸入。** 第一個輸入的參數**表格抽選程式**運算質是**表格迴圈**運算質。  
  
    -   **第二個輸入。** 第二個輸入參數指定要擷取資料的資料列中的資料行。  
  
     如需如何設定逐步指示**表格抽選程式**與相關聯的運算質**表格迴圈**運算質，請參閱[如何新增表格迴圈和表格擷取程式運算質至對應](../core/how-to-add-table-looping-and-table-extractor-functoids-to-a-map.md)。 特別是，請參閱步驟 11 至 16。  
  
## <a name="see-also"></a>另請參閱  
 [表格迴圈運算質](../core/table-looping-functoid.md)   
 [表格抽選程式運算質](../core/table-extractor-functoid.md)   
 [表格驅動迴圈範例](../core/table-driven-looping-example.md)   
 [如何新增表格迴圈和表格擷取程式運算質至對應](../core/how-to-add-table-looping-and-table-extractor-functoids-to-a-map.md)   
 [進階運算質](../core/advanced-functoids.md)   
 [索引運算質](../core/index-functoid.md)   
 [反覆項目運算質](../core/iteration-functoid.md)   
 [迴圈運算質](../core/looping-functoid.md)   
 [記錄計數運算質](../core/record-count-functoid.md)