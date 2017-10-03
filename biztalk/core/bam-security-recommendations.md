---
title: "BAM 安全性建議 |Microsoft 文件"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- security, BAM
- managing [BAM], security
- BAM, security
ms.assetid: 73613123-c1ed-477a-9f5c-342b2573c975
caps.latest.revision: "23"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 7f26cd3051dd296cc2849cb9c8ba7f8aa1d7ac6a
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/20/2017
---
# <a name="bam-security-recommendations"></a>BAM 安全性建議
建議您依照下列則保護與部署您環境中的 BAM：  
  
-   如果您使用 [!INCLUDE[SQLServer2008or2005](../includes/sqlserver2008or2005-md.md)]，管理電腦必須安裝下列軟體才能部署 BAM：  
  
    -   [!INCLUDE[SQLServer2008or2005](../includes/sqlserver2008or2005-md.md)]  
  
    -   [!INCLUDE[SQLServer2008or2005](../includes/sqlserver2008or2005-md.md)] 用戶端工具  
  
    -   [!INCLUDE[SQLServer2008or2005](../includes/sqlserver2008or2005-md.md)]Integration Services  
  
    -   [!INCLUDE[SQLServer2008or2005](../includes/sqlserver2008or2005-md.md)] Analysis Services  
  
    -   [!INCLUDE[SQLServer2005_SP3_long](../includes/sqlserver2005-sp3-long-md.md)] (如果您要使用 BAM 警示)  
  
        > [!NOTE]
        >  [!INCLUDE[SQLServer2005_SP3_short](../includes/sqlserver2005-sp3-short-md.md)] 含有 [!INCLUDE[btsSQLServerNoVersion](../includes/btssqlservernoversion-md.md)] 適用的 [!INCLUDE[SQLServer2008or2005](../includes/sqlserver2008or2005-md.md)] Notification Services。  
  
    > [!NOTE]
    >  執行分析 DTS 封裝的使用者內容，必須是 BAM 主要匯入資料庫和 BAM 星狀結構描述資料庫 db_owner [!INCLUDE[btsSQLServerNoVersion](../includes/btssqlservernoversion-md.md)] 角色的成員。 此外，執行 Analysis Services 的服務帳戶必須是 OLAP 系統管理員，且必須是 BAM 星狀結構描述資料庫的 db_owner。 如需詳細資訊，請參閱 「 Microsoft 說明及支援 」 網站，網址[http://go.microsoft.com/fwlink/?LinkId=22781](http://go.microsoft.com/fwlink/?LinkId=22781)。  
  
-   多個使用者需要存取即時和封存資料： 銷售人員、 商務經理人，以及其他等等。 這些使用者必須擁有 BAM 主要匯入資料庫與 BAM 分析資料庫所在網域 (企業網域) 的網域帳戶，但是他們的帳戶不需具備存取 BizTalk 資源的權限。  
  
-   若要讓使用者能夠存取 BAM 資料的檢視，您必須使用 BAM 管理公用程式 (BM.exe) 授與使用者檢視的權限，並且使用者必須擁有 SQL 登入權限。 如需 BAM 管理公用程式的詳細資訊，請參閱[BAM 管理公用程式](../core/bam-management-utility.md)。  
  
-   若要將使用者新增至具有 BAM 分析資料庫中 Cube 存取權限的角色，您必須擁有位於與 BAM 資料庫相同網域的管理電腦。  
  
-   管理 BAM 的人員必須是 BAM 主要匯入資料庫、星狀結構描述資料庫以及 BAM 封存資料庫的 db_owner， 該人員同時必須是 BAM 分析資料庫的 OLAP 系統管理員。  
  
-   如果您正在部署 Microsoft Office Excel 活頁簿 (.xls 檔案)，Excel 必須安裝於管理電腦上。 在部署活頁簿之前，請先開啟活頁簿，確定巨集安全性設定為「高」，而且沒有出現任何警告。  
  
-   如果沒有任何商務需要傳遞給連接實際資料的使用者 BAM Excel 活頁簿，建議您使用 XML 檔案部署活頁簿。 這樣就不需要在管理電腦上安裝 Excel 和需要檢查巨集安全性層級。  
  
    > [!IMPORTANT]
    >  當您移除使用者的檢視權限時，也必須記得刪除使用者設定的任何警示訂閱。 如需有關如何從警示移除訂閱者的詳細資訊，請參閱[如何從警示移除訂閱者](../core/how-to-remove-subscribers-from-an-alert.md)。  
  
## <a name="see-also"></a>另請參閱  
 [最低安全性使用者權限](../core/minimum-security-user-rights.md)   
 [BizTalk Server 部署的安全性建議](../core/security-recommendations-for-a-biztalk-server-deployment.md)