---
title: 如何變更追蹤 QueryTimeout 值 |Microsoft 文件
ms.custom: ''
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- queries [HAT], time-out limits
- HAT, time-out limits
ms.assetid: abc26f37-6537-42fa-81ff-bc8b758b4e10
caps.latest.revision: 8
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: ca9f61466323e0b154bdeb0499cc5cee6e4ef10c
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/20/2017
ms.locfileid: "22247470"
---
# <a name="how-to-change-the-tracking-querytimeout-value"></a>如何變更追蹤 QueryTimeout 值
根據預設，訊息和服務執行個體追蹤會逾時查詢的執行時間超過 60 秒。 您可以在登錄中變更此逾時值，讓查詢的執行時間可以超過 60 秒。  
  
> [!CAUTION]
>  不當編輯登錄可能會造成系統嚴重受損。 在變更登錄之前，應備份電腦上的所有重要資料。  
  
## <a name="prerequisites"></a>必要條件  
 您必須以「系統管理員」群組成員的身分登入，才能執行此程序。  
  
### <a name="to-change-the-query-timeout-value"></a>若要變更查詢逾時值  
  
1.  按一下**啟動**，按一下 **執行**，型別**regedit**，然後按一下 **確定**。  
  
2.  在登錄編輯程式中，找出下列子機碼然後按一下它：  
  
     **HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\BizTalk server\3.0**  
  
3.  如果有 Tracking 子機碼，請跳到步驟 6。  
  
4.  若要建立 Tracking 子機碼，在**編輯**功能表上，指向**新增**，然後按一下 **金鑰**。  
  
5.  型別**追蹤**，然後按 ENTER 鍵。  
  
6.  找出下列子機碼，然後按一下它：  
  
     **HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\BizTalk Server\3.0\Tracking**  
  
7.  在**編輯**功能表上，指向**新增**，然後按一下  **DWORD 值**。  
  
8.  型別**ConnectionTimeout**，然後按 ENTER 鍵。  
  
9. 以滑鼠右鍵按一下**ConnectionTimeout**，然後按一下 **修改**。  
  
10. 在**編輯 DWORD 值**對話方塊中，按一下 **十進位**。  
  
11. 在**數值資料**方塊中，輸入值以秒為單位，您想要設定查詢逾時值，然後按一下 **確定**。  
  
12. 在 **[檔案]** 功能表上按一下 **[結束]**。  
  
    > [!NOTE]
    >  您可能需要先關閉再重新開啟 BizTalk Server 管理主控台中新的逾時值的訂單才會生效。  
  
## <a name="see-also"></a>另請參閱  
 [檢視歷程記錄和追蹤資料](../core/viewing-historical-and-tracked-data.md)