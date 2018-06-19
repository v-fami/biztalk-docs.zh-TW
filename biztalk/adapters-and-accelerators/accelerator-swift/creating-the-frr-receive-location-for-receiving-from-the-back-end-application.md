---
title: 建立 FRR 接收位置從後端應用程式接收 |Microsoft 文件
ms.custom: ''
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- receive locations, creating
- creating, receive locations
- FRR, creating receive locations
ms.assetid: 78bd8084-ddec-4066-a474-ab5b1a0a849f
caps.latest.revision: 6
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 46895ff64e6585c8b80979c09874dffb510cf049
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/20/2017
ms.locfileid: "22210078"
---
# <a name="creating-the-frr-receive-location-for-receiving-from-the-back-end-application"></a>建立 FRR 接收位置從後端應用程式接收
若要執行 FIN 回應重新調整，您必須建立接收位置從後端應用程式進入接收之訊息[!INCLUDE[btaA4SWIFT2.3abbrevnonumber](../../includes/btaa4swift2-3abbrevnonumber-md.md)]。  
  
 **摘要**  
  
 建立具有下列屬性和元件的接收位置：  
  
|屬性/元件|設定|  
|-------------------------|-------------|  
|接收埠|單向連接埠|  
|傳輸類型|後端應用程式所使用的傳輸類型|  
|位址的 URI|傳輸類型的必要項|  
|接收處理常式|BizTalkServerApplication|  
|接收管線|[!INCLUDE[btaA4SWIFT2.3abbrevnonumber](../../includes/btaa4swift2-3abbrevnonumber-md.md)]接收管線所建立的 FRR|  
  
### <a name="to-add-an-frr-receive-location-for-receiving-from-the-back-end-application"></a>若要加入 FRR 接收接收位置從後端應用程式  
  
1.  在 BizTalk Server 管理主控台中，展開**BizTalk Server 管理**， **BizTalk 群組**，**應用程式**，和**BizTalk 應用程式1**節點。  
  
2.  以滑鼠右鍵按一下**管線**，然後按一下 **重新整理**。  
  
3.  以滑鼠右鍵按一下**接收埠**，指向 **新增**，然後按一下 **單向接收埠**。  
  
4.  在 [接收埠屬性] 對話方塊中**名稱**方塊中，輸入接收埠，例如 FRRBackEndReceivePort 的名稱。  
  
5.  按一下**套用**來繫結連接埠，然後按一下**確定**。  
  
6.  在管理主控台中，以滑鼠右鍵按一下**接收位置**，指向 **新增**，然後按一下 **單向接收位置**。  
  
7.  在 [選取接收埠] 對話方塊中，選取您剛才的接收埠建立，，然後按一下**確定**。  
  
8.  在 [接收位置屬性] 對話方塊中**名稱**方塊中，輸入接收位置的名稱。  
  
9. 在**傳輸** 區段中，針對**類型**文字方塊中，選取由後端應用程式使用的傳輸類型。  
  
10. 按一下**設定**。  
  
11. 在 FILE 傳輸屬性 對話方塊中，填入所需的傳輸類型的屬性，然後按一下 **確定**。  
  
12. 在 [接收位置屬性] 對話方塊的**接收處理常式**，選取**BizTalkServerApplication**。  
  
13. 在 [接收位置屬性] 對話方塊的**接收管線**，選取[!INCLUDE[btaA4SWIFT2.3abbrevnonumber](../../includes/btaa4swift2-3abbrevnonumber-md.md)]接收管線 FRR 所建立。  
  
14. 按一下**套用**，然後按一下 [**確定**關閉**接收位置屬性**] 對話方塊。  
  
15. 在 [BizTalk 總管] 中，以滑鼠右鍵按一下您剛才的接收位置建立，，然後按一下**啟用**。