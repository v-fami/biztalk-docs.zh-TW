---
title: 如何建立屬性結構描述 |Microsoft 文件
ms.custom: ''
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 24086dea-62b8-4ef6-8af8-eb4ab7c3c018
caps.latest.revision: 6
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: ee97f4cb3065fdb201ec19f88a79e7899f03ac49
ms.sourcegitcommit: 5abd0ed3f9e4858ffaaec5481bfa8878595e95f7
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/28/2017
ms.locfileid: "25970476"
---
# <a name="how-to-create-property-schemas"></a>如何建立屬性結構描述
如果您選擇要升級為屬性欄位的欄位，您必須先定義屬性結構描述。 此屬性結構描述將指定未結構化的欄位集合，您可以將欄位從與屬性結構描述相關之結構描述所定義的執行個體訊息升級至其中。  
  
> [!IMPORTANT]
>  請勿複製和編輯現有的屬性結構描述，來建立新的結構描述。 屬性結構描述會包含結構描述特定的內部資料。  
  
> [!NOTE]
>  您不需要建立屬性結構描述以升級辨別欄位。  
  
### <a name="to-create-a-property-schema"></a>建立屬性結構描述  
  
1.  在**方案總管] 中**，以滑鼠右鍵按一下 BizTalk 專案，指向**新增**，然後按一下 [**新項目**。  
  
2.  在**加入新項目**對話方塊中，於**範本**區段中，按一下**屬性結構描述**。  
  
3.  在**名稱**方塊、 輸入結構描述的名稱，然後按一下**新增**。  
  
     開啟新的屬性結構描述，且它已包含**欄位項目**名為 Property1 的節點。  
  
4.  在結構描述樹狀目錄中，使用滑鼠右鍵按一下**欄位項目**] 節點，按一下 [**重新命名**中結構描述中，輸入第一個屬性的描述性名稱，然後按 ENTER 鍵。  
  
5.  設定**資料型別**和其他相關的屬性，適當地為**欄位項目**屬性 視窗中的節點。  
  
6.  如果您想要插入**欄位項目**節點的其他屬性，以滑鼠右鍵按一下\<結構描述\>節點中，按一下 **插入結構描述節點**，然後按一下  **子欄位項目**，然後重複步驟 4 和 5。 若要建立一組必要的視需要重複**欄位項目**您打算從執行個體訊息升級值的節點。  
  
## <a name="see-also"></a>請參閱  
 [管理專案中的結構描述](../core/managing-schemas-within-projects.md)