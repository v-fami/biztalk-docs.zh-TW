---
title: 步驟 2： 新增 v2.3.1 通用結構描述 |Microsoft 文件
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
ms.openlocfilehash: ba84c9f45c477aefe7615eca906c40014b06bd04
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/20/2017
ms.locfileid: "22206510"
---
# <a name="step-2-add-common-schemas-for-v231"></a>步驟 2： 新增 v2.3.1 通用結構描述
在此步驟中，您可以建立新 BTAHL7231Common 專案範本為基礎的專案。 此範本包含三個的通用結構描述 （適用於資料類型、 區段和資料表值）， [!INCLUDE[btsCoName](../../includes/btsconame-md.md)] BizTalk Accelerator for HL7 ([!INCLUDE[btaBTAHL71.3abbrevnonumber](../../includes/btabtahl71-3abbrevnonumber-md.md)]) 用來驗證 v2.3.1 訊息執行個體。 [!INCLUDE[btaBTAHL71.3abbrevnonumber](../../includes/btabtahl71-3abbrevnonumber-md.md)]HL7 v2.3.1 結構描述，包括將用於內送的批次中的個別訊息的結構描述搭配使用這些常見的結構描述 (ADT ^ A03)。  
  
 在此步驟結束時，您可以指派至組件的強式金鑰和部署。 您沒有建立第二個的強式金鑰。您可以使用您在建立強式金鑰[步驟 1： 加入標頭和通知結構描述](../../adapters-and-accelerators/accelerator-hl7/step-1-add-header-and-acknowledgment-schemas.md)。  
  
### <a name="to-add-v231-common-schemas-and-deploy-the-assembly"></a>新增 v2.3.1 常見的結構描述及部署組件  
  
1.  在[!INCLUDE[btsVStudioNoVersion](../../includes/btsvstudionoversion-md.md)]上**檔案**功能表上，指向**新增**，然後按一下 **專案**。  
  
2.  在 [新增專案] 對話方塊中**專案類型**區段中，展開**BizTalk 專案**，然後選取**BTAHL7Projects**。  
  
3.  在**範本**區段中，選取**BTAHL7V231Common 專案**。  
  
4.  在**名稱**方塊中，輸入**BTAHL7V231Common 專案**做為專案名稱。  
  
5.  在**方案**方塊中，選取**將加入至方案**。  
  
6.  按一下 **[確定]**。  
  
    > [!NOTE]
    >  在方案總管 中，三個結構描述 （datatypes_231.xsd、 segments_231.xsd 和 tablevalues_231.xsd） 都包含在專案中。  
  
7.  在 方案總管 中，以滑鼠右鍵按一下**BTAHL7V231Common 專案**，然後按一下 **屬性**。  
  
8.  在 BTAHL7V231Common 屬性頁 對話方塊中，按一下 **簽署**。  
  
9. 請檢查**簽署組件**核取方塊。  
  
10. 在 選擇強式名稱金鑰檔下拉式清單中，選取。  
  
11. 瀏覽至 **: \Batching 教學課程**，選取**key.snk**，然後按一下 **開啟**。  
  
12. 以滑鼠右鍵按一下**BTAHL7V231Common**，然後按一下 **部署**。 確定成功的訊息出現在 [輸出] 視窗。  
  
    > [!NOTE]
    >  如果未出現正確的訊息，使用[!INCLUDE[btsVStudioNoVersion](../../includes/btsvstudionoversion-md.md)]疑難排解您的結構描述。  
  
 若要繼續[步驟 3： 新增觸發程序事件 （訊息） 結構描述](../../adapters-and-accelerators/accelerator-hl7/step-3-add-a-trigger-event-message-schema.md)。