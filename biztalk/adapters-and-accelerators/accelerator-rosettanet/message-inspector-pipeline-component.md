---
title: "訊息偵測器管線元件 |Microsoft 文件"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- creating, pipelines
- pipelines, custom pipelines
- pipelines, Message Inspector Pipeline Component
- Message Inspector Pipeline Component
- pipelines, creating
ms.assetid: d9c00718-c8cd-4289-8f58-e4edc61b9a05
caps.latest.revision: "12"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: fc9e1a520153220bcc86d844ca94203ff2b78548
ms.sourcegitcommit: 3fc338e52d5dbca2c3ea1685a2faafc7582fe23a
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/01/2017
---
# <a name="message-inspector-pipeline-component"></a>訊息偵測器管線元件
此管線元件可讓您檢查多部分訊息的所有部分以及訊息內容，以判斷訊息是否有問題。 您可使用此元件進行疑難排解。  
  
 管線元件會將 XML 檔案放到您所指定的目錄中。 這些檔案中的每個檔案都包含 RNIFv2.0 訊息之四個部分 (前序標頭、傳遞標頭、服務標頭和服務內容) 或 RNIFv1.1 訊息之三個部分 (前序標頭、服務標頭和服務內容) 的其中一個部分。 另一個 XML 檔案則包含訊息內容。  
  
 您可將此元件建置到自訂管線，並將它附加到傳送埠。 您可在傳送埠中建立篩選器，訂閱您想監視的訊息。 除了 [!INCLUDE[btsCoName](../../includes/btsconame-md.md)]® [!INCLUDE[BTARN_CurrentVersion_FirstRef](../../includes/btarn-currentversion-firstref-md.md)] 已經執行的標準程序之外，也會進行這項疑難排解。  
  
## <a name="building-a-custom-pipeline-using-the-message-inspector-pipeline-component"></a>使用訊息偵測器管線元件建置自訂管線  
 如果要使用「訊息偵測器管線元件」，您必須建置和部署包含該元件的自訂管線。 如需詳細資訊，請參閱 「 建立管線的管線設計師 」 在 BizTalk Server 說明中。  
  
#### <a name="to-deploy-the-message-inspector-pipeline-component"></a>部署訊息偵測器管線元件  
  
1.  啟動 Visual Studio。  
  
2.  在**檔案**功能表上，指向**開啟**，然後按一下 **專案**。  
  
3.  移至 C:\Program Files\Microsoft BizTalk 2013 Accelerator for RosettaNet\SDK\Message Inspector Pipeline Component，選取**MessageInspector.csproj**，然後按一下 **開啟**。  
  
4.  開啟 Visual Studio 命令提示字元。  
  
5.  在命令提示字元中，移至 C:\Program Files\Microsoft BizTalk 2013 Accelerator for RosettaNet\SDK\Message Inspector Pipeline Component\obj\debug。  
  
6.  在命令提示字元中，輸入**"sn-k MessageInspector.snk"** ，建立金鑰，然後按 ENTER。  
  
7.  在[!INCLUDE[btsVStudioNoVersion](../../includes/btsvstudionoversion-md.md)]，在 [方案總管] 中，以滑鼠右鍵按一下**MessageInspector**，然後按一下 **屬性**。  
  
8.  在**MessageInspector 屬性**頁面上，按一下**簽署**索引標籤，然後再按一下**簽署組件**核取方塊。  
  
9. 在**選擇強式名稱金鑰檔**下拉式清單中，瀏覽至 C:\Program Files\Microsoft BizTalk 2013 Accelerator for RosettaNet\SDK\Message Inspector Pipeline Component\obj\debug 並選取**MessageInspector.snk** ，然後按一下 **開啟**。  
  
10. 在 方案總管 中，以滑鼠右鍵按一下**MessageInspector**，然後按一下 **建置**。 在 [輸出] 窗格中，驗證組建是否成功。  
  
11. 按一下**啟動**，指向 **所有程式**，指向 **附屬應用程式**，然後按一下**Windows 檔案總管**。  
  
