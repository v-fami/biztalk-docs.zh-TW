---
title: 建立和部署 A4SWIFT 管線 |Microsoft Docs
ms.custom: ''
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- creating, pipelines
- deploying, pipelines
- pipelines, deploying
- pipelines, creating
ms.assetid: 2a614510-7e15-4e88-9012-fc019d3aefee
caps.latest.revision: 4
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: d337b97dfb1973ef10c113ae0a206a51dcd63b1a
ms.sourcegitcommit: 266308ec5c6a9d8d80ff298ee6051b4843c5d626
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/27/2018
ms.locfileid: "37002447"
---
# <a name="creating-and-deploying-a4swift-pipelines"></a>建立和部署 A4SWIFT 管線
下圖所示，請執行下列步驟來建立和部署訊息修復和新送出，SWIFT 管線。  

 ![](../../adapters-and-accelerators/accelerator-swift/media/a4swift-pipeline-configuration.gif "A4SWIFT_Pipeline_Configuration")  

 **摘要**  

 將下列的結構描述的部署：  

-   自訂接收管線，其中含有 SWIFT 解譯器。 將 BRE 驗證 」 和 「 XML 驗證的屬性設定為 True，而且 SWIFT 標頭結構描述屬性，為 （無）。  

-   自訂傳送管線與 SWIFT 組合器  

### <a name="to-create-a-pipeline-project"></a>若要建立管線專案  

1. 在 Visual Studio 中，按一下**檔案**，指向**新增**，然後按一下**專案**。  

2. 在 [新增專案] 對話方塊中，在**專案類型**窗格中，選取**BizTalk 專案**資料夾。  

3. 在 **範本**窗格中，選取**空白 BizTalk Server 專案**。  

4. 在 **名稱**方塊中，輸入您想針對專案名稱的名稱。  

5. 在 **解決方案**方塊中，選取**加入至方案**。 在 **位置**方塊中，輸入您在建立結構描述專案的位置[部署 A4SWIFT 結構描述](../../adapters-and-accelerators/accelerator-swift/deploying-a4swift-schemas.md)。  

6. 按一下 **確定**開啟新的專案。  
   [!INCLUDE[btsVStudioNoVersion](../../includes/btsvstudionoversion-md.md)][!INCLUDE[btsDotNet](../../includes/btsdotnet-md.md)] 將新專案加入方案總管 中，並在指定的資料夾中建立的專案資料夾和檔案。  

7. 建立並指派至專案的強式的金鑰檔。 如需詳細資訊，請參閱 < 建立強式名稱的 SWIFT 專案 」 中[部署 A4SWIFT 結構描述](../../adapters-and-accelerators/accelerator-swift/deploying-a4swift-schemas.md)。  

### <a name="to-add-a-custom-receive-pipeline"></a>若要新增自訂接收管線  

1. 在 [方案總管] 中，以滑鼠右鍵按一下管線專案，指向**新增**，然後按一下**新項目**。  

2. 在 加入新項目 對話方塊中，按一下**管線檔案**類別 窗格，然後選取**接收管線**從 範本 窗格。  

3. 在 **名稱**方塊中，輸入管線的名稱。  

4. 按一下 **新增**BizTalk 管線設計師中開啟空白的管線。  

5. 在  [!INCLUDE[btsVStudioNoVersion](../../includes/btsvstudionoversion-md.md)]，按一下**檢視**，然後**工具箱**。  

6. 從**BizTalk 管線元件 [工具箱]**，拖曳**SWIFT 解譯器**來**放在此處**下面的方塊**解譯**階段成形**BizTalk 管線設計師**。 離開**SWIFT 解譯器**中，選取**BizTalk 管線設計師**。  

7. 中**屬性**，確認**BRE 驗證**並**XML 驗證**屬性設定為**True**。  

   > [!NOTE]
   >  SWIFT 標頭結構描述屬性應該設定為 **（無）**。  

8. 在  [!INCLUDE[btsVStudioNoVersion](../../includes/btsvstudionoversion-md.md)]，按一下**檔案**，然後**全部儲存**。  

### <a name="to-add-a-custom-send-pipeline"></a>若要新增自訂傳送管線  

1. 在 [方案總管] 中，以滑鼠右鍵按一下**SWIFTPipelines**專案，指向**新增**，然後按一下**新項目**。  

2. 在 [加入新項目] 對話方塊中，確認**管線檔案**已選取在 [分類] 窗格中，然後選取**傳送管線**從 [範本] 窗格。  

3. 在 **名稱**方塊中，輸入管線的名稱。  

4. 按一下 **新增**BizTalk 管線設計師中開啟空白的管線。  

   > [!NOTE]
   >  BizTalk 管線設計師 」 中，會出現空的管線。 [!INCLUDE[btsVStudioNoVersion](../../includes/btsvstudionoversion-md.md)] 將方案總管 中的新管線 SWIFTPipelines 專案底下。  

5. 在  [!INCLUDE[btsVStudioNoVersion](../../includes/btsvstudionoversion-md.md)]，按一下**檢視**，然後**工具箱**。  

6. 在**BizTalk 管線元件 [工具箱]**，拖曳**SWIFT 組合器**來**放在此處**下面的方塊**組合**階段中的圖形**BizTalk 管線設計師**。  

7. 在  [!INCLUDE[btsVStudioNoVersion](../../includes/btsvstudionoversion-md.md)]，按一下**檔案**，然後**全部儲存**。  

8. 以滑鼠右鍵按一下管線專案，然後按一下**建置**。  

   > [!NOTE]
   >  在編譯過程中，您應該不會看到任何失敗。 如果這麼做，請檢查錯誤的來源更正它，然後重新建置專案。 不過，您可能會看到警告。 您可以修正警告的狀況。 如需詳細資訊，請參閱 「 建置管線專案可能會導致警告 」，在[其他已知問題](http://msdn.microsoft.com/library/bc94c781-2a56-4f80-8ecb-e654de2f6ed6)。  

9. 以滑鼠右鍵按一下管線專案，然後按一下**部署**。
