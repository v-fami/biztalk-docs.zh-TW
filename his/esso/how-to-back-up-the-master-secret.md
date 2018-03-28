---
title: 如何備份主要密碼 |Microsoft 文件
ms.custom: ''
ms.date: 11/30/2017
ms.prod: host-integration-server
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 0841c52a-7b15-45f8-9900-f5c9e3abd90b
caps.latest.revision: ''
author: gplarsen
ms.author: hisdocs; plarsen
manager: anneta
ms.openlocfilehash: 124c077d7a15a4938f94239518ad02c8268074a4
ms.sourcegitcommit: 8418b1a8f38b7f56979cd6e203f0b591e2f40fe1
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/28/2018
---
# <a name="how-to-back-up-the-master-secret"></a>如何備份主要密碼
您可以從主要密碼伺服器將主要密碼備份至 NTFS 檔案系統或卸除式媒體 (例如磁片)。  
  
 您必須是單一登入系統管理員和 Windows 系統管理員才能執行這項工作。 單一登入 (SSO) 系統會提示您輸入密碼。 若以後要復原密碼，您必須指定相同密碼。  
  
> [!CAUTION]
>  如果主要密碼伺服器當機和遺失金鑰，或如果是金鑰損毀，您將無法擷取儲存在認證資料庫中的資料。 您必須備份主要密碼或您可能會遺失認證資料庫中的資料。  
  
### <a name="to-back-up-the-master-secret-using-the-mmc-snap-in"></a>使用 MMC 嵌入式管理單元備份主要密碼  
  
1.  按一下**啟動**，指向 **程式**，按一下  **Microsoft 企業單一登入**，然後按一下  **SSO 管理**。  
  
2.  在 ENTSSO Microsoft Management Console (MMC) 嵌入式管理單元的範圍窗格中，展開 **企業單一登入**節點。  
  
3.  以滑鼠右鍵按一下**系統**，然後按一下 **備份主要密碼**。  
  
### <a name="to-back-up-the-master-secret-using-the-command-line"></a>使用命令列備份主要密碼  
  
1.  在**啟動**功能表上，按一下 **程式**，然後按一下 **附屬應用程式**。 以滑鼠右鍵按一下 **命令提示字元**, ，然後按一下  **執行身分...**。  
  
2.  選取適當的系統管理員，然後按一下 **確定**。  
  
3.  在命令提示字元中，移至 「 企業單一登入 」 安裝目錄。  
  
     預設安裝目錄是*\<磁碟機 >*: \Program Files\Common Files\Enterprise Single Sign-on。  
  
4.  型別`ssoconfig –backupsecret <backup file>`，其中*\<備份檔案 >*是其中的主要密碼將備份，例如，檔案的名稱與路徑`A:\ssobackup.bak`。  
  
5.  提供密碼來保護這個檔案。  
  
     此時會提示您確認密碼，並輸入協助您記住此密碼的密碼提示。  
  
> [!IMPORTANT]
>  您必須將備份檔案儲存並存放在安全的位置。  
  
## <a name="see-also"></a>另請參閱  
 [如何產生主要密碼](../esso/how-to-generate-the-master-secret.md)   
 [如何還原主要密碼](../esso/how-to-restore-the-master-secret.md)   
 [主要密碼伺服器](../esso/master-secret-server.md)   
 [管理主要密碼](../esso/managing-the-master-secret.md)