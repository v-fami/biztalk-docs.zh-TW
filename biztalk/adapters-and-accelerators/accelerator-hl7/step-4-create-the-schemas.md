---
title: 步驟 4： 建立結構描述 |Microsoft Docs
ms.custom: ''
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- message enrichment tutorial, schemas
- creating, schemas
- schemas, creating
ms.assetid: 81b1f538-9743-433a-87f9-a423dcb868c8
caps.latest.revision: 6
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 914efbfe8632bb727724a5115f6423b9abb8f54f
ms.sourcegitcommit: 266308ec5c6a9d8d80ff298ee6051b4843c5d626
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/27/2018
ms.locfileid: "37000935"
---
# <a name="step-4-create-the-schemas"></a>步驟 4： 建立結構描述
在此步驟中，您會建立新的專案 (**BTAHL7 專案**)，其中包含此專案的成品： 結構描述、 對應和協調流程。 接著，您建立結構描述 (**Doorbell.xsd**) 內送的 XML 編碼訊息，然後選取現有的結構描述 (**ADT_A04_22_GLO_DEF.xsd**) HL7 編碼的外寄訊息。 您可以使用這些結構描述來定義您在協調流程內交換訊息的結構。  

### <a name="to-create-the-schemas"></a>若要建立結構描述  

1. 在 **[檔案]** 功能表上，指向 **[開新檔案]**，然後按一下 **[專案]**。  

2. 在 [新增專案] 對話方塊中，展開**BizTalk 專案**資料夾，然後再按一下**BTAHL7Projects**資料夾。  

3. 在 **範本**窗格中，按一下**空白 BTAHL7 專案**。  

4. 在 **名稱**欄位中，輸入**BTAHL7 專案**做為專案名稱。  

5. 在 **解決方案**欄位中，選取**加入至方案**。  

6. 在 **位置**欄位中，確認 **\<*磁碟機*\>: \Tutorial\BTAHL7V22Common**是路徑。  

7. 按一下 **確定**開啟新的專案。  

   > [!NOTE]
   >  [!INCLUDE[btsVStudioNoVersion](../../includes/btsvstudionoversion-md.md)] 將新的專案加入至方案總管 中。 它也會將專案資料夾，並建立中\<*磁碟機*\>: \Tutorial\\**BTAHL7V22Common**專案資料夾。  

8. 在 [方案總管] 中，以滑鼠右鍵按一下**BTAHL7 專案**專案，指向**新增**，然後按一下**新項目**。  

9. 在加入新項目-BTAHL7 專案對話方塊中，於**分類** 窗格中，按一下**結構描述檔案**，然後在**範本**窗格中，按一下**結構描述**.  

10. 在 **名稱**欄位中，輸入**Doorbell.xsd**命名結構描述。  

11. 按一下 **新增**在 「 BizTalk 編輯器 」 中開啟空白的結構描述。  

12. 在  **\<結構描述\>** 樹狀結構中，以滑鼠右鍵按一下**根**節點，然後再按一下**重新命名**。  

13. 型別**DoorbellRoot**作為新的名稱，然後按**Enter**。  

14. 以滑鼠右鍵按一下**DoorbellRoot**節點，指向**插入結構描述節點**，然後按一下**子欄位項目**加入 （每個欄位重複此步驟中的下列欄位項目）：  

    -   **FirstName**  

    -   **MiddleName**  

    -   **lastName**  

    -   **SSN**  

15. 在 [方案總管] 中，以滑鼠右鍵按一下**BTAHL7 專案**，指向**新增**，然後按一下**新項目**。  

16. 在加入新項目-BTAHL7 專案對話方塊中，於**分類** 窗格中，按一下**BTAHL7 結構描述**，然後按一下**新增**。  

17. 在 HL7 結構描述選取器 對話方塊中，在**Message 類別**方塊中，選取**V2.X**，然後在**結構描述詳細資料** 窗格中，執行下列動作：  


    |     使用      |                                     以進行此動作                                     |
    |-------------------|------------------------------------------------------------------------------------|
    |    **版本(Version)**    |    選取 HL7 訊息的版本號碼。 在本教學課程中，使用**2.2**。    |
    | **訊息類型**  |           選取 HL7 訊息的類型。 在本教學課程中，使用**ADT**。           |
    | **觸發程序事件** | 選取 HL7 訊息的觸發程序事件值。 在本教學課程中，使用**A04**。 |


18. 按一下 **完成**ADT_A04_22_GLO_DEF.xsd （註冊病人） 結構描述新增至您的專案。 關閉 [HL7 結構描述選取器] 對話方塊。  

19. 在 方案總管底下**BTAHL7 專案**，以滑鼠右鍵按一下**參考**，然後按一下 **加入參考**。  

20. 在 加入參考 對話方塊中上,**專案**索引標籤上，選取**BTAHL7V22Common**專案，按一下 **新增**，然後按一下**確定**。  

    > [!NOTE]
    >  這會加入至原始專案的參考，讓[!INCLUDE[btsVStudioNoVersion](../../includes/btsvstudionoversion-md.md)]正確辨識 HL7 結構描述。  

21. 在 方案總管底下**BTAHL7 專案**，以滑鼠右鍵按一下**參考**，然後按一下 **加入參考**。  

22. 在 [加入參考] 對話方塊中，按一下**瀏覽**] 索引標籤。在 [**查詢**方塊中，移至\<*磁碟機*\>: \Program Files\Microsoft BizTalk\<版本\>HL7\SDK\End 端對端教學課程中的快速鍵對應\Tutorial_BTAHL7Drop\Bin。 按一下  **Microsoft.Solutions.BTAHL7.HL7Schemas.dll**，按一下**新增**，然後按一下**確定**。  

    請繼續進行[步驟 5： 升級結構描述屬性](../../adapters-and-accelerators/accelerator-hl7/step-5-promote-schema-properties.md)。  

## <a name="see-also"></a>另請參閱  
 [訊息擴充教學課程](../../adapters-and-accelerators/accelerator-hl7/message-enrichment-tutorial.md)