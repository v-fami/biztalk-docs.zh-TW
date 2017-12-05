---
title: "如何設定虛擬目錄 |Microsoft 文件"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- virtual directory, configuring
- configuring virtual directory
- applications, verifying for users
- verifying applications for users
ms.assetid: 3da16524-8238-426a-88f8-434be5992e13
caps.latest.revision: "9"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: f00c5f75062ffd084cd19f23bfa66768d3d67ca5
ms.sourcegitcommit: 5abd0ed3f9e4858ffaaec5481bfa8878595e95f7
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/28/2017
---
# <a name="how-to-configure-the-virtual-directory"></a>如何設定虛擬目錄
此主題說明設定虛擬目錄與為使用者驗證應用程式的程序。  
  
### <a name="to-configure-the-virtual-directory"></a>設定虛擬目錄  
  
1.  在 %systemdrive%，建立設定為虛擬目錄的資料夾。  
  
2.  按一下**啟動**，指向 **程式**，按一下**系統管理工具**，然後按一下**網際網路資訊服務 (IIS) 管理員**。  
  
3.  展開**\<伺服器名稱\>** ，然後展開 **網站**。  
  
4.  以滑鼠右鍵按一下**Default Web Site**按一下**新增虛擬目錄**。  
  
5.  在**新增虛擬目錄**對話方塊方塊中，輸入別名。  
  
6.  輸入步驟 1 中建立之資料夾的路徑。 或者，按一下**（...）**瀏覽至資料夾位置。  
  
7.  按一下 **[確定]**。 資料夾會顯示在**Default Web Site**資料夾。  
  
8.  以滑鼠右鍵按一下資料夾，然後按一下**轉換成應用程式**。  
  
9. 在**新增應用程式**對話方塊中，按一下 **確定**。 資料夾會轉換成應用程式 （您可以看到在圖示 – 從資料夾圖示的網站 圖示以變更）。  
  
## <a name="see-also"></a>請參閱  
 [保護配接器](../core/security-in-biztalk-adapter-for-peoplesoft-enterprise.md)