---
title: 如何建立追蹤設定檔 |Microsoft 文件
ms.custom: ''
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- tracking profiles, creating
- creating, tracking profiles
ms.assetid: 676ae7e8-f3eb-45f1-ad2e-807b434c0bf9
caps.latest.revision: 14
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 34f5d6cbb210cb292cd8ae7d0e2f4ff811984377
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/20/2017
ms.locfileid: "22248934"
---
# <a name="how-to-create-a-tracking-profile"></a>如何建立追蹤設定檔
您可建立追蹤設定檔，將 BAM 活動定義連結到部署的組件和 BizTalk Server 傳訊屬性。 當您開啟追蹤設定檔編輯器時，可以按一下匯入活動連結或匯入功能表項目建立新的追蹤設定檔。  
  
## <a name="prerequisites"></a>必要條件  
 以下是執行此主題中之程序的必要條件：  
  
-   您具有權限的現有 BizTalk 管理資料庫。  
  
-   設定為使用 BizTalk 管理資料庫的 TPE。  
  
-   BAM 主要匯入資料庫中的現有 BAM 活動定義。  
  
### <a name="to-create-a-tracking-profile"></a>建立追蹤設定檔  
  
1.  在電腦或在已識別為來源系統的電腦，開啟**追蹤設定檔編輯器**。 若要這樣做，請按一下**啟動**，按一下**執行**，型別**BTSTrkEditor.exe**，然後按一下 **確定**。  
  
    > [!NOTE]
    >  在支援使用者帳戶控制 (UAC) 的系統上，您可能需要使用系統管理權限來執行工具。 若要這樣做，應用程式，以滑鼠右鍵按一下，然後選取**系統管理員身分執行**。  
  
2.  中間的 TPE 左窗格中，按一下**按一下這裡匯入 BAM 活動定義**連結。 這會開啟**匯入 BAM 活動定義** 對話方塊。  
  
3.  從**BAM 活動定義名稱**清單方塊選取要設立追蹤的活動。 如果您的清單包含許多已部署的活動，您可以輸入中的活動名稱的一部分**中字串**文字方塊中，然後按一下**搜尋** 按鈕。 如此便會限定所顯示的活動清單，只列出其名稱包含所輸入之部分名稱的活動。  
  
4.  一旦您選取活動，按一下**確定** 按鈕。 這會根據所選取的活動開啟新的追蹤設定檔，並在 TPE 的左窗格中顯示該設定檔。  
  
## <a name="see-also"></a>另請參閱  
 [建立追蹤設定檔](../core/creating-tracking-profiles.md)