12. 在[!INCLUDE[btsWinNoVersion](../../includes/btswinnoversion-md.md)]總管] 中，移至 C:\Program Files\Microsoft BizTalk 2013 Accelerator for RosettaNet\SDK\Message Inspector Pipeline Component\obj\debug，以滑鼠右鍵按一下**Microsoft.Solutions.BTARN.SDK.MessageInspector.dll**，然後按一下 [**複製**。  
  
13. 移至 C:\Program Files\Microsoft BizTalk 2013 Accelerator for RosettaNet\Pipeline 元件，以滑鼠右鍵按一下**管線元件**，然後按一下 **貼上**。  
  
14. 在[!INCLUDE[btsVStudioNoVersion](../../includes/btsvstudionoversion-md.md)]上**檔案**功能表上，指向**新增**，然後按一下 **專案**。  
  
15. 在**新專案**對話方塊中的，在範本窗格中，選取**空白 BizTalk Server 專案**，請在**名稱**方塊中，輸入專案的名稱。 在**位置**方塊中，移至您想要儲存專案的資料夾，然後按一下**確定**。  
  
16. 在 方案總管 中，以滑鼠右鍵按一下專案名稱，指向**新增**，然後按一下 **加入新項目**。  
  
17. 在**加入新項目**對話方塊中，選取**傳送管線**，請在**名稱**方塊中，輸入自訂管線檔案的名稱，然後按一下**開啟**.  
  
    > [!NOTE]
    >  只將「訊息偵測器管線元件」新增至傳送埠，而不要新增至接收埠。  
  
18. [工具箱] 窗格的 [BizTalk 管線元件] 窗格中按一下滑鼠右鍵，然後按一下**新增/移除項目**。  
  
19. 在**自訂工具箱**對話方塊**BizTalk 管線元件**索引標籤上，選取**BTARN 訊息偵測器元件**，然後按一下 **確定**.  
  
20. 在 [工具箱] 窗格的 [BizTalk 管線元件] 窗格中，按住**BTARN 訊息偵測器元件**，然後將元件拖曳上**放置到此處 ！** 方塊。  
  
21. 在[!INCLUDE[btsVStudioNoVersion](../../includes/btsvstudionoversion-md.md)]，在 [方案總管] 中，以滑鼠右鍵按一下管線專案的名稱，然後按一下**屬性**。  
  
22. 在**屬性頁**對話方塊中，按一下 **通用屬性**，然後按一下 **組件**。  
  
23. 在右窗格中，與相關聯的文字方塊中**組件金鑰檔案**中，按一下省略符號，移至 C:\Program Files\Microsoft BizTalk 2013 Accelerator for RosettaNet\SDK\Message Inspector Pipeline Component\obj\debug，選取**MessageInspector.snk**，然後按一下 **確定**。  
  
24. 在[!INCLUDE[btsVStudioNoVersion](../../includes/btsvstudionoversion-md.md)]管線設計師中，選取**BTARN 訊息偵測器元件**圖形。  
  
25. 在[!INCLUDE[btsVStudioNoVersion](../../includes/btsvstudionoversion-md.md)]屬性 視窗，請在**目錄**方塊中，輸入您要放置 XML 檔案的目錄名稱。  
  
26. 在 [方案總管] 中，以滑鼠右鍵按一下專案名稱，然後**建置**。 驗證組建是否成功。  
  
27. 在 [方案總管] 中，以滑鼠右鍵按一下專案名稱，然後**部署**。 驗證部署是否成功。  
  
28. 在[!INCLUDE[btsVStudioNoVersion](../../includes/btsvstudionoversion-md.md)]上**檢視**功能表上，按一下  **BizTalk 總管**。  
  
29. 以滑鼠右鍵按一下**傳送埠**，然後按一下 **新增傳送埠**。  
  
30. 在**建立新傳送埠**對話方塊中，按一下 **確定**。  
  
31. 在**傳送埠屬性**對話方塊中，於**名稱**方塊中，輸入傳送埠的名稱與**主要**選取左窗格中，按一下**傳輸類型**右窗格中，然後選取**檔案**。  
  
32. 在**傳送埠屬性**對話方塊中，於**位址 (URI)**方塊中，按一下省略符號按鈕 (**...**).  
  
33. 在**FILE 傳輸屬性**] 對話方塊中，輸入**目的地**資料夾名稱，按一下 [**傳送**左窗格中，然後再針對**傳送管線**在右窗格中，選取您剛才建立的自訂管線。  
  
34. 按一下**篩選 & 對應**在左的窗格中，然後按一下**篩選**。  
  
35. 在右窗格中輸入篩選條件運算式，指定您要管線放置 XML 檔案的檔案類型。 例如，如果您想要針對卸除所有的 RNIF v1.1 訊息的檔案**屬性**會選取 [Microsoft.Solutions.BTARN.Schemas.RNIFv11.GlobalBusinessAction] 以及**運算子**一樣選取"Exists"，然後再按一下**確定**。  
  
36. 在 [BizTalk 總管] 中，以滑鼠右鍵按一下您剛才建立的傳送埠，請按一下**登錄**，以滑鼠右鍵按一下傳送埠，然後按**啟動**。  
  
## <a name="remarks"></a>備註  
 在一般的處理中，您一次只能檢查一個訊息 (您在協調流程中指定為訊息內文的部分)。 因此，您只能在 BizTalk 管理主控台中檢查其中一個部分，您進行疑難排解的能力是受限的。 「訊息偵測器管線元件」可幫助您克服這項限制。  
  
## <a name="see-also"></a>請參閱  
 [公用程式](../../adapters-and-accelerators/accelerator-rosettanet/utilities1.md)