---
title: "如何設定活動視窗的持續時間 |Microsoft 文件"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- Set-ActivityWindow command [BAM]
- activities [BAM], time intervals
- managing [BAM], time intervals
ms.assetid: e39c315e-f215-4f81-9774-cf7aedf6ba33
caps.latest.revision: "14"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 50b4aaa0187c10038dde907fa8b5fa8c595d2847
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/20/2017
---
# <a name="how-to-set-the-duration-on-an-activity-window"></a>如何設定活動視窗的持續時間
系統管理員使用**組 activitywindow**命令設定指定之活動的持續時間。  
  
### <a name="to-set-the-duration-on-an-activity"></a>設定活動的持續時間  
  
1.  開啟命令提示字元，如下所示： 按一下**啟動**，按一下**執行**，型別**cmd**，然後按一下 **確定**。  
  
2.  在命令提示字元中，輸入 [!INCLUDE[btsBiztalkServerPath](../includes/btsbiztalkserverpath-md.md)]Tracking，以瀏覽至追蹤資料夾。 按 ENTER 鍵。  
  
3.  型別**bm 組 activitywindow-活動：\<活動名稱 >-TimeLength:\<整數數字 >-TimeUnit： 月份 &#124; 天 &#124;小時 &#124;分鐘**。  
  
    > [!NOTE]
    >  在支援使用者帳戶控制 (UAC) 的系統上，您可能需要使用系統管理權限來執行工具。  
  
4.  按 ENTER 鍵。  
  
## <a name="see-also"></a>另請參閱  
 [管理 BAM 動態基礎結構](../core/managing-the-bam-dynamic-infrastructure.md)   
 [BAM 管理公用程式](../core/bam-management-utility.md)   
 [如何取得活動視窗的持續時間](../core/how-to-get-the-duration-on-an-activity-window.md)