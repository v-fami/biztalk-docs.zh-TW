---
title: 如何顯示 SSO 資料庫資訊 |Microsoft Docs
ms.custom: ''
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- managing [SSO], viewing SSO database
- SSO database, viewing
- viewing, SSO database
ms.assetid: 0ebadd2e-6ea5-460c-b0a8-f48589e6bf1c
caps.latest.revision: 11
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 8371ccae36fe66051178da5baa55360e9fcf8406
ms.sourcegitcommit: 266308ec5c6a9d8d80ff298ee6051b4843c5d626
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/27/2018
ms.locfileid: "37010015"
---
# <a name="how-to-display-the-sso-database-information"></a>如何顯示 SSO 資料庫資訊
您可以使用 MMC 嵌入式管理單元或是命令列 (ssomanage) 公用程式，以檢視 SSO 資料庫資訊。  
  
### <a name="to-display-the-sso-database-information-using-the-mmc-snap-in"></a>若要使用 MMC 嵌入式管理單元顯示 SSO 資料庫資訊  
  
1.  在 **[開始]** 功能表上，依序按一下 **[所有程式]** 及 **[Microsoft 企業單一登入]**，然後按一下 **[SSO 管理]**。  
  
2.  在 ENTSSO MMC 嵌入式管理單元的範圍窗格中，展開 **[企業單一登入]** 節點。  
  
3.  使用滑鼠右鍵按一下 **[系統]**，然後按一下 **[屬性]**。  
  
4.  按一下索引標籤**系統屬性**對話方塊以檢視 SSO 資料庫資訊。  
  
### <a name="to-display-the-sso-database-information-using-the-command-line"></a>使用命令列顯示 SSO 資料庫資訊  
  
1.  在上**開始**功能表上，按一下**執行**，然後輸入**cmd**。  
  
2.  在命令列提示字元中，移至「企業單一登入」安裝目錄。 預設的安裝目錄**\<磁碟機\>**: \Program Files\Common Files\Enterprise Single Sign-on。  
  
3.  型別**ssomanage – displaydb**。  
  
    > [!NOTE]
    >  在支援 [使用者帳戶控制] \(UAC) 的系統上，您必須以系統管理權限執行此工具。  
  
### <a name="to-display-the-sso-database-the-sso-server-is-connected-to-using-the-command-line"></a>使用命令列顯示 SSO 伺服器連接的 SSO 資料庫  
  
1. 在上**開始**功能表上，按一下**執行**，然後輸入**cmd**。  
  
2. 在命令列提示字元中，移至「企業單一登入」安裝目錄。 預設的安裝目錄**\<磁碟機\>**: \Program Files\Common Files\Enterprise Single Sign-on。  
  
3. 型別**ssomanage – showdb**。  
  
   > [!NOTE]
   >  在支援 [使用者帳戶控制] \(UAC) 的系統上，您必須以系統管理權限執行此工具。  
  
   下表說明這些程序顯示的值。  
  
|屬性|ReplTest1|  
|--------------|-----------|  
|[SQL Server]|**\<SQL Server 名稱\>**|  
|單一登入資料庫|**\<SQL Server 資料庫名稱\>**|  
|單一登入密碼伺服器名稱|**\<單一登入伺服器名稱\>**|  
|單一登入系統管理員帳戶|網域\帳戶名稱|  
|單一登入分支機構系統管理員帳戶|網域\帳戶名稱|  
|已刪除應用程式的稽核表格大小 (稽核項目的數目)|1,000 （預設值）|  
|已刪除使用者對應的稽核表格大小 (稽核項目的數目)|1,000 （預設值）|  
|外部認證查詢的稽核表格大小 (稽核項目的數目)|1,000 （預設值）|  
|票證逾時 (分鐘)|2 （預設值）<br /><br /> 這個值可以是 1 到 525,600 的整數|  
|認證快取逾時 (分鐘)|60 （預設值）|  
|單一登入狀態|已啟用/已停用|  
|允許票證|是/否 (預設值)|  
|驗證票證|是 (預設值)/否|  
  
## <a name="see-also"></a>另請參閱  
 [如何設定 SSO 票證](../core/how-to-configure-the-sso-tickets.md)   
 [使用 SSO](../core/using-sso.md)