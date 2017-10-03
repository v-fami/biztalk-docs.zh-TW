---
title: "如何建立 XML 訊息的結構描述 |Microsoft 文件"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: a0270293-fe23-42bd-b090-e877d5e9ce0b
caps.latest.revision: "12"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 83a06aa7ca1ee4e37c29083ac38f5285565b7325
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/20/2017
---
# <a name="how-to-create-schemas-for-xml-messages"></a>如何建立 XML 訊息的結構描述
有數種方法可以建立 BizTalk 訊息結構描述。 本主題提供部分這些方法的逐步指示。  
  
### <a name="to-create-a-new-schema"></a>建立新結構描述  
  
1.  在**方案總管 中**，選取您要新增結構描述的 BizTalk 專案。  
  
2.  在 [專案] 功能表上，按一下 [加入新項目]。  
  
3.  在**加入新項目- \<* BizTalk ProjectName*> * * 對話方塊中，於**範本**區段中，按一下**結構描述**。  
  
4.  在**名稱**方塊、 輸入結構描述的名稱，然後按一下**新增**。  
  
5.  如有需要，請按 F4，開啟 [[!INCLUDE[btsVStudioNoVersion](../includes/btsvstudionoversion-md.md)] 屬性] 視窗。  
  
6.  在結構描述樹狀結構檢視中，選取**結構描述** 節點，然後在 屬性 視窗中，選取**目標命名空間**內容，然後輸入目標命名空間的名稱。 您在建立結構描述; 的初始階段中設定這個屬性很重要請避免使用預設**目標命名空間**屬性值。  
  
    > [!NOTE]
    >  某些專案成員檔案 (例如結構描述檔案) 名稱的選擇，可能會因為和 C# 保留字、.NET Framework 類型及命名空間名稱 (例如 System) 衝突，而在之後造成編譯錯誤。 結構描述的範例包括 schema.xsd、XmlContent 及 RootNodes。 這是因為**型別名稱**屬性預設為基底 （不含副檔名） 部分**Filename**屬性。 您可以藉由明確地變更的值解決這種類型的編譯錯誤**型別名稱**為不衝突的屬性。  
  
    > [!NOTE]
    >  您可能需要新增、刪除和修改結構描述中的記錄和欄位，及其關聯的屬性。 若要深入了解，請參閱[管理內結構描述節點](../core/managing-the-nodes-within-a-schema.md)。  
  
### <a name="to-generate-a-schema-from-a-non-xsd-source"></a>從非 XSD 來源產生結構描述  
  
1.  在**方案總管] 中**，以滑鼠右鍵按一下 BizTalk 專案，指向**新增**，然後按一下 [**新增產生的項目**。  
  
2.  在**新增產生的項目- \<* BizTalk ProjectName*> * * 對話方塊中，於**範本**區段中，按一下**產生結構描述**，然後按一下 **新增**。  
  
3.  在**產生結構描述**對話方塊中，於**文件類型**下拉式清單中，選取**XDR 結構描述**， **DTD 結構描述**，或**格式正確的 XML**。  
  
     如果您看到**DTD （未載入）**或**格式正確的 XML （未載入）**在下拉式清單中，選取適當的文件類型，並將引導您安裝的程序遺失的 DLL。 接著，請重複這些步驟。  
  
4.  在**產生結構描述**對話方塊中，按一下 **瀏覽**，找出您想要匯入，然後按一下 的檔案**開啟**。 您找到的檔案必須符合您在上一個步驟中選取的文件類型。  
  
     此時會從指定的檔案產生新的結構描述，此結構描述會使用與該檔案相同的名稱並含有副檔名 .xsd，並在 [BizTalk 編輯器] 中開啟。  
  
## <a name="see-also"></a>另請參閱  
 [管理專案中的結構描述](../core/managing-schemas-within-projects.md)