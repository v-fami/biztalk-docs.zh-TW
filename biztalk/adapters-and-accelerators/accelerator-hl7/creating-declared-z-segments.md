---
title: "建立宣告的 Z 區段 |Microsoft 文件"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- Z objects, creating segments
- segments, creating Z segments [Z objects]
- Z segments, creating
- creating, Z segments [Z objects]
ms.assetid: afd1b7b7-089e-4c6a-a063-e708431bb888
caps.latest.revision: "6"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: dae9148547f527d29238b6080cd499be8da7b7e6
ms.sourcegitcommit: 3fd1c85d9dc2ce7b77da75a5c2087cc48cfcbe50
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 01/17/2018
---
# <a name="creating-declared-z-segments"></a>建立宣告的 Z 區段
您可以建立宣告的 Z 區段 （不同於未宣告 Z 區段，其必須是多個合作對象的訊息，下列的內文部分的最後一個部分） 結構任何的描述層級。  
  
### <a name="to-create-a-z-segment-in-biztalk-editor"></a>在 [BizTalk 編輯器] 中建立 Z 區段  
  
1.  在 方案總管的 Visual Studio 中，以滑鼠右鍵按一下您想要新增 Z 區段，然後按一下 結構的描述**開啟**。  
  
2.  在 BizTalk 編輯器 中，以滑鼠右鍵按一下結構描述名稱的節點，指向**插入結構描述節點**，然後按一下 **子記錄**。  
  
3.  名稱的名稱開頭為三個英數字元數字，以大寫，為正在"Z"的第一個數字的記錄。 （Z 區段標記必須包含三個字元）。插入底線 (_)，然後再加入 區段的簡短描述。 描述應該有一個或一系列的字，不含空格，每個字大寫的第一個字母。 最後一個字應該是 「 區段 」。 （範例為"ZPP_PatientPreferencesSegment。）按 **Enter**鍵。  
  
4.  在 屬性 窗格中，輸入 Z 區段中，您想要的屬性包括**資料結構型別**（結構描述名稱或具有 xsd: anytype） **Max Occurs**，和**Min Occurs**。  
  
    > [!NOTE]
    >  如果您輸入的資料結構類型的記錄，您無法加入子欄位項目。  
  
5.  在 BizTalk 編輯器 中，以滑鼠右鍵按一下 Z 區段的名稱，指向**插入結構描述節點**，然後按一下 **子欄位項目**。  
  
6.  輸入欄位，名稱開頭的區段名稱，後面接著句號和欄位中，後面接著底線，然後的簡短描述的欄位數目的前三個位數的名稱。 描述應該有一個或一系列的字，不含空格，每個字大寫的第一個字母。 按 **Enter**鍵。  
  
7.  在 屬性 窗格中，輸入 Z 區段中，您想要的屬性包括**資料型別**， **Nillable**，**固定**， **Max Occurs**，和**Min Occurs**。  
  
8.  若要建立欄位與元件，建立記錄、 欄位，然後建立該記錄每個元件的子項目。 若要建立欄位時的子元件，建立欄位和元件的記錄，並且為子系的子元件項目。 請注意，子元件不能是複合資料類型。 例如，對於名為 ZPP_PatientPreferencesSegment 區段，您可以建立 ZPP.1_Dietary 欄位和 PD.1 的過敏情況元件與 PD.1.1_FoodGroupAllergy 子元件。 PD.1.1_FoodGroupAllergy 子元件必須是簡單的資料類型。  
  
## <a name="see-also"></a>另請參閱  
 [擴充 HL7 2.X Z 物件結構描述](../../adapters-and-accelerators/accelerator-hl7/extending-hl7-2-x-schemas-with-z-objects.md)   
 [在結構描述中建立自訂資料型別](../../adapters-and-accelerators/accelerator-hl7/creating-custom-data-types-in-schemas.md)   
 [在結構描述中建立自訂的資料表](../../adapters-and-accelerators/accelerator-hl7/creating-custom-tables-in-schemas.md)   
 [擴充列舉型別](../../adapters-and-accelerators/accelerator-hl7/extending-enumerations.md)   
 [處理未宣告的 Z 區段](../../adapters-and-accelerators/accelerator-hl7/handling-undeclared-z-segments.md)