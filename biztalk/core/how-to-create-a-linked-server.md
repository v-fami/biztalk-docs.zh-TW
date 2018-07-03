---
title: 如何建立連結的伺服器 |Microsoft Docs
ms.custom: ''
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- servers, linking for backups
- backing up, linking servers
ms.assetid: 7d4aba3d-77c0-4cdf-8547-71e821ce34a1
caps.latest.revision: 26
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: fcb954062bb2cb2484a51570109b37341b1c12f9
ms.sourcegitcommit: 266308ec5c6a9d8d80ff298ee6051b4843c5d626
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/27/2018
ms.locfileid: "36980983"
---
# <a name="how-to-create-a-linked-server"></a>如何建立連結的伺服器
以分散式拓撲安裝 [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] 時，屬於 BizTalk 群組的資料庫會存在於多個 [!INCLUDE[btsSQLServerNoVersion](../includes/btssqlservernoversion-md.md)] 上。 您必須先設定每個遠端伺服器的連結伺服器連線，才能從 BizTalk 管理伺服器備份整個 BizTalk 環境。 連結的伺服器是 OLE DB 資料來源中使用[!INCLUDE[btsSQLServerNoVersion](../includes/btssqlservernoversion-md.md)]分散式查詢。  
  
 備份和還原程序的一部分，備份[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]工作會自動建立連結的伺服器。 但是，如果需要，您可以手動使用這個程序來建立連結的伺服器。  
  
 連結的伺服器也可以建立使用*sp_addlinkedserver*預存程序。 有這項作業相關聯的安全性考量。 使用 sp_addlinkedserver 來建立連結的伺服器時，所有本機登入將會對應到新增連結的伺服器的預設值。 若要控制存取連結的伺服器， *sp_droplinkedsvrlogin*程序應該用來卸除全域的登入對應，後面接著*sp_addlinkedsvrlogin*對應所需的登入帳戶新增連結的伺服器。 當使用 sp_addlinkedsvrlogin，建議您設定@useself參數 = TRUE。 這可避免需要嵌入您的 SQL 指令碼中的使用者名稱和密碼。  

> [!TIP]
> 這些步驟可能會隨著時間改變。 我們建議您參考[!INCLUDE[btsSQLServerNoVersion](../includes/btssqlservernoversion-md.md)]文件，網址[建立連結的伺服器](https://docs.microsoft.com/sql/relational-databases/linked-servers/create-linked-servers-sql-server-database-engine)。
  
## <a name="prerequisites"></a>必要條件  
  
- 使用成員的帳戶登入[!INCLUDE[btsSQLServerNoVersion](../includes/btssqlservernoversion-md.md)] **sysadmin**固定的伺服器角色  
  
- 建立本機[!INCLUDE[btsSQLServerNoVersion](../includes/btssqlservernoversion-md.md)]登入。 在下列步驟中，此帳戶會對應至登入上[!INCLUDE[btsSQLServerNoVersion](../includes/btssqlservernoversion-md.md)]您會連結到。 
  
## <a name="create-a-linked-server"></a>建立連結的伺服器
  
1. 開啟**SQL Server Management Studio**，輸入您的本機名稱[!INCLUDE[btsSQLServerNoVersion](../includes/btssqlservernoversion-md.md)]，然後選取**Connect**。  
  
2. 依序展開**Server 物件**，以滑鼠右鍵按一下**連結的伺服器**，然後選取**新增連結的伺服器**。  

   若要查看**Server Objects**，連接到本機內部[!INCLUDE[btsSQLServerNoVersion](../includes/btssqlservernoversion-md.md)]。 然後， **Server 物件**應該會顯示。
  
3. 在 **連結的伺服器**文字中，輸入完整的網路名稱[!INCLUDE[btsSQLServerNoVersion](../includes/btssqlservernoversion-md.md)]您想要連結至。  
  
   > [!NOTE]
   >  此程序通常是指您要連結至與遠端伺服器的伺服器。 這是僅為方便參考，表示要在本機伺服器的連結 （「 遠端 」） 伺服器的關聯性。  
  
4. 底下**伺服器類型**，選取**SQL Server**。  
  
5. 在左窗格中選取 [安全性] 。 

   在此步驟中，您可以對應您所建立的本機帳戶遠端伺服器登入。 您的選項： 
    
   | | | 
   |---|---|
   | **會使用登入的目前安全性內容** | 在網域環境中，使用者通常連接使用其網域登入。 此選項可能是最佳，因為登入的網域帳戶的安全性內容會對應至您所建立的本機帳戶。|
   | **使用此安全性內容建立** | 當使用者連線到本機的 SQL Server 使用 SQL Server 登入時，此選項可能是最佳的。 然後輸入登入和密碼帳戶連結的伺服器上。 |


6. 選取 **新增**，並輸入下列命令： 

   1. 底下**本機登入**，選取您所建立的本機帳戶。 
   2. 請檢查**Impersonate**如果本機登入也存在於遠端伺服器上。 
   3. 或者，如果本機登入將會對應至遠端[!INCLUDE[btsSQLServerNoVersion](../includes/btssqlservernoversion-md.md)]登入，請輸入**遠端使用者**名稱並**遠端密碼**遠端伺服器登入。  
  
      > [!NOTE]
      >  若要使用模擬，您[!INCLUDE[btsSQLServerNoVersion](../includes/btssqlservernoversion-md.md)]設定和登入帳戶必須符合委派的需求。 請參閱[以便進行委派設定連結伺服器](https://msdn.microsoft.com/library/ms189580.aspx)如需詳細資訊。  

7. 在左窗格中，選擇**伺服器選項**。 設定**RPC**並**RPC 輸出**參數**True**，然後選取 **[確定]**。 
 
> [!TIP]
> 如需詳細資訊和建議建立連結的伺服器時使用 includig`sp_addlinkedserver`儲存 procedcure，請參閱 <<c2> [ 建立連結的伺服器](https://docs.microsoft.com/sql/relational-databases/linked-servers/create-linked-servers-sql-server-database-engine)。

  
## <a name="see-also"></a>另請參閱  
 [備份和還原的進階資訊](../core/advanced-information-about-backup-and-restore1.md)