---
title: 步驟 2： 新增 v2.3.1 通用結構描述 |Microsoft Docs
ms.custom: ''
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: da98fe6c-4776-4cb8-8454-af3128dea4ab
caps.latest.revision: 4
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 36b07419b50d02d1f810dffbd7417533e844a3ea
ms.sourcegitcommit: 266308ec5c6a9d8d80ff298ee6051b4843c5d626
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/27/2018
ms.locfileid: "36994159"
---
# <a name="step-2-add-common-schemas-for-v231"></a>步驟 2： 新增 v2.3.1 通用結構描述
在此步驟中，您可以建立根據 BTAHL7231Common 專案範本的新專案。 此範本包含三個常見的結構描述 （適用於資料類型、 區段和資料表值），Microsoft BizTalk Accelerator for HL7 ([!INCLUDE[btaBTAHL71.3abbrevnonumber](../../includes/btabtahl71-3abbrevnonumber-md.md)]) 用以驗證 v2.3.1 訊息執行個體。 [!INCLUDE[btaBTAHL71.3abbrevnonumber](../../includes/btabtahl71-3abbrevnonumber-md.md)] HL7 v2.3.1 結構描述，包括您要用於內送的批次中的個別訊息的結構描述搭配使用這些常見的結構描述 (ADT ^ 將 adt^a03)。  
  
 在此步驟結束時，您指派給組件的強式金鑰，並部署。 您不需要建立第二個的強式金鑰;您可以使用您在中建立的強式金鑰[步驟 1： 新增標頭和通知結構描述](../../adapters-and-accelerators/accelerator-hl7/step-1-add-header-and-acknowledgment-schemas.md)。  
  
### <a name="to-add-v231-common-schemas-and-deploy-the-assembly"></a>若要新增 v2.3.1 通用結構描述，並部署組件  
  
1. 在 [!INCLUDE[btsVStudioNoVersion](../../includes/btsvstudionoversion-md.md)]上**檔案**功能表上，指向**新增**，然後按一下 **專案**。  
  
2. 在 [新增專案] 對話方塊中，在**專案類型**區段中，展開**BizTalk 專案**，然後選取**BTAHL7Projects**。  
  
3. 在 **範本**區段中，選取**BTAHL7V231Common 專案**。  
  
4. 在 **名稱**方塊中，輸入**BTAHL7V231Common 專案**做為專案名稱。  
  
5. 在 **解決方案**方塊中，選取**加入至方案**。  
  
6. 按一下 [確定] 。  
  
   > [!NOTE]
   >  在 [方案總管] 中，三個結構描述 （datatypes_231.xsd segments_231.xsd 和 tablevalues_231.xsd），會包含在專案中。  
  
7. 在 [方案總管] 中，以滑鼠右鍵按一下**BTAHL7V231Common 專案**，然後按一下**屬性**。  
  
8. 在 BTAHL7V231Common 屬性頁 對話方塊中，按一下 **簽署**。  
  
9. 請檢查**簽署組件**核取方塊。  
  
10. 在 選擇強式名稱金鑰檔下拉式清單中選取。  
  
11. 瀏覽至 **: \Batching 教學課程**，選取**key.snk**，然後按一下**開啟**。  
  
12. 以滑鼠右鍵按一下**BTAHL7V231Common**，然後按一下**部署**。 請確定在 [輸出] 視窗中會出現成功訊息。  
  
    > [!NOTE]
    >  如果未出現正確的訊息，使用[!INCLUDE[btsVStudioNoVersion](../../includes/btsvstudionoversion-md.md)]疑難排解您的結構描述。  
  
    請繼續進行[步驟 3： 新增觸發程序事件 （訊息） 結構描述](../../adapters-and-accelerators/accelerator-hl7/step-3-add-a-trigger-event-message-schema.md)。