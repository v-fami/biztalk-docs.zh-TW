---
title: "表格迴圈和表格擷取程式運算質 |Microsoft 文件"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 2907aada-f11a-485c-85c8-03092803ccf7
caps.latest.revision: "8"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 02d4433255ac00d51c88b45bd1a2b5205bd1c735
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/20/2017
---
# <a name="table-looping-and-table-extractor-functoids"></a>表格迴圈和表格擷取程式運算質

## <a name="overview"></a>概觀
在對應中，輸入執行個體訊息中的每個結構通常在輸出執行個體訊息中有一個結構。 然而，有時候您也會需要建立輸入執行個體結構，以便產生多重輸出執行個體結構。 您可以使用表格驅動迴圈來建立可產生這類多重結構的對應。  
  
 表格驅動迴圈使用**表格迴圈**運算質和**表格抽選程式**運算質。 **表格迴圈**運算質有您所設定的內部資料表。 每個輸入記錄或欄位，**表格迴圈**運算質會輸出一次一個資料表的資料列。 例如，如果有十筆記錄，在輸入執行個體訊息和內部資料表中的兩個資料列**表格迴圈**，運算質最後總共 20 個資料列，每十筆記錄輸出。 **表格抽選程式**運算質從一個資料列擷取所需的項目，並將它傳遞到輸出執行個體訊息。  
  
 如需詳細資訊，請參閱**表格迴圈運算質參考**和**表格抽選程式運算質參考** [!INCLUDE[ui-guidance-developers-reference](../includes/ui-guidance-developers-reference.md)]。
  
## <a name="next-steps"></a>後續的步驟
  
-   [表格迴圈運算質](../core/table-looping-functoid.md)  
  
-   [表格抽選程式運算質](../core/table-extractor-functoid.md)  
  
-   [表格驅動迴圈組態](../core/table-driven-looping-configuration.md)  
  
-   [表格驅動迴圈範例](../core/table-driven-looping-example.md)