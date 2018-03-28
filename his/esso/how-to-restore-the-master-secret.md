---
title: 如何還原主要密碼 |Microsoft 文件
ms.custom: ''
ms.date: 11/30/2017
ms.prod: host-integration-server
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: b331c9c5-ca90-4a05-b3f6-59db88bf73dc
caps.latest.revision: ''
author: gplarsen
ms.author: hisdocs; plarsen
manager: anneta
ms.openlocfilehash: 5e640f2762ed9f9cc03a7795062c98a6aa76a59d
ms.sourcegitcommit: 8418b1a8f38b7f56979cd6e203f0b591e2f40fe1
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/28/2018
---
# <a name="how-to-restore-the-master-secret"></a>如何還原主要密碼
資料復原程序的一部分，您可能必須還原主要密碼，才能重複使用現有的資料。 若要執行這項工作中，您必須登入主要密碼伺服器使用的是 Windows 系統管理員和單一登入 (SSO) 系統管理員的帳戶。  
  
### <a name="to-restore-the-master-secret-using-the-mmc-snap-in"></a>若要使用 MMC 嵌入式管理單元還原主要密碼  
  
1.  按一下**啟動**，指向 **程式**，按一下  **Microsoft 企業單一登入**，然後按一下  **SSO 管理**。  
  
2.  在 ENTSSO Microsoft Management Console (MMC) 嵌入式管理單元的範圍窗格中，展開 **企業單一登入**節點。  
  
3.  以滑鼠右鍵按一下**系統**，然後按一下 **還原主要密碼**。  
  
### <a name="to-restore-the-master-secret-using-the-command-line"></a>使用命令列還原主要密碼  
  
1.  在**啟動**功能表上，按一下 **程式**，然後按一下 **附屬應用程式**。 以滑鼠右鍵按一下 **命令提示字元**, ，然後按一下  **執行身分...**。  
  
2.  選取適當的系統管理員，然後按一下 **確定**。  
  
3.  在命令提示字元中，移至 「 企業單一登入 」 安裝目錄。  
  
     預設安裝目錄是*\<磁碟機 >*: \Program Files\Common Files\Enterprise Single Sign-on。  
  
4.  型別`ssoconfig –restoresecret <restore file>`，其中*\<還原檔案 >*是儲存主要密碼的檔案名稱與路徑。  
  
## <a name="see-also"></a>另請參閱  
 [如何產生主要密碼](../esso/how-to-generate-the-master-secret.md)   
 [如何備份主要密碼](../esso/how-to-back-up-the-master-secret.md)   
 [主要密碼伺服器](../esso/master-secret-server.md)   
 [管理主要密碼](../esso/managing-the-master-secret.md)