---
title: 如何備份主要密碼 |Microsoft 文件
ms.custom: ''
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- managing [Master Secret server], backing up
- backing up, Master Secret server
- Master Secret server, backing up
ms.assetid: 22c23f66-b7df-4379-8a9f-065406ba8aa8
caps.latest.revision: 14
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 185f3ea674015e02cac2bdaa785c2ee06e67db65
ms.sourcegitcommit: 8418b1a8f38b7f56979cd6e203f0b591e2f40fe1
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/28/2018
ms.locfileid: "25969580"
---
# <a name="how-to-back-up-the-master-secret"></a>如何備份主要密碼
您可以從主要密碼伺服器將主要密碼備份至 NTFS 檔案系統或卸除式媒體 (例如磁片)。  
  
 您必須是「單一登入管理員」和 Windows 系統管理員才能執行此作業。 SSO 系統會提示您輸入密碼。 若以後要復原密碼，您必須指定相同密碼。  
  
> [!CAUTION]
>  若主要密碼伺服器失敗且遺失金鑰，或者是金鑰損毀，您將無法擷取儲存在 SSO 資料庫中的資料。 您必須備份主要密碼，否則會有遺失 SSO 資料庫資料的風險。  
  
### <a name="to-back-up-the-master-secret-using-the-mmc-snap-in"></a>使用 MMC 嵌入式管理單元備份主要密碼  
  
1.  在 **[開始]** 功能表上，依序按一下 **[所有程式]** 及 **[Microsoft 企業單一登入]**，然後按一下 **[SSO 管理]**。  
  
2.  在 ENTSSO MMC 嵌入式管理單元的範圍窗格中，展開 **[企業單一登入]** 節點。  
  
3.  以滑鼠右鍵按一下 **系統**, ，然後按一下  **備份密碼**。  
  
### <a name="to-back-up-the-master-secret-using-the-command-line"></a>使用命令列備份主要密碼  
  
1.  在 **啟動**  功能表上，按一下  **所有程式**, ，然後按一下  **附屬應用程式**。 以滑鼠右鍵按一下 **命令提示字元**, ，然後按一下  **執行身分...**。  
  
2.  選取適當的系統管理員，然後按一下 **確定**。  
  
3.  在命令列，移至「企業單一登入」安裝目錄。 預設安裝目錄是*\<磁碟機\>*: \Program Files\Common Files\Enterprise Single Sign-on。  
  
4.  型別 * * ssoconfig – backupSecret *\<備份檔案\>* * *，其中*\<備份檔案\>* 是其中的主要密碼將備份的檔案的名稱與路徑。 例如，A:\ssobackup.bak  
  
    > [!NOTE]
    >  在支援使用者帳戶控制 (UAC) 的系統上，您可能需要使用系統管理權限來執行工具。  
  
5.  輸入用來保護此檔案的密碼。 此時會提示您確認密碼，並輸入協助您記住此密碼的密碼提示。  
  
> [!IMPORTANT]
>  您必須將備份檔案儲存並存放在安全的位置。  
  
## <a name="see-also"></a>另請參閱  
 [如何產生主要密碼](../core/how-to-generate-the-master-secret.md)   
 [如何還原主要密碼](../core/how-to-restore-the-master-secret.md)   
 [主要密碼伺服器](../core/master-secret-server.md)   
 [管理主要密碼](../core/managing-the-master-secret.md)