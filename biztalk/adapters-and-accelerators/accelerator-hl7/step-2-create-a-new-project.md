---
title: 步驟 2： 建立新的專案 |Microsoft Docs
ms.custom: ''
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- creating, projects
- projects, creating
- message enrichment tutorial, projects
ms.assetid: 6e994845-53b8-4de8-a64f-32d36f7b5412
caps.latest.revision: 6
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 4e17dccc7ef83114fe17c26b03aaa8d06f7ac783
ms.sourcegitcommit: 266308ec5c6a9d8d80ff298ee6051b4843c5d626
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/27/2018
ms.locfileid: "36994647"
---
# <a name="step-2-create-a-new-project"></a>步驟 2： 建立新的專案
在此步驟中，您必須建置新的解決方案藉由使用 Microsoft[!INCLUDE[btsVStudio2008](../../includes/btsvstudio2008-md.md)]環境。 首先，您會建立新的專案 (BTAHL7V22Common) 包含三個常見結構描述 （適用於資料類型、 區段和資料表值），V2.2 HL7 結構描述使用，包括您要用於外寄的 HL7 訊息結構描述。 第二，您會建立另一個新專案 （btahl7v2xc 通用），其中包含用於 HL7 訊息 (MSH_25_GLO_DEF) 中的標頭的常見標準結構描述。  
  
### <a name="to-create-a-new-project"></a>建立新的專案  
  
1. 開始**Visual Studio**。  
  
2. 在 **[檔案]** 功能表上，指向 **[開新檔案]**，然後按一下 **[專案]**。  
  
3. 在 [新增專案] 對話方塊中，展開**BizTalk 專案**資料夾，然後再按一下**BTAHL7Projects**資料夾。  
  
4. 在 **範本**窗格中，按一下**BTAHL7V22Common 專案**。  
  
5. 在 **名稱**欄位中，輸入**BTAHL7V22Common**做為專案名稱。  
  
6. 在 **位置**欄位中，輸入*\<磁碟機\>* * *:\Tutorial** 作為路徑，然後按一下**確定**開啟新的專案。  
  
   > [!NOTE]
   >  BizTalk Accelerator for HL7 ([!INCLUDE[btaBTAHL71.3abbrevnonumber](../../includes/btabtahl71-3abbrevnonumber-md.md)]) 新的專案加入方案總管 中，具有三個常見的結構描述：  
  
   - datatypes_22.xsd  
  
   - segments_22.xsd  
  
   - tablevalues_22.xsd  
  
     [!INCLUDE[btsVStudioNoVersion](../../includes/btsvstudionoversion-md.md)] 建立專案資料夾和檔案中\<*磁碟機*\>: \Tutorial\BTAHL7V22Common 資料夾。  
  
7. 在 **[檔案]** 功能表上，指向 **[開新檔案]**，然後按一下 **[專案]**。  
  
8. 在 [新增專案] 對話方塊中，展開**BizTalk 專案**資料夾，然後再按一下**BTAHL7Projects**資料夾。  
  
9. 在 **範本**窗格中，按一下**btahl7v2xc 通用專案**。  
  
10. 在 **名稱**欄位中，輸入**btahl7v2xc 通用**做為專案名稱。  
  
11. 在 **位置**欄位中，輸入*\<磁碟機\>* * *:\Tutorial** 作為路徑。  
  
12. 在 **解決方案**欄位中，選取**將加入至方案**，然後按一下  **確定**。  
  
    > [!NOTE]
    >  [!INCLUDE[btaBTAHL71.3abbrevnonumber](../../includes/btabtahl71-3abbrevnonumber-md.md)] 將新的專案加入方案總管，使用下列結構描述：  
  
    - ACK_24_GLO_DEF.xsd  
  
    - ACK_25_GLO_DEF.xsd  
  
    - MSH_25_GLO_DEF.xsd  
  
      [!INCLUDE[btsVStudioNoVersion](../../includes/btsvstudionoversion-md.md)] 建立專案資料夾和檔案中**\<磁碟機\>: \Tutorial\BTAHL7V22Common\BTAHL72XCommon**資料夾。  
  
    請繼續進行[步驟 3： 指派強式名稱組件](../../adapters-and-accelerators/accelerator-hl7/step-3-assign-a-strong-name-to-the-assembly.md)。  
  
## <a name="see-also"></a>另請參閱  
 [訊息擴充教學課程](../../adapters-and-accelerators/accelerator-hl7/message-enrichment-tutorial.md)