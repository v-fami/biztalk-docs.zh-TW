---
title: 擴充列舉 |Microsoft Docs
ms.custom: ''
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- enumeration values
- 2.X schemas, enumeration values
ms.assetid: 043def35-b644-4502-a2e2-cc1a5fc0328a
caps.latest.revision: 6
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: dc5b91513833b76ba7dc3697f9eee409bf9752bf
ms.sourcegitcommit: 266308ec5c6a9d8d80ff298ee6051b4843c5d626
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/27/2018
ms.locfileid: "36987847"
---
# <a name="extending-enumerations"></a>擴充列舉
您可以加入 HL7 訊息內文、 通知和訊息內文結構描述中建立可接受的許多欄位，區段和資料類型值的列舉值。 這包括變更一組常見 HL7 版本，您使用資料表值結構描述檔案中的特定資料表的值 ( **Tablevalues_\<**<em>版本</em> **\>.xsd**結構描述檔案)。  
  
 您加入至列舉的訊息標頭結構描述不同的方式不同於其他結構描述，例如訊息內文結構描述。 針對訊息標頭結構描述中，您必須變更 MSH_25_GLO_DEF.xsd 檔案內的資料表。 對於其他結構描述中，您可以變更資料表值的結構描述檔案中的資料表 (tablevalues_\<版本\>.xsd)。  
  
### <a name="to-add-an-enumeration-value-to-the-table-values-common-schema-file"></a>將列舉值新增至資料表值 common 結構描述檔案  
  
1. 您首先要決定資料表，其中包含您想要加入的列舉型別。 在 Visual Studio 的方案總管中開啟結構描述檔案，其中包含您想要變更的項目。 在 [BizTalk 總管] 中，按一下您想要新增的值欄位項目。  
  
   > [!NOTE]
   >  當您變更資料表值 common 結構描述檔案中的列舉型別時，會影響所有參考該列舉的物件。  
  
2. 在 **屬性**窗格中，記下的資料表中的名稱**Base Data Type**欄位。  
  
   > [!NOTE]
   >  中如果沒有列出任何資料表**基底資料型別** 欄位中，而**Derived By**屬性未設定為**Restricted**，沒有與其相關聯的列舉型別欄位.  
  
3. 在 [方案總管] 中，開啟**Tablevalues_\<**<em>版本</em>**\>.xsd**，然後按一下**開啟**。  
  
   > [!NOTE]
   >  您必須為每個您想要變更的 HL7 結構描述版本，個別執行此程序。  
  
4. 在 「 BizTalk 編輯器 」 中，瀏覽至您想要變更此項目，然後再按一下該資料表節點的資料表。  
  
5. 在 屬性 視窗中，在**限制**區段中，按一下**列舉**，然後按一下省略符號 （...） 按鈕，以開啟 列舉編輯器。  
  
6. 在 列舉編輯器 中，將新的值新增到現有的值清單，然後按一下 **確定**。  
  
### <a name="to-add-an-enumeration-value-to-a-message-header-schema"></a>將列舉值新增至訊息標頭結構描述  
  
1. 在 [方案總管] 中，開啟 MSH_25_GLO_DEF 結構描述，然後**開啟**。  
  
2. 以滑鼠右鍵按一下**MSH**節點，指向**插入結構描述節點**，然後按一下**子欄位項目**。 [!INCLUDE[btsVStudioNoVersion](../../includes/btsvstudionoversion-md.md)] 將 [欄位] 節點新增至 MSH，稱為**欄位**。 按一下  **ENTER**。  
  
3. 在 **屬性** 視窗中，按一下**資料型別** 節點，然後從下拉式清單中，選取您要加入的列舉值的資料表。  
  
4. 在**屬性**] 視窗，請在**限制**區段中，按一下**列舉型別**，然後按一下省略符號 （...） 按鈕，以開啟 [列舉編輯器。  
  
5. 在 列舉編輯器 中，將新的值新增到現有的值清單，然後按一下 **確定**。  
  
    當您將值加入對於任何節點中，列舉這類**欄位**節點中，新增使用該資料表的所有物件的全域值。 如此一來，您現在可以刪除**欄位** 節點和值仍然會出現資料表。 您可以驗證，請捲動在右窗格在 「 BizTalk 編輯器 」 的資料表，並驗證您所加入的值存在。  
  
6. 以滑鼠右鍵按一下**欄位**節點在 「 BizTalk 編輯器 」 中，按一下**刪除**，然後按一下**是**。  
  
## <a name="see-also"></a>另請參閱  
 [資料表值的通用結構描述](../../adapters-and-accelerators/accelerator-hl7/table-values-common-schemas.md)   
 [使用 Z 物件擴充 HL7 2.X 結構描述](../../adapters-and-accelerators/accelerator-hl7/extending-hl7-2-x-schemas-with-z-objects.md)   
 [建立宣告的 Z 區段](../../adapters-and-accelerators/accelerator-hl7/creating-declared-z-segments.md)   
 [結構描述中建立自訂資料類型](../../adapters-and-accelerators/accelerator-hl7/creating-custom-data-types-in-schemas.md)   
 [結構描述中建立自訂的資料表](../../adapters-and-accelerators/accelerator-hl7/creating-custom-tables-in-schemas.md)   
 [處理未宣告的 Z 區段](../../adapters-and-accelerators/accelerator-hl7/handling-undeclared-z-segments.md)