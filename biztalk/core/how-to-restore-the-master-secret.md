---
title: "如何還原主要密碼 |Microsoft 文件"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- managing [Master Secret server], restoring
- Master Secret server, restoring
- restoring, Master Secret server
ms.assetid: 68e133c5-4591-4d76-9a3b-c9564ff1aa60
caps.latest.revision: "11"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 2550d8e1ea0ad45147b2f27daef7244f6c18770b
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/20/2017
---
# <a name="how-to-restore-the-master-secret"></a>如何還原主要密碼
您必須還原主要密碼，才能重新使用現有的資料，這是資料回復程序的一部分。 要執行此作業，您必須使用同時是 Windows 管理員和 SSO 系統管理員的帳戶，登入主要密碼伺服器。  
  
### <a name="to-restore-the-master-secret-using-the-mmc-snap-in"></a>若要使用 MMC 嵌入式管理單元還原主要密碼  
  
1.  在 **[開始]** 功能表上，依序按一下 **[所有程式]**及 **[Microsoft 企業單一登入]**，然後按一下 **[SSO 管理]**。  
  
2.  在 ENTSSO MMC 嵌入式管理單元的範圍窗格中，展開 **[企業單一登入]** 節點。  
  
3.  以滑鼠右鍵按一下**系統**，然後按一下 **還原密碼**。  
  
### <a name="to-restore-the-master-secret-using-the-command-line"></a>使用命令列還原主要密碼  
  
1.  在**啟動**功能表上，按一下 **所有程式**，然後按一下 **附屬應用程式**。 以滑鼠右鍵按一下**命令提示字元**，然後按一下 **執行身分...**.  
  
2.  選取適當的系統管理員，然後按一下**確定**。  
  
3.  在命令列，移至「企業單一登入」安裝目錄。 預設安裝目錄是*\<磁碟機 >*: \Program Files\Common Files\Enterprise Single Sign-on。  
  
4.  型別**ssoconfig – restoreSecret\<還原檔案 >**，其中**\<還原檔案 >**是儲存主要密碼的檔案名稱與路徑。  
  
    > [!NOTE]
    >  在支援使用者帳戶控制 (UAC) 的系統上，您可能需要使用系統管理權限來執行工具。  
  
## <a name="see-also"></a>另請參閱  
 [如何產生主要密碼](../core/how-to-generate-the-master-secret.md)   
 [如何備份主要密碼](../core/how-to-back-up-the-master-secret.md)   
 [主要密碼伺服器](../core/master-secret-server.md)   
 [管理主要密碼](../core/managing-the-master-secret.md)