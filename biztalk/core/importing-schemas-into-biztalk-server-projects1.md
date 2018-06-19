---
title: 結構描述匯入到 BizTalk Server Projects1 |Microsoft 文件
ms.custom: ''
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- importing schemas
- orchestration variables, messages
- schemas, importing into BizTalk Server
- orchestration types, port types
ms.assetid: fa640195-a735-4201-a893-48f3405ddcb5
caps.latest.revision: 4
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 719679dffa5bcffdeddcbcd889f847f147a705b4
ms.sourcegitcommit: dd7c54feab783ae2f8fe75873363fe9ffc77cd66
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/07/2017
ms.locfileid: "24015445"
---
# <a name="importing-schemas-into-biztalk-server-projects"></a>結構描述匯入至 BizTalk Server 專案
下列資訊說明如何將結構描述匯入至 BizTalk Server 專案。  
  
## <a name="importing-schemas"></a>匯入結構描述  
  
#### <a name="to-import-schemas"></a>若要匯入結構描述  
  
1.  在 [方案總管] 中，以滑鼠右鍵按一下專案，指向**新增**，然後選取**新增產生的項目**。  
  
2.  按一下**新增配接器**，然後選取**開啟**。  
  
3.  選取的介面卡 **，J.D.Edwards OneWorld XE**。  
  
4.  在下拉式清單中，選取 連接埠**SSOSendToJD Edwards OneWorld XE**，然後按一下 **下一步**。  
  
     MyJ.D。 Edwards OneWorld XESSO 邏輯系統隨即出現在瀏覽器中 （這個邏輯系統使用 SSOSendToJ.D 建立。 Edwards OneWorld XE 連接埠）。  
  
5.  展開**myJ.D。Edwards OneWorld XESSO**。  
  
6.  按一下箭頭圖示來移動項目 （或直接拖曳） 到**傳輸**視窗中，然後再按一下**確定**。  
  
     結構描述隨即加入至 SSOSchedule 專案。  
  
7.  在 [方案總管] 中，展開**SSOSchedule 專案**。  
  
8.  以滑鼠右鍵按一下**BizTalk orchestration.odx**，然後按一下 **刪除**。  
  
9. 在 [方案總管] 中，按兩下 **[getlist.odx]** 檢查協調流程。  
  
## <a name="orchestration-types---port-types"></a>協調流程類型 - 連接埠類型  
  
-   **PortTypeIn/中/要求：** SSOSchedule.myJ.D。 Edwards OneWorld XEsso_transmitService_3.method  
  
-   **PortTypeOut/Out/回應：** SSOSchedule.myJ.D。 Edwards OneWorld XE sso_transmitService_3.methodResponse  
  
-   **PortTypeInOut/InOut/要求：** SSOSchedule.myJ.D。 Edwards OneWorld XEsso_transmitService_3.method  
  
-   **PortTypeInOut/InOut/回應：** SSOSchedule.myJ.D。 Edwards OneWorld XE sso_transmitService_3.methodResponse  
  
## <a name="orchestration-variables---messages"></a>協調流程變數 - 訊息  
  
-   **MessageIn:** SSOSchedule.myJ.D。 Edwards OneWorld XEsso_transmitService_3.method  
  
-   **MessageOut:** SSOSchedule.myJ.D。 Edwards OneWorld XE sso_transmitService_3.methodResponse  
  
## <a name="see-also"></a>另請參閱  
 [在配接器的安全性](../core/security-in-biztalk-adapter-for-jd-edwards-oneworld.md)