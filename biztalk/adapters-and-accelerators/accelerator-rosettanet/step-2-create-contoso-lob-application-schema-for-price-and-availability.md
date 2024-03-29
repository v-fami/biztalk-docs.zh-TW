---
title: 步驟 2： 在使用 「 BizTalk 編輯器 」 的價格與可用性專案建立 Contoso LOB 應用程式結構描述 |Microsoft Docs
ms.custom: ''
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- private process tutorial, creating LOB schemas
ms.assetid: 70e26dc9-4299-4d30-8f8b-5cc3469a2025
caps.latest.revision: 8
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: f899a6614ea5d5d28c555be1b39e72b5880fe3ae
ms.sourcegitcommit: 266308ec5c6a9d8d80ff298ee6051b4843c5d626
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/27/2018
ms.locfileid: "36999327"
---
# <a name="step-2-creating-the-contoso-lob-application-schemas-for-the-price-and-availability-project-using-biztalk-editor"></a>步驟 2： 建立 Contoso LOB 應用程式結構描述為價格與可用性專案使用 「 BizTalk 編輯器
在此步驟中，您將產生結構描述，用來向 Contoso ERP 系統查詢特定產品的價格與可用性。 您可以使用 BizTalk server 的 Microsoft® SQL 配接器，以產生此結構描述。  

### <a name="to-update-the-sql-stored-procedure-for-schema-generation"></a>更新 SQL 預存程序以準備產生結構描述  

1.  按一下 **開始**，指向**所有程式**，指向**Microsoft SQL Server 2008 R2**，然後按一下**SQL Server Management Studio**。  

2.  在 Microsoft SQL Server Management Studio 中，展開**資料庫**，展開**Contoso**，展開**可程式性**，然後展開**預存程序**.  

3.  以滑鼠右鍵按一下**dbo。SP_GetInventoryForProductID**，然後按一下**修改**。  

4.  在查詢視窗中，插入逗號和空格，然後輸入 "xmldata" 後面加上 "for xml auto"。 此程式碼行應如下所示：  

    ```  
    for xml auto, xmldata  
    ```  

5.  按一下  **Execute**預存程序中儲存的變更。  

    > [!NOTE]
    >  讓 Microsoft SQL Server Management Studio 保持開啟供下一個程序使用。  

### <a name="to-create-the-contoso-price-and-availability-schema"></a>若要建立 Contoso 價格與可用性結構描述  

1. 開啟中的 Contoso 解決方案[!INCLUDE[btsVStudioNoVersion](../../includes/btsvstudionoversion-md.md)]。  

2. 在 [方案總管] 中，以滑鼠右鍵按一下**ContosoPriceAndAvailability**專案，指向**新增**，然後按一下**新增產生的項目**。  

3. 在 [新增產生的項] 對話方塊中，使用**新增的配接器中繼資料**選取左窗格中，按一下**新增配接器中繼資料**在右窗格中，然後按一下**新增**。  

4. 在 [**新增配接器精靈**頁面上，選取**SQL**從清單中已註冊的配接器，然後再按一下**下一步]**。  

5. 在 **資料庫資訊**頁面上，按一下**設定**。  

6. 在 [資料連結屬性] 對話方塊中，在**選取或輸入伺服器名稱**方塊中，輸入**localhost**。 選取 **使用 Windows NT 整合式安全性**。 針對**選取的伺服器上的資料庫**，選取**Contoso**資料庫從資料庫清單。 按一下 [確定] 。  

7. 在 [**資料庫資訊**頁面上，按一下**下一步]**。  

8. 在 **結構描述資訊**頁面上，執行下列動作：  


   |                使用                 |              以進行此動作              |
   |-----------------------------------------|--------------------------------------|
   |          **目標命名空間**           | 型別**<http://Contoso.com/Price>**。 |
   |        **選取連接埠類型**         |        選取 **傳送埠**。         |
   | **要求文件根元素名稱**  |      型別**rootPriceRequest**。      |
   | **回應文件根元素名稱** |     型別**rootPriceResponse**。      |


9. 按 [下一步] 。  

10. 在 [**陳述式類型資訊**頁面上，選取**預存程序**，然後按一下**下一步]**。  

11. 在上**陳述式資訊**頁面上，如**\<選取預存程序\>**，選取**SP_GetInventoryForProductID**從下拉式清單中。 按一下 [ **Generate**，然後按一下**下一步]**。  

12. 在 **完成 SQL 傳輸結構描述產生精靈**頁面上，按一下**完成**結構描述匯入 ContosoPriceAndAvailability BizTalk 專案。  

13. 在 [方案總管] 中，以滑鼠右鍵按一下所產生的結構描述 (SQLService_Price.xsd)，請按一下**重新命名**，然後輸入**ContosoPriceAndAvailability.xsd**做為結構描述的新名稱。 按一下 **[輸入]**。  

14. 在 ContosoPriceAndAvailability 結構描述的 屬性 視窗中，設定**型別名稱**屬性設**ContosoPriceSchema**。  

15. 根據預設，[!INCLUDE[btsBizTalkServerNoVersion](../../includes/btsbiztalkservernoversion-md.md)]建立名為 BizTalk 協調流程**BizTalk Orchestration.odx**。 此協調流程，以滑鼠右鍵按一下，然後按一下**刪除**因為您不需要此協調流程。 在協調流程將會永久刪除，指出快顯視窗，按一下**確定**。  

16. 在 Microsoft SQL Server Management Studio 中，移除`xmldata`述詞，並從逗號`SP_GetInventoryForProductID`預存程序，您在上一個步驟中，新增，然後按一下**Execute**。  

## <a name="see-also"></a>另請參閱  
 [步驟 3：使用 BizTalk 對應工具為價格與可用性專案建立 Contoso LOB 應用程式對應](../../adapters-and-accelerators/accelerator-rosettanet/step-3-create-contoso-lob-application-map-for-price-and-availability-in-mapper.md)