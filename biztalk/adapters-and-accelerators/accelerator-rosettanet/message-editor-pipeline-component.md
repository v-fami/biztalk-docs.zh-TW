---
title: 訊息編輯器管線元件 |Microsoft 文件
ms.custom: ''
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- messages, Message Editor Pipeline Component
- Message Editor Pipeline Component
- messages, editing
- pipelines, Message Editor Pipeline Component
ms.assetid: f2b22dea-54e8-410b-868f-2978139f438b
caps.latest.revision: 11
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 7f7685fbf800ad69b20eda31e9b64cb75ec7c511
ms.sourcegitcommit: 436ebffd959a9c4bdaafd4da9a5843c59a018eb7
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/08/2018
ms.locfileid: "34855681"
---
# <a name="message-editor-pipeline-component"></a>訊息編輯器管線元件
此元件可讓您自動編輯傳送或接收管線中多部分訊息的任何部分。 您可將此元件新增至現有的管線中，設定取代做為一般處理的一部分。  
  
## <a name="building-the-message-editor-pipeline-component-into-an-existing-pipeline"></a>將訊息編輯器管線元件建置至現有的管線  
 如果要使用「訊息編輯器管線元件」，您必須將該元件新增至現有的管線。 如需詳細資訊，請參閱 「 建立管線的管線設計師 」 在 BizTalk Server 說明中。  
  
#### <a name="to-add-the-message-editor-pipeline-component-to-an-existing-pipeline"></a>將訊息編輯器管線元件新增至現有的管線  
  
1.  啟動 Visual Studio。  
  
2.  在**檔案**功能表上，指向**開啟**，然後按一下 **專案**。  
  
3.  移至 C:\Program Files (x86) \Microsoft BizTalk\<版本\>Accelerator for RosettaNet\SDK\Message Editor Pipeline Component，選取**MessageEditor.csproj**，然後按一下 **開啟**.  
  
4.  啟動 Visual Studio 命令提示字元。  
  
5.  在命令提示字元中，移至 C:\Program Files (x86) \Microsoft BizTalk\<版本\>Accelerator for RosettaNet\SDK\Message Editor Pipeline Component\obj\debug。  
  
6.  在命令提示字元中，輸入**sn-k MessageEditor.snk** ，建立金鑰，然後按 ENTER。  
  
7.  在[!INCLUDE[btsVStudioNoVersion](../../includes/btsvstudionoversion-md.md)]，在 [方案總管] 中，以滑鼠右鍵按一下**MessageEditor**，然後按一下 **屬性**。  
  
8.  在**MessageEditor 屬性**頁面上，按一下**簽署**索引標籤，然後再按一下**簽署組件**核取方塊。  
  
9. 在**選擇強式名稱金鑰檔**下拉式清單中，瀏覽至 C:\Program Files (x86) \Microsoft BizTalk\<版本\>Accelerator for RosettaNet\ SDK\Message Editor Pipeline Component\obj\debug，然後選取**MessageEditor.snk** ，然後按一下 **開啟**。  
  
10. 在 方案總管 中，以滑鼠右鍵按一下**MessageEditor**，然後按一下 **建置**。 在 [輸出] 窗格中，驗證組建是否成功。  
  
11. 按一下**啟動**，指向 **所有程式**，指向 **附屬應用程式**，然後按一下**Windows 檔案總管**。  
  
12. 在[!INCLUDE[btsWinNoVersion](../../includes/btswinnoversion-md.md)]總管] 中，移至 C:\Program Files\Microsoft BizTalk 2013 Accelerator for RosettaNet\SDK\Message Editor Pipeline Component\obj\debug，以滑鼠右鍵按一下**Microsoft.Solutions.BTARN.SDK.MessageEditor.dll**，然後按一下 [**複製**。  
  
13. 移至 C:\Program Files\Microsoft BizTalk Server 2013\Pipeline 元件，以滑鼠右鍵按一下**管線元件**，然後按一下 **貼上**。  
  
14. 在[!INCLUDE[btsVStudioNoVersion](../../includes/btsvstudionoversion-md.md)]上**檔案**功能表上，指向**開啟**，然後按一下 **專案**。  
  
15. 開啟包含您想新增編輯器的管線。  
  
16. 在 [方案總管] 中，按兩下管線名稱，在「管線設計師」中開啟管線。  
  
17. 在 [BizTalk 管線元件] 窗格的 [工具箱] 窗格中，按一下滑鼠右鍵，然後按一下**新增/移除項目**。  
  
18. 在**自訂工具箱**對話方塊**BizTalk 管線元件**索引標籤上，選取**BTARN 訊息編輯器元件**，然後按一下 **確定**.  
  
19. 在 [工具箱] 窗格的 [BizTalk 管線元件] 窗格中，按住**BTARN 訊息編輯器元件**，然後將元件拖曳至您要在管線中的位置。  
  
20. 在 [工具箱] 窗格的 [BizTalk 管線元件] 窗格中，按住**BTARN 訊息編輯器元件**，然後將元件拖曳至您要在管線中的位置。  
  
    > [!NOTE]
    >  建議您在接收管線元件的「解譯」階段或傳送管線元件的「預先組合」階段之後再新增「訊息編輯器管線元件」。  
  
21. 在[!INCLUDE[btsVStudioNoVersion](../../includes/btsvstudionoversion-md.md)]，在管線設計師中，選取**BTARN 訊息編輯器元件**圖形。  
  
22. 在 屬性 窗格的 與相關聯的文字方塊中**XPath 查詢**，輸入您要變更值的 XPath 項目名稱。  
  
23. 在相關聯的文字方塊中**XPath 值**，輸入您要設定 XPath 元素的值。  
  
24. 在 [方案總管] 中，以滑鼠右鍵按一下專案名稱，然後**建置**。 驗證組建是否成功。  
  
25. 在 [方案總管] 中，以滑鼠右鍵按一下專案名稱，然後**部署**。 驗證部署是否成功。  
  
## <a name="example"></a>範例  
 若要變更 0C1 PIP 結構描述中的 `ProprietaryDocumentIdentifier` 項目值，請將下列程式碼區段中顯示的「XPath 查詢」加入至「訊息編輯器管線元件」的 XPath Query 屬性。  
  
```  
/*[local-name()='Pip0C1AsynchronousTestNotification' and namespace-uri()='http://schemas.microsoft.com/biztalk/btarn/2004/0C1_MS_R01_02_AsynchronousTestNotification.dtd']/*[local-name()='thisDocumentIdentifier' and namespace-uri()='http://schemas.microsoft.com/biztalk/btarn/2004/0C1_MS_R01_02_AsynchronousTestNotification.dtd']/*[local-name()='ProprietaryDocumentIdentifier' and namespace-uri()='http://schemas.microsoft.com/biztalk/btarn/2004/0C1_MS_R01_02_AsynchronousTestNotification.dtd']  
```  
  
 若要取得完整的 XPath 查詢，請在 BizTalk 編輯器中開啟結構描述，然後從 `Instance XPath` 屬性 ([屬性] 視窗底下) 複製 Xpath。 您提供的 XPath 查詢中應該具備所有的命名空間參考。  
  
## <a name="see-also"></a>另請參閱  
 [公用程式](../../adapters-and-accelerators/accelerator-rosettanet/utilities1.md)
