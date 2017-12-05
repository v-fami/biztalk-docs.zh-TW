---
title: "擴充列舉 |Microsoft 文件"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- enumeration values
- 2.X schemas, enumeration values
ms.assetid: 043def35-b644-4502-a2e2-cc1a5fc0328a
caps.latest.revision: "6"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 2abb040d79f0c9312a8761289c0bf6252fef2f3a
ms.sourcegitcommit: 3fc338e52d5dbca2c3ea1685a2faafc7582fe23a
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/01/2017
---
# <a name="extending-enumerations"></a>擴充列舉型別
您可以將值加入至 HL7 訊息本文、 通知和訊息內文結構描述中建立可接受的許多欄位、 區段，以及資料類型值的列舉型別。 這項作業包括變更一組通用 HL7 版本，您使用資料表值結構描述檔中特定資料表中的值 ( **Tablevalues_\<***版本* **\>.xsd**結構描述檔案)。  
  
 您在列舉中加入訊息標頭結構描述的不同方式不同於其他結構描述，例如訊息內文結構描述。 訊息標頭結構描述中，您必須變更 MSH_25_GLO_DEF.xsd 檔案內的資料表。 其他結構描述中，您可以變更資料表值的結構描述檔案中的資料表 (tablevalues_\<版本\>.xsd)。  
  
### <a name="to-add-an-enumeration-value-to-the-table-values-common-schema-file"></a>若要加入的資料表值 common 結構描述檔案列舉值  
  
1.  您必須先判斷資料表，其中包含您想要加入至列舉。 在 Visual Studio 的方案總管，開啟包含您想要變更之項目的結構描述檔案。 在 BizTalk 總管 中，按一下您想要加入的值欄位項目。  
  
    > [!NOTE]
    >  當您變更資料表值 common 結構描述檔案中的列舉型別時，受影響的所有物件，參考該列舉型別。  
  
2.  在**屬性** 窗格中，記下中的資料表名稱**基底資料型別**欄位。  
  
    > [!NOTE]
    >  如果沒有任何資料表中列出**基底資料型別** 欄位中，和**Derived By**屬性未設定為**restricted**，欄位沒有與其相關聯的列舉.  
  
3.  在 方案總管 中，開啟**Tablevalues_\<***版本***\>.xsd**，然後按一下 **開啟**。  
  
    > [!NOTE]
    >  您必須為每個您想要變更 HL7 結構描述版本的個別執行此程序。  
  
4.  在 [BizTalk 編輯器] 中，瀏覽至您想要變更，然後再按一下該資料表節點的資料表。  
  
5.  在 屬性 視窗中**限制**區段中，按一下**列舉**，然後按一下省略符號 （...） 按鈕開啟 列舉編輯器。  
  
6.  在 列舉編輯器 中，將新的值加入至現有的值清單，然後按一下 **確定**。  
  
### <a name="to-add-an-enumeration-value-to-a-message-header-schema"></a>將列舉值新增至訊息標頭結構描述  
  
1.  在 方案總管開啟 MSH_25_GLO_DEF 結構描述，然後按一下 **開啟**。  
  
2.  以滑鼠右鍵按一下**MSH**節點，指向**插入結構描述節點**，然後按一下 **子欄位項目**。 [!INCLUDE[btsVStudioNoVersion](../../includes/btsvstudionoversion-md.md)]將欄位的節點加入 MSH，稱為**欄位**。 按一下**ENTER**。  
  
3.  在**屬性**視窗中，按一下 [**資料型別**] 節點，然後從下拉式清單中，選取您要新增的列舉值的資料表。  
  
4.  在**屬性**視窗，請在**限制**區段中，按一下**列舉**，然後按一下省略符號 （...） 按鈕開啟 列舉編輯器。  
  
5.  在 列舉編輯器 中，將新的值加入至現有的值清單，然後按一下 **確定**。  
  
     當您將值加入至列舉型別之任何節點，例如**欄位**節點中，新增全域使用該資料表的所有物件的值。 如此一來，您現在可以刪除**欄位**節點，然後此值仍然會出現資料表。 您可以驗證，捲動到資料表，右窗格 BizTalk 編輯器中，確認您所加入的值存在。  
  
6.  以滑鼠右鍵按一下**欄位**節點在 BizTalk 編輯器 中，按一下**刪除**，然後按一下 **是**。  
  
## <a name="see-also"></a>請參閱  
 [資料表值的通用結構描述](../../adapters-and-accelerators/accelerator-hl7/table-values-common-schemas.md)   
 [擴充 HL7 2.X Z 物件結構描述](../../adapters-and-accelerators/accelerator-hl7/extending-hl7-2-x-schemas-with-z-objects.md)   
 [建立宣告的 Z 區段](../../adapters-and-accelerators/accelerator-hl7/creating-declared-z-segments.md)   
 [在結構描述中建立自訂資料型別](../../adapters-and-accelerators/accelerator-hl7/creating-custom-data-types-in-schemas.md)   
 [在結構描述中建立自訂的資料表](../../adapters-and-accelerators/accelerator-hl7/creating-custom-tables-in-schemas.md)   
 [處理未宣告的 Z 區段](../../adapters-and-accelerators/accelerator-hl7/handling-undeclared-z-segments.md)