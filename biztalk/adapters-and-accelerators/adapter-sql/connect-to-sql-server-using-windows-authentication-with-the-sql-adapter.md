---
title: 連接到 SQL Server 使用 Windows 驗證搭配 SQL 配接器 |Microsoft 文件
ms.custom: ''
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 45c54b2a-e056-496f-9f10-f19b6a3ca1a6
caps.latest.revision: 12
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: db7d0cbe07155d09085091d995b524b3058c0bf0
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/20/2017
ms.locfileid: "22222310"
---
# <a name="connect-to-sql-server-using-windows-authentication-with-the-sql-adapter"></a>連接到 SQL Server 使用 Windows 驗證搭配 SQL 配接器
[!INCLUDE[adaptersql_md](../../includes/adaptersql-md.md)]可讓配接器用戶端使用 Windows 驗證來建立與 SQL Server 的連線。 若要使用 Windows 驗證，配接器用戶端必須輸入空的使用者名稱和密碼。 

若要連接到 SQL Server 使用 Visual Studio 中的 Windows 驗證，請參閱[連接到 SQL Server 使用配接器服務增益集所使用的 Visual Studio 中](../../adapters-and-accelerators/adapter-sql/connect-to-sql-server-in-visual-studio-using-the-consume-adapter-service-add-in.md)。  
  
 若要讓配接器用戶端使用 Windows 驗證來連接到 SQL Server，請執行 SQL Server 的電腦上的使用者啟用 Windows 驗證。  

> [!TIP]
> 如果您的 SQL Server 上未安裝 SQL Server Management Studio，您可以[下載 SQL Server Management Studio (SSMS)](https://docs.microsoft.com/sql/ssms/download-sql-server-management-studio-ssms)，並安裝它。 
 
## <a name="add-the-user-in-sql-server"></a>SQL Server 中新增使用者  
  
1.  開啟 SQL Server Management Studio。 在**連接到伺服器**，選取**Database Engine**，輸入您的 SQL**伺服器名稱**，並輸入管理員認證以連接到伺服器。  

    選取 [連接]。
  
2.  在**物件總管] 中**，依序展開 [SQL Server**安全性**，以滑鼠右鍵按一下**登入**，然後選取**新登入**。  
  
3.  如**登入名稱**，輸入中的 Windows 使用者名稱`domain\username`格式。  

    > [!NOTE]
    >* 當此配接器使用 BizTalk 中，您輸入時，則登入名稱是主控件執行個體帳戶的身分識別。  
    >
    >* .NET 程式碼中使用此配接器，當您輸入時，登入名稱是該處理序的識別。
  
4.  選取**使用者對應**（左的窗格）。 選取要與使用者相關聯的資料庫。 在一般 BizTalk 使用者應該與下列資料庫相關聯： 

* BizTalkDTADb
* BizTalkMgmtDb
* BizTalkMsgBoxDb
* BTAHL7
* SSODB

5. 在**資料庫角色成員資格，對**方塊中，選取**db_owner**所有 BizTalk 資料庫。  

    > [!NOTE]
    > [伺服器和 SQL Server 中的資料庫角色](https://msdn.microsoft.com/library/bb669065.aspx)的角色提供良好的資訊。 
  
6.  選取 [確定] 儲存您的變更。
  
 加入使用者之後，使用者可以連接和驗證至 SQL Server 使用[!INCLUDE[adaptersqlshort](../../includes/adaptersqlshort-md.md)]、 記錄以空白的使用者名稱和密碼。  



## <a name="see-also"></a>另請參閱  
 [建立 SQL Server 的連接](../../adapters-and-accelerators/adapter-sql/create-a-connection-to-sql-server.md)