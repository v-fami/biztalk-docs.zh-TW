---
title: 步驟 2： 建立新的專案 |Microsoft 文件
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
ms.openlocfilehash: c4b296b01179b3ce52aef41dc246dbed2588c3e6
ms.sourcegitcommit: 3fc338e52d5dbca2c3ea1685a2faafc7582fe23a
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/01/2017
ms.locfileid: "26004695"
---
# <a name="step-2-create-a-new-project"></a>步驟 2： 建立新的專案
在此步驟中，您必須建立新的方案使用[!INCLUDE[btsCoName](../../includes/btsconame-md.md)][!INCLUDE[btsVStudio2008](../../includes/btsvstudio2008-md.md)]環境。 首先，您會建立新的專案 (BTAHL7V22Common) 包含三個一般結構描述 （適用於資料類型、 區段和資料表值），使用 V2.2 HL7 結構描述，包括將用於外寄 HL7 訊息結構描述。 第二，您可以建立另一個新的專案 (BTAHL7V2XCommon) 包含用於 HL7 訊息 (MSH_25_GLO_DEF) 中的標頭的一般標準結構描述。  
  
### <a name="to-create-a-new-project"></a>建立新的專案  
  
1.  啟動**Visual Studio**。  
  
2.  在 **[檔案]** 功能表上，指向 **[開新檔案]**，然後按一下 **[專案]**。  
  
3.  在 [新增專案] 對話方塊中，展開**BizTalk 專案**資料夾，然後再按一下**BTAHL7Projects**資料夾。  
  
4.  在**範本**] 窗格中，按一下 [ **BTAHL7V22Common 專案**。  
  
5.  在**名稱**欄位中，輸入**BTAHL7V22Common**做為專案名稱。  
  
6.  在**位置**欄位中，輸入*\<磁碟機\>***: \Tutorial**作為路徑，然後按一下**確定**開啟新的專案。  
  
    > [!NOTE]
    >  BizTalk Accelerator for HL7 ([!INCLUDE[btaBTAHL71.3abbrevnonumber](../../includes/btabtahl71-3abbrevnonumber-md.md)]) 將新的專案加入至方案總管 中，有三種常見的結構描述：  
  
    -   datatypes_22.xsd  
  
    -   segments_22.xsd  
  
    -   tablevalues_22.xsd  
  
     [!INCLUDE[btsVStudioNoVersion](../../includes/btsvstudionoversion-md.md)]建立專案資料夾和檔案中\<*磁碟機*\>: \Tutorial\BTAHL7V22Common 資料夾。  
  
7.  在 **[檔案]** 功能表上，指向 **[開新檔案]**，然後按一下 **[專案]**。  
  
8.  在 [新增專案] 對話方塊中，展開**BizTalk 專案**資料夾，然後再按一下**BTAHL7Projects**資料夾。  
  
9. 在**範本**] 窗格中，按一下 [ **btahl7v2xc 通用專案**。  
  
10. 在**名稱**欄位中，輸入**btahl7v2xc 通用**做為專案名稱。  
  
11. 在**位置**欄位中，輸入*\<磁碟機\>***: \Tutorial**做為路徑。  
  
12. 在**方案**欄位中，選取**將加入至方案**，然後按一下 **確定**。  
  
    > [!NOTE]
    >  [!INCLUDE[btaBTAHL71.3abbrevnonumber](../../includes/btabtahl71-3abbrevnonumber-md.md)]具有下列結構描述會將新的專案加入方案總管 中：  
  
    -   ACK_24_GLO_DEF.xsd  
  
    -   ACK_25_GLO_DEF.xsd  
  
    -   MSH_25_GLO_DEF.xsd  
  
     [!INCLUDE[btsVStudioNoVersion](../../includes/btsvstudionoversion-md.md)]建立專案資料夾和檔案中**\<磁碟機\>: \Tutorial\BTAHL7V22Common\BTAHL72XCommon**資料夾。  
  
 若要繼續[步驟 3： 指派強式名稱組件](../../adapters-and-accelerators/accelerator-hl7/step-3-assign-a-strong-name-to-the-assembly.md)。  
  
## <a name="see-also"></a>請參閱  
 [訊息擴充教學課程](../../adapters-and-accelerators/accelerator-hl7/message-enrichment-tutorial.md)