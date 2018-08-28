---
title: 步驟 2： 建立 V2.3.1 通用結構描述 |Microsoft Docs
ms.custom: ''
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- end-to-end tutorial, common schemas
- common schemas
ms.assetid: db1a2206-559f-475a-803d-55522cce007e
caps.latest.revision: 5
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: e6331538a3dd46dcd45d63bcbdbc3b8f19b2c531
ms.sourcegitcommit: 266308ec5c6a9d8d80ff298ee6051b4843c5d626
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/27/2018
ms.locfileid: "36995407"
---
# <a name="step-2-create-common-schemas-for-v231"></a>步驟 2： 建立 V2.3.1 通用結構描述
V2.3.1 結構描述是經常參考的結構描述，用來驗證訊息執行個體。  
  
### <a name="to-create-a-common-schema-for-v231"></a>若要建立 V2.3.1 通用結構描述  
  
1. 在 [!INCLUDE[btsVStudioNoVersion](../../includes/btsvstudionoversion-md.md)]上**檔案**功能表上，指向**新增**，然後按一下 **專案**。  
  
2. 在 [新增專案] 對話方塊中，在**專案類型**區段中，展開**BizTalk 專案**，然後選取**BTAHL7Projects**。  
  
3. 在 [範本] 區段中，選取**BTAHL7V231Common 專案**。  
  
4. 在 **名稱**方塊中，輸入**BTAHL7V231Common 專案**做為專案名稱。  
  
5. 在 **解決方案**方塊中，選取**加入至方案**。  
  
6. 按一下 [確定] 。  
  
   > [!NOTE]
   >  在 [方案總管] 中，三個結構描述 （datatypes_231.xsd segments_231.xsd 和 tablevalues_231.xsd），會包含在專案中。  
  
7. 在 [方案總管] 中，以滑鼠右鍵按一下**BTAHL7V231Common 專案**，然後按一下**屬性**。  
  
8. 在 BTAHL7V231Common 屬性頁面上，按一下**簽署**。  
  
9. 選取 **簽署組件**核取方塊。  
  
10. 在 **選擇強式名稱金鑰檔**，選取**\<瀏覽...\>** .  
  
11. 瀏覽至\<磁碟機\>: \Batching 教學課程中，選取**key.snk**，然後按一下**開啟**。  
  
12. 在 [方案總管] 中，以滑鼠右鍵按一下**BTAHL7V231Common 專案**，然後按一下**部署**。 請確定在 [輸出] 視窗中會出現成功訊息。  
  
    > [!NOTE]
    >  如果未出現正確的訊息，使用[!INCLUDE[btsVStudioNoVersion](../../includes/btsvstudionoversion-md.md)]疑難排解您的結構描述。  
  
    請繼續進行[步驟 3： 新增觸發程序事件 （訊息） 結構描述](../../adapters-and-accelerators/accelerator-hl7/step-3-add-a-trigger-event-message-schema.md)。