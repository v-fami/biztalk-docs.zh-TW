---
title: "步驟 8： 使用 BizTalk 對應工具建立對應 |Microsoft 文件"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- message enrichment tutorial, maps
- creating, maps
- maps, creating
- BizTalk Mapper
ms.assetid: 785426c7-5651-48be-b3f4-7f9d8051ba23
caps.latest.revision: "3"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 48e2578211d65ade2a50916e909c87a6fd84bf44
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/20/2017
---
# <a name="step-8-create-a-map-with-biztalk-mapper"></a>步驟 8： 使用 BizTalk 對應工具建立對應
在此步驟中，您可以使用 BizTalk 對應工具來建立對應。 您可以建立關聯的資料 （欄位） 的連結，使用此對應來補充要求文件中拒絕文件要求的資料中。  
  
### <a name="to-create-a-map"></a>若要建立對應  
  
1.  在 方案總管 中，以滑鼠右鍵按一下**BTAHL7 專案**，指向 **新增**，然後按一下 **新項目**。  
  
2.  在**加入新項目**對話方塊中，於**類別**] 窗格中，按一下 [**對應檔**。  
  
3.  在**名稱**欄位中，輸入**DoorbellMap**來命名對應，然後按一下**新增**啟動 BizTalk 對應工具。  
  
4.  在**來源結構描述**窗格 （左側），按一下 **開啟來源結構描述**。  
  
5.  在 BizTalk 型別選擇器 對話方塊中，依序展開**BTAHL7 專案**，依序展開**結構描述**，按一下  **BTAHL7_Project.Doorbell**，然後按一下 **確定**.  
  
6.  在**目的結構描述**窗格 （右側），按一下 **開啟目的結構描述**。  
  
7.  在 BizTalk 型別選擇器中，展開**BTAHL7 專案**，依序展開**結構描述**，按一下  **BTAHL7Schemas.ADT_A04_22_GLO_DEF**，然後按一下 **確定**.  
  
8.  在**目的結構描述**窗格 （右側），依序展開**ADT_A04_22_GLO_DEF**，依序展開**PID_PatientIdentification**，並展開**PID.5_PatientName**.  
  
9. 在**來源結構描述**窗格 （左側），依序展開**DoorbellRoot**。 拖曳**LastName**欄位設為**PN_0_FamilyName**欄位**目的結構描述**窗格。  
  
10. 在**來源結構描述**窗格拖曳**FirstName**欄位設為**PN_1_GivenName**欄位**目的結構描述**窗格。  
  
11. 在**來源結構描述**窗格拖曳**MiddleName**欄位設為**PN_2_MiddleInitialOrName**欄位**目的結構描述**窗格.  
  
12. 在**目的結構描述**] 窗格中，展開 [ **PID_3_PatientIdInternalId**。  
  
13. 在**來源結構描述**窗格拖曳**SSN**欄位設為**CM_PAT_ID_0_PatientID**中**目的結構描述**窗格。  
  
14. 在**檔案**功能表上，按一下 **全部儲存**。  
  
 在一般訊息豐富 」 案例中，如果任何病患的資訊已遺失，您會在您的協調流程呼叫以病患記錄資料庫並加入遺漏的資訊，然後完成對應中使用的其他資訊。 比方說，您可能會擷取某個病患的住家地址從病患記錄資料庫，因為輸入的 XML doorbell 觸發程序事件訊息未提供。  
  
 若要繼續[步驟 9： 驗證和建置對應專案](../../adapters-and-accelerators/accelerator-hl7/step-9-validate-and-build-the-map-project.md)。  
  
## <a name="see-also"></a>另請參閱  
 [訊息擴充教學課程](../../adapters-and-accelerators/accelerator-hl7/message-enrichment-tutorial.md)