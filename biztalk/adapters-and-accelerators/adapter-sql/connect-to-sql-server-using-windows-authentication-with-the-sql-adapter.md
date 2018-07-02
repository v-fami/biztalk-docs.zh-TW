---
title: 連接到 SQL 配接器搭配使用 Windows 驗證的 SQL Server |Microsoft Docs
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
ms.openlocfilehash: fa19a836d4465b96b663dd4abc5f89500b37e338
ms.sourcegitcommit: 266308ec5c6a9d8d80ff298ee6051b4843c5d626
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/27/2018
ms.locfileid: "36973639"
---
# <a name="connect-to-sql-server-using-windows-authentication-with-the-sql-adapter"></a>連接到 SQL 配接器搭配使用 Windows 驗證的 SQL Server
[!INCLUDE[adaptersql_md](../../includes/adaptersql-md.md)]可讓配接器用戶端使用 Windows 驗證來建立與 SQL Server 的連線。 若要使用 Windows 驗證，空白的使用者名稱和密碼，必須輸入配接器用戶端。 

若要連接到使用 Visual Studio 內的 Windows 驗證的 SQL Server，請參閱[連接到 SQL Server，在 Visual Studio 中使用 取用配接器服務增益集](../../adapters-and-accelerators/adapter-sql/connect-to-sql-server-in-visual-studio-using-the-consume-adapter-service-add-in.md)。  
  
 若要啟用配接器用戶端使用 Windows 驗證來連接到 SQL Server，請執行 SQL Server 的電腦上的使用者啟用 Windows 驗證。  

> [!TIP]
> 如果您的 SQL Server 上未安裝 SQL Server Management Studio，您可以[下載 SQL Server Management Studio (SSMS)](https://docs.microsoft.com/sql/ssms/download-sql-server-management-studio-ssms)，並將它安裝。 
 
## <a name="add-the-user-in-sql-server"></a>在 SQL Server 中加入使用者  
  
1.  開啟 SQL Server Management Studio。 在**連接到伺服器**，選取**Database Engine**，輸入您的 SQL**伺服器名稱**，並輸入管理員認證以連接到伺服器。  

    選取 [連接]。
  
2.  在**物件總管 中**、 展開 SQL Server，展開**安全性**，以滑鼠右鍵按一下**登入**，然後選取**新登入**。  
  
3.  針對**登入名稱**，輸入中的 Windows 使用者名稱`domain\username`格式。  

    > [!NOTE]
    >* 當此配接器使用 BizTalk 中，您輸入時，登入名稱是主控件執行個體帳戶的身分識別。  
    >
    >* .NET 程式碼中使用此配接器，當您輸入時，登入名稱會是該處理序的識別。
  
4.  選取 **使用者對應**（左的窗格）。 選取要與使用者相關聯的資料庫。 典型的 BizTalk 使用者應該與下列資料庫相關聯： 

* BizTalkDTADb
* BizTalkMgmtDb
* BizTalkMsgBoxDb
* BTAHL7
* SSODB

5. 在 **資料庫角色成員資格對象**方塊中，選取**db_owner**的所有 BizTalk 資料庫。  

    > [!NOTE]
    > [伺服器和 SQL Server 中的資料庫角色](https://msdn.microsoft.com/library/bb669065.aspx)在角色上提供良好的資訊。 
  
6. 選取 [確定] 儲存您的變更。
  
   新增使用者之後，使用者可以連接並使用 SQL Server 驗證進行驗證[!INCLUDE[adaptersqlshort](../../includes/adaptersqlshort-md.md)]、 記錄以空白的使用者名稱和密碼。  



## <a name="see-also"></a>另請參閱  
 [建立 SQL Server 的連線](../../adapters-and-accelerators/adapter-sql/create-a-connection-to-sql-server.md